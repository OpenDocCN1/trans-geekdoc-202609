follow the required distribution. Another way of view this technique is that a random point $(z_1, z_2)$ within the unit circle is mapped to the point $(z_1/\sqrt{8}, z_2/\sqrt{8})$ on the unit circle. This point is multiplied by a radius following the required distribution in Equation (3.2).

The advantage of this method is that the calculation of the sine and cosine is avoided. On the other hand, more random numbers need to be generated, since a fraction of $1-f$ are rejected as they lie outside the unit circle. Most software packages include implementations of random number generators for various underlying distributions. Nevertheless, Listings 3.1 and 3.2 are example implementations.

# 3.2 Rejection Sampling

We now consider the case where the probability density function $f$ is available and can be evaluated, the cumulative distribution function $F$ is not, and inverse sampling is not option. Let $g$ be a probability density function such that $f(x) \leq cg(x)$ for all $x$ for some finite $c > 1$. Let $G$ be the cumulative distribution function. We now assume that we have a method to draw samples from the distribution given by $G$. That is $g(x)$ is a simpler probability density function and $cg(x)$ is an envelope of $f(x)$. $f$ has two modes. The first choice is a uniform distribution over the support of $f$. That is the range of $x$ where $f(x)$ is nonzero. The other two, $g$ is normally distributed. For the second choice the mean of $g$ is at the same location as one of the modes of $f$, and for the third choice the mean lies between the two modes. We see that there are infinitely many possibilities for $g$.

> *Rejection sampling*, also known as the acceptance-rejection method, proceeds as:

+   1. Draw a random variable $x$ following the distribution given by $g$;n2. Draw a random variable $u$ from the uniform distribution over $(0,1)$;
3. If $u \leq \frac{f(x)}{cg(x)}$, accept $x$ as a sample from the distribution given by $f$. Otherwise return to 1.

```
$u \leq \frac{f(x)}{cg(x)} \quad (3.3)$
```

Intuitively, the method samples points from under $cg$ and discards those which fall in the shaded area between the curves of $cg$ and $f$. The $x$-position of the retained points are samples from the distribution governed by $f$. To keep the number of discarded points low, the area of the areas has to be as small as possible. In other words, the ratio of $cg$ and $f$ needs to be as close to one as possible. This ratio is $c$, since both