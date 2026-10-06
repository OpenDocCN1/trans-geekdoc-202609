# MRI image Correlation Lasso RFE

![](bbox=[0.137, 0.123, 0.826, 0.243])

**Figure 8.7** Feature importances for volumes of brain structures to predict age at scan. High importances shown in red, low importances in blue. Left: the original MRI image. Correlation: Pearson correlation coefficient between structure volumes and age at scan. Gray matter regions are the most correlated with Lasso: Absolute values of lasso regression weights. RFE: Ranking of the features by recursive feature-elimination algorithm.

+   a. Select four features predictive of age at scan using the F-value and mutual information and print out their names. Do you obtain the same or different features? Can you explain why?
b. Perform model-based feature selection using the lasso model and fit linear regression to the selected features. Calculate performance of your model. Experiment with different thresholds for lasso coefficients to see which one results in the best performance. Print out the names of the selected features.
c. Fit recursive feature elimination with cross-validation (RFECV) and ridge ranking model with alpha=45 to select features. Fit the ridge model with alpha=45 to the selected features, calculate performance and print the number and names of the selected features.