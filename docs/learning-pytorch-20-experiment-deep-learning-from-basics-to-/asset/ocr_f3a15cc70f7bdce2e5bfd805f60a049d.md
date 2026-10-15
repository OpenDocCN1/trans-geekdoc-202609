calculating gradients, calling optimizer.step() updates the parameters.

For example:

```
# Define the model

model = torch.nn.Linear(10, 5)

# Define the optimizer

optimizer = torch.optim.Adam(model.parameters(), lr=0.001)

# Training step

for input, target in dataset:
    optimizer.zero_grad()
    output = model(input)
    loss = loss_fn(output, target)
```