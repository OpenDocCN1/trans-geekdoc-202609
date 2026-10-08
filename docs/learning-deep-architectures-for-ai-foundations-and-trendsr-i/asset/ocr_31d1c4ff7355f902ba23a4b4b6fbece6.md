# 5.3 Restricted Boltzmann Machines 57

and in the binary case

```
$P(x_j = 1|\mathbf{h}) = 	ext{sig}(\mathbf{b}_j + W_j^T\mathbf{h}) \quad (5.24)$
```

where $W_j$ is the $j$th column of $W$.

In [73], binomial input units are used to encode pixel gray levels in input images as if they were the probability of a binary event. In the case of handwritten character images this approximation works well, but in others it does not. Experiments showing the advantage of using Gaussian input units rather than binomial units the inputs are continuous-valued are described in [17]. See [200] for a general formulation where $\mathbf{x}$ and $\mathbf{h}$ (given the other) can be in any of the exponential family distributions (discrete and continuous).

Although RBMs might not be able to represent efficiently some distributions that could be represented compactly with an unrestricted Boltzmann machine, RBMs can represent any discrete distribution [51, 102], if enough hidden units are used. In addition, it can be shown that unless the RBM perfectly models the training distribution, adding a hidden unit (and properly choosing its weights and offset) can improve the log-likelihood [102].

An RBM can also be seen as forming a multi-clustering (Section 3.2), as illustrated in Figure 3.2. Each hidden unit creates a two-region partition of the input space (with a linear separation). When we consider the configurations of three hidden units, there are eight possible intersections of three half-planes (by choosing each half-plane among the linear separation performed by a hidden unit). Each of these eight intersections corresponds to a region in input space associated with the same hidden configuration (i.e., code). The binary setting of the hidden units identifies one region in input space. For all $\mathbf{x}$ in one of these regions, $P(\mathbf{h}|\mathbf{x})$ is maximal for the corresponding $\mathbf{h}$ configuration. Note that not all configurations of the hidden units correspond to a non-empty region in input space. As illustrated in Figure 3.2, this representation is similar to what an ensemble of two-leaf trees would create.

The sum over the exponential number of possible hidden-layer configurations of an RBM can also be seen as a particularly interesting form