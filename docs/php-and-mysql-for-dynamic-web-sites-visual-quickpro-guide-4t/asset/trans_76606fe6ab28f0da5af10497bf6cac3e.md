

![cover-image](graphics/0132767589.jpg)

# Visual QuickPro Guide

# PHP and MySQL for Dynamic Web Sites

## Fourth Edition

## Larry Ullman

![Image](graphics/pub.jpg)

Visual QuickPro Guide

**PHP and MySQL for Dynamic Web Sites, Fourth Edition**

Larry Ullman

Peachpit Press

1249 Eighth Street

Berkeley, CA 94710

510/524-2178

510/524-2221 (fax)

Find us on the Web at: [www.peachpit.com](http://www.peachpit.com)

To report errors, please send a note to: [errata@peachpit.com](mailto:errata@peachpit.com)

Peachpit Press is a division of Pearson Education.

Copyright © 2012 by Larry Ullman

Editor: Rebecca Gulick

Copy Editor: Patricia Pane

Technical Reviewer: Anselm Bradford

Production Coordinator: Myrna Vladic

Compositor: Debbie Roberti

Proofreader: Bethany Stough

Indexer: Valerie Haynes-Perry

Cover Design: RHDG / Riezebos Holzbaur Design Group, Peachpit Press

Interior Design: Peachpit Press

Logo Design: MINE™ [www.minesf.com](http://www.minesf.com)

## 版权声明

保留所有权利。未经出版商事先书面许可，本书任何部分不得以任何形式、任何方式（电子、机械、影印、录制或其他方式）复制或传播。如需获取重印和摘录的许可信息，请联系 [permissions@peachpit.com](mailto:permissions@peachpit.com)。

## 免责声明

本书信息按“现状”提供，不提供任何担保。虽然编写本书时已采取一切预防措施，但作者和 Peachpit Press 对任何人或实体因本书包含的说明或书中描述的计算机软硬件产品而直接或间接导致的任何损失或损害（或据称导致的损失或损害）均不承担任何责任。

## 商标

Visual QuickPro Guide 是 Peachpit Press（Pearson Education 的一个部门）的注册商标。MySQL 是 MySQL AB 在美国和其他国家的注册商标。Macintosh 和 Mac OS X 是 Apple, Inc. 的注册商标。Microsoft 和 Windows 是 Microsoft Corp. 的注册商标。本书使用的其他产品名称可能是其各自所有者的商标。本书中的网站图像版权归原持有者所有，经许可使用。本书未得到上述任何公司（包括 MySQL AB）的官方认可，也与其无关联。

制造商和销售商用于区分其产品的许多名称均声称拥有商标权。凡在本书中出现的此类名称，只要 Peachpit 知晓其商标权声明，均按商标所有者的要求印刷。本书中提及的所有其他产品名称和服务仅用于编辑目的，旨在造福相关公司，无意侵犯商标。此类使用或任何商业名称的使用均不旨在暗示本书获得认可或与其有关联。

ISBN-13: 978-0-321-78407-0

ISBN-10: 0-321-78407-3

9 8 7 6 5 4 3 2 1

Printed and bound in the United States of America

## 献词

献给我的母校东北密苏里州立大学的优秀师资。特别要感谢：Monica Barron 博士、Dennis Leavens 博士、Ed Tyler 博士和 Cole Woodcox 博士，后者我还有幸称为我的挚友。如果没有这些教育工作者慷慨、深刻且卓越的教导，我就不会成为今天作为作家、学生、教师或一个人的我。

## 特别鸣谢

衷心感谢 Peachpit Press 的所有人，一如既往。

感谢杰出的编辑 Rebecca Gulick，她让我的工作轻松了许多。感谢 Patricia Pane 的辛勤工作、有益的建议和令人印象深刻的细致关注。感谢 Valerie Haynes-Perry 编写索引，感谢 Myrna Vladic 和 Deb Roberti 负责书籍排版，感谢 Anselm Bradford 进行技术审阅。

向 PHP、MySQL、Apache、phpMyAdmin、MAMP 和 XAMPP 等其他优秀项目的开发者们致敬。向各新闻组、邮件列表、支持论坛等的热心人士致以衷心的“干杯”，他们为有需要的人提供帮助和建议。

感谢读者们一如既往的支持，赋予了我的工作意义。特别多谢那些为[第 17 章](#ch17.html#ch17)“示例——留言板”提供翻译的人员，以及提出希望在本版中看到什么内容建议的人员。

感谢 Karnesha 和 Sarah 照顾和陪伴孩子们，让我能腾出手来完成一些工作。

最后，如果没有妻子 Jessica 的爱与支持，我无法完成任何一本书。特别向 Zoe 和 Sam 致意，他们给了我写书的理由，也给了我不写书的理由！

## 目录

[简介](#pre02.html#pre02)

**第 1 章 PHP 简介** [#ch01.html#ch01](#ch01.html#ch01)

- [基本语法](#ch01.html#ch01lev1sec1)
- [向 Web 浏览器发送数据](#ch01.html#ch01lev1sec2)
- [编写注释](#ch01.html#ch01lev1sec3)
- [什么是变量？](#ch01.html#ch01lev1sec4)
- [字符串简介](#ch01.html#ch01lev1sec5)
- [字符串拼接](#ch01.html#ch01lev1sec6)
- [数字简介](#ch01.html#ch01lev1sec7)
- [常量简介](#ch01.html#ch01lev1sec8)
- [单引号与双引号](#ch01.html#ch01lev1sec9)
- [基本调试步骤](#ch01.html#ch01lev1sec10)
- [复习与实践](#ch01.html#ch01lev1sec11)

**第 2 章 PHP 编程** [#ch02.html#ch02](#ch02.html#ch02)

- [创建 HTML 表单](#ch02.html#ch02lev1sec1)
- [处理 HTML 表单](#ch02.html#ch02lev1sec2)
- [条件判断与运算符](#ch02.html#ch02lev1sec3)
- [验证表单数据](#ch02.html#ch02lev1sec4)
- [数组简介](#ch02.html#ch02lev1sec5)
- [For 循环和 While 循环](#ch02.html#ch02lev1sec6)
- [复习与实践](#ch02.html#ch02lev1sec7)

**第 3 章 创建动态网站** [#ch03.html#ch03](#ch03.html#ch03)

- [包含多个文件](#ch03.html#ch03lev1sec1)
- [再谈 HTML 表单处理](#ch03.html#ch03lev1sec2)
- [创建粘性表单](#ch03.html#ch03lev1sec3)
- [创建自定义函数](#ch03.html#ch03lev1sec4)
- [复习与实践](#ch03.html#ch03lev1sec5)

**第 4 章 MySQL 简介** [#ch04.html#ch04](#ch04.html#ch04)

- [命名数据库元素](#ch04.html#ch04lev1sec1)
- [选择列类型](#ch04.html#ch04lev1sec2)
- [选择其他列属性](#ch04.html#ch04lev1sec3)
- [访问 MySQL](#ch04.html#ch04lev1sec4)
- [复习与实践](#ch04.html#ch04lev1sec5)

**第 5 章 SQL 简介** [#ch05.html#ch05](#ch05.html#ch05)

- [创建数据库和表](#ch05.html#ch05lev1sec1)
- [插入记录](#ch05.html#ch05lev1sec2)
- [查询数据](#ch05.html#ch05lev1sec3)
- [使用条件判断](#ch05.html#ch05lev1sec4)
- [使用 LIKE 和 NOT LIKE](#ch05.html#ch05lev1sec5)
- [对查询结果排序](#ch05.html#ch05lev1sec6)
- [限制查询结果](#ch05.html#ch05lev1sec7)
- [更新数据](#ch05.html#ch05lev1sec8)
- [删除数据](#ch05.html#ch05lev1sec9)
- [使用函数](#ch05.html#ch05lev1sec10)
- [复习与实践](#ch05.html#ch05lev1sec11)

**第 6 章 数据库设计** [#ch06.html#ch06](#ch06.html#ch06)

- [规范化](#ch06.html#ch06lev1sec1)
- [创建索引](#ch06.html#ch06lev1sec2)
- [使用不同的表类型](#ch06.html#ch06lev1sec3)
- [语言与 MySQL](#ch06.html#ch06lev1sec4)
- [时区与 MySQL](#ch06.html#ch06lev1sec5)
- [外键约束](#ch06.html#ch06lev1sec6)
- [复习与实践](#ch06.html#ch06lev1sec7)

**第 7 章 高级 SQL 和 MySQL** [#ch07.html#ch07](#ch07.html#ch07)

- [执行连接查询](#ch07.html#ch07lev1sec1)
- [对选定结果分组](#ch07.html#ch07lev1sec2)
- [高级查询](#ch07.html#ch07lev1sec3)
- [执行全文搜索](#ch07.html#ch07lev1sec4)
- [优化查询](#ch07.html#ch07lev1sec5)
- [执行事务](#ch07.html#ch07lev1sec6)

