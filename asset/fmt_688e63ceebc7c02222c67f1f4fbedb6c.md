
- 123: 声明 `numrowsDB()` 函数。该函数需要数据库类型 (`$db`) 和上一个查询的结果集 (`$result`) 作为参数。
- 124: 开始一个 `switch` 语句，根据 `$db` 的值检查应该运行哪一个分支。
- 125: 如果 `$db = "psql"`，则用户想要使用 PostgreSQL 数据库。
- 126: 调用 `pg_numrows()` 并检查是否存在错误。
- 127: 如果有错误，返回 `0` 通知调用函数关闭失败。
- 128–129: 如果没有错误，通知调用函数关闭成功。
- 130: 结束 `if` 语句。
- 131: 跳出 `switch` 语句，因为分支已经满足。
- 132: 如果 `$db = "mysql"`，则用户想要使用 MySQL 数据库。
- 133: 调用 `mysql_num_rows()` 并检查是否存在错误。
- 134: 如果有错误，返回 `0` 通知调用函数关闭失败。
- 135–136: 如果没有错误，通知调用函数关闭成功。
- 137: 结束 `if` 语句。
- 138: 跳出 `switch` 语句，因为分支已经满足。
- 139: 如果 `$db = "mssql"`，则用户想要使用 MS SQL 数据库。
- 140: 调用 `mssql_num_rows()` 并检查是否存在错误。
- 141: 如果有错误，返回 `0` 通知调用函数关闭失败。
- 142–143: 如果没有错误，通知调用函数关闭成功。
- 144: 结束 `if` 语句。
- 145: 跳出 `switch` 语句，因为分支已经满足。
- 146–147: 如果没有一个分支被满足，则显示消息，说明发送给函数的 `$db` 值无效。
- 148: 返回 `0` 通知调用函数函数失败。
- 149: 结束 `switch` 语句。
- 150: 结束函数声明。

示例的下一个部分是为示例应用程序创建表所需的 SQL：

### 脚本 3–3 addressbook.sql

```sql
1.  CREATE TABLE addressbook (
2.  first VARCHAR(32),
3.  last VARCHAR(32),
4.  home VARCHAR(16),
5.  cell VARCHAR(16),
6.  work VARCHAR(16));
```

最后一部分是示例应用程序，它使用 `DBlib.php` 文件作为其数据库封装，允许应用程序在无需更改任何代码的情况下与三种不同的数据库后端配合。关于该脚本产生的输出，请参阅图 3-2。

### 脚本 3–4 customDB.php

```php
1.  <?
 2.  $page = "customDB.php";
 3.
4.  require_once("DBlib.php");
 5.  /* DBlib.php 必要条件 */
 6.//$db = "psql"; //PostgreSQL 数据库
 7.//$db = "mysql"; //MySQL 数据库
 8.  $db = "mssql"; // MS SQL 数据库
 9.  $host = "192.168.0.1";
10.  $database = "php";
11.  $username = "mssqluser";
12.  $password = "password";
13.  /**************************/
 14.
15.  function display_addresses ($db) {
16.    global $dbconn;
17.    selectDB($db, $dbconn);
18.    $sql = "select * from addressbook";
19.    if(!$result = queryDB($db, $sql)) {
20.      echo "<P>Error with query!";
21.    }
22.    $rows = numrowsDB($db, $result);
23.    if($rows == 0) {
24.      echo "您的通讯录中没有条目.";
25.    } else {
26.    ?><table border=1><?
 27.      while($row = returnDBarray($db, $result)) {
 28.        ?>
 29.        <tr><td colspan=2><b><?=$row['first'];?> <?=$row['last'];?></b></td></tr>
 30.        <tr><td>家庭: </td><td><?=$row['home'];?></td></tr>
 31.        <tr><td>手机: </td><td><?=$row['cell'];?></td></tr>
 32.        <tr><td>工作: </td><td><?=$row['work'];?></td></tr>
 33.        ?>
 34.      }
 35.    ?></table><?
 36.    }
 37.  }
 38.
39.  function add_address($db, $HTTP_POST_VARS) {
40.    global $dbconn;
41.    selectDB($db, $dbconn);
42.    $query = "insert into addressbook values ('" .
 43.      $HTTP_POST_VARS['first'] . "','" .
 44.      $HTTP_POST_VARS['last'] . "','" .
 45.      $HTTP_POST_VARS['home'] . "','" .
 46.      $HTTP_POST_VARS['cell'] . "','" .
 47.      $HTTP_POST_VARS['work'] . "')";
48.    if(!queryDB($db, $query)) {
49.      echo $query;
50.      return 0;
51.    } else {
52.      return 1;
53.    }
54.  }
 55.
56.  function add_address_form(){
57.    global $page;
 58.    ?>
 59.    <h3>添加地址：h3>
60.    <form action=<?=$page?> method=post>
61.    <p>名: <input type="text" name="first">
62.    <br>姓: <input type="text" name="last">
63.    <br>家庭: <input type="text" name="home">
64.    <br>手机: <input type="text" name="cell">
65.    <br>工作: <input type="text" name="work">
66.    <p><input type="submit" name="add_address" value="添加条目!">
67.    </form>
 68.    ?>
69.  }
70.  /***** 主程序 *****/
71.  ?>
72.  <h3>通讯录</h3>
73.  <p><a href=<?=$page?>?action=add>添加条目</a>
74.  <p>
 75.  <?
76.  $dbconn = connectDB($db);
 77.  if(isset($add_address)) {
78.    if(!add_address($db, $HTTP_POST_VARS)) {
79.      echo "<h3>添加条目出错!</h3>";
80.    } else {
81.      echo "<h3>条目已添加!</h3>";
82.    }
83.  }
```

PEAR 是一个“用于可复用 PHP 组件的框架和发行系统”。PEAR 提供了类似于 PERL CPAN 模块集的“模块”。可以将这些模块想象成预构建组件的库，通过它们你可以让你的 PHP 编码变得更容易。PEAR 目前处于测试阶段并正在火热开发中，但它已经包含了许多你可以在自己的项目中使用的有用模块。PEAR 提供了开源模块、这些模块的发行和维护，并为这些模块制定了编码标准。

> [1] 取自 PEAR 网站：[pear.php.net](http://pear.php.net)。

PEAR 随 PHP 一起发行。如果你最近安装了 PHP，可能会注意到 `pear` 目录及其包含的许多文件。由于 PEAR 仍处于测试阶段，它尚未被广泛宣传，但它已经开始受到 PHP 开发者的关注，特别是那些一直使用诸如 PHPLIB 和 ADOdb 等第三方库的开发者。虽然已经有很多良好的第三方库可用，但在编码指南、发行和维护方面还没有统一的标准。PEAR 看起来是解决这个问题的方案。

开始变得非常流行的模块之一是 PEAR DB，它是“访问 SQL 数据库的统一 API”。PEAR DB 的功能大大超过了 DBX 库，并且几乎是纯面向对象的。PEAR DB 支持 PHP 核心支持的数据库的子集，并正在扩展以支持更多数据库。PEAR DB 是编写与数据库无关的 PHP 应用程序的工具。

### 下载 PEAR

你可以从 PEAR 网站 [pear.php.net](http://pear.php.net) 下载 PEAR 的最新版本。在网站右上角的“搜索”框中输入“DB”。

点击出现的第一个搜索结果“DB”，然后从发布列表中下载最新的稳定版本。

### 从并发版本系统 (CVS) 下载 PEAR

尽管 PEAR 包含在所有最新版本的 PHP 中，并且你可以从 PEAR 网站下载较晚的稳定版本，但包含最新功能的、最先进且最强大的 PEAR 版本可能仍然停留在 CVS 仓库中。请注意，你不应该在生产网站上使用 CVS 版本！如果你有权访问 CVS ([www.cvshome.org](http://www.cvshome.org))，那么你应该利用这一机会，从 PHP CVS 仓库下载最新的 PEAR 源码。你可以在 [`cvs.php.net/`](http://cvs.php.net/) 找到 PHP CVS 仓库的所有详细信息。

下载最新的 PEAR 源码：

1. 切换到你想要放置源码的位置（或一个方便拷贝文件的地方）。
2. 执行命令：

   ```bash
   cvs -d :pserver:cvsread@cvs .php.net:/repository login
   ```

   系统会提示输入密码。输入 "phpfi"。

3. 执行命令：

   ```bash
   cvs -d :pserver:cvsread@cvs .php.net:/repository export -D "last week" php4/pear
   ```

   PEAR DB 文档的主要贡献者之一 Thomas V. V. Cox 建议使用 "last week" 标记。有时候最新版本会有小 bug，但大多数时候没有。

### 安装 PEAR

将 PEAR 文件夹复制到你的 Web 目录。完成后，你需要在你的脚本中包含 `pear.php` 文件。

```php
require_once('pear.php');
$dsn = "mysql://user:password@host/database";
$dbconn = DB::connect($dsn);

if (DB::isError($dbconn)) {
    die($dbconn->getMessage());
}
```

### 回归基础

现在你已经建立好了连接，并有了在连接失败时捕获错误的方法，接下来你需要学会的是向数据库发送查询。这是通过 `query()` 方法实现的。

```php
$result = $dbconn->query(QUERY);
```

`query()` 接受一个参数 `QUERY`，它是一个 SQL 语句。你将查询结果赋值给一个变量（例如 `$result`），这是一个结果对象。

一旦你获得了一个有效的结果对象，就可以使用“fetch”方法之一来从结果中获取数据，然后将其格式化并显示给用户，或者对其进行一些其他处理。你可以使用两种 fetch 方法：`fetchRow()` 和 `fetchInto()`。

```php
$row = $result->fetchRow();
```

以及

```php
$result->fetchInto($row);
```

这两种方法产生的结果完全相同：一个名为 `$row` 的变量，其中包含了结果中的当前行数据。

* `DB_FETCHMODE_ASSOC` — 数据被格式化为关联数组。
* `DB_FETCHMODE_OBJECT` — 数据被格式化为对象，其中列名为属性。

例如，假设你有一个名为“crew”的表格（表 3-2），其中包含以下信息：

### 表 3-2. 示例数据

| ID | NAME | ORIGIN |
| --- | --- | --- |
| 0 | Spike | MA |
| 1 | Jett | AZ |
| 2 | Faye | FL |
| 3 | Ed | NM |
| 4 | Ein | CO |

你查询数据库并获得结果：

```php
$sql = "select name, origin from crew"; 
$result = $dbconn->query($slq);
```

这三种格式将是：

```php
// 使用默认的 DB_FETCHMODE_ORDERED 格式 
$row = $result->fetchRow();
$name = $row[0]; // $name = "Spike";
$origin = $row[1]; //$origin = "MA";

// 使用关联数组作为格式
$row = $result->fetchRow(DB_FETCHMODE_ASSOC);
$name = $row['name']; // $name = "Spike";
$origin = $row['origin']; //origin = "MA";

// 使用对象作为格式
$result->fetchInto($row, DB_FETCHMODE_OBJECT);
$name = $row->name; // $name = "Spike";
$origin = $row->origin; //origin = "MA";
```

这些格式提供了极大的灵活性。另外注意，不同的 fetch 方法会产生相同的预期结果。

由于在脚本中为每个 fetch 方法都手动输入 `DB_FETCHMODE_ASSOC` 或 `DB_FETCHMODE_OBJECT` 作为参数可能会非常麻烦（如果你选择使用这些格式），PEAR DB 提供了一个名为 `setFetchMode()` 的巧妙方法。

```php
$dbconn->setFetchMode(MODE); 
```

`setFetchMode()` 是连接对象的一个方法，用于设置所有 fetch 函数的默认抓取模式。参数 `MODE` 可以是之前指定的三个抓取模式中的任何一个。注意，如果你还没有将抓取模式设置为其他值之一，那么将抓取模式设置为 `DB_FETCHMODE_ORDERED` 是没有意义的，因为已经是默认值。一旦你使用此方法，你调用的所有 fetch 方法都会使用 `setFetchMode()` 指定的模式，除非你在 fetch 方法本身中指定了不同的抓取模式。

你还应该使用检查连接错误的相同方法来检查结果是否存在错误。如果 `query()` 产生错误，它将返回一个错误对象：

```php
$result = $dbconn->query($sql); 
if (DB::isError($result)) { die ($result->getMessage());}
```

在你完成结果集后，应该使用 `free()` 方法释放结果对象。这将“释放”与结果集相关的内存并减少对 Web 服务器的负载：

```php
$result->free(); 
```

最后，当你完成脚本后，应该关闭与服务器的连接。这是通过连接对象的 `disconnect()` 方法实现的：

```php
$dbconn->disconnect(); 
```

你现在拥有了创建简单脚本的构建模块。接下来的脚本将说明不同的 fetch 方法和错误处理。

### 脚本 3–5 peardb1.php
