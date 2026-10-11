
在本章中，我们将通过一个用于 LBVS（基于配体的虚拟筛选）的虚拟筛选工作流的实际示例来引导您。我们将讨论运行所需的代码，以及分析过程中决策背后的思维过程。我们将使用已知能与特定蛋白结合的分子，以及假定不结合的分子，来训练一个卷积神经网络，旨在识别能与该蛋白结合的新分子。

### 准备数据集

首先，我们创建一个图卷积模型，用于预测分子是否抑制蛋白 ERK2。该蛋白也称为原癌基因激活的蛋白激酶 1 或 MAPK1，在调节细胞生长的信号通路中发挥着重要作用。ERK2 参与多种癌症的发生，目前 ERK2 抑制剂正在临床试验中作为非小细胞肺癌和黑色素瘤的潜在疗法进行测试。

我们的模型应能区分 ERK2 活性物质（active）和非活性物质（decoy）。活性和非活性分子源自 DUD-E 数据库（*[http://dud.docking.org/](http://dud.docking.org/)*），该数据库可用于测试预测模型。在实践中，我们会从科学文献或像欧洲生物信息学研究所（EBI）的 ChEMBL 数据库（*[https://www.ebi.ac.uk/chembl/](https://www.ebi.ac.uk/chembl/)*）这样的数据库中获取活性和非活性分子。为了获得最佳模型，我们希望非活性分子具有与活性分子相似的性质。假设非活性分子的重量低于活性分子，那么我们的模型很可能只会学会区分低重量分子和高重量分子。这样的模型在实践中效用非常有限。

为了更好地理解数据，我们来看看活性和非活性分子的一些计算性质。为了创建一个可靠的模型，我们必须确保这两组分子的性质相似。

首先导入所需的库：

```
from rdkit import Chem # 具有化学功能的 RDKit 库
from rdkit.Chem import Draw # 绘制化学结构
import pandas as pd # 处理数据
from rdkit.Chem import PandasTools # 处理化学数据
from rdkit.Chem import Descriptors # 计算分子描述符
from rdkit.Chem import rdmolops # 更多分子性质
import seaborn as sns # 创建图表
```

在本示例中，分子以 SMILES 字符串表示。有关 SMILES 的更多信息，请参见[第 4 章](#Chapter04_9783960103516.xhtml#ch4)。我们将一个 SMILES 文件读入 Pandas DataFrame，并向 DataFrame 添加一个 RDKit 分子。虽然 SMILES 文件技术上不是 *csv* 文件，但只要指定分隔符（在本例中为空格），就可以使用 Pandas 函数 `read_CSV()` 读取它：

```
active_df = pd.read_CSV("mk01/actives_final.ism",header=None,sep=" ")
active_rows,active_cols = active_df.shape
active_df.columns = ["SMILES","ID","ChEMBL_ID"]
active_df["label"] = ["Active"]*active_rows
PandasTools.AddMoleculeColumnToFrame(active_df,"SMILES","Mol")
```

接下来，我们定义一个函数，用于将计算出的性质添加到 DataFrame 中：

```
def add_property_columns_to_df(df_in):
    df_in["mw"] = [Descriptors.MolWt(mol) for mol in df_in.Mol]
    df_in["logP"] = [Descriptors.MolLogP(mol) for mol in df_in.Mol]
    df_in["charge"] = [rdmolops.GetFormalCharge(mol) for mol in df_in.Mol]
```

利用此函数，我们可以计算分子的分子量、LogP 和形式电荷。这些性质决定了分子的大小、其从油性物质（辛醇）中分离进入水中的能力，以及分子带正电还是负电。获得计算结果后，我们可以比较活性和非活性分子的性质分布：

```
add_property_columns_to_df(active_df)
```

我们查看 DataFrame 的前几行，以确保内容与输入文件匹配（见[表 11-1](#Chapter11_9783960103516.xhtml#ch11tab1)）：

```
active_df.head()
```

*表 11-1：DataFrame active_df 的前几行*

![image](Images/p177-01.png)

我们对非活性分子执行相同的操作：

```
decoy_df = pd.read_CSV("mk01/decoys_final.ism",header=None,sep=" ")
decoy_df.columns = ["SMILES","ID"]
decoy_rows, decoy_cols = decoy_df.shape
decoy_df["label"] = ["Decoy"]*decoy_rows
PandasTools.AddMoleculeColumnToFrame(decoy_df,"SMILES","Mol")
add_property_columns_to_df(decoy_df)
```

为了创建模型，我们需要一个包含活性和非活性分子的 DataFrame。我们使用 Pandas 函数 `append` 将两个 DataFrame 合并，并创建一个名为 `tmp_df` 的新 DataFrame：

```
tmp_df = active_df.append(decoy_df)
```

为了比较活性和非活性分子的性质，我们使用小提琴图。小提琴图是箱线图的一种变体。小提琴图显示频率分布的镜像水平视图。在理想情况下，我们会看到活性和非活性分子具有相似的分布。结果如[图 11-1](#Chapter11_9783960103516.xhtml#abb11-1)所示：

```
sns.violinplot(tmp_df["label"],tmp_df["mw"])
```

![image](Images/p178-01.png)

*图 11-1：活性和非活性分子分子量的小提琴图*。

观察该图，我们发现分子量的分布大致相同。虽然非活性分子的重量较低，但包含中间 50% 元素的两个分布区间（以矩形表示）是相似的。

我们同样使用小提琴图来比较 LogP 分布（见[图 11-2](#Chapter11_9783960103516.xhtml#abb11-2)）。在这里分布也很相似，非活性分子的值略低于活性分子：

```
sns.violinplot(tmp_df["label"],tmp_df["logP"])
```

![image](Images/p179-01.png)

*图 11-2：活性和非活性分子 LogP 的小提琴图*。

最后，我们也来看一下形式电荷的比较（见[图 11-3](#Chapter11_9783960103516.xhtml#abb11-3)）：

```
sns.violinplot(new_tmp_df["label"],new_tmp_df["charge"])
```

![image](Images/p179-02.png)

*图 11-3：活性和非活性分子形式电荷的小提琴图*。

这里我们看到了一个明显的差异。所有活性分子都是中性的，电荷均为 0，而一些非活性分子带有 +1 或 -1 的电荷。接下来，我们检查带电非活性分子所占的比例。为此，我们创建一个仅包含带电分子的新 DataFrame：

```
charged = decoy_df[decoy_df["charge"] != 0]
```

通过 `shape` 可以显示 DataFrame 的行数和列数。因此，通过 `shape[0]` 我们可以获得行数。我们将包含带电分子的 DataFrame 的行数除以包含所有非活性分子的 DataFrame 的行数：

```
charged.shape[0]/decoy_df.shape[0]
```
