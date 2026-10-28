respectively, for the non-convex and strongly convex cases. Note that, if we choose the batch-size $b \in \Omega_{\star}\left(\frac{\sigma^{2}}{\zeta}\right)$, we get$^{3}$

$$\varepsilon \in \mathcal{O}_{T, n}\left(\sqrt{\frac{\sigma^{2}}{b(n-f) T}}+\frac{f}{n} \zeta\right) \text { and } \varepsilon \in \mathcal{O}_{T, n}\left(\frac{\sigma^{2}}{b(n-f) T}+\frac{f}{n} \zeta\right),$$

respectively, for the non-convex and strongly convex cases. Finally, setting the number of iterations $T \in \Omega_{\star}\left(\frac{n^{2}}{f^{2}(n-f)} \frac{1}{\zeta^{2}}\right)$ and $T \in \Omega_{\star}\left(\frac{n}{f(n-f)} \frac{1}{\zeta}\right)$, respectively, for the non-convex and strongly convex cases, we get training error $\varepsilon \in \mathcal{O}_{\star}\left(\frac{f}{n} \zeta\right)$ in both cases. We show in the following that this training error is order optimal, in the sense that no distributed algorithm (either in a sever-based or a peer-to-peer communication topology) can yield a training error smaller than $\frac{f}{n} \zeta$ times a multiplicative factor. This claim is formally shown in Sect. 5.3.2.

# ### 5.3.2 Lower Bound on the Training Error

In this section, we analyze in Theorem 5.3 the contribution of the gradient dissimilarity $\zeta$ toward the training error of any distributed machine learning algorithm (including robust DMGD). Essentially, we show that under Assumption 4.1, the error is unavoidably $\Omega_{\star}\left(\frac{f}{n} \zeta\right)$ in the presence of $f$ adversarial nodes. However, note that the theorem does not imply a lower bound for general distributed machine learning tasks under adversarial nodes, as the assumption of uniformly bounded gradient dissimilarity (i.e., Assumption 4.1) need not hold true for many machine learning problems (see Sect. 5.4). Yet, the result is a good indicator for the suboptimality of robust DMGD (or its variants), in terms of the asymptotic training error.

**Theorem 5.3** *Suppose Assumptions 3.1, 3.2, and 4.1. Let $f>0$ and $n>2 f$. Then, a distributed algorithm is $(f, \varepsilon)$-stationary resilient only if $\varepsilon \geq \frac{f}{4 n} \zeta$.*

> *Proof* To prove the theorem, we consider a mean estimation problem, a special case of the learning problem formalized in Chap. 2, where $\mathcal{X}=\mathcal{Y}=\mathbb{R}^{d}, \Theta=\mathbb{R}^{d}$, and $h_{\boldsymbol{\theta}}(\mathbf{x})=\boldsymbol{\theta}$ for all $\mathbf{x} \in \mathbb{R}^{d}$. Given a parameter $\boldsymbol{\theta}$ and data
> 
> (continued)