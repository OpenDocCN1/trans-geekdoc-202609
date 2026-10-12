

![image](images/cover.jpg)

![](images/halft.jpg)

![](images/titlef.jpg)

*云计算中的数据安全，第二卷*

版权所有 © Momentum Press^®, LLC, 2019。

保留所有权利。未经出版商事先许可，本出版物的任何部分不得以任何形式或任何方式（电子、机械、复印、录音或其他）复制、存储于检索系统或传播，简短引用（不超过 250 词）除外。

2019 年首版由以下机构出版

Momentum Press^®, LLC

222 East 46th Street, New York, NY 10017

[www.momentumpress.net](http://www.momentumpress.net)

ISBN-13: 978-1-94944-923-5 (印刷版)

ISBN-13: 978-1-94944-924-2 (电子书)

Momentum Press 计算机工程基础、前沿与趋势系列

封面及内文设计：S4Carlisle Publishing Services Private Ltd., Chennai, India

第一版：2019

10  9  8  7  6  5  4  3  2  1

在美国印刷

***献词***

*献给我的妻子 Eimear，感谢她在我的职业生涯和写作本书过程中始终陪伴在我身边。*

## 摘要

云计算因其经济性、可靠性、可扩展性和服务质量保障等优势，已被许多组织和个人采用。读者将了解软件即服务（`SaaS`）、平台即服务（`PaaS`）、基础设施即服务（`IaaS`）、服务器和桌面虚拟化等具体内容。

本书不仅涵盖云计算安全与风险管理中的信息保护，还涵盖将现有应用迁移到云端所需的规划、管理和深度实施细节。读者将更深入地理解云工程，以及在降低 IT 实施风险的同时快速获益所需采取的行动。本书内容非常适合希望迁移上云的用户、寻求云基础知识概览的 IT 专业人士，以及将构建云解决方案用于测试目的的计算机科学学生。

## 关键词

Amazon Web Services；`API`；`Azure`；`BaaS`；云计算；计算机工程与科学；`Google Cloud`；`Java`；`MySQL`；`Node.js`；`SaaS`；`SQL`

## 目录

[图表目录](#07_figures.xhtml#h-1)

[表格目录](#08_tables.xhtml#h-2)

[缩略语表](#09_abbreviations.xhtml#h-3)

[致谢](#10_ack.xhtml#h-4)

[引言](#11_introduction.xhtml#h-5)

[第 7 章 安全云架构](#12_chapter07.xhtml#h-6)

[7.1. 治理与综合风险分析](#12_chapter07.xhtml#h-7)

[第 8 章 风险与信任评估](#13_chapter08.xhtml#h-8)

[第 9 章 云中风险管理](#14_chapter09.xhtml#h-9)

[第 10 章 云安全访问控制](#15_chapter10.xhtml#h-10)

[10.1. 改进](#15_chapter10.xhtml#h-11)

[10.2. 多级认证](#15_chapter10.xhtml#h-12)

[10.3. 加密](#15_chapter10.xhtml#h-13)

[10.4. 密码管理](#15_chapter10.xhtml#h-14)

[10.5. 分布式服务器](#15_chapter10.xhtml#h-15)

[第 11 章 云安全风险管理](#16_chapter11.xhtml#h-16)

[11.1. 云中的风险](#16_chapter11.xhtml#h-17)

[11.2. 间接测量与指标](#16_chapter11.xhtml#h-18)

[11.3. 风险定义](#16_chapter11.xhtml#h-19)

[11.4. 风险与云](#16_chapter11.xhtml#h-20)

[11.4.1. 非云计算特有的安全风险](#16_chapter11.xhtml#h-21)

[11.4.2. 云特有的危害](#16_chapter11.xhtml#h-22)

[11.4.3. 云服务安全 SLA](#16_chapter11.xhtml#h-23)

[第 12 章 基础设施即服务 (IAAS)](#17_chapter12.xhtml#h-24)

[12.1. 考量因素](#17_chapter12.xhtml#h-25)

[12.2. 网络](#17_chapter12.xhtml#h-26)

[12.3. 安全隐患](#17_chapter12.xhtml#h-27)

[12.4. 存储](#17_chapter12.xhtml#h-28)

[12.5. 数据库](#17_chapter12.xhtml#h-29)

[12.6. 控制](#17_chapter12.xhtml#h-30)

[第 13 章 用于数据保护的加密密钥管理](#18_chapter13.xhtml#h-31)

[13.1. 密钥管理系统设计选择](#18_chapter13.xhtml#h-32)

[13.2. 云密钥管理挑战](#18_chapter13.xhtml#h-33)

[13.3. 云密钥管理策略](#18_chapter13.xhtml#h-34)

[13.3.1. 建立对加密模块的信任](#18_chapter13.xhtml#h-35)

[13.3.2. 使用密钥分割技术](#18_chapter13.xhtml#h-36)

[第 14 章 管理法律合规风险与个人数据保护](#19_chapter14.xhtml#h-37)

[14.1. 2015 年欧洲数字议程](#19_chapter14.xhtml#h-38)

[14.2. 应对法律合规](#19_chapter14.xhtml#h-39)

[14.2.1. 合同前阶段](#19_chapter14.xhtml#h-40)

[14.2.2. 步骤 1：合同前阶段](#19_chapter14.xhtml#h-41)

[14.2.3. 云服务客户的风险与机遇](#19_chapter14.xhtml#h-42)

[14.2.4. 云服务外包](#19_chapter14.xhtml#h-43)

[14.2.5. 步骤 2：签订云服务合同的主要问题](#19_chapter14.xhtml#h-44)

[14.2.6. 司法管辖权与适用法律](#19_chapter14.xhtml#h-45)

[14.2.7. 隐私角色](#19_chapter14.xhtml#h-46)

[14.2.8. 合同修正](#19_chapter14.xhtml#h-47)

[14.2.9. 数据位置与数据传输](#19_chapter14.xhtml#h-48)

[14.2.10. 分包商对个人数据的处理](#19_chapter14.xhtml#h-49)

[14.2.11. 数据主体权利（可介入性）](#19_chapter14.xhtml#h-50)

[14.2.12. 步骤 3：退出云服务合同的主要问题](#19_chapter14.xhtml#h-51)

[14.2.13. 锁定与互操作性](#19_chapter14.xhtml#h-52)

[14.2.14. 服务级别协议](#19_chapter14.xhtml#h-53)

[14.2.15. 合同终止](#19_chapter14.xhtml#h-54)

[第 15 章 云计算安全的未来方向](#20_chapter15.xhtml#h-55)

[15.1. 类别](#20_chapter15.xhtml#h-56)

[作者简介](#21_author.xhtml#h-57)

[索引](#22_index.xhtml#h-58)

## 图表目录

[图 7.1. 云计算结构](#12_chapter07.xhtml#fig7-1)

[图 7.2. 你的云究竟有多安全？](#12_chapter07.xhtml#fig7-2)

[图 7.3. 四大安全要素](#12_chapter07.xhtml#fig7-3)

[图 7.4. 安全代理执行的角色](#12_chapter07.xhtml#fig7-4)

[图 7.5. 云用户与服务提供商](#12_chapter07.xhtml#fig7-5)

[图 7.6. 合规架构示例](#12_chapter07.xhtml#fig7-6)

[图 7.7. 云计算供应商内部局域网安全基础设施示意图](#12_chapter07.xhtml#fig7-7)

[图 8.1. 风险控制策略](#13_chapter08.xhtml#fig8-1)

[图 8.2. 云危害评估模型](#13_chapter08.xhtml#fig8-2)

[图 8.3. 使用 0 到 8 刻度的风险矩阵](#13_chapter08.xhtml#fig8-3)

[图 8.4. 威胁要素间的关系](#13_chapter08.xhtml#fig8-4)

[图 8.5. 描述每个重点事件风险程度的矩阵](#13_chapter08.xhtml#fig8-5)

[图 9.1. 表 9.1 和 NIST SP 800-37 Rev. 1 中记录的 RMF 程序](#14_chapter09.xhtml#fig9-1)

[图 9.2. 表 9.1 和 NIST SP 800-37 Rev. 1 中记录的 RMF 程序](#14_chapter09.xhtml#fig9-2)

[图 10.1. 安全层级](#15_chapter10.xhtml#fig10-1)

[图 10.2. 三层数据库结构](#15_chapter10.xhtml#fig10-2)

[图 10.3. 展示 Windows 和 Linux 等最流行的服务器操作系统](#15_chapter10.xhtml#fig10-3)

[图 10.4. 云计算复杂性与接入点](#15_chapter10.xhtml#fig10-4)

[图 13.1. 加密密钥拥有包含部分或全部以下状态的生命周期](#18_chapter13.xhtml#fig13-1)

[图 13.2. 云平台的概念决策流程图](#18_chapter13.xhtml#fig13-2)

## 表格目录

[表 7.1. 风险评估矩阵](#12_chapter07.xhtml#tab7-1)

[表 9.1. NIST SP 800-37 Rev. 1](#14_chapter09.xhtml#tab9-1)

