
The R function `predict()` can be used to predict the probability of being diabetes-positive, given the predictor values.

**Predict the probabilities** of being diabetes-positive:

```
##     21     25     28     29     32     36 
## 0.3914 0.6706 0.0501 0.5735 0.6444 0.1494
```

Which classes do these probabilities refer to? In our example, the output is the probability that the diabetes test will be positive. We know that these values correspond to the probability of the test to be positive, rather than negative, because the `contrasts()` function indicates that R has created a dummy variable with a 1 for "pos" and "0" for neg. The probabilities always refer to the class dummy-coded as "1".

Check the dummy coding:

```
##     pos
## neg   0
## pos   1
```

**Predict the class of individuals** :

The following R code categorizes individuals into two groups based on their predicted probabilities `p` of being diabetes-positive. Individuals, with `p` above 0.5 `random guessing`, are considered as diabetes-positive.

```
##    21    25    28    29    32    36 
## "neg" "pos" "neg" "pos" "pos" "neg"
```

## 22.8 Assessing model accuracy

The model accuracy is measured as the proportion of observations that have been correctly classified. Inversely, the classification error is defined as the proportion of observations that have been misclassified.

Proportion of correctly classified observations:

```
## [1] NA
```

The classification prediction accuracy is about 77%, which is good. The misclassification error rate is 23%.

Note that, there are several metrics for evaluating the performance of a classification model `Chapter 30`.

## 22.9 Discussion

In this chapter, we have described how logistic regression works and we have provided R codes to compute logistic regression. Additionally, we demonstrated how to make predictions and to assess the model accuracy. Logistic regression model output is very easy to interpret compared to other classification methods. Additionally, because of its simplicity it is less prone to overfitting than flexible methods such as decision trees.

Note that, many concepts for linear regression hold true for the logistic regression modeling. For example, you need to perform some diagnostics `Chapter 25` to make sure that the assumptions made by the model are met for your data.

Furthermore, you need to measure how good the model is in predicting the outcome of new test data observations. Here, we described how to compute the raw classification accuracy, but not that other important performance metric exists `Chapter 30`

In a situation, where you have many predictors you can select, without compromising the prediction accuracy, a minimal list of predictor variables that contribute the most to the model using `stepwise regression` `Chapter 23` and `lasso regression` techniques `Chapter 24`.

Additionally, you can add interaction terms in the model, or include spline terms.

The same problems concerning confounding and correlated variables apply to logistic regression `see Chapter 11` and `Chapter 10`.

你也可以拟合 *广义加性模型*（第 7 章），当预测变量的线性关系无法假设时。这可以使用 `mgcv` 包完成：

```

Logistic 回归仅限于两类分类问题。有一个扩展，称为 *多项 logistic 回归*，用于多类分类问题（第 26 章）。

请注意，对于多类任务，最流行的方法是 *线性判别分析*（第 27 章）。

## 23 逐步 Logistic 回归

**逐步 logistic 回归** 包括自动选择较少的预测变量数量来构建性能最佳的 logistic 回归模型。更多内容请阅读第 18 章。

本章描述如何在 **R** 中计算逐步 logistic 回归。

## 23.1 加载所需的 R 包

* `tidyverse` 用于便捷的数据操作和可视化
* `caret` 用于便捷的机器学习工作流

```

## 23.2 准备数据

数据集：`PimaIndiansDiabetes2` [在 `mlbench` 包中]，在第 21 章中介绍，用于基于多个临床变量预测患糖尿病的概率。

我们将随机将数据拆分为训练集（80% 用于构建预测模型）和测试集（20% 用于评估模型）。请确保设置种子以保证可重复性。

```

## 23.3 计算逐步 logistic 回归

逐步 logistic 回归可以使用 `MASS` 包中提供的 R 函数 `stepAIC()` 轻松计算。它通过 AIC 进行模型选择。它有一个名为 `direction` 的选项，可以具有以下值：“both”、“forward”、“backward”（参见第 18 章）。

### 23.3.1 快速入门 R 代码

```

### 23.3.2 完整 logistic 回归模型

包含所有预测变量的完整模型：

```

```

## (Intercept)    pregnant     glucose    pressure     triceps     insulin 

##    -9.50372     0.04571     0.04230    -0.00700     0.01858    -0.00159 

##        mass    pedigree         age 

##     0.04502     0.96845     0.04256

```

### 23.3.3 执行逐步变量选择

选择最具贡献的变量：

```

```
## (Intercept)     glucose        mass    pedigree         age 
##     -9.5612      0.0379      0.0523      0.9697      0.0529
```

该函数选择了一个最终模型，其中一个变量已从原始完整模型中移除。被剔除的预测变量是：`triceps`。

### 23.3.4 比较完整模型和逐步模型

在这里，我们将比较完整和逐步 logistic 模型的性能。最佳模型定义为在预测新测试数据的类别时分类错误率最低的模型：

完整 logistic 回归模型的预测准确率：

```

```

## [1] 0.808

```

逐步 logistic 回归模型的预测准确率：

```

```
## [1] 0.795
```

## 23.4 讨论

本章描述了如何在 R 中执行逐步 logistic 回归。在我们的示例中，逐步回归选择了较少的预测变量数量，得到了一个最终模型，其性能与完整模型相似。

因此，逐步选择降低了模型的复杂性而没有损害其准确性。请注意，在其他条件相同的情况下，我们始终应选择更简单的模型，这里是逐步回归返回的最终模型。

另一种用于模型选择的逐步方法替代方案是惩罚回归方法（第 24 章），它对模型拥有过多变量进行惩罚。

## 24 惩罚 Logistic 回归

## 24.1 引言

当你的 logistic 回归模型中有多个变量时，找到一个变量的减少集合以获得最优性能的模型可能是有用的（参见第 19 章）。

**惩罚 logistic 回归** 对 logistic 模型拥有过多变量施加惩罚。这会导致将贡献较小的变量的系数收缩至零。这也称为 **正则化**。

最常用的惩罚回归包括：

* **岭回归**：贡献较小的变量其系数接近于零。然而，所有变量都被纳入模型。这在根据领域知识需要将所有变量纳入模型时很有用。

* **lasso 回归**：一些贡献较小的变量的系数被强制为恰好为零。仅最显著的变量保留在最终模型中。

* **弹性网络回归**：岭回归和 lasso 回归的组合。它将一些系数收缩至零（像岭回归）并将一些系数设为恰好为零（像 lasso 回归）

本章描述如何计算惩罚 logistic 回归，例如 lasso 回归，以自动选择包含最具贡献预测变量的最优模型。

## 24.2 加载所需的 R 包

* `tidyverse` 用于便捷的数据操作和可视化

* `caret` 用于便捷的机器学习工作流

* `glmnet`，用于计算惩罚回归

```

## 24.3 准备数据

数据集：`PimaIndiansDiabetes2` [在 `mlbench` 包中]，在第 21 章中介绍，用于基于多个临床变量预测患糖尿病的概率。

我们将随机将数据拆分为训练集（80% 用于构建预测模型）和测试集（20% 用于评估模型）。请确保设置种子以保证可重复性。

```

## 24.4 计算惩罚 logistic 回归

### 24.4.1 额外的数据准备

R 函数 `model.matrix()` 有助于创建预测变量矩阵，并自动将分类预测变量转换为适当的哑变量，这对于 `glmnet()` 函数是必需的。

```

### 24.4.2 R 函数

我们将使用 R 函数 `glmnet()` [glmnet 包] 来计算惩罚 logistic 回归。

简化格式如下：

```

* `x`：预测变量矩阵

* `y`：响应或结果变量，是一个二元变量。

* `family`：响应类型。对于二元结果变量使用 "binomial"

* `alpha`：弹性网络混合参数。允许的值包括：

  * "1"：用于 lasso 回归

  * "0"：用于岭回归

  * 0 到 1 之间的值（例如 0.3）用于弹性网络回归。

* `lamba`：定义收缩量的数值。应由分析师指定。

在惩罚回归中，你需要指定一个常数 `lambda` 来调整系数收缩的量。数据的最佳 `lambda` 可以定义为使交叉验证预测错误率最小化的 `lambda`。这可以使用函数 `cv.glmnet()` 自动确定。

在下面的 R 代码中，我们将展示如何通过指定选项 `alpha = 1` 来计算 lasso 回归。你也可以尝试使用 `alpha = 0` 的岭回归，看看哪种更适合你的数据。

### 24.4.3 快速入门 R 代码

拟合 lasso 惩罚回归模型：

```

### 24.4.4 计算 lasso 回归

**找到使交叉验证误差最小化的 lambda 的最优值**：

```

![](img/Image00020.jpg)

该图显示了交叉验证误差随 lambda 的对数的变化。左侧的虚线垂直线表明 lambda 的对数的最优值约为 -5，这是使预测误差最小化的值。此 lambda 值将给出最准确的模型。`lambda` 的精确值可以如下查看：

```

```

## [1] 0.00871

```

一般来说，正则化的目的是平衡准确性和简洁性。这意味着，选择预测变量数量最少，同时也能获得良好准确性的模型。为此，函数 `cv.glmnet()` 还会找到使模型最简单但同时仍在最优 `lambda` 值一个标准误差范围内的 `lambda` 值。该值称为 `lambda.1se`。

```

## [1] 0.0674

```

使用 `lambda.min` 作为最佳 lambda，得到以下回归系数：

```

## 9 x 1 sparse Matrix of class "dgCMatrix"

##                     1

## (Intercept) -8.615615

## pregnant     0.035076

## glucose      0.036916

## pressure     .       

## triceps      0.016484

## insulin     -0.000392

## mass         0.030485

## pedigree     0.785506

## age          0.036265

```

从上面的输出中，只有可行的 `triceps` 的系数恰好等于零。

使用 `lambda.1se` 作为最佳 lambda，得到以下回归系数：

```

## 9 x 1 sparse Matrix of class "dgCMatrix"

##                    1

## (Intercept) -4.65750

## pregnant     .      

## glucose      0.02628

## pressure     .      

## triceps      0.00191

## insulin      .      

## mass         .      

## pedigree     .      

## age          0.01734

```

使用 `lambda.1se`，只有 5 个变量具有非零系数。lasso 算法将所有其他变量的系数设为零，从而降低了模型的复杂度。

将 `lambda = lambda.1se` 设置为模型会比使用 `lambda.min` 产生更简单的模型，但该模型的准确性可能比使用 `lambda.min` 获得的模型稍差一些。

在下一节中，我们将使用 `lambda.min` 计算最终模型，然后评估模型在测试数据上的准确性。我们还将讨论使用 `lambda = lambda.1se` 拟合模型所获得的结果。

### 计算最终的 lasso 模型

* 使用 `lambda.min` 计算最终模型：

```

## [1] 0.769

```

* 使用 `lambda.1se` 计算最终模型：

```

## [1] 0.705

```

在下一节中，我们将比较 lasso 回归获得的准确性与使用完整逻辑回归模型（包含所有预测变量）获得的准确性。

#### 24.4.5 计算完整的逻辑模型

```

## [1] 0.808
