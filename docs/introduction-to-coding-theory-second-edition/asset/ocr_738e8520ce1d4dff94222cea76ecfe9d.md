# 15.17 Definition.

For every element $z = (z_1, z_2, \dots, z_n) \in V$, consider the function $\phi_z \in L^2(V)$ defined by

$$\phi_z(x) = \zeta^{x \cdot z}.$$

The $\phi_z$ are known as the **characters** of the group $V$. Here $\zeta$ is a primitive complex $v$-th root of unity, which will be fixed throughout the discussion, and $x \cdot z$ denotes the standard dot product.

The characters form an orthonormal basis of the $g$-dimensional complex vector space $L^2(V)$.

# 15.18 Definition.

Let $f \in L^2(V)$. Express $f$ in terms of the characters in the form

$$f = \sum_{z \in V} \hat f(z) \phi_z.$$

The complex numbers $\hat f(z)$ are known as the **Fourier coefficients** of $f$. The **Fourier transform** of $f$ is the function $\hat f$, which has value $\hat f(z)$ at $z$.

Because of the orthonormality of the characters, the Fourier coefficients are given by

$$\hat f(z) = \langle f, \phi_z \rangle = \frac{1}{g} \sum_{x \in V} f(x) \zeta^{-x \cdot z}. \tag{15.6}$$

The objects we are primarily interested in, codes or orthogonal arrays, consist of $n$-tuples with entries in the alphabet $E$. They can therefore be identified with their characteristic functions:

# 15.19 Definition.

Let $\mathcal{A}$ be an array with $n$ columns and entries in the $v$-set $E$. The characteristic function $f(x) = \chi_{\mathcal{A}}(x)$ counts with which multiplicity $x \in E^n$ occurs as a row of $\mathcal{A}$. We define the Fourier transform $\hat{\mathcal{A}}(z)$ of $\mathcal{A}$ by identifying $\mathcal{A}$ with its characteristic function and applying Definition 15.18.

We will prove a close link between the Fourier coefficients and the strength of an array. If $\mathcal{A}$ has strength $t$, then $\hat{\mathcal{A}}(z) = 0$ for every $0 \neq z \in G$ of weight $wt(z) \le t$. This follows from the definition of an orthogonal array and the fact that the sum of all powers of a root of unity vanishes. The converse is also true, as the condition $\hat{\mathcal{A}}(z) = 0$ for all $0 \neq z \in G$ defines a one-dimensional subspace of $L^2(G)$, the constant functions.

# 15.20 Theorem.

The following are equivalent for each array $\mathcal{A} \subseteq G = E^n$ and each subset $D$ of coordinate positions:

+   - $\hat{\mathcal{A}}(z) = 0$ for all $0 \neq z \in V$ such that $\operatorname{supp}(z) \subseteq D$.
+   - The projection of $\mathcal{A}$ to $D$ is uniformly distributed.

In particular, $\mathcal{A}$ has strength $t$ if and only if the Fourier coefficients with respect to all nonzero vectors $z$ of weight at most $t$ vanish.