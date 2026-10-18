

- 存储侧控制器/缓冲器用于控制压缩数据的输出
- 内存控制器用于控制与外部存储器的数据访问
- 全局控制器/调度器用于确定和控制整个处理过程

![image](OEBPS/images/PBCS0600-11-f14.jpg)

图 11.14 (a) JPEG2000 编码器和 (b) 水印嵌入模块 ([Seo 和 Kim, 2003](#Chapter11.html#c11_bib96))

量化器/熵编码器模块包含水印方案。[图 11.14(b)](#Chapter11.html#c11_fig14) 显示了水印模块的架构。

### 11.7.1.6 不可见-鲁棒空间域模块

不可见-鲁棒插入算法由 [Mohanty *et al*. (2004)](#Chapter11.html#c11_bib82) 提出。该算法在 Xilinx FPGA 板上实现，并使用 VIRTEX 技术和 XCV50-BG256-6 目标器件进行了综合。

[图 11.15](#Chapter11.html#c11_fig15) 显示了编码器芯片的功能图。该设计的编码器由水印生成器、插入模块、地址解码器、控制器和寄存器组成。使用外部存储器来加载图像。LFSR 用于水印生成，这是设计中最重要的部分。LFSR 应避免随机上电，否则可能会永久卡在某些禁止状态中。插入模块由加法器/减法器、加法器、减法器、乘法器和移位器组成。控制器是一个八状态有限状态机 (FSM)。

![image](OEBPS/images/PBCS0600-11-f15.jpg)

图 11.15 不可见-鲁棒空间域水印模块 ([Mohanty et al., 2004](#Chapter11.html#c11_bib68))

### 11.7.1.7 可见空间域芯片

[Mohanty *et al*. (2004, 2005b)](#Chapter11.html#c11_bib81) 提出了一种可以在图像中插入两个可见水印的水印 VLSI 架构。在这种情况下，根据要求，两个水印中的任何一个都可以嵌入图像中。该设计使用 ![image](OEBPS/images/c11-Eqn-in-63.gif) 技术实现，占用面积为 ![image](OEBPS/images/c11-Eqn-in-64.gif)。该模块的功耗为 6.9286 mW，工作电压为 3.3 V，频率为 292.27 MHz。该设计实现了两种空间域可见水印算法。第一种是由 [Braudaway *et al*. (1996)](#Chapter11.html#c11_bib9) 提出的可见水印，第二种是由 Mohanty *et al*. (1999) 提出的空间域水印。

令 *i* 为原始图像，*w* 为水印图像，![image](OEBPS/images/c11-Eqn-in-65.gif) 为带水印图像。第一种算法的带水印图像如下获得：

![image](OEBPS/images/c11_eqn11.gif)

其中 ![image](OEBPS/images/c11-Eqn-in-66.gif) 是全局缩放因子，![image](OEBPS/images/c11-Eqn-in-67.gif)，且 ![image](OEBPS/images/c11-Eqn-in-68.gif) 是用于线性化立方根的线性回归系数。在第二种算法中，带水印图像块是通过修改 ![image](OEBPS/images/c11-Eqn-in-69.gif) 原始图像块 ![image](OEBPS/images/c11-Eqn-in-70.gif) 来获得的，如下所示：

![image](OEBPS/images/c11_eqn12.gif)

其中带水印图像块由 ![image](OEBPS/images/c11-Eqn-in-71.gif) 表示，缩放因子为 ![image](OEBPS/images/c11-Eqn-in-72.gif)，嵌入因子为 ![image](OEBPS/images/c11-Eqn-in-73.gif)。![image](OEBPS/images/c11-Eqn-in-74.gif) 图像块的缩放因子和嵌入因子使用以下方程获得：

![image](OEBPS/images/c11_eqn13.gif)

其中 ![image](OEBPS/images/c11-Eqn-in-75.gif)、![image](OEBPS/images/c11-Eqn-in-76.gif) 和 ![image](OEBPS/images/c11-Eqn-in-77.gif) 分别是 ![image](OEBPS/images/c11-Eqn-in-78.gif) 图像块的归一化平均灰度值、![image](OEBPS/images/c11-Eqn-in-79.gif) 图像块的灰度值归一化标准差以及图像的归一化平均灰度值。

[图 11.16](#Chapter11.html#c11_fig16) 显示了水印方案的架构。设计中包含多种单元，例如边缘检测单元、![image](OEBPS/images/c11-Eqn-in-80.gif) 计算单元、比较器、寄存器文件、乘法器和加法器。缩放因子和嵌入因子由 ![image](OEBPS/images/c11-Eqn-in-81.gif) 计算单元计算。水印过程使用保存在寄存器中的常数。像素处理在加法器和乘法器中执行。![image](OEBPS/images/c11-Eqn-in-82.gif) 计算单元和边缘检测单元均使用加法器、加法器/减法器、乘法器、除法器、比较器、累加器和指数单元构建。控制器使用五级有限状态机 (FSM) 设计。

![image](OEBPS/images/PBCS0600-11-f16.jpg)

图 11.16 空间域可见水印架构 ([Mohanty et al., 2004, 2005b](#Chapter11.html#c11_bib79))

### 11.7.1.8 可见小波域芯片

[Fan *et al*. (2005)](#Chapter11.html#c11_bib27) 提出了一种基于离散小波变换 (WT) 的水印设计。这减少了操作和资源共享，可以提高设计的整体效率。水印和原始图像被转换为三级多分辨率结构。原始图像随后被分为两个相同模式长度的不同序列。使用双路并行处理来计算处理时间。解多路复用器随后将信号发送到不同的元素进行处理。水印图像通过修改图像的系数来嵌入。

### 11.7.1.9 具有 DCT 域不可见-鲁棒和可见功能的低功耗芯片

[Mohanty *et al*. (2005a)](#Chapter11.html#c11_bib79) 提出了一种低功耗水印芯片。该芯片既支持不可见水印技术，也支持可见水印技术。该芯片的功耗显著降低，并且还集成了动态频率时钟和时钟门控。使用并行架构和三级流水线来显著提高水印的性能。设计和验证使用了 TSMC ![image](OEBPS/images/c11-Eqn-in-83.gif) 技术。芯片的双频率为 280 和 70 MHz，工作电压为 2.5 和 1.5 V。芯片的平均功耗估计为 0.3 mW。

由 [Mohanty (1999)](#Chapter11.html#c11_bib65) 和 Mohanty *et al*. ([2000a](#Chapter11.html#c11_bib73), [2000b](#Chapter11.html#c11_bib74)) 提出的 DCT 域可见水印算法以及由 [Cox *et al*. (1996)](#Chapter11.html#c11_bib37) 提出的频谱不可见水印算法用于该芯片的实现。计算原始图像的 DCT 系数并将其视为一个单一块。之后，识别出 1,000 个最大系数作为原始媒体对象在感知上重要的部分。计算水印 ![image](OEBPS/images/c11-Eqn-in-84.gif)，其中每个 ![image](OEBPS/images/c11-Eqn-in-85.gif) 根据 ![image](OEBPS/images/c11-Eqn-in-86.gif) 选择，其中 ![image](OEBPS/images/c11-Eqn-in-87.gif) 表示均值为 0、方差为 1 的正态分布。然后，水印被嵌入原始对象的 DCT 域中，在 ![image](OEBPS/images/c11-Eqn-in-88.gif) 的频率分量中使用以下公式：

![image](OEBPS/images/c11_eqn14.gif)

*m* 和 *n* 的值对应于 1,000 个最大 DCT 系数的像素位置，以及 ![image](OEBPS/images/c11-Eqn-in-89.gif)。可见插入算法如下：将原始图像 *I*（待加水印的图像）和水印图像 *W* 分块。计算原始图像所有块的 DCT 系数 ![image](OEBPS/images/c11-Eqn-in-90.gif)。每个块的缩放因子和嵌入因子计算如下：

![image](OEBPS/images/c11_eqn15.gif)

