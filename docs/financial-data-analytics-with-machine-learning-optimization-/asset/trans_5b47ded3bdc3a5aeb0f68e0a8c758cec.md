

# 12.5.6.1 金融领域的银行客户流失

银行客户流失数据集

CIBer 具有相似的能力和功能，用于拟合

在拟合模型之前，需要准备数据集。在 Programm 12.2 中通过 Python，`pd.factorize` 是一个 `pandas` 函数，用于将分类特征的值联合编码为离散值。

然后在 [Programme 12.3](#c12.xhtml#c12-sec-3003) 中通过 Python，我们将数据集分为训练集和测试集。由于该数据集高度不平衡，我们抽取 7,000 个数据点作为训练数据集，然后从每个类别中选取 200 个数据点作为测试数据集。

在 Programm 12.4 中使用 Python，`cont_col` 是连续特征变量的索引列表，而 `min_asso` 是用于衡量所有特征变量对之间线性关联度的最小阈值，可通过网格搜索找到。要拟合 CIBer，我们创建一个名为 `CIBer_clf` 的 CIBer 对象，然后使用训练数据集 `X_train` 及其标签集 `y_train` 拟合模型。最后，我们通过分别调用函数 `predict()` 和 `predict_porba()`，从 CIBer 中获取预测结果及其对应的概率。

[Figure 12.7](#c12.xhtml#c12-fig-0007) 显示了每个分类器的 `F1`‐分数箱线图。我们立即观察到，CIBer 在 `δ = 0.05` 时（记为 `CIBer (Normal)`）的 `F1`‐分数略高于 CIBer 在 `δ = 0` 时（记为 `CIBer (No CM)`）的 `F1`‐分数，后者不涉及任何共单调结构。此外，CIBer 两个箱线图的范围均小于复合朴素贝叶斯和高斯朴素贝叶斯分类器的范围，且其位置也高于后两者，表明 CIBer 中应用的特征工程技术同时提升了朴素贝叶斯分类器的鲁棒性和有效性。

![FIGURE 12.7 Boxplot of upper F 1‐score for each classifier in the bank churners dataset.](images/c12f007.png)

[**FIGURE 12.7**](#c12.xhtml#R_c12-fig-0007) Boxplot of `F1`‐score for each classifier in the bank churners dataset.

结果表明，两个版本的 CIBer 均仅次于多层感知机（MLP）和分类（决策）树（DT）。作为一项备注，我们指出，MLP 和分类树获得的结果通常难以解释，而在 CIBer 的情况下，我们能够解释所获得的共单调簇背后的理由。以本数据集为例，我们在实际标签为 `0` 的多数类中获得了一个共单调簇，即 `Card_Category` 和 `Credit_Limit`。具体而言，`Card_Category` 是一个具有四个类别的分类特征，包括 `Blue`、`Silver`、`Gold` 和 `Platinum`，按升序表示信用卡持卡人的状态等级。对于实际标签为 0 的现有持卡人来说，信用卡状态等级越高，信用额度越高，这是自然而然的，这解释了为什么这两个特征是共单调的。另一方面，我们还揭示了一个实际标签为 1 的共单调簇，即 (`Card_Category`、`Avg_Open_To_Buy`）。在少数类中，实际标签为 1 的流失持卡人倾向于较少使用信用卡，导致平均可用额度（average open‐to‐buy）值较大。由于更高级别的信用卡需承担更高的费用和收费，平均可用额度较大的持卡人预计更有可能终止服务。识别这些共单调结构确实带来了一些性能提升，如从 `CIBer (No CM)` 到 `CIBer (Normal)` 的 `F1`‐分数略有增加所示。其他分类器的 `F1`‐分数大致相同，而 `K`‐NN 表现最差。如 [Figure 12.8](#c12.xhtml#c12-fig-0008) 所示，所有分类器的相应准确率箱线图中也得出了类似观察结果。

在不平衡数据集上检查模型性能时，召回率很重要，尤其是当更关注少数类而非多数类时。在本数据集中，银行旨在解决客户流失问题，因此他们专注于对少数类客户做出正确预测。[Figure 12.9](#c12.xhtml#c12-fig-0009) 显示了所有分类器的召回率箱线图。观察发现，两个版本的 CIBer 以及 MLP 和分类树的召回率均约为 0.8，显著高于所有其他竞争者，表明这些分类器在检测客户流失方面表现良好。

![FIGURE 12.8 Boxplots of accuracies for all classifiers in the bank churners dataset.](images/c12f008.png)

[**FIGURE 12.8**](#c12.xhtml#R_c12-fig-0008) Boxplots of accuracies for all classifiers in the bank churners dataset.

![FIGURE 12.9 Boxplots of recall rates for all classifiers in the bank churners dataset.](images/c12f009.png)

[**FIGURE 12.9**](#c12.xhtml#R_c12-fig-0009) Boxplots of recall rates for all classifiers in the bank churners dataset.

# 12.5.6.2 默认保险保费支付

此保险数据集

