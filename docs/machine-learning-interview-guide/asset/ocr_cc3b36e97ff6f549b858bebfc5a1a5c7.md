used to select the category with the highest probability.

# • Ordinal probit regression:

+   ○ Model structure: Like OLR, ordinal probit regression also works with ordered categories. However, instead of the logistic function, it uses the integral of the standard normal distribution or the probit function.
+   
+   ○ Cumulative probabilities: The probit function is then used to get cumulative probabilities for each of the categories from the weighted sums of the input features.
+   
+   ○ Prediction: As for the predicted category, the one with the highest sum of cumulative probability is chosen, similarly to what OLR does.

OLR stands for ordered logistic regression, which is similar to logistic regression and is an extension of ordinal probit regression that deals with ordered nominal data. Thus, the selection of one or another method can depend on the assumptions made with regard to the data as well as the features of the problem being considered. These methods give an indication of how the ordinal outcomes could be modeled and predicted with regard to the order of the categories.

Question 13: Explain the concept of logistic regression with interaction terms.

Answer: Logistic regression with interaction terms can be defined as the addition of interaction effects of two or more independent variables to the general logistic regression model. The other type of terms, namely the interaction terms, enables the model to estimate how specific variable combinations affect the log-odds of the outcome.