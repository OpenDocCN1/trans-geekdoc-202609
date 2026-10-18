

# 现代消费电子产品中异构片上系统（SoC）架构的应用

现代消费电子（CE）产品（如智能手机、游戏机、平板电脑和数码相机）中异构片上系统（SoC）架构的应用已成为半导体行业的常见做法。内部 SoC 设计师或系统集成商大多从第三方 IP 厂商导入知识产权（IP）核，以尽量减少设计时间并满足严格的产品交付期限。这些第三方 IP（3PIP）核可以是 DSP/媒体处理器，例如 JPEG 图像压缩-解压缩（CODEC）、有限冲激响应（FIR）滤波器、无限冲激响应（IIR）滤波器、快速傅里叶变换（FFT）算法、哈尔小波变换（HWT）算法和离散余弦变换（DCT）算法，也可以是微型 IP 核/模块，例如加法器、乘法器和比较器。然而，这些 3PIP 核存在严重的信任问题，因为不可信的 IP 厂商可能会将称为“硬件木马”的恶意逻辑元素插入其 IP 核中，从而导致 SoC 出现故障/失效（[Tehranipoor and Koushanfar, 2010](#Chapter3.html#c03_bib32); [Liu *et al.*, 2014](#Chapter3.html#c03_bib12); Sengupta, [2016](#Chapter3.html#c03_bib20), [2017](#Chapter3.html#c03_bib21); [Chakraborty *et al.*, 2009](#Chapter3.html#c03_bib6); [Sengupta and Kundu, 2017](#Chapter3.html#c03_bib23)）（上述陈述在 SoC 生命周期中的主题式表现如 [图 3.1](#Chapter3.html#c03_fig1) 所示）。此外，受木马感染的 IP 核可能会通过在设计中创建后门泄露机密信息，或降低处理器的性能（[Bhunia *et al.*, 2013](#Chapter3.html#c03_bib4)）。SoC 设计生命周期中典型的可信和不可信阶段如 [图 3.2](#Chapter3.html#c03_fig2) 所示。

![image](OEBPS/images/PBCS0600-03-f01.jpg)

图 3.1 SoC 设计流程

![image](OEBPS/images/PBCS0600-03-f02.jpg)

图 3.2 CE 产品的 SoC 生命周期及其可能的漏洞（[Chakraborty et al., 2009](#Chapter3.html#c03_bib6)）

硬件木马的检测并不总是容易或直接，因为聪明的对手总是会插入仅在偶发条件下才会被激活的恶意逻辑（[Wolff *et al.*, 2008](#Chapter3.html#c03_bib34)）和/或仅在短时间内表现出其效果以逃避检测。此外，对完整 SoC 进行彻底的分析、测试和验证既复杂又耗时。木马激活条件称为触发条件，一旦触发，木马的效果称为有效载荷（[Narasimhan *et al.*, 2010](#Chapter3.html#c03_bib13)）。逻辑测试（[Banga and Hsiao, 2009](#Chapter3.html#c03_bib2)）和旁路信道分析（[Narasimhan *et al.*, 2010](#Chapter3.html#c03_bib13); [Koushanfar and Mirhoseini, 2011](#Chapter3.html#c03_bib11））是两种常用的检测硬件木马的技术（[Narasimhan *et al.*, 2010](#Chapter3.html#c03_bib13); [Liu *et al.*, 2014](#Chapter3.html#c03_bib12)）。在第一种方法中，执行功能或结构测试（[Chakraborty *et al.*, 2009a](#Chapter3.html#c03_bib7); [Wolff *et al.*, 2008](#Chapter3.html#c03_bib34); [Banga and Hsiao, 2009](#Chapter3.html#c03_bib2)）以产生罕见条件，从而使硬件木马逻辑的效果在输出中得到体现。这种检测方法对超小型木马有效（[Narasimhan *et al.*, 2010](#Chapter3.html#c03_bib13)）。在第二种方法中，通过测量物理“旁路信道”参数（如延迟（[Jin and Makris, 2008](#Chapter3.html#c03_bib10); [Rai and Lach, 2009](#Chapter3.html#c03_bib16)）或功耗签名（[Agrawal *et al.*, 2007](#Chapter3.html#c03_bib1); [Banga and Hsiao, 2008](#Chapter3.html#c03_bib3); [Rad *et al.*, 2010](#Chapter3.html#c03_bib15)））来检测硬件木马。在这种方法中，无需激活木马逻辑并监控其对输出的影响，即可检测硬件木马。

硬件木马有多种类别，我们将在 3.2.1 节中讨论；然而，我们主要关注如何针对一种特定类型的木马提供安全性（检测），这种木马会改变基于 DSP 的 IP 核的功能或输出。更具体地说，我们讨论了通过双模块冗余（DMR）调度和厂商分配过程，为 DSP 核设计低成本硬件木马安全数据通路设计的过程（[Rajendran *et al.*, 2013](#Chapter3.html#c03_bib17); [Sengupta *et al.*, 2017b](#Chapter3.html#c03_bib27)）。为了获得低成本的抗木马设计，对 DSP 核进行基于粒子群优化（PSO）的设计空间探索（DSE）（Sengupta and Sedaghat, [2011](#Chapter3.html#c03_bib24), [2013](#Chapter3.html#c03_bib25)）。

## 3.2 硬件木马的类型

本节讨论了不同类型的硬件木马、在更高抽象级别处理 DSP 核的这种木马安全性的优势，以及硬件木马威胁模型的详细信息。

### 3.2.1 木马特征

我们在此讨论基于木马的硬件威胁的主要分类（如 [图 3.3](#Chapter3.html#c03_fig3) 所示）（[Chakraborty *et al.*, 2009](#Chapter3.html#c03_bib6); [Sinanoglu *et al.*, 2013](#Chapter3.html#c03_bib31); [Sengupta, 2017](#Chapter3.html#c03_bib21)）。数字硬件木马分为两种类型：基于触发的和基于有效载荷的。如前所述，木马的触发表示激活它，可以通过组合逻辑或时序逻辑机制来执行。同样，木马的有效载荷表示木马逻辑的效果，可以改变功能、降低性能，或在不改变功能的情况下泄露秘密信息。

![image](OEBPS/images/PBCS0600-03-f03.jpg)

图 3.3 数字硬件威胁的广义分类

**基于组合触发的硬件木马：** 这种类型的木马在非常罕见的条件或事件下被触发。在该条件出现之前，电路工作正常。例如，如 [图 3.4](#Chapter3.html#c03_fig4) 所示，原始输出（*Q*）对于 *A* 和 *B* 的所有输入组合都与受木马感染的输出（*Q*^(\*)) 相同，除了 *A* = *B* = 0 的情况。在这种情况下，插入的木马逻辑被触发，并在 *Q*^(\*) 中生成错误输出作为有效载荷。因此，在这个电路中，*A* = *B* = 0 是触发条件。

![image](OEBPS/images/PBCS0600-03-f04.jpg)

图 3.4 基于罕见事件的组合触发式硬件木马（[Chakraborty et al., 2009](#Chapter3.html#c03_bib6)）

**基于时序触发的硬件木马：** 这种类型的木马在计数器的特定计数值时被触发。一旦触发，电路就会产生错误输出（[Chakraborty *et al.*, 2009](#Chapter3.html#c03_bib6)）。例如，如 [图 3.5](#Chapter3.html#c03_fig5) 所示，有 *p* 个计数器，所有计数器都使用时钟信号同步执行。一旦计数器达到 2^(*p*)−1 的计数值，木马逻辑就会被触发，并在 *Q*^(\*) 中生成错误输出作为有效载荷，而不是 *Q*。由于这种类型的木马在特定时间段内被触发，它也被称为“定时炸弹硬件木马”。

![image](OEBPS/images/PBCS0600-03-f05.jpg)

图 3.5 同步计数器时序触发式硬件木马

