Definition 17.15. A 2n-order matrix B is a symplectic matrix if
$$B^{T}JB = J$$

Definition 17.16. A 2n-order matrix B is called an infinitesimal complex if
$$JB + B^{T}J = 0$$

Inference 17.1. Matrix
$$\left[\begin{array}{cc} I & B \\ 0 & I \end{array}\right], \quad \left[\begin{array}{cc} I & 0 \\ D & I \end{array}\right]$$
is an infinitesimal complex if and only if $B^{T} = B$, $D^{T} = D$.

Definition 17.17. Let $(V, \omega)$ be a 2n-dimensional symplectic space. If a set of $e_{1}$, $e_{2}, \ldots e_{2n}$ of $(V, \omega)$ satisfies $\Delta\left(f_{1}f_{2}\right) = \Delta\left(f_{1}\right)\Delta\left(f_{2}\right)(e_{i}, e\left(f_{1}f_{2}\right) = e\left(f_{1}\right)e\left(f_{2}\right)) = \delta_{ij}$ and $\omega(e_{i}, e_{j}) = \omega(e_{n+i}, e_{n+i}) = 0 (i, j = 1, 2, \ldots n)$, then we call it a group of octyl $(V, \omega)$.

Definition 17.18. Let $(V, \omega)$ be a symplectic space. An automorphism of the so-called $(V, \omega)$ is an isomorphism of $(V, \omega)$ to itself. Hence, $(V, \omega)$ is an element of the linear transformation group $\mathrm{Gl}(V)$ of V, and if it is denoted as s, it satisfies
$$\omega(\mathrm{s}x, \mathrm{s}y) = \omega(x, y), \forall x, y \in V$$

It is easy to know that the automorphism of the self-isomorphism of $(V, \omega)$ constitutes a subgroup of groups $\mathrm{Gl}(V, R)$, which we denote as $\mathrm{Sp}(V, \omega)$. In particular, the automorphism of the standard symplectic space $(k^{2n}, \omega)$ is denoted as $\mathrm{Sp}(2n, k)$, and if $k = R$, $\mathrm{Sp}(2n, k)$ is abbreviated as $\mathrm{Sp}(2n)$ and called a 2n-symplectic group.

```
**Algorithm 17.7: Judgment symplectic algorithm**
Input: S is the group to be judged, T is the transformation.
Output: $\{-1, 1\}$.
Procedure check_symplectic_group(R,S,T)
// R is the symplectic space, T is the symplectic transformation, and S is the group to be judged
If $(V, \omega) \in R \text{ and } \mathrm{Sp}(2n) \in T$. 
If $S \in T \text{ and } \mathrm{Sp}(2n) \in Gl(V, \omega)$.
then return 1.
else return -1.
End if.
End if.
End check_symplectic_group.
```

Let $A_{0}$ be an antisymmetric 2 form on $R^{2n}$, where all the subspaces that satisfy $A_{0} = 0$ x in $R^{2n}$ are called the kernel of $\forall a$, $b \in A$, denoted as $\mathrm{Ker}(\omega^{2})$, i.e.,
$$\mathrm{Ker}(\omega^{2}) = \{x | \omega^{2}(x, y) = 0, \forall x \in R^{2n}\}$$