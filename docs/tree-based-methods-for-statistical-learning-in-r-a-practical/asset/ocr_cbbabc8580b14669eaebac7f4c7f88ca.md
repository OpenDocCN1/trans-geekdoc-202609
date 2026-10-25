and potential interactions). Note that the techniques discussed in this chapter are model-agnostic, meaning they can be applied to any type of supervised learning algorithm, not just tree-based ensembles. For example, they can also be used to help interpret neural networks or a more complicated tree structure that uses linear splits or non-constant models in the terminal nodes.

The next three sections cover post-hoc methods to help comprehend various aspects of any fitted model:

+   * feature importance (Section 6.1);
+   * feature effects (Section 6.2);
+   * feature contributions (Section 6.3).

# ## 6.1 Feature importance

For the purposes of this chapter, we can think of variable importance (VI) as the extent to which a feature has a “meaningful” impact on the predicted outcome. A more formal definition and treatment can be found in van der Laan [2006]. Given that point of view, a natural way to assess the impact of an arbitrary feature xj is to remove it from the training data and examine the drop in performance that occurs after refitting the model without it. This procedure is referred to as leave-one-covariate-out (LOCO) importance; see Hooker et al. [2019] and the references therein.

Obviously, the LOCO importance method is computationally prohibitive for larger data sets and complex fitting procedures because it requires retraining the model once more for each dropped feature. In the next section, I’ll discuss an approximate approach based on reassessing performance after randomly permuting each feature (one at a time). This procedure is referred to as permutation importance.

# ## 6.1.1 Permutation importance

While some algorithms, like tree-based models, have a natural way of quantifying the importance of each predictor, it is useful to have a model-agnostic procedure that can be used for any type of supervised learning algorithm. This also makes it possible to directly compare the importance of features across different types of models. In this section, I’ll discuss a popular method for measuring the importance of predictors in any supervised learning model called permutation importance.