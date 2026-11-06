
# Impurity Reduction Measures for Class Targets

## Figure A.3.1: Impurity Reduction Measures

![Figure 1.1 Some JMP Help Options](Images/Image822.jpg)

After a set of candidate splits is determined, a splitting criterion is used to determine the best one. In some situations, the worth of a split is obvious. If target distributions are the same in the child nodes as they are in the parent node, then no improvement was made, and the split is worthless. In contrast, if a split results in pure children, then the split is definitely the best.

In classification trees, the three most well-known splitting criteria are based on the `Gini index` (BFOS 1984), `entropy` (Quinlan 1993), and the `chi-square test` (Kass 1980). Well-known algorithms and software products associated with these three splitting criteria are `CART` (classification and regression tree); `C5.0` (developed by the machine learning researcher Quinlin); and the `CHAID` algorithm (chi-squared automatic interaction detection).

## Details: Impurity Reduction Measures for Interval Targets

Regression trees endeavor to partition the input space into segments where the target values are alike. (That is, each segment or node has low variability.) All target values would be equal in a pure node. In other words, the variance of the target would be zero within a pure node.

The split-search considerations and the `p-value` adjustments are the same as with classification trees. However, the appropriate splitting criteria are different. The default splitting criterion for a regression tree is change in response variance. `CHAID` and `F Statistic` are also available as splitting methods.

Entropy and the Gini index are measures of variability of nominal variables. When the target distribution is continuous, the sample variance is the obvious measure of impurity (Morgan and Sonquist 1963, Breiman et al. 1984).

![Figure 1.1 Some JMP Help Options](Images/Image8301.png)

Note: The denominator is `ni`, not `ni-1`. This is the `MLE` and not the usual unbiased estimate of sample variance.

The `F test` can be used analogously to the chi-square test for regression trees. A split at a node can be thought of as a one-way analysis of variance where the `B` branches are the `B` treatments. Let

![Figure 1.1 Some JMP Help Options](Images/Image8371.png)

be the mean of the target in each node and ![Figure 1.1 Some JMP Help Options](Images/Image8453.png)be the mean in the root node (the overall mean). The between-node sum of squares (`SSbetween`) is a measure of the distance between the node means and the overall mean. The within-node sum of squares (`SSwithin`) measures the variability within a node. Large values of the `F statistic` indicate departures from the null hypothesis that all the node means are equal. When the target values, conditional on the inputs, are independently, normally distributed with constant variance, then the `F statistic` follows an `F` distribution with `B – 1` and `n – B` degrees of freedom. The `p-value` of the test is used in the same way as the `p-value` for a chi-square test for classification trees.

The total sum of squares (`SStotal`) can be considered fixed with regard to comparing splits at a particular node. Thus, it follows from the ANOVA identity

![Figure 1.1 Some JMP Help Options](Images/Image854.png)that the `F test statistic` can be thought of as either maximizing the differences between the node means or reducing the within-node variance. This latter interpretation indicates the equivalency between the `F statistic` and the reduction in impurity (variance) splitting criterion.

![Figure 1.1 Some JMP Help Options](Images/Image861.png)

Thus, using `Dvariance` is equivalent to not adjusting the `F test` for degrees of freedom (number of branches).

# A.4: Decision Tree Split Search

Understanding the details of an algorithm used for building trees enables you to better use SAS Visual Data Mining and Machine Learning to build a tree and interpret your results. The description presented here assumes a binary target, but the algorithm for interval targets is similar. (The algorithm for categorical targets with more than two outcomes is more complicated and is not discussed.) In `Model Studio`, the algorithm described here is known as `chi-square`.

The first part of the algorithm is called the split search. The split search starts by selecting an input for partitioning the available training data. If the measurement scale of the selected input is interval, each unique value serves as a potential split point for the data. If the input is categorical, the average value of the target is taken within each categorical input level. The averages serve the same role as the unique interval input values in the discussion that follows.

For a selected input and fixed split point, two groups are generated. Cases with input values less than the split point are said to branch left. Cases with input values greater than the split point are said to branch right. The groups, combined with the target outcomes, form a 2x2 contingency table with columns specifying branch direction (left or right) and rows specifying target value (0 or 1). A Pearson `chi-squared statistic` is used to quantify the independence of counts in the table’s columns. Large values for the `chi-squared statistic` suggest that the proportion of 0s and 1s in the left branch is different from the proportion in the right branch. A large difference in outcome proportions indicates a good split.

Because the Pearson `chi-squared statistic` can be applied to the case of multiway splits and multi-outcome targets, the statistic is converted to a probability value, or `p-value`. The `p-value` indicates the likelihood of obtaining the observed value of the statistic assuming identical target proportions in each branch direction. For large data sets, these `p-values` can be very close to zero. For this reason, the quality of a split is reported by `logworth = -log(chi-squared p-value)`.

Note: At least one `logworth` must exceed a threshold for a split to occur with that input. By default, this threshold corresponds to a `chi-squared p-value` of 0.20 or a `logworth` of approximately 0.7.

## Figure A.4.1: Decision Tree Split Search

![Figure 1.1 Some JMP Help Options](Images/Image869.jpg)

The best split for an input is the split that yields the highest `logworth`.

Several peripheral factors make the split search somewhat more complicated than what is described above.

First, the tree algorithm settings disallow certain partitions of the data. Settings, such as the minimum number of observations required for a split search and the minimum number of observations in a leaf, force a minimum number of cases in a split partition. This minimum number of cases reduces the number of potential partitions for each input in the split search.

Second, when you test for the independence of column categories in a contingency table, it is possible to obtain significant (large) values of the `chi-squared statistic` even when there are no differences in the true, underlying proportions between split branches. In other words, if there are many ways to split the variable that labels the rows of the table (and thus many Chi-square tables and tests), then you are likely to get at least one with a very small `p-value` even when the variable has no true effect. As the number of possible split points increases, the likelihood of obtaining significant values also increases. In this way, an input with a multitude of unique input values has a greater chance of accidentally having a large `logworth` than an input with only a few distinct input values.
