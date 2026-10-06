

## 6.5 调整多项式模型的复杂度

均方根误差 (rmse)、$r^2$ (rsq) 和平均绝对误差 (mae) 是针对每个参数值和每个折叠计算的。^6

```r
TuneResultsHouses=tune_grid(TuneMFHouses, resamples=FoldsHouses,
  grid=ParGridHouses,
  metrics=metric_set(rmse,rsq))
```

调整工作流（workflow）可能需要一些时间，从几秒钟到一天更久不等，取决于要调整的超参数数量以及用于验证的折叠数量。在上面的代码中，`tune_grid()` 的每个参数值、每个折叠和每个性能指标的结果都保存在 R 对象 `Houses` 中。

有几种方法从 R 对象 `Houses` 中提取信息。例如，你可以使用 `autoplot()` 命令创建不同超参数值性能的图形化概述（见图 6.5）。

![](img/f240d449191f5add983daf6c380e4fe3_169_0.png)

图 6.5 调整期间的性能指标

图 6.5 中的图表明，线性方程（degree=1）的表现不如某些次数大于1 的多项式。

> ^6 如果你倾向于使用我们在本节初开发的验证集，可以将 `resamples=` 参数更改为 `resamples=OutVal|date`。

## 6 多项式回归 — 过拟合/调整详细说明

次数 2 到 8 的性能在三个指标上是类似的（rsq 指标的 degree=7 除外）。

根据对交叉验证折叠的评估，次数为 9 和 10 的多项式预测性能较差。

为了了解更多细节，我们根据这三个性能指标从工作流 `TuneResultsHouses` 中提取超参数值排名。我们首先使用均方根误差 (rmse) 指标选取前五个超参数：

```r
show_best(TuneResultsHouses, metric="rmse")
```

## 表格：5 x 7
| degree | .estimator | mean | n | std_err |
| :--- | :--- | :--- | :--- | :--- |
| 6 | rmse | standard | 251993 | 4 | 6179. |
| 8 | rsq | standard | 252279 | 4 | 5971. |
| 2 | rmse | standard | 255965 | 4 | 7243. |
| 3 | rmse | standard | 257680 | 4 | 7875. |
| 4 | rsq | standard | 260994 | 4 | 9911. |

对于次数为 6 的多项式，最佳）rmse 为 251,993。线性模型（degree=1）没有进入前五。

基于 $r^2$ 的前五个最佳模型排名与以下项的排名是相同的：

平均绝对误差 mae 的排名略有不同。然而，最佳模型仍然是 6 次多项式模型：

```r
show_best(TuneResultsHouses, metric="mae")
```

## 表格：5 x 7
| degree | .metric_estimator | mean | n | std_err |
| :--- | :--- | :--- | :--- | :--- |
| 6 | mae | standard | 165798 | 4 | 1924. |
| 8 | mae | standard | 165868 | 4 | 1764. |
| 4 | mae | standard | 166325 | 4 | 2137. |
| 3 | mae | standard | 166434 | 2 | 1863. |
| 2 | mae | standard | 166546 | 4 | 1840. |

由于所有三个性能指标都将 6 次多项式模型评为最佳模型，因此选择哪种性能指标来提取最佳模型的数据并不重要。例如，为了提取最小 rmse 的最佳超参数，我们可以使用：

```r
BestHyperPar=select_best(TuneResultsHouses, "rmse")
print(BestHyperPar)
```

## 表格：1 x 2
| degree | .config |
| :--- | :--- |
| 6 | Preprocessor06_Modell |

`BestHyperPar` 的输出显示最佳超参数值保存在数据列 `degree` 中，作为第一个且也是唯一的条目。

我们将使用此数据框创建一个具有最佳超参数（degree=6）的模型（最佳模型）。

为了做到，我们使用 `finalize_workflow()` 将最佳参数添加到 tune 工作流中。该命令更新 `tune()` 占位符为存储在 `BestHyperPar` 中的最优参数值。之后，我们调用 `fit()` 管道来训练工作流模型：

```r
BestWFModelHouses=TuneWFModelHouses |
  finalize_workflow(BestHyperPar) |
  fit(DataTrain)
print(BestWFModelHouses)
```

## Workflow [已训练] ==================================
## Preprocessor: Recipe
## Model: linear_reg()
##
## Preprocessor
## 1 Recipe
## 1 Step
## * step_poly()

```r
## Model -
## Call:
 stats::lm(formula = ..y ., data = data)
## Coefficients:
## (Intercept) Sqft_poly_1 Sqft_poly_2 Sqft_poly_3
## -1.30e+04 6.57e-02 -4.90e-01 2.05e-04
## Sqft_poly_4 Sqft_poly_5 Sqft_poly_6
## -1.76e-08 3.18e-12 -9.93e-07
```

上述拟合工作流的输出确认了 `WFModelHouses` 是一个拟合的工作流，因为它包含了参数值（见 Coefficients）。因此，`WFModelHouses` 可用于预测。我们使用 `augment()` 命令根据测试数据集进行预测并计算指标：

```r
DataTestWithBestModel=augment(BestModelHouses, DataTest)
metrics(DataTestWithBestModel, true.pred, estimate)
```

## 表格：3 x 3
| .metric | .estimate |
| :--- | :--- |
| rmse | standard |
| rsq | standard |
| mae | standard |

由于所有三个性能指标都将 6 次多项式模型评为最佳模型，因此选择哪种性能指标来提取最佳模型的数据并不重要。例如，为了提取最小 rmse 的最佳超参数，我们可以使用：

（注：此处原文逻辑似乎存在重复或断码，已根据语意进行翻译）

