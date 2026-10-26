The following result shows that the expected generalization loss of $\mathcal{A}$ on $S_n$ can be bounded by the expected training loss of $\mathcal{A}$ on $S_{n+1}$. The proof is left as an exercise.

# Theorem 7.7

If an algorithm $\mathcal{A}$ is $\epsilon(\cdot,\cdot)$-leave-one-out stable, then

$\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) \le \mathbb{E}_{S_{n+1}}\mathbb{E}_{\mathcal{A}}\phi(\bar{\mathcal{A}}(S_{n+1}),S_{n+1}) + \mathbb{E}_{S_{n+1}}\frac{1}{n+1}\sum_{Z\in S_{n+1}}\epsilon(Z,S_{n+1})$

For certain problems, one can obtain more refined results using the data-dependent leave-one-out stability analysis of Theorem 7.7. We will mostly consider this approach in this chapter.

# 7.2 Regularized Empirical Risk Minimization

In this section, we consider empirical risk minimization with convex functions, and analyze its generalization using stability. Properties of convex functions that are useful for our purpose can be found in Appendix A. Additional background on convex analysis and convex optimization can be found in Rockafellar (2015) and Boyd and Vandenberghe (2004).

We can now analyze the empirical risk minimization method for convex objectives.

# Theorem 7.8

Assume that $\phi(w,z)$ is $G(z)$-Lipschitz in $w$ on a closed convex set $\Omega$. The training loss $\bar\phi(w,S_n)=\phi(w,S_n)+h(w)$ is $\lambda$ strongly convex. Then the regularized empirical risk minimization method

$\mathcal{A}(S_n)=\arg\min_{w\in\Omega}\bar\phi(w,S_n)$

is $\epsilon(Z_{n+1},S_{n+1})=G(Z_{n+1})^2/(\lambda(n+1))$ leave-one-out stable. If moreover we have $\sup_z G(z)\le G$, then it is $\epsilon=2G^2/(\lambda n)$ uniformly stable.

Assume $h(w)\ge0$, then the following expected oracle inequality holds:

$\mathbb{E}_{S_n}\phi(\mathcal{A}(S_n),\mathcal{D}) \le \inf_{w\in\Omega}[\phi(w,\mathcal{D})+h(w)] + \frac{\mathbb{E}_Z G(Z)^2}{\lambda(n+1)}$

Proof Consider $\mathcal{S}_n$ and $\mathcal{S}_{n+1}=\mathcal{S}_n\cup\{Z_{n+1}\}$. We define

$\bar\phi(w,S_{n+1})=\phi(w,S_{n+1})+\frac{n}{n+1}h(w)$

and let $\bar{\mathcal{A}}(S_{n+1})$ be its minimizer on $\Omega$. Using the optimality of $\mathcal{A}(S_n)$ and Proposition A.8, we obtain

$\nabla\bar\phi(\mathcal{A}(S_n),S_n)^\top(\bar{\mathcal{A}}(S_{n+1})-\mathcal{A}(S_n))\ge0,$ (7.4)