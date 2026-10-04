

一般来说，所有降维方法都首先将原始预测变量汇总为少数几个新变量，称为主成分（`PCs`），然后将这些主成分用作预测变量来拟合线性回归模型。这些方法避免了预测变量之间的多重共线性，这在回归设定中是一个大问题（参见第 [10](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) 章）。

在使用降维方法时，通常建议对每个预测变量进行标准化以使其可比较。标准化包括将预测变量除以其标准差。

这里，我们描述了两种基于降维的知名回归方法：`Principal Component Regression`（`PCR`）和 `Partial Least Squares`（`PLS`）回归。我们还提供了 R 中的实践示例。

## 20.2 主成分回归

主成分回归（`PCR`）首先对数据集应用 [主成分分析](http://www.sthda.com/english/articles/31-principal-component-methods-in-r-practical-guide/112-pca-principal-component-analysis-essentials/)，将原始预测变量汇总为少数几个新变量，也称为主成分（`PCs`），它们是原始数据的线性组合。

这些 `PCs` 然后用于构建线性回归模型。要纳入模型的 principal components 数量由交叉验证（`cv`）选择。请注意，`PCR` 适用于数据集中包含高度相关预测变量的情况。

## 20.3 偏最小二乘回归

`PCR` 的一个可能缺点是，我们无法保证所选的主成分与结果相关。这里，主成分的选择纳入模型时不受结果变量的监督。

`PCR` 的替代方法是 `Partial Least Squares`（`PLS`）回归，它识别新的主成分，这些主成分不仅汇总原始预测变量，而且与结果相关。这些成分随后用于拟合回归模型。因此，与 `PCR` 相比，`PLS` 使用一种由结果监督的降维策略。

与 `PCR` 一样，`PLS` 适用于具有高度相关预测变量的数据。`PLS` 中使用的 `PCs` 数量通常由交叉验证选择。预测变量和结果变量通常应进行标准化，以使变量可比较。

## 20.4 加载所需的 R 包

* `tidyverse` 用于轻松的数据操作和可视化
* `caret` 用于轻松的机器学习工作流
* `pls`，用于计算 `PCR` 和 `PLS`

```
```

## 20.5 准备数据

我们将使用 `Boston` 数据集 [在 `MASS` 包中]，该数据集在第 [3](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) 章中介绍，用于基于多个预测变量预测波士顿郊区的房屋中位数价值（`medv`）。

我们将随机将数据拆分为训练集（80% 用于构建预测模型）和测试集（20% 用于评估模型）。请确保设置种子以确保可重复性。

```
```

## 20.6 计算

R 函数 `train()` [`caret` 包] 提供了通过调用 `pls` 包来计算 `PCR` 和 `PLS` 的简易工作流。它有一个名为 `method` 的选项，可以取值为 `pcr` 或 `pls`。

一个附加参数是 `scale = TRUE`，用于标准化变量以使其可比较。

`caret` 使用交叉验证自动识别要纳入模型的最佳主成分数量（`ncomp`）。

在这里，我们将测试调优参数 `ncomp` 的 10 个不同值。这是通过选项 `tuneLength` 指定的。最佳主成分数量的选择使得交叉验证误差（`RMSE`）最小化。

### 20.6.1 计算主成分回归

```
```

```
##   ncomp
## 5     5
```

```
```

```
## Data:    X dimension: 407 13 
##  Y dimension: 407 1
## Fit method: svdpc
## Number of components considered: 5
## TRAINING: % variance explained
##           1 comps  2 comps  3 comps  4 comps  5 comps
## X           47.48    58.40    68.00    74.75    80.94
## .outcome    38.10    51.02    64.43    65.24    71.17
```

```
```

```
##   RMSE Rsquare
## 1 5.18   0.645
```

![](Image00017.jpg)

该图显示了模型根据纳入模型的主成分数量所产生的预测误差（`RMSE`，第 [13](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) 章）。

我们的分析表明，选择五个主成分（`ncomp = 5`）可获得最小的预测误差 `RMSE`。

`summary()` 函数还提供了使用不同数量成分在预测变量（`x`）和结果（`medv`）中解释的方差百分比。

例如，5 个主成分（`ncomp = 5`）捕获了预测变量中 80.94% 的变异（或信息）。此外，设置 `ncomp = 5`，捕获了结果变量（`medv`）中 71% 的信息，这是不错的。

综合来看，交叉验证确定 `ncomp = 5` 为使预测误差（`RMSE`）最小化并解释预测变量和结果中足够变异的最佳 `PCs` 数量。

### 20.6.2 计算偏最小二乘

R 代码与 `PCR` 方法完全相同。

```
```

```
##   ncomp
## 9     9
```

```
```

```
## Data:    X dimension: 407 13 
##  Y dimension: 407 1
## Fit method: oscorespls
## Number of components considered: 9
## TRAINING: % variance explained
##           1 comps  2 comps  3 comps  4 comps  5 comps  6 comps  7 comps
## X           46.19    57.32    64.15    69.76    75.63    78.66    82.85
## .outcome    50.90    71.84    73.71    74.71    75.18    75.35    75.42
##           8 comps  9 comps
## X           85.92    90.36
## .outcome    75.48    75.49
```

```
```

```
##   RMSE Rsquare
## 1 4.99   0.671
```

![](Image00018.jpg)

纳入 `PLS` 模型的最佳主成分数量为 9。这捕获了预测变量中 90% 的变异和结果变量（`medv`）中 75% 的变异。

在我们的示例中，使用 `PLS` 模型获得的交叉验证误差 `RMSE` 低于使用 `PCR` 方法获得的 `RMSE`。因此，与 `PCR` 模型相比，`PLS` 模型是解释我们数据的最佳模型。

## 20.7 讨论

本章描述了基于主成分的回归方法，包括主成分回归（`PCR`）和偏最小二乘回归（`PLS`）。这些方法对于包含相关预测变量的多变量数据非常有用。

数据中存在相关性允许将数据汇总为少数几个非冗余成分，可用于回归模型。

与岭回归和 lasso（第 [19](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) 章）相比，最终的 `PCR` 和 `PLS` 模型更难解释，因为它们不执行任何变量选择，甚至不直接产生回归系数估计。

# 21 引言

之前，我们描述了回归模型（第 [3](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) 章），它用于基于一个或多个预测变量预测定量或连续的结果变量。

在 `Classification` 中，结果变量是定性的（或分类的）。`Classification` 指的是一组机器学习方法，用于根据一个或多个预测变量预测个体的类别（或类别）。

在本部分中，我们将涵盖以下主题：

* Logistic 回归，用于二元分类任务（第 [22](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) 章）
* 用于变量选择的逐步和惩罚 logistic 回归（第 [23](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) 和 [24](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) 章）
* Logistic 回归假设和诊断（第 [25](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) 章）

