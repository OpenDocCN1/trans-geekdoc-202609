EX 4.4. This is a nice example to illustrate the power of sampling. Imagine sampling pairs of values from uniform distributions between -0.5 and 0.5. These values would be uniformly distributed in the square shown below:

The probability that one of these points lies within the circle must be equal to the ratio of the area of the circle to the area of the square. We can obtain an empirical estimate of this value by say generating N pairs (i.e. points) and then computing the number of pairs that lie within the circle (s). Then:

```
$$\frac{s}{N} \approx \frac{\pi r^{2}}{1 \times 1} = 0.5^{2}\pi.$$
```

Re-arranging this expression will give an approximate value of π:

```
$$\pi \approx \frac{s}{0.5^{2}N}.$$
```

For example, one random sample of 100 points yields a value of:

```
$$\pi \approx 3.240.$$
```

As we would expect, this approximation will, on average, get better as we take more samples. An example after 10000 is:

```
$$\pi \approx 3.129.$$
```

# EX 4.5. Re-arrange as follows:

```
$$P(T_{\text{new}}=1|\mathbf{x}_{\text{new}},\widehat{\mathbf{w}}) = \frac{1}{1+\exp(-\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}})}$$ $$0.5 = \frac{1}{2}=\frac{1}{1+\exp(-\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}})}$$ $$2 = 1+\exp(-\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}})$$ $$1 = \exp(0)=\exp(-\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}})$$ therefore $\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}}=0.$
```

# EX 4.6. Assuming a Gaussian prior:

```
$$p(\mathbf{w}) = \mathcal{N}(\mathbf{0},\mathbf{I}_{D}),$$
```

and:

```
$$v_{n}=\exp\{\mathbf{w}^{\mathsf{T}}\mathbf{x}_{n}\}$$
```

the log posterior is proportional to:

```
$$g = -\frac{1}{2}\mathbf{w}^{\mathsf{T}}\mathbf{w} + \sum_{n}(t_{n}\log v_{n} - v_{n}).$$
```

The gradient is obtained by taking partial derivatives with respect to w:

```
$$\frac{\partial g}{\partial \mathbf{w}} = -\mathbf{w} + \sum_{n}\frac{t_{n}}{v_{n}}\frac{\partial v_{n}}{\partial \mathbf{w}} - \frac{\partial v_{n}}{\partial \mathbf{w}}.$$
```