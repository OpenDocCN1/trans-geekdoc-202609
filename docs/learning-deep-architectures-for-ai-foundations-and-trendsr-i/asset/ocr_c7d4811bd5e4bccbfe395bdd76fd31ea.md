4.4 Deep Generative Architectures 41

![](bbox=[0.393, 0.176, 0.599, 0.375])

empirical distribution of the training set, or the generating distribution for our training examples). The bottom layer generates a vector x in the input space, and we would like to give high probability to the training data. Considering multiple levels, the generative model is this decomposed as:

```
$P(\mathbf{x}, \mathbf{h}^1, \dots, \mathbf{h}^l) = P(\mathbf{h}^l) \left( \prod_{k=1}^{l-1} P(\mathbf{h}^k|\mathbf{h}^{k+1}) \right) P(\mathbf{x}|\mathbf{h}^1) \quad (4.4)$
```

and marginalization yields $P(\mathbf{x})$, but this is intractable in practice except for tiny models. In a sigmoid belief network, the top level $P(\mathbf{h}^l)$ is generally chosen to be factorized, i.e., very simple: $P(\mathbf{h}^l) = \prod P(\mathbf{h}^l)$, and a single Bernoulli parameter is required for each $P(\mathbf{h}^l = 1)$ in the case of binary units.

Deep Belief Networks are similar to sigmoid belief networks, but with a slightly different parametrization for the top layers, as illustrated in Figure 4.4:

```
$P(\mathbf{x}, \mathbf{h}^1, \dots, \mathbf{h}^l) = P(\mathbf{h}^{l-1}, \mathbf{h}^l) \left( \prod_{k=1}^{l-2} P(\mathbf{h}^k|\mathbf{h}^{k+1}) \right) P(\mathbf{x}|\mathbf{h}^1) \quad (4.5)$
```