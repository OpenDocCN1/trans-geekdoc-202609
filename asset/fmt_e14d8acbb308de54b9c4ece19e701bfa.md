
| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | weak | yes |
| rain | cool | normal | strong | no |

**分组属性值 (mild)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | mild | high | weak | yes |

- 目标属性类别计数(Yes/No)= `{'yes': 1, 'no': 1}`
- 与 `cool` 关联的实例/记录总数为：`2`
- 类别 `no` 的概率为：`0.5000`
- 类别 `yes` 的概率为：`0.5000`
- 目标属性类别计数(Yes/No)= `{'yes': 1}`
- 与 `mild` 关联的实例/记录总数为：`1`
- 类别 `yes` 的概率为：`1.0000`
- 目标属性类别计数(Yes/No)= `{'yes': 2, 'no': 1}`
- 与 `S-rain` 关联的实例/记录总数为：`3`
- 类别 `no` 的概率为：`0.3333`
- 类别 `yes` 的概率为：`0.6667`
- **`Temperature` 的信息增益为：`0.2516291673878229`**

##### `Humidity` 的信息增益计算（`rain` 的子树）

**分组属性值 (high)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | mild | high | weak | yes |

**分组属性值 (normal)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | weak | yes |
| rain | cool | normal | strong | no |

- 目标属性类别计数(Yes/No)= `{'yes': 1}`
- 与 `high` 关联的实例/记录总数为：`1`
- 类别 `yes` 的概率为：`1.0000`
- 目标属性类别计数(Yes/No)= `{'yes': 1, 'no': 1}`
- 与 `normal` 关联的实例/记录总数为：`2`
- 类别 `no` 的概率为：`0.5000`
- 类别 `yes` 的概率为：`0.5000`
- 目标属性类别计数(Yes/No)= `{'yes': 2, 'no': 1}`
- 与 `S-rain` 关联的实例/记录总数为：`3`
- 类别 `no` 的概率为：`0.3333`
- 类别 `yes` 的概率为：`0.6667`
- **`Humidity` 的信息增益为：`0.2516291673878229`**

##### `Wind` 的信息增益计算（`rain` 的子树）

**分组属性值 (strong)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | strong | no |

**分组属性值 (weak)：**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | mild | high | weak | yes |
| rain | cool | normal | weak | yes |

- 目标属性类别计数(Yes/No)= `{'no': 1}`
- 与 `strong` 关联的实例/记录总数为：`1`
- 类别 `no` 的概率为：`1.0000`
- 目标属性类别计数(Yes/No)= `{'yes': 2}`
- 与 `weak` 关联的实例/记录总数为：`2`
- 类别 `yes` 的概率为：`1.0000`
- 目标属性类别计数(Yes/No)= `{'yes': 2, 'no': 1}`
- 与 `S-rain` 关联的实例/记录总数为：`3`
- 类别 `no` 的概率为：`0.3333`
- 类别 `yes` 的概率为：`0.6667`
- **`Wind` 的信息增益为：`0.9182958340544896`**

**信息增益最大的属性为：** `Wind`

#### 生成的决策树

```python
{'Outlook': {'overcast': 'yes',
  'rain': {'Wind': {'strong': 'no', 'weak': 'yes'}},
  'sunny': 'no'}}
```

### 实验 4

**目的：** 通过实现反向传播算法构建人工神经网络，并使用合适的数据集进行测试。

#### 反向传播算法

##### 反向传播

每个训练样本均为一对形式，其中 是网络输入值的向量， 是目标网络输出值的向量。

`ƞ` 为学习率（例如 `.05`）。 为网络输入数， 为隐藏层单元数， 为输出单元数。

从单元 i 输入到单元 j 的值记为 ，从单元 i 到单元 j 的权重记为 。

创建一个具有 输入、 隐藏单元和 输出单元的前馈网络。

将所有网络权重初始化为小的随机数。

直到满足终止条件，执行以下操作：

对于训练样本中的每个 `(⃗𝑥, 𝑡)`，执行：

向前传播输入通过网络：

输入实例 `⃗𝑥` 到网络，并计算网络中每个单元 u 的输出。

向后传播误差通过网络：

##### 程序

```python
import numpy as np

X =
y =
X = # X 数组纵向的最大值
y = y/100

###### Sigmoid 函数
def sigmoid
    return \+ np.exp(-x)))

###### Sigmoid 函数的导数
def
    return x \* \- x)

###### 变量初始化
###### 设置训练迭代次数
###### 设置学习率
inputlayer_neurons = 2 # 数据集中的特征数量
hiddenlayer_neurons = 3 # 隐藏层神经元数量
output_neurons = 1 # 输出层神经元数量

###### 权重和偏置初始化
wh=np.random.uniform(size=(inputlayer_neurons,hiddenlayer_neurons))
wout=np.random.uniform(size=(hiddenlayer_neurons,output_neurons))
###### 均匀抽取一定范围的随机数，维度为 x*y

###### 前向传播
for i in
    hinp1=np.dot(X,wh)
    hinp=hinp1 \+ bh
    hlayer_act = sigmoid(hinp)
    outinp1=np.dot(hlayer_act,wout)
    outinp= outinp1+ bout
    output = sigmoid(outinp)
    EO = y-output
    outgrad = derivatives_sigmoid(output)
    d_output = EO\* outgrad
    EH = d_output.dot(wout.T)
    hiddengrad = derivatives_sigmoid(hlayer_act)
    # 隐藏层权重对误差的贡献程度
    d_hiddenlayer = EH \* hiddengrad
    wout += hlayer_act.T.dot(d_output) \*lr
    # 下一层误差与当前层输出的点积
    bout += \*lr
    wh += X.T.dot(d_hiddenlayer) \*lr
    #bh += np.sum(d_hiddenlayer, axis=0,keepdims=True) \*lr
    \n" \+ str(X))
Output: \n" \+ str(y))
Output: output)
```

#### 输出

**输入：**

```
[[0.66666667 1.        ]
 [0.33333333 0.55555556]
 [1.         0.66666667]]
```

**实际输出：**

```
[[92.]
 [86.]
 [89.]]
```

**预测输出：**

```
[[0.99999928]
 [0.99999802]
 [0.9999994]]
```

---

### 实验 5

**目的：** 编写程序实现朴素贝叶斯分类器，用于存储为 .CSV 文件的样本训练数据集。考虑少量测试数据集，计算分类器的准确率。

#### 贝叶斯定理

`P(H/E) = P(E/H) P(H)/P(E)`

H-假设，E-事件/证据

贝叶斯定理基于条件概率工作。

已知事件已发生或事件为真，则需计算在此事件下假设的概率。

即事件 `E` 发生时假设 `H` 发生的几率。

`P(H)` - 称为先验概率，事件 `E` 发生前 `H` 的概率。

`P(H/E)` - 后验概率，事件 `E` 为真后 `E` 的概率。

#### 训练数据集：红酒数据集

红酒数据集包含在意大利特定地区种植的葡萄酒化学分析结果。

共包含 178 个样本（数据），每个样本记录了 13 项化学分析（特征）。

包含三个类别（目标），无缺失值。

##### 程序

```python
import numpy as np
import pandas as pd
from sklearn import datasets

wine = datasets.load_wine()
print wine.feature_names)
print wine.target_names)

y=print (wine.target)

from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(wine.data, wine.target,

from sklearn.naive_bayes import GaussianNB
gnb = GaussianNB()
gnb.fit(X_train, y_train)
y_pred = gnb.predict(X_test)

from sklearn import metrics
y_pred))

from sklearn.metrics import confusion_matrix
cm=np.array(confusion_matrix(y_test,y_pred))
print Matrix:
```

#### 输出

**特征：** `['alcohol', 'malic_acid', 'ash', 'alcalinity_of_ash', 'magnesium', 'total_phenols', 'flavanoids', 'nonflavanoid_phenols', 'proanthocyanins', 'color_intensity', 'hue', 'od280/od315_of_diluted_wines', 'proline']`

**标签：** `['class_0' 'class_1' 'class_2']`

```
         0      1      2      3       4      5  ...      7      8      9      10     11       12
0    14.23   1.71   2.43   15.6   127.0   2.80  ...   0.28   2.29   5.64   1.04   3.92  1065.0
1    13.20   1.78   2.14   11.2   100.0   2.65  ...   0.26   1.28   4.38   1.05   3.40  1050.0
2    13.16   2.36   2.67   18.6   101.0   2.80  ...   0.30   2.81   5.68   1.03   3.17  1185.0
3    14.37   1.95   2.50   16.8   113.0   3.85  ...   0.24   2.18   7.80   0.86   3.45  1480.0
4    13.24   2.59   2.87   21.0   118.0   2.80  ...   0.39   1.82   4.32   1.04   2.93   735.0
[5 rows x 13 columns]
```

```
(178, 13)
[0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
 0 0 0 0 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2
 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2]
[0 0 1 2 0 1 0 0 1 0 2 2 2 2 0 1 1 0 0 1 2 1 0 2 0 0 1 2 0 1 2 1 1 0 1 1 0
 2 2 0 2 1 0 0 0 2 2 0 1 1 2 0 0 2]
```

**准确率：** `0.9074074074074074`

**混淆矩阵：**

```
[[20  1  0]
 [ 2 15  2]
 [ 0  0 14]]
```

### 实验编号 6

#### 目的

假设有一组需要分类的文档，使用朴素贝叶斯分类器模型来执行此任务。可以使用内置的 Java 类/API 来编写程序。计算数据集的准确率、精确率和召回率。

#### 用于学习和分类文本的朴素贝叶斯算法

**Examples** 是一组文本文档及其目标值。**V** 是所有可能目标值的集合。该函数学习概率项 **P**，描述从某类文档中随机抽取的单词是英文单词的概率。它还学习类先验概率。

1. 收集 **Examples** 中出现的所有单词、标点符号和其他标记。

2. **Vocabulary** ← **Examples** 中任何文本文档出现的所有不同单词和其他标记的集合。

3. 计算所需的概率项。

4. 对 **V** 中的每个目标值执行：

   - 目标值为 **vj** 的 **Examples** 文档子集。

   - **P(vj)** ← |**Examples**| / |**Examples**|。

   - **Textj** ← 通过连接 **Examples** 的所有成员创建的单个文档。

   - **n** ← **Textj** 中不同单词位置的总数。

   - 对 **Vocabulary** 中的每个单词：

     - **nk** ← 单词在 **Textj** 中出现的次数。

     - **P(wk | vj)** ← ( **nk** + 1 ) / ( **n** + |**Vocabulary**| )。

#### 训练数据集

**ML6.CSV**

##### 程序
