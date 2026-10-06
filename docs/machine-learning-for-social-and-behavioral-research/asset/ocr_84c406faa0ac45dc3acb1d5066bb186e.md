# 70 Machine Learning for Social and Behavioral Research

**FIGURE 3.18.** The precision recall curve and AUPRC value from the logistic regression model.

![](bbox=[0.273, 0.206, 0.663, 0.442])

# 3.8 Conclusion

**Beyond Continuous or Binary Outcomes** This chapter has discussed the common functions and model metrics for continuous (Gaussian) and binary outcomes. The outcome type influences two primary aspects of modeling: 1) the fit function paired with each algorithm, and 2) the model metric used to evaluate the model. For point #1, the main limitation occurs at the software level, as most machine learning algorithm packages only include fit functions to continuous and binary outcomes. Note that in R, this is generally referred to as the argument family. Some packages and functions, such as glm, allow for count, ordinal, and survival (cox) outcomes. Sometimes there are additional packages that implement algorithms for a specific type of outcome, such as the ordinalForest package (Hornung, 2021). For aspect #2, it is often less straightforward, and specific methods have been developed for interpreting the relationship between the outcome and predictions outside of continuous or binary. For instance, for multinomial or ordinal outcomes, one can use the AUC for a single class versus single or multiple classes, but this results in multiple AUC values. Additionally, while some methods have been developed, for instance to create a single AUC for ordinal outcomes (DeCastro, 2019), they often aren't implemented as R packages.