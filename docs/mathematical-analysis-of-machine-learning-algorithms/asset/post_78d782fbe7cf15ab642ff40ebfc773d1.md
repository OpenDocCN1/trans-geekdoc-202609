
**Proof**  LSI holds for a strongly concave density function as a direct consequence of the Bakry–Emery criterion (Bakry and Emery, 1985). It is also known that LSI is stable under a bounded perturbation (see Holley and Stroock, 1987), which implies the result.

**Example 11.22**  Lemma 11.21 implies the following result. Assume that $g_0(w,q)$ is smooth in $w$: $\|\nabla_w^2 g_0(w,q)\|_2 \le L$ for all $w$ and $q$. If we take $r(w)=\lambda'\|w\|^\alpha$, then for any $\lambda'>0$ and $\alpha>2$, (11.11) is valid for some $\mu>0$ (see Exercise 11.7). This implies that the convergence result in Theorem 11.20 holds.

### Generalization Analysis

Because the parameter $q$ of the mean-field model is a distribution, the two-layer NN in this continuous formulation can be regarded as a convex hull of the individual models $u h(\theta^\mathsf{T}x)$. We can thus apply the $L_1$-regularization result and the entropy-regularization result from Chapter 10 to compute the corresponding Rademacher complexity. The following result is identical to Proposition 11.9, except that we allow $q$ to be learned for both parameters $[u,\theta]$.

**Proposition 11.23**  *Let*

$$\mathcal{F}^{\mathrm{mf}}_A=\left\{\mathbb{E}_{[u,\theta]\sim q}u h(\theta^\mathsf{T}x):\mathbb{E}_{u\sim q}|u|\le A\right\},$$

then

$$R(\mathcal{F}^{\mathrm{mf}}_A,\mathcal{S}_n)\le AM\frac{32\sqrt{d+1}}{\sqrt{n}}.$$

Moreover, Theorem 11.20 shows that noisy gradient descent for the mean-field formulation leads to entropy regularization. We can analyze its generalization performance by using the Rademacher complexity analysis in Theorem 10.17, or by using Theorem 10.18 without assuming the boundedness of $uh(\cdot)$.

In addition to Theorem 11.20, it is also possible to prove convergence without entropy regularization under suitable conditions (see Chizat and Bach, 2018). One can study properties of the global solution of (11.8) as the limiting solution of the ERM method for two-layer neural networks. An interesting observation of the mean-field formulation (11.8) without entropy regularization is that any convex regularization in $u$ leads to $L_1$ regularization, which implies that Proposition 11.23 can be directly applied for the solution of the mean-field formulation.

**Proposition 11.24**  *Consider an arbitrary distribution* $\widehat{D}$ *on* $\mathcal{X}\times\mathcal{Y}$. *Assume that* $\sup\{|h(\theta^\mathsf{T}x)|:\theta\in\Omega\}$ *is bounded. Let* $\Delta(\mathbb{R}\times\Omega)$ *be the set of probability measures on* $(u,\theta)\in\mathbb{R}\times\Omega$. *Consider the following optimization problem:*

$$\min_{q\in\Delta(\mathbb{R}\times\Omega)}\ \mathbb{E}_{(X,Y)\sim\widehat{D}}\left[L\left(\mathbb{E}_{[u,\theta]\sim q}u h(\theta^\mathsf{T}X),Y\right)+\mathbb{E}_{u\sim q}r(|u|)\right].$$

*where $r(\cdot)$ is an increasing and strictly convex function on $\mathbb{R}_+$. Let $\hat{q}$ be an optimal solution. Then there exists $A > 0$ such that $|u| = A$ a.e. $u \sim \hat{q}(\cdot)$, and $\hat{q}$ is a solution to*

$$\min_{q\in\Delta(\mathbb{R}\times\Omega)} \mathbb{E}_{(X,Y)\sim\widehat{D}} L\left( \mathbb{E}_{[u,\theta]\sim q} u h(\theta^\top X), Y\right) \quad \text{subject to} \quad \mathbb{E}_{u\sim q}|u| \le A.$$

**Proof**  For notation simplicity, we consider discrete $\hat{q}$ (the continuous case is analogous except for more complex notations). Consider discrete values of $[u_1,\theta_1]$ with probability $\hat{q}_1 > 0$ and $[u_2,\theta_2]$ with probability $\hat{q}_2 > 0$. Without loss of generality, we may assume that $|u_1| \ge |u_2| \ge 0$.

We prove the first statement by contradiction. If $|u_1| > |u_2|$, then we can find $\delta > 0$, and let $\hat{q}_1' = \hat{q}_1 + \delta$, $\hat{q}_2' = \hat{q}_2 - \delta$, so that $|u_1'| = |u_2'|$ with $u_1' = u_1 \hat{q}_1/\hat{q}_1'$ and $u_2' = u_2 \hat{q}_2/\hat{q}_2'$. Let $\hat{q}'$ be the distribution on $[u,\theta]$ which equals $\hat{q}$ on all other points, except for a change of probability mass $\hat{q}_j$ on $[u_j,\theta_j]$ to a probability mass $\hat{q}_j'$ on $[u_j',\theta_j]$ $(j = 1,2)$. The construction implies that $\mathbb{E}_{[u',\theta]\sim\hat{q}'} u' h(\theta^\top x) = \mathbb{E}_{[u,\theta]\sim\hat{q}} u h(\theta^\top x)$ and

$$\mathbb{E}_{u'\sim\hat{q}'} r(|u'|) - \mathbb{E}_{u\sim\hat{q}} r(|u|) = (\hat{q}_1 + \hat{q}_2) r\left( \frac{\hat{q}_1|u_1| + \hat{q}_2|u_2|}{\hat{q}_1 + \hat{q}_2} \right) - \sum_{j=1}^2 \hat{q}_j r(|u_j|) < 0,$$

where we used $|u_1'| = |u_2'| = (\hat{q}_1|u_1| + \hat{q}_2|u_2|)/(\hat{q}_1 + \hat{q}_2)$. This is a contradiction to the optimality of $\hat{q}$. Therefore we must have $|u_1| = |u_2|$. This implies that $|u| = \mathrm{const}$ when $u \sim \hat{q}(\cdot)$.

We prove the second statement by contradiction. If $\hat{q}$ is not a solution of the $L_1$ regularization formulation, then we can find $\hat{q}'$ with a smaller objective value so that $\mathbb{E}_{u'\sim\hat{q}'} |u'| \le A$. From the previous analysis, we can also find a solution $\hat{q}'$ such that $|u'| = A'$ for some $A' \le A$ with a smaller objective value. However, this is not possible because $\hat{q}'$ would lead to a smaller regularized loss than that of $\hat{q}$ with respect to the $r(\cdot)$ regularization formulation.

Proposition 11.24 can be interpreted as follows. Even if we use $L_2$ regularization on $u$ in a two-layer neural network, which seemingly is related to the kernel method, it effectively solves an $L_1$ regularization problem for the mean-field formulation, when we allow both $u$ and $\theta$ to be optimized simultaneously. The optimization of $\theta$ modifies the $L_2$ regularization on $u$ into the $L_1$ regularization with respect to the function class $\{h(\theta^\top x)\}$. This means Proposition 11.23 can be used to characterize the complexity of the mean-field formulation.

In the discrete mean-field formulation (11.7), $\{[u_j,\theta_j]\}$ may be regarded as $m$ independent samples from $q$. In such a formulation, $[u_j,\theta_j]$ are trained simultaneously. The following result shows that with $L_1$ regularization, the Rademacher complexity is insensitive to $m$.

**Corollary 11.25**  Let

$$\mathcal{F}_{A,m}^{\mathrm{mf}} = \left\{ \frac{1}{m} \sum_{j=1}^m u_j h(\theta_j^\top x) : \|u\|_1 \le mA \right\}.$$

Assume that $h(\cdot) \in [-M, M]$ and $h(\cdot)$ is monotone. Then

$$R(\mathcal{F}_{A,m}^{\mathrm{mf}}, \mathcal{S}_n) \le A M \frac{32\sqrt{d+1}}{\sqrt{n}}.$$

Note that unlike Corollary 11.10, where $\{\theta_j\}$ are random, Corollary 11.25 allows $\{\theta_j\}$ to be trained together with $\{u_j\}$. This means that it is more effective in learning the correct feature representation using a small $m$.

## 11.6 Analysis of Deep Neural Networks

It is possible to extend the NTK analysis to deep neural networks using an extension of the linear approximation (11.6) for two-layer neural networks without too much difficulty. We will not consider it here for simplicity. It has similar flaws as the kernel approaches for random features and for two-layer neural networks, in that the linearization requires model parameters to be restricted in a small region around the initialization.

An additional disadvantage of the NTK approximation is that it can be regarded as a shallow network approximation of a deep network using a linear model. According to Theorem 11.4, highly oscillating functions with large crossing numbers cannot be approximated efficiently with NTK, although they can be well approximated using deep neural networks. This is related to the fact that NTK cannot learn features efficiently. However, the efficient learning of feature representation is the key advantage of deep neural networks. Therefore in this section we will investigate the deep neural network method directly without considering the NTK approximation.

Here we consider a formulation of deep neural networks which may be considered as an extension of the mean-field formulation of two-layer neural networks, and then investigate its generalization. The deep function class is defined recursively as follows:

$\mathcal{F}^{(1)} = \{\theta^\top x : \theta \in \Theta\}$,

and for $k = 2, \dots, K$, using the notation of Section 10.2, we define

$$\mathcal{F}^{(k)} = \mathcal{F}_{A_k, L_1} \big(h \circ \mathcal{F}^{(k-1)}\big) \tag{11.15}$$

$$= \left\{ \sum_{j=1}^m w_j h\big(f_j(x)\big) : \|w\|_1 \le A_k,\ f_j \in \mathcal{F}^{(k-1)},\ m > 0 \right\}.$$

When $A_1, \dots, A_k$ are sufficiently large, then it is clear that any function $f(x)$ that can be represented by a deep $K$-layer neural network that belongs to $\mathcal{F}^{(K)}$. The representation allows an arbitrary large $m$, and thus can handle continuous deep neural networks. This implies that it can be regarded as an extension of the two-layer mean-field formulation, which, as we have shown, also employs $L_1$-regularization implicitly.
