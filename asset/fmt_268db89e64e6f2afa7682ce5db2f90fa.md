
将找到薪资大于 3000 的每个位置。在这种情况下，三座城市中至少有一人薪资大于 3000。因此查询的第一部分将打印表中的所有行。共有七行。

迄今为止给出的命令可以在 MySQL、Oracle 和 Microsoft 的 Access 等数据库中工作。

如果使用编辑器在将 PHP 脚本上传到网站之前在计算机上开发，则首先要做的是查找它是否附带 PHPMyadmin 模块。

本书中的示例使用 EasyPHP 编辑器开发，可在以下网站获取- [`www.easyphp.org`](http://www.easyphp.org)。本书撰写时 PHP 的当前版本为 7，其界面已在第 1 章中展示。下面的界面适用于 PHP 5 系列。

![](img/00049.jpeg)

点击 MySQL Administration-PHPMyAdmin 模块，或在版本 7 中先启动数据库，然后再点击界面页面中间的 PHPMyAdmin。

会出现如下所示的页面。

![](img/00050.jpeg)

如图所示，可以使用左侧上方的 `new` 链接创建数据库。所有基于 Unix/Linux 的网络托管的 C-Panel 也会显示类似的屏幕。

上图顶部的菜单可列出与账户或安装相关的数据库，并可运行 SQL 命令。导出和导入允许备份数据库和输入批量数据。

因此，使用 EasyPHP 等开发软件可以模拟真实的托管环境。其中最重要的一点是找到数据库的路径。这在主机和开发软件上会略有不同。数据库路径方法将在主机的技术常见问题解答表中给出。要创建 staff 等表格，请点击结构标签并输入名称和列数，如下所示。

![](img/00051.jpeg)

要完成表格创建，输入 staff 表中每个字段的数据类型和字段长度，并选择 `sid` 作为主键。主键是值不重复且必需的字段。之前介绍的 staff 表的字段为 `sid`、`name`、`job`、`salary` 和 `location`。其中除 `salary` 为数字外，其余均为文本。

下面显示了表格字段详情。

![](img/00052.jpeg)

点击保存/继续按钮后，表格将被创建。PHPMyAdmin 屏幕左侧的结果将类似于下图。

![](img/00053.jpeg)

这些步骤与在实际网络托管上执行的操作非常相似，但界面方式或外观可能存在细微差异。

# 第 8 章. PHP 用于 MySQL 数据库

本章的重点是编写针对 MySQL 数据库和表的 PHP 代码。如果此脚本在独立计算机或笔记本电脑上的编辑器中运行，则首先要弄清楚的是数据库的路径。

如果代码直接在共享托管位置编写，此信息将在托管服务的常见问题解答部分提供。

在上一章中展示了 staff 表。本章将使用该表来演示 select、insert、update 和 delete 查询。

从数据库表获取数据或向其中添加数据的第一步是首先连接到 MySQL。注意：以下示例适用于 PHP 5 系列。有关版本 7，请查看本章末尾。

为此，使用 `mysql_connect` 函数在 PHP 中连接到 MySQL，当目标数据库为 MySQL 时。编程中打开的东西必须关闭，因此 `mysql_close()` 函数发挥此作用。

```
<html><body><?phpif($dx =mysql_connect('localhost','root ',' ')){print"Connected to MySQL.";mysql_close();} else {print"Could not connect to MySQL.";}?></body></html>
```

连接机制如上所示的 PHP 脚本所示。行 `mysql_connect('localhost',' root',' '))` 在使用的网络主机上会略有不同。`localhost` 后跟用户名和密码。

在独立机器上的开发软件的情况下，用户名通常为 `root`，但这需要在使用的 PHP 编辑器的帮助手册中进行验证。

现在在连接到 MySQL 之后，第二步是连接到所选数据库，然后连接到表以执行某些操作。让我们从选择或检索选项开始我们的操作示例。

```
<html><body><?php$link_id = mysql_connect( 'localhost','root','') or die ("Could not connect: " . mysql_error());mysql_select_db( "thottungal", $link_id );$sql = "SELECT * FROM staff";$result_id = mysql_query( $sql, $link_id ) or die ( "Statement failed: " . mysql_error() );$x=mysql_num_rows($result_id);print "<b>Total number of entries retrieved: </b>$x";print "<table border=1 width=800>";while ( $row = mysql_fetch_array( $result_id ) ) {print "<tr><td>".$row['sid']."</td>"."<td>".$row['name']."</td>"."<td>".$row['job']."</td>"."<td>".$row['salary']."</td>"."<td>".$row['location']."</td></tr>";}mysql_close( $link_id );print "</table>";?></body></html>
```

我们使用上一章中使用的 staff 表来检索其中的所有行。该表中共有七 (7) 行。上面代码行的含义如下：

`$link_id = mysql_connect( 'localhost','root','') or die ("Could not connect: " . mysql_error());`

连接到 My SQL。如果连接失败则给出错误并停止程序。

`mysql_select_db( "thottungal", $link_id );`

已连接到 MySQL 后查找数据库。

`$sql = "SELECT * FROM staff";`

编写需要在数据库中运行的查询。

`$result_id = mysql_query( $sql, $link_id ) or die ( "Statement failed: " . mysql_error() );`

运行查询并将结果保存到变量中或给出错误。

`$x=mysql_num_rows($result_id);`

此行将给出此查询可用的行数。

```
while ( $row = mysql_fetch_array( $result_id ) ) {
print "<tr><td>".$row['sid']."</td>"."<td>".$row['name']."</td>"."<td>".$row['job']."</td>"."<td>".$row['salary']."</td>"."<td>".$row['location']."</td></tr>";
}
```

查询的行将通过循环打印。这里使用 while 循环。查询中期望的每个列或字段都放在表格的行中。这里引号非常重要。通常的错误是没有用正确的引号括住元素。

`mysql_close( $link_id );`

## 数据库必须关闭，表也是如此。运行此代码的结果如下：

![](img/00054.jpeg)

如果不需要所有字段，则只需编写要显示的字段，其余的保持不变。

如果查询带有 where 条件 - 例如查找所有员工及其信息，如果其薪水大于 3000，则代码可以写成如下：

```
<html><body><?php$link_id = mysql_connect( 'localhost','root','') or die ("Could not connect: " . mysql_error());mysql_select_db( "thottungal", $link_id );$sql = "SELECT * FROM staff where salary >3000";$result_id = mysql_query( $sql, $link_id ) or die ( "Statement failed: " . mysql_error() );$x=mysql_num_rows($result_id);print "<b>Total number of entries retrieved: </b>$x";print "<table border=1 width=800>";while ( $row = mysql_fetch_array( $result_id ) ) {print "<tr><td>".$row['sid']."</td>"."<td>".$row['name']."</td>"."<td>".$row['job']."</td>"."<td>".$row['salary']."</td>"."<td>".$row['location']."</td></tr>";}mysql_close( $link_id );print "</table>";?></body></html>
```

结果如下：

![](img/00055.jpeg)

除了 `$sql` 行外没有变化。

插入数据是数据库表的重要组成部分。如果没有数据，则没有可检索的内容，数据库将实际上毫无用处。

为了演示使用 PHP 向 MySQL 中的表插入数据的方法，让我们按如下方式创建一个 PHP 文件：

PHP 文件末尾有一个表单，允许用户为表格中的每个字段输入值。`isset` 函数用于检查提交按钮是否被点击，如果是，则表单中输入的值将被插入到数据库中。可以在 `mysql_query( $sql, $link_id ) or die ( "Statement failed: " . mysql_error() );` 行之后写一个友好的提示信息。

在插入语句中，务必注意引号错误。数据录入的结果可以通过使用 `PHPMyadmin` 浏览表格来观察。

以下是针对上述代码的 PHPMyadmin 浏览搜索示例。

![](img/00056.jpeg)

### Update method

为了演示 PHP 代码中用于 MySQL 的更新方法，我们要记住在 Staff 表中 `sid` 是主键。

因此，下面的代码允许更新除此之外的所有其他字段。代码如下：

```
<html><body><?phpif (isset($_POST['submit'])){$link_id = mysql_connect( 'localhost','root','') or die ("Could not connect: " . mysql_error());mysql_select_db( "thottungal", $link_id );$sql = "update staff set name='{$_POST['name']}', job='{$_POST['job']}',salary='{$_POST['salary']}',location='{$_POST['location']}' where sid='{$_POST['sid']}'";$r =mysql_query( $sql, $link_id ) or die ( "Statement failed: " . mysql_error() );if (mysql_affected_rows() ==1){print"Table is updated.";}mysql_close( $link_id ); }?><form action="database.php" method="post">sid:<input type=text= name="sid" size ="20"><p>name:<input type=text= name="name" size ="50"><p>job:<input type=text= name="job" size ="30"><p>salary:<input type=text= name="salary" size ="10"><p>location:<input type=text= name="location" size ="30"><p><input type=submit name="submit" value="Update database"><p></form></body></html>
```

在上面的代码中，表单部分与插入代码的情况相同。变化在于查询以及用于设置更新字段的格式。主键是 `sid`。

这里使用了新的函数 `mysql_affected_rows()`，并且在 PHP 中进行更新/删除时使用该函数。结果可以通过以下方式在 PHPMyadmin 中浏览表格来观察：

![](img/00057.jpeg)

### Delete data

最后但并非最不重要的，从数据库中删除数据的代码如下：

```
<html><body><?phpif (isset($_POST['submit'])){$link_id = mysql_connect( 'localhost','root','') or die ("Could not connect: " . mysql_error());mysql_select_db( "thottungal", $link_id );$sql = "delete from staff where sid='{$_POST['sid']}' limit 1";$r =mysql_query( $sql, $link_id ) or die ( "Statement failed: " . mysql_error() );if (mysql_affected_rows() ==1){print"Row has been deleted.";}mysql_close( $link_id );}?><form action="database.php" method="post">sid:<input type=text= name="sid" size ="20"><p><input type=submit name="submit" value="Update database"><p></form></body></html>
```

在上面的代码中，用于从表中删除一行的查询以单词 `LIMIT 1` 结尾。这确保最多只删除一行。

删除和更新函数在数据库中使用时必须谨慎。一般来说，此功能仅限于特定角色。然而，在互联网网站上，用户需要更新或删除自己的信息。

`mysql_affected_rows()` 函数与删除代码一起使用。更新代码和删除代码之间有很多相似之处。

删除的结果可以通过 PHPMyadmin 如下观察：

![](img/00058.jpeg)

上面被删除的行是使用 `sid=107` 在插入代码中输入的那一行。

上面的删除代码可以修改为截断表，保留结构但不保留表中的数据。实现此操作的的代码行如下：

```
$link_id = mysql_connect( 'localhost','root','') or die ("Could not connect: " . mysql_error());
mysql_select_db( "thottungal", $link_id );
$sql = "truncate table staff";
```

也可以修改上面的代码行来删除表。

然而，截断和删除都是数据库管理员保留的功能，因此在实际情况下，除非授予了特定权限，否则程序员可能无法执行代码来执行这些功能。

#### Version 7 PHP

PHP 的第 7 版是一个主要版本，并且受新功能影响的领域之一是处理 MySQL 的方式。新的功能被称为 `mysqli`，其中 `i` 代表改进。好消息是，对于熟悉以前连接 MySQL 方式的人来说，可以轻松迁移到新功能，因为连接方式的相似性。

`mysqli_connect()` 替换 `mysql_connect()`

`mysqli_query()` 替换 `mysql_query()`

`mysqli_fetch_array()` 替换 `mysql_fetch_array()`

简而言之，除了 `mysql_` 之外，新函数以 `mysqli_` 开头。让我们看一个使用 PHP 7 中的新 mysqli 函数从 staff 数据中选择数据的示例。

```
<html><body><?php$link_id = mysqli_connect( 'localhost','root','','thottungal') or die ("Could not connect: " . mysqli_connect_error());$sql = "SELECT * FROM staff";$result_id = mysqli_query( $link_id, $sql ) or die ( "Statement failed: " . mysqli_error($sql) );$x=mysqli_num_rows($result_id);print "<b>Total number of entries retrieved: </b>$x";print "<table border=1 width=800>";while ( $row = mysqli_fetch_array( $result_id ) ) {print "<tr><td>".$row['sid']."</td>"."<td>".$row['name']."</td>"."<td>".$row['job']."</td>"."<td>".$row['salary']."</td>"."<td>".$row['location']."</td></tr>";}mysqli_free_result($result_id);mysqli_close( $link_id );print "</table>";?></body></html>
```
