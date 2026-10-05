

带随机效应的面板数据模型使用广义最小二乘 `GCM` 方法进行估计。

![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png)

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.8 面板数据的动态模型

![image](d2d_images/chapter_title_below.png)

面板数据模型也可以具有滞后变量，并且滞后可能出现在因变量和自变量中，尽管最常见的是滞后出现在因变量中。具有因变量时间滞后的动态面板数据模型将具有以下表达式：

![image](d2d_images/image360.png)

为了估计这种类型的模型，通常使用工具变量将滞后的内生变量 `yi,t-1` 替换为与 `yi,t-1` 高度相关且与误差不相关的工具 `y*i,t-1`。需要估计的新模型将为：

![image](d2d_images/image609.png)

在这种情况下，可以使用普通最小二乘法进行估计，但很难找到合适的工具变量。关于在实践中应用面板模型中最常用的经济及其他变量的工具可用性，存在大量文献。在使用工具变量估计这种类型的面板时，应特别注意多重共线性和自相关问题。我们也不应忘记异方差性问题，尤其是在样本非常大的情况下。还有用于估计某些动态结构面板的特殊替代方法。Arellano 和 Bond 的方法为动态面板数据模型的估计提供了解决方案。

![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png)

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.9 面板数据的 Logit 和 Probit 模型

![image](d2d_images/chapter_title_below.png)

给定一般线性模型：

![image](d2d_images/image456.png)

以概率作为因变量，如果函数 `F` 被选为 `Normal(0,1)` 的分布函数，使得 `Pi` 的值始终落在区间 `[0,1]` 中，我们得到所谓的 Probit 模型，其参数 `β` 允许通过最大似然进行估计。

让我们不要忘记：

![image](d2d_images/image458.png)

在 ![image](d2d_images/image625.png) 的情况下，我们将处理 Logit 模型。

Logit 和 Probit 模型可以通过引入新的时变指标赋予面板结构。

面板数据 Logit 模型可以写成如下形式：

![image](d2d_images/image256.png)

通过最大似然估计模型参数导致我们最大化函数：

![image](d2d_images/image188.png)

这样就得到了 Logit 模型参数的最大似然估计。

同样，Probit 面板数据模型可以写成如下形式：

![image](d2d_images/image205.png)

通过最大似然估计模型参数导致我们最大化函数：

![image](d2d_images/image065.png)

这样就得到了 Probit 模型参数的最大似然估计。

可以遵循类似的路径来定义具有 Poisson 分布的面板数据模型和具有负二项分布的面板数据模型。

![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png)

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.10 面板数据的单位根与协整

![image](d2d_images/chapter_title_below.png)

面板数据的单位根检验与对单个序列进行的单位根检验相似。以下方程用作起点：

![image](d2d_images/image133.png)

可以对 ![image](d2d_images/image574.png) 做出两个假设。第一个是 = ![image](d2d_images/image677.png]，这是 Levin、Lin 和 Chu `LLC` 检验、Breitung 和 Hadri 使用的假设。第二个假设允许 ![image](d2d_images/image009.png) 在截面中自由变化，这是 Im、Pesaran 和 Sim `IPS` 检验中使用的假设，以及 Maddala 和 Wu 提出的 Fisher-ADF 和 Fisher-PP 检验和 Choi 检验。

Maddala 和 Wu 提出的 Fisher-ADF 和 Fisher-PP 检验用于检验面板数据中单位根的存在，将个体单位根检验的 p 值结合起来。如果我们将 `πi` 定义为第 i 个截面单位根检验的 p 值，则在所有 N 个截面都存在单位根的原假设下，验证：

![image](d2d_images/image170.png)

此外 Choi 证明：

![image](d2d_images/image375.png)

最简单的面板协整检验是通过面板单位根检验来检查面板模型的残差是否没有单位根。还有其他正式的面板协整检验，例如 Engel 和 Granger 检验、Kao 和 Pedroni 检验以及 McKoskey 和 Kao 检验。

![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png)

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.11 stata 与面板数据模型

![image](d2d_images/chapter_title_below.png)

`STATA` 具有 `xtreg` 命令，允许估计具有固定效应和随机效应面板数据的模型。其语法如下：

随机效应模型

```
xtreg dependent_independent variable independent variables, re options
```

最重要的选项是 `i(variable)` 用于指示面板 ID 变量，`sa` 用于使用 Swamy-Arora 方差复合估计量，`vce(type)` 用于指示稳健、Bootstrap 或 Jackknife 估计的类型，`cluster` 用于调整组内相关性的标准误，以及 `level(n)` 用于置信水平 n。

使用回归估计器之间估计的模型

```
xtreg dependent_independent variable independent variables, be options
```

最重要的选项是 `i(variable)` 用于指示面板 ID 变量，`wls` 用于使用加权最小二乘估计量，`vce(type)` 用于指示 Bootstrap 或 Jackknife 估计类型以及 `level(n)` 用于置信水平 n。

![image](d2d_images/scene_break.png)

固定效应模型

```
xtreg independent_dependent variable independent variables, fe options
```

最重要的选项是 `i(variable)` 用于指示面板 ID 变量，`vce(type)` 用于指示稳健、Bootstrap 或 Jackknife 估计的类型，`cluster` 用于调整组内相关性的标准误，以及 `level(n)` 用于置信水平 n。

最大似然随机效应模型

```
xtreg dependent_independent variable independent variables, mle options
```

最重要的选项是 `i(variable)` 用于指示面板 ID 变量，`noconstant` 用于从模型中移除常数项，`vce(type)` 用于指示 Bootstrap 或 Jackknife 估计的类型以及 `level(n)` 用于置信水平 n。

总体平均模型

```
xtreg dependent_independent variable independent variables, pa options
```

