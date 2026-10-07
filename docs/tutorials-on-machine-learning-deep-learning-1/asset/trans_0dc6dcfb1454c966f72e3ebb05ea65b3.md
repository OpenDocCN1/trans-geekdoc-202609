

# 10.9 逻辑回归中的 LDA：模型构建与结果可视化

LDA 并不是另一种特征提取技术。我们考虑了来自 PCA 的 `wine.csv` 数据。我们将像在 PCA 中做的那样，提取新的变量来降低我们数据的维度。

- PCA 特征提取技术通过提取解释大部分变异的变量来降低问题维的维度。
- LDA 则完全不同。在这里，我们正在提取一些新的独立变量（从数据集的 $n$ 个独立变量中提取 $p \le n$ 个新的独立变量），这些变量将分离因变量的类别。
- 因变量（DV）的存在使得 LDA 被视为一种**有监督模型**。
- LDA 是一种有监督特征提取方法：由于 LDA 考虑了因变量的类别，LDA 将提取能够分离类别的独立变量，而这些类别与因变量相关，即 LDA 配合因变量进行特征提取。
- 这使得 LDA 成为一个有监督的降维模型（另一方面，PCA 是无监督的，因为我们没有考虑因变量）。

**问题描述：** 我们将处理同一个业务问题“葡萄酒化学客户细分问题”，并将使用 LDA 来超过 PCA 所获得的 97% 准确率，我们将看看是否能获得 100% 的完美准确率（无错误细分）。

- 我们将采用上一节中编写的代码，并进行几处改动。

**数据预处理：** 这与 PCA 中相同，因为我们只需要一个训练集和一个测试集，并在它们上应用特征筛选。

- 我们可以直接创建，无需任何更改。
- 我们将使用原始数据集，包含关于葡萄酒的所有化学信息以及包含已聚类的客户细分的因变量。
- 我们的训练集已经过缩放，包含了 13 个独立变量。

**导入 LDA：** 我们的模型分类不需要非是逻辑回归，可以是 SVM 或决策树分类。

- 但在将分类模型拟合到训练集之前，我们需要应用 LDA。

```
from sklearn.discriminant_analysis import LinearDiscriminantAnalysis
dcpose_lda = LinearDiscriminantAnalysis(n_components=2)
```

**线性判别器：** 在 PCA 中，我们把提取的特征称为主成分。在 LDA 中，提取的特征是线性判别器。

- n_components：我们指定的组件数量 $i$ 就是线性判别器的数量。
- 我们不需要构建 `explained_variance` 层，因为我们不是在寻找解释变异的独立变量或任何类型的可观测向量。我们将直接取 `n_components = 2`。

不需要 `explained_variance`，因为我们不是在寻找解释大部分变异的独立变量。我们现在寻找的是能够分离因变量最多类别的独立变量（已经有三个类别细分）。

- 我们的目标是可视化训练结果和测试集结果。我们已经准备使用 2 个线性判别器就绪了。由于这个原因，我们直接选择 `n_components = 2`。

**构建 LDA 模型：** LDA 也是一种有监督技术，我们需要同时对独立变量（特征矩阵）和因变量向量使用 `fit_method`。

- 注意，对于训练集我们使用了 `fit_transform(X_train, y_train)`，但对于测试集只使用了独立变量（特征矩阵） `transform(X_test)`。我们将通过拟合测试数据来预测因变量。

```
X_train = dcPose_lda.transform(X_train, y_train)
X_test = dcPose_lda.transform(X_test)
```

`fit_transform` 方法拟合训练集中的对象 `(X_train, y_train)`，并同时提取 2 个线性判别器，使得 `X_train` 变成一个包含两个新特征的矩阵（从13个特征中）。

我们在测试集上使用 `transform`，使得 `X_test` 变成一个包含2 个线性判别器的特征矩阵。

我们没有在 `transform` 中包含 `y_test`，`fit_transform` 中的 `y_train` 仅用于构建/拟合 LDA 对象以训练 LDA 模型。

```
# 应用 LDA
from sklearn.discriminant_analysis import LinearDiscriminantAnalysis
dcPose_lda = LinearDiscriminantAnalysis(components=2)
# 注意：在 fit_transform 中独立和依赖变量都是：X_train, y_train
X_train = dcPose_lda.transform(X_train, y_train)
X_test = dcPose_lda.transform(X_test)
# explained_variance = dcPose_lda.explained_variance_ratio_
```

注意 LDA 是一个有监督模型，它需要因变量，因此 `X_train` 和 `y_train` 都被使用了，因为我们正在寻找分离因变量中最不同的类别。
这就是无监督 PCA 和有监督模型 LDA 之间的区别。

要构建/拟合逻辑模型，我们不需要更改任何，只需修改标签：
plt.xlabel('LDA_1')
plt.ylabel('LDA_2')

混淆矩阵：LDA 正在尝试分离尽可能类别，我们预期类别将被完美分离，因此如果这样做的话……

