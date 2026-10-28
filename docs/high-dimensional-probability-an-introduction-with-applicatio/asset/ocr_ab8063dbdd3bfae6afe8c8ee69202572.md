as long as⁴ $m \gtrsim d(T)$. Since $\dim(E)= n - m$, this condition is equivalent to

$$\dim(E) + cd(T) \le n.$$

That lines up with linear algebra intuition: if $T$ is a centered Euclidean ball in some subspace $F \subset \mathbb{R}^n$, slicing can shrink the diameter of $T$ only when $\dim E + \dim F \le n$ (why?).

To practice, extend the $M^*$ bound to affine sections (Exercise 9.12), prove its high-probability version (Exercise 9.13), and compute the diameter of a random slice of the $\ell^p$ ball (Exercise 9.14).

# 9.3.2 The escape theorem

When does a random subspace $E$ miss a given set $T$ entirely with high probability? Not if $T$ contains the origin – but if $T$ lies on the unit sphere (see Figure 9.3), then it does as long as the codimension of $E$ is not too small:

**Theorem 9.3.4 (Escape theorem).** Let $T \subset S^{n-1}$ be any set, and let $A$ be an $m \times n$ matrix with independent, isotropic and subgaussian rows $A_i$. If

$$m \ge C K^4 w(T)^2, \tag{9.14}$$

then the random subspace $E = \ker A$ satisfies

$$T \cap E = \varnothing$$

with probability at least $1 - 2\exp(-c m / K^4)$. Here $K = \max_i \|A_i\|_{\psi_2}$.

Proof Let us use the high-probability version of matrix deviation inequality (see Remark 9.1.4): with probability at least $1 - 2\exp(-u^2)$, $$\sup_{x\in T} \big| \|Ax\|_2 - \sqrt{m} \big| \le C_1 K^2 (w(T) + u). \tag{9.15}$$ Suppose (9.15) occurs. If $T \cap E \ne \varnothing$, then for any $x \in T \cap E$ we have $Ax = 0$, so $$\sqrt{m} \le C_1 K^2 (w(T) + u).$$ Set $u = \sqrt{m}/(2 C_1 K^2)$ and simplify this bound to get $$\sqrt{m} \le 2 C_1 K^2 w(T),$$ which contradicts the assumption if the absolute constant $C$ is large enough. So, with that choice of $u$, the event (9.15) implies $T \cap E = \varnothing$. Done!

Now show the tightness of the escape theorem (Exercise 9.15 and prove its cousin for a point set instead of a subspace (Exercise 9.16).