```
# Define a simple linear model

model = torch.nn.Linear(10, 5)

# Define the loss function

loss_fn = torch.nn.MSELoss()

# Define the optimizer - Adam

optimizer = torch.optim.Adam(model.parameters(),
lr=0.001)

# Example data

input = torch.randn(100, 10)

target = torch.randn(100, 5)

# Define the batch size

batch_size = 10
```