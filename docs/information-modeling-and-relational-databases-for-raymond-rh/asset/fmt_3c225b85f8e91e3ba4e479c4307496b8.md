
# SQL LIKE 操作符与空值处理

## LIKE 操作符中的通配符

注意，“%”和“_”仅在 **like** 条件的上下文中被解释为通配符。例如，以下查询返回空集。没有行满足该条件，因为如果使用“=”代替 **like**，表达式“A%”将被按字面意思理解。

```
select starsign from Person
```

```
where starsign = ‘A%’
```

如前所述，要在字符串中包含单引号，我们使用两个单引号。例如，对于前面考虑的表模式 *Actor*（surname, firstname, gender），以下查询返回姓氏以“D’”开头的每个演员：

**select** surname **from** Actor **where** surname **like** ‘D”%’。

## LIKE 操作符的实用示例

要查看 **like** 操作符非常有用的几个示例，请考虑 [表 12.10](#Ch012_539-646_B9780443237904000268_1.xhtml#t0055)，该表显示了给定大学在哪个学期提供哪些科目。样本数据量较小以节省空间。

[表 12.10](#Ch012_539-646_B9780443237904000268_1.xhtml#B-t0055) 显示科目及学期的关系表。

| ![t12-10-9780443237904](images/B9780443237904000268/t12-10-9780443237904.jpg) |

---

在该大学中，科目代码具有以下含义：前两个字符表示学科领域（例如，“CS”表示计算机科学，“PD”表示哲学），第三个字符表示年级（例如，“1”表示一年级）。

请尝试自己构思以下查询，然后再查看答案。

*   列出计算机科学科目。
*   列出一年级科目。
*   列出高于一年级且在第二学期开设的科目。

按顺序，查询如下：

```
select distinct subject from Offering where subject like 'CS%'
```

```
select distinct subject from Offering where subject like '_ _1%'
```

```
select distinct subject from Offering
```

```
where subject not like '_ _1%' and semester = 2
```

## 人名的结构化处理

另一个常被解释为具有结构的字符串示例是人名。通常，会记录一个人的姓氏以及名字或首字母缩写（例如，“Smith, James”或“Smith JB”）。在西方文化中，“surname”和“first name”常分别用于指代姓氏和名字。在某些国家（如日本），姓氏在前。

假设我们希望区分人名的这两个部分。一种实现方法是包含两列，一列用于姓氏，另一列用于名字（或首字母缩写）。这样结构就为系统所知，可以单独访问名字的这两个部分（这对于 SQL 的 **group by** 功能特别方便）。

或者，我们可以只用一列存储全名，然后使用 **like** 操作符来区分这两个部分——此时名字结构变为派生结构而非存储结构。

例如，考虑 [表 12.11](#Ch012_539-646_B9780443237904000268_1.xhtml#t0060)，该表提供了混合双打网球比赛选手的详细信息。尝试以下查询，然后核对答案。

*   列出姓氏为“Smith”的人的详细信息
*   列出名字为“James”的人的详细信息

[表 12.11](#Ch012_539-646_B9780443237904000268_1.xhtml#B-t0060) 网球选手关系表。

| ![t12-11-9780443237904](images/B9780443237904000268/t12-11-9780443237904.jpg) |

---

按顺序，查询如下：

```
select * from Player where personName like 'Smith, %'
```

```
select * from Player where personName like '%, James'
```

## 转义字符

使用 **like** 操作符的条件可以选择性地包含*转义字符*。如果选定，它可作为引导字符，使“%”和“_”按字面意思解释，而非作为通配符。例如，[图 12.48](#Ch012_539-646_B9780443237904000268_1.xhtml#f0245) 中的查询列出了名称中包含下划线字符的星舰。这里使用“\\”作为引导字符；任何不在被检查字符串中出现的字符都可使用。某些 SQL 方言通过额外通配符扩展了 **like** 操作符的功能。例如，SQL Server 使用 `[]` 包含字符范围，使用 `[^∧]` 排除字符。

![Fig. 12.48 Here, “\\” is used as an escape character to detect an underscore.](images/B9780443237904000268/f12-48-9780443237904.jpg)

[图 12.48](#Ch012_539-646_B9780443237904000268_1.xhtml#B-f0245) 这里使用“\\”作为转义字符来检测下划线。

## 空值处理

虽然空值可能被显示（例如显示为“?”），但它们不能与常规比较操作符一起使用。相反，使用特殊的后缀布尔 **is null** 操作符。该操作符放在其操作的列名之后。如果列值为空则返回 True，否则返回 False。例如，以下针对 Player 表的查询返回“Smith, Sue”，因为她的身高未知：

```
select personName from Player
```

```
where height is null
```

不允许使用表达式“height = null”或“height = ‘?’”。要指定值不为空，请在列名或单词 **null** 前使用逻辑 **not** 操作符。例如，以下任一查询均返回其他三名选手的姓名。

```
select personName from Player where not height is null
```

```
select personName from Player where height is not null
```

使用“col”表示列，SQL-89 中空值比较的 BNF 语法为：

```
col is [ not ] null
```

## 三值逻辑

虽然 **is null** 操作符总是返回 True 或 False，但其他比较操作符在参数之一为空值时返回 unknown。假设我们想要身高在 170 到 175 厘米之间（含边界）的选手姓名。以下查询仅返回两个姓名：“Smithers, James”、“James, Susan”。

```
select personName from Player where height between 170 and 175
```

虽然现实世界中 Sue Smith 的身高可能在此范围内，但她被排除在结果之外。系统不知道她的身高，因此在她的情况下不会将条件评估为 True。假设现在我们想要身高不在 170..175 范围内的选手姓名。以下查询仅返回一个姓名：“Smith, James”。

```
select personName from Player
```

```
where height not between 170 and 175
```

请注意，Sue Smith 也被排除在该结果之外。就系统而言，在她的情况下，“height between 170 and 175”这一条件的真值既非真也非假；而是 unknown。

只有满足搜索条件的行才会包含在结果中，即系统已知该条件对该行为 True。如果条件为 False 或 Unknown，该行将从结果中排除。

作为一个极端示例，以下查询返回除 Sue Smith 以外的所有选手。

```
select personName from Player
```

```
where height = 170 or height <> 170
```

对于 Sue Smith 的行，该条件中的每个比较都评估为 unknown，对 unknown 应用 **or** 操作符返回 unknown。任何条件的真值均根据*三值逻辑*进行评估，如 [图 12.49](#Ch012_539-646_B9780443237904000268_1.xhtml#f0250) 所示。此处，“1”、“0”和“?”分别表示“True”、“False”和“Unknown”。

![Fig. 12.49 Truth tables for three-valued logic (1 = True, 0 = False, ? = Unknown).](images/B9780443237904000268/f12-49-9780443237904.jpg)

[图 12.49](#Ch012_539-646_B9780443237904000268_1.xhtml#B-f0250) 三值逻辑真值表（1 = True，0 = False，? = Unknown）。
