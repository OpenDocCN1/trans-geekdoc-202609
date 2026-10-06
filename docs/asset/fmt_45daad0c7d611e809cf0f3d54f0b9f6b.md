
# MACDA: 多剂代理反事实药物-靶标亲和力框架

> Nguyen, Tri Minh, et al. "基于多剂代理强化学习的药物靶标预测反事实解释". arXiv preprint arXiv:2103.12983 (2021).

## MACDA: 多剂代理反事实药物-靶标亲和力框架

### 药物剂

- 行动:
  - 移除原子和键
  - 添加原子和键

### 蛋白质剂

- 用阿拉宁酸替换其他类型的氨基酸

### 药物-靶标环境

### DTA 模型

### 奖励

- 药物表示相似度
- 蛋白质表示相似度
- Δ 亲和力

## C1 部分

## 分子优化与生成

### 议程

### 分子优化

- 潜在空间的贝叶斯优化
- 目标导向强化学习

## 生成分子的生成

- 分子的深度生成模型
- 分子的循环模型

## 药物发现的三个基本问题

给定分子，它是药物吗？即属性、靶标或效应预测。

- 药物相似性
- 它可以调节的靶标及其程度
- 如果口服或注射，其动力学/动力学、效应、代谢情况

给定靶标，什么分子？

- 如果给出分子列表，挑选合适的一个。如果评估昂贵，需要搜索，例如使用贝叶斯优化。
- 如果未找到分子，需要从零开始生成 → 生成模型 + 贝叶斯优化，或强化学习。
- 药物相似空间呈现怎样的形态？

给定分子图，生成分子的步骤是什么？

- 合成可行性
- 反应规划，或逆合成

### 药物设计作为结构化机器翻译，即条件生成

> 可以表示为结构化机器翻译：
> • (知识库 + 结合属性) 到 (查询) → 一对多关系。

将图表表示为字符串（例如 `SMILES`），并使用序列 `VAEs` 或 `GANs`。

### 生成式图形模型

- 模型节点和交互
- 模型团体

### 序列

- 迭代方法

### 强化学习

- 离散目标

这些的任何组合 + 记忆。

### 分子优化

我们将起始分子优化为期望的性质。通常我们需要在多个目标之间取得平衡，包括与原分子的相似性。

策略 1：在离散化的化学空间中依次进行操作（如原子和键的添加/删除），确保结果化学上合法。

策略 2：将离散结构映射到连续空间，在潜在空间中搜索，然后映射回离散空间。

### 黑盒优化

这适用于任何我们没有详细了解但可以确定目标函数的过程。

### Typical methods:

- 贝叶斯优化
- 强化学习
- 主动学习
- 进化算法

### 强化学习用于分子优化

State: Current molecule

Actions: Atom/Bond addition/removal

Rewards: the properties of molecules (final reward) and chemical validity (intermediate and final reward)

### Learning:

- 政策梯度
- Q-value function with TD learning

> 周振鹏, 等. "通过深度强化学习优化分子". Scientific reports 9.1 (2019): 1-10.

### 图形 + 强化学习

生成式图形很难搞对：空间太大！

强化学习提供逐步构建：一步一步地构建

- 也称为马尔可夫决策过程
- 如前所述：图形提供属性估计

### 在潜在空间中搜索

### 模型: SMILES → VAE+RNN

#REF: Gómez-Bombarelli, Rafael, 等. "基于数据驱动的连续分子表示的自动化化学设计". ACS Central Science (2016).

### 分子优化作为机器翻译

- 修改现有分子更容易，即“分子改写”
- 分子优化作为图到图翻译

> #REF: Jin, W., Yang, K., Barzilay, R., & Jaakkola, T. (2019). 学习多模态图到图翻译用于分子优化. ICLR.

### 议程

### 分子优化

- 潜在空间中的贝叶斯优化
- 目标导向强化学习

### 生成分子生成

- 分子的深度生成模型
- 分子的循环模型

### 逆设计

- 给定期望的性能/表现来设计结构。
- 利用现有数据，离线查询模拟器
- 方法 1：通过优化搜索最佳结构（即分子优化）
- 方法 2：学习逆设计函数 `g(y) = f⁻¹(y)`
- 单步预测设计变量

### 背景: 变分自编码器

学习设计结构的密度函数 `P(x)`。

两个独立过程：生成过程（隐藏 → 可见）与识别过程（可见 → 隐藏）

### VAE 用于药物空间建模

将 `SMILES` 映射到向量空间（识别 RNN）

探索向量空间，例如随机采样或 `BO`（贝叶斯优化）进行搜索。

将结果映射回 `SMILES` 空间（生成 RNN）

> #REF: Gómez-Bombarelli, Rafael, 等. "基于数据驱动的连续分子表示的自动化化学设计". ACS Central Science (2016).

### 图形VAE

消除了分子的顺序表示的需求。

### 处理不规则结构

- 预测整个邻接矩阵、节点类型和边类型

### 处理变大小图

- 受限于训练数据中最大图的大小。

### 处理 permutation invariance

- 对两个图中每一对节点进行匹配

### 邻接矩阵

#REF: Simonovsky, M., & Komodakis, N. (2018). GraphVAE: 通过变分自编码器生成小图。arXiv preprint arXiv:1802.03480.

### 连接树 VAE

图形具有表达性但困难。字符串更易处理，但可能生成无效分子。

连接树是一种将图转换为“厚树”的方法

### 聚类词汇:

- 环
- 键
- 原子

> Jin, W., Barzilay, R., & Jaakkola, T. (2018). 连接树变分自编码器用于分子图生成. ICML'18.

### 算法 2 分子 G = (V, E) 的树分解

`V1 ← 所有不属于任何环的键 (u, v) ∈ E 的集合。`

`V2 ← G 中简单环的集合。`

`for r1, r2 in V2 do`

`合并 r1, r2 为一个环，如果它们共享超过两个原子（桥接环）。`

`end for`

`V0 ← 位于 V1 ∪ V2 中三个或更多集合交集的原子。`

`V ← V0 ∪ V1 ∪ V2`

`E ← {(i, j, c) ∈ V × V × ℝ | |i ∩ j| > 0}. 当 i ∈ V0 或 j ∈ V0 时设置 c = ∞，否则 c = 1。`

`返回集群图 (V, E) 上的最大生成树。`

| Method | Reconstruction | Validity |
| :--- | :--- | :--- |
| CVAE | 44.6% | 0.7% |
| GVAE | 53.7% | 7.2% |
| SD-VAE² | 76.2% | 43.5% |
| GraphVAE | - | 13.5% |
| JT-VAE | 76.7% | 100.0% |

> Jin, W., Barzilay, R., & Jaakkola, T. (2018). 连接树变分自编码器用于分子图生成. ICML'18.

### 图RNN

这是一种图动态的情况：节点和边是依次添加的。

通过 `BFS` 解决可扩展性问题

> You, Jiaxuan, 等. "GraphRNN: 使用深度自回归模型生成真实图形". ICML (2018).

### VAE + BO 方式的问题

这仍然是一个插值问题

在训练数据的高密度区域之外搜索会导致生成质量极差。

我们需要一种更内在的探索策略

- 组合性
- 语法/语法
- 网络生成生成网络（进行中）

### 语法 VAE

拟议方法

1. 定义语法
2. 将有效序列解析为一系列生产规则的序列
3. 学习一个 `VAE`，它生成语法生产规则的序列
4. 使用该 `VAE` 生成有效的生产规则序列
5. 按顺序应用这些规则将得到原始序列

> Kusner, Matt J., Brooks Paige, and José Miguel Hernández-Lobato. "语法变分自编码器". International Conference on Machine Learning. PMLR, 2017.

### 编码

### 语法 VAE (2)

### 第 122 页

### 解码

### 语法 VAE (3)

### 其他作品

Shi, Chence, 等. "GraphAF: 基于流的分子图生成自回归模型". International Conference on Learning Representations. 2019.

Mahmood, Omar, 等. "面具图建模用于分子生成". Nature communications 12.1 (2021): 1-12.

## Part C2

### Knowledge graph reasoning & Drug synthesis

### Agenda

### Reasoning on biomedical knowledge graphs

- Recommendation
- Drug repurposing

### Retrosynthesis

- Chemical planning
- Chemical reaction as graph morphism

### Wrapping up

### Biomedical knowledge graphs

> Callahan, Tiffany J., et al. "Knowledge-based biomedical data science." Annual review of biomedical data science 3 (2020): 23-41.

### Some biomedical knowledge graphs

| KG Dataset | Link | Entities | Triples | Entity Types | Relation Types | Contains Features | Constituent Datasets | Version Info | Last Update |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Hetionet [56] | https://het.io/ | 47K | 2.2M | 11 | 24 | ✗ | 29 | ✗ | 2017 |
| DRKG [65] | https://github.com/gnn4dr/DRKG | 97K | 5.7M | 13 | 107 | ✗ | 34 | ✗ | 2020 |
| BioKG [151] | https://github.com/dsi-bdi/biokg | 105K | 2M | 10 | 17 | categorical | 13 | ✗ | 2020 |
| PharmKG [164] | https://github.com/MindRank-Biotech/PharmKG | 7.6K | 500K | 3 | 29 | continuous | 7 | ✗ | 2020 |
| OpenBioLink [14] | https://zenodo.org/record/3834052 | 184K | 4.7M | 7 | 30 | ✗ | 17 | ✗ | 2020 |
| Clinical Knowledge Graph [124] | https://data.mendeley.com/datasets/mrcf7f4tc2/1 | 16M | 220M | 35 | 57 | ✗ | 35 | ✗ | 2020 |

### Examples of ontologies suitable for drug discovery

| Ontology Name | Entities Covered | Classes | Average # of children | Classes with no definition | Number of Properties | Max Depth | License |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Monarch Disease Ontology (MonDO) | Diseases | 24K | 5 | 8K | 25 | 16 | Creative Commons |
| Experimental Factor Ontology (EFO) | Diseases | 28K | 6 | 7K | 66 | 20 | Apache 2.0 |
| Orphanet Rare Disease Ontology (ORDO) | Rare Diseases | 15K | 17 | 8.5K | 24 | 11 | Creative Commons |
| Medical Subject Headings (MeSH) | Medical Terms | 300K | 4 | 270K | 38 | 15 | UMLS License |
| Human Phenotype Ontology (HPO) | Disease Phenotype | 19K | 3 | 6.5K | 0 | 16 | HPO License |
| Disease Ontology (DO) | Diseases | 19K | 4 | 8K | 89 | 33 | Creative Commons |
| Drug Target Ontology (DTO) | Drug Targets | 10K | 4 | 3K | 43 | 11 | Creative Commons |
| Gene Ontology (GO) | Genes | 44K | - | - | 11 | - | Creative Commons |

### Biomedical knowledge graph construction

- Nodes: Terms within biological ontologies
- Edge: Relationship between terms. Some notable entities relationship resources:
