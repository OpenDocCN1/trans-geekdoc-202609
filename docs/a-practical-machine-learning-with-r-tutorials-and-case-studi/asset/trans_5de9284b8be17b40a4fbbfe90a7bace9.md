

## 7 Ridge, Lasso, 和 Elastic-Net — 正则化 $\beta$

$\widehat{Price}_i = \beta_1Sqft_i + \beta_2Sqft_i^2 + \beta_3Sqft_i^3 + \beta_4Sqft_i^4 + \beta_5Sqft_i^5 + \beta_6 \quad (7.1)$

对于像这样的未正则化模型，其**模型参数**由**优化器**（Optimizer）决定，目标是最小化误差函数——即均方误差（MSE）：

$MSE = \frac{1}{20} \sum_{i=1}^{20} (\widehat{Price}_i - Price_i)^2 \quad (7.2)$

其中：
$$\widehat{Price}_i = \beta_1Sqft_i + \beta_2Sqft_i^2 + \beta_3Sqft_i^3 + \beta_4Sqft_i^4 + \beta_5Sqft_i^5 + \beta_6$$

当你在误差函数 (7.2) 中用房屋观测的估计价格 ($\widehat{Price}_i$) 替换时，你可以发现 $MSE$ 仅取决于**模型参数**（$\beta$）。这是因为训练数据决定了所有其他值（$Price$ 和 $Sqft_i$）。

因此，**优化器**可以通过系统的**试错**（trial-and-error）方法寻找最优模型参数（$\beta_{opt}$），从而达到最小化 $MSE$ 的目标。

下面的代码块显示 `WFModel\Benchmark` 与我们在第 6.4 节中为**多项式回归**模型创建的工作流之间区别不大。

不同在于配方（recipe），因为我们使用 `step_normalize(all_predictors())` 对所有预测变量进行 $Z$-score 标准化（关于预测变量归一化的细节见第 4.6 节）。

**多项式回归模型**通常不需要归一化。但我们仍然对预测变量进行了归一化，因为我们将此工作流模型作为基准，与三个正则化回归模型进行比较——**Lasso**（见第 7.1 节）、Ridge（见第 7.4.2 节）和 **Elastic-Net**（见第 7.4.3 节）。这三个模型都需要**归一化**，基准模型也必须使用归一化的预测变量才能具有可比性。

要了解正则化模型为何需要归一化，请参此章的数字资源部分（见第 7.7 节）。

```
library(tidymodels)
ModelDesignBenchmark<-linear_reg() |>
  set_engine("lm") |>
  set_model("regression")
RecipeHouses<-recipe(Price=,data=DataTrain) |>
  step_mutate(Sqft2=Sqft^2,Sqft3=Sqft^3)
```

## 7.3 未正则化的基准模型

```
Sqft4=Sqft^4,Sqft5=Sqft^5) |>
  step_normalize(all_predictors())
```

```
WFModelBenchmark~workflow() |>
add_model(ModelDesignBenchmark) |>
add_recipe(RecipeHouses) |>
fit(DataTrain)
```

由于上述代码为 5 次多项式模型创建了一个拟合的工作流模型，我们可以利用 `tidy()` 命令从该拟合工作流中提取用于房价分析的 $\beta$ 参数：

### 表格：6 x 5
| term | estimate std.error statistic p.value |
| <dbl> | <dbl> | <dbl> | <dbl> |
| (Intercept) | 509945 | 36463 | 14.0 | 1.28e-09 |
| Sqft2 | 8853783 | 1051548 | 0.842 | 4.14e-04 |
| Sqft3 | -5094714 | 54350275 | -0.937 | 3.64e-01 |
| Sqft4 | 112589222 | 111217647 | 1.01 | 3.29e-01 |
| Sqft5 | -106894260 | 101895738 | -1.05 | 3.12e-01 |
| Sqft6 | 36592435 | 3468741 | 1.05 | 3.09e-01 |

我们稍后会回到这些值。现在，请记住单个 $\beta$ 参数（estimate 列）是不可解释的。这是因为 5 次多项式模型太复杂，难以易于解释。但请尝试记住，除了截距（$\beta_0$）外，大多数 $\beta$ 值都在三百万范围内。我们稍后将看到正则化如何降低其中一些值或将它们置零。

现在，让我们看看未正则化基准模型 (WFModelBenchmark) 的预测质量。我们使用下方代码块所示 R 代码开始评估训练数据。`augment()` 命令创建预测并将它们扩展到训练数据中。之后，`metrics()` 计算了均方根误差 (rmse)、$r^2$ (rsq) 和平均绝对误差 (mae)，其中 `DataTrainWithPredBenchmark` 包含了训练观测的预测价格和真实价格：

```
DataTrainWithPredBenchmark=augment(WFModelBenchmark, DataTrain)
metrics(DataTrainWithPredBenchmark, true=Price, estimate=.pred)
```

## 7 Ridge, Lasso, 和 Elastic-Net — 正则化解释

### tibble: 3 x 3
| .metric | .estimator | .estimate |
| <chr> | <chr> | <dbl> |
| 1 rmse | standard | 136432. |
| 2 rsq | standard | 0.715 |
| 3 mae | standard | 104847. |

为了评估测试数据上的预测质量，我们将相同的代码应用于测试数据：

```
DataTestWithPredBenchmark=augment(WFModelBenchmark, DataTest)
metrics(DataTestWithPredBenchmark, truth=Price, estimate=$.pred)
```

### tibble: 3 x 3
| .metric | .estimator | .estimate |
| <chr> | <chr> | <dbl> |
| 1 rmse | standard | 9994240. |
| 2 rsq | standard | 0.0215 |
| 3 mae | standard | 1719470. |

基于训练数据的平均绝对误差 (mae) 约为 104,000，而测试数据上的相同指标约为 1,719,500。这是过拟合问题的强信号。

## 7.4 正则化的原理

在第 6 章中，我们调整了超参数以避免过拟合。在本章中，我们将通过正则化来解决这个问题。

### 正则化

正则化是在模型校准期间应用的一种技术。其目标是生成比相关未正则化模型更小的模型参数 ($\lambda$)，可能为零。

小的模型参数削弱相关预测变量的影响，或者在参数为零时将其消除。

变量较少或某些变量影响被严重削弱的模型灵活性较低，因此过拟合的可能性会降低。

从本质上说，正则化最小化或消除了解释能力弱的预测变量对输出变量的影响，从而提高了预测性能。

