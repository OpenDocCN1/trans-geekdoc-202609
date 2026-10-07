
图 2-12 至 2-14 展示了二项概率族与 Probit 联系函数的模型拟合。模型具有良好的整体拟合度（全距对比 p 值很小）、显著的效应以及参数估计具有可接受的小 p 值。

![image](img/image152.png)![image](img/image131.png)

图 2-12 图 2-13

![image](img/image562.png)

图 2-14

估计的 Probit 模型的预测方程为：

![Imagen que contiene Tabla Descripción generada automáticamente](img/image076.png)

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

### 2.6 GENERALISED LINEAR MODELS WITH R

![image](img/chapter_title_below.png)

在 R 中，高级模型可以通过 `glm` 命令进行拟合，其通用语法如下：

![image](img/image652.png)

可使用的族及其默认链接如下：

![image](img/image172.png)

对于 GLM 模型可以获得以下信息：

| `summary(r)` || 显示拟合模型的详细结果 |

| --- | --- |

| `coefficients(r)` || 列出模型的拟合参数 |

| `confint(r)` || 列出估计模型参数的 95% 置信区间。 |

| `plot(hatvalues(model))` || 列出拟合模型中的预测值 |

| `residuals(r)` || 列出拟合模型的残差 |

| `anova(r)` || 列出拟合模型的 ANOVA 表 |

| `plot(rstudent(model))` || 绘制研究的废料图 |

| `influencePlot(model)` || 找出杠杆点 |

| `plot(cooks.distance(model))` || 检测异常废料 |

| `plot(r)` || 显示拟合模型的图形诊断 |

| `predict(r)` || 使用拟合模型预测值 |

作为第一个例子，我们拟合一个 logit 模型，用来预测汽车故障的概率作为燃油消耗、功率和发动机函数的模型。

![image](img/image575.png)

我们观察到拟合效果相当好。模型拟合的预测方程如下：

![image](img/image402.png)

要对上述情况拟合 probit 模型，我们使用以下语法：

![image](img/image485.png)

输出如下：

![image](img/image187.png)

完整输出如下所示：

![image](img/image698.png)

我们注意到拟合效果相当好。模型拟合的预测方程如下：

![image](img/image321.png)

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

### 2.7 Generalised linear models IN R THROUGH MENUS

![image](img/chapter_title_below.png)

统计菜单的 Fit models 选项中的 General linear model 子选项允许（图 2-15）拟合广义线性、logit、probit、clogloglog 及其他模型。按图 2-16 所示填写输入屏幕可得到下一页所示的二项 logit 模型的输出。

![image](img/image292.png)

Figure 2-15

![image](img/image222.png)

Figure 2-16

![image](img/image711.png)

可以观察到，用燃油消耗、功率、发动机和重量来解释汽车故障概率的二项 logit 模型的拟合是正确的，因为估计参数的 p 值非常低。模型的估计预测方程如下：

![image](img/image225.png)

如果我们想使用 probit 模型进行上述调整，我们按图 2-17 所示填写输入屏幕。点击 OK 后会产生下一页的输出。

![image](img/image634.png)

Figure 2-17

![image](img/image390.png)

![image](img/image696.png)

可以观察到，用燃油消耗、功率、发动机和重量来解释汽车故障概率的二项 probit 模型的拟合是正确的，因为估计参数的 p 值非常低。估计模型的预测方程如下：

![image](img/image330.png)

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

### 2.8 Generalised linear models THROUGH STATGRAPHICS CENTURION

![image](img/chapter_title_below.png)

STATGRAPHICS 在 Relate → Attribute Data 选项中包含了 Logit、Probit、Poisson 和 Negative Binomial 模型（图 2-18）。

![image](img/image678.png)

Figure 2-18

作为一个例子，我们考虑文件 `7-10.xls` 包含变量 `narr86` 的信息，该变量代表 1986 年一个人被逮捕的次数，我们希望用变量 `pcnv`（以前被逮捕中被定罪的比例）、`avgsen`（刑期平均长度，月）、`tottime`（监禁时间，月）、`ptime86`（1986 年监禁时间，月）、`qemp86`（1986 年就业季度）、`inc86`（1986 年合法收入，百美元）、`black`（黑人被捕者虚拟变量，值为 1）、`hispan`（西班牙裔被捕者虚拟变量，值为 1）和 `born60`（被捕者出生于 1960 年的虚拟变量，值为 1）来解释它。

由于被解释变量在大量情况下取值为 0，且仅在 8 种情况下取值大于 5，因此可以使用计数数据模型。目的是研究解释变量对被解释变量的影响，使用 Poissson 计数数据、指数和负二项式。比较模型。

为了将我们的问题拟合到负二项式模型，我们使用 Relate → Attribute Data → Negative Binomial Regression（图 2-19）并按图 2-20 所示填写该过程的输入屏幕。

![image](img/image017.png)

Figure 2-19

![image](img/image621.png)

Figure 2-20

按下 OK 并按图 2-21 所示填写 Negative Binomial Regression Options 屏幕。按图 2-22 所示填充 Tables and graphs 屏幕。

![image](img/image368.png)

Figure 2-21

![image](img/image092.png)

Figure 2-22

分析摘要输出显示模型拟合非常好，联合显著性非常好，估计参数的粗略个体显著性可接受（也许除 AVGSEN 和 BORN60 外，它们在约 50% 时显著）。

![image](img/image398.png)

![image](img/image699.png)

![image](img/image230.png)

可以观察到，估计的负二项式模型的预测方程如下：

![image](img/image399.png)

估计参数的 95% 置信区间在下表中给出：

95.0% confidence intervals for coefficient estimates

|  ||  || Error ||  ||  |

| --- | --- | --- | --- | --- |

| Parameter || Dear || Standard || Lower Limit || Upper Limit |

| CONSTANT || 0,510418 || 0,0891951 || 0,335599 || 0,685238 |

| PCNV || \-0,401615 || 0,0717093 || \-0,542163 || \-0,261067 |

| AVGSEN || \-0,0238654 || 0,0156566 || \-0,0545519 || 0,00682115 |

| TOTTIME || 0,0245856 || 0,0113967 || 0,00224842 || 0,0469228 |

| PTIME86 || \-0,0985997 || 0,0182358 || \-0,134341 || \-0,0628582 |

| QEMP86 || \-0,0380555 || 0,0241328 || \-0,0853549 || 0,00924395 |

| INC86 || \-0,00808062 || 0,000930773 || \-0,00990491 || \-0,00625634 |

| BLACK=0 || \-0,661117 || 0,0593497 || \-0,77744 || \-0,544793 |

| HISPAN=0 || \-0,499853 || 0,0612882 || \-0,619976 || \-0,37973 |

| BORN60=0 || 0,0510633 || 0,0525824 || \-0,0519964 || 0,154123 |

![Tabla Descripción generada automáticamente](img/image493.png)

![image](img/image468.png)

然后使用 Poisson 回归模型拟合上述模型。为此，我们使用 Relate → Attribute Data → Poisson Regression（图 2-23）并按图 2-24 所示填写该过程的输入屏幕。

![image](img/image457.png)

Figure 2-23

![image](img/image705.png)

Figure 2-24

按下 OK 并按图 2-25 所示填充 Poisson Regression Options 屏幕。按图 2-26 所示填充 Tables and Graphs 屏幕。

![image](img/image438.png)

Figure 2-25

![image](img/image100.png)

Figure 2-26

The Analysis Summary output shows a very good model fit with very good joint significance and acceptable coarse individual significance of the estimated parameters (except perhaps `BORN60` which is significant at about 60%). The fit is better than in the previous case of the Negative Bnomial.

![image](img/image423.png)

![image](img/image351.png)

![image](img/image564.png)

The predictive equation of the estimated Poisson model is as follows:

![image](img/image428.png)

The 95% confidence intervals for the estimated parameters are as follows:

![image](img/image612.png)

![image](img/image615.png)

#### Exercise 2-1

File `7-10.sav` contains information on the variable `narr86` which represents the number of times a man is arrested during 1986 and which is to be explained by the variables `pcnv` (proportion of previous arrests in which he was convicted), `avgsen` (average length of sentences in months), `tottime` (time in prison in months), `ptime86` (time in prison in 1986 in months), `qemp86` (quarters employed in 1986), `inc86` (legal income in 1986 in hundreds of dollars), `black` (dummy worth 1 for black arrestee), `hispan` (dummy worth 1 for hispanic arrestee) and `born60` (dummy worth 1 if arrestee was born in 1960).

As the explained variable takes the value 0 in a large number of cases and only takes a value greater than 5 in 8 cases, a count data model could be used. Study the effect of the explanatory variables on the explained variable using Poissson count data, exponential and negative binomial. Compare the models. Use SPSS software.

We start by using the option `Analyse → Generalised Linear Models → Generalised Linear Models`. In the Model Type tab of the wizard we choose Negative Binomial with log link (Figure 2-27).

![image](img/image039.png)

Figure 2-27

The Response, Predictors, Model and Statistics tabs are filled in as shown in Figures 2-28 to 2-31.

![image](img/image364.png)

Figure 2-28

![image](img/image466.png)

Figure 2-29

![image](img/image413.png)

Figure 2-30

![image](img/image130.png)

Figure 2-31

Pressing OK produces the output presented in Figures 2-32 to 2-34. A fit with Negative Binoial Probability Family and Log Link Function is observed. The individual and joint significance of the estimated parameters is quite acceptable.

![image](img/image247.png)![image](img/image341.png)

Figure 52-32

![image](img/image244.png)

Figure 2-33

It can be seen that the estimated predictive model does not coincide exactly with that obtained in STATGRAPHICS, but it is practically similar.

To estimate the same model using a Poisson regression, fill in the Model Type tab of the generalised linear models wizard by choosing Poisson Loglinear (Figure 2-34).

![image](img/image660.png)

Figure 2-34
