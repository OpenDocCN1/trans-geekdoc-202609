
在本章中，我们提出了一种基于语义 Web 工具的可扩展细粒度在线社交网络访问控制模型。此外，我们提出了使用 `OWL` 和 `SWRL` 建模的授权、管理和过滤策略。支持该模型的框架架构也已呈现。我们还描述了基于语义 Web 工具的可扩展细粒度在线社交网络访问控制模型的实现。特别是，我们讨论了使用 `OWL` 和 `SWRL` 建模的授权、管理和过滤策略的实现。也就是说，我们讨论了 [第 19 章](#ch19.xhtml#chapter19) 中描述的框架的一个版本的实现，并展示了使用该方案评估访问控制所需时间长度的实验结果。进一步的工作可在确定一组最小访问策略方面开展，以便在评估访问请求时使用，从而进一步提高这些请求的效率。

我们打算向几个方向扩展这项工作。第一个方向源于这样一个事实：支持灵活的管理策略可能会使系统进入一种场景，即由不同用户指定的多个访问控制策略可应用于同一资源。确实，在我们的框架中，根据所支持的本体，社交网络的资源可能与不同的用户相关联。例如，给定的一张照片可能关联到所有者（例如 Bob），以及所有被标记的用户（例如 Alice 和 Carl）。根据管理策略的语义，这些被标记的用户中的某些用户可能被授权为该资源指定访问控制策略（例如仅 Alice）。例如，Alice 可能指定标记给她的照片只能由她的直接好友访问，而 Bob 可能指定他的照片必须由他的直接好友和同事访问。为了实施访问控制，框架必须决定如何将指定的访问控制策略组合在一起。因此，所提议框架的一个重要扩展将是支持多种策略集成策略。作为另一项重要的未来工作，我们计划利用本章讨论的思路实现我们的框架，并测试基于前向链接和后向链接推理的各种组合方式在不同场景下的效率。

此外，我们已经表明，现有的社交网络需要某种形式的合理数据分区，以使其访问控制的语义推理在速度和内存需求方面保持合理，这是由于执行推理的可用内存受限。此外，进一步的工作可用于确定在社交网络中表示个人信息的最佳方法，以判断混合语义/关系方法还是纯方法能提供最佳的整体系统。

## 参考文献

*   `[ALI2007]` [B. Ali](#ch17.xhtml#Cref17_1), W. Villegas, M. Maheswaran, A Trust Based Approach for Protecting User Data in Social Networks, *2007 Conference of the Center for Advanced Studies on Collaborative research (CASCON’07)*, 2007, pp. 288–293.

*   `[BERT2007]` [S. Berteau](#ch17.xhtml#Cref17_2), Facebook's misrepresentation of Beacon's Threat to Privacy: Tracking Users Who Opt Out or Are Not Logged. CA Security Advisor Research Blog, March 2007. Available at: [http://community.ca.com/blogs/securityadvisor/archive/2007/11/29/facebook-s-misrepresentation-of-beacon-s-threat-to-privacy-tracking-users-who-opt-out-or-are-not-logged-in.aspx](http://community.ca.com).

*   `[BRIC2007]` [D. Brickley](#ch17.xhtml#Cref17_3), L. Miller, FOAF Vocabulary Specification 0.91, RDF Vocabulary Specification, November 2007. Available at [http://xmlns.com/foaf/0.1](http://xmlns.com).

*   `[CARM2008]` [B. Carminati](#ch17.xhtml#Cref17_4), E. Ferrari, A. Perego, Security and Privacy in Social Networks, volume VII of Encyclopedia of Information Science and Technology, IGI Publishing, 2nd edition, 2008, pp. 3369–3376.

*   `[CARM2009a]` B. Carminati, E. Ferrari, R. Heatherly, M. Kantarcioglu, B.M. Thuraisingham, A Semantic Web Based Framework for Social Network Access Control, In B. Carminati and J. Joshi, editors, SACMAT, ACM, 2009, pp. 177–186.

*   `[CARM2009b]` B. Carminati, E. Ferrari, A. Perego, Enforcing Access Control in Web-based Social Networks, ACM Transactions on Information Systems Security, Volume 13, # 1, 2009, pp. 1–38.

*   `[CHOI2006]` H. Choi, S. R. Kruk, S. Grzonkowski, K. Stankiewicz, B. Davis, J. G. Breslin, Trust Models for Community Aware Identity Management, The Identity, Reference and Web Workshop (IRW2006) at the 15th International World Wide Web Conference (WWW2006), 2006.

*   `[CARM2011]` [B. Carminati](#ch17.xhtml#Cref17_8), E. Ferrari, R. Heatherly, M. Kantarcioglu, B. Thuraisingham, Semantic Web-based Social Network Access Control, Computers & Security, Volume 30, #2-3, 2011, pp. 108–115.

*   `[ELAH2008]` [N. Elahi](#ch17.xhtml#Cref17_9), M.M.R. Chowdhury, J. Noll, Semantic Access Control in Web Based Communities, *Computing in the Global Information Technology, 2008. ICCGI’08. The Third International Multi-Conference, Washington, DC, USA*, 2008, pp. 131–136.

*   `[FINI2008]` [T. W. Finin](#ch17.xhtml#Cref17_10), A. Joshi, L. Kagal, J. Niu, R.S. Sandhu, W.H. Winsborough, B.M. Thuraisingham, R. OWL BAC: Representing Role based Access Control in OWL, In I. Ray and N. Li, editors, SACMAT, ACM, 2008, pp. 73–82.

*   `[HORR2004]` [I. Horrocks](#ch17.xhtml#Cref17_11), P.F. Patel-Schneider, H. Boley, S. Tabet, B. Grosof, M. Dean, SWRL: A Semantic Web Rule Language Combining OWL and RuleML. W3C Member Submission, World Wide Web Consortium, May 2004. Available at: [http://www.w3.org/Submission/SWRL](http://www.w3.org).

*   `[KRUK2006]` [S.R. Kruk](#ch17.xhtml#Cref17_12), S. Grzonkowski, A. Gzella, T. Woroniecki, H. Choi, D-FOAF: Distributed Identity Management with Access Rights Delegation, In R. Mizoguchi, Z. Shi, and F. Giunchiglia, editors, ASWC, volume 4185 of Lecture Notes in Computer Science, Springer, 2006, pp. 140–154.

*   `[MIKA2007]` [P. Mika](#ch17.xhtml#Cref17_13), Social Networks and the Semantic Web, Springer, 2007.

*   `[THUR2020]` [B. Thuraisingham](#ch17.xhtml#Cref17_14), Multigenerational Database Inference Controllers, *IEEE Big Data Security Conference*, May 2020.

*   `[TONT2003]` [G. Tonti](#ch17.xhtml#Cref17_15), J.M. Bradshaw, R. Jeffers, R. Montanari, N. Suri, A. Uszok, Semantic Web Languages for Policy Representation and Reasoning: A Comparison of KAoS, rei, and ponder, In D. Fensel, K.P. Sycara, and J. Mylopoulos, editors, International Semantic Web Conference, volume 2870 of Lecture Notes in Computer Science, Springer, 2003, pp. 419–437.

*   `[WWW2006]` [World Wide Web Consortium](#ch17.xhtml#Cref17_16), Defining n-ary Relations on the Semantic Web, 2006, [http://www.w3.org/TR/swbp-n-aryRelations/](http://www.w3.org)

*   `[WWW1999]` [World Wide Web Consortium](#ch17.xhtml#Cref17_17), Status for Resource Description Framework (rdf) Model and Syntax Specification, 1999, [http://www.w3.org/1999/.status/PR-rdf-syntax-19990105/status](http://www.w3.org)

*   `[YAGU2005]` [M.L. Yague](#ch17.xhtml#Cref17_18), M.-del-M. Gallardo, A. Mana, Semantic Access Control Model: A Formal Specification, ESORICS: European Symposium on Research in Computer Security, LNCS, Springer-Verlag, 2005.

# 18 大数据的推理与访问控制

DOI: [10.1201/9781003081845-29](https://doi.org/10.1201/9781003081845-29)

## 18.1 简介
