

## II.4.13. 从数据库转储下载数据

与 MP3 文件一样，如果 `echo $file['content']` 语句之后有任何到浏览器窗口的输出（包括 `?>` 标签之后的空格或换行符），图像文件将会损坏。

为了从数据库转储中执行多个 SQL 查询，会读取 `catalog.sql` 文件的内容，并使用正则表达式 `#;[\s]*\r\n#` 将其拆分为独立的查询（列表 II.4.39）。在执行得良好的 MySQL 数据库转储中，每个查询都以分号结束。

+ 列表 II.4.39. 从数据库转储下载数据

```php
<?php
// 连接到数据库
include "config.php";
// 包含 SQL 指令的文件
$filename = "catalog.sql";
// 打开指令文件
// 并将其读取缓冲区
$fp = fopen($filename, "r");
$contents = fread($fp, filesize($filename));
fclose($fp);
// 在分号边界处
// 拆分文件内容
$quer = preg_split("#;\\s]*\r\n#is", $contents);
// 执行 SQL 查询
foreach($quer as $query) {
    if(!$mysql_query($query)) exit(mysql_error());
}
?>
```

## 第 II.5 章：Session 和 Cookie

![](img/a893312ec68b8170fe567f785e95c06e_242_0.png)

### II.5.1. 在线用户

HTTP 不允许用户建立会；因此，它不允许你追踪特定访问访问 Web 资源的时间间隔。唯一可以追踪的是客户端访问服务器资源的时间。之后，访问者可以花费几个小时阅读加载的页面——Web 服务器无法判断访问者何时停止使用加载资源。因此，如果访问者上次加载页面后已过去 20 分钟，则认为访问者离开了特定的 Web 资源。

为了记录访问访问资源页的时间，需要在 MySQL 数据库中创建一个会话表，用于存储用户名以及他们最后访问资源页的时间（列表 II.5.1）。

列表 II.5.1. 会话表

```sql
CREATE TABLE session (
  id_session tinytext NOT NULL,
  putdate datetime NOT NULL default '0000-00-00 00:00:00',
  user tinytext NOT NULL
) TYPE = MyISAM;
```

该表由三个字段组成：

- id_session — Session 标识符
- putdate — 访问者最后访问网站页面的时间
- user — 用户

为了注册当前活跃的访问者，需要创建列表 II.5.2 所示的脚本。

# 列表 II.5.2. 用户注册

```php
<?php
//  session
session_start();
// 获取唯一的 SID
$id_session = session_id();
// 建立数据库连接
include "config.php";
// 检查数据库是否存在此类 SID
$query = "SELECT * FROM session WHERE id_session = '$id_session'";
$ses = mysql_query($query);
if(!$ses) exit("<p>查询会话表出错</p>");
// 如果存在此编号的会话，
// 用户在线。有必要
// 刷新最后访问时间。
if (mysql_num_rows($ses))>0)
{
$query = "UPDATE session SET putdate = NOW(), user = '$_SESSION[user] ' WHERE id_session = '$id_session'";
mysql_query($query);
}
// 如果没有此类 SID，用户刚刚
// 登录。有必要在表中
// 为新用户输入记录。
else
{
$query = "INSERT INTO session
```

## 第 II.5 章：Session 和 Cookie 231

```php
VALUES('$id_session', NOW(), '$_SESSION[user]');
if(!mysql_query($query)) {
  echo $query."<br>";
  echo "<p>添加新用户出错</p>";
  exit();
}
// 假设在过去 20 分钟内没有访问资源的用户已经离开，并从数据库中
// 删除 他们的 id_session 值。
$query = "DELETE FROM session
WHERE putdate < NOW() - INTERVAL '20' MINUTE";
mysql_query($query);
?>
```

在脚本开头，使用 `session_id()` 函数获取当前的 `session_id`。如果会话表中缺少此类标识符，则向数据库中添加一条新记录，这相当于新访问者的到达。如果会话表中存在 SID，说明该访问者已经进入，并且有必要更新访问时间和用户名，以防访问者已以其他身份授权或已完成授权。在脚本末尾，自上次更新访问时间以来已超过 20 分钟的所有记录将从数据库中删除。因此，该脚本记录了访问者的离开。

在聊天应用程序中，通常做法是通知其他访问者特定用户已离开资源。为了这一目的，需要选择所有自上次更新以来已超过 20 分钟的记录，并向具有相应姓名的访问者输出消息：“某某离开了聊天”。

之前在列表 II.55 中提供的脚本必须使用 `include` 指令包含在网站所有频繁访问的页面中。这样做是为了可靠地追踪访问者在网站上的存在状态。

在你组织好会话表的动态更新后，输出当前活跃的访问者列表将不再困难，如列表 II.5.3 所示。

# 列表 II.5.3. 输出当前在线访问者列表

```php
<?php
// 建立数据库连接
include "config.php";
// 输出会话表中有记录的所有访问者姓名
$query = "SELECT * FROM session";
$auth = mysql_query($query);
if(!$$auth) exit("<p>请求会话表出错</p>");
// 如果有人在，输出表格
if(mysql_num_rows($query) > 0) {
echo "<table>";
while($auth = mysql_fetch_array($auth)) {
    // 如果用户未注册，输出
    // 匿名字符串
    if(empty($auth['user'])) echo "<tr>Anonymous</td></tr>";
    else echo "<tr><td>" . $auth['user'] ."</td>></tr>";
}
echo "</table>";
}
?>
```

## II.5.2. 自定义会话

自定义会话机制可以通过注册 `session_set_save_handler()` 处理器来实现，该函数的语法如下：

```
session_set_save_handler(open, close, read, write, destroy, gc);
```

该函数接受六个字符串参数，这些是处理函数的名称。这些名称含义如下：

- open 在客户端代码应用 `session_start()` 函数初始化会话时执行的方法。建立数据库连接的代码应放在此处。
- close 终止操作的方法。终止数据库连接的代码应放在此处。
- read 从数据库中检索当前会话的数据。
- write 向数据库表中插入一条新记录，如果这是首次访问会话，则更新对应字符串的记录。
- destroy 抹毁会话的方法。放在此处的代码将删除指定当前会话的记录。
- gc 收集垃圾的方法。移除不再重要的旧记录。

数据将存储在会话表中，该表具有以下字段：

- id_session — 具有 AUTO_INCREMENT 属性表的主键
- session — 唯一的会话标识符
- putdate — 上次访问会话的日期
- value — 会话值（使用 `serialize()` 函数封装的数组）

