# Identities involving quadratic forms

One can show the following results.

$$\frac{\partial}{\partial X}(a^{\top} X b)= a b^{\top}\tag{B.47}$$ $$\frac{\partial}{\partial X}(a^{\top} X^{\top} b)= b a^{\top}\tag{B.48}$$

# Identities involving matrix trace

One can show the following results.

$$\frac{\partial}{\partial X}\operatorname{tr}(A X B)= A^{\top} B^{\top}\tag{B.49}$$ $$\frac{\partial}{\partial X}\operatorname{tr}(X^{\top} A)= A\tag{B.50}$$ $$\frac{\partial}{\partial X}\operatorname{tr}(X^{-1} A)= -X^{-\top} A^{\top} X^{-\top}\tag{B.51}$$ $$\frac{\partial}{\partial X}\operatorname{tr}(X^{\top} A X)= (A + A^{\top}) X\tag{B.52}$$

# Identities involving matrix determinant

One can show the following results.

$$\frac{\partial}{\partial X}\det(A X B)= \det(A X B) X^{-T}\tag{B.53}$$ $$\frac{\partial}{\partial X}\ln(\det(X))= X^{-T}\tag{B.54}$$

# B.4 Convexity

In this section, we introduce the concept of convexity, which plays a fundamental role in the theory and practice of optimization, as we see in Chapter 5, as well as several other areas of mathematics and statistics. It builds on several ideas from linear algebra. More details can be found in various textbooks, such as [Dah10].

# B.4.1 Convex sets

We say $\mathcal{S}$ is a convex set if, for any $x, x' \in \mathcal{S}$, we have

$$\lambda x + (1-\lambda)x' \in \mathcal{S}, \quad \forall \lambda \in [0,1]\tag{B.55}$$

That is, if we draw a line from $x$ to $x'$, all points on the line lie inside the set. See Fig. B.6 for some illustrations of convex and non-convex sets.