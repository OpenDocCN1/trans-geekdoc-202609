
* `nvmax` : 模型中的变量数量。例如 `nvmax = 2`，指定最佳的 2 变量模型

* `RMSE` 和 `MAE` 是衡量每个模型预测误差的两种不同指标。`RMSE` 和 `MAE` 越低，模型越好。

* `Rsquared` 表示观测结果值与模型预测值之间的相关性。R 平方越高，模型越好。

在我们的示例中，可以看出变量数为 4 的模型（`nvmax = 4`）具有最低的 `RMSE`。你可以按如下方式显示由 `train()` 函数自动选择的最佳调优值（`nvmax`）：

```
```

```
##   nvmax
## 4     4
```

这表明最佳模型是具有 `nvmax = 4` 个变量的模型。函数 `summary()` 会报告每个模型规模的最佳变量集合，直到最佳的 4 变量模型。

```
```

```
## Subset selection object
## 5 Variables  (and intercept)
##                  Forced in Forced out
## Agriculture          FALSE      FALSE
## Examination          FALSE      FALSE
## Education            FALSE      FALSE
## Catholic             FALSE      FALSE
## Infant.Mortality     FALSE      FALSE
## 1 subsets of each size up to 4
## Selection Algorithm: backward
##          Agriculture Examination Education Catholic Infant.Mortality
## 1  ( 1 ) " "         " "         "*"       " "      " "             
## 2  ( 1 ) " "         " "         "*"       "*"      " "             
## 3  ( 1 ) " "         " "         "*"       "*"      "*"             
## 4  ( 1 ) "*"         " "         "*"       "*"      "*"
```

星号指定某个变量被包含在对应的模型中。例如，可以看出最佳的 4 变量模型包含 Agriculture、Education、Catholic、Infant.Mortality（`Fertility ~ Agriculture + Education + Catholic + Infant.Mortality`）。

最终模型（`id = 4`）的回归系数可以按如下方式访问：

```
```

或者，通过仅使用所选预测变量计算线性模型：

```
```

```
## 
## Call:
## lm(formula = Fertility ~ Agriculture + Education + Catholic + 
##     Infant.Mortality, data = swiss)
## 
## Coefficients:
##      (Intercept)       Agriculture         Education          Catholic  
##           62.101            -0.155            -0.980             0.125  
## Infant.Mortality  
##            1.078
```

## 18.4 讨论

本章描述了逐步回归方法，以便在不损害模型精度的情况下选择一个最优的简单模型。

我们演示了如何使用 `leaps` R 包计算逐步回归。另一个替代方案是 MASS 包中提供的函数 `stepAIC()`。它有一个名为 `direction` 的选项，可以具有以下值："both"、"forward"、"backward"。

```
```

此外，caret 包有使用 MASS 包计算逐步回归的方法（`method = "lmStepAIC"`）：

```
```

逐步回归对于包含多个预测变量的高维数据非常有用。其他替代方案是惩罚回归（岭回归和套索回归）（第 [19](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) 章）和基于主成分的回归方法（PCR 和 PLS）（第 [20](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) 章）。

# 19 惩罚回归：岭回归、套索回归和弹性网络

## 19.1 引言

标准线性模型（或普通最小二乘法）在你拥有一个包含变量数多于样本数的大型多变量数据集的情况下表现不佳。

更好的替代方案是惩罚回归，它允许创建在模型中变量过多时受到惩罚的线性回归模型，通过在方程中添加约束来实现（James et al. [2014](#text00039.html#ref-james2014)，P. Bruce and Bruce ([2017](#text00039.html#ref-bruce2017)))。这也被称为收缩或正则化方法。

施加此惩罚的后果是使系数值减小（即收缩）趋向于零。这使得贡献较小的变量的系数接近于零或等于零。

请注意，收缩需要选择一个调优参数（lambda），该参数决定收缩的程度。

在本章中，我们将描述最常用的惩罚回归方法，包括岭回归、套索回归和弹性网络回归。我们还将提供 R 中的实际示例。

## 19.2 收缩方法

### 19.2.1 岭回归

岭回归收缩回归系数，使得对结果贡献较小的变量的系数接近于零。

系数的收缩是通过对回归模型施加一个称为 L2 范数的惩罚项来实现的，该惩罚项是系数的平方和。

惩罚的程度可以通过一个常数 lambda（`λ\lambda`）进行微调。选择 `λ\lambda` 的良好值至关重要。

当 `λ=0\lambda = 0` 时，惩罚项没有效果，岭回归将产生经典的最小二乘系数。然而，随着 `λ\lambda` 增加到无穷大，收缩惩罚的影响增大，岭回归系数将接近于零。

请注意，与普通最小二乘回归相反，岭回归受预测变量尺度的影响很大。因此，在应用岭回归之前最好对预测变量进行标准化（即缩放）（James et al. [2014](#text00039.html#ref-james2014)），以便所有预测变量处于同一尺度。

预测变量 `x` 的标准化可以通过公式 `x' = x / sd(x)` 实现，其中 `sd(x)` 是 `x` 的标准差。其后果是，所有标准化后的预测变量的标准差都为一，从而使最终拟合不依赖于预测变量的测量尺度。

岭回归的一个重要优点是，与普通最小二乘法（第 [4](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) 章）相比，在预测变量数（`p`）大于观测数（`n`）的大型多变量数据情况下，它仍然表现良好。

岭回归的一个缺点是，它会将所有预测变量都包含在最终模型中，不像逐步回归方法（第 [18](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) 章），后者通常会选择涉及较少变量集的模型。

岭回归将系数收缩向零，但不会将任何系数精确地设为零。套索回归是克服这一缺点的替代方法。

### 19.2.2 套索回归

Lasso 代表 Least Absolute Shrinkage and Selection Operator。它通过对回归模型施加一个称为 L1 范数的惩罚项来收缩回归系数向零，该惩罚项是系数的绝对值之和。

在套索回归的情况下，惩罚的效果是使一些对模型贡献较小的系数估计强制精确等于零。这意味着套索也可以被视为一种替代子集选择方法，用于执行变量选择以减少模型的复杂性。

与岭回归一样，选择套索的 `λ\lambda` 的良好值至关重要。

套索回归相对于岭回归的一个明显优势是，它产生更简单、更易解释的模型，仅包含一组减少的预测变量。然而，岭回归和套索都不会普遍占优于另一个。

一般来说，套索可能在某些预测变量具有大系数，而剩余预测变量具有非常小系数的情况下表现更好。

