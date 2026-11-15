

![](img/1ddec54918a4802eb9b4febec3d4e7f6_0_0.png)

## PHP 5.3 入门

## 充分利用 WROX.com

- **互动**：通过参与我们的 P2P 论坛，在线上发挥积极作用
- **按需章节**：以 PDF 格式购买单独的图书章节
- **Wrox 在线图书馆**：我们有数百本书可通过 Books24x7.com 在线获取
- **加入社区**：在 newsletter.wrox.com 注册我们的免费月度简报
- **Wrox Blox**：下载简短的信息片段和代码，让您时刻掌握最新动态，避免出错！
- **浏览**：想要更多 Wrox 内容吗？我们有关于 .NET、SQL Server、Java、XML、Visual Basic、C#/ C++ 等众多主题的图书和电子书！
- **联系我们。** 我们始终欢迎读者反馈。有书的想法吗？需要社区支持？请通过 wrox-partnerwithus@wrox.com 电子邮件告知我们。

| 章节/部分 | 页码 |
|-----------|------|
| 引言 | xxvii |
| 第一部分：使用 PHP 入门 | |
| 第 1 章：PHP 简介 | 3 |
| 第 2 章：你的第一个 PHP 脚本 | 11 |
| 第二部分：学习语言 | |
| 第 3 章：PHP 语言基础 | 33 |
| 第 4 章：决策与循环 | 51 |
| 第 5 章：字符串 | 73 |
| 第 6 章：数组 | 101 |
| 第 7 章：函数 | 141 |
| 第 8 章：对象 | 165 |
| 第三部分：在实践中使用 PHP | |
| 第 9 章：使用 PHP 处理 HTML 表单 | 221 |
| 第 10 章：使用查询字符串、Cookie 和 会话 保持状态 | 267 |
| 第 11 章：使用文件和目录 | 297 |
| 第 12 章：数据库和 SQL 简介 | 337 |
| 第 13 章：使用 PHP 从 MySQL 检索数据 | 367 |
| 第 14 章：使用 PHP 操作 MySQL 数据 | 403 |
| 第 15 章：使用 PEAR 让工作更轻松 | 441 |
| 第 16 章：PHP 与外部世界 | 471 |
| 第 17 章：使用 PHP 生成图像 | 507 |
| 第 18 章：使用正则表达式进行字符串匹配 | 539 |
| 第 19 章：使用 XML | 573 |
| 第 20 章：编写高质量代码 | 619 |
| 附录 A：练习题解答 | 673 |
| 附录 B：配置 PHP | 719 |
| 附录 C：MySQL 的替代方案 | 757 |
| 附录 D：从命令行使用 PHP | 765 |
| 索引 | 775 |

## PHP 5.3 入门

## PHP 5.3 入门

Matt Doyle

![](img/1ddec54918a4802eb9b4febec3d4e7f6_6_0.png)

威利出版公司

Published by
威利出版公司
10475 Crosspoint Boulevard
Indianapolis, IN 46256

www.wiley.com

Copyright © 2010 by 威利出版公司，印第安纳波利斯，印第安纳州

ISBN: 978-0-470-41396-8

在美国制造

10 9 8 7 6 5 4 3 2 1

国会图书馆控制号：2009017149

本出版物的任何部分不得以任何形式或之任何手段（包括电子、机械、影印、录制、扫描或其他方式）复制、存储在检索系统中或传播，除非符合 1976 年美国版权法第 107 节或第 108 节的规定，或获得出版商的事先书面许可，或通过向版权清算中心（Copyright Clearance Center，222 Rosewood Drive, Danvers, MA 01923, (978) 750-8400, fax (978) 646-8600）支付相应的每份复制费获得授权。向出版商申请许可的请求应寄至 Permissions Department, John Wiley & Sons, Inc., 111 River Street, Hoboken, NJ 07030, (201) 748-6011, fax (201) 748-6008，或在线访问 http://www.wiley.com/go/permissions。

Limit of Liability/Disclaimer of Warranty: 出版商和作者对本作品内容的准确性或完整性不作任何陈述或担保，并明确否认所有担保，包括但不限于对特定用途适销性的担保。销售或推广材料不得创建或延伸任何担保。此处包含的建议和策略可能并不适合每种情况。出售本作品时，默认出版商不提供法律、会计或其他专业服务。如需专业协助，应寻求合格专业人士的服务。出版商和作者均不应对由此产生的损害承担责任。本作品中提及某个组织或网站作为引用和/或潜在的进一步信息来源，并不意味着作者或出版商认可该组织或网站可能提供的信息或其提出的建议。此外，读者应注意，本作品中列出的互联网网站在本作品撰写时和阅读时之间可能已更改或消失。

For general information on our other products and services please contact our Customer Care Department within the United States at (877) 762-2974, outside the United States at (317) 572-3993 or fax (317) 572-4002.

Trademarks: Wiley 和 Wiley 标志是 John Wiley & Sons, Inc. 及/或其附属公司在美国和其他国家的商标或注册商标，未经书面许可不得使用。所有其他商标均归其各自所有者所有。Wiley Publishing, Inc. 与本书中提及的任何产品或供应商无关。

威利还以多种电子格式出版其图书。某些印刷版中出现的内容可能无法在电子书中获得。

本书献给 Cat，我在风暴中的依靠，以及 Zack，我在阴霾中的阳光。

## 关于作者

**Matt Doyle**，生长于英格兰，很早就发现了计算机的乐趣，多亏他妈妈明智地决定投资一台旧款的自组装电脑，竟有惊人的 4K 内存。从那以后，他一发不可收拾，获得了计算机科学学士学位，并进入 IT 行业。

在不同公司担任 IT 经理、C 程序员、软件测试员、Web 设计师和 Web 开发者等不同职务后，Matt 决定是时候创业了。1997 年，他联合创立了 ELATED（`www.elated.com`），这是一家致力于帮助人们构建优秀网站的公司。

Matt 最初使用 C、Perl 和 JavaScript 进行 Web 开发，多年来还使用过包括 Java、ASP 和 Python 在内的其他一些 Web 编程语言。PHP 是他构建动态网站时目前的首选语言。

2002 年，厌倦了英格兰寒冷的天气，他与妻子 Cat 一起退隐到澳大利亚悉尼北部海滩地区阳光明媚的海岸。他们现在和儿子 Isaac 一起生活在新南威尔士州南部高地（讽刺的是，那里的天气也很像英格兰）。

## 致谢

- **执行编辑**：Carol Long
- **副总裁兼执行集团出版商**：Richard Swadley
- **开发编辑**：Ed Connor
- **副总裁兼执行出版商**：Barry Pruett
- **技术编辑**：Ben Schupak
- **副出版商**：Jim Minatel
- **制作编辑**：Rebecca Anderson
- **封面项目协调员**：Lynsey Stanford
- **文字编辑**：Kim Cofer
- **校对员**：Nate Pitts, Word One
- **编辑经理**：Mary Beth Wakefield
- **索引编制员**：J & J Indexing
- **制作经理**：Tim Tate
- **封面图像**：© Purestock/Punchstock

