structures by allowing splits in linear combinations of (two) predictors, and fitting more complex (i.e., non-constant) models in the nodes (e.g., k-nearest neighbor or polynomial regression). Although this can lead to much shorter tree structures, the trees themselves are not necessarily simpler to interpret (e.g., is the GUIDE-based regression tree for the Ames housing example based on stepwise regression fits actually that simple to interpret?). Fortunately, the post-hoc interpretation procedures outlined in Chapter 6 are model-agnostic, and allow us to easily interpret various aspects of any supervised learning model (including GUIDE-based decision trees with complex terminal node summaries).

GUIDE is not just for simple classification and regression problems, and can be used in all sorts practical situations, including:

+   - quantile regression;
+   - Poisson regression (i.e., for modeling count data and rates);
+   - multivariate outcomes;
+   - censored outcomes;
+   - longitudinal data [Loh and Zheng, 2013] (e.g., when multiple subjects are continually measured over time);
+   - propensity score grouping;
+   - variable reduction;
+   - subgroup identification [Loh et al., 2015];
+   - and more.

For more, visit Wei-Yin Loh's website at http://pages.stat.wisc.edu/~loh/guide.html. An example of the effectiveness of riluzole, a drug approved for the treatment of ALS (Amyotrophic Lateral Sclerosis) by the US FDA, can be found in Loh and Zhou [2020]g.