

BatchNorm: 用于加速神经网络的运行。BatchNorm 是神经网络层间传递的输入值内部归一化的强制执行者。内部归一化限制了通常发生在层内激活值中的协变量偏移。以下是其数学工作原理。

ReLU: 该模型中的激活函数。公式：`f(x)=max(0,x)`。有助于捕捉归一化后数据中的非线性。

我们的 Keras 模型结构概述于 [图 1.1](#ch01.xhtml#fig1_1)。它使用卷积层以及 BathNorm 来实现加速和稳定性，并使用 ReLU 作为激活函数，最终获得稠密输出。

使用的损失函数是稀疏分类交叉熵。其数学模型如下，见公式 (1.1)：

```
$L\_{CE} = - \\sum\\limits\_{i = 1}^{n}{t\_{i}\\ \\log\\left( p\_{i} \\right),\\mspace{9mu}{for}\\mspace{9mu} n\\mspace{9mu}{classes},}$ (1.1)
```

`where t[i] is the truth label and p[i] is the Softmax probability for the ith class`

**公式 1.1:** 序列模型损失函数

#### [1.3.3.2 SVM 模型](#ch01.xhtml#c_sec1_003_003_002)

使用此算法在 N 维空间中获得一个超平面，其中 N 是特征的数量。该超平面必须能够分离数据点，以便将其分类为不同的组。这个最优超平面是两个类别数据点之间距离最大的那个，从而能够创建良好的组分离。确保较大的边距距离为未来数据点提供了更高置信度分类的空间。

SVM 的损失函数可以如下表征，见公式 (1.2)。该损失函数有助于在 N 维空间中推导当前超平面，以准确计算多维数据集的分类。在此，它与五个特征一起用于特征工程后，以分析恶意和良性 DoH 数据包。SVM 模型在高维情况下非常有用，因为它提供了一个基于超平面分类的唯一损失函数。

```
$min\_{w}\\lambda \\parallel w \\parallel^{2} + \\sum\\limits\_{i = 1}^{n}{({1 - y\_{i} < x\_{i},w >})}\_{+}$ (1.2)
```

where `< \\mspace{-4mu} x_{i},w >` 是 SVM 函数，为输入 `x[i]` 和 SVM 参数 `w` 提供分类标签，而 `y[i]` 是真实标签。

**公式 1.2:** SVM 损失函数

## [1.4 结果与分析（含图表）](#ch01.xhtml#c_sec1_4)

对于我们的模型，有两个指标。第一个是 F1 分数指标，它能够结合模型的精确率和召回率。更具体地说，它被定义为这两个指标的调和平均数。公式如下，见公式 1.3。完美模型的 F 分数为 1。

```
\\begin{array}{lll} {F\_{1} = \\frac{2}{\\frac{1}{\\ {recall}\\ } \\times \\frac{1}{\\ {precision}\\ }}} & = & {2 \\times \\frac{\\ {precision} \\times {recall}\\ }{\\ {precision} + {recall}\\ }} \\\\ & = & \\frac{tp}{{tp} + \\frac{1}{2}({fp} + {fn})} \\\\ \\end{array}$ (1.3)
```

where tp 是真正例的数量，fp 是假正例的数量，fn 是假负例的数量

**公式 1.3:** F1 分数

第二个指标是稀疏分类准确率，它计算与真实整数标签匹配的标签百分比。

1. 特征工程模块 – 额外树分类器的输出显示于 [图 1.2](#ch01.xhtml#fig1_2)。将整个训练数据集输入特征工程模块，以获取最重要特征的可视化表示。

![图 1.2 特征重要性。](images/fig1_2.jpg)

[图 1.2 特征重要性。](#ch01.xhtml#Ffig1_2)

[图 1.2](#ch01.xhtml#fig1_2) 显示，在尝试识别 DoH 数据包时，有五个重要特征。以下是最重要的特征，这是我们研究独特提供的：

* `PacketLengthMean`
* `PacketLengthStandardDeviation`
* `PacketLengthMode`
* `PacketLengthCoefficientofVariation`
* `Duration`

可以看出，这些特征可以从我们的解析技术中轻松获得，因为它们是公开可用且未加密的。还观察到，一般来说，对数据包长度和时间的统计分析提供了足够的信息来识别 DoH 数据包。

2. 模型性能 – Keras 模型在整个数据集上提供了 90.8% 的稀疏分类得分。SVM 模型在数据集上提供了 F1 分数，并在测试集上达到了 97% 的准确率。两个模型在各个时代的准确率描述于 [图 1.3](#ch01.xhtml#fig1_3) 和 [图 1.4](#ch01.xhtml#fig1_4)。

两种架构的训练时间最长为 2 分钟，这使得对于我们的数据集大小来说极其快速。

![图 1.3 序列模型准确率。](images/fig1_3.jpg)

[图 1.3 序列模型准确率。](#ch01.xhtml#Ffig1_3)

![图 1.4 SVM 模型准确率。](images/fig1_4.jpg)

[图 1.4 SVM 模型准确率。](#ch01.xhtml#Ffig1_4)

## [1.5 结论](#ch01.xhtml#c_sec1_5)

我们的数据集提供了比之前工作更改进、更多样的数据集。本章提供了一组更具挑战性的数据包，以更好的方式复制现实世界环境，与之前的工作相比。所提出的深度学习模型在检测这些数据包方面提供了 93% 的准确率，证明在该任务上高度准确和稳健。最后，所提出的模型在恶意 DoH 检测方面也提供了 97% 的高准确率，超越了所有之前的工作，并在该领域树立了基准。协议检测和安全是一个高度挑战性的领域。本文提出了一种机制，研究人员可以通过我们的数据集进一步将深度学习和自动化引入检测和分类中。此外，这项工作引入了一种新的深度学习方法，用于在现实世界环境中分类和检测 DoH。未来工作将涉及探索 DoT 检测，以及使用深度学习解密这些协议中的消息。解密构成了最大的挑战，我们希望所提出的工作能作为此目的的基础。

## [参考文献](#ch01.xhtml#c_chapter1_RL_1)

1. [M. MontazeriShatoori](#ch01.xhtml#Cref1_1), L. Davidson, G. Kaur, and A. Habibi Lashkari, “Detection of dohtunnels using time-series classification of encrypted traffic”, in 2020 IEEE Intl Conf onDependable, Autonomic and Secure Computing, Intl Conf on Pervasive Intelligence andComputing, Intl Conf on Cloud and Big Data Computing, Intl Conf on Cyber Scienceand Technology Congress (DASC/PiCom/CBDCom/CyberSciTech), 2020, pp. 63–70. doi: [10.1109/DASC-PICom-CBDCom-CyberSciTech49142.2020.00026](https://doi.org/10.1109/DASC-PICom-CBDCom-CyberSciTech49142.2020.00026).

2. [D. Vekshin](#ch01.xhtml#Cref1_2), K. Hynek, and T. Cejka, “Doh insight: Detecting dns over https by machine learning”, New York, NY, USA: Association for Computing Machinery, 2020, isbn: 9781450388337. doi: [10.1145/3407023.3409192](https://doi.org/10.1145/3407023.3409192). \[Online\]. Available: [10.1145/3407023.3409192](https://doi.org/10.1145/3407023.3409192).

3. [\[Online\]](#ch01.xhtml#Cref1_3). Available: [https://dnscrypt.info/](https://dnscrypt.info)

4. [C. L ́ Opez Romera](#ch01.xhtml#Cref1_4), “Dns over https traffic analysis and detection”, 2020.

5. [L. Jun](#ch01.xhtml#Cref1_5), Z. Shunyi, L. Yanqing, and Z. Zailong, “Internet traffic classification using machine learning”, in 2007 Second International Conference on Communications andNetworking in China, IEEE, 2007, pp. 239–243.

6. [T. T. Nguyen](#ch01.xhtml#Cref1_6) and G. Armitage, “A survey of techniques for internet traffic classification using machine learning”, IEEE communications surveys & tutorials, vol. 10, no. 4, pp. 56–76, 2008.

