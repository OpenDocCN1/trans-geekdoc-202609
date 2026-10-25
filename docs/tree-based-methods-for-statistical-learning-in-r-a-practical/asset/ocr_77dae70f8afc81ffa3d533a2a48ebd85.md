# 8.2.0.2 Always a regression tree?

Another subtle difference from bagging or RFs is that GBMs always use regression trees for the base learner, even for classification problems! It makes sense if you think about it: gradient tree boosting involves fitting a tree to the negative gradient of the loss function (i.e., pseudo residuals) at each iteration, which is always ordered and treated as continuous.

# 8.2.0.3 Priors and missclassification cost

In Section 2.2.4, I discussed how CART can naturally incorporate specific class priors and unequal misclassification costs (through a loss/cost matrix) when used for classification. Unfortunately, these concepts do not carry over to GBMs since the base learners are always regression trees; hence, there is no concept of false positives or negatives. One workaround is to use loss functions that incorporate case weights, which would allow us to give more weights to different subsets of the data (e.g., the underrepresented class). For example, we can incorporate case weights into the LS loss function by using

\(\frac{1}{\sum_{i=1}^N w_i} \sum_{i=1}^N w_i [y_i - f(\boldsymbol{x}_i)]^2 ,\)

where \(\{w_i\}_{i=1}^N\) are positive case weights that affect the terminal node estimates. For example, a terminal node in a regression tree with values 2, 3, and 8 would be given estimate of (2 + 3 + 8) / 3 = 4.333 under equal case weights (the default). However, if the corresponding case weights were 1, 5, and 1, then the terminal node estimate would become [(1 × 2) + (5 × 3) + (1 × 8)] / (1 + 5 + 1) = 3.571. See Krieger and Berk [2010] for an example on boosted quantile regression with case weights for small area estimation. The discussion in Berk [2008, Sec. 6.5] is also worth reading.

# 8.3 Hyperparameters and tuning

Gradient tree boosting provides a powerful and flexible approach to predictive modeling. The flexibility in choosing a loss function allows you to fit a rich class of models to all kinds of response outcomes. The flexibility and state-of-the-art performance come at the price of a relatively large number of tuning parameters, which fall into two categories: boosting-specific and tree-specific hyperparameters. These will be discussed in the next two sections. Several modern implementations of GBMs include even more tunable