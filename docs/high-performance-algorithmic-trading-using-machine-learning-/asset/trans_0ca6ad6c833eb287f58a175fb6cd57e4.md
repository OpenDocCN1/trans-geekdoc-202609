
`selected_features_mask = sel2.get_support()`

# 获取所选特征的列标签

`X_train.columns[selected_features_mask]`

作为回报，我们获得了所选特征的列表：

`['Adj Close_ret', 'Low_ret' , 'Relative_Change_Open_Close_ret' , 'BBB_20_2.0_ret', 'High_1', … ]`

### 递归特征消除

给定一个分配重要性[25](#chap06.xhtml#footnote-096)（权重）给特征的外部估计器（`clf`），递归特征消除（RFE）的目标是通过递归地考虑越来越小的特征集来选择特征。首先，估计器在初始特征集上进行训练，并获得每个特征的重要性。然后，从当前特征集中剔除最不重要的特征。该过程在剪枝后的特征集上递归重复，直到达到所需的选择特征数量。

```
from sklearn.feature_selection import RFE

sel3 = RFE(clf, n_features_to_select = k_best , step = 0.3)

sel3.fit(X_train, y_train)

sel3.get_feature_names_out()[:100]
```

以下是所选特征的一小部分摘录：

```
['Gap_Previous_Close', 'CCI', 'GOOG_Adj Close_ret', 'AMZN_Open_ret',
'TSLA_Low_ret', 'NVDA_Low_ret', 'IBM_Low_ret', 'IBM_Adj Close_ret',
'Close_diff_frac_0.2_ret', 'Price_Momentum_ret', 'BBB_20_2.0_ret',
'MSFT_Volume_5', 'IBM_Open_4', 'IBM_Low_3', 'IBM_Volume_3',
'IBM_Volume_5', 'Price_Momentum_3', 'Intraday_Price_Range_1',
'Intraday_Price_Range_4', 'Intraday_Price_Range_5','Closing_Position_1', 'Gap_Previous_Close_5','Relative_Change_Open_Close_3' 'Normalized_Volume_Weighted_Close_1', 'MACD_Histogram_3',
'Open_ret_5', 'Adj Close_ret_3', …]
```

`RFE` 迭代地移除最不重要的特征，直到只保留最相关的特征。上述代码演示了如何使用分类器（`clf`）对特征重要性进行排序并选择前 `k_best` 个特征来应用 `RFE`。

拟合模型后，`get_feature_names_out()` 函数检索对预测贡献最大的最有信息量的特征。以下是所选特征的示例，其中包括技术指标（例如 `CCI`、`MACD_Histogram`）、基于价格的变换（例如 `Gap_Previous_Close`、`Intraday_Price_Range`）和分数阶差分（`Close_diff_frac_0.2_ret`）。这些所选特征通过减少噪声并专注于最有影响力的变量，增强了模型的预测能力。

在 `RFE` 识别出最相关的特征后，我们现在将探索使用降维技术（如 `PCA` 和 `UMAP`）进行特征选择。

### 使用 PCA 和 UMAP 进行特征选择

之前，我们将 `PCA` 和 `UMAP` 作为特征工程的方法进行了讨论。这些技术常用于特征选择阶段。在这些场景中，原始特征被替换为从 `PCA` 或 `UMAP` 衍生出的新特征。

与其简单地为模型输入选择合适的特征，重点转移到使用所有特征并利用 `PCA` 或 `UMAP` 技术将它们合并。这种方法创建了一组具有降低维度的新特征。对于实现部分，我们已经在前面专门介绍 `UMAP` 的章节中展示了代码。

现在我们知道了如何选择重要特征，让我们看看当你想从这些方案中的每一个的优点中受益时该如何进行。

### 使用集合运算符组合最佳特征

集合运算符是组合所有这些特征提议的合适答案。在本例中，我们结合了前几节中介绍的三种竞争性特征选择方法（`sel1`、`sel2` 和 `sel3`）的提议：

```
sel1 = SelectPercentile(mutual_info_classif, percentile = pct , n_neighbors = 10)

# 使用互信息初始化 SelectKBest
sel2 = SelectKBest(mutual_info_classif, k = k_best) 
sel3 = RFE(clf, n_features_to_select = k_best , step = 0.3)
```

集合方法将所选特征封装在集合中：

```
set1 = set(sel1.get_feature_names_out())
set2 = set(sel2.get_feature_names_out())
set3 = set(sel3.get_feature_names_out())
```

使用集合运算符 `union`[26](#chap06.xhtml#footnote-095) 和 `intersection`[27](#chap06.xhtml#footnote-094) 来组合集合：

```
set1or2 = set1.intersection(set2)
print(len(set1or2))
set1or2or3 = set1or2.union(set3)
```

在竞争性特征选择方法的特征集的 `union`（并集）和 `intersection`（交集）之间进行选择取决于上下文：

- 对于观测值数量有限（与特征数量相比）的数据集，`intersection` 是避免过拟合的更安全选择。
- 如果特征选择方法从根本上不同且互补（例如，一种基于统计，如 `mutual_info_classif`，另一种基于模型，如 `RFE`），它们的 `union` 可能会产生一个更全面的特征集。当方法互补且有足够数据支持更大的特征集时，`union` 是有益的。否则，`union` 可能导致更大的特征集，这可能会增加模型的复杂性并可能导致过拟合。

## 结论

在本章结束时，我们了解了如何掌握优化机器学习模型性能所必需的特征工程和特征选择技术。

这不仅适用于预测性能，同样重要的是适用于机器学习模型的后期生产、部署和维护方面。这些方面统称为机器学习运营（`ML-Ops`）。我们还应该提到，特征选择在生产环境中具有实际好处。特征较少的模型通常运行更快、更易于解释且更具成本效益，特别是在处理大型数据集时。

现在我们已经拥有了坚实的机器学习基础，准备好探索高级算法了。

在下一章中，我们将专注于复杂的机器学习方法，范围从集成技术到持续在线学习方法。

---

- `H` 是随机变量 `X` 的熵
- `p(x_i)` 是第 `i` 个结果出现的概率
- 求和遍历 `X` 的所有 `n` 个可能结果

**加入我们书籍的 Discord 空间**

加入书籍的 Discord 工作区，获取最新动态、优惠、全球科技动态、新版本发布和作者见面会：

[https://discord.bpbonline.com](https://discord.bpbonline.com)

![Discord](images/Discord.png)

# 第 7 章  

## 交易的高级机器学习模型

### 简介

本章探讨了算法交易的高级机器学习技术，研究了超越传统监督学习的方法。我们将研究最先进的集成方法和在线学习方法，以改进交易策略。

本章首先深入探讨集成方法，通过组合多个模型来提高预测准确性并减少过拟合。然后我们讨论 Boosting、Bagging 以及 `XGBoost` 和 `LightGBM` 等特定算法，重点介绍它们在算法交易中的应用。

本章还探讨了高级回归方法，包括最小绝对收缩和选择算子（`LASSO`）和岭回归，并深入分析了它们在金融预测中的有效性。此外，我们将探索在线学习，考察 `Scikit-multi flow` 等工具以展示它们在实时金融信号跟踪中的作用。本章的目标是提供对这些高级方法的全面理解，以便读者能够有效地应用它们。

### 结构

在本章中，我们将涵盖以下主题：

- [理解高级机器学习](#chap07.xhtml#h32)
- [集成方法简介](#chap07.xhtml#h33)
- [用于分类的高级集成方法](#chap07.xhtml#h34)

