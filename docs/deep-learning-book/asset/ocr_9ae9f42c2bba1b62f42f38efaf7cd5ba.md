![](bbox=[0.32, 0.09, 0.65, 0.28])

Figure 3.2: Samples from a Gaussian mixture model. In this example, there are three components. From left to right, the first component has an isotropic covariance matrix, meaning it has the same amount of variance in each direction. The second has a diagonal covariance matrix, meaning it can control the variance separately along each axis-aligned direction. This example has more variance along the x₂ axis than along the x₁ axis. The third component has a full-rank covariance matrix, enabling it to control the variance separately along an arbitrary basis of directions.

The logistic sigmoid is commonly used to produce the φ parameter of a Bernoulli distribution because its range is (0,1), which lies within the valid range of values for the φ parameter. See figure 3.3 for a graph of the sigmoid function. The sigmoid function saturates when its argument is very positive or very negative, meaning that the function becomes very flat and insensitive to small changes in its input.

Another commonly encountered function is the softplus function (Dugas et al., 2001):

```
ζ(x) = log(1 + exp(x)). (3.31)
```

The softplus function can be useful for producing the β or σ parameter of a normal distribution because its range is (0, ∞). It also arises commonly when manipulating expressions involving sigmoids. The name of the softplus function comes from the fact that it is a smoothed, or “softened,” version of

```
x⁺ = max(0, x). (3.32)
```

See figure 3.4 for a graph of the softplus function.

The following properties are all useful enough that you may wish to memorize