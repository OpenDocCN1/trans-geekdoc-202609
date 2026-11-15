

如果你只想插入某些字段的值，其余字段留空 NULL 或其他默认值，请使用：

```sql
INSERT INTO table ( field1, field2, ... ) VALUES ( value1, value2, ... );
```

虽然第一种方法简洁，如果你想填充行中的所有字段，它也是完全有效的，但第二种方法通常更灵活、更易读。

那么如何在 PHP 脚本中插入记录呢？你以与传递 SELECT 语句类似的方式，通过 PDO 将 INSERT 语句传递给 MySQL。如果你不想从任何 PHP 变量传递数据，可以使用更简单的 PDO::query() 方法——例如：

```php
<?php
$dsn = "mysql:dbname=mydatabase";
$username = "root";
$password = "mypass";

try {
  $conn = new PDO( $dsn, $username, $password );
  $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
} catch ( PDOException $e ) {
  echo "Connection failed: " . $e->getMessage();
}

$sql = "INSERT INTO members VALUES ( 8, 'derek', password('mypass'), 'Derek',
  'Winter', '2008-06-25', 'm', 'crime', 'derek@example.com', 'Watching TV,
  motor racing' )";

try {
  $conn->query( $sql );
} catch ( PDOException $e ) {
  echo "Query failed: " . $e->getMessage();
}
?>
```

请注意，尽管 $conn->query() 调用仍然返回一个 PDOStatement 对象，但在这种情况下该对象会被丢弃。没有结果集可供检查，因此无需保留 PDOStatement 对象。

但是，你很可能确实想插入存储在 PHP 变量中的数据。例如，如果会员刚刚使用注册表单注册，你会希望将表单数据传递给 INSERT 语句以添加会员记录。最安全的方法是使用 PDO::prepare() 创建预处理语句，就像你在上一章处理 SELECT 查询时所做的那样。然后，你可以在查询字符串中为要插入的每个字段值使用占位符，并通过调用 PDOStatement::bindValue() 将数据传递给查询。例如：

```php
<?php
$dsn = "mysql:dbname=mydatabase";
$username = "root";
$password = "mypass";

try {
$conn = new PDO( $dsn, $username, $password );
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
} catch ( PDOException $e ) {
echo "Connection failed: " . $e->getMessage();
}

$id = 8;
$username = "derek";
$password = "mypass";
$firstName = "Derek";
$lastName = "Winter";
$joinDate = "2008-06-25";
$gender = "m";
$favoriteGenre = "crime";
$emailAddress = "derek@example.com";
$otherInterests = "Watching TV, motor racing";

$sql = "INSERT INTO members VALUES ( :id, :username, password(:password),
:firstName, :lastName, :joinDate, :gender, :favoriteGenre, :emailAddress,
:otherInterests )";

try {
$st = $conn->prepare( $sql );
$st->bindValue( ":id", $id, PDO::PARAM_INT );
$st->bindValue( ":username", $username, PDO::PARAM_STR );
$st->bindValue( ":password", $password, PDO::PARAM_STR );
$st->bindValue( ":firstName", $firstName, PDO::PARAM_STR );
$st->bindValue( ":lastName", $lastName, PDO::PARAM_STR );
$st->bindValue( ":joinDate", $joinDate, PDO::PARAM_STR );
$st->bindValue( ":gender", $gender, PDO::PARAM_STR );
$st->bindValue( ":favoriteGenre", $favoriteGenre, PDO::PARAM_STR );
$st->bindValue( ":emailAddress", $emailAddress, PDO::PARAM_STR );
$st->bindValue( ":otherInterests", $otherInterests, PDO::PARAM_STR );
$st->execute();
} catch ( PDOException $e ) {
echo "Query failed: " . $e->getMessage();
}

?>
```

在这个示例中，变量值已在脚本中硬编码。在实际应用中，你当然会从脚本外部接收这些值，例如通过 `$_POST` 超全局数组中的提交表单值。

请记住，尽管使用预处理语句和占位符可以防范 SQL 注入攻击，但在对用户输入做任何操作（例如将其存储在数据库中）之前，你应始终检查或过滤用户输入。你可以在第 20 章中了解更多相关信息以及其他安全问题。

## 更新记录

如你在第 12 章中所见，可以使用 SQL UPDATE 语句修改现有表行中的数据：

```sql
mysql> UPDATE fruit SET name = 'grapefruit', color = 'yellow' WHERE id = 2;
Query OK, 1 row affected (0.29 sec)
Rows matched: 1 Changed: 1 Warnings: 0
```

```sql
mysql> SELECT * from fruit;
```

| id | 名称 | 颜色 |
|----|------|-------|
| 1 | 香蕉 | 黄色 |
| 2 | 葡萄柚 | 黄色 |
| 3 | 李子 | 紫色 |

3 行记录，耗时 0.00 秒

与插入新记录类似，通过 PHP 脚本更新记录的情况也很简单：如果在 UPDATE 语句中传递的是字面量值，则使用 PDO::query()；如果传递的是变量值，则使用带占位符的 PDO::prepare()。例如，以下脚本更改了上一节中添加的“Derek Winter”记录的电子邮件地址字段：

```php
<?php
$dsn = "mysql:dbname=mydatabase";
$username = "root";
$password = "mypass";

try {
$conn = new PDO( $dsn, $username, $password );
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
} catch ( PDOException $e ) {
echo "Connection failed: " . $e->getMessage();
}

$id = 8;
$newEmailAddress = "derek.winter@example.com";

$sql = "UPDATE members SET emailAddress = :emailAddress WHERE id = :id";

try {
$st = $conn->prepare( $sql );
$st->bindValue( ":id", $id, PDO::PARAM_INT );
$st->bindValue( ":emailAddress", $newEmailAddress, PDO::PARAM_STR );
$st->execute();
} catch ( PDOException $e ) {
echo "Query failed: " . $e->getMessage();
}

?>
```

## 删除记录

通过 PHP 删除数据行的过程与更新类似。第 12 章向你展示了如何使用 SQL DELETE 关键字从表中删除行：

```sql
mysql> DELETE FROM fruit WHERE id = 2;
Query OK, 1 row affected (0.02 sec)
```

要使用 PHP 删除行，可以直接通过 PDO::query() 传递 DELETE 语句，或者使用带占位符的 PDO::prepare() 创建语句，并使用 PDOStatement::bindValue() 传递值（例如 WHERE 子句中的条件），再使用 PDOStatement::execute() 运行查询。

以下脚本从 members 表中删除 ID 为 8 的会员记录：

```php
<?php
$dsn = "mysql:dbname=mydatabase";
$username = "root";
$password = "mypass";

try {
  $conn = new PDO( $dsn, $username, $password );
  $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
} catch ( PDOException $e ) {
  echo "Connection failed: " . $e->getMessage();
}

$id = 8;

$sql = "DELETE FROM members WHERE id = :id";

try {
  $st = $conn->prepare( $sql );
  $st->bindValue( ":id", $id, PDO::PARAM_INT );
  $st->execute();
} catch ( PDOException $e ) {
  echo "Query failed: " . $e->getMessage();
}

?>
```

顺便说一句，你可以使用 PDOStatement::bindParam() 绑定变量本身，而不是使用 PDOStatement::bindValue() 将变量值绑定到占位符。如果在调用 bindParam() 后更改变量的值，占位符值会自动更新为新值（换句话说，变量是按引用绑定而非按值绑定）。如果在准备语句时不确定将传递什么值，这会很有用。有关 bindParam() 的更多信息，请参阅在线 PHP 手册：http://www.php.net/manual/en/pdostatement.bindparam.php。

## 构建会员注册应用程序

既然你知道如何通过 PHP 将记录插入 MySQL 表，就可以编写一个脚本，让新会员报名参加你的读书俱乐部。与其重新造轮子，不如基于你在第 13 章中创建的面向对象会员查看器应用程序进行扩展，扩展类以添加新功能，并创建一个脚本来注册新会员。

### 添加更多公共代码

首先，在 book_club 文件夹内的 common.inc.php 文件中添加一些额外的代码。在编辑器中打开此文件。

在此文件中，包含应用程序其余部分使用的其他公共文件是合理的。这样，脚本只需包含 common.inc.php，其他文件将自动包含。在 common.inc.php 文件的开头添加以下内容：

```php
require_once ("config.php");
require_once ("Member.class.php");
require_once ("LogEntry.class.php");
```

现在，在 displayPageHeader() 函数中的 CSS 声明里添加以下行：

```css
<style type="text/css">
th { text-align: left;
background-color: #bbb; }
th, td { padding: 0.4em; }
tr.alt td { background: #ddd; }
.error { background: #d33; color: white; padding: 0.2em; }
</style>
```

此行创建一个 CSS .error 类，用于突出显示注册表单中的任何问题。

最后，添加三个额外的实用函数，以帮助显示注册表单：

```php
function validateField( $fieldName, $missingFields ) {
if ( in_array( $fieldName, $missingFields ) ) {
echo ' class="error"';
}
}

function setChecked( DataObject $obj, $fieldName, $fieldValue ) {
if ( $obj->getValue( $fieldName ) == $fieldValue ) {
echo ' checked="checked"';
}
}

function setSelected( DataObject $obj, $fieldName, $fieldValue ) {
if ( $obj->getValue( $fieldName ) == $fieldValue ) {
echo ' selected="selected"';
}
}
```

