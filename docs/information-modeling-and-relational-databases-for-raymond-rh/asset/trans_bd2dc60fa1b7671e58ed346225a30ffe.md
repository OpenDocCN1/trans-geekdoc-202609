
*   [Falkenberg E.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb0420) Concepts for modelling information. In: Nijssen G., ed. *Modelling in Database Management Systems.* Amsterdam: North-Holland Publishing; 1976.

*   [Fillmore C.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb0440) The case for case. In: Bach E., Harms R., eds. *Universals in Linguistic Theory.* New York: Holt, Rinehart and Winston; 1968:1–88.

*   [Haack S.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb0520) *Philosophy of Logics.* London: Cambridge University Press; 1978.

*   [Habrias H.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb0525) Normalized object oriented method. In: *Encyclopedia of Microcomputers.* New York: Marcel Dekker; 271–285. 1993;vol. 12.

*   [Halpin T., Evans K., Hallock P., MacLean W.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb0790) *Database Modeling with Microsoft® Visio for Enterprise Architects.* San Francisco: Morgan Kaufmann; 2003.

*   [Harris R.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb0815) *Information Graphics: A Comprehensive Illustrated Reference.* Atlanta, GA: Management Graphics; 1996.

*   [Kent W.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb0875) Entities and Relationships in Information. In: Nijssen G., ed. *Proc. 1977 IFIP Working Conf. on Modelling in Data Base Management Systems.* Nice, France: North-Holland Publishing; 1977:67–91.

*   [Levesque H.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb0930) *A fundamental trade-off in knowledge representation and reasoning.* In: Proc. CSCSI-84, London, Ontario; 1984:141–152.

*   [Meersman R.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb0965) *The RIDL Conceptual Language.* Research Report Brussels: Int. Centre for Information Analysis Services, Control Data Belgium; 1982.

*   [Nijssen G.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb1025) A gross architecture for the next generation database management systems. In: Nijssen G., ed. *Proc. 1976 IFIP Working Conf. on Modelling in Data Base Management Systems.* Freudenstadt, Germany: North-Holland Publishing; 1976:1–24.

*   [Nijssen G.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb1030) Current issues in conceptual schema concepts. In: Nijssen G., ed. *Proc. 1977 IFIP Working Conf. on Modelling in Data Base Management Systems.* Nice, France: North-Holland Publishing; 1977:31–66.

*   [Senko M.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb1150) Information systems: records, relations, sets, entities and things. *Information Systems.* 1975;1(1):3–13 Jan. 1995, Pergamon Press.

*   [Shoval P., Shreiber N.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb1165) Database reverse engineering: from the relational to the binary relational model. *Data Knowl. Eng.* 1993;10:293–315.

*   [ter Hofstede A.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb1225) *Information Modeling in Data Intensive Domains.* PhD Thesis University of Nijmegen; 1993.

*   [ter Hofstede A., Proper H., van der Weide T.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb1240) Formal definition of a conceptual language for the description and manipulation of information models. *Inform. Syst.* 1993;18(7):489–523.

*   [Trog D., Vereecken J., De Leenheer P., Meersman R.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb1265) T-Lex: a role-based ontology engineering tool. In: Meersman R., Tari Z., Herrero P., et al., eds. *On the Move to Meaningful Internet Systems 2006: OTM 2006 Workshops.* Montpellier: Springer LNCS 4278; 2006.

*   [van Griethuysen, 1982](#Ch003_59-110_B9780443237904000037.xhtml#B-bb1280) van Griethuysen J., ed. *Concepts and Terminology for the Conceptual Schema and the Information Base.* Eindhoven: ISO TC97/SC5/WG3; 1982.

*   [Verheijen G., van Bekkum J.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb1285) NIAM: an information analysis method. In: *Information Systems Design Methodologies: a comparative review, Proc. IFIP WG8.1 Working Conf.* Noordwijkerhout, The Netherlands: North Holland Publishing; 1982:537–590.

*   [Vermeir D.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb1290) Semantic hierarchies and abstractions in conceptual schemata. *Inform. Syst.* 1983;8(2):117–124.

*   [Wintraecken J.](#Ch003_59-110_B9780443237904000037.xhtml#B-bb1320) *The NIAM Information Analysis Method: Theory and Practice.* Deventer, The Netherlands: Kluwer; 1990.

---

# 4 唯一性约束

## 摘要

本章讨论如何向 ORM 概念模式添加唯一性约束（UC）。内容涵盖一元、二元及更长事实类型的内部唯一性约束，以及事实类型之间的外部唯一性约束。随后展示如何检查事实类型是否为原子的。

### 关键词

ORM；唯一性约束；概念连接；元数检查；投影；连接

## 章节大纲

*   4.1 **CSDP 步骤 4 简介**
*   4.2 **一元和二元事实类型上的唯一性约束**
*   4.3 **较长事实类型上的唯一性约束**
*   4.4 **外部唯一性约束**
*   4.5 **元数检查**
*   4.6 **投影和连接**
*   4.7 **总结**

## 4.1 CSDP 步骤 4 简介

到目前为止，概念模式设计程序（CSDP）一直专注于指定基本事实类型，包括断言的和派生的。CSDP 的其余部分主要关注指定**约束**。约束适用于数据库，且为静态或动态。*静态约束*适用于数据库的每个单独状态，通常可在模式图上指定，如 CSDP 步骤 4-7 所述。示例包括唯一性、强制角色、集合比较、值、子类型、频率和环约束。*动态约束*限制状态间的转换，通常用其他方式表达（如状态图），并在步骤 7 中与其他约束一起考虑。在实践中，我们通常在转向模型的另一部分之前，捕获与正在讨论的事实类型相关的所有约束。

本章讨论**唯一性约束**（UC）。向事实类型添加 UC 后，会进行检查以查看该事实类型是否具有正确的元数或长度。有一个简单的唯一性检查，可表明某些类型的事实类型并非基本类型，因此应予以拆分。

静态约束常被描述为“事实类型上的约束”。更准确地说，*静态约束适用于数据库的每一种可能状态*。这里的“每种状态”是指“*每一个状态，单独考虑*”。因此，静态约束适用于事实类型的所有可能*实例集*。例如，给定事实类型 `Person(Surname) has Weight(kg:)`，让我们添加约束**每个** Person **至多有一个** Weight。两个状态的示例实例集如[图 4.1](#Ch004_111-158_B9780443237904000232.xhtml#f0010)所示。

![图 4.1 单独考虑每个状态时，每个人至多有一个体重。](images/B9780443237904000232/f04-01-9780443237904.jpg)

[图 4.1](#Ch004_111-158_B9780443237904000232.xhtml#B-f0010) 单独考虑每个状态时，每个人至多有一个体重。

在信息系统的生命周期内，数据库会经历一系列状态。在某一状态下，记录 Smith 体重 90 公斤，Jones 体重 100 公斤（[图 4.1](#Ch004_111-158_B9780443237904000232.xhtml#f0010)(a)）。在稍后的状态下，Smith 体重不变，但 Jones 通过锻炼或节食减轻了体重（[图 4.1](#Ch004_111-158_B9780443237904000232.xhtml#f0010)(b)）。随着时间的推移，Jones 有不同的体重，但在每个数据库状态中，Jones、Smith 或任何其他人的当前体重至多只记录一个。

这就是如何解释静态约束**每个** Person **至多有一个** Weight。诸如 Person has Weight 之类的事实类型是“快照事实类型”——每个实例适用于数据库的单个状态或快照。记录历史的一种方法是使用带有时间引用的“历史事实类型”，例如，Person had Weight on Date（人在日期拥有体重）。

