

一个完整而优雅的结果。尽管我们的讨论局限于逻辑和概念级别，对应用程序进行重新工程化还涉及外部级（例如，修订用户界面）和物理级（例如，重新调优）的工作。

现在通过一个详细示例说明四个基本的重新工程化阶段。作为该过程的主要输入，图 14.78 显示了一个关系模式以及每个表的两行数据（为节省空间，右侧显示为元组）。

| 关系模式（部分约束缺失）： | 示例数据（无重要性） |
|---|---|
| Committee ({cteeCode, chairPerson, [budget] }) | ('Prog', 'Adams, Prof. A.B.', '?') |
| | ('Org', 'Bloggs, Dr F.', '10000') |
| Person ({ personName, affiliation, [email] }) | ('Adams, Prof. A.B.', 'MIT', '?') |
| | ('Pi, Dr Q.T.', 'UQ', 'pi@uq.au') |
| Rated ({ referee_paperNr, rating }) | ('Adams, Prof. A.B.', 43, 8) |
| | ('Pi, Dr Q.T.', 5, 4) |
| Referees ({ personName, paperNr }) | ('Adams, Prof. A.B.', 43) |
| | ('Knot, Prof. I.M.', 43) |
| Authored ({ personName, paperNr, paperTitle }) | ('Sea, Ms A.B.', 5, 'EER models') |
| | ('Pi, Dr Q.T.', 43, 'ORM dialects') |
| Presents ({ author_paperNr }) | ('Pi, Dr Q.T.', 43) |
| | ('Knot, Dr I.M.', 61) |
| Paper ({ paperNr, paperTitle, status }) | (5, 'EER models', 'undec') |
| | (43, 'ORM dialects', 'accept') |
| AcceptedPaper ({ paperNr, [pageLength] }) | (43, 14) |
| | (75, ?) |
| AcPaperDiags ({ paperNr, diagramKind, qty }) | (43, 'tbl', 3) |
| | (43, 'fig', 5) |
| PaperSlot ({ slotNr, stream_hr, [bldgNr, roomNr], [paperNr] }) | (1, 'A', 9, 69, '110', 43) |
| | (2, 'B', 9, 50, '110', ?) |
| Room ({ bldgNr, roomNr, roomType, area }) | (69, '110', 'lec', 100) |
| | (50, '110', 'lab', 120) |
| LabOrLecRm ({ bldgNr, roomNr, [nrPCs], [nrSeats] }) | (69, '110', ?, 350) |
| | (50, '110', 40, ?) |

图 14.78 原始数据库模式及部分示例数据。

假设这种设计用于记录关于一天计算机会议的详细信息，但其性能较差，主要是因为常见查询需要的表连接数量较多。

此外，应用程序开发人员认为架构的某些部分笨拙甚至不安全。例如，Committee 表中的 budget 列适用于整个委员会，而不适用于该委员会的特定主席（每个委员会最多有两位主席）。人们怀疑这并非表格中唯一的非规范化特征。

由于您在概念建模方面的专长，您受聘为该应用程序提供一个概念模型，以便能够清晰、完整地了解业务领域。此外，如果可能，您还被要求提供一个既规范化又高效的新关系设计。

在实践中，重新工程化通常需要与领域专家对话以澄清 UoD，特别是为了识别缺失的约束。为了帮助您尝试逆向工程阶段，图中描绘了唯一性、取值、互斥和频率约束。但是，省略了其他约束（例如，子集约束，以及由于反规范化导致的未隐含函数依赖）。有些缺失的约束是“显而易见”的，其他约束可以从下面的简要描述中识别出来。

另外，示例数据行使您能够应用 CSDP 第 1 步。这些行并未提供显著，甚至合法的数据填充（例如，如果数据库仅由这些数据组成，表之间的子集约束将被违反）。

缩写代码的含义如下：Prog = Programming；Org = Organizing；undec = undecided；tbl = table；fig = figure；lec = lecture；lab = laboratory。作者提交论文，随后将其发送给评审进行评分。确定哪些论文被接受的方法在此未建模。

可关于被接受的论文保留各种统计数据（页数、表数和图数），部分用于帮助出版会议论文集。如果为论文保留统计数据，则必须记录所有三个数字。

一篇被接受的论文可以在会议上由其一位或多位作者发表。哪些作者发表论文可能在论文被接受之前都不确定。会议议程包含最终分配给被接受论文的时段。每个时段为 1 小时。时间采用军用时间计量（例如，14 = 下午 2 点）。为了在同一天安排更多论文，可以并行运行两个流（A 和 B）（因此两个论文时段可能具有相同的时间）。

房间目录用于帮助将时段分配给房间；房间面积单位为平方米。只有讲堂或实验室可用于论文演示。座位数仅为讲堂记录，PC 数量仅为实验室记录。在偷看解决方案之前，请尝试为该应用程序提供一个概念架构。包括所有约束（包括原始关系模式中缺失的约束）。在此过程中，将显而易见一些表存在冗余问题。这些表是哪些？

将您的解决方案与图 14.79 中提供的解决方案进行比较。如果您掌握了所有约束，可以为自己鼓掌庆贺。

![](img/1344db3eba3d550e6edb009556fcd95c_786_0.png)

- 每个 AcceptedPaper 是 Status 为 'accept' 的 Paper。
- 每个 LabOrLecRoom 是 RoomType 为 {'lab', 'lec'} 的 Room。
- 每个 Lab 是 RoomType 为 'lab' 的 Room。
- 每个 LecRoom 是 RoomType 为 'lec' 的 Room。

图 14.79 逆向工程得出的概念架构。

表分组与 Rmap 生成的不同，例如，两个 Committee 事实类型被错误地分组到同一表中，尽管其中一个是非功能性的。因此，原始 Committee 表容易出现 Committee has budget of MoneyAmt 类型事实的冗余问题。同样，Authored 表通过包含 Paper has PaperTitle 类型事实而出现冗余。因此，原始设计以不受控制的方式对关系模式进行了反规范化。

虽然 ORM 架构看起来复杂，但概念化澄清了 UoD，例如，PaperSlot 表的语义在 ORM 架构中更容易理解。现在详细语义以图形方式显示，我们更有能力以受控方式探索优化可能性。

作为重新工程化的第二阶段，使用概念优化过程将概念架构转换为 Rmaps 到更高效关系模式的架构。将您的解决方案与图 14.80 进行比较。将 chairperson 和 diagram 谓词专业化为功能二元谓词是简单直接的。

![](img/1344db3eba3d550e6edb009556fcd95c_787_0.png)

- 每个 AcceptedPaper 是 Status 为 'accept' 的 Paper。
- 每个 LabOrLecRoom 是 RoomType 为 {'lab', 'lec'} 的 Room。
- 每个 Lab 是 RoomType 为 'lab' 的 Room。
- 每个 LecRoom 是 RoomType 为 'lec' 的 Room。
- 每个 AcceptedAuthoring 是 (Person authors AcceptedPaper)。

图 14.80 优化后的概念架构。

在嵌入 referee 和 author 谓词时，我们本可以将这些互斥但兼容的谓词合并。尽管这种替代方案会减少一个表，但嵌入这些互斥谓词会降低可读性并导致尴尬的约束模式。

即使图 14.80 中的嵌入也会导致尴尬的口头表述。原始的四个谓词展平似乎比两个嵌入更自然。理想情况下，CASE 工具应允许建模人员为清晰起见选择展平显示，并可选择在隐藏的预处理阶段进行嵌入以进行标准映射。

下一阶段是映射图 14.81 中的优化概念架构。作为练习，在查看图 14.81 中的解决方案之前，请先尝试自己完成。请注意，最终关系模式仅包含七个表（与原始的 12 个表相比），完全规范化，并捕获了所有原始约束以及原始模式中缺失的约束。

最后，执行数据迁移。此转换的主要方面涉及根据原始关系类型定义新关系类型。完成此操作后，数据迁移可以自动执行。图 14.81 为每个新表显示一行转换后的数据。

![](img/1344db3eba3d550e6edb009556fcd95c_788_0.png)

图 14.81 最终关系模式。

## 练习 14.8

- 1. 以下关系模式旨在记录学者和学科的详细信息，但其性能较差，主要是因为常见查询需要许多连接。此外，开发人员发现 Academic 表及其 qualified

