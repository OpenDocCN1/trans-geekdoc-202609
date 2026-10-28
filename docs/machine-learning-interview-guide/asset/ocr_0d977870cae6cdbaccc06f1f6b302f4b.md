replacement. It is to be noted that bootstrapping can be done on either row or the column. This appeared to work fine and the concept of bootstrapping can be applied in a wide range of areas ranging from model assessment through the resampling in cross-validation. Here is an explanation of the bootstrapping method and how it can be used in cross-validation:

+   - **Bootstrapping method**:
+     - **Technique**: The technique of bootstrapping entails a random sampling of *n* data points from the original database with replacement. This implies that each value on the original dataset has the probability of being picked several times while other values will not be picked at all. This generates a new set of random data.
+     - **Creation of bootstrap samples**: The outcome is a bootstrap sample that has some of the records repeated and some missing out. This is done several times to produce other bootstrap samples.
+     - **Variability and estimation**: A valuable tool when it comes to estimating the sampling distribution of a statistician; be it the variation or the mean or another parameter. It assists in determining the amount of variation in the statistic where the distribution of original values is unknown or complicated.

Bootstrapping can be incorporated into the cross-validation process in the following several ways:

+   - **Bootstrapped cross-validation (Bootstrapped K-fold)**: As opposed to utilizing a predetermined, non-variant, *K* for model assessment that happens in K-fold cross-validation, bootstrapping allows the creation of *K* folds randomly. This process makes it possible to