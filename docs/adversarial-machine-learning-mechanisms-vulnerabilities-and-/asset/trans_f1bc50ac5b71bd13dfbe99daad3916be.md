
所有权利保留，包括文本和数据挖掘以及人工智能技术或类似技术的训练权利。本出版物的任何部分不得复制、存储在检索系统中或以任何形式或任何方式（电子方式、机械方式、影印、录音或其他方式）传输，除非法律允许。关于如何获得本标题中材料再使用许可的建议可在 [http://www.wiley.com/go/permissions](http://www.wiley.com/go/permissions) 查阅。

杰森·爱德华兹有权根据法律确认为本作品的作者。

`Registered Offices`  

John Wiley & Sons, Inc., 111 River Street, Hoboken, NJ 07030, USA  

John Wiley & Sons Ltd, New Era House, 8 Oldlands Way, Bognor Regis, West Sussex, PO22 9NQ, UK

关于我们全球编辑部、客户服务以及 Wiley 产品的更多信息，请访问 [www.wiley.com](http://www.wiley.com)。

根据欧盟产品安全法规，本产品的授权代表为 Wiley-VCH GmbH，地址为 Boschstr. 12, 69469 Weinheim, Germany，电子邮件： [Product_Safety@wiley.com](mailto:Product_Safety@wiley.com)。

Wiley 还以多种电子格式出版书籍，并提供按需印刷。一些内容在标准印刷版本中可能在其他格式中不可用。

商标：Wiley 和 Wiley 标志是 John Wiley & Sons, Inc. 及/或其关联公司在美国及其他国家的商标或注册商标，未经书面许可不得使用。其他所有商标均归其各自所有者所有。John Wiley & Sons, Inc. 与本书中提及的任何产品或供应商均无关联。

`Limit of Liability/Disclaimer of Warranty`  

尽管出版商和作者在准备本工作时尽了最大努力（包括对内容进行审查），但出版商和作者不对本工作内容的准确性或完整性做出任何声明或保证，并明确免除所有保证，包括但不限于任何暗示保证的merchantability（适销性）或 fitness for a particular purpose（特定目的适用性）。本工作不因销售代表、书面销售材料或宣传声明而创建或延伸任何保证。本工作中提及的组织、网站或产品作为引用或潜在信息来源并不意味着出版商和作者认可该组织、网站或产品所提供的信息、服务或建议。本工作出售之初，出版商并未提供专业服务。本文中的建议和策略可能不适合您的具体情况，您应在适当时咨询专家。此外，请注意，本工作中列出的网站在撰写时与阅读时可能已发生变化或消失。出版商和作者不对任何利润损失或其他商业损失（包括但不限于特殊、偶发、 consequential（间接）或其他损失）承担责任。

`***Library of Congress Cataloging-in-Publication Data Applied for***`

Hardback ISBN:`9781394402038`  

ePDF ISBN:`9781394402052`  

ePUB ISBN:`9781394402045`

Cover Design:`Wiley`  

Cover Image:`© sankai/Getty Images`

`***To my beloved family. To my mom and dad, who are no longer with us but whose love and guidance continue to inspire me every day. To my wife, Selda, and my children, Michelle, Chris, Ceylin, and Mayra, for your endless love, patience, and encouragement. To my close family members: Derek, Meltem, Nilos, and Ken. And to my sisters, Robin, Kelly, and Lynn. This book is dedicated to you, with all my love and gratitude.***`

# 前言

人工智能已从研究项目快速发展到医疗、金融、国防和日常生活中的决策系统。随之而来的 sobering reality（令人警醒的现实）是：智能系统容易受到操纵、欺骗或劫持，而传统的安全措施从未设计用于应对这种情况。正是这种现实激励我撰写本书。

我已在网络安全领域工作了二十多年，近年来大部分精力集中在教育上——无论是在多所大学的课堂上，还是通过 [BareMetalCyber.com](http://baremetalcyber.com) 开发学习资源。在这些所有环境中，我观察到对实际指导的需求日益增长：如何确保 AI 系统的安全，而不仅仅是构建或应用它们。学生、工程师、分析师和高管们都在提出同样的核心问题：这些攻击如何运作？它们带来哪些风险？我们该如何防御？

本书旨在回答这些问题。它面向广泛的读者——设计 AI 模型的工程师和科学家、负责防御的安全专业人员、准备进入该领域的学生，以及必须评估风险和政策的决策者。与其单纯罗列威胁，章节旨在构建一个理解 adversaries（对手）如何运作以及防御者如何应对的框架。书中不断加入真实案例、案例研究和练习，使内容更具针对性和可操作性。

我与学习者的工作（无论是通过 Bare Metal Cyber 还是学术项目）表明，将理论与实践结合至关重要。正是这种精神使本书得以问世。我的希望是，它不仅为读者提供工具和知识，还能培养一种责任感、韧性以及对未来系统的信任。

`*Dr. Jason Edwards*`

10 月 30<sup>(th)</sup>, 2025

New Braunfels, TX, USA

# 致谢

我要衷心感谢所有促成本书问世的朋友们。首先，我要向我的家人致以最诚挚的感谢，感谢他们在整个写作过程中提供的无条件支持与理解。对我妻子 Selda 以及孩子们 Michelle、Chris、Ceylin 和 Mayra 的耐心与鼓励，我永远都有依靠。我也感谢与我共享爱与支持的扩展家庭：Derek、Meltem、Nilos 和 Ken，以及我的姐妹 Robin、Kelly 和 Lynn。

我感谢那些对我的职业发展和本书成功作出重要贡献的组织与众多教育者：Hallmark University、Moravian University、IronCircle、Cybrary，以及关注我的 LinkedIn 账户的 10 万多位订阅者。

向每年在 [BareMetalCyber.com](http://BareMetalCyber.com) 上关注我网络安全内容的数百万读者和听众致以感谢，您的信任与参与为这项工作注入动力。感谢让这段旅程成为可能。

我也鼓励所有阅读此文的人支持我心爱的 Beagle Freedom Project，该项目致力于争取并救助用于实验室测试的动物的权利。您可以在 CyberBeagle.kids 了解他们的工作以及我儿子的网络安全书系列（主角为 Darwin the Cyber Beagle）的更多信息。

想了解我的更多著作，请访问 CyberAuthor.Me。加入网络安全专业人士社区，请访问 [BareMetalCyber.com](http://BareMetalCyber.com)。

# 作者的话

