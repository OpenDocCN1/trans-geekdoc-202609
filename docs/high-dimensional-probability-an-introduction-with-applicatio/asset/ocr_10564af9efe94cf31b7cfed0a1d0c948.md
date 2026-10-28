proof works. We will first prove a discrete version using dyadic scales $\varepsilon=2^{-k}$ (like a Riemann sum), then move to the continuous version.

# **Theorem 8.1.4 (Discrete Dudley inequality).** Let $(X_t)_{t\in T}$ be a mean-zero random process on a metric space $(T,d)$ with subgaussian increments as in (8.1). Then

$\displaystyle \mathbb{E}\sup_{t\in T}X_t\le CK\sum_{k\in\mathbb{Z}}2^{-k}\sqrt{\log\mathcal{N}(T,d,2^{-k})}. \tag{8.2}$

The proof uses the important technique of *chaining*. It is basically a multi-scale version of the $\varepsilon$-net argument we have used before, like in the proofs of Theorems 4.4.3 and 7.6.1.

In the $\varepsilon$-net argument, we approximate $T$ by an $\varepsilon$-net $\mathcal{N}$ so every point $t\in T$ is close to some $\pi(t)\in\mathcal{N}$, with $d(t,\pi(t))\le\varepsilon$. Then the increment condition (8.1) gives

$\displaystyle \|X_t-X_{\pi(t)}\|_{\psi_2}\le K\varepsilon. \tag{8.3}$

This leads to

$\displaystyle \mathbb{E}\sup_{t\in T}X_t\le \mathbb{E}\sup_{t\in T}X_{\pi(t)}+\mathbb{E}\sup_{t\in T}(X_t-X_{\pi(t)}).$

We can handle the first term via a union bound over $|\mathcal{N}|=\mathcal{N}(T,d,\varepsilon)$ points $\pi(t)$. But the second term is tricky — it is not clear how to combine (8.3) with a union bound over all $t\in T$. To fix this, we don’t stop at one net, but we choose smaller and smaller $\varepsilon$ to get better approximations $\pi_1(t),\pi_2(t),\ldots$ to $t$ with finer nets. That is the idea behind *chaining*, which we will now formalize.

*Proof of Theorem 8.1.4.* **Step 1: Chaining set-up.** Without loss of generality, we may assume that $K=1$ (why?) and $T$ is finite (see Remark 7.2.1). Define the dyadic scale

$\displaystyle \varepsilon_k=2^{-k},\qquad k\in\mathbb{Z}. \tag{8.4}$

and choose $\varepsilon_k$-nets $T_k$ of $T$ so that

$\displaystyle |T_k|=\mathcal{N}(T,d,\varepsilon_k). \tag{8.5}$

Only a part of the dyadic scale will be needed. Since $T$ is finite, there exists a small enough number $\kappa\in\mathbb{Z}$ (defining the coarsest net) and a large enough number $K\in\mathbb{Z}$ (defining the finest net), such that

$\displaystyle T_\kappa=\{t_0\}\text{ for some }t_0\in T,\qquad T_K=T. \tag{8.6}$

For a point $t\in T$, let $\pi_k(t)$ denote a closest point in $T_k$, so we have

$\displaystyle d(t,\pi_k(t))\le\varepsilon_k. \tag{8.7}$

Since $\mathbb{E}X_{t_0}=0$ by assumption, we have

$\displaystyle \mathbb{E}\sup_{t\in T}X_t=\mathbb{E}\sup_{t\in T}(X_t-X_{t_0}).$