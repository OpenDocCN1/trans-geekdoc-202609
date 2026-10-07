
X = df.drop("target", axis=1, inplace=False)
y = df["target"]
from sklearn.model_selection import train_test_split

```python
XTrain, XTest, yTrain, yTest = train_test_split(X, y, test_size=0.1,
random_state=42)
print("Shape of Training Data:", XTrain.shape)
print("\nDistribution of Target Variable in Training Dataset\n", yTrain.value_counts())
```

训练数据形状形状: (137, 19)

### 训练数据集中的目标变量分布

| Target | 计数 |
| :--- | :--- |
| 2 | 109 |
| 1 | 28 |

Name: target, dtype: int64

由于连续数据列的范围很大，我们将对数据进行标准化，使得所有数据处于相同的范围内。参考第3章K-最近邻算法中关于 Standard Scaler 的讨论：

from sklearn.preprocessing import StandardScaler

```python
columns_to_scale = [1, 15, 16, 17, 18, 19]

sc = StandardScaler()
arrTrainScaled = sc.fit_transform(XTrain[columns_to_scale])
arrTrainScaled[:5]
array([[ 0.06306600, -0.84976737, -0.21832346, -0.01053376, -1.83085539,
        1.05246962],
[ 0.46680671, 1.41670315, -0.63177997, -1.93470076, -1.71650518,
        1.05246962],
[ 1.274288 , -0.03485287 , -0.43593215, -1.93470076, 0.68484962,
        -0.95014619],
[ 0.46680671, -0.37032169, -0.70794301, 0.63085524, 0.28462352,
        1.05246962]])
```

[-0.58291898, -1.54714292, -0.69706258, 0.31016074, 0.85637457,
-0.950146199]]

在标准化数据后，我们将移除原始列（已标准化的列）并添加包含标准化后数据的列。

```python
# 删除已标准化的列并添加标准化后的值列
XTrain = XTrain.drop(columns_to_scale, axis=1, inplace=False)
XTrain = pd.concat([XTrain.reset_index(drop=True),
pd.DataFrame(arrTrainScaled,
columns=columns_to_scale).reset_index(drop=True)])
```

现在数据已经准备好用于创建模型，我们将构建逻辑回归模型：

```python
from sklearn.linear_model import LogisticRegression

l = LogisticRegression(solver="liblinear",
class_weight="balanced",
max_iter=10000,
random_state=42)

l.fit(XTrain, yTrain)
LogisticRegression(class_weight="balanced", max_iter=10000, random_
state=42,
solver="liblinear")
```

用于创建 LogisticRegression 类实例时使用的参数：

- 参数 `solver` 设置了用于获取系数最佳值的算法。这里使用的 `“liblinear` 求解器最适用于小型数据集。
- 参数 `class_weight = “balanced”` 给数据点较少的类别赋予更高的权重。通过这种方式，我们解决了数据集不平衡的问题。

现在逻辑回归模型已准备就绪，我们可以使用模型进行预测，并检查模型在训练数据集上的准确率。我们还创建了混淆矩阵来检查模型在哪些方面表现良好，在哪些方面表现佳。

# 124 机器学习分类算法大师

from sklearn.metrics import confusion_matrix, accuracy_score,
ConfusionMatrixDisplay

yTrain = lr.predict(XTrain)

```python
print("Accuracy = %7.5f%% %n" (accuracy_score(yTrain, yTrainPred) * 100, "%"))

cm = confusion_matrix(yTrain, yTrainPred)
ConfusionMatrixDisplay(cm, display_labels=lr.classes_).plot()
Accuracy = 86.86131%
<sklearn.metrics._plot.confusion_matrix.ConfusionMatrixDisplay at 0x7f991175b70>
```

![](img/11af2c4c7dddfed06ed008516c0c6dfb_143_0.png)

**图 4.12：** 在训练数据集上进行预测的混淆矩阵

因此，训练数据集的准确率为 86.86131%。
