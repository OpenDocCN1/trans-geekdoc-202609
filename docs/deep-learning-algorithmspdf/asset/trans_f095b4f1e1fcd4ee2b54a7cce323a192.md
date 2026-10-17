
![Image 1471](index-334_5.png)

![Image 1472](index-334_6.png)

![Image 1473](index-334_7.png)

Deep Learning Algorithms

308

**Figure 1**. 单模型 BP 神经网络。

' +

因此，选择标准的三层 BP 神经网络作为混合网络的子网络。对于混合网络的每个子网络，输入层的神经元数量对应于面部特征提取的维度，输出层的神经元数量为 1。隐藏层的神经元数量由以下经验公式计算：(22)

其中，m 是输出层的神经元数量，n 是输入层的神经元数量，a 是介于 1 - 10 的常数 \[38\]。如果面部特征提取的维度为 X，则混合网络的每个子网络的结构如下：

(23)

BP 神经网络的结构如下：

(24)

本书版权归 Arcler 所有

![Image 1474](index-335_1.jpg)

![Image 1475](index-335_2.jpg)

![Image 1476](index-335_3.png)

![Image 1477](index-335_4.png)

![Image 1478](index-335_5.jpg)

![Image 1479](index-335_6.png)

![Image 1480](index-335_7.png)

![Image 1481](index-335_8.png)

Deep Learning Algorithms

309

子网络的结构比单模型 BP 神经网络更简单。当网络结构复杂时，每增加一个神经元，训练时间会显著增加。此外，随着网络规模逐渐变大，越来越复杂的结构容易出现收敛缓慢、陷入局部极小、泛化能力差等问题。相较之下，下面是：

\# # # # #

**Figure 2**. 混合 BP 神经网络 (HBPNNs)。

***3)***

***RBF 神经网络：-*** Radial Basis Function (RBF) 模拟人脑接收域中相互调整和覆盖的神经网络结构，能够以任意精度逼近任意连续函数。具有快速学习、不易陷入局部极小的特点。

RBF 的表达式如下 \[39\]：

(25)

其中，

欧氏距离为 x 到 c 的

。RBF 神经网络最常用的径向基函数是高斯函数，如下所示：

(26)

本书版权归 Arcler 所有

![Image 1482](index-336_1.jpg)

![Image 1483](index-336_2.jpg)

![Image 1484](index-336_3.jpg)

![Image 1485](index-336_4.png)

![Image 1486](index-336_5.png)

![Image 1487](index-336_6.png)

![Image 1488](index-336_7.png)

![Image 1489](index-336_8.png)

Deep Learning Algorithms

310

构建函数如下：

(27)

不同的径向基函数的 c 参数和权重 w 存在差异。训练 RBF 的具体步骤如下。

i

对于样本数据集，我们使用方程 (27) 与 M 个隐藏节点对这些样本数据进行分类。

(28)

隐藏节点的数量最初在应用中被设为一个小整数。如果训练误差不佳，可以增加隐藏节点以降低误差。同时考虑测试误差，存在一个适当

\# < ?

在图 3 中。

***4)***

***混合 RBF 神经网络 (HRBFNNs)：-*** 混合 RBF 神经网络 (HRBFNNs) 由多个 RBF 网络组成，用于替代单个 RBF 网络用于面部识别。混合网络具有更好的容错能力、更快的收敛速率和更强的泛化能力，并且可以实现分布式计算，大幅缩短网络训练时间 \[40\]。

如果面部特征提取的维度为 n，则混合网络的每个子网络结构如下：

(29)

RBF 神经网络的结构如下：

(30)

子网络的结构比 RBF 神经网络更简单。此外，当网络结构复杂时，每增加一个神经元，训练时间和计算量会显著增加

< ¯??

***5)***

***支持向量机 (SVM)：-*** SVM 是基于统计学习理论的一种新型机器学习技术，能够在高维特征空间中构建决策函数，以预测示例的标签。

+

\` ## |

训练数据在高维特征空间中，新的测试数据

\# # + {

本书版权归 Arcler 所有

![Image 1490](index-337_1.jpg)

![Image 1491](index-337_2.jpg)

![Image 1492](index-337_3.jpg)

![Image 1493](index-337_4.png)

![Image 1494](index-337_5.jpg)

![Image 1495](index-337_6.png)

![Image 1496](index-337_7.png)

![Image 1497](index-337_8.png)

Hierarchical Representations Feature Deep Learning for Face Recognition 311

假设有两类示例（正类和负类），正类和负类示例的数量分别为 n 和 m。训练集包含这些正负示例。标签集为 i x，其中

。

**Figure 3**. RBF 神经网络。

**Figure 4**. 混合 RBF 神经网络 (HRBFNNs)。

本书版权归 Arcler 所有

![Image 1498](index-338_1.jpg)

![Image 1499](index-338_2.jpg)

![Image 1500](index-338_3.jpg)

![Image 1501](index-338_4.png)

![Image 1502](index-338_5.jpg)

![Image 1503](index-338_6.png)

![Image 1504](index-338_7.jpg)

![Image 1505](index-338_8.jpg)

![Image 1506](index-338_9.jpg)

![Image 1507](index-338_10.jpg)

![Image 1508](index-338_11.jpg)

![Image 1509](index-338_12.png)

![Image 1510](index-338_13.png)

![Image 1511](index-338_14.png)

Deep Learning Algorithms

312

SVM 用于学习一个决策函数，以预测示例的标签。SVM 的优化公式为：

(31)

其中，Ò #

i

训练示例。这是一个二次规划问题，使用拉格朗日乘子法并满足 KKT 条件，可得到最优解

\# #

(32)

其中，

为确定最优解的参数，

是两个向量的点积。

对于非线性问题，SVM 可以将其映射到高维空间，使原问题线性可分。如方程 (32) 所示，如果我们知道两个向量的点积运算，则计算简单。根据 Mercer 理论，对于任意

(33)

任意的对称函数

将在特定变换空间中成为点积。方程 (32) 对应于：

(34)

这就是 SVM。核函数 K (x, x ) 有以下几类：

i

线性核函数

；

多项式核函数

，其中 s、c 和 d 为参数；

径向基核函数，

的参数；

Sigmoid 核函数

，其中 s 和 c 为参数。

本书版权归 Arcler 所有

![Image 1512](index-339_1.jpg)

![Image 1513](index-339_2.png)

![Image 1514](index-339_3.png)

![Image 1515](index-339_4.png)

![Image 1516](index-339_5.png)

Hierarchical Representations Feature Deep Learning for Face Recognition 313

SVM 的模型图如图 \[43\] \[44\] \[45\] 所示，见图 5。SVM 本质上是两类分类的分类器。解决多类分类问题需要构建更合适的分类器。

< ¶~

使用优化问题求解多类分类。

< '

\# +

**Figure 5**. 支持向量机 (SVM)。

该方法有两种方式：

一种是 One-Against-One：在任意两类之间构建超平面，k 类需要构建

++ + < # #

一种是 One-Against-the-Rest：将一类与其他多个类进行对比，k 类需要

\# #

我们将在实验中使用 “One-Against-One” 和 “One-Against-the-Rest” 两种方法，并选择效果更好的方法。

¶~

本书版权归 Arcler 所有

![Image 1517](index-340_1.jpg)

![Image 1518](index-340_2.jpg)

![Image 1519](index-340_3.png)

![Image 1520](index-340_4.png)

![Image 1521](index-340_5.png)

![Image 1522](index-340_6.jpg)

![Image 1523](index-340_7.png)

![Image 1524](index-340_8.png)

![Image 1525](index-340_9.png)

Deep Learning Algorithms

314

***!"***

***#$ %&'\*\* %+&\*\*,0*** 不同

?

#

特征融合和决策融合是两种主要方法

? #

+<

MCDFC 的不同

Figure 6.

我们使用加权投票对每个分类器进行决策融合：(35)

where, w

i

