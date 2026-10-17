
Pressing OK produces the output presented in Figures 2-35 to 2-37. A fit with Poisson likelihood family and Log link function is observed. The individual and joint significance of the estimated parameters is quite acceptable.

It can be seen that the estimated predictive model does not coincide exactly with that obtained in STATGRAPHICS, but it is practically similar.

––––––––

![image](img/scene_break.png)

![image](img/image087.png)![image](img/image408.png)

Figure 2-35    Figure 2-36

![image](img/image680.png)

Figure 2-37

#### Exercise 2-2

Consider the `logitb.sav` file containing data from a sample of 53 prostate cancer patients, measuring age, the acid level that measures the extent of the tumour, the aggressiveness of the tumour, the stage of the tumour, the results of an X-ray, and when the cancer was detected by surgery to have spread to the lymph nodes. From these data, the aim is to fit a model that can predict when the cancer does (or does not) spread to the lymph nodes without the need for surgery.

We start by reading the `logitb.sav` file, looking at its contents and enabling its variables.

![image](img/image709.png)

We then adjust the ordered logít model.

![image](img/image228.png)

![image](img/image590.png)

It is observed that the constant is not significant. We will then fit the model without constant.

![image](img/image278.png)

The model is now more or less acceptable, except perhaps for the `GRADE` variable whose significance is 70%.

#### Exercise 2-3

Solve the previous exercise using a Probit model.

We start by estimating the model using a probit regression.

![image](img/image193.png)

It is observed that the constant is not significant, which leads us to estimate the model without constant.

![image](img/image393.png)

![image](img/image097.png)

The model is already more or less acceptable, except perhaps for the `GRADE` variable whose significance is 70%. The results are very similar to the case of the logit model.

# Chapter 3

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

## LIMITED DEPENDENT VARIABLE, DISCRETE CHOICE, COUNT, CENSORED, TRUNCATED AND SAMPLE SELECTION MODELS. TREATMENT WITH STATA

![image](img/chapter_title_below.png)

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

### 3.1 limited dependent variable models

![image](img/chapter_title_below.png)

The functional expression of the multiple regression analysis model is ![image](img/image451.png). Multiple regression admits the possibility of working with dependent variables whose range of values is restricted (binary variables with values 0 and 1, variables with positive integer values, etc.). In general, models that admit dependent variables with restricted range are called limited dependent variable models.

Most of the economic variables under analysis have values that are constrained in some way, often because they must be positive. For example, hourly wages, house prices, and nominal interest rates must be greater than zero. But not all of these variables require special treatment. No special econometric model is usually needed to deal with variables that are strictly positive but take many different values. When the dependent variable is discrete (discrete choice models) and takes a small number of values, it does not make sense to treat it as if it were an approximately continuous variable. The fact that the dependent variable is discrete does not necessarily imply that linear models are not appropriate. However, for binary responses (binary choice models), Logit and Probit models and in certain cases the linear probability model are often used. Also for multiple responses (multiple choice models), logit and probit models are used.

Another important example of a limited dependent variable is the count variable, which takes non-negative integer values. A count data model is one that has as its dependent variable a discrete count variable that takes non-negative integer values. Poisson regression models are appropriate for analysing count variables.

In econometric analysis, other types of limited dependent variables appear, especially when we analyse the behaviour of individuals, households, or firms. For example, suppose that during a given year a large number of households in a region do not make any charitable donations. Therefore, the population distribution of donations made by households is highly dispersed over positive values, but with a high concentration at zero. This is an example of a corner solution. The Tobit model is explicitly designed for dependent variables that have corner solutions. These variables are zero for a considerable proportion of the population but are approximately continuously distributed for positive values.

另一种受限因变量是由数据删失引起的。删失回归模型是指其因变量在某个值以上（上删失）或以下（下删失）被删失的模型，即对于总体的一部分，因变量未被观测到。在删失回归模型中，潜在的因变量近似连续，但由于数据收集方式或制度性约束而被下删失或上删失。截断回归模型与删失回归模型相似，但有一个重要区别：在截断回归模型中，我们没有关于总体中某个重要部分的

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

### 3.2 离散选择模型

![image](img/chapter_title_below.png)

多元回归分析模型的函数表达式为 ![image](img/image686.png)。多元回归允许使用离散而非连续的因变量来对离散现象进行建模。当因变量是一个离散变量，反映个体决策且选择集由相互排斥的备选方案组成时，我们就是在处理离散选择模型。当因变量是离散的且仅取少量值时，将其视为连续变量是没有意义的，通常我们感兴趣的是在某些解释变量取值条件下，主体做出某一离散决策的概率。这些刻画每个解释变量取值下概率的分布函数通常是非线性的且通常没有解析解，因此通常需要借助数值方法。选择集只有两种可能备选方案的离散选择模型称为二元选择模型。当选择集有多个离散值时，这些称为多项选择模型或多项模型。

当离散因变量的取值是不反映类别的数字时，离散选择模型称为计数数据模型。如果离散因变量的数值取值反映类别，则模型称为分类离散选择模型，通常分为有序分类离散选择模型（数值没有数量意义且反映类别的排序）和无序分类离散选择模型（数值仅反映类别）。

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

### 3.3 二元离散选择模型

![image](img/chapter_title_below.png)

在选择集只有两种互斥可能备选方案的离散选择模型中，我们将考虑线性概率模型、`Logit`模型和`Probit`模型。

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

#### 3.3.1 线性概率模型

![image](img/chapter_title_below.png)

![Texto, Carta Descripción generada automáticamente](img/image296.png)

我们现在处理的是线性概率模型，其中例如 `β1` 衡量在其他条件不变时，`X1` 单位变化导致“成功”概率（`Y = 1`）的变化。

由于 `Y` 是一个伯努利随机变量：

![Texto, Carta Descripción generada automáticamente](img/image189.png)

我们于是面临一个具有异方差性的模型，因为误差方差不是常数，对于 `X1 ,...,Xk` 的每个取值，误差方差都有不同的值（`V(u)` 不是常数）。此外，`Y` 是一个伯努利变量，因此正态性假设也得不到满足。这使得有必要通过普通最小二乘法的替代方法来估计这些模型，例如使用最大似然估计量或广义最小二乘法。

估计线性概率模型后我们有：

![image](img/image431.png)

可以被解释为“成功”概率（`Y = 1`）的估计值。在某些应用中，有意义将 ![image](img/image086.png) 解释为所有 `X'sj` 均为 0 时的成功概率。

线性概率模型的另一个重要局限是，对于解释变量 `X1 ,...,Xk` 的某些组合，估计的概率可能大于零或小于一。

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

#### 3.3.2 Probit 和 Logit 模型

![image](img/chapter_title_below.png)

我们可以将 `Logit` 和 `Probit` 模型视为二元响应模型：

––––––––

![image](img/scene_break.png)

![image](img/image014.png)

为避免线性概率模型的问题，它们被设定为 `Y = G(Xβ)`，其中 `G` 是一个函数，对所有实数 `z` 均取严格介于 0 和 1 之间的值（`0<G(Z)<1`）。根据 `G` 的不同定义，我们得到不同的二元选择模型。

![Texto, Carta Descripción generada automáticamente](img/image631.png)

`Probit` 和 `Logit` 模型作为非线性模型，不能用 `OLS` 估计，必须使用最大似然方法。

假设我们有 `n` 个独立同分布的观测值（随机样本）服从模型：

![Texto Descripción generada automáticamente](img/image030.png)

`β` 的 `MV` 估计量是使对数似然函数最大化的估计量：

![image](img/image091.png)

它将是一个一致的、渐近正态且渐近有效的估计量。

一阶条件应为：

![Diagrama Descripción generada automáticamente con confianza media](img/image280.png)

其中 `g(.)` 是正态或逻辑密度函数（由分布函数导出）。
