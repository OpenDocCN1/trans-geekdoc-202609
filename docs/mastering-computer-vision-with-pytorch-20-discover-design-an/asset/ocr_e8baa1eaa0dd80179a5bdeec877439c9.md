One of the standout features of PyTorch Lightning is how easily it scales models to multiple devices such as GPUs or even distributed training setups. Without Lightning, scaling PyTorch models to multi-GPU setups or distributed environments requires significant code changes and complexity. With PyTorch Lightning, this process is abstracted, allowing developers to scale their models with just a few lines of code.

Additionally, Lightning provides built-in support for features such as automatic mixed precision training, which can further optimize the training process, reducing memory usage while maintaining model performance.

# Example: PyTorch vs PyTorch Lightning Training Loop

Let's look at a basic example of training a model in PyTorch and compare it with how PyTorch Lightning simplifies this process.

# Standard PyTorch Training Loop:

```
import torch
import torch.nn as nn
import torch.optim as optim

# Define a simple model
class SimpleModel(nn.Module):
    def __init__(self):
        super(SimpleModel, self).__init__()
        self.fc = nn.Linear(10, 1)

    def forward(self, x):
        return self.fc(x)

# Training loop in PyTorch
model = SimpleModel()
optimizer = optim.Adam(model.parameters(), lr=0.001)
criterion = nn.MSELoss()

for epoch in range(100):
    for inputs, targets in dataloader:
```