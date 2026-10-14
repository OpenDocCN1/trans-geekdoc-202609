
* **.vbox:** 这是机器设置文件的扩展名。在 4.0 版本之前，它是 `.xml`。

* 虚拟 PC：

    * **.vhx:** 这些是实际的虚拟硬盘。它们对取证调查来说显而易见非常重要。

    * **.bin 文件：** 这些文件包含虚拟机的内存，因此必须对这些文件进行检查。

    * **.xml 文件：** 这些文件包含虚拟机的配置详情。每个虚拟机及其快照都有一个这样的文件。这些文件总是以用于内部标识虚拟机的 GUID 命名。

##### Cloud

云被定义为“虚拟化计算机资源的池”。

人们常常把云当作只有一个云，或者至少是一种云的类型。这种印象是不准确的。有多个云以及多种云的类型。任何拥有适当资源的组织都可以建立云，并且可能出于多种原因建立云，从而导致不同类型的云。

公有云是 NIST 定义的，指那些向公众或至少向大型行业集团提供基础设施或服务的云。

私有云是专门供单个组织使用且不向外部提供服务的云。当然，混合云结合了私有云和公有云的元素。这些本质上是带有一定公共访问权限的私有云。

社区云是介于私有云和公有云之间的中间点。这些是为特定社区需求而多个组织共享云的系统。例如，几家计算机公司可能会合作创建一个专注于共同安全问题的云。

云系统依赖于多个部分。这些部分中的每一个都可能是证据的存放地：

* **虚拟存储：** 虚拟服务器托管在一个或多个实际/物理服务器上。这些物理服务器的硬盘空间和内存被划分用于不同虚拟服务器的使用。

* **审计监视器：** 通常会有一个审计监视器来监控资源池的使用情况。该监视器还会确保一个虚拟服务器无法/不能访问另一个虚拟服务器的数据。

* **超级用户（Hypervisor）：** 超级用户机制是提供虚拟服务器访问资源的过程。

* **逻辑网络边界：** 由于云由虚拟服务器而非物理服务器组成，因此需要逻辑网络和逻辑网络边界。该边界用于将资源池相互隔离。

单个云实现可能包含额外的实用程序，例如管理控制台，允许网络管理员监控、配置和管理云。

云取证有两个问题。第一个是管辖权。云数据通常会在不同国家的服务器上复制，每个国家都有自己的法律。然后是技术问题——获取数据。很可能无法对整个云进行镜像。因此，你可能需要对相关数据进行逻辑复制，甚至进行实时分析。

### Summary

在这一章中，你了解了计算机取证的基础知识。你学到的最重要的事情是制作取证副本以供操作，并记录所有过程。你无法过度记录。你还学会了如何检索浏览器信息和恢复已删除文件，并学习了一些可能对取证有用的命令。你还探索了 Windows 注册表的取证价值，甚至包括云取证。

### Test Your Skills

#### Multiple Choice Questions

**[1](#app02.xhtml#ch14ans1).** 在计算机取证调查中，描述证据在你发现它直到案件结案或进入法院期间所走的路径的是什么？

**A.** 证据规则

**B.** 概率法则

**C.** 证据链

**D.** 分离政策

**[2](#app02.xhtml#ch14ans2).** Ian 正在对 Linux 服务器进行取证调查，他试图恢复电子邮件。Linux 存储电子邮件服务器日志的位置是什么？

**A.** `/var/log/mail.*`

**B.** `/etc/log/mail.*`

**C.** `/mail/log/mail.*`

**D.** `/server/log/mail.*`

**[3](#app02.xhtml#ch14ans3).** 为什么在你想要作为证据扣押的电脑上记录所有的电缆连接？

**A.** 了解外部连接的情况

**B.** 以防其他设备被连接

**C.** 了解外设设备的情况

**D.** 了解硬件的情况

**[4](#app02.xhtml#ch14ans4).** Pedro 正在检查一台 Windows 7 电脑，他提取了 index.dat 文件并正在检查该文件。Index.dat 文件中包含什么？

**A.** Internet Explorer 信息

**B.** Windows 机器的通用 Internet 历史、文件浏览历史等

**C.** Firefox 的所有网页历史

**D.** Linux 机器的通用 Internet 历史、文件浏览历史等

**[5](#app02.xhtml#ch14ans5).** 哪个标准 Linux 命令也作为 Windows 应用程序可用，可用于创建位流图像并进行取证副本？

**A.** `mcopy`

**B.** `image`

**C.** `MD5`

**D.** `dd`

**[6](#app02.xhtml#ch14ans6).** 在 cataloging（目录化）数字证据时，主要目标是什么？

**A.** 对所有硬盘制作位流图像。

**B.** 保持证据的完整性。

**C.** 避免从现场移除证据。

**D.** 禁止计算机关机。

**[7](#app02.xhtml#ch14ans7).** Mahmoud 使用一系列 Windows 实用程序从正在排查的电脑中提取信息。他刚刚使用了 `Openfiles` 命令。`Openfiles` 命令显示什么？

**A.** 任何已打开的文件

**B.** 任何已打开的共享文件

**C.** 任何系统文件已打开

**D.** 任何带有 ADS（隔离存储）的已打开文件

**[8](#app02.xhtml#ch14ans8).** “Interesting data”（有趣的数据）是什么？

**A.** 与你调查相关的数据

**B.** 色情内容

**C.** 文档、电子表格和数据库

**D.** 图纸或其他基于经济的信息

**[9](#app02.xhtml#ch14ans9).** 在对数字证据进行目录化时，以下哪项对调查员来说很重要？

**A.** 记录方法

**B.** 日志保留期限

**C.** 存储日志的位置

**D.** 以上全部

#### Exercises

**Exercise 14.1:** DiskDigger

下载 DiskDigger 并搜索你的电脑以查找已删除文件。尝试恢复你选择的一个文件。

**Exercise 14.2:** Making a Forensic Copy

此练习需要两台电脑。你必须下载要么 Kali Linux 要么 Knoppix（两者均为免费）。然后尝试通过将计算机 A 的数据发送到计算机 B 来对计算机 A 进行取证副本的制作。

**Exercise 14.3:** OSForensics

下载 OSForensics 的试用版（https://www.osforensics.com/osforensics.html）。

使用 https://www.osforensics.com/faqs-and-tutorials/video_demonstrations.html 上的教程，在你自己的电脑上使用 OSForensics 进行基本取证。

## Chapter 15. Cybersecurity Engineering

Chapter Objectives

After reading this chapter and completing the exercises, you will be able to do the following:

*   Understand basic systems engineering concepts

*   Understand how to integrate systems engineering into cybersecurity

### Introduction

