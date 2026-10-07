
# 最近邻算法

因此，变量 `x` 包含所有的独立变量，变量 `y` 包含因变量。

从数据中注意到 `Recency`（最近性）和 `Frequency`（频率）的值远小于 `Monetary Value`（金额）。这将影响距离的计算。我们将数据进行缩放，使得所有独立变量的值处于相似的范围。对于数据缩放，我们使用 `sklearn` 中的 `StandardScaler()` 类。`StandardScaler()` 存在于 `sklearn.preprocessing` 中。

当我们使用 `StandardScaler()` 时，必须对现有数据进行固定。在 `StandardScaler()` 的情况下，调用 `fit()` 方法计算数据的均值和标准差。一旦获取了这些值，就可以调用 `transform()` 方法来转换每个数据。另一种方法是调用 `fit_transform()` 方法，它首先执行 `fit()` 操作然后执行 `transform()` 方法。

```python
from sklearn.preprocessing import StandardScaler

sc = StandardScaler()
XS = sc.fit_transform(X.numpy())
XS = pd.DataFrame(XS, columns=['Frequency', 'MonetaryValue', 'Recency'])
XS.head()
```

| 频率 (Frequency) | 金额 (MonetaryValue) | 最近性 (Recency) |
|---|---|---|
| 0 | 8.785658 | 2.324680 |
| 1 | 0.398556 | 0.253157 | -0.900354 |
| 2 | -0.280101 | -0.061603 | -0.171476 |
| 3 | -0.088205 | -0.067495 | -0.740600 |
| 4 | -0.326905 | -0.190139 | 2.174911 |

注意到在缩放所有独立变量的值后，它们处于相似的范围。

在此阶段，我们将分离用于训练模型和测试的数据。我们将 80% 的数据用于训练，20% 用于测试。为了创建训练集和测试集，我们使用 `sklearn.model_selection` 中的 `train_test_split()` 方法。`train_test_split()` 方法存在于 `sklearn` 中。我们传递所有独立变量的值（在我们案例中，这些在 `XS` 中）和因变量（在我们案例中，存储在 `y` 中）。`test_size` 参数决定了测试集中随机选择的样本数量。

剩余的数据点被分配到训练集。我们为 `random_state` 参数设置了一个值，以便每次运行此脚本时结果都是相同的。

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(XS, y, test_size=0.2, random_state=42)
```

```python
print("Shape of X_train =", X_train.shape)
```

```python
print("Shape of X_test =", X_test.shape)
```

```python
print("\nDistribution of labels in X_train\n")
```

X_train 的形状 (3466, 3)

X_test 的形状 (867, 3)

X_train 中的标签分布：

```
0 1358
7 737
1 470
5 419
10 376
9 79
8 13
2 5
3 5
4 2
11 1
Name: Segment, dtype: int64
```

在训练集和测试集之后，我们注意到训练集中的数据点需要平衡，以便让所有类别具有相似数量的样本。平衡数据集的一种方法是对数据进行过采样（Over Sample）。通过过采样，我们为数据点数量较少的标签随机创建额外的数据点。有许多过采样的算法。我们将使用 `RandomOverSampler` 算法来创建额外的数据点。

然而，在使用 `RandomOverSampler` 库之前，我们需要导入提供此功能的库。`RandomOverSampler` 可以在 `imblearn`（或 `imbalanced learn`）包可用。通常，你需要在你的环境中安装该包：

```bash
!pip install imblearn
```

一旦成功安装 `imblearn` 包，我们就可以使用 `RandomOverSampler`。

我们需要传递所有独立变量的值（在我们案例中在 `X_train` 中）以及因变量（在我们案例中在 `y_train` 中）。`RandomOverSampler` 有 `fit()` 方法来拟合数据，有 `resample()` 方法创建随机样本。这里使用了 `fit_resample()`。过采样后的数据集存储在变量 `X0` 和 `y0` 中：

```python
from imblearn.over_sampling import RandomOverSampler

oversample = RandomOverSampler(random_state=42)
X0, y0 = oversample.fit_resample(X_train)
print("Number of samples after oversampling", y0.value_counts())
print("Shape of X after oversampling =", X0.shape)
```

过采样后每个标签的样本数：

```
0 1358
7 737
1 470
5 419
10 376
9 79
8 13
2 5
3 5
4 2
11 1
Name: Segment, dtype: int64
```

过采样后 X 的形状 = (16296, 3)

# 学习分类算法

过采样后，每个类别都有相同数量的样本。

```python
from sklearn.neighbors import KNeighborsClassifier
```

```python
model = KNeighborsClassifier()
model.fit(X_train, y_train)
```

```python
y_pred = model.predict(X_test)
```

现在我们将评估模型的性能：

```python
from sklearn.metrics import classification_report, confusion_matrix, accuracy_score

print(classification_report(y_test, y_pred))
print(confusion_matrix(y_test, y_pred))
print(accuracy_score(y_test, y_pred))
```

输出如下：

```
              precision    recall  f1-score   support

           0      0.998      1.000      0.999       737
           1      0.998      0.998      0.998       470
           2      0.000      0.000      0.000         5
           3      0.000      0.000      0.000         5
           4      0.000      0.000      0.000         2
           5      0.998      0.998      0.998       419
           6      0.000      0.000      0.000         0
           7      1.000      1.000      1.000      1358
           8      0.000      0.000      0.000        13
           9      0.986      1.000      0.993        79
          10      0.997      1.000      0.999       376
          11      0.000      0.000      0.000         1

       average      0.893      0.898      0.893      2675
weighted avg      0.996      0.898      0.991      2675
```

```
[[737   0   0   0   0   0   0   0   0   0   0]
 [  0 470   0   0   0   0   0   0   0   0   0]
 [  0   0   5   0   0   0   0   0   0   0   0]
 [  0   0   0   5   0   0   0   0   0   0   0]
 [  0   0   0   0   2   0   0   0   0   0   0]
 [  0   0   0   0   0 419   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0 1358   0   0   0]
 [  0   0   0   0   0   0   0   0  13   0   0]
 [  0   0   0   0   0   0   0   0   0  79   0]
 [  0   0   0   0   0   0   0   0   0   0 376   0]
 [  0   0   0   0   0   0   0   0   0   0   0   1]]
```

准确率：0.898129

现在我们将可视化混淆矩阵：

```python
import matplotlib.pyplot as plt
import seaborn as sns

cm = confusion_matrix(y_test, y_pred)
plt.figure(figsize=(10,8))
sns.heatmap(cm, annot=True, fmt='d', cmap='Blues')
plt.xlabel('Predicted')
plt.ylabel('Actual')
plt.title('Confusion Matrix')
plt.show()
```

混淆矩阵显示模型在类别 0、1、5、7、9 和 10 上表现良好，但在类别 2、3、4 和 11 上遇到困难。这是因为这些类别在测试集中的样本非常少。

为了改进这一点，我们可以使用一种名为 SMOTE（合成少数类过采样技术）的技术。

```python
from imblearn.over_sampling import SMOTE

smote = SMOTE(random_state=42)
X_train_res, y_train_res = smote.fit_resample(X_train, y_train)
```

现在我们将使用重采样后的数据重新训练模型：

```python
model = KNeighborsClassifier()
model.fit(X_train_res, y_train_res)
y_pred_res = model.predict(X_test)
```

我们将再次评估性能：

```python
print(classification_report(y_test, y_pred_res))
print(confusion_matrix(y_test, y_pred_res))
print(accuracy_score(y_test, y_pred_res))
```

性能应该在少数类上得到提高。

