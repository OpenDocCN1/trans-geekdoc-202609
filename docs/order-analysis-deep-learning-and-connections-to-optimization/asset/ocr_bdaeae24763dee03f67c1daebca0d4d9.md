Finally, if one considers a single artificial neuron with set-valued inputs $A_1, \dots, A_n \in \widetilde{P}(X)$ (where $n \in \mathbb{N}$ and $X$ being a real space), arbitrary weights $w_1, \dots, w_n \in \mathbb{R}$, and an arbitrary set $B \in \widetilde{P}(X)$ (commonly called bias), the affine linear combination

```
$$\sum_{i=1}^n w_i A_i + B \quad (7.1)$
```

is a well-defined set. The question of an appropriate activation function is discussed in the next section.

# 7.3 Activation Map

If the term (7.1) using an activation function such as the sigmoid function would convert it to a more usable form. However, since this set is a set, this transformation cannot be performed in this way. But the softsign function (see Definition 6.2) as a special activation function can be extended to sets.

First, we recall the known definition of the norm of a set in a real space (e.g., see [11]).

**Definition 7.2** $(X, |\cdot|)$ be a real normal space. The norm of a set $A \in \widetilde{P}(X)$ is defined by

```
$$\|A\ := \sup_{a \in A} \|a\|$$
```

Of special importance are now sets $A \in \widetilde{P}(X)$ with the additional property $\|A\| < \infty$; we summarize these sets in the system space $\mathcal{P}(X) \subset \widetilde{P}(X)$, i.e.,

```
$$\mathcal{P}(X) := \{A \in \widetilde{P}(X) \| \\|A\| < \infty\\}$
```

For deep learning networks, it is useful to work with norm-bounded sets. With this concept of the norm of a set, an activation map can also be defined.

**Definition 7.3** $(X, |\cdot|)$ be a real normal space. A map $\mathcal{F} : \widetilde{P}(X) \to \widetilde{P}(X)$ with

```
$$\mathcal{F}(A) := \frac{1}{1+\\|A\|}} A \text{ for all } A \in \widetilde{P}(X)$$$
```

is called activation map.