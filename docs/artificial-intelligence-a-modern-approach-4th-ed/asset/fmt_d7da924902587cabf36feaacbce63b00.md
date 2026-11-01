
$P(x_{0}) = \\alpha\\, e^{- \\frac{1}{2}(\\frac{{(x_{0} - \\mu_{0})}^{2}}{\\sigma_{0}^{2}})}.$

(For simplicity, we use the same symbol `α` for all normalizing constants in this section.) The transition model adds a Gaussian perturbation of constant variance `σ[x]²` to the current state:

$P(x_{t + 1}\\text{|}x_{t}) = \\alpha\\, e^{- \\frac{1}{2}(\\frac{{(x_{t + 1} - x_{t})}^{2}}{\\sigma_{x}^{2}})}.$

The sensor model assumes Gaussian noise with variance `σ[z]²`:

$P(z_{t}\\text{|}x_{t}) = \\alpha\\, e^{- \\frac{1}{2}(\\frac{{(z_{t} - x_{t})}^{2}}{\\sigma_{z}^{2}})}.$

Now, given the prior `P(X0)`, the one-step predicted distribution comes from [Equation (14.17)](#Chapter14-04.xhtml#eq14-17):

$\\begin{array}{l} {P\\text{(}x_{\\text{1}}\\text{)}} \\\\ \\\\ \\end{array}\\,\\,\\,\\begin{array}{l} {= {\\int_{- \\infty}^{\\infty}{P(x_{1}\\text{|}x_{\\text{0}})P(x_{0})dx_{0} = \\alpha{\\int_{- \\infty}^{\\infty}{e^{- \\frac{1}{2}(\\frac{{(x_{1} - x_{0})}^{2}}{\\sigma_{x}^{2}})}e^{- \\frac{1}{2}(\\frac{{(x_{0} - \\mu_{0})}^{2}}{\\sigma_{0}^{2}})}dx_{0}}}}}} \\\\ {= \\alpha{\\int_{- \\infty}^{\\infty}{e^{- \\frac{1}{2}(\\frac{\\sigma_{0}^{2}{(x_{1} - x_{0})}^{2}}{\\sigma_{0}^{2}\\sigma_{x}^{2}})}dx_{0}.}}} \\\\ \\end{array}$

This integral looks rather complicated. The key to progress is to notice that the exponent is the sum of two expressions that are quadratic in x0 and hence is itself a quadratic in x0. A simple trick known as completing the square allows the rewriting of any quadratic `a x[0]² + b x[0] + c` as the sum of a squared term $a{(x_{0} - \\frac{- b}{2a})}^{2}$ and a residual term $c - \\frac{b^{2}}{4a}$ that is independent of x0. In this case, we have `a` = (`σ[0]²` + `σ[x]²`)/(`σ[0]² σ[x]²`), `b` = −2(`σ[0]² x[1]` + `σ[x]² μ[0]`)/(`σ[0]² σ[x]²`), and `c` = (`σ[0]² x[1]²` + `σ[x]² μ[0]²`)/(`σ[0]² σ[x]²`). The residual term can be taken outside the integral, giving us

<p class="sidebar">Completing the square</p>

$\\begin{matrix} {P\\text{(}x_{\\text{1}}\\text{)~} = \\ \\alpha\\,\\, e^{- \\frac{1}{2}(c - \\frac{b^{2}}{4a})}} & {\\int_{- \\infty}^{\\infty}e^{- \\frac{1}{2}(a{(x_{0} - \\frac{- b}{2a})}^{2})}} \\\\ \\end{matrix}dx_{0}$

Now the integral is just the integral of a Gaussian over its full range, which is simply 1. Thus, we are left with only the residual term from the quadratic. Plugging back in the expressions for a, b, and c and simplifying, we obtain

$P(x_{1}) = \\alpha\\,\\, e^{- \\frac{1}{2}(\\frac{{(x_{1} - \\mu_{0})}^{2}}{\\sigma_{0}^{2} + \\sigma_{x}^{2}})}.$

That is, the one-step predicted distribution is a Gaussian with the same mean μ0 and a variance equal to the sum of the original variance `σ[0]²` and the transition variance `σ[x]`.

To complete the update step, we need to condition on the observation at the first time step, namely, z1. From [Equation (14.18)](#Chapter14-04.xhtml#eq14-18), this is given by

$\\begin{array}{l} \\left. P(x_{1} \\middle| z_{1}) = \\alpha\\, P(z_{1} \\middle| x_{1})P(x_{1}) \\right. \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = \\,\\alpha e^{- \\frac{1}{2}(\\frac{{(z_{1} - x_{1})}^{2}}{\\sigma_{z}^{2}})}e^{- \\frac{1}{2}(\\frac{{(x_{1} - \\mu_{0})}^{2}}{\\sigma_{0}^{2} + \\sigma_{x}^{2}})}.} \\\\ \\end{array}$

Once again, we combine the exponents and complete the square (Exercise 14.KALM), obtaining the following expression for the posterior:

$\\left. P(x_{1} \\middle| z_{1}) = \\alpha\\, e^{- \\frac{1}{2}\\frac{{(x_{1} - \\frac{(\\sigma_{0}^{2} + \\sigma_{x}^{2})z_{1} + \\sigma_{z}^{2}\\mu_{0}}{\\sigma_{0}^{2} + \\sigma_{x}^{2} + \\sigma_{z}^{2}})}^{2}}{(\\sigma_{0}^{2} + \\sigma_{x}^{2})\\sigma_{z}^{2}/(\\sigma_{0}^{2} + \\sigma_{x}^{2} + \\sigma_{z}^{2})}}.{\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,(14.19)} \\right.$

Thus, after one update cycle, we have a new Gaussian distribution for the state variable.

From the Gaussian formula in [Equation (14.19)](#Chapter14-04.xhtml#eq14-19), we see that the new mean and standard deviation can be calculated from the old mean and standard deviation as follows:

$\\begin{matrix} {\\mu_{t + 1} = \\frac{(\\sigma_{t}^{2} + \\sigma_{x}^{2})z_{t + 1} + \\sigma_{z}^{2}\\mu_{t}}{\\sigma_{t}^{2} + \\sigma_{x}^{2} + \\sigma_{z}^{2}}} & \\text{and} & {\\sigma_{t + 1}^{2} = \\frac{(\\sigma_{t}^{2} + \\sigma_{x}^{2})\\sigma_{z}^{2}}{\\sigma_{t}^{2} + \\sigma_{x}^{2} + \\sigma_{z}^{2}}} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,(14.20)} \\\\ \\end{matrix}.$

[Figure 14.10](#Chapter14-04.xhtml#fig14-10) shows one update cycle of the Kalman filter in the one-dimensional case for particular values of the transition and sensor models.

Description

The horizontal axis is labeled x position and ranges from negative 10 to 10 in increments of 5 units. The vertical axis is labeled P (x) and ranges from 0 to 0.45 in increments of 0.05 units. The graph consists of three curves. A dashed curve labeled P (x subscript 1) starts at (negative 10, 0), rises toward the upper right to form a peak at (0, 0.15), then drops to end at (7, 0). A solid curve labeled P (x subscript 0) starts at (negative 10, 0), rises toward the upper right to form a peak at (negative 2, 0.25), then drops and ends at (5, 0). A dashed curve labeled P (x subscript 1 vertical bar Z subscript 1 equals 2.5) starts at (negative 3, 0), rises to form a peak at (2.5, 0.43), then drops and ends at (6, 0). The point (2.5, 0) is labeled Z subscript 1.

×![](images/Fig-200.jpg)

Figure 14.10 Stages in the Kalman filter update cycle for a random walk with a prior given by μ[0] = 0.0 and σ0 \= 1.5, transition noise given by σx = 2.0, sensor noise given by σz = 1.0, and a first observation z1 = 2.5 (marked on the x\-axis). Notice how the prediction P(x1) is flattened out, relative to P(x0), by the transition noise. Notice also that the mean of the posterior distribution P(x1 | z1) is slightly to the left of the observation z1 because the mean is a weighted average of the prediction and the observation.

[Equation (14.20)](#Chapter14-04.xhtml#eq14-20) plays exactly the same role as the general filtering [equation (14.5)](#Chapter14-02.xhtml#eq14-5) or the HMM filtering [equation (14.12)](#Chapter14-03.xhtml#eq14-12). Because of the special nature of Gaussian distributions, however, the equations have some interesting additional properties.

First, we can interpret the calculation for the new mean μt+1 as a weighted mean of the new observation zt+1 and the old mean μt. If the observation is unreliable, then `σ[z]²` is large and we pay more attention to the old mean; if the old mean is unreliable (`σ[t]²` is large) or the process is highly unpredictable (`σ[x]²` is large), then we pay more attention to the observation.

Second, notice that the update for the variance `σ[t + 1]²` is independent of the observation. We can therefore compute in advance what the sequence of variance values will be. Third, the sequence of variance values converges quickly to a fixed value that depends only on `σ[x]²` and `σ[z]²`, thereby substantially simplifying the subsequent calculations. (See Exercise 14.VARI.)

## 14.4.3 The general case

The preceding derivation illustrates the key property of Gaussian distributions that allows Kalman filtering to work: the fact that the exponent is a quadratic form. This is true not just for the univariate case; the full multivariate Gaussian distribution has the form

$N(\\mathbf{x};\\mu,\\sum) = \\alpha e^{- \\frac{1}{2}({(\\mathbf{x} - \\mu)}^{\\text{T}}\\sum^{- 1}(\\mathbf{x} - \\mu))}.$

Multiplying out the terms in the exponent, we see that the exponent is also a quadratic function of the values xi in x. Thus, filtering preserves the Gaussian nature of the state distribution.
