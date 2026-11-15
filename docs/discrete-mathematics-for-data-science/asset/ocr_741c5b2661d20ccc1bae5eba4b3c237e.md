y-intercept and so makes interpretation easier. For example, it would only make sense to use an average \(\beta_0\) based on all the predictors if all the data were first normalized.

Unless the dependent variables are, themselves, synthetic products of one another, standardization will not affect the results of a regression, as the equations for the regression coefficients already scale the results into relative terms.

# 20.6 TESTING THE SIGNIFICANCE OF REGRESSION VARIABLES

When performing multivariable linear regression, it is best to only include those independent variables that provide a relatively significant contribution to the model.

One method for determining which independent variables to use is to test the full model, removing one predictor at a time to check the impact of each on the accuracy of the model, also called the *efficacy of the model*.\(^2\)

Another method for determining which independent variables to include involves comparing the y data to each independent variable, one at a time, to look for a significant linear relationship. For each comparison, a *hypothesis test* involving a statistic called *t-statistic* can be performed. A general overview of the hypothesis testing procedure follows:

Formally, the claim that two variables do **not** have a significant relationship is called the *null hypothesis*, and is denoted \(H_0\). In contrast to the null hypothesis is the *alternative hypothesis*, denoted as \(H_1\) or \(H_a\). The alternative hypothesis is the claim that a significant relationship **does** exist between two variables. In a hypothesis test, we decide whether or not to reject the null hypothesis based on the data, or more specifically, based on a *test-statistic* computed from the data. If the test-statistic leads us to reject the null hypothesis, then we have