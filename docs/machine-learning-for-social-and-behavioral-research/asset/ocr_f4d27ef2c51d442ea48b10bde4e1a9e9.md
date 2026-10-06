# Multivariate Trees

+   - Best if there are meaningful covariates of interest.

+   - It is unknown what effect non-normality of the outcome variables can have on group formation.

+   - Can be computationally expensive when the number of covariates is large.

+   - In the presence of complex outcome models, it can be difficult to determine parameters are meaningfully different across groups.

+   - The problems with decision trees, most notably instability.

# Mixtures

+   - Heterogeneity is thought to be due to unobserved variables.

+   - Will fit better than multivariate trees.

+   - Non-normality can pose problems (see Bauer & Curran, 2004).

+   - Describing the makeup of each class is less straightforward than in multivariate trees.

+   - Can be difficult to choose among the constraints placed on class variance/covariance.

A ripe area for future research is in comparing these approaches and providing guidance on when algorithm may be most appropriate. Additionally, there is a recent focus on combining the benefits of each algorithm, making the comparison inherent in deriving groups (see Grimm et al., 2022), which is aided by new software developments (see Serang et al., 2020). We expect this to be a hot topic of inquiry in the near future.

# 10.4.1 Further Reading

+   - A number of methods have been developed to examine the effects of covariates in a mixture model after the classes are formed. For a more recent overview of the literature, see Steffmann and Grimm (2018).

+   - Recent research has focused on combining the use of mixture models and decision trees in searching for classes/groups, see Grimm et al. (2022) and the mlTrees package in R for its implementation.