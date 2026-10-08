from any of the exponential family distributions [200]. Whereas any probability distribution can be cast as an energy-based models, many more specialized distribution families, such as the exponential family, can benefit from particular inference and learning procedures. Some have instead explored rather general-purpose approaches to learning in energy-based models [84, 106, 149].

The normalizing factor Z is called the partition function by analogy with physical systems,

```
$Z = \sum_{x} e^{-\text{Energy}(\mathbf{x})} \quad (5.2)$
```

with a sum running over the input space, or an appropriate integral when $\mathbf{x}$ is continuous. Some energy-based models can be defined when $Z$ does not exist (see Section 5.1.2).

In the product of *experts* formulation [69, 70], the energy function is a sum of terms, each associated with an "expert" $f_i$:

```
$\text{Energy}(\mathbf{x}) = \sum_{i} f_i(\mathbf{x}), \quad (5.3)$
```

i.e.,

```
$P(\mathbf{x}) \propto \prod_{i} P_i(\mathbf{x}) \propto \prod_{i} e^{-f_i(\mathbf{x})}, \quad (5.4)$
```

Each expert $P_i(\mathbf{x})$ can thus be seen as a detector of implausible configurations on $\mathbf{x}$, or equivalently, enforcing constraints on $\mathbf{x}$. This is clearer if we consider the special case where $f_i(\mathbf{x})$ can only take two values, one (small) corresponding to the case where the constraint is satisfied, and one (large) corresponding to the case where it is not. [69] explains the advantages of a product of experts by opposition to a mixture of experts where the product of probabilities is replaced by a weighted sum of probabilities. To simplify, assume that each expert corresponds to a constraint that can either be satisfied or not. In a mixture model, the constraint associated with an expert is an indication of belonging to a region which excludes the other regions. The advantage of the product of experts formulation is therefore that the set of $f_i(\mathbf{x})$ forms a distributed representation: instead of trying to partition the space with one region per expert as in mixture models, they