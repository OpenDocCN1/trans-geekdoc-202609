

## 6.4 使用多项式模型演示过拟合

```r
library(tidymodels); library(rio); library(janitor)
DataHousing=import("https://ai.large-analytics.com/data/HousingData.csv") |>
clean_names("upper_camel") |>
select(Price, Sqft=SqftLifting)
```

```r
set.seed(777)
Split01=DataHousing |>
initial_split(prop=0.01, strata=Price, breaks=5)
DataTrain=training(Split01)
DataTest=testing(Split01)
```

注意参数 `split=0.01` 只将 20 个观测值分配给训练数据。剩余的 21,503 个观测值将作为测试数据。尽管有足够的观测值来创建一个更大的数据集，但仅考虑 20 个观测值进行训练的原因是人为刻意制造了可能导致过拟合的情况。在现实世界的分析中，我们处理的是更大的数据集；过拟合会更加微妙且难以识别。

我们使用预测来根据居住面积（Sqft）估计房屋价格。该模型是多项式的，因为 Sqft 具有各种值：

> $Price = \beta_1Sqft + \beta_2Sqft^2 + \beta_3Sqft^3 + \beta_4Sqft^4 + \beta_5Sqft^5 + \beta_6$ (6.1)

由于房屋价格（Price）仅根据其建筑面积估计，因此该模型被归类单变量模型。选择单变量模型是因为它允许我们通过 2D 图展示结果，其中纵轴为价格，横轴为建筑面积。

正如我们在方程 (6.1) 中所示，预测变量 Sqft 使用了范围从 1 到 5 的幂次，这使得模型是非线性的。

如果你查看上一节末尾信息框中可能导致过拟合的图表，你会发现这里满足了所有条件：

- 1. 训练数据集的观测值数量不足（在我们的案例中为 20 个观测值）。
- 2. 模型包含许多变量，因此有许多参数需要校准（5 个变量和 6 个校准参数通常不被认为很多，但与仅 20 个观测值相比，参数的数量可以认为是大量的）。
  - 多变量房地产模型将在第 7 章介绍。
- 3. 本章后面将使用具有不同阶数的多项式模型。

## 6 多项式回归 — 过拟合/调优详解

- 3. 模型是高度非性的（5 次多项式是高度非线性的）。

使用 `tidymodels` 创建多项式模型时，我们使用了与交互章节 5.5 相同的模型设计。为了引入非线性，我们使用了 recipe（数据：

```r
ModelDesignLinReg=linear_reg() |>
  set_engine("lm") |>
  set_mode("regression")

RecipeHouses=recipe(Price~, data=DataTrain) |>
  step_update(Sqft2=Sqft^2, Sqft3=Sqft^3,
Sqft4=Sqft^4, Sqft5=Sqft^5)
```

该 recipe 利用 `step_update` 创建了四个额外的变量，这些变量计算为变量 Sqft 的平方、立方、四次方和五次方：

- Sqft2=Sqft^2
- Sqft3=Sqft^3
- Sqft4=Sqft^4
- Sqft5=Sqft^5

因为 Sqft 不仅以原始形式使用，还以各种幂次（平方、立方、四次方和五次方）使用，所以模型（在数据中）是非线性的。

观察方程 (6.1)，你可以看到为什么模型在参数上是线性的。如果我们将变量 $Sqft, Sqft^2, ..., Sqft^5$ 视为单变量 OLS 模型中的任何其他变量，那么每个变量都会乘以一个参数 $\beta_1-\beta_5$ 并加到方程中。因此，只要我们将 Sqft 的不同幂次视为单独变量，6.1) 就是一个线性函数。

### 多项式模型在参数上是线性的，但在数据上是非线性的。

因此，方程 (6.1) 中的多项式模型仍然像普通的 OLS 模型一样进行优化，因为当我们 Sqft 的每个幂次视为单独变量时，它在参数上仍然是线性的。

通过将 recipe 和线性模型设计添加到工作流 WFModelHouses 中进行优化，并使用 `fit(DataTrain)` 对训练数据集中的 20 个观测值进行拟合：

```r
WFModelHouses=workflow() |>
add_recipe(RecipeHouses) |>
add_model(ModelDesignLinReg) |>
fit(DataTrain)
```

由于工作流 WFModelHouses 是针对训练数据拟合的，我们可以用它来预测并衡量模型的预测性能。我们从测量训练数据的性能开始。

与之前一样，我们使用 `augment()` 命令将预测附加到训练数据集，然后使用 `metrics()` 命令计算性能指标（详情见第 4.7.6 和 4.7.7 节）：

```r
DataTrainWithPred=augment(WFModelHouses, DataTrain)
metrics(DataTrain, truth=Price, estimate=.pred)
```

| metric | estimate | n |
| :--- | :--- | :--- |
| rmse | | |
| rsq | | |
| mae | | |

| metric | estimate | n |
| :--- | :--- | :--- |
| rmse | | |
| rsq | | |
| mae | | |

| metric | estimate | n |
| :--- | :--- | :--- |
| rmse | | |
| rsq | | |
| mae | | |

`augment()` 命令将预测附加到训练数据集，然后我们使用 `metrics()` 命令计算性能指标（详情见第 4.7.6 和 4.7.7 节）：

`rmse`、`rsq` 和 `mae` 是针对训练数据计算的。（此处省略重复的计算描述描述）

