where

$$\Lambda_T = \Lambda_0 + \sum_{s=1}^{T} \psi(X_s)\psi(X_s)^{\top}.$$

Proof We can apply Theorem 15.6 by taking $\sigma^2 = M^2$. By using the following inequality

$$0 \le \frac{1 - b_t}{b_t} + \ln b_t,$$

we obtain

$$\begin{aligned}
\sum_{t=1}^{T}(Y_t - \hat Y_t)^2 &\le \sum_{t=1}^{T}\left[(Y_t - \hat Y_t)^2 + M^2\frac{1 - b_t}{b_t} + M^2\ln b_t\right]\\
&\le \sum_{t=1}^{T}\left[(Y_t - \hat Y_t)^2 + (Y_t - \hat Y_t)^2\frac{1 - b_t}{b_t} + M^2\ln b_t\right] \tag{15.5}\\
&\le \sum_{t=1}^{T}\left[\frac{(Y_t - \hat w(\mathcal{S}_{t-1})^{\top}\psi(X_t))^2}{b_t} + M^2\ln b_t\right],
\end{aligned}$$

where $b_t$ is defined in Theorem 15.6. Note that (15.5) used $1 - b_t \le 0$ and $(Y_t - \hat Y_t)^2 \le M^2$. The desired result is now a direct application of Theorem 15.6. $\square$

In order to interpret the regret bound in Corollary 15.7, we need to find an interpretable upper bound of $\Lambda_0^{-1}\Lambda_T$. For $\Lambda_0 = \lambda I$, we have the following result.

# Proposition 15.8

Given any $\mathcal{X}$ and $\psi: \mathcal{X} \to \mathcal{H}$, where $\mathcal{H}$ is an inner product space. Then for each $\lambda > 0$ and integer $T$, the embedding entropy of $\psi(\cdot)$ can be defined as

$$\text{entro}(\lambda, \psi(\mathcal{X})) = \sup_{\mathcal{D}} \ln \left| I + \frac{1}{\lambda} \mathbb{E}_{X \sim \mathcal{D}} \psi(X)\psi(X)^{\top} \right|.$$

If $\sup_{X \in \mathcal{X}} \|\psi(X)\|_{\mathcal{H}} \le B$ and $\dim(\mathcal{H}) < \infty$, then

$$\text{entro}(\lambda, \psi(\mathcal{X})) \le \dim(\mathcal{H}) \ln \left(1 + \frac{B^2}{\dim(\mathcal{H})\lambda}\right).$$

Moreover, generally, assume that $\mathcal{H}$ has representation $\psi(x) = [\psi_j(x)]_{j=1}^{\infty}$ with 2-norm, and given any $\epsilon > 0$, 

$$d(\epsilon) = \min \left\{ |S| : \sup_{x} \sum_{j \notin S} (\psi_j(x))^2 \le \epsilon \right\}.$$

Then

$$\text{entro}(\lambda, \psi(\mathcal{X})) \le \inf_{\epsilon > 0} \left[ d(\epsilon) \ln \left(1 + \frac{B^2}{\lambda d(\epsilon)}\right) + \frac{\epsilon}{\lambda} \right].$$