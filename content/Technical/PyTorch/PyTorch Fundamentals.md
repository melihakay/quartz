---
title: PyTorch Fundamentals
draft: false
description: 
aliases: 
tags: 
date:
---
Many fundamental [[PyTorch]] operations used for deep learning and neural networks.

## Creating Tensors

```python
import torch
print(torch.__version__)

tn = torch.tensor([3, 4, 5])
tn.ndim # dimensions
tn.shape # n of items 
if tn.ndim == 0: tn.item() # returns the values of scalar

if tn.ndim > 1: pass # use UPPER CASE for naming tensors with dimension > 1
```

## Random Tensors

```python
# Create a random tensor of size (3, 4)
random_tensor = torch.rand(size=(3, 4))
random_tensor, random_tensor.dtype
```

## Zeros and Ones

```python
# Create a tensor of all zeros
zeros = torch.zeros(size=(3, 4))
zeros, zeros.dtype

# Create a tensor of all ones
ones = torch.ones(size=(3, 4))
ones, ones.dtype

# Like
ones_like = torch.ones_like(input=zeros)
zeros_like = torch.zeros_like(input=ones)
```

## Arranging

```python
# Use torch.arange(), torch.range() is deprecated 
zero_to_ten_deprecated = torch.range(0, 10) # Note: this may return an error in the future

# Create a range of values 0 to 10
zero_to_ten = torch.arange(start=0, end=10, step=1)
```

## Dtypes

8-bit, 16-bit inference in ML means that model uses x-bit floats to hold the values. This has impact on performance and precision.

```python
# Default datatype for tensors is float32
float_32_tensor = torch.tensor([3.0, 6.0, 9.0],
                               dtype=None, # defaults to None, which is torch.float32 or whatever datatype is passed
                               device=None, # defaults to None, which uses the default tensor type
                               requires_grad=False) # if True, operations performed on the tensor are recorded 

print(float_32_tensor.shape, float_32_tensor.dtype, float_32_tensor.device)

# Create a tensor and check its datatype
tensor = torch.arange(10., 100., 10.)
tensor.dtype

# Create a float16 tensor
tensor_float16 = tensor.type(torch.float16)
tensor_float16

# Create an int8 tensor
tensor_int8 = tensor.type(torch.int8)
tensor_int8
```

## Information from tensors

```python
# Create a tensor
some_tensor = torch.rand(3, 4)

# Find out details about it
print(some_tensor)
print(f"Shape of tensor: {some_tensor.shape}")
print(f"Datatype of tensor: {some_tensor.dtype}")
print(f"Device tensor is stored on: {some_tensor.device}") # will default to CPU
```

## Operations

```python
# Element-wise multiplication (each element multiplies its equivalent, index 0->0, 1->1, 2->2)
print(tensor, "*", tensor)
print("Equals:", tensor * tensor)

# Matrix multiplication
torch.matmul(tensor, tensor)
# short for matmul
torch.mm(tensor, tensor)
```

## nn.Linear

```python
linear = torch.nn.Linear(in_features=2, # in_features = matches inner dimension of input 
                         out_features=6) # out_features = describes outer value 
x = tensor_A
output = linear(x)
```

## Aggregation

```python
print(f"Minimum: {x.min()}")
print(f"Maximum: {x.max()}")
# print(f"Mean: {x.mean()}") # this will error
print(f"Mean: {x.type(torch.float32).mean()}") # won't work without float datatype
print(f"Sum: {x.sum()}")

torch.max(x), torch.min(x), torch.mean(x.type(torch.float32)), torch.sum(x)

# Create a tensor
tensor = torch.arange(10, 100, 10)
print(f"Tensor: {tensor}")

# Returns index of max and min values
print(f"Index where max value occurs: {tensor.argmax()}")
print(f"Index where min value occurs: {tensor.argmin()}")
```

