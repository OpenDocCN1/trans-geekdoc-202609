
## Theorem 14.5
*Let $\{\ell_t(w): w\in\Omega\}$ be a sequence of real-valued convex loss functions defined on a convex set $\Omega$. Assume that all $\ell_t(w)$ are $G$-Lipschitz (i.e. $\|\nabla\ell_t(w)\|_2\le G$). If we let $\eta_t=\eta>0$ be a constant in Algorithm 14.3. Then for all $w\in\Omega$, we have*

$$\sum_{t=1}^{T}\ell_t(w_{t-1})\le\sum_{t=1}^{T}\ell_t(w)+\frac{\|w_0-w\|_2^2}{2\eta}+\frac{\eta T}{2}G^2.$$

*Proof*  We have the following inequality:

$$\begin{aligned}
\|\tilde w_t-w\|_2^2
&=\|w_{t-1}-w-\eta\nabla\ell_t(w_{t-1})\|_2^2\\
&=\|w_{t-1}-w\|_2^2-2\eta\nabla\ell_t(w_{t-1})^{\mathsf T}(w_{t-1}-w)+\eta^2\|\nabla\ell_t(w_{t-1})\|_2^2\\
&\le\|w_{t-1}-w\|_2^2-2\eta\nabla\ell_t(w_{t-1})^{\mathsf T}(w_{t-1}-w)+G^2\eta^2\\
&\le\|w_{t-1}-w\|_2^2-2\eta[\ell_t(w_{t-1})-\ell_t(w)]+G^2\eta^2,
\end{aligned}$$

where the first inequality used the Lipschitz condition, and the second inequality used the convexity condition.

Since $w_t\in\Omega$ is the projection of $\tilde w_t$ onto $\Omega$ and $w\in\Omega$, we also have

$$\|w_t-w\|_2^2\le\|\tilde w_t-w\|_2^2.$$

Therefore, we have

$$\|w_t-w\|_2^2\le\|w_{t-1}-w\|_2^2-2\eta[\ell_t(w_{t-1})-\ell_t(w)]+G^2\eta^2.$$

Now we may sum over $t=1$ to $t=T$, and obtain

$$\|w_T-w\|_2^2\le\|w_0-w\|_2^2-2\eta\sum_{t=1}^{T}[\ell_t(w_{t-1})-\ell_t(w)]+TG^2\eta^2.$$

Rearrange the terms and we obtain the desired bound. $\square$

The analysis technique of Theorem 14.5 is quite similar to that of the perceptron mistake bound. In fact, we may state the following more general result which includes both online convex optimization and perceptron mistake analysis as special cases. We leave its proof as an exercise.

## Theorem 14.6
*Consider Algorithm 14.5 with the update rule replaced by the following method:*

$$\tilde w_t=w_{t-1}-\eta_tg_t.$$

If we can choose $g_t$ so that

$$g_t^{\mathsf T}(w-w_{t-1})\le\tilde\ell_t(w)-\ell_t(w_{t-1}),$$

then

$$\sum_{t=1}^{T}\ell_t(w_{t-1})\le\sum_{t=1}^{T}\tilde\ell_t(w)+\frac{\|w_0-w\|_2^2}{2\eta}+\frac{\eta T}{2}G^2.$$

Note that in Theorem 14.6, $\ell_t(w_{t-1})$ may not necessarily be a convex function of $w_{t-1}$.

### Example 14.7
Theorem 14.5 is a special case of Theorem 14.6 by taking $\tilde{\ell}_t(w)=\ell_t(w)$ and $g_t=\nabla\ell_t(w_{t-1})$.

### Example 14.8
When $w_{t-1}^{\top}X_tY_t\le 0$, we have

$$-(w-w_{t-1})^{\top}X_tY_t\le \gamma-w^{\top}X_tY_t-\gamma$$
$$\le \max(0,\gamma-w^{\top}X_tY_t)-\gamma\mathbf{1}(w_{t-1}^{\top}X_tY_t\le 0).$$

When $w_{t-1}^{\top}X_tY_t>0$, we have

$$0\le \max(0,\gamma-w^{\top}X_tY_t)-\gamma\mathbf{1}(w_{t-1}^{\top}X_tY_t\le 0).$$

Therefore let $g_t=-\mathbf{1}(w_{t-1}^{\top}X_tY_t\le 0)X_tY_t$, then

$$(w-w_{t-1})^{\top}g_t\le \max(0,\gamma-w^{\top}X_tY_t)-\gamma\mathbf{1}(w_{t-1}^{\top}X_tY_t\le 0).$$

This implies that Theorem 14.1 is a special case of Theorem 14.6 by taking $\tilde{\ell}_t(w)=\max(0,\gamma-w^{\top}X_tY_t)$ and $\ell_t(w_{t-1})=\gamma\mathbf{1}(w_{t-1}^{\top}X_tY_t\le 0)$.

We may also obtain an oracle inequality for Algorithm 14.3 as follows.

## Theorem 14.9
*Consider loss function* $\phi(w,Z)\in[0,M]$ *with* $Z\sim\mathcal{D}$, *and* $w\in\Omega$, *where* $\Omega$ *is a convex set. Assume that* $\phi(w,Z)$ *is convex and* $G$-*Lipschitz with respect to* $w$. *Let* $[Z_1,\ldots,Z_T]\sim\mathcal{D}^T$ *be independent samples, and consider* $\hat{w}$ *obtained from Algorithm 14.3, with* $\ell_i(w)=\phi(w,Z_i)$ *and* $\eta_t=\eta>0$. *Then with probability at least* $1-\delta$,

$$\mathbb{E}_{Z\sim\mathcal{D}}\phi(\hat{w},Z)\le \inf_{w\in\Omega}\left[\mathbb{E}_{Z\sim\mathcal{D}}\phi(w,Z)+\frac{1}{2\eta T}\|w-w_0\|_2^2\right]+\frac{\eta}{2}G^2+M\sqrt{\frac{2\ln(2/\delta)}{T}}.$$

*Proof*  Note that the convexity and Jensen’s inequality imply

$$\mathbb{E}_{Z\sim\mathcal{D}}\phi(\hat{w},Z)\le \frac{1}{T}\sum_{t=1}^{T}\mathbb{E}_{Z_t}\phi(w_{t-1},Z_t). \tag{14.4}$$

Moreover, using Azuma’s inequality, we have with probability at least $1-\delta/2$,

$$\frac{1}{T}\sum_{t=1}^{T}\mathbb{E}_{Z_t}\phi(w_{t-1},Z_t)\le \frac{1}{T}\sum_{t=1}^{T}\phi(w_{t-1},Z_t)+M\sqrt{\frac{\ln(2/\delta)}{2T}}. \tag{14.5}$$

Using Theorem 14.5, we obtain

$$\frac{1}{T}\sum_{t=1}^{T}\phi(w_{t-1},Z_t)\le \frac{1}{T}\sum_{t=1}^{T}\phi(w,Z_t)+\frac{\|w_0-w\|_2^2}{2\eta T}+\frac{\eta}{2}G^2. \tag{14.6}$$

Using the Chernoff bound, we have with probability at least $1-\delta/2$,

$$\frac{1}{T}\sum_{t=1}^{T}\phi(w,Z_t)\le \mathbb{E}_{Z\sim\mathcal{D}}\phi(w,Z)+M\sqrt{\frac{\ln(2/\delta)}{2T}}. \tag{14.7}$$

By taking the union bound, and combining the four inequalities, we obtain the following. With probability at least $1 - \delta$,

\begin{align*}
\mathbb{E}_{Z\sim\mathcal{D}}\phi(\hat{w}, Z) &\le \frac{1}{T}\sum_{t=1}^{T}\mathbb{E}_{Z_t}\phi(w_{t-1}, Z_t) \\
&\le \frac{1}{T}\sum_{t=1}^{T}\phi(w_{t-1}, Z_t) + M\sqrt{\frac{\ln(2/\delta)}{2T}} \\
&\le \frac{1}{T}\sum_{t=1}^{T}\phi(w, Z_t) + \frac{\|w_0 - w\|_2^2}{2\eta T} + \frac{\eta}{2}G^2 + M\sqrt{\frac{\ln(2/\delta)}{2T}} \\
&\le \mathbb{E}_{Z\sim\mathcal{D}}\phi(w, Z) + \frac{\|w_0 - w\|_2^2}{2\eta T} + \frac{\eta}{2}G^2 + M\sqrt{\frac{2\ln(2/\delta)}{T}}.
\end{align*}

The first inequality used (14.4). The second inequality used (14.5). The third inequality used (14.6). The last inequality used (14.7).

If we take $\eta = O(1/\sqrt{T})$, then we obtain a convergence result of $O(1/\sqrt{T})$ in Theorem 14.9. This result can be compared to that of Corollary 9.27, which has a similar convergence rate if we set $\lambda = 1/(\eta T)$.

In Corollary 9.27, the loss function does not have to be convex, and the theorem applies to ERM, which implies the following bound for the ERM estimator:

\begin{align*}
\mathbb{E}_{\mathcal{D}}\phi(\hat{w}, Z) &\le \mathbb{E}_{\mathcal{D}}\phi(w, Z) + \lambda\|w\|_2^2 \\
&+ O\left(\sqrt{\frac{\ln((\lambda + B^2)/(\delta\lambda))}{n}}\right) + O\left(\frac{B^2\ln((\lambda + B^2)/(\delta\lambda))}{\lambda n}\right).
\end{align*}

This result is similar to that of Theorem 14.9 with $\eta = 1/(\lambda T)$.

However, the result in Theorem 14.9 does not apply to ERM, but rather the specific online learning procedure for convex functions described in Algorithm 14.3. We note that the definitions of Lipschitz constants are different, with $G \le \gamma B$, where $\gamma$ is the Lipschitz of the loss function, and $B = \sup\{\|X\|_2\}$. In addition, one may regard the regret bound in the online learning analysis as an analogy of the Rademacher complexity bound for ERM estimator. Azuma's inequality is the counterpart of McDiarmid's inequality to obtain the concentration results.

The techniques used in online learning analysis are closely related to the stability analysis of Chapter 7. In fact, these two techniques often lead to similar results. Stability analysis has the advantage of allowing the computational procedure (SGD) to go through the data more than once, while the online to batch conversion technique only allows the computational procedure (online algorithm) to go through the training data once.

For vector-valued functions, the Rademacher complexity analysis is trickier unless one works with covering numbers. This is due to the fact that the corresponding comparison lemma based on the Lipschitz loss assumption may depend on the dimensionality of the vector function, as discussed in Section 9.4. However, the Lipschitz parameter of $\phi(w,\cdot)$ in Theorem 14.9 is with respect to the model parameter, and thus the difficulty of Rademacher complexity analysis does not exist. In particular, we may directly analyze the structured-SVM loss of Example 9.32 without much difficulty using online learning (or stability analysis).

### Example 14.10
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

## Theorem 14.11
Consider convex loss functions $\ell_t(w):\Omega\to\mathbb{R}$, which are $G$-Lipschitz (i.e. $||\nabla\ell_t(w)||_2\le G$) and $\lambda$ strongly convex. If we let $\eta_t=1/(\lambda t)>0$ in Algorithm 14.3, then for all $w\in\Omega$, we have

$$\sum_{t=1}^{T}\ell_t(w_{t-1})\le\sum_{t=1}^{T}\ell_t(w)+\frac{1+\ln T}{2\lambda}G^2.$$$

Proof Similar to the proof of Theorem 14.5, we have

$$||w_t-w||_2^2\le||\tilde{w}_t-w||_2^2=||w_{t-1}-w-\eta_t\nabla\ell_t(w_{t-1})||_2^2=||w_{t-1}-w||_2^2-2\eta_t\nabla\ell_t(w_{t-1})^\top(w_{t-1}-w)+\eta_t^2||\nabla\ell_t(w_{t-1})||_2^2\le||w_{t-1}-w||_2^2+2\eta_t[\ell_t(w)-\ell_t(w_{t-1})]-\eta_t\lambda||w_{t-1}-w||_2^2+G^2\eta_t^2=(1-\lambda\eta_t)||w_{t-1}-w||_2^2+2\eta_t[\ell_t(w)-\ell_t(w_{t-1})]+G^2\eta_t^2,$$

where strong convexity is used to derive the second inequality. Note that $1-\eta_t\lambda=\eta_t/\eta_{t-1}$ and for notation convenience we take $1/\eta_0=0$. This implies that

$$\eta_t^{-1}||w_t-w||_2^2\le\eta_{t-1}^{-1}||w_{t-1}-w||_2^2+2[\ell_t(w)-\ell_t(w_{t-1})]+G^2\eta_t.$$
