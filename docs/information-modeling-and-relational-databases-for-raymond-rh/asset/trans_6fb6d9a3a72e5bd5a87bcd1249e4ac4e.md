
请注意四个表间子集约束（等式约束显示了其中两个）。除非我们稍后使用 `alter table` 或 `create assertion` 语句添加这些表间约束，否则创建表的*顺序*很重要。为了尽量减少后续添加的需要，你应该尽可能在引用表之前创建被引用表。在我们的示例中，这意味着在 `Invoice` 表之前创建 `Customer` 表，在 `LineItem` 表之前创建 `Item` 表。

列默认是可选的，但可以使用 `not null` 声明为强制性。SQL 要求 `primary key` 列必须声明为 `not null`。`primary key` 默认假定具有 `unique` 约束，但也可以为其他列或列组合显式声明 `unique`，其含义是非空值唯一。例如，如果可选的 `phoneNr` 列被声明为 `unique`，则实际电话号码在该列中最多只能出现一次，但该列中可以有多个空值。在这种情况下，某些商业系统可能会将 `null` 视为一个值，此时 `phoneNr` 列中最多只能有一个空值。

外键通过 `references` 子句声明，指示被引用的表，后面可选地跟随被引用的列列表，该列表必须已被声明为 `primary key` 或 `unique`。如果未给出被引用的列列表，则假定 `primary key` 为目标。

软件零售商模式图形版本中的等式约束等同于 `LineItem.invoiceNr` 和 `Invoice.invoiceNr` 之间双向的两个子集约束——一个引用循环。从 `LineItem.invoiceNr` 到 `Invoice.invoiceNr` 的子集约束是一个外键约束，因为目标是主键。因此，可以使用 `references` 子句声明，如所示。然而，从 `Invoice.invoiceNr` 到 `LineItem.invoiceNr` 的子集约束*不是*外键约束，因为其目标只是复合主键的一部分。

在 SQL-92 及以后版本中，此约束可以使用 `create assertion` 语句声明，如所示。在不支持断言的 SQL 方言中（如 SQL Server），断言可以用其他方式编码（例如，通过 `check` 约束、触发器或存储过程）。我们稍后将更详细地讨论参照完整性。

`check` 子句指定一个必须满足的条件。值约束通常使用 `check` 约束实现。当且仅当其条件计算结果为 `false`（非 `true` 且非 `unknown`）时，`check` 约束才会被违反。与 `select` 语句中的 `where` 子句相比，有些人觉得这不直观，后者必须计算结果为 `true`（非 `false` 且非 `unknown`），该行才会包含在结果集中。

默认选项可以用 `default` 子句声明。如果用户插入行时未指定某列的值，系统会自动插入该列定义的默认值。在 SQL-89 中，允许的默认值仅限于字面值、`user` 或 `null`。如果可选列没有 `default` 子句，则假定 `null` 为默认值。SQL-92 将可能的默认值扩展为包括零参数函数 `current_user`、`session_user`、`system_user`、`current_date`、`current_time`、`current_timestamp`。SQL:1999 增加了 `current_role`、`current_path` 以及任何隐式类型的值规范（例如，用于处理集合类型）。

以下是一个建议的程序，用于决定在 SQL 中何处声明约束，如果你想最小化按键次数，可能会觉得有用：

```
If a constraint applies to only one table or is a foreign key constraint then if it applies to only one column then declare it with the column else declare it at the end of the table definition else declare it with an assertion (or trigger etc.)
```

SQL:2003 增加了另一个列选项来处理*标识列*的创建，其列语法如下：

*   ```
    colname data-type [ generated { always | by default } as identity ]
    ```
*   ```
    [ ( start with start-value | increment by increment-value |
    ```
*   ```
    { maxvalue value | no maxvalue } | { minvalue value | no minvalue } |
    ```
*   ```
    { cycle | no cycle } [ ,… ] ) ]
    ```

一个表中最多只能有一个标识列，且其数据类型必须为数值且小数位为零（例如 `integer`）。当向表中插入行时，系统会按选项定义生成序列中的下一个值。如果指定了 `always`，则尝试向标识列插入值会报错。如果指定了 `by default`，则在未提供值时系统会生成一个值；否则，将使用提供的值。如果随后删除了某行，其标识值不会被重用。

`start with` 和 `increment by` 的默认值均为 1，除非显式指定否则。增量值可以是正数或负数。序列可能的最大值和最小值取决于实现，除非定义了特定的 `maxvalue` 或 `minvalue`，否则将采用这些实现相关的值。一旦达到或超过 `maxvalue`（向上计数）或 `minvalue`（向下计数），序列停止，不再生成值。根据起始值和增量大小的关系，序列可能恰好落在 `maxvalue` 或 `minvalue` 上，也可能不会。

除非指定了 `cycle` 选项，否则序列不会循环回滚并生成已生成的重复值。如果指定了 `cycle`，向上计数时序列将在 `maxvalue` 停止并重置为 `minvalue`，向下计数则相反。起始值可以位于这两个值定义的范围内的任何位置。

大多数实现都支持标识列，尽管不一定使用 SQL 标准语法。生成的值保证在表内唯一，这使得它们很适合用作主键。在表的自然主键笨拙的情况下（例如，多个 `varchar` 列的组合），通常会引入标识列作为代理键。

SQL:1999 标准允许基于现有表定义创建表。SQL:2003 对此功能进行了细化，以提供对新表中应包含或排除哪些列的更精确控制。基本语法如下：

*   ```
    create table new-tablename like existing-tablename
    ```
*   ```
    [ { including identity | excluding identity } |
    ```
*   ```
    { including defaults | excluding defaults } |
    ```
*   ```
    { including generated | excluding generated } [,..] ]
    ```

`create table` … `like` … 语句的结果是一个空表，具有与原表相同的列名、数据类型和可空性。原表和新表之间不建立依赖关系。这些选项指定了对“特殊”列应采取的操作。

### 维护参照完整性

现在让我们更详细地讨论*参照完整性*的概念。回顾一下，参照完整性是子集约束的一种特殊情况。下面的关系模式大纲显示了一个典型情况，其中 `S.a` 是引用 `R.a` 的外键。基本上，如果 `S.a` 中的每个值要么作为 `R.a` 的值出现，要么为 `null`，则满足子集约束。

![](images/B9780443237904000049/u13-01-9780443237904.jpg)

子集约束可能以以下四种方式中的任何一种被违反：

1.  向 `S` 插入一行，其 `S.a` 的值不是 `R.a` 中的值
