

The ![image](OEBPS/images/c11-Eqn-in-92.gif)and ![image](OEBPS/images/c11-Eqn-in-93.gif)are scaled to the range ![image](OEBPS/images/c11-Eqn-in-94.gif)and ![image](OEBPS/images/c11-Eqn-in-95.gif), respectively. The edge blocks are determined, and the ![image](OEBPS/images/c11-Eqn-in-96.gif)and ![image](OEBPS/images/c11-Eqn-in-97.gif)for edge blocks are taken to be ![image](OEBPS/images/c11-Eqn-in-98.gif)and ![image](OEBPS/images/c11-Eqn-in-99.gif), respectively. Then the calculation of the DCT coefficient, ![image](OEBPS/images/c11-Eqn-in-100.gif), is performed and the visible watermark is inserted in the original image block-by-block and watermarked image block is obtained as follows:

![image](OEBPS/images/c11_eqn16.gif)

[图 11.17(a)](#Chapter11.html#c11_fig17)介绍了水印方案的架构，[图 11.17(b)](#Chapter11.html#c11_fig17)介绍了不同模块在不同供电电压下的运行方式。DCT 模块与随机数生成器和不可见插入一起用于插入。插入模块将随机数添加到从原始图像计算出的 DCT 系数中。插入模块的输入是 ![image](OEBPS/images/c11-Eqn-in-101.gif)参数。用于可见水印的模块包括边缘检测、DCT、感知、缩放和嵌入因子以及可见水印插入。缩放和嵌入模块将计算 ![image](OEBPS/images/c11-Eqn-in-102.gif)和 ![image](OEBPS/images/c11-Eqn-in-103.gif)。可见水印插入模块将水印嵌入到宿主图像中。

![image](OEBPS/images/PBCS0600-11-f17.jpg)

图 11.17 低功耗 DCT 域不可见和域可见水印芯片：(a) 数据通路架构和 (b) 双电压和频率操作 ([Mohanty et al., 2005a](#Chapter11.html#c11_bib77))

### 11.7.2 视频水印硬件系统

到目前为止，本节讨论了图像文件的基于硬件的水印方案的实现。但本节的这一部分介绍了用于视频系统水印方案实现的不同模块。

#### 11.7.2.1 不可见-鲁棒空间域模块

开发了实时嵌入器-检测器模块，用于在 VLIW DSP 处理器框架内进行广播实现，并由 [Depovere *et al*. (1999)](#Chapter11.html#c11_bib24)、Strycker *et al*. ([1999](#Chapter11.html#c11_bib101), [2000](#Chapter11.html#c11_bib102)) 和 Termont *et al*. ([1999](#Chapter11.html#c11_bib107)) 提出。在水印插入过程中，伪随机数被添加到接收到的视频流中，并基于帧的亮度值。水印检测将取决于相关值计算。空间域和傅里叶域用于水印插入和检测。插入过程包括将伪随机数添加到流中。初始序列是用户密钥，然后进行移位并计算和以生成 *n* 个基本伪随机模式。然后从这 *n* 个模式中选择一个模式，从而创建一个密钥。创建的这个数字的大小是 ![image](OEBPS/images/c11-Eqn-in-104.gif)，与视频帧的大小相同。插入深度将决定水印的不可感知性和鲁棒性。较大的值使水印更安全，但比较小的数字更可能可见。该算法旨在提高安全性的同时降低可见性。如果存在水印，检测模块将检索密钥。选择一组 *G* 帧，然后进行折叠。计算其和，使用大小为 ![image](OEBPS/images/c11-Eqn-in-105.gif)的缓冲区，并与每个 *n* 个伪随机数进行相关性计算。这相当于 2D 循环卷积，可以在傅里叶域中高效执行。如果获得的相关性（称为决策变量）超过预定义阈值，则该视频被声明为带水印。[图 11.18(a)](#Chapter11.html#c11_fig18)显示了商业电视广播，其中使用了两个 Trimedia 处理器。[图 11.18(b)](#Chapter11.html#c11_fig18)显示了两台 PC 的设置，每台 PC 内部都有一个 Trimedia PCI 卡。

![image](OEBPS/images/PBCS0600-11-f18.jpg)

图 11.18 广播环境模拟：(a) 电视广播和 (b) 模拟 ([Depovere et al., 1999](#Chapter11.html#c11_bib24); Strycker et al., [1999](#Chapter11.html#c11_bib101), [2000](#Chapter11.html#c11_bib102); Termont et al., [1999](#Chapter11.html#c11_bib107))

#### 11.7.2.2 不可见-鲁棒空间域芯片

[Maes *et al*. (2000)](#Chapter11.html#c11_bib56) 提出了一种千禧年水印方案系统，用于 DVD 视频系统的实现。[Maes *et al*. (2000)](#Chapter11.html#c11_bib56) 讨论了水印检测器的位置和 DVD 副本的生成。该算法中水印的插入阶段包括在空间域中将缩放的水印添加到原始媒体对象信号中。检测阶段包括在傅里叶域中计算相关性。该算法由 Strycker *et al*. ([1999](#Chapter11.html#c11_bib101), [2000](#Chapter11.html#c11_bib102)) 提出。该方案中用于 DVD 视频水印的内存使用量应尽可能小。

设计并实现了一个实时检测模块，使用三个不同的模块，例如 Trimedia 处理器板、高端硅图形工作站和一个 FPGA。FPGA 平台实现是 DVD 水印最相关的实现 ([Maes *et al*., 2000](#Chapter11.html#c11_bib54))。实现了一个随机数生成器，它提高了整个模块和水印的鲁棒性。

[Tsai and Wu (2003)](#Chapter11.html#c11_bib111) 提出了原始视频编码水印的实现。使用标准视频编码器实现水印算法，如 MPEG-1/2/4、H.26x 和 Motion JPEG，用于实时 IP 保护。插入算法有三个步骤。最初读取水印，并使用混沌函数执行二进制转换。然后生成伪噪声，长度为 63 和 31，用于空间域和混沌变换域。然后执行插入，使用人类视觉特性，该特性将决定水印插入的权重因子 ![image](OEBPS/images/c11-Eqn-in-106.gif) 为边缘块的 16，否则为 4。

在水印检测的情况下，计算原始伪随机噪声的相关性。为了实现该算法，使用 Verilog 实现水印功能。这有利于使用 MPEG 编码器进行压缩并提高视频的鲁棒性。水印功能有三个部分，伪噪声生成器、数据通路、插入组件和水印信息生成器。

#### 11.7.2.3 不可见-鲁棒分形域模块

[Petitjean *et al*. (2002)](#Chapter11.html#c11_bib87) 提出了一种实时视频水印方案。这实际上借助分形近似嵌入水印。水印提取是通过执行与插入阶段相反的过程来完成的。C 编程语言用于编码器和解码器的实现。该算法的通用 PC 实现将产生比其他方法更好的结果。

为了提高水印的安全性，嵌入利用了分形编码的仿射变换不变性属性。水印嵌入有三个不同的阶段：

*   格式化和加密

*   覆盖生成

*   嵌入

