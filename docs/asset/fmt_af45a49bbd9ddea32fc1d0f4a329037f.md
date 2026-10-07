
逻辑流程与之前的版本 5 相同。`$link_id` 连接到数据库。这里的区别是 `mysqli_connect` 括号内需要输入四个元素。最后一个是数据库名称。其余条目对于开发目的的本地安装是正确的，并且在托管站点上会略有不同。如果网站位于共享托管站点，则需要从共享托管站点的技术支持处获取这些值。

在将查询赋给 `$sql` 之后，`mysqli_fetch_array` 创建的数组中获得的行数将被打印。然后如代码所示打印出数组。程序通过释放查询的内存然后关闭连接来结束。`mysqli_fetch_array` 函数可以处理带有字符串或数字关键字的数组。

因此，除了上面提到的两个段落中的区域外，PHP 5 和 7 的版本非常相似。现在让我们尝试将一行插入到数据库中。版本 5 的相同代码将在下面修改以适应版本 7。

进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

### PHP 数据库操作示例

```
<html><body><?phpif (isset($_POST['submit'])){$link_id = mysqli_connect( 'localhost','root','','thottungal') or die ("Could not connect: " . mysqli_connect_error());$sql = "insert into staff (sid,name,job,salary,location) values('$_POST['sid']','$_POST['name']','$_POST['job']','$_POST['salary']', '$_POST['location']')";mysqli_query($link_id, $sql) or die ( "Statement failed: " . mysqli_error($sql) );mysqli_close( $link_id );}?><form action="database.php" method="post">sid:<input type=text= name="sid" size ="20"><p>name:<input type=text= name="name" size ="50"><p>job:<input type=text= name="job" size ="30"><p>salary:<input type=text= name="salary" size ="10"><p>location:<input type=text= name="location" size ="30"><p><input type=submit name="submit" value="add to database"><p></form></body></html>
```

与前一版本类似，我们连接到数据库并执行查询然后关闭连接。该单文件 PHP 包含一个用于显示的表单，使用 `isset()` 函数在验证提交按钮被点击后进行插入。让我们来看一下更新的代码。

```
<html><body><?phpif (isset($_POST['submit'])){$link_id = mysqli_connect( 'localhost','root','','thottungal') or die ("Could not connect: " . mysql_error());$sql = "update staff set name='$_POST['name']', job='$_POST['job']',salary='$_POST['salary']',location='$_POST['location']' where sid='$_POST['sid']'";$r =mysqli_query( $link_id, $sql ) or die ( "Statement failed: " . mysqli_error($sql) );if ($r){print"Table is updated.";}mysqli_close( $link_id );}?><form action="database.php" method="post">sid:<input type=text= name="sid" size ="20"><p>name:<input type=text= name="name" size ="50"><p>job:<input type=text= name="job" size ="30"><p>salary:<input type=text= name="salary" size ="10"><p>location:<input type=text= name="location" size ="30"><p><input type=submit name="submit" value="Update database"><p></form></body></html>
```

与使用 PHP 5 版本的相同代码相比，此处的不同之处在于 `mysql_affected_rows` 已被 if 语句取代，同时在 `mysql_functions` 之后使用了 i。

要删除一行，将 `$sql` 中的查询替换为 `"delete from staff where sid='$_POST['sid']' limit 1"` 并移除除 `sid` 之外的所有输入文本框，`sid` 是主键。

if 条件下的消息应为 `if ($r) { print"Row deleted"}`

## 第 9 章. PHP 用于 Oracle 数据库

在上一章中讨论的数据库是 MySQL。在本章中，让我们来看一下 PHP 与 Oracle 数据库的关系。这里讨论的 Oracle 数据库是 express 版本 11.2。如果客户端或独立机器上没有安装，附录 II 展示了如何安装它。

要使用 PHP 与 Oracle 进行配合，需要对 PHP 安装进行一些配置更改。本书的代码使用 WAMP 编辑器 EasyPHP 开发，该编辑器有多个版本。并非必须使用最新版本，但运行本书代码所需的最低编辑器版本是运行 PHP 5 及以上的版本。使用编辑器或类似工具连接到 Oracle 所需的配置更改在附录 III 和 IV 中显示。

非常重要的是要写下 Oracle 安装的默认值。在本章的示例中，默认安装的数据库称为 `orcl`。`hr` 用户及其关联的表将被使用。

让我们在 Oracle 数据库的 `hr` 用户下创建一个名为 `employee` 的表，密码为 `hr`。为此，请从 Windows 开始菜单中的 Oracle 应用菜单使用 SQL Plus 接口。界面看起来像这样。如果 `hr` 账户被锁定，以 `sysdba` 登录并使用以下命令 - `alter user hr account unlock;` 然后连接到 `hr`。

![](img/00059.jpeg)

要创建 employee 表，使用以下命令：

```
create table employee (sid varchar2(10), name varchar2(50), manager varchar2(10) constraint sid_pk primary key = (sid));
```

这将创建 employee 表并将 `sid` 设为主键。就本书而言，这个简单的表已足够。如果 Oracle 相关的 SQL 对你来说是新的，我的 SQL 书籍可能会有所帮助。

如果已按照附录 III 和 IV 中讨论的方式对 `PHP.ini`（配置文件）进行了更改并保存，那么现在是时候了解 PHP 连接器用于 Oracle 了。PHP 程序使用 PHP `OCI8` 扩展连接到 Oracle 数据库。

在撰写本书时，该扩展可用于 Oracle 12、11、10 和 9 数据库。PHP 本身与 Oracle 数据库无关。

要连接到数据库，OCI8 PHP 类库提供了以下函数 `oci_connect()`、`oci_pconnect()` 和 `oci_new_connect()`。如果需要非持久连接，则使用 `oci_connect()`。这也是缓存的。这提高了连接效率。

`oci_connect` 使用的缓存会在脚本运行后或连接资源被关闭时被移除。

`oci_new_connect` 不会被缓存，而 `oci_pconnect()` 会被缓存并可在请求之间使用。`oci_close()` 函数与前面提到的三个函数中的任何一个一起使用都是必需的。

在上面使用 create 语句创建 employee 表之后，必须插入值。

最简单的方法是使用如下的 insert 语句：

```
insert into employee values('101','Albert','103');
```

并类似地插入上一页图片中显示的其他三行数据。

安装 Oracle 后，找到 `tnsnames.ora` 文件，通常位于 `network/admin/` 文件夹中。该文件会给出数据库的 `sid` 值。默认是如本章前面提到的 `orcl`。通常端口是 `1521`，主机为本地。如果是独立计算机或笔记本上安装的 Oracle 11.2 express，则主机为该安装。

`oci_connect()` 函数有三个部分 - 用户名、密码和 connection_string。

由于我们要连接到 `hr` 用户下的表，因此用户名为 `hr`，密码为 `hr`，连接字符串为 `orcl` - 即 sid 名称或数据库名称。

确保 sid 名称与 `tnsmames.ora` 文件中所述完全一致。

`oci_parse()` 用于解析查询。

`oci_execute()` 用于执行语句。

`oci_fetch_array()` 用于以数组格式获取查询的下一行。

最后 `oci_close()` 将关闭与数据库的连接。

可能会注意到所有这些步骤都与 PHP 连接到 MySQL 数据库的方式相似。现在让我们来看下面的代码。

```
<?php
$db = oci_connect('hr', 'hr', 'orcl');
if (!$db) {trigger_error('Unable to connect to database', E_USER_ERROR);}
$sql = 'select * from employee';
$stmt = oci_parse($db, $sql);
oci_execute($stmt);
$count = 0;
print"<table border=1>";
while (($row = oci_fetch_array($stmt,OCI_BOTH)) != false) {
print "<tr><td>".$row['0']."</td>"."<td>".$row['1']."</td>"."<td>".$row['2']."</td></tr>";
$count++;
}
print"</table>";
print $count . ' record(s) found.';
oci_free_statement($stmt);
```

```
oci_close($db);?></body></html>
```

输出如下：

![](img/00060.jpeg)

`oci_free_statement()` 函数主要与 select 查询一起使用，因为会涉及大量数据，最好在执行此类查询后清除内存。

在上面的代码中，`oci_fetch_array` 有两个参数 - 正在解析的语句和数组键的类型。`OCI_BOTH` 表示数组同时使用字符串和数字键。如果键是字符串，则可改用 `OCI_ASSOC`。`row[0]` 表示数组中 oracle 表的第一列。

如果需要使用每个 Oracle 表的列标题，请记住名称可能区分大小写。默认情况下，列标题为大写字母。因此，如果需要将列标题而不是数字用作数组键，上面的代码可以修改如下。

```
while (($row = oci_fetch_array($stmt,OCI_BOTH)) != false) {print '<tr><td>'.$row["SID"].'</td>'.'<td>'.$row["NAME"].'</td>'.'<td>'.$row["MANAGER"].'</td></tr>';}
```

其余代码保持不变。PHP 中有一个名为 `htmlentities` 的函数。其目的是将所有适用字符转换为 HTML 实体。它接受两个参数。其中一个是字符串或输入，另一个参数必须从下面选择：

`ENT_COMPAT` - 将双引号转换并保留单引号。

`ENT_QOUTES` - 将双引号和单引号都转换。

`ENT_NOQOUTES` - 将双引号和单引号都保持不转换。

`ENT_IGNORE` - 丢弃无效代码单元序列，而不是返回空字符串。由于安全问题，应谨慎使用。

`ENT_SUBSTITUTE` - 用 Unicode 替换字符 U + FFFD（UTF-8）或 `&#FFFD` 替换无效代码单元序列，而不是返回空字符串。

`ENT_DISALLOWED` - 用替换字符 U + FFFD（UTF-8）或 `&#FFFD` 替换给定文档类型中无效的代码点，而不是保留原样。在包含嵌入外部内容的 XML 文档中有用。

让我们修改上面的代码以使用 html 实体打印员工表的输出结果。

```
<?php
$db = oci_connect('hr', 'hr', 'orcl');
if (!$db) {trigger_error('Unable to connect to database', e_user_error);}
$sql = 'select * from employee';
$stmt = oci_parse($db, $sql);
oci_execute($stmt);
$count = 0;
print"<table border=1>";
while (($row = oci_fetch_array($stmt,OCI_ASSOC+OCI_RETURN_NULLS)) != false) {
echo "<tr>";
foreach ($row as $item) {
```

```
echo "<td>" . ($item !== null ? htmlentities($item, ENT_QUOTES) : "&nbsp;") . "</td>\n";    
}
print "</tr>";
$count++;
}
print"</table>";
print $count . ' record(s) found.';
oci_free_statement($stmt);
oci_close($db);
?></body></html>
```

输出将与之前的代码相同。这里的不同之处在于无需以数字或非数字方式提及键值。

现在让我们看一个向 Oracle 数据库插入数据的代码。

```
<?php
$db = oci_connect('hr', 'hr', 'orcl');
if (!$db) {trigger_error('Unable to connect to database', e_user_error);}
$sql = "insert into employee (sid,name,manager) values ('104','Adam','102')";
$stmt = oci_parse($db, $sql);
oci_execute($stmt, OCI_NO_AUTO_COMMIT);
oci_commit($db);
oci_close($db);
?></body></html>
```

执行语句后跟一个提交以确认向数据库表插入。

`oci_execute()` 函数接受两个参数。第一个是如上所示的解析语句，第二个是一个方法。`oci_execute()` 中可用的方法如下：

`OCI_COMMIT_ON_SUCCESS` - 当语句成功时，这将自动提交此连接的所有未决更改。这是默认值。

`OCI_DEFAULT` - 这是一种旧方法，可能在使用的 OCI8 版本中可用，但自 PHP 5.3.2 版本以来不建议使用。

`OCI_NO_AUTO_COMMIT` - 与上面示例中使用的类似，不提交更改。因此如果需要提交，则必须使用 `oci_commit()`，类似于上面的示例。如果未使用此方法，执行语句请求的任何更改将在程序退出后回滚。

上面示例中完成的插入可以通过另一种方法完成。此方法涉及使用 OCI8 函数 `oci_bind_by_name()`。

`oci_bind_by_name()` 将 PHP 变量绑定到 Oracle 占位符。此绑定可提高数据库性能，也是避免 SQL 注入安全问题的一种方法。SQL 注入是一种计算机攻击，其中恶意代码嵌入到设计不佳的应用程序中，然后传递到后端数据库。绑定变量不被视为 SQL 语句的一部分，因此减少了 SQL 注入问题。代码如下：
