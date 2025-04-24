![[deep_learning_institute_logo.png|center]]

This is the notes I have taken while studying instructor-led Fundamentals of Deep Learning course given by [[Prof. Dr. Ünver Çiftçi]]. Course mainly revolves around [[PyTorch]].

# 1. Image Classification with the MNIST Dataset

# 1.1 Preparing Dataset
First set device, see [[How to select the device in PyTorch]]. Then load the data into memory using [[Torch Vision]]:

```python
import torchvision
train_set = torchvision.datasets.MNIST("./data/", train=True, download=True)
valid_set = torchvision.datasets.MNIST("./data/", train=False, download=True)
```

One can inspect these datasets as follows:

```python
x_0, y_0 = train_set[0]
print(f"X_0: {x_0}, type: {type(x_0)}")
print(f"Y_0: {y_0}, type: {type(y_0)}")
```

The dataset contains [[PIL]] images. To use them we need to convert them to [[PyTorch Tensors|Tensors]].
```python
import torchvision
import torchvision.transforms.v2 as transforms
import torchvision.transforms.functional as F
import matplotlib.pyplot as plt

# Create a tranform function.
trans = transforms.Compose([transforms.ToTensor()])
x_0_tensor = trans(x_0)

print("Tensor data type: {}".format(x_0_tensor.dtype)) # torch.float32
print("Tensor size: {}".format(x_0_tensor.size())) # torch.Size([1, 28, 28])

x_0_gpu = x_0_tensor.cuda() # copies the tensor to GPU
# alternatively you can use x_0_tensor.to(device)
```

One can convert tensors to PIL images to visualize:
```python
image = F.to_pil_image(x_0_tensor)
plt.imshow(image, cmap='gray')
```

>[!tip] [Transforms](https://pytorch.org/vision/stable/transforms.html) are a group of torchvision functions that can be used to transform a dataset.

You can apply a transform to a dataset as following:
```python
trans = transforms.Compose([transforms.ToTensor()])
train_set.transform = trans
valid_set.transform = trans
```

If our dataset is a deck of flash cards, a [DataLoader](https://pytorch.org/tutorials/beginner/basics/data_tutorial.html#preparing-your-data-for-training-with-dataloaders) defines how we pull cards from the deck to train an AI model. We could show our models the entire dataset at once. Not only does this take a lot of computational resources, but [research shows](https://arxiv.org/pdf/1804.07612) using a smaller batch of data is more efficient for model training.

For example, if our `batch_size` is 32, we will train our model by shuffling the deck and drawing 32 cards. We do not need to shuffle for validation as the model is not learning, but we will still use a `batch_size` to prevent memory errors.

```python
batch_size = 32

train_loader = DataLoader(train_set, batch_size=batch_size, shuffle=True)
valid_loader = DataLoader(valid_set, batch_size=batch_size)
```

# 1.2 Creating Model

1. A [Flatten](https://pytorch.org/docs/stable/generated/torch.nn.Flatten.html) used to convert n-dimensional data into a vector.
2. An input layer, the first layer of neurons
3. A hidden layer, another layor of neurons "hidden" between the input and output
4. An output layer, the last set of neurons which returns the final prediction from the model

More information about these layers is available in [this blog post](https://medium.com/@sarita_68521/basic-understanding-of-neural-network-structure-eecc8f149a23) by Sarita.

First import NN and create layers for the network:
```python
import torch.nn as nn
layers = list()
```

### 1.2.1 Flattening the image
```python
test_matrix = torch.tensor(
    [[1, 2, 3],
     [4, 5, 6],
     [7, 8, 9]]
)
batch_test_matrix = test_matrix[None, :] # `None` adds a new dimension where `:` selects all the data in a tensor.
nn.Flatten()(batch_test_matrix)
```
Order matters! This is what happens when we do it the other way:
```python
nn.Flatten()(test_matrix[:, None])
# tensor([[1, 2, 3],
#         [4, 5, 6],
#         [7, 8, 9]])
```

Now let's add this to the network:
```python
layers = [
    nn.Flatten()
]
```

Our first layer of neurons connects our flattened image to the rest of our model. To do that, we will use a [Linear](https://pytorch.org/docs/stable/generated/torch.nn.Linear.html) layer. This layer will be _densely connected_, meaning that each neuron in it, and its weights, will affect every neuron in the next layer.

In order to create these weights, Pytorch needs to know the size of our inputs and how many neurons we want to create. Since we've flattened our images, the size of our inputs is the number of channels, number of pixels vertically, and number of pixels horizontally multiplied together.

```python
input_size = 1 * 28 * 28
layers = [
    nn.Flatten(),
    nn.Linear(input_size, 512),  # Input
    nn.ReLU(),  # Activation for input
]
```

### 1.2.2 Hidden Layer

```python
layers = [
    nn.Flatten(),
    nn.Linear(input_size, 512),  # Input
    nn.ReLU(),  # Activation for input
    nn.Linear(512, 512),  # Hidden
    nn.ReLU()  # Activation for hidden
]
```

### 1.2.3 Output Layer

```python
n_classes = 10

layers = [
    nn.Flatten(),
    nn.Linear(input_size, 512),  # Input
    nn.ReLU(),  # Activation for input
    nn.Linear(512, 512),  # Hidden
    nn.ReLU(),  # Activation for hidden
    nn.Linear(512, n_classes)  # Output
]
```

### 1.2.4 Compiling the model

A [Sequential](https://pytorch.org/docs/stable/generated/torch.nn.Sequential.html) model expects a sequence of arguments, not a list, so we can use the [* operator](https://docs.python.org/3/reference/expressions.html#expression-lists) to unpack our list of layers into a sequence. We can print the model to verify these layers loaded correctly.

```python
model = nn.Sequential(*layers)
model.to(device) # to GPU if available
```

To check which device a model is on, we can check which device the model parameters are on. Check out this [stack overflow](https://stackoverflow.com/questions/58926054/how-to-get-the-device-type-of-a-pytorch-module-conveniently) post for more information.
```
next(model.parameters()).device
```

[PyTorch 2.0](https://pytorch.org/get-started/pytorch-2.0/) introduced the ability to compile a model for faster performance. Learn more about it [here](https://pytorch.org/tutorials/intermediate/torch_compile_tutorial.html).
```python
model = torch.compile(model)
```


## 1.3 Training the model

Let's first define the loss and optimization.
```python
from torch.optim import Adam

loss_function = nn.CrossEntropyLoss()
optimizer = Adam(model.parameters())
```

Calculating the accuracy:
```python
train_N = len(train_loader.dataset)
valid_N = len(valid_loader.dataset)

def get_batch_accuracy(output, y, N):
    pred = output.argmax(dim=1, keepdim=True)
    correct = pred.eq(y.view_as(pred)).sum().item()
    return correct / N
```

Train function:
```python
def train():
    loss = 0
    accuracy = 0

    model.train()
    for x, y in train_loader:
        x, y = x.to(device), y.to(device)
        output = model(x)
        optimizer.zero_grad()
        batch_loss = loss_function(output, y)
        batch_loss.backward()
        optimizer.step()

        loss += batch_loss.item()
        accuracy += get_batch_accuracy(output, y, train_N)
    print('Train - Loss: {:.4f} Accuracy: {:.4f}'.format(loss, accuracy))
```

Validation function:
```python
def validate():
    loss = 0
    accuracy = 0

    model.eval()
    with torch.no_grad():
        for x, y in valid_loader:
            x, y = x.to(device), y.to(device)
            output = model(x)

            loss += loss_function(output, y).item()
            accuracy += get_batch_accuracy(output, y, valid_N)
    print('Valid - Loss: {:.4f} Accuracy: {:.4f}'.format(loss, accuracy))
```

Main loop that trains and validates for 5 epochs.
```python
epochs = 5

for epoch in range(epochs):
    print('Epoch: {}'.format(epoch))
    train()
    validate()
```

Sample output would be:
```
Epoch: 0
Train - Loss: 379.7267 Accuracy: 0.9386
Valid - Loss: 40.7633 Accuracy: 0.9590
Epoch: 1
Train - Loss: 161.8372 Accuracy: 0.9729
Valid - Loss: 23.9223 Accuracy: 0.9759
Epoch: 2
Train - Loss: 109.4331 Accuracy: 0.9813
Valid - Loss: 31.3984 Accuracy: 0.9719
Epoch: 3
Train - Loss: 82.3793 Accuracy: 0.9861
Valid - Loss: 29.4242 Accuracy: 0.9724
Epoch: 4
Train - Loss: 66.2442 Accuracy: 0.9888
Valid - Loss: 22.8222 Accuracy: 0.9797
```

To see a single prediction:
```python
prediction = model(x_0_gpu)
prediction.argmax(dim=1, keepdim=True) == y_0
```

# 2. Image Classification with American Sign Language Dataset

