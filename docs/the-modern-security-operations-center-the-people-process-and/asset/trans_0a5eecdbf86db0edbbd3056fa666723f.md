

![](Images/9780135619742.jpg)

## 关于本书

ePUB 是一种开放的、行业标准的电子书格式。然而，不同阅读设备和应用程序对 ePUB 及其众多功能的支持程度各不相同。请使用您的设备或应用程序设置来自定义呈现效果，以符合您的喜好。通常可自定义的设置包括字体、字号、单栏或双栏、横向或纵向模式，以及可点击或轻触放大的图表。有关您的阅读设备或应用程序的设置和功能的更多信息，请访问设备制造商的网站。

许多书籍包含编程代码或配置示例。为优化这些元素的呈现效果，请在单栏、横向模式下查看电子书，并将字号调整至最小设置。除了以可重排文本格式呈现代码和配置外，我们还包含了模仿印刷书籍呈现效果的代码图片；因此，当可重排格式可能影响代码清单的呈现时，您将看到一个“点击此处查看代码图片”链接。点击该链接即可查看高保真的印刷版代码图片。要返回之前查看的页面，请点击设备或应用程序上的“返回”按钮。

# 现代安全运营中心

# 现代安全运营中心

运营 SOC 服务的人员、流程与技术

Joseph Muniz

![](Images/pub.jpg)

Boston • Columbus • New York • San Francisco • Amsterdam • Cape Town  
Dubai • London • Madrid • Milan • Munich • Paris • Montreal • Toronto • Delhi • Mexico City  
São Paulo • Sidney • Hong Kong • Seoul • Singapore • Taipei • Tokyo

制造商和销售商用于区分其产品的许多名称均声称拥有商标权。凡本书中出现的此类名称，且出版商知晓其商标权声明的，均已以首字母大写或全大写形式印刷。

作者和出版商在编写本书时已尽职尽责，但不对任何种类的明示或暗示担保承担责任，也不对错误或遗漏承担任何责任。对于因使用本书中包含的信息或程序而引起的或与之相关的附带损害或后果性损害，不承担任何责任。

如需批量购买本书，或了解特殊销售机会（可能包括电子版、定制封面设计，以及针对您的业务、培训目标、营销重点或品牌利益的特定内容），请联系我们的企业销售部门：`corpsales@pearsoned.com` 或 (800) 382-3419。

政府采购咨询，请联系 `governmentsales@pearsoned.com`。

美国境外销售咨询，请联系 `intlcs@pearson.com`。

访问我们的网站：`informit.com/aw`

美国国会图书馆控制编号：2021930517

版权所有 © 2021 Pearson Education, Inc.

保留所有权利。本出版物受版权保护，未经出版商事先许可，不得以任何形式或任何方式（电子、机械、复印、录制或同样方式）进行任何被禁止的复制、存储于检索系统或传播。有关权限申请、申请表格及 Pearson Education 全球版权与许可部门的相关联系方式，请访问 `www.pearson.com/permissions/`。

ISBN-13: 978-0-13-561985-8  
ISBN-10: 0-13-561985-8

**ScoutAutomatedPrintCode**

**主编**  
Mark Taub

**采购编辑**  
James Manly

**责任编辑**  
Christopher A. Cleveland

**管理编辑**  
Sandra Schroeder

**高级项目编辑**  
Tonya Simpson

**文字编辑**  
Bill McManus

**索引编制**  
Ken Johnson

**校对**  
Betty Pessagno

**技术审校**  
Anthony Giandomecino  
Kevin Tigges  
Willow Young

**编辑助理**  
Cindy Teeters

**封面设计**  
Chuti Prasertsith

**排版**  
codeMantra

## 献词

*我想将这本书献给两个人。首先，献给 Atticus Muniz，他还不会走路、不会阅读、甚至不懂得如何使用厕所，但总有一天他会掌握这一切。他现在一岁，正在成长。希望他将来能成就一番伟业，并在此时抽出时间阅读这本书。其次，献给 Raylin Muniz，她今年 11 岁，是我见过的最狂热的书虫之一。希望她也能将这本书加入她的阅读清单。*

## 目录

[**前言**](#pref01.xhtml#pref01)

[**第 1 章：安全运营与 SOC 简介**](#ch01.xhtml#ch01)

[SOC 简介](#ch01.xhtml#ch01lev1sec1)

[导致 SOC 失灵的因素](#ch01.xhtml#ch01lev1sec2)

[网络威胁](#ch01.xhtml#ch01lev1sec3)

[安全投资](#ch01.xhtml#ch01lev1sec4)

[泄露事件的影响](#ch01.xhtml#ch01lev1sec5)

[建立基线](#ch01.xhtml#ch01lev1sec6)

[变更的影响](#ch01.xhtml#ch01lev2sec1)

[基础安全能力](#ch01.xhtml#ch01lev1sec7)

[特征检测](#ch01.xhtml#ch01lev2sec2)

[行为检测](#ch01.xhtml#ch01lev2sec3)

[异常检测](#ch01.xhtml#ch01lev2sec4)

[最佳单品 vs. 深度防御](#ch01.xhtml#ch01lev2sec5)

[标准、指南与框架](#ch01.xhtml#ch01lev1sec8)

[NIST 网络安全框架](#ch01.xhtml#ch01lev2sec6)

[ISO 3100:2018](#ch01.xhtml#ch01lev2sec7)

[FIRST 服务框架](#ch01.xhtml#ch01lev2sec8)

[应用框架](#ch01.xhtml#ch01lev2sec9)

[行业威胁模型](#ch01.xhtml#ch01lev1sec9)

[网络攻击链模型](#ch01.xhtml#ch01lev2sec10)

[钻石模型](#ch01.xhtml#ch01lev2sec11)

[MITRE ATT&CK 模型](#ch01.xhtml#ch01lev2sec12)

[选择威胁模型](#ch01.xhtml#ch01lev2sec13)

[漏洞与风险](#ch01.xhtml#ch01lev1sec10)

[无休止的漏洞](#ch01.xhtml#ch01lev2sec14)

[业务挑战](#ch01.xhtml#ch01lev1sec11)

[自建 vs. 外包](#ch01.xhtml#ch01lev1sec12)

[服务优势](#ch01.xhtml#ch01lev2sec15)

[服务劣势](#ch01.xhtml#ch01lev2sec16)

[混合服务](#ch01.xhtml#ch01lev2sec17)

[SOC 服务](#ch01.xhtml#ch01lev1sec13)

[SOC 成熟度模型](#ch01.xhtml#ch01lev1sec14)

[SOC 成熟度评估](#ch01.xhtml#ch01lev2sec18)

[SOC 项目成熟度](#ch01.xhtml#ch01lev2sec19)

[SOC 目标评估](#ch01.xhtml#ch01lev1sec15)

[定义目标](#ch01.xhtml#ch01lev2sec20)

[SOC 目标排序](#ch01.xhtml#ch01lev2sec21)

[威胁排序](#ch01.xhtml#ch01lev2sec22)

[SOC 目标评估总结](#ch01.xhtml#ch01lev2sec23)

[SOC 能力评估](#ch01.xhtml#ch01lev1sec16)

[能力图谱](#ch01.xhtml#ch01lev2sec24)

[SOC 能力差距分析](#ch01.xhtml#ch01lev2sec25)

[能力图谱后续步骤](#ch01.xhtml#ch01lev2sec26)

[SOC 发展里程碑](#ch01.xhtml#ch01lev1sec17)

[总结](#ch01.xhtml#ch01lev1sec18)

[参考资料](#ch01.xhtml#ch01lev1sec19)

[**第 2 章：建设安全运营中心**](#ch02.xhtml#ch02)

[使命声明与范围声明](#ch02.xhtml#ch02lev1sec1)

[制定使命与范围声明](#ch02.xhtml#ch02lev2sec1)

[SOC 范围声明](#ch02.xhtml#ch02lev2sec2)

[建设 SOC](#ch02.xhtml#ch02lev1sec2)

[SOC 程序](#ch02.xhtml#ch02lev1sec3)

[设计程序](#ch02.xhtml#ch02lev2sec3)

[安全工具](#ch02.xhtml#ch02lev1sec4)

[评估漏洞](#ch02.xhtml#ch02lev2sec4)

[防护技术](#ch01.xhtml#ch02lev2sec5)

[检测技术](#ch02.xhtml#ch02lev2sec6)

[移动设备安全顾虑](#ch02.xhtml#ch02lev2sec7)

[规划 SOC](#ch02.xhtml#ch02lev1sec5)

[产能规划](#ch02.xhtml#ch02lev2sec8)

[制定产能计划](#ch02.xhtml#ch02lev2sec9)

