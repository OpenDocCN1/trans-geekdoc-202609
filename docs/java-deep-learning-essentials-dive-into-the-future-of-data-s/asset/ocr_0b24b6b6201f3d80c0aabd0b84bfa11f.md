```
dtype=theano.config.floatX
),
name='b',
borrow=True
)
```

The activation function of multi-class logistic regression is the softmax function and we can just write and define the output as follows:

```
self.p_y_given_x = T.nnet.softmax(T.dot(input, self.W) + self.b)
```

We can write the predicted values as:

```
self.y_pred = T.argmax(self.p_y_given_x, axis=1)
```

In terms of training, since the equations of the backpropagation algorithm are computed from the loss function and its gradient, what we need to do is just define the function to be minimized, that is, the negative log likelihood function:

```
def negative_log_likelihood(self, y):
    return -T.mean(T.log(self.p_y_given_x)[T.arange(y.shape[0]), y])
```

Here, the mean values, not the sum, are computed to evaluate across the mini-batch.

With these preceding values and definitions, we can implement MLP. Here again, what we need to do is define the equations and symbols of MLP. The following is an extraction of the code:

```
class MLP(object):
    def __init__(self, rng, input, n_in, n_hidden, n_out):
        # self.hiddenLayer = HiddenLayer(...)
        # self.logRegressionLayer = LogisticRegression(...)
        # L1 norm
        self.L1 = (
            abs(self.hiddenLayer.W).sum()
            + abs(self.logRegressionLayer.W).sum()
        )
        # square of L2 norm
        self.L2_sqr = (
            (self.hiddenLayer.W ** 2).sum()
            + (self.logRegressionLayer.W ** 2).sum()
        )
        # negative log likelihood of MLP
```