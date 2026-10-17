
# C2 部分

# 知识图推理与药物合成

# 议程

# 生物医学知识图的推理

- 推荐
- 药物再利用

# 逆向合成

- 化学规划
- 化学反应作为图形变形

# 总结

# 生物医学知识图

![](img/becaa13a45abf256713c782a26b8b29d_126_0.png)

> Callahan, Tiffany J., et al. "基于知识的生物医学数据科学." 《生物医学数据科学年度评论》 3 (2020): 23-41.

# 生物医学知识图谱

| 数据集 | 首次发布 | 更新频率 | 1 年内更新 | 策展方法 | 主要领域 | 摘要 |
|---------|----------------|------------------|----------------------|-----------------|----------------|---------|
| STRING | 2003 | 每月 | ✓ | 专家与自动化 | 蛋白质/基因相互作用 | 现有知识图谱中最常用的物理和功能性蛋白质-蛋白质相互作用来源之一。 |
| BioGRID | 2003 | 每月 | ✓ | 专家 | 生物相互作用 | 包含基因、蛋白质和化学实体之间的相互作用，可直接纳入知识图谱。 |
| IntAct | 2003 | 每月 | ✓ | 专家 | 分子相互作用 | 包含基因、蛋白质和化学实体之间的分子反应。使用 UniProt 作为标识符。 |
| OmniPath | 2016 | > 每年 | ✓ | 专家 | 通路 | 可通过其 RDF 版本纳入知识图谱的相互作用资源整合器。 |
| Pathway Commons | 2010 | 每半年 | ✓ | 专家与自动化 | 通路 | 包含许多资源的集合，包括本表讨论的其他资源。 |

### 知识图谱推理的用例

- 多重用药预测
- 药物-靶点相互作用预测
- 基因-疾病优先级排序

![](img/becaa13a45abf256713c782a26b8b29d_130_0.png)

> #REF: Yuan, J., Jin, Z., Guo, H., Jin, H., Zhang, X., Smith, T., & Luo, J. (2020). Constructing biomedical domain-specific knowledge graph with minimum supervision. Knowledge and Information Systems, 62(1), 317-336.

### 多重用药预测

预测同时使用一种或多种药物时的不良副作用。

![](img/becaa13a45abf256713c782a26b8b29d_131_0.png)

### 多重用药预测

### Decagon (Zitnik, M 等)

### 单个药物节点（蓝色）的 GCN 每层更新

### B 多重用药副作用预测

### C 六种药物的一批网络

> #REF: Zitnik, M., Agrawal, M., & Leskovec, J. (2018). Modeling polypharmacy side effects with graph convolutional networks. Bioinformatics, 34(13), i457-i466.

### 药物-靶点相互作用预测

预测药物与靶点之间未知的相互作用

TriModel (Mohamed, S. K. 等) 学习知识实体和关系的低秩向量表示。

![](img/becaa13a45abf256713c782a26b8b29d_133_0.png)

> #REF: Mohamed, S. K., Nováček, V., & Nounu, A. (2020). Discovering protein drug targets using knowledge graph embeddings. Bioinformatics, 36(2), 603-610.

### 基因-疾病优先级排序

预测疾病与分子实体（蛋白质和基因）之间的关系。

![](img/becaa13a45abf256713c782a26b8b29d_134_0.png)

[PAGE 135]

### 基因-疾病优先级排序

预测疾病与分子实体（蛋白质和基因）之间的关系。

![](img/becaa13a45abf256713c782a26b8b29d_135_0.png)

#REF: Paliwal, S., de Giorgio, A., Neil, D., Michel, J. B., & Lacoste, A. M. (2020). Preclinical validation of therapeutic targets predicted by tensor factorization on heterogeneous graphs. Scientific reports, 10(1), 1-19.

### 药物再利用

从头药物发现成本高昂、耗时漫长且无成功保证

罕见病市场太小，不足以支持商业开发

像 COVID-19 这样紧迫的新疾病等待不起

药物再利用（又称药物重新定位、重新分析或重新任务）是最佳途径之一。

+   为已批准或研究性药物寻找除原设计目的外的新用途。

缩短时间和成本，相比从头药物发现更快进入临床试验

> Lee, Wing-Hin, et al. "The potential to treat lung cancer via inhalation of repurposed drugs." Advanced drug delivery reviews 133 (2018): 107-130.

### 方法

+   签名匹配、基于相似性（药物-疾病、药物-药物、不良反应谱）
+   详细的药物-蛋白质结合预测
+   通路/网络映射 → 知识图谱推理，如链接预测
+   来自电子健康记录的回顾性临床分析

> MERS、SARS 和 [SARS-CoV-2] 病毒的总体基因组布局、总体复制动力学和生物学非常相似，因此测试针对这些冠状病毒相对通用部分的药物是合乎逻辑的一步。

(Vincent Munster, 美国国立卫生研究院病毒生态学部门负责人，截至 2020 年 2 月)

Pushpakom, Sudeep, et al. "Drug repurposing: progress, challenges and recommendations." Nature reviews Drug discovery 18.1 (2019): 41-58.

### 作为分子图上多靶点预测的再利用

(a) 一个包含 4 个节点和 3 个标签的输入图

(b) 输入节点更新

(c) 标签节点更新

#REF: Do, Kien, et al. "Attentional Multilabel Learning over Graphs-A message passing approach." Machine Learning, 2019.

### 作为生物医学知识图谱中药物-靶点预测的再利用

知识图谱是一组三元组（头实体、尾实体、关系），其中头和尾是节点/实体，关系是链接类型。例如：头 = 蛋白质，尾 = 药物，关系 = 药物-蛋白质结合。

通常知识图谱是不完整的，例如任意一对（头实体、尾实体）之间缺少关系。

再利用是为现有节点（药物）寻找新链接。

搜索通常从靶点（如蛋白质）开始，以定位适合进一步开发（如试验或优化）的药物。
