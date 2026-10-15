# Model Evaluation

First, we will evaluate our model to see how well it has learned from the training data. To do this, we run our model on the test data. The steps include setting the model in evaluation mode, running the forward pass, and then computing the loss:

```
# Set model to evaluation mode

model.eval()
```

```
# Forward pass on test data

with torch.no_grad():
    y_pred = model(x_test)
```

```
# Compute loss

loss = criterion(y_pred, y_test)
```