![](bbox=[0.385, 0.105, 0.615, 0.315])

Figure 4.7: Illustration of the Markov blanket of a node in a directed graphical model. The target node $X_i$ is shown in gray, its parents $U_{1:m}$ are shown in green, its children $Y_{1:n}$ are shown in blue, and its coparents $Z_{1:m,1:j}$ are shown in red. $X_i$ is conditionally independent of all the other variables in the model given these variables. Adapted from Figure 13.4b of [RN19].

where the **non-descendants** of a node nd(i) are all the nodes except for its descendants, nd(i) = {1, ..., Ng} \\ {i $\cup$ desc(i)}. Equation (4.33) is called the (directed) **local Markov property**. For example, in Figure 4.23(a), we have nd(3) = {1, 2, 4}, and pa(3) = 1, so 3 $\perp$ 2, 4 | 1.

A special case of this property is when we only look at predecessors of a node according to some topological ordering. We have

```
$i \perp \text{pred}(i) \setminus \text{pa}(i) | \text{pa}(i)$
```

which follows since pred(i) $\subseteq$ nd(i). This is called the **ordered Markov property**, which justifies Equation (4.2). For example, in Figure 4.23(a), if we use the ordering 1, 2, ..., 7. we find pred(3) = {1, 2} and pa(3) = 1, so 3 $\perp$ 2 | 1.

We have now described three Markov properties for DAGs: the directed global Markov property G in Equation (4.17), the directed local Markov property L in Equation (4.33), and the ordered Markov property O in Equation (4.34). It is obvious that G $\Longrightarrow$ L $\Longrightarrow$ O. What is less obvious, but nevertheless true, is that O $\Longrightarrow$ L $\Longrightarrow$ G (see e.g., [KF09a] for the proof). Hence all these properties are equivalent.

Furthermore, any distribution p that is Markov wrt a graph can be factorized as in Equation (4.2); this is called the **factorization property** F. It is obvious that O $\Longrightarrow$ F, but one can show that the converse also holds (see e.g., [KF09a] for the proof).

# ## 4.2.5 Generation (sampling)

It is easy to generate prior samples from a DPGM: we simply visit the nodes in **topological order**, parents before children, and then sample a value for each node given the value of its parents. This will generate independent samples from the joint, $(x_1, ..., x_{N_G}) \sim p(\mathbf{x}|\boldsymbol{\theta})$. This is called **ancestral sampling**.