
在许多英文键盘布局中，反引号键位于数字 `1` 键的正左侧并且在 `Esc` 键下方。在非英文键盘和/或各种设备（如笔记本电脑和平板电脑）上，其位置可能会有所不同。

## 查看存储的数据

我们用来查看数据库表中存储数据的命令是 `SELECT`。你之前看到过由 MySQL Workbench 为你生成的示例 `SELECT` 查询。`SELECT` 查询是 SQL 中最复杂的命令。之所以如此复杂，是因为数据库的主要优势在于其数据检索的灵活性。在我们使用数据库的这个早期阶段，我们只需要关注相当简单的结果列表，因此这里让我们考虑 `SELECT` 命令的更简单形式。

该命令将列出 `joke` 表中存储的所有内容：

```
SELECT * FROM `joke`
```

该命令的意思是“从 joke 中选择所有内容”，其中 `*` 表示“所有列”。默认情况下，`SELECT` 查询会返回表中的每一条记录。如果你尝试此命令，你的结果将类似于下图。

![MySQL Workbench 结果](Images/mysql-workbench-results.png)

注意 `id` 列中存在一些值，即使你在之前运行的 `INSERT` 查询中并未指定它们。MySQL 已自动为笑话分配了 ID。这是因为你在创建表时勾选了“AI”（自动递增）复选框。如果你没有勾选该框，你就需要为插入的每个笑话指定 ID。

如果你在这样的数据库上进行严肃的工作，你可能会想停下来阅读数据库中所有有趣的笑话。为了避免分心，你可能希望告诉 MySQL 省略 `joketext` 列。执行此操作的命令如下：

```
SELECT `id`, `jokedate` FROM joke
```

这次，我们没有告诉它“选择所有内容”，而是精确地告诉它我们想要查看哪些列。结果应如下图所示。

![你可以选择所需的内容](Images/mysql-workbench-select-columns.png)

如果我们想查看 *部分* 笑话文本怎么办？除了能够指定我们希望 `SELECT` 命令显示的特定列外，我们还可以使用函数来修改每列的显示方式。其中一个函数名为 `LEFT`，它使我们能够告诉 MySQL 显示列内容最多指定数量的字符。例如，假设我们只想查看 `joketext` 列的前 20 个字符。这里是我们将使用的命令：

```
SELECT `id`, LEFT(`joketext`, 20), `jokedate` FROM `joke`
```

![LEFT 函数将文本修剪到指定长度](Images/mysql-workbench-select-left.png)

看到它是如何工作的吗？另一个有用的函数是 `COUNT`，它可以让我们统计返回的结果数量。例如，如果你想知道表中存储了多少个笑话，你可以使用以下命令：

```
SELECT COUNT(`id`) FROM `joke`
```

正如你在下图中所看到的，你的表中只有两个笑话。

![COUNT 函数统计行数](Images/mysql-workbench-count.png)

### 改用 *

你可以使用 `COUNT(*)` 得到相同的结果，但这样会更慢，因为所有列都将被从表中选取。通过使用主键，只需要检索一列。

到目前为止，我们查看的示例都获取了表中的所有条目。然而，你可以将结果限制为仅具有你想要的特定属性的数据库条目。你通过向 `SELECT` 命令添加所谓的 `WHERE` 子句来设置这些限制。请考虑以下示例：

```
SELECT COUNT(*) FROM `joke` WHERE `jokedate` >= "2021-01-01"
```

此查询将统计日期大于或等于 2021 年 1 月 1 日的笑话数量。对于日期而言，“大于或等于”意味着“在...之后或当天”。此主题的另一个变体允许你搜索包含特定文本的条目。查看此查询：

```
SELECT `joketext` FROM `joke` WHERE `joketext` LIKE "%programmer%"
```

此查询显示 `joketext` 列中包含文本“programmer”的所有笑话的完整文本。`LIKE` 关键字告诉 MySQL 命名列必须与给定的模式匹配。在本例中，我们使用的模式是 `"%programer%"`。`%` 符号（称为 **通配符**）表示文本“programmer”前面和/或后面可能跟随任意字符串的文本。（有趣的是，`LIKE` 不区分大小写，因此此模式也将匹配包含“Programmer”甚至“FuNkYProGRammeR”的笑话。）

`WHERE` 子句中也可以组合条件以进一步限制结果。例如，仅显示 2021 年 4 月的敲门笑话，你可以使用以下查询：

```
SELECT `joketext` FROM `joke` WHERE
`joketext` LIKE "%knock%" AND
`jokedate` >= "2021-04-01" AND
`jokedate` < "2021-05-01"
```

在表中输入一些更多笑话。（例如，“程序员为什么辞职？他得不到数组。”）然后尝试使用 `SELECT` 查询。

你可以用 `SELECT` 命令做很多事情，所以我鼓励你非常熟悉它。我们稍后在需要时再查看其更高级的功能。

## 修改存储的数据

在向数据库表输入数据后，你可能会发现想要更改它。无论是纠正拼写错误，还是更改附加到笑话的日期，此类修改都是使用 `UPDATE` 命令进行的。该命令包含 `SELECT` 和 `INSERT` 命令的元素，因为该命令既挑选出要修改的条目，又设置列值。`UPDATE` 命令的一般形式如下：

```
UPDATE `tableName` SET
  `colName` = newValue, …
WHERE conditions
```

例如，如果我们想更改之前输入的笑话的日期，我们将使用以下命令：

```
UPDATE `joke` SET `jokedate` = "2021-04-01" WHERE id = "1"
```

这里 `id` 列派上了用场，使你能够轻松地单独选出一个笑话进行更改。这里使用的 `WHERE` 子句的工作方式与在 `SELECT` 命令中相同。例如，下一个命令会更改所有包含单词“programmer”的条目的日期：

```
UPDATE `joke` SET `jokedate` = "2021-04-01"
WHERE `joketext` LIKE "%programmer%"
```

### WHERE 是可选的

信不信由你，`UPDATE` 命令中的 `WHERE` 子句是可选的。因此，在输入此命令时你应非常小心！如果你省略 `WHERE` 子句，`UPDATE` 命令将应用于 *表中的所有条目*。

以下命令将为表中的所有记录设置日期！

```
UPDATE `joke` SET `jokedate` = "2021-04-01"
```

## 删除存储的数据

在 SQL 中删除条目是危险地简单，这你可能已经注意到是一个反复出现的主题。这里是命令语法：

```
DELETE FROM `tableName` WHERE conditions
```

要从表中删除所有程序员笑话，你将使用以下查询：

```
DELETE FROM `joke` WHERE `joketext` LIKE "%programmer%"
```

### 再次，WHERE 是可选的

与 `UPDATE` 一样，`DELETE` 命令中的 `WHERE` 子句也是可选的。因此，在使用它时你应非常小心。如果你省略 `WHERE` 子句，`DELETE` 命令将应用于 *表中的所有条目*。

以下命令将一次性清空 joke 表：

```
DELETE FROM `joke`
```

可怕吧？

## 让 PHP 来输入

MySQL 数据库服务器软件和 SQL 的内容远不止我在此介绍的少数基本命令，但这些命令无疑是最常用和最有用的！

在此时，你可能会认为数据库似乎有点笨重。SQL 打字起来可能很棘手，因为与其它计算机语言相比，其命令往往很长且冗长。你可能正担心输入一个完整的笑话库的想法，这些笑话以 `INSERT` 命令的形式出现。
