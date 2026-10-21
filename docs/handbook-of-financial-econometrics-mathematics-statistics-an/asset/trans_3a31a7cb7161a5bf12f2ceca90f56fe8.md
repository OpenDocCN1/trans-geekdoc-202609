
结果还表明，使用 RBF 核优于使用线性核。此外，我们还利用 MLP 模型来学习隐藏且复杂的关系。MLP 是一种前馈人工神经网络模型，可将输入数据集映射到一组适当的输出。MLP 由有向图中的多层节点组成，每一层与下一层全连接。在我们的工作中，模型结构使用一个隐藏层，并使用 sigmoid 作为激活函数。标准反向传播算法用于神经网络的监督训练。

特征提取与预测的过程如算法 1 所示。

### 算法 1 特征提取与预测的过程

```
Input: Users U and tweets X from Xueqiu, firm-specific factors F of stock S_i at trading day t_j^i
Output: Stock movement y_j^i at next trading day t_{j+1}^i
function SPECIFICFEATURE(F, s_j^i)
    Extracting firm-specific features: f_j^i ← F for stock s_j^i at t_j^i;
    return f_j^i
end function
function SENTIMENTSCORE(X, U, s_i)
    Counting the number of tweets in the positive category (i.e., x) and negative category (i.e., y) respectively;
    Constructing the user forwarding network;
    PageRank value for user u_t : PR(v_t) ← Σ PR(u_i)/L(u_i);
    Positive weighted count: PositiveCount ← Σ_x PR(u(x))
    Negative weighted count: NegativeCount ← Σ_y PR(u(y))
    Sentiment Score: SC_j^i ← PositiveCount_j^i / (PositiveCount_j^i + NegativeCount_j^i);
    return SC_j^i
end function
function RELATEDNESSFEATURE(f_j^i, X, s_i)
    Constructing the stock network: G = {V, E};
    Correlation between stock s_i and s_k : r_j^{i,k} ← (Σ_{k=1}^N r_j^{i,k} f_k) / (Σ_{k=1}^N r_j^{i,k});
    Relatedness feature: corr(f_k)_j^i, f_k is a specific feature of stock k;
    return corr(f_k)_j^i
end function
function PREDICTION(f_j^i, SC_j^i, corr(f)^i_j)
    Combining features into a vector: x⃗_j^i ← {f_j^i, SC_j^i, corr(f)_j^i};
    Predicting stock movement: y_j^i ← SVM(x⃗_j^i)(or y_j^i ← MLP(x⃗_j^i));
    return y_j^i
end function
```

## 18.2.4 实验

我们进行实验以评估从雪球获取的特征在预测股票价格变动方面的有效性。

### 18.2.4.1 实验设置

我们使用了 2014 年 11 月至 2015 年 5 月的雪球数据。目标股票从 A 股市场的所有股票中选取，需满足两个要求：(1) 该股票在此期间有超过 10 个交易日；(2) 关于该股票的推文数量每天超过 10 条。雪球中的垃圾内容可能会给我们的分析和预测任务带来较大噪声。为了检测垃圾内容，我们确定了 10 个特征（包括内容中数字的百分比、用户的粉丝数等），并使用逻辑回归来识别它们。然后，我们为每只股票提取雪球相关特征（情感特征和股票关联特征）。股票特定特征则是从通过 TuShare⁴ 获得的历史信息中提取的。雪球上每条推文的情感由 SnowNLP⁵ 分类，这是一个开源的中文文本处理工具包。最终，我们从数据集中获得了约 35.7K 个有效的测试样本。

我们使用 SVM（带 RBF 核）和 MLP 作为预测模型。最后一个月的样本将用作训练集，以预测下一个月每个交易日的股票价格变动。例如，当 2014 年 11 月的样本用作训练集时，2014 年 12 月的交易日即为相应的测试集。预测通过两个常用指标进行评估：分类准确率（ACC）和 ROC 曲线下面积（AUC）。ACC 对数据偏斜非常敏感。当某个类别出现的频率极高时，使用对多数类进行预测的分类器可以获得较高的准确率。因此，我们也使用 AUC 来避免数据偏斜带来的偏差。尽管我们的数据并非严重偏斜，我们仍使用 AUC 进行比较。在对所有这些测试集进行预测后，我们将所有 AUC 和 ACC 结果汇总为一个总体输出。

### 18.2.4.2 预测结果

根据先前的研究（Li 等，2014；Fama 和 French，1992），股票特定特征对于股票预测至关重要，因此我们采用仅使用股票特定特征的预测方法（即 SVM 和 MLP）作为基线。为了验证从雪球中提取的知识是否对股票预测有效，我们将同时使用股票特定特征和雪球特征（即情感特征和股票关联特征）的预测方法与基线进行了对比评估。

![](img/31ee7e6fa5107b22bbf7960ec96106a1_735_0.png)

图 18.6：使用仅含股票特定特征（SSF）的 SVM 和 MLP 与同时含有 SSF 和雪球特征的预测结果。

结果如图 18.6 所示。可以观察到，在给定相同的预测模型（SVM 或 MLP）的情况下，涉及雪球特征的方法在 ACC 和 AUC 指标上均持续优于仅涉及股票特定特征的方法。这证实了从雪球中提取的投资者感知有助于股票预测。这也表明，中国社交媒体能够反映投资者在中国股市中的观点和行为。此外，MLP 模型比 SVM 模型取得了更好的性能，部分原因在于有效学习了特征与价格变动之间的隐藏关系。基于上述分析，我们可以观察到特征和算法都会对性能产生影响。

### 18.2.4.3 特征重要性分析

特征重要性分析研究在预测任务中各种特征的重要性。从宏观角度来看，我们首先研究源自不同类型知识的特征的重要性。

![](img/31ee7e6fa5107b22bbf7960ec96106a1_736_0.png)

图 18.7：使用 SVM 在不同特征组合上训练的预测结果。

图 18.7 展示了不同特征组的预测结果。毫不奇怪，股票特定特征对股票预测非常有用。仅使用股票特定特征即可在 ACC 上达到 0.57，在 AUC 上达到 0.54。情感特征和股票关联特征都有帮助，且情感特征比股票关联特征发挥更重要的作用。当我们将所有特征放在一起时，ACC 方面的预测结果与同时使用情感特征和股票特定特征时相同，但 AUC 方面的结果可以得到进一步改善。原因在于 ACC 未考虑数据集的不平衡性。AUC 的改善表明，添加股票关联特征可以提高我们模型的判别能力。

然后，我们从微观角度研究特征的重要性。为了评估特征如何对预测结果做出贡献，我们使用随机森林模型来获取特征重要性的排序（Genuer 等，2010），如表 18.3 所示。

**表 18.3：** 最重要的 10 个特征。

| 特征 |
| --- |
| 股票价格变动率 |
| 股票 MA5 值 |
| 股票换手率变动率 |
| 股票交易量变动率 |
| 情感得分 |
| 股票交易量 5 日均值 |
| 情感推文数量（正面） |
| 关联股票加权平均值（MA5） |
| 情感推文数量（负面） |
| 情感推文数量（中性） |

很明显，股票特定特征是模型中影响最大的特征类型，因为前 4 个特征都属于该类型。在考虑附加特征时，情感特征比股票关联特征更重要，这与上文图 18.7 中的特征分析一致。在情感特征中，情感得分是最关键的，它不仅包含推文内容，还包含用户网络的结构。关联股票加权平均值（MA5）位列前 10 个特征之中，表明它也对我们的任务有用。

### 18.2.4.4 总结

我们通过以下观察结果来总结实验结论：

- 1. 从雪球中提取的知识对股票预测有用。结果表明，通过利用雪球的知识，ACC 和 AUC 方面的预测结果都能得到持续改善。先前的研究显示了情感在美国股市预测中的有效性。我们的研究证实，从雪球中提取的情感对中国股市同样有效。此外，我们还观察到用户感知的股票关联在股票预测中的有效性。
- 2. 股票特定特征对预测任务至关重要。仅使用股票特定特征的预测结果和特征重要性分析都表明，股票特定特征是我们任务中最重要的特征。
- 3. 情感特征比股票关联特征更有用。一个可能的原因是用户感知的股票关联比情感更稀疏。在推文中，只有少数股票会与其他股票同时被提及，尤其考虑到我们的股票网络是时间敏感的，即只考虑最近 3 天的共现。尽管存在稀疏性，预测结果对于市场中几乎全部股票来说都相当不错。
