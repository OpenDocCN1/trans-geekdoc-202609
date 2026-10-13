
![Image](graphics/circle-f.jpg)填充 `messages` 表需要了解来自 `users` 和 `forums` 表的外键值。

由于 `messages` 表中的两个字段（`forum_id` 和 `user_id`）关联到其他表中的值，因此在向该表插入新记录之前，你需要知道这些值。例如，当用户 `troutster` 在 `MySQL` 论坛创建一条新消息时，`INSERT` 语句将包含 `forum_id` 为 1 和 `user_id` 为 1。

`parent_id` 列使情况变得更加复杂，它应存储新消息所回复的那条消息的 `message_id`。添加到数据库的第二条消息将拥有 `message_id` 为 2，因此对该消息的回复需要 `parent_id` 为 2。

有了你的 PHP 脚本——一旦你为该数据库创建了界面，这个过程将容易得多，但首先理解 SQL 层面的理论很重要。

对于 `date_entered` 字段，将使用 `UTC_TIMESTAMP()` 函数返回的值。使用 `UTC_TIMESTAMP()` 函数，记录将存储 UTC 日期和时间，而非服务器上的日期和时间。

**6.** 重复步骤 1 到 3 以填充数据库。

本章和下一章的其余示例将使用已填充的数据库。你可能想从本书对应的网站下载 SQL 命令，尽管你也可以使用自己的示例填充表，然后只需相应地更改本章其余部分的查询即可。

**7.** 使用存储的日期和时间查看 `messages` 表中最近的一条记录 ![Image](graphics/circle-g.jpg)：

```sql
SELECT message_id, subject, date_entered FROM messages
ORDER BY date_entered DESC LIMIT 1;
```

![Image](graphics/06_figure_26_g.jpg)

![Image](graphics/circle-g.jpg)刚刚插入的记录，显示的时间超前四小时（服务器为 UTC-4）。

正如你在图表和表定义中所见，UTC 时间的存储方式与非 UTC 时间完全相同。图表中不明显的是，刚插入的记录反映的时间比服务器时间超前四小时（因为我特定的服务器位于比 UTC 晚四小时的时区）。

**8.** 检索同一记录，并将 `date_entered` 转换为你的时区 ![Image](graphics/circle-h.jpg)：

```sql
SELECT message_id, subject,
CONVERT_TZ(date_entered, 'UTC', 'America/New_York') AS local
FROM messages ORDER BY date_entered DESC LIMIT 1;
```

![Image](graphics/06_figure_27_h.jpg)

![Image](graphics/circle-h.jpg)存储的 UTC 日期和时间已转换为我的本地时间。

使用 `CONVERT_TZ()` 函数，你可以将任何日期和时间转换为不同的时区。对于 `from` 时区，使用 `UTC`。对于 `to` 时区，使用你的时区。

如果得到 `NULL` 结果 ![Image](graphics/graycircle-b.jpg)，则可能是你的某个时区名称错误，或者 MySQL 尚未加载时区表（见侧栏）。

***

提示

无论你决定如何处理日期，关键在于**保持一致**。如果你决定使用 UTC，则*始终*使用 UTC。

***

***

提示

UTC 也称为**祖鲁时间**，用字母 *Z* 表示。

***

***

提示

除了与时区和夏令时无关外，UTC 也更精确。它考虑了不规则的闰秒，以补偿地球运动的不精确性。

***

### 外键约束

InnoDB 表类型的一项特性（其他存储引擎不支持）是应用*外键约束*的能力。当你拥有相关联的表时，表 B 中的外键关联到表 A 中的主键（为便于理解，可以将表 B 视为子表，表 A 视为父表）。例如，在 `forums` 数据库中，`messages.user_id` 关联到 `users.user_id`。如果管理员删除一个用户账户，这些表之间的关系就会被破坏（因为 `messages` 表将拥有 `users` 表中不存在的 `user_id` 值的记录）。外键约束设定了当这种破坏发生时应采取的规则，包括防止这种破坏。

创建外键约束的语法是：

```sql
FOREIGN KEY (item_name) REFERENCES table (column)
```

（这放在 `CREATE TABLE` 或 `ALTER TABLE` 语句中。）

项名是当前表中的外键列。`table(column)` 子句引用了该外键应约束到的父表列。如果你仅使用上述语法，即仅标识关系而不指定违反约束时应发生什么，MySQL 将在你尝试删除存在子记录的父记录时抛出错误 ![Image](graphics/circle-a.jpg)。如果你尝试使用不存在的父 ID 创建子记录，MySQL 也会抛出错误 ![Image](graphics/circle-b.jpg)。

![Image](graphics/06_figure_28_a.jpg)

![Image](graphics/circle-a.jpg)此错误表明 MySQL 正阻止删除父记录的查询，因为该记录被约束到一个或多个现有的子记录。

![Image](graphics/06_figure_29_b.jpg)

![Image](graphics/circle-b.jpg)外键约束也会影响 `INSERT` 查询。

你可以通过在上述语法后跟随以下一项或两项来规定应发生的替代操作：

```sql
ON DELETE action
ON UPDATE action
```

有五个操作选项，但其中两个——`RESTRICT` 和 `NO ACTION`——是同义词，也是默认值（即与完全不指定操作相同）。第三个操作选项——`SET DEFAULT`——不起作用（别问我，去问 MySQL 手册！）。剩下的就是 `CASCADE` 和 `SET NULL`。如果操作设为 `SET NULL`，删除父记录将导致子表中对应的外键被设为 `NULL`。如果该表将该列定义为 `NOT NULL`（几乎总是应该这样定义），删除父记录将触发错误。

`CASCADE` 操作是最有用的选项。它告诉数据库对相关表应用相同的更改。有了这条指令，如果你删除父记录，MySQL 也将删除具有该父 ID 作为外键的子记录。

由于只有 InnoDB 表类型支持外键约束，关系中的两个表都必须是 InnoDB 类型。此外，为了让 MySQL 能够比较外键-主键值，相关列必须是兼容的类型。这意味着数值列必须是相同的类型和大小；文本列必须使用相同的字符集和排序规则。

以 `forums` 示例为例，无法使用外键约束，因为唯一关联到另一个表的表——`messages` 同时关联 `forums` 和 `users`——必须使用 MyISAM 表类型（以支持 `FULLTEXT` 搜索）。相反，让我们看一个用于银行业务的新假设示例 ![Image](graphics/circle-c.jpg)。

![Image](graphics/06_figure_30_c.jpg)

![Image](graphics/circle-c.jpg)`banking` 数据库可用于虚拟银行业务。
