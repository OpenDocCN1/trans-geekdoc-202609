
其中![image](img/image369.png)是一个未知参数。如果![image](img/image424.png)我们有泊松方差假设。如果![image](img/image671.png)我们有过度离散，这在许多应用中都会发生。如果![image](img/image671.png)我们有欠离散，这在经验应用中很少见。

在方差与均值成比例的假设下，很容易调整通过最大似然得到的泊松标准误。它们必须乘以![image](img/image525.png)，其中![image](img/image301.png)是![image](img/image301.png)的相合估计量：

![image](img/image121.png)

这样得到的标准误称为 `GLM`（广义线性模型）标准误。这些标准误是在方差与均值成比例的假设下得到的，但也可以在不限制方差的情况下获得泊松模型 `CMV` 估计量的标准误。

在泊松分布的假设下，对于排除限制检验，我们可以使用似然比检验：

![image](img/image163.png)

它渐近服从自由度为 `q` 的卡方分布。

在方差与均值成比例的假设下，要进行排除限制检验，只需将似然比检验除以![image](img/image494.png)即可得到非受限模型（`CMV` 统计量）。为了衡量这些模型的拟合优度，可以使用定义为 `Yi` 与![image](img/image547.png)之间的相关系数的平方的 `R²`。它具有始终介于 0 和 1 之间的优点。

### 3.6.2 负二项回归模型

还有其他用于计数数据的回归模型，使用推广泊松的分布，例如使用负二项分布。这就是负二项回归模型。该模型用于过度离散的情况，因为假设 `V(Y|X) = σ² E(Y|X) = (1+η²) E(Y|X)`。在这种情况下，参数![image](img/image007.png)和![image](img/image211.png)通过最大似然法联合估计。为了使估计量相合且有效，必须满足负二项假设。如果我们对固定的![image](img/image211.png)估计![image](img/image007.png)，只要 `E(Y|X)` 设定良好，估计量就会相合。

### 3.6.3 指数回归模型

在指数回归模型中，参数使用指数分布通过最大似然法估计。如果 `E(Y|X)` 设定良好，即使分布不是指数分布，估计量也会相合（与其他 `CMV` 估计量类似）。为了得到 `GLM` 标准误，假设：`V(Y|X) = σ 2 [E(Y|X)]2`。

### 3.6.4 正态回归模型

在正态回归模型中，参数使用正态分布通过最大似然法估计。对于固定的`σ 2`，如果 `E(Y|X)` 设定良好，即使分布不是正态的，估计量也会相合。

## 3.7 截断模型：托比特模型

一种非常特殊的受限因变量类型是由数据截断引起的。截断回归模型是指其因变量在某个值以上（上截断）或以下（下截断）被截断，即因变量对部分人群不可观察。在截断回归模型中，潜在的因变量近似连续，但由于我们收集数据的方式或制度约束，它要么被低截断要么被高截断。

数据截断的一个特殊情况是因变量对很大一部分人群为零，而对正值是连续的。我们此时处理的是具有角点解的有界变量模型。托比特模型专门为具有角点解的因变量而设计。这些变量对相当比例的人群为零，但对正值近似连续分布。

截断托比特或托比特 I 型回归模型表示如下：

![Texto, Carta Descripción generada automáticamente](img/image010.png)

我们将托比特模型表述为潜在变量 `Y*`，它满足经典回归模型的假设，正态分布、同方差且条件均值线性。

给定 `X` 的 `Y` 的密度与给定 `X` 的 `Y*` 的密度在正值上相同。此外，我们知道：

![Texto, Carta Descripción generada automáticamente](img/image513.png)

通过最大化似然函数，我们得到`β` 和`σ` 的 `MV` 估计量。可以得到估计系数的标准误并构建 Student t 统计量用于对比。Wald 统计量和 RV 也可使用。

### 3.7.1 托比特模型中系数的解释

我们注意到：

![Texto, Carta Descripción generada automáticamente](img/image567.png)

然后，如果我们仅使用 `Y>0` 的观测值，用 `OLS` 估计托比特模型，省略零值，我们将得到`β` 的无偏且不一致的估计量，因为我们省略了与 `X` 相关的 Mills 比值。

在托比特模型中我们有：

![Texto, Carta Descripción generada automáticamente](img/image501.png)

我们于是面对 `X` 和`β` 的非线性函数，这使我们得出结论：如果我们用所有观测值将托比特模型作为线性模型用 `OLS` 估计，我们将没有相合估计量。

### 3.7.2 托比特模型中的偏效应

如果 `Xj` 是连续变量，则对正值子人群中 `Y` 的期望值的偏效应将取决于`βj` 和一个介于 0 和 1 之间的项，其值为（*）：

![image](img/image589.png)

我们可以使用`β` 和`σ` 的 `MV` 估计值来估计该偏效应，用于 `X` 的均值或其他在我们应用中有兴趣的值。如果 `Xj` 是二元变量，我们可以计算 `E(Y|Y>0,X)` 在 `Xj = 1` 和 `Xj = 0` 之间的差值。同样，这也可以对任何离散 `Xj` 进行。

Likewise, if `Xj` is a continuous variable, we can compute the partial effect on the expected value of `Y`. This partial effect can be decomposed into two parts, the effect on the mean value of `Y` in the positive part of the distribution, and the effect on the probability in the other part of the distribution. We have (**):

![Tabla Descripción generada automáticamente con confianza media](img/image389.png)

This value of the effects can be easily estimated using the `MV` estimates of `β` and `σ` for the mean values of `X` or for other values of interest in our applications.

The Tobit model is based on the assumptions of normality and homoscedasticity in the latent model. When these assumptions are not met, the problem is not only the inconsistency of the `MV` estimator of `β` and `σ`. Even the expressions of the conditional expectation are not adequate. The model can be generalised to allow for certain forms of heteroskedasticity and non-normality. There are also tests for certain types of normality and heteroscedasticity, for example:

![image](img/image377.png)

But, for mild breaches of the assumptions, it is thought that the Tobit model can generate a good approximation of the partial effects.

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

### 3.7.3 Tobit model with censorship in the data

![image](img/chapter_title_below.png)

We have analysed the Tobit model for corner solution, but we can generalise to the case where there is censoring of any kind in the data. The most general case is when the variable of interest is continuous but is censored above (right censoring) or below a value (left censoring) which need not be zero.

We can write the Tobit model as:

![image](img/image243.png) which can also be written as:

![Diagrama, Texto Descripción generada automáticamente con confianza media](img/image570.png)

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

### 3.7.4 Maximum Likelihood (MV) estimation of the censored Tobit model

![image](img/chapter_title_below.png)

If we had a random sample we could estimate `β` by `OLS` and perform inference in the usual way, but censoring the data causes us problems of inconsistency in `OLS` estimation (with all observations or without the censored ones). Given a random sample, we can obtain consistent estimates from `β` and `σ` if we estimate by `OLS`. For uncensored observations, `Y = Y*`, the density of `Y` is the same as that of `Y*`. For censored observations we have:

![image](img/image465.png)

We will calculate the logarithm of the likelihood function and perform the `MV` estimation. In this model the `βj` are interpreted as in the linear regression model.

The expression for the logarithm of the likelihood function for a sample of size `n` is as follows:

![image](img/image353.png)

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

### 3.7.5 Two-stage ordinary least squares estimation of the censored Tobit model

![image](img/chapter_title_below.png)

Although the estimation of the `OLS`-censored Tobit model cannot be done directly, we can use the following two-step method:

1. The dichotomous dummy variable is constructed which is worth 1 for positive values of `Y` (`Yi > 0` or `Yi > c`) and which is worth 0 for values of `Y` less than or equal to zero (`Y i≤ 0` or `Y i≤ c`). The corresponding Probit model is estimated and the Mills ratio is obtained from the estimated values:

![image](img/image026.png)

1. We estimate by `OLS` the model ![image](img/image268.png)

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

## 3.8 SAMPLE SELECTION: TRUNCATED MODELS

![image](img/chapter_title_below.png)

A truncated regression model is similar to a censored regression model, but has some important differences: in a truncated regression model, we do not have the data about some important segment of the population. This is usually the case when a sample targets a particular subset of the population and, perhaps because it is costly, ignores the rest of the population. This is a particular case of the general problem of sample selection, where we observe a non-random sample of the underlying population.

Suppose we have an underlying population model that satisfies the assumptions of the classical regression model:

![image](img/image476.png)

If we had a random sample of the population, the most efficient estimation procedure would be `OLS`. However, in the case of the truncated model the problem is that we do not have a random sample, because our observed sample has a bound of the type `Yi ≤ ci` or `Yi > ci` (Truncated Tobit Model). If we want to estimate `β` and `σ` we need to know the distribution of `Yi` given `X` and that `Yi ≤ ci` or `Yi > ci`. That is:

![Texto, Carta Descripción generada automáticamente](img/image051.png)

where `f(Y|X ,iβσ² )` is the density of a normal with mean `Xiβ` and variance `σ²` and `F(ci |X ,iβσ² )` is the distribution function of a normal with mean `Xiβ` and variance `σ` evaluated at `ci`.
