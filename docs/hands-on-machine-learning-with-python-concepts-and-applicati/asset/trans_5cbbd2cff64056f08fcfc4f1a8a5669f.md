

# 数据预处理与模型训练

## Fare 特征分箱与序数化

```python
train_df['FareBand'] = pd.qcut(train_df['Fare'], 4)
```

```python
train_df[['FareBand', 'Survived']].groupby(['FareBand'], as_index=False).mean().sort_values(by='FareBand', ascending=True)
```

![](images/00047.jpeg)

然后我们将其转换为序数值（类似于我们在 AgeBand 中所做的操作）。

```python
for dataset in combine:
    dataset.loc[dataset['Fare'] <= 7.91, 'Fare'] = 0
    dataset.loc[(dataset['Fare'] > 7.91) & (dataset['Fare'] <= 14.454), 'Fare'] = 1
    dataset.loc[(dataset['Fare'] > 14.454) & (dataset['Fare'] <= 31), 'Fare'] = 2
    dataset.loc[dataset['Fare'] > 31, 'Fare'] = 3
    dataset['Fare'] = dataset['Fare'].astype(int)
```

```python
train_df = train_df.drop(['FareBand'], axis=1)
combine = [train_df, test_df]
train_df.head(10)
```

![](images/00048.jpeg)

这是测试集。让我们也看一眼测试数据集：

```python
test_df.head(10)
```

![](images/00049.jpeg)

呼！我们终于完成了数据分析和机器学习中严谨的部分。请注意，我们还没有进行任何机器学习。还要注意，在几乎每一步中，我们都查看了数据集，观察数值是如何转换的。这是为了进行合理性检查，确保我们做的是正确的事情。

## 模型选择与训练

现在到了最令人期待的部分。我们现在准备好训练模型了。请始终牢记，我们的目标是从数据中学习，然后基于之前的学习对未见过的数据进行预测。但首先有几十种预测算法可供选择。让我们尝试以下 6 种算法，因为它们在分类任务中很流行（我们稍后会详细讨论它们）：

1.  逻辑回归
2.  K 近邻算法或 KNN
3.  支持向量机 (SVM)
4.  朴素贝叶斯分类器
5.  决策树
6.  随机森林

首先，我们在训练集中定义自变量 (`X_train`) 和目标变量 (`Y_train`)（我们在测试集中同样这么做）：

```python
X_train = train_df.drop("Survived", axis=1)
Y_train = train_df["Survived"]
X_test  = test_df.drop("PassengerId", axis=1).copy()
X_train.shape, Y_train.shape, X_test.shape
```

```
((891, 8), (891,), (418, 8))
```

### 逻辑回归

然后让我们使用第一个选项（逻辑回归）来训练模型：

```python
from sklearn.linear_model import LogisticRegression

logreg = LogisticRegression()
logreg.fit(X_train, Y_train)
Y_pred = logreg.predict(X_test)
acc_log = round(logreg.score(X_train, Y_train) * 100, 2)
acc_log
```

```
80.36
```

80.36% 是逻辑回归在预测乘客是否生还时的准确率。

### 随机森林分类器

让我们尝试另一个模型（随机森林分类器）：

```python
from sklearn.ensemble import RandomForestClassifier

random_forest = RandomForestClassifier(n_estimators=100)
random_forest.fit(X_train, Y_train)
Y_pred = random_forest.predict(X_test)
random_forest.score(X_train, Y_train)
acc_random_forest = round(random_forest.score(X_train, Y_train) * 100, 2)
acc_random_forest
```

```
86.76
```

这是使用随机森林时的准确率水平。请注意，它明显高于我们从逻辑回归中获得的结果。

这是很自然的，因为不同的算法具有不同的机制，会产生不同的准确率水平。一个好的方法是选择准确率最高的那个，或者使用所有合适的算法并对结果取平均值。

## 启示与可能性

这大致就是机器学习在现实生活中的工作流程。我们获取数据，执行数据操作和转换，最后应用几行代码（实际的机器学习部分），然后就可以进行预测了。

前面的例子（泰坦尼克号生还预测）是一个极好的例子，因为我们已经了解了典型机器学习项目的不同方面。好吧，请注意，其中大部分远非机器学习，而更多是关于做假设和操作数据。

这是一个极好且简单的例子。但如果我们将这些概念同样应用于其他问题，潜力将是巨大的。事实上，许多现实世界的商业和科学挑战都可以用二元方式表示（生还或未生还）。

- 一个人会购买某个产品吗（购买或未购买）？
- 肿瘤是良性还是恶性（0 代表良性，1 代表恶性）？
- 邮件是垃圾邮件吗？
- 某人会偿还她的贷款吗（基于其他客户的记录和还款倾向）？
- 基于 12 个变量，是否应该将某人送入重症监护室？

这只是开始，这只是机器学习的一个子集。这就是为什么许多专家说我们才刚刚触及皮毛。随着计算能力的增强和海量数据集的出现，我们将能够深入挖掘，并将机器学习应用于几乎所有领域。

# 通用工作流程

无论领域或主题的复杂程度如何，总有一些共同的原则贯穿始终。机器学习也是类似的情况，其通用原则保持不变。

首先，我们必须获得具有足够数值的高质量数据。如果数据集很混乱，我们将花费额外的时间进行清理和整理。第二步是查看数据本身并将其可视化。这使我们能快速从数据中获得洞察。事实上，即使不使用机器学习，仅通过可视化和查看数据摘要（均值、中位数、众数、标准差等），我们也能快速获得洞察。

第三步可能涉及大量的数据转换和操作，就像我们之前所做的那样。我们可能需要丢弃一些无关特征。我们也可以为了简单起见将特征合并为一个。我们还可以创建新特征供模型算法使用。

而在最令人期待的部分，我们现在选择模型和算法，开始从数据中学习。有了 `scikit-learn`，我们已经有了预建的代码，所以不必从头编写。这就是为什么我们只花了 1% 的时间在实际的机器学习上。但如果我们从头写所有东西，将会花费我们非常长的时间。

你可以随时深入研究模型和算法是如何工作的。幕后原理通常因数学而复杂。但如果你仍选择学习所有这些，你将比其他人更有优势。

无论如何，让我们先专注于基础。毕竟，“第一性原理”永远适用。让我们开始吧。

# 通用机器学习概念

在上一章中，我们讨论了一个机器学习如何应用于真实数据集的例子。这是为了快速展示和说明机器学习的威力。

但在深入之前，让我们先探索基础知识。这样你将拥有一个心智框架，让各个碎片拼凑在一起。这能让你更扎实地学习，并牢固掌握机器学习的真谛。工具和技术将永远在变。但有了正确的基础，你将始终能随之调整。

那么，让我们从机器学习的主要“类别”开始。数量虽有争议，但这些是你在阅读其他关于机器学习和数据科学资源时最常遇到的最重要内容：监督学习、无监督学习和深度学习。

## 什么是机器学习

