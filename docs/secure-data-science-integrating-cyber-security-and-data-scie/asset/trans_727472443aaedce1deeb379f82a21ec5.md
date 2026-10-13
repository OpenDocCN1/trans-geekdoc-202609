

每个 AT 允许访问一组三元组。我们将此集合称为 AT 的 `result set`（结果集）。代理可访问的三元组集合是该代理 AT 列表中所有 AT 的结果集的并集。形式上，如果 `Y[1], Y[2], …, Y[n]` 分别是代理 AT 列表中 `AT[1], AT[2], …, AT[n]` 的结果集，则该代理可访问集合 `Y[1] ∪ Y[2] ∪ … ∪ Y[n]` 中的三元组。

### 15.7.2.2 安全级别默认值

通过为系统中的数据保守地选择默认安全级别，可以大大简化管理员的 AT 分配负担。在我们的实现中，数据存储中的所有项目都具有默认安全级别。个人的个人信息默认通过拒绝访问任何数据类型为 `Person` 的 URI 来保持私密。这防止了代理对其未被授予显式权限的任何个人进行推断。然而，如果代理被授予对特定类型或属性的显式访问权限，则该代理也将被授予该类型或属性的子类型或子属性的默认访问权限。

举个例子，考虑一个列出个人喜好元素的谓词文件 `Likes`。进一步假设 `Jim` 是一个喜欢 `Flying`、`SemanticWeb` 和 `Jenny` 的人，它们分别是类型为 `Hobby`、`ResearchInterest` 和 `Person` 的 URI，而 1 是一个具有 ATTs `⟨1, Subject, URI, Jim⟩` 和 `⟨1, Likes, Predicate, _⟩` 的 AT。默认情况下，仅拥有 AT 1 的代理 `Ben` 无法得知 `Jenny` 在 `Jim` 的 `Likes` 列表中，因为 `Jenny` 的数据类型是 `Person`。然而，如果 `Ben` 还拥有由 ATT `⟨2, Object, URI, Jenny⟩` 描述的 AT 2，那么 `Ben` 将能够看到 `Jim` 的 `Likes` 列表中的 `Jenny`。

### 15.7.3 冲突

当满足以下三个条件时会产生冲突：(1) 代理拥有两个 AT 1 和 2，(2) AT 2 的结果集是 AT 1 的真子集，(3) AT 1 的时间戳早于 AT 2 的时间戳。在这种情况下，后者（更具体的 AT）取代前者，因此 AT 1 将从 AT 列表中丢弃以解决冲突。此类冲突有两种类型，我们称之为 `subset conflicts`（子集冲突）和 `subtype conflicts`（子类型冲突）。

当 AT 2 是细化 AT 1 的 ATTs 的合取时，会发生子集冲突。例如，假设 AT 1 由 ATT `⟨1, Subject, URI, Sam⟩` 定义，而 AT 2 由 ATTs `⟨2, Subject, URI, Sam⟩` 和 `⟨2, Predicate, Has Accounts, _⟩` 定义。在这种情况下，AT 2 的结果集是 AT 1 结果集的子集。因此，如果拥有 AT 1 的代理稍后被分配了 AT 2，将会发生冲突。当这种情况发生时，AT 1 将从代理的 AT 列表中丢弃以解决冲突。

当 AT 2 中的 ATTs 涉及的数据类型是 AT 1 中数据类型的子类型时，会发生子类型冲突。这些数据类型可以是主语、宾语或两者的类型。

冲突解决由[算法 15.2](#ch15.xhtml#alg15_2)总结。此处，`Subset(AT[1], AT[2])` 是一个函数，如果 `AT[1]` 的结果集是 `AT[2]` 结果集的真子集，则返回 true；`SubjectSubType(AT[1], AT[2])` 如果 `AT[1]` 的主语是 `AT[2]` 主语的子类型，则返回 true。类似地，`ObjectSubType(AT[1], AT[2])` 用于判断宾语而非主语的子类型关系。

### 15.7.4 基于 XACML 的访问控制

基于 XACML 的访问控制基于 ABAC（基于属性的访问控制模型）。XACML 由四个主要模块组成：PEP（策略执行点）、PDP（策略决策点）、PIP（策略信息点）和 PAP（策略访问点/策略管理点）。

在 ABAC 模型中，用户提供其凭据并向资源发起请求。XACML 的 PEP 接收请求和凭据，并请求 PDP 决定是否应授予用户访问权限。PDP 与 PAP 协作获取策略，与 PIP 协作获取关于资源以及用户凭据的信息。基于策略，用户被授予或拒绝对资源的访问。决策由 PDP 做出并将结果返回给 PEP。然后 PEP 执行请求或拒绝请求。更多详细信息请参阅 [[THUR2013](#ch15.xhtml#ref15_48)]。

## 15.8 总结与展望

我们提出了一个能够处理海量 RDF 数据的框架，可用于表示社交网络等大数据系统。由于我们的框架基于 Hadoop（一个分布式且高度容错的系统），它自动继承了这两个特性。该框架具有高度可扩展性。要增加系统容量，只需向 Hadoop 集群添加新节点即可。我们提出了一种存储 RDF 数据的模式、一种确定查询处理计划的算法（其最坏情况有界），用于回答 SPARQL 查询，以及一种供该算法使用的简化成本模型。我们的实验表明，该系统具有高度可扩展性。如果增加数据量，回答查询引入的延迟不会成比例地增加。结果表明，对于非常大的数据集（超过十亿三元组），如果查询包含低选择性连接或大量推理，Hadoop RDF 更可取且更高效。如果查询包含产生高选择性的绑定对象，其他解决方案可能更高效。我们还概述了构建在查询处理系统之上的安全模型。

未来，我们希望在多个方向上扩展这项工作。首先，我们将研究更复杂的查询模型。我们将缓存最频繁查询的统计信息，并利用动态规划来挖掘这些统计信息。其次，我们将评估用户可指定的 Hadoop 作业唯一参数——Reducer 的数量对查询运行时间的影响。第三，我们将研究索引机会和二进制格式的进一步用法。第四，我们将处理更复杂的 SPARQL 模式，例如包含 OPTIONAL 块的查询。第五，我们将用现实的大数据应用（如社交网络系统）来演示我们的系统。最后，我们将在系统的所有层面融入安全性。也就是说，安全性不应只是查询处理原型的附加组件，而必须内置于 SPARQL 查询优化器中。

## 参考文献

*   [ABAD2007] [D.J. Abadi](#ch15.xhtml#Cref15_1), A. Marcus, S. R. Madden, K. Hollenbach, Scalable Semantic Web Data Management Using Vertical Partitioning, *Proceedings of 33rd Interntional Conference on Very Large Data Bases*, Vienna, Austria, 2007.

*   [ABAD2009a] D.J. Abadi, Data Management in the Cloud: Limitations and Opportunities, IEEE Data Engineering Bulletin, Volume 32, #1, 2009, 3–12.

*   [ABAD2009b] [D.J. Abadi](#ch15.xhtml#Cref15_3), A. Marcus, S.R. Madden, K. Hollenbach, SW- Store: A Vertically Partitioned DBMS for Semantic Web Data Management, VLDB Journal, Volume 18, # 2, 2009, 385–406.

*   [ABOU2009] A. Abouzeid, K. Bajda-Pawlikowski, D.J. Abadi, A. Silberschatz, A. Rasin, HadoopDB: An Architectural Hybrid of MapReduce and DBMS Technologies for Analytical Workloads, Proceedings of VLDB Endowment, Volume 2, 2009, 922–933.

*   [ATRE2008] [M. Atre](#ch15.xhtml#Cref15_5), J. Srinivasan, J. A. Hendler, BitMat: A Main-Memory Bit Matrix of RDF Triples for Conjunctive Triple Pattern Queries, *Proceedings of International Semantic Web Conference*, Karlsruhe, Germany, 2008.

