
Note that entropy regularization is closely related to $L_1$ regularization. Here we consider the case of convex hull, with weights $w \ge 0$, and $\sum_j w_j = 1$. For entropy regularization, we will consider a probability interpretation of $w$, which may now be regarded as a distribution over models, to be learned from the training data. Since we work with distributions in this section, in the following we will adopt a different notation, and replace the weight $w$ by a general distribution $q(\theta)$ on $\Theta$, where $\Theta$ may be either continuous or discrete.

Our goal is to find a distribution $q$ on $\Theta$, such that the additive model (10.1) is replaced by the average over $\psi(\theta,x) \in \Psi$ according to $q$:

$f(q,x)=\int \psi(\theta,x)q(\theta)d\theta = \mathbb{E}_{\theta\sim q(\cdot)}\psi(\theta,x). \tag{10.11}$

Since $q(\theta)$ is learned from the training data $\mathcal{S}_n$, we will call such a distribution $q(\theta)$ posterior distribution, using the Bayesian statistics analogy. Consider a prior distribution $q_0(\theta)$ on $\Theta$ (we use the term prior distribution to indicate that it does not depend on the training data $\mathcal{S}_n$), and we may consider the entropy regularization to regularize the posterior distribution $q$:

$\mathrm{KL}(q||q_0)=\int q(\theta)\ln \frac{q(\theta)}{q_0(\theta)}d\theta.$

We have the following Rademacher complexity estimate for this entropy regularization.

## Theorem 10.16
Consider $h(q)=h_0(q)=\lambda\mathrm{KL}(q||q_0)$, and $\mathcal{F}=\{f(q,x)\}$ in (10.11). The offset Rademacher complexity can be bounded as

$R^{h}(\mathcal{F},\mathcal{S}_n)\le \frac{\lambda}{2}\ln \mathbb{E}_{\theta\sim q_0}\exp\left[\frac{2}{\lambda^2 n^2}\sum_{i=1}^n \psi(\theta,X_i)^2\right]\le \frac{1}{\lambda n^2}\sup_{\theta}\sum_{i=1}^n \psi(\theta,X_i)^2.$

Proof  We have

$R^{h}(\mathcal{F},\mathcal{S}_n)=\mathbb{E}_{\sigma}\sup_{q}\left[\frac{1}{n}\sum_{i=1}^n \sigma_i\mathbb{E}_{\theta\sim q}\psi(\theta,X_i)-\frac{\lambda}{2}\mathrm{KL}(q||q_0)\right]$ 
$=\frac{\lambda}{2}\mathbb{E}_{\sigma}\ln \mathbb{E}_{\theta\sim q_0}\exp\left[\frac{2}{\lambda n}\sum_{i=1}^n \sigma_i\psi(\theta,X_i)\right]$ 
$\le \frac{\lambda}{2}\ln \mathbb{E}_{\theta\sim q_0}\mathbb{E}_{\sigma}\exp\left[\frac{2}{\lambda n}\sum_{i=1}^n \sigma_i\psi(\theta,X_i)\right]$ 
$\le \frac{\lambda}{2}\ln \mathbb{E}_{\theta\sim q_0}\exp\left[\frac{2}{\lambda^2 n^2}\sum_{i=1}^n \psi(\theta,X_i)^2\right].$

The first equation is the definition of Rademacher complexity (with offset). The second equation follows from Proposition 7.16. The first inequality used Jensen's inequality and the concavity of $\ln(\cdot)$. The second inequality follows from the sub-Gaussian exponential inequality. This implies the desired bound.

The above result for Rademacher complexity appeared in Meir and Zhang (2003), which immediately implies the following result.

## Corollary 10.17

Let $\mathcal{F}_A = \{f(q,x): \mathrm{KL}(q||q_0) \le A^2\}$ be entropy regularized functions of (10.11). Then

$R(\mathcal{F}_A,\mathcal{S}_n) \le \sqrt{\frac{2}{n}}A\sup_{\theta}\sqrt{\frac{1}{n}\sum_{i=1}^n\psi(\theta,X_i)^2}$.

Proof  From Theorem 10.16, we have

$R(\mathcal{F}_A,\mathcal{S}_n) \le \frac{\lambda}{2}A^2 + \frac{1}{\lambda n^2}\sup_{\theta}\sum_{i=1}^n\psi(\theta,X_i)^2$.

By optimizing over $\lambda$, we obtain the desired bound.

This bound holds for general function classes. In the case of finite family with $\Theta = \{\theta_1,\dots,\theta_m\}$, and $q_0(\theta)=1/m$ for all $\theta$, we have

$\mathrm{KL}(q||q_0) \le \ln m$

for all $q$. Therefore entropy regularization implies a bound for $L_1$ regularization with nonnegative constraint $\sum_{j=1}^m w_j = 1$ and $w_j \ge 0$. Since this is exactly the convex hull of $\Psi = \{\psi(\theta,x)\}$, Corollary 10.17 implies that

$R(\mathrm{CONV}(\Psi),\mathcal{S}_n) \le \sqrt{\frac{2\ln m}{n}}\sup_{\theta}\|\psi(\theta,\cdot)\|_{L_2(\mathcal{S}_n)}$

which is identical to the Rademacher complexity of convex hull of finite function class obtained in Theorem 10.8 (by using Theorem 6.23).

Similar to Corollary 10.12 and Corollary 10.14, one can use the Rademacher complexity of entropy regularization and Theorem 6.31 to obtain uniform convergence and oracle inequalities for additive models with entropy regularization. In addition, a particularly interesting application of entropy regularization is the information theoretical approach to generalization analysis, which we describe in the following.

We now consider the notations introduced in Section 3.3, where we are interested in minimizing a loss function $\phi(w,z): \Omega \times \mathcal{Z} \to \mathbb{R}$. We consider a general randomized algorithm $\mathcal{A}: \mathcal{Z}^n \to \Delta(\Omega)$, where $\Delta(\Omega)$ denotes probability measures on $\Omega$. That is, given training data $\mathcal{S}_n$, $\mathcal{A}(\mathcal{S}_n)$ returns a posterior distribution $\hat q$ on $\Omega$. It then randomly draws a model from $\hat q$ to make a prediction. The following uniform convergence result can be interpreted as a generalization bound for an arbitrary randomized learning algorithm.

## Theorem 10.18

Consider a randomized algorithm $\mathcal{A}$ that returns a distribution $\hat q(w|\mathcal{S}_n)$ on the parameter space $\Omega$ for each training data $\mathcal{S}_n \in \mathcal{Z}^n$. Let

$\Lambda(\lambda,w) = -\frac{1}{\lambda}\ln \mathbb{E}_{Z\sim\mathcal{D}}\exp\big(-\lambda\phi(w,Z)\big)$.

*Then for any data independent distribution $q_0$ on $\Omega$ and $\lambda > 0$, we have*

$$\mathbb{E}_{\mathcal{S}_n}\mathbb{E}_{w\sim\hat{q}(\cdot|\mathcal{S}_n)}\Lambda(1/(\lambda n),w)\le \mathbb{E}_{\mathcal{S}_n}\mathbb{E}_{w\sim\hat{q}(\cdot|\mathcal{S}_n)}\frac{1}{n}\sum_{i=1}^n\phi(w,Z_i)+\lambda\mathbb{E}_{\mathcal{S}_n}\mathrm{KL}(\hat{q}||q_0).$$

*Moreover, for any $\lambda > 0$, with probability at least $1-\delta$ over $\mathcal{S}_n$,*

$$\mathbb{E}_{w\sim\hat{q}(\cdot|\mathcal{S}_n)}\Lambda(1/(\lambda n),w)\le \mathbb{E}_{w\sim\hat{q}(\cdot|\mathcal{S}_n)}\frac{1}{n}\sum_{i=1}^n\phi(w,Z_i)+[\lambda\mathrm{KL}(\hat{q}||q_0)+\lambda\ln(1/\delta)].$$

*Proof* Let

$$\Delta(\mathcal{S}_n)=\sup_{\hat{q}}\Big[\mathbb{E}_{w\sim\hat{q}(\cdot|\mathcal{S}_n)}\Big(\Lambda(1/(\lambda n),w)-\frac{1}{n}\sum_{i=1}^n\phi(w,Z_i)\Big)-\lambda\mathrm{KL}(\hat{q}||q_0)\Big].$$

We have

$$\ln\mathbb{E}_{\mathcal{S}_n\sim\mathcal{D}^n}\exp(\lambda^{-1}\Delta(\mathcal{S}_n))$$ $$=\ln\mathbb{E}_{\mathcal{S}_n\sim\mathcal{D}^n}\exp\Big[\ln\mathbb{E}_{w\sim q_0}\exp\Big(\lambda^{-1}\Lambda(1/(\lambda n),w)-\frac{\lambda^{-1}}{n}\sum_{i=1}^n\phi(w,Z_i)\Big)\Big]$$ $$=\ln\mathbb{E}_{w\sim q_0}\Big[\exp(\lambda^{-1}\Lambda(1/(\lambda n),w))\mathbb{E}_{\mathcal{S}_n\sim\mathcal{D}^n}\exp\Big(-\frac{\lambda^{-1}}{n}\sum_{i=1}^n\phi(w,Z_i)\Big)\Big]$$ $$=\ln\mathbb{E}_{w\sim q_0}\Big[\exp(\lambda^{-1}\Lambda(1/(\lambda n),w))\Big(\mathbb{E}_{Z\sim\mathcal{D}}\exp\Big(-\frac{\lambda^{-1}}{n}\phi(w,Z)\Big)\Big)^n\Big]$$ $$=\ln\mathbb{E}_{w\sim q_0}\Big[\exp(\lambda^{-1}\Lambda(1/(\lambda n),w))\Big(\exp\Big(-\frac{1}{\lambda n}\Lambda(1/(\lambda n),w)\Big)\Big)^n\Big]$$ $$=0.$$

The first equation used Proposition 7.16. The second equation used algebraic manipulation. The third equation used the independence of $Z_i$. The fourth equation used the definition of $\Lambda(\lambda,w)$. This implies that $$\lambda^{-1}\mathbb{E}_{\mathcal{S}_n\sim\mathcal{D}^n}\Delta(\mathcal{S}_n)\le\ln\mathbb{E}_{\mathcal{S}_n\sim\mathcal{D}^n}\exp(\lambda^{-1}\Delta(\mathcal{S}_n))=0.$$

This implies the first bound. For the second inequality, we know that $$\Pr\big(\lambda^{-1}\Delta(\mathcal{S}_n)\ge\ln(1/\delta)\big)\le\mathbb{E}_{\mathcal{S}_n}\exp\big(\lambda^{-1}\Delta(\mathcal{S}_n)-\ln(1/\delta)\big)=\delta.$$ This proves the second result.

The style of the generalization result stated in Theorem 10.18 is often referred to as *PAC-Bayes* analysis (McAllester, 1999), which can be applied to an arbitrary randomized learning algorithm $\mathcal{A}:\mathcal{Z}^n\to\Delta(\Omega)$. In the literature, it is often applied to bounded loss functions, for which we can estimate the logarithmic moment generating function $\Lambda(\lambda,w)$ easily. More generally, we may consider sub-Gaussian loss functions as in the following example.

## Example 10.19
Assume that $\phi(w,Z)$ is uniformly sub-Gaussian: there exists $\sigma>0$ so that
