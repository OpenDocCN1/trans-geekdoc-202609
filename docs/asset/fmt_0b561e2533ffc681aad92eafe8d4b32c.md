
*   Yadav, G., Maheshwari, S., & Agarwal, A. (2016). Multi-domain image enhancement of foggy images using contrast limited adaptive histogram equalization method. *Proceedings of the International Conference on Recent Cognizance in Wireless Communication & Image Processing*（无线通信与图像处理最新认知国际会议论文集），31–38。

# 6

# Forecasting Time Series Data Using Artificial Neural Network

## A Review

Sarbjit Singh, Kulwinder Singh Parmar, Harpreet Kaur, and Jatinder Kaur

DOI: [10.1201/9781003153405-6](https://doi.org/10.1201/9781003153405-6)

## Contents

*   6.1 Introduction
*   6.2 Historical Developments in the Field of ANN
*   6.3 Methodology
*   6.4 Classification of ANN
    *   6.4.1 Feed-Forward Neural Networks
    *   6.4.2 Recurrent Neural Networks
    *   6.4.3 Elman Back Propagation Neural Networks
    *   6.4.4 Time-Delay Feed-Forward Neural Network
*   6.5 Structural Design of ANN
*   6.6 Review of Applications, Results and Discussions
    *   6.6.1 River Flow Forecasting
    *   6.6.2 Environmental Pollution Forecasting
    *   6.6.3 Stock Market Forecasting
    *   6.6.4 Agriculture Related Forecasting
*   6.7 Conclusions
*   References

### 6.1 Introduction

预测是一项极具挑战性的任务。研究人员和专业分析师提出了各种统计模型和软计算技术，以获得更准确的预测。在各种预测模型中，人工神经网络（`ANNs`）是最准确、快速和可靠的技术。`ANN` 几乎应用于所有领域，无论是社会、经济、工程、大气科学还是应用数学领域。`ANN` 最显著的特点是它能够处理数据的非线性、季节性、噪声和鲁棒性（Khashei and Bijari, 2010）。基于 `ANN` 计算的动机是设计此类数学算法，使其能够并行地模拟人脑进行信息处理的工作方式（Basheer and Hajmeer, 2000）。`ANN` 最重要的特征是它们具有以高精度逼近任何连续函数的能力（Zhang and Min Qi, 2005; Chen et al. 2003）。`ANN` 具有独特的泛化能力。样本中未见的部分可以通过 `ANN` 正确推断。与线性/回归模型不同，使用 `ANN` 时不需要对模型做任何先验假设。这种数据驱动的方法使 `ANN` 成为预测现实生活中复杂问题的绝佳工具，因此它成为预测股票市场、环境污染、河流流量、天气、农业以及科学和工程中许多预测起关键作用领域的合适工具。在预测中，多层前馈方法是 `ANN` 最广泛使用的范式。本章旨在为预测领域的研究人员提供关于不同类型神经网络发展以及建模和预测不同时间序列方法论的详细研究。本章还涉及使用 `ANNS` 的监督学习技术综述，以解决与环境、股票市场、水文学和农业相关的预测问题。

### 6.2 Historical Developments in the Field of ANN

沃伦·麦卡洛克和沃尔特·皮茨于 1943 年设计了麦卡洛克-皮茨神经元计算元件模型。在该模型中，每个元件被分配输入的加权和，然后应用阈值逻辑运算（McCulloch and Pitts 1943）。使用这些计算元件的组合进行了多项分析计算（Figure 6.1）。

![Figure 6.1 McCulloch-Pitts neuron model.](img/9780367720919_C006_001.jpg)

**Figure 6.1** McCulloch-Pitts neuron model.

唐纳德·赫布于 1949 年提出了一种可调连接权重的学习方案，这成为了神经网络领域的一个重要学习规则（Hebb, 1949）。马文·明斯基于 1954 年创建了一种自适应学习方案，可自动调整连接强度（Minsky and Papert, 1969）。著名的感知机模型由罗森布拉特于 1958 年提出。其中权重通过感知机学习法则进行调整（Rosenblatt, 1958）。该法则最适合使用多层感知机进行模式分类问题（Figure 6.2）。

![Figure 6.2 Rosenblatt’s perceptron model of a neuron.](img/9780367720919_C006_002.jpg)

**Figure 6.2** Rosenblatt’s perceptron model of a neuron.

感知机模型的主要缺点是无法在重组分类任务时调整权重。这在 1969 年由明斯基和帕珀特克服（Minsky and Papert, 1969）。1960 年，维德罗和霍夫提出了用于调整权重的自适应元件 Adaline 模型（Widrow and Hoff, 1960）（Figure 6.3）。由于算法的收敛性，它成功地应用于自适应信号处理问题。

![Figure 6.3 Widrow’s Adaline model of a neuron.](img/9780367720919_C006_003.jpg)

**Figure 6.3** Widrow’s Adaline model of a neuron.

1964 年，胡在其论文中使用维德罗的自适应网络进行天气预报。由于缺乏训练算法，研究受限直到 1986 年反向传播算法由 Chauvin and Rumelhart (1995) 引入。

在过去的 30 年里，竞争学习、自组织和模拟退火等概念的若干杰出贡献影响了人工神经网络这一领域，从而促成了新的学习算法和模式识别问题的发展。目前，模糊逻辑方法与神经网络相结合，以开发一种自适应框架，从而高效地处理现实世界的问题。

### 6.3 方法论

人工神经网络（ANN）可被视为包含比生物神经网络更简单的互联处理单元结构。ANN 由若干相互连接的处理单元组成，以执行规定的任务。ANN 由三个重要层组成，即输入层、隐藏层和输出层。输入层和输出层分别拥有对应输入和输出变量的节点（图 6.4）。

![Figure 6.4 Basic architecture of an artificial neural network.](img/9780367720919_C006_004.jpg)

图 6.4 人工神经网络的基本架构。

数据通过加权连接在层之间传输（Kaul 等，2005）。输入被送至处理单元的求和部分，该部分计算加权和以从此和生成输出。离散或连续的输入值也可被送至处理单元以生成输出。送至处理单元的输入要么独立给出，要么来自其他处理单元的输出。连接单元的能力体现在权重值中。ANN 中的每个单元在给定时刻都有一个唯一的激活值，该值决定了网络的激活状态。输出函数单元生成总体输出，该输出由激活值决定（图 6.5）。可使用线性、阶跃、斜坡、Sigmoid、双曲正切和高斯函数等不同类型的激活函数来生成激活值（图 6.6）并确定网络的输出路径。

![Figure 6.5 Processing unit of artificial neural network.](img/9780367720919_C006_005.jpg)

图 6.5 人工神经网络的处理单元。

![Figure 6.6 Different types of activation functions (a) linear function (b) step Function (c) Ramp function (d) sigmoid function (e) hyperbolic tangent function (f) Gaussian function.](img/9780367720919_C006_006.jpg)

图 6.6 不同类型的激活函数 (a) 线性函数 (b) 阶跃函数 (c) 斜坡函数 (d) Sigmoid 函数 (e) 双曲正切函数 (f) 高斯函数。

### 6.4 ANN 分类

根据层间连接的结构，ANN 分类如下：

#### 6.4.1 前馈神经网络

前馈神经网络是人工神经网络最基本的形式，其中信息流是单向的，绝不反向。前馈 ANN 中节点之间的连接不形成循环（图 6.7）。

![Figure 6.7 Architecture of feed-forward artificial neural network.](img/9780367720919_C006_007.jpg)

图 6.7 前馈人工神经网络架构。

#### 6.4.2 循环神经网络

在循环神经网络中，相同的操作会在一组序列输入上反复执行。从某些先前阶段生成的输出作为下一阶段操作的输入。隐藏层承担着重要任务，即回溯反复输入的数据的某些信息。由于这一特性，循环神经网络具有记忆，从而提高了其性能（图 6.8）。

![Figure 6.8 Architecture of recurrent artificial neural network.](img/9780367720919_C006_008.jpg)

图 6.8 循环人工神经网络架构。

#### 6.4.3 Elman 反向传播神经网络

Elman 神经网络是一种反馈神经网络，其隐藏层不仅与输出层互联，还与另一层（称为上下文层）互联，连接权重等于 1。上下文层充当延迟算子以保持记忆，使网络具备适应时变主动特征的能力，从而增加稳定性（图 6.9）。

![Figure 6.9 Architecture of Elman back propagation neural networks.](img/9780367720919_C006_009.jpg)

图 6.9 Elman 反向传播神经网络架构。

#### 6.4.4 时延前馈神经网络

时延前馈神经网络利用时延特性构建网络结构，以建立短期记忆，使神经网络具有动态性。时延特性被应用于神经网络的输入层（图 6.10）。

![Figure 6.10 Architecture of time-delay feed-forward neural network.](img/9780367720919_C006_010.jpg)

图 6.10 时延前馈神经网络架构。

### 6.5 ANN 结构设计

ANN 的结构布局主要包括定义所需的输入、输出和隐藏层的数量，以及神经元之间的交互方案（Gardner and Dorling 1998）。输入层和输出层的神经元数量因问题而异。但没有具体标准来确定每个隐藏层需要多少神经元。隐藏层中神经元数量较少会导致较高的训练误差（欠拟合），而神经元数量较多则会导致较高的验证误差（过拟合）。这两种误差均不可接受。模型根据输入预测输出。

各层的处理单元通过非循环链接连接。输出（`y[t]`）与输入（`y[t-1], ..., y[t-p]`）之间的关系由下式给出：

```
y_t = w_0 + \sum_{j = 1}^{q} w_j g(w_{0,j} + \sum_{j = 1}^{p} w_{i,j} y_{t - i}) + \epsilon_t
```

其中 `w[i, j]`（`i`=0,1,2,...`p`，`j`=1,2,...`q`）和 `w[j]`（`j`=0,1,2,...`q`）为连接权重；`p` 和 `q` 分别为输入节点和隐藏节点的数量。

### 6.6 应用、结果与讨论综述

Zhang（1998）发现，ANN 能以同等期望精度处理线性和非线性问题。随后，Gorr 于 1994 年补充指出，ANN 能同时处理季节性和非线性。当 Sharda 和 Patil（1992）分析著名的 M 竞赛中的 88 个季节性时间序列时，他们得出了类似的结论：使用 ANN 时无需对数据进行预先去季节化。然而，对去季节化数据的预测明显优于对季节性数据的预测（Nelson 等，1999）。Franses 和 Draisma（1997）识别出了变化的季节模式。神经网络的自组织能力及其灵活的特性，使其成为应用于波动大且频繁的股票市场的合适工具（Bing 等，2012）。因此，ANN 具有广泛的应用范围，但此处我们主要讨论 ANN 高效用的四大领域。

#### 6.6.1 河流流量预测

自 Kang et al. (1993) 提出将人工神经网络（ANN）应用于河流流量的逐日和逐时预报以来，大量研究（Abrahart and See 1998，Jain et al., 1999，Zealand et al., 1999）已利用 ANN 预测不同的河流流量参数。在所使用的各种模型中，采用反向传播（BP）算法改进的多层感知机模型是最流行且应用最广泛的技术。径向基函数在河流流量预报中也有大量应用（Dawson et al. (2002)；Dibike and Solomatine (2001)；Fernando and Jayawardena (1998)）。为了对非平稳数据进行更好、更准确的预报，ANN 与小波相结合，开发出了各种混合模型。小波与人工神经网络（WA–ANN）的混合模型被开发并应用于法国和美国的一日提前流量预报（Anctil and Tape 2004）、意大利和土耳其的月度预报（Kisi 2009）以及河流流量的逐日预报（Kisi 2009）。所有这些研究均得出结论：WA–ANN 模型在河流流量预报方面表现优于 ANN 模型。

#### 6.6.2 环境污染预报

为保护人们免受污染的有害影响，卫生机构有必要获得关于周围污染物排放和空气质量的可靠提前预测。大气污染浓度及其与气候的统计关系是环境污染预报的基础。长期以来，多元线性回归模型被用于此目的（Comrie 1997）。然而，污染-天气关系是非线性且复杂的。因此，由于计算效率和泛化能力，ANN 模型为统计模型提供了更好的替代方案。ANN 能非常适当地处理非线性复杂的污染-天气关系。甚至高维数据也能以同等精度处理。但数据的异质性和广泛的影响参数使得环境模型难以被完全彻底地研究（Jakeman et al. 2006）。Perez and Trier (2001) 在圣地亚哥实现了 `PM2.5` 颗粒物浓度的 24 小时提前预测。此项工作采用了一个具有 24 个输入和 1 个输出的三层前馈神经网络。早在 1998 年，Gardner 和 Dorling 就对人工神经网络在大气科学中的应用进行了广泛而全面的综述。多层感知机（MLP）结构被认为最为适用，特别是在大气科学研究中。Moseholm et al. (1996) 在估算西雅图北部大学区（一个遮蔽的城市十字路口）的 CO 浓度水平时采用了该技术。Chelani et al. (2002) 在德里对多元回归模型和三层神经网络进行了比较以预测 `SO2` 浓度，结论是后者比前者给出了更准确、更可靠的结果。

#### 6.6.3 股市预测

股市预测是一项充满挑战的任务，因为它涉及大量风险。各种研究人员使用不同方法对股市数据进行建模和预测。但由于股市数据的非线性和复杂性，人工神经网络被发现是最准确、最精确的软计算技术。Li and Ma (2010) 对 ANNs 在各类股市中的应用进行了综述，内容涉及应用 ANNs 预测各类股市和金融指数的未来值。Wang and Wang (2015) 借助随机时效函数神经网络和主成分分析的耦合方法，对金融时间序列数据进行了预测。与常规的反向传播神经网络（BPNN）和 PCA-BPNN 相比，所提混合方法生成的预测更准确。Niaki and Hoseinzade (2013) 应用人工神经网络（ANN）方法按日预测标准普尔 500（S&P 500）指数。他们采用实验设计从 27 个金融和经济变量中选择最有效的特征，并利用 ANN 进行预测。所提技术的性能优于传统的买入持有策略。Zahedi and Rounaghi (2015) 采用 ANN 模型和主成分分析（PCA）方法预测德黑兰证券交易所价格，并从 20 个会计变量中提取了 20 个主要特征。准确的预测以所有变量的新模式形式呈现。Wang and Wang (2016) 通过结合 MLP 和 ERNN 与随机时效函数，开发了一种预测原油价格波动的新技术。具有时变预测系统显著特征的 ERNN 的发展，具备记录近期事件以预测未来值的能力。随机时效函数的主要目标是为投资者体现近期信息相较于旧信息的稳健性。

#### 6.6.4 农业相关预测

##### 作物及时管理与人工神经网络在农学中的应用

作物的及时管理是农学领域的重中之重，因此模拟技术可在该领域发挥关键作用。温度、降雨、水分胁迫等环境因素对水稻、玉米、大豆、小麦等许多农作物的生长和产量有着显著影响（Khairunniza-Bejo et al. 2014）。

人工神经网络（ANN）可成为作物生长发育建模（Elizondo et al., 1994）、土壤-水分保持估算（Schaap and Bouten, 1996）、农药与养分流失评估（Yang et al., 1997）以及病害预测（Batchelor et al. 1997）的有效工具。总体而言，大多数农业模型采用的是力学或实验方法（Poluektov and Topaj, 2001）。力学模型较为复杂，而经验模型存在无法预测数据集范围以外情况的局限性（Wang and Wang 2016）。由于 ANN 简单且用途更广，因此它是农学中更有效、更适用的技术。
