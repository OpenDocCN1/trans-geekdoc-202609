
## 连接

`SELECT` 语句中唯一有一点费力的是：连接。因为连接是 SQL 的有用功能之一，我们应该在这里详细解释它们。

不带连接的单表 `SELECT` 很容易被想象成类似于电子表格中的东西。虽然这并不是 SQL 数据库存储或安排数据的方式，但对于这个目的来说，它是一个方便的可视化工具。

但 SQL 查询从定义上说是关系的。要理解关系型数据库概念背后的哲学，你应该回想一下你曾被迫填写大量表格的时刻——例如申请贷款、第一次去诊所看病，或处理某种政府手续。（如果你从未经历过这种事情，意味着你足够年轻，生活在一个关系型数据库的世界里。）当你第 15 次填写你的姓名、地址、电话和社会安全号码时，你可能在想：“我不能只写下我的地址，然后他们可以在需要的时候查一下吗？”这正是关系型数据库背后的概念。

关系型数据库与纸质表格的区别在于主标识符。人类擅长处理文本，并倾向于通过文本标识符（如名称）进行分类。如果诊所或汽车修修理店按数字顺序存储纸质文件，那么当 John Johnson 下次需要服务时，任何人很难拿到他的表格。坦率地说，大多数纸质文件是按数字顺序排列的。

这种连接的另一种语法如下：

```
SELECT Fears.Fear
FROM (Fears INNER JOIN Person_Fear ON FearID JOIN People on PersonID)
WHERE Person.Name = 'Jane Jones';
```

如你所见，你只需要一条信息就可以获取数据库中关于主题连接的所有数据。实际上，连接是将两个或多个表合并为一个表，以便于搜索特定信息。

连接有几种不同的类型。上一个例子中的类型被称为**内连接**，它是最常见且限制性最强的类型。另一种常见类型是**外连接**（outer join）。它用于返回所有恐惧的列表，即使它们没有关联的人。在这个例子中，我们使用的是**左外连接**（也称为自然连接）：

```
SELECT Fear
FROM Fears LEFT JOIN People ON PersonID;
```

关联了人员的恐惧将会在数据集中出现多次，而没有关联人员的恐惧将只出现一次。

你也可以使用**右外连接**来获取没有关联恐惧的所有恐惧列表：

```
SELECT Name
FROM Fears RIGHT JOIN People ON PersonID;
```

同样，实际关联到人的恐惧会显示多次，而未被任何人遭受的恐惧在数据集中仍显示一次。右外连接的区别在于你想要从两个表中的哪一个获取实际数据：第一个（左）还是第二个（右）。由于你可以随意切换它们，许多人一律使用外连接来处理所有的外连接操作。

问问自己你是否真的需要使用外连接。因为外连接对格式的精确度要求较低，缺乏经验的 SQL 用户经常先执行外连接，然后在代码层中过滤结果。这是因为外连接会返回 `NULL` 值，而这些值无法被内连接轻易替换。外连接的一个良好用例是创建一个报告，你想查看哪些用户拥有过但没有下载你最新的软件产品，以及他们下载了多少次。如果你不在这种情况下，请改用内连接。

最后，如果你需要进行复杂且频繁的连接，这可能会限制你所使用的 SQL 数据库类型，因为并不是所有的数据库都支持每类型的连接。

## 子查询

在我们离开 `SELECT` 语句领域之前，我们应该提到子查询。这是一个如下的语句：

```
SELECT phone_number
FROM table
WHERE name = 'SELECT name FROM table2 WHERE ID = 1';
```

子查询与其说是一种便利，不如说是必需。当你处理大量批数据时，它们会非常有用；但你也可以通过简单的 `SELECT` 语句获得相同的结果。如果子查询从返回大型数据集，`select` 的速度会更快，但在某些情况下，两个 `select` 对性能不会产生显著影响。

## 插入

当然，如果你根本没有向数据库中放入任何信息，那么你使用多少次 `SELECT` 查询都是徒劳的。将新数据放入数据库的所需命令是 `INSERT`。

```
INSERT INTO table(col1, col2, col3) VALUES(val1, val2, val3);
```

显然，如果你搞乱了数组，列和它们的值就需要匹配，否则不会发生任何好结果。如果某些行的某些字段将没有值，你需要使用一个目项、`null` 或自动递增值——而且在更深的层面上，你必须预先确保字段是可以为空或可自动递增的。如果这不可行，你应该在 `INSERT` 语句中省略任何你希望默认为空值的列。

基础 `INSERT` 的变体是 `INSERT INTO...SELECT`。这意味着你可以插入一个 `SELECT` 语句的结果：

```
INSERT customer(birthmonth, birthflower, birthstone) SELECT * FROM
birthday_info WHERE birthmonth = $birthmonth;
```

并不是每个 SQL 数据库都有这种能力。此外，你需要对这个命令保持小心，因为你很容易引起问题——例如，你可以覆盖数据或遇到锁定问题。通常情况下，从你正在插入的数据库中查询并不是好主意。

## 更新

`UPDATE` 用于编辑数据库中已的信息，而不删除任何其他信息。在其他行中，你可以选择更改某些信息，而无需删除整个旧记录并插入新记录。其语法为：

```
UPDATE table
SET field1='val1', field2='val2', field3='val3'
WHERE condition;
```

条件语句与 `SELECT` 条件完全一样，例如 `WHERE ID>15 AND ID<21` 或 `WHERE gender='F'`。

## 删除

`DELETE` 相当自而易见。你用它从数据库中永久删除一个或多个记录的内容。其语法为：

```
DELETE datapoint
FROM table
WHERE condition;
```

最要重要的是条件——如果你不设置条件，你将从数据库中删除指定列中的每个条目，在许多情况下，还没有确认或第二次机会！

让我们再次强调：你每次执行 `UPDATE` 或 `DELETE` 时都必须记得使用条件！如果你没有，表中的每一行都将经历相同的更改或删除。即使是经验丰富的程序员也曾忘记包含条件，这为了避免他们巨大的职业尴尬。你还应该给予大量的数据库权限限制，以让尽可能少的人执行这些潜在危险的操作。

## 数据库设计

正如前一节显而易见的，学习使用 SQL 数据库并不是什么复杂的科学——你可以通过简单的命令完成很多工作。困难的部分是设计模式。在最基础的层，数据库设计可以分解为：

- 一对多，
- 一对多；
- 多对多，
- 多对一；

一对多的数据示例来自医学领域：患者与就诊。每个患者将始终是一个离散的个体，但可能有任何次数的就诊。

最后，多对多的数据可以通过作者与书籍之间的关系很好地表示。不仅某本书可以有多位作者，而且每个作者都可能共同创作过许多书。

### 表 13-5: 交互

| `Interaction_id` | `Type` |
| :--- | :--- |
| 1 | 电话支持事件 |
| 2 | 现场事件 |
| 3 | 书面投诉 |
| 4 | 电话投诉 |
| 5 | 赞扬 |

### 表 13-6: 客户交互

| `Customer_interaction_id` | `Customer_id` | `Interaction_id` |
| :--- | :--- | :--- |
| 1 | 1 | 1 |
| 2 | 3 | 5 |
| 3 | 2 | 4 |
| 4 | 2 | 3 |
| 5 | 1 | 2 |

在决定了数据库设计后，构建数据库的机械细节是非常非常少的。SQL 的主要数据结构语句是 `CREATE`、`ALTER`、`ALTER` 和 `DROP`。

`CREATE` 用于创建一个全新的表。所有的工作都在于定义每个表的列。首先，你声明表名，然后你必须在所谓的“创建定义”中详细说明该表列的具体数据类型。`CREATE` 语句具有以下形式：

```
CREATE TABLE tableName (
  id_col INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
  col1 TEXT NULL INDEX,
  col2 DATE NOT NULL
);
```

SQL 服务器的数据类型和定义选项略有不同，一种语言的语法可能无法完全迁移到另一种。Oracle 数据库不支持自增；要获取新值，你通常必须调用一个函数。

`DROP` 可完全删除一个表及其所有关联数据。它不是一个微妙的命令：

```
DROP TABLE tableName;
```

显然，你需要对这条语句非常小心。

`ALTER` 是更改表结构的方法。你只需指示你正在更改哪一个表并重新定义它的规格。同样，SQL 产品在功能方面存在差异。`ALTER` 语句通常采用以下形式：

```
ALTER table RENAME AS new_table;
ALTER table new_table ADD COLUMN col3 VARCHAR(50);
ALTER table new_table DROP COLUMN col12;
```

## 权限与安全

正如我们在第 29 章中所说的，网络安全类似于现实世界的安全。任何警察都会告诉你，你无法让你的房子绝对防范犯罪。一个更现实的目标是增加难度和风险，使得很大比例的闯入者会选择去街街另一头更容易攻击的目标。

在 PHP 中使用数据库类似于在你的正门上装两把锁，通过减少如系统文件写入等高风险操作，大幅增强了你网站的安全性——但前提是你至少遵循了数据库卫生的几个要素。PHP 让这些许多技术的实现变得容易了一些，这意味着你疏于大意的理由就更少了。

## 设置数据库权限

数据库使用的基本规则是只给每个用户或组提供完成所需任务的权限。你不会把陌生人带进你的家里，然后回你的卧室读你的日记——那么，你为什么要给他们提供在你网站上做类似事情的机会呢？管理多个用户并确保所有权限始终处于正确水平需要稍微费一点精力；但如果这微小的痛苦可以防止严重的感染，拒绝这种简单有效的预防措施将是极其愚蠢的。

除了恶意/实验性外部人员的威胁，设置正确的权限还可以保护你免受同事和自身的伤害。众内部人员已知因分歧、无知、一瞬间的大脑空白或多种动机的结合而引发巨大的问题。你不想去应对离职员工离开时的后果，或者一个新实习生尝试 `DROP` 数据库命令看看会发生什么。

一个典型的数据库权限包可能如下：

- 访问者: 仅 `SELECT`
- 贡献者: `SELECT`, `INSERT`，可能还有 `UPDATE`
- 编辑者: `SELECT`, `INSERT`, `UPDATE`，可能还有 `DELETE` 和 `GRANT`
- 根用户: `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `GRANT` 和 `DROP`

`DROP` 特别是 SQL 中的核原子弹，因为它允许你用一条命令炸掉整个表或数据库。必须有人拥有这种能力，但责任的重王冠在数据库根用户身上。明智地使用它，小青虫。

在许多数据库（包括 MySQL）中，密码的加密算法与系统密码不同（当然，它们通常存储在完全不同的位置）。即使其中一个被破解了，另一个也不一定会危险。这假设你花时间正确设置权限、选择良好的密码，并且通常使用特殊命令将用户名和密码正确插入授权表（而不是作为其他数据插入）。

**注意**

数据库用户名和密码不应与系统用户名和密码相同。永远、永远、永远不要将任何数据库密码设置为根系统用户的密码！如果黑客追逐通过 Web 脚本进入你的数据库，你可不想把它们暴露给整个系统。

第 14 章专门针对 MySQL 的权限。

## 将数据库密码保存在 Web 树之外

将密码与使用它们的 Web 页面分离是一个好主意。通过 PHP 的 `include()`/`include_once()` 和 `require_once()` 函数，可以很容易在运行时从另一个文件中引入文本（如数据库密码）。记住，这些包含的文件不必非位于 PHP 或启用了 Web 服务器的目录中！尽可能将它们保持在 Web 树之外，例如在 Web 根目录以上的目录或主目录下。

将变量从 PHP 文件中提取出来对其他人也有好处。如果你有许多 PHP 脚本使用相同的密码，可以将密码放在不可读的目录中。

这种做法的缺点是该文件必须是不可访问的。如果你有许多 PHP 脚本使用相同的密码，可以将密码放在不可读的目录中。

从 PHP5 开始，MySQL 错误不再显示。两个函数 `mysql_errno()` 和 `mysql_error()` 允许你选择显示错误，除非你严谨地使用 `error_log()` 函数将消息发送到错误日志，而不是标准输出。

## 使用两层保护

Band-and-suspend 可以通过存储在数据库中的另一轮用户名和密码为其最敏感的 PHP 脚本增加另一层保护，你可以直接从脚本中进行检查。

这是一个检查数据库密码的典型形式：

```html
<HTML>
<BODY>
<FORM METHOD="POST" ACTION="form_check.php">
<P>用户名:<INPUT TYPE="TEXT" SIZE=20 NAME="try_user"></P>
<P>密码:<INPUT TYPE="PASSWORD" SIZE=10 name="try_pass"></P>
<P>日期:<INPUT TYPE="TEXT" SIZE=10 NAME="try_date"></P>
<P>条目:<BR>
<TEXTAREA COL=50 ROWS=10 NAME="try_entry"></TEXTAREA></P>
<P><INPUT TYPE="SUBMIT"></P>
</FORM>
</BODY>
</HTML>
```

此文件是前一个表单 `ACTION` 中处理的文件，`form_check.php`。

```php
<?php
// Unix 用户
if ($REMOTE_ADDR != '127.0.0.1') {
    die();
}
// 检查数据库用户
// Webvars.inc 是一个包含 $host, $db_user 和 $password
// 值的文件
include('/home/phpuser/Webvars.inc');
mysql_connect($hostname, $db_user, $password)
or die("你不是我要找的数据库用户");
mysql_select_db('captainslog');
// 检查表单用户
$post_try_user = $_POST['try_user'];
$post_try_date = $_POST['try_date'];
$post_try_entry = $_POST['try_entry'];
$query = "SELECT password
FROM finalcheck
WHERE user='post_try_user';
$result = mysql_query($query);
$passcheck = mysql_fetch_array($result);
if($passcheck['D'] == $_POST['try_pass']) {
    // New entry
    $query = "INSERT INTO captainslog (ID, date, entry)
VALUES(NULL, 'post_try_date', 'post_try_entry');";
    $result = mysql_query($query);
    print("New entry result is $result.");
} else {
    mail('security@localhost', 'Database alert.',
    $REMOTE_ADDR " is trying to get into your captain's log.");
}
```
