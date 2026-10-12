

# K近邻算法实现

```python
# loop over all observations
for i in range(n_predictions):
    # calculation of single prediction
    predictions[i] = self.pred_from_neighbors(self.X, self.y, X_test[i, :], self.n_neighbors)
return(predictions)
```

上述类的工作流程是：在测试阶段，输入一个测试样本（实例），并计算其到整个训练集中每个样本的欧氏距离。根据要考虑的最近邻居数量（`k`值），这些邻居的标签参与投票，以确定测试样本的类别。

## 生成响应

为了生成响应或创建预测，我们首先必须初始化自定义分类器。`k` 的值不能超过数据集中的样本数量。这是意料之中的，因为我们无法与训练集中可用数量以上的邻居进行比较。

```python
# instantiate learning model (k = 3)
my_classifier = MyKNeighborsClassifier(n_neighbors=3)
```

接下来，我们可以在数据上训练模型。请记住，在 K-NN 中实际上不发生训练过程。

```python
# fitting the model
my_classifier.fit(X_train, y_train)
```

## 评估准确率

为了评估模型的准确率，我们在模型未见过的示例（如测试集中的样本）上测试其性能。

```python
# predicting the test set results
my_y_pred = my_classifier.predict(X_test)
```

然后我们将预测类别与真实标签进行核对，并使用 Scikit-Learn 的准确率模块来计算分类器的准确率。

```python
from sklearn.metrics import confusion_matrix, accuracy_score

accuracy = accuracy_score(y_test, my_y_pred) * 100
print('Accuracy: ' + str(round(accuracy, 2)) + ' %.')
```

![](images/00080.jpeg)

我们的模型达到了 97.8% 的准确率，对于这样一个简单而优雅的模型来说，这令人印象深刻。

## 维度灾难

当输入空间的维度较小时（如本例所示），K 近邻算法表现最佳。我们有四个预测变量（花萼长度、花萼宽度、花瓣长度、花瓣宽度）输入算法。K-NN 在高维输入空间（如图像处理中遇到的空间）中表现吃力。这是因为距离度量所表达的相似性度量非常有限，无法正确建模这种高维空间。通常，机器学习算法试图降低维度，以便我们对低维空间的直觉仍然适用。当维度数量增加时，算法的准确率或性能通常会下降。这被称为**维度灾难**。

# 朴素贝叶斯

## 朴素贝叶斯的应用

朴素贝叶斯算法是一种基于贝叶斯定理的**急切学习算法**，其假设是：给定类别标签的情况下，所有特征相互独立。朴素贝叶斯算法非常适合文本分类，因为其测试阶段的预测速度很快，因此可以部署在大型数据集上进行推理。

朴素贝叶斯通常用于需要实时预测的应用场景，例如信用卡交易的欺诈检测。在这些应用中，需要一个能够近乎瞬间完成分类的分类器。朴素贝叶斯还广泛用于文本分类、垃圾邮件过滤和情感分析。在垃圾邮件过滤中，邮件或短信的单词作为模型的输入特征，并假设每个单词与其他单词相互独立。当这种独立性假设成立时，朴素贝叶斯通常能产生良好的结果，加上其推理时间短，有时比更复杂的分类器更受青睐。

朴素贝叶斯算法广泛应用的另一个领域是**多类分类**。在该领域，给定输入特征可以预测多个类别或类别，并为预测类别分配概率。

## 如何在 Python 中使用朴素贝叶斯构建基础模型

在我们的实战示例中，我们将使用 Python 构建一个朴素贝叶斯模型来解决垃圾短信分类问题。我们将使用 SMS 垃圾邮件收集数据集，这是一个包含 5,574 条英语短信的集合，并已标注类别。共有两个类别——ham（正常短信）和 spam（垃圾短信）。该数据集可从以下 URL 下载（`https://www.kaggle.com/uciml/sms-spam-collection-dataset/downloads/spam.csv/1`）。

我们将使用 Scikit-Learn 机器学习库中的多项式朴素贝叶斯分类器。像往常一样，我们首先导入将要使用的库。

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# comment the magic command below if not running in Jupyter notebook
%matplotlib inline
```

接下来，我们使用 Pandas 加载数据集并显示前 5 行。

```python
data = pd.read_csv('spam.csv', encoding='latin-1')
data.head(5)
```

![](images/00081.jpeg)

列 `v1` 包含类别标签，而 `v2` 是短信内容，我们将其作为模型的特征。

让我们绘制一个柱状图来直观展示正常短信和垃圾短信的分布。

```python
count_class = pd.value_counts(data['v1'], sort=True)
count_class.plot(kind='bar', color=[['blue', 'red']])
plt.title('Bar chart')
plt.show()
```

![](images/00082.gif)

单词不能直接作为特征输入模型，因此我们必须将它们向量化以创建新特征。我们通过考虑单词频率（在移除英语句子中常见的词如 "the"、"a"、"of" 等之后）来实现这一点。我们可以使用 Scikit-Learn 轻松完成此特征提取。

```python
from sklearn.feature_extraction.text import CountVectorizer

f = CountVectorizer(stop_words='english')
X = f.fit_transform(data["v2"])
print(np.shape(X))
```

![](images/00083.jpeg)

向量化后，创建了 8,404 个新特征。

接下来，我们将目标变量映射为类别，并将数据集划分为训练集和测试集。

```python
from sklearn.model_selection import train_test_split

data["v1"] = data["v1"].map({'spam': 1, 'ham': 0})
X_train, X_test, y_train, y_test = train_test_split(X, data['v1'], test_size=0.25, random_state=42)
```

下一步是初始化朴素贝叶斯模型并在数据上对其进行训练。

```python
from sklearn.naive_bayes import MultinomialNB

clf = MultinomialNB()
clf.fit(X_train, y_train)
```

最后，我们在测试集上评估模型性能。

```python
score = clf.score(X_test, y_test)
print('Accuracy: {}'.format(score))
```

![](images/00084.jpeg)

朴素贝叶斯分类器达到了 0.976 的准确率，这意味着它正确预测了 97.6% 样本的类别。

# 决策树与随机森林

## 分区的熵

熵可以定义为随机事件序列中不确定性的度量。它是样本空间中无序程度的比率，与知识直接对立。当系统的熵较高时，从系统中获得的知识较低，反之亦然。对熵的一个直观理解是将其视为为了获得某些知识所需提出的问题数量。例如，如果我选了一个随机数字，你试图猜出它是什么。问一个问题，“它是奇数吗”，会将可能性空间减半。这意味着试图确定我选择的数字时的熵或不确定性降低了。同样，信息增益量很大，因为该问题通过划分样本空间让你更接近答案。熵通常在 0 到 1 之间。熵为 0 的系统高度稳定，从这种系统中获得的知识很高。一般来说，系统中低熵表示高知识，而高熵表示低知识或不稳定。

熵可以用数学公式表示为：

![](images/00085.jpeg)

