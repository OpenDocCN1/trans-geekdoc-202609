
In the NTK regime, the generalization of neural network can be easily obtained using Rademacher complexity. Specifically, the following result can be obtained from Theorem 9.20.

## Corollary 11.19
*Let*
$\mathcal{F}_A^{\mathrm{NTK}}(\widetilde{w}) = \{f_m^{\mathrm{NTK}}(w,x): \|w-\widetilde{w}\|_2^2 \le A^2\},$
then
$R_n(\mathcal{F}_A^{\mathrm{NTK}}(\widetilde{w}),\mathcal{D}) \le A\sqrt{\frac{\mathbb{E}_{x\sim\mathcal{D}}k_m^{\mathrm{NTK}}(x,x)}{n}}.$

## 11.5 Mean-Field Formulation
As pointed out in Section 11.4, the NTK approximation of neural networks (11.1) does not have a continuous integral formulation similar to that of the continuous random feature method (11.4), due to the $1/\sqrt{m}$ normalization in the NTK formula. The reason for this normalization is to ensure that (11.5) has a nonzero finite variance. In this section, we consider a different normalization of (11.1) (still ignoring $b_j$) as

$$f_m(x)=\frac{\alpha}{m}\sum_{j=1}^{m}u_j h(\theta_j^\mathsf{T}x), \tag{11.7}$$

with a scaling constant $\alpha>0$. We assume that $\theta_j\in\mathbb{R}^d$ and $u_j\in\mathbb{R}$. If we allow $\alpha$ to vary with $m$, and take $\alpha=\sqrt{m}$, then it leads to the NTK formulation (11.5) and (11.6). On the other hand, if we let $m\to\infty$ with $\alpha$ fixed, then we may treat $[u_j,\theta_j]$ as iid random samples from an underlying distribution $q$ on $\mathbb{R}^{d+1}$. Similar to the continuous formulation of the random feature method, this leads to a continuous formulation of two-layer neural network as $m\to\infty$:

$$f_{\mathrm{mf}}(q,x)=\alpha\mathbb{E}_{[u,\theta]\sim q}u h(\theta^\mathsf{T}x). \tag{11.8}$$

This continuous formulation is referred to as the *mean-field formulation* in Mei et al. (2018). In this formulation, the distribution $q$ on $\mathbb{R}^{d+1}$ characterizes the model, and can be trained using noisy gradient descent (see Mei et al., 2018). The finite two-layer neural network can be regarded as sampling from this distribution. In essence, this approach is a generalization of the random feature method but with the underlying random distribution trained to better fit the data, instead of using a fixed random distribution. The training of the underlying random distribution corresponds to feature learning in neural networks.

In the mean-field formulation, as $\alpha\to\infty$, the behavior of the resulting model becomes more and more similar to that of the NTK formulation. Therefore one may argue that the mean-field formulation is more general, while the NTK formulation is a limiting situation with $\alpha\to\infty$. One disadvantage of the mean-field formulation is that with standard random initialization for $[\widetilde{u},\widetilde{\theta}]$, the initial function is always 0 in the continuous limit of $m\to\infty$. This is not desirable when we train a neural network in practice. On the other hand, the advantage of the mean-field formulation is that it allows $[u, \theta]$ to move outside a small neighbor of $[\hat{u}, \hat{\theta}]$, which is consistent with feature learning in practical neural network applications.

## Convergence Analysis
It can be shown that in the continuous limit, neural network training converges to the optimal solution of the mean-field formulation (11.8), under suitable conditions (see Chizat and Bach, 2018; Mei et al., 2018). We will consider the entropy regularization model studied in Mei et al. (2018) for the mean-field formulation. It was shown in Mei et al. (2018) that for the mean-field formulation of two-layer neural networks, the Langevin algorithm converges to an entropy regularized ERM problem. In the following, we will prove this result for the continuous mean-field formulation, in which we seek a density function $q$ on $\mathbb{R}^{d+1}$ to solve the following optimization problem:

$$\min_q \left[ \frac{1}{n} \sum_{i=1}^n L\big(f_{\mathrm{mf}}(q, X_i), Y_i\big) + \mathbb{E}_{[u,\theta]\sim q} r(u,\theta) + \lambda \mathbb{E}_{[u,\theta]\sim q} \ln q([u,\theta]) \right] ,$$

where $f_{\mathrm{mf}}(q, x)$ is given by (11.8), and $r([u,\theta])$ is an appropriately chosen regularization term such as $L_2$ regularization.

In the convergence analysis, we employ a simplified notation with $w = [u,\theta] \in \mathbb{R}^{d+1}$, and take

$$p_0(w) \propto \exp(-r(w)/\lambda).$$

We thus obtain the following equivalent optimization problem:

$$q_* = \arg\min_q Q(q), \quad Q(q) = \left[ \frac{1}{n} \sum_{i=1}^n L\big(f_{\mathrm{mf}}(q, X_i), Y_i\big) + \lambda \mathrm{KL}(q||p_0) \right], \tag{11.9}$$

where

$$f_{\mathrm{mf}}(q, x) = \int \tilde{h}(w, x) q(w) dw, \qquad \tilde{h}(w, x) = \alpha u h(\theta^\top x).$$

The convergence theory of continuous two-layer neural networks to optimize (11.9) requires some knowledge on partial differential equations (PDEs). Since the required mathematical background is isolated from other parts of the book, we shall keep the discussion concise without concerning ourselves with issues such as the existence of PDE solutions. Readers who are not familiar with PDEs can skip the derivation.

In the convergence analysis, we will consider the continuous time noisy gradient descent, which can be described by a PDE. In this setting, the underlying mathematical model is to sample $m \to \infty$ neurons, each represented by an initial weight $w_0 \sim q_0$ at $t = 0$. When time $t$ increases, we move each sampled neuron, represented by a weight $w_t$ from the neuron distribution $q_t(w)$ at time $t$, using noisy gradient descent (Langevin algorithm). We assume that the moving neuron distribution of $w_t$ at time $t$ has density $q_t(w)$. Mathematically, the gradient descent method can be implemented as a stochastic partial differential equation (SDE):

$$dw_t=-\tilde g(w_t,q_t)dt+\sqrt{2\lambda\eta}\,dB_t,$$

$$\tilde g(w,q)=\frac{1}{n}\sum_{i=1}^{n}L_1'(f_m(q,X_i),Y_i)\nabla_w h(w,X_i)+\nabla r(w),$$

where $B_t$ is the standard Brownian motion and $L_1'(f,y)$ is the derivative of $L(f,y)$ with respect to $f$. The discretized version can be implemented using the SGLD algorithm (see Algorithm 7.2). It is well known that the dynamics of $q_t$ satisfy the following Fokker–Planck equation (see Pavliotis, 2014, for example):

$$\frac{\partial q_t(w)}{\partial t}=\eta\nabla_w\cdot\left[q_t(w)\nabla_w g(w,q_t)\right]. \tag{11.10}$$

where

$$g(w,q)=g_0(w,q)+\lambda\ln\frac{q(w)}{p_0(w)},\qquad g_0(w,q)=\frac{1}{n}\sum_{i=1}^{n}L_1'(f_m(q,X_i),Y_i)\tilde h(w,X_i).$$

We have the following general convergence result for (11.10).

## Theorem 11.20
Assume that $L(f,y)$ is convex in $f$. Moreover, for any density function $q'$ on $\mathbb{R}^{d+1}$, the density

$$q(w)\propto p_0(w)\exp\left(-\lambda^{-1}g_0(w,q')\right)$$

satisfies the logarithmic Sobolev inequality (LSI) with parameter $\mu>0$: for all density functions $p$ on $\mathbb{R}^{d+1}$,

$$\operatorname{KL}(p\|q)\leq\frac{1}{2\mu}\mathbb{E}_{w\sim p}\left[\left\|\nabla\ln\left(\frac{p(w)}{q(w)}\right)\right\|_2^2\right]. \tag{11.11}$$

Then we have

$$Q(q_t)\leq Q(q_*)+e^{-2\eta\lambda\mu t}[Q(q_0)-Q(q_*)].$$

**Proof** We define a density function

$$q_t'(w)\propto p_0(w)\exp\left(-\lambda^{-1}g_0(w,q_t)\right),$$

then it is easy to verify that

$$q_t'(w)\propto q_t(w)\exp\left(-\lambda^{-1}g(w,q_t)\right). \tag{11.12}$$

We have

$$\begin{aligned}
\frac{dQ(q_t)}{dt} &= \int \frac{\delta Q(q_t)}{\delta q_t}\cdot\frac{\partial q_t(w)}{\partial t}\,dw\\
&= \int g(w,q_t)\,\eta\nabla_w\cdot[q_t(w)\nabla_w g(w,q_t)]\,dw\\
&= -\eta\int \|\nabla_w g(w,q_t)\|_2^2q_t(w)\,dw\\
&= -\eta\lambda^2\int \left\|\nabla_w\ln\frac{q_t(w)}{q'_t(w)}\right\|_2^2q_t(w)\,dw\\
&\leq -\eta\lambda^2\mu\operatorname{KL}(q_t\|q'_t). \tag{11.13}
\end{aligned}$$

The first equation used calculus of variation. The second equation used (11.10), and the fact $g(w,q_t)$ may be considered as a functional gradient of $Q$ with respect to $q_t$ by treating $q_t$ as an infinite-dimensional vector indexed by $w$. The third equation used integration by parts. The fourth equation used (11.12). The last inequality used (11.11), which is satisfied by $q'_t$. Moreover,

$$\begin{aligned}
Q(q_*)-Q(q_t)&\geq\int g(w,q_t)(q_*(w)-q_t(w))\,dw+\lambda\operatorname{KL}(q_*\|q_t)\\
&\geq-\lambda\ln\mathbb{E}_{w\sim q_t}\exp\bigl(-\lambda^{-1}g(w,q_t)\bigr)-\mathbb{E}_{w\sim q_t}g(w,q_t)\\
&=-\lambda\operatorname{KL}(q_t\|q'_t). \tag{11.14}
\end{aligned}$$

The first inequality used the fact that $Q(q)-\lambda\operatorname{KL}(q\|p_0)$ is convex in $q$, and $g_0(w,q_t)$ is the functional gradient of $Q(q_t)-\lambda\operatorname{KL}(q\|p_0)$ with respect to $q$ as an infinite-dimensional vector indexed by $w$; it also used the fact that $\operatorname{KL}(q_*\|p_0)-\operatorname{KL}(q_t\|p_0)=\int\ln(q_t(w)/p_0(w))(q_*(w)-q_t(w))dw+\operatorname{KL}(q_*\|q_t)$. The second inequality used Proposition 7.16 (with $p=q_*$ and $p_0=q_t$).

Now by combining (11.13) and (11.14), we obtain

$$\frac{d[Q(q_t)-Q(q_*)]}{dt}\leq-2\eta\lambda\mu[Q(q_t)-Q(q_*)].$$

By solving the differential equation, we obtain the result.

Theorem 11.20 shows that the logarithmic Sobolev inequality (11.11) implies that the two-layer neural network in the mean-field regime converges linearly. To obtain concrete examples for which (11.11) holds, we can employ the following well-known result.

## Lemma 11.21
Let $V(w)$ be a smooth and $\lambda$-strongly convex function on $\mathbb{R}^{d+1}$, and $U(w)$ be a smooth function so that $|U(w)-V(w)|\leq M<\infty$. Then the density

$$q(w)=\frac{\exp(-U(w))}{\int\exp(-U(w))\,dw}$$

satisfies (11.11) with parameter $\mu=\lambda\exp(-2M)$.
