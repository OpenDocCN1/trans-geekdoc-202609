# Variants of Proposition 7.1, a Gibbs chain can still be run easily.

Thanks to Proposition 7.1, a Gibbs chain can still be run easily. Truncating the log-likelihood gradient expansion (Equation (5.28)) after $k$ steps of the Gibbs chain, and approximating expectations with samples from this chain, one obtains an approximation of the log-likelihood gradient at training point $\mathbf{x}_1$, that depends only on Gibbs samples $\mathbf{h}_1$, and $\mathbf{x}_{k+1}$:

```
$$\frac{\partial}{\partial\theta} P(\mathbf{x}_1) \simeq -\frac{\partial\text{FreeEnergy}(\mathbf{x}_1)}{\partial\theta} + \frac{\partial\text{FreeEnergy}(\mathbf{x}_{k+1})}{\partial\theta}$\n$\simeq (\sum_{i,j} \frac{\partial\eta_{i,j}(\mathbf{h}_i, \mathbf{x}_j)}{\partial\theta} + \sum_{i,j} \frac{\partial\eta_{i,j}(\mathbf{h}_{k+1}, \mathbf{x}_j)}{\partial\theta}) \propto \Delta\theta$,
```

with $\Delta\theta$ the update rule for parameters $	heta$ of the model, corresponding to CD-$k$ in such a generalized RBM. Note that in most parametrizations we would have a particular element of $	heta$ depend on $\eta_{i,j}$s in such a way that no explicit sum is needed. For instance (taking expectation over $\mathbf{h}_{k+1}$ instead of sampling) we recover Algorithm 1 when

```
$$\eta_{i,j}(\mathbf{h}_i, \mathbf{x}_j) = -W_{ij}\mathbf{h}_i\mathbf{x}_j - \frac{\mathbf{b}_j}{n_h} - \frac{\mathbf{c}_i}{n_x}$,
```

where $n_h$ and $n_x$ are, respectively, the numbers of hidden and visible units, and we also recover the other variants described by [200, 17] for different forms of the energy and allowed set of values for hidden and input units.