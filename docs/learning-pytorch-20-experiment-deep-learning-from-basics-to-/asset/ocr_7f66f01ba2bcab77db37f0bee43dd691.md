Adding momentum to our SGD optimizer in PyTorch is as simple as adding an extra argument when we instantiate the optimizer.

We will see how this looks in practice:

```
# Define a simple linear model
model = torch.nn.Linear(10, 5)

# Define the loss function
loss_fn = torch.nn.MSELoss()

# Define the optimizer - SGD with momentum
optimizer = torch.optim.SGD(model.parameters(),
lr=0.01, momentum=0.9)

# Example data
input = torch.randn(100, 10)

target = torch.randn(100, 5)
```