# Table 12.1 Outlier counts for the Boston Housing variables using 1.5-IQR criteria, percentage of the total data, and correlation coefficients with respect to MEDV.

| Feature set | Number of outliers | Percent (%) | Correlation coefficient (MEDV) |
|---|---|---|---|
| CRIM | 65 | 12.9% | -0.39 |
| ZN | 68 | 13.4% | 0.36 |
| INDUS | 0 | 0.0% | -0.48 |
| CHAS | N/A | N/A | 0.18 |
| NOX | 0 | 0.0% | -0.43 |
| RM | 30 | 5.9% | 0.70 |
| AGE | 0 | 0.0% | -0.38 |
| DIS | 5 | 1.0% | 0.25 |
| RAD | 0 | 0.0% | -0.38 |
| TAX | 0 | 0.0% | -0.47 |
| PTRATIO | 15 | 3.0% | -0.51 |
| B | 77 | 15.2% | 0.33 |
| LSTAT | 7 | 1.4% | -0.74 |
| MEDV | 40 | 7.9% | 1.00 |

headaches for the least squares (LS) method. We now have mounting evidence that we should resort to robust approaches.

One more check can be performed to determine the nature of the apparent outliers for two important variables. The RM variable has a strong positive correlation with MEDV (see Table 12.1) and a scatter plot confirms this, as shown in Figure 12.2. The LSTAT variable has a strong negative correlation with MEDV and a scatter plot in Figure 12.2 confirms this as well. We can observe the $50K homes along the top right and top left portions of the two plots, respectively. More outliers seem to be present for RM compared to LSTAT, but it is not clear if they are outliers or inliers at this stage. Any removal of the inliers would be a mistake so if we were to consider eliminating all $50K homes from the dataset, we may lose valuable information. Again, the idea of removing outliers before any regression is applied can be dangerous as it may lead to lower-quality models and higher prediction errors.

# 12.2.2 Neural Network Architecture

After the preliminary analysis of the data and potential outliers, it is time to decide how to proceed in building a model. For comparison purposes, LC can be used for the robust case, while for the non-robust case, LS can be used. It is possible to use standard linear regression methods but this is a particularly challenging dataset. The option of polynomial expansion of the variables exists to increase the feature space. A more powerful method to tackle this problem is to use a neural network (NN) for linear regression, as shown in Figure 12.3. It has 13 inputs, 1 output and one hidden layer comprised of 39 relu units.