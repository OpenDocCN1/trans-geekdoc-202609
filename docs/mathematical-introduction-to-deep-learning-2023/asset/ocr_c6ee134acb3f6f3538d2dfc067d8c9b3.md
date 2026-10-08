# # Chapter 14
# Overall error decomposition

In Chapter 15 below we combine parts of the approximation error estimates from Part **II**, parts of the optimization error estimates from Part **III**, and parts of the generalization error estimates from Part **IV** to establish estimates for the overall error in the training of ANNs in the specific situation of GD-type optimization methods with many independent random initializations. For such a combined error analysis we employ a suitable overall error decomposition for supervised learning problems. It is the subject of this chapter to review and derive this overall error decomposition (see Proposition 14.2.1 below).

In the literature such kind of error decompositions can, for example, be found in [25, 35, 36, 87, 230]. The specific presentation of this chapter is strongly based on [25, Section 4.1] and [230, Section 6.1].

# ## 14.1 Bias-variance decomposition

**Lemma 14.1.1** (Bias-variance decomposition). *Let* $(\Omega,\mathcal{F},\mathbb{P})$ *be a probability space, let* $(S,\mathcal{S})$ *be a measurable space, let* $X: \Omega \rightarrow S$ *and* $Y: \Omega \rightarrow \mathbb{R}$ *be random variables with* $\mathbb{E}[|Y|^{2}] < \infty$*, and let* $\mathbf{r}: \mathcal{L}^{2}(\mathbb{P}_{X};\mathbb{R}) \rightarrow [0,\infty)$ *satisfy for all* $f \in \mathcal{L}^{2}(\mathbb{P}_{X};\mathbb{R})$ *that*

```
$\mathbf{r}(f) = \mathbb{E}[|f(X) - Y|^{2}]$.

(14.1)

*Then*

*(i)* *it holds for all* $f \in \mathcal{L}^{2}(\mathbb{P}_{X};\mathbb{R})$ *that*
```

```
$\mathbf{r}(f) = \mathbb{E}\big[|f(X) - \mathbb{E}[Y|X]|^{2}\big] + \mathbb{E}\big[Y - \mathbb{E}[Y|X]|^{2}\big]$,

(14.2)
```

*(ii)* *it holds for all* $f,g \in \mathcal{L}^{2}(\mathbb{P}_{X};\mathbb{R})$ *that*

```
$\mathbf{r}(f) - \mathbf{r}(g) = \mathbb{E}\big[|f(X) - \mathbb{E}[Y|X]|^{2}\big] - \mathbb{E}\big[|g(X) - \mathbb{E}[Y|X]|^{2}\big]$

(14.3)

*and*
```