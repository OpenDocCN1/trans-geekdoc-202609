

## 8.2 机器学习的核心 R 包

在对传染病传播进行机器建模以及评估传染病导致的 DALYs（伤残调整寿命年）变化时，最常用的建模包包括：

### 8.2.1 元包 (Meta-Packages)

- 1. {tidymodels}¹ 该框架提供了一系列用于建模和机器学习任务的包，包括 {tidyr}、{dplyr} 和 ggplot2。它为预处理、模型构建、评估和可视化提供了一致且整洁的工作流。
- 2. {caret}² 用于分类和回归（Classification and REgression）的 caret 框架为训练和评估机器学习模型提供了统一的接口。它支持广泛的算法，并为超参数调优和模型选择提供了方便函数。
- 3. {mlr3}³ 这是一个现代且可扩展的机器学习框架。它为建模任务提供了统一的接口，便于训练和评估各种机器学习算法。

### 8.2.2 引擎 (Engines)

引擎是机器学习算法的实际实现。它们执行训练和评估模型所需的计算。引擎可以集成到各种元包/框架中，以利用它们特定的算法和计算效率。每个引擎可能都有自己的参数集和功能，可以通过元包提供的高层接口进行访问。

- 1. {randomForest}: 用于随机森林模型。
- 2. {xgboost}: 一个优化的分布式梯度提升库，旨在实现高度高效、灵活和可移植性。它在梯度提升框架下实现了机器学习算法。
- 3. {glmnet}: 用于 lasso 和岭回归。
- 4. {nnet}: 用于神经网络。
- 5. {kernel}: 用于基于核的机器学习方法。
- 6. {e1071}: 用于支持向量方法和其他函数。
- 7. {lme4}: 用于线性和广义混合效应模型。
- 8. {mgcv}: 用于广义加性模型。
- 9. {rpart}: 用于递归划分回归和回归树。
- 10. {h2o}: 一个强大的机器学习框架，可以与 {tidymodels} 高效集成。{h2o} 提供了一系列机器学习算法，包括线性模型、基于树的模型和集成方法，并能高效处理大型数据集且支持并行计算。

> ¹Silge and Julia, Tidy Modeling with r.
> ²Max Kuhn, The Caret Package, n.d., https://topepo.github.io/caret/.
> ³Mlr-Org, n.d., https://mlr-org.com/.

{keras3} 是 Keras 的 R 接口，是一种深度学习技术，提供了用 Python 编写的高级神经网络 API。设计用于在 {tensorflow}（由 Google 开发的开源机器学习框架）之上快速进行深度学习模型实验。

### 2.2.3 时间序列分析

- 1. {forecast}: 用于预测函数。
- 2. {prophet}: 专门为时间序列预测设计，强调灵性和易用性。由 Facebook 开发，prophet 可以处理各种时间序列模式，包括季节性、节日效应和趋势变化，适用于对传染病随时间传播的建模。
- 3. {fpp3}:4 该包是《预测分析：原理与实践》（第三版）的一部分，为时间序列数据预测提供数据和工具，例如带有 ARIMA() 模型的 {fable} 包的导入，这对于建模疾病随时间的传播非常相关。

### 2.2.4 贝斯分析

- 1. {rms}: 使用 Stan 进行贝斯广义多变量非线性多层模型。
- 2. {rstan}: 使用 Stan 进行贝斯推断。

### 2.2.5 专业工具

- 1. {spdep} 是一个强大的空间统计工具，它提供了一系列函数用于分析空间数据中的空间依赖性和自相关性，这在传染病建模中特别相关。它还将空间效应整合到模型中，允许更好地理解传染病如何在空间上传播。
- 2. {INLA}:5 整合嵌套拉普拉斯近似（INLA）是一个使用 INLA 方法进行贝斯推断的包。它特别适用于空间和时空建模，这对于研究传染病的传播具有相关意义。

这些包为传染病传播的建模以及评估其对 DALYs 等健康指标的影响提供了多样化的工具和技术。这些包提供了关于传染病动态的宝贵见解，可为公共卫生干预和政策提供参考。然而，这些包是否合适取决于多种因素，包括：

- 分析的具体要求
- 研究者的专业知识
- 所用数据的性质

每个包都有其优缺点，包的选择通常取决于诸如下因素：

- 建模任务的复杂度
- 可用数据的类型
- 偏好的建模方法（例如频率派 vs. 贝斯派）

例如，tidymodels 为建模任务提供了一个整洁且一致的工作流，而 mlr3 为机器学习算法和超参数调优提供了广泛的支持。

还应该考虑其他对分析特定方面相关的包，例如空间建模（如 spdep）和时间预测（如 prophet）。

在选择最符合需求和目标的包之前，应该根据具体的研究目标仔细评估每个包的功能和能力。此外，值得考虑对不同的包和技术进行实验可能对识别针对特定分析的最有效方法有益。

## 8.3 模型框架应用示例

在本节中，我们提供了不同模型框架应用的一些示例。使用了在第 7 章中介绍的数据，来演示 mlr3、h2o 和 keras 等模型框架在机器学习任务中的应用。

我们已经在第 6 章和第 7 章中展示了 {tidymodels} 元包的应用，它特别有助于借助 `workflow()`、`workflow_set()` 和 `workflow_map()` 等关键函数测试不同类型的模型。

### 8.3.1 示例：使用 ml3 分析登热导致的 DALYs

此示例的数据集来自 {nmsidR} 包，包含了 1980 年至 2021 年选定传染病导致的死亡人数、DALYs、YLDs、YLLs、患病率和发病率的数据。

```r
library(tidyverse)
hmsidR::infectious_diseases %>%
# [1] "year"               "location_name" "location_id"    "cause_name"
# [5] "Deaths"             "DALYs"           "YLDs"             "YLLs"
# [9] "Prevalence"         "Incidence"
```

让我们来看报告过登热的地区：

```r
nmsidR::infectious_diseases %>%
filter(cause_name == "Dengue") %>%
distinct(location_name)
# A tibble: 5 x 1
# location_name
# <chr>
# 1 Malawi
# 2 Central African
# 3 Lesotho
# 4 Eswatini
# 5 Zambia
```

并观察登热健康指标随时间的变化：

```r
nmsidR::infectious_diseases %>%
filter(cause_name == "Dengue") %>%
group_by(year, location_name) %>%
summarise(DALYs = sum(DALYs), .groups = "drop") %>%
ggplot(aes(x=year, y=DALYs, color=location_name)) +
  geom_line() +
  labs(title="Health Metrics due to Dengue")
![](img/66610d3ab4460cd4e88d549.png)

图 8.1** 登热导致的健康指标

在某些地区，指标趋势是平坦的，而在其他地区则更为明显。YLLs 是 DALYs 的主要原因，但 YLDs 也有贡献。我们关注三个地区——马拉维、赞比比亚和中非共和国的 DALYs。2017 年至 2021 年的数据（5 年）未被留作测试，1990 年的数据被包含并按位置 id 分组。

```r
dalys_engue <- hmsidR::infectious_diseases %>%
  filter(cause_name == "Dengue",
  location_name %in% c("Eswatini", "Lesotho")) %>%
  drop_na() %>%
  group_by(location_id) %>%
  select(-location_name)
```

```r
dalys_engue %>%
head()
# # A tibble: 6 x 7
# # Groups: location_id [3]
#   year location_id Deaths DALYs YLDs YLLs Prevalence
#   <int> <chr> <num> <num> <num> <num> <num>
# 1    1990     1   182.0   7.59  5.35  2.24      33.7
# 2    1991     1   191.0   6.88  6.64  0.23      42.4
# 3    1990     2   169.0   2.25 -13.1  0.00      22.0
# 4    1991     1   191.0   8.57  8.54  0.23      52.5
# 5    1991     1   182.0   8.68  6.47  2.21      40.9
# 6    1991     2   169.0   2.23  2.22  0.12      13.0
```

{mlr3} 是一个元包，其语法特别有用，通过提供一致的命名规范引导用户完成机器学习步骤。它对于基准测试模型也非常有用。除了 {mlr3} 包外，还加载了 {mlr3learners}、{mlr3viz}、{mlr3verse} 以及 {data.table} 包。这些每一个

