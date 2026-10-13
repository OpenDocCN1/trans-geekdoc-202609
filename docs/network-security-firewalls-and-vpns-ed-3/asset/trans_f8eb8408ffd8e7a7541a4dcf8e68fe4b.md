
本书的写作风格实用且通俗易懂。全书贯穿了信息安全概念和程序的分步示例。每章开头都列出了学习目标。插图既用于阐明内容，也用于丰富呈现形式。正文中穿插着注释、提示、参考信息、警告和边栏，旨在提醒读者关注与讨论主题相关的额外有用信息。

章节测验位于每章末尾，答案提供在书后。章节总结包含在正文中，旨在提供快速复习或预习材料，并帮助学生理解所呈现概念的相对重要性。

## 读者对象

本书适合计算机科学、信息科学、网络安全专业的本科生或研究生，具备基础技术背景的两年制技术学院或社区学院学生，以及具备基本 IT 原理理解并希望扩展知识的读者。

## 本版新增内容

本版提供了改进的格式，每个主要主题（网络安全、防火墙、VPN）都从入门讲解到高级主题，然后再过渡到下一个主题，并加强了主题间的整合。本版还反映了最新的软件版本和技术。最后几章介绍了网络安全的最佳实践，并探讨了技术的未来、法规考量以及人员和流程管理。

## 云实验室

本书配套网络安全云实验室。这些实操虚拟实验室提供了沉浸式的模拟 IT 基础设施，学生可在其中学习和实践基础网络安全技能，作为本书课程的延伸。如需更多信息或购买实验室，请访问 [go.jblearning.com/stewart3e](http://go.jblearning.com/chapple3e)。

![© Digital_Art/Shutterstock](Images/Chapter-Opener.jpg)

© Digital_Art/Shutterstock

## 致谢

Denise Kinsey 博士要感谢 Rob 和 M.C. 始终如一的支持与鼓励；感谢开发团队和 JBL 的所有人员，特别感谢 Ned、Melissa 和 Kim。我感激你们为构建此版本提出的所有意见和想法。

Jones & Bartlett Learning 感谢所有审阅本书第二版的人员。你们的反馈帮助塑造了此次修订。

Georgia Brown

*美国军事大学*

*ECPI*

*EC Council University*

*西部州长大学*

*泰德沃特社区学院*

Shana Bumpas

*约翰·泰勒社区学院*

Colin T. Carlile

*圣母湖大学*

Casimer DeCusatis

*马里斯特学院*

Charles DeSassure

*塔兰特县学院*

M. Lamine Diop

*蓝岭社区学院*

Perry Hood

*威尔格拉斯佐治亚技术学院*

Richard McKinney

*纳什维尔州立社区学院*

Teresa Nash

*刘易斯-克拉克州立学院*

Nicholas Peirce

*托马斯·纳尔逊社区学院*

Richard S. Riddle Jr.

*丹维尔社区学院*

Jianhua Yang

*哥伦布州立大学*

Tatyana Zidarov

*黑格斯敦社区学院*

![© Digital_Art/Shutterstock](Images/Chapter-Opener.jpg)

© Digital_Art/Shutterstock

## 作者简介

**James Michael Stewart** 从事计算机和技术工作已超过 25 年。他的工作重点在于安全、认证和各种操作系统。最近，Michael 一直在教授职业技能和认证课程，如 `CISSP`、`CEH` 和 `Security+`。他是《CISSP 学习指南 第 4 版》和《Security+ 2008 复习指南》的主要作者。此外，Michael 还撰写了大量关于其他安全、Microsoft 认证和管理主题的文本。他开发了认证课程教材和培训材料，并在课堂上讲授这些材料。Michael 持有以下认证：`CISSP`、`ISSAP`、`SSCP`、`MCT`、`CEI`、`CEH`、`TICSA`、`CIW SA`、`Security+`、`MCSE+Security: Windows 2000`、`MCSA Windows Server 2003`、`MCDST`、`MCSE NT & W2K`、`MCP+I`、`Network+`、`iNet+`。他于 1992 年毕业于德克萨斯大学奥斯汀分校，获得哲学学士学位。

**Denise Kinsey, Ph.D** 在计算机网络和网络安全领域拥有超过 20 年的工作经验。她为政府和私营部门设计、实施和管理过 IT 和 OT 项目。Denise 是多部 IT 和网络安全教材的作者，旨在教育读者、赋能读者，使其了解更多技术知识，并为其雇主和家庭实施安全系统。在不解决网络安全问题时，她喜欢与学生合作，改善非营利组织和本地企业的网络和网络安全。Denise 持有多项认证，包括 `CISSP`、`C|CISO`、`Security+` 等。Kinsey 博士是副教授。

![© Digital_Art/Shutterstock](Images/Part-Opener.jpg)

© Digital_Art/Shutterstock

# 第 1 部分

# 网络安全基础

[第 1 章 网络安全基础](#10_chapter01.xhtml)

[第 2 章 网络安全威胁](#11_chapter02.xhtml)

[第 3 章 常见网络拓扑和基础设施](#12_chapter03.xhtml)

[第 4 章 网络设计考量](#13_chapter04.xhtml)

![© Digital_Art/Shutterstock](Images/Chapter-Opener.jpg)

© Digital_Art/Shutterstock

## 网络安全基础

## 第 1 章

计算机网络安全非常复杂。来自网络内外的新威胁层出不穷。作为回应，安全社区不断开发新产品和程序，以抵御过去的威胁和未来的未知威胁。

随着公司合并、人员失业、新设备上线以及[业务任务](#30_glossary.xhtml#gloss68)变更，人们的行为并不总是符合预期。昨天行之有效的网络安全配置，明天可能就不那么奏效了。在瞬息万变的商业环境中，你该信任谁？你的信任被背叛了吗？你怎么知道？这次是谁在试图破坏你的网络？为什么？

鉴于这些复杂问题，你需要了解网络安全的基本要素。本章将向你介绍网络安全的基本要素。一旦你牢固掌握这些基础知识，就能为组织网络实施有效的安全措施做好充分准备。

### 第 1 章主题

本章涵盖以下主题和概念：

*   网络安全的含义
*   典型 IT 基础设施七大领域中受保护的项目
*   网络安全的目标
*   如何评估网络安全实施的成效
*   书面网络安全策略为何重要
*   谁负责网络安全
*   增强有线和无线局域网（`LAN`）基础设施安全的控制措施
*   内部和外部网络问题的示例
*   用于缓解整个 IT 基础设施威胁的常见网络安全组件
*   传输控制协议/互联网协议（`TCP/IP`）的基础知识

### 第 1 章目标

完成本章后，你将能够：

*   描述与网络安全相关的关键概念和术语
*   描述书面安全策略的重要性；解释策略如何帮助将网络基础设施的风险敞口和威胁降至最低
*   定义网络安全角色和职责；确定 IT 组织中谁对这些安全实施负责
*   识别网络安全关注点或威胁的示例，这些威胁需要加强安全对策以妥善将风险敞口和威胁降至最低
