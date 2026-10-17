
```python
# 使用 LabelEncoder 编码“Gender”。Gender”在“第3列”，因此为 X[:, 2]
label_encoder = LabelEncoder()
# 以下适用于 numpy 数组，如果使用 X = dataset.loc[:, 3:]
# X 是一个 numpy 数组，所以它不是 Array。即未应用 .values
X[:, 2] = label_encoder.fit_transform(X[:, 2])
print(X)
```

```python
# 对于数据集，我们仍然可以使用“Key”进行编码
# X["Gender"] = Label_encoder.fit_transform(X["Gender"])
# 使用 OneHotEncoder 编码“Geography”。Geography”在“第2列”
```

```python
# 数据划分
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)
```

## 11.2.3 使用 XGBoost：应用模型

这里我们将通过分类器实现 XGBoost 并创建该分类器的对象。

- 我们将此对象拟合到训练集上，并且

- 我们将使用混淆矩阵评估模型性能。

- 我们还应用了 交叉验证来评估模型性能。

**导入类：使用 xgboost 模块中的 XGBClassifier（我们刚刚安装了）。**

**参数：** 当我们创建 `XGBClassifier` 对象时，我们注意到在使用它时关于它的信息非常少（c-1 或 cmd-1）。**文档非常少。** 我们只剩下可以使用的参数。

- **某些参数：** `learning_rate`（在深度学习中）。**`n_estimators`（估计器的数量，xgboost 实际上是一种带树的梯度提升算法）。** 估计器的数量其实很多，然后我们还有许多其他参数，但我们现在不会玩这些参数。

```python
XGBClassifier
Definition XGBClassifier(max_depth=3, learning_rate=0.1, n_estimators=100, eval_metric=None, objective='binary:logistic', min_child_weight=1, gamma=0, subsample=0.8, colsample_bytree=0.8, reg_alpha=0, reg_lambda=1, scale_pos_weight=1, base_score=0, seed=None)
Type: Present in xgboostmodule
class XGBClassifier(XGBobject):
```

然而，这只是本课程的介绍，但你可以在互联网上找到任何信息。

现在我们将输入任何参数，并将使用我们在 `XGBClassifier` 中使用的默认值。

- 所以我们将设置 `max_depth=3`，`n_estimators=100`（一百），其余都是没问题的，因为我们实际上有一个二分类输出。

你也可以尝试一点练习，尝试使用网格搜索参数调优（Grid Search Parameter Tuning）来寻找 `learning_rates` 和 `n_estimators` 的最优参数。这与我们在上一节中实现网格搜索的技术完全相同。

- 可以尝试通过网格搜索调优 `gamma` 参数。

将此分类器拟合到训练集：我们只需获取分类器对象并拟合训练集。与我们实现的其他分类模型完全一样。

```python
# 在训练集中拟合 XGBoost
from xgboost import XGBClassifier
cla5_XGB = XGBClassifier()
cla5_XGB.fit(X_train, y_train)
```

预测、混淆矩阵、k折交叉验证：全部来自之前的项目。只需更改分类器名称。

- 我们在测试集上进行预测

- 我们还调用了混淆矩阵。

- 最后我们应用 k 折交叉验证以获得相关的性能指标，评估我们 XGBoost 模型的性能。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_356_0.png)

该数据集包含银行客户的信息。

- 我们选择的自变量是从信用评分到预估薪资的所有自变量，因变量是离开和留下的变量。这些是银行记录的过去六个月的数据。

- 我们在数据中训练这个 XGBoost 模型，使其理解这些信息之间的相关性，例如信用评分、地理位置、年龄、预估薪资以及客户离开银行的决定，这是一个分类问题。

- XGBoost 将客户分为两类：离开的客户和留下的客户，我们的目标是对未来的客户进行一些预测，并预测他们是否将会离开。

```python
# 第3部分：预测和评估模型
# 预测
y_pred = cla5_XGB.predict(X_test)

# 通过制作混淆矩阵我们使用函数 "confusion_matrix"
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(true=y_test, y_pred=y_pred)
print("\nConfusion Matrix :\n{cm}")

# cm 的参数：True 真实值，y_pred：预测值
Accuracy_from_confusion_matrix = [cm[0][0] + cm[1][1]]/X_test.shape[0]
print("\nAccuracy = {Accuracy_from_confusion_matrix[0]}%")
```

```python
# k折交叉验证
from sklearn.model_selection import cross_val_score
accuracies = cross_val_score(estimator=cla5_XGB, X=X_train, y=y_train, cv=10)
mean_acc = accuracies.mean()
std_acc = accuracies.std()

print("\nAccuracy using k-fold-cross-validation: {:.2f}%".format(mean_acc*100))
print("\nStandard Deviation from k-fold-cross-validation: {:.2f}%".format(std_acc*100))
```

结果：我们有许多正确的预测。我们对 1491 个未离开银行的客户预测正确，218 个离开银行的客户也预测正确。

```
Confusion Matrix :
[1491 104]
[187 218]

Accuracy = 0.8545%
Accuracy using k-fold-cross-validation: 85.29%
Standard Deviation from k-fold-cross-validation: 1.16%
```

然后我们有 104 + 187 次错误的预测。准确率为 (1709/2000) = 0.8545，即 85.5% 的准确率。

我们知道这并不是最相关的指标。通过 K 折交叉验证我们得到的相关准确率是 85.29%。

我们还得到了 1.16% 的偏差。我们的模型准确率范围为 84.13% 到 86.45%（85.29%+1.16%）。

此外，提高准确率非常困难，因为正如之前之前所使用的，它受限于问题本身。

# 所有代码（练习版）

```python
# 使用 XGBoost 代替 ANN

# 导入库
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# 第1部分：数据预处理
# 数据提取
dat = pd.read_csv("Churn_Modelling.csv")
x = dataset.iloc[:, 3:-1].values # 也可以用
X = dataset.iloc[:, 3:13].values # 从索引 3 开始的所有列，排除索引为 13 的列
y = dataset.iloc[:, 13].values # 最后一列

# 编码分类数据
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
from sklearn.compose import ColumnTransformer
# label_encoder = LabelEncoder(). "Gender" 在“第 3 列”，因此 X[:, 2] =
# 以下代码适用于 numpy 数组，如果使用了 "X" = dataset.iloc[:, 3:13]
X = np.array(X) # 如果 X 不是数组，则需要此操作。即未应用 "values"
X[:, 2] = label_encoder.fit_transform(X[:, 2])
print(X)

# 对于数据集，我们可以使用列 "Key" 进行编码
X("Gender") = label_encoder.fit_transform(X("Gender"))

# OneHotEncoder。"Geography" 在“第 2 列”，因此为 [1]
ct = ColumnTransformer(transformers=["Encoding", OneHotEncoder(), [1]], remainder="passthrough") # 剩余列保持不变
X = ct.fit_transform(X)
X = np.array(X) # 将此输出转换为 Numpy 数组
print(X)
X = X[:, 1:] # 排除索引 0 列以避免虚拟变量陷阱

# 数据划分
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)
```

```python
# 第2部分：在训练集上拟合 XGBoost-
from xgboost import XGBClassifier
clasifire_XGB = XGBClassifier()
clasifire_XGB.fit(X_train, y_train)
```

```python
# 第3部分：预测与模型评估
y_pred = clasifire_XGB.predict(X_test)

# 混淆矩阵
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_true=y_test, y_pred=y_pred)
print(f"Confusion Matrix :\n{cm}")
# cm 的参数：y_true: 真实值，y_pred: 预测值
accuracy_By_Confusion_matrix = (cm[0][0] + cm[1][1]) / X_test.shape[0]
print(f"\nAccuracy: {accuracy_By_Confusion_matrix}%")
```

```python
# K 折交叉验证
from sklearn.model_selection import cross_val_score
accuracies = cross_val_score(estimator=clasifire_XGB, X=X_train, y=y_train, cv=10)
mean_accu = accuracies.mean()
std_accu = accuracies.std()

print(f"\nAccuracy using k-fold-cross-validation: {:.2f}%".format(mean_accu*100))
print(f"\nStandard Deviation from k-fold-cross-validation: {:.2f}%".format(std_accu*100))
# python prctc_XGBoost.
```

# 第11 章：第3部分

## 深度学习

ANN: 使用 K 折交叉验证评估性能

& 超参数调优

K 折 CV（或 K 折交叉验证），keras-wrapper，Dropout 正则化

### 11.3.1 ANN 中的 K 折交叉验证

- ANN 中的 K 折 CV：在上一节中，我们讨论了 K 折 CV 并将其应用于核-SVM 和 XGBoost。在本节中，我们将 K 折 CV 应用于 ANN，这是我们的第一个深度学习算法。

- 在第 8 章（ANN）中，我们训练了两次人工神经网络，并注意到准确率是不同的。我们想要应用 K 折 CV 来准确地评估模型性能。

- **方差权衡 (Variance Tradeoff)**：我们正尝试训练一个不仅准确，而且在多次训练时其准确率的差不应有太大的波动。

- 之前我们训练了 ANN 并获得了两个不同的准确率：85% 和 84%。当这两个其中一个时，我们应该取哪一个来**评估我们的性能**？

- 我们将数据分为训练集和测试集。这导致了方差问题：当我们获得测试集上的准确率时，如果再次运行模型并在另一个测试集上进行测试，可能会得到非常不同的准确率。

因此，仅根据一个测试集来判断我们的模型性能并不是评估模型性能最相关的方法。

这就是为什么我们将训练集（或整个数据集）分为等等的 k 组，并对 (k-1) 个训练组和 1 个测试组的 k 种组合进行 k 次迭代。最后我们得到一个准确率向量，从中计算平均准确率和标准差。这为我们提供了模型性能的更好评估。

在大多数情况下，K=10，我们在 9 折上训练模型，并在剩余的1 折上进行测试。10 折意味着 10 种不同的“9 折训练”和“1 折测试”的组合。

- 这意味着我们可以在训练集和测试集的组合上训练和测试模型，观察准确率之间有多大的差异。

- 通过取准确率差异的平均值并计算标准差，这将让我们对模型性能有一个更清晰的认识。

我们将性能分为四类：

i. 高准确率 - 小方差；

ii. 高准确率 - 高方差；

iii. 低准确率 - 小方差；

iv. 低准确率 - 高方差

### 11.3.2 在 ANN 中实现 K 折交叉验证

我们在数据预处理阶段之后实现 K 折 CV。

- Keras wrapper：我们使用 Keras-TensorFlow 实现了我们的 ANN 模型。而 K 折 CV 属于 Scikit-learn。

Keras wrapper 将 Keras 和 Scikit 结合在一起。Keras wrapper 模块属于 Keras。它会在 Keras 中封装来自 Scikit-learn 的 K 折交叉验证。

```python
from keras.wrappers import KerasClassifier
from sklearn.model_selection import cross_val_score
```

![img/092657a359a0b6d8f92d657a359a0b6d](img/092657a359a0b6d8f92d657a359a0b6d)

```python
def build_ANN():
    # 初始化 ANN
    ANN = Sequential()

    # “输入层” & “第一隐藏层”
    ANN.add(Dense(6, activation="relu", input_dim=11))

    # “第二隐藏层”
    ANN.add(Dense(6, activation="relu"))

    # “输出层”
    ANN.add(Dense(1, activation="sigmoid"))

    # 编译 ANN
    ANN.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])
    return ANN
```

我们在数据预处理阶段使用 KerasClassifier。K 折 CV 属于 Scikit-learn。

Keras wrapper 将 Keras 和 Scikit 结合在一起。Keras wrapper 模块属于 Keras。它会在 Keras 中封装来自 Scikit-learn 的 K 折交叉验证。

```python
from keras.wrappers import KerasClassifier
from sklearn.model_selection import cross_val_score
```

![img/092657a359a0b6d8f92d657a359a0b6d](img/092657a359a0b6d8f92d657a359a0b6d)

`cross_val_score()`; 正如我们之前做的那样，我们创建了一个准确率向量变量 `accuracies`，并将全局分类器变量 `ann_classifier_for_eval` 设置为估计器。

```python
accuracies = cross_val_score(estimator=ann_classifier_for_eval, x=X_train, y=y_train, cv=10, n_jobs=None)
```

所有操作与我们之前相同。

`n_jobs`（在深度学习中非常重要）：注意，这里 `n_jobs = -1` 对于 ANN 和所有深度学习技术至关重要。因为所有深度学习技术都是并行计算过程，这会让它们的运行速度变慢。此外，我们使用了 K 折交叉验证，这会让模型变慢 K 倍，模型实际上运行了 K 次，执行时间也增加了 K 倍。

因此，为了利用 CPU 的全部容量进行更快的计算，由于这个原因，我们对所有深度学习技术使用 `n_jobs = -1`（在这里如果我们需要在电脑上执行其他任务，则使用 `n_jobs=0`）。
