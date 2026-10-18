
# 视频内容分析与 IP 视频监控

视频内容分析（Video Content Analysis, VCA），如今更常被称为视频分析（Video Analytics），是周界入侵检测和视频监控演进中非常创新且重要的一项进步。绩效研究表明，负责监控实时视频流或审查录制视频画面的人员，其有效性可能在短短 22 分钟内大幅下降。如果考虑到在 8–12 小时的班次中盯着显示器，或观看数小时的录制画面来发现入侵者，人为疏忽导致漏检威胁的窗口期非常大。视频分析利用自动化算法和检测参数，识别特定视野内的移动、异常或行为模式。例如，[Figure 33.2](#9781466508507_epub_c33_r1.htm#fig_33.2) 描绘了一台 IP 监控摄像机，正在跟踪停车场视野内的移动，其中一个人在某辆或某组可能被视为高价值资产的车辆附近停留。

![](OEBPS/images/fig_33.2.jpg)

**Figure 33.2  Sample video analytics for motion or loitering.**

使用视频分析，人工干预可以大幅减少，显著降低疲劳相关错误的数量，同时允许更高效地管理视频监控系统。视频分析提供来自多台摄像机的可定制实时安全事件分析和检测，同时识别事件发生，并提供工具来分析这些情况并触发响应，例如通知、警报和警报，以及物理安全操作，例如锁定门、启动或停止 HVAC 系统，以及在战略位置激活照明。一些最常见的算法和行为检测场景包括：

![](OEBPS/images/box.jpg)    *Motion Detection*：物体、动物或人穿过特定视野。

![](OEBPS/images/box.jpg)    *Video Tripwire*：基于检测到定义边界被突破而触发的警报。这可以简单到运动检测，或识别摄像机视野中仅一部分区域内实体的移动或存在。此外，视频绊线可用于触发徘徊警报，其中可疑人员可能在安全门附近徘徊等待进入设施，同时设施内部有人正在离开。

![](OEBPS/images/box.jpg)    *Erratic/Suspicious Behavior*：在某个区域停留异常长的时间，或在停车场车辆周围出现重复的移动模式。

![](OEBPS/images/box.jpg)    *Congestion Detection*：特定空间内人数过多。

![](OEBPS/images/box.jpg)    *Abandoned Object Detection*：例如机场无人看管的包裹或行李。

![](OEBPS/images/box.jpg)    *Opposing Flow*：物体或人与正常流动方向相反移动，例如汽车逆向行驶在单行道上。

![](OEBPS/images/box.jpg)    *Shape-Based Detection*：汽车检测、人或动物检测、视野中异常大小的物体检测。

![](OEBPS/images/box.jpg)    *Missing Object Detection*：检测从场景中移除的物体。

![](OEBPS/images/box.jpg)    *Character Recognition*：检测特定字符、文本或模式。

![](OEBPS/images/box.jpg)    *License Plate Recognition*：识别车辆或车牌注册状态。

![](OEBPS/images/box.jpg)    *Facial Recognition*：通过引用作为独特标识符的固有人类特征的面部识别程序来识别特定个人。

当我们从 IP 角度处理视频监控和分析时，我们立即开始将网络基础设施中的功能和实用程序纳入其中，以增强视频监控所能实现的物理安全增强。例如：

![](OEBPS/images/box.jpg)    *Enable the use of wired and wireless video surveillance cameras*：随时随地覆盖。允许克服在布线方面困难或成本高昂的情况下放置监控摄像机所面临的挑战。

![](OEBPS/images/box.jpg)    *Taking advantage of an existing infrastructure*：基于 IP 的物理安全利用通常已经存在的网络，并提供可以调整和/或轻松扩展的物理基础设施，以提供更多视频摄像机覆盖选项。

![](OEBPS/images/box.jpg)    *Leverage network security features*：使用现有网络安全平台原生的身份验证、授权和访问控制功能。实时监控流氓设备植入并实施基于策略的对策。

![](OEBPS/images/box.jpg)    *Digitally record video*：提供对录制事件的即时访问，并实现实时事件响应、调查和解决。

![](OEBPS/images/box.jpg)    *Ability to distribute management and recording of video*：消除“孤岛”效应，防止系统成为单点故障。

![](OEBPS/images/box.jpg)    *Monitoring and controls can be transferred to any point in the network*：不再需要与视频监控基础设施物理共置即可操作和管理视频系统。提供对视频流、摄像机控制、系统管理和录制视频的真正远程访问。

![](OEBPS/images/box.jpg)    *Integration with other physical (environmental) security tools and systems*：正如我们在分层防御模型中所探讨的，感知与执行以及物理访问控制，安全技术及其相应数据的融合可以为安全团队提供更宏观、更详细的运营图景。

在部署基于 IP 的视频监控和分析解决方案时，我们现在转向 IP 网络以提供通信基础设施。考虑到这一点，Cisco Systems 已为 IP 视频监控制定了一些关键最佳实践和网络设计注意事项，该公司正开始从网络角度切入市场，挑战传统的物理安全品牌。本章的大部分内容以及紧随其后的章节，将基于 Cisco Systems 制定的设计指南。

## IP 网络与视频监控流量

专注于 IP 网络时，有几个因素需要考虑。本节将讨论本章中一些最重要的元素。

### 视频监控流量的特性

监控流量以恒定比特率和可变比特率视频的形式对网络基础设施提出要求，这两者对带宽利用率有不同的影响。恒定比特率视频为每个视频流定义带宽，这对于容量规划和存储很有用，但也可能偶尔浪费带宽。可变比特率视频会随着视频流中差异的捕获而变化。通常这会导致整体带宽消耗降低，但流量可能会突发，这使得容量规划变得困难。为了更好地理解这一点，让我们查看 [Table 33.1](#9781466508507_epub_c33_r1.htm#table_33.1)，该表描绘了基于视频分辨率的恒定比特率指标。

**Table 33.1 Constant Bit-Rate Bandwidth Consumption Guidelines**

![](OEBPS/images/table_33.1.jpg)

为了更好地理解视频分辨率，[Table 33.2](#9781466508507_epub_c33_r1.htm#table_33.2) 概述了各自的分辨率数据，表示为宽度和高度的像素测量值。

**Table 33.2 Video Resolution Represented in Pixels**

| Resolution | PAL | NTSC |
| --- | --- | --- |
| QCIF | 176 × 144 | 176 × 120 |
| VGA | 640 × 480 | 640 × 480 |
| SVGA | 800 × 600 | 800 × 600 |
| XGA | 1024 × 768 | 1024 × 768 |
| CIF | 352 × 288 | 352 × 240 |
| 2 CIF | 704 × 288 | 704 × 240 |
