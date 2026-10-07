
假设成员已找到并检索到，脚本调用 `LogEntry::logEntries()`，再次传递成员 ID 以检索与该成员相关的访问表行。接下来，脚本在 HTML `dl` 元素内部显示所有成员。大多数情况下，使用 `Member::getValueEncoded()` 处理每个字段。对于性别（gender）和喜好（favorite genre）的特殊情况，调用了 `getGender()` 和 `getFavoriteGenre()` 方法以更易于人类阅读的格式显示字段。

访问记录以以 `view_members.php` 脚本类似的方式显示。对于每个条目，URL、访问次数和访问日期显示在表格中。最后，在页面末尾创建一个 JavaScript 链接，允许用户返回成员列表。

# 测试应用程序

现在你已经创建了应用程序的所有脚本，是时候尝试一下了。在 浏览器中打开 `view_members.php` 脚本，你会看到一个类似于图13-1 的页面。尝试使用“下一页”和“上一页”链接在页面之间移动，并通过点击列标题更改排序顺序。

# 第十三章：使用 PHP 从 MySQL 检索数据

现在你点击成员列表中的用户名，你将被带到 `view_member.php` 脚本，它应该类似于图13-2。点击“返回”链接返回成员列表。

![](img/ede05b7b7796b82cbd9a5122fb183_438_0.png)

图 13-2

你现在处于编写复杂的数据库驱动 PHP 应用程序的良好道路上。逻辑下一步是创建一个可以向数据库写入数据而不仅仅是检索数据的应用程序，你将在下一章完成此任务。

## 总结

在本章中，你扩展了对 MySQL 和 PDO 的知识，并学习了创建能够从数据库表读取数据并显示给用户的 PHP 应用程序：

首先，你为整个章节中使用的虚拟书俱乐部数据库设置了表。在此过程中，你探索了 `BINARY` 属性及其大小写敏感性；`UNIQUE` 约束用于强制列中的唯一值；`ENUM` 数据类型用于创建少量可能值的字段；以及 `TIMESTAMP` 数据类型用于自动记录记录创建或更新的时间。

# 第三部分：使用 PHP 练习

接下来，你更仔细地查看了 SQL `SELECT` 语句。学习了如何使用 `LIMIT` 来限制查询返回的行数，以及如何使用 `ORDER` 子句对结果集的行进行排序。通过使用 `LIKE` 和 `NOT LIKE` 运算符让查询更加灵活，并学习了如何使用 `count()`、`sum()`、`min()` 和 `avg()` 等函数来汇总列。

重复行在结果集中可能是一个问题，你看到了如何通过 `DISTINCT` 关键字来解决这个问题。你还学习了如何通过 `GROUP BY` 根据指定的列或多个列对结果进行分组。

关系型数据库的优势之一是可以一次从多个表中提取数据——这一过程被称为表连接。你学习了如何这样做，以及如何使用别名让查询和结果集更具可读性。

为了结束 `SELECT` 查询，你探索了许多可以增强查询功能的 MySQL 运算符和函数。

在章节的后半部分，你将构建一个成员查看应用程序，它能够列出虚拟书俱乐部数据库中的所有成员，并查看每个成员的详细信息。在此过程中，你使用了类（classes），学习了如何创建处理数据库访问的类，使用了 PDO 最实用的功能如预处理查询（prepared queries），并发现了如何使用 MySQL 的 `SQL_CALC_FOUND_ROWS` 关键字来帮助你在多个页面上显示表内容。

你现在已经有了通过 PHP 脚本构建查询并与 MySQL 通信的坚实基础。下一章将更进一步，探讨如何从 PHP 操作数据库中的数据。

同时，请尝试以下两个练习，它们将同时测试你的 SQL 查询技能和 PHP 编程技能。你可以在附录 A 中找到这些练习的答案。

### 练习

- 1. 写一个 SQL 查询来计算书俱乐部网站所有男性访问者的页面总数，以及所有女性访问者的页面总数。
- 2. 参考你在本章中创建的成员查看应用程序，修改 `Member` 类的 `getMembers()` 方法，允许一个可选的第四参数 `$interest`。当提供此参数时，该方法应只返回 `otherInterests` 字段包含 `$interest` 字符串的成员。

# 使用 PHP 操作 MySQL 数据

这是关于构建数据库驱动 PHP 应用程序主题的第三也是最后一个章节。在第12章中，你掌握了 MySQL 和关系型数据库的基础知识，并学习了如何使用 PDO（PHP Data Objects）从 PHP 连接 MySQL 数据库。十三章探讨了在 PHP 脚本中从数据库检索数据的概念；你详细学习了如何创建 `SELECT` 查询，并为书俱乐部数据库中的成员编写了一个简单的记录查看器。

# 第 14 章：使用 PHP 操作 MySQL 数据

```php
try {
$conn = new PDO($dsn, $username, $password);
$conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ATTR_ERRMODE_EXCEPTION);
} catch (PDOException $e) {
    echo "Connection failed: " . $e->getMessage();
}
```

```php
$id = 8;
$username = "derek";
$password = "mypass";
$firstName = "Derek";
$lastName = "Winter";
$joinDate = "2008-06-25";
$gender = "m";
$favoriteGenre = "crime";
$emailAddress = "derek@example.com";
$otherInterests = "Watching TV, racing";
```

```php
$sql = "INSERT INTO members VALUES (:id, :username, :password, :firstName, :lastName, :joinDate, :gender, :favoriteGenre, :emailAddress, :otherInterests)";

try {
    $stmt = $conn->prepare($sql);
    $stmt->bindValue(":id", $id, PDO::PARAM_INT);
    $stmt->bindValue(":username", $username, PDO::PARAM_STR);
    $stmt->bindValue(":password", $password, PDO::PARAM_STR);
    $stmt->bindValue(":firstName", $firstName, PDO::PARAM_STR);
    $stmt->bindValue(":lastName", $lastName, PDO::PARAM_STR);
    $stmt->bindValue(":joinDate", $joinDate, PDO::PARAM_STR);
    $stmt->bindValue(":gender", $gender, PDO::PARAM_STR);
    $stmt->bindValue(":favoriteGenre", $favoriteGenre, PDO::PARAM_STR);
    $stmt->bindValue(":emailAddress", $emailAddress, PDO::PARAM_STR);
    $stmt->bindValue(":otherInterests", $otherInterests, PDO::PARAM_STR);
    $stmt->execute();
} catch (PDOException $e) {
    echo "Query failed: " . $e->getMessage();
}
```

在这个示例中，变量值是在脚本中硬编码的。在实际应用中，你将从脚本外部接收这些值，例如通过 `$_POST` 超局变量数组提交的值。

请记住，虽然使用预处理语句和占位符可以提供免受 SQL 攻击的保护，但在对用户输入进行任何操作（例如存储到数据库）之前，你应该始终进行检查或过滤。你可以在第 20 章中了解更多关于此类及安全相关的问题。

## 更新记录

正如你在第 12 章中看到的，你可以使用 SQL `UPDATE` 语句更改现有表行中的数据：

```sql
mysql UPDATE fruit SET name = 'grapefruit', color = 'yellow' WHERE id = 2;

Query OK, 1 row affected (0.29 sec)
Rows matched: 1 Changed: 1 Warnings: 0

mysql SELECT * from fruit;
```

| id | name | color |

| :--- | :--- | :--- |

| 1 | banana | yellow |

| 2 | grapefruit | yellow |

| 3 | plum | purple |

3 rows in set (0.00 sec)

在插入新记录时，如果你在 `UPDATE` 语句中传递值，则通过 `PDO::query()` 使用 PHP 脚本更新记录是一个简单的情况；如果你传递的是变量，则使用带有占位符的 `PDO::prepare()`。例如，以下脚本更改了在后续节添加的 "Derek Winter" 记录中的电子邮件地址字段：

```php
<?php
$dsn = "mysql:dbname=database";
$username = "root";
$password = "myapp";

try {
    $conn = new PDO($dsn, $username, $password);
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ATTR_ERRMODE_EXCEPTION);
} catch (PDOException $e) {
    echo "Connection failed: " . $e->getMessage();
}

$id = 8;
$newEmailAddress = "derek.winter@example.com";

$sql = "UPDATE members SET emailAddress = :emailAddress WHERE id = :id";

try {
    $stmt = $conn->prepare($sql);
    $stmt->bindValue(":id", $id, PDO::PARAM_INT);
    $stmt->bindValue(":emailAddress", $newEmailAddress, PDO::PARAM_STR);
    $stmt->execute();
} catch (PDOException $e) {
    echo "Query failed: " . $e->getMessage();
}

?>
```

## 删除记录

通过 PHP 删除行的过程与更新过程相似。第 12 章向你展示了如何使用 SQL `DELETE` 关键字从从删除删除行：

```sql
mysql> DELETE FROM fruit WHERE id = 2;
Query OK, 1 row affected (0.02 sec)
```

使用 PHP 删除行时，你直接通过 `PDO::query()` 传递 `DELETE` 语句，或者使用 `PDO::prepare()` 创建带有占位符的语句，通过 `PDOStatement::bindValue()` 传递值（`WHERE` 子句的条件），并运行 `PDOStatement::execute()` 执行查询。

以下脚本删除了 `members` 表中 ID 为 8 的成员记录：

```php
<?php
$dsn = "mysql:dbname=mydatabase";
$username = "root";
$password = "myapp";

try {
  $conn = new PDO($dsn, $username, $password, array(PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION));
} catch (PDOException $e) {
  echo "Connection failed: " . $e->getMessage();
}

$id = 8;
$sql = "DELETE FROM members WHERE id = :id";

try {
  $stmt = $conn->prepare($sql);
  $stmt->bindValue(":id", $id, PDO::PARAM_INT);
  $stmt->execute();
} catch (PDOException $e) {
  echo "Query failed: " . $e->getMessage();
}

?>
```

顺便提一下，与其使用 `PDOStatement::bindValue()` 将变量的值绑定到占位符，你还可以使用 `PDOStatement::bindParam()` 绑定变量本身。如果你在调用 `bindParam()` 后更改了变量的值，占位符的值将自动更新为新值（换句话说，是通过引用而非按值）。如果你不确定在准备语句时将传递什么值，这会非常有用。你可以在在线 PHP 手中找到更多关于 `bindParam()` 的信息：http://www.php.net/manual/en/pdostatement.bindparam.php。

## 构建成员注册应用程序

现在你已经知道如何通过 PHP 向 MySQL 表插入记录了，你可以编写一个脚本让新成员加入你的书社俱乐部。与其重复发明轮，不如基于你在第 13 章创建的面向对象的成员查看器进行构建，扩展类以添加新功能，并创建一个注册新成员的脚本。

### 添加更多公共代码

首先，为 `book_club` 文件夹中的 `common.inc.php` 文件添加一些额外代码。在编辑器中打开此文件。

在该文件中，包含应用程序其他部分使用的公共文件是有。这样脚本只需要包含 `common.inc.php`，其他文件就会自动包含。将以下内容添加到 `common.inc.php` 的开头：

现在将以下内容添加到 `displayPageHeader()` 函数的 CSS 声明中：

```css
<style type="text/css">
th { text-align: left; background-color: #bbb; }
td, th { padding: 0.4em; }
tr.alt { background: #ddd; }
.error { color: red; }
</style>
```

最后，添加三个额外的实用函数来帮助显示注册表单：

```php
function validate($fieldName, $missingFields) {
    if (in_array($fieldName, $missingFields)) {
        echo ' class="error";';
    }
}

function setChecked($obj, $fieldName, $fieldValue) {
    if ($obj->getValue($fieldName) == $fieldValue) {
        echo ' checked="checked";';
    }
}

function setSelected($obj, $fieldName, $fieldValue) {
    if ($obj->getValue($fieldName) == $fieldValue) {
        echo ' selected="selected";';
    }
}
```

# 第三部分：在实践中使用 PHP

```php
$stmt = $conn->prepare($sql);
$stmt->bindValue(":emailAddress", $emailAddress, PDO::PARAM_STR);
$stmt->execute();
$row = $stmt->fetch();
parent::disconnect($conn);
if ($row) return new Member($row);
catch (PDOException $e) {
    parent::disconnect($conn);
    die("Query failed: " . $e->getMessage());
}
```

这些方法自而易明。你可以看到它们的工作方式与你在上一章中创建的 `getMember()` 相同。

接下来，添加一个方法 `getGenres()`，它简单地获取私有属性 `$_genres` 中的值。这将用于为潜在成员显示类型列表供其选择。在类文件的现有 `getGenreString()` 方法下方插入插入：

```php
public function getGenres() {
    return $this->genres;
}
```

到目前为止，该类包含了从 `members` 表中检索记录的方法。现在你将添加一个新方法 `insert()`，用于向表中添加新成员。将以下代码添加到类文件的末尾，紧挨结束类的大括号之前：
