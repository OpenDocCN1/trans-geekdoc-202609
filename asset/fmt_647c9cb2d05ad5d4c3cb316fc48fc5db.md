
算法4展示了针对我们问题陈述的自适应算法的结构，我们将其称为 `SBSAda-Rip`。该算法使用数据的 70% 并进行 `T` 轮迭代。该方法以分布 `D₁` 和空规则集 `RS` 初始化。在每一轮 `t` 中，`AdaBoost` 使用分布 `Dₜ` 调用 `JRip` 分类器。`JRip` 分类器要经过一系列阶段。它从构建阶段开始。它逐一构建规则（同时满足最高信息增益：`p(log(p/t)-log(P/T))`）并逐一剪枝（根据剪枝度量：`p/(p+n)`）。当达到其中一个终止标准时，它会创建初始规则集 `RI`。优化阶段使用 `RI` 来拆分规则，并通过重新生长和重新剪枝（使用 `(TP+TN)/(P+N)`）来优化这些规则。选择最佳规则并重新添加到 `RI` 中。最后阶段，即删除和选择阶段，使用新的 `RI` 生成最终规则集 `RS`。该阶段删除阻碍规则集的条件，并将生成的规则集添加到 `RS`。从 `JRip` 分类器执行的计算中，`AdaBoost` 获得假设 `hₜ`。然后计算该假设的错误率，如果错误率大于 0.5，则更新分布 `Dₜ₊₁`。整个过程重复进行，直到数据中不再有错误分类的样本。最终，我们获得带有假设 `H(x)` 及其规则集的最合适的分类器。

### 5.4.3. 测试子阶段

该阶段使用测试数据来衡量训练模型的性能。我们从选定的最佳假设和规则集中获得所提出的模型，我们将其视为最优选项。

### 5.5. 验证

为了评估我们算法生成预测规则的性能，本节探讨两个主要研究问题。

## 算法4：增强型 Boosting 模型的高级伪代码。

```
Algorithm: SBSAda-rip algorithm
Input: -A sequence of m instances S = {(x₁, y₁)...(xₘ, yₘ)} where xᵢ ∈ Xₖ (Xₖ the subset obtained from SBS) with labels yᵢ ∈ Y={0,1} from Polish bankruptcy dataset
-JRip algorithm
-T (number of iterations)
Output: The final classifier with hypothesis H(x) and its final rule set RS
Initialize: D_t(i)=1/m for all i=1,...,m, a rule set RS = {}
1-For t = 1 to T
2- Call JRip using distribution D_t:
3- For each class:
4- [Building Stage]: Generate an initial rule set RI
5- Repeat:
6- Grow phase: grow one rule by adding conditions that satisfy the highest information gain: p(log(p/t)-log(P/T)) until the rule is 100% accurate
7- Prune phase: prune each rule according to the pruning metric: p/(p+n)
8- Until error rate >= 0.5 | no more positive instances | description length (DL) of the ruleset is 64 bits greater than the smallest DL
9- [Optimization Stage]:
10- from RI, generate two variants, A and B (A from an empty rule and B from the full rule) using the grow phase
11- prune A and B on metric: (TP+TN)/(P+N)
12- compute the original rule according to the description length DL of A and B
13- select the variant with the minimal DL for RI
14- If there are residual positives:
15- ([Building Stage])
16- [Deletion Stage]:
17- Delete the rules from the ruleset that would increase the DL of the whole ruleset
18- Add resultant ruleset to RS
19- End For
20- Get JRip classifier and obtain hypothesis h_t
21- Calculate the error rate e_t = Σ_i=1^m D_ti [h_t(x_i)≠y_i] of h_t
22- If e_t > 0.5 then T=t-1 and abort loop
23- set α_t = ½ ln [(1-e_t)/e_t]
24- Update D_{t+1}(i)= D_t(i) exp[-α_t y_i h_t(i)] / Z_t (Z is a normalization factor)
```

#### 5.5.1. 研究问题

`RQ 01`：与其他方法相比，所提出的方法能在多大程度上从给定数据集中发现准确的分类模型？

`RQ02`：现有模型与所提出的模型之间的显著比较是什么？

#### 5.5.2. 实验数据库描述

为了验证我们的工作，我们使用了波兰公司的财务信息，这些信息位于

制造业部门。数据集包含破产和非破产公司的信息。2004年之后，该行业有多家波兰公司破产（图5.2）[66]。

| ID 描述 | ID 描述 |
|---|---|
| X1 净利润 / 总资产 | X33 营业费用 / 短期负债 |
| X2 总负债 / 总资产 | X34 营业费用 / 总负债 |
| X3 营运资本 / 总资产 | X35 销售利润 / 总资产 |
| X4 流动资产 / 短期负债 | X36 总销售额 / 总资产 |
| X5 [(现金 + 短期证券 + 应收账款 - 短期负债) / (营业费用 - 折旧)] * 365 | X37 (流动资产 - 存货) / 长期负债 |
| X6 留存收益 / 总资产 | X38 固定资本 / 总资产 |
| X7 息税前利润 / 总资产 | X39 销售利润 / 销售额 |
| X8 权益账面价值 / 总负债 | X40 (流动资产 - 存货 - 应收账款) / 短期负债 |
| X9 销售额 / 总资产 | X41 总负债 / ((营业利润 + 折旧) * (12/365)) |
| X10 权益 / 总资产 | X42 营业利润 / 销售额 |
| X11 (毛利润 + 非常项目 + 财务费用) / 总资产 | X43 应收账款周转率 = 存货周转天数 |
| X12 毛利润 / 短期负债 | X44 (应收账款 * 365) / 销售额 |
| X13 (毛利润 - 折旧) / 销售额 | X45 净利润 / 存货 |
| X14 (毛利润 + 利息) / 总资产 | X46 (流动资产 - 存货) / 短期负债 |
| X15 (总负债 * 365) / (毛利润 - 折旧) | X47 (存货 * 365) / 产品销售成本 |
| X16 (毛利润 - 折旧) / 总负债 | X48 EBITDA（营业利润 - 折旧）/ 总资产 |
| X17 总资产 / 总负债 | X49 EBITDA（营业利润 - 折旧）/ 销售额 |
| X18 毛利润 / 总资产 | X50 流动资产 / 总负债 |
| X19 毛利润 / 销售额 | X51 短期负债 / 总资产 |
| X20 (存货 * 365) / 销售额 | X52 (短期负债 * 365) / 产品销售成本 |
| X21 销售额（n）/ 销售额（n-1） | X53 权益 / 固定资产 |
| X22 营业利润 / 总资产 | X54 固定资本 / 固定资产 |
| X23 净利润 / 销售额 | X55 营运资本 |
| X24 毛利润（3年内）/ 总资产 | X56 (销售额 - 产品销售成本) / 销售额 |
| X25 (权益 - 股本) / 总资产 | X57 (流动资产 - 存货 - 短期负债) (销售额 - 毛利润 - 折旧) |
| X26 (净利润 + 折旧) / 总负债 | X58 总成本 / 总销售额 |
| X27 营业利润 / 财务费用 | X59 长期负债 / 权益 |
| X28 营运资本 / 固定资产 | X60 销售额 / 存货 |
| X29 总资产的对数 | X61 销售额 / 应收账款 |
| X30 (总负债 - 现金) / 销售额 | X62 (短期负债 * 365) / 销售额 |
| X31 (毛利润 + 利息) / 销售额 | X63 销售额 / 短期负债 |
| X32 (流动负债 * 365) / 产品销售成本 | X64 销售额 / 固定资产 |

图（5.2） 波兰破产数据集的特征集。

描述近700家财务困境公司状况的经济因素收集于2007年至2013年间。对于仍在运营的公司，信息获取于2000年至2012年间。该数据集包含64个财务指标和五个数据子集。

表1列出了数据子集的名称、预测期内财务比率的提取年份、破产状态、每个类别标签的样本数量以及实例总数。研究中考虑的属性在图（5.2）中有详细定义。

## 表5 使用G-mean的破产预测模型性能。

| 特征选择方法 | 分类器 | 第1年 | 第2年 | 第3年 | 第4年 | 第5年 |
|---|---|---:|---:|---:|---:|---:|
| SBS | SBSAda-Rip | **92.9** | **88.1** | **89.1** | **87.2** | **81.4** |
| SBS | AdaBoost+ C4.5 | 78.5 | 73.6 | 72.2 | 63 | 76.2 |
| SBS | AdaBoost+OneR | 77.9 | 63.9 | 57.4 | 64.7 | 75.4 |
| SBS | AdaBoost+PART | 90.2 | 76.6 | 83.7 | 64.1 | 64.2 |
| SBS | AdaBoost+CART | 85 | 90.6 | 65.8 | 57.6 | 91 |
| SBS | AdaBoost+RF | 79.6 | 75.3 | 80.2 | 54.6 | 78.6 |
| SFS | AdaBoost+JRip | 87 | 78.1 | 80.3 | 78.6 | 81.8 |
| SFS | AdaBoost+ C4.5 | 78.7 | 66.2 | 70.8 | 49.5 | 74.1 |
| SFS | AdaBoost+OneR | 79.6 | 47.5 | 53.5 | 61.4 | 73.3 |
| SFS | AdaBoost+PART | 94.5 | 74.7 | 81.3 | 66.7 | 75.1 |
| SFS | AdaBoost+CART | 91.5 | 76.2 | 67.7 | 79.5 | 91 |
| SFS | AdaBoost+RF | 83.7 | 63.9 | 69.4 | 41 | 79.4 |
| PSO | AdaBoost+JRip | 89.1 | 85.5 | 82 | 84.6 | 79.4 |
| PSO | AdaBoost+ C4.5 | 82.2 | 85.2 | 65.2 | 63.2 | 71.3 |
| PSO | AdaBoost+OneR | 74.2 | 40.1 | 63.3 | 57.5 | 77.4 |
| PSO | AdaBoost+PART | 72.3 | 73.6 | 62.1 | 65.1 | 78.7 |
| PSO | AdaBoost+CART | 86.5 | 74.3 | 65.5 | 77.5 | 91 |
| PSO | AdaBoost+RF | 69.4 | 61.5 | 54.8 | 56 | 76.6 |
| RSFS | AdaBoost+JRip | 92.2 | 87.3 | 73.6 | 76.8 | 87.4 |
| RSFS | AdaBoost+ C4.5 | 78.4 | 82 | 72.4 | 67 | 72.4 |
| RSFS | AdaBoost+OneR | 71.2 | 41.5 | 60.1 | 66 | 77.6 |
| RSFS | AdaBoost+PART | 72.3 | 67 | 61.3 | 63.6 | 76.7 |
| RSFS | AdaBoost+CART | 86.5 | 72.5 | 68.1 | 79 | 81.6 |
| RSFS | AdaBoost+RF | 69.4 | 55.7 | 54.3 | 43.7 | 72.8 |

表6展示了本研究中所有算法在F-measure方面的性能。该表显示，与表5类似，其他算法的某些实例略优于我们提出的方法。然而，与我们的技术性能（范围在94.3%至97.1%之间）相比，很明显其平均表现优于其他算法，因为它在所有数据集上保持稳定结果。这使我们验证了`SBSAda-Rip`在企业破产预测中的性能。

## 表6 使用F-measure的破产预测模型性能。

| 特征选择方法 | 分类器 | 第1年 | 第2年 | 第3年 | 第4年 | 第5年 |
|---|---|---|---|---|---|---|
| SBS | SBSAda-Rip | 97.1 | 96.1 | 95.8 | 96.1 | 94.3 |
| SBS | AdaBoost+ C4.5 | 95.6 | 95.4 | 94.8 | 93.8 | 93 |
| SBS | AdaBoost+OneR | 95.8 | 94.9 | 94.2 | 94 | 93.2 |
| SBS | AdaBoost+PART | 96.5 | 95.8 | 95.5 | 93.7 | 91.3 |
| SBS | AdaBoost+CART | 96.2 | 95.8 | 94.7 | 95.3 | 93.6 |
| SBS | AdaBoost+RF | 94.6 | 95.3 | 94.9 | 93.1 | 92.9 |
| SFS | AdaBoost+JRip | 96.8 | 95.8 | 96.1 | 95.6 | 94.4 |
| SFS | AdaBoost+ C4.5 | 95.7 | 95.2 | 95.1 | 93.1 | 92.5 |
| SFS | AdaBoost+OneR | 95.5 | 94.5 | 94.1 | 93.9 | 93 |
| SFS | AdaBoost+PART | 96.8 | 95.4 | 95.3 | 94 | 93 |
| SFS | AdaBoost+CART | 96.9 | 95.3 | 94.7 | 95.3 | 93.6 |
| SFS | AdaBoost+RF | 95.7 | 94.9 | 94.5 | 92.9 | 93 |
| PSO | AdaBoost+JRip | 96 | 96.4 | 95.7 | 95.2 | 94.1 |
| PSO | AdaBoost+ C4.5 | 95.2 | 95.9 | 94.6 | 93.7 | 92.5 |
| PSO | AdaBoost+OneR | 94.9 | 94.3 | 94.4 | 93.5 | 93.2 |
| PSO | AdaBoost+PART | 94.9 | 95.2 | 94.7 | 93.8 | 92.4 |
| PSO | AdaBoost+CART | 96.5 | 95.3 | 94.7 | 95.2 | 93.6 |
| PSO | AdaBoost+RF | 94.6 | 94.8 | 94.1 | 93.1 | 92.4 |
| RSFS | AdaBoost+JRip | 96.8 | 96.5 | 95.3 | 95 | 94.2 |
| RSFS | AdaBoost+ C4.5 | 95.1 | 95.4 | 94.5 | 93.6 | 92.4 |
| RSFS | AdaBoost+OneR | 94.7 | 94.3 | 94.4 | 93.8 | 93.4 |
| RSFS | AdaBoost+PART | 94.9 | 95 | 94.4 | 93.7 | 93.1 |
| RSFS | AdaBoost+CART | 96.5 | 95.1 | 94.7 | 95.4 | 94.2 |
| RSFS | AdaBoost+RF | 94 | 95.5 | 94 | 92.9 | 91.9 |

#### 5.6.3 研究问题2的结果

已有大量研究成功预测了企业破产。因此，我们分析了我们的方法与在同一波兰数据集上采用的不同技术的性能对比。表7展示了其他研究及我们自己的研究结果。该比较考虑了两个因素：`AUC`指标和模型的可解释性。可解释性考察分类器提取决策规则的能力、这些规则的数量以及提取的特征数量。

## 表7. 我们的模型与波兰破产数据集上类似工作的比较。

|  | 方法 | AUC | 提取特征数 | 规则数 |
|---|---|---:|---:|---:|
| 我们的模型 (Zięba *等*, 2016) (Q. Zhang, Wang, Lu, Wang, & Ma, 2018) (Tuong, Son, Vo, Lee, & Baik, 2018) (Uthayakumar, Metawa, Shankar, & Lakshmanaprabu, 2018) | SBSAda-Rip | 94.5 | 26 | 4 |
|  | LDA | 63.9 | - | - |
|  | MLP | 54.3 | - | - |
|  | LR | 62.0 | - | - |
|  | JRip | 52.3 | - | - |
|  | CJRip | 74.5 | - | - |
