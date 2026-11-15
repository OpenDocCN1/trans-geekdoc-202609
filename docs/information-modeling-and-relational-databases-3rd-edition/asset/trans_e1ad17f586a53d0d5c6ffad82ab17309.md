

![](img/1344db3eba3d550e6edb009556fcd95c_747_0.png)

图 14.44 该次优模式映射为六个表。

- **联合讲授** ( topiccode, colecturer )
- **研究生主题** ( topiccode, topicTitle, headLecturer, period )
- **实际先决条件** ( topiccode, actualPrereq )
- **偏好先决条件** ( topiccode, preferredPrereq )
- **主题选择** ( studentNr, subjectCode, topicCode )
- **注册** ( studentNr, subjectCode )

图 14.45 从图 14.44 映射而来的关系模式。

PGtopic.topicCode（即，PGtopic.topicCode 是 ActualPrerequisite.topicCode 和 PrefPrerequisite.topicCode 的不相交并集）。普通的“x”表示联合讲授和 PGtopic 中的主题-讲授者对是互斥的。其他约束都很简单。

假设该领域的一个聚焦查询如下：列出所有主题（代码和标题），以及它们的主讲教师、联合讲授者、实际先决条件和偏好先决条件。设另一个聚焦查询如下：列出学生、他们注册的科目以及他们为这些科目选择的主题（如有）。利用图 14.45 的关系模式，第一个查询涉及四个表的连接，第二个查询涉及两个表的复合外连接。因此，这些查询运行速度会很慢。

![](img/1344db3eba3d550e6edb009556fcd95c_748_0.png)

图 14.46 通过优化图 14.44 得到的概念模式。

将优化步骤 1 和 2 应用于图 14.44 的概念模式，会产生三个主要变化，如图 14.46 所示。

步骤 1.2 通过提取对象类型 PrereqKind {"actual", "preferred"}，将两个先决条件二元关系推广为一个三元关系。步骤 1.3 使用重叠算法将注册和主题事实类型嵌套。步骤 2.1 将 colecturer 谓词专门化为两个互斥的二元关系，仅按 Topic 键控。如果我们还要求：一个主题若有 colecturer2，则必须有 colecturer1，则可将此作为子集约束添加。作为练习，重新映射图 14.46 中的模式，然后与图 14.47 所示的解法核对。

```
PGtopic ( topicCode, topicTitle, period, headLecturer, [colecturer1], [colecturer2] )
{ sem1, sem2, yr }
Prerequisite ( topicCode, subjectCode, prereqKind )
{actual, preferred}
Enrollment ( studentNr, subjectCode, [topicCode] )
```

图 14.47 从图 14.46 映射而来的关系模式。

优化后的关系模式仅有三个表：一个用于三元关系，一个用于嵌套，一个用于主题的五个功能性二元关系。“≠”符号表示：在同一行中，headLecturer、colecturer1 和 colecturer2 的任何非空值都必须互不相同。该关系模式使聚焦查询的执行速度大大加快，并且对更新的约束执行也更简单。

现在我们来考虑优化过程中的最后几步（3、4、5）。与之前的步骤不同，这些步骤不会减少表的数量。步骤 3 在图 14.48 中说明。其目的是减少自连接，被称为表宽度准则（TWG），因为它指示何时更宽的表（更多列）可能更可取。

图示的模式等价性之前已讨论过。如果对象类型 A 扮演功能角色，则转换为二元关系的操作已在步骤 2.1 的最后阶段完成。即使 A 没有功能角色，如果将其专门化为二元关系可以避免聚焦查询中的自连接，那么这样做仍然可能值得。

![](img/1344db3eba3d550e6edb009556fcd95c_749_0.png)

每个 S<sub>i</sub> 对应于 R，其中 B = b<sub>i</sub>，

- 3 对于上述三元模式，如果对 R 的聚焦查询需要在不同元组之间进行比较，并且 b<sub>1</sub>、...、b<sub>n</sub> 的值很少且相当稳定，则吸收 B，将 R 专门化为 n 个功能性二元关系。

图 14.48 优化步骤 3：表宽度准则。

作为步骤 3 的示例，假设我们想查看 2021–2023 三年期内各学位全日制大学学费的变化情况。让我们用三元关系 Degree in Year had FulltimeFee 来建模，该关系对前两个角色施加唯一性约束，对第一个角色施加频率约束 3，并对 Year 的角色施加值约束 {2021...2023}，如图 14.49 所示。假设我们将此映射为关系模式 FulltimeFee ( degree, feeYear, Fee )，并在关系级别强制执行频率和值约束。

该表的示例数据片段如图 14.49 所示。设一个示例聚焦查询为：BS 全日制学费在三年期内增加了多少？请通过观察表格自行回答此问题。

| 学位 | 费年 | 费用 |
|---|---|---|
| BS | 2021 | 5000 |
| BS | 2022 | 5000 |
| BS | 2023 | 5500 |
| MBA | 2021 | 7000 |
| MBA | 2022 | 7300 |
| MBA | 2023 | 7700 |

![](img/1344db3eba3d550e6edb009556fcd95c_749_1.png)

BS 学位全日制学费在 3 年内增加了多少？

```
SQL code for query: select New.fee - Old.fee
from FullTimeFee as Old cross join FullTimeFee as New
where Old.feeYear = 2021 and Old.degree = 'BS' and
New.feeYear = 2023 and New.degree = 'BS'
```

图 14.49 此查询需要自连接，因为它比较不同的行。

可通过先使用 TWG 转换模式来避免此类连接。应用 PSG1 的一个变体，其中值约束应用于角色而非对象类型，三元关系专门化为三个概念二元关系：Degree had 2021- FulltimeFee；Degree had 2022- FulltimeFee；Degree had 2023- FulltimeFee。

在这里，Degree 的角色是功能性的，并通过等式约束关联。如果在全局模式中，Degree 的学费信息是强制性的，则这些角色是强制性的（这隐含了等式约束）。如果 Degree 没有其他功能角色，则这三个概念二元关系映射到一个表：FulltimeFee ( degree, fee2021, fee2022, fee2023 )

如果 Degree 有其他功能角色，则优化本应在步骤 2.1 中执行，额外的功能事实类型将映射到同一表。

图 14.50 展示了概念模式，并说明了更宽的表如何使查询仅需比较同一行上的值即可完成，这比之前的查询容易得多。

![](img/1344db3eba3d550e6edb009556fcd95c_750_0.png)

| 学位 | 2021学费 | 2022学费 | 2023学费 |
|---|---|---|---|
| BS | 5000 | 5000 | 5500 |
| MBA | 7000 | 7300 | 7700 |

BS 学位全日制学费在 3 年内增加了多少？

```
SQL code for query: select fee2023 - fee2021
from FullTimeFee
where degree = 'BS'
```

图 14.50 转换后的模式带来了更高效的查询。

此示例简单而明确，但生活并不总是如此简单。如果费用年份范围很大，转换生成的额外列数可能过高。例如，假设我们必须记录 1984...2023 期间的费用。将三元关系专门化将生成 50 个二元关系，并导致一个包含 51 列的关系表：FulltimeFee( degree, fee1984, ..., fee2023 )。

如此多的二元关系会使概念模式变得混乱（尽管可将灵活的 CASE 工具设置为显示隐藏在映射中的优化三元关系）。非常宽的关系表在查看（需大量水平滚动）和打印时也会很不方便。出于这些原因，一旦值约束的基数超过合理数量（例如，5），三元事实类型可能更受青睐。

值约束的稳定性也很重要。在许多情况下，这样的约束已知是稳定的（例如，gendercode 的 {"m", "f"}）。但是，有时值约束会随时间变化。例如，假设要记录从 2001 年到当前年的所有年份的费用，或者仅记录最近三年期的费用。二元方法

