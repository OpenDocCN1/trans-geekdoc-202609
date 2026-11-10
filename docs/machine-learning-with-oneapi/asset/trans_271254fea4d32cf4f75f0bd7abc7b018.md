
# 使用 oneAPI 实现 KNN

是时候使用 `oneAPI` 实现 `KNN` 了。读者将获得逐步的实现说明，结果将在最后讨论。

### 第 1 步
进行必要的导入非常重要。代码已在 [https://github.com/shriramkv/MachineLearningwithoneAPI](https://github.com) 中提供以供快速参考。

![](images/inline6.6.jpg)

### 第 2 步
我们加载 `connect-4` 游戏数据集。我们根据给定数据集中进行的移动预测其中一名玩家的胜/负/平结果。我们执行多个预处理步骤并应用 `onehot` 编码。

![](images/inline6.7.jpg)

### 第 3 步
我们将比较标准 `sklearn` 与 Intel 优化的 `sklearn` 在 `KNN` 实现中的性能。因此，如代码下方所示，采用了 `patch` 和 `unpatch` 方法。

![](images/inline6.8.jpg)

### 第 4 步
下方将引入 Intel 优化的 `sklearn`。生成了报告，可用作比较标准 `sklearn` 和 Intel 优化的 `sklearn` 的指标。可以清楚地看到 `KNN` 被引入其中。

![](images/inline6.9.jpg)

### 第 5 步
下面的代码片段有助于理解使用标准 `sklearn` 的性能指标。

![](images/inline6.10.jpg)

可以看到 `scikit-learn` 的 Intel 扩展已明确启用，并在执行期间通过一条消息可见。经过时间也一并给出，同时还有 `precision`、`recall`、`F1 score` 等，均可与标准 `scikit-learn` 结果进行比较。

![](images/inline6.11.jpg)

下面的截图展示了 `scikit-learn` 标准版本的结果。可以看到，经过时间要高得多，为 0.78 秒，而使用 Intel 优化的 `scikit-learn` 时我们得到的为 0.06 秒。

![](images/inline6.12.jpg)

使用 Intel 优化的 `scikit-learn` 时在执行时间方面可实现的百分比提升如下所示，截图中显示提升了 233%，这一结果无疑为开发者所赞赏。

![](images/inline6.13.jpg)

## 6.6 损失函数和代价函数、偏差与方差权衡、正则化、特征选择和超参数调优

`Linear regression` 试图预测目标变量，最小化独立输入变量上的 `Error`。这有助于了解模型在对未见过的测试输入进行准确预测方面的准确性。`Regularization` 是用于防止生成模型过拟合的方法。让我们通过合适的例子更深入地了解模型的欠拟合和过拟合。为了详细了解它们，有必要涉及某些术语，如 `loss` 和 `cost` 函数。

由于 `Linear regression` 是一种专注于减少误差的有监督机器学习模型，至少有必要了解 `loss function`、`cost function` 和 `gradient descent`。

`Loss function` 是理解给定的 `Linear regression` 机器学习模型对特定训练数据集拟合程度的最简单方法。这基本上计算预测 `Error`。假设我们考虑值的真实值，如果预测值与真实值之间存在较大差异，则可以说 `loss function` 较高。`Loss functions` 通常用于 `hyperparameter` 调优或优化。

`Cost Function` 是训练数据集中所有观测值的综合 `loss function`。就 `Linear regression` 而言，`loss function` 的示例可以是最小平方误差，而 `cost function` 是均方误差 (`MSE`)。

那么，让我们了解机器学习中“`Error`”到底是什么。请参阅下文中的 [图 6.23](#c6.xhtml#f6.23)。这描述了 `Error`，实际上是训练和验证 `Error` 用 `Bias` 和 `Variance` 表示。

![图 6.23 错误与模型复杂度。](images/fig6.23.jpg)

[**图 6.23**](#c6.xhtml#re_f6.23) 错误与模型复杂度。

`Error` 只是衡量机器学习算法对未见数据集进行预测的程度的指标。主要地，误差分为可减少误差和不可减少误差，如 [图 6.24](#c6.xhtml#f6.24) 所示。

![图 6.24 机器学习中的误差。](images/fig6.24.jpg)

[**图 6.24**](#c6.xhtml#re_f6.24) 机器学习中的误差。

`Bias and Variance` 基本上是机器学习中的可减少误差。这是什么意思？这仅仅意味着你可以减少这些误差并提高模型的准确性。相反，不可减少误差是模型中默认存在的误差。

什么是偏差？`Bias` 是预测值与模型预期预测的实际值之间的差异。这显示了模型无法理解各个数据点之间相关性的能力。`Bias` 可以分为两种类型：低 `Bias` 和高 `Bias`。

低 `Bias` 是指模型对目标函数包含较少假设的情况。例如，像 `Linear regression` 算法这样的算法简单且学习速度快，会具有较高的 `Bias`。这意味着具有较高 `Bias` 的模型将无法匹配训练数据集。换句话说，如果 `Bias` 较高，模型会欠拟合；如果 `Bias` 较低，模型会过拟合。

考虑我们需要根据一个人的教育资格预测其薪水的例子。假设我们通过当面询问 100 人进行了经验分析，如果我们考虑绘制薪水和年龄时所取的数据，这是一个简单的任务。由于欠拟合或高 `Bias`，模型可能无法带来准确的结果。

例如，如果我们考虑许多独立变量，如年龄、性别、教育水平、职业等，即使模型变得复杂并试图泛化以在训练数据集上做出良好预测，它在测试数据集上也无法做出良好预测。这不过是过拟合或高 `Variance`，如 [图 6.25](#c6.xhtml#f6.25) 所示。

![图 6.25 数据点的过拟合。](images/fig6.25.jpg)

[**图 6.25**](#c6.xhtml#re_f6.25) 数据点的过拟合。

就 `Linear regression` 而言，我们可以有各种独立变量，如年龄、教育水平、性别、职业等，如前所述。所有这些独立变量都可能采用不同的值（或权重）以各种排列组合来预测薪水。这就是 `hyperparameter` 优化或调优或 `hyperparameter` 权重发挥作用的地方。对独立变量进行的权重调整称为 `Regularization`，目的是使模型对测试数据集做出最佳预测。

那么，`Regularization` 到底是什么？

通过 `Regularization`，你让模型选择最佳特征，以帮助模型在测试数据集中做出最佳预测。简单来说，我们可以说 `Regularization` 有助于模型的特征选择。用 `Bias` 和 `Variance` 来表述，`Regularization` 有助于在高 `Bias` 和高 `Variance` 之间找到权衡，如 [图 6.26](#c6.xhtml#f6.26) 所示。这不过是机器学习问题中的 `Bias`–`Variance` 权衡场景。这意味着我们希望将训练数据集上的准确率从例如 100% 降低到 80%，但仍能在测试或未见数据集上实现例如 50% 到 80% 的准确率。

![图 6.26 偏差与方差权衡。](images/fig6.26.jpg)

[**图 6.26**](#c6.xhtml#re_f6.26) 偏差与方差权衡。
