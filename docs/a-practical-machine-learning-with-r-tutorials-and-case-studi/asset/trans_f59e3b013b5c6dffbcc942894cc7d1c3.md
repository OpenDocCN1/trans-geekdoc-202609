

# 项目：使用 Elastic-Net 预测房价

```r
Split005=initial_split(DataHousing, prop=0.005, strata=Price, breaks=5)
DataTrain=training(Split005)
DataTest=testing(Split005)
```

在创建训练数据集时，我们使用了 `prop=0.005` 参数，这导致训练集包含约 100 个观测值。虽然这个规模很小，但对于训练数据集来说通常是合理的。然而，考虑到总共有 20,699 个可用观测值，我们本可以使用更常用的 `prop=0.7`。在这种情况下，训练集将拥有 14,489 个观测值。有了如此庞大的训练集，我们在在本节后续使用的非正则化模型可能不会导致过拟合，因此将不再需要正则化——这会违背我们本次交互演示的目的。

## 7.5.2 非正则化基准模型

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

当你执行代码块中的 `tidy()` 时，你会发现除截距项外，所有预测变量的参数 (β) 都在百万级，有些甚至是十亿级（请看 `estimate` 列）。

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

## 7.5.3 正则化 Elastic-Net 模型

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

## 7.5.4 调优 Elastic-Net 模型

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

