# Perform Quantization for Model Compression and Efficient Inference

We will start by creating a simple model in PyTorch and we'll apply the post-training static quantization method to it:

```
import torch

import torch.nn as nn

import torch.quantization as quantization

class SimpleModel(nn.Module):
    def __init__(self):
        super(SimpleModel, self).__init__()
        self.fc1 = nn.Linear(10, 10)
        self.relu1 = nn.ReLU()
```