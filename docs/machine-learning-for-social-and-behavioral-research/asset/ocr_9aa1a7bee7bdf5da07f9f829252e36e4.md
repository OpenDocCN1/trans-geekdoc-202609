# The Practices of Machine Learning

with a high propensity to overfit. This was seen recently in a paper by Jacobucci, Littlefield, Kleiman, & Steinley (2021), where extreme amounts of bias were found when the random forests algorithm was paired with the optimistic corrected bootstrap.

There have been a number of studies that have compared the bias and variance (detailed) of CV and bootstrapping, but it has generally been difficult to evaluate the results the differences in which algorithms were used, types of data (simulation or benchmark datasets), and which methods of resampling were tested. Across studies, a general recommendation has been to use repeated k-fold CV when the sample size is not small (a few hundred), and the bootstrap when the sample size is small. Just as in the no-free theorem, no method has performed universally across various conditions of study, as seen in a recent study by Xu and Goodcaire (2018). Further, this study concluded that when using the bootstrap, the number of repeats should be large (> 100).

While the use of repeated k-fold CV or bootstrap sampling is recommended for model assessment, nested CV should be used when conducting model selection and assessment. In nested CV, it does not seem to matter whether k-fold CV or bootstrap sampling is used for the outer and inner loops. The main drawback to this approach is a lack of easy implementation in R. As of this writing, users need to program their own CV script.

Regardless of the resampling method used, it is extremely important to use the same resampling method when comparing results across models or algorithms. Depending on dataset characteristics, each resampling method is likely to be at least biased. Thus, when performing selection it is important to use the same resampling method so that the bias is consistent across models or algorithms.

# 3.6 Classification

In modeling binary outcomes (classification), the methods and recommendations detailed above apply equally well as they do to continuous outcomes. The one caveat is in the presence of imbalanced (skewed) binary outcomes. We cover this further in the Imbalanced Outcomes section. In this section, our focus is on detailing the many prediction performance metrics that are different with binary outcomes.