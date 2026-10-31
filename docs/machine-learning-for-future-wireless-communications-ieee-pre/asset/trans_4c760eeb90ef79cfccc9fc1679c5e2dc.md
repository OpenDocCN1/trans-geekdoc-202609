
作为 `DNN` 需要完全连接隐藏层中的所有节点，参数数量通常呈指数增长。为解决此问题，提出了 `CNNs`，其中利用了若干卷积层来提取输入数据的 高维 特征。如 [图 14.3](#c14.xhtml#c14-fig-0003) 所示，`CNN` 利用相邻像素的相关性来减少神经网络中的参数数量以及潜在的计算复杂度，并且已被广泛应用于一些图像处理任务。`CNNs` 的典型示例包括 `AlexNet`（Krizhevsky et al.，[2012](#c14.xhtml#c14-bib-0018)）、`VGG`（Simonyan and Zisserman，[2014](#c14.xhtml#c14-bib-0027)）和 `ResNet`（He et al.，[2016](#c14.xhtml#c14-bib-0013)）。

`DNNs` 的另一个问题是其处理视频流中时间相关目标检测和跟踪任务的能力有限。为了纳入时域相关性，循环架构已在标准 `DNN` 架构之上使用，如 [图 14.4](#c14.xhtml#c14-fig-0004) 所示；时域信息通过各层中不同神经元之间的循环传播来建模。虽然如前所述 `RNN` 结构可以提取时间相关特征，但它通常会遭受梯度消失问题（Ian Goodfellow，[2016](#c14.xhtml#c14-bib-0015)）；最近已发明了几种改进的网络架构，例如长短期记忆（Gers et al.，[1999](#c14.xhtml#c14-bib-0007)）和双向 `RNNs`（`BRNNs`）（Graves and Schmidhuber，[2005](#c14.xhtml#c14-bib-0009)）。

![图 14.4 一个 RNN 网络架构的说明，该架构将神经元的输出反馈回神经元的输入。](images/c14f004.jpg)

[图 14.4](#c14.xhtml#R_c14-fig-0004) 一个 RNN 网络架构的说明，该架构将神经元的输出反馈回神经元的输入。

在所有这些神经网络中，激活函数和损失函数通常被认为是最重要的组成部分：前者引入非线性，后者提出神经网络的评估指标。典型的激活函数是 `tanh`（Glorot et al.，[2011](#c14.xhtml#c14-bib-0008)）、`sigmoid` 和修正线性单元（`ReLU`）（Hao Ye，[2017](#c14.xhtml#c14-bib-0012)），而交叉熵（`CE`）和均方误差（`MSE`）通常被归类为常见的损失函数。

由于大量激活函数和损失函数的评估需要巨大的计算能力，`DL` 技术直到 2012 年才得到广泛部署，当时高性能图形处理单元（`GPUs`）和张量处理单元（`TPUs`）（Jouppi et al.，[2017](#c14.xhtml#c14-bib-0016)）变得流行。与此同时，除了传统的计算机视觉和语音处理任务外，`DL` 技术还被用于解决其他领域中的许多具有挑战性的问题，例如医学图像诊断（Litjens et al.，[2017](#c14.xhtml#c14-bib-0020)）、棋类游戏（Silver et al.，[2016](#c14.xhtml#c14-bib-0026)）和无线通信（O'Shea and Hoydis，[2017](#c14.xhtml#c14-bib-0024)）。例如，在无线通信中，最优的多输入多输出（`MIMO`）检测算法可以用自动编码器网络很好地近似，如（Yan et al.，[2017](#c14.xhtml#c14-bib-0030)）所示，并且使用 `DL` 的联合信道估计和信号检测结构已在（Hao Ye，[2017](#c14.xhtml#c14-bib-0012)）中提出。

作为现代无线通信系统中的关键要素，信道编码通常被认为是一项计算密集型任务，其中专用集成电路（`ASIC`）通常被视为唯一解决方案。随着对无线通信中支持不同类型信道代码的需求不断增长，设计挑战日益增加。得益于神经网络的泛化能力，`DL` 技术已与不同的信道编码方案相结合，并提出了几项开创性工作。在本章的其余部分，我们根据不同类型的神经网络对它们进行分类，这可能为未来的通用编码器和解码器铺平道路。

## 14.2 用于信道编码的 DNNs

`DNN` 是一种相对简单的神经网络，通过增加网络中的层数来增强学习性能。`DNN` 的输入和输出与信道编码一致，这使得使用 `DNN` 进行解码成为可能。

在数字通信系统中，信息序列通过信道编码被转换为编码序列。通常这些序列是二进制序列，因此这种映射可以被视为可由神经网络学习到的分类问题。这启发我们使用 `DNNs` 而不是传统的解码器来解码接收到的序列。

![图 14.5 用于直接极化解码的 DNN 方法。](images/c14f005.jpg)

[图 14.5](#c14.xhtml#R_c14-fig-0005) 用于直接极化解码的 DNN 方法。

关于此问题的代表性工作包括使用 `DNNs` 直接解码（Gruber et al.，[2017](#c14.xhtml#c14-bib-0010)），将 `DNNs` 与传统的解码方法（如置信传播（`BP`）和逐次抵消（`SC`）缩放方法）相结合以解码中等长度码（Cammerer et al.，[2017](#c14.xhtml#c14-bib-0003)）（Doan et al.，[2018](#c14.xhtml#c14-bib-0005)），使用 `DNNs` 联合均衡和解码（Hao Ye，[2017](#c14.xhtml#c14-bib-0012)）（Xu et al.，[2018](#c14.xhtml#c14-bib-0029)），以及使用 `DNNs` 解码多码（Wang et al.，[2018](#c14.xhtml#c14-bib-0028)）。

### 14.2.1 使用 DNNs 直接解码

（Gruber et al.，[2017](#c14.xhtml#c14-bib-0010)）中的作者提出了用于长度为 (16, 8) 的极化码的神经网络解码器（`NND`）。`NND` 是一个具有层 (16, 128, 64, 32, 8) 的 `DNN`，其结构如 [图 14.5](#c14.xhtml#c14-fig-0005) 所示。

如 [图 14.5](#c14.xhtml#c14-fig-0005) 所见，![图像](images/c14-i0001.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>k</mi></mrow></math>信息位被编码为 ![图像](images/c14-i0002.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>N</mi></mrow></math> 位极化码，然后由 `BPSK` 调制并由发射机发送。在接收端，通过信道传输的信号被接收并解码。为了用 `DNN` 替换整个传统解码器，网络的输入要么是实际值 ![图像](images/c14-i0003.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="bold">y</mi></mrow></math> 要么是对数似然比（`LLR`），其中输出为估计的码字。这里 `LLR` 定义为：

(14.1)![方程](images/c14-math-0001.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mtable> <mtr> <mtd> <mtext>LLR</mtext> <mo>=</mo> <mn>2</mn> <mo>&#42;</mo> <mi mathvariant="bold">y</mi> <mo stretchy="false">/</mo> <msup> <mi>&#963;</mi> <mn>2</mn> </msup> <mo>,</mo> </mtd> </mtr> </mtable> </mrow> </math> 

其中 ![图像](images/c14-i0004.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="bold">y</mi></mrow></math> 是接收到的信号，而 ![图像](images/c14-i0005.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msup><mi>&#963;</mi><mn>2</mn></msup></mrow></math> 是噪声方差。

