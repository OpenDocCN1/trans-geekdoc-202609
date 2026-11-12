

表中（如果表中只有两行，且你的搜索匹配其中一行，那将占 50%）。最后需要注意的一点是，FULLTEXT 搜索只匹配超过三个字母的搜索词；索引机制会忽略三个字符或更少的单词，以避免构建庞大的索引。这很像书籍的索引；你会非常惊讶地发现，在书籍的索引中，单词“the”出现在哪些页面！

## 以下是基本的 FULLTEXT 搜索：

```
SELECT * FROM articles
WHERE MATCH (title,body,author) AGAINST ( 'MySQL' );
```

此搜索将返回标题、正文或作者中包含单词“MySQL”的所有行。

FULLTEXT 索引的另一个用途是在搜索中为每个结果返回相关性。例如：

```
// Select all rows but display relevance
$sql = "SELECT
  *, MATCH (title, body, author)
  AGAINST
  ('The PHP Anthology Released Long Word Matching')
  AS
  score
  FROM
  articles
  ORDER BY score DESC";
// Run the query, identifying the connection
$queryResource = mysql_query($sql, $dbConn);
// Fetch rows from MySQL one at a time
while ($row = mysql_fetch_array($queryResource, MYSQL_ASSOC)) {
  echo 'Title: ' . $row['title'] . '<br />';
  echo 'Author: ' . $row['author'] . '<br />';
  echo 'Body: ' . $row['body'] . '<br />';
  echo 'Score: ' . $row['score'] . '<br />';
}
```

别名 score 现在包含一个值，用于标识该行与搜索的相关程度。该值不是百分比，而仅是一种度量；0 表示完全没有匹配。匹配一个单词将产生大约 1 的值。匹配的单词越多，数值就越大，因此五个单词匹配的排名将产生大约 13 的相关性评分。MySQL 的相关性算法专为大型表设计，因此你拥有的数据越多，相关性值就越有用。

总的来说，MySQL 的 FULLTEXT 搜索功能提供了一种易于实现且能够提供有用结果的机制。

## 如何备份我的数据库？

数据库越大，如果没有包含其中数据的备份，就越令人不安。如果服务器崩溃，一切都丢失了怎么办？幸运的是，MySQL 提供了两种替代方案：一个名为 mysqldump 的命令行实用程序，以及用于备份表的查询语法。

以下是如何使用 mysqldump 从命令行导出数据库内容：

```
mysqldump -uharryf -psecret sitepoint > sitepoint.sql
```

该命令将以用户“harry”（-uharryf）和密码“secret”（-psecret）登录到 MySQL，并将 sitepoint 数据库的内容输出到名为 sitepoint.sql 的文件。sitepoint.sql 的内容将是一系列可以针对 MySQL 运行的查询，也许可以使用 mysql 实用程序从命令行执行反向操作：

```
mysql -uharryf -psecret sitepoint < sitepoint.sql
```

使用 PHP 的 system 函数，你可以在 PHP 脚本中执行上述命令（这要求你已登录并能够从命令行执行 PHP 脚本）。以下类将所有这些整合成一个方便的 PHP 形式，你可以使用它来定期备份你的网站。

```
File: Database/MySQLDump.php (in SPLIB)

/**
 * MySQLDump Class<br />
 * Backs up a database, creating a file for each day of the week,
 * using the mysqldump utility.<br />
 * Can compress backup file with gzip or bzip2<br />
 * Intended for command line execution in conjunction with
 * cron<br />
 * Requires the user executing the script has permission to execute
 * mysqldump.
 * <code>
* $mysqliDump = new MySQLDump('harryf', 'secret', 'sitepoint',
    '/backups');
*
* $mysqliDump->backup();
* </code>
* @access public
* @package SPLIB
*/
class MySQLDump {
/**
* The backup command to execute
* @private
* @var string
*/
var $cmd;

/**
* MySQLDump constructor
* @param string dbUser (MySQL User Name)
* @param string dbPass (MySQL User Password)
* @param string dbName (Database to select)
* @param string dest (Full dest. directory for backup file)
* @param string zip (Zip type; gz - gzip [default], bz2 - bzip)
* @access public
*/
function MySQLDump($dbUser, $dbPass, $dbName, $dest,
    $zip = 'gz')
{
    $zip_util = array('gz'=>'>gzip', 'bz2'=>'>bzip2');
    if (array_key_exists($zip, $zip_util)) {
        $fname = $dbName . '.' . date("w") . '.sql.' . $zip;
        $this->cmd = 'mysqldump -u ' . $dbUser . ' -p' . $dbPass .
            ' ' . $dbName . '|' . $zip_util[$zip] . '> ' .
            $dest . '/' . $fname;
    } else {
        $fname = $dbName . '.' . date("w") . '.sql';
        $this->cmd = 'mysqldump -u ' . $dbUser . ' -p' . $dbPass .
            ' ' . $dbName . '> ' . $dest . '/' . $fname;
    }
}

/**
* Runs the constructed command
* @access public
* @return void
*/
function backup()
{
	system($this->cmd, $error);
	if ($error) {
		trigger_error('Backup failed: ' . $error);
	}
}
```

MySQLDump 类对操作系统配置做了一些假设。它假设 mysqldump 实用程序可在执行此脚本的用户的路径中使用。如果使用 gzip 或 bzip2 实用程序，它们也需要存在于执行此脚本的用户的路径中。
bzip2 提供比 gzip 更好的压缩，有助于节省磁盘空间。

以下代码演示了如何使用此类：

```
<?php
// Include the MySQLDump class
require_once 'Database/MySQLDump.php';

$dbUser = 'harryf';        // db User
$dbPass = 'secret';        // db User Password
$dbName = 'sitepoint';     // db name
$dest   = '/home/harryf/backups'; // Path to directory
$zip    = 'bz2';           // ZIP utility to compress with

// Instantiate MySQLDump
$mysqlDump = new MySQLDump($dbUser, $dbPass, $dbName, $dest,
		$zip);

// Perform the backup
$mysqlDump->backup();
?>
```

$dest 变量指定应放置备份文件的目录路径。创建的文件名将采用以下格式：

databaseName.dayOfWeek.sql.zipExtension

例如：

sitepoint.1.sql.bz2

dayOfWeek 元素可以是 0 到 6 之间的任何数字（0 代表星期日，6 代表星期六）。这提供了每周“滚动”备份，下周的文件将覆盖上周的文件。这应该提供足够的备份，给你一周的时间来发现任何严重问题，而无需过多磁盘空间来存储文件。

使用 ZIP 实用程序是可选的。如果 `$zip` 变量的值不是 `gz` 或 `bz2` 之一，则不会进行压缩，尽管对于大型数据库，显然使用压缩工具来最大限度地减少所需磁盘空间是个好主意。

此类旨在与 `crontab` 实用程序一起使用，这是一个 Unix 功能，允许你定期（例如每天）执行脚本。

MySQL 还提供 SQL 语句 `BACKUP TABLE` 和 `RESTORE TABLE`，允许你将表的内容复制到文件系统上的另一个位置。与 `mysqldump` 实用程序不同，以这种方式备份的表保留其原始格式（不可读），但此机制不需要访问命令行实用程序，因此可以通过网页执行。

这些语句的一般语法如下：

```
BACKUP TABLE tbl_name[, tbl_name ...]
TO '/path/to/backup/directory'
```

```
RESTORE TABLE tbl_name[, tbl_name ...]
FROM '/path/to/backup/directory'
```

请注意，在 Windows 系统上，最好使用正斜杠指定路径（例如 `C:/backups`）。

通过将这些与 MySQL 提供的某些“内省”语句相结合，我们可以使用本章构建的 MySQL 类来备份数据库。首先，我们需要获取数据库中的表列表，可以使用 `SHOW TABLES` 查询语法快速实现：

```
<?php
// Include the MySQL class
require_once 'Database/MySQL.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name
```

