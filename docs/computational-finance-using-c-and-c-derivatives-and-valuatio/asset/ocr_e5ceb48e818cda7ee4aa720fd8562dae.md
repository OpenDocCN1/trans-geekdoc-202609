# D.4.3 The Distribution for Shape Parameter, a

If the distribution has variance $h_i$, then from Appendix D.4.1

$$\lambda = \left( \frac{2^{-2/a} \Gamma(1/a) h_i}{\Gamma(3/a)} \right)^{1/2}$

Now for $0 < x < 1$ we have $\Gamma(1+x) = 1+a_1x+a_2x^2+a_3x^3$, where the coefficients are $|a_i| < 1$, Abramowitz and Steegun (1968). Since $x\Gamma(x) = \Gamma(1+x)$, to third order in $x$, we have:

to third order in $x$, we have $x\Gamma(x) = 1+a_1x+a_2x^2+a_3x^3$.

This gives $\Gamma(x) = \frac{1}{x} + a_1 + a_2x + a_3x^2$ and $\Gamma(x) \approx \frac{1}{x} - \frac{1}{x}a \to 0$.

So as $a \to \infty$, we have the following:

$2^{(1+1/a)} \approx 2, \quad 2^{-2/a} \approx 1, \quad \frac{1}{\Gamma(1/a)} \approx \frac{1}{a},$

$\frac{\Gamma(1/a)}{\Gamma(3/a)} \approx \frac{3a}{a} \approx 3, \text{ and } \frac{\Gamma(5/a)}{\Gamma(3/a)} \approx \frac{3a}{5a} \approx \frac{3}{5}$.

The kurtosis is then

$$\kappa = \frac{\Gamma(5/a) \Gamma(1/a)}{\Gamma(3/a) \Gamma(3/a)} \approx \frac{9}{5}$.$.

Also as $a \to \infty \lambda \approx (3h_i)^{1/2}$ and for the range $-(3h_i)^{1/2} < \epsilon_i < (3h_i)^{1/2}$, we have

$$\left[ \frac{\epsilon_i^2}{\lambda} \right] \approx \left[ \frac{\epsilon_i}{(3h_i)^{1/2}} \right]^2 \approx 0, \text{ and therefore } \exp \left( -\frac{1}{2} \frac{\epsilon_i^2}{\lambda} \right) \approx 1.$.

Substituting the above results into equation (D.4.1), the probability density reduces to

$$\f(\epsilon_i) \approx \frac{1}{2(3h_i)^{1/2}}$.

which is a uniform distribution $\mathcal{U}(-(3h_i)^{1/2}, (3h_i)^{1/2})$, with lower limit $-(3h_i)^{1/2}$ and upper limit $-(3h_i)^{1/2}$.