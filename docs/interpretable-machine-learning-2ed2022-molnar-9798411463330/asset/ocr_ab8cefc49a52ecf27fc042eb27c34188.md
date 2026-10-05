# 7.3 FEATURE INTERACTION

![](bbox=[0.28, 0.13, 0.822, 0.442])

Figure 7.19: The interaction (H-statistic) for each feature with all other features for a support vector machine predicting bicycle rentals. Overall, the interaction effects between the features are very weak (below 10% of variance explained per feature).

In the next example, we calculate the interaction statistic for a classification problem. We analyze the interactions between features in a random forest trained to predict cervical cancer, given some risk factors.

After looking at the feature interactions of each feature with all other features, we can select one of the features and dive deeper into all the 2-way interactions between the selected feature and the other features.

# 7.3.4 Advantages

The interaction H-statistic has an underlying theory through the partial dependence-composition.

The H-statistic has a meaningful interpretation: The interaction is defined as the share of variance that is explained by the interaction.

Since the statistic is dimensionless, it is comparable across features and even across models.

The statistic detects all kinds of interactions, regardless of their particular form.