```
optimizer.zero_grad()

# Backward pass

loss.backward()

# Update weights

optimizer.step()

print('Training complete.')
```

During each epoch, we start by running a forward pass on the x_train data through the model to get the predictions y_pred. We then compute the loss using the criterion function, which takes the predicted and actual values as input. The zero_grad() function zeroes out any old gradients from the last iteration. Then, loss.backward() computes the new gradients, and optimizer.step() updates the model's parameters using these gradients.

We store the value of the loss during each epoch in a list of losses for later analysis. We also print the loss every