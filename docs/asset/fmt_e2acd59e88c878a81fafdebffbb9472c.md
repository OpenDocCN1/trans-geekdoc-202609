
## 2. 尝试为业务用例寻找最佳 ML 问题时，以下哪个方面不在考虑范围内？

1.  模型算法
2.  超参数
3.  指标
4.  数据可用性

## 3. 您的公司希望使用机器学习预测未来 7 天的降雨量。这属于哪种 ML 问题？

1.  分类
2.  预测
3.  聚类
4.  强化学习

## 4. 您在一家大公司工作，每天收到数千张支持工单。您的经理希望您创建一个机器学习模型来检测支持工单是否有效。您会选择哪种类型的模型？

1.  线性回归
2.  二分类
3.  主题建模
4.  多分类

## 5. 您正在为体育运动构建一款先进的相机产品，并希望追踪球。这属于哪种问题？

1.  以当前最先进的算法无法实现
2.  图像检测
3.  视频目标跟踪
4.  场景检测

## 6. 您的公司拥有来自多个研究团队的数百万篇学术论文。您希望以某种方式组织它们，但公司没有关于如何对文档进行分类的政策。您正在寻找任何聚类文档并深入了解热门趋势的方法。您可以怎么做？

1.  无能为力。问题定义不清。
2.  使用简单的回归问题。
3.  使用二分类。
4.  使用主题建模。

## 7. 您永远不会为线性回归选择哪个指标？

1.  `RMSE`
2.  `MAPE`
3.  精确率
4.  `MAE`

## 8. 您正在构建一个机器学习模型来预测房价。您希望确保预测没有极端误差。您会选择哪个指标？

1.  `RMSE`
2.  `RMSLE`
3.  `MAE`
4.  `MAPE`

## 9. 您正在构建一个植物分类模型来预测 `variety1` 和 `variety2`，它们在田间以相等数量存在。您会选择哪个指标？

1.  准确率
2.  `RMSE`
3.  `MAPE`
4.  `R²`

# 机器学习场景题与数据探索

## 场景题

### 10. 引擎裂纹检测模型的指标选择

你为一家大型汽车制造商工作，需要使用 X 射线图像检测发动机中的隐藏裂纹。然而，漏检裂纹可能导致发动机在行驶过程中随机故障。裂纹相对罕见，约每 100 台发动机中出现 1 台。一台特殊相机在发动机通过装配线时拍摄 X 射线图像。你将构建一个机器学习模型来分类发动机是否有裂纹。如果检测到裂纹，发动机将接受进一步测试以验证。你会为分类模型选择什么指标？

1.  `Accuracy`（准确率）
2.  `Precision`（精确率）
3.  `Recall`（召回率）
4.  `RMSE`（均方根误差）

### 11. 无标签训练数据的学习类型

你被要求构建一个分类模型，并获得了一个训练数据集，但数据未标记。你被要求找出使用机器学习处理此数据的方法。你将使用哪种学习类型？

1.  `Supervised learning`（监督学习）
2.  `Unsupervised learning`（无监督学习）
3.  `Semi‐supervised learning`（半监督学习）
4.  `Reinforcement learning`（强化学习）

### 12. 视频推荐系统的 ML 方法

你在一家托管数百万视频、拥有数千用户的公司工作。网站有“点赞”按钮，一些视频获得数千个“赞”。你被要求创建一个机器学习模型，基于收集的所有数据向用户推荐视频，以增加用户在网站上的停留时间。你的 ML 方法是什么？

1.  基于视频流行度的 `Supervised learning`（监督学习）进行预测
2.  基于用户观看视频时长的 `Deep learning model`（深度学习模型）
3.  基于显性反馈的 `Collaborative filtering method`（协同过滤方法）
4.  因为你有一些视频的数据，所以用 `Semi‐supervised learning`（半监督学习）

### 13. 视觉搜索引擎的不良做法

你为一家大型五金连锁店的网络部门工作。你为网站构建了一个视觉搜索引擎。你想建立一个模型来分类图像是否包含产品。每周都有新产品加入产品目录，这些新产品必须纳入视觉搜索引擎。以下哪个选项是坏主意？

1.  创建管道自动化步骤：获取数据集，训练模型。
2.  创建一个 `golden dataset`（黄金数据集），至少一年不更改数据集，因为创建数据集耗时。
3.  频繁扩展数据集以包含新产品并重新训练模型。
4.  将模型评估作为管道的一部分。

### 14. 非机器学习方法

以下哪个选项不是一种机器学习方法？

1.  `Supervised learning`（监督学习）
2.  `Unsupervised learning`（无监督学习）
3.  `Semi‐supervised learning`（半监督学习）
4.  `Hyper‐supervised learning`（超监督学习）

### 15. 模型串联的正确陈述（多选）

你的经理正在讨论一种机器学习方法，询问你关于将一个模型的输出输入到另一个模型的做法。选择两个关于这种方法的正确陈述。

1.  存在许多 `ML pipelines`（机器学习管道），其中一个模型的输出被输入到另一个模型中。
2.  这是一种糟糕的设计，在实践中从不采用。
3.  永远不要将一个模型的输出输入到另一个模型中。这可能会放大错误。
4.  存在多种设计模式，其中一个模型（如 `encoder` 编码器或 `transformer` 转换器）的输出被传递给第二个模型，依此类推。

### 16. 信贷评分模型部署前的关键步骤

你正在构建一个预测信用资质并用于批准贷款的模型。你创建了一个表现极好且影响重大的模型。下一步是什么？

1.  部署模型。
2.  部署模型并将其与系统集成。
3.  移交给软件集成团队。
4.  `Test your model and data for biases (gender, race, etc.)`（测试模型和数据中的偏见，如性别、种族等）。

### 17. 信贷模型的可解释性需求

你构建了一个预测信用资质的模型，训练数据已检查偏见。你的经理仍想知道每个预测的原因以及模型的工作原理。你该怎么做？

1.  获取更多测试数据。
2.  `ML model`（机器学习模型）是黑盒。你无法满足此要求。
3.  `Use model interpretability/explanations`（使用模型可解释性/解释）。
4.  移除所有可能导致偏见的字段（种族、性别等）。

### 18. Android 贴纸应用模型准确率下降的原因

你的公司正在构建一个 Android 应用，在照片上添加滑稽胡须。你构建了一个深度学习模型来检测照片中人脸的位置，基于网上找到的公共照片数据集，模型准确率很高。但集成到 Android 手机应用后，收到关于准确率的负面反馈。可能的原因是什么？

1.  模型未正确部署。
2.  Android 手机无法处理深度学习模型。
3.  `Your dataset was not representative of all users`（你的数据集不能代表所有用户）。
4.  指标错误。

### 19. 癌症预测模型的隐私担忧（多选）

你构建了一个深度学习模型，基于数千份个人记录和扫描预测癌症。数据用于训练和测试。模型受防火墙保护，并采取了所有网络安全预防措施。是否存在隐私担忧？（选择两项。）

1.  没有。不存在隐私担忧。这不包含照片，只有扫描件。
2.  `Yes. This is sensitive data being used.`（是的。正在使用敏感数据。）
3.  没有。虽然使用了敏感数据，但仅用于训练和测试。
4.  `The model could reveal some detail about the training data. There is a risk.`（模型可能泄露训练数据的某些细节。存在风险。）

### 20. 鞋类推荐系统的无效步骤

你为一家在线鞋店工作，公司想增加收入。你有一个大型数据集，包含数千名客户的浏览历史和购物车历史。你被要求创建一个推荐模型。以下哪项不是有效的下一步？

1.  使用你的 `ML model`（机器学习模型）在结账时推荐产品。
2.  `Creatively use all the data to get maximum value because there is no privacy concern.`（创造性地使用所有数据以获取最大价值，因为没有隐私顾虑。）
3.  定期重新训练模型以调整性能并包含新产品。
4.  除了用户历史，还可以在训练模型时使用产品数据（描述、图像）。

---

# Chapter 2：探索数据与构建数据管道

数据收集和清洗是机器学习中的主要步骤，因为你的模型只能像你的数据一样好。机器学习中大部分时间花在清洗数据和特征工程上。在本章中，我们将重点关注数据清洗和探索性数据分析（`EDA`）。我们将讨论数据可视化和统计技术，以检查坏数据（遗漏值、异常值、重复值）。然后我们将介绍如何规范化数据和处理坏数据（如拥有 `data schema` 数据模式），如何处理缺失数据，以及如何检查 `data leakage`（数据泄露）。我们还将介绍如何使用 `TensorFlow Data Validation (TFDV)` 为大规模系统验证数据。

## 可视化

`Data visualization`（数据可视化）是一种数据探索技术，用于发现数据中的趋势和异常值。数据可视化有助于数据清洗过程，因为你可以通过在图表上可视化数据来发现数据是否不平衡。它还有助于特征工程过程，因为你可以通过可视化来选择特征、丢弃特征，并查看特征将如何影响你的模型。

可视化数据有两种方式：

*   `Univariate Analysis`（单变量分析） 在这种分析中，每个特征被独立分析，例如特征的范围以及数据中是否存在异常值。最常用的可视化工具是 `box plots`（箱线图）和 `distribution plots`（分布图）。
*   `Bivariate Analysis`（双变量分析） 在这种分析中，我们比较两个特征之间的数据。这种分析有助于发现特征之间的相关性。执行此分析的一些方法包括使用 `line plots`（折线图）、`bar plots`（条形图）和 `scatterplots`（散点图）。

### Box Plot（箱线图）

#### Box Plots

Box plots help divide observations into defined intervals called `quartiles` and compare them with the entire observation. It represents the data as the 25th, 50th, and 75th quartiles. It consists of a body (the interquartile range, IQR) where most observations are concentrated. The whiskers or lines represent the maximum and minimum values. Points outside the whiskers are considered `outliers`.

Figure 2.1 shows a box plot.

![Figure 2.1 Box plot showing quartiles](img/c02f001.png)

**Figure 2.1** Box plot showing quartiles

### Line Plots

Line plots plot the relationship between two variables to analyze trends in data over time.

Figure 2.2 shows a line plot.

![Figure 2.2 Line plot](img/c02f002.png)

**Figure 2.2** Line plot

### Bar Plots

Bar plots are used to analyze data trends and compare categorical data, such as weekly sales figures, website visitor counts, or monthly product revenue.

Figure 2.3 shows a bar plot.

![Figure 2.3 Bar plot](img/c02f003.png)

**Figure 2.3** Bar plot

### Scatter Plots

Scatter plots are the most commonly used plots in data science, primarily used to visualize clusters in datasets and show the relationship between two variables.

## Statistics Basics

In statistics, we have three measures of central tendency: mean, median, and mode. They help us describe data and can be used to clean data from a statistical perspective.

### Mean

The mean is an accurate measure to describe data when there are no outliers present in the data.

### Median

The median is used when there are outliers in the dataset. You can find the median by arranging the data values from low to high.

If the number of data points is even, the median is the average of the two middle numbers; if odd, the median is the middle value. For example, in the dataset 1, 1, 2, 4, 6, 6, 9, the median is 4. For the dataset 1, 1, 4, 6, 6, 9, the median is 5. Take the average of 4 and 6, which is `(4+6) / 2 = 5`.

### Mode

The mode is used when there are outliers and most of the data is the same. The mode is the value or values that appear most frequently in a dataset.

For example, for the dataset 1, 1, 2, 5, 5, 5, 9, the mode is 5.

### Outlier Detection

The mean is a measure of central tendency affected by outliers, which in turn affects the standard deviation.

For example, consider the following small dataset:

*   `[15, 18, 7, 13, 16, 11, 21, 5, 15, 10, 9, 210]`

It is visible to the naked eye that 210 is an outlier far greater than the other values.

As shown in Table 2.1, adding the outlier caused a significant change in the mean compared to the median and mode. `Variance` is the average of the squared differences from the mean.

**Table 2.1** Mean, Median, and Mode for Outlier Detection

| With Outlier | Without Outlier |
| --- | --- |
| Mean: 12.72 | Mean: 29.16 |
| Median: 13 | Median: 14 |
| Mode: 15 | Mode: 15 |

### Standard Deviation

Standard deviation is the square root of variance. Standard deviation is an excellent method for identifying outliers. Data points that are more than one standard deviation away from the mean can be considered outliers.

### Correlation
