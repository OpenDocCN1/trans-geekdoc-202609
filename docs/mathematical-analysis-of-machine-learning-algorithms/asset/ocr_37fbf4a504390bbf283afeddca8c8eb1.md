which is similar to the random feature method (11.3), but $\tilde{w}_j$ is also drawn randomly. Note that in practice, we often choose $\mu$ to be a normal distribution with a diagonal covariance matrix. We do not make this assumption unless specified explicitly. However, to simplify the computation, throughout the section, we assume that $\mu$ is chosen so that

$$\mathbb{E}[\tilde{u}_j\mid\tilde{\theta}_j]=0.$$

Given $x\in\mathbb{R}^d$, the variance of $\tilde{f}^{\mathrm{NTK}}_m(x)$ is

$$\operatorname{Var}_{\mu}\bigl(\tilde{f}^{\mathrm{NTK}}_m(x)\bigr)=\mathbb{E}_{[\tilde{u}_0,\tilde{\theta}_0]\sim\mu}\left[\tilde{u}_0^2h(\tilde{\theta}_0^\top x)^2\right].$$

This implies that the variance is finite when the right-hand side is finite. Moreover, the variance is independent of $m$ as $m\to\infty$. This explains why we divide by $\sqrt{m}$ instead of dividing by $m$ as in (11.3). Because of this normalization difference, we cannot obtain an explicit integration formulation similar to (11.4) for $\tilde{f}^{\mathrm{NTK}}_m(x)$ as $m\to\infty$. Nevertheless, we have the following limiting behavior of $\tilde{f}_m$ using the central limit theorem. This means that the $m\to\infty$ limit of the NTK initialization converges to a well-behaved random function as $m\to\infty$.

**Proposition 11.12**  *Assume that the central limit theorem holds for (11.5) (uniformly for all $x$) as $m\to\infty$. Then as $m\to\infty$, $\tilde{f}^{\mathrm{NTK}}_m(x)$ converges to a Gaussian process $\tilde{f}^{\mathrm{NTK}}_\infty(x)$ with zero-mean and covariance matrix,*

$$k(x,x')=\mathbb{E}_{[\tilde{u}_0,\tilde{\theta}_0]\sim\mu}\left[\tilde{u}_0^2h(\tilde{\theta}_0^\top x)h(\tilde{\theta}_0^\top x')\right].$$

In general, neural networks are trained via SGD (see Algorithm 7.1), which employs gradients of the neural network. We have the following characterization of gradients at the NTK initialization.

**Proposition 11.13**  *Consider $\tilde{f}^{\mathrm{NTK}}_m(x)$ defined in (11.5). Let $h'(z)$ be the derivative of $h(\cdot)$. We have for all $x$ and $j$,*

$$\mathbb{E}\left[\left\|\nabla_{\tilde{u}_j}\tilde{f}^{\mathrm{NTK}}_m(x)\right\|_2^2\right]=\frac{1}{m}\mathbb{E}_{\tilde{\theta}_0\sim\mu}\left[h(\tilde{\theta}_0^\top x)^2\right],$$

$$\mathbb{E}\left[\left\|\nabla_{\tilde{\theta}_j}\tilde{f}^{\mathrm{NTK}}_m(x)\right\|_2^2\right]=\frac{1}{m}\mathbb{E}_{[\tilde{u}_0,\tilde{\theta}_0]\sim\mu}\left[\tilde{u}_0^2h'(\tilde{\theta}_0^\top x)^2\right]\|x\|_2^2,$$

*where the expectation is with respect to the random initialization. Moreover, for any $x$, as $m\to\infty$, *

$$\left\|\nabla_{\tilde{u}}\tilde{f}^{\mathrm{NTK}}_m(x)\right\|_2^2\xrightarrow{p}\mathbb{E}_{\tilde{\theta}_0\sim\mu}\left[h(\tilde{\theta}_0^\top x)^2\right],$$

$$\left\|\nabla_{\tilde{\theta}}\tilde{f}^{\mathrm{NTK}}_m(x)\right\|_2^2\xrightarrow{p}\mathbb{E}_{[\tilde{u}_0,\tilde{\theta}_0]\sim\mu}\left[\tilde{u}_0^2h'(\tilde{\theta}_0^\top x)^2\right]\|x\|_2^2,$$

*where the probability is with respect to the random initialization.*

Proposition 11.13 shows that as $m\to\infty$, the gradient $g$ of the NTK formulation has small $L_\infty$-norm: $\|g\|_\infty\to 0$, although the $L_2$-norm is finite: $\|g\|_2=O(1)$. We note that the progress of the SGD procedure is measured by the gradient 2-norm (e.g. see Theorem 14.9). Therefore in the NTK formulation, the convergence of