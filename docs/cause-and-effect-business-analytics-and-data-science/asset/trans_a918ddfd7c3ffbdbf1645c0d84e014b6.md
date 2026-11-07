
![](images/cover.jpg)

![封面：因果业务分析与数据科学，Chapman and Hall/CRC 商业与经济统计系列，由 Dominique Haughton、Jonathan Haughton 和 Victor S.Y. Lo 编著，由 CRC Press、Taylor and Francis Group 出版，Boca Raton、London、New York，CRC Press 是 Taylor and Francis Group 的一个印记，是一家 Informa 业务，是一本 Chapman and Hall 书籍。](images/cover.jpg)

# CHAPMAN & HALL/CRC 商业与经济统计系列

Chapman & Hall/CRC 商业与经济统计系列是一个全面的前沿书籍集合，致力于推进商业和经济领域统计方法理解和应用。

**会计实证研究**
工具与方法
*Ian D. Gow 和 Tongqing Ding*

**应用计量经济学家的博弈论**
使用 R 进行数据分析
*Chritopher P. Adams*

**大数据贝叶斯计量经济建模**
*Hang Qian*

**因果业务分析与数据科学**
*Dominque Haughton, Jonathan Haughton, and Victor S. Y. Lo*

**使用 R 进行商业风险与预测分析**
*Ozgur M. Araz 和 David L. Olson*

有关本系列的更多信息，请访问：[https://www.routledge.com/Chapman-and-HallCRC-Series-on-Statistics-in-Business-and-Economics/book-series/CHSBE](https://www.routledge.com/Chapman-and-HallCRC-Series-on-Statistics-in-Business-and-Economics/book-series/CHSBE)

封面图片：filip robert/Shutterstock

首版出版于 2026 年
由 CRC Press 出版
2385 NW Executive Center Drive, Suite 320, Boca Raton FL 33431
由 CRC Press 出版
4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

CRC Press 是 Taylor & Francis Group, LLC 的一个印记

© 2026 Dominique Haughton, Jonathan Haughton, and Victor S.Y. Lo

已做出合理努力以出版可靠的数据和信息，但作者和出版商不能承担所有材料有效性或其使用后果的责任。作者和出版商已尝试追溯本出版物中 reproduced 材料的版权持有者，如果未获得以此形式出版的许可，我们向版权持有者道歉。如有任何未署名的版权材料，请致函告知，以便我们在今后的再版中予以纠正。

除了美国版权法允许的情况外，未经出版商书面许可，本书的任何部分不得以任何形式通过任何电子、机械或其他手段重新印刷、复制、传输或使用，包括复印、缩微胶片和录音，或存入任何信息存储或检索系统。

如需复印或以电子形式使用本作品的材料，请访问 [www.copyright.com](https://www.copyright.com) 或联系 Copyright Clearance Center, Inc. (CCC)，地址为 222 Rosewood Drive, Danvers, MA 01923，电话 978-750-8400。对于 CCC 上不可用的作品，请联系 [mpkbookspermissions@tandf.co.uk](mailto:mpkbookspermissions@tandf.co.uk)

商标声明：产品或公司名称可能为商标或注册商标，仅用于识别和说明，无侵权意图。

国会图书馆编目出版数据
\[如有可用，请在此插入国会图书馆编目数据\]

ISBN: 978-1-482-21647-9 (hbk)
ISBN: 978-1-041-07411-3 (pbk)
ISBN: 978-0-429-17258-8 (ebk)

DOI: [10.1201/9780429172588](https://doi.org/10.1201/9780429172588)

由 KnowledgeWorks Global Ltd. 排版
使用 Palatino 字体

# 作者简介

**Dominique Haughton** (PhD MIT 1983) 是波士顿附近 Bentley University 数学科学和全球研究荣休教授，同时是 Université Paris 1 (Pantheon-Sorbonne, SAMM) 和 Université Toulouse 1 (TSE-R) 的附属研究员。她的广泛出版物集中于如何最好地利用现代分析技术来解决商业或社会利益相关的问题。她是 Ecole Normale Supérieure 的校友，也是美国统计协会的会士。

**Jonathan Haughton** 于 1983 年在哈佛大学获得经济学博士学位。他在经济发展、税收、环境以及贫困的分析和衡量等方面发表了大量著作。如今已退休，他曾担任波士顿 Suffolk University 经济系主任，并在五大洲的 20 多个国家教授或担任顾问。

**Victor S.Y. Lo** 是一位拥有三十多年咨询和企业经验的高管，在营销、风险管理、金融计量经济学、保险、产品开发、交通运输、医疗保健、运营管理、人力资源等众多业务领域运用数据驱动解决方案，并是提升建模的先驱。他目前担任 Fidelity Investments 的数据科学和人工智能高级副总裁，并在多个组织领导数据科学和分析团队。Victor 拥有运筹学硕士学位和统计学博士学位，曾担任管理科学博士后研究员。

# 致谢

我们谨向 CRC Press/Taylor & Francis 的 David Grubbs 及其编辑团队表示感谢，他们启动了本书的出版流程，并在过去十年中给予了无尽的支持、耐心和鼓励。还要感谢 Mayank Sharma 和 KnowledgeWorks Global 团队的专业编辑工作。

我们收到了 Suffolk University 的 Alison Kelly、Jongbyung Jun 和 Le (Sarah) Tang 以及 Bentley University 的 Mingfei Li 对我们章节草稿的非常有帮助的审阅意见。

Dominique 感谢 Bentley University 多年来的支持。Jonathan 也非常感谢 Suffolk University 的支持，包括带薪休假，这有助于推动工作进展。

首先，Victor 衷心感谢全能的上帝在本书撰写期间的过去多年里给予机会、灵感和保护。他还感谢家人无数个周末的慷慨支持以及整个项目期间的鼓励。最后，他要感谢 Jane Zheng 和 Karl Rexer 提供的宝贵建议。

# 1 因果业务分析导论

DOI: [10.1201/9780429172588-1](https://doi.org/10.1201/9780429172588-1)

> *“在上帝面前我们信任，其余的人请拿出数据”*
>
> *W. Edwards Deming*

本书讨论两个主要相关主题：应用于商业问题的因果分析方法以及提升分析。本书的写作面向具备分析学、经济学、统计学、市场营销等相关领域基础知识的任何人，都易于理解。对于相关领域硕士项目学生以及希望扩展知识和技能的分析实践者而言，本书很可能有用。

重点在于概念以及重要技术的核心要素。这可以让读者入门，但要掌握任何特定技术仍需进一步阅读、深入研究、实践和实验。我们的目标是提供正确的路径和初始步骤，但我们并未撰写编程手册，因为我们相信，一旦读者大致知道要寻找什么，在 Stata、SAS、社会科学统计软件包（SPSS）、R、Python 或专业软件中找到合适的程序应该不会太困难。

本章其余部分讨论了在商业思维中因果关系的重要性，并建议读者如何选择阅读章节顺序以最大程度地受益于本书。

## 1.1 迈向商业分析与数据科学的趋势
