# APPENDIX: PROBING HIDDEN HIERARCHIES IN DATA

Notice that the expectation values $p_\ell$ and $q_\ell$ depend on the layer $\ell$ and not on the specific position of the node $i$ inside the layer. Once $p_\ell$ and $q_\ell$ have been computed for every layer $\ell=0, \dots, L$, the average marginal probability of reconstructing the original value $\vec{a} \in \mathcal{Y}^{(\ell)}$ of the variable $h^{(\ell)}$ is given by

```
P(h^{(\ell)} = ar{a}) = \frac{p_\ell q_\ell}{p_\ell q_\ell + (1-p_\ell)(1-q_\ell)} \quad (351)
```

This marginal probability is conditioned on the initialization of the leaf nodes (Equation 342) and only depends on the layer $\ell$, not on the position of the node inside the layer. Given the initialization of $q_L$, the probability of reconstructing the root node $P(h^{(L)} = ar{a})$, is, the class of the datum, is given by

```
P(h^{(L)} = ar{a}) = p_L. \quad (352)
```

Therefore, in the limit of large depth $L 	o \infty$, the value of $p_i$ is given by one of the fixed of the iterative map $F(p)$. When $F'(1) > 1$, $F(p)$ has two fixed points: $p=1$, which is repulsive, and $p=1/v$, which is attractive. This implies that, in this regime, for any noise $\epsilon >0$ at the leaf nodes, it is impossible to reconstruct the value of the class better than random chance. When, $F'(1) < 1$, the class is

```
\frac{v-1}{m} \frac{v}{v^s-1} < 1, \quad (353)
```

a non-trivial fixed point $p^* = F(p^*)$ appears, which is repulsive, while both $p=1$ and $p=1/v$ are attractive. The presence of a phase transition at a specific noise level $e^* = \frac{1-p^*}{\sqrt{1-1/v}}$. For $\epsilon < e^*$, the class is reconstructed, for $e > e^*$ it is not.

# COMPUTATION OF THE CORRELATION FUNCTIONS

Similar to the marginal probabilities, the average correlation function can also be computed through an annealed average over the RHM rules. We consider two leaf nodes $h_i^{(0)}$ and $h_j^{(0)}$ connected to the common ancestor $h_i^{(\ell)}$ at layer $\ell$ through the nodes $h_i^{(\ell-1)}$ and $h_2^{(\ell-1)}$. Given the tree structure, their joint probability distribution can be written as

```
P(h_i^{(0)}, h_j^{(0)}) = \\sum P(h_i^{(\ell)}|h_i^{(\ell-1)}) P(h_j^{(\ell)}|h_m^{(\ell-1)}) \sum P(h_i^{(\ell-1)}|h_m^{(\ell-2)}) P(h_m^{(\ell-1)}|h_k^{(\ell-2)}) \quad (354)
```

In the mean-field approach, the average joint probability only depends on the tree-distance $\ell$ between $i$ and $j$ and not their precise location. Moreover, we are only interested in the probability that both