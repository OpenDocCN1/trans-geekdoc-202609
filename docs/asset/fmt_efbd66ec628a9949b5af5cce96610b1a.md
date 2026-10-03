
这种陈述通常关注代码层面的问题，而忽略了宏观问题。首先，使用 PEAR DB 会带来非常大的性能影响——许多人都有感，因为问题将是“抽象退化性能？”，而不是“抽象退化性能如何？”。PEAR DB 的设计——用 PHP 本身的 C 中编写、完全面向对象、将集合复制到多维数组中，而许多数据库在功能上有显著差异——表明 PEAR 并不是该行业的首要考虑因素。一个比较原生 MySQL 数据库访问 MySQL 的信息性基准测试可以在 `https://freshmeat.net/scott/scott3013/` 找到。此外，PEAR DB 的设计总是落后数据库和 PHP 的开发，并且并不总是包含每一个高级功能——因此你可能一段时间内或永远无法通过 PEAR DB 使用 DBMS 的新功能。此外，如果你在理论上具有支持一组数据库的能力，你就承担了这样做的实际责任。有时，说一句“我们只能支持 MySQL 和 PostgreSQL”并就此为止，可以为你省去很多烦恼。

此外，PEAR DB 能够赋予你连接到多个数据库的能力，并不意味着相同的代码可以在所有数据库上运行。在理论上的最佳情况下——例如，仅使用 MySQL 和 PostgreSQL 之间共享的最常用功能——你只需要在数据库直接相关的代码（如打开查询等）中进行调整，这就是唯一的调整。你必须指定新数据库是 Oracle 类型的，并提供有关其主机名和其他实现方面的细节。在现实中，为了支持众多数据库，你可能需要对 SQL 语句进行一些调整，因为所有数据库服务器在实现 SQL 的方式上都不同。除了基于标准之外，数据库服务器在使用的语法上可能有很大差异，这是可以接受的。新的数据库服务器将配置有迁移应用程序所需的表、列名和行。

使用数据库抽象层的决定应该根据项目逐一做出。请放心地地驳斥那些告诉你数据库抽象总是好或总是坏的编码员的意见，即他们认为数据库抽象的好处是你将能够轻松地在数据库之间切换。这种情况极少发生（而且通常伴随着使用上的更大错误），并且永远不应该作为一个主要的考虑因素。支持多个数据库的实际益处在于，如果你的用户需要多个数据库。经验法是，你的应用程序的用户（在独立实例）越多，对各种数据库的需求就越大——因此从 PEAR DB 或其竞争对手中获益的也就越多。

独立网站从 PEAR DB 中获益非常少，因为抽象层的额外重量比未来更改数据库的小可能性要大得多。构造者需要权衡易用性的潜在收益与对性能的潜在损失。在可能可能需要集成众多 PHP 软件包的情况下，PEAR DB 可能会帮助或损害你。PEAR DB 具有明显优势的情况是对于具有多个安装版本的、需要在尽可能多的 DBMS 上运行的独立程序，作为一个开发者社区且不需要是性能的。许多开源 PHP 软件包——例如维基、博客、工单系统、公告板等——都符合这些标准，因此从数据库抽象层中获益。移植性对于这类项目来说几乎是一个比对于单站 Web 开发者更重要的问题。

![](img/70f9bfaf3d714f908e4cb0592b8eb9a6_711_0.png)

使用 PEAR DB 的一个原因是个人开发者想要遵循完美的面向对象的数据库范式。这很好，但技术主管和架构师应该意识到，存在免费的特定数据库类，在性能上可能优于 PEAR DB。

然而，主点仍然是：如果你设计的应用程序是使用 PEAR DB 类，那么在将应用程序从一个数据库管理服务器移动到另一个时，你的 PHP 代码将极少需要修改。如果你预计会有许多用户可能希望使用各种数据库来运行你的应用程序，那么这是一个真正的优势。

# PEAR DB 与 PHP5

在编写本文时，针对 PHP5 的更改大多尚未被纳入 PEAR DB：PHP5 中的所有重大更改，外：新的对象模型、异常处理、SQLite 以及新的 `mysqli` 扩展尚未包含。在这些功能中，目前只有 SQLite 正在被正确处理。当这些新功能引入时，预计 PEAR DB 将发生变化。

# 原生数据库连接

原生数据库函数由于是用 C 语言编写而非 PHP，将是 PHP 脚本连接数据库最快的方法。然而，对于每个支持的数据库都有系列函数。简而言之，该过程涉及一系列步骤，每一步都针对所使用的数据库进行了定制。

连接到 MySQL 数据库，程序使用如下命令：

```php
mysql_connect('localhost', 'root', 'sesame');
mysql_select_db('phpbook');
```

然后程序定义并执行一个查询：

```php
$query = "SELECT Surname FROM personal_info WHERE ID<10";
$result = mysql_query($query);
```

之后，只需遍历结果集查看从数据库返回了什么：

```php
while($name_row = mysql_fetch_row($result)) {
print("$name_row[0] $name_row[1] $name_row[2]<BR>\n");
}
```

要在另一个数据库管理服务器上执行相同的工作，必须修改六行中的四行。以下是 PostgreSQL 的代码（假设主机名和其他细节相同）：

```php
pg_connect('localhost', 'root', 'sesame');
pg_select_db('phpbook');

$query = "SELECT Surname From personal_info WHERE ID<10";
$result = pg_query($query);

while($name_row = pg_fetch_row($result)) {
print("$name_row[0] $name_row[1] $name_row[2]<BR>\n");
}
```

这可能会非常麻烦，而且该过程引入了各种错误机会。

PEAR DB 解决了这个问题。

# 数据库抽象

通过应用面向对象的方法和一些通用标准，PEAR DB 已经进化到从 MySQL 切换到 PostgreSQL（或任何其他几个数据库）只需更改一行代码（假设 SQL 查询保持不变）。以下是在 PEAR DB 下解决相同问题的方法：

```php
$dsn = "mysql://root:sesame@localhost/phpbook";
$db = DB::connect($dsn);

if ($db->isError($db)) {
    $db->getMessage();
}

$sql = "SELECT cityName FROM cities ORDER BY cityName";
$result = $db->query($sql);

if ($db->isError($result)) {
    $errorMessage = $result->getMessage();
}

$i=0;
while ($row = $result->fetchRow()) {
    $returnArray[$i]=$row[0];
    $i++;
}
$db->disconnect();
```

这里的点是，在 PostgreSQL 下实现相同目的的代码完全相同，除了第一行：

```php
$dsn = "postgresql://root:sesame@localhost/phpbook";
```

更改 Microsoft SQL Server 代码仅涉及一处修改，如下：

```php
$dsn = "mysql://root:sesame@localhost/phpbook";
```

以此此类推。下一节将详细解释数据源名称 (DSNs) 和其他重要的 PEAR 概念。

# PEAR DB 概念

在 PEAR DB 中，你需要理解许多概念才能有效地使用该类。这些包括：

- 数据源名称
- 连接
- 查询
- 行检索
- 断开连接

下面的小节将依次解释每一个。

## 数据源名称 (DSNs)

数据源名称 (DSN) 是一个描述数据库位置以及如何访问它的简单字符串。DSN 就像数据库的 URL。因为数据库几乎总是有用户级访问控制，DSN 指定了用户名和密码。注意，DSN 指定的是你连接的字面量，而不是数据库中的表。

为了形成 DSN，你需要确定几个值：

- 你连接的数据库类型
- 运行数据库服务器的主机名或 IP 地址
- 数据库名称
- 你想使用的用户名
- 相应的密码

通常情况下，你需要这些值在几个不同的相关程序中创建 DSN。因此，在一个特殊程序并将这些字面值分配给变量是有意义的。这样的程序可能如下（称之为 `dbSpecs.php`）：

```php
$type = 'mysql';
$host = 'localhost';
$database = 'inventory';
$username = 'user';
$password = 'sesame';
```

剩下的唯一部分是 `$type` 的值，它是一个于特定数据库（例如 MySQL）的标准字符串。将你的变量放在一个简单的库中，当你想要创建 DSN 时，可以导入 `dbSpecs.php` 并访问它的值。其优势是，如果 `dbSpecs.php` 中的值发生变化，你只需要在一个地方修改它们即可。导入语句是：

```php
require_once('dbSpecs.php');
```

之后，你就可以使用 `dbSpecs.php` 中定义的值在函数内部创建 DSN（这是变量作用域的特性）：

```php
global $type;
global $host;
global $database;
global $username;
global $password;
```

### DSN 的有效标识符

这里是 PEAR DB 支持的所有数据库管理服务器列表，并包含了你在 DSN 中标识它们时应使用的字符串：

- FrontBase (`fbs`)
- InterBase (`ibase`)
- Informix (`ifx`)
- Microsoft SQL (`mssql`)
- MySQL (`mysql`)
- Oracle (`oci8`)
- ODBC (`odbc`)
- PostgreSQL (`pgsql`)
- SyBase

一旦你有了这些值，将它们组合成一个格式正确的 DSN 就非常简单了。标准格式如下：

```php
$dsn = "$type://$username:$password@$host/$database";
```

有更多选项可定义 DSN。详细信息请见 `http://pear.php.net/manual/en/package/database.intro-dsn.php`。一如既往，我们建议将数据库连接变量存储在 Web 之外以获得更高的安全性。

## 连接

当你有一个 DSN 时，告诉 PEAR DB 建立连接是一件简单的事。代码如下：

```php
$db = DB::connect($dsn);
```

如果连接尝试成功，一切都好——`$db` 包含一个连接的对象（在其他活动中）。

```php
if ($db->isError()) {
    die($db->getMessage());
}
```

`isError()` 方法在数据库对象出现错误时返回 `true`，否则返回 `false`。

## 查询

在成功建立连接的基础上，你通常想对数据库运行查询。这通过结构化查询语言 (SQL) 实现，该语言在第 13 节详细介绍。

惯常做法是将你的 SQL 查询写入字符串并将该字符串放入变量 `$sql` 或 `$query` 中：

```php
$sql = 'SELECT cityName FROM cities ORDER BY cityName';
```

然后将其作为数据库对象（换句话说，代表连接的变量）的 `query()` 方法的参数，并将结果赋值另一个变量：

```php
$result = $db->query($sql);
```

再次考虑到错误的可能性：

```php
if ($db->isError($result)) {
  $errorMessage = $result->getMessage();
  die($errorMessage);
}
```

## 行检索

作为 `query()` 操作的结果，`$result` 包含一个结果集。结果集是某些行（可能为零）。

为了从结果中提取值，使用如下 `while` 循环：

```php
$i=0;
while ($row = $result->fetchRow()) {
    $returnArray[$i]=$row[0];
    $i++;
}
```

这个循环针对结果对象中的每一行运行 `fetchRow()` 函数并提取。因为我们知道结果集只有一个列（SQL 语句仅请求了 `cityName`），所以我们可以提取每一行的第一个元素 `$row[0]`（唯一的元素）并将其放入另一个数组 `$returnArray` 中。

## 断开连接

当数据库连接完成目的后，使用数据库对象的 `disconnect()` 方法来释放与连接相关的资源：

```php
$db->disconnect();
```

记住这一点很重要；否则连接将保持活动状态直到超时（这是一个很长的时间）。

# 完整示例

查看一个通过 PEAR DB 类执行数据库操作的完整函数可能会有所帮助。

该函数将调用 `getItems.php`，其作用是从名为 `INVENTORY_item` 的 Microsoft Server 数据库中提取所有项目。为了返回所有项目，我们需要一个 `SELECT` 语句从 `INVENTORY_item` 表中提取列。由于 `INVENTORY` 没有外键（这是为了本说明而做的假设），提取细节涉及通过 PEAR DB 连接遵循简单的 `SELECT` 语句到达数据库服务器。

让我们逐行检查 `getItems.php` 来这是如何实现的。

```php
<?php
require_once('dbSpecs.php');
require_once('dbSpecs.php');
```

首先，我们必须导入 PEAR DB 类和 `dbSpecs.php`，后者包含了数据库服务器的信息和安全凭据（在本章的前面已列出）。

```php
function getItems() {
    global $phptype;
    global $hostspec;
    global $database;
    global $username;
    global $password;
```

在函数中，必须声明全局变量（来自 `dbSpecs.php` 的 `$password`）才能访问它们。

```php
$dsn = "$phptype://$username:$password@$hostspec/$database";
$db = DB::connect($dsn);
if (DB::isError($db)) {
    die($db->getMessage());
}
```

使用本章之前过的 PEAR DB 程序，程序连接到数据库服务器。程序检查错误条件，如果在连接后发现错误，则终止。

程序定义了要在已建立的数据库上运行的 SQL 语句：

```php
$sql = "select id, desc, weight, packageQty, unit, supplierID, cost from INVENTORY_item";
```

这就是将发送到数据库服务器的 SQL 查询。注意，尽管包含了所有列，我们仍然指定了列。我们知道列在结果中的顺序如下：

```php
$result = $db->query($sql);
if (DB::isError($result)) {
    $errorMessage = $result->getMessage();
    die($errorMessage);
}
```

程序将查询发送到数据库并检查是否返回了错误消息。

```php
$returnArray = array();
while ($row = $result->fetchRow()) {
    $id = $row[0];
    $desc = $row[1];
    $weight = $row[2];
    $packageQty = $row[3];
    $unit = $row[4];
    $supplierID = $row[5];
    $cost = $row[6];
    $returnArray[] = array(
      'id' => $id, 'desc' => $desc, 'weight' => $weight,
      'packageQty' => $packageQty, 'unit' => $unit,
      'supplierID' => $supplierID, 'cost' => $cost
    );
}
$db->disconnect();
return $returnArray;
```

程序的其余部分设置了一个名为 `returnArray` 的数组。它被一系列子数组填充，使其成为一个二维数组。子数组是关联数组；它们的键与数据库中的列名对应，其值来自 `$result` 的每一行。

# PEAR DB 函数

PEAR DB 类非常广泛，其成员数量远于本章示例中已涵盖的广泛使用的成员。大多数其他成员都是专门的，因此只在特定情况下才有用。

本节总结了 PEAR DB 类一些最实用的成员，但并非详尽。请务必参考 `http://pear.php.net/manual/en/package/database.php` 获取官方列表和文档。

## DB 类成员

`DB` 类是主要的 PEAR DB 类，用于表示与数据库的连接（或尝试创建连接）。方法包括：

- `DB::connect()`: 使用 DSN 连接到数据库。
- `DB::isWarning()`: 如果连接尝试产生警告，则返回 `true`。
- `DB::isError()`: 如果连接尝试产生错误，则返回 `true`。

## DB_Common 类成员
