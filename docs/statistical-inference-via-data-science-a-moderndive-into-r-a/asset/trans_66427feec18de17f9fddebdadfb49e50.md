

## 5.3.3 get_regression_x() 函数

在本章中，我们介绍了 `moderndive` 包中的一个包装函数：

- `get_regression_points()`，它返回来自 5.1.3 节中回归模型的逐点点信息。

`get_regression_points()` 函数在背后是如何运行的？我们在 5.1.2 节中提到过这是包装函数的一个示例。此类函数获取其他已存在的函数并将其“封装”成单个函数，从而向用户隐藏其内部工作机制。用户只需要关心输入是什么样子的以及输出是什么样子的。在本小节中，我们将“深入底层”这些函数的内部构造，看看这些包装函数的“引擎”是如何工作的。

`get_regression_points()` 函数是一个包装函数，它返回有关回归模型中涉及的单个点的信息，如拟合值、观测值和残差。`get_regression_points()` 使用 `broom` 包中的 `augment()` 函数³ 生成表 5.9 所示的数据。此外，它还使用了 `janitor` 包⁴ (Firke, 2023) 中的 `clean_names()` 来清理变量名。

```r
library(broom)
library(janitor)
demographics_model |>
augment() |>
mutate_if(is.numeric, round, digits = 3) |>
clean_names() |>
select(-c("std_resid", "hat", "sigma", "cooksd"))
```

### 表 5.9：使用 broom 包中的 augment() 获取回归点

| fert_rate | life_exp | fitted | resid |
|---|---|---|---|
| 4.3 | 53.6 | 5.23 | -0.934 |
| 1.4 | 79.5 | 1.69 | -0.289 |
| 2.7 | 78.0 | 1.89 | 0.813 |
| 5.0 | 62.1 | 4.07 | 0.928 |
| 1.6 | 77.8 | 1.92 | -0.318 |
| 1.9 | 78.3 | 1.85 | 0.052 |
| 1.6 | 76.1 | 2.15 | -0.548 |
| 1.6 | 83.1 | 1.19 | 0.408 |
| 1.5 | 82.3 | 1.30 | 0.195 |
| 1.6 | 74.2 | 2.42 | -0.819 |

³https://broom.org/
⁴https://github.com/ourke/janitor

## 5.4 结论

在这种情况下，它仅输出学生学习回归感兴趣的变量：结果变量 $y$ ($fert\_rate$)、所有解释/预测变量 ($life\_exp$)，通过应用回归方程得到的所有拟合值 $\hat{y}$ 以及残差 $y - \hat{y}$。

如果你对这些和其他包装函数的工作原理更加好奇，可以查看 GitHub 上的源代码。

### 5.4.1 额外资源

所有*学习检查*的答案可以在书的附录中找到。附录开始于 https://moderndive.com/v2/appendix。

本章使用的所有 R 代码脚本位于 https://www.moderndive.com/v2/scripts/05-regression.R。

如 5.1.1 节建议的，解释接近 -1、0 和 1 等极端值的系数可能是主观的。为了帮助建立对相关性的感觉，我们建议你玩名为“猜相关性”的 80 风格游戏：http://guesssthecorrelation.com/。

![](img/44574218041017e8f01b1c90.png)

图 5.13：“猜相关性”游戏预览。

## 5.4.2 将要做什么

在本章中，你学习了*简单线性回归*，即拟合只有一个解释变量的模型。在第 6 章，我们将学习*多元回归*，我们的回归模型现在可以有多个解释变量，比简单线性回归的形式稍微高级一点！特别是，我们将考虑两种情况：具有一个数值和一个分类解释变量的模型，以及具有两个解释变量的模型。这将允许你构建更复杂、更强大的模型，以更好地解释结果变量 $y$。

## 6 # 多元回归

在第 5 章，我们学习了简单线性回归，它代表两个变量之间的关系：结果变量或响应变量 $y$ 和解释变量或回归变量 $x$。此外，为了简单起见，我们只考虑了一个解释变量 $x$ 的模型。

在本章中，我们引入了多元回归，这是考虑到多个解释变量时对简单线性回归的扩展。正如后续章节所示，任何一个解释变量的相关效应必须考虑到模型中的其他解释变量。

## 所需包

如果需要，请阅读 1.3 节关于如何安装和加载 R 包的信息。

```r
library(tidyverse)
library(moderndive)
library(ISLR2)
```

## 6.1 一个和一个分类解释变量

我们继续使用 5.1 节介绍的联合国各国数据集。记得我们学习了结果变量生育率 $y$ 与回归变量寿命 $x$ 之间的关系。

在本节中，我们为该模型引入了一个额外的回归变量：四个类别的收入分组：低收入、中低收入、中高收入和高收入。我们现在想研究生育率如何随寿命的变化而变化。为此，我们使用多元回归。观察我们现在：

1. 一个结果变量 $y$，生育率。
2. 两个解释变量：
   a. 数值变量 $x1$，寿命。
   b. 分类变量 $x2$，收入。

### 6.1.1 探索性分析

联合国各国数据框在下一节中。为了简单起见，我们只选择这里需要的变量，并将其保存到名为 `UN_data6` 的新数据框中。我们将收入设置为因子以便显示其水平。R 将此变量读取为字符 `<chr>`，除了识别国家之外将不再需要。

```r
UN_data6 <- member_states %>%
  select(country, expectancy, fertility_rate, income) %>%
  mutate(income = factor(income, levels = c("Low income", "Lower middle income", "Upper middle income", "High income")))
```

回探索性分析的三个共同步骤：
1. 检查原始数据样本。
2. 计算汇总统计。
3. 创建可视化。

我们首先通过在 RStudio 中查看 `UN_data6` 或使用 `dplyr` 包中的 `glimpse()` 函数来查看原始数据值：

```r
glimpse(UN_data6)

# Rows: 182
Columns: 4
$ country <chr> "Afghanistan", "Albania", "Algeria", "Angola", ...
$ expectancy dbl> 53.6, 79.5, 78.0, 62.1, 77.8, 78.3, 76.1, 83.1, 82.3, 74.2,
$ fertility_rate dbl> 4.3, 1.4, 2.7, 5.0, 1.6, 1.9, 1.6, 1.5, 1.5, 1.4,
$ income <fct> Low income, Upper middle, Lower middle, High income
```

寿命（`life_exp`）是一个国家人口平均预期寿命年数的估算。生育率（`fert_rate`）是一个国家内生育年龄女性的平均活出生数。正如我们在 5.1.1 和 5.2.1 节的探索性数据分析中所做的那样，我们找到汇总统计：

```r
summary(UN_data6)
```

我们还显示了对应于不同国家的 182 行数据中 10 行的随机样本。由于抽样的随机性，你可能会得到一组不同的 10 行。

```r
UN_data6 |> sample_n(size = 10)
```

### 表 6:1：从 182 个联合国各国中随机抽取 10 行

| country | life_exp | fert_rate | income |
|---|---|---|---|
| Trinidad and Tobago | 75.9 | 1.6 | High income |
| Micronesia, Federated States of | 74.4 | 2.6 | Lower middle income |
| North Macedonia | 76.8 | 1.4 | Upper middle income |
| Portugal | 81.5 | 1.4 | High income |
| Madagascar | 68.2 | 3.7 | Low income |
| Cambodia | 70.7 | 2.3 | Lower middle income |
| Dominica | 78.2 | 1.6 | Upper middle income |
| Peru | 68.9 | 2.1 | Upper middle income |
| Cyprus | 79.7 | 1.3 | High income |
| Guinea-Bissau | 63.7 | 3.8 | Low income |

