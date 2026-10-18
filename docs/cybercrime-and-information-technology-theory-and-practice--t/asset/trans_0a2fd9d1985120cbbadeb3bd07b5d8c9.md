

# [Chapter 8 Mobile Devices](#contents.xhtml#re_c8)

## [The Smartphone](#contents.xhtml#re_c8)

DOI: [10.4324/9780429318726-8](https://doi.org/10.4324/9780429318726-8)

## [Objectives](#contents.xhtml#re_h-8-1)

完成本章后，学生将能够：

* 了解移动电话技术的历史意义。
* 识别设备的主要组件和架构。
* 了解蜂窝网络的工作原理。
* 了解智能手机的主要组件、操作系统、应用程序和架构。
* 了解移动设备的追踪。
* 识别移动安全面临的威胁。

## [8.1 Introduction](#contents.xhtml#re_h-8-3)

智能手机和平板电脑改变了我们的生活。随时随地联系几乎任何人的能力就在您的掌心；曾经需要花时间查找的信息，现在只需点击一下即可获得。数千个免费应用程序帮助我们充分利用技术，而无需具备高超的专业知识。不再需要打字——发送消息时启动语音识别应用程序，直接对着手机说话即可——不再需要拇指！

*移动设备一词是指所有手持式计算设备，例如电子阅读器、手机、平板电脑等，这些设备便于携带，并支持通过无线传输（无需物理网络连接）传输高质量多媒体数据，例如数据、语音和视频。*

这些设备通常具有 Wi-Fi 和蜂窝网络连接、小型可充电电池（通常是锂离子或 Li-ion 电池）、触摸屏界面、虚拟助手（例如 Siri 或 Alexa）以及下载应用程序或应用的功能。

本章将讨论移动设备及其功能、基本组件、架构、蜂窝网络结构和安全性。

不久以前，还有一个时代，不在家的人必须找一个电话亭才能进行一次简单的电话通话（[Figure 8.1](#c8.xhtml#f8.1)）。智能手机永远地改变了我们的生活。不可或缺的智能手机几乎可以做任何事情，并已成为现代社会所有需求的 `Swiss army knife`。它取代了我们过去依赖的许多东西，例如闹钟、应答机、计算器、摄像机、相机、手电筒、GPS 设备、固定电话、公用电话、地图、音乐播放器、寻呼机、手表、地址簿等。

![FIGURE 8.1 The disappearance of phone booths. Courtesy of Shutterstock.](images/fig8.1.jpg)

**FIGURE 8.1** The disappearance of phone booths. Courtesy of Shutterstock.

## [8.2 A Brief History and Significant Milestones of Mobile Phones](#contents.xhtml#re_h-8-4)

移动无线电实际上自 1800 年代以来就已存在，当时 `Heinrich Hertz` 基于 `James Clerk Maxwell's` 的光电磁理论证明了发送和接收无线电波的可能性。此外，`Guglielmo Marconi` 在 1901 年在陆地基站和一艘船之间建立了无线电链路。^([^(402)](#fn402))

在 1970 年代，移动电话用于车辆和火车，但不是手持式设备。1973 年，摩托罗拉推出了第一款 `portable radio telephone` 摩托罗拉 DynaTAC，DYNamic Adaptive Total Area Coverage^([^(403)](#fn403))

![FIGURE 8.2 Motorola’s DynaTAC 8000X. Courtesy of Shutterstock.](images/fig8.2.jpg)

**FIGURE 8.2** Motorola’s DynaTAC 8000X. Courtesy of Shutterstock.

在美国，第一个模拟自动蜂窝网络于 1983 年启动。它被称为高级移动电话系统（AMPS），是第一代移动标准，决定了移动设备如何与基站通信，为每次对话使用不同的频率。该标准由 AT&T 的子公司贝尔实验室开发。^([^(404)](#fn404))

在 1990 年代，`second generation (2G)` 蜂窝通信出现了两种系统。第一种是欧洲移动通信全球系统（GSM），由欧盟强制实施；第二种是美国开发的码分多址（CDMA）标准。2G 蜂窝网络与 1G 的不同之处在于它使用数字传输。因此，2G 使容量扩展成为可能，并使手机在全球广泛使用。

随着对更快无线数据传输需求的增长，2G 无法处理这种增长。因此，`third generation (3G)` 承诺提供更强大的数字蜂窝网络。3G 通信网络出现在 21 世纪初，提供多媒体访问和手机上广泛使用互联网的功能。3G 使用一组电话塔将信号传输到手机并从手机接收信号，确保稳定快速的连接。最初，3G 的空口数据速率在 384 kbit/s 覆盖范围和 2 Mbps 室内/微小区覆盖范围之间测量。此后，该技术发展为高速移动宽带网络覆盖，称为 3.5G、3G+ 和 turbo 3G，提供更快的下载速度，并允许数据传输速度高达 14 Mbps。^([^(405)](#fn405))

2007 年，苹果推出了 iPhone。这是第一款使用多点触控界面的手机，标志着多媒体新时代的开始。

蜂窝通信的两个全球标准是 GSM 和 CDMA。两者都是 2G 通信标准。GSM 已占据国际市场的近五分之二。^([^(406)](#fn406))

要发起呼叫，语音首先从模拟声波转换为数据（数字），并由蜂窝网络传输。用户身份模块（`SIM`）卡包含用户的移动信息，包括分配给移动用户的个人号码。GSM 用户的一个优势是 `SIM` 卡可以移动到另一部手机，轻松解锁并将设备转移到另一个网络。但是，使用 CDMA 时，`SIM` 卡仅适用于同一公司的移动设备。

相比之下，在美国开发的 CDMA 被归类为 `code division` 系统，并基于扩频信令，导致用户的信号在时频域内扩展。这意味着许多用户可以瞬时通过单个信道发送信息，或共享一个频段。^([^(407)](#fn407))

2007 年 iPhone 的问世将移动互联网带入了每个人的手中（[Figure 8.3](#c8.xhtml#f8.3)）。其多媒体功能和移动互联网访问使 3G 成为“慢”网络。因此，由芬兰 Telia Sonera 于 2010 年推出的 `fourth generation (4G)` 蜂窝网络承诺为移动用户支持 100 Mbps 峰值速率和低移动性下的 1 Gbps。^([^(408)](#fn408))

![FIGURE 8.3 The first-generation iPhone. Courtesy of Shutterstock.](images/fig8.3.jpg)

**FIGURE 8.3** The first-generation iPhone. Courtesy of Shutterstock.

