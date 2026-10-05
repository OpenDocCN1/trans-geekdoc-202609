

Likewise, if `Xj` is a continuous variable, we can compute the partial effect on the expected value of `Y`. This partial effect can be decomposed into two parts, the effect on the mean value of `Y` in the positive part of the distribution, and the effect on the probability in the other part of the distribution. We have (**):

![Tabla Descripción generada automáticamente con confianza media](d2d_images/image389.png)

This value of the effects can be easily estimated using the MV estimates of `β` and `σ` for the mean values of `X` or for other values of interest in our applications.

The Tobit model is based on the assumptions of normality and homoscedasticity in the latent model. When these assumptions are not met, the problem is not only the inconsistency of the MV estimator of `β` and `σ`. Even the expressions of the conditional expectation are not adequate. The model can be generalised to allow for certain forms of heteroskedasticity and non-normality. There are also tests for certain types of normality and heteroscedasticity, for example:

![image](d2d_images/image377.png)

But, for mild breaches of the assumptions, it is thought that the Tobit model can generate a good approximation of the partial effects.

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.7.3 Tobit model with censorship in the data

![image](d2d_images/chapter_title_below.png)

We have analysed the Tobit model for corner solution, but we can generalise to the case where there is censoring of any kind in the data. The most general case is when the variable of interest is continuous but is censored above (right censoring) or below a value (left censoring) which need not be zero.

We can write the Tobit model as:

![image](d2d_images/image243.png) which can also be written as:

![Diagrama, Texto Descripción generada automáticamente con confianza media](d2d_images/image570.png)

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.7.4 Maximum Likelihood (MV) estimation of the censored Tobit model

![image](d2d_images/chapter_title_below.png)

If we had a random sample we could estimate `β` by OLS and perform inference in the usual way, but censoring the data causes us problems of inconsistency in OLS estimation (with all observations or without the censored ones). Given a random sample, we can obtain consistent estimates from `β` and `σ` if we estimate by OLS. For uncensored observations, `Y = Y*`, the density of `Y` is the same as that of `Y*`. For censored observations we have:

![image](d2d_images/image465.png)

We will calculate the logarithm of the likelihood function and perform the MV estimation. In this model the `βj` are interpreted as in the linear regression model.

The expression for the logarithm of the likelihood function for a sample of size `n` is as follows:

![image](d2d_images/image353.png)

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.7.5 Two-stage ordinary least squares estimation of the censored Tobit model

![image](d2d_images/chapter_title_below.png)

Although the estimation of the OLS-censored Tobit model cannot be done directly, we can use the following two-step method:

1. The dichotomous dummy variable is constructed which is worth 1 for positive values of `Y` (`Yi > 0` or `Yi > c`) and which is worth 0 for values of `Y` less than or equal to zero (`Y i≤ 0` or `Y i≤ c`). The corresponding Probit model is estimated and the Mills ratio is obtained from the estimated values:

![image](d2d_images/image026.png)

1. We estimate by OLS the model ![image](d2d_images/image268.png)

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.8 SAMPLE SELECTION: TRUNCATED MODELS

![image](d2d_images/chapter_title_below.png)

A truncated regression model is similar to a censored regression model, but has some important differences: in a truncated regression model, we do not have the data about some important segment of the population. This is usually the case when a sample targets a particular subset of the population and, perhaps because it is costly, ignores the rest of the population. This is a particular case of the general problem of sample selection, where we observe a non-random sample of the underlying population.

Suppose we have an underlying population model that satisfies the assumptions of the classical regression model:

![image](d2d_images/image476.png)

If we had a random sample of the population, the most efficient estimation procedure would be OLS. However, in the case of the truncated model the problem is that we do not have a random sample, because our observed sample has a bound of the type `Yi ≤ ci` or `Yi > ci` (Truncated Tobit Model). If we want to estimate `β` and `σ` we need to know the distribution of `Yi` given `X` and that `Yi ≤ ci` or `Yi > ci`. That is:

![Texto, Carta Descripción generada automáticamente](d2d_images/image051.png)

where `f(Y|X ,iβσ² )` is the density of a normal with mean `Xiβ` and variance `σ²` and `F(ci |X ,iβσ² )` is the distribution function of a normal with mean `Xiβ` and variance `σ` evaluated at `ci`.

If we divide the density of `Y` given `X` by the probability that `Yi ≤ ci` or `Yi > ci` (given `X`), we take logarithms and sum for all `n` maximising the result we obtain the MV estimators of `β` and `σ²`, which will be consistent and asymptotically normal. But if the assumptions of homoscedasticity and normality are not met, the MV estimators will be inconsistent.

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.8.1 Truncated Tobit model estimation

![image](d2d_images/chapter_title_below.png)

Let us suppose that we have a model `Yi = Xiβ + ui` and that the variable `Yi` is truncated from a certain boundary or barrier `a` (it only takes values from the barrier onwards). We have:

![Diagrama Descripción generada automáticamente](d2d_images/image373.png)

The truncated variable model can be specified as follows:

![image](d2d_images/image343.png)

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.8.2 Partial effects in the truncated Tobit model

![image](d2d_images/chapter_title_below.png)

This involves quantifying the effect of a unit increase of a regressor `Xk` on the explained variable, which will be given by the partial derivative of its expected value with respect to the variable `Xk` we have:

![Diagrama Descripción generada automáticamente](d2d_images/image679.png)

Then the marginal effect of variable `Xk` with respect to the explained variable is equal to the estimated coefficient `βk` multiplied by the correction factor ![image](d2d_images/image670.png) being:

![Imagen de la pantalla de un celular con letras Descripción generada automáticamente con confianza media](d2d_images/image376.png)

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.8.3 Maximum Likelihood (MV) estimation of the truncated Tobit model

![image](d2d_images/chapter_title_below.png)

The likelihood function of the truncated regression model is calculated from the density function:

![image](d2d_images/image008.png)

