used in estimating the degree to the output of the models corresponds to real values.

The pointers of MSE for which it is widely used are as follows:

+   - MSE calculates the mean of the squared errors of the regression model’s predictions in order to present the level of accuracy of the said predictions. It is a measure that enables one to determine the global quality of the model’s predictions by calculating a single value.
+   - MSE is more concerned with the big errors because the squared difference increases with the increase in the value of the error. This makes it responsive to distortions or large differences between the anticipated/inferred values and the factual ones; in other words, those models that make drastic mistakes will be punished.

The other flavor of the MSE algorithm is RMSE. RMSE is the square root of MSE hence it is an average of the square of the differences. RMSE is used to provide the idea of accumulated error by presenting it in the same unit of measure as the target variable.

In practical applications, a lesser value of MSE (or RMSE) suggests that it is easier for the regression model to minimize the prediction errors and thus, the model is capable of offering a closer fit to the data. Nonetheless, like most measures of dispersion used to calculate performance, it should be noted that MSE is rather influenced by outliers, and therefore, the availability of a limited number of large or significant figures will be much more critical than when calculating the average.

# Question 4: Can you explain the interpretation of R-squared in regression evaluation and its limitations?