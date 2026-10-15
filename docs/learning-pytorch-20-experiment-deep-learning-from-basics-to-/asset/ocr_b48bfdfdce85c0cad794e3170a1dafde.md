# # Example data

```
input = torch.randn(100, 10)
```

```
target = torch.randn(100, 5)
```

# # Define the batch size

```
batch_size = 10
```

# # Training loop

```
for i in range(100):
```

```
for j in range(0, input.shape[0], batch_size):
```

# # Compute the predicted output

```
output = model(input[j:j+batch_size])
```

# # Compute the loss