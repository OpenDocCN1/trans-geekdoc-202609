

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

#### 探索性数据分析

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

```csv
mpg,cylinders,displacement,horsepower,weight,acceleration,model_year,origin,car_name
18.0,8.0,307.0,130.0,3504.0,12.0,1,1,chevrolet malibu
15.0,8.0,350.0,165.0,3693.0,11.5,1,1,buick skylark 320
18.0,8.0,318.0,150.0,3436.0,11.0,1,2,plymouth satellite
16.0,8.0,304.0,150.0,3433.0,12.0,1,1,amc rebel sst
17.0,8.0,302.0,140.0,3449.0
```

在不同的情况下，你需要通过数据探索来发现信息。因此，如果我们不知道特征的特征，就应该通过初步数据探索来发现它们，这可以通过几个 pandas 命令快速完成。例如，我们可以请求前几行并立即对我们处理的数据有一个直观。我们使用 `.head(n)` 方法获取前五行：

```python
data.head(5)
```

结果显示在图 2.5 中。

| mpg | cylinders | displacement | horsepower | weight | acceleration | model_year | origin | car_name |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 18.0 | 8 | 307.0 | 130.0 | 3504.0 | 12.0 | 1 | 1 | chevrolet malibu |
| 15.0 | 8 | 350.0 | 165.0 | 3693.0 | 11.5 | 1 | 1 | buick skylark 320 |
| 18.0 | 8 | 318.0 | 150.0 | 3436.0 | 11.0 | 1 | 2 | plymouth satellite |
| 16.0 | 8 | 304.0 | 150.0 | 3433.0 | 12.0 | 1 | 1 | amc rebel sst |
| 17.0 | 8 | 302.0 | 140.0 | 3449.0 | 10.5 | 1 | 1 | ford torino |

图 2.5 来自 data.head(5) 命令的结果

