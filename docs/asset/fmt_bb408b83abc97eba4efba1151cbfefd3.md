
*   **Google Big Query**：`Big Query` 本质上是一个管理 PB 级数据的数据仓库。它运行在 `Google` 的基础设施上，可以极快地处理 SQL 查询或进行分析。

*   **NoSQL 数据库**：`NoSQL database` 本质上是指非关系型数据库设计或面向 Web 的可扩展性的通用术语。它被称为非关系型高性能数据库。`NoSQL` 数据库的数据模型可能包括图、文档结构和键值对。一些流行的 `NoSQL` 数据库包括 `MongoDB` 和 `HBase`。

图 17.5 展示了我们可扩展安全社交媒体系统的架构。在这里，大数据管理工具托管在基础设施工具之上。大数据管理工具增强了推理引擎。这些推理引擎本质上实现了各种机器学习算法，包括深度学习算法以及聚类算法。这些算法将检查策略、了解数据，然后提取模式并进行预测。如果模式和预测不是用户被授权查看的内容，则不会提供给用户。更多详情见[[THUR2020]](#ch17.xhtml#ref17_14)。

![图 17.5 可扩展安全社交媒体系统。](img/fig17_5.jpg)

图 17.5 可扩展安全社交媒体系统。

## 17.11 总结与展望

在本章中，我们提出了一种基于语义 Web 工具的可扩展细粒度在线社交网络访问控制模型。此外，我们提出了使用 `OWL` 和 `SWRL` 建模的授权、管理和过滤策略。支持该模型的框架架构也已呈现。我们还描述了基于语义 Web 工具的可扩展细粒度在线社交网络访问控制模型的实现。特别是，我们讨论了使用 `OWL` 和 `SWRL` 建模的授权、管理和过滤策略的实现。也就是说，我们讨论了 第 19 章 中描述的框架的一个版本的实现，并展示了使用该方案评估访问控制所需时间长度的实验结果。进一步的工作可在确定一组最小访问策略方面开展，以便在评估访问请求时使用，从而进一步提高这些请求的效率。

我们打算向几个方向扩展这项工作。第一个方向源于这样一个事实：支持灵活的管理策略可能会使系统进入一种场景，即由不同用户指定的多个访问控制策略可应用于同一资源。确实，在我们的框架中，根据所支持的本体，社交网络的资源可能与不同的用户相关联。例如，给定的一张照片可能关联到所有者（例如 Bob），以及所有被标记的用户（例如 Alice 和 Carl）。根据管理策略的语义，这些被标记的用户中的某些用户可能被授权为该资源指定访问控制策略（例如仅 Alice）。例如，Alice 可能指定标记给她的照片只能由她的直接好友访问，而 Bob 可能指定他的照片必须由他的直接好友和同事访问。为了实施访问控制，框架必须决定如何将指定的访问控制策略组合在一起。因此，所提议框架的一个重要扩展将是支持多种策略集成策略。作为另一项重要的未来工作，我们计划利用本章讨论的思路实现我们的框架，并测试基于前向链接和后向链接推理的各种组合方式在不同场景下的效率。

此外，我们已经表明，现有的社交网络需要某种形式的合理数据分区，以使其访问控制的语义推理在速度和内存需求方面保持合理，这是由于执行推理的可用内存受限。此外，进一步的工作可用于确定在社交网络中表示个人信息的最佳方法，以判断混合语义/关系方法还是纯方法能提供最佳的整体系统。

## 参考文献

*   `[ALI2007]` B. Ali, W. Villegas, M. Maheswaran, A Trust Based Approach for Protecting User Data in Social Networks, *2007 Conference of the Center for Advanced Studies on Collaborative research (CASCON’07)*, 2007, pp. 288–293.

*   `[BERT2007]` S. Berteau, Facebook's misrepresentation of Beacon's Threat to Privacy: Tracking Users Who Opt Out or Are Not Logged. CA Security Advisor Research Blog, March 2007. Available at: [`community.ca.com/blogs/securityadvisor/archive/2007/11/29/facebook-s-misrepresentation-of-beacon-s-threat-to-privacy-tracking-users-who-opt-out-or-are-not-logged-in.aspx`](http://community.ca.com).

*   `[BRIC2007]` D. Brickley, L. Miller, FOAF Vocabulary Specification 0.91, RDF Vocabulary Specification, November 2007. Available at [`xmlns.com/foaf/0.1`](http://xmlns.com).

*   `[CARM2008]` B. Carminati, E. Ferrari, A. Perego, Security and Privacy in Social Networks, volume VII of Encyclopedia of Information Science and Technology, IGI Publishing, 2nd edition, 2008, pp. 3369–3376.

*   `[CARM2009a]` B. Carminati, E. Ferrari, R. Heatherly, M. Kantarcioglu, B.M. Thuraisingham, A Semantic Web Based Framework for Social Network Access Control, In B. Carminati and J. Joshi, editors, SACMAT, ACM, 2009, pp. 177–186.

*   `[CARM2009b]` B. Carminati, E. Ferrari, A. Perego, Enforcing Access Control in Web-based Social Networks, ACM Transactions on Information Systems Security, Volume 13, # 1, 2009, pp. 1–38.

*   `[CHOI2006]` H. Choi, S. R. Kruk, S. Grzonkowski, K. Stankiewicz, B. Davis, J. G. Breslin, Trust Models for Community Aware Identity Management, The Identity, Reference and Web Workshop (IRW2006) at the 15th International World Wide Web Conference (WWW2006), 2006.

*   `[CARM2011]` B. Carminati, E. Ferrari, R. Heatherly, M. Kantarcioglu, B. Thuraisingham, Semantic Web-based Social Network Access Control, Computers & Security, Volume 30, #2-3, 2011, pp. 108–115.

*   `[ELAH2008]` N. Elahi, M.M.R. Chowdhury, J. Noll, Semantic Access Control in Web Based Communities, *Computing in the Global Information Technology, 2008. ICCGI’08. The Third International Multi-Conference, Washington, DC, USA*, 2008, pp. 131–136.

*   `[FINI2008]` T. W. Finin, A. Joshi, L. Kagal, J. Niu, R.S. Sandhu, W.H. Winsborough, B.M. Thuraisingham, R. OWL BAC: Representing Role based Access Control in OWL, In I. Ray and N. Li, editors, SACMAT, ACM, 2008, pp. 73–82.

*   `[HORR2004]` I. Horrocks, P.F. Patel-Schneider, H. Boley, S. Tabet, B. Grosof, M. Dean, SWRL: A Semantic Web Rule Language Combining OWL and RuleML. W3C Member Submission, World Wide Web Consortium, May 2004. Available at: [`www.w3.org/Submission/SWRL`](http://www.w3.org).

*   `[KRUK2006]` S.R. Kruk, S. Grzonkowski, A. Gzella, T. Woroniecki, H. Choi, D-FOAF: Distributed Identity Management with Access Rights Delegation, In R. Mizoguchi, Z. Shi, and F. Giunchiglia, editors, ASWC, volume 4185 of Lecture Notes in Computer Science, Springer, 2006, pp. 140–154.

*   `[MIKA2007]` P. Mika, Social Networks and the Semantic Web, Springer, 2007.

*   `[THUR2020]` B. Thuraisingham, Multigenerational Database Inference Controllers, *IEEE Big Data Security Conference*, May 2020.

*   `[TONT2003]` G. Tonti, J.M. Bradshaw, R. Jeffers, R. Montanari, N. Suri, A. Uszok, Semantic Web Languages for Policy Representation and Reasoning: A Comparison of KAoS, rei, and ponder, In D. Fensel, K.P. Sycara, and J. Mylopoulos, editors, International Semantic Web Conference, volume 2870 of Lecture Notes in Computer Science, Springer, 2003, pp. 419–437.

*   `[WWW2006]` World Wide Web Consortium, Defining n-ary Relations on the Semantic Web, 2006, [`www.w3.org/TR/swbp-n-aryRelations/`](http://www.w3.org)

*   `[WWW1999]` World Wide Web Consortium, Status for Resource Description Framework (rdf) Model and Syntax Specification, 1999, [`www.w3.org/1999/.status/PR-rdf-syntax-19990105/status`](http://www.w3.org)

*   `[YAGU2005]` M.L. Yague, M.-del-M. Gallardo, A. Mana, Semantic Access Control Model: A Formal Specification, ESORICS: European Symposium on Research in Computer Security, LNCS, Springer-Verlag, 2005.

# 18 大数据的推理与访问控制

DOI: [10.1201/9781003081845-29](https://doi.org/10.1201/9781003081845-29)

## 18.1 简介

### 使用语义 Web 技术进行推理控制

推理是从前提形成结论的过程。如果用户从收到的合法响应中得出未经授权的结论，则该过程是有害的。这个问题被称为推理问题。推理控制器是防止用户得出未经授权结论的设备。我们过去曾广泛研究推理问题。具体而言，我们定义了各种类型的推理策略，并开发了处理某些类型推理策略的推理控制器 [THUR1993]。

关于构建推理控制器以保护数据机密性的早期工作描述于 20 世纪 80 年代末和 90 年代初 [THUR1987, THUR1993]；然而，这些工作主要集中在多级安全数据库领域，且支持的推理能力有限。通过使用语义 Web 技术，我们目前的工作在更复杂的推理和策略表示技术方面，较先前的工作有了实质性改进 [THUR2014]。我们使用 `资源描述框架 (RDF)` 作为数据模型，它支持具有不同数据模式的多数据库的互操作性。此外，我们使用语义 Web 规则和约束来表示策略和规则，并使用语义 Web 软件工具（如 `Pellet`、`Jena` 和 `Protégé`）对数据项及其之间的关系进行分类 [SIRI2007, CARR2004, KNUB2004]。

我们的工作重点在于对溯源数据进行分类和保护，溯源数据是一种元数据，它记录了感兴趣的单个数据项的来源，以及数据操纵操作和时间信息等其他相关信息 [THUR2014]。虽然可以使用任何数据格式来表示溯源，但有时使用有向图布局来可视化其结构会更容易。因此，我们将溯源数据称为有向图，因为有向图结构除了流行之外，在语义 Web 环境的数据建模方面还有许多优势。语义 Web 通过使用形式语义，扩展了 `RDF` 图数据模型，使其具备推理能力。在我们的工作中，我们利用语义 Web 的推理能力来支持推理控制器的推理策略。此外，我们还提出了几种新的查询修改（即重写）技术，可用于在溯源图上强制执行安全策略。

在本章中，我们将讨论采用围绕语义 Web 技术构建的推理策略和技术的推理控制，这些技术可用于社交媒体中的推理控制。我们的工作重点是针对表示为 `RDF` 图的溯源数据的推理控制。由于社交网络数据也可以建模为 `RDF` 图，因此我们的方法可适配于社交网络数据。我们还提供了推理控制器的详细实现。值得注意的是，访问控制是我们推理控制工作的核心。也就是说，我们不仅防止直接访问未经授权的数据，还防止通过推理间接访问未经授权的数据。

本章的组织结构如下。我们的设计见 18.2 节。查询修改见 18.3 节。我们的实现方法见 18.4 节。溯源方面见 18.5 节。实现细节见 18.6 节。生成器中的概念见 18.7 节。医疗示例见 18.8 节。约束见 18.9 节。下一代推理控制器见 18.10 节。18.11 节总结了本章。图 18.1 描述了推理控制器的架构。

![图 18.1 推理控制器架构。](img/fig18_1.jpg)

图 18.1 推理控制器架构。

## 18.2 推理控制器的设计

### 18.2.1 架构

推理问题的不可解性已在 [THUR1990] 中得到证明。其复杂性仍是一个开放问题。虽然有必要分析推理问题的复杂性类，但大量研究仍围绕基于传统数据库的实现展开。然而，由于溯源具有逻辑图结构，它也可以用图数据模型表示和存储；因此，它不局限于任何特定的数据格式。尽管我们在该设计中的重点是构建基于溯源图表示的推理控制器，但我们的推理控制器也可用于保护传统数据库的情况。此外，使用 `RDF` 数据模型不会给我们的实现带来过多限制，因为其他数据格式均可由 `RDF` 数据模型良好支持。此外，[BIZE2003] 中讨论的工具等可将关系数据转换为 `RDF` 数据。

我们的架构接收用户的输入查询，并返回一组经过用户定义的策略约束修剪后的响应。我们假设用户可以与我们的系统交互以获取传统数据和溯源数据。然而，由于我们的重点是保护溯源，我们将更多地关注推理控制器和溯源数据层的设计。

在我们的设计中，我们假设可用信息分为两部分：实际数据和溯源。数据和溯源均表示为 `RDF` 图。读者应注意，我们不对实际信息的存储方式做任何假设。用户可能将数据和溯源存储在两个不同的三元组存储中，也可能存储在同一个存储中。用户应用程序可以提交查询以访问数据及其关联的溯源，反之亦然。图 18.2 展示了我们的设计以及基于溯源数据的推理控制器原型实现中的一些模块。我们现在介绍图 18.2 中的模块。

![图 18.2 系统模块。](img/fig18_2.jpg)

图 18.2 系统模块。

#### 18.2.1.1 用户界面管理器

用户界面管理器负责处理用户请求、认证用户并向用户提供合适的响应。界面管理器还提供了一个抽象层，允许用户与系统交互。因此，用户可以向该层提交数据查询或溯源查询。用户界面管理器还确定查询应针对传统数据还是溯源数据进行评估。

#### 18.2.1.2 策略管理器

策略管理器负责确保查询用户有权使用系统。它根据用户的查询和相关的查询结果评估策略，以确保不会向未经授权的用户发布机密信息。策略管理器可以针对传统数据或溯源数据强制执行策略。每种数据类型可能有自己的策略管理器；例如，传统数据的存储格式可能与溯源数据不同。因此，我们可能需要每个策略管理器的不同实现。

#### 18.2.1.3 推理引擎
