If you do find evidence of autocorrelation, then obviously, you need to employ time series models and techniques, or otherwise, you would have to attempt to adjust the model to cater for such problems of autocorrelation.

# Question 9: What is the purpose of normality tests (for example, Shapiro-Wilk) in linear regression?

Answer: A Shapiro-Wilk test used in linear regression aims at checking whether residuals in the chosen regression model are normally distributed. This is important because several statistical tests and procedures, such as hypothesis tests and confidence intervals, will require the residuals to be normally distributed.

However, it often is a key assumption of normality in linear regression models, since they usually can handle some violations of this assumption mildly, and all the more so if it is a large sample size is being dealt with. As such, the need for analysis of non-normality can be addressed or reduced through the use of the central limit theorem. However, if the deviations are quite extreme, then suggestions may be made for the use of other models, such as generalized linear models.

# Question 10: Describe the steps involved in gradient descent for linear regression.

Answer: The gradient descent is a process used in later and repeated steps to determine the appropriate coefficients (parameters) of the linear regression model. Here are the steps involved in gradient descent for linear regression:

+   - **Initialize coefficients**: Begin with heuristically chosen values of the coefficients of the linear regression model. These initial coefficients can be set to zero or to small random values, close to zero.