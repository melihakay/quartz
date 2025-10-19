Use the following to select the device that [[PyTorch]] will use:

```python
import torch

device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
print("Torch device: {}".format(device))
```
