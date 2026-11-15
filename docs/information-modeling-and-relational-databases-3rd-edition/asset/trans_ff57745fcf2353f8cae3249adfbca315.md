
SQL:1999 走得更远，例如，可以使用 **of** 子句声明表为用户定义类型，该类型之前已用 **create type** 语句声明为行类型。可以使用 **under** 子句定义子表以引用超表。

商业 SQL 方言通常支持所有 SQL-89 功能，可能使用一些不同的语法。它们倾向于仅支持标准较新版本（如 SQL:2019 和 SQL:2023）中的部分新语法。约束名称和参照操作得到广泛支持，但断言和无限制的 **check** 子句很少得到支持。大多数厂商还提供自己的额外功能和语法。

让我们以软件零售商数据库的关系模式声明为例。该模式的图形版本如图 13.1 所示。接下来给出了 SQL-92 语法中的模式声明。您可以根据需要将其调整为适用于自己的 SQL 方言，也可以按需添加约束名称。

![](img/1344db3eba3d550e6edb009556fcd95c_673_0.png)

图 13.1 软件零售商数据库的关系模式。

```
create schema SoftwareRetailer;
create table Customer (
customerNr smallint not null primary key,
customerName varchar(20) not null,
address varchar(40) not null,
phoneNr varchar(10),
unique (customerName, address) );
create table Item (
itemCode char(4) not null primary key,
title varchar(20) not null unique,
category char(2) not null check (category in ('DB','SS','WP')),
stock smallint not null default 0,
listPrice decimal(6,2) not null );
create table Invoice (
invoiceNr smallint not null primary key,
customerNr smallint not null references Customer,
issueDate   date   not null,
paidDate date );

create table LineItem (
invoiceNr   smallint   not null   references Invoice,
itemCode    char(4)    not null   references Item,
qty         smallint   not null,
unitPrice   decimal(6,2) not null,

primary key ( invoiceNr, itemCode ) );
```

```
create assertion each_invoice_has_a_line_item
check ( not exists
(select * from Invoice
where invoiceNr not in
(select invoiceNr from LineItem)) );
```

注意四个表间子集约束（等式约束展示了其中两个）。除非我们稍后使用 alter table 或 create assertion 语句添加这些表间约束，否则表的创建顺序很重要。为了尽量减少此类后续添加的需求，应尽可能在引用表之前创建被引用表。在我们的示例中，这意味着要在 Invoice 表之前创建 Customer 表，并在 LineItem 表之前创建 Item 表。

默认情况下列是可选的，但可以使用 not null 声明为必填。SQL 要求主键列声明为 not null。主键隐含唯一约束，但也可以显式声明其他列或列列表，其含义是非空值唯一。例如，如果可选的 phoneNr 列改为声明为 unique，则实际电话号码在该列中最多出现一次，但该列中可以有许多 null 值。在某些商业系统中，这种情况下 null 可能被视为一个值，在这种情况下，phoneNr 列中最多只能有一个 null 值。

外键使用 references 子句声明，指示被引用表，后面可选地跟引用列列表，该列表必须已声明为主键或唯一。如果未给出引用列列表，则假定主键为目标。

软件零售商模式图形版本中的等式约束相当于 LineItem.invoiceNr 和 Invoice.invoiceNr 之间两个方向上的两个子集约束——一个参照循环。从 LineItem.invoiceNr 到 Invoice.invoiceNr 的子集约束是外键约束，因为目标是主键。因此，可以使用引用的 references 子句进行声明，如所示。但是，从 Invoice.invoiceNr 到 LineItem.invoiceNr 的子集约束不是外键约束，因为其目标只是复合主键的一部分。

从 SQL-92 开始，可以使用 create assertion 语句声明此约束，如所示。在不支持断言的 SQL 方言（如 SQL Server）中，可以通过其他方式编码断言（例如，使用 check 约束、触发器或存储过程）。我们将稍后详细讨论参照完整性。

check 子句指定必须满足的条件。值约束通常使用 check 约束实现。仅当 check 约束的条件计算结果为 false（非 true 和非 unknown）时，才会违反该约束。有些人发现这与 select 语句中的 where 子句相比不太直观，where 子句必须计算结果为 true（非 false 和非 unknown），行才会被包含在结果集中。

可以使用 default 子句声明默认选项。如果用户插入行而未指定列的值，则系统会自动为该列插入定义的默认值。在 SQL-89 中，仅允许的默认值为字面量值、user 或 null。如果可选列没有 default 子句，则假定 null 为默认值。SQL-92 将可能的默认值扩展为包括无参函数 current_user、session_user、system_user、current_date、current_time、current_timestamp。SQL:1999 添加了 current_role、current_path 以及任何隐式类型的值规范（例如，用于处理集合类型）。

下面是一个在 SQL 中决定在何处声明约束的建议过程，如果您希望尽量减少按键次数，可能会发现它很有用：

- 如果约束仅适用于一个表
  - 或为外键约束
- 如果它仅适用于一个列
  - 则随列声明它
  - 否则在表定义末尾声明它
- 否则使用断言（或触发器等）声明它

SQL:2003 添加了另一个列选项来处理标识列的创建，其列语法为

```
colname data-type [ generated { always | by default } as identity ]
[ ( start with start-value | increment by increment-value |
{ maxvalue value | no maxvalue } | { minvalue value | no minvalue } |
{ cycle | no cycle } [ , ... ] ) ]
```

表中最多只能有一个标识列，其数据类型必须是标度为零的数值类型（例如，integer）。当将行插入表中时，系统会根据相当复杂的选项集生成序列中的下一个值。如果指定了 always，则尝试向标识列插入值会导致错误。如果指定了 by default，系统会在未提供值时生成一个值；否则，将使用提供的值。如果随后删除行，其标识值不会被重复使用。

start with 和 increment by 的默认值均为 1，除非显式指定其他值。增量值可以是正数或负数。序列可能的最大值和最小值取决于实现，除非定义了特定的 maxvalue 或 minvalue，否则将采用这些值。一旦达到或超过 **maxvalue**（递增时）或 **minvalue**（递减时），序列将停止且不再生成更多值。根据起始值和增量大小之间的关系，序列可能正好落在 **maxvalue** 或 **minvalue** 上，也可能不会。

除非指定了 **cycle** 选项，否则序列不会循环回去并重复已生成的值。如果指定了 **cycle**，则在递增时序列会在 **maxvalue** 处停止并重置为 **minvalue**，递减时则反之。起始值可以位于这两个值定义的范围内的任何位置。

大多数实现都支持标识列，尽管不一定使用 SQL 标准语法。生成的值在表中唯一的保证使其很有吸引力，可用作主键。在表的自然主键笨拙的情况下（例如，多个 **varchar** 列的组合），通常会引入标识列作为代理键。

SQL:1999 标准允许基于现有表定义创建表。该功能在 SQL:2003 中得到改进，以便更精确地控制新表中应包含或排除的列。基本语法如下。

```
create table new-tablename like existing-tablename
[ { including identity | excluding identity } |
{ including defaults | excluding defaults } |
{ including generated | excluding generated } [...] ]
```

**create table ... like ...** 语句的结果是一个空表，与原始表具有相同的列名、数据类型和空性。现有表和新表之间不建立依赖关系。这些选项指定对“特殊”列应采取什么操作。

## 维护参照完整性

现在让我们更详细地讨论 *参照完整性* 的概念。回顾一下，参照完整性是子集约束的特例。以下关系模式大纲显示了一个典型案例，其中 *S.a* 是引用 *R.a* 的外键。基本上，如果 *S.a* 中的每个值要么作为 *R.a* 的值出现，要么为 null，则子集约束得到满足。

```
R ( a b , ... )
  ^
  |
S ( a c , d, ... )
```

子集约束可能以以下任何一种方式被违反：

- (1) 向 S 插入带有不在 R.a 中的值的 S.a 的行
- (2) 更新 S 的行，将 S.a 的值替换为不在 R.a 中的值
