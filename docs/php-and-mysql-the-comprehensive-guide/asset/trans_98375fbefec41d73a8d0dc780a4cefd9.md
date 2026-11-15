

![](img/ae7820c36e8f24c1623d26668b28e80e_660_0.png)

图 23.1 Windows 安装程序的安装选项

对于 Unix/Linux，要么有预配置的软件包，要么发行版本身就已经自带了数据库。如果你想手动设置软件，安装过程与通常情况相同。也就是说，解压下载的归档文件，然后执行神奇的三个步骤（最后一步 `make install` 需要 root 权限，当然）：

```
./configure
make
make install
```

接着是配置。首先创建一个用户，就像 Windows 安装程序所做的那样：

```
adduser postgres
```

现在在属于 postgres 用户的 PostgreSQL 目录中创建一个名为 *data* 的子目录：

```
cd /usr/local/pgsql
mkdir data
chown postgres data
```

然后以 postgres 用户身份登录，并使用以下命令初始化 PostgreSQL：

```
/usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data
```

如果上述操作成功，你可以启动 `postmaster` 程序，即实际的 PostgreSQL 守护进程。具体做法如下：

```
/usr/local/pgsql/bin/postmaster -D /usr/local/pgsql/data &
```

注意

最后一步是创建代码中将使用的数据库。如果你使用的是 Unix/Linux 或 macOS，请按以下方式创建数据库：

createdb PHP

Windows 用户还有另一个选择：在 PostgreSQL 程序组中，有一个 pgAdmin 4 条目。pgAdmin 4 是一个功能强大、基于图形和 Web 的 PostgreSQL 管理工具。（它也非常适合检查 PHP 编程的结果。）你也可以用它来创建 PHP 数据库。此方法也适用于其他操作系统的用户。你可以在 www.pgadmin.org 获取 pgAdmin。

提示

还有一个用于 PostgreSQL 数据库的基于 Web 的管理程序：phpPgAdmin，最初可于 http://s-prs.co/v602233 获取。该项目沉寂了几年，但现在 GitHub 上有一个更新的版本（新管理下）。你可以在那里找到它：http://s-prs.co/v602234。然而，使用 pgAdmin 4 可能更好，因为它维护得更加积极（见图 23.2）。

![](img/ae7820c36e8f24c1623d26668b28e80e_661_0.png)

图 23.2 新数据库在 pgAdmin 4 中方便地创建

其余所有操作都直接在 PHP 代码中完成。说到 PHP，当然也必须告知它要支持 PostgreSQL。在 Windows 上，这是通过在 php.ini 文件中添加一个简单条目来完成的：

```
extension=pgsql
```

如果你自己编译 PHP，请使用 --with-pgsql=/path/to/pgsql 开关进行配置，然后重新编译。接下来是必不可少的步骤：查看 phpinfo() 的输出，确认安装是否成功。你可能会收到类似图 23.3 中所示的消息。在 Windows 上可能的原因是：PostgreSQL 扩展需要 libpq.dll 库，该库位于 PHP 目录中。在某些系统上，该 DLL 必须位于系统路径中才能被找到。到这一步最迟，你应该会看到如图 23.4 所示的屏幕：扩展已设置。

![](img/ae7820c36e8f24c1623d26668b28e80e_662_0.png)

图 23.3 未找到 DLL（尚未找到）

![](img/ae7820c36e8f24c1623d26668b28e80e_662_1.png)

图 23.4 PostgreSQL 扩展已成功安装

## 23.2 使用 PostgreSQL 进行数据库访问

数据库名称可能不同，工作方式也与之前的不同，但相关任务始终相同：建立连接、发送 SQL 命令和查询返回值。值得庆幸的是，函数名称也相似。

### 23.2.1 连接设置

用于连接 PostgreSQL 数据库的函数名为 pg_connect()（或 pg_pconnect(), 其中 p 代表 persistent）。所有 PHP PostgreSQL 函数都以前缀 pg_- 开头。你将连接字符串作为参数指定。有许多可能性；这里你可以看到一个包含大量信息（以及不安全密码）的版本：

```
"host=localhost port=5432 dbname=PHP user=postgres password=pwd."
```

因此，你指定服务器、端口、数据库名称和用户数据。1 服务器和端口按默认值指定，因此在某些情况下可以省略。pg_connect() 函数返回一个连接句柄，如果出错则返回 false。使用 pg_close() 可以再次关闭连接。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres password=pwd.")) {
    echo "Connection established successfully.";
    pg_close($db);
} else {
    echo "Error!";
}
?>
```

清单 23.1 建立数据库连接 ("pgsql-connect.php")

> 注意
> 如果使用相同的连接字符串两次调用 pg_connect()，则不会打开新连接，而是重复使用之前的连接（并将其返回）。

### 23.2.2 查询

使用 pg_query() 向数据库发送 SQL 命令。这是在数据库中创建测试表的绝佳方法。唯一的特殊之处是（再次）自动值，在 PostgreSQL 中通过特殊数据类型 SERIAL 实现。如果出现问题，pg_last_error() 函数返回最后发生的错误文本。但是，如果 pg_connect() 发生错误，则此方法无效；在此示例中，它仅对 pg_query() 的调用有效。

1 你当然必须输入你数据库使用的数据；我们的密码不符合任何安全标准，你不应该直接使用 postgres 用户，而应该创建一个应用程序特定的用户。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
    password=pwd.")) {
    $sql = "CREATE TABLE my_table (
    id SERIAL PRIMARY KEY,
    field VARCHAR(255)
    )";
    if (pg_query($db, $sql)) {
        echo "Table created.<br />";
    } else {
        echo "Error: " . pg_last_error() . "!";
    }
    $sql = "INSERT INTO my_table (field) VALUES ('value1')";
    if (pg_query($db, $sql)) {
        echo "Data entered.<br />";
    } else {
        echo "Error: " . pg_last_error() . "!";
    }
    $sql = "INSERT INTO my_table (field) VALUES ('value2')";
    if (pg_query($db, $sql)) {
        echo "Data entered.";
    } else {
        echo "Error: " . pg_last_error() . "!";
    }
    pg_close($db);
} else {
    echo "Error!";
}
?>
```

清单 23.2 将数据写入数据库 ("pgsql-query.php")

> 提示
> 
> PHP 的 PostgreSQL 模块还支持一个特殊的辅助函数，用于从值中释放危险的 SQL 特殊字符或正确地对其进行转义。你应该在将所有动态数据用于 SQL 命令之前使用此函数 pg_escape_string()。

例如，使用 pgAdmin 查看表。你会看到一个序列已自动创建（见图 23.5），这可能与你在 Oracle 中所见类似（另见第 22 章）。每次将序列插入表中时，它都会递增 1；新表条目的 id 字段随后会自动包含序列的当前值。这个“变通方法”用于实现自动值。

![](img/ae7820c36e8f24c1623d26668b28e80e_665_0.png)

图 23.5 自动创建的序列

### IDs 和 OIDs

当你查看表的 SQL 命令时，会注意到另一个特殊之处——不是你自己发出的命令，而是 pgAdmin 中显示的命令：

```
CREATE TABLE my_table
(
  id serial NOT NULL,
  field varchar(255),
  CONSTRAINT my_table_pkey PRIMARY KEY (id)
)
WITH OIDS;
```

首先，已集成主键约束；其次，命令以 WITH OIDS 结尾。这些是全局 PostgreSQL ID，即比自动值高一级的 ID。如果激活了 WITH OIDS，则每个表条目都有一个在数据库中唯一的 ID。你可以在 WHERE 条件中查询 OID，但不能直接读取它（因此 SELECT oid FROM my_table 不可行）。为什么这很重要？如果你想在插入操作后确定自动值，在 PostgreSQL 中这并不容易。但是，PHP 提供了一种查找相应 OID 的方法。这反过来又允许访问自动值。有关详细信息，请参阅第 23.2.4 节。在较新的 PostgreSQL 版本中，也可以停用 OID——因此请确保你的测试数据库支持 OID。

