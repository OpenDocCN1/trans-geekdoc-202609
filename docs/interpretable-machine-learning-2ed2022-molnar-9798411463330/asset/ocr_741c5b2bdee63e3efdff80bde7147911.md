# 7.5 Permutation FEATURE IMPORTANCE

![](bbox=[0.278, 0.137, 0.813, 0.442])

Figure 7.26: The importance of each of the features for predicting cervical cancer with a random forest. The most important feature was Hormonal.Contraceptives..years., Permuting Hormonal.Contraceptives.,years., resulted in an increase in 1-AUC by a factor of 6.13

Feature importance provides a highly compressed, global insight into the model behavior.

A positive aspect of using the error ratio instead of the error difference is that the feature importance measurements are comparable across different problems.

The importance measure automatically takes into account all interactions with other features. By permuting the means that the permutation feature importance takes into account both the main feature effect and the interaction effects on model performance. This is also a disadvantage because the importance of the interaction between two features is included in the importance measurements of both features. This means that the features do not add up to the total drop in performance, but the sum is larger. Only if there is no interaction between the features, as in a linear model, the importances add up approximately.

Permutation feature importance does not require retraining the model. Some other methods suggest deleting, retraining the model and comparing the error result. Since the retraining of a machine learning model can take a long time, “only” permuting a feature can save a lot of time. Importance methods that retain the model with a subset of features appear intuitive at first glance, but the model with the reduced data is meaningless for the feature importance. We are interested in the feature importance of a fixed model.