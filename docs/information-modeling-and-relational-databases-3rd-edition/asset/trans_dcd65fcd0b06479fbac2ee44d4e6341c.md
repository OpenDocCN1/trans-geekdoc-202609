

图 12.13 显示了三个等效查询，用于列出既不高于 172 厘米也不低于 168 厘米的球员信息。运算符优先级确保图 12.13 中的查询 (a) 表示 Player where (not (height>172)) and (not (height<168))。请注意，六个比较运算符可以分为三组对立符号：=, <>; <, >; 和 >=, <=。因此，图 12.13(a) 中的查询可以用图 12.13(b) 中更简短的查询替换。

- (a) Player where not height > 172 and not height < 168
- (b) Player where height <= 172 and height >= 168
- (c) Player where not (height > 172 or height < 168)

| 姓名 | 性别 | 身高 |
|---|---|---|
| David | M | 172 |
| Norma | F | 170 |

图 12.13 三个等效查询。

德·摩根定律，以著名逻辑学家 Augustus De Morgan 命名，如下所示。这里，p 和 q 表示任何命题或逻辑条件。

```
not (p and q) ≡ not p or not q
not (p or q) ≡ not p and not q
```

这些定律在二值逻辑和三值逻辑中都成立，因此可以安全地用于空值。使用第二条定律，可以轻易看出图 12.13(c) 中的查询与图 12.13(a) 中的查询等效。

## 关系投影

下一个表操作，称为 **投影**，在第 4 章中介绍过。该操作涉及从表中选择一列或多列，然后消除可能产生的任何重复行。据说它产生一个垂直子集或列子集。图 12.14 说明了对两列的投影。

![](img/1344db3eba3d550e6edb009556fcd95c_571_0.png)

仅选择列 a 和 b。消除结果中的任何重复行。

图 12.14 关系代数中的投影操作。

我们可以将投影操作表示为 _T_ [_a,b, ..._]，其中 _T_ 是表达式，_a, b, ..._ 是所需列的名称（此列列表称为 _投影列表_）。为了限定投影列表，我们使用方括号而不是圆括号，因为后者在查询中有其他用途（例如，更改运算的求值顺序）。将方括号“[ ]”斜体化有助于将其与用于限定可选项（或袋）的“[ ]”以及在选择列后指示额外任务（重复消除）的用法区分开来。

替代符号 \(\pi_{a,b...}(T)\) 在学术期刊中很常见。“\(\pi\)” 符号是 pi，即希腊字母“_p_”（“projection”的首字母）。与 SQL 类似，此符号在表格之前列出所需列。我们偏好的符号则鼓励自顶向下思考，即在列出列之前先识别相关表格。

| 姓名 | 性别 | 身高 |
|---|---|---|
| David | M | 172 |
| Norma | F | 170 |
| Selena | F | 165 |
| Terry | M | 178 |

| 姓名 | 性别 |
|---|---|
| David | M |
| Norma | F |
| Selena | F |
| Terry | M |

| 性别 |
|---|
| M |
| F |

图 12.15 投影涉及选择列并删除任何重复项。

图 12.15 基于表 _Player_ (name, gender, height) 给出了两个示例。在单个基本表上进行投影时，如果所选列包含候选键，则不会产生重复行。否则，可能会出现重复项。例如，仅选择 gender 列会得到袋 [“M”, “F”, “F”, “M”]。要完成投影，需消除重复值，得到集合 {“M”, “F”}。如果对所有列进行投影，我们将得到同一个表。例如，Player [name, gender, height] 与 Player 是同一个表。

投影中不得重复提及同一列。例如，Player [name, name] 是非法的（为什么？）。投影也可以用于以不同顺序显示列。例如，Player [height, gender, name] 会反转顺序。由于结果中列出了唯一的列名，这不会改变含义。

如果关系架构完全规范化，则基本表具有并兼性（union compatible）的情况相当少见（之前考虑的 Eats 和 Likes 表是例外）。因此，\(\cup, \cap,\) 和 – 操作几乎专用于因投影而变得并兼的结果表。

我们现在来看一些稍微困难的示例。为了方便讨论此类情况的逐步方法，我们使用 **关系赋值** 操作。由于内容可能会变化，表方案可以被视为 _变量_。事实上，表是关系代数中允许的唯一变量类型。关系赋值操作与代数本身严格分开，类似于编程语言中的赋值。使用符号 “:=” 表示“变为”或“被赋值为”，我们可以写出如下形式的赋值语句。

```
table variable := table expression
```

这是一条指令，先对右侧的表达式求值，然后将其值放入左侧命名的变量中。如果该变量之前有值，旧值将被新值替换。例如，如果 X、A 和 B 是表值，则语句 “X := A := B” 表示 X 被赋值为 A – B。其他一些符号使用 “=” 或 “←” 代替 “:=”。

一旦在关系赋值中命名，结果表就可以在后续表达式中像基本表一样使用。例如，要将高个男性球员的详细信息存储在名为 “TallMalePlayer” 的表中，我们可以进行以下三个赋值。要列出这些详细信息，我们现在可以直接查询 TallMalePlayer。

```
MalePlayer := Player where gender = 'M'
TallPlayer := Player where height > 175
TallMalePlayer := MalePlayer ∩ TallPlayer
```

作为更困难的示例，请考虑图 12.16 中的 UoD。我们如何在关系代数中表述以下查询：哪些非欧洲国家说法语？在继续阅读前，请先自己尝试一下。

![](img/1344db3eba3d550e6edb009556fcd95c_573_0.png)

| 语言 | 国家 |
|---|---|
| Dutch | Belgium |
| Dutch | Netherlands |
| English | Australia |
| English | Canada |
| French | Belgium |
| French | Canada |
| French | France |

| 国家 | 地区 |
|---|---|
| Australia | Australasia |
| Belgium | Europe |
| Canada | North America |
| France | Europe |
| Netherlands | Europe |

图 12.16 概念和关系架构，包含示例数据。

我们可以分步表述查询，在过程中使用中间表来获得最终结果表。例如：

```
NonEuroCountry := (Location where region <> 'Europe') [country]
FrenchSpeakingCountry := (SpokenIn where language = 'French') [country]
FrenchSpeakingNonEuroCountry := NonEuroCountry ∩ FrenchSpeakingCountry
```

这里，我们的第一步是找出非欧洲国家：{Australia, Canada}。然后我们找出说法语的国家：{Belgium, Canada, France}。最后，我们对这些国家取交集，得到结果：{Canada}。

以这种方式表述查询称为 *逐步表述*。分步操作有时可以让表述困难查询变得更容易。然而，使用单个表达式来表述查询可以节省一些书写。例如，刚才考虑的三个赋值语句可以替换为以下内容：

```
FrenchSpeakingNonEuroCountry :=
    (Location where region <> 'Europe') [country] ∩
    (SpokenIn where language = 'French') [country]
```

分配给 FrenchSpeakingNonEuroCountry 的冗长表表达式被称为 *嵌套表述*，因为它将一个或多个查询嵌套在另一个查询中。对于复杂查询，我们可能在脑海中或在某处潦草记下逐步表述，然后将其转换为嵌套表述。一般来说，任何可以通过一系列关系代数查询提取的信息，都可以在单个关系代数查询中指定。

请注意，投影不分配于交换。换句话说，给定表 A 和 B 以及投影列表 p，可能出现 (A ∩ B)[p] ≠ A[p] ∩ B[p]。例如，以下查询与前一个查询不等效（为什么？）。

```
((Location where region <> 'Europe') ∩ (SpokenIn where language = 'French')) [country]
```

此查询非法，因为 ∩ 的表操作数不兼容。即使 A 和 B 兼容，投影也不一定分配于 ∩ 或 −。如果 A 和 B 兼容，投影确实分配于 ∪，即 (A ∪ B)[p] = A[p] ∪ B[p]。作为练习，你可以尝试证明这些结果。

## 关系连接

概念级别的对象连接在第 4.4 节中介绍，以帮助澄清外部唯一性约束的含义。我们现在考虑两个表（或同一表的两个出现）之间的关系连接操作，该操作使用比较运算符（=, <, >, <>, <=, >=）比较表中的属性值。

存在多种连接操作，这里仅讨论其中一些。任何连接操作中被比较的列必须定义在同一域上；它们不需要具有相同的名称。在需要区分具有相同本地名称的连接列时，我们使用它们的完全限定名。

设 Θ（theta）表示任何比较运算符（=, < 等）。那么，表 A 和 B 在属性 a（来自 A）和 b（来自 B）上的 Θ-*连接* 等于笛卡尔积 A × B，仅限于 A.a Θ B.b 的那些行。我们按如下所示编写此内容。另一种学术符号在花括号中显示。

```
(A × B) where c    {or A >< c B}
```

