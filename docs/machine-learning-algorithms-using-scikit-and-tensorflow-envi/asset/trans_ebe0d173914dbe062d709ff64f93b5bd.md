

### 图 2. 输出

![](img/20813928ec98c7f6fbdbab0d52bde2f1_30_0.png)

按定义，如果 C 是混淆矩阵，则 $C_{ij}$ 等于已知属于组 i 且预测属于组 j 的观测值的数量。

### 图 3. 混淆矩阵

| 预测值 \ 实际值 | 正类 (1) | 负类 (0) |
| :--- | :--- | :--- |
| 正类 (1) | 真正例 (TP) | 假正例 (FP) |
| 负类 (0) | 假负例 (FN) | 真负例 (TN) |

因此，在二分类中，真负例的计数为 C_{0,0}，假负例的计数为 C_{1,0}，真正例的计数为 C_{1,1}，假正例的计数为 C_{0,1}。2x2 混淆矩阵的图示如下，如图 3 所示。

- 真正例 (TP)：模型准确预测为正类的结果。
- 真负例 (TN)：模型正确预测为负类的结果。
- 假正例 (FPs)：模型预测为正类但实际上为负类的结果。
- 假负例 (FN)：模型错误预测为负类但实际上属于正类的结果。

要衡量分类模型的性能，需要找出模型的准确率、召回率、精确率、特异性和 F1-Score 值。

示例（二分类）：

```python
from sklearn.metrics import confusion_matrix, ConfusionMatrixDisplay
import matplotlib.pyplot as plt
y_actual = [1, 0, 1, 0, 0, 1]
y_predicted = [1, 1, 1, 0, 1, 1]
conf_mat=confusion_matrix(y_actual, y_predicted)
print(conf_mat)
disp=ConfusionMatrixDisplay(confusion_matrix=conf_mat, display_labels=[0,1])
disp.plot()
plt.show()
```

输出：

```
[[1 2]
 [0 3]]
```

示例（多类分类）：

```python
from sklearn.metrics import confusion_matrix, ConfusionMatrixDisplay
import matplotlib.pyplot as plt
y_actual = [2, 0, 2, 2, 0, 1]
y_predicted = [0, 0, 2, 2, 0, 2]
conf_mat = confusion_matrix(y_actual, y_predicted)
print(conf_mat)
disp = ConfusionMatrixDisplay(confusion_matrix= conf_mat, display_labels=[0,1,2])
disp.plot()
plt.show()
```

输出：

### 图 4. 输出

![](img/20813928ec98c7f6fbdbab0d52bde2f1_32_0.png)

### 图 5. 输出

![](img/20813928ec98c7f6fbdbab0d52bde2f1_32_1.png)

```
[[2 0 0]
 [0 0 1]
 [1 0 2]]
```

## 6.3 准确率

这仅仅等于模型正确分类的预测所占的比例。

准确率 = \frac{正确预测数}{预测总数} = \frac{TP + TN}{TP + TN + FP + FN}

示例：

```python
# Accuracy
from sklearn.metrics import accuracy_score
y_actual = [0, 1, 3, 2, 2]
y_predicted = [0, 3, 1, 2, 3]
print(accuracy_score(y_actual, y_predicted))
```

输出：

0.4

## 6.4 精确率

精确率是通过在所有被预测为正类的样本中找出实际为正类的样本数量来计算的。它也称为阳性预测值。实际上，它是所有正类预测中真正例的百分比。

精确率 = \frac{TP}{TP + FP}

示例：

```python
# Precision
from sklearn.metrics import precision_score
y_actual = [0, 1, 3, 2, 2]
y_predicted = [0, 3, 1, 2, 3]
print(precision_score(y_actual, y_predicted, average=None))
```

输出：

[1. 0. 1. 0.]

## 6.5 召回率

召回率（也称为灵敏度、命中率或真正率 (TPR)）是通过从所有给定的正类样本中找出被正确预测的样本数量来计算的。它回答了问题：“实际正类中有多少比例被正确识别了？”

$$召回率 = \frac{TP}{TP + FN}$$

示例：

```python
# Recall
from sklearn.metrics import recall_score
y_actual = [0, 1, 3, 2, 2]
y_predicted = [0, 3, 1, 2, 3]
print(recall_score(y_actual, y_predicted, average=None))
```

输出：

[1. 0. 0.5 0. ]

## 6.6 特异性

特异性衡量被正确识别为负类的实际负类所占的比例。它也称为真负率 (TNR)。它是召回率的对立指标。

$$特异性 = \frac{TN}{TN + FP}$$

## 6.7 F1 分数

F1 分数是精确率和召回率的调和平均数。其最高分为 1，表示精确率和召回率完美。

$$F1 分数 = \frac{2*(精确率*召回率)}{精确率 + 召回率}$$

示例：

```python
# f1_score
from sklearn.metrics import f1_score
y_actual = [0, 1, 3, 2, 2]
y_predicted = [0, 3, 1, 2, 3]
print(f1_score(y_actual, y_predicted, average='macro'))
print(f1_score(y_actual, y_predicted, average='micro'))
print(f1_score(y_actual, y_predicted, average='weighted'))
```

输出：

0.41666666666666663
0.4000000000000001
0.4666666666666666

## 参考文献

Dada, E. G., Bassi, J. S., Chiroma, H., Shafi'i, M. A., Adetunmbi, A. O., & Ajibuwa, O. E. (2019). 电子邮件垃圾邮件过滤的机器学习：综述、方法和开放研究问题. Heliyon, 5(6). doi:10.1016/j.heliyon.2019.e01802

Mukhamediev, R., Yakunin, K., Iskakov, S., Sainova, S., Abdilmanova, A., & Kuchin, Y. (2015). 分类算法的比较分析. doi:10.1109/ICAICT.2015.7338525

Pedregosa, Varoquaux, Gramfort, Michel, Thirion, & Grisel. (2011). Scikit-learn：Python 中的机器学习. 机器学习研究杂志, 12(Oct), 2825–2830.

Vujovic, Z. (2021). 分类模型评估指标. 国际先进计算机科学与应用杂志, 12(6), 599–606. doi:10.14569/IJACSA.2021.0120670

## 第 2 章

### 面向下一代系统的 TensorFlow 与 SciKit 机器学习算法

Aryan Chopra
印度维洛尔技术学院

Aditya Modi
印度维洛尔技术学院

Brijendra Singh
https://orcid.org/0000-0003-2608-3388
印度维洛尔技术学院

### 摘要

机器学习在医疗保健、银行、金融和营销等所有主要领域都发挥着至关重要的作用。有必要更好地理解 ML 算法的作用和工作原理。每当我们尝试浏览互联网以获取所需信息时，Google 也会使用学习算法对网页进行排名。理解这些算法的平台和工作原理对研究人员至关重要。在本章中，作者介绍了机器学习基础知识及这些算法的工作原理，并附有合适的示例。他们还强调了 TensorFlow 和 SciKit 等主要机器学习库在开发和部署大型应用中的重要性。最后，介绍了 ML 应用案例研究以更好地理解该概念。ML 应用的未来前景也进行了详细描述。

### 1. 引言

自石器时代以来，人类就使用不同类型的工具来让生活更轻松。人类大脑的巧妙性反过来使许多不同的机器成为可能。机器学习就是其中一项发明。根据 Arthur Samuel 的说法，机器学习被定义为“赋予计算机在无需明确编程的情况下学习能力的研究领域”（Mahesh, 2020）。图 1 展示了不同类型机器学习（ML）算法的快速概览。

### 图 1. ML 算法的流行度上升 (Sarker, 2021)

![](img/20813928ec98c7f6fbdbab0d52bde2f1_37_0.png)

机器学习已成为人工智能（AI）的一个关键分支，专注于数据操作和建模，以进行预测和分析复杂模式。本文献综述旨在提供机器学习基础知识的概述，探讨各种机器学习算法，强调 TensorFlow 和 SciKit 等流行机器学习库的重要性，并通过案例研究突出实际应用。

> “各种 ML 算法（受监督、无监督、半监督和强化学习）在 0（最小值）到 100（最大值）范围内随时间变化的全球流行度评分，其中 x 轴表示时间戳信息，y 轴表示相应的评分”（Sarker, 2021）。

机器学习是人工智能的一个分支，涉及数据操作和建模，从而帮助从数据中进行预测和绘制图表以共同分析。通过使用统计方法，算法可以进行从一周内股票价格到未来十年全球变暖增加水平等各种预测。随着技术的进步，机器学习在我们生活的方方面面都很普遍，大公司经常使用它来帮助进行消费者行为分析，然后向他们推荐可能购买的产品和服务，从而增加收入。利用数据操作来构建有助于预测下一组数据的模型，这被称为机器学习算法。

现在我们将讨论各种学习方法：

### 1.1 受监督学习

受监督学习是在教师的监督下进行的。对于给定的一组输入，我们知道输出，或者说类别级别是已知的。我们可以基于受监督数据训练模型。当我们将新数据呈现给模型时，它将预测我们未知的类别级别。分类是受监督学习技术之一，具有大量现实世界的应用。例如，在医学领域，我们可以分类癌症是良性还是恶性。图 2 描绘了受监督机器学习算法的工作原理。受监督学习的目标是构建一个预测模型，能够准确预测新的、未见的输入数据的输出。

