
例如，在 Google 搜索引擎上搜索“信用评分”会在浏览器左侧打开一个面板，列出一系列可能满足你查询的数据集。你可以根据数据的最新性、格式、许可（如果你想对数据进行商业用途则需要处理）、成本和感兴趣类别对结果进行过滤。在右侧面板上，会出现所选数据集的关键特征描述，并有一个允许你访问存储和记录数据的原始存储库的链接。要下载数据，请遵循指向的每个落地页上的说明。

据我们所知，Google 数据集搜索是寻找你需要或正在寻找的数据的最佳工具。此外，我们想指出 Google 通过 Kaggle 提供的另一个用于数据科学竞赛的资源，Kaggle 在 2017 年被 Google 收。

Kaggle 是一个数据科学家可以在此参加比赛、学习和共享数据集的平台。Kaggle 是数据科学家社区，他们可以共享自己的代码、笔记本和数据集。Kaggle 也是公司举办比赛和寻找人才的平台。

Kaggle 是为你的项目寻找高质量数据集的好地方。Kaggle 上有成千上万的数据集可用，涵盖了金融、医疗、体育等多个领域。其中许多数据集是免费使用的。

Kaggle 也是学习数据科学和机器学习的好地方。Kaggle 上有很多免费的教程和课程，可以帮助你提高技能。你还可以参加比赛来测试你的技能并赢得奖励。

Kaggle 是一个很好的社区，你可以在那里与其他数据科学家联系并分享想法。你可以加入讨论、提问并获得他人的帮助。Kaggle 也是展示你的工作并被雇主关注的好地方。

## 德国信用风险

信用分类

| 数据 | 代码 (83) | 讨论 (10) |
| :--- | :--- | :--- |
| 新笔记本 | | |
| 书签 | | |
| 复制 API 命令 | | |
| 社交分享 | | |
| 报告问题 | | |

**图 2.4 Kaggle 上德国信用风险页面的选项（右侧菜单）。可以从上到下的菜单中通过 API 命令轻松下载整个数据集，如图所示。**

```
kaggle datasets download -d uciml/german-credit
```

## 2.8.3 合成数据

在已经成功获取了一些数据集但需要增加表格数据的场景下，我们提到了合成数据生成，它不会从零创建任何数据，但可以有效率增加和改进你现有的数据集，使得使用需要更多示例的机器学习和深度学习模型变得可行。合成数据生成是一种生成式 AI 应用，也是一个不断增长的领域，因为它

- 通过增加可用表格示例的数量来克服数据稀缺性
- 通过增强数据的部分来提供数据多样性，例如不平衡分类问题中的少数类情况
- 生成边缘情况（edge cases），以便为你提供你不经常遇到的数据示例，你可以用它们来测试你设计的系统
- 保护隐私，因为它有助于生成具有原始数据特征但没有隐私问题的表格数据，所有代表的数据都是虚构的

在最近，数据生成已经有了飞跃，迈向了生成对抗网络（GANs）和变分自动编码器（VAEs）的首次生成实验，这两种深度学习架构在几年前是生成领域的先锋。

GAN 是 Ian Goodfellow 及其同事在 2014 年引入的。它们由两个深度网络——即生成器和判别器组成，同时训练，并通过挑战判别器去猜测生成器的作品对比原始示例来使它们互动。尽管这是一个这是一个无监督过程。在足够的时间和计算条件下，生成器和判别器之间的持续比较将引导生成器模拟

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

## 寻找外部和内部数据

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

## 探索性数据分析

仅通过特征的图形化表示及其与其他特征的关系，就可以告诉你该如何处理数据。通常，首先通过使用描述性统计和图表来检查每一个特征，这被称为单变量分析法。然后检查特征之间的相互关系，这被称为双变量分析法。最后，你尝试使用多变量技术和降维技术（如 t-SNE 和 UMAP）来一览所有特征。

在这一阶段，在将数据组装成表格格式之后，EDA 可以完成以下操作：

- 告知你数据的特征，例如数值型、序型、分类特征。
- 让你对每个特征的值及其分布情况有一个直观的。这在处理对尺度敏感神经网络时特别有用。
- 告诉你是否存在缺失值，因为神经网络和某些机器学习算法在存在缺失值时会被认为失效。
- 定位离群值和可以聚合的聚类。

我们将展示如何使用简单的 pandas 命令来实现此类探索，因为分析师的推理比自动化推理更有效。然而，如果需要探索的特征数量巨大且你需要节省时间，你也可以使用自动探索工具。稍后，你可以将自动 EDA 与特定数据集成。在自动 EDA 的开源包中，有几个值得向你推荐的，它们都易于学习和使用：

- AutoViz (https://github.com/AutoML/AutoViz)
- Sweetviz (https://github.com/ydata/sweetviz)
- Pandas Profiling (https://github.com/ydata/profiling)

在接下来的章节中，我们将重温 EDA，以完成根据你想要应用于数据预测目的的技术（机器学习或深度学习）而可能需要的内容。

### 2.9.1 加载 Auto MPG 数据集

现在，作为一个简单的 EDA 如何为进一步处理数据提供思路，并在适配你想要使用的模型时采取必要步骤的示例，我们采用 Auto MPG Set，这是一个在 UCI 机器学习仓库（https://archive.ics.uci.edu/ml/machine-learning-databases/auto-mpg/）免费提供的数据。该数据集由 Ernesto Ribeiro 和 David Hornik 组装，源自卡内基梅梅隆大学维护的 StatLib 库。此前，它曾出现在 1983 年美国统计协会展览（https://archive.ics.uci.edu/ml/datasets/autompg）以及 Ross Quinlan 的作品中。Ross Quinlan 是决策树算法开发的主要贡献者，C4.5 和 ID3 算法的创建者。他在1993 年的论文“Combining Instance-Based and Model-Based Learning”（https://archive.ics.uci.edu/ml/machine-learning-databases/auto-mpg/）中引用了该数据集，这是机器学习回归问题的一篇里程碑论文。对于我们的目的来说，这是一个简单且易管理的示例，因为它的特征集以及在 mpg 和 horsepower 特征中有一些需要处理的缺失数据。

以下是数据集中可用特征的列表：

- mpg: 连续型
- cylinders: 离型
- displacement: 连续型
- horsepower: 连续型
- weight: 连续型
- acceleration: 连续型
- model year: 离散型
- origin: 离散型
- car name: 字符串（每个示例唯一，可以作为 pandas DataFrame 中的索引）

在我们的示例中，列表很短，但在大多数复杂的表格数据集中，可用特征可能几十页。

为了上传我们的示例数据集，我们参考以下列表，它将连接到 UCI 仓库并将数据导入到 pandas DataFrame 中。

#### 列表 2.7 从 UCI 仓库下载 Auto MPG Set

| StringIO 读取和写入内存中的缓冲区。 | Requests 是一个 HTTP 库，可以帮助你从网络恢复数据。 |
| :--- | :--- |
| from io import StringIO | import pandas as pd |

```python
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/auto-mpg/"
data = "auto-mpg.data-original"
columns = ["mpg","cylinders","displacement","horsepower","weight","acceleration","model_year","origin","car_name"]
colcspecs = [(0, 4), (6, 9), (12, 17), (23, 28), (34, 39), (45, 49), (52, 55), (57, 59), (61, 66)]
data_ingestion = StringIO
```

根据 UCI 机器学习仓库的文档，固定宽数据需要为每个特征提供其在输入中的起始和结束位置。

## 探索性数据分析

```python
requests.get(url + data).text
data = pd.read_fwf(data_ingestion, colspec=colcspecs, names=columns)
```

数据集通过 `requests.get()` 从网络读取，然后转换为字符串缓冲区。`pd.read_fwf` 将固定宽格式的行表读取到 DataFrame。

Auto MPG 数据存储在固定宽文件中，其中值位于同一行，用特定数量的空格或制表符分隔。行尾的回车符标志着文件的结束。以下是 request 库从 UCI 机器学习仓库返回的文本文件样本：

```text
18.0   8.0 307.0      130.0 3504.0  12.0     1  1  chevrolet malibu
15.0   8.0 350.0      165.0 3693.0  11.5     1  1  buick skylark 320
18.0   8.0 318.0      150.0 3436.0  11.0     1  2  plymouth satellite
16.0   8.0 304.0      150.0 3433.0  12.0     1  1  amc rebel sst
17.0   8.0 302.0      140.0 3449.0
```

由于固定宽数据需要提供每个特征的起始和结束位置，这解释了为什么我们必须使用固定宽读取器。如果数据以 CSV 格式存储，看起来将如下：

```csv
mpg,cylinders,displacement,horsepower,weight,acceleration,model_year,origin,car_name
18.0,8.0,307.0,130.0,3504.0,12.0,1,1,chevrolet malibu
15.0,8.0,350.0,165.0,3693.0,11.5,1,1,buick skylark 320
18.0,8.0,318.0,150.0,3436.0,11.0,1,2,plymouth satellite
16.0,8.0,304.0,150.0,3433.0,12.0,1,1,amc rebel sst
17.0,8.0,302.0,140.0,3449.0
```

由于固定宽数据需要提供每个特征的起始和结束位置，这解释了为什么我们必须使用固定宽读取器。如果数据以 CSV 格式存储，看起来将如下：
