
The formulation in (8.19) for `η` is essentially that of `g(f(x))`; that is, we are taking, in a general sense, a *composite function*, which, as we will see in our discussion of *neural networks* later, allows us to use backpropagation via the chain rule in calculus. Once more, as we do in several other places in the book, in appreciating the nature of *neural networks* it is helpful to see what other methods can be conceived as related or even special cases of that more global framework or approach. We encourage the reader to return to this and other sections in the book where we relate models to *neural networks* once we discuss and develop them more thoroughly later.

### 8.7.5 Linking the Logit to the Additive Logistic Model

We have seen that generalized additive models are a way to deal with nonlinearities in our data via nonparametric estimation. Perhaps not surprisingly at this point, there is a natural connection between the logit link function and the additive logistic regression model ([Hastie 等，2009](#ref.xhtml#re_CIT000145)). Consider the logit once more, that is, the log of the odds,325

$$\\log\\left( \\frac{\\mu\\left( x \\right)}{1 - \\mu\\left( x \\right)} \\right) = \\alpha + \\beta\_{1}x\_{1} + \\cdot \\cdot \\cdot \\beta\_{p}x\_{p}$$

(8.20)

where now `μ(x)` is the probability of the event of interest (e.g., survival) and 1 − `μ(x)` the probability of its complement (e.g., death). The *additive logistic regression model* exchanges each linear term by a more general and to-be-defined functional form `f[1]` through `f[p]`, generating the following function:

$$\\log\\left( \\frac{\\mu\\left( x \\right)}{1 - \\mu\\left( x \\right)} \\right) = \\alpha + f\_{1}x\_{1} + \\cdot \\cdot \\cdot f\_{p}x\_{p}$$

(8.21)

As before, not all of the `f[1]x[1] + ... + f[p]x[p]` need to be nonlinear. As was the case where the generalized additive model replaced terms in the general linear model with nonparametric estimates, the generalized additive model likewise replaces the parametric terms in the logistic generalized linear model with smooth nonparametric estimates.

The package `mgcv` ([Wood, 2017](#ref.xhtml#re_CIT000391)) can be used in `R` for fitting generalized additive models.

## 8.8 Overview and Recap of Nonlinear Approaches for Nonlinear Responses

The purpose of this chapter thus far has been to introduce and survey ways of modeling and accounting for nonlinearity or unknown structure in data where the response variable is something other than a continuous variable and instead binary or polytomous. As mentioned from the outset, while many or even most statistical models are linear in nature, many if not most scientific *phenomena* are *nonlinear* or at minimum, unknown, such that we may be better off allowing the data to “speak for itself.” A powerful way to understand the range of nonlinear and nonparametric methods is to consider how far we wish to depart from linearity to capture nonlinear effects. In this section, we provide a global review of the strategies we have surveyed so far. To set things up for this review, consider the basic scatterplot ([图 8.5](#c8.xhtml#f8.5)) with a single response variable and two predictors.326

![图 8.5 `y` 作为 `x` 和 `z` 的函数的通用散点图。返回正文。⏎](images/fig8.5.jpg)

*图 8.5* `y` 作为 `x` 和 `z` 的函数的通用散点图。[返回正文。⏎](#c8.xhtml#re_f8.5)

The central question we wish to ask is:

> *What are the options for modeling this data where `y` is hypothesized as a function of `x` and `z`?*

We now review and summarize the ways of modeling such data discussed in this and the previous chapter, which include *linear*, *nonlinear*, as well as *nonparametric* approaches. For each of the following, we encourage the reader to keep the plot in [图 8.5](#c8.xhtml#f8.5) in mind to help conceptualize how each of the following approaches would address this data:

1. 1\. *线性回归* – This classic approach will ignore any nonlinearity in the data and simply model a linear function to the data points. This can be a useful strategy if we are not that concerned about any nonlinear trend that may or may not be present in the data. Linear regression can be interpreted as a special case of the *general linear model*, which in turn can be considered a special case of the more *general nonlinear model* framework.

2. 2\. *主成分回归* – In this approach, we generate principal components on the predictor side and use those component scores to predict the response variable. Recall that one limitation to this approach is that the components generated on the predictor side are not those necessarily maximally related to the variance in the response. That is, *there is no guarantee that the components generated vary in the directions of the response*. Still, this approach can be useful for reducing the data on the predictor side. However, the approach is still linear and will inadequately address any nonlinearities in the data. For the data depicted in [图 8.5](#c8.xhtml#f8.5), the approach would not be fruitful since we only have two predictors. However, given a much larger number of predictors, dimension reduction on the predictor side before predicting the response may be an effective strategy.

3. 3\. *偏最小二乘回归* – As was the case for principal components regression, we seek to reduce the set of predictors to a smaller set that can be used for prediction of the response. In doing so, PLS, unlike PCR (principal components regression), attempts to incorporate both the response and predictor sides of the equation.

4. 4\. *多元降秩回归* – Many models can be conceived as a special case of the wider reduced-rank regression problem. This context is more pedagogical than applied, as most models we will fit will not go by this name.

5. 5\. *正则化* (*ridge*, *lasso*, *elastic net*) – This approach seeks to regularize the model by the concept of *shrinkage*, where one or more predictors have weights driven toward (or *to*) 0. This serves to simplify the model so that predictors that are not essential are minimized in importance. While the ridge estimator will drive weights *toward* 0, lasso will drive them exactly *to* 0, making lasso a kind of variable-selection procedure. Elastic net can be interpreted as a kind of compromise between the ridge and the lasso.

6. 6\. *最小角回归* – This takes a linear and stepwise approach, but instead of including variables at each step, estimated parameters are increased in a direction *equiangular* (in part, motivating the name *least-angle*) to each one’s correlations with the residual. That is, least-angle regression only includes that “part” of a predictor that is “next up” in terms of importance (at least, *statistical* importance) at each step.

7. 7\. *典型相关分析* – This relates each side of the equation just as in bivariate linear correlation, where each side is a set of variables. A Pearson Product-Moment correlation is a special case of the canonical correlation where each side of the equation consists of very simple linear combinations, those of only a single variable. That is, the “variate” in this case is a single variable on each side.327

8. 8\. *多项式回归* – This seeks to model a polynomial that is more general than a degree 1 polynomial (line). This is a *global approach* that seeks to capture the *global nonlinearity* or trend of the data. Linear models can be considered a special case of the wider and more general polynomial regression problem. Linear regression can generally be considered a special case of polynomial regression.
