
To fit $K$-means in R, we need to first transform the data into a numeric matrix x (i.e., you need to expand any factors into dummy variables). In the case of this protein data, everything is numeric to start. However, we still need to think about *scaling*. As is always the case when you are minimizing squared errors across dimensions of $x$ (e.g., as in $K$ nearest neighbors), the *units* used for these dimensions will influence the result. We will convert to the units of *standard deviation* and cluster on the transformed $\tilde{x}_j = (x_{ij} - \bar{x}_j)/\text{sd}(x_j)$. These new units are also shifted to have mean of zero and are thus interpretable as units of *standard deviations from the pooled average*.

```r
> xfood <- scale(food)
> round(head(xfood),1)
```

|  | RedMeat | WhiteMeat | Eggs | Milk | Fish | Cereals | Starch | Nuts | Fr.Veg |
|---|---|---|---|---|---|---|---|---|
| Albania | 0.1 | -1.8 | -2.2 | -1.2 | -1.2 | 0.9 | -2.2 | 1.2 | -1.4 |
| Austria | -0.3 | 1.7 | 1.2 | 0.4 | -0.6 | -0.4 | -0.4 | -0.9 | 0.1 |
| Belgium | 1.1 | 0.4 | 1.0 | 0.1 | 0.1 | -0.5 | 0.9 | -0.5 | -0.1 |
| Bulgaria | -0.6 | -0.5 | -1.2 | -1.2 | -0.9 | 2.2 | -1.9 | 0.3 | 0.0 |
| Czechoslovakia | 0.0 | 0.9 | -0.1 | -0.6 | -0.7 | 0.2 | 0.4 | -1.0 | -0.1 |
| Denmark | 0.2 | 0.8 | 0.7 | 1.1 | 1.7 | -0.9 | 0.3 | -1.2 | -1.0 |

The `kmeans` function takes argument `centers` to define $K$ and `nstart` to determine the number of repeats of the algorithm (each corresponding to a different random start, as described earlier). The minimum deviance found across `nstart` runs is reported to the user. We fit a simple 3-mean model to the protein data:

```r
>(grpMeat <- kmeans(xfood, centers=3, nstart=10))
K-means clustering with 3 clusters of sizes 6, 15, 4

Cluster means:
    RedMeat WhiteMeat  Eggs  Milk Fish Cereals Starch Nuts Fr.Veg
1     -0.8      -0.5 -1.2 -0.9 -1.0     1.4 -0.8  0.9 -0.5
2      0.5       0.5  0.6  0.6  0.1    -0.6  0.4 -0.7 -0.2
3     -0.5      -1.1 -0.4 -0.8  1.0     0.1 -0.2  1.3  1.6

Clustering vector:
  Albania   Austria  Belgium  Bulgaria Czechoslovakia
        1         2         2         1              2
...
```

The grp$cluster object holds cluster assignments for each observation, and we’ve used them to plot the 3-means clustering in the red-meat versus white-meat plane in Figure 7.4. The results show one large group, with a smaller cluster created for the USSR and some neighboring satellites and another for a Western European Mediterranean block.

![](img/315929ad4bddd26368466d02e06e2385_283_0.png)

**FIGURE 7.4:** 3-means clustering of countries by protein consumption, shown in the red-meat versus white-meat plane (but fit on all protein categories).

For comparison, **Figure 7.5** shows a 7-means clustering. Again, we are clustering on all nine protein categories but plotting in the red-meat versus white-meat plane. The shades and fonts indicate membership, and we see many familiar cultural and geographic groupings represented in the clustering learned through only protein consumption.

![](img/315929ad4bddd26368466d02e06e2385_284_0.png)

**FIGURE 7.5:** 7-means clustering of countries by protein consumption, shown in the red-meat versus white-meat plane.

THE CHOICE OF K IS HIGHLY SUBJECTIVE. There is little information in the data on how many clusters there are in reality, and algorithms that automatically select K will be sensitive to assumptions about the component probability models. The exception to this is if you are using the cluster memberships *downstream* in some sort of prediction task, e.g., as inputs to a regression model. In that case, you can use the usual CV routines as a referee on the number of clusters. But otherwise, everything is descriptive—you are just trying to break the data into relatively homogeneous groups. It is wise to try a few K and use the one leading to clusters that make sense to you.

If you choose to ignore this advice, it is possible to use data-based model building here. As always, the procedure follows a recipe of model enumeration followed by selection:

- 1. Enumerate models for $K_1 < K_2 \dots K_T$ clusters.
- 2. Use a selection tool to choose the best model for new x.

The newness of x is key: as always, you want the model to have low out-of-sample deviance. In-sample deviance is useless, as you could always get a deviance of zero by setting $K = n$.

A CV routine is possible here: for each $K$, fit the mixture on part of the data and evaluate the deviance on the left-out sample for the fitted *unconditional* likelihood in Equation 7.1.2. It will be necessary to use a deviance built from the unconditional likelihood because you don't know $k_f$ for left-out $x_f$.

However, since $K$-means is computationally expensive, it is usually impractical to run a full CV experiment. It is more common to use an information criterion for selecting the number of clusters. The full in-sample deviance for $K$-means—for the model in Equation 7.5—is the sum of squares, $\sum_i\sum_j (x_{ij} - \hat{\mu}_{k_{ij}})^2$. The number of degrees of freedom is equal to the number of parameters in the cluster centers: $K \times p$. With these two facts, the usual AIC/AICc and BIC formulas apply. For example, Figure 7.6 shows the BIC surface for the protein data country clustering—it selects $K = 2$.

![](img/315929ad4bddd26368466d02e06e2385_285_0.png)

**FIGURE 7.6:** BIC for $K$ in the protein-consumption clustering example.

However, you should beware: all of these tools—from CV to BIC—are less reliable here than in regression. The CV routine will have trouble with the instability of the model fit as a function of $K$ (this is like forward stepwise regression, where CV does poorly) while the AIC/AICc/BIC rely upon theoretical approximations that are less valid here for mixtures than they are for the regression models. If you are going to use anything, there is some evidence that the BIC works well for mixtures, and I'd trust it before the others. But I still don't trust it much at all. For example, Figure 7.6 shows the BIC selecting fewer clusters than intuition would suggest for our European protein example.

## FACTOR MODELS AND PCA

Clustering and mixture modeling are special cases of a more general framework for unsupervised dimension reduction: factorization. Given a matrix of high-dimensional data $x$, you’d like to reduce this to a function of a few “important” factors. You do this by building a linear model for $x$ as a function of these unknown factors and then estimating both factors and model at the same time. A factor model has

$$ \mathbb{E}[\boldsymbol{x_i}] = \boldsymbol{\varphi_1}\boldsymbol{v_{i1}} + \ldots \boldsymbol{\varphi_K}\boldsymbol{v_{iK}} $$ (7.6)

where $x_i$ and $\varphi_k$ are all length-$p$ vectors, while the $v_{ik}$ are univariate scores indicating how observation $i$ loads on factor $k$.

When you use a $K$ that is much smaller than $p$, factor models provide a parsimonious representation for $x$. Each observation $x_i$ is mapped to $K$ factors $v_{i1}$ . . . $v_{ik}$, and these factors are a low dimensional summary of $x$. Consider the nifty example in Figure 7.7. This shows the fitted mapping from vectors of genetic SNP information (a high-dimensional $x$) to a 2D factor space. After shading by each person’s country of origin, a pattern emerges: the factor representation resembles a (tilted) map of Europe. This means that the best two-dimensional summary of genetic material simply corresponds to the latitude and longitude—in other words, knowing where you are from provides information about your genes.
