

# 目录

## 第13章
- [使用 SmoothWall 执行测试](#21_chapter13.xhtml#sec276)
- [防火墙故障排除](#21_chapter13.xhtml#sec277)
- [SmoothWall 附加功能](#21_chapter13.xhtml#sec278)
- [防火墙实施最佳实践](#21_chapter13.xhtml#sec279)
- [**章节总结**](#21_chapter13.xhtml#sec280)
- [**关键概念和术语**](#21_chapter13.xhtml#sec281)
- [**第13章评估**](#21_chapter13.xhtml#sec282)

## 第14章 真实世界的 VPN
- [基于操作系统的 VPN](#22_chapter14.xhtml#sec283)
- [VPN 设备](#22_chapter14.xhtml#sec284)
  - [配置典型 VPN 设备](#22_chapter14.xhtml#sec285)
  - [客户端配置](#22_chapter14.xhtml#sec286)
- [远程桌面协议](#22_chapter14.xhtml#sec287)
- [使用远程控制工具](#22_chapter14.xhtml#sec288)
- [使用远程访问](#22_chapter14.xhtml#sec289)
  - [远程使用的技术](#22_chapter14.xhtml#sec290)
  - [在 IPSec 和 SSL 远程访问 VPN 之间进行选择](#22_chapter14.xhtml#sec291)
- [终端服务](#22_chapter14.xhtml#sec292)
  - [TS RemoteApp](#22_chapter14.xhtml#sec293)
  - [TS Web Access](#22_chapter14.xhtml#sec294)
- [Microsoft DirectAccess](#22_chapter14.xhtml#sec295)
- [DMZ、外联网和内联网 VPN 解决方案](#22_chapter14.xhtml#sec296)
  - [内联网 VPN](#22_chapter14.xhtml#sec297)
  - [外联网 VPN](#22_chapter14.xhtml#sec298)
- [网吧 VPN](#22_chapter14.xhtml#sec299)
- [在线远程 VPN 选项](#22_chapter14.xhtml#sec300)
  - [安全性](#22_chapter14.xhtml#sec301)
  - [Wake-on-LAN 支持](#22_chapter14.xhtml#sec302)
  - [文件共享](#22_chapter14.xhtml#sec303)
  - [远程打印](#22_chapter14.xhtml#sec304)
  - [Mac 支持](#22_chapter14.xhtml#sec305)
- [Tor 应用程序](#22_chapter14.xhtml#sec306)
- [规划 VPN 实施](#22_chapter14.xhtml#sec307)
  - [需求](#22_chapter14.xhtml#sec308)
  - [安装](#22_chapter14.xhtml#sec309)
  - [部署](#22_chapter14.xhtml#sec310)
  - [测试和故障排除](#22_chapter14.xhtml#sec311)
- [VPN 实施最佳实践](#22_chapter14.xhtml#sec312)
- [**章节总结**](#22_chapter14.xhtml#sec313)
- [**关键概念和术语**](#22_chapter14.xhtml#sec314)
- [**第14章评估**](#22_chapter14.xhtml#sec315)

## 第15章 视角、资源与未来
- [网络安全、防火墙和 VPN 的未来展望](#23_chapter15.xhtml#sec316)
  - [威胁](#23_chapter15.xhtml#sec317)
  - [防火墙能力](#23_chapter15.xhtml#sec318)
  - [加密](#23_chapter15.xhtml#sec319)
  - [认证](#23_chapter15.xhtml#sec320)
  - [度量指标](#23_chapter15.xhtml#sec321)
  - [焦点](#23_chapter15.xhtml#sec322)
  - [保护云安全](#23_chapter15.xhtml#sec323)
  - [保护移动设备安全](#23_chapter15.xhtml#sec324)
  - [移动 IP](#23_chapter15.xhtml#sec325)
  - [自带设备](#23_chapter15.xhtml#sec326)
- [网络安全、防火墙和 VPN 资源站点](#23_chapter15.xhtml#sec327)
- [网络安全、防火墙和 VPN 工具](#23_chapter15.xhtml#sec328)
  - [商用现成软件](#23_chapter15.xhtml#sec329)
  - [开源应用程序和工具](#23_chapter15.xhtml#sec330)
- [无处不在的无线连接的影响](#23_chapter15.xhtml#sec331)
- [安全技术的潜在用途](#23_chapter15.xhtml#sec332)
  - [当不存在边界时会发生什么？](#23_chapter15.xhtml#sec333)
- [可用的专用防火墙](#23_chapter15.xhtml#sec334)
  - [入侵检测系统 (IDS) 和入侵防御系统 (IPS)](#23_chapter15.xhtml#sec335)
- [蜜罐、蜜网和填充单元的效果](#23_chapter15.xhtml#sec336)
- [新兴网络安全技术](#23_chapter15.xhtml#sec337)
  - [IP 版本 6](#23_chapter15.xhtml#sec338)
  - [VPN、防火墙和虚拟化](#23_chapter15.xhtml#sec339)
  - [隐写术](#23_chapter15.xhtml#sec340)
  - [反取证](#23_chapter15.xhtml#sec341)
- [**章节总结**](#23_chapter15.xhtml#sec342)
- [**关键概念和术语**](#23_chapter15.xhtml#sec343)
- [**第15章评估**](#23_chapter15.xhtml#sec344)

## 附录
- [附录 A：答案](#24_app.xhtml#app-a)
- [附录 B：标准首字母缩略词](#24_app.xhtml#app-b)
- [关键术语词汇表](#25_glossary.xhtml)
- [参考文献](#26_ref.xhtml)
- [索引](#27_index.xhtml)

---

# 前言

## 本书目的

本书是 Jones & Bartlett Learning 出版的信息系统安全与保障系列丛书（*[www.jblearning.com](http://www.jblearning.com)*）的一部分。该系列专为 IT 安全、网络安全、信息保障和信息系统安全课程及课程体系设计，全面、系统地阐述了这一关键学科领域最前沿的思维和趋势。这些书籍将基本的信息安全原则与现实世界的应用和示例相结合。由认证信息系统安全专家 (CISSP) 编写，涵盖了信息安全各个方面的综合信息。经该领域领先技术专家逐字逐句审核，这些书籍不仅紧跟当前，更具前瞻性——使您能够解决不仅是当今，而且是未来的网络安全挑战。

本书第一部分关于网络安全的内容，侧重于当您将组织网络物理连接到公共互联网时所面临的业务挑战和威胁。它将向您介绍关键概念和术语，并揭示黑客在试图访问您的网络时的所作所为，从而为后续讨论提供必要的网络安全基础。它将定义防火墙和虚拟专用网络 (VPN)，使您了解如何将它们作为安全对策来解决业务挑战。

[第2部分](#11_part2.xhtml) 讨论如何实施网络安全并回顾最佳实践。它讨论如何选择和部署防火墙以及用于管理和监控它们的工具。它还回顾了 VPN 的实施、所涉及的技术以及 VPN 管理最佳实践。

[第3部分](#20_part3.xhtml) 侧重于实践，给出了实施防火墙和 VPN 的具体分步示例。它还讨论了从事网络安全的信息安全专业人员未来面临的挑战。它涵盖了专业人员可用的工具和资源，并展望了新兴技术的前景。

## 学习特色

本书的写作风格实用且通俗易懂。全书贯穿了信息安全概念和程序的分步示例。每章开头都有学习目标陈述。插图既用于阐明材料，也用于丰富呈现方式。正文穿插了注释、提示、相关信息、警告和侧边栏，以提醒读者注意与讨论主题相关的额外有用信息。章节评估位于每章末尾，答案在书后提供。

正文包含章节总结，旨在提供材料的快速复习或预览，并帮助学生理解所呈现概念的相对重要性。

## 受众

本教材适合本科或研究生计算机科学专业或信息科学专业的学生、具备基本技术背景的两年制技术学院或社区学院学生，或具备基本 IT 安全知识并希望扩展知识的读者。

