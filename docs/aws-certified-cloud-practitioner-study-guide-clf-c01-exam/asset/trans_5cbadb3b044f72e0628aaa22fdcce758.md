
![](images/cover.jpg)

高级收购编辑：`Kenyon Brown`

发展编辑：`Kathryn Duggan`

制作编辑：`Lauren Freestone`

副总编辑：`Kim Wimpsett`

编辑经理：`Pete Gaughan`

制作经理：`Kathleen Wisor`

联合出版商：`Jim Minatel`

校对员：`Tiffany Taylor`

索引员：`Johnna VanHoose Dinse`

项目协调员，封面：`Brent Savage`

封面设计师：`Wiley`

封面图片：© Getty Images, Inc./Jeremy Woodhouse

版权 © 2019 由 `John Wiley & Sons, Inc.`，印第安纳州出版

同时在美国和加拿大发行

ISBN：`978-1-119-49070-8`

ISBN：`978-1-119-49069-2` (电子版)

ISBN：`978-1-119-49071-5` (电子版)

在美国生产

未经出版商书面许可，本出版物的任何部分不得复制、存储在检索系统中或以任何形式或通过任何方式（电子、机械、影印、录音、扫描或其他方式）传输，除非符合 1976 年美国版权法第 107 或第 108 节的规定，或已向版权清除中心支付相应的每份副本费用。请将版权许可请求发送至出版商 `John Wiley & Sons, Inc.` 的权限部门，地址为 `111 River Street, Hoboken, NJ 07030`，电话 (201) 748-6011，传真 (201) 748-6008，或在线访问 [http://www.wiley.com/go/permissions](http://www.wiley.com/go/permissions)。

免责声明/担保免责声明：出版商和作者不对本作品内容的准确性或完整性作出任何声明或担保，并明确免除所有担保，包括但不限于适用于特定目的的担保。销售或促销材料不得创建或扩展任何担保。本文档所含建议和策略可能不适用于所有情况。本作品出售时，出版商不提供法律、会计或其他专业服务。如需专业帮助，请联系合格的专业人士。出版商和作者均不对由此产生的损害负责。本文中引用的组织或网站的链接不代表作者或出版商对其内容或建议的认可。此外，请注意，本文中列出的互联网网站在本文撰写时可能已发生变化或消失。

如需了解我们其他产品和服务或获取技术支持，请在美国联系客户服务部，电话 (877) 762-2974，或在美国境外致电 (317) 572-3993，传真 (317) 572-4002。

Wiley 以多种印刷和电子格式发行，并提供按需印刷。标准印刷版本中包含的部分材料可能不在电子书或按需印刷版本中。如果本书提及的 CD 或 DVD 未包含在您购买的版本中，您可以在 [http://booksupport.wiley.com](http://booksupport.wiley.com/) 下载相关材料。有关 Wiley 产品的更多信息，请访问 [www.wiley.com](http://www.wiley.com/)。

**Library of Congress Control Number:** `2019939496`

商标：`Wiley`、`Wiley` 标志和 `Sybex` 标志是 `John Wiley & Sons, Inc.` 及其关联公司在美国和其他国家的商标或注册商标，未经书面许可不得使用。`AWS` 是 `Amazon Technologies, Inc.` 的注册商标。其他所有商标均属其所属所有者。`John Wiley & Sons, Inc.` 与本书中提及的任何产品或供应商均无关联。

# Acknowledgments

我们谨向以下帮助我们完成 `AWS Certified Cloud Practitioner Study Guide CLF-C01 Exam` 的人员致谢。

首先，特别感谢我们的朋友 Wiley。`Kenyon Brown`，高级收购编辑，推动了本项目的开展，并将所有环节组织起来。我们的项目编辑 `Kathi Duggan` 保持了项目的进度，确保我们走在正确的方向上。我们还要感谢我们细心的技术编辑 `John Mueller` 以及 `Pete Gaughan`：我们可能不清楚“内容启用经理”具体指什么，但我们确信这一角色发挥了重要作用。

最后，再次向作者们致谢，感谢他们之间的合作！

# About the Authors

![](images/ffirst001.jpg)

**`David Clinton`** 是一名 Linux 服务器管理员，曾在学术和企业环境中参与 IT 基础设施工作。他撰写过多本技术书籍，包括 *`AWS Certified Solutions Architect Study Guide: Associate SAA-C01 Exam, Second Edition`*（Sybex，2019），并为 Pluralsight 制作了 20 部讲解 Amazon Web Services、Linux 管理、服务器虚拟化和 IT 安全的视频课程。

在之前的职业生涯中，`David` 曾担任高中教师 20 年。他目前居住于加拿大多伦多，与妻子和家人同住，可通过他的网站 [https://bootstrap-it.com](https://bootstrap-it.com) 联系。

![](images/ffirst002.jpg)

**`Ben Piper`** 是一名云计算和网络顾问，曾撰写多本著作，包括 *`AWS Certified Solutions Architect Study Guide: Associate SAA-C01 Exam, Second Edition`*（Sybex，2019）。他制作了 20 多门涵盖 Amazon Web Services、Cisco 路由交换、Citrix、Puppet 配置管理以及 Windows Server 管理的培训课程。您可以通过访问他的网站 [https://benpiper.com](https://benpiper.com) 与他联系。

# CONTENTS

1.  [Cover](fcover.xhtml)

2.  [Acknowledgments](#f03.xhtml)

3.  [About the Authors](#f04.xhtml)

4.  [Table of Exercises](#f05.xhtml)

5.  [Introduction](#f06.xhtml)

6.  [Assessment Test](#f07.xhtml)

7.  [Answers to Assessment Test](#f08.xhtml)

8.  [Chapter 1 The Cloud](#c01.xhtml) 

    1.  [Introduction](#c01.xhtml#c1_1)

    2.  [What Is Cloud Computing?](#c01.xhtml#c1_2)

    3.  [Server Virtualization: The Basics](#c01.xhtml#c1_3)

    4.  [Cloud Platform Models](#c01.xhtml#c1_4)

    5.  [Scalability and Elasticity](#c01.xhtml#c1_5)

    6.  [Summary](#c01.xhtml#c1_6)

    7.  [Exam Essentials](#c01.xhtml#c1_7)

    8.  [Review Questions](#c01.xhtml#c01-exsec-0001)

9.  [Chapter 2 Understanding Your AWS Account](#c02.xhtml) 

    1.  [Introduction](#c02.xhtml#c2_1)

    2.  [The Free Tier](#c02.xhtml#c2_2)

    3.  [Product Pricing](#c02.xhtml#c2_3)

    4.  [Service Limits](#c02.xhtml#c2_4)

    5.  [Billing and Cost Management](#c02.xhtml#c2_5)

    6.  [Summary](#c02.xhtml#c2_6)

    7.  [Exam Essentials](#c02.xhtml#c2_7)

    8.  [Review Questions](#c02.xhtml#c02-exsec-0001)

10.  [Chapter 3 Getting Support on AWS](#c03.xhtml) 

     1.  [Introduction](#c03.xhtml#c3_1)

     2.  [Support Plans](#c03.xhtml#c3_2)

     3.  [Documentation and Online Help](#c03.xhtml#c3_3)

     4.  [Trusted Advisor](#c03.xhtml#c3_4)

     5.  [Summary](#c03.xhtml#c3_5)

     6.  [Exam Essentials](#c03.xhtml#c3_6)

     7.  [Review Questions](#c03.xhtml#c03-exsec-0001)

11.  [Chapter 4 Understanding the AWS Environment](#c04.xhtml) 

     1.  [Introduction](#c04.xhtml#c4_1)

     2.  [AWS Global Infrastructure: AWS Regions](#c04.xhtml#c4_2)

     3.  [AWS Global Infrastructure: Availability Zones](#c04.xhtml#c4_3)

     4.  [AWS Global Infrastructure: Edge Locations](#c04.xhtml#c4_4)

     5.  [The AWS Shared Responsibility Model](#c04.xhtml#c4_5)

     6.  [Summary](#c04.xhtml#c4_6)

     7.  [Exam Essentials](#c04.xhtml#c4_7)

     8.  [Review Questions](#c04.xhtml#c04-exsec-0001)

12.  [Chapter 5 Securing Your AWS Resources](#c05.xhtml) 

     1.  [Introduction](#c05.xhtml#c5_1)

     2.  [AWS Identity and Access Management](#c05.xhtml#c5_2)

