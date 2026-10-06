

# Mark Minasi
Kevin Greene
Christian Booth
Robert Butler
John McCabe
Robert Panek
Michael Rice
Stefan Roth

![](img/41a83208e6906a3732620203b836cea7_0_0.png)

# 精通 Windows
Server® 2012 R2

![](img/41a83208e6906a3732620203b836cea7_0_1.png)

# 精通 Windows Server 2012 R2

Mark Minasi
Kevin Greene
Christian Booth
Robert Butler
John McCabe
Robert Panek
Michael Rice
Stefan Roth

![](img/41a83208e6906a3732620203b836cea7_2_0.png)

采购编辑：Mariann Barsolo

开发编辑：Tom Cirtin

技术编辑：Gavin McShera

制作编辑：Rebecca Anderson

校对：Linda Reckenton

编辑经理：Pete Gaugan

制作经理：Tim Tate

副总裁兼执行集团出版：Richard Swann

助理出版：Cites Webb

书籍编辑：Maureen Forys, Happenstance Type-O-Rama; Judy Fung

校对员：Sarah Kakhiki, Word One New

索引员：Jd Indexing

项目协调（封面）：Katherine Crocker

封面设计师：Ryan Sneed

封面图片：© Getty Images,/ 北北美

版权所有 © 2014 John Wiley & Sons, Inc., 印第安纳州印第纳利斯
出版于 John Wiley & Sons, Inc., 印第安纳州印第纳利斯
在加拿大同步出版

ISBN: 978-1-118-33942-6
ISBN: 978-1-118-33945-5 (电子版)
ISBN: 978-1-118-33172-9 (电子版)

未经出版者书面许可，本出版物的任何部分不得在检索系统中复制、发行或以任何形式或手段（电子、机械、复印、录制、扫描或其他）传输，除非符合《美国版权法》第 107 节或第 108 节的规定，或根据适当的单份费用向版权许可中心（地址1220 Roosevelt Drive, Dover, MA 02148, (978) 750-8400）支付许可。许可申请请邮寄至 John Wiley & Sons, Inc., 111 River Street, Hoboken, NJ 07030, (201) 748-6061，或在线访问：http://www.wiley.com/go/permission

责任限制/免责声明：出版者和作者对本书的准确性或完整性不作任何陈述或保证，并辞弃所有保证，包括对特定用途的适用性的保证。不提供任何明示或暗示的保证。本书中的建议和意见可能不适用于您的需求。本书的销售基于以下理解：出版者并未提供法律、会计或其他专业服务。如果需要专业建议，应寻求能力专业人士的服务。作者和出版者均对所遭受的损害不承担责任。机构或网站提供本书并不意味着该机构或网站认可书中所包含的信息，也不表明其有效性。建议读者注意，所使用的网站自本书编写及实际上可能发生变化或消失。

有关其他产品和服务的一般信息或需获取技术支持，请联系我们的美国客户服务中心，电话 (877) 762-2974 或 (317) 572-3993

Wiley 出版多种印刷和电子格式以及按需打印。书中包含的某些材料可能未包含在电子书或按需打印版本中。如果书中提到的媒体（如 CD 或 DVD）未包含在购买的版本中，您可以从 http://bookstore.wiley.com 下载这些材料。有关有关 Wiley 产品的更多信息，请访问...

美国国会图书馆编号：2013948018

商标：Wiley 和 Wiley 标志是 John Wiley & Sons, Inc. 及其附属公司在美国和其他国家的注册商标或已注册商标，未经书面许可不得使用。Windows Server 是微软公司的注册商标。所有其他商标均为其各自所有者的财产。John Wiley & Sons, Inc. 与书中提到的任何产品或供应商均无。

10 987654321

亲爱的读者：

感谢选择《精通 Windows Server 2012 R2》。本书是 Sybex 高质量书籍系列的一部分，所有书籍均由卓越作者编写，他们将实践经验与教学天赋相结合。

Sybex 成立于 1976 年。30 多年后，我们仍然致力于制作水平一贯卓越的书籍。在每一部作品中，我们都在努力为行业树立新标准。从我们使用的纸张到我们合作的作者，我们的目标是为您提供最好的书籍。

我希望在这些页面中看到所有的努力。我非常兴趣听取您的意见并获得对我们工作情况的反馈。欢迎通过电子邮件 contact@wiley.com 告诉我您对此书或任何其他 Sybex 书籍的看法。如果您认为在书中发现了技术错误，请访问 http://www.sybex.com。客户反馈对我们的工作至关重要。

顺颂商祺，

![](img/41a83208e6906a3732620203b836cea7_0_0.png)

Chris Webb
Sybex 助理出版

# 致谢

作者感谢 Gavin McShera 提供的广泛帮助和建设性批评，并感谢 Tom Cirtin 将我们风格迥异的草稿整理成可出版的形式。我们感谢 Wiley 的制作团队：编辑经理 Pete Gaugan、采购编辑 Mariann Barsolo、制作编辑 Rebecca Anderson、校对 Linda Reckenton 和校对员 Sarah Kakhiki。

特别感谢我美丽的妻子，感谢她在我编写本书章节的漫长时间里对我付出的耐心！当然，感谢 Mariann Barsolo 和 Pete Gaugan 邀请我加入这个项目，并让我有机会与一些才华横溢的思想、贡献者和编辑合作——尽管为了出版，我们不得不重写了半本书的内容！

还要感谢我在 Ergo 的同事们，他们让我有机会参与此类企业级项目，这些项目帮助我积累了编写此类书籍所需的经验。最后，我想将我在书中的工作献给我的岳父 Cecil，多年来他一直像父亲一样对待我。他的力量和勇气是我们我们所有人的灵感。

我想感谢家人的支持。投入到这本书中的时间似乎是永恒的，失去了许多周末，守在键盘前编写章节。我非常感谢你们的耐心。我爱你们！

我想感谢我的妻子 Nicole 以及我们的两个儿子 Alex 和 Miles。他们的爱和支持帮助我度过了我的一切。

我想感谢我的妻子 Sharon 以及三个孩子 Sophie、Adam 和 Sam 的耐心。在忙碌的工作与家庭生活之间取得平衡并不容易！

首先，我必须感谢 Kevin Greene 给我机会编写这本书并指导我完成第一步工作。特别感谢我的妻子 Simona，接纳了我花在书上而非陪伴她的时间！

我最后的感谢来自我的家人、朋友和我的公司，他们以多种方式支持我跟上项目进度。Roth

# 关于作者

**Mark Minasi** 是一位畅销书作家、技术专栏作家、演讲者兼 IT 顾问。他自 1973 年就开始接触计算机。在大学期间他学到了两点：

- 第一，计算机很棒（在 20 世纪是如此）。
- 第二，很多技术人员都是很好的人，但他们在解释技术问题时可能会让你听睡。

Mark 通过撰写数千篇技术专栏、编写畅销技术书籍，让计算机变得更容易理解、更有趣。他编写了许多关于操作系统和网络规划、安装和维护的指南，曾被 Wiley 四次评为“最受欢迎的技术作者”。Mark 最著名的可能是他的《Windows Server》和《计算机计算机升级与维护》书籍，这两本书已出版了 12 版，销量超过百万册。

Mark 幽默、具有挑衅性且富有启发性的风格深受全球观众的喜爱。通过他的公司 MR&D (www.minasi.com)，Mark 提供技术研讨会、课程和演讲，此外还有通讯。您也可以订阅 Mark 的通讯。

**Kevin Greene** 是本书作者团队的负责人，是微软云与数据中心管理 MVP，自 1999 年起一直从事 IT 工作。目前在爱尔兰的 Ergo担任 System Center 专家。在该职位上，他为客户提供 Windows Server 和 System Center 的企业级解决方案。过去，他曾担任 IT 管理员、技术团队领袖和高级顾问。他从 Windows 4.0 时代就开始参加微软认证，拥有 MCSE、MCSA、MCIT、MCT 和 CTS 等资质。Kevin 是 Windows Server and System Center (WSSC) 社区的活跃参与者，通过他的博客 http://kevengreeneblog.blogspot.com，您可以在 Twitter 上通过 @kgreene 找到他。

Kevin 经常就 Windows Server 和 System Center 进行演讲并参与播客，是《Mastering System Center 2012 Operations Manager》(Sybex, 2012) 的合著者。

Kevin 住在爱尔兰基尔代郡的 Sallins，与妻子 Laura 以及儿子 Matthew 和 Dylan 生活在一起。在不使用电脑时，他会与家人共度时光并支持曼联。他还是自由派踢拳的二级黑带，虽然不再像过去那样参与这项运动，但他仍然是这项武术的热门爱好者。

