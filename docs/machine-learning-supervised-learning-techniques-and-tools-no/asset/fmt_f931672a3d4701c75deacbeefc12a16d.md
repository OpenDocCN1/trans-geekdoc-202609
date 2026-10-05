
Another type of limited dependent variables are those caused by data censoring. A censored regression model is one whose dependent variable is censored above (upper censoring) or below (lower censoring) some value, i.e. the dependent variable is not observed for a part of the population. In censored regression models the underlying dependent variable is approximately continuous, but is lower or upper censored, due to the way we collect the data or to institutional constraints. A truncated regression model is similar to a censored regression model, but has one important difference: in a truncated regression model, we do not have the data about some important segment of the population. This is usually the case when a sample targets a particular subset of the population and, perhaps because it is costly, ignores the rest of the population. This is a particular case of the general problem of sample selection, where we observe a non-random sample of the underlying population.

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.2 DISCRETE CHOICE MODELS

![image](d2d_images/chapter_title_below.png)

The functional expression of the multiple regression analysis model is ![image](d2d_images/image686.png). Multiple regression admits the possibility of working with discrete rather than continuous dependent variables to allow the modelling of discrete phenomena. When the dependent variable is a discrete variable reflecting individual decisions in which the choice set consists of separate and mutually exclusive alternatives, we are dealing with discrete choice models. When the dependent variable is discrete and takes only a small number of values, it does not make sense to treat it as if it were a continuous variable and it is usually of interest to characterise the probability that an agent takes a certain discrete decision, conditional on the values of certain explanatory variables. These distribution functions that characterise probabilities for each value of the explanatory variables are usually non-linear and do not usually have an analytical solution, so it is usually necessary to resort to numerical methods. Discrete choice models in which the choice set has only two possible alternatives are called binary choice models. When the choice set has several discrete values, these are called multiple choice models or multinomial models.

Discrete choice models are called count data models when the values of the discrete dependent variable are numbers that do not reflect categories. In case the numerical values of the discrete dependent variable reflect categories, the models are called categorical discrete choice models, and are usually classified into ordered categorical discrete choice models (the numerical values have no quantitative meaning and reflect an ordering of categories) and unordered categorical discrete choice models (the numerical values reflect only categories).

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.3 BINARY DISCRETE CHOICE MODELS

![image](d2d_images/chapter_title_below.png)

Within the discrete choice models in which the choice set has only two mutually exclusive possible alternatives, we will consider the linear probability model, the `Logit` model and the `Probit` model.

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

## 3.3.1 Linear probability model

![image](d2d_images/chapter_title_below.png)

![Texto, Carta Descripción generada automáticamente](d2d_images/image296.png)

We are now dealing with the linear probability model, where, for example, `β1` measures the variation in the probability of "success" (`Y = 1`) for a unit variation in `X1` (all else constant).

As `Y` is a Bernouilli random variable:

![Texto, Carta Descripción generada automáticamente](d2d_images/image189.png)

We are then faced with a model with heteroscedasticity because the error variance is not constant, since for each value of `X1 ,...,Xk`, the error variance has a different value (`V(u)` is not constant). Moreover, `Y` is a Bernouilli variable, so that the normality hypothesis is not satisfied either. This makes it necessary to estimate these models by an alternative method to ordinary least squares, for example, using maximum likelihood estimators or generalised least squares.

After estimating the linear probability model we have that:

![image](d2d_images/image431.png)

can be interpreted as an estimate of the probability of "success" (that `Y = 1`). In some applications it makes sense to interpret ![image](d2d_images/image086.png) as the probability of success when all `X'sj` are worth 0.

Another important limitation of the linear probability model is that for certain combinations of the explanatory variables `X1 ,...,Xk`, the estimated probabilities may be greater than zero or less than one.

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

## 3.3.2 Probit and Logit models

![image](d2d_images/chapter_title_below.png)

We can consider `Logit` and `Probit` models as binary response models:

––––––––

![image](d2d_images/scene_break.png)

![image](d2d_images/image014.png)

which, to avoid the problems of the linear probability model, are specified as `Y = G(Xβ)`, where `G` is a function that takes values strictly between 0 and 1 (`0<G(Z)<1`) for all real numbers `z`. According to the different definitions of `G` we have the different binary choice models.

![Texto, Carta Descripción generada automáticamente](d2d_images/image631.png)

The `Probit` and `Logit` models, as they are non-linear models, cannot be estimated by `OLS` and maximum likelihood methods have to be used.

Suppose we have `n` identically and independently distributed observations (random sample) that follow the model:

![Texto Descripción generada automáticamente](d2d_images/image030.png)

The `MV` estimator of `β` is the one that maximises the logarithm of the likelihood function:

![image](d2d_images/image091.png)

which will be a consistent, asymptotically normal and asymptotically efficient estimator.

The first-order conditions shall be:

![Diagrama Descripción generada automáticamente con confianza media](d2d_images/image280.png)

where `g(.)` is the normal or logistic density function (derived from the distribution function).

The non-linearity of the problem means that to obtain the `MV` estimator from `β` we need to apply an iterative algorithm and obtain the estimator by iterative numerical methods. By means of the Scoring algorithm we have:

![Diagrama, Texto Descripción generada automáticamente](d2d_images/image044.png)

To perform hypothesis tests in `Logit` and `Probit` models we will take into account that the square root of the elements of the main diagonal of the asymptotic covariance matrix are the (asymptotic) standard errors of each of the ![image](d2d_images/image379.png), which we can use to construct t-statistics (which will have an asymptotic normal distribution) or approximate confidence intervals for each parameter. We can also test several restrictions simultaneously. Usually, what we are interested in are exclusion restrictions, so this is what we are going to focus on.

To test the null hypothesis that a set of parameters is equal to zero we can use several procedures:

*   Wald statistic. It is asymptotically distributed as a Chi-square with `q` (number of restrictions) degrees of freedom and is provided by most programs.
