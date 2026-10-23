
If we define $\eta_K = 0$, we can rewrite this as follows:

$\mu_k = \frac{e^{\eta_k}}{\sum_{j=1}^{K} e^{\eta_j}}$ (12.24)

for $k = 1 : K$. Hence $\boldsymbol{\mu} = \mathcal{S}(\boldsymbol{\eta})$, where $\mathcal{S}$ is the softmax or multinomial logit function in Eq. (3.28). From this, we find

$\mu_K = 1 - \frac{\sum_{k=1}^{K-1} e^{\eta_k}}{1 + \sum_{k=1}^{K-1} e^{\eta_k}} = \frac{1}{1 + \sum_{k=1}^{K-1} e^{\eta_k}}$ (12.25)

and hence

$A(\boldsymbol{\eta}) = -\log(\mu_K) = \log\left(\sum_{k=1}^{K} e^{\eta_k}\right)$ (12.26)

### 12.2.2.3 Univariate Gaussian

The univariate Gaussian is usually written as follows:

$\mathcal{N}(y|\mu,\sigma^2) = \frac{1}{(2\pi\sigma^2)^{\frac{1}{2}}} \exp\left[-\frac{1}{2\sigma^2}(y-\mu)^2\right]$ (12.27)

$= \frac{1}{(2\pi)^{\frac{1}{2}}} \exp\left[\frac{\mu}{\sigma^2}y - \frac{1}{2\sigma^2}y^2 - \frac{1}{2\sigma^2}\mu^2 - \log\sigma\right]$ (12.28)

We can put this in exponential family form by defining

$\boldsymbol{\eta} = \begin{pmatrix} \mu/\sigma^2 \\ -\frac{1}{2\sigma^2} \end{pmatrix}$ (12.29)

$\mathbf{t}(y) = \begin{pmatrix} y \\ y^2 \end{pmatrix}$ (12.30)

$A(\boldsymbol{\eta}) = \frac{\mu^2}{2\sigma^2} + \log\sigma = \frac{-\eta_1^2}{4\eta_2} - \frac{1}{2}\log(-2\eta_2)$ (12.31)

$h(y) = \frac{1}{\sqrt{2\pi}}$ (12.32)

We define the moment parameters as the mean of the sufficient statistics vector, $\mathbf{m} = \mathbb{E}[\mathbf{t}(\mathbf{y})]$.

We see that for a univariate Gaussian, we have $\mathbf{m} = [\mu, \mu^2 + \sigma^2]$.

If we fix $\sigma^2 = 1$, we can write this as a natural exponential family, by defining

$\eta = \mu$ (12.33)

$\mathbf{t}(y) = y$ (12.34)

$A(\mu) = \frac{\mu^2}{2\sigma^2} + \log\sigma = \frac{\mu^2}{2}$ (12.35)

$h(y) = \frac{1}{\sqrt{2\pi}} \exp\left[-\frac{y^2}{2}\right]$ (12.36)

From this, we see that the mean (moment) parameters are given by

$\mathbf{m} = \mathbb{E}[\mathbf{t}(y)] = [\mu; \mu\mu^\top + \Sigma]$ (12.51)

(Note that the above is not a minimal representation, since $\Sigma$ is a symmetric matrix. We can convert to minimal form by working with the upper or lower half of each matrix.)

In Sec. 3.5.3, we gave the equations for marginalization and conditioning of an MVN in moment form. It is also possible to derive the marginalization and conditioning formulas in information form (see Exercise 3.9). We find

$p(y_2) = \mathcal{N}_c(y_2 | \xi_2 - \Lambda_{21} \Lambda_{11}^{-1} \xi_1, \Lambda_{22} - \Lambda_{21} \Lambda_{11}^{-1} \Lambda_{12})$ (12.52)

$p(y_1 | y_2) = \mathcal{N}_c(y_1 | \xi_1 - \Lambda_{12} y_2, \Lambda_{11})$ (12.53)

Thus we see that marginalization is easier in moment form, and conditioning is easier in information form.

### 12.2.2.5 Non-examples

Not all distributions of interest belong to the exponential family. For example, the Student distribution (Sec. 3.4.1) does not belong, since its pdf (Eq. (3.60)) does not have the required form. (However, there is a generalization, known as the $\phi$-exponential family [Nau04; Tsa88] which does include the Student distribution.)

As a more subtle example, consider the uniform distribution, $Y \sim \text{Unif}(\theta_1, \theta_2)$. The pdf has the form

$p(y|\theta) = \frac{1}{\theta_2 - \theta_1} \mathbb{I}(\theta_1 \leq y \leq \theta_2)$ (12.54)

It is tempting to think this is in the exponential family, with $h(y)=1, t(y)=0$, and $Z(\theta)=\theta_2-\theta_1$. However, the support of this distribution (i.e., the set of values $\mathcal{Y}=\{y:p(y)>0\}$) depends on the parameters $\theta$, which violates an assumption of the exponential family.

## 12.2.3 Log partition function is cumulant generating function

The first and second cumulants of a distribution are its mean $\mathbb{E}[Y]$ and variance $\mathbb{V}[Y]$, whereas the first and second moments are $\mathbb{E}[Y]$ and $\mathbb{E}[Y^2]$. We can also compute higher order cumulants (and moments). An important property of the exponential family is that derivatives of the log partition function can be used to generate all the cumulants of the sufficient statistics. In particular, the first and second cumulants are given by

$\nabla_{\eta} A(\eta) = \mathbb{E}[t(y)]$ (12.55)

$\nabla^2 A(\eta) = \text{Cov}[t(y)]$ (12.56)

We prove this result below.

From the above result, we see that the Hessian of $A$ is positive definite, and hence $A$ is a convex function (see Appendix B.4). This will be important when we talk about parameter estimation in Sec. 12.2.4.

### 12.2.3.1 Derivation of the mean

To prove the result, we focus on the 1d case. For the first derivative we have

$$
\begin{aligned}
\frac{dA}{d\eta} &= \frac{d}{d\eta}\left(\log\int \exp(\eta t(y))h(y)\,dy\right) && (12.57)\\
&= \frac{\frac{d}{d\eta}\int \exp(\eta t(y))h(y)\,dy}{\int \exp(\eta t(y))h(y)\,dy} && (12.58)\\
&= \frac{\int t(y)\exp(\eta t(y))h(y)\,dy}{\exp(A(\eta))} && (12.59)\\
&= \int t(y)\exp(\eta t(y)-A(\eta))h(y)\,dy && (12.60)\\
&= \int t(y)p(y)\,dy=\mathbb{E}[t(y)] && (12.61)
\end{aligned}
$$

For example, consider the Bernoulli distribution. We have $A(\eta)=\log(1+e^\eta)$, so the mean is given by

$$
\frac{dA}{d\eta}=\frac{e^\eta}{1+e^\eta}=\frac{1}{1+e^{-\eta}}=\sigma(\eta)=\mu \qquad (12.62)
$$

### 12.2.3.2 Derivation of the variance

For the second derivative we have

$$
\begin{aligned}
\frac{d^2A}{d\eta^2} &= \frac{d}{d\eta}\int t(y)\exp(\eta t(y)-A(\eta))h(y)\,dy && (12.63)\\
&= \int t(y)\exp(\eta t(y)-A(\eta))h(y)(t(y)-A'(\eta))\,dy && (12.64)\\
&= \int t(y)p(y)(t(y)-A'(\eta))\,dy && (12.65)\\
&= \int t^2(y)p(y)\,dy-A'(\eta)\int t(y)p(y)\,dy && (12.66)\\
&= \mathbb{E}[t^2(Y)]-\mathbb{E}[t(y)]^2=\mathbb{V}[t(y)] && (12.67)
\end{aligned}
$$

where we used the fact that $A'(\eta)=\frac{dA}{d\eta}=\mathbb{E}[t(y)]$. For example, for the Bernoulli distribution we have

$$
\begin{aligned}
\frac{d^2A}{d\eta^2} &= \frac{d}{d\eta}(1+e^{-\eta})^{-1}=(1+e^{-\eta})^{-2}e^{-\eta} && (12.68)\\
&=\frac{e^{-\eta}}{1+e^{-\eta}}\frac{1}{1+e^{-\eta}}=\frac{1}{e^\eta+1}\frac{1}{1+e^{-\eta}}=(1-\mu)\mu && (12.69)
\end{aligned}
$$

## 12.2.4 MLE for the exponential family

The likelihood of an exponential family model has the form

$p(\mathcal{D}|\boldsymbol{\eta}) = \left[\prod_{n=1}^{N} h(\mathbf{y}_n)\right] \exp\left(\boldsymbol{\eta}^\top \left[\sum_{n=1}^{N} \mathbf{t}(\mathbf{y}_n)\right] - N A(\boldsymbol{\eta})\right) \propto \exp\left[\boldsymbol{\eta}^\top \mathbf{t}(\mathcal{D}) - N A(\boldsymbol{\eta})\right]$ (12.70)

where $\mathbf{t}(\mathcal{D})$ are the sufficient statistics:

$\mathbf{t}(\mathcal{D}) = \left[\sum_{n=1}^{N} \mathbf{t}_1(\mathbf{y}_n), \dots, \sum_{n=1}^{N} \mathbf{t}_K(\mathbf{y}_n)\right]$ (12.71)

For example, for the Bernoulli model we have $\mathbf{t}(\mathcal{D}) = \left[\sum_n \mathbb{I}(y_n = 1)\right]$, and for the univariate Gaussian, we have $\mathbf{t}(\mathcal{D}) = \left[\sum_n y_n, \sum_n y_n^2\right]$.

The Pitman-Koopman-Darmois theorem states that, under certain regularity conditions, the exponential family is the only family of distributions with finite sufficient statistics. (Here, finite means a size independent of the size of the data set.) In other words, for an exponential family with natural parameters $\boldsymbol{\eta}$, we have

$p(\mathcal{D}|\boldsymbol{\eta}) = p(\mathbf{t}(\mathcal{D})|\boldsymbol{\eta})$ (12.72)

We now show how to use this result to compute the MLE. The log likelihood is given by

$\log p(\mathcal{D}|\boldsymbol{\eta}) = \boldsymbol{\eta}^\top \mathbf{t}(\mathcal{D}) - N A(\boldsymbol{\eta}) + \text{const}$ (12.73)

Since $-A(\boldsymbol{\eta})$ is concave in $\boldsymbol{\eta}$, and $\boldsymbol{\eta}^\top \mathbf{t}(\mathcal{D})$ is linear in $\boldsymbol{\eta}$, we see that the log likelihood is concave, and hence has a unique global maximum. To derive this maximum, we use the fact (shown in Sec. 12.2.3) that the derivative of the log partition function yields the expected value of the sufficient statistic vector:

$\nabla_{\boldsymbol{\eta}} \log p(\mathcal{D}|\boldsymbol{\eta}) = \nabla_{\boldsymbol{\eta}} \boldsymbol{\eta}^\top \mathbf{t}(\mathcal{D}) - N \nabla_{\boldsymbol{\eta}} A(\boldsymbol{\eta}) = \mathbf{t}(\mathcal{D}) - N \mathbb{E}[\mathbf{t}(\mathbf{y})]$ (12.74)

Setting this gradient to zero, we see that at the MLE, the empirical average of the sufficient statistics must equal the model's theoretical expected sufficient statistics, i.e., $\hat{\boldsymbol{\eta}}$ must satisfy

$\mathbb{E}[\mathbf{t}(\mathbf{y})] = \frac{1}{N} \sum_{n=1}^{N} \mathbf{t}(\mathbf{y}_n)$ (12.75)

This is called moment matching. For example, in the Bernoulli distribution, we have $\mathbf{t}(y) = \mathbb{I}(Y = 1)$, so the MLE satisfies

$\mathbb{E}[\mathbf{t}(y)] = p(Y = 1) = \mu = \frac{1}{N} \sum_{n=1}^{N} \mathbb{I}(y_n = 1)$ (12.76)
