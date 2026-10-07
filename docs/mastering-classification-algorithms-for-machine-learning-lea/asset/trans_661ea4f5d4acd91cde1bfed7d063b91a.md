
## BaggingClassifier

在 sklearn 中，**BaggingClassifier** 类用于实现分类的 Bagging 集成模型。表 6.1 列出了 **BaggingClassifier** 类的关键参数：

| 参数 | 解释 |
| --- | --- |
| estimator | Bagging Classifier 类使用的估计器。默认情况下，估计器是决策树分类（DecisionTreeClassifier）。此参数需要作为估计器类的一个实例提供。 |
| n_estimators | 要创建的估计器实例的数量。这意味着 Bagging Classifier 将使用估计器类创建数量与 n_estimators 值相等的模型，并从提供的数据集中创建 n_estimators 数量的数据集。在 Scikit-Learn 的某些版本中，该参数可能以 `base_estimator` 的形式存在。 |
| bootstrap | 这是一个布尔值参数，取值为 True 或 False。如果 `bootstrap` 参数的值设置为 True，则进行有放回抽样。如果 `bootstrap` 参数的值设置为 False，则进行不放回抽样。 |
| max_samples | 为每个估计器实例需要提供从原始数据集中提取的最大数据点数。 |
| oob_score | 这是一个布尔值参数，取值为 True 或 False。该参数仅在 `bootstrap` 参数设置为 True 时有效。当其设置为 True 时，将使用袋外（out-of-bag）数据点来检查泛化误差。 |

表 6.1：BaggingClassifier 的参数

在下面的代码中，我们看到如何使用 Scikit-Learn 包中的 BaggingClassifier：

```python
from sklearn.ensemble import BaggingClassifier
```

```python
from sklearn.tree import DecisionTreeClassifier
```

```python
baggingClf = BaggingClassifier(estimator=DecisionTreeClassifier(), n_estimators = 1000, bootstrap=True, max_samples=500, oob_score=True)
```

## StackingClassifier

在 sklearn.ensemble 中，**StackingClassifier** 类用于实现分类的 Stacking 集成模型。StackingClassifier 类有两个关键参数。第一个关键参数是 **estimators**，它接收一个不同分类器的列表用于构建基模型。第二个关键参数是 **final_estimator**，它接收用于构建元模型的类。

**StackingClassifier** 的另一个重要参数是 passthrough。它接收一个布尔值（即，我们将此参数设置为 True 或 False）。当 `passthrough` 设置为 False 时，**StackingClassifier** 使用基模型的预测结果作为构建元模型的输入。当 `passthrough` 设置为 True 时，**StackingClassifier** 将使用基模型的预测结果和原始数据集来构建元模型，如下代码所示：

```python
from sklearn.ensemble import StackingClassifier
...
```

```python
from sklearn.naive_bayes import MultinomialNB
from sklearn.neighbors import KNeighborsClassifier
from sklearn.tree import DecisionTreeClassifier
from sklearn.linear_model import LogisticRegression
```

```python
...
nbCls = MultinomialNB()
knnCls = KNeighborsClassifier()
dtCls = DecisionTreeClassifier()
lrCls = LogisticRegression()
```

```python
...
stackingClf = StackingClassifier(estimators=[('nb', nbCls), ('knn', knnCls), ('dt', dtCls)], final_estimator=lrCls)
...
```

## 使用 Bagging 算法构建语音情感分析模型

情感分析在许多行业中被广泛使用。提供在线服务的公司使用情感分析来分析客户反馈。在临床调查中，它用于预测患者的状态。人力资源部门将其用于离职预测等应用。在保险行业，情感分析有更多其他用例。

情感分析通常在文本数据上进行。这是自然语言处理（NLP）的一个领域。该领域通过分析不同的单词来确定情感。我们将对语音进行情感分析，在语音中，音高、语调、语速、音量等方面被分析以确定表达的情感。

使用机器学习进行情感分析的领域仍处于起步阶段，一些可靠的数据集用于构建模型。我们可以通过提供更高质量的数据来改进模型。

## 关于数据集

正如本章所述，用于情感分析的数据集从 Kaggle 获取。数据集的第一个来源是多伦多大学（University of Toronto），第二个来源是里森音视频数据库（Ryerson Audio-Visual Database）。

## TESS 数据集

TESS 数据集包含 2880 个文件，每个文件都包含一段录音。200 个目标词由两位女演员在“Say the word ______”的短语中读出，并录制了七种不同的情感（愤怒、厌恶、恐惧、快乐、惊讶、悲伤和中性）。两位女演员的英语均为母语，拥有大学学历，并接受过音乐训练。听学测试显示两者的阈值都在正常范围内。

- 1 https://borealisdata.com/dataset.xhtml?persistentid=do:10.5683/SP2/E82MF
- 2 https://zenodo.org/record/1188976#Y_RMYuxBzA1

## Ravdess 数据集

Ravdess 数据集包含 2880 个文件，每个文件都包含一段录音。200 个目标词由两位女演员在“Say the word ______”的短语中读出，并录制了七种不同的情感（愤怒、厌恶、恐惧、快乐、惊讶、悲伤和中性）。两位女演员的英语均为母语，拥有大学学历，并接受过音乐训练。听学测试显示两者的阈值都在正常范围内。
