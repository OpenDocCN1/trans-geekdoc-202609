```
# Zero the gradients
optimizer.zero_grad()
# Compute the gradients
loss.backward()
# Update the parameters
optimizer.step()
```

In the above demonstration, the loop over j represents looping over the mini-batches. For simplicity, we've used a batch size of 1. In practice, you would likely use a larger batch size, such as 32 or 64.

# Mini-batch Gradient Descent

Mini-Batch Gradient Descent (MBGD), as the name suggests, is a trade-off between Batch Gradient Descent and Stochastic Gradient Descent. In MBGD, the dataset is divided into small mini-batches of a specific size, and