# Fitted models over epochs

![](bbox=[0.165, 0.093, 0.843, 0.296])

Figure **9.4** Linear regression in PyTorch. Left: Fitted linear model calculated in different epochs. The model fits the data better as the number of epochs increases. Right: MSE loss is decreasing with increasing epochs.

Note that we can plot the PyTorch tensors that do not require gradients, but the predicted target values da be accessed through `prediction.data` because the tensor requires gradients.

# Evaluation

The performance of the model needs to be evaluated on the test set that has been excluded from the training. Let's assume that our test set consists of feature matrix `X_test` and target `y_test`, which are both PyTorch tensors. We then predict outputs on the test set as

```
prediction_test = net(X_test)
```

and calculate the loss on the test set as

```
mse = loss_function(prediction_test, y_test).data
```

If we wish to evaluate the root-mean-squared error (for regression models only), we can take the square root of the mean squared error loss

```
rmse = torch.sqrt(mse)
```

# 9.2.6 Summary: creating and training neural networks

Here, we recap the steps we need to train a neural network in PyTorch:

+   1. Convert the training data to PyTorch tensors of type `float`.
2. Define the model architecture derived from `nn.Module:`
   a. In function `__init__` define the layers and parameters.
   b. In function `forward` define the operations of the forward pass.
3. Create an instance of the network, loss function, and optimizer.