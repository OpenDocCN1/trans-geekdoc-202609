
Shi, Y. and Eberhart, R. C. (1999). 粒子群优化的实证研究. 1999年IEEE大会论文集, 3, 1945–1950.
Sun, D. X., Li, J. P. and Wei, L. W. (2008). 使用高斯核自适应LQ惩罚SVM的信用风险评估. 东南大学学报, 24, 33-36.
Suykens, J. A. K. and Vandewalle, J. (1999). 最小二乘支持向量机分类器. 神经计算快报, 9, 293-300.
Syarif, I., Prugel-Bennett, A. and Wills, G. (2016). 使用网格搜索和遗传算法优化SVM参数以提高分类性能. TELKOMNIKA (电信计算电子与控制), 14(4), 1502-1509.
UCI机器学习库. Irvine, CA: 加州大学信息与计算机科学学院. http://archive.ics.uci.edu/ml/datasets.html.
Vanitha, C. D. A., Devaraj, D. and Venkatesulu, M. (2015). 使用支持向量机和基于互信息的基因选择进行基因表达数据分类. 计算机科学程序, 47, 13-21.
Vapnik, V. N. (1995). 统计学习理论的本质. Springer, New York.
Vapnik, V. N. (1998). 统计学习理论. Addison-Wesley, Reading, MA.
Wang, W. J., Xu, Z. B., Lu, W. Z. and Zhang, X. Y. (2003). 分类和回归中高斯核中扩展参数的确定. 神经计算, 55, 643-663.
Wei, L. W., Chen, Z. Y., Li, J. P. and Xu, W. X. (2007). 稀疏且鲁棒的最小二乘支持向量机：线性规划公式. IEEE灰色系统与智能服务国际会议论文集, 54-58.
Wei, L. W. (2008). 基于多目标规划的数据挖掘分类模型研究及其应用. 博士论文.
Wei, L. W., Chen, Z. Y. and Li, J. P. (2011). 基于进化策略的自适应L_p LS-SVM. 信息科学, 181(14), 3000-3016.
Welsh, D. J. A. (1988). 模拟退火：理论与应用. 应用数学学报, 12(1), 108-111.
Wiatowski, T. and Bölcskei, H. (2018). 用于特征提取的深度卷积神经网络的数学理论. IEEE信息理论汇刊, 64(3), 1845-1866.
Xia, Y., Liu, C., Li, Y. Y., et al. (2017). 使用贝叶斯超参数优化的信用评分提升决策树方法. 专家系统与应用, 78, 225-241.
Yu, L., Wang, S. Y. and Lai, K. K. (2008). 基于多阶段神经网络集成学习方法的信用风险评估. 专家系统与应用, 34, 1434-1444.
Yu, L., Zhou, R., Tang, L. and Chen, R. D. (2018). 基于DBN的重采样SVM集成学习范式用于不平衡数据的信用分类. 应用软计算, 69, 192-202.
Zhang, L., Hu, H. and Zhang, D. (2015). 基于SVM的供应链金融中小企业信用风险评估模型. 金融创新, 1(1), 14.
Zhang, Y., Wang, S. and Ji, G. (2015). 粒子群优化算法及其应用的全面综述. 工程中的数学问题, 2015.
Zhu, J., Rosset, S., Tibshirani, R., et al. (2004). 1-范数支持向量机. 神经信息处理系统进展, 2004, 49-56.

## 附录 20A：数据归一化方法

在数据归一化步骤中，我们利用最小-最大归一化方法，也称为0-1归一化方法，来处理信用数据。

对于原始样本数据的某一属性，设 x_i (i = 1,2,...,n) 表示该属性的第 i 个样本值，x_i* (i = 1,2,...,n) 表示归一化后的对应值，则最小-最大归一化方法的公式如下：

x_i* = (x_i - min) / (max - min)

其中 min 表示样本的最小值，max 表示样本的最大值。经过此归一化过程后，该属性的所有值将被转换到 [0, 1] 范围内。

## 附录 20B：基于SVM方法论的详细流程

本章构建了一个基于SVM的方法论框架，该框架结合了不同种类的特征提取方法、核函数和超参数优化方法。下面将介绍基于SVM方法论的详细流程：

- (1) 对于某个数据集，我们首先利用附录 20A 中介绍的方法对原始数据进行归一化。然后，我们随机选择整个数据集的 80% 作为机器学习过程中使用的训练集，其余 20% 作为测试集。在某种基于SVM方法的整个过程中，此随机划分将重复进行 10 次，目的是获得算法的平均分类准确率。

- (2) 接下来，根据训练集的数据结构，我们选择某种基于SVM的方法来实现分类任务，选择流程如下：
  - (a) 首先，我们确定将使用哪种惩罚形式，从备选的 L1、L2 和 Lq 中选择。对于 L1 和 L2 方法，我们使用名为 LIBSVM 的相应 Matlab 工具箱（版本 3.22，发布于 2016 年 12 月 22 日），该工具箱由 Chang 和 Lin 于 2011 年提出（例如，参见 Chang and Lin, 2011）。对于 Lq 方法，我们可以使用 Liu 等人在 2007 年提出的 Matlab 代码的一部分（例如，参见 Liu et al., 2007）。
  - (b) 其次，我们确定将使用哪种核函数，从备选的线性、多项式、高斯和 sigmoid 核函数中选择。实际上，每当我们选择某种核函数时，只需在 SVM 分类器的 Matlab 代码中选择相应的参数即可。
  - (c) 第三，我们确定将使用哪种超参数优化方法，从备选的 GS、PSO、SA 和 ES 中选择。每种方法都有不同数量的参数需要设置。例如，GS 方法需要初始化 SVM 方法中出现的每个参数的最小值和最大值，以及参数搜索过程中使用的步长。此外，最优超参数将通过交叉验证的准确率来选择。因此，k 折交叉验证的 k 值也需要事先设定。

上述 a、b 和 c 三个步骤之后，我们可以得到 48 种不同的基于 SVM 的方法，可在下表 20B.1 中找到。实际上，在本章中，只有 12 种具有高斯核函数的方法适用于信用数据集。也就是说，其他核函数的方法的分类准确率明显低于具有高斯核函数的方法。

- (3) 到目前为止，我们已经确定了某种基于 SVM 的方法。例如，ES-ALqG-SVM 是由自适应 L_q 形式、高斯核函数和 ES 方法组合生成的基于 SVM 的算法。然后我们可以在训练集上使用该算法来训练我们的分类模型，其中将构建最优模型。最后，我们可以在原始数据集的测试集上使用该模型来计算平均分类准确率。

对于归一化的训练集、归一化的测试集和某种基于 SVM 的方法，算法的整体流程如下：

- (1) 确定在 SVM 训练过程中将被优化的超参数。对于不同的基于 SVM 的方法，超参数的数量是不同的。表 20B.2 显示了将被调整的相应超参数。此外，这些参数的波动范围也应确定。在我们的研究中，我们设定 λ ∈ [2^{-8},2^{8}]，σ² ∈ [2^{-8},2^{8}]，q ∈ [0.1,0.2,...,2]，d ∈ [1,2,3] 且 γ ∈ [2^{-8},2^{8}]。

- (2) 除了基于 SVM 方法的超参数外，不同的超参数优化方法中还有若干参数需要事先确定。这些参数列在

### 表 20B.1：48 种不同的基于 SVM 的方法。

| 方法 | 惩罚形式 | 核函数 | 超参数优化方法 |
|---|---|---|---|
| GS-L1L-SVM | L1 | 线性 | GS |
| PSO-L1L-SVM | L1 | 线性 | PSO |
| SA-L1L-SVM | L1 | 线性 | SA |
| ES-L1L-SVM | L1 | 线性 | ES |
| GS-L2L-SVM | L2 | 线性 | GS |
| PSO-L2L-SVM | L2 | 线性 | PSO |
| SA-L2L-SVM | L2 | 线性 | SA |
| ES-L2L-SVM | L2 | 线性 | ES |
| GS-ALqL-SVM | Lq | 线性 | GS |
| PSO-ALqL-SVM | Lq | 线性 | PSO |
| SA-ALqL-SVM | Lq | 线性 | SA |
| ES-ALqL-SVM | Lq | 线性 | ES |
| GS-L1G-SVM | L1 | 高斯 | GS |
| PSO-L1G-SVM | L1 | 高斯 | PSO |
| SA-L1G-SVM | L1 | 高斯 | SA |
| ES-L1G-SVM | L1 | 高斯 | ES |
| GS-L2G-SVM | L2 | 高斯 | GS |
| PSO-L2G-SVM | L2 | 高斯 | PSO |
| SA-L2G-SVM | L2 | 高斯 | SA |
| ES-L2G-SVM | L2 | 高斯 | ES |
| GS-ALqG-SVM | Lq | 高斯 | GS |
| PSO-ALqG-SVM | Lq | 高斯 | PSO |
| SA-ALqG-SVM | Lq | 高斯 | SA |
| ES-ALqG-SVM | Lq | 高斯 | ES |
| GS-L1P-SVM | L1 | 多项式 | GS |
| PSO-L1P-SVM | L1 | 多项式 | PSO |
| SA-L1P-SVM | L1 | 多项式 | SA |
| ES-L1P-SVM | L1 | 多项式 | ES |
| GS-L2P-SVM | L2 | 多项式 | GS |
| PSO-L2P-SVM | L2 | 多项式 | PSO |
| SA-L2P-SVM | L2 | 多项式 | SA |
| ES-L2P-SVM | L2 | 多项式 | ES |
| GS-ALqP-SVM | Lq | 多项式 | GS |
| PSO-ALqP-SVM | Lq | 多项式 | PSO |
| SA-ALqP-SVM | Lq | 多项式 | SA |
| ES-ALqP-SVM | Lq | 多项式 | ES |
| GS-L1S-SVM | L1 | Sigmoid | GS |
| PSO-L1S-SVM | L1 | Sigmoid | PSO |
| SA-L1S-SVM | L1 | Sigmoid | SA |
| ES-L1S-SVM | L1 | Sigmoid | ES |
| GS-L2S-SVM | L2 | Sigmoid | GS |
| PSO-L2S-SVM | L2 | Sigmoid | PSO |
| SA-L2S-SVM | L2 | Sigmoid | SA |
| ES-L2S-SVM | L2 | Sigmoid | ES |
| GS-ALqS-SVM | Lq | Sigmoid | GS |
| PSO-ALqS-SVM | Lq | Sigmoid | PSO |
| SA-ALqS-SVM | Lq | Sigmoid | SA |
| ES-ALqS-SVM | Lq | Sigmoid | ES |

