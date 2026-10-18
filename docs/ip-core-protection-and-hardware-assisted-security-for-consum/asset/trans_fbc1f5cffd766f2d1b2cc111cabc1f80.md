

当今的消费电子（CE）设备，从现代智能手机、智能电视、家用电器、机顶盒、平板电脑、数码相机到最近的智能音箱，均采用片上系统（SoC）平台设计（[Thavalengal and Corcoran, 2016](#Chapter7.html#c07_bib40); [Mohanty, 2015](#Chapter7.html#c07_bib18); [Kim *et al.*, 2015](#Chapter7.html#c07_bib12)）。这些 SoC 包含各种系统模块，例如存储器（SRAM、Flash）、模数转换器、定制处理器或协处理器、DSP 内核、A/V 编解码器和无线调制解调器。在这些模块中，以 IP 核形式存在的 DSP 内核主要负责高速、低功耗、最小硅面积下的数据/功率密集型计算（[Li *et al.*, 2015](#Chapter7.html#c07_bib16)）。因此，DSP IP 核是每个基于 SoC 的 CE 设备的核心。例如，用于语音互联网协议（VoIP）和无线移动设备电信基础设施的 ConnX D2 DSP IP 核（[ConnX, 2009](#Chapter7.html#c07_bib42)）。在蜂窝电话系统中，它用于语音编码/解码过程。低端 DSP IP 核包含在数码相机、便携式电话、消费音频、耳机中，而中端 DSP 核包含在蜂窝电话、传真/语音接收器中。最后，高端 DSP IP 核包含在各种 CE 系统中，包括无线基站和有线调制解调器。此外，DSP IP 核的可重用性最大限度地提高了设计生产力，以应对电子系统日益增加的设计复杂性（[Castillo *et al.*, 2007](#Chapter7.html#c07_bib6)），从而保持基于 SoC 的 CE 设备全球供应链的平衡（Sengupta and Sedaghat, [2011](#Chapter7.html#c07_bib33), [2013](#Chapter7.html#c07_bib34)）。

这些可重用的 DSP IP 核需要 IP 厂商/设计师在研究、人力、资金和时间方面进行大量投资。因此，必须保护它们免受克隆和/或侵权以及逆向工程（RE）等新兴 IP 威胁的影响（[Roy and Sengupta, 2017](#Chapter7.html#c07_bib24); [Sengupta and Bhadauria, 2016](#Chapter7.html#c07_bib28); [Wong *et al.*, 2004](#Chapter7.html#c07_bib47); [Koushanfar, 2012](#Chapter7.html#c07_bib13); [Alkabani and Koushanfar, 2007](#Chapter7.html#c07_bib1); [Sengupta and Kundu, 2017](#Chapter7.html#c07_bib29); [Sengupta *et al.*, 2018](#Chapter7.html#c07_bib35)）。根据文献资料，2013 年 G20 国家因盗版和假冒造成的总财政收入损失为 960 亿至 1300 亿美元，预计到 2022 年将增加至 1990 亿至 2700 亿美元。据预测，国际上销售的电子产品中有 10% 是伪造品（[Guajardo *et al.*, 2008](#Chapter7.html#c07_bib11); [Lao and Parhi, 2015](#Chapter7.html#c07_bib14)）。攻击者可以在未经 IP 所有者合法许可的情况下“静默”地重用 DSP IP 核，以节省设计时间、成本和精力（[Sengupta, 2016](#Chapter7.html#c07_bib26)）。他/她可以通过 RE 从架构中轻松识别 DSP IP 核的功能。IP 核的 RE 是识别其设计、结构和功能的过程（[Rajendran *et al.*, 2013](#Chapter7.html#c07_bib22)）。使用 RE，可以识别器件技术（[Intel Transistors, 2012](#Chapter7.html#c07_bib39)）、提取门级网表（[Torrance and James, 2009](#Chapter7.html#c07_bib43)）并推断 IP 功能（[ExtremeTech, 2012](#Chapter7.html#c07_bib10））。虽然根据 1984 年《半导体芯片保护法》（SCPA），RE 是一种用于教学、分析和评估目的的合法过程；但是，攻击者可以利用 RE 过程进行非法的 IP 盗版/攻击。如果攻击者能够通过 RE 识别 DSP IP 核的功能，他/她还可以将恶意木马逻辑插入 IP 核。因此，以一种能够提供强大抗 RE 能力的方式设计 DSP IP 核至关重要（[Yang *et al.*, 2013](#Chapter7.html#c07_bib48); [Parhi, 2012](#Chapter7.html#c07_bib20); [Lao and Parhi, 2015](#Chapter7.html#c07_bib14); [Walz and Schrder, 2016](#Chapter7.html#c07_bib45); [Sengupta, 2017](#Chapter7.html#c07_bib27)）。受保护的 DSP IP 核在不同 CE 设备中的主题式攻击场景如 [Figure 7.1](#Chapter7.html#c07_fig1) 所示（[Mohanty, 2003](#Chapter7.html#c07_bib17); [Sengupta, 2016](#Chapter7.html#c07_bib26)）。实现抗 RE 弹性的一种方法是通过转换 DSP IP 核的架构来模糊其功能。这种转换应将 DSP IP 核的标准结构转换为不明显的架构，同时保持正确的功能。因此，功能将不易从其结构中识别，从而增加对手的 RE 复杂性。此过程称为结构混淆。更广义地说，混淆是一种模糊或伪装设计（产品）实际功能的过程，以保护其知识产权内容。尽管硬件混淆源于软件混淆，但前者比后者更复杂，尽管两者的根本目标相同。软件混淆旨在使用诸如死代码消除、代码展开等技术隐藏算法的实现代码，而硬件混淆旨在模糊电路（硬件）的功能/结构。此过程可分类，因为它可以通过多种复杂技术实现，具体取决于硬件电路描述所在的形式（设计抽象层。参阅 [Figure 7.2](#Chapter7.html#c07_fig2)），例如 RTL 代码、网表、布局、制造芯片。有时，经过定制的软件混淆方法可以应用于硬件混淆。但是，根据硬件设计抽象层级，可能需要一种完全专用的方法来进行硬件混淆。总之，硬件混淆器（过程或算法）负责将设计表示“D”转换为其混淆形式“O(D)”，该形式与“D”具有相同的功能，但对于试图从“O(D)”恢复“D”的对手来说是不可理解的。关于混淆威胁模型的更多细节将在本章后续章节中解释。

![image](OEBPS/images/PBCS0600-07-f01.jpg)

Figure 7.1 面向 CE 设备的安全 DSP IP 核的主题式表示，可抵御对手攻击

![image](OEBPS/images/PBCS0600-07-f02.jpg)

Figure 7.2 集成电路设计的抽象层级

#### 7.1.1 威胁模型

硬件结构混淆将 IP 核的原始硬件设计架构转换为不明显的结构架构。因此，增强了 RE 复杂性，因为攻击者从转换后的结构中发现 IP 核的实际功能更加困难。因此，它提供了针对由 `RE` 导致的威胁（如 `IP 盗版`、`IP 侵权（假冒）` 和 `木马插入`）的防御。

#### 7.1.2 在更高设计抽象层级提供安全性的优势

