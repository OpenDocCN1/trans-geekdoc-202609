
另一种方法是通过采样参数值来生成大量形状。符合细长型陨石类型的形状构成了一个代表该类型的人工样本（合成数据），并可添加到训练集中，从而形成所谓的**增强数据**。在神经网络的背景下，这种技术被称为**GAN**，即**生成式对抗网络**的缩写。为了评估拟合质量，可使用 R 平方等指标来度量一组合成形状与一组真实形状之间的距离或相似度。使用 GAN 时，会引入一个分类器：如果它无法区分细长的合成形状与真实数据中的细长陨石，则该类别的合成数据被视为优良。Python 中 GAN 的实现见文献[\[1\]](#Chp001_1-34_B9780443218576000059.xhtml#br0005)。一些作者使用效用指标[\[4\]](#Chp001_1-34_B9780443218576000059.xhtml#br0020)来衡量合成数据与其所代表的真实数据之间的拟合质量。

在第 [1.3.4.3](#Chp001_1-34_B9780443218576000059.xhtml#s0095) 节（聚类）中，我使用了非高斯分布的混合模型。经典但不够通用的方法是使用**高斯混合模型**（GMM），并利用**EM 算法**估计各成分的权重。

最后，要生成类似第 [1.3.3](#Chp001_1-34_B9780443218576000059.xhtml#s0065) 节所述的合成时间序列（典型例子为海洋潮汐），可采用与陨石问题相同的流程。经过标准化（例如去趋势）后，真实数据集可能包含不同类别：具有 2、3 个或更多周期的时间序列、大或小振幅、高或低频率（快或慢振荡）、平滑或混沌。每个类别对应参数空间中参数值的一个子集。要向特定类别添加合成数据，可用相关参数子集中的参数值模拟时间序列，或模拟大量时间序列并为每个序列分配一个类别：即与数据集中某种特定类型的时间序列最匹配的类别。为训练集中完全没有的模拟时间序列创建新类别。与真实数据的比较基于训练集中的估计参数值，而非时间序列本身。这些参数汇总了时间序列，使得时间序列聚类变得容易。它们的估计方法见第 [1.3.3](#Chp001_1-34_B9780443218576000059.xhtml#s0065) 节。这引出了**可解释 AI**，区别于那些无法解释为何将特定时间序列归入特定类别的方法。

## 参考文献

- [\[1\]](#Chp001_1-34_B9780443218576000059.xhtml#cf0400) A. Géron, *Hands-on Machine Learning with Scikit-Learn, Keras & TensorFlow*. 第三版 O'Reilly; 2023.
- \[2\] R. Halir, J. Flusser, *Numerically stable direct least squares fitting of ellipses*. \[预印本, pp. 1–8\] 1998. [\[链接\]](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.1.7559).
- [\[3\]](#Chp001_1-34_B9780443218576000059.xhtml#cf0175) C. Hill, *Learning Scientific Programming with Python*. 剑桥大学出版社; 2016. [\[链接\]](https://scipython.com/book2/).
- [\[4\]](#Chp001_1-34_B9780443218576000059.xhtml#cf0405) J. Snoke 等, General and specific utility measures for synthetic data, *Journal of the Royal Statistical Society Series A* 2018;181:663–688. [arXiv:1604.06651](http://www.arxiv.org/abs/1604.06651). [\[链接\]](https://arxiv.org/abs/1604.06651).
- [\[5\]](#Chp001_1-34_B9780443218576000059.xhtml#cf0035) C. Tofallis, Fitting equations to data with the perfect correlation relationship, 预印本, pp. 1–11, 2015, 赫特福德郡商学院工作论文 [\[链接\]](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2707593).
- \[6\] D. Umbach, K.N. Jones, A few methods for fitting circles to data, *IEEE Transactions on Instrumentation and Measurement* 2003;52(6):1881–1885. [\[链接\]](https://www.researchgate.net/publication/3090706_A_Few_Methods_for_Fitting_Circles_to_Data).
- [\[7\]](#Chp001_1-34_B9780443218576000059.xhtml#cf0115) D.A. Vaccari, H.K. Wang, Multivariate polynomial regression for identification of chaotic time series, *Mathematical and Computer Modelling of Dynamical Systems* 2007;13(4):1–19. [\[链接\]](https://www.tandfonline.com/doi/pdf/10.1080/13873950600883691).

# 第 2 章：一种简单、稳健且高效的集成方法

## 自然语言处理的应用

## 摘要

此处描述的方法阐释了集成方法的概念，并将其应用于一个实际的 NLP 问题：对网站上发布的文章进行排序，以预测尚未撰写的未来博客文章的表现，并帮助决定标题和其他特征，以最大化流量和质量，从而增加收入。该方法称为隐式决策树（HDT），隐式地构建大量小型可用（可能重叠）的决策树。不适合任何可用节点的观测值将使用备选方法（通常是简化逻辑回归）进行分类。

这种混合程序结合了决策树组合和回归模型的优点。它直观且易于实现。代码使用 Python 编写，我也提供了一个基础 Excel 精简版。交互式 Excel 版面向有兴趣学习 Python 或机器学习的分析师。HDT 属于与装袋、提升、堆叠和 **AdaBoost** 同一类别。本章鼓励你理解所有细节，在需要时改进技术，并像自己编写的那样操作完整代码或电子表格。这与在不了解内部原理和局限性的情况下使用黑盒 Python 函数形成对比。最后，我将讨论如何为预测值构建无模型置信区间。

### 关键词

集成方法；XGBoost；逻辑回归；决策树；置信区间

## 2.1 简介
