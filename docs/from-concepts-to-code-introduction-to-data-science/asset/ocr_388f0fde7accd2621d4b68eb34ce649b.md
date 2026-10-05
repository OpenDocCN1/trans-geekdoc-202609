Note that 0 is the zero vector. Next, we rearrange:

```
$$$X^T y = X^T X \beta$$
```

This produces the *normal equations*, the last step is to solve for $\beta$. We multiply the left by the inverse of the matrix $X^T X$. This is done to each side of the equation:

```
$$$\beta = (X^T X)^{-1} X^T y$$
```

This section required knowledge of linear algebra and matrix derivatives. A helpful reference is [42]. The important part is to remember the matrix formula for the parameter estimates. This formula makes it possible to solve the linear regression problem for any number of parameters.

# 13.6 Exercises

Exercises with solutions are marked with ($\S$). Solutions can be found in the book.materials folder of the course repo at this location:

https://github.com/PredictionNN/intro_data_science_course/

+   1. What assumptions are made in the linear regression model?
2. True or False: You have a system of linear equations with more equations than unknowns. This system can be solved exactly.
3. True or False: The linear regression model uses a weighted combination of predictors to closely match the target values.
4. True or False: An intercept term adds flexibility to the linear regression model.
5. Explain the difference between residuals and errors in the context of regression.
6. Explain how the parameters of a linear regression model can be estimated. The discussion should include the concept of critical points.
7. True or False: When estimating the parameters of a simple linear regression model, it is necessary to compute partial derivatives.
8. Consider a simple linear regression model where the predictor is uncorrelated to the response variable. What do you expect will be the value of the slope parameter?