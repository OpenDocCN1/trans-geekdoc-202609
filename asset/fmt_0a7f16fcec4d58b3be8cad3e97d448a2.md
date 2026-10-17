
通过将概念模式视为样本数据库状态，可用 `CSDP` 开发概念**元模式**。`CASE` 工具可用它确保仅输入有效的概念模式。**元建模**活动，即对模型建模，也有助于澄清不同形式化方法间的关系并进行转换。

### 章节注释

数据仓库和 `OLAP` 文献丰富。Date (2000, Chapter 21) 提供了决策支持的清晰概览。Inmon (1993)、Kimball (1996) 和 Silverston (2001a,b) 提供了数据仓库的实用建议和示例。Jukik (2006) 提供了数据仓库建模替代策略的有用概览。数据清洗的 `gendercode` 示例由 Scot Becker 建议——谢谢 Scot！关于 `SQL Server 2022 MDX` 的详尽论述，见 [MDX Language Reference (MDX) - SQL Server | Microsoft Learn](https://learn.microsoft.com/en-us/sql/mdx/mdx-language-reference-mdx?view=sql-server-ver16)。关于微软 `OLAP` 架构的详细覆盖，见 [Logical Architecture (Analysis Services - Multidimensional Data) | Microsoft Learn](https://learn.microsoft.com/en-us/analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture?view=asallproducts-allversions)。

## 参考文献与延伸阅读

关于概念查询原型（如 `ERQL`、`Super`、`Hybris` 和 `CBQL`）的简要回顾，请参阅 Bloesch and Halpin (1997)。其他图形化数据库查询语言的综述见 Ozsoyoglu and Wang (1993)。若需了解多款 `SQL` 查询构建器的详细信息，可访问 [9 Best SQL Query Builder & Generator Tools (2023) (guru99.com)](https://www.guru99.com/best-sql-query-builders.html) 和 [www.activequerybuilder.com/](http://www.activequerybuilder.com/)。

`RIDL` 语言最初配合 Control Data 的 `IAST` 工具用于 `NIAM`，这是首个真正用于信息建模的 `CASE` 工具 (Meersman and Van Assche, 1983)。`RIDL` 语言的完整描述见 Meersman et al. (1984)；更多关于 `RIDL` 的讨论可参考 Meersman (1982) 和 Verheijen and van Bekkum (1982)。关于 `ConQuer` 的进一步讨论，请见 Bloesch and Halpin (1996、1997) 以及 Halpin (1998)。

关于 `ORM` 中模式抽象的更多细节，请参阅 Campbell and Halpin (1994a)、Campbell et al. (1996) 及其引用文献。从主要对象类型生成默认外部窗体的过程在 Campbell and Halpin (1993) 中有讨论。

McLeod (2000) 为在 `UML` 中扩展用例图和活动图提供了有益的建议。关于利用传统方式建模信息系统过程方面的实用建议，请见 Barker and Longman (1992) 以及 Barker (1990a、b)。整合数据与过程的几种有前景的方法分别由 Shoval and Kabeli (2000)、Halpin and Wagner (2003)、Dietz and Halpin (2003) 以及 Morgan (2007) 探讨。

关于 `HCI` 设计的大量讨论由 Shneiderman (1992) 和 Dix et al. (1993) 提供。Microsoft 产品和技术的大量文档可在 [`learn.microsoft.com/en-gb/docs/`](https://learn.microsoft.com/en-gb/docs/) 访问。在搜索字段中输入“user interface guidelines”可查找 Microsoft 推荐的 UI 指南。

`RDF`、`RDFS` 和 `OWL` 的规范可在 [www.w3.org](http://www.w3.org) 在线查阅。关于 `OWL 2`，请见 [`www.w3.org/TR/owl-overview/`](https://www.w3.org/TR/owl-overview/)。描述逻辑的标准参考书是 Baader et al. (2003)。关于将 `ORM` 映射到 `OWL` 和描述逻辑的讨论，请见 Keet (2007)。关于基于 `ORM` 的本体工具示例，请见 Trog et al. (2006)。我们关于本体建模和语义 Web 的讨论主要源自 Halpin 撰写的 15 部分系列文章（见 [www.orm.net/resources](http://www.orm.net/resources)）。该系列包含许多采用 Turtle 语法和 Manchester 语法的 `OWL` 示例。

关于 `ORM`、`Barker ER` 和 `UML` 元模型的比较，请见 Halpin (2004b)。`UML 2` 的元模型包含在可于 [`www.omg.org/spec/UML`](https://www.omg.org/spec/UML) 访问的在线 `UML` 规范中。点击最新版本的抽象语法章节，即可查看元模型各部分的图表。

## 参考文献

*   Baader et al., 2003 Baader F., Calvanese D., McGuinness D., Nardi D., Patel-Schneider P., eds. *The Description Logic Handbook.* Cambridge University Press; 2003.

*   Barker R. *CASE*Method: Entity Relationship Modelling.* Wokingham: Addison-Wesley; 1990.

*   Barker R. *CASE*Method: Tasks and Deliverables.* Wokingham: Addison-Wesley; 1990.

*   Barker R., Longman C. *CASE*Method: Function and Process Modelling.* Wokingham: Addison-Wesley; 1992.

*   Berners-Lee T., Hendler J., Lassila O. The semantic web. *Scientific Am.* 2001;2001.

*   Bloesch A., Halpin T. ConQuer: a conceptual query language. In: *Proc. ER’96: 15th Int. Conf. on Conceptual Modeling.* Springer LNCS 1157; 1996:121–133 *.

*   Bloesch A., Halpin T. Conceptual queries using ConQuer-II. In: *Proc. ER’97: 16th Int. Conf. on Conceptual Modeling.* Springer LNCS 1331; 1997:113–126 *.

*   Campbell L., Halpin T. Automated support for conceptual to external mapping. In: Brinkkemper S., Harmsen F., eds. *Proc. 4th Workshop on Next Generation CASE Tools.* Univ. Twente Memoranda Informatica 93-32; 1993:35–51.

*   Campbell L., Halpin T. Abstraction techniques for conceptual schemas. In: *Proc. 5th Australasian Database Conf., Christchurch (Jan.).* Singapore: World Scientific; 1994.

*   Campbell L., Halpin T., Proper H. Conceptual schemas with abstractions: making flat conceptual schemas more comprehensible. *Data Knowl. Eng.* 1996;20(1):39–85 *.

*   Cattell and Barry, 2000 Cattell R., Barry D., eds. *The Object Data Standard: ODMG 3.0.* San Francisco: Morgan Kaufmann; 2000.

*   Codd E., Codd S., Salley C. *Providing OLAP (On-line Analytical Processing) to User-Analysts: An IT Mandate.* Arbor Software Corporation; 1993. Accessible online at [www.arborsoft.com/essbase/wht_ppr/coddToc.html](http://www.arborsoft.com/essbase/wht_ppr/coddToc.html).

*   Date C. *An Introduction to Database Systems.* seventh ed. Reading MA: Addison-Wesley; . 2000;vol. 1.

*   Dietz J., Halpin T. *Combining DEMO and ORM—an investigation of mutual benefits.* In: Proc. EMMSAD’03: 8th IFIP WG8.1 Int. Workshop on Evaluation of Modeling Methods in Systems Analysis and Design, Velden, Austria (June); 2003.

*   Dix A., Finlay J., Abowd G., Beale R. *Human-Computer Interaction.* New York: Prentice Hall; 1993.

*   Embley D., Wu H., Pinkston J., Czejdo B. *OSM-QL: A Calculus-based Graphical Query Language.* Tech. Report Utah: Dept. of Comp. Science, Brigham Young Univ.; 1996.

*   Halpin T. Conceptual queries. In: Ross R., ed. *Database Newsletter.* Boston: Database Research Group, Inc; . 1998;vol. 26(2) (March/April 1998).*.

*   Halpin T. Comparing metamodels for ER, ORM and UML data models. In: Siau K., ed. *Advanced Topics in Database Research.* Hershey, PA: Idea Group; 23–44. 2004;vol. 3.

*   Halpin T., Wagner G. *Modeling reactive behavior in ORM.* In: Conceptual Modeling—ER2003, Proc. 22nd ER Conference, Chicago, October 2003; Springer LNCS; 2003.

*   Inmon W. *Building the Data Warehouse.* New York: John Wiley and Sons; 1993.

*   Jeyaraj A., Sauter V. An empirical investigation into the effectiveness of systems modeling and verification tools. *CACM.* 2007;50(6):63–67.

*   Jukik N. Modeling strategies and alternatives for data warehousing projects. *CACM.* 2006;49(4):83–88.

*   Keet C. *Mapping the Object-Role Modeling language ORM2 into Description Logic Language *DLR*[*ifd*].* KRDB Research Centre TR KRDB07-2 Italy: Faculty of Computer Science, Free University of Bozen-Bolzano; 2007.

*   Kimball R. *The Data Warehouse Toolkit.* New York: John Wiley and Sons; 1996.

*   McLeod G. *Beyond use cases.* In: Proc. EMMSAD’00: 5th IFIP WG8.1 Int. Workshop on Evaluation of Modeling Methods in Systems Analysis and Design, Kista, Sweden; 2000.

*   Meersman R. *The RIDL Conceptual Language.* Research Report Brussels: Int. Centre for Information Analysis Services, Control Data Belgium; 1982.

*   Meersman R., Van Assche F. Modeling and manipulating production databases in terms of semantic nets. In: *Proc. 8th IJCAI Conference.* Morgan Kaufmann; 1983.

*   Meersman R., De Troyer O., Ponsaert F. *The RIDL User Guide.* Brussels: Control Data Corp; 1984.

*   Moody D., Kortink M. From enterprise models to dimensional models: a methodology for data warehouse and data mart design. In: *Proc. DMDW’00: Int. Workshop on Design and Management of Data Warehouses, Report 25.* Zurich: Swiss Life IT RandD; 2000.

*   Morgan T. Business process modeling and ORM. In: Meersman R., Tari Z., Herrero P., et al., eds. *On the Move to Meaningful Internet Systems 2007: OTM 2007 Workshops.* Vilamoura: Springer LNCS 4805; 2007.

*   Ozsoyoglu G., Wang H. Example-based graphical database query languages. *Computer.* 1993;26(5):25–38.

*   Shneiderman B. *Designing the User Interface.* second ed. Reading, MA: Addison-Wesley; 1992.

*   Shoval P., Kabeli J. *Functional and object-oriented analysis and design of information systems—an integrated methodology.* In: Proc. EMMSAD’00: 5th IFIP WG8.1 Workshop on Evaluation of Modeling Methods in Systems Analysis and Design, Kista, Sweden; 2000.

*   Silverston L. *The Data Model Resource Book.* New York: John Wiley; . 2001;vol. 1.

*   Silverston L. *The Data Model Resource Book.* New York: John Wiley; . 2001;vol. 2.

*   ter Hofstede A., Proper H., van der Weide T. Query formulation as an information retrieval problem. *Comput. J.* 1996;39(4):255–274.
