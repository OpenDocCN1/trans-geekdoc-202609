

### AdaBoost
`AdaBoost`，也称为自适应提升，是第一个使用粗糙且不准确的规则来产生非常高精度预测规则的提升算法（[Rätsch et al., 2001](#bodymatter-006.xhtml#b_9783110648195-006_ref_080)）。`AdaBoost` 算法可以与其他 ML 算法结合以提高其效率。它通过将较弱算法的输出组合成加权和来给出最终的准确输出。`AdaBoost` 分类 的数学方程为：

(6.13) `${F(x)} = {sign}\left( {\sum_{m = 1}^{M}\theta_{mf_{m}(x)}} \right)$`

其中 `F(x)` 是正确的分类器输出，即加权的 *M* 个软分类器组合。`Fm` 是第 m 个弱分类器，`θm` 指相关权重。`AdaBoost` 的框图见 ([Figure 6.12](#bodymatter-006.xhtml#b_9783110648195-006_fig_012))。

![Figure 6.12: Block diagram of AdaBoost.](graphic/converted/b_9783110648195-006_fig_012.png)

Figure 6.12: Block diagram of AdaBoost.

### Gradient Boosting
`Gradient Boosting` 是用于构建预测模型的有用算法之一，其可以快速对训练数据集过拟合。该技术也命名为 XGBoost。`Gradient Boosting` 的主要目标是结合所有弱算法的预测强度以获得更准确的预测结果（[Friedman, 2002](#bodymatter-006.xhtml#b_9783110648195-006_ref_033)）。`Gradient Boosting` 中使用的最常见类型的弱算法是决策树。设 `Fm` 为不完美模型，则使用 `h` 估计量的新准确模型方程如下：

(6.14) `F[m + 1](x) = F[m](x) + h(x)`

其中 `h(x) = y − Fm(x)` 且 `y` 为输出变量。使用决策树的 `Gradient Boosting` 方程可在下图中表示（[Figure 6.13](#bodymatter-006.xhtml#b_9783110648195-006_fig_013)）。

![Figure 6.13: Gradient boosting structure using decision trees.](graphic/converted/b_9783110648195-006_fig_013.png)

Figure 6.13: Gradient boosting structure using decision trees.

## 6.2.3 Disease prediction using semisupervised machine learning

### A. What is semisupervised learning
半监督学习包括在包含标记数据和未标记数据的数据集组合上训练的算法。通常，这类组合包含少量标记数据集和非常大的未标记数据集。这些算法有助于克服监督学习的缺点，即涉及机器学习工程师或数据科学家对数据集进行手工标记，当涉及大量数据时这是一件非常昂贵的事情。此外，由于无监督学习的应用范围有限，半监督学习算法有助于克服这些缺点（Zhu and Goldberg, 2009）。半监督学习算法的基本流程涉及程序员或数据科学家使用无监督学习算法对数据进行聚类，然后使用现有标记数据对剩余的未标记数据进行标记。未标记数据集相对便宜获取，而标记数据集非常昂贵。半监督学习算法基于某些假设，例如连续性假设、聚类假设和流形假设。

### B. Related work on diseases predicted using semi-supervised machine learning
表 6.2 描述了用于预测各种精神障碍的各种半监督 ML 技术，以及每种技术的 数据集和准确率范围。

Table 6.2:Disease prediction using semisupervised ML techniques.

| Disease || Ml techniques || Data type || Accuracy range |
| --- | --- | --- | --- |
| Alzheimer’s disease || `GA` ([Vandewater et al., 2015](#bodymatter-006.xhtml#b_9783110648195-006_ref_099); [Brasil, et al., 2009](#bodymatter-006.xhtml#b_9783110648195-006_ref_008); [Johnson et al., 2014](#bodymatter-006.xhtml#b_9783110648195-006_ref_046)) || `Biological` ([Vandewater et al., 2015](#bodymatter-006.xhtml#b_9783110648195-006_ref_099)), `clinical assessment` ([Brasil et al., 2009](#bodymatter-006.xhtml#b_9783110648195-006_ref_008); [Johnson et al., 2014](#bodymatter-006.xhtml#b_9783110648195-006_ref_046)) || `GA -` 86–90 % |
| --- | --- | --- | --- |
| Dementia || `GA` ([Kumari et al., 2014](#bodymatter-006.xhtml#b_9783110648195-006_ref_057), pp.165–172) || `Imaging` ([Kumari et al., 2014](#bodymatter-006.xhtml#b_9783110648195-006_ref_057), pp.165–172) || `GA -` 95.5–98% with NN |
| Attention deficit hyperactivity disorder || `GA` ([Yaghoobi and Azadi, 2018](#bodymatter-006.xhtml#b_9783110648195-006_ref_104)) || `Clinical assessment` ([Yaghoobi and Azadi, 2018](#bodymatter-006.xhtml#b_9783110648195-006_ref_104)) || `GA -` 97%–98.07% |
| Depression || `GA` ([Mohammadi et al., 2015](#bodymatter-006.xhtml#b_9783110648195-006_ref_069)) || `Imaging` ([Mohammadi et al., 2015](#bodymatter-006.xhtml#b_9783110648195-006_ref_069)) || `GA -` > 80% |
| Schizophrenia || `GA` ([Kaufmann et al., 2017](#bodymatter-006.xhtml#b_9783110648195-006_ref_048)) || `Imaging` ([Kaufmann et al., 2017](#bodymatter-006.xhtml#b_9783110648195-006_ref_048)) || `GA -` 74–76.2% |
| Suicide/self-harm || `GA` ([Poulin et al., 2014](#bodymatter-006.xhtml#b_9783110648195-006_ref_077)) || `Clinical notes` ([Poulin et al., 2014](#bodymatter-006.xhtml#b_9783110648195-006_ref_077)) || `GA -` 67–69% |

### C. Techniques used for disease prediction in semisupervised machine learning
`Genetic Algorithm (GA)` 是一种随机搜索算法，由 John Holland 于 1975 年提出用于解决优化问题。`GA` 使用重组和选择标准来生成新的样本点。它们应用于代码，即称为染色体的有限长度字符串。每个字符串包含有限长度的符号，称为基因。通过对它们进一步应用“突变”和“交叉”过程来生成新的数据点。在医学领域，`GA` 用于高维模式的分类和特征提取（[Figure 6.14](#bodymatter-006.xhtml#b_9783110648195-006_fig_014)）显示了 `GA` 的基本步骤。

![Figure 6.14: Steps for GA.](graphic/converted/b_9783110648195-006_fig_014.png)

Figure 6.14: Steps for GA.

## 6.2.4 Disease prediction using unsupervised machine learning

### A. What is unsupervised learning
与监督学习相比，无监督机器学习涉及未标记数据。使用无监督学习的主要原因不是为了预测目标结果变量；而是为了在没有监督的情况下处理有意义的信息。无监督学习的一些实例是寻找数据对象之间的相似性、弄清属性之间的联系、重塑属性以降低维度等。聚类是一种事实发现技术，旨在在没有来自现有组的先前信息的情况下识别相关数据中的可能子组。例如，自杀分析师可能想知道哪些“患者”聚类来自自杀群体。([Coates et al., 2011](#bodymatter-006.xhtml#b_9783110648195-006_ref_017))。

### B. Related work on diseases predicted using unsupervised machine learning
表 6.3 描述了用于预测各种精神障碍的各种无监督机器学习技术，以及每种技术的 数据集和准确率范围。

Table 6.3:Disease prediction using unsupervised machine learning techniques.

| Disease || ML techniques || Data type || Accuracy range |
| --- | --- | --- | --- |
| Anxiety || `k-means clustering` ([Park et al., 2018](#bodymatter-006.xhtml#b_9783110648195-006_ref_073)) || `Social media` ([Park et al., 2018](#bodymatter-006.xhtml#b_9783110648195-006_ref_073)) || – |
| --- | --- | --- | --- |

