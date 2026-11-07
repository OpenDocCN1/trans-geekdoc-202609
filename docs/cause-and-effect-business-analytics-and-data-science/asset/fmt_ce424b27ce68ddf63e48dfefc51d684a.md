
$$= {\sum\limits_{i = 1}^{n}{\sum\limits_{j = 1}^{m}{{\bigtriangleup \hat{p}}_{ij}x_{ij}}}} + {\sum\limits_{i = 1}^{n}{~\hat{p}_{i0,~}\left( using~constraint~\left( 8.5.1 \right) \right)}}~$$

which is the same as the objective function in Eqn. (8.4) plus a constant that does not depend on the decision variables. Hence, Eqns. (8.4) and (8.5) are equivalent. Additional constraints can also be added to model (8.4) or (8.5), for example, limited quantities available for certain treatments.

Model (8.4) or (8.5) is a binary (or zero-one) integer programming problem and is well-known to be challenging to solve. Unlike `LP` problems, there is no efficient general algorithm available due to its `NP-completeness` Page 218nature (which is a formal way of saying they are really hard to solve and can take a very long time

An alternative to solving Eqn. (8.4) or (8.5) is to use heuristics such as first grouping individuals into clusters (using cluster analysis, for example, based on certain individual characteristics) and solving the `LP` problem at the cluster level (as well as individual-level optimization in each cluster); see [Storey and Cohen (2002)](#chapter8.xhtml#ref8_31) for general marketing optimization (not specific to uplift problems). General heuristics or approximation algorithms such as simulated annealing, genetic algorithms, and tabu search can also be considered; see [Goldberg (1989)](#chapter8.xhtml#ref8_16), [Bertsimas and Tsitsiklis (1997)](#chapter8.xhtml#ref8_1), or [Michalewicz and Fogel (2002)](#chapter8.xhtml#ref8_26).

In practice, instead of using individual-level model estimates for `△p[i j]`, we recommend using the holdout sample estimates that are less biased, for reasons given in [Section 8.2.1](#chapter8.xhtml#sec8_2_1) for the single-treatment case. However, unlike the deciling method for the single-treatment situation in [Algorithm 8.3](#chapter8.xhtml#box8_3), since each treatment has its own set of deciles, we cannot compare the lift estimate for decile 1 of treatment 1 to the lift estimate for decile 1 of treatment 2 in order to pick the better treatment, as the two decile 1s are not the same group of individuals. To address this issue, we employ cluster analysis to group individuals in the algorithm described below (see [Chapter 2](#chapter2.xhtml) for an introduction to cluster analysis).

[Algorithm 8.4](#chapter8.xhtml#box8_4) provides an optimal solution at the cluster level, that is, optimizing the treatment allocation to each cluster (including no allocation to some clusters, which is also part of an optimal solution). So exactly who should receive each treatment at the individual level for a given cluster? If the cluster size for a given cluster in the target population is larger than the quantity recommended by the optimization algorithm, one recommendation is to simply choose the targeted individuals at random. This approach, while simple, has the advantage of having a natural randomized control group (those who are not selected but similar to those selected for the next campaign), a key for measurement and further refinement. After all, the individual-level model-based lift scores should be relatively homogenous within each cluster (through cluster analysis in Step 2 of [Algorithm 8.4](#chapter8.xhtml#box8_4)). Additionally, we may not have good model-based estimates to differentiate between individuals within a given cluster. Alternatively, if we really have to “optimize” at the individual level for a given cluster, we can prioritize the selection by individual-level model-based lift value score, even though those individual-level estimates may not be very accurate (i.e., choose those with the highest individual-level estimates).

## 8.3 Joint Men's and Women's Merchandise Optimization Example (Using Excel Solver)

### Example 8.1 (Extension of [Example 6.2](#chapter6.xhtml#secex6_2)), adapted from [Lo and Pachamanova (2015](#chapter8.xhtml#ref8_22))

This data set has two email treatment groups for men's and women's merchandise, respectively, plus a no-mail control group. In this example, we apply the Two Model Approach and Treatment Dummy Approach from Page 221[Lo (2002)](#chapter8.xhtml#ref8_21), that is, Methods 1 and 2 from [Chapter 6](#chapter6.xhtml), to maximize overall visits. Using the Two Model Approach (Method 1), we can calculate the lift score for men's merchandise and the lift score for women's merchandise as inputs to cluster analysis (clustering on two variables), and similarly for the Treatment Dummy Approach (Method 2).

1. We first calculate the individual model scores for all individuals using each method (Methods 1 and 2).
2. Perform clustering using `k-means` with 10 clusters (one may choose other clustering algorithms such as hierarchical or EM-based) under each method. [Figure 8.2](#chapter8.xhtml#fig8_2) illustrates the women's treatment lift score (vertical) and men's treatment lift score (horizontal) using Method 1 (the original clusters 1 and 3 are merged into cluster 1 because of small sizes, a common issue with clustering). It is clear that the two treatment lift scores are related, although not strongly linearly.
3. Cluster-level means and computations for the squared distance to the overall lift means are in [Table 8.1](#chapter8.xhtml#tbl8_1).
4. Page 222Between Methods 1 and 2, Method 1 has the highest squared distance to the overall sample mean and thus is chosen as the cluster solution for the next steps. The bubble chart in [Figure 8.3](#chapter8.xhtml#fig8_3) shows the two-dimensional distance of each cluster (denoted by black bubbles) to the overall sample mean (large gray bubble), where the size of each bubble is proportional to cluster sample size.
5. Page 223We can now apply the chosen cluster solution to *future* data for optimization. For this illustrative example, we assume the future data is 10 times the holdout sample, and the cluster distribution is the same as in the holdout sample.
6. The last step is to solve the `LP` problem in model (8.7). The results are shown in [Table 8.2](#chapter8.xhtml#tbl8_2). Note that cluster sizes (`N[c]`) in the second column are used in the cluster size constraint. The third and fourth columns are simply taken from the holdout sample's observed (sample mean) lift values by cluster and are used in the objective function calculations. The cost per treatment contact is assumed to be $1.0 each for both men's and women's merchandise, and the total budget is set at $60,000. The decision variables are set up such that the estimated total number of visits is maximized (shaded cell). The optimal solution, solved by the “`Simplex LP`” option in `Excel Solver`, is:

![Figure 8.2 Lift score for women's merchandise by lift score for men's by cluster. ⏎](images/fig8_2.jpg)

Figure 8.2 Lift score for women's merchandise by lift score for men's by cluster. [⏎](#chapter8.xhtml#b8fig8_2)

Table 8.1 Lift in Response by Treatment by Cluster and Calculation of the Squared Distance to Overall Means [⏎](#chapter8.xhtml#b8tbl8_1)

| Obs || Cluster || Size || Obs. Lift in Response: Men's || Obs. Lift in Response: Women's || Sqr dist1 || Sqr dist2 || Squared Distance to Overall Mean |

| --- | --- | --- | --- | --- | --- | --- | --- |

| 1 || Overall || 18985 || 0.07408 || 0.043863 ||  ||  ||  |

| --- | --- | --- | --- | --- | --- | --- | --- |

| 2 || 1 || 418 || 0.15871 || 0.022388 || 0.007162 || 0.000461 ||  |

| 3 || 2 || 565 || 0.06521 || −0.005547 || 7.87E-05 || 0.002441 ||  |

| 4 || 4 || 6022 || 0.06577 || 0.062776 || 6.91E-05 || 0.000358 ||  |

| 5 || 5 || 1237 || 0.12903 || 0.06177 || 0.00302 || 0.000321 ||  |

| 6 || 6 || 894 || 0.06717 || 0.076013 || 4.77E-05 || 0.001034 ||  |

| 7 || 7 || 2924 || 0.0519 || 0.021328 || 0.000492 || 0.000508 ||  |

| 8 || 8 || 2807 || 0.08684 || 0.025362 || 0.000163 || 0.000342 ||  |
