

## 3.3 宫颈癌的风险因素（分类）

你也可以去 YouTube 查看评论区。但请不要陷入“YouTube 地狱”，最后一直在看猴子在沙滩上偷游客并喝游客喝鸡尾酒的视频。Google 的垃圾邮件检测器自 2015 年以来可能也发生了很大变化。

在此处查看播放记录视频“江南江南风”⁵。

如果你想尝试处理这些数据，可以在书的 Github 仓库中找到 RData 文件⁹以及带有一些便利函数的 Rscript¹⁰。

## 3.3 宫颈癌的风险因素（分类）

宫颈癌数据集包含了预测女性是否会患上宫颈癌的指标和风险因素。特征包括人口统计学数据（如年龄）、生活方式和病史。数据可以从 UCI 机器学习库¹¹ 下载，并由 Fernandes、Cardoso 和 Fernandes (2017)¹² 描述。

书中示例中使用的特征子集为：

- 年龄（岁）
- 性伴数量
- 首次性行为年龄（年龄，岁）
- 怀孕次数
- 是否吸烟（是/否）
- 吸烟年数（年）
- 是否使用激素避孕药（是/否）
- 使用激素避孕药时长（年）
- 是否使用宫内节（IUD）
- 使用宫内节年数（年）
- 患者是否曾患过性传播疾病（STD）（是/否）
- STD 诊断次数
- 距离首次 STD 诊断以来经过的时间
- 距离上一次 STD 诊断以来经过的时间
- 活检结果“健康”或“癌症”。这是目标输出。

活检是诊断宫颈癌的金标准。对于书中的示例，活检结果被用作目标。每列的缺失值通过众数（出现频率的值）进行填充，这可能是一个糟糕的解决方案，因为真实答案可能与值缺失的概率相关。可能存在

> ⁸https://www.youtube.com/watch?v=9bZkp7qi98?feature=player_embedded
⁹https://github.com/christophM/interpretable-ml-book/blob/master/data/ycomments.RData
¹⁰https://github.com/christophM/interpretable-ml-book/blob/master/R/Get-Spam-Tute-dataset.R
¹¹https://arxiv.org/ml/datasets/Cervical-cancer+%28Risk-Factors%29

> ¹²Fernandes, Kelvin, João Cardoso, and Jessica Fernandes. “Transfer learning with partial observability applied to cervical cancer.” In Iberian Conference on Pattern Recognition and Image Analysis, 24–50. Springer. (2017).

偏差，因为这些问题具有很强的私密性。但这不是一本关于缺失值填充的书，所以众数填充对于示例来说。

要用此数据集重现书中的示例，请在书的 Github 仓库中找到预处理 R 脚本$^{13}$ 和最终的 RData 文件$^{14}$。

$^{13}$https://github.com/christophM/interpretable-ml-book/blob/master/R/get-cervical-cancer-dataset.R
$^{14}$https://github.com/christophM/interpretable-ml-book/blob/master/data/cervical.RData

## 4 可解释模型

实现解释性最简单的方法是仅使用创建可解释模型的算法子集。线性回归、逻辑回归和决策树是常用的可解释模型。

在接下来的章节中，我们将讨论这些模型。不会进行详细阐述，只介绍基础知识，因为有大量的书籍、视频、教程、论文和更多材料可用。我们将重点关注如何解释模型。书中更详细地讨论了线性回归、逻辑回归、其他线性回归扩展、决策树、决策规则和 RuleFit 算法。它还列出了其他可解释模型。

书中解释的所有可解释模型都是模块化解释的，最近邻方法除外。下表提供了可解释模型类型及其概述。如果特征与目标之间的关联是线性建模，则是线性的。单调性约束确保特征与目标结果在整个范围内方向相同：特征值的增加会导致目标的增加或减少。单调性对于解释很有用。某些模型可以提高性能，但过多的交互会损害可解释性。

| 算法 | 单调性 | 交互 | 任务 |
|---|---|---|
| 线性回归 | 是 | 是 | 回归 |
| 逻辑回归 | 否 | 是 | 分类 |
| 决策树 | 否 |  | | 分类 |
| RuleFit | 是 | 是 | 回归 |
| 朴叶贝斯 | 否 | 否 | 分类 |
| 最近邻 | 否 | 否 | 分类 |

## 4.1 线性回归

线性回归模型通过特征的加权和来预测目标。线性回归长期以来被统计学家、计算机科学家和其他人员使用。对于单个实例，它可以写为：

$$y = \beta_0 + \beta_1 x_1 + ... + \beta_p x_p + \epsilon$$

betas ($\beta_j$) 代表学习到的权重或系数。截距和  epsilon ($\epsilon$) 是我们仍然犯的错误。假设这些误差遵循高斯分布，这意味着它们会在正负两个方向出现。

可以使用各种方法来估计权重，以最小化实际结果与估计结果之间的平方差：

$$\hat{\beta} = \arg \min_{\beta} \sum_{i=1}^n \left( y^{(i)} - \left( \beta_0 + \sum_{j=1}^p \beta_j x_j^{(i)} \right) \right)^2$$

我们不会详细介绍如何找到最优权重，但如果你感兴趣，可以阅读《统计学习方法》第 3.2 节（Friedman, Hastie and Tibshirani 2009)$^1$。估计的权重可以带有置信区间。置信区间是权重估计的一个范围，以一定的置信度覆盖“真实”权重。例如，权重 2 的 95% 置信区间范围可能从 1 到 3。该区间的解释是：如果我们使用新采样的数据重复估计 100 次，置信

> ^1Friedman, Jerome, Trevor Hastie, and Robert Tibshirani. "The elements of statistical learning." www.stanford.edu/~hastie/ElemStatLearn/(2009).

