of uniform convergence complexity. We also allow distribution dependent offset in the definition of offset Rademacher complexity.

The following result shows that for some cases, offset Rademacher complexity can be obtained easily for some function classes.

# Example 6.12

Consider a function class $\mathcal{F} = \{f(w,x)=w^\top \psi(x): w \in \mathbb{R}^d\}$, consisting of linear functions. Let $h(w)=h_0(w)=0.5\lambda\|w\|_2^2$. Then for any $\mathcal{S}_n$, we have

$R^h(\mathcal{F},\mathcal{S}_n)=\mathbb{E}_\sigma \sup_{w\in\mathbb{R}^d}\left[\frac{1}{n}\sum_{i=1}^n \sigma_i w^\top \psi(X_i)-\frac{\lambda}{4}\|w\|_2^2\right]$

$=\frac{1}{\lambda}\mathbb{E}_\sigma\left\|\frac{1}{n}\sum_{i=1}^n \sigma_i \psi(X_i)\right\|_2^2 = \frac{1}{\lambda n^2}\sum_{i=1}^n \|\psi(X_i)\|_2^2.$

Let $\mathcal{F}_{A,B}=\{\{f(w,x)=w^\top \psi(x): \|w\|_2 \le A, \|\psi(x)\|_2 \le B\}\}$. Then, for any $\lambda$,

$R(\mathcal{F}_{A,B},\mathcal{S}_n) \le R^h(\mathcal{F},\mathcal{S}_n)+\frac{\lambda}{4}A^2 \le \frac{B^2}{\lambda n}+\frac{\lambda}{4}A^2.$

By optimizing over $\lambda$, we obtain

$R(\mathcal{F}_{A,B},\mathcal{S}_n) \le AB/\sqrt{n}.$

The following example illustrates that offset Rademacher complexity can lead to a result analogous to the multiplicative form of the Chernoff bound.

# Example 6.13

Consider a (binary-valued) VC class $\mathcal{G}$ such that $\mathrm{vc}(\mathcal{G})=d$. Consider $n \ge d$, and let $h(f,\mathcal{S}_n)=h_1(f,\mathcal{S}_n)=(\gamma/n)\sum_{i=1}^n f(Z_i)$. Then Sauer's lemma implies that for any $\mathcal{S}_n$, the number of functions of $\phi \in \mathcal{G}$ on $\mathcal{S}_n$ is no more than $(en/d)^d$. We thus obtain (see Theorem 6.23)

$R^h(\mathcal{G},\mathcal{S}_n) \le \frac{(1+0.5\gamma)^2 d \ln(en/d)}{\gamma n}.$

This result can be compared to the standard Rademacher complexity result in Example 6.5, which leads to an additive expected generalization bound.

The following result is a generalization of Theorem 6.4.

# Theorem 6.14

Consider offset function of (6.3). We have $\epsilon_n^h(\mathcal{G},\mathcal{D}) \le 2R_n^h(\mathcal{G},\mathcal{D}).$

Consequently, the approximate regularized ERM method of (6.1) satisfies $\mathbb{E}_{\mathcal{S}_n}\phi(\hat{w},\mathcal{D}) \le \inf_{w\in\Omega}[\phi(w,\mathcal{D})+\mathbb{E}_{\mathcal{S}_n}h(w,\mathcal{S}_n)]+\epsilon'+2R_n^h(\mathcal{G},\mathcal{D}).$

Proof Let $\mathcal{S}'_n=\{Z'_1,\dots,Z'_n\}\sim\mathcal{D}^n$ be $n$ iid samples from $\mathcal{D}$ that are independent of $\mathcal{S}_n$. We have