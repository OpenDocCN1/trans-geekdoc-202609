
同样地，可视化我们模型的结果也很有帮助。为此，我们为验证数据生成预测：

```
pred = [x.flatten() for x in model.predict(valid_dataset)]
```

为了简化处理，我们创建一个包含预测结果的 Pandas DataFrame：

```
pred_df = pd.DataFrame(pred, columns=["neg", "pos"])
```

我们向该 DataFrame 进一步添加分子的状态（1 = 活性，0 = 非活性）和 SMILES 字符串：

```
pred_df["active"] = [int(x) for x in valid_dataset.y]
pred_df["SMILES"] = valid_dataset.ids
```

为了确保数据合理，我们查看 DataFrame 的前几行（参见[表 11-3](#Chapter11_9783960103516.xhtml#ch11tab3)）。

*表 11-3：包含预测结果的 DataFrame 的前几行*

![image](Images/p184-02.png)

我们可以使用箱线图来比较活性和非活性分子的预测值（参见[图 11-6](#Chapter11_9783960103516.xhtml#abb11-6)）。

```
sns.boxplot(pred_df.active, pred_df.pos)
```

![image](Images/p185-02.png)

*图 11-6：预测分子的正类得分*。

我们的模型运行良好：我们可以清晰地看到活性（1）和非活性（0）分子之间的分离。构建预测模型时，重要的是要更仔细地检查被预测为活性的非活性分子（**假阳性**），以及被预测为非活性的活性分子（**假阴性**）。正如我们从箱线图中所见，我们的活性分子中只有一个获得了较低的正类得分。为了进行更详细的检查，我们创建一个新的 DataFrame，其中包含所有正类得分 < 0.5 的活性分子：

```
false_negative_df = pred_df.query("active == 1 & pos < 0.5").copy()
```

为了研究这些分子的化学结构，我们使用 RDKit 中的 `PandasTools` 模块：

```
PandasTools.AddMoleculeColumnToFrame(false_negative_df, "SMILES", "Mol")
```

新的 DataFrame 如下所示（参见[图 11-7](#Chapter11_9783960103516.xhtml#abb11-7)）：

```
false_negative_df
```

![image](Images/p186-01.png)

*图 11-7：假阴性预测*。

我们需要药物化学知识来解读所呈现的信息。通常，将假阴性分子的化学结构与真阳性分子的化学结构进行比较，以弄清楚为什么分子未被正确预测，这很有启发性。通常原因在于假阴性分子与真阳性分子都不相似。在这种情况下，进行额外的文献检索以增加训练数据集中分子的多样性会有所帮助。

我们采用类似的方法来研究假阳性分子，这些分子本身是非活性的，但获得了正类得分 > 0.5（参见[图 11-8](#Chapter11_9783960103516.xhtml#abb11-8)）。在这里，与真阳性分子的化学结构进行比较也能给我们提供线索：

```
false_positive_df = pred_df.query("active == 0 & pos > 0.5").copy()
PandasTools.AddMoleculeColumnToFrame(false_positive_df, "SMILES", "Mol")
false_positive_df
```

![image](Images/p186-02.png)

*图 11-8：一个假阳性分子*。

在训练模型期间，评估模型性能对我们很重要。因此，我们在一部分数据上训练模型，在另一部分上进行验证。现在我们已完成性能评估，想要获得最高效的模型。为此，我们使用所有数据训练模型：

```
model.fit(dataset)
```

我们获得了 91% 的准确率。在最后一步中，我们将模型保存在之前创建的目录中，以便将其用于未来的预测：

```
model.save()
```

### 为预测准备数据集

创建好预测模型后，我们可以将其应用于新数据。预测模型通常基于文献检索创建，然后应用于想要筛选的分子。待筛选的分子可能来自内部数据库或商业可用的数据集。作为示例，我们使用创建的预测模型，对 ZINC 数据库中 100,000 个分子的小样本进行筛选，ZINC 数据库是一个包含超过十亿种商业可用分子的集合。

进行虚拟筛选时可能存在的一个问题是分子对生物学分析产生干扰。在过去 25 年中，许多研究小组开发了规则来识别潜在的问题分子。其中一些规则以 SMILES 字符串编码，由维护 ChEMBL 数据库的同一小组收集整理。这些规则通过 Python 脚本 `rd_filters.py` 提供。我们使用 `rd_filters.py` 来识别 ZINC 数据库 100,000 个分子样本中潜在的问题分子。

脚本 `rd_filters.py` 及相关文件可在我们的 GitHub 仓库（[https://github.com/deepchem/DeepLearningLifeSciences](https://github.com/deepchem/DeepLearningLifeSciences)）中获取。

调用 `-h` 可查看脚本的可用选项和参数。

```
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

```
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
*   69% 的分子通过了过滤器，31% 被判定为有问题。

我们首先查看导致 31% 分子被拒绝的原因。这可以让我们了解是否需要调整某个过滤器。我们显示 `zinc.CSV` 的前几行（参见[表 11-4](#Chapter11_9783960103516.xhtml#ch11tab4)）。

```
import pandas as pd
df = pd.read_CSV("zinc.CSV")
df.head()
```
