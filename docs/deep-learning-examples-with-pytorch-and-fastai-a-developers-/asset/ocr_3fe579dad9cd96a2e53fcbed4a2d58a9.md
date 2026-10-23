![](bbox=[0.13, 0.08, 0.65, 0.37])

So the model doesn’t fit so well, of course because we initialized our weights with random parameter-values. We need to iterate and adapt our weights (train our model).

# 3.1 Model Optimizer

During optimization, our goal is to minimize the error (calculated by the loss function mse). Our optimizer starts with some random parameters, calculates the gradient and makes some adjustment to the parameters. Next, we repeat this step until our error is smaller than a value epsilon or until a fixed amount of epochs. (https://en.wikipedia.org/wiki/Stochastic_gradient_descent)

First lets make this parameter:
a = nn.Parameter(a); a
Parameter containing: tensor([0.5000, 0.7500], requires_grad=True)

Now we have to implement our update function which checks if the current value of our parameter a improves the training results. If so, move in this direction.

```
def update():
y_hat = x@a
loss = mse(y, y_hat)
```