This way of generating data is known as the *Chinese Restaurant Process* (CRP). Many Chinese restaurants feature round tables with a centre that can be turned. The various dishes are placed there, and the diners can share by turning the centre. Data generation is likened to a hypothetical Chinese restaurant with an infinite variety of tables and each table can seat as many diners as necessary. The first customer sits at the first table and orders a variety of food. This determines the distribution. What they eat fancy corresponds to a sample data. The second customer might choose to sit at the same table. They will eat from the same selection of food, but not exactly as the first customer. They sample a distinct set of food. On the other hand, they might choose to sit at a new table and order a different set of dishes which constitutes the distribution of the second process. As new customers arrive, they either sit at an available open table or open a new one.

Since the final number of customers V is finite, so is the number of tables K. The final configuration is reached it is unique up to the relelling of tables. This means there are K! equivalent ways this configuration could have been reached. In this turn the order in which the customers arrive is of no importance. If a different ordering the first customer sits at a different table which becomes the first table, we relabel this table to 1 and change all labels.

# 6.7 Dirichlet Process

Having considered the process of how the dataset is generated, we need to change our viewpoint and deduce the number of clusters and which samples belong to which the data. As before with Bayesian mixtures, we choose a concentration parameter $\alpha$ and prior probability distributions, and deduce posterior probabilities from the data using Gibbs sampling. However, now K is the current number of clusters and is variable. The normal, inverse Wishart distribution with parameters $m$, $\Psi$ and $
u$ are used as prior to illustrate.

At initialization stage the samples are considered in a random order. Let $\mathbf{v}_1$ be first considered. It also constitutes the first cluster. The posterior normal, inverse Wishart distribution of this cluster is calculated from the prior as

```
$$\begin{aligned} \mathbf{m}_1 &= \frac{\mathbf{v}_1}{\lambda + 1} \ \lambda_1 &= \lambda \ \nu_1 &= \nu + 1 \ \Psi_1 &= \Psi + \frac{\lambda}{\lambda + 1}(\mathbf{v}_1 - \mathbf{m})(\mathbf{v}_1 - \mathbf{m})^T \end{aligned}$
```

A covariance matrix $\mathbf{\Sigma}_1$ and mean $oldsymbol{\mu}_1$ are drawn from this distribution for this cluster.