
-   [生物神经系统](https://wiki.example.org/feynmans_learning_method)由几个节点组成，模拟了人脑中的生物神经元，作为ANN分类系统的模型。节点，或神经元，相互连接并进行通信。节点接收输入数据，对其进行分析，然后将其转换后通过连接发送到其他神经元作为输出。每个连接都有一个重量，该重量可能会发生变化。每个节点的输出会通过重量进行处理。

-   隐藏层是位于输入层和输出层之间的层，对加权输入进行计算以生成净输入。

-   最终输出随后通过将激活函数与净输入结合来创建。

-   输入层和输出层的节点相加可能等于一个或两个隐藏层。

-   网络在从输入层到输出层传递时会随机增加重量，结果发送到下一个节点。最终结果与目标进行比较。如果输出不符合目标，则向后传播并修改重量。ANN架构如下[Figure 78.1](#ch78.xhtml#fig78_1)。[Figure 78.2](#ch78.xhtml#fig78_2)展示了基于ANN的自动化稻谷质量评估系统建议。

![Figure 78.1 ANN architecture](images/fig78_1_C.jpg)

[Figure 78.1 ANN architecture](#ch78.xhtml#R_fig78_1)

![Figure 78.2 Flow chart of the process](images/fig78_2_B.jpg)

[Figure 78.2 Flow chart of the process](#ch78.xhtml#R_fig78_2)

-   Matta和Ponni，两种广受消费的稻米品种，是本研究的主题。如[Table 78.1](#ch78.xhtml#tab78_1)所示，它们被分配了四个等级。稻米被分为两类，Ponni稻和Matta稻，使用各种图像的平均RGB值来区分。[Figure 78.3](#ch78.xhtml#fig78_3)展示了Ponni品种的测试结果，[Figure 78.4](#ch78.xhtml#fig78_4)展示了Matta品种的测试结果。稻谷根据几何特征被分为1、2、3、4等级。

[Table 78.1 Grade of rice grains](#ch78.xhtml#R_tab78_1)

| Grade || Type |
| --- | --- |
| 1 || Perfect small rice grains |
| 2 || Perfect large rice grains |
| 3 || Rice grains with impurities |
| 4 || Imperfect (mixed) rice grains |

![Figure 78.3 Test image for grade-2 Ponni rice](images/fig78_3_C.jpg)

[Figure 78.3 Test image for grade-2 Ponni rice](#ch78.xhtml#R_fig78_3)

![Figure 78.4 Test image for grade-2 Matta rice](images/fig78_4_C.jpg)

[Figure 78.4 Test image for grade-2 Matta rice](#ch78.xhtml#R_fig78_4)

## Results

-   使用MATLAB的NN-toolbox进行稻谷分类方案的实施。NN分类系统利用了七个数据集。本研究使用的ANN框架如下[Figure 78.5](#ch78.xhtml#fig78_5)。考虑了七个输入特征，而稻谷质量和品种被视为输出。为了达到最高准确率，该模型包含48个隐藏层。[Figure 78.6](#ch78.xhtml#fig78_6)展示了NN分类器的结果，回归图在[Figure 78.7](#ch78.xhtml#fig78_7)中讨论。

![Figure 78.5 ANN framework](images/fig78_5_C.jpg)

[Figure 78.5 ANN framework](#ch78.xhtml#R_fig78_5)

![Figure 78.6 Grading of rice grains according to varieties using ANN classifier](images/fig78_6_C.jpg)

[Figure 78.6 Grading of rice grains according to varieties using ANN classifier](#ch78.xhtml#R_fig78_6)

![Figure 78.7 Regression plots](images/fig78_7_C.jpg)

[Figure 78.7 Regression plots](#ch78.xhtml#R_fig78_7)

-   不同稻种根据其周长评估进行分类。[Table 78.2](#ch78.xhtml#tab78_2)详细列出了每个样本图像中每颗稻谷的像素值，基于粒子分析。[Table 78.3](#ch78.xhtml#tab78_3)利用对象检测方法区分小、正常、大和破碎稻谷，并以样本中总种子数的百分比形式呈现数值。此外，[Table 78.4](#ch78.xhtml#tab78_4)列出了人类检查员检测到的不同稻谷的数值及其对应的百分比，基于样本中总种子数。

[Table 78.2 Analysis of rice seeds in a random sample](#ch78.xhtml#R_tab78_2)

| S. No. || Perimeter (pixels) |
| --- | --- |
| 1 || 198 |
| 2 || 198 |
| 3 || 176 |
| 4 || 199 |
| 5 || 198 |
| 6 || 236 |
| 7 || 227 |
| 8 || 114 |
| 9 || 177 |
| 10 || 121 |
| 11 || 206 |
| 12 || 190 |
| 13 || 209 |
| 14 || 209 |
| 15 || 116 |
| 16 || 203 |
| 17 || 223 |
| 18 || 226 |
| 19 || 187 |
| 20 || 225 |
| 21 || 237 |
| 22 || 211 |
| 23 || 148 |
| 24 || 216 |
| 25 || 196 |
| 26 || 218 |

[Table 78.3 Results of a random sample regarding the size of the rice seeds with percentage values](#ch78.xhtml#R_tab78_3)

| Sample no || Small seed || % || Normal seed || % || Large seed || % || Broken seed || % || Total seeds |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 || 3 || 10.71 || 15 || 53.57 || 3 || 10.71 || 7 || 25.00 || 28 |
| 2 || 4 || 12.90 || 20 || 64.52 || 2 || 6.45 || 5 || 16.13 || 31 |
| 3 || 2 || 7.69 || 16 || 61.54 || 2 || 7.69 || 6 || 23.08 || 26 |
| 4 || 2 || 6.25 || 19 || 59.37 || 3 || 9.37 || 8 || 25.00 || 32 |
| 5 || 3 || 10.00 || 19 || 63.33 || 2 || 6.67 || 6 || 20.00 || 30 |
| 6 || 2 || 6.45 || 18 || 58.06 || 4 || 12.90 || 7 || 22.58 || 31 |
| 7 || 2 || 7.41 || 18 || 66.67 || 4 || 14.81 || 3 || 11.11 || 27 |
| 8 || 3 || 10.34 || 19 || 65.52 || 3 || 10.34 || 4 || 13.79 || 29 |
| 9 || 4 || 13.79 || 19 || 65.52 || 2 || 6.90 || 4 || 13.79 || 29 |
| 10 || 2 || 6.90 || 17 || 58.62 || 4 || 13.79 || 6 || 20.69 || 29 |
| 11 || 2 || 6.67 || 18 || 60.00 || 5 || 16.67 || 5 || 16.67 || 30 |
| 12 || 2 || 6.67 || 18 || 60.00 || 4 || 13.33 || 6 || 20.00 || 30 |
| 13 || 2 || 6.25 || 20 || 62.50 || 2 || 6.25 || 8 || 25.00 || 32 |
| 14 || 4 || 13.33 || 17 || 56.67 || 3 || 10.00 || 6 || 20.00 || 30 |
| 15 || 2 || 6.67 || 18 || 60.00 || 4 || 13.33 || 6 || 20.00 || 30 |
| Average || 8.80% ||  || 61.05% ||  || 10.61% ||  || 19.52% ||  ||  |

[Table 78.4 Results of a random sample in terms of the size of the rice seeds with percentage values by Human inspector](#ch78.xhtml#R_tab78_4)

| Sample no || Small seed || % || Normal seed || % || Large seed || % || Broken seed || % || Total seeds |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 || 4 || 14.28 || 14 || 50.00 || 4 || 14.28 || 6 || 21.42 || 28 |
| 2 || 5 || 16.12 || 17 || 54.83 || 3 || 9.67 || 6 || 19.35 || 31 |
| 3 || 3 || 11.53 || 14 || 53.84 || 3 || 11.53 || 6 || 23.07 || 26 |
| 4 || 4 || 12.50 || 17 || 53.12 || 4 || 12.50 || 7 || 21.87 || 32 |
| 5 || 4 || 13.33 || 15 || 50.00 || 4 || 13.33 || 7 || 23.33 || 30 |
| 6 || 3 || 9.67 || 15 || 48.38 || 5 || 16.12 || 8 || 25.80 || 31 |
| 7 || 4 || 14.81 || 14 || 51.85 || 5 || 18.51 || 4 || 14.81 || 27 |
| 8 || 4 || 13.79 || 15 || 51.72 || 4 || 17.24 || 4 || 17.24 || 29 |
| 9 || 6 || 20.68 || 14 || 48.27 || 4 || 13.79 || 5 || 17.24 || 29 |
| 10 || 5 || 17.24 || 15 || 51.72 || 5 || 17.24 || 4 || 13.79 || 29 |
| 11 || 4 || 13.33 || 14 || 46.66 || 6 || 20.00 || 6 || 20.00 || 30 |
| 12 || 3 || 10.00 || 15 || 50.00 || 5 || 16.66 || 7 || 23.33 || 30 |
| 13 || 3 || 9.37 || 16 || 50.00 || 4 || 12.50 || 9 || 28.12 || 32 |
| 14 || 5 || 16.66 || 14 || 46.66 || 4 || 13.33 || 7 || 23.33 || 30 |
| 15 || 3 || 10.00 || 15 || 50.00 || 5 || 16.66 || 7 || 23.33 || 30 |
| Average || 50.46% ||  || 12.21% ||  || 16.48% ||  || 21.06% ||  ||  |

