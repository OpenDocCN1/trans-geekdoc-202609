# 10.2 Theory-based inference for simple linear regression 383

Observe how the spread of the residuals increases as the regressor increases. Lack of constant variance is also known as heteroskedasticity. When heteroskedasticity is present, some of the results such as the standard error of the least-square estimators, confidence intervals, or the conclusion for a related hypothesis test would not be valid.

What is the conclusion?

We did not find conclusive evidence against any of the assumptions of the model:

+   1. Linearity of relationship between variables
2. Independence of the error terms
3. Normality of the error terms
4. Equality or constancy of the variance

This does not mean that our model was perfectly adequate. For example, the residual plot was a null plot and had some clusters of points that cannot be explained by the model. But overall, there were no trends that could be considered clear violations of the assumptions and the conclusions we get from this model may be valid.

# What do we do when the assumptions are not met?

When there are clear violations of the assumptions in the model, all the results found may suspect. In addition, there may be some remedial measures that can be taken to improve the model. None of these measures will be addressed in-depth as this material extends the scope of this book, but we briefly discuss potential solutions for future reference.

When the Linearity of the relationship between variables is not met, a simple transformation of the regressor, the response, or both variables may solve the problem.

If not, alternative methods as spline regression, generalized linear models, or non-linear models may be used to address these situations. When additional regressors are available, including other regressors as in multiple linear regression may produce better results.

If the Independence assumption is not met, but the dependency is established by a variable within the data at hand, linear mixed-effects models can also be used. These models may also be referred to as hierarchical or multilevel models.

Small departures of the Normality of the error terms are not too concerning and most of the results, including those related to confidence intervals and hypothesis tests, may still be valid. On the other hand, when the number of violations to the normality assumption is large, many of the results may no longer be valid. Using the advanced methods suggested earlier here may correct these problems too.

When the Equality or constancy of the variance is not met, adjusting the variance by adding weights to individual observations may be possible if relevant information is available that makes those weights known. This method is called linear regression or weighted least squares, and it is a direct extension of the model we have