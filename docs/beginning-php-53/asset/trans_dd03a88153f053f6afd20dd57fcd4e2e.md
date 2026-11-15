
## 创建 view_member.php 脚本

你需要创建的最后一个 PHP 文件是用于查看单个成员详细信息的脚本。将以下代码保存为 book_club 文件夹中的 view_member.php：

```
<?php
require_once( "common.inc.php" );
require_once( "config.php" );
require_once( "Member.class.php" );
require_once( "LogEntry.class.php" );

$memberId = isset( $_GET["memberId"] ) ? (int)$_GET["memberId"] : 0;

if ( !$member = Member::getMember( $memberId ) ) {
    displayPageHeader( "Error" );
    echo "<div>Member not found.</div>";
    displayPageFooter();
    exit;
}

$logEntries = LogEntry::getLogEntries( $memberId );
displayPageHeader( "View member: " . $member->getValueEncoded( "firstName" )
. " " . $member->getValueEncoded( "lastName" ) );
?>
<dl style="width: 30em;">
    <dt>Username</dt>
    <dd><?php echo $member->getValueEncoded( "username" ) ?> </dd>
    <dt>First name</dt>
    <dd><?php echo $member->getValueEncoded( "firstName" ) ?> </dd>
    <dt>Last name</dt>
    <dd><?php echo $member->getValueEncoded( "lastName" ) ?> </dd>
    <dt>Joined on</dt>
    <dd><?php echo $member->getValueEncoded( "joinDate" ) ?> </dd>
    <dt>Gender</dt>
    <dd><?php echo $member->getGenderString() ?> </dd>
    <dt>Favorite genre</dt>
    <dd><?php echo $member->getFavoriteGenreString() ?> </dd>
    <dt>Email address</dt>
    <dd><?php echo $member->getValueEncoded( "emailAddress" ) ?> </dd>
    <dt>Other interests</dt>
    <dd><?php echo $member->getValueEncoded( "otherInterests" ) ?> </dd>
</dl>
<h2>Access log</h2>
<table cellspacing="0" style="width: 30em; border: 1px solid #666;">
    <tr>
    <th>Web page</th>
    <th>Number of visits</th>
    <th>Last visit</th>
    </tr>
<?php
$rowCount = 0;

foreach ( $logEntries as $logEntry ) {
    $rowCount++;
?>
    <tr<?php if ( $rowCount % 2 == 0 ) echo ' class="alt"'; ?>>
        <td><?php echo $logEntry->getValueEncoded( "pageUrl" ) ?></td>
        <td><?php echo $logEntry->getValueEncoded( "numVisits" ) ?></td>
        <td><?php echo $logEntry->getValueEncoded( "lastAccess" ) ?></td>
    </tr>
<?php
}
?>
</table>

<div style="width: 30em; margin-top: 20px; text-align: center;">
    <a href="javascript:history.go(-1)">Back</a>
</div>

<?php
displayPageFooter();
?>
```

此脚本期望接收一个指定要显示成员的 `memberId` 查询字符串参数。该值随后传递给 `Member::getMember()`，以将记录检索为 `Member` 对象。如果对 `getMember()` 的调用未返回任何内容，则表示在 `members` 表中未找到该成员，因此会显示错误消息并退出脚本。

假设已找到并检索到成员，脚本随后会调用 `LogEntry::getLogEntries()`，再次传入成员 ID，以检索与该成员关联的 `accessLog` 表中的行（如果有的话）。

接下来，脚本在 HTML 定义列表（`dl`）元素中显示所有成员字段。这通常只需为每个字段调用 `Member::getValueEncoded()`，传入要检索的字段名称，并显示返回的值即可。对于性别和喜爱类型等特殊情况，会调用 `getGenderString()` 和 `getFavoriteGenreString()` 方法，以更易于人类阅读的格式显示字段值。

成员详细信息之后是访问日志条目。这些条目的显示方式与 `view_members.php` 脚本中的成员类似。对于每个日志条目，页面 URL、访问次数和上次访问日期都会显示在表格行中。最后，在页面末尾，会创建一个 JavaScript 链接，以允许用户返回成员列表页面。

## 测试应用程序

现在你已经为该应用程序创建了所有脚本，是时候尝试一下了。在 Web 浏览器中打开 `view_members.php` 脚本的 URL。你应该会看到一个类似于图 13-1 的页面。尝试使用“下一页”和“上一页”链接在页面之间导航（应该有两页），并通过单击列标题来更改排序顺序。

现在单击成员列表中的用户名。你将被带到 view_member.php 脚本，其外观应类似于图 13-2。单击“后退”链接以返回成员列表。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_438_0.png)

图 13-2

你现在已经朝着编写复杂的数据驱动型 PHP 应用程序迈出了坚实的一步。当然，下一步的逻辑是创建能够向数据库写入数据（而不仅仅是检索数据）的应用程序，你将在下一章中完成此操作。

## 总结

在本章中，你扩展了对 MySQL 和 PDO 的知识，并学习了如何创建能够从数据库表中读取数据并将数据显示给用户的 PHP 应用程序：

- 首先，你为本章中使用的虚构图书俱乐部数据库设置了表格。在此过程中，你探索了 BINARY 属性和区分大小写；用于强制列中唯一值的 UNIQUE 约束；用于创建具有少量可能值的字段的 ENUM 数据类型；以及用于自动记录记录创建或更新时间的 TIMESTAMP 数据类型
- 接下来，你更深入地了解了 SQL `SELECT` 语句。你学习了如何使用 `LIMIT` 来限制查询返回的行数，以及如何使用 `ORDER BY` 子句对结果集中的行进行排序。你了解了如何通过使用 `LIKE` 和 `NOT LIKE` 运算符使查询更加灵活，以及如何使用 `count()`、`sum()`、`min()`、`max()` 和 `avg()` 等函数来汇总表中的列
- 重复行在结果集中可能是个问题，你了解了如何通过使用 `DISTINCT` 关键字来解决这个问题。你还学习了如何通过使用 `GROUP BY` 子句按指定列或多列对结果进行分组
- 关系数据库的主要优势之一是，你可以一次从多个表中提取数据——这一过程称为 *连接* 表。你学习了如何执行此操作，还学习了如何使用别名来使查询和结果集更易于阅读
- 为了结束对 `SELECT` 查询的讨论，你探索了大量 MySQL 运算符和函数中的一些，你可以使用它们为查询增添更多威力

在本章的后半部分，你构建了一个成员查看器应用程序，该应用程序能够列出虚构图书俱乐部数据库中的所有成员，并查看每个成员的详细信息。在此过程中，你使用了抽象类，了解了如何创建用于处理数据库表访问的类，学习了 PDO 的一些更有用的功能，例如预处理查询，并发现了如何使用 MySQL 的 `SQL_CALC_FOUND_ROWS` 关键字来帮助你跨多个页面显示表内容。

你现在已经掌握了如何从 PHP 脚本构建查询并与 MySQL 通信的坚实基础。下一章将深入探讨如何在 PHP 内操作数据库中的数据。

同时，尝试下面的两个练习，它们将测试你的 SQL 查询技能和 PHP 编程技能。你可以在附录 A 中找到这些练习的答案。

## 练习

- 1. 编写一个 SQL 查询，计算图书俱乐部网站所有男性访问者的页面浏览总数，以及所有女性访问者的页面浏览总数。
- 2. 回到本章中创建的成员查看器应用程序，修改 `Member` 类的 `getMembers()` 方法，以允许一个可选的第四个参数 `$interest`。指定该参数时，该方法应仅返回其 `otherInterests` 字段包含 `$interest` 中提供的字符串的成员。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_440_0.png)

## 使用 PHP 操作 MySQL 数据

这是关于构建数据驱动型 PHP 应用程序主题的第三个也是最后一章。在第 12 章中，你掌握了 MySQL 和关系数据库的基础知识，并学习了如何使用 PDO（PHP 数据对象）从 PHP 连接到 MySQL 数据库。第 13 章探讨了在 PHP 脚本中从数据库检索数据的概念；你详细了解了如何创建 `SELECT` 查询，并编写了一个简单的记录查看器，用于显示图书俱乐部数据库中成员的详细信息。

在本章中，你将学习如何使用 PHP 更改 MySQL 数据库中的数据。这包括：

- 使用 `INSERT` 语句向表中插入新记录
- 使用 `UPDATE` 语句更改记录中的字段值
- 使用 `DELETE` 语句删除记录

你将详细探索这三种操作，并学习如何在 PHP 脚本中执行它们。

一旦你了解如何操作 MySQL 数据库中的数据，你将构建一个应用程序，允许新成员为你的图书俱乐部数据库注册并登录到你网站的仅限会员区域，并编写一些 PHP 代码，用于记录会员区域中每个成员的页面浏览量。最后，你将扩展在第 13 章中创建的成员记录查看器，以允许你编辑和删除成员记录。

### 插入记录

你在第 12 章和第 13 章中学习了如何使用 SQL 向表中添加记录。请记住，你可以使用以下语句插入一行数据：

```
`INSERT INTO table VALUES ( value1, value2, ... );`
```
