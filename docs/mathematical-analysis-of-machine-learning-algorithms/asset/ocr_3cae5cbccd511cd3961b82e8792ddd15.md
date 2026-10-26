parameter, and thus the difficulty of Rademacher complexity analysis does not exist. In particular, we may directly analyze the structured-SVM loss of Example 9.32 without much difficulty using online learning (or stability analysis).

# Example 14.10

Consider the structured-SVM loss of Example 9.32, where

$$\phi(w,z)=\max_{\ell}[\gamma(y,\ell)-w^{\top}(\psi(x,y)-\psi(x,\ell))].$$

If $||\psi(x,y)-\psi(x,\ell)||_2 \le B$, then we can take $G=B$. Using Theorem 14.5, we obtain

$$\frac{1}{T}\sum_{t=1}^{T}\phi(w_{t-1},Z_t)\le\frac{1}{T}\sum_{t=1}^{T}\phi(w,Z_t)+\frac{||w_0-w||_2^2}{2\eta T}+\frac{\eta}{2}B^2.$$

By taking expectation, and using Jensen's inequality with $\lambda=1/(\eta T)$, we obtain

$$\mathbb{E}_{S_T}\mathbb{E}_{Z\sim\mathcal{D}}\phi(\hat{w},Z)\le\mathbb{E}_{Z\sim\mathcal{D}}\phi(w,Z)+\frac{\lambda}{2}||w_0-w||_2^2+\frac{1}{2\lambda T}B^2.$$

For $L_2$ regularization (or kernel methods), one can obtain a better bound using strong convexity. Observe that for regularized loss, we take

$$\ell_t(w)=\phi(w,Z_t)+\frac{\lambda}{2}||w-w_0||_2^2.\tag{14.8}$$

If $\phi(w,z)$ is convex in $w$, then $\ell_t(w)$ is $\lambda$ strongly convex.

The following result holds for strongly convex loss functions, and the specific learning rate schedule was proposed by Shalev-Shwartz et al. (2011) to solve SVMs.

# Theorem 14.11

Consider convex loss functions $\ell_t(w):\Omega\to\mathbb{R}$, which are $G$-Lipschitz (i.e. $||\nabla\ell_t(w)||_2\le G$) and $\lambda$ strongly convex. If we let $\eta_t=1/(\lambda t)>0$ in Algorithm 14.3, then for all $w\in\Omega$, we have

$$\sum_{t=1}^{T}\ell_t(w_{t-1})\le\sum_{t=1}^{T}\ell_t(w)+\frac{1+\ln T}{2\lambda}G^2.$$

Proof Similar to the proof of Theorem 14.5, we have

$$||w_t-w||_2^2\le||\tilde{w}_t-w||_2^2=||w_{t-1}-w-\eta_t\nabla\ell_t(w_{t-1})||_2^2=||w_{t-1}-w||_2^2-2\eta_t\nabla\ell_t(w_{t-1})^\top(w_{t-1}-w)+\eta_t^2||\nabla\ell_t(w_{t-1})||_2^2\le||w_{t-1}-w||_2^2+2\eta_t[\ell_t(w)-\ell_t(w_{t-1})]-\eta_t\lambda||w_{t-1}-w||_2^2+G^2\eta_t^2=(1-\lambda\eta_t)||w_{t-1}-w||_2^2+2\eta_t[\ell_t(w)-\ell_t(w_{t-1})]+G^2\eta_t^2,$$

where strong convexity is used to derive the second inequality. Note that $1-\eta_t\lambda=\eta_t/\eta_{t-1}$ and for notation convenience we take $1/\eta_0=0$. This implies that

$$\eta_t^{-1}||w_t-w||_2^2\le\eta_{t-1}^{-1}||w_{t-1}-w||_2^2+2[\ell_t(w)-\ell_t(w_{t-1})]+G^2\eta_t.$$