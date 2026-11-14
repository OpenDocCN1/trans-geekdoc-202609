
Since the Hessian measures the curvature of the likelihood, we see that the FIM tells us how well the likelihood function can identify the best set of parameters. (If a likelihood function is flat, we cannot infer anything about the parameters, but if it is a delta function at a single point, the best parameter vector will be uniquely determined.) Thus the FIM is intimately related to the frequentist notion of uncertainty of the MLE, which is captured by the variance we expect to see in the MLE if we were to compute it on multiple different datasets drawn from our model.

More precisely, we have the following theorem.

### Theorem 3.3.2. If \( log \, p(x|\theta) \) is twice differentiable, and under certain regularity conditions, the FIM is equal to the expected Hessian of the NLL, i.e.,

\[
\mathbf{F}(\theta)_{ij} \triangleq \mathbb{E}_{x\sim\theta} \left[ \left( \frac{\partial}{\partial \theta_i} log \, p(x|\theta) \right) \left( \frac{\partial}{\partial \theta_j} log \, p(x|\theta) \right) \right] = \mathbb{E}_{x\sim\theta} \left[ \frac{\partial^2}{\partial \theta_i \partial \theta_j} log \, p(x|\theta) \right] \tag{3.43}
\]

Before we prove this result, we establish the following important lemma.

### Lemma 3.3.1. The expected value of the score function is zero, i.e.,

\[
\mathbb{E}_{p(x|\theta)} [\nabla log \, p(x|\theta)] = \mathbf{0} \tag{3.44}
\]

We prove this lemma in the scalar case. First, note that since \(\int p(x|\theta) dx = 1\), we have

\[
\frac{\partial}{\partial \theta} \int p(x|\theta) dx = 0 \tag{3.45}
\]

Combining this with the identity

\[
\frac{\partial}{\partial \theta} p(x|\theta) = \left[ \frac{\partial}{\partial \theta} log \, p(x|\theta) \right] p(x|\theta) \tag{3.46}
\]

we have

\[
0 = \int \frac{\partial}{\partial \theta} p(x|\theta) dx = \int \left[ \frac{\partial}{\partial \theta} log \, p(x|\theta) \right] p(x|\theta) dx = \mathbb{E} [s(\theta)] \tag{3.47}
\]

Now we return to the proof of our main theorem. For simplicity, we will focus on the scalar case, following the presentation of [Ric95, p263].

**Proof.** Taking derivatives of Equation (3.47), we have

\[
0 = \frac{\partial}{\partial \theta} \int \left[ \frac{\partial}{\partial \theta} log \, p(x|\theta) \right] p(x|\theta) dx \tag{3.48}
\]

\[
= \int \left[ \frac{\partial^2}{\partial \theta^2} log \, p(x|\theta) \right] p(x|\theta) dx + \int \left[ \frac{\partial}{\partial \theta} log \, p(x|\theta) \right] \frac{\partial}{\partial \theta} p(x|\theta) dx \tag{3.49}
\]

\[
= \int \left[ \frac{\partial^2}{\partial \theta^2} log \, p(x|\theta) \right] p(x|\theta) dx + \int \left[ \frac{\partial}{\partial \theta} log \, p(x|\theta) \right]^2 p(x|\theta) dx \tag{3.50}
\]

and hence

\[
-\mathbb{E}_{x\sim\theta} \left[ \frac{\partial^2}{\partial \theta^2} log \, p(x|\theta) \right] = \mathbb{E}_{x\sim\theta} \left[ \left( \frac{\partial}{\partial \theta} log \, p(x|\theta) \right)^2 \right] \tag{3.51}
\]

as claimed.

Now consider the Hessian of the NLL given $N$ iid samples $\mathcal{D} = \{ \mathbf{x}_n : n = 1 : N \}$:

$$H_{ij} \triangleq -\frac{\partial^2}{\partial \theta_i \partial \theta_j} \log p(\mathcal{D}|\boldsymbol{\theta}) = - \sum_{n=1}^N \frac{\partial^2}{\partial \theta_i \partial \theta_j} \log p(\mathbf{x}_n|\boldsymbol{\theta})$$

From the above theorem, we have

$$ \mathbb{E}_{p(\mathcal{D}|\boldsymbol{\theta})} [ \mathbf{H}(\mathcal{D}) | \boldsymbol{\theta} ] = N \mathbf{F}(\boldsymbol{\theta}) $$

This is useful when deriving the sampling distribution of the MLE, as discussed in Section 3.3.3.

### 3.3.4.3 Example: FIM for the binomial

Suppose $x \sim \text{Bin}(n, \theta)$. The log likelihood for a single sample is

$$l(\theta|x) = x \log \theta + (n-x) \log(1-\theta)$$

The score function is just the gradient of the log-likelihood:

$$s(\theta|x) \triangleq \frac{d}{d\theta} l(\theta|x) = \frac{x}{\theta} - \frac{n-x}{1-\theta}$$

The gradient of the score function is

$$s'(\theta|x) = -\frac{x}{\theta^2} - \frac{n-x}{(1-\theta)^2}$$

Hence the Fisher information is given by

$$F(\theta) = \mathbb{E}_{x\sim\theta} [ -s'(\theta|x) ] = \frac{n\theta}{\theta^2} + \frac{n-n\theta}{(1-\theta)^2} = \frac{n}{\theta} + \frac{n}{1-\theta} = \frac{n}{\theta(1-\theta)}$$

### 3.3.4.4 Example: FIM for the univariate Gaussian

Consider a univariate Gaussian $p(x|\boldsymbol{\theta}) = \mathcal{N}(x|\mu, v)$. We have

$$\ell(\boldsymbol{\theta}) = \log p(x|\boldsymbol{\theta}) = -\frac{1}{2v}(x-\mu)^2 - \frac{1}{2} \log(v) - \frac{1}{2} \log(2\pi)$$

The partial derivatives are given by

$$\frac{\partial \ell}{\partial \mu} = (x-\mu)v^{-1}, \frac{\partial^2 \ell}{\partial \mu^2} = -v^{-1}$$

$$\frac{\partial \ell}{\partial v} = \frac{1}{2}v^{-2}(x-\mu)^2 - \frac{1}{2}v^{-1}, \frac{\partial^2 \ell}{\partial v^2} = -v^{-3}(x-\mu)^2 + \frac{1}{2}v^{-2}$$

$$\frac{\partial \ell}{\partial \mu \partial v} = -v^{-2}(x-\mu)$$

and hence

$$\mathbf{F}(\boldsymbol{\theta}) = \left( \begin{matrix} \mathbb{E}[v^{-1}] & \mathbb{E}[v^{-2}(x-\mu)] \\ \mathbb{E}[v^{-2}(x-\mu)] & \mathbb{E}[v^{-3}(x-\mu)^2 - \frac{1}{2}v^{-2}] \end{matrix} \right) = \left( \begin{matrix} \frac{1}{v} & 0 \\ 0 & \frac{1}{2v^2} \end{matrix} \right)$$

### 3.3.4.5 Example: FIM for logistic regression

Consider \(\ell_2\)-regularized binary logistic regression. The negative log joint has the following form:

\[
\mathcal{E}(\boldsymbol{w}) = -\log[p(\boldsymbol{y}|\mathbf{X}, \boldsymbol{w})p(\boldsymbol{w}|\lambda)] = -\boldsymbol{w}^\mathsf{T}\mathbf{X}^\mathsf{T}\boldsymbol{y} + \sum_{n=1}^N \log(1 + e^{\boldsymbol{w}^\mathsf{T}\boldsymbol{x}_n}) + \frac{\lambda}{2}\boldsymbol{w}^\mathsf{T}\boldsymbol{w}
\]

The derivative has the form

\[
\nabla_{\boldsymbol{w}} \mathcal{E}(\boldsymbol{w}) = -\mathbf{X}^\mathsf{T}\boldsymbol{y} + \mathbf{X}^\mathsf{T}\boldsymbol{s} + \lambda \boldsymbol{w}
\]

where \(s_n = \sigma(\boldsymbol{w}^\mathsf{T}\boldsymbol{x}_n)\). The FIM is given by

\[
\mathbf{F}(\boldsymbol{w}) = \mathbb{E}_{p(\boldsymbol{y}|\mathbf{X}, \boldsymbol{w}, \lambda)} \left[ \nabla^2 \mathcal{E}(\boldsymbol{w}) \right] = \mathbf{X}^\mathsf{T} \boldsymbol{\Lambda} \mathbf{X} + \lambda \mathbf{I}
\]

where \(\boldsymbol{\Lambda}\) is the \(N \times N\) diagonal matrix with entries

\[
\Lambda_{nn} = \sigma(\boldsymbol{w}^\mathsf{T}\boldsymbol{x}_n)(1 - \sigma(\boldsymbol{w}^\mathsf{T}\boldsymbol{x}_n))
\]

### 3.3.4.6 FIM for the exponential family

In this section, we discuss how to derive the FIM for an exponential family distribution with natural parameters \(\boldsymbol{\eta}\), which generalizes many of the previous examples. Recall from Equation (2.216) that the gradient of the log partition function is the expected sufficient statistics

\[
\nabla_{\boldsymbol{\eta}} A(\boldsymbol{\eta}) = \mathbb{E}[\mathcal{T}(\boldsymbol{x})] = \boldsymbol{m}
\]

and from Equation (2.247) that the gradient of the log likelihood is the statistics minus their expected value:

\[
\nabla_{\boldsymbol{\eta}} \log p(\boldsymbol{x}|\boldsymbol{\eta}) = \mathcal{T}(\boldsymbol{x}) - \mathbb{E}[\mathcal{T}(\boldsymbol{x})]
\]

Hence the FIM wrt the natural parameters \(\mathbf{F}_\boldsymbol{\eta}\) is given by

\[
(\mathbf{F}_\boldsymbol{\eta})_{ij} = \mathbb{E}_{p(\boldsymbol{x}|\boldsymbol{\eta})} \left[ \frac{\partial \log p(\boldsymbol{x}|\boldsymbol{\eta})}{\partial \eta_i} \frac{\partial \log p(\boldsymbol{x}|\boldsymbol{\eta})}{\partial \eta_j} \right]
= \mathbb{E}_{p(\boldsymbol{x}|\boldsymbol{\eta})} [(\mathcal{T}(\boldsymbol{x})_i - m_i)(\mathcal{T}(\boldsymbol{x})_j - m_j)]
= \text{Cov}[\mathcal{T}(\boldsymbol{x})_i, \mathcal{T}(\boldsymbol{x})_j]
\]

or, in short,

\[
\mathbf{F}_\boldsymbol{\eta} = \text{Cov}[\mathcal{T}(\boldsymbol{x})]
\]

Sometimes we need to compute the Fisher wrt the moment parameters \(\boldsymbol{m}\):

\[
(\mathbf{F}_{\boldsymbol{m}})_{ij} = \mathbb{E}_{p(\boldsymbol{x}|\boldsymbol{m})} \left[ \frac{\partial \log p(\boldsymbol{x}|\boldsymbol{\eta})}{\partial m_i} \frac{\partial \log p(\boldsymbol{x}|\boldsymbol{\eta})}{\partial m_j} \right]
\]
