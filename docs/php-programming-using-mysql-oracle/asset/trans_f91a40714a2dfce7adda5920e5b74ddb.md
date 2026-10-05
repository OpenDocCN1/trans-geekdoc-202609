
PHP 文件末尾有一个表单，允许用户为表格中的每个字段输入值。`isset` 函数用于检查提交按钮是否被点击，如果是，则表单中输入的值将被插入到数据库中。可以在 `mysql_query( $sql, $link_id ) or die ( "Statement failed: " . mysql_error() );` 行之后写一个友好的提示信息。

在插入语句中，务必注意引号错误。数据录入的结果可以通过使用 `PHPMyadmin` 浏览表格来观察。

以下是针对上述代码的 PHPMyadmin 浏览搜索示例。

![](images/00056.jpeg)

### Update method

为了演示 PHP 代码中用于 MySQL 的更新方法，我们要记住在 Staff 表中 `sid` 是主键。

因此，下面的代码允许更新除此之外的所有其他字段。代码如下：

```
<html><body><?phpif (isset($_POST['submit'])){$link_id = mysql_connect( 'localhost','root','') or die ("Could not connect: " . mysql_error());mysql_select_db( "thottungal", $link_id );$sql = "update staff set name='{$_POST['name']}', job='{$_POST['job']}',salary='{$_POST['salary']}',location='{$_POST['location']}' where sid='{$_POST['sid']}'";$r =mysql_query( $sql, $link_id ) or die ( "Statement failed: " . mysql_error() );if (mysql_affected_rows() ==1){print"Table is updated.";}mysql_close( $link_id ); }?><form action="database.php" method="post">sid:<input type=text= name="sid" size ="20"><p>name:<input type=text= name="name" size ="50"><p>job:<input type=text= name="job" size ="30"><p>salary:<input type=text= name="salary" size ="10"><p>location:<input type=text= name="location" size ="30"><p><input type=submit name="submit" value="Update database"><p></form></body></html>
```

在上面的代码中，表单部分与插入代码的情况相同。变化在于查询以及用于设置更新字段的格式。主键是 `sid`。

这里使用了新的函数 `mysql_affected_rows()`，并且在 PHP 中进行更新/删除时使用该函数。结果可以通过以下方式在 PHPMyadmin 中浏览表格来观察：

![](images/00057.jpeg)

# Delete data

最后但并非最不重要的，从数据库中删除数据的代码如下：

```
<html><body><?phpif (isset($_POST['submit'])){$link_id = mysql_connect( 'localhost','root','') or die ("Could not connect: " . mysql_error());mysql_select_db( "thottungal", $link_id );$sql = "delete from staff where sid='{$_POST['sid']}' limit 1";$r =mysql_query( $sql, $link_id ) or die ( "Statement failed: " . mysql_error() );if (mysql_affected_rows() ==1){print"Row has been deleted.";}mysql_close( $link_id );}?><form action="database.php" method="post">sid:<input type=text= name="sid" size ="20"><p><input type=submit name="submit" value="Update database"><p></form></body></html>
```

在上面的代码中，用于从表中删除一行的查询以单词 `LIMIT 1` 结尾。这确保最多只删除一行。

删除和更新函数在数据库中使用时必须谨慎。一般来说，此功能仅限于特定角色。然而，在互联网网站上，用户需要更新或删除自己的信息。

`mysql_affected_rows()` 函数与删除代码一起使用。更新代码和删除代码之间有很多相似之处。

删除的结果可以通过 PHPMyadmin 如下观察：

![](images/00058.jpeg)

上面被删除的行是使用 `sid=107` 在插入代码中输入的那一行。

上面的删除代码可以修改为截断表，保留结构但不保留表中的数据。实现此操作的的代码行如下：

```
$link_id = mysql_connect( 'localhost','root','') or die ("Could not connect: " . mysql_error());
mysql_select_db( "thottungal", $link_id );
$sql = "truncate table staff";
```

也可以修改上面的代码行来删除表。

然而，截断和删除都是数据库管理员保留的功能，因此在实际情况下，除非授予了特定权限，否则程序员可能无法执行代码来执行这些功能。

## Version 7 PHP

PHP 的第 7 版是一个主要版本，并且受新功能影响的领域之一是处理 MySQL 的方式。新的功能被称为 `mysqli`，其中 `i` 代表改进。好消息是，对于熟悉以前连接 MySQL 方式的人来说，可以轻松迁移到新功能，因为连接方式的相似性。

`mysqli_connect()` 替换 `mysql_connect()`

`mysqli_query()` 替换 `mysql_query()`

`mysqli_fetch_array()` 替换 `mysql_fetch_array()`

简而言之，除了 `mysql_` 之外，新函数以 `mysqli_` 开头。让我们看一个使用 PHP 7 中的新 mysqli 函数从 staff 数据中选择数据的示例。

```
<html><body><?php$link_id = mysqli_connect( 'localhost','root','','thottungal') or die ("Could not connect: " . mysqli_connect_error());$sql = "SELECT * FROM staff";$result_id = mysqli_query( $link_id, $sql ) or die ( "Statement failed: " . mysqli_error($sql) );$x=mysqli_num_rows($result_id);print "<b>Total number of entries retrieved: </b>$x";print "<table border=1 width=800>";while ( $row = mysqli_fetch_array( $result_id ) ) {print "<tr><td>".$row['sid']."</td>"."<td>".$row['name']."</td>"."<td>".$row['job']."</td>"."<td>".$row['salary']."</td>"."<td>".$row['location']."</td></tr>";}mysqli_free_result($result_id);mysqli_close( $link_id );print "</table>";?></body></html>
```

逻辑流程与之前的版本 5 相同。`$link_id` 连接到数据库。这里的区别是 `mysqli_connect` 括号内需要输入四个元素。最后一个是数据库名称。其余条目对于开发目的的本地安装是正确的，并且在托管站点上会略有不同。如果网站位于共享托管站点，则需要从共享托管站点的技术支持处获取这些值。

在将查询赋给 `$sql` 之后，`mysqli_fetch_array` 创建的数组中获得的行数将被打印。然后如代码所示打印出数组。程序通过释放查询的内存然后关闭连接来结束。`mysqli_fetch_array` 函数可以处理带有字符串或数字关键字的数组。

因此，除了上面提到的两个段落中的区域外，PHP 5 和 7 的版本非常相似。现在让我们尝试将一行插入到数据库中。版本 5 的相同代码将在下面修改以适应版本 7。

