

![cover-image](graphics/9780134085050.jpg)

## 关于本书

ePUB 是一种开放的、行业标准的电子书格式。然而，不同阅读设备和应用程序对 ePUB 及其诸多功能的支持程度各不相同。请使用您的设备或应用程序设置来自定义呈现效果，以符合您的喜好。通常可自定义的设置包括字体、字号、单栏或双栏、横向或纵向模式，以及可点击或点按放大的图表。有关阅读设备或应用程序的设置和功能的更多信息，请访问设备制造商的网站。

许多书籍包含编程代码或配置示例。为优化这些元素的呈现效果，请在单栏、横向模式下查看电子书，并将字号调整至最小设置。除了以可重排文本格式呈现代码和配置外，我们还包含了模仿印刷书籍呈现效果的代码图片；因此，当可重排格式可能影响代码清单的呈现时，您将看到一个“点击此处查看代码图片”链接。点击该链接即可查看高保真印刷版代码图片。要返回之前查看的页面，请点击设备或应用程序上的“后退”按钮。

# 计算机安全

## 第五版

Charles P. Pfleeger  
Shari Lawrence Pfleeger  
Jonathan Margulies

![Image](graphics/pub.jpg)

Upper Saddle River, NJ • Boston • Indianapolis • San Francisco  
New York • Toronto • Montreal • London • Munich • Paris • Madrid  
Capetown • Sydney • Tokyo • Singapore • Mexico City

制造商和销售商用于区分其产品的许多名称均声称拥有商标权。凡本书中出现的此类名称，且出版商知晓其商标权声明的，均已以首字母大写或全大写形式印刷。

作者和出版商在本书的编写过程中已尽职尽责，但不对任何种类的明示或暗示担保承担责任，也不对错误或遗漏承担任何责任。对于因使用本书所含信息或程序而引起的或与之相关的附带损害或后果性损害，不承担任何责任。

如需批量购买本书，或了解特殊销售机会（可能包括电子版、定制封面设计，以及针对您的业务、培训目标、营销重点或品牌利益的特定内容），请联系我们的企业销售部门：[corpsales@pearsoned.com](mailto:corpsales@pearsoned.com) 或 (800) 382-3419。

政府采购咨询，请联系 [governmentsales@pearsoned.com](mailto:governmentsales@pearsoned.com)。

美国境外销售咨询，请联系 [international@pearsoned.com](mailto:international@pearsoned.com)。

访问我们的网站：[informit.com/ph](http://informit.com/ph)

*美国国会图书馆预编目数据*

Pfleeger, Charles P., 1948–

计算机安全 / Charles P. Pfleeger, Shari Lawrence Pfleeger, Jonathan Margulies.—

第五版。

pages cm

包括参考文献和索引。

ISBN 978-0-13-408504-3 (精装 : 碱性纸) — ISBN 0-13-408504-3 (精装 : 碱性纸)

1. 计算机安全。2. 数据保护。3. 隐私权。 I. Pfleeger, Shari Lawrence。

II. Margulies, Jonathan。 III. 书名。

QA76.9.A25P45 2015

005.8—dc23 2014038579

版权所有 © 2015 Pearson Education, Inc.

保留所有权利。在美国印刷。本出版物受版权保护，未经出版商事先许可，不得以任何形式或任何方式（电子、机械、复印、录制或类似方式）进行任何被禁止的复制、存储于检索系统或传播。如需获得使用本著作材料的许可，请向 Pearson Education, Inc., Permissions Department, One Lake Street, Upper Saddle River, New Jersey 07458 提交书面申请，或传真至 (201) 236-3290。

ISBN-13: 978-0-13-408504-3

ISBN-10: 0-13-408504-3

正文在美国印刷，使用再生纸，由马萨诸塞州韦斯特福德的 Courier 公司印制。

首印，2015 年 1 月

**执行编辑**

Bernard Goodwin

**编辑助理**

Michelle Housley

**责任编辑**

John Fuller

**项目编辑**

Elizabeth Ryan

**文案编辑**

Mary Lou Nohr

**校对员**

Linda Begley

**封面设计师**

Alan Clements

**排版**

Shepherd, Inc.

*献给 Willis Ware，计算机安全与隐私领域的英雄。*

## 目录

**[前言](#pref01.html#pref01)**

**[序言](#pref02.html#pref02)**

**[致谢](#pref03.html#pref03)**

**[作者简介](#pref04.html#pref04)**

**[第 1 章 简介](#ch01.html#ch01)**

[1.1 什么是计算机安全？](#ch01.html#ch01lev1sec1)

*[资产价值](#ch01.html#ch01lev2sec1)*

*[脆弱性-威胁-控制范式](#ch01.html#ch01lev2sec2)*

[1.2 威胁](#ch01.html#ch01lev1sec2)

*[机密性](#ch01.html#ch01lev2sec3)*

*[完整性](#ch01.html#ch01lev2sec4)*

*[可用性](#ch01.html#ch01lev2sec5)*

*[威胁类型](#ch01.html#ch01lev2sec6)*

*[攻击者类型](#ch01.html#ch01lev2sec7)*

[1.3 危害](#ch01.html#ch01lev1sec3)

*[风险与常识](#ch01.html#ch01lev2sec8)*

*[方法-机会-动机](#ch01.html#ch01lev2sec9)*

[1.4 脆弱性](#ch01.html#ch01lev1sec4)

[1.5 控制](#ch01.html#ch01lev1sec5)

[1.6 结论](#ch01.html#ch01lev1sec6)

[1.7 接下来是什么？](#ch01.html#ch01lev1sec7)

[1.8 练习](#ch01.html#ch01lev1sec8)

**[第 2 章 工具箱：认证、访问控制与密码学](#ch02.html#ch02)**

[2.1 认证](#ch02.html#ch02lev1sec1)

*[识别与认证的区别](#ch02.html#ch02lev2sec1)*

*[基于短语和事实的认证：你所知](#ch02.html#ch02lev2sec2)*

*[基于生物特征的认证：你所是](#ch02.html#ch02lev2sec3)*

*[基于令牌的认证：你所有](#ch02.html#ch02lev2sec4)*

*[联合身份管理](#ch02.html#ch02lev2sec5)*

*[多因素认证](#ch02.html#ch02lev2sec6)*

*[安全认证](#ch02.html#ch02lev2sec7)*

[2.2 访问控制](#ch02.html#ch02lev1sec2)

*[访问策略](#ch02.html#ch02lev2sec8)*

*[实施访问控制](#ch02.html#ch02lev2sec9)*

*[面向过程的访问控制](#ch02.html#ch02lev2sec10)*

*[基于角色的访问控制](#ch02.html#ch02lev2sec11)*

[2.3 密码学](#ch02.html#ch02lev1sec3)

*[加密解决的问题](#ch02.html#ch02lev2sec12)*

*[术语](#ch02.html#ch02lev2sec13)*

*[DES：数据加密标准](#ch02.html#ch02lev2sec14)*

*[AES：高级加密标准](#ch02.html#ch02lev2sec15)*

*[公钥密码学](#ch02.html#ch02lev2sec16)*

*[利用公钥密码学交换密钥](#ch02.html#ch02lev2sec17)*

*[错误检测码](#ch02.html#ch02lev2sec18)*

*[信任](#ch02.html#ch02lev2sec19)*

*[证书：可信的身份与公钥](#ch02.html#ch02lev2sec20)*

*[数字签名——所有要素](#ch02.html#ch02lev2sec21)*

[2.4 练习](#ch02.html#ch02lev1sec4)

**[第 3 章 程序与编程](#ch03.html#ch03)**

[3.1 无意（非恶意）编程疏忽](#ch03.html#ch03lev1sec1)

*[缓冲区溢出](#ch03.html#ch03lev2sec1)*

*[中介不完整](#ch03.html#ch03lev2sec2)*

*[检查时刻到使用时刻](#ch03.html#ch03lev2sec3)*

*[未文档化的访问点](#ch03.html#ch03lev2sec4)*

*[差一错误](#ch03.html#ch03lev2sec5)*

*[整数溢出](#ch03.html#ch03lev2sec6)*

*[未终止的空终止字符串](#ch03.html#ch03lev2sec7)*

*[参数长度、类型和数量](#ch03.html#ch03lev2sec8)*

*[不安全的实用程序](#ch03.html#ch03lev2sec9)*

