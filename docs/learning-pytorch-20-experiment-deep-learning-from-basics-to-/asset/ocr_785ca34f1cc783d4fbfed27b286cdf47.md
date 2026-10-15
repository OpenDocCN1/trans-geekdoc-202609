The following is a simple example, assuming we have some new data in x_new:

```
# Forward pass on new data

with torch.no_grad():
    y_new = model(x_new)

# Print predictions

print(y_new)
```

Do not forget that this new data should be processed in the same way as your training and test data, i.e., it should be normalized in the same way and it should be a PyTorch tensor.

With this, you have a working pipeline for training, evaluating, tuning, and making predictions with a linear regression model in PyTorch!