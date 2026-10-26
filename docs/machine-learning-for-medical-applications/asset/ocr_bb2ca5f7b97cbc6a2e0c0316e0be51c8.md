![](bbox=[0.16, 0.1, 0.78, 0.44])

Figure 3: Methods for feature selection in machine learning models.

model. Although filter techniques can handle high-dimensional datasets and are computationally efficient, they miss feature relationships and interactions.

On the other hand, wrapper approaches measure how well the built predictive models, which include different feature subsets, are, so as to assess the importance of a feature. Such examples of wrapper techniques include recursive feature elimination (RFE), forward selection, and backward elimination. These approaches constantly build predictive models, employing different feature combinations, and select the set with the highest model performance. Despite the fact that they can comprehensively capture feature dependencies and interactions, wrapper approaches are often computationally expensive, especially on large-scale datasets with many features.

In general, feature selection is performed during training, when it is used as an embedded technique, where the training selects the feature. Several modern tree-based models such as random forest, stochastic gradient boosting machines, and linear regression techniques such as LASSO, inherently perform feature selection by penalizing less informative features. The computational efficiency and the quality of the prediction of the result are satisfactory for embedded approaches, but the performance of feature selection is appropriate after adjustment of its hyperparameter.

Hybrid methods use embedded, filter, and wrapper techniques to exploit the benefits that each of the three possess. To enhance the ensemble’s stability and robustness, this work incorporates multiple feature selection algorithms into the ensemble feature selection approach. Filter techniques involve using statistical measures to identify the best set of features for a model from the existing data. While $Features