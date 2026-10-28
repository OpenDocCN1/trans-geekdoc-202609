
单例属性、RDF 具体化、命名图和 PaCE [17]。使用的数据集包括（带元知识和不带元知识）：SPARQL 性能基准测试（SP2Bench）、生物医学知识库（BKR）和 Gov-track。结果表明，LKG 优于这些方法：其生成的语句更少、图规模更小、避免了资源冗余，并且查询响应时间更快。

[12] 提出了一个基准测试（数据集和一组查询）来分析具体化模型。为了说明该基准测试的实用性，作者使用三种具体化模型在 Stardog 三元组存储上分析了查询性能、存储效率和可用性，这三种模型分别为：标准具体化、单例属性和 RDF-star。作者使用了生物医学知识库（BKR）数据集 20，以使他们的结果与 [8] 可比，后者将单例属性与标准具体化进行了比较。使用十二个查询来评估性能。其中五个查询是本研究为聚焦 SPARQL-star 而提出的。实验结果表明，单例属性似乎表现最差。这可能是因为唯一属性的数量众多，而且索引通常没有针对这一点进行优化。作者还观察到，对于简单查询，标准具体化的表现优于 RDF-star。对于复杂查询，RDF-star 明显优于标准具体化。

[18] 提出了一种表示元数据的新方法，该方法优于现有的具体化模型，如单例属性、命名图、PaCE、伴随属性、N 元关系、RDF-star 和 RDF-star [19]。作者在研究中使用多种数据集，包括 BKR 数据集、Gov-track 数据集、合成数据集以及从 [20] 获取的数据集。通过实验，所提出的方法在处理多维和嵌套元数据方面展现出优势，同时减少了图规模并生成了更少的语句。

## 6. 结论

本文介绍了教育资源（ER）知识图谱（KG）的生成流程，以及使用多个三元组存储库对几种具体化模型的评估。目标是确定最适合该知识图谱的方法。为实现这一目标，我们定义了七个查询模板，并实例化为 26 个具体查询。在知识图谱中，具体化被用于一个多值属性，以添加两个取值范围在 0 到 1 之间的注解。基于这项实验研究得出的见解，我们能够得出有意义的结论。标准具体化和 Virtuoso 上的命名图表现出相似的性能。在某些情况下，特别是连接查询中，命名图显示出轻微的优势。如果 RDF 1.2 中包含引用三元组，RDF-star 应得到更高效的实现。最后，对于本文介绍的知识图谱，采用带有命名图的 Virtuoso 是一个不错的选择。

## 致谢

本工作获得了法国政府在“投资未来”计划下通过国家研究机构授予 Labex Cominlabs 卓越实验室的支持，编号为 ANR-10-LABX-07-01。作者感谢南特大学计算机科学专业的硕士研究生们参与本工作的某些方面。

## 参考文献

- [1] Mihalcea R, Csomai A. Wikify！将文档链接到百科知识。见：Conference on Information and Knowledge Management (CIKM)；2007. doi:10.1145/1321440.1321475.
- [2] Brank J, Leban G, Grobelnik M. 基于维基百科概念的文档语义标注. Informatica. 2018;42(1):23-32.
- [3] Alexander K, Cyganiak R, Hausenblas M, Zhao J. 描述关联数据集。见：Workshop on Linked Data on the Web (LDOW)；2009. .
- [4] Albertoni R, Browning D, Cox S, Gonzalez-Beltran A, Perego A, Winstanley P, 等. 数据目录词汇表（DCAT）版本 2；2020. 取自：https://www.w3.org/TR/vocab-dcat-2/.
- [5] Delva T, Arenas-Guerrero J, Iglesias-Molina A, Corcho O, Chaves-Fraga D, Dimou A. RML-star：用于 RDF-star 生成的声明式映射语言。见：International Semantic Web Conference (ISWC) Posters, Demos and Industry tracks；2021. p. 5.
- [6] Manola F, Miller E, McBride B, 等. RDF 入门. W3C 推荐标准. 2004. 取自：https://www.w3.org/TR/rdf-primer/.
- [7] Carroll JJ, Bizer C, Hayes P, Stickler P. 命名图. Journal of Web Semantics. 2005;3(4):247-67. doi:10.1016/j.websem.2005.09.001.
- [8] Nguyen V, Bodenreider O, Sheth A. 不喜欢 RDF 具体化？使用单例属性对语句进行陈述。见：International World Wide Web Conference (WWW)；2014. p. 759-70. doi:10.1145/2566486.2567973.
- [9] Hartig O. RDF\* 和 SPARQL\* 的基础（RDF 中语句级元数据的替代方法）。见：International Workshop on Foundations of Data Management and the Web (AMW)；2017. .
- [10] Dimou A, Vander Sande M, Colpaert P, Verborgh R, Mannens E, Van de Walle R. RML：一种用于异构数据集成 RDF 映射的通用语言. Workshop on Linked Data on the Web (LDOW). 2014;1184.
- [11] Arenas-Guerrero J, Iglesias-Molina A, Chaves-Fraga D, Garijo D, Corcho O, Dimou A. Morph-KGC star：从异构数据声明式生成 RDF-star 图；2022.
- [12] Orlandi F, Graux D, O'Sullivan D. 对 RDF 元数据表示进行基准测试：具体化、单例属性和 RDF-star。见：International Conference on Semantic Computing (ICSC)；2021. p. 233-40. doi:10.1109/ICSC50631.2021.00049.
- [13] Hernández D, Hogan A, Krötzsch M. 具体化 RDF：什么在 Wikidata 上效果良好？International Workshop on Scalable Semantic Web Knowledge Systems (SSWS). 2015;1457:32-47.
- [14] Frey J, Müller K, Hellmann S, Rahm E, Vidal ME. RDF 存储库中元数据表示的评估. Semantic Web Journal (SWJ). 2017;10:205—229. doi:10.3233/SW-180307.
- [15] Orlandi F, Graux D, O'Sullivan D. 你能在这个星座中看到多少颗星星？见：European Semantic Web Conference (ESWC) poster demo；2020. p. 175-80. doi:10.1007/978-3-030-62327-2_30.
- [16] Sen S, Malta MC, Katoriya D, Dutta B, Dutta A. 数据网络中用于语句标注的标记 k 部图. 见：2020 IEEE/WIC/ACM International Joint Conference on Web Intelligence and Intelligent Agent Technology (WI-IAT). IEEE；2020. p. 63-71. doi:10.1109/WIIAT50758.2020.00014.
- [17] Sahoo SS, Bodenreider O, Hitzler P, Sheth A, Thirunarayan K. 来源上下文实体（PaCE）：面向科学 RDF 数据的可扩展来源追踪. 见：Scientific and Statistical Database Management: 22nd International Conference, SSDBM 2010, Heidelberg, Germany, June 30–July 2, 2010. Proceedings 22. Springer；2010. p. 461-70. doi:10.1007/978-3-642-13818-8_32.
- [18] Sen S, Katoriya D, Dutta A, Dutta B. RDFM：在数据网络中表示、存储和维护元知识的替代方法. Expert Systems with Applications. 2021;179:115043. doi:10.1016/j.eswa.2021.115043.
- [19] Schueler B, Sizov S, Staab S, Tran DT. 查询元知识. 见：Proceedings of the 17th international conference on World Wide Web；2008. p. 625-34. doi:10.1145/1367497.1367582.
- [20] Fu G, Bolton E, Rosinach NQ, Furlong LI, Nguyen V, Sheth A, 等. 使用不同 RDF 模型公开来源元数据. arXiv 预印本 arXiv:1509.02822. 2015. doi:10.48550/arXiv.1509.02822.

## BiPaSs：Wikidata 中快速路径查找的进一步研究

Leon MARTIN a,1

a 班贝格大学媒体信息学系，An der Weberei 5, 96047 Bamberg。
ORCiD ID：Leon Martin https://orcid.org/0000-0002-6747-5524

摘要. 目的：先前的一篇论文提出了一种双向 A\* 搜索算法，利用实体之间的语义距离作为搜索启发式的一部分，在 Wikidata 中快速查找有意义的路径。然而，该工作尚存在若干不足，包括缺乏对算法超参数的优化以及缺乏在大型数据集上的评估。本文的目的在于解决这些有待解决的问题。方法：讨论了旨在提高语义距离准确性的方法。此外，还探讨了为 Wikidata 路径查找构建双实体查询数据集的不同方案。使用编译数据集的 20% 通过 Simple 优化器对算法的超参数进行微调。随后，利用剩余 80% 的数据集，将优化后的配置与包括基线在内的其他配置进行了对比评估。发现：额外考虑实体描述提高了语义距离的准确性。从 TREC 2007 Million Query Track 数据集中派生出一个包含 1,196 个实体对的双实体查询数据集。优化得到的超参数值为 0.699/0.109/0.823。该配置以较少的实体访问次数（平均 24.7 次）和适中的路径长度（平均 4.4 条）实现了更高的测试集覆盖率（79.2%）。为了可复现性，提供了名为 BiPaSs 的实现、查询数据集和基准测试结果。价值：网络搜索引擎只有针对提及单个实体的查询，才能可靠地生成包含摘要信息的知识面板。本文表明，在 Wikidata 中快速查找未见过的实体之间的路径是可行的。基于这些路径，可以为双实体查询生成知识面板，解释所提及实体之间的关系，从而有可能满足用户的信息需求。

关键词. 知识图谱，路径查找，超参数优化，Wikidata

## 1. 引言

为了更快地满足用户的信息需求，Google²、Bing³ 和 Startpage⁴ 等现代网络搜索引擎的结果页面，除了标准搜索结果排序外，还提供了各种组件。一个突出的例子是知识面板，它通常位于结果页面的右上角。这些
