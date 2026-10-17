

**Alex Alexandrou** 是 John Jay College of Criminal Justice（约翰·杰伊刑事司法学院）安全、火灾与应急管理系的助理教授。他获得 Youngstown State University（扬斯敦州立大学）的学士学位，Brooklyn College of the City University of New York（纽约市立大学布鲁克林学院）的硕士学位，以及 Pace University（佩斯大学）的计算机研究博士学位。Alexandrou 博士在商业和学术环境中都拥有丰富的工作经验。他在健康信息技术和运营领导方面拥有 18 年的经验，包括软件集成、生物识别和访问控制系统、通过将物理服务器过渡使用来部署虚拟化，以及将 IT 架构与基于云的网络和安全平台/技术重新对齐。自 2015 年以来，Alexandrou 博士在本科和研究生阶段教授过网络安全、健康信息技术和远程医疗课程。他是一位坚信 `Hard work`、`determination and never giving up on what you really want to do.` 的人。

Alexandrou 博士在医疗保健领域的移动设备安全、Deep Fake 视频、网络犯罪和生物识别认证方面进行了研究。他目前的研究兴趣包括医疗保健应用的系统安全和隐私、移动取证调查以及移动设备漏洞和威胁。

# [Chapter 1 Understanding Essential Computer Concepts](#contents.xhtml#re_c1)

DOI: [10.4324/9780429318726-1](https://doi.org/10.4324/9780429318726-1)

## [Objectives](#contents.xhtml#re_h-1-1)

完成本章后，学生将能够：

*   了解计算设备中的信息处理

*   解释位和字节之间的区别

*   了解二进制、十六进制 ASCII、EBCDIC 和 UNICODE 编码

*   了解布尔代数、逻辑门和真值表

*   解释色深、颜色模型和屏幕分辨率

*   了解有损压缩和无损压缩

*   了解量子计算的基础知识

*   识别计算机术语

*   了解计算机及其周围技术的历史

## [1.1 Understanding Computation](#contents.xhtml#re_h-1-3)

### [Conventional Computer Systems](#contents.xhtml#re_h-1-4)

技术创新是大脑的计算能力与模拟人类智能的愿望的结合。技术的进步是人类解决问题和提高生活质量愿望的结果。电子设备是与我们解决问题的努力相关的技术进步。

计算机是一种电子设备，它接受输入，通过修改或操纵数据来处理数据，存储数据以供进一步参考，并产生输出，所有这些都根据一系列指令或命令进行。这一组过程是冯·诺依曼架构，或称冯·诺依曼概念，由 John von Neumann 于 1945 年发表，描述了一种拟议的计算机架构。该概念描述了一种存储程序计算机，其中指令和程序数据存储在同一内存中。^([¹](#fn1))

所有传统计算设备仍然通过这四个基本功能运行：接收输入、处理数据、存储数据和产生输出。

首先，用户使用触控板、键盘、鼠标、触控板、麦克风或摄像机等输入设备输入信息。数据被转换为二进制数据，标识为 `0` 或 `1`。中央处理器（`CPU`），即计算机的“大脑”，在内存的帮助下，分析如何显示每个字符。

接下来，`CPU` 操纵二进制数据并将其存储在内存中以供进一步参考。`CPU` 处理二进制数据并创建输出，在屏幕、扬声器或打印机上查看。要在显示器上查看图像，`CPU` 与软件应用程序或向计算机显卡发送指令的程序协同工作。显卡控制视觉显示，决定如何安排屏幕以创建图像。所有这些都通过计算机遵循的一系列指令或命令来完成。复杂任务，例如编辑高清视频或 3D 建模和渲染，需要更多的处理能力和内存。最后，处理后的数据存储在硬盘驱动器（`HD`）上。[Figure 1.1](#c1.xhtml#f1.1) 总结了计算设备中的信息处理。

![FIGURE 1.1 Information processing in a computing device.](images/fig1.1.jpg)

**FIGURE 1.1** Information processing in a computing device.

计算机一词最初是数学术语。“单词 `computer` 是拉丁语单词 `putare`（意为‘思考或训练’）和 `com`（意为‘一起’）的组合。《牛津英语词典》将该词的首次使用定为 1579 年，将其与‘算术或数学计算’联系起来。”^([²](#fn2))

![FIGURE 1.2 Computers at work – calculating test data. Ames Research Center, c1958. Photograph from National Aeronautics and Space Administration (NASA).](images/fig1.2.jpg)

**FIGURE 1.2** Computers at work – calculating test data. Ames Research Center, c1958. Photograph from National Aeronautics and Space Administration (NASA).

值得注意的是，数理逻辑领域对计算机科学的发展产生了重大影响。这一实例体现在程序验证领域。“由于计算机程序只是计算的正式描述，因此可以像使用逻辑验证数学定理一样对其进行验证。”^([³](#fn3))

希腊哲学家亚里士多德为 `mathematical logic` 提供了基础，使后来的想法得以成为现实。亚里士多德将逻辑视为哲学家和科学家的工具。^([⁴](#fn4))

20 世纪 60 年代的美国太空计划，以及为其任务进行的研究和开发，帮助加速了计算机行业的发展，导致电子和计算机系统发生了巨大变化 ([Figures 1.3](#c1.xhtml#f1.3) 和 [1.4).](#c1.xhtml#f1.4)

![FIGURE 1.3 Electronic Machine Computing Branch, IBM 704 Date Processor, c1958. Photograph from National Aeronautics and Space Administration (NASA).](images/fig1.3.jpg)

**FIGURE 1.3** Electronic Machine Computing Branch, IBM 704 Date Processor, c1958. Photograph from National Aeronautics and Space Administration (NASA).

![FIGURE 1.4 Dr. Werner von Braun (seated) examining a Saturn computer in the Astrionics Laboratory at the Marshall Space Flight Center, c1966. Photograph from National Aeronautics and Space Administration (NASA).](images/fig1.4.jpg)

**FIGURE 1.4** Dr. Werner von Braun (seated) examining a Saturn computer in the Astrionics Laboratory at the Marshall Space Flight Center, c1966. Photograph from National Aeronautics and Space Administration (NASA).

## [1.2 Input](#contents.xhtml#re_h-1-5)

用户界面（`UI`）是用户与机器（`computer`）交互的方式。基本的人机交互包括物理输入，例如键盘、鼠标、语音命令、屏幕上的选项卡（其中运行命令），以将物理动作和条件转换为二进制数据 ([Figure 1.5](#c1.xhtml#f1.5))。 

![FIGURE 1.5 A research to improve the human–computer interface, c1966. MAGIC (Machine for Automatic Graphics Interface to a Computer) Photograph from NIST Digital Archives.](images/fig1.5.jpg)

**FIGURE 1.5** A research to improve the human–computer interface, c1966. MAGIC (Machine for Automatic Graphics Interface to a Computer) Photograph from NIST Digital Archives.

### [Understanding Binary Data](#contents.xhtml#re_h-1-6)

