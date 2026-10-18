# 20.1.6 Feature engineering and feature selection help make the most of the available information

Feature engineering is the practice of extracting useful/predictive information from existing variables, that is currently in a less useful format. For example, this could be extracting gender from transcribed medical notes, or it could be combining various financial metrics to create an index of market stability. Feature engineering usually requires some domain knowledge and some thought about what features are likely to impact the outcome variable. We first discovered feature engineering in chapter 4, and used it again in chapter 10.

Feature selection, on the other hand, is concerned with removing variables that contribute no or little predictive information to the model. In doing so, we can protect ourselves from both overfitting, and the curse of dimensionality. We learned in chapter 9 that feature selection can be done in two different ways: filter methods and wrapper methods.

Filter methods are computationally less expensive, but are less likely to result in an optimal selection of features. Filter methods rely on calculating some metric of the relationship between each feature, and the outcome variable. This metric could simply be the correlation between each feature and the outcome, for example. We can then simply skim off a specific number or proportion of features that have a weaker relationship with the outcome.

Wrapper methods are more computationally expensive, but are more likely to result in a better-fitting model. Wrapper methods consist of iteratively fitting and evaluating models with different permutations of the predictor variables. The combination of variables that gave the best-performing model is chosen.

Feature engineering and selection are extremely important, arguably more important that your choice of algorithm. You can use the most cutting-edge, high-performing algorithm ever developed, but if your features are not making the most of the predictive information they contain, or there are many irrelevant variables in the data, your model won't perform as well as it should.

If your feature engineering/selection processes are data-dependent, it's important you include them in your cross-validation.