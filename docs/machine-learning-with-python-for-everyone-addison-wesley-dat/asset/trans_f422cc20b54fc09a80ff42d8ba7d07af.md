

In [36]:

```python
design_df = patsy.dmatrix("big_sepal:big_petal - 1",
                         data=iris_df.iloc[[0, 50, 100]],
                         return_type='dataframe')

# breaking up the long column names
display(design_df.iloc[:, :2])
display(design_df.iloc[:,2: ])
```

|  | big_sepal[False]:big_petal[False] | big_sepal[True]:big_petal[False] |
|---|---|---|
| 0 | 0.0000 | 1.0000 |
| 50 | 0.0000 | 0.0000 |
| 100 | 0.0000 | 0.0000 |

|  | big_sepal[False]:big_petal[True] | big_sepal[True]:big_petal[True] |
|---|---|---|
| 0 | 0.0000 | 0.0000 |
| 50 | 0.0000 | 1.0000 |
| 100 | 0.0000 | 1.0000 |

示例 50 和 100 的花萼和花瓣都很大。示例 0 的花萼大而花瓣小。

当我们创建类别特征与数值特征的交互项时，实际上为我们考虑的每个类别都得到了该数值特征的一个权重：

In [37]:

```python
# we (Q)uote sepal length because it has a space in the name
design_df = patsy.dmatrix("C(species,Treatment):Q('sepal length') - 1",
                         data=iris_df.iloc[[0, 50, 100]],
                         return_type='dataframe')

# breaking up the long column names
display(design_df.iloc[:,[0]])
display(design_df.iloc[:,[1]])
display(design_df.iloc[:,[2]])
```

|  | C(species, Treatment)[setosa]:Q('sepal length') |
|---|---|
| 0 | 5.1000 |
| 50 | 0.0000 |
| 100 | 0.0000 |

|  | C(species, Treatment)[versicolor]:Q('sepal length') |
|---|---|
| 0 | 0.0000 |
| 50 | 7.0000 |
| 100 | 0.0000 |

|  | C(species, Treatment)[virginica]:Q('sepal length') |
|---|---|
| 0 | 0.0000 |
| 50 | 0.0000 |
| 100 | 6.3000 |

如果我们回到数据中仔细查看，就能明白这些值的来源——列值正是该类别下所选取的花萼长度值。它是(1)物种的独热编码与(2)花萼长度的逐元素相乘。

In [38]:

```python
print(iris_df.iloc[[0, 50, 100]]['sepal length'])
```

```
0              5.1000
50             7.0000
100            6.3000
Name: sepal length, dtype: float64
```

## 10.6.2.2 从 Patsy 到 sklearn

我们还可以看一个将 patsy 公式与 sklearn 模型连接起来的简单示例。本质上，我们手动构建设计矩阵——即原始特征与用于学习参数的数据之间的映射——然后手动应用它，最后运行模型。

In [39]:

```python
import statsmodels as sm
import statsmodels.formula.api as smf
```

In [40]:

```python
# we can build a design matrix and send it to sklearn
design = "C(species,Treatment):petal_area"
design_matrix = patsy.dmatrix(design, data=iris_df)

# intercept is already in design matrix
lr = linear_model.LinearRegression(fit_intercept=False)

mod = lr.fit(design_matrix, iris_df['sepal width'])
print(mod.coef_)
```

```
[ 2.8378  1.402  -0.0034  0.0146]
```

In [41]:

```python
# hey, we get the same results!
formula = "Q('sepal width') ~ C(species,Treatment):petal_area"
res1 = smf.ols(formula=formula, data=iris_df).fit()
print(res1.params)
```

```
Intercept 2.8378
C(species, Treatment)[setosa]:petal_area 1.4020
C(species, Treatment)[versicolor]:petal_area -0.0034
C(species, Treatment)[virginica]:petal_area 0.0146
dtype: float64
```

幸运的是，无论我们手动处理数据以输入到 sklearn，还是使用自包含的 statsmodels 方法，都能得到相同的结果——其中存在一些舍入误差。

## 10.6.3 使用转换器添加特征

如果我们希望与 sklearn 更紧密地集成，可以使用 FunctionTransformer 定义独立函数的特征变换，或者通过继承 TransformerMixin 来定义基于类的变换。如果我们不需要在训练集和测试集之间记忆或学习任何东西——也就是说变换完全自包含，比如取数据绝对值的对数——那么就不需要引入基于类的复杂性。我们先在一个干净的 DataFrame 中重新创建最初的面积特征。

In [42]:

```python
iris_df = pd.DataFrame(iris.data, columns=iris.feature_names)
iris_df['species'] = iris.target_names[iris.target]

area_df = pd.DataFrame({"sepal_area" : iris_df['sepal length'] *
                        iris_df['sepal width'],
                        "petal_area" : iris_df['petal length'] *
                        iris_df['petal width']})
```

现在，如果我们只想与整个数据集的中位数进行比较——不区分训练集和测试集——我们可以快速创建一个转换器：

In [43]:

```python
def median_big_small(d):
    return d > np.median(d)

transformer = skpre.FunctionTransformer(median_big_small)
res = transformer.fit_transform(area_df)

print("Large areas as compared to median?")
print(res[[0, 50, 100]])
```

```
Large areas as compared to median?
[[ True False]
 [ True False]
 [ True  True]]
```

如果我们希望在训练数据上学习中位数，然后基于学到的中位数将离散化应用于测试数据，就需要更多的支持。我们必须先在训练数据上计算中位数，然后将这些中位数作为阈值应用于训练数据或测试数据。

In [44]:

```python
from sklearn.base import TransformerMixin
class Median_Big_Small(TransformerMixin):
    def __init__(self):
        pass
    def fit(self, ftrs, tgt=None):
        self.medians = np.median(ftrs)
        return self
    def transform(self, ftrs, tgt=None):
        return ftrs > self.medians
```

其使用模式与内置转换器相同，并且与标准学习模型非常相似。因为我们使用了 train_test_split，所以这里会得到随机选取的示例。

In [45]:

```python
# training-testing split
training, testing = skms.train_test_split(area_df)

# create and run the transformer
transformer = Median_Big_Small()
train_xform = transformer.fit_transform(training)
test_xform = transformer.transform(testing)

# the dataframes survived!

print('train:')
display(train_xform[:3])
print('test:')
display(test_xform[ :3])
```

train:

|  | sepal_area | petal_area |
|---|---|---|
| 39 | True | False |
| 142 | True | False |
| 64 | True | False |

test:

|  | sepal_area | petal_area |
|---|---|---|
| 147 | True | False |
| 78 | True | False |
| 133 | True | False |

## 10.7 目标变量的处理

在线性回归模型的背景下，你可能会听到以下建议：

- 变换输入特征主要是修正输入特征与目标变量之间关系的非线性。
- 变换目标值可以修正输入特征与目标变量之间无法解释的差异问题。

我想补充几点说明。修正非线性意味着特征与目标之间的基本关系不是线性的。线性回归模型专门寻找一条最佳直线。若想突破简单直线的限制，就需要解决线性回归的偏差问题。

无法解释的差异问题体现在预测与真实值之间误差的特征上。这些就是 7.3.2 节中的残差。我们可能看到两种模式：(1) 系统性行为，例如输入 x 值越大，误差也越大；(2) 误差呈非正态分布。非正态性意味着误差在预测线上下可能不均衡，或者误差不会迅速衰减。

我们可以大胆地将这些观点转化为处理建模问题的一般经验法则。

- 操作输入主要是为了解决模型中的偏差。
- 操作目标主要是为了解决噪声如何影响输入与目标之间的关系。这种噪声出现在关系本身中，并不是参数估计的变化。

## 10.7.1 操作输入空间

让我们通过观察第一条规则——修正非线性关系，或者更一般地说，修正偏差——的实际表现，来让这些想法更加具体。

In [46]:

```python
x = np.linspace(1,10,50)
n1 = np.random.normal(size=x.shape)

comparison = pd.DataFrame({'x' : x,
    'd1' : 2*x+5   + n1,
    'd2' : 2*x*x+5 + n1})

comparison['x'] = x
melted = pd.melt(comparison, id_vars=['x'])
```

两个数据列中有一个与众不同：

In [47]:

```python
sns.lmplot(x='x', y='value',
    data=melted, col='variable', ci=None,
    size=3);
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_379_0.png)

看下面的图，用于关联 d1 和 x 的模型表现良好。其残差看起来有些接近正态分布——尽管我们只使用了 50 个数据点，所以不会看到非常平滑的正态形状。d2 模型的残差则与正态曲线完全没有明显关系。

