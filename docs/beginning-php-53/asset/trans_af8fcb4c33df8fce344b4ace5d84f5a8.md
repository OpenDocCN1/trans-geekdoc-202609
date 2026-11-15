

## 附录 B：配置 PHP

soap.wsdl_cache_ttl=86400

; 设置缓存大小限制。（要缓存的 WSDL 文件最大数量）
soap.wsdl_cache_limit = 5

[sysvshm]
; 共享内存段的默认大小
;sysvshm.init_mem = 10000

[ldap]
; 设置打开链接的最大数量，或 -1 表示无限。
ldap.max_links = -1

[mcrypt]
; 有关 mcrypt 设置的更多信息，请参阅 http://php.net/mcrypt-module-open

; 加载 mcrypt 算法的目录
; 默认：编译到 libmcrypt 中（通常为 /usr/local/lib/libmcrypt）
;mcrypt.algorithms_dir=

; 加载 mcrypt 模式的目录
; 默认：编译到 libmcrypt 中（通常为 /usr/local/lib/libmcrypt）
;mcrypt.modes_dir=

[dba]
;dba.default_handler=

; 本地变量：
; tab-width: 4
; 结束：

![](img/1ddec54918a4802eb9b4febec3d4e7f6_794_0.png)

## MySQL 的替代方案

在第 12 至 14 章中，你学习了如何在 PHP 应用程序内访问 MySQL 数据库。如果你正在编写 PHP 脚本，MySQL 通常是一个不错的选择，因为它可免费获得，跨平台，并且在大多数支持 PHP 的 Web 服务器上默认安装。

然而，MySQL 并非适合所有人，在某些场景下，使用替代数据库引擎更可取。本附录简要介绍了市场上一些更流行的替代方案。其中大多数可以与第 12 至 14 章中描述的 PDO 扩展一起使用，因此如果你想尝试不同的数据库引擎，那些章节中的大多数内容和示例仍然适用。

### SQLite

如果你询问普通开发者当今使用最广泛的 SQL 数据库引擎是什么，他们可能会想到 MySQL、Oracle 或 SQL Server。事实上，答案很可能是 SQLite（有关详细信息，请参阅 `http://www.sqlite.org/mostdeployed.html`）。造成这种情况的原因（除了它非常出色之外）是它是一个嵌入式数据库引擎。这意味着它被捆绑在每个使用它的应用程序的每个副本中，从 Firefox 到 Skype 以及包括 Symbian 和 iPhone 在内的各种移动平台。相比之下，MySQL 由一个独立的服务器应用程序组成，以及用于与服务器通信的客户端库。

关于 SQLite 的另一个好处是，其代码属于公有领域，这意味着任何人都可以按需使用和修改代码。

如今，SQLite 已随 PHP 引擎一起捆绑，这意味着你无需安装任何额外内容即可开始使用它。它非常快，支持几乎所有标准 SQL 命令，并且有一些相当特殊的绝招。它也相对简单（因为它没有客户端-服务器架构）且非常可靠。简而言之，它值得一试。

以下是 SQLite 的一些其他特点，使其脱颖而出：

- 它是动态类型的：同一个字段可以在不同记录之间存储不同的数据类型。这与 PHP 的弱类型很契合，并为你提供了很大的灵活性。（不过，这可能使维护数据库完整性变得更加困难，并且它与其他 SQL 数据库系统不兼容。）
- 数据库存储在单个跨平台数据库文件中：这使得备份 SQLite 数据库以及将其移植到不同操作系统变得容易。
- 它易于配置：无需安装、启动或配置单独的应用程序，并且在使用前无需创建用户或为数据库分配权限。
- 你可以在 SQL 查询中调用 PHP 函数：这是 SQLite 最令人印象深刻的功能之一，之所以可行，是因为 SQLite 引擎嵌入在 PHP 中。（参见本节稍后的示例。）

一般而言，如果你需要为 Web 应用程序选择一个快速、轻量级的数据库引擎，SQLite 值得一看。但是，如果你需要用于非常复杂的查询、非常大量的数据或高流量 Web 网站的“工业”级数据库，你可能需要寻找其他方案。

> 有关何时（以及何时不）使用 SQLite 的详细讨论，请参阅 http://www.sqlite.org/whentouse.html

撰写本文时，SQLite 的最新版本是 3 版。你的 PHP 脚本可以通过 SQLite3 扩展（请参阅 http://www.php.net/manual/en/book.sqlite3.php）或通过 PDO（请参阅 http://www.php.net/manual/en/ref.pdo-sqlite.php）与 SQLite 3 通信。

下面是一个简单的示例，演示如何使用 PDO 创建 SQLite 数据库和表，向表中插入一条记录，并检索该记录（同时从 SQL 内部调用 PHP str_word_count() 函数）：

```
<?php
$dsn = "sqlite:/home/matt/proverbs.sqlite3";
// Create a connection to the database
// (database file is automatically created)
try {
    $conn = new PDO( $dsn );
    $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
} catch ( PDOException $e ) {
    echo "Connection failed: " . $e->getMessage();
}
// Create a new SQLite function based on the PHP str_word_count() function
$conn->sqliteCreateFunction( "wordCount", "str_word_count", 1 );
```

```
// Create the proverbs table
// (columns of type INTEGER PRIMARY KEY serve as auto-increment columns)
$sql = "DROP TABLE IF EXISTS proverbs";
$conn->exec( $sql );
$sql = "CREATE TABLE proverbs ( id INTEGER PRIMARY KEY, proverbText )";
$conn->exec( $sql );

// Add a proverb
$sql = "INSERT INTO proverbs ( proverbText ) VALUES ( :proverbText )";
$st = $conn->prepare( $sql );
$st->bindValue( ":proverbText", "A bird in the hand is worth two in the bush" );
$st->execute();

// Retrieve the proverb and its word count, and display the results
$sql = "SELECT id, proverbText, wordCount( proverbText ) AS numWords FROM proverbs";
$st = $conn->query( $sql );
$proverb = $st->fetch();
echo "ID: " . $proverb["id"] . "<br />";
echo "Proverb: " . $proverb["proverbText"] . "<br />";
echo "Word count: " . $proverb["numWords"]. "<br />";

?>
```

此脚本显示以下内容：

```
ID: 1
Proverb: A bird in the hand is worth two in the bush
Word count: 11
```

### PostgreSQL

PostgreSQL（http://www.postgresql.org/）是一个免费、开源且符合标准的数据库引擎。PHP 允许你通过原生扩展（http://www.php.net/manual/en/book.pgsql.php）与 PostgreSQL 数据库通信，该扩展的工作方式与其 MySQL 对应物非常相似，或者通过 PDO（http://www.php.net/manual/en/ref.pdo-pgsql.php）

在 PHP 支持的所有数据库引擎中，PostgreSQL 可能是 MySQL 最接近的竞争对手。两者都是开源且免费的；两者提供大致相同的性能和可扩展性；两者在 Web 开发者中都拥有强大的追随者。

事实上，这种接近性经常导致“圣战”，双方系统的支持者会争论哪个更好。从历史上看，MySQL 被认为更易于使用且更快，而 PostgreSQL 则以功能更丰富、更强大、更可靠而闻名（如果你愿意，可以将其视为 Oracle 的开源替代品）。

## 附录 C：MySQL 的替代方案

然而，如今两个系统之间的差异已经很小了，因为 MySQL 变得更加功能丰富和稳定，而 PostgreSQL 变得更易于使用。撰写本文时，对 MySQL 的主要批评可能是它在防止数据丢失方面不够严格（例如，允许你插入无效的 `DATETIME` 值并悄悄将其转换为零），而 PostgreSQL 缺乏内置复制（尽管可以作为插件添加），并且安装在的 Web 托管账户不如 MySQL 多。但是，等你读到这篇文章时，两者之间的差距无疑会进一步缩小。

事实是，作为 Web 开发者，你最初选择哪个系统可能并不重要。如果你使用 PDO 连接数据库，并且没有使用任何一个引擎的一些更深奥的功能，你通常会发现将应用程序从 MySQL 移植到 PostgreSQL，或反之亦然，相当简单。

你可以在 http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL 上找到关于 MySQL 和 PostgreSQL 相对优缺点的详细讨论。

以下是第 12 章中 get_fruit.php 脚本的重写版本，用于使用 PostgreSQL 而非 MySQL。如你所见，所需的更改很小：

```
<!DOCTYPE html PUBLIC "--//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Fruit</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Fruit</h1>
<?php
$dsn = "pgsql:host=localhost;dbname=mydatabase";
$username = "postgres";
$password = "mypass";
try {
$conn = new PDO( $dsn, $username, $password );
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
} catch ( PDOException $e ) {
echo "Connection failed: " . $e->getMessage();
}

$sql = "SELECT * FROM fruit";
echo "<ul>";
try {
$rows = $conn->query( $sql );
foreach ( $rows as $row ) {
echo "<li>A " . $row["name"] . " is " . $row["color"] . "</li>";
}
}

