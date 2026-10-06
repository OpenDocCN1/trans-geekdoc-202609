
在比较预测值和实际值之前，我们可以要求模型预测一些值，例如 30 岁女性的收入以及 42 岁男性的收入是多少。

```python
In [5]: RegModel.predict([0,30], [1,42])

Out[5]: array([[60.5504497], [62.09356734]])
```

我们传递值的方式。由于 Female（女性）和 Male（男性）被编码为 0 和 1，我们传递了 [0,30], [1,42]，模型告诉我们30 岁的女性收入约为 60.5k，42 岁的男性的收入约为 62k。现在，让我们预测测试输入并与实际结果进行比较。

```python
In [6]: pred_y = RegModel.predict(test_X)
cmp = pandas.DataFrame({'Predicted':pred_y.flatten(), 'Actual':test_y['kind='Annual Income ($k)'].values})
cmp.plot(kind='bar',figsize=(7.5,6))

Out[6]: <matplotlib.axes.AxesSubplot object at 0x1402ccc89a0>
```

![](img/d75fea3635f5553f1cb0585b399b1b4b_140_0.png)

正如你所观察到的，由于数据的分布，大多数值都是错误的，那么我们现在该做什么？

提高模型性能的方法有很多，我们可以增加数据，在我们案例中只有 200 行数据，为了精确预测值，我们至少至少是目前数据量的 10 倍，因为在这种情况下分布不是正态的。

```python
In [7]: cmp['Predicted'].plot(kind='density')
plt.show()
cmp['Actual'].plot(kind='density',color='orange')
plt.show()
```

![](img/d75fea3635f5553f1cb0585b399b1b4b_141_0.png)
![](img/d75fea3635f5553f1cb0585b399b1b4b_141_1.png)

我们将在性能和指标课程中详细学习更多提高模型性能的方法。

## 16 分类算法

- 决策树
- 逻辑回归
- 朴素贝叶斯

![](img/d75fea3635f5553f1cb0585b399b1b4b_142_0.png)

## 16 分类

我们已经知道什么是分类算法了，但分类算法有两种类型：懒学习器（lazy learners）和急学习器（eager learners）。即懒学习器在训练期间学习较少，例如 KNN 算法；而急学习器在训练中学习而在测试中减少，例如决策树、朴素贝叶斯等。现在让我们使用决策树创建一个分类器。

### # 决策树

让我们创建一个分类器，在提供年龄和性别输入的情况下，将客户分类为他们喜欢的口味。为此，我们将使用决策树，这是一种可以执行分类和回归任务的算法。它学习数据集中的类别并使用决策树创建类别，然后预测输入的类别。
我们将使用 scikit-learn 的 DecisionTreeClassifier 来创建我们的模型。你可以从这里下载数据集——
现在进入你的 Jupyter notebook 并导入此项目所需的包和模块。

```python
import pandas
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split (optional)
```

![](img/d75fea3635f5553f1cb0585b399b1b4b_143_0.png)

```python
In [1]: import pandas
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split
```

我们可以导入数据集并使用 head() 函数进行预览。

```python
In [2]: import pandas
from sklearn.tree import DecisionTreeClassifier
dt = pandas.read_csv('flavour.csv')
dt.head()
```

| Age | Gender | Flavour |
|---|---|---|
| 0 | 6 | Chocolate |
| 1 | 6 | Strawberry |
| 2 | 7 | Chocolate |
| 3 | 8 | Strawberry |
| 4 | 11 | Butterscotch |

正如你所看到的，我们需要对数值进行编码。所以，让我们导入预处理模块并编码标签。

```python
In [3]: import pandas
from sklearn.tree import DecisionTreeClassifier
from sklearn import preprocessing
dt = pandas.read_csv('flavour.csv')
Enc = preprocessing.LabelEncoder().fit(['Male', 'Female'])
dt['Gender'] = Enc.transform(dt['Gender'])
dt.head()
```

| Age | Gender | Flavour |
|---|---|---|
| 0 | 6 | Chocolate |
| 1 | 6 | Strawberry |
| 2 | 7 | Chocolate |
| 3 | 8 | Strawberry |
| 4 | 11 | Butterscotch |

Male 和 Female 标签使用 LabelEncoder 分别编码为 1 和 0。注意我们对 Male 和 Female 进行了拟合。

现在我们可以移动新单元格，并将数据拆分为输入和输出。然后我们将使用 DecisionTreeClassifier 创建分类器，并使用输入和输出值训练模型。

```python
In [4]: inp_X = dt.drop(columns='Flavour')
out_y = dt.drop(columns=['Age', 'Gender'])
# Classifier
model = DecisionTreeClassifier()
model.fit(inp_X,out_y)
```
Out[4]: DecisionTreeClassifier()

我们使用 fit() 函数训练了模型，模型已准备好进行预测。让我们询问模型 7 岁男孩和 9 岁女孩会喜欢什么：

```python
In [5]: model.predict([[7,1], [9,0]])
```
Out[5]: array(['Chocolate', 'Strawberry'], dtype=object)

根据我们的模型，7 岁的男孩 [7,1] 会喜欢巧克力，9 岁的女孩会喜欢草莓，这很准确。但我们只训练了 20 行数据，得到了一些结果。如果我们询问模型预测 30 岁的女性会喜欢什么，即超出了数据提供的年龄范围：

```python
In [8]: model.predict([[30,0]])
```
Out[8]: array(['Coffee'], dtype=object)

根据我们的模型，30 岁的女性 [7,1] 会喜欢咖啡，这可能是错误的，因为数据集提供的最大年龄是 24。为了查看模型用于分类数值的决策树，可以使用以下代码：

```python
In [1]: import graphviz
from sklearn.tree import export_graphviz

data = export_graphviz(model,
out_file='dt_tree.dot', feature_names=['Age', 'Gender'],
class_names=['Chocolate', 'Strawberry', 'Butterscotch', 'Vanilla', 'Mango', 'Almond_Choco', 'Coffee'], filled=True, rounded=True, special_characters=True)
graph = graphviz.Source(data)
```

![](img/d75fea3635f5553f1cb0585b399b1b4b_146_0.png)

此时你需要在 anaconda prompt 中使用以下代码安装 graphviz
`conda install -c conda-forge python-graphviz`
然后导入 export_graphviz 和 graphviz。使用 export_graphviz 可视化决策树并使用 graphviz 的 Source 函数将其存储在 data 中。我们查看树，但你可以看到树太大无法放入页面，所以让我们通过拆分来理解它。
看看如果输入 [7,1]（7岁男孩）会发生什么：

![](img/d75fea3635f5553f1cb0585b399b1b4b_147_0.png)

从根节点开始，第一次比较是年龄是否小于等于20.5（Age <= 20.5），输入的年龄为7，所以我们移动到 True 侧。

![](img/d75fea3635f5553f1cb0585b399b1b4b_147_1.png)

接下来算法比较年龄是否小于等于9，我们的年龄较小，所以我们向下移动（直接到绿色区域）。

![](img/d75fea3635f5553f1cb0585b399b1b4b_147_2.png)

现在我们正在检查性别是否小于等于 0.5（即 0）。但这里的性别是 1，所以我们移动到非绿色侧。

![](img/d75fea3635f5553f1cb0585b399b1b4b_148_0.png)
![](img/d75fea3635f5553f1cb0585b399b1b4b_148_1.png)
![](img/d75fea3635f5553f1cb0585b399b1b4b_148_2.png)

再次比较年龄，年龄小于等于或小于18，且结果是7，所以我们最终停在橙色框处（orange = True, False）并选择类别，即巧克力。

![](img/d75fea3635f5553f1cb0585b399b1b4b_148_3.png)
![](img/d75fea3635f5553f1cb0585b399b1b4b_148_4.png)
![](img/d75fea3635f5553f1cb0585b399b1b4b_148_5.png)

从根节点开始，我们得出结论：输入属于巧克力类类别，即一个 7 岁的男孩喜欢巧克力。

但你可能会问还有哪些其他属性，如 gini、samples 等。Gini 是代价函数的名称，用于评估数据集中的二分划分，并与分类目标变量“Success”（成功）或“Failure”（失败）配合。完美的 Gini 指值为 0，最差的是 0.5，用于判断是否进一步拆分。你可以看到 gini 分数为 0 的没有被进一步拆分。samples 是给定数据集中具有相应特征的数据点数量。

