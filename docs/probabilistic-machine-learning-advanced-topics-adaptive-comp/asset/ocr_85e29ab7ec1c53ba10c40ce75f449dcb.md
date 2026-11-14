and hence are close to the orientation of the maximum likelihood decision boundary. The points
are ordered by increasing weight norm (3.16, 4.47, 5.83, and 7.62). The unconstrained MLE has
\(||\boldsymbol{w}||=\infty\), so is infinitely far to the top right.
To ensure a unique solution, we use a (spherical) Gaussian prior centered at the origin, \(\mathcal{N}(\boldsymbol{w}|\boldsymbol{0},\sigma^2\boldsymbol{I}\)).
The value of \(\sigma^2\) controls the strength of the prior. If we set \(\sigma^2=\infty\), we force the MAP estimate
to be \(\boldsymbol{w}=\boldsymbol{0}\); this will result in maximally uncertain predictions, since all points \(\boldsymbol{x}\) will produce a
predictive distribution of the form \(p(y=1|\boldsymbol{x})=0.5\). If we set \(\sigma^2=0\), the MAP estimate becomes
the MLE, resulting in minimally uncertain predictions. (In particular, all positively labeled points
will have \(p(y=1|\boldsymbol{x})=1.0\), and all negatively labeled points will have \(p(y=1|\boldsymbol{x})=0.0\), since the
data is separable.) As a compromise (to make a nice illustration), we pick the value \(\sigma^2=100\).
Multiplying this prior by the likelihood results in the unnormalized posterior shown in Figure 15.6(c).
The MAP estimate is shown by the blue dot. The Laplace approximation to this posterior is shown
in Figure 15.6(d). We see that it gets the mode correct (by construction), but the shape of the
posterior is somewhat distorted. (The southwest-northeast orientation captures uncertainty about the
magnitude of \(\boldsymbol{w}\), and the southeast-northwest orientation captures uncertainty about the orientation
of the decision boundary.)

# ## 15.3.6 Approximating the posterior predictive distribution

Next we need to convert the posterior over the parameters into a posterior over predictions, as follows:

```
\(p(y|\boldsymbol{x},\mathcal{D})=\int p(y|\boldsymbol{x},\boldsymbol{w})p(\boldsymbol{w}|\mathcal{D})d\boldsymbol{w}\) (15.146)
```

The simplest way to evaluate this integral is to use a Monte Carlo approximation. For example, in
the case of binary logistic regression, we have

```
\(p(y=1|\boldsymbol{x},\mathcal{D})\approx\frac{1}{S}\sum_{s=1}^S \sigma(\boldsymbol{w}_s^\top\boldsymbol{x})\) (15.147)
```

where \(\boldsymbol{w}_s\sim p(\boldsymbol{w}|\mathcal{D})\) are posterior samples.

However, we can also use deterministic approximations to the integral, which are often faster. Let
\(\boldsymbol{f}_*=f(\boldsymbol{x}_*,\boldsymbol{w})\) be the predicted logits, before the sigmoid/softmax layer, given test point \(\boldsymbol{x}_*\). If the
posterior over the parameters is Gaussian, \(p(\boldsymbol{w}|\mathcal{D})=\mathcal{N}(\boldsymbol{\mu},\boldsymbol{\Sigma})\), then the predictive distribution over
logits is also Gaussian:

```
\(p(\boldsymbol{f}_*|\boldsymbol{x}_*,\mathcal{D})=\int\delta(\boldsymbol{f}_*-f(\boldsymbol{x}_*,\boldsymbol{w}))\mathcal{N}(\boldsymbol{w}|\mathcal{D})d\boldsymbol{w}=\mathcal{N}(\boldsymbol{f}_*|\boldsymbol{\mu}^\top\boldsymbol{x}_*,\boldsymbol{x}_*^\top\boldsymbol{\Sigma}\boldsymbol{x}_*)\unknown\mathcal{N}(\boldsymbol{f}_*|\boldsymbol{\mu}_*,\boldsymbol{\Sigma}_*)\) (15.148)
```

In the case of binary logistic regression, we can approximate the sigmoid with the probit function \(\Phi\)
(see Section 15.4), which allows us to solve the integral analytically:

```
\(p(y_*|\boldsymbol{x}_*)\approx\int\Phi(f_*)\mathcal{N}(f_*|\mu_*,\sigma_*^2)df_*=\sigma\left(\frac{\mu_*}{\sqrt{1+\frac{\pi}{8}\sigma_*^2}}\right)\) (15.149)
```