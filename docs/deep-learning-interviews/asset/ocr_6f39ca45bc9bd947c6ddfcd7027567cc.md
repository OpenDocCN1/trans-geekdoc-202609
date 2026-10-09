# SOL-260 CH.SOL- 8.84.

A larger batch size decreases the variance of the gradient estimation of SGD. Therefore, if your training loop uses larger batches, the model will converge faster. On the other hand, smaller batch sizes increase the variance, leading to the opposite phenomena; longer convergence times.

# Momentum

# SOL-261 CH.SOL- 8.85.

Momentum introduces an extra term which comprises a moving average which is used in gradient descent update rule to exponentially decay the historical gradients Using such term has been demonstrated to accelerate the training process ( [1] ) requiring less epochs to converge.

# SOL-262 CH.SOL- 8.86.

The answers are as follows:

+   1 The derivative of the logistic activation function is extremely small for either negative or positive large inputs.

+   2 The use of the $\tanh$ function does not alleviate the problem since we can scale and translate the sigmoid function to represent the $\tanh$ function:

```
$$ \begin{align} \operatorname{tanh}(z) = 2\sigma(2z) - 1 \end{align} $$
```

While the sigmoid function is centred around 0.5, the $\tanh$ activation is centred around zero. Similar to the application of BN, centring the activations may aid the optimizer converge faster. Note: there is no relation to SGD; the issue exists when using other optimization functions as well.