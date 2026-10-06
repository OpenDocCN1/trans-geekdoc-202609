36

-C Representing Functionals

Proof Since

$1 < ||\ell||_{y^*} = \sup_{y\neq 0} \frac{|\ell(y)|}{||y||}$

there is some $\psi \neq 0$ with

$- \ell(\tilde{y}) = |\ell(\tilde{y})| > ||\tilde{y}||$.

This implies $\varphi_\ell(\tilde{y}) = \ell(\tilde{y}) + ||\tilde{y}|| < 0$, which has to be shown.

In addition to Proposition 2.4 (d), we now introduce further assumptions that guarantee the equality $\psi(0_Y) = 0$.

**Proposition 2.10** Let $\psi$ 2.1 be satisfied, and let $\psi$ be a $-C$ representing functional. If $\psi$ is positively homogeneous, i.e.,

$\psi(\lambda y) = \lambda\psi(y)$ for all $y \in Y$ and all $\lambda \geq 0$, (2.4)

or subadditive, i.e.,

$\psi(y^1 + y^2) \leq \psi(y^1) + \psi(y^2)$ for all $y^1, y^2 \in Y$, (2.5)

$\psi(0_Y) = 0$.

**Proof**

+   (a) If the functional $\psi$ is positively homogeneous, then the assertion follows from the equality (2.4) for $\lambda = 0$.

+   (b) If the functional $\psi$ is subadditive, then we get from the inequality (2.5)

$\psi(0_Y) = \psi(0_Y + 0_Y) \leq 2\psi(0_Y)$.

which implies $\psi(0_Y) \geq 0$. By Proposition 2.4 (c), we then conclude $\psi(0_Y) = 0$, which has to be shown.

Note that by Proposition 2.10 $-C$ representing sublinear functional has the property $\psi(0_Y) = 0$.

# 2.5 Directional Derivative

Directional derivatives cannot be given in general $-C$ representing functionals, of course. However, in special linear spaces and for special functionals $\psi$, this is possible. Directional derivatives can be useful in the context of optimality