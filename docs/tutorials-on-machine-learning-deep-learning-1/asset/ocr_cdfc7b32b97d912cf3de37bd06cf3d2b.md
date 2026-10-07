# Simple Linear Regression

y = b_0 + b_1*x_1

# Multiple Linear Regression

Dependent variable (DV) Independent variables (IVs)

y = b_0 + b_1*x_1 + b_2*x_2 + ... + b_n*x_n

# 2.2.3 Multiple Linear Regression Assumptions

**ASSUMPTIONS:** Before building a linear regression model you need to check that these assumptions are true.

# Assumptions of a Linear Regression:

+   1. Linearity
2. Homoscedasticity
3. Multivariate normality
4. Independence of errors
5. Lack of multicolinearity

If you ever need to build a linear regression make sure you don't just follow the steps presented here.

First need to check the assumptions of the linear regression and make sure that they are correct when you're building your regression model.

And then you can only proceed and be sure you're building a good linear regression model.

[1] **Linearity**: There must be a linear relationship between the *dependent variable* and the *independent variables*.

**Scatterplots** Show whether there is a linear or curvilinear relationship.

[2] **Homoscedasticity**: This assumption states that the variance of error terms is similar to the values of the independent variables.

[3] **Multivariate normality**: Multiple Linear Regression assumes that the *residuals* (the *differences between the observed predicted values* of the *dependent variable y*) are *normally distributed*

[4] **Independence of errors**: Multiple Linear Regression deman that the *errors* (the *differences between the dependent variable y* and the *predicted value y*) are *independent*

[5] **Lack of multi-linearity**: Multiple Linear Regression assumes that the *independent variables* are not *highly correlated* with each other. This assumption is tested using *Variance Inflation Factor (VIF)* values.

# 2.2.4 Dummy Variables

In following *profit* is our dependent variable and the rest ones are all *Independent* variables.

What we place in equation for the *State* column because we don't have numerical values here

First need to *go through* the *column* and find all the *different categories* that you. For every *single category* that you find, need to create a new column. Then in each category-column 1 where corresponding matching category appears and 0 for unmatched.