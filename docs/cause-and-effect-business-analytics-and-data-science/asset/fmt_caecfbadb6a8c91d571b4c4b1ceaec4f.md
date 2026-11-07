
| 9 || 9 || 410 || 0.22491 || 0.023865 || 0.02275 || 0.0004 ||  |
| 10 || 10 || 3708 || 0.05717 || 0.042621 || 0.000286 || 1.54E-06 ||  |
|   || Sum ||  ||  ||  || 19.5151 || 7.662298 || 27.18 |

![Figure 8.3 Bubble chart for observed lift by cluster. (Cluster-level means (black bubbles) versus overall sample mean (large gray bubble); bubble size is proportional to sample size.) ⏎](images/fig8_3.jpg)

Figure 8.3 Bubble chart for observed lift by cluster. (Cluster-level means (black bubbles) versus overall sample mean (large gray bubble); bubble size is proportional to sample size.) [⏎](#chapter8.xhtml#b8fig8_3)

Table 8.2 Linear Programming Computations Using Excel Solver [⏎](#chapter8.xhtml#b8tbl8_2)

| Cluster || Cluster Size in New Data || Obs. Lift in Response: Men's || Obs. Lift in Response: Women's || Cost per Treatment ($) || Decision var on Number of Men's || Decision var on Number of Women's || Total Number of Treated by Cluster |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 || 4,180 || 0.1587 || 0.0224 || 1 || 4,180 || – || 4,180 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 2 || 5,650 || 0.0652 || −0.0055 || 1 || – || – || – |
| 4 || 60,220 || 0.0658 || 0.0628 || 1 || 2,340 || – || 2,340 |
| 5 || 12,370 || 0.1290 || 0.0618 || 1 || 12,370 || – || 12,370 |
| 6 || 8,940 || 0.0672 || 0.0760 || 1 || – || 8,940 || 8,940 |
| 7 || 29,240 || 0.0519 || 0.0213 || 1 || – || – || – |
| 8 || 28,070 || 0.0868 || 0.0254 || 1 || 28,070 || – || 28,070 |
| 9 || 4,100 || 0.2249 || 0.0239 || 1 || 4,100 || – || 4,100 |
| 10 || 37,080 || 0.0572 || 0.0426 || 1 || – || – || – |
| Total || 189,850 ||  ||  || obj value || 5,773 || 680 || 6,453 |
|   ||  ||  ||  || cost || $51,060 || $8,940 || $60,000 |
|   ||  ||  ||  || Budget ||  ||  || $60,000 |

* 4,180 men's mailings to cluster 1 (again, the original clusters 1 and 3 are merged as cluster 1),
* 2,340 men's mailings to cluster 4,
* 12,370 men's mailings to cluster 5,
* 8,940 to women's mailings to cluster 6,
* 28,070 men's mailings to cluster 8, and
* 4,100 men's mailings to cluster 9.

The optimal results here are clearly governed by the observed lift values as well as the cluster sizes. This example will be extended to consider other situations in subsequent parts of this chapter.

## 8.4 Random Errors and Bootstrapping

Recall that the optimization methods in [Algorithms 8.1](#chapter8.xhtml#box8_1), [8.2](#chapter8.xhtml#box8_2), and model 8.4 assume that the model scores are *exactly* correct for single treatment or multiple treatment problems. [Algorithms 8.3](#chapter8.xhtml#box8_3) and [8.4](#chapter8.xhtml#box8_4), however, mitigate the inaccuracy of the individual-level model scores by using decile/semi-decile/cluster-level performance in the holdout sample. As explained in [Section 8.2.1](#chapter8.xhtml#sec8_2_1), this approach of using the grouped data in the holdout sample has the advantages of using group-level mean lift values (lower variance) and taking data from the holdout sample (lower re-substitution bias).

Are the group-level holdout sample lift values “accurate” enough? While they are better than using individual-level model scores, they still have some degree of uncertainty for the following reasons:

1. **Random Errors:** While sample lift values may be good representations of the true mean lift values (when group sizes are sufficiently large), there is no guarantee that a new sample (even following the same distribution) would result in the same set of lift values, due to randomness from sampling.
2. **Population Difference:** If the future target population is changed from the current population (because of demographic or regional differences, for example), one may make some appropriate adjustments – see [Section 8.5](#chapter8.xhtml#sec8_5) for the “data shift” problem.
3. **Systematic Change:** This can be driven by many factors, such as changes in the economy and customer behavioral changes, and is particularly important for products that are highly driven by the economy or market trends (the latter applies to many technology products such as tablet PCs and 3D TVs). Typical ways to handle this problem include updating models frequently enough to address the latest changes and including those factors (such as economic variables) in the model so that a change in the economy can change the model scores.

This section and the next address the first issue – random errors. Following [Lo and Pachamanova (2015)](#chapter8.xhtml#ref8_22), a natural choice for mitigating random errors is through resampling, also known as bootstrapping. In other words, it assumes there are very many possible samples (resamples drawn from the original samples with replacement) so that we can calculate the lift values for each sample. Using results from many different samples, we then obtain a distribution of lift values, and, as a result, many useful statistics, such as standard deviations and percentiles, can be calculated (for each group/cluster) to assess the uncertainty. This section discusses how this is done; see [Efron and Tibshirani (1993)](#chapter8.xhtml#ref8_12) or [Davison and Hinkley (1997)](#chapter8.xhtml#ref8_11) for a full description of bootstrapping.

### Example 8.2: Continuation of Example 8.1 in Section 8.3

Applying the bootstrapping process in [Algorithm 8.5](#chapter8.xhtml#box8_5) to the previous example with `B = 60` bootstrap samples, we have obtained the results in [Figures 8.4](#chapter8.xhtml#fig8_4) and [8.5](#chapter8.xhtml#fig8_5) and [Tables 8.3](#chapter8.xhtml#tbl8_3) and [8.4](#chapter8.xhtml#tbl8_4). First, [Figure 8.4](#chapter8.xhtml#fig8_4) shows the box plot of the distributions of men's and women's lift values by cluster (see the legend of [Figure 8.4](#chapter8.xhtml#fig8_4) for interpretation), indicating that some clusters have a wider dispersion of lift values than others. In [Table 8.3](#chapter8.xhtml#tbl8_3), cluster-level lift value percentiles are shown along with the bootstrapped standard deviations, which indicate that the uncertainty measured by standard deviation is not uniform across clusters. The correlation matrix of the cluster-level men's lift values and cluster-level women's lift values is shown in [Table 8.4](#chapter8.xhtml#tbl8_4) along with a subset of scatter plots shown in [Figure 8.5](#chapter8.xhtml#fig8_5). Notice that the correlations across clusters are generally small for most combinations.

![Figure 8.4 Distribution of men's and women's lift by cluster using bootstrapping. ⏎](images/fig8_4a.jpg)

Figure 8.4 Distribution of men's and women's lift by cluster using bootstrapping. [⏎](#chapter8.xhtml#b8fig8_4)

![Figure 8.5 Scatter plots of men's and women's lift scores by cluster. (Truncated plots: Only clusters 1, 2, 4, 5, and 6 are shown.) ⏎](images/fig8_5.jpg)

Figure 8.5 Scatter plots of men's and women's lift scores by cluster. (Truncated plots: Only clusters 1, 2, 4, 5, and 6 are shown.) [⏎](#chapter8.xhtml#b8fig8_5)

Table 8.3 Bootstrapped Results of Lift Values by Cluster [⏎](#chapter8.xhtml#b8tbl8_3)

| Cluster || Men's 5th Percentile || Women's 5th Percentile || Men's 50th Percentile || Women's 50th Percentile || Men's 95th Percentile || Women's 95th Percentile || Bootstrap SD for Men's || Bootstrap SD for Women's |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 || 0.1105 || −0.0298 || 0.1491 || 0.0229 || 0.2341 || 0.0840 || 0.0376 || 0.0357 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2 || −0.0111 || −0.0575 || 0.0813 || −0.0050 || 0.1351 || 0.0774 || 0.0452 || 0.0401 |
| 4 || 0.0489 || 0.0471 || 0.0671 || 0.0640 || 0.0848 || 0.0879 || 0.0099 || 0.0122 |
| 5 || 0.0791 || 0.0128 || 0.1233 || 0.0623 || 0.1746 || 0.1083 || 0.0301 || 0.0291 |
