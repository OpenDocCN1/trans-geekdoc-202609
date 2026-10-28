step, the results should be checked for multicollinearity in order to avoid problems in interpreting the outputs.

+   - **Large sample size**: One should note that logistic regression is known to work better with bigger samples. Regarding small datasets, one should be careful as it may overfit the model and regularization can be used to handle this scenario.

Some ways to check assumptions are:

+   - **Residual analysis**: Look at residuals for patterns. The residuals are the difference between the observed and the predicted values. There is no discernible pattern to follow for the adherence to assumptions. We need to keep in mind that the residual from linear regression do not behave in the same way, like logistic regression. There are some concepts like Pearson residuals and deviance residuals which can be used.
+   - **Cook's distance**: Measures the influence of each data point on the fitted model. Values greater than 1 indicate potential influential points.
+   - **Hosmer-Lemeshow test**: If the predicted probabilities are presented, then the goodness of fit can be checked by dividing the values into groups and comparing them with the observed results.
+   - **Variance inflation factor (VIF)**: To control for multicollinearity, use VIF to determine if there is a problem. This typically ranges from ten and above to signify that the variables are strongly related to each other.
+   - **Graphical exploration**: In addition to checking for linearity, plot predictor variables against the log-odds or the predicted probabilities when the events are relatively rare.