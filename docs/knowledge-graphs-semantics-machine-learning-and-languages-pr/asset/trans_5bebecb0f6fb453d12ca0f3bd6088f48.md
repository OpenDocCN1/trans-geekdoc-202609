

![](img/5368dd329bd72fa0bf97ac91d6cef632_104_0.png)

**图 1.** 在第一种配置下，系统相对于其 pAvgQPS 的性能。黑色线条表示在预热运行中报告的值。

![](img/5368dd329bd72fa0bf97ac91d6cef632_104_1.png)

**图 2.** 在第一种配置下，系统相对于其 QPS 的性能。

![](img/5368dd329bd72fa0bf97ac91d6cef632_104_2.png)

**图 3.** 在第二种配置下，系统相对于其 pAvgQPS 的可扩展性。

|  | Neo4jC | Neo4jGQL | TentrisGQLBase | TentrisGQL |
|---|---:|---:|---:|---:|
| LinGBM100 | 230.32 | 91.51 | 366.27 | 524.90 |
| LinGBM500 | 72.13 | 33.72 | 164.23 | 229.90 |
| LinGBM1000 | 43.99 | 20.11 | 124.59 | 169.79 |

**表 3.** Neo4jGQL 中结果重写的开销（pAvgQPS）。

我们将所有基准测试的超时时间设置为三分钟，并使用每秒执行的查询数（QPS）和惩罚平均 QPS（pAvgQPS）来衡量我们实现的性能；失败查询（例如超时查询）的惩罚设置为三分钟。最后，我们比较了所有系统生成的结果，以确保它们在所有查询中返回相同的结果。

## 4.4. 结果

第一种基准测试配置的结果如图 1 和图 2 所示。图 1 表明，在所有数据集的所有查询模板中，TentrisGQL 和 TentrisGQLBase 均优于 Neo4jC，其中在最大的数据集 LinGBM1000 上，TentrisGQL 的 pAvgQPS 比 Neo4jC 高 1.5 倍（QT2 和 QT13）至 7.4 倍（QT3）。此外，在所有数据集中，TentrisGQL 和 TentrisGQLBase 的 QPS 中位数均高于 Neo4jC（图 2）。

图 3 总结了第二种基准测试配置的结果。我们从第二种配置的查询列表中移除了对应于 QT5 的查询实例，因为当多个客户端发出该查询时，Neo4j 的 JVM 内存会耗尽。TentrisGQL 和 TentrisGQLBase 没有遇到任何与内存相关的问题。图 3 显示，在最小的数据集（即 LinGBM100）中，当有 4 个和 8 个并发客户端查询时，Neo4jC 的可扩展性优于 TentrisGQL 和 TentrisGQLBase。然而，在所有情况下，TentrisGQL 和 TentrisGQLBase 都实现了比 Neo4jC 更高的 pAvgQPS，特别是在 LinGBM1000 中有 16 个客户端的情况下，TentrisGQL 的 pAvgQPS 比 Neo4jC 高 3.5 倍。

为了测量将 Neo4j 的结果重写为 GraphQL 响应所带来的开销，我们使用了只有一个并发用户的第二种基准测试配置。表 3 显示，重写过程使 TentrisGQL 的 pAvgQPS 比 Neo4jGQL 高出最多 8.4 倍。

## 4.5. 讨论

系统在所有数据集上的性能没有显著变化。特别是，系统的性能没有受到数据集规模增大的显著影响。系统的性能主要受查询模板的平均结果大小（aRS）影响（表 2）。具体而言，所有系统在所有数据集中的最高和最低 pAvgQPS 分别出现在 QT3 和 QT5 中。QT3 的 aRS 最低，而 QT5 的 aRS 最高。查询模板的深度也会影响系统的性能。例如，系统在 QT6 中的 pAvgQPS 低于 QT7，尽管后者的 aRS 更高。深度值更高的查询在 TentrisGQL 中需要更多的左连接操作，在 Neo4j 中则需要更长的路径遍历。

影响我们 GraphQL 服务性能的另一个因素是与叶字段对应的操作数的大小，这些叶字段通过左连接操作求值。这一观察基于 TentrisGQLBase 的性能（图 1），其性能始终与 TentrisGQL 相当或更差。回顾一下，与 TentrisGQL 不同，TentrisGQLBase 分别通过左连接和连接操作来求值叶字段和 ID 类型的参数。Neo4j 采用属性图模型，这使它能够将叶字段表示为节点属性。因此，在求值叶字段时，Neo4j 不需要遍历特定属性键的所有属性。尽管存在这些额外操作，TentrisGQL 和 TentrisGQLBase 的性能仍然优于 Neo4j。这表明我们的算法没有给计算带来太多开销。

表 3 的结果与文献 [18] 中报告的结果一致，并证明了 GraphQL 服务能够直接构建 GraphQL 响应的重要性。关于内存使用情况，我们使用 pmap10 测量了在 LinGBM1000 上由 16 个并发客户端查询时系统所使用的内存。TentrisGQL 和 Neo4jC 报告的最高常驻内存集大小（RSS）分别为 41 GB 和 44 GB。

## 5. 相关工作

最近，一些图存储解决方案已做出努力，允许用户通过 GraphQL 访问其数据。Dgraph [16] 是一个分布式图数据库，原生支持 GraphQL。它还提供自己的查询语言，即 DQL。在 Dgraph 中，GraphQL 操作会被转换为 DQL 操作。然而，响应对象是按照 GraphQL 规范构建的。因此，不需要对结果进行重写。

我们没有将 Dgraph 纳入实验，原因有二。首先，Dgraph 不完全支持 RDF，因为它无法处理 URI。此外，Dgraph 的 GraphQL 服务要求谓词以其主语类型作为前缀。因此，现有的 RDF 图需要经过大量修改才能存储到 Dgraph 实例中。其次，Dgraph 没有为其 GraphQL 服务提供批量加载器；因此，它无法高效地加载大型知识图谱。[^11]

除了第 4 节中使用的转换工具外，Neo4j 还提供了一个库，作为应用程序和数据库实例之间的中间件。该库[^12]负责将 GraphQL 查询转换为 Cypher 查询。对于三元组存储，Stardog [37] 和 GraphDB [9] 的商业版通过将 GraphQL 转换为 SPARQL 来提供 GraphQL 支持。Virtuoso [8] 引入了一个 GraphQL 插件[^13]，允许其用户通过 GraphQL 查询 RDF 图。为了弥合 GraphQL 与 SPARQL 之间的差距，该插件依赖 OWL 本体将 GraphQL 模式中的类型和字段映射到 RDF 术语。我们没有将 Virtuoso 纳入实验，因为它在内部字段中不执行类型过滤，这会导致查询返回不正确的结果。[^14]

## 6. 结论与未来工作

我们提出了一种在 RDF 图上原生求值 GraphQL 查询的方法。由于 GraphQL 查询需要左连接操作，我们专注于开发一种新颖的相互左连接算法，该算法受最坏情况最优多路连接算法的启发。与最坏情况最优多路连接算法类似，所提出的左连接算法在逐变量的基础上递归地求值查询，从而允许对 GraphQL 查询进行增量枚举。通过在我们基于张量的三元组存储 Tentris 中实现我们的方法，我们提供了第一个公有可用的、将 GraphQL 视为一等公民的三元组存储。对我们实现的性能评估证明了左连接算法的效率，因为我们的实现优于最先进的图数据库，即 Neo4j。

我们当前的实现支持该语言形式语义（式 1）所要求的特性。我们未来的工作将重点扩展我们的 GraphQL 服务，使其包含规范中的所有特性。据我们所知，目前还没有工作关注在逐变量基础上求值需要左连接操作的 SPARQL 查询。为此，我们计划使用我们的方法来求值此类 SPARQL 查询（即包含可选图模式的查询）。

[^11]: https://discuss.dgraph.io/t/graphql-vs-dql-dgraph-blog/14311；参见“When not to use GraphQL”段落。

[^12]: https://neo4j.com/docs/graphql-manual/current/

[^13]: https://community.openlinksw.com/t/introducing-native-graphql-support-in-virtuoso/3378

[^14]: https://github.com/openlink/virtuoso-opensource/issues/1115

