
CDFs are monotonically non-decreasing functions.

The cdf of the Gaussian is defined by

$$\Phi(y; \mu, \sigma^2) \triangleq \int_{-\infty}^{y} \mathcal{N}(z|\mu, \sigma^2)\, dz = \frac{1}{2}\left[1 + \operatorname{erf}\left(\frac{z}{\sqrt{2}}\right)\right] \tag{3.42}$$

where \(z = (y - \mu)/\sigma\) and \(\operatorname{erf}(u)\) is the **error function**, defined as

$$\operatorname{erf}(u) \triangleq \frac{2}{\sqrt{\pi}} \int_0^u e^{-t^2}\, dt \tag{3.43}$$

This latter function is built into most software packages. See Fig. 3.6a for a plot.

The parameter \(\mu\) encodes the mean of the distribution, which is the same as the mode, since the distribution is unimodal. The parameter \(\sigma^2\) encodes the variance. (Sometimes we talk about the **precision** of a Gaussian, which is the inverse variance, denoted \(\lambda = 1/\sigma^2\).) When \(\mu = 0\) and \(\sigma = 1\), the Gaussian is called the **standard normal** distribution.

If \(P\) is the cdf of \(Y\), then \(P^{-1}(q)\) is the value \(y_q\) such that \(P(Y \le y_q) = q\); this is called the \(q\)-th **quantile** of \(P\). The value \(P^{-1}(0.5)\) is the **median** of the distribution, with half of the probability mass on the left, and half on the right. The values \(P^{-1}(0.25)\) and \(P^{-1}(0.75)\) are the lower and upper **quartiles**.

For example, let \(\Phi\) be the cdf of the Gaussian distribution \(N(0,1)\), and \(\Phi^{-1}\) be the inverse cdf (also known as the **probit function**). Then points to the left of \(\Phi^{-1}(\alpha/2)\) contain \(\alpha/2\) of the probability mass, as illustrated in Fig. 3.6b. By symmetry, points to the right of \(\Phi^{-1}(1 - \alpha/2)\) also contain \(\alpha/2\) of the mass. Hence the central interval \((\Phi^{-1}(\alpha/2), \Phi^{-1}(1 - \alpha/2))\) contains \(1 - \alpha\) of the mass. If we set \(\alpha = 0.05\), the central 95% interval is covered by the range

$$(\Phi^{-1}(0.025), \Phi^{-1}(0.975)) = (-1.96, 1.96) \tag{3.44}$$

If the distribution is \(N(\mu, \sigma^2)\), then the 95% interval becomes \((\mu - 1.96\sigma, \mu + 1.96\sigma)\). This is often approximated by writing \(\mu \pm 2\sigma\).

## 3.3.2 Probability density function

We define the **probability density function** or **pdf** as the derivative of the cdf:

$$p(y) \triangleq \frac{d}{dy} P(y) \tag{3.45}$$

The pdf of the Gaussian is given by

$$\mathcal{N}(y|\mu, \sigma^2) \triangleq \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(y-\mu)^2}{2\sigma^2}} \tag{3.46}$$

where \(\sqrt{2\pi\sigma^2}\) is the normalization constant needed to ensure the density integrates to 1 (see Exercise 3.2). See Fig. 3.6b for a plot.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_84_0.png)

As the size of the interval gets smaller, we can write

$$\Pr(y \le Y \le y+dy) \approx p(y)\,dy \tag{3.48}$$

Intuitively, this says the probability of \(Y\) being in a small interval around \(y\) is the density at \(y\) times the width of the interval. One important consequence of the above result is that the pdf at a point can be larger than 1. For example, \(N(0|0, 0.01) = 3.99\).

We can use the pdf to compute the mean, or expected value, of the distribution:

$$E[Y] \triangleq \int y\, p(y)\, dy \tag{3.49}$$

For a Gaussian, we have the familiar result that \(E[N(\mu,\sigma^2)] = \mu\). (Note, however, that for some distributions, this integral is not finite, so the mean is not defined.)

We can also use the pdf to compute the variance of a distribution. This is a measure of the “spread”, and is often denoted by \(\sigma^2\). The variance is defined as follows:

$$V[Y] \triangleq E[(Y - \mu)^2] = \int (y - \mu)^2 p(y)\, dy \tag{3.50}$$

$$= \int y^2 p(y)\, dy + \mu^2 \int p(y)\, dy - 2\mu \int y p(y)\, dy = E[Y^2] - \mu^2 \tag{3.51}$$

from which we derive the useful result

$$E[Y^2] = \sigma^2 + \mu^2 \tag{3.52}$$

The standard deviation is defined as

$$\operatorname{std}[Y] \triangleq \sqrt{V[Y]} = \sigma \tag{3.53}$$

(The standard deviation can be more interpretable than the variance since it has the same units as \(Y\) itself.) For a Gaussian, we have the familiar result that \(\operatorname{std}[N(\mu,\sigma^2)] = \sigma\).

## 3.3.3 Regression

So far we have been considering the unconditional Gaussian distribution. In some cases, it is helpful to make the parameters of the Gaussian be functions of some input variables, i.e., we want to create a conditional density model of the form

$$p(y \mid \mathbf{x}; \boldsymbol{\theta}) = \mathcal{N}(y \mid f_\mu(\mathbf{x}; \boldsymbol{\theta}), f_\sigma(\mathbf{x}; \boldsymbol{\theta})^2) \tag{3.54}$$

where \(f_\mu(\mathbf{x}; \boldsymbol{\theta}) \in \mathbb{R}\) predicts the mean, and \(f_\sigma(\mathbf{x}; \boldsymbol{\theta}) \in \mathbb{R}_+\) predicts the standard deviation.

It is common to assume that the variance is fixed, and is independent of the input. This is called **homoskedastic regression**. Furthermore it is common to assume the mean is a linear function of the input. The resulting model is called **linear regression**:

$$p(y \mid \mathbf{x}; \boldsymbol{\theta}) = \mathcal{N}(y \mid \mathbf{w}^\top \mathbf{x} + b, \sigma^2) \tag{3.55}$$

where \(\boldsymbol{\theta} = (\mathbf{w}, b, \sigma^2)\). See Fig. 3.7(a) for an illustration of this model in 1D, and Sec. 11.2 for more details on this model.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_85_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_85_1.png)

*Figure 3.7: Linear regression using Gaussian output with mean \(\mu(x)=b+wx\) and (a) fixed variance \(\sigma^2\) (homoskedastic) or (b) input-dependent variance \(\sigma(x)^2\) (heteroskedastic). Generated by linreg_1d_hetero_tfp.py.*

However, we can also make the variance depend on the input; this is called **heteroskedastic regression**. In the linear regression setting, we have

$$p(y \mid \mathbf{x}; \boldsymbol{\theta}) = \mathcal{N}(y \mid \mathbf{w}_\mu^\top \mathbf{x} + b, \sigma_+(\mathbf{w}_\sigma^\top \mathbf{x})) \tag{3.56}$$

where \(\boldsymbol{\theta} = (\mathbf{w}_\mu, \mathbf{w}_\sigma)\) are the two sets of regression weights, and

$$\sigma_+(a) = \log(1 + e^a) \tag{3.57}$$

is the **softplus** function, that maps from \(\mathbb{R}\) to \(\mathbb{R}_+\), to ensure the predicted standard deviation is non-negative. See Fig. 3.7(b) for an illustration of this model in 1D.

Note that Fig. 3.7 plots the 95% predictive interval, \([\mu(x) - 2\sigma(x), \mu(x) + 2\sigma(x)]\). This is the uncertainty in the predicted observation \(y\) given \(\mathbf{x}\), and captures the variability in the blue dots. By contrast, the uncertainty in the underlying (noise-free) function is represented by \(\sqrt{\mathbb{V}[f_\mu(\mathbf{x}; \boldsymbol{\theta})]}\), which does not involve the \(\sigma\) term; now the uncertainty is over the parameters \(\boldsymbol{\theta}\), rather than the output \(y\). See Sec. 11.6 for details on how to model parameter uncertainty.

## 3.3.4 Why is the Gaussian distribution so widely used?

The Gaussian distribution is the most widely used distribution in statistics and machine learning. There are several reasons for this. First, it has two parameters which are easy to interpret, and which capture some of the most basic properties of a distribution, namely its mean and variance. Second, the central limit theorem (Sec. D.5.6) tells us that sums of independent random variables have an approximately Gaussian distribution, making it a good choice for modeling residual errors or “noise”. Third, the Gaussian distribution makes the least number of assumptions (has maximum entropy), subject to the constraint of having a specified mean and variance. This makes it a good default choice in many cases. Finally, it has a simple mathematical form, which results in easy to implement, but often highly effective, methods, as we will see in Sec. 3.5.

From a historical perspective, it’s worth remarking that the term “Gaussian distribution” is a bit misleading, since, as Jaynes [Jay03, p241] notes: “The fundamental nature of this distribution and its main properties were noted by Laplace when Gauss was six years old; and the distribution itself had been found by de Moivre before Laplace was born”. However, Gauss popularized the use of the distribution in the 1800s, and the term “Gaussian” is now widely used in science and engineering.

The name “normal distribution” seems to have arisen in connection with the normal equations in linear regression (see Sec. 11.2.2.2). However, we prefer to avoid the term “normal”, since it suggests other distributions are “abnormal”, whereas, as Jaynes [Jay03] points out, it is the Gaussian that is abnormal in the sense that it has many special properties that are untypical of general distributions.

## 3.3.5 Half-normal

For some problems, we want a distribution over non-negative reals. One way to create such a distribution is to define \(Y = |X|\), where \(X \sim N(0, \sigma^2)\). The induced distribution for \(Y\) is called the half-normal distribution, which has the pdf

$$\mathcal{N}_+(y|\sigma) \triangleq 2\mathcal{N}(y|0, \sigma^2) = \frac{\sqrt{2}}{\sigma\sqrt{\pi}} \exp\left(-\frac{y^2}{2\sigma^2}\right), \quad y \ge 0 \tag{3.58}$$

This can be thought of as the \(N(0, \sigma^2)\) distribution “folded” onto itself. This distribution has the following moments:

$$\text{mean} = \frac{\sigma\sqrt{2}}{\sqrt{\pi}}, \quad \text{var} = \sigma^2\left(1 - \frac{2}{\pi}\right) \tag{3.59}$$

## 3.4 Some other common univariate distributions

In this section, we briefly introduce some other univariate distributions that we will use in this book.

### 3.4.1 Student t distribution

The Gaussian distribution is quite sensitive to outliers. A robust alternative to the Gaussian is the Student t-distribution, which we shall call the Student distribution for short.² Its pdf is
