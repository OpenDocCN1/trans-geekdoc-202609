# Assumption 7.1 Let $X$ be a real space, $n \in \mathbb{N}$ be the total number of weights, $m \in \mathbb{N}$ be the total number of biases, let $S_{	ext{pred}} : \mathbb{R}^n 	imes (\hat{P}(X))^m 	o \hat{P}(X)$ be given, and let $S_{	ext{true}} \in \hat{P}(X)$ be a given true.

If $d : 	ilde{P}(X) 	imes 	ilde{P}(X) 	o \mathbb{R}$ defines any appropriate distance function between two sets, optimal weights and biases can be calculated as solutions of the optimization problem

```
$$\min d(S_{	ext{pred}}(w_1, \dots, w_n), B_1, \dots, B_m), S_{	ext{true}})$$\n$\text{subject to}$
$$w_1, \dots, w_n \in \mathbb{R}; B_1, \dots, B_m \in \hat{P}(X). (7.2)$
```

In the following subsections, we investigate three different distances in problem (7.2), namely, the Hausdorff distance and the radial and constraint distances.

# 7.4.1 Hausdorff Distance

For the comparison of two sets, the well-known Hausdorff distance plays an important role.

**Definition 7.4** $(X, ||\cdot||)$ be a real normed space. For two sets $A, B \in \tilde{P}(X)$, the *Hausdorff distance* is defined by

```
$d_H(A, B) := \max \left\ \sup_{a \in A} b \in B} ||a - b||, \sup_{b \in B} a \in A} ||a - b|\ \right\.$
```

The two results in Proposition 7.2 provide the motivation for optimization problem (7.2) using the Hausdorff distance. Although the first result for comparing two sets with the Hausdorff distance is well-known in special cases, we provide a simple proof of the reverse implication for reflexive Banach spaces (compare also Ha [52, Subsection 5.1]).

**Proposition 7.2** $(X, ||\cdot||)$ be a real normed space, and let two sets $A, B \in \tilde{P}(X)$ be arbitrarily chosen.

+   (a) $A = B \implies d_H(A, B) = 0$.
(b) If, in addition, $(X, ||\cdot||)$ is a real reflexive Banach space and the sets $A, B$ are convex and closed,
$d_H(A, B) = 0 \implies A = B.$

*Proof* For two arbitrary sets $A, B \in \tilde{P}(X)$, we get

```
$A \subseteq B \iff \forall a \in A : a \in B$\n$\iff \forall a \in A \ \exists b \in B : ||a - b|| = 0$
```