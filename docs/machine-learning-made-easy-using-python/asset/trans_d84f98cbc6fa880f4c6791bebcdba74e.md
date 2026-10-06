

| | 年龄 | 性别 | 观看内容 | 类型 |
|---|---|---|---|---|
| 0 | 19 | 男性 | 喜剧 | 悬疑 |
| 1 | 19 | 女性 | 浪漫 | 剧情 |
| 2 | 19 | 男性 | 浪漫 | 剧情 |

在第二次运行中，我们打印了数据集的前三行，通过观察，我们可以说：如果一个 18 岁的男性（该样本未在数据集中出现）之前看过喜剧电影，那么他很可能也会喜欢悬疑电影，同时也喜欢喜剧电影。

所以，我们使用非常少的数据创建了电影推荐模型，现在轮你来测试这个模型，甚至可以听听亲戚的意见并使用模型向他们推荐！

## 22 机器学习应用 2

-   广告处理

![](img/d75fea3635f5553f1cb0585b399b1b4b_208_0.png)

## 机器学习应用 2

**问题：** 你必须决定是否向用户投放广告。如果是，则向哪个节目投放广告？例如汽车广告或保险广告。输入为用户的年龄和用户类别（即由另一个模型根据用户过去的搜索结果提供的分组）。你将获得以下数据集

![](img/d75fea3635f5553f1cb0585b399b1b4b_209_0.png)

我们再次需要决定使用哪种方法，显然这是一个分类问题。我们可以使用 KNN 分类算法来完成此任务。

现在让我们进入 Jupyter Notebook，导入算法、LabelEncoder、pandas 库以及数据集

```python
In [1]: import pandas
from sklearn.neighbors import KNeighborsClassifier
from sklearn.preprocessing import LabelEncoder
dt = pandas.read_csv('advertisement.csv')
dt.head(3)
```

| 年龄 | 搜索 | 广告 |
|---|---|---|---|
| 0 | 18 | Cars | Car |
| 1 | 19 | Automobiles | None |
| 2 | 21 | Automobiles | None |

我们的可处理数据仍然非常少。我们将年龄和搜索作为输入，广告作为输出。但我们需要对标签进行预处理。

```python
In [2]: Enc = LabelEncoder()
Enc.fit(['Cars','Automobiles','Health','Car',
'Insurance', 'None'])
for col in ['Search','Ad']:
    dt[col] = Enc.transform(dt[col])
```

我们使用 Enc 编码器对 Search 和 Ad 列中的值进行了编码。现在我们可以进入数据划分的下一步，正如早之前提到的，我们没有足够的数据将其划分为训练集和测试集。因此，我们需要手动创建训练集。让我们来看整个数据集：

我们有 20 行 3 列数据。我们已经知道输入（即年龄和搜索）和输出（即广告），其中输入搜索将由另一个分类器提供，该分类器将根据之前的搜索将用户分为 Cars、Automobiles、Health 和 None 类别。我们可以从数据中直观地理解：18-28 岁的用户在处于 Cars 类别时应只为其展示汽车广告；否则，当处于 Health 类时，显示保险广告。同样，30 岁或以上的人如果处于 Cars 或 Automobiles 类，应该向他们展示汽车广告，反之亦然。

| 年龄 | 搜索 | 广告 |
|---|---|---|
| 18 | Cars | Car |
| 19 | Automobiles | None |
| 21 | Automobiles | None |
| 22 | Cars | Car |
| 23 | None | None |
| 25 | None | None |
| 26 | Health | Insurance |
| 27 | Cars | Car |
| 18 | Health | Insurance |
| 19 | None | None |
| 20 | None | None |
| 22 | Automobiles | None |
| 26 | None | Insurance |
| 30 | Health | Insurance |
| 14 | Automobiles | Car |
| 29 | Cars | Car |
| 29 | Health | Insurance |
| 29 | None | Insurance |
| 32 | Automobiles | Car |
| 32 | Health | Insurance |

