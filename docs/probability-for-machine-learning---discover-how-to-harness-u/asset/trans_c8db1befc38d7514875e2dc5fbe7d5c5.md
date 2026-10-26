
或者：

H(13/20, 7/20) − 8/20 × H(7/8, 1/8) + 12/20 × H(6/12, 6/12) (24.5)

或在代码中：

```
...
# calculate the information gain
gain = s_entropy - (8/20 * s1_entropy + 12/20 * s2_entropy)
print('Information Gain: %.3f bits' % gain)
```

清单 24.7：计算信息增益的示例。

将这一切结合起来，完整示例列在下面。

```
# calculate the information gain
from math import log2

# calculate the entropy for the split in the dataset
def entropy(class0, class1):
    return -(class0 * log2(class0) + class1 * log2(class1))

# split of the main dataset
class0 = 13 / 20
class1 = 7 / 20
# calculate entropy before the change
s_entropy = entropy(class0, class1)
print('Dataset Entropy: %.3f bits' % s_entropy)

# split 1 (split via value1)
s1_class0 = 7 / 8
s1_class1 = 1 / 8
# calculate the entropy of the first group
s1_entropy = entropy(s1_class0, s1_class1)
print('Group1 Entropy: %.3f bits' % s1_entropy)

# split 2 (split via value2)
s2_class0 = 6 / 12
s2_class1 = 6 / 12
# calculate the entropy of the second group
s2_entropy = entropy(s2_class0, s2_class1)
print('Group2 Entropy: %.3f bits' % s2_entropy)

# calculate the information gain
gain = s_entropy - (8/20 * s1_entropy + 12/20 * s2_entropy)
print('Information Gain: %.3f bits' % gain)
```

清单 24.8：计算数据集两次分割的信息增益的示例。

首先，数据集的熵计算为略低于 1 位。然后，第一组和第二组的熵分别计算约为 0.5 和 1 位。最后，变量的信息增益计算为 0.117 位。也就是说，通过所选变量对数据集进行分割所带来的增益为 0.117 位。

```
Dataset Entropy: 0.934 bits
Group1 Entropy: 0.544 bits
Group2 Entropy: 1.000 bits
```

```
Information Gain: 0.117 bits
```

清单 24.9：计算数据集两次分割的信息增益的示例输出。

## 24.4 机器学习中信息增益的示例

在机器学习中，信息增益最流行的用途是在决策树中。一个例子是迭代二分器 3 算法，简称 ID3，用于构建决策树。

信息增益正是 ID3 在生长树时在每一步选择最佳属性时使用的度量。

> — 第 58 页，Machine Learning，1997。

信息增益是针对数据集中每个变量计算的。具有最大信息增益的变量被选中来分割数据集。通常，更大的增益表示更小的熵或更少的惊讶。

请注意，最小化熵等同于最大化信息增益 ...

> — 第 547 页，Machine Learning: A Probabilistic Perspective，2012。

该过程随后在每个创建的组上重复，排除已选中的变量。这在达到决策树的期望深度或无法再进行分割时停止。

选择新属性并划分训练示例的过程现在对每个非终端后代节点重复，这次仅使用与该节点关联的训练示例。已在树中更高位置合并的属性被排除，因此任何给定属性在树中的任何路径上最多只能出现一次。

> — 第 60 页，Machine Learning，1997。

信息增益可以用作大多数现代决策树实现中的分割标准，例如 scikit-learn Python 机器学习库中用于分类的 Classification and Regression Tree（CART）算法的实现中的 DecisionTreeClassifier 类。这可以通过在配置模型时将 criterion 参数设置为‘entropy’来实现；例如：

```
# example of a decision tree trained with information gain
from sklearn.tree import DecisionTreeClassifier
model = DecisionTreeClassifier(criterion='entropy')
...
```

清单 24.10：定义 DecisionTreeClassifier 分类器以使用信息增益的示例。

这可以正式表述如下：

$$I(X;Y) = KL(p(X,Y)\|p(X) \times p(Y)) \tag{24.7}$$

互信息始终大于或等于零，其中值越大，两变量之间的关系越大。如果计算结果为零，则变量是独立的。互信息通常用作相关系数的一般形式，例如随机变量之间依赖性的度量。它也用作某些机器学习算法中的一个方面。一个常见的例子是独立成分分析，简称 ICA，它提供了数据集的统计独立成分的投影。

## 24.6 信息增益和互信息是如何相关的？

互信息和信息增益是同一事物，尽管度量的上下文或用法通常导致不同的名称。例如：

- 对数据集的变换的影响（*决策树*）：信息增益。
- 变量之间的依赖关系（*特征选择*）：互信息。

注意互信息计算方式与信息增益计算方式的相似性；它们是等价的：

$$I(X;Y) = H(X) - H(X|Y) \tag{24.8}$$

和

$$IG(S,a) = H(S) - H(S|a) \tag{24.9}$$

因此，互信息有时被用作信息增益的同义词。技术上，如果应用于相同的数据，它们计算相同的量。我们可以将两者之间的关系理解为联合和边缘概率分布的差异越大（互信息），信息增益（信息增益）就越大。

## 24.7 进一步阅读

如果您想深入了解，本节提供了更多资源。

### 24.7.1 书籍

- *信息论、推断与学习算法*，2003。
  https://amzn.to/2KfDDF7
- *机器学习：概率视角*，2012。
  https://amzn.to/2xKSTCP
- *模式识别与机器学习*，2006。
  https://amzn.to/2JwHETI
- *机器学习*，1997。
  https://amzn.to/2jWd51p
- *数据挖掘：实用机器学习工具与技术*，第 4 版，2016。
  https://amzn.to/2lnW5S7

### 24.7.2 API

- `scipy.stats.entropy` API。
  https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.entropy.html

### 24.7.3 文章

- 熵（信息论），维基百科。
  https://en.wikipedia.org/wiki/Entropy_(information_theory)
- 决策树中的信息增益，维基百科。
  https://en.wikipedia.org/wiki/Information_gain_in_decision_trees
- ID3 算法，维基百科。
  https://en.wikipedia.org/wiki/ID3_algorithm
- 信息增益比，维基百科。
  https://en.wikipedia.org/wiki/Information_gain_ratio
- 互信息，维基百科。
  https://en.wikipedia.org/wiki/Mutual_information

## 24.8 摘要

在本教程中，您了解了机器学习中的信息增益和互信息。具体来说，您学习了：

- 信息增益是通过转换数据集而降低的熵或惊讶度，并且通常用于训练决策树。
- 信息增益是通过比较转换前后数据集的熵来计算的。
- 互信息计算两个变量之间的统计依赖性，并且是信息增益在应用于变量选择时所使用的名称。

### 24.8.1 下一步

这是本部分的最后一个教程。在下一部分中，您将发现在使用分类预测建模问题时有用的概率工具。

## 第 25 章

## 如何开发和评估朴素分类器策略

朴素分类器是一种简单的分类模型，假设关于问题的信息很少或没有，其性能提供了所有其他在数据集上评估的模型可以比较的基线。朴素分类器可以使用不同的策略，并且有些策略比其他策略更好，这取决于数据集和性能度量的选择。最常见的性能度量是分类准确率，常见的朴素分类策略包括随机猜测类别标签、从训练数据集中随机选择标签以及使用多数类标签。开发一个小的概率框架来计算给定朴素分类策略的预期性能并进行实验以确认理论预期是有用的。这些练习提供了对朴素分类算法一般行为的直觉，以及为分类任务建立性能基线的重要性。在本教程中，您将了解如何为机器学习开发和评估朴素分类策略。完成本教程后，您将知道：

- 朴素分类模型的性能提供了所有其他模型可以被认为是有技能还是没有技能的基线。
- 多数类分类器比其他朴素分类模型（如随机猜测和预测随机选择的观察类标签）具有更好的准确性。
- 朴素分类策略可以通过 scikit-learn 库中的 `DummyClassifier` 类用于预测建模项目。

让我们开始吧。

## 25.1 教程概述

本教程分为五个部分；它们是：

- 1. 朴素分类器
- 2. 预测随机猜测

