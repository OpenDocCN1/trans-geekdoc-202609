# 4.3.5 Disadvantages

As advantage I have said that linear models live in their own universe. The sheer **number of ways you can extend the simple linear model is overwhelming**, not just for beginners. Actually, there are multiple parallel universes, because many communities of researchers and practitioners have their own names for methods that do more or less the same thing, which can be very confusing.

Most modifications of the linear model make the model **less interpretable**. Any link function (in a GLM) that is not the identity function complicates the interpretation; interactions also complicate the interpretation; nonlinear feature effects are either less intuitive (like the log transformation) or can no longer be summarized by a single number (e.g. spline functions).

GLMs, GAMs and so on **rely on assumptions** about the data generating process. If those are violated, the interpretation of the weights is no longer valid.

The performance of tree-based ensembles like the random forest or gradient tree boosting is in many cases better than the most sophisticated linear models. This is partly my own experience and partly observations from the winning models on platforms like kaggle.com.

# 4.3.6 Software

All examples in this chapter were created using the R language. For GAMs, the `gam` package was used, but there are many others. R has an incredible number of packages to extend linear regression models. Unsurpassed by any other analytics language, R is home to every conceivable extension of the linear regression model extension. You will find implementations of e.g. GAMs in Python (such as `pyGAM`), but these implementations are not as mature.

# 4.3.7 Further Extensions

As promised, here is a list of problems you might encounter with linear models, along with the name of a solution for this problem that you can copy and paste into your favorite search engine.

My data violates the assumption of being independent and identically distributed (iid).
For example, repeated measurements on the same patient.
Search for **mixed models** or **generalized estimating equations**.

My model has heteroscedastic errors.
For example, when predicting the value of a house, the model errors are usually higher in expensive houses, which violates the homoscedasticity of the linear model.
Search for **robust regression**.

I have outliers that strongly influence my model.
Search for **robust regression**.

I want to predict the time until an event occurs.
Time-to-event data usually comes with censored measurements, which means that for some instances there was not enough time to observe the event. For example, a company wants to predict the failure of its ice machines, but only has data for two years. Some machines are still intact after two years, but might fail later.
Search for **parametric survival models**, **cox regression**, **survival analysis**.

My outcome to predict is a category.
If the outcome has two categories use a **logistic regression model**, which models the probability for the categories.
If you have more categories, search for **multinomial regression**.
Logistic regression and multinomial regression are both GLMs.