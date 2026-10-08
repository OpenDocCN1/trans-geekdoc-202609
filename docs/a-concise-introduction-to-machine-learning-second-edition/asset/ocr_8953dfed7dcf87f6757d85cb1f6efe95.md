![](bbox=[0.297, 0.183, 0.715, 0.447])

3.2: The Weibull cumulative distribution function for various choices of $k$ and $\lambda$.

function

$F(x) = \exp\left(-\int_{0}^{x} \left(\frac{t}{\lambda}\right)^{k-1} dt\right)\n= \exp\left(-\left(\frac{x}{\lambda}\right)^{k}\right) = 1 - \exp\left(-\left(\frac{x}{\lambda}\right)^{k}\right).$.

Setting this equal to $y$ and solving for $x$ leads to

$x = \lambda [-\log(1 - y)]^{1/k}$.

which is a random variable drawn from the Weibull distribution, if $y$ is drawn from the uniform distribution over (0,1). Now, $z = 1 - y$ is equally drawn from the uniform distribution over (0,1). So the transformation is often stated as

$x = \lambda [-\log z]^{1/k}$.

This technique can be used as the cumulative distribution function is known and can be inverted. This is not always the case, the normal distribution being a prime example. In the following, we derive the *Box-Muller transform* to generate a pair of random variables following the standard normal distribution from a pair of uniformly distributed random variables.