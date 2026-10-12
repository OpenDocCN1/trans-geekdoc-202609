
```python
from neutralize import NeutraliseCharges
```

我们现在创建一个新的 DataFrame，包含非活性分子的 SMILES 字符串、ID 和标签：

```python
revised_decoy_df = decoy_df[["SMILES","ID","label"]].copy()
```

利用这个新 DataFrame，我们可以用分子中性形式的 SMILES 字符串替换原始的 SMILES 字符串。函数 `NeutraliseCharges` 返回两个值。第一个包含分子中性形式的 SMILES 字符串，第二个是一个布尔变量，指示分子是否被修改。因为我们只需要 SMILES 字符串，所以仅使用 `NeutraliseCharges` 返回元组的第一个元素。

```python
revised_decoy_df["SMILES"] = [NeutraliseCharges(x)[0] for x in revised_decoy_df["SMILES"]]
```

一旦替换了 SMILES 字符串，我们就可以向新 DataFrame 添加分子列并重新计算属性：

```python
PandasTools.AddMoleculeColumnToFrame(revised_decoy_df,"SMILES","Mol")
add_property_columns_to_df(revised_decoy_df)
```

接下来，我们将包含活性分子的 DataFrame 追加到包含修订后的中性分子的 DataFrame 后面：

```python
new_tmp_df = active_df.append(revised_decoy_df)
```

现在我们再次创建小提琴图，以比较形式电荷的分布（参见 图 11-4）：

```python
sns.violinplot(new_tmp_df["label"],new_tmp_df["charge"])
```

![image](img/p181-01.png)

*图 11-4：修订后非活性分子形式电荷分布的小提琴图*。

正如我们从图中所见，数据集中仅剩下少数带电荷的非活性分子。我们再次创建一个仅包含带电荷分子的 DataFrame，并检查其中还剩下多少带电荷分子：

```python
charged = revised_decoy_df[revised_decoy_df["charge"] != 0]
charged.shape[0]/revised_decoy_df.shape[0]
```

结果为 0.003。我们已将带电荷分子的比例从 16% 降低至 0.3%。因此，我们可以假设我们的数据是平衡的。

为了能在 DeepChem 中使用这些数据集，我们必须将分子作为 *csv* 文件输出，该文件需包含每个分子的 SMILES 字符串、ID、名称以及一个指示其为活性 (1) 还是非活性 (0) 分子的数字：

```python
active_df["is_active"] = [1] * active_df.shape[0]
revised_decoy_df["is_active"] = [0] * revised_decoy_df.shape[0]
combined_df = active_df.append(revised_decoy_df)[["SMILES","ID","is_active"]]
combined_df.head()
```

前五行如 表 11-2 所示。

*表 11-2：我们新建 DataFrame 的前五行*

![image](img/p182-01.png)

最后一步是将 `combined_df` 作为 *csv* 文件输出。`index=False` 可防止行号作为第一列被写入 *csv* 文件：

```python
combined_df.to_csv("dude_erk1_mk01.CSV",index=False)
```

## 训练预测模型

现在我们的数据已格式化完毕，可以用来训练图卷积模型。首先导入所需的库。虽然其中一些库已在第一节中导入，但若要开始读取 *csv* 文件，我们需要全部导入：

```python
import deepchem as dc # DeepChem 库
from deepchem.models import GraphConvModel # 图卷积
import numpy as np # NumPy 用于数值运算
import sys # 错误处理
import pandas as pd # 数据处理
import seaborn as sns # 用于绘图的 Seaborn 库
from rdkit.Chem import PandasTools # Pandas 中的化学结构
```

下一步，我们定义一个用于创建 `GraphConvModel` 的函数。在本例中，我们需要一个分类模型。因为我们稍后想在另一个数据集上应用该模型，所以应创建一个用于保存模型的目录。请根据您的文件系统调整路径 (`model_dir`)：

```python
def generate_graph_conv_model():
    batch_size = 128
    model = GraphConvModel(1, batch_size=batch_size, mode='classification', model_dir="/tmp/mk01/model_dir")
    return model
```

我们现在需要上一节创建的 *csv* 文件：

```python
dataset_file = "dude_erk2_mk01.CSV"
tasks = ["is_active"]
featurizer = dc.feat.ConvMolFeaturizer()
loader = dc.data.CSVLoader(tasks=tasks, smiles_field="SMILES", featurizer=featurizer)
dataset = loader.featurize(dataset_file, shard_size=8192)
```

现在我们可以构建模型了。我们将读取的数据集分别拆分为训练集和验证集，以便评估模型。为此我们使用 `RandomSplitter`（DeepChem 提供了多种拆分数据的方法，例如 `ScaffoldSplitter`，它根据分子的化学骨架拆分数据；以及 `ButinaSplitter`，它先对数据进行聚类，再拆分使得训练集和验证集包含不同的簇）：

```python
splitter = dc.splits.RandomSplitter()
```

通过拆分数据集，我们可以在训练集上训练模型，随后在验证集上进行检查。为了评估模型，我们需要合适的指标。在本例中，数据是不平衡的：活性分子数量少，非活性分子数量多。因此我们需要一种能处理不平衡数据的指标。马修斯相关系数 (MCC) 就是一种这样的指标：

```python
metrics = [
    dc.metrics.Metric(dc.metrics.matthews_corrcoef, np.mean, mode="classification")
]
```

为了评估模型性能，我们执行十折交叉验证，在训练数据上训练模型，随后在验证数据上验证：

```python
training_score_list = []
validation_score_list = []
transformers = []
cv_folds = 10

for i in range(0, cv_folds):
    model = generate_graph_conv_model()
    res = splitter.train_valid_test_split(dataset)
    train_dataset, valid_dataset, test_dataset = res
    model.fit(train_dataset)
    train_scores = model.evaluate(train_dataset, metrics, transformers)
    training_score_list.append(train_scores["mean-matthews_corrcoef"])
    validation_scores = model.evaluate(valid_dataset, metrics, transformers)
    validation_score_list.append(validation_scores["mean-matthews_corrcoef"])

print(training_score_list)
print(validation_score_list)
```

为了直观展示性能，我们使用箱线图（参见 图 11-5）：

```python
sns.boxplot(
    ["training"] * cv_folds + ["validation"] * cv_folds,
    training_score_list + validation_score_list
)
```

![image](img/p184-01.png)

*图 11-5：训练集和验证集得分的箱线图*。

正如预期所示，图表表明训练集上的性能优于验证集——但验证集的性能也相当不错。因此，我们可以信任我们的模型。

同样地，可视化我们模型的结果也很有帮助。为此，我们为验证数据生成预测：

```python
pred = [x.flatten() for x in model.predict(valid_dataset)]
```

为了简化处理，我们创建一个包含预测结果的 Pandas DataFrame：

```python
pred_df = pd.DataFrame(pred, columns=["neg", "pos"])
```

我们向该 DataFrame 进一步添加分子的状态（1 = 活性，0 = 非活性）和 SMILES 字符串：

```python
pred_df["active"] = [int(x) for x in valid_dataset.y]
pred_df["SMILES"] = valid_dataset.ids
```

为了确保数据合理，我们查看 DataFrame 的前几行（参见表 11-3）。

*表 11-3：包含预测结果的 DataFrame 的前几行*

![image](img/p184-02.png)

我们可以使用箱线图来比较活性和非活性分子的预测值（参见图 11-6）。

```python
sns.boxplot(pred_df.active, pred_df.pos)
```

![image](img/p185-02.png)

*图 11-6：预测分子的正类得分*。

我们的模型运行良好：我们可以清晰地看到活性（1）和非活性（0）分子之间的分离。构建预测模型时，重要的是要更仔细地检查被预测为活性的非活性分子（**假阳性**），以及被预测为非活性的活性分子（**假阴性**）。正如我们从箱线图中所见，我们的活性分子中只有一个获得了较低的正类得分。为了进行更详细的检查，我们创建一个新的 DataFrame，其中包含所有正类得分 < 0.5 的活性分子：

```python
false_negative_df = pred_df.query("active == 1 & pos < 0.5").copy()
```

为了研究这些分子的化学结构，我们使用 RDKit 中的 `PandasTools` 模块：

```python
PandasTools.AddMoleculeColumnToFrame(false_negative_df, "SMILES", "Mol")
```

新的 DataFrame 如下所示（参见图 11-7）：

```python
false_negative_df
```

![image](img/p186-01.png)

*图 11-7：假阴性预测*。

我们需要药物化学知识来解读所呈现的信息。通常，将假阴性分子的化学结构与真阳性分子的化学结构进行比较，以弄清楚为什么分子未被正确预测，这很有启发性。通常原因在于假阴性分子与真阳性分子都不相似。在这种情况下，进行额外的文献检索以增加训练数据集中分子的多样性会有所帮助。

我们采用类似的方法来研究假阳性分子，这些分子本身是非活性的，但获得了正类得分 > 0.5（参见图 11-8）。在这里，与真阳性分子的化学结构进行比较也能给我们提供线索：

```python
false_positive_df = pred_df.query("active == 0 & pos > 0.5").copy()
PandasTools.AddMoleculeColumnToFrame(false_positive_df, "SMILES", "Mol")
false_positive_df
```

![image](img/p186-02.png)

*图 11-8：一个假阳性分子*。

在训练模型期间，评估模型性能对我们很重要。因此，我们在一部分数据上训练模型，在另一部分上进行验证。现在我们已完成性能评估，想要获得最高效的模型。为此，我们使用所有数据训练模型：

```python
model.fit(dataset)
```

我们获得了 91% 的准确率。在最后一步中，我们将模型保存在之前创建的目录中，以便将其用于未来的预测：

```python
model.save()
```

### 为预测准备数据集

创建好预测模型后，我们可以将其应用于新数据。预测模型通常基于文献检索创建，然后应用于想要筛选的分子。待筛选的分子可能来自内部数据库或商业可用的数据集。作为示例，我们使用创建的预测模型，对 ZINC 数据库中 100,000 个分子的小样本进行筛选，ZINC 数据库是一个包含超过十亿种商业可用分子的集合。

进行虚拟筛选时可能存在的一个问题是分子对生物学分析产生干扰。在过去 25 年中，许多研究小组开发了规则来识别潜在的问题分子。其中一些规则以 SMILES 字符串编码，由维护 ChEMBL 数据库的同一小组收集整理。这些规则通过 Python 脚本 `rd_filters.py` 提供。我们使用 `rd_filters.py` 来识别 ZINC 数据库 100,000 个分子样本中潜在的问题分子。

脚本 `rd_filters.py` 及相关文件可在我们的 GitHub 仓库（[`github.com/deepchem/DeepLearningLifeSciences`](https://github.com/deepchem/DeepLearningLifeSciences)）中获取。

调用 `-h` 可查看脚本的可用选项和参数。

```bash
rd_filters.py -h
```

```
Usage:
rd_filters.py $ filter --in INPUT_FILE --prefix PREFIX [--rules RULES_FILE_NAME]
[--alerts ALERT_FILE_NAME][--np NUM_CORES]
rd_filters.py $ template --out TEMPLATE_FILE [--rules RULES_FILE_NAME]

Options:
--in INPUT_FILE 输入文件名
--prefix PREFIX 输出文件名前缀
--rules RULES_FILE_NAME 规则 JSON 文件名
--alerts ALERTS_FILE_NAME 结构警示文件名
--np NUM_CORES 使用的 CPU 核心数（默认为全部）
--out TEMPLATE_FILE 参数模板文件名
```

要将脚本应用于名为 `zinc_100k.smi` 的输入文件，请指定文件名和输出文件的前缀。`filter` 以过滤模式调用脚本并识别潜在的问题分子。`--prefix` 指定输出文件名以 `zinc` 为前缀。

```bash
rd_filters.py filter --in zinc_100k.smi --prefix zinc
```

```
using 24 cores
Using alerts from Inpharmatica
Wrote SMILES for molecules passing filters to zinc.smi
Wrote detailed data to zinc.CSV
68752 of 100000 passed filters 68.8%
Elapsed time 15.89 seconds
```

此输出意味着：

*   该脚本在 24 个 CPU 核心上运行。它并行地在多个 CPU 核心上运行，使用的核心数可通过 `-np` 设置。

*   该脚本使用“Inpharmatica”规则集，该规则集涵盖了广泛的化学功能性，这些功能性在生物学分析中被证明是有问题的。更多信息请参阅 `rd_filters.py` 的文档。

*   通过过滤器的 SMILES 字符串被写入名为 `zinc.smi` 的文件。我们将使用此文件作为预测模型的输入。

*   关于哪些分子触发了特定结构警示的详细信息被写入名为 `zinc.CSV` 的文件。

*   69% 的分子通过了过滥器，31% 被判定为有问题。

我们首先查看导致 31% 分子被拒绝的原因。这可以让我们了解是否需要调整某个过滤器。我们显示 `zinc.CSV` 的前几行（参见表 11-4）。

```python
import pandas as pd
df = pd.read_CSV("zinc.CSV")
df.head()
```

# 表 11-4：基于 zinc.CSV 的 DataFrame 的前几行

![image](img/p188-01.png)

该 DataFrame 有六列：

- **SMILES**：每个分子的 SMILES 字符串。

- **NAME**：输入文件中列出的分子名称。

- **FILTER**：分子被拒绝的原因，如果分子通过了过滤器则为 OK。

- **MW**：分子的分子量。默认情况下，分子量超过 500 的分子会被丢弃。

- **LogP**：分子的计算辛醇/水分配系数。默认情况下，LogP 超过 5 的分子会被剔除。

- **HBD**：氢键供体的数量。默认情况下，拥有超过 5 个供体的分子会被丢弃。

借助 Python `collections` 库中的 `Counter` 类，我们可以确定哪些过滤器导致移除了最多的分子（参见 表 11-5）：
