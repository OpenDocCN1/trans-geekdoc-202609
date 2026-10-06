
$b_{0j} = \beta_{00} + u_{0j}$
$b_{1j} = \beta_{10} + u_{ij} \quad (9.4)$

where $\beta_{00}$ and $\beta_{10}$ are fixed-effects parameters and $u_{0j}$ and $u_{ij}$ are the random effects. In this format, additional observation-level predictor variables are included in Equation 9.3 and cluster-level predictor variables are included in Equation 9.4.

## 9.3 Machine Learning with Clustered Data

Machine learning methods have been developed to handle clustered data because biased results can be found when the clustering of observations is not taken into consideration (Miller, McArthur & Lubke, 2017). Machine learning methods for clustered data are particularly important when there is a mix of observation-level and cluster-level variables, and when sample sizes differ across the clusters. However, R packages were developed to perform a variety of machine learning techniques with clustered data. We focus on extensions of recursive partitioning and regularized regression for mixed-effects models, and illustrate these techniques with longitudinal data.

### 9.3.1 Recursive Partitioning with Mixed-Effects Models

For the past few decades, researchers have developed recursive partitioning algorithms to examine individual change trajectories with mixed-effects models. Abdolle, LeBlanc, Stephens, and Harrison (2002) were the first to combine linear mixed-effects model with a recursive partitioning algorithm to search for person-level (cluster-level) variables to explain heterogeneity in change trajectories. In this approach, person-level covariates partition the data into two nodes, a user-specified linear mixed-effects model is estimated within each node, and the $-2$ likelihood ($-2LL$) is computed for each node. The sum of the node-level $-2LL$ is computed and compared to the $-2LL$ when the data are not partitioned, with the partition of the data that minimizes the $-2LL$ retained if the overall improvement in $-2LL$ is greater than a user-provided criterion. While Abdolle and colleagues' work was on studying determinants of change processes and cluster-level predictors, the integration of recursive partitioning and the linear mixed-effects model provided a framework to apply recursive partitioning to all types of clustered data and predictors (observation-level and cluster-level predictors).

Hajjem, Bellavance, and Larocqu (2011) and Sela and Simonoff (2012) extended Abdolell and colleagues’ work with their developing the RE-EM (random effects using the EM algorithm) tree algorithm. This work was focused on the prediction of observation-level scores as opposed to cluster-level differences and was designed to simultaneously handle observation-level predictors and cluster-level predictors. Thus, observations within the same cluster can be partitioned into different nodes. In this approach, indicator (dummy) variables are used to construct the decision tree in a mixed-effects model. Thus, there is a single set of random-effects parameters for all nodes. Given the differences between these approaches, the RE-EM algorithm has been shown to be better for prediction (Stegmann, Jacobucci, Serang, Grimm, 2018), but lacks structure because indicator variables are used to form the decision tree structure. Abdolell’s algorithm can be specified by having an empty random intercept within each node; however, constraints on the variance of the random intercept across nodes cannot be implemented.

Variants of the recursive partitioning algorithm for mixed-effects have been proposed. Fu and Simonoff (2015) extended the RE-EM tree (Sela and Simonoff, 2012) algorithm to account for selection bias (i.e., variables with more unique values are more likely to be chosen) using the conditional inference trees (ctree; Hothorn et al., 2006) algorithm. Another variant of recursive partitioning for longitudinal data (MELIS) algorithm proposed by Eo and Cho (2014). The focus of this algorithm is on predictors of random slopes, which partitions the data based on cluster-level covariates. At each node, a linear mixed-effects model is fit, and the individual slices for each individual are computed. The partition that minimizes the distance between the individuals’ slopes and the mean slope at the node is chosen. Thus, approach is viable when the focus is on finding moderators of observation-level associations. In the past few years, several extensions of these models have improved the utility and applicability of these models. For example, Kekisma, Smiths, Zeiles, Hothorn, and Kelderman (2018) proposed the generalized mixed-effects tree (GLMM tree) algorithm which allows for non-Gaussian outcomes (e.g., count) and model-based (MOB; Zeiles, Hothorn, & Hornik, 2018) partitioning. In the GLMM tree the random-effects parameters are invariant across nodes, which is similar to the RE-EM tree algorithm; however, GLMM tree allows for greater flexibility than the work by Abdolell et al. (2002). Stegmann, Jacobucci, Serang, and Grimm (2018) extended Abdolell et al.’s approach to allow for nonlinear mixed-effects models (e.g., exponential models) and Serang, Jacobucci, Grimm, Stegmann, and Baummaier (2020a) integrated the CART algorithm with Mplus to allow for more complex multilevel models within each node (e.g., multivariate outcomes).

## Software

The first software package was developed by Abdoleol et al. (2002), who utilized the macro language in SAS and the PROC MIXED (Singer, 1999).

### 9.3.2 Algorithm

In this chapter, we focus on the recursive partitioning algorithm which follows the following steps:

- A stopping threshold $k$ is specified.
- The mixed-effects model is estimated on the full sample and the $-2LL$ is retained.
- Given a predictor variable $w_{li}$, the data are partitioned based on each unique value $c$ ($w_{li} < c$ versus $w_{li} \geq c$).
- The mixed-effects model is estimated on each partition, the two $-2LL$ are obtained, referred to as $node_i(-2LL)$ and $node_j(-2LL)$.
- The $-2LL$ for the partition is calculated as $node(-2LL) = node_i(-2LL) + node_j(-2LL)$.
- Steps 4, 5, and 6 are repeated for each variable in the predictor set.
- If $(-2LL) - node(-2LL) < k$ for all partitions, the algorithm is stopped and the data are not further partitioned.
- If $(-2LL) - node(-2LL) > k$ for some set of partitions, the data are partitioned based on the predictor variable and value that resulted in the greatest improvement in $-2LL$.
- Steps 3 through 9 are repeated within each node with $base(-2LL)$ and $node_i(-2LL)$, respectively.

The stopping threshold $k$ can be set to a specific value (e.g., 20) or based on the root $(-2LL)$. For example, $k=0.01 \times (-2LL)$, such that the improvement in model fit must be greater than 1% of the $-2LL$ when the model is estimated on the full sample. At a minimum, $k$ should be set equal to $\lambda \sigma(p)$, where $p$ is the difference in the number of estimated parameters when partitioning the data.

## 9.4 Regularization with Mixed-Effects Models

A second machine learning technique that has been integrated into the mixed-effects modeling framework is regularization—primarily used with the lasso penalty for variable selection. In regularized mixed-effects models, fixed-effects parameters are often penalized to examine which effects should be retained in the model; however, approaches have also penalized random-effects parameters to determine which slopes should be random and which slopes should be fixed (estimated without a random component). The parameters in regularized mixed-effects models are found by minimizing the $-2LL$ with a penalty for the size of model parameters. Then is, the $-2$ log-likelihood for the mixed-effects model is

$$-2LL = n \log(2\pi\sigma_0^2) + \log(I + ZZ^T') + \frac{1}{\sigma_0^2}(y_i - X\beta)'(y_i - X\beta) \quad (9.5)$$
