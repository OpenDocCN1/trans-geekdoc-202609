
$$q_{n}(\mathbf{x}_{1:n}) = q_{1}(\mathbf{x}_{1})\prod\limits_{k = 2}^{n}q_{k}(\mathbf{x}_{k}|\mathbf{x}_{1:k - 1}).$$

![Equation](images/B9780443292385000238/si61.png)(17.8)

This means that one has only to choose $q_{k}(\mathbf{x}_{k}|\mathbf{x}_{1:k - 1})$, $k = 2, 3, \dots, n$, together with the initial (prior) $q_{1}(\mathbf{x}_{1})$. Note that the dimensionality of the involved random vector in $q_{k}(\cdot | \cdot)$, given the past, remains *fixed* for all time instants. Eq. [(17.8)](#Chp017_855-884_B9780443292385000238.xhtml#deq12), viewed from another angle, reveals that in order to draw a single (multivariate) sample that spans the time interval up to time $n$, that is, $\mathbf{x}_{1:n}^{(i)} = \{\mathbf{x}_{1}^{(i)}, \mathbf{x}_{2}^{(i)}, \dots, \mathbf{x}_{n}^{(i)}\}$, we build it up *recursively*; we first draw $\mathbf{x}_{1}^{(i)} \sim q_{1}(\mathbf{x})$ and then draw $\mathbf{x}_{k}^{(i)} \sim q_{k}(\mathbf{x}|\mathbf{x}_{1:k - 1}^{(i)})$, $k = 2, 3, \dots, n$. The corresponding unnormalized weights are also computed recursively [16]. Indeed,
