

# 表 11-4：基于 zinc.CSV 的 DataFrame 的前几行

![image](Images/p188-01.png)

该 DataFrame 有六列：

- **SMILES**：每个分子的 SMILES 字符串。
- **NAME**：输入文件中列出的分子名称。
- **FILTER**：分子被拒绝的原因，如果分子通过了过滤器则为 OK。
- **MW**：分子的分子量。默认情况下，分子量超过 500 的分子会被丢弃。
- **LogP**：分子的计算辛醇/水分配系数。默认情况下，LogP 超过 5 的分子会被剔除。
- **HBD**：氢键供体的数量。默认情况下，拥有超过 5 个供体的分子会被丢弃。

借助 Python `collections` 库中的 `Counter` 类，我们可以确定哪些过滤器导致移除了最多的分子（参见 [表 11-5](#Chapter11_9783960103516.xhtml#ch11tab5)）：

```python
from collections import Counter

count_list = list(Counter(df.FILTER).items())
count_df = pd.DataFrame(count_list, columns=["Rule", "Count"])
count_df.sort_values("Count", inplace=True, ascending=False)
count_df.head()
```

## 表 11-5：使用最频繁的五个过滤器

| | **Rule** | **Count** |
|---|---|---|
| 1 | OK | 69156 |
| 6 | Filter41_12_dicarbonyl > O | 19330 |
| 0 | Filter82_pyridinium > O | 7761 |
| 10 | Filter93_acetyl_urea > O | 1541 |
| 11 | Filter78_bicyclic_lmide > O | 825 |

表中标记为 OK 的第一行表示通过所有过滤器的分子数量。这适用于我们输入的 69,156 个分子。大多数分子（19,330 个）因含有 1,2-二羰基而被剔除。此类分子可与丝氨酸和半胱氨酸等蛋白质残基反应并形成共价键。我们可以通过在 `filter_collection.CSV` 文件（它是 `rd_filters.py` 的输出）中搜索字符串 `Filter41_12_dicarbonyl` 来找到识别这些分子的 SMARTS 模式。该 SMARTS 模式为 `*C(=O)C(=O)*`，含义如下：

- 任意原子，连接至
- 羰基碳（C(=O)），连接至
- 羰基碳（C(=O)），连接至
- 任意原子

为确保一切按预期工作，我们来查看一下数据。为此，我们使用 RDKit 函数 `MolsToGridImage()` 的 `highlightAtomLists` 选项来高亮显示 1,2-二酮官能团（参见 [图 11-9](#Chapter11_9783960103516.xhtml#abb11-9)）：

```python
from rdkit import Chem
from rdkit.Chem import Draw

mol_list = [Chem.MolFromSmiles(x) for x in smiles_list]
dicarbonyl = Chem.MolFromSmarts('*C(=O)C(=O)*')
match_list = [mol.GetSubstructMatch(dicarbonyl) for mol in mol_list]

Draw.MolsToGridImage(mol_list,
                     highlightAtomLists=match_list,
                     molsPerRow=5)
```

正如我们在图中所见，这些分子确实含有二酮基团。以此方式，我们也可以评估其他过滤器。不过，我们对过滤结果感到满意，接下来转向应用我们的模型。我们已从用于虚拟筛选的数据集中移除了有问题的分子。剩余的分子位于文件 `zinc.smi` 中，将在本练习的下一步中使用。

![image](Images/p190-01.png)

**图 11-9：含有 1,2-二酮基团的分子**。

# 应用预测模型

我们创建的 `GraphConvModel` 现在可用于筛选分子。应用模型分几个步骤进行：

1.  从磁盘加载模型。
2.  创建特征化器。
3.  读取并生成要通过模型的分子的特征。
4.  检查预测分数。
5.  检查得分最高的分子的化学结构。
6.  对选定的分子进行聚类。
7.  将每个簇中选定的分子输出到 `csv` 文件。

首先导入所需的库：

```python
import deepchem as dc # DeepChem 库
import pandas as pd # 用于数据处理的 Pandas
from rdkit.Chem import PandasTools, Draw # Pandas 中的化学功能
from rdkit import DataStructs # 用于处理指纹
from rdkit.ML.Cluster import Butina # 分子聚类
from rdkit.Chem import rdMolDescriptors as rdmd # 描述符
import seaborn as sns # 图形绘制
```

然后加载我们创建的模型：

```python
model = dc.models.TensorGraph.load_from_dir("/tmp/mk01/model_dir")
```

为了从模型生成预测，我们首先必须生成想要用于预测的分子的特征。为此，我们实例化一个 DeepChem `ConvMolFeaturizer`：

```python
featurizer = dc.feat.ConvMolFeaturizer()
```

为了生成分子特征，我们必须将 SMILES 文件转换为 `csv` 文件。创建 DeepChem 特征化器需要一列活性状态。我们添加这样一列并创建 `csv` 文件：

```python
df = pd.read_CSV("zinc.smi", sep=" ", header=None)
df.columns = ["SMILES", "Name"]
rows, cols = df.shape

# 添加一个虚拟列以满足特征化器要求
df["Val"] = [0] * rows
```

我们再次显示 DataFrame 的前几行（参见 [表 11-6](#Chapter11_9783960103516.xhtml#ch11tab6)），以确保一切正确：

```python
df.head()
```

## 表 11-6：创建的 DataFrame 的前几行

![image](Images/p192-01.png)

请注意，`Val` 列只是一个占位符，用于满足 DeepChem 特征化器的要求。由于 DataFrame 看起来不错，我们将其输出到 `csv` 文件，该文件将作为 DeepChem 的输入。我们使用 `index=False` 以防止 Pandas 将行号作为第一列输出：

```python
infile_name = "zinc_filtered.CSV"
df.to_CSV(infile_name, index=False)
```

借助 DeepChem，我们可以用加载器读取此 `csv` 文件并生成我们要预测的分子的特征：

```python
loader = dc.data.CSVLoader(tasks=['Val'],
                           smiles_field="SMILES",
                           featurizer=featurizer)
dataset = loader.featurize(infile_name, shard_size=8192)
```

现在可以使用这些分子进行预测：

```python
pred = model.predict(dataset)
```

为简化操作，我们为预测结果创建一个 Pandas DataFrame：

```python
pred_df = pd.DataFrame([x.flatten() for x in pred],
                       columns=["Neg", "Pos"])
```

Seaborn 库中的分布图提供了分数分布的概览。遗憾的是，虚拟筛选中没有明确的规则规定分子从多少分以上视为活性。最佳策略通常是检查分数分布并选择得分最高的分子。如果我们看 [图 11-10](#Chapter11_9783960103516.xhtml#abb11-10)，会发现只有少数分子的分数超过 0.3。我们将此值作为可能值得进一步实验研究的分子的初步截断值。

我们可以将带有分数的 DataFrame 与带有 SMILES 字符串的 DataFrame 合并。这使我们能够查看得分最高的分子的化学结构：

```python
combo_df = df.join(pred_df, how="outer")
combo_df.sort_values("Pos", inplace=True, ascending=False)
```

正如您已经看到的，通过添加分子列，我们可以检查命中分子的化学结构（参见 [图 11-11](#Chapter11_9783960103516.xhtml#abb11-11)）。

![image](Images/p193-01.png)

**图 11-10：预测分子分数的分布图**。

![image](Images/p193-02.png)

