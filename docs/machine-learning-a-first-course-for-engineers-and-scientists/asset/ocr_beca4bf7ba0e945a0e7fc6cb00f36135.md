# 5.5 Optimization with large datasets

![](bbox=[0.141, 0.093, 0.858, 0.219])

Fig. 5.13 It is clear that the shape of the decision boundaries becomes more complex as t increases, and the number of iterations t can be almost identical to, some extent, understood as a way to control the model flexibility. This example is indeed somewhat exaggerated, but the same effect can be seen in particular when training deep neural networks (Chapter 6).

# 5.5 Optimization with large datasets

In machine learning the training data may have n = millions (or more) of data points. Computing, for example, of the cost function

```
$$\nabla_{\theta}J(\theta) = \frac{1}{n} \sum_{i=1}^{n} \nabla_{\theta}L(x_i, y_i, \theta)$ (5.37)
```

thus involves summing a million of terms. Besides taking lot of time to use, it can also be an issue to keep all data points in the memory at the same time. However, with many data points many of them are relatively simple, and in practice we might not need to consider all of them looking only a subset of them might give sufficient information. This is a general idea subsampling, and we will have a closer look at how subsampling can be combined with gradient descent method stochastic gradient descent. It is, however, possible to combine the subsampling idea with other methods.

# Stochastic gradient descent

With n being big, we can compute the gradient only for the first half of the dataset $\nabla_{\theta}J(\theta) \approx \sum_{i=1}^{n/2} \nabla_{\theta}L(x_i, y_i, \theta)$ to be almost identical to the gradient based on the second half of the dataset $\nabla_{\theta}J(\theta) \approx \sum_{i=n/2}^{n} \nabla_{\theta}L(x_i, y_i, \theta)$. Consequently, it would be a waste of time to compute the gradient based on the whole training dataset at each iteration of gradient descent. Instead, we could compute the gradient based on the first half of the training dataset, update the parameters according to the gradient descent method Algorithm 5.1, and then compute the gradient for the second half of the training.

```
$$\theta^{(t+1)} = \theta^{(t)} - \frac{\gamma}{n/2} \sum_{i=1}^{n/2} \nabla_{\theta}L(x_i, y_i, \theta^{(t)})$ (5.38a)
```

```
$$\theta^{(t+2)} = \theta^{(t+1)} - \frac{\gamma}{n/2} \sum_{i=n/2}^{n} \nabla_{\theta}L(x_i, y_i, \theta^{(t+1)})$ (5.38b)
```

In other words, we use only a sample of the training data when we compute the gradient. In this way, we still use all of the training data, but it is split into two consecutive parameter updates. Hence, (5.38) requires half the computational time compared to two parameter updates of normal gradient descent. This computational saving illustrates the benefits of subsampling idea.