
通常，我们对于是否保留所有预测变量感到犹豫。目标是最大化预测性能并最小化过拟合。因此，要确定哪种算法优越通常是很的。那么为什么不将 Lasso 和岭回归结合起来呢？

这正是弹性网络方法的方法。它同时使用两者——Lasso 的惩罚和岭回归的惩罚——将它们的加权平均值加到目标函数的 MSE 中：

```
$T_{Elastic}^{2} = \frac{1}{MSE} \sum_{i=1}^{20} (Price_{i} - Price_{i})^{2} + \lambda (\alpha \frac{penalty_{Lasso}}{MSE} + (1-\alpha) \frac{penalty_{Ridge}}{MSE})$  (7.8)
```

```
$T_{Elastic}^{2} = \frac{1}{MSE} \sum_{i=1}^{20} (Price_{i} - Price_{i})^{2} + \lambda (\alpha \sum_{j=1}^{5} |\beta_{j}| \frac{penalty_{Lasso}}{MSE} + (1-\alpha) \sum_{j=1}^{5} \beta_{j}^{2} \frac{penalty_{Ridge}}{MSE})$  (7.9)
```

其中：$Price_{i} = \beta_{1}Sqft_{i} + \beta_{2}Sqft_{i} + \beta_{3}Sqft_{i} + \beta_{4}Sqft_{i} + \beta_{5}Sqft_{i} + \beta_{6}$

在方程 `(7.5)` 中你可以看到，`$penalty_{Lasso}$` 和 `$penalty_{Ridge}$` 的惩罚是加权平均值计算的。超参数 `$\alpha$` (`$0 \le \alpha \le 1$`) 决定了 Lasso 惩罚的占比。例如，如果 `$\alpha=0.5$`，则 Lasso 惩罚的占比为 50%，岭回归惩罚的占比 `$(1-\alpha)=0.5$` 也是 50%。如果 `$\alpha=0.3$`，Lasso 惩罚的占比为 30%，岭回归惩罚的占比 `$(1-\alpha)=0.7$` 为 70%。

超参数 `$\alpha$` 对应于 `linear_reg()` 函数中的混合参数。在第 7.4.1 节中已经使用过，当你设置 `mixture=1` 给 Lasso 惩罚分配 100% 的占比，给岭回归惩罚分配 0% 的占比 `$((1-\alpha)=0)$`——基本上是运行一个纯 Lasso 模型。

在第 7.4.2 节中，你可以通过设置 `mixture=$phi` (`$\alpha=0$`) 来运行纯岭回归，这意味着岭回归惩罚的占比为 100% `$((1-\alpha)=1)$`。

# 7 岭回归、Lasso 和弹性网络 —— 正则化详解

弹性方法的优点是你可以运行任何 Lasso 和岭回归正则化的混合。缺点是你需要对 `$\alpha$` (`mixture`) 另一个超参数进行调优，该参数需要在 `linear_reg` 命令中设置，或者与超参数 `$\lambda$` (`penalty`) 一起进行调优。

你将在后的第 7.5 节的交互式项目中调优这些超参数。在本节中，为了保持简单，我们通过任意设置超参数来将弹性网络实现到 tidymodels 中。

为弹性网络模型设置 tidymodels 工作流的命令与上一节几乎相同，只是我们任意设置了 `penalty=10000` 和 `mixture=0.5`。

```
seed(7777)
ModelDesignElasticNet=linear_reg(penalty=10000, mixture=0.5) |>
  set_engine("glmnet") |>
  set_mode("regression")

WFModelElasticNet=workflow() |>
  add_model(ModelDesignElasticNet) |>
  add_recipe(RecipeMouses) |>
  fit(DataTrain)
```

由于工作流 `WFModelRidge` 是一个已拟的工作流模型（它是使用训练数据进行校准的），我们可以使用 `tidy()` 命令提取模型：

```
tidy(WFModelElasticNet)
```

## A tibble: 6 x 3

| term estimate penalty |

| <chr> <dbl> <dbl> |

| 1 (Intercept) | 509945. | 10000 |

| 2 Sqft | 151417. | 10000 |

| 3 Sqft2 | 89828. | 10000 |

| 4 Sqft3 | 0 | 10000 |

| 5 Sqft4 | 0 | 10000 |

| 6 Sqft5 | -58923. | 10000 |

如预期的那样，`$\beta$` 参数（见 `estimate` 列）比第 7.3 节中未正则化的基准模型小得多。`$\beta_3$` 和 `$\beta_4$` 参数设置为零，消除了相关的预测变量

## 7.5 项目：使用弹性网络预测房价

交互章节

在这一节中，你将发现可以执行、修改和重新运行的 R 代码。阅读和处理本章节的最佳方法是在 RStudio 中打开它。你也可以选择在线

# 7 岭回归、Lasso 和弹性网络 —— 正则化详解

**要在交互式环境 中处理本章节，请按照以下步骤操作：**

- 确保已安装 `tweed` 和 `shiny` 包。如果没有，请从 RStudio 的主菜单（Tools -> Install Packages）安装。

- 下载交互式 R 文件并保存到你的项目文件夹。你需要下面的链接。

- 在 RStudio 中打开下载的文件，并点击编辑窗口顶部的“Run Document”按钮。

**不要跳过这个交互章节**，除了应用已涵盖的内容，它还将扩展你所学的知识。

详细帮助请参考：https://blog.large-analytics.com/2022/01/intersessions.html

以下是下载交互章节的链接：

https://ai.large-analytics.com/exc/?file=07-LassoExerc.100.Rmd

### 7.5.1 数据

你将使用 King County House Sale 数据集 (Kaggle2015) 预测房价。在下面的代码块中，加载了数据集。我们没有只选择一个变量来预测房价 (`Price`,)，而是使用 `select()` 命令选择了卧室数量 (`Bedr`,) 和建筑年份 (`Year`)，以及房屋的面积 (`Sqft`)。我们过滤了价格超过 $1,300,000 面积超过 4,500 平英尺的房屋，这些是离群值：

```
library(tidymodels); library(rio); library(janitor); library(glnet)
DataHousing=
import("https://ai.large-analytics.com/data/HousingData.csv") |
clean_names("upper_camel") |
select(Price, Sqft=Sqftliving, Bedr=Bedrooms, Year=YearBuilt) |
filter(Price<=1300000, Sqft<=4500)
set.seed(777)
```

# 项目：使用 Elastic-Net 预测房价

```r
Split005=initial_split(DataHousing, prop=0.005, strata=Price, breaks=5)
DataTrain=training(Split005)
DataTest=testing(Split005)
```

在创建训练数据集时，我们使用了 `prop=0.005` 参数，这导致训练集包含约 100 个观测值。虽然这个规模很小，但对于训练数据集来说通常是合理的。然而，考虑到总共有 20,699 个可用观测值，我们本可以使用更常用的 `prop=0.7`。在这种情况下，训练集将拥有 14,489 个观测值。有了如此庞大的训练集，我们在在本节后续使用的非正则化模型可能不会导致过拟合，因此将不再需要正则化——这会违背我们本次交互演示的目的。

### 7.5.2 非正则化基准模型

作为基准，我们从一个非正则化模型开始。在这种情况下，这是一个多变量二次多项式模型。它包含了 `Sqft`、`Bedr` 和 `Year` 变量。它们以原始形式出现，并作为各种交互项的形式：

```
Price = \beta_1Sqft + \beta_2Bedr + \beta_3Year$
$+ \beta_4Sqft^2 + \beta_5Bedr^2 + \beta_6Year^2$
$+ \beta_7SqftBedr + \beta_8SqftYear + \beta_9BedrYear$
$+ \beta_{10}Sqft^2Bedr + \beta_{11}SqftBedr^2 + \beta_{12}Sqft^2Bedr^2$
$+ \beta_{13}SqftYear^2 + \beta_{14}SqftYear^2 + \beta_{15}Year^2$
$+ \beta_{16}Bedr^2Year + \beta_{17}BedrYear^2 + \beta_{18}BedrYear^2$ (7.10)
```

随后，我们使用 `recipe` 来生成并归一化预测变量：

```r
RecipeHousesMultivar=recipe(Price ~, data=DataTrain) |>
step_mutate(Sqft=Sqft^2, Bedr=Bedr^2, Year=Year^2,
SqftBedr=Sqft*Bedr, SqftYear=Sqft*Year,
BedrYear=Bedr*Year, Sqft2Bedr=Sqft*Bedr,
SqftBedr2=Sqft*Bedr^2, Sqft2Bedr2=Sqft^2*Bedr,
Sqft2Year=Sqft^2*Year, SqftYear2=Sqft*Year,
Sqft2Year2=Sqft*Year^2, Bedr2Year=Bedr^2*Year,
BedrYear2=Bedr*Year^2, Bedr2Year2=Bedr^2) |>
step_normalize(all_predictors())
```

随后，我们创建了模型设计 (`ModelDesignBenchmark`)、工作流 (workflow)

## 7 Ridge、Lasso 和 Elastic-Net — 正则化详解

`model(WFModelBenchmark)`，并将 `WFModelBenchmark` 拟准到训练数据：

```r
ModelDesignBenchmark=linear_reg() |>
set_engine("lm") |>
set_mode("regression")
```

```r
WFModelBenchmark=workflow() |>
add_model(ModelDesignBenchmark) |>
add_recipe(RecipeHousesMultivar) |>
fit(DataTrain)
```

当你执行代码块中的 `tidy()` 时，你会发现除截距项外，所有预测变量的参数 (`β`) 都在百万级，有些甚至是十亿级（请看 `estimate` 列）。

```r
tidy(WFBenchmark)
```

当你执行下面的代码块时，模型对训练数据和测试数据的预测值将与真实值 (`Price`) 进行比较，并计算相关指标：

```r
DataTrainWithPredBenchmark=augment(WFBenchmark, DataTrain)
print("Metrics for Training Data:")
metrics(DataTrainWithPredBenchmark, truth=Price, estimate=.pred)
```

```r
DataTestWithPredBenchmark=augment(WFBenchmark, DataTest)
print("Metrics for Testing Data:")
metrics(DataTestWithPredBenchmark, truth=Price, estimate=.pred)
```

执行代码后，你会发现训练数据的 `mae` 约为 111,700，而测试数据的 `mae` 约为 142,800。如此低的训练 `mae` 强烈表明过拟合。在接下来的章节中，我们将使用 Elastic-Net 模型来提高预测质量。

### 7.5.3 正则化 Elastic-Net 模型

将下方 `mixture=` 和 `penalty=` 替换为你选择的值并执行，模型的 β 值将被校准并打印。同时也会计算并打印测试数据的指标。记住，如果 `mixture=0`，将运行 Ridge 模型；如果 `mixture=1`，将运行 Lasso 模型。对于之间的任何值，将运行混合模型。

寻找合适的 `penalty=` 值比较复杂。对于 Ridge，15,000 到 14,000 之间的值是有效的。对于 Lasso，15 到 14,000 之间的值也是有效的。通过几个设置可以观察结果的变化，例如 `mixture=1` (Lasso) 和 `penalty=10000`。你也可以设置 `mixture=0.5` 或 `0.7` 来尝试不同的 Elastic-Net 模型。尝试不同的超参数值并观察 beta 和指标将有助于更好地理解正则化。

```r
ModelDesignRegularized=linear_reg(penalty=..., mixture=...) |>
set_engine("glmnet") |>
set_mode("regression")

WFModelRegularized=workflow() |>
add_model(ModelDesignRegularized) |>
add_recipe(RecipeHousesMultivar) |>
fit(DataTrain)

print("Beta Values (see Column Estimate):")
tidy(WFRegularized)

DataTestWithPredRegularized=augment(WFRegularized, DataTest)
print("Metrics for Testing Data:")
metrics(DataTestWithPredRegularized, truth=Price, estimate=.pred)
```

**警告****永远不要使用测试数据来寻找最佳参数。相反，请使用来自训练集的验证数据。

### 7.5.4 调优 Elastic-Net 模型

在本节中，我们将使用模板来调优超参数 `penalty` 和 `mixture`。

- 步骤 1 - 生成 Recipe 和数据：训练和测试数据已经生成（见上方 7.5.3 节）。

- 步骤 2 - 创建 Recipe：多变量二次多项式模型的预测变量 Recipe (`RecipeHousesMultivar`) 是结合非正则化模型创建的，建立了各种幂次和交互。

- 步骤 3 - 创建模型设计：上一节的模型设计需要微调。你需要为超参数添加 `tune()` 占位符：

```r
ModelDesignElasticTune <- linear_reg(penalty=tune(), mixture=tune()) |>
set_engine("glm") |>
set_mode("regression")
```

- 步骤 4 - 将 Recipe 和模型设计添加到 Workflow：我们将 Recipe 和（修改后的）模型设计添加到 workflow：

```r
TuneWorkflow <- workflow() |>
add_recipe(RecipeHousesMultivar) |>
add_model(ModelDesignElasticTune)
```

- 步骤 5 - 创建超参数网格：之前当只调优一个超参数时，你将尝试的值添加到与超参数同名的列中。当你有多个超参数时，情况变得稍微复杂，因为你想尝试不同的组合。如果你决定尝试两个或多个超参数值的所有组合，可以使用 `crossing()` 命令。`crossing()` 命令的参数是你想要尝试的超参数。分配给这些参数的值是你对每个超参数想要尝试的值。它们作为 R 向量分配给每个参数。然后 `crossing()` 命令会生成超参数值的所有组合。

例如，在该项目中，你之后尝试了从 15,000 到 80,000、增量为 1,000 的 66 个罚值，以及三个混合值（0、0.5 和 1）。你可以使用 `crossing()` 命令生成所有组合：

```r
ParGridHouses=crossing(mixture=c(0, 0.5, 1),
              penalty=seq(15000, 80000, 1000))
```

## A tibble: 198 x 2

| mixture | penalty |

| :--- | :--- |

| 1 | 15000 |

| 2 | 16000 |

| 3 | 17000 |

| 4 | 18000 |

| 5 | 19000 |

| 6 | 20000 |

| 7 | 21000 |

| 8 | 22000 |

| 9 | 23000 |

| 10 | 24000 |

| ... | 188 more rows |

分配给 `mixture` 的 R 向量是用 `c()` 命令创建的。分配给 `penalty` 的 R 向量是用 `seq()` 命令创建的。`seq()` 中的第一个值决定序列开始于（15,000），第二个值结束于（80,000）。第三个参数决定增量（步长；1,000）。

你可以从上面的输出中看到 `crossing()` 生成了罚值和混合值的所有可能组合。当你稍后调优工作流时，这 198 个组合中的每一个都将尝试尝试。

194 Ridge、Lasso 和 Elastic-Net —— 正化详解
