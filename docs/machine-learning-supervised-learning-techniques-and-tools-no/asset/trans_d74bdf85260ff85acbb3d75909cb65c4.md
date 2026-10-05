

另一种受限因变量是由数据删失引起的。删失回归模型是指其因变量在某个值以上（上删失）或以下（下删失）被删失的模型，即对于总体的一部分，因变量未被观测到。在删失回归模型中，潜在的因变量近似连续，但由于数据收集方式或制度性约束而被下删失或上删失。截断回归模型与删失回归模型相似，但有一个重要区别：在截断回归模型中，我们没有关于总体中某个重要部分的<|message|>数据。这通常发生在样本针对总体中的特定子集时，并且可能由于成本原因而忽略其余总体。这是样本选择这一更一般问题的特例，在该问题中，我们观测到的是总体中一个非随机的样本。

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.2 离散选择模型

![image](d2d_images/chapter_title_below.png)

多元回归分析模型的函数表达式为 ![image](d2d_images/image686.png)。多元回归允许使用离散而非连续的因变量来对离散现象进行建模。当因变量是一个离散变量，反映个体决策且选择集由相互排斥的备选方案组成时，我们就是在处理离散选择模型。当因变量是离散的且仅取少量值时，将其视为连续变量是没有意义的，通常我们感兴趣的是在某些解释变量取值条件下，主体做出某一离散决策的概率。这些刻画每个解释变量取值下概率的分布函数通常是非线性的且通常没有解析解，因此通常需要借助数值方法。选择集只有两种可能备选方案的离散选择模型称为二元选择模型。当选择集有多个离散值时，这些称为多项选择模型或多项模型。

当离散因变量的取值是不反映类别的数字时，离散选择模型称为计数数据模型。如果离散因变量的数值取值反映类别，则模型称为分类离散选择模型，通常分为有序分类离散选择模型（数值没有数量意义且反映类别的排序）和无序分类离散选择模型（数值仅反映类别）。

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.3 二元离散选择模型

![image](d2d_images/chapter_title_below.png)

在选择集只有两种互斥可能备选方案的离散选择模型中，我们将考虑线性概率模型、`Logit`模型和`Probit`模型。

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

## 3.3.1 线性概率模型

![image](d2d_images/chapter_title_below.png)

![Texto, Carta Descripción generada automáticamente](d2d_images/image296.png)

我们现在处理的是线性概率模型，其中例如 `β1` 衡量在其他条件不变时，`X1` 单位变化导致“成功”概率（`Y = 1`）的变化。

由于 `Y` 是一个伯努利随机变量：

![Texto, Carta Descripción generada automáticamente](d2d_images/image189.png)

我们于是面临一个具有异方差性的模型，因为误差方差不是常数，对于 `X1 ,...,Xk` 的每个取值，误差方差都有不同的值（`V(u)` 不是常数）。此外，`Y` 是一个伯努利变量，因此正态性假设也得不到满足。这使得有必要通过普通最小二乘法的替代方法来估计这些模型，例如使用最大似然估计量或广义最小二乘法。

估计线性概率模型后我们有：

![image](d2d_images/image431.png)

可以被解释为“成功”概率（`Y = 1`）的估计值。在某些应用中，有意义将 ![image](d2d_images/image086.png) 解释为所有 `X'sj` 均为 0 时的成功概率。

线性概率模型的另一个重要局限是，对于解释变量 `X1 ,...,Xk` 的某些组合，估计的概率可能大于零或小于一。

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

## 3.3.2 Probit 和 Logit 模型

![image](d2d_images/chapter_title_below.png)

我们可以将 `Logit` 和 `Probit` 模型视为二元响应模型：

––––––––

![image](d2d_images/scene_break.png)

![image](d2d_images/image014.png)

为避免线性概率模型的问题，它们被设定为 `Y = G(Xβ)`，其中 `G` 是一个函数，对所有实数 `z` 均取严格介于 0 和 1 之间的值（`0<G(Z)<1`）。根据 `G` 的不同定义，我们得到不同的二元选择模型。

![Texto, Carta Descripción generada automáticamente](d2d_images/image631.png)

`Probit` 和 `Logit` 模型作为非线性模型，不能用 `OLS` 估计，必须使用最大似然方法。

假设我们有 `n` 个独立同分布的观测值（随机样本）服从模型：

![Texto Descripción generada automáticamente](d2d_images/image030.png)

`β` 的 `MV` 估计量是使对数似然函数最大化的估计量：

![image](d2d_images/image091.png)

它将是一个一致的、渐近正态且渐近有效的估计量。

一阶条件应为：

![Diagrama Descripción generada automáticamente con confianza media](d2d_images/image280.png)

其中 `g(.)` 是正态或逻辑密度函数（由分布函数导出）。

问题的非线性意味着为了从 `β` 得到 `MV` 估计量，我们需要应用迭代算法并通过迭代数值方法获得估计量。通过 Scoring 算法我们有：

![Diagrama, Texto Descripción generada automáticamente](d2d_images/image044.png)

为了在 `Logit` 和 `Probit` 模型中进行假设检验，我们将考虑到渐近协方差矩阵主对角线元素的平方根是每个 ![image](d2d_images/image379.png) 的（渐近）标准误，我们可以用它来构造 t 统计量（将具有渐近正态分布）或为每个参数构建近似置信区间。我们也可以同时检验多个限制。通常，我们感兴趣的是排除限制，因此我们将重点关注这一点。

检验一组参数等于零的原假设时，我们可以使用多种程序：

*   Wald 统计量。它渐近服从自由度为 `q`（限制数量）的卡方分布，并且大多数程序都提供。

