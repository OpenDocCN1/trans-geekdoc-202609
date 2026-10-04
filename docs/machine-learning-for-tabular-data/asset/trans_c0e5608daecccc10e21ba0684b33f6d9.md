

# 第2章 探索表格化数据集

判别器用于比较的原始示例的真实世界分布。如果你考虑到生成器是从纯随机噪声中构建其工作的，那么它能够看到它应该记住的数据任何实例，这确实是非常智能且令人惊讶的。这一过程对于图像和表格数据效果极佳。

VAE 由一个编码器和一个解码器组成。它们的功能是使用编码器将输入数据压缩到一个被称为“潜空间”（latent space）的状态，其中数据信息被高度压缩。随后，解码器以高保真度解码数据并重建原始数据。其核心思想是，如果压缩-解压缩过程是有效的，潜空间就会封装数据的核心分布信息，从而能够生成新数据。VAE 的架构设计使得输入被编码器捕获并通过一系列层，这些层可能包含相同数量的神经元或数量递减的神经元，最终到达一个表示潜空间的层。该层作为解码器的起点。

这些深度学习方法如何生成良好的数据，可以从像 Kaggle 这样的数据科学竞赛平台如何在比赛中使用合成数据得到证明。由于缺乏针对表格化数据的竞赛，Kaggle 最近推出了一系列基于合成数据的竞赛，这些竞赛与基于精选数据的传统竞赛毫无关系。表格游戏系列（Tabular Playground Series）在过去两年一直是 Kaggle 的一个特色，并将持续进行（https://www.kaggle.com/competitions）。

在 2.5 中，我们使用 `sdv` 包从原始德国信用风险数据集（German Credit Risk dataset）中生成额外的 10,000 个示例，该数据集由我们在上一节介绍过的。要在你的系统上安装 `sdv` 包，请使用以下 shell 命令：

```
pip install sdv
```

`sdv` 包源于 MIT 的计划，是一系列开源工具，旨在帮助个人和企业从某些原始数据生成合成数据。此类工具使用了经典的统计方法（例如可以同时复制多个变量分布的高斯共轭模型，Gaussian copulas）以及深度学习。深度学习工具基于 GAN 和 VAE。在我们的示例中，我们发现 VAE 架构可以更好地且容易地模拟手头的数据。你可以在项目的 GitHub 仓库（https://github.com/sdv-dev/sdv）上找到更多关于 `sdv` 包的信息，或者通过阅读这篇说明该方法的参考论文：Neha Patki, Roy Wedge, Kalyan Veeramachaneni, "The Synthetic Data Vault," IEEE DSAA 2016 (https://mng.bz/ga4V)。

## 2.5 生成合成数据集

```python
import pandas as pd
from sdv.metadata import SingleTableMetadata
```

从 `sdv` 导入从你的原始数据生成元数据的函数

# 寻找外部和内部数据

```python
from sdv.single_import import TVAESynthesizer

data = pd.read_csv("german_credit_data.csv", index_col=0)
data = data.reset_index()
print(data.shape)
print(data.head)
```

从 `sdv` 导入用于生成合成数据的 VAE

实例化德国信用风险数据集

```python
metadata = SingleTableMetadata()
metadata.detect_from_dataframe(data)
print(metadata.to_dict())
metadata.update_column(column_name="Saving accounts", dtype="categorical")
synthesizer = TVAESynthesizer(metadata, epochs=10_000)
synthesizer.fit(data)
synthetic_data = synthesizer.sample(num_rows=10_000)
synthetic_data.head()
```

从原始数据中检测元数据

检查每列的元数据是否已正确检测

生成包含 10,000 个示例的新合成数据集

修正“Saving accounts”列的元数据

使用原始数据拟合 VAE 模型

实例化 VAE 模型并构建结构以训练 10,000 轮

在原始数据上完成一定次数迭代所需的时间，对于 VAE 开发数据原始特征和分布的良好潜表示是必要的。一旦完成，合成数据中的示例将类似于原始数据中的样本，但如果你需要更正式的证明，必须诉诸对抗验证评估（adversarial validation evaluation），其中机器学习算法被要求区分原始数据和生成数据。其中一种机器学习算法更能检测数据中极其细微的模式；因此，在区分原始数据和生成数据时可能会产生困惑，假设生成的数据具有良好的质量。在下面的列表中，我们展示了如何对德国信用风险数据生成的合成数据设置对抗验证。

| 列表 2.6 使用对抗验证测试合成数据集 |

```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import cross_val_predict
from sklearn.metrics import roc_auc_score
```

```python
X = pd.concat([synthetic_data, data])
categorical_columns = [
"Sex", "Saving accounts",
"Checking account", "Purpose"]
X_encoded = pd.get_dummies(X, columns=categorical_columns)
X = X.drop("index", axis="columns")
y = [0] * len(synthetic_data) + [1] * len(data)
```

合并合成数据和数据

将分类特征编码为哑变量

```python
model = RandomForestClassifier()
```

|- ROC 曲线下面积（也称为曲线下面积，AUC）是一种用于评估机器学习算法在二分类问题中性能的指标。它根据分配给每个观测值的概率来区分正负样本。1 分表示完美分类器，而 0.5 分意味着模型优于随机猜测。你可以通过咨询 mlu.github.io/roc-auc/（来自机器学习仓库的教育计划）了解更多关于该指标的信息 | 分类示例是原始还是合成 | 计算分类的 AUC 分 |

在这种情况下，ROC AUC 约为 0.567，这表明合成数据与原始数据几乎不可区分。

在下一节中，我们将通过探索从 UCI 机器学习仓库和 Kaggle 数据集获取的数据来完成对表格数据的概述。之前段落中提到的许多问题将在分析数据时被发现，并实施相应的解决方案。

