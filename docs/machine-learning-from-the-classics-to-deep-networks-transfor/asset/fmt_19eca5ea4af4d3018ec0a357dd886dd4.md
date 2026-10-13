
In [72], the connection between Gaussian processes and Kalman filtering is exploited and the solution is obtained via the involvement of stochastic differential equations, which makes the dependence of the complexity on time to be linear.

Finally, an extended review of related techniques is provided in [44].

### 13.12.3 Classification

In contrast to the regression task, under the Gaussian assumptions for the noise and the involved random process, the classification task gets more involved. In Section [13.7](#Chp013_635-716_B9780443292385000196.xhtml#s0060), the logistic regression in its parametric form, given in Eq. [(13.68)](#Chp013_635-716_B9780443292385000196.xhtml#deq99), was employed. In the context of the Gaussian processes, the model becomes

$$P(\omega_{1}|\mathbf{x}) = \frac{1}{1 + \exp\left( - f(\mathbf{x}) \right)} = \sigma\left( f(\mathbf{x}) \right),$$

where now `f(x)` will be treated in terms of a Gaussian random process, associated with a kernel function `κ(⋅, ⋅)`. Given a set of training samples, `(y[n], x[n])`, `n = 1, 2, …, N`, `y[n] ∈ {0, 1}`, and following the same arguments as in Section [13.7](#Chp013_635-716_B9780443292385000196.xhtml#s0060), we can now write

$$P(\mathbf{y}|\mathbf{f}) = \prod\limits_{n = 1}^{N}\sigma{(f_{n})}^{y_{n}}{(1 - \sigma(f_{n}))}^{1 - y_{n}},$$

where `f[n] := f(x[n])`, and

$$p(\mathbf{f}) = \mathcal{N}(\mathbf{f}|0, \mathcal{K}).$$
