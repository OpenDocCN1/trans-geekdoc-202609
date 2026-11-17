```
super(CNNModel, self).__init__()
self.conv1 = nn.Conv2d(1, 32, kernel_size=3)
self.conv2 = nn.Conv2d(32, 64, kernel_size=3)
self.fc1 = nn.Linear(9216, 128)
self.fc2 = nn.Linear(128, 10)

def forward(self, x):
    x = torch.relu(self.conv1(x))
    x = torch.relu(self.conv2(x))
    x = torch.flatten(x, 1)
    x = torch.relu(self.fc1(x))
    return self.fc2(x)
```

```
# Initialize model, optimizer, and loss function
model = CNNModel()
optimizer = optim.Adam(model.parameters(), lr=0.001)
criterion = nn.CrossEntropyLoss()

# Training loop
for epoch in range(5):
    for inputs, targets in train_dataloader:
        optimizer.zero_grad()
        outputs = model(inputs)
        loss = criterion(outputs, targets)
        loss.backward()
        optimizer.step()
```

In this example, the model logic, forward pass, and training loop are tightly coupled, requiring manual management of each step. Now, let’s convert this model into PyTorch Lightning to simplify and clean up the code.

# **Converting to PyTorch Lightning:**

```
import pytorch_lightning as pl
import torch
import torch.nn as nn
import torch.optim as optim
from torchvision import datasets, transforms
```