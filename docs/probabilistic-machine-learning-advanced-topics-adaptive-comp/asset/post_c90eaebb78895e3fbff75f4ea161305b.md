
where

$$h(x) = (2\pi)^{-D/2}$$

$$\eta = [\xi; -\frac{1}{2}\text{vec}(\Lambda)] = [\Sigma^{-1}\mu; -\frac{1}{2}\text{vec}(\Sigma^{-1})]$$

$$\mathcal{T}(x) = [x; \text{vec}(xx^\mathsf{T})]$$

$$A(\eta) = -\log g(\eta) = -\frac{1}{2} \log |\Lambda| + \frac{1}{2} \xi^\mathsf{T} \Lambda^{-1} \xi$$

From this, we see that the mean (moment) parameters are given by

$$m = \mathbb{E}[\mathcal{T}(x)] = [\mu; \mu\mu^\mathsf{T} + \Sigma]$$

(Note that the above is not a minimal representation, since \(\Lambda\) is a symmetric matrix. We can convert to minimal form by working with the upper or lower half of each matrix.)

## 2.4.2.6 Non-examples

Not all distributions of interest belong to the exponential family. For example, the Student distribution (Section 2.2.2.3) does not belong, since its pdf (Equation (2.30)) does not have the required form. (However, there is a generalization, known as the \(\phi\)-exponential family [Nau04; Tsa88] which does include the Student distribution.)

As a more subtle example, consider the uniform distribution, \(Y \sim \text{Unif}(\theta_1, \theta_2)\). The pdf has the form

$$p(y|\theta) = \frac{1}{\theta_2 - \theta_1} \mathbb{I}(\theta_1 \le y \le \theta_2)$$

It is tempting to think this is in the exponential family, with \(h(y) = 1\), \(\mathcal{T}(y) = \mathbf{0}\), and \(Z(\theta) = \theta_2 - \theta_1\). However, the support of this distribution (i.e., the set of values \(\mathcal{Y} = \{y : p(y) > 0\}\)) depends on the parameters \(\theta\), which violates an assumption of the exponential family.

## 2.4.3 Log partition function is cumulant generating function

The first and second **cumulants** of a distribution are its mean \(\mathbb{E}[X]\) and variance \(\mathbb{V}[X]\), whereas the first and second moments are \(\mathbb{E}[X]\) and \(\mathbb{E}[X^2]\). We can also compute higher order cumulants (and moments). An important property of the exponential family is that derivatives of the log partition function can be used to generate all the **cumulants** of the sufficient statistics. In particular, the first and second cumulants are given by

$$\nabla_\eta A(\eta) = \mathbb{E}[\mathcal{T}(x)]$$

$$\nabla_\eta^2 A(\eta) = \text{Cov}[\mathcal{T}(x)]$$

We prove this result below.

### 2.4.3.1 Derivation of the mean

For simplicity, we focus on the 1d case. For the first derivative we have

$$
\begin{align}
\frac{dA}{d\eta} &= \frac{d}{d\eta} \left( \log \int \exp(\eta \mathcal{T}(x)) h(x) dx \right) \label{eq:deriv_mean_1} \\
&= \frac{\frac{d}{d\eta} \int \exp(\eta \mathcal{T}(x)) h(x) dx}{\int \exp(\eta \mathcal{T}(x)) h(x) dx} \label{eq:deriv_mean_2} \\
&= \frac{\int \mathcal{T}(x) \exp(\eta \mathcal{T}(x)) h(x) dx}{\exp(A(\eta))} \label{eq:deriv_mean_3} \\
&= \int \mathcal{T}(x) \exp(\eta \mathcal{T}(x) - A(\eta)) h(x) dx \label{eq:deriv_mean_4} \\
&= \int \mathcal{T}(x) p(x) dx = \mathbb{E} [\mathcal{T}(x)] \label{eq:deriv_mean_5}
\end{align}
$$

For example, consider the Bernoulli distribution. We have \(A(\eta) = \log(1 + e^\eta)\), so the mean is given by

\(\frac{dA}{d\eta} = \frac{e^\eta}{1 + e^\eta} = \frac{1}{1 + e^{-\eta}} = \sigma(\eta) = \mu\)

### 2.4.3.2 Derivation of the variance

For simplicity, we focus on the 1d case. For the second derivative we have

$$
\begin{align}
\frac{d^2 A}{d\eta^2} = \frac{d}{d\eta} \int \mathcal{T}(x) \exp(\eta \mathcal{T}(x) - A(\eta)) h(x) dx \label{eq:deriv_var_1} \\
= \int \mathcal{T}(x) \exp(\eta \mathcal{T}(x) - A(\eta)) h(x) (\mathcal{T}(x) - A'(\eta)) dx \label{eq:deriv_var_2} \\
= \int \mathcal{T}(x) p(x) (\mathcal{T}(x) - A'(\eta)) dx \label{eq:deriv_var_3} \\
= \int \mathcal{T}^2(x) p(x) dx - A'(\eta) \int \mathcal{T}(x) p(x) dx \label{eq:deriv_var_4} \\
= \mathbb{E} [\mathcal{T}^2(X)] - \mathbb{E} [\mathcal{T}(x)]^2 = \mathbb{V} [\mathcal{T}(x)] \label{eq:deriv_var_5}
\end{align}
$$

where we used the fact that \(A'(\eta) = \frac{dA}{d\eta} = \mathbb{E} [\mathcal{T}(x)]\). For example, for the Bernoulli distribution we have

\(\frac{d^2 A}{d\eta^2} = \frac{d}{d\eta} (1 + e^{-\eta})^{-1} = (1 + e^{-\eta})^{-2} e^{-\eta}\)

$$
= \frac{e^{-\eta}}{1 + e^{-\eta}} \frac{1}{1 + e^{-\eta}} = \frac{1}{e^\eta + 1} \frac{1}{1 + e^{-\eta}} = (1 - \mu)\mu
$$

### 2.4.3.3 Connection with the Fisher information matrix

In Section 3.3.4, we show that, under some regularity conditions, the Fisher information matrix is given by

\(\mathbf{F}(\boldsymbol{\eta}) \triangleq \mathbb{E}_{p(\boldsymbol{x}|\boldsymbol{\eta})} [\nabla \log p(\boldsymbol{x}|\boldsymbol{\eta}) \nabla \log p(\boldsymbol{x}|\boldsymbol{\eta})^T] = - \mathbb{E}_{p(\boldsymbol{x}|\boldsymbol{\eta})} [\nabla^2_{\boldsymbol{\eta}} \log p(\boldsymbol{x}|\boldsymbol{\eta})]\)

Hence for an exponential family model we have

\(\mathbf{F}(\boldsymbol{\eta}) = - \mathbb{E}_{p(\boldsymbol{x}|\boldsymbol{\eta})} [\nabla^2_{\boldsymbol{\eta}} (\boldsymbol{\eta}^T \mathcal{T}(\boldsymbol{x}) - A(\boldsymbol{\eta}))] = \nabla^2_{\boldsymbol{\eta}} A(\boldsymbol{\eta}) = \text{Cov}[\mathcal{T}(\boldsymbol{x})]\)

Thus the Hessian of the log partition function is the same as the FIM, which is the same as the covariance of the sufficient statistics. See Section 3.3.4.6 for details.

## 2.4.4 Canonical (natural) vs mean (moment) parameters

Let \(\Omega\) be the set of normalizable natural parameters:

\(\Omega \triangleq \{ \boldsymbol{\eta} \in \mathbb{R}^K : Z(\boldsymbol{\eta}) < \infty \}\)

We say that an exponential family is **regular** if \(\Omega\) is an open set. It can be shown that \(\Omega\) is a convex set, and \(A(\boldsymbol{\eta})\) is a convex function defined over this set.

In Section 2.4.3, we prove that the derivative of the log partition function is equal to the mean of the sufficient statistics, i.e.,

\(\boldsymbol{m} = \mathbb{E}[\mathcal{T}(\boldsymbol{x})] = \nabla_{\boldsymbol{\eta}} A(\boldsymbol{\eta})\)

The set of valid moment parameters is given by

\(\mathcal{M} = \{ \boldsymbol{m} \in \mathbb{R}^K : \mathbb{E}_p[\mathcal{T}(\boldsymbol{x})] = \boldsymbol{m} \}\)

for some distribution \(p\).

We have seen that we can convert from the natural parameters to the moment parameters using

\(\boldsymbol{m} = \nabla_{\boldsymbol{\eta}} A(\boldsymbol{\eta})\)

If the family is minimal, one can show that

\(\boldsymbol{\eta} = \nabla_{\boldsymbol{m}} A^*(\boldsymbol{m})\)

where \(A^*(\boldsymbol{m})\) is the convex conjugate of \(A\):

\(A^*(\boldsymbol{m}) \triangleq \sup_{\boldsymbol{\eta} \in \Omega} \boldsymbol{\mu}^T \boldsymbol{\eta} - A(\boldsymbol{\eta})\)

Thus the pair of operators \((\nabla A, \nabla A^*)\) lets us go back and forth between the natural parameters \(\boldsymbol{\eta} \in \Omega\) and the mean parameters \(\boldsymbol{m} \in \mathcal{M}\).

For future reference, note that the Bregman divergences (Section 5.1.10) associated with \(A\) and \(A^*\) are as follows:

\(B_A(\boldsymbol{\lambda}_1 || \boldsymbol{\lambda}_2) = A(\boldsymbol{\lambda}_1) - A(\boldsymbol{\lambda}_2) - (\boldsymbol{\lambda}_1 - \boldsymbol{\lambda}_2)^T \nabla_{\boldsymbol{\lambda}} A(\boldsymbol{\lambda}_2)\)

\(B_{A^*}(\boldsymbol{\mu}_1 || \boldsymbol{\mu}_2) = A(\boldsymbol{\mu}_1) - A(\boldsymbol{\mu}_2) - (\boldsymbol{\mu}_1 - \boldsymbol{\mu}_2)^T \nabla_{\boldsymbol{\mu}} A(\boldsymbol{\mu}_2)\)

## 2.4.5 MLE for the exponential family

The likelihood of an exponential family model has the form

$$p(\mathcal{D}|\boldsymbol{\eta}) = \left[ \prod_{n=1}^N h(\mathbf{x}_n) \right] \exp \left( \boldsymbol{\eta}^\mathsf{T} [\sum_{n=1}^N \mathcal{T}(\mathbf{x}_n)] - N A(\boldsymbol{\eta}) \right) \propto \exp \left[ \boldsymbol{\eta}^\mathsf{T} \mathcal{T}(\mathcal{D}) - N A(\boldsymbol{\eta}) \right] \quad (2.242)$$

where \(\mathcal{T}(\mathcal{D})\) are the sufficient statistics:

$$\mathcal{T}(\mathcal{D}) = [\sum_{n=1}^N \mathcal{T}_1(\mathbf{x}_n), \dots, \sum_{n=1}^N \mathcal{T}_K(\mathbf{x}_n)] \quad (2.243)$$

For example, for the Bernoulli model we have \(\mathcal{T}(\mathcal{D}) = [\sum_n \mathbb{I}(x_n = 1)]\), and for the univariate Gaussian, we have \(\mathcal{T}(\mathcal{D}) = [\sum_n x_n, \sum_n x_n^2]\).

The **Pitman-Koopman-Darmois theorem** states that, under certain regularity conditions, the exponential family is the only family of distributions with finite sufficient statistics. (Here, finite means a size independent of the size of the dataset.) In other words, for an exponential family with natural parameters \(\boldsymbol{\eta}\), we have

$$p(\mathcal{D}|\boldsymbol{\eta}) = p(\mathcal{T}(\mathcal{D})|\boldsymbol{\eta}) \quad (2.244)$$

We now show how to use this result to compute the MLE. The log likelihood is given by

$$\log p(\mathcal{D}|\boldsymbol{\eta}) = \boldsymbol{\eta}^\mathsf{T} \mathcal{T}(\mathcal{D}) - N A(\boldsymbol{\eta}) + \text{const} \quad (2.245)$$

Since \(-A(\boldsymbol{\eta})\) is concave in \(\boldsymbol{\eta}\), and \(\boldsymbol{\eta}^\mathsf{T}\mathcal{T}(\mathcal{D})\) is linear in \(\boldsymbol{\eta}\), we see that the log likelihood is concave, and hence has a unique global maximum. To derive this maximum, we use the fact (shown in Section 2.4.3) that the derivative of the log partition function yields the expected value of the sufficient statistic vector:

$$\nabla_{\boldsymbol{\eta}} \log p(\mathcal{D}|\boldsymbol{\eta}) = \nabla_{\boldsymbol{\eta}} \boldsymbol{\eta}^\mathsf{T} \mathcal{T}(\mathcal{D}) - N \nabla_{\boldsymbol{\eta}} A(\boldsymbol{\eta}) = \mathcal{T}(\mathcal{D}) - N \mathbb{E} [\mathcal{T}(\mathbf{x})] \quad (2.246)$$

For a single data case, this becomes

$$\nabla_{\boldsymbol{\eta}} \log p(\mathbf{x}|\boldsymbol{\eta}) = \mathcal{T}(\mathbf{x}) - \mathbb{E} [\mathcal{T}(\mathbf{x})] \quad (2.247)$$

Setting the gradient in Equation (2.246) to zero, we see that at the MLE, the empirical average of the sufficient statistics must equal the model's theoretical expected sufficient statistics, i.e., \(\hat{\boldsymbol{\eta}}\) must satisfy

$$\mathbb{E} [\mathcal{T}(\mathbf{x})] = \frac{1}{N} \sum_{n=1}^N \mathcal{T}(\mathbf{x}_n) \quad (2.248)$$

This is called **moment matching**. For example, in the Bernoulli distribution, we have \(\mathcal{T}(x) = \mathbb{I}(X = 1)\), so the MLE satisfies

$$\mathbb{E} [\mathcal{T}(x)] = p(X = 1) = \mu = \frac{1}{N} \sum_{n=1}^N \mathbb{I}(x_n = 1) \quad (2.249)$$
