

### 3.7.12 ROC-AUC 得分

它是通过 ROC 曲线计算得出的，该曲线表达了真阳性率（以前称为灵敏度或召回率）与假阳性率之间的关系。ROC/AUC 得分是利用 ROC 曲线（1 - 特异性）确定的。二分类中 ROC 曲线下面积或 ROC-AUC 表明模型在正负目标类别上的区分能力有多强 [[Riti et al., 2016]]; [[Kavitha et al., 2019]]。特别是，当正负组的值相似时，ROC-AUC 得分的成功标准可能是有益的。

## 3.8 分类

作者分析了 1010 例恶性和良性病例，旨在挑选模型训练集，随后测试模式的准确性，并经常同时寻求有监督和无监督学习方法。然而，如 [图 3.5(a)](#ch11.xhtml#f16)、[3.5(b)](#ch11.xhtml#f17)、[3.5(c)](#ch11.xhtml#f18) 和 [3.5(d)](#ch11.xhtml#f19) 所示，变量之间不存在共线性问题，可用于预测癌变或非癌变细胞 [[Vinod Kumar et al. 2021]]。预测扇区、熵和标准差之间的相关性很高 [[Hussein Sarfaraz et al., 2019]]。峰度和偏度也密切相关。这种共线性也意味着此类预测变量被排除在外。

![Figure 3.4(a) P-Id: LIDC-IDRI-0001-00096.dcm. Figure 3.4(b) P-Id: LIDC-IDRI-0006-00057.dcm. Figure 3.4(c) P-Id: LIDC-IDRI-0013-00027.dcm. Figure 3.4(d) P-Id: LIDC-IDRI-0082-00007.dcm.](html/images/9780367720919_C003_004.jpg)

Figure 3.4(a) P-Id: LIDC-IDRI-0001-00096.dcm. Figure 3.4(b) P-Id: LIDC-IDRI-0006-00057.dcm. Figure 3.4(c) P-Id: LIDC-IDRI-0013-00027.dcm. Figure 3.4(d) P-Id: LIDC-IDRI-0082-00007.dcm.

### 3.8.1 双向长短期记忆网络 (BLSTM)

自 20 世纪中叶以来，长短期记忆 (LSTM) [[Zhang et al., 2018]] 的提出使得人工神经网络 [[Kumar et al., 2012]] (ANN) 成为一种极其出色的循环神经网络 (RNN)。通过其在分组中的直连，RNN 可能变得依赖于时间。为了证明这一点，前馈网络应实现静态模式映射的使用，例如 MLP。此外，传统 RNN [[Wang Ran et al., 2018]] 对这一极其真实的问题变得敏感，特别是在梯度下降训练中，包括梯度消失问题。此问题产生的原因是梯度呈指数级消失或爆炸。因此，经过几个步骤后，传统 RNN 在梯度消失后“遗忘”少于十次的关注点。其影响可能对后续研究方法受到异常限制，并且逐渐隔离的前序层之间的链接和连接变得非常复杂和棘手。

LSTM [[Zhang et al., 2018]] 所精妙阐释的问题将其自身概括为一种特殊的循环结构，能够像可微容量单元一样运作。LSTM 模块内部的误差可以长期维持，可以在交汇点长期保持。LSTM 可以监管多达 10,000 步的时间跨度 [[Salehi et al., 2018]] 以及极长的周期。LSTM [[Salman et al., 2020]] 释放出一种惊人的能力，能够从循环集合中的其他能力中学习，例如精确计时、精确复制值、扩展，以及有时的增加 [[Albu et al. 2019]]。分析师们利用梯度通过时间反向传播来学习 LSTM 的度量 [[Mhaske Diksha et al., 2019]]。

它涉及单向经典循环网络架构。这意味着此类网络的输入序列按正确方向解释：其行为朝向正确方向。输入背景被收集在网络的先前上下文中。因此，这些问题是仅靠先前上下文无法正确学习的问题。获取潜在的未来上下文可能也就足够了，例如，在临床场景中，通过提供关于即将到来的信息，来识别输入序列中可能令人不安的局部部分。只有在计算时刻输入序列通常已完全给出时，未来上下文才能被精确提供。双向循环神经网络的原理允许某些过去上下文和未来上下文在循环神经网络中均可访问 [[Razzak et al., 2018]]。考虑一个仅具有一个隐藏层循环的经典 RNN。现在，引入第二个循环隐藏层，并将其与输入层以及输出层连接，尽管具体不是与另一个隐藏层连接。其次，通常按正向方向，将输入序列引入输入层。仅计算第一隐藏层，然后所有激活值随每个过程进行处理 [[Mobile et al., 2017]]。第三，输入序列按反向显示。仅第二隐藏层工作，并保持其所有操作。在此之后，输出层通过在每个阶段融合历史知识（即第一隐藏层）和未来信息（即第二隐藏层）来生成输出序列。第二层包含第二个隐藏层。现在，反向隐藏层的梯度计算在反转时间下以几乎相同的方式运行。

后来，双向层的概念在 LSTM 网络中得到了类似实现 [[Mhaske Diksha et al., 2019]]。双向长短期存储网络 (BLSTM) 凭借 BLSTM 在惊人的手动分类准确性方面变得更加突出。因此，LSTM 以及隐马尔可夫模型 (HMM) 等其他技术，为本章规定的分类任务选择 BLSTM。

## 3.9 实验与结果

使用 GPU 框架 MATLAB R2018b、Intel® CoreTM i5-7200U 第 7 代 CPU @3.1 GHZ、Intel(R) HD Graphics 620 RAM 1 GB 适配器、8 GB DDR4 RAM，为 BLSTM 和 SVM 给出了以下先决条件。如 [图 3.5(a)](#ch11.xhtml#f16)、[3.5(b)](#ch11.xhtml#f17)、[3.5(c)](#ch11.xhtml#f18) 和 [3.5(d)](#ch11.xhtml#f19) 所示，分类器的结果需牢记各种要求。

![Figure 3.5(a) Benign as zero and malign as one in a resulting CT image were identified after compilation of classifier SVM algorithms from 50% to 90% TTR respectively.](html/images/9780367720919_C003_005a.jpg)

Figure 3.5(a) Benign as zero and malign as one in a resulting CT image were identified after compilation of classifier SVM algorithms from 50% to 90% TTR respectively.

机器训练系统使用 395 个 CT 图像片段来检测肺癌，并遵循 LIDC-IDRI 数据集，在将文件从 (dot) DCM 格式转换为 (dot) PNG 格式后获得数据集。使用 MATLAB 脚本，该系统可以检测并定位肺部肿瘤。在肿瘤识别过程之后，此处癌变和非癌变细胞的图像分别由 [图 3.5(a)](#ch11.xhtml#f16)、[3.5(b)](#ch11.xhtml#f17)、[3.5(c)](#ch11.xhtml#f18) 和 [3.5(d)](#ch11.xhtml#f19) 表示，用零和一标识。

