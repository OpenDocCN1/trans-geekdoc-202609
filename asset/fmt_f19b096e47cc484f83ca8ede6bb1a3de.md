
| 熵 `H(F)` | = | $-\sum_{\text{all classes} \in \mathit{C}} P_{c} \log_{2}P_{c} - P_{\text{forged}}\log_{2}(P_{\text{forged}}) - P_{\text{genuine}}\log_{2}(P_{\text{genuine}})$ |
| --- | --- | --- |

| 朴素贝叶斯, `P(Y|X)` | = | $\frac{P(X|Y)P(Y)}{P(X)}$ 因此，$\frac{P(\text{Forged}, F)P(\text{Forged})}{P(\text{Genuine})} = \frac{P(G|F)P(F)}{P(G)}$ |
| --- | --- | --- |

| Gini 指数, `Gini(F*)` | = | $1 - \sum_{i=1}^{r} P_{i}^{2}$ |
| --- | --- | --- |
| | | $P_{1}(g*) = \frac{\text{Number of data samples with class Genuine}}{\text{Total number of data samples}}$ |
| | | $P_{2}(f*) = \frac{\text{Number of data samples with class Forged}}{\text{Total number of data samples}}$ |

| 分裂信息 `(F, A)` | = | $-\sum_{i=1}^{\text{all classes}} \frac{|S_{f}|}{|S|} \log_{2}\frac{|S_{g}|}{|S|} + \frac{|S_{yes}|}{|S|} \log_{2}\frac{|S_{yes}|}{|S|} - \frac{|S_{no}|}{|S|} \log_{2}\frac{|S_{no}|}{|S|}$ |
| --- | --- | --- |

| 增益率 `(F, A)` | = | $\frac{\text{Gain}(F,A)}{\text{Split information}(F,A)}$ |
| --- | --- | --- |

将整个大象群分为若干族。精英策略解释了“将最好的大象保存在临时数组中”或“保护大象个体不受破坏”。EHO 是一种基于大象群聚行为的优化算法。完成一次迭代后，最差的 `m` 只大象的适应度值将被保存的最大象实体替换（图 1.12）。

图 1.12 EHO 过程

### EHO 原理

EHO 通过建立 `CUO` 和 `SO` 来对其行为建模。

- 将整个种群分为若干族。
- 每个族由一个女性个体领导，称为象母，代表每次迭代中优出的个体。
- 每次迭代中最差的个体代表成年的雄性大象，它们离开族群，单独生活。

### 族更新算子

象母是领导每个族大象的领导者。对于族 `C[i]` 中的搜索个体 `j`，其位置必须根据其与族长的关系进行调整。

`x[new, ci, j] = x[ci, j] + α * (x[best, ci] - x[ci, j]) * r`

`x[new, ci, j]` 和 `x[ci, j]` 是族 `C[i]` 中搜索个体 `j` 的新个体或新位置，以及族 `C[i]` 中大象个体 `j` 的旧位置。

`α` 表示 0 到 1 之间的数字，且 `α ∈ [0,1]`。

`x[best, ci]` 是族中最好大象的位置。

`r ∈ [0,1]`

`a ∈ [0,1]`

族长的位置根据族中所有个体的当前位置进行调整。

`x[new, ci, j] = β * x[center, Ci]`

其中 `x[center, Ci]` 是族 `C[i]` 中所有个体的中心位置。

```
x_{\text{center},C_{i}} = \frac{1}{n_{C_{i}}} \sum_{j=1}^{n_{C_{i}}} x_{ci,j}
```

`β ∈ [0,1]`

`n[C[i]]` 是族 `C[i]` 中的个体数量。

### 分离算子

引发雄性大象的生存特征。在解决优化问题时，雄性大象离开家庭群的行为可以在分离算子中体现。这是通过每代中适应度最差的大象实现的。

`x[worst, ci] = x[min] + (x[max] - x[min]) * r`

`x[worst, ci]` 是族 `C[i]` 中最差的个体。

`x[min] & x[max]` 是所有人的下界和上界。

`r` 是 0 到 1 之间的随机分布，且 `r ∈ [0,1]`。

```
x_{\text{center},ci,d} = \frac{1}{n_{ci}} \sum_{j=1}^{n_{ci}} x_{ci,j}
```

`x[center, Ci]` 是族 `C[i]` 中所有个体的中心位置。

`n[C[i]]` 是族 `C[i]` 中的个体数量。

（注：原文文本中部分公式描述存在重复或断裂，已按逻辑翻译）

### F1 分

这是一个衡量伪造检测系统有效性的平衡指标，它是精确率和召回率的调和平均数。确定每个分类器的 F 值，可以得到一个平衡的评估指标，它是精确率和召回率的调和平均数。

`F1` 分等于 `2 * (recall * precision) / (recall + precision)`。

### 接收工作特征（ROC）曲线

在不同的分类阈值下，ROC 曲线图形化展示了 `TPR` 与假正性率（`FPR`）之间的权衡。ROC 曲线面积越大表示性能越好，它经常被用作性能指标（表 1.6 和 表 1.7）。

表 1.6 熵、信息增、Gini 指数、分裂信息和增益率（过程 1）

| GLCM | LBP | ILBP | MBP | LTP | ILTP | RLBP | SLBP | P | L |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 特征 | | | | | | | | | G | Y |
| | | | | | | | | F | N |
| | | | | | | | | F | N |
| | | | | | | | | G | Y |
| | | | | | | | | G | Y |
| | | | | | | | | G | N |
| | | | | | | | | F | N |

表 1.7 熵、信息增、Gini 指数、分裂信息和增益率（过程 2）

| GLCM 到 SLBP | 预测 | 标签 |
| --- | --- | --- |
| 特征 | 真实 | 是 |
| | 伪造 | 否 |
| | 伪造 | 否 |
| | 真实 | 是 |
| | 真实 | 是 |
| | 真实 | 是 |
| | 伪造 | 否 |
| | 伪造 | 否 |

### 信息增

这是一个用于决策树和机器学习的概念，用于量化特征在分类或预测目标变量时的重要性。

可以使用多种性能指标来评估图像伪造检测系统的有效性。以下是常用的性能指标以及各自的公式（见图 1.14 和 图 1.15）。

图 1.14 各种性能指标（部分 1）

图 1.15 各种性能指标（部分 2）

可以使用多种性能指标来评估图像伪造检测系统的有效性。以下是常用的性能指标以及各自的公式（表 1.8 和 表 1.9）。

表 1.8 性能指标

| 准确率 (ACC) | $\text{Accuracy} = \text{Overall correctness of the forgery detection system}$ |
| --- | --- |
| | $\text{Accuracy} = \frac{\text{Correctly classified images}}{\text{Total number of images}}$ |
| | $\text{ACC} = \frac{(\text{Number of correctly detected forgeries} + \text{Correctly detected authentic images})}{\text{Total number of images} \text{ or } (\text{Correctly detected forgeries} + \text{correctly detected authentic images} + \text{authentic images incorrectly classified as forgeries} + \text{forged images incorrectly classified as authentic})}$ |

| 精确率 (Precision) | $\text{Precision} = \frac{\text{Correctly predicted forged images}}{\text{Total predicted forged images}}$ |
| --- | --- |
