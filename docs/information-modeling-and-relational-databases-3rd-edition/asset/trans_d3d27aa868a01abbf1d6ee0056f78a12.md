

然而，图 14.60(b) 中的表不符合 3NF，因为 population 取决于 birth-country，而这两者都是非关键属性。请注意，population 对键具有传递依赖关系（studentNr 决定 birthcountry，而 birthcountry 决定 population）。该表表现出冗余：美国人口为 301,139,947 这一事实被显示了两次。为避免这种冗余，非关键属性之间 FD 所依据的事实类型被拆分到另一个表中，如图 14.61 所示，该图展示了示例的 ORM 和关系模式。

![](img/1344db3eba3d550e6edb009556fcd95c_763_0.png)

图 14.61 图 14.60(b) 的概念模式和正确的关系模式。

现在考虑图 14.62 中的表，它是第 5.5 节中用于说明 CSDP 中逻辑推导检查的示例的修改版本。如果此 CSDP 步骤已正确执行，则从 Rmap 得到的任何表中都不可能出现一个非关键属性到另一个非关键属性的 FD。在第 5.5 节的原始示例中，我们将此表拆分为两个表，一个对应事实类型 Lecturer works for Department，另一个对应事实类型 Department is located in Building，推导出事实类型 Lecturer works in Building 当且仅当 Lecturer works for a Department that is located in Building。

Lecturer ( 姓氏, 部门, 楼宇 )

| 姓氏 | 部门 | 楼宇 |
|---|---|---|
| Halpin | CS | 69 |
| Okimura | JA | 1 |
| Orlowska | CS | 69 |
| Wang | ? | 1 |
| Zelewski | ? | 2 |

图 14.62 函数依赖 surname → building 所依据的事实能否通过传递推导？

然而，如果这个双条件语句中“iff”的“only if”部分未得到满足，则两表设计会丢失信息。例如，假设 Wang 和 Zelewski 不为任何部门工作（例如，他们可能是访问讲师）。这种情况由图 14.62 中表格的最后两行表示，使用“？”表示空值。如果我们如前所述将表拆分为两个表，则将无法推导出关于 Wang 和 Zelewski 在哪里工作的事实。

规范化的早期工作假设不会出现空值，但这一假设往往不成立。如果我们同意 Codd (1990, p. 201) 的观点，即在应用关于 FD 的规则时应忽略空值，那么图 14.62 中所示的 FD 仍然存在；然而，将此表分解为两个表是错误的，因此此规范化步骤可能是不安全的。处理此类问题的最安全方式是在概念层面。

比尔·肯特 (Bill Kent, 1983) 对第二和第三范式的完善原则进行了精妙总结：“非关键字段必须提供关于键、整个键、仅关于键的事实”。应将最后一次出现的“the key”替换为“a key”来细化此原则。

Codd 在 2NF 和 3NF 工作中，根据属性是否属于候选键，将属性分类为“主属性”或“非主属性”。我们现在使用“关键属性”和“非关键属性”这两个术语来表示这些概念。因此，关键属性属于某个键（主键或备用键），而非关键属性不属于任何键。

因此，从某一意义上讲，3NF 的定义确实允许传递依赖，前提是中间属性是一个键。考虑图 14.63 中的表。它有两个键。我们可以认为，函数依赖 countryCode → population 是由函数依赖 countryCode → countryName 和 countryName → population 传递推导而来的。或者，我们可以认为 countryName → population 是由 countryName → countryCode 和 countryCode → population 推导而来的。然而，该关系仍然符合 3NF，因为非关键属性之间没有 FD。图的左侧显示了 ORM 模式。

| 国家（国家代码，国家名称，人口） |
|---|---|---|
| AU | 澳大利亚 | 26477504 |
| CA | 加拿大 | 38829398 |
| US | 美国 | 340265309 |

图 14.63 函数依赖 countryCode → population 是一种无害的传递依赖。

设 X 和 Y 为同一表的属性（可能是复合属性）。如果且仅当 X 包含 Y，则函数依赖 X → Y 是平凡的。例如，表方案 Student( studentNr, gender ) 有六个平凡函数依赖：studentNr → studentNr，(studentNr, gender) → studentNr，等等。如果且仅当不存在仅来自 X 部分到 Y 的函数依赖，则函数依赖 X → Y 是全函数依赖（而非部分依赖）。

一个全且非平凡的函数依赖称为初等函数依赖。考虑图 14.64 中关于美国城市人口（2023 年数据）的表。该表有三个从主键 cityNr 开始的初等函数依赖，以及两个从备用键 (cityName, stateCode) 开始的初等函数依赖。该表中的一些非初等函数依赖包括 cityNr → cityNr 和 (cityName, stateCode ) → cityName。我们通常避免显示非初等函数依赖，因为它们显然由初等函数依赖推导而来。

| 城市（城市编号，城市名称，州代码，人口） |
|---|---|---|---|
| 1 | Portland | OR | 632309 |
| 2 | Portland | ME | 68085 |
| 3 | Seattle | WA | 684451 |

图 14.64 五个初等函数依赖：三个来自 cityNr，两个来自 (cityName, stateCode)。

如果存在从某个键到表中某个属性的初等函数依赖，则该键是一个 *初等键*。仅当某个属性属于某个初等键时，它才是初等键属性。例如，图 14.64 中的城市表有两个初等键，cityNr 和 (cityName, stateCode)。我们现在可以定义下一个更强的范式，该范式被提出作为对 3NF 的改进（Zaniolo, 1982）。

一个表方案处于 **初等键范式（EKNNF）** 的当且仅当条件是，其所有初等函数依赖均始于整个键或终止于初等键属性。换句话说，对于每个形式为 X → Y 的全非平凡函数依赖，要么 X 是一个键，要么 Y 是（某个初等键的一部分）。例如，图 14.64 中的 City 表处于 EKNNF。如果表的主键包含其所有列，则该表自动处于 EKNNF，因为它没有初等函数依赖；例如：Enrollment( studentNr, subjectCode )。

现在考虑图 14.65(a) 中的 OfficialLanguage 表，该表记录了各国正式使用的语言。国家可以通过其代码或名称来识别。此表有两个复合键：(countryCode, language)；(countryName, language)。主键用双下划线标记；由于其属性不相邻，添加了虚线连接器以指示这是一个单一的复合键，而不是两个简单的键约束。次要键用单下划线标记。

由于 OfficialLanguage 表没有非关键属性，它自动符合 3NF。然而，它存在明显问题（例如，代码为“CA”的国家名为“Canada”这一事实被重复了）。

![](img/1344db3eba3d550e6edb009556fcd95c_765_0.png)

图 14.65 (a) 符合 3NF 但不符合 EKNNF 的表。(b) Rmap 提供了正确的模式。

发现这种糟糕设计的一种方法是注意到该表不符合 EKNNF。存在从 countryCode 到 countryName 的函数依赖，以及从 countryName 到 countryCode 的函数依赖（由表上方的箭头描绘）。这些初等函数依赖来自键的部分而非整个键，并且它们不终止于初等键属性，因为复合键都不是初等键。因此，该表不符合 EKNNF。

通过将表拆分为图 14.65(b) 所示的两个 EKNNF 表来避免冗余：Country( 国家代码, 国家名称 )；LanguageUse( 国家代码, 语言 )。原始表方案中遗漏的两个函数依赖现在由 Country 表中的键约束捕获，冗余被消除。通过对所示 ORM 模式进行 Rmap 也能得到相同的设计。如果语言事实类型对 Country 不是强制性的，则将关系模式中的等式约束替换为从 LanguageUse.countryCode 到 Country.countryCode 的简单子集约束。

下一个范式以 Raymond Boyce 和 Edgar Codd 命名，他们将其作为对 3NF 的改进提出。Heath (1971) 更早给出了一个等价定义。一个表方案处于 **Boyce–Codd范式（BCNF）** 的当且仅当条件是 _其所有初等函数依赖均始于整个键_（即，对于任何全非平凡函数依赖 X → Y，X 必须是一个键）。例如，关系方案 _学生_ ( studentNr, gender, birthdate ) 处于 EKNF，因为其所有初等函数依赖均始于 studentNr 键。只有当关系至少具有两个重叠的候选键时，它才可能处于 3NF（或 EKNF）但不处于 BCNF（Vincent and Srinivasan 1994）。

现在考虑图 14.66(a) 中的表。它与前一个表类似，只是记录了该国实际使用该语言的人口百分比（此处加拿大的数据为虚构的）。现在这些键是初等键，因为它们函数决定 percentUsage 属性。由于 countryCode 和 countryName 之间的函数依赖现在终止于初等键属性，该表处于 EKNF。但该表与前一个表具有相同的冗余。

该表不符合 BCNF，因为表上方所示的函数依赖不始于整个键。例如，存在函数依赖 countryCode → countryName，但 countryCode 只是 (countryCode, language) 键的一部分。通过将表拆分为图 14.66(b) 所示的两个 BCNF 表来避免冗余。

![](img/1344db3eba3d550e6edb009556fcd95c_766_0.png)

![](img/1344db3eba3d550e6edb009556fcd95c_766_1.png)

图 14.66 (a) 符合 EKNF 但不符合 BCNF 的表。(b) Rmap 提供了正确的模式。

该设计通过对所示 ORM 模式进行 Rmap 自动获得。与以前一样，如果语言使用事实类型是可选的，则将等式约束更改为子集约束。

