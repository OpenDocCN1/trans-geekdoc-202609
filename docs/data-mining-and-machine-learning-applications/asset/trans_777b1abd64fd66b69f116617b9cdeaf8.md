

![](img/48ffcb334b2fea865a1f194394911123_130_0.png)

图 4.8 MOA 中的聚类可视化。

![](img/48ffcb334b2fea865a1f194394911123_130_1.png)

图 4.9 MOA 中的概念漂移检测技术。

![](img/48ffcb334b2fea865a1f194394911123_131_0.png)

图 4.10 MOA 中的主动学习算法。

![](img/48ffcb334b2fea865a1f194394911123_131_1.png)

图 4.11 MOA 中可用的异常值检测算法。

![](img/48ffcb334b2fea865a1f194394911123_132_0.png)

图 4.12 MOA 中的异常值可视化。

## 4.5.2 Python 中的实现

Python 提供了借助 multiflow API 实现数据流挖掘操作的功能，multiflow API 是 Scikit 的一部分，是机器学习的标准 Python API。Multiflow 由 Montiel 等人 [17] 开发。要使用 Python 流挖掘 API，用户需要先使用 pip 或 conda 命令安装 multiflow 包，例如：

```
pip install -U scikit-multiflow
```

与 Java MOA API 类似，multiflow 也为实现数据流挖掘操作提供了一个标准框架。multiflow API 大致分为七个主要部分，即核心、数据、学习方法、漂移检测、评估、转换和杂项 API。

- **核心** multiflow API 的核心模块包含所有主要数据流挖掘操作类的基类。例如，为了与 scikit-learn 包兼容而包含的基估计器类，以使 multiflow 数据流挖掘操作与基本的 Python 分析和学习操作兼容。同样，分类器、回归和元估计器的混入类也包含在 multiflow 包的核心包中。

- **数据** 在 Python 中，使用 multiflow 的数据模块进行流生成。它提供从数据源或文件创建流的选项。它还提供带有概念漂移或时序数据流的流生成选项。它具有多种用于生成流的算法，主要算法包括 LED 流生成器、超平面生成器、随机 RBF 生成器、随机树生成器、SEA 生成器、正弦生成器、交错生成器、波生成器、多标签生成器和回归流生成器。

- **学习方法** 学习方法模块包括异常检测方法、基于概率的朴素贝叶斯分类器、惰性学习方法和集成方法的实现。惰性学习方法进一步包括 KNN 分类器、带有 ADWIN 变化检测器的 KNN 分类器、自调整内存耦合 KNN 分类器和 KNN 回归分类器的实现。集成方法进一步包括准确度加权分类器、自适应随机森林、加性专家分类器、带多标签学习的分类器链、蒙特卡洛采样分类器、动态加权多数分类、Learn++.分类器、在线 AdaC2 分类器、在线提升分类器、在线 CSB2 分类器、在线 CSB2 分类器、在线 SMOTE 袋装分类器、Oza 袋装分类器、带有 ADWIN 变化分类器的 Oza 袋装、多输出分类器的回归器链和流式随机补丁集成分类器的实现。

- **神经网络** 神经网络模块提供了用于借助神经网络处理流数据的感知器算法的掩码实现。

- **基于原型的方法** 此原型提供了用于流数据和非流数据的稳健软学习向量量化算法的实现。

- **基于规则的方法** multiflow 的基于规则的方法中提供了非常快速的决策规则分类器。

- **基于树的方法** Multiflow 模块还为流挖掘操作提供了基于树的学习方法的实现。其中可用的关键算法有：Hoeffding 自适应树分类器、Hoeffding 树或非常快速决策树分类器、极快速决策树分类器、带多标签分类的标签组合 Hoeffding 树分类器、Hoeffding 树回归器、Hoeffding 自适应树分类器、增量结构化输出预测树和堆叠单目标 Hoeffding 树回归器算法。

- **漂移检测** 漂移检测模块通过 multiflow 模块提供了 Python 中各种概念漂移检测技术的实现。它包括 ADWIN 算法、漂移检测方法、早期漂移检测方法以及使用移动平均和加权平均方法的 Hoeffding 边界漂移检测、Kolmogorov–Smirnov 窗口方法和 Page–Hinkley 方法的实现，用于概念漂移检测。

- **评估** 在 multiflow 中，multiflow API 存在三种用于数据流挖掘操作评估的评估策略。这些评估方法是保留评估（holdout evaluation）、预quential 评估（prequential evaluation）和延迟预quential 评估方法。参数准确度、Kappa、精确率、召回率、F-度量和 G-mean 用于 multiflow API 中分类算法的评估。对于多目标分类，使用汉明得分、汉明损失、精确匹配和 J 索引参数。对于回归技术，使用均方误差、平均绝对误差和平均根均方误差。对于多目标回归，使用平均均方误差、平均绝对误差和平均根均方误差。

## 4.5.3 R 中的实现

R 编程语言中的流数据挖掘通过 stream 包提供。stream 包由 Hahsler 等人 [18] 开发，为流聚类的聚类和动画提供了一种简单且美观的方法。图 4.13 给出了执行数据流聚类的示例代码片段及其输出。聚类可视化示例输出显示在图 4.14 中。

图 4.15 显示了 R 中用于聚类动画的另一个代码片段，动画输出显示在图 4.16 中。

- **流生成和聚类算法** BICO（K-means 核心集算法）、BIRCH（使用层次结构的平衡迭代缩减聚类）、DBSCAN（基于密度的聚类算法）、DBSTREAM、D-Stream、进化算法、层次微聚类重聚类算法、K-means、Sample（来自数据流的固定大小样本）、Window（来自数据流的滑动窗口）以及 Bars and Gaussians 生成器。

```
>>stream <- DSD_Gaussians(k=5, d=2)
>>stream <- DSC_DStream(gridsize=0.05, Cm=1.5)
>>update(stream, stream, 500)
>>plot(dstream, stream)
>>evaluate(dstream, stream, measure=c("numMicro","numMacro","purity","crand","SSQ"),
...   n = 100)
Evaluation results for micro-clusters.
Points were assigned to micro-clusters.
   numMicroClusters numMacroClusters    purity    cRand        SSQ
25.0000000 5.0000000   0.9145658 0.1286303  0.4904225
```

**图 4.13** 演示用于流聚类的 R stream 包的代码片段。

![](img/48ffcb334b2fea865a1f194394911123_135_0.png)

图 4.14 用于流聚类的 R stream 包的输出。

```
>stream <- DSD_Gaussians(k=5, d=2)
>dstream <- DSC_DStream(gridsize=0.05, lambda=0.1)
>animate_cluster(dstream, stream, horizon=100, n=5000,
+     measure=c("crand","type","macro","assign="micro",
+     plot.args = list(type="both", xlim=c(0,1), ylim=c(0,1)))
```

图 4.15 来自 R stream 包的聚类动画代码片段。

![](img/48ffcb334b2fea865a1f194394911123_135_1.png)

图 4.16 来自 R stream 包的聚类动画。

为了评估流数据聚类的性能，stream 包中包含了众多性能参数。用于评估流聚类的关键参数包括微聚类数量、宏聚类数量和类别数量。

该包提供了三个与噪声相关的参数，即：预测为噪声的数据点数量、实际为噪声的数据点数量以及预测噪声的精确度。

流聚类评估参数大致分为两类，即内部评估度量和外部评估度量。R 的 stream 包提供了这两类性能参数的实现。内部评估度量包括簇内平方和、轮廓系数、簇间平均距离、簇内平均距离、最大簇直径、最小簇分离度、簇内平方和、Goodman 和 Kruskal 的 Gamma 系数、Pearson Gamma 相关系数、Dunn 指数和聚类成员的熵。外部评估度量包括精确率、召回率、F1 度量、纯度、欧氏不相似度、曼哈顿不相似度、Rand 指数、调整 Rand 指数、归一化互信息、Katz–Powell 指数、协议间夹角的最大余弦、最大共分类率、Fowlkes 和 Mallows 的索引、Jaccard 指数、预测强度和信息变化量。

## 4.6 应用

随着物联网的发明和基于先进互联网的在线应用的发展，大量连续数据作为数据流产生。挖掘此类数据流可以产生有用的知识和模式，利用这些知识和模式可以为各种应用开发智能和智慧系统。本节讨论了数据流挖掘的一些主要应用。

### 4.6.1 股票市场中的股票预测

股票市场是不仅利用机器学习技术，还利用深度学习等先进技术来预测股票价格的领域。由于股票市场本身具有波动性，在工作时间的每一刻，特定股票的价格都会波动。这些波动是由于各种因素造成的，价格

