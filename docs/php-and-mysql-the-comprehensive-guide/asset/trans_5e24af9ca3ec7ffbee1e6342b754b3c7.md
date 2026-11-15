

如有需要，解压缩存档并调整`config.inc.php`配置文件中的一些设置。你还必须在`php.ini`中启用`mbstring`扩展。

![](img/ae7820c36e8f24c1623d26668b28e80e_561_0.png)

图 19.5 MySQL Workbench

![](img/ae7820c36e8f24c1623d26668b28e80e_561_1.png)

图 19.6 phpMyAdmin警告配置不安全

### 作为"root"且无密码的连接设置

默认情况下，MySQL超级用户root的密码为空。phpMyAdmin的默认配置也如此。多年前，在一篇关于phpMyAdmin的杂志文章中，本行的作者曾机智地评论说这对于初步测试来说完全足够（居心叵测：这在生产系统中毫无立足之地！）。这反过来促使phpMyAdmin团队不仅给编辑写了一封愤怒的信，还发出了一条红色警告消息，当用户以root身份且密码为空时连接会显示该消息。几年后，这甚至被收紧，只有在事先进行额外配置后才允许无密码登录。我深感荣幸。

phpMyAdmin通过名为*config.inc.php*的文件进行配置。默认情况下不包含此文件，但*config.sample.inc.php*文件包含一个模板，你可以使用它来入门。你可以在在线用户手册中找到更多详细信息，网址为 http://s-prs.co/v602223。

如果一切正常，你将完全访问phpMyAdmin的强大功能。图 19.7显示起始页。

![](img/ae7820c36e8f24c1623d26668b28e80e_562_0.png)

图 19.7 phpMyAdmin的起始页（以root身份）

现在只缺少一小样东西，但至关重要：PHP的MySQL支持。Windows用户又很轻松：向*php.ini*添加一行——一切就绪。但是，自PHP 5.5版本起，"旧"扩展官方已弃用，并且还会引发E_DEPRECATED类型的警告。如已提及，PHP 8.x不再支持旧扩展（PHP 7也是如此）：

```
extension = mysqli # for the mysqli extension
 extension = php_mysql.dll # for the deprecated mysql extension
```

你还需要MySQL客户端库。幸运的是，这已经包含在内，并称为mysqli.nd。即使你没有启用MySQL扩展，在phpinfo()的输出中也会找到mysqli.nd的条目。

在Unix/Linux下，该扩展已集成到大多数发行版的二进制包中。如果你想自己编译，则需要为mysql扩展使用--with-mysql=/path/to/mysql配置开关。该扩展需要特殊程序mysql_config，该程序提供并接受配置选项。相应的开关随后称为--with-mysql=/path/to/mysql_config。因此，你在这里需要程序的完整路径，包括程序名。

然后值得再次调用phpinfo()（或php -m）以查看扩展是否处于活动状态。图 19.8显示了PHP 8.3下的输出。顺便说一句，MySQL的PDO扩展称为pdo_mysql，而非pdo_mysqli。

![](img/ae7820c36e8f24c1623d26668b28e80e_563_0.png)

图 19.8 “phpinfo()”输出中的“改进型”MySQL扩展

## 19.2 使用MySQL进行数据库访问

安装并配置MySQL后，其余部分不再是大问题。
现在最重要的步骤是建立连接、发送SQL命令，以及在必要时检查返回值。这正是你将在本节中看到的内容。作为基础，我们使用新创建的PHP数据库和名为user的用户。

### 19.2.1 连接设置

建立连接的函数称为mysqli_connect()。你可以指定最多六个参数，所有参数均为可选（归功于php.ini中的配置选项）：

- 1. 服务器名称
- 2. 用户名
- 3. 密码
- 4. 数据库名称（目录）
- 5. 端口号
- 6. 要使用的套接字名称

返回值是连接的句柄，你必须在其他MySQL函数中使用它。你使用mysqli_close()再次关闭连接。下面的清单显示了一个简单的测试示例。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    echo "Connection successful.";
    mysqli_close($db);
} else {
    echo "Error!";
}
?>
```

清单 19.1 使用MySQL进行连接设置（"mysqli-connect.php"）

如果你喜欢命名函数参数，可以按以下方式调用mysqli_connect()：

```php
mysqli_connect(
    host: "localhost",
    username: "user",
    passwd: "password",
    dbname: "PHP");
```

> 提示
>
> 你不一定必须随`mysqli_connect();`传递数据库名称；你也可以使用`mysqli_select_db()`函数。你向它传递连接的句柄和数据库名称：
>
> ```php
> <?php
> if ($db = mysqli_connect("localhost", "user", "password")) {
>     mysqli_select_db($db, "PHP");
>     echo "Connection successful.";
>     mysqli_close($db);
> } else {
>     echo "Error!";
> }
> ?>
> ```

`mysqli_connect()`的返回值是一个资源，因此类型为`resource`。这可以转换为整数值——以前是显式转换（通过添加`(int)`前缀），但自PHP 8起使用单独的函数：

```php
$id = get_resource_id(
    mysqli_connect( /* ... */ );
);
```

或者，MySQL扩展（但仅限`mysqli`）还提供面向对象访问。这有一个非常简单的规则：大多数`mysqli`函数随后可作为`MySQLi`对象的方法使用，同时删除`mysqli_`前缀。因此，`mysqli_close()`函数变成了`close()`方法。当然，也有对规则的小偏差，例如`mysqli_connect()`。对于此没有特殊方法，但它变成了对象的构造函数。下面的清单显示了面向对象风格的连接设置。

```php
<?php
try {
    $db = new MySQLi("localhost", "user", "password", "PHP");
    echo "Connection successfully established.";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 19.2 使用MySQL进行连接设置（"mysqli-connect-oop.php"）

我们并列展示这两种方法，但始终以通过函数进行的"旧"访问为起点。这样做的原因是，通常可以不费太多劲地将应用程序移植到mysqli扩展，因为通常只需调整函数名。

### 19.2.2 查询

对于没有返回值的查询，使用mysqli_query()。你传递连接的句柄和SQL命令。在我们的示例中，我们在PHP数据库中创建一个测试表。同样值得注意的是，自动值的数据类型是如何实现的。在MySQL中，你使用INT AUTO_INCREMENT PRIMARY KEY。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    $sql = "CREATE TABLE my_table (
    id INT AUTO_INCREMENT PRIMARY KEY,
    field VARCHAR(255)
    )";
    if (mysqli_query($db, $sql)) {
        echo "Table created.<br />";
    } else {
        echo "Error!";
    }
    $sql = "INSERT INTO my_table (field) VALUES ('Value1')";
    if (mysqli_query($db, $sql)) {
        echo "Data entered.<br />";
    } else {
        echo "Error!";
    }
    $sql = "INSERT INTO my_table (field) VALUES ('value2')";
    if (mysqli_query($db, $sql)) {
        echo "Data entered.";
    } else {
        echo "Error!";
    }
    mysqli_close($db);
} else {
    echo "Error!";
}
?>
```

清单 19.3 表被创建并填充（"mysqli-query.php"）

面向对象API中变化不大；本质上，mysqli_query()被query()方法取代。

```php
<?php
try {
  $db = new MySQLi("localhost", "user", "password", "PHP");
  $sql = "CREATE TABLE my_table (
    id INT AUTO_INCREMENT PRIMARY KEY,
    field VARCHAR(255)
  )";
  $db->query($sql);
  echo "Table created.<br />";

  $sql = "INSERT INTO my_table (field) VALUES ('value1')";
  $db->query($sql);
  echo "Data entered.<br />";

  $sql = "INSERT INTO my_table (field) VALUES ('Value2')";
  $db->query($sql);
  echo "Data entered.";

  $db->close();
} catch (Exception $ex) {
  echo "Error: " . $ex->getMessage();
}
?>
```

清单 19.4 表被创建并填充（"mysqli-query-oop.php"）

将静态值写入数据库（如示例中）没有安全问题。但是，对于来自表单数据、URL或Cookie等动态值，情况则不同。这里你必须防止输入中危险字符（另见第32章）。为此，有`mysqli_real_escape_string()`函数或`real_escape_string()`方法，例如将撇号转换为字符串`\\'`。下面是相应的代码片段：

```php
$value = $_POST["value"] ?? "";
$value = mysqli_real_escape_string($db, $value);
// alternatively: $value = $db->real_escape_string($value);
$sql = "INSERT INTO my_table (field) VALUES ('$value')";
```

> **注意**
>
> 为什么`mysqli_real_escape_string()`需要数据库连接的句柄？
> 这是个合理的问题，但有个好答案：在掩码数据时会考虑连接的字符集。函数名中的`real`部分也暗示了这一点。

1 顺便说一句，这与其他一些数据库不同，在这些数据库中，撇号需要通过加倍（''）来"降级"。

