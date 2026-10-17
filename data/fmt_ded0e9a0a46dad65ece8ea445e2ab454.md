
# GNNExplainer

GNNExplainer explains DL model by providing a small subgraph of the input graph together with a small subset of node features that are most influential for the prediction.

![](img/becaa13a45abf256713c782a26b8b29d_53_0.png)

![](img/becaa13a45abf256713c782a26b8b29d_53_1.png)

`max_{GS} MI(Y, (GS, XS)) = H(Y) - H(Y|G = GS, X = XS)`

## GNNExplainer (2)

![](img/becaa13a45abf256713c782a26b8b29d_54_0.png)

Ying, Rex, et al. "Gnnexplainer: Generating explanations for graph neural networks." Advances in neural information processing systems 32 (2019): 9240.

## GNNExplainer (3)

![](img/becaa13a45abf256713c782a26b8b29d_55_0.png)

- Input to GNN
- GNN's Prediction
- Molecule's mutagenicity
- Ground Truth Feature Importance

GNNExplainer

![](img/becaa13a45abf256713c782a26b8b29d_55_1.png)

- Grad
- Att
- Not applicable

# Few-shot learning for drug property prediction

Some ideas are in place:

- Prototype, distance metric learning.
- Joint feature learning of many small tasks, then fine-tuning on new task.

![](img/becaa13a45abf256713c782a26b8b29d_56_0.png)

# Part B2

## Protein representation and protein-drug binding

### Agenda

## Protein representation learning

- Embedding, BERT
- 2D contact map
- 3D structure
- Protein folding

![](img/becaa13a45abf256713c782a26b8b29d_63_0.png)

> #REF: Yang, K. K., Wu, Z., Bedbrook, C. N., & Arnold, F. H. (2018). Learned protein embeddings for machine learning. Bioinformatics, 34(15), 2642-2648.

## Sequential representation

- **One-hot encoding**: simple, but inherently sparse, memory-inefficient, contains no prior knowledge and contextual information.

![](img/becaa13a45abf256713c782a26b8b29d_64_0.png)

#REF: Lim, S., Lu, Y., Cho, C. Y., Sung, I., Kim, J., Kim, Y., ... & Kim, S. (2021). A review on compound-protein interaction prediction methods: Data, format, representation and model. Computational and Structural Biotechnology Journal, 19, 1541.

## Sequential representation (cont.)

- **One-hot encoding**: simple, but inherently sparse, memory-inefficient, contains no prior knowledge and contextual information.
- **Evolutionary information**: search for related proteins to perform multiple sequence alignment (MSA) and extract evolutionary information. Can be effective (AlphaFold2) but computational costly and requires sufficient data and diversity.

![](img/becaa13a45abf256713c782a26b8b29d_65_0.png)

> #REF: Kandathil, S. M., Greener, J. G., Lau, A. M., & Jones, D. T. (2021). Ultrafast end-to-end protein structure prediction enables high-throughput exploration of uncharacterised proteins.

## NLP-inspired embedding

- **NLP-inspired embedding**: protein sequence as a sentence and residues as tokens then apply language modelling (word2vec, doc2vec, glove, seq2vec, ELMo, BERT, etc).

![](img/becaa13a45abf256713c782a26b8b29d_67_0.png)

## Spatial representation

- **2D contact/distance map**: distance between residues pairs of 3D protein structure.
- **3D structure**: coordinate of residues in 3D space.
- **Graph representation**: residues as nodes and distance as edges. Can combine with sequential representation via attributed graph.

![](img/becaa13a45abf256713c782a26b8b29d_68_0.png)

![](img/becaa13a45abf256713c782a26b8b29d_68_1.png)

![](img/becaa13a45abf256713c782a26b8b29d_68_2.png)

## Protein sequence

AKLMMAATTAGVVVTTTH...

Pretraining

![](img/becaa13a45abf256713c782a26b8b29d_69_0.png)

Protein contact map

![](img/becaa13a45abf256713c782a26b8b29d_69_1.png)

## Protein graph

![](img/becaa13a45abf256713c782a26b8b29d_69_2.png)

## Protein folding prediction progress

CASP: MEDIAN ACCURACY of PREDICTIONS in FREE-MODELING by THE BEST TEAM, 2006-20.

Source: DeepMind, 2020 | Chart: 2021 AI Index Report

![](img/becaa13a45abf256713c782a26b8b29d_70_0.png)

## Protein 3D structure prediction

- **Input**: protein amino acid sequence `X = (x₁ x₂ ... x_L)` where `L` is protein sequence length, `x_i` is residue type at position `i`.

![](img/becaa13a45abf256713c782a26b8b29d_71_0.png)

![](img/becaa13a45abf256713c782a26b8b29d_71_1.png)

> "#REF: "Hemoglobin", En.wikipedia.org, 2020. [Online]. Available: https://en.wikipedia.org/wiki/Hemoglobin."

### Approaches

- **Template-based**
  - Using known structure of proteins that have high sequence similarity with target protein as the initial structure template.
  - From the initial structure, protein fragments are inserted or deleted to minimize the global free energy.
  - An effective method if the target protein sequence has at least 30% sequence identity with the template protein.

- **Template-free**
  - Without using solved protein structure
  - Main goal is to find a conformation that has minimum free energy
  - Requires a vast computational resource such as powerful supercomputer or distributed computing projects (Rosetta@Home, Folding@Home)

![](img/becaa13a45abf256713c782a26b8b29d_73_0.png)

## AlphaFold 2

![](img/becaa13a45abf256713c782a26b8b29d_74_0.png)

### AlphaFold 2 – Evoformer 块

![](img/becaa13a45abf256713c782a26b8b29d_75_0.png)

### Pair 表示 (r,r,c)

![](img/becaa13a45abf256713c782a26b8b29d_75_1.png)

### 对应的图中的边

![](img/becaa13a45abf256713c782a26b8b29d_75_2.png)

### 使用 'outgoing' 边的三角乘法更新

![](img/becaa13a45abf256713c782a26b8b29d_75_3.png)

### 使用 'incoming' 边的三角乘法更新

![](img/becaa13a45abf256713c782a26b8b29d_75_4.png)

### 起始节点周围的三角自注意

![](img/becaa13a45abf256713c782a26b8b29d_75_5.png)

### 结束节点周围的三角自注意

![](img/becaa13a45abf256713c782a26b8b29d_75_6.png)

### AlphaFold 2 – 结构模块

![](img/becaa13a45abf256713c782a26b8b29d_76_0.png)

### 议程

## 蛋白质表示学习

- 嵌入, BERT
- 2D 接触图
- 3D 结构
- 蛋白质折叠

## 药物-靶标结合预测

- 多靶标预测
- 药物-蛋白质结合作为图-图交互
- 冷启动问题
- 解释

> Cheng, Feixiong, et al. "预测药物-靶标相互作用和药物重新定位通过基于网络的推理". PLoS computational biology 8.5 (2012): e1002503.

## 药物-靶标双部分网络

![](img/becaa13a45abf256713c782a26b8b29d_78_0.png)

- 代谢
- 血液
- 心血管
- 皮肤
- 生殖泌尿
- 内分泌
- 抗感染
- 抗肿瘤
- 骨骼肌肉
- 神经系统
- 呼吸
- 感官器官
- 各种
- 未知
- 靶标
- 95
- 47
- 28
- 20
- 11
- 5
- 1

## 双部分网络操作

- 链接预测
- 推荐技术，例如 SVD、随机游走、最近邻。
- 知识图完成技术，例如 TransE
- 稍后在 C2 部分中更多

> #REF: Do, Kien, et al. "基于图的_attentional multilabel learning_ 传递方法". Machine Learning, 2019.

## 多靶标结合

规模随靶标数量线性增长，并通过消息因子化实现高效处理。

- (a) 一个输入图包含 4 个节点和 3 个标签
- (b) 输入节点更新
- (c) 标签节点更新

> #REF: Do, Kien, et al. "基于图的_attentional multilabel learning_ 传递方法". Machine Learning, 2019.

## 药物和蛋白质

## 药物分子

一种小分子与生物大分子（如蛋白质）结合，以改变其活性或功能

## 蛋白质

大分子由氨基酸残基链形成三维形状。蛋白质在生物体中执行许多功能

## 药物和蛋白质 (2)

## 药物分子

- 结合到蛋白质结合位点
- 改变其靶标活性
- 结合强度即为结合亲和力

## 蛋白质

- 可能因与药物分子的相互作用而改变构象
- 其功能因药物分子在结合位点的存在而改变

## 药物和蛋白质 (3)

我们需要理解药物-靶标相互作用，因为：

- 快速且安全的药物重新定位和发现/重新定位过程，用于快速应对疫情
- 寻找对困难疾病的解决方案

![](img/becaa13a45abf256713c782a26b8b29d_83_0.png)

> 图片来源: Lancet

## 药物-靶标结合作为问答

- **上下文/数据库**: 结合靶标（例如 RNA/蛋白质序列，或 3D 结构），作为集合、序列或图，加上现有的结合、交互数据库。
- **查询**: 药物（例如 SMILES 字符串，或分子图）
- **答案**: 亲和力、结合位点、调节效应、构象变化。

![](img/becaa13a45abf256713c782a26b8b29d_84_0.png)

> #REF: Nguyen, T., Le, H., & Venkatesh, S. (2019). GraphDTA: 使用图卷积网络预测药物-靶标亲和力。BioRxiv, 684662.

### 药物图

### 图内图交互

### 蛋白质图

> Nguyen, T. M., Nguyen, T., Le, T. M., & Tran, T. (2021). “GEFA: 早期融合方法用于药物-靶标亲和力预测”。IEEE/ACM Transactions on Computational Biology and Bioinformatics

## GEFA (续)

我们设计了一个用于详细分析药物与蛋白质残基相互作用的模型。

该架构是一种新的图内图结构。

这使得对结合位点和强度的预测更加准确和精确。

![](img/becaa13a45abf256713c782a26b8b29d_86_0.png)

## GEFA (续): 药物-靶标图

![](img/becaa13a45abf256713c782a26b8b29d_87_0.png)

## GEFA (续): GCN + 融合

![](img/becaa13a45abf256713c782a26b8b29d_88_0.png)

![](img/becaa13a45abf256713c782a26b8b29d_88_1.png)

## 冷启动问题

## 训练集

![](img/becaa13a45abf256713c782a26b8b29d_89_0.png)

## 测试集

![](img/becaa13a45abf256713c782a26b8b29d_89_1.png)

![](img/becaa13a45abf256713c782a26b8b29d_89_2.png)

## 冷启动问题

## 测试集

## 结果可视化

![](img/becaa13a45abf256713c782a26b8b29d_91_0.png)

预测的 MST1 靶标结合位点的注意力值。残基 ASP 167.A 拥有最高的注意力分数。

![](img/becaa13a45abf256713c782a26b8b29d_91_1.png)

模拟预测的残留-配体相互作用。残基 ASP 167.A 是结合位点之一

## 解释 DTA 深度学习模型: 特征归因

展示输入各部分对模型决策的贡献

不显示模型输入与输出之间的因果关系

## 解释 DTA 深度学习模型: 反事实

观测数据

## 反事实解释生成

## 反事实解释生成目标
