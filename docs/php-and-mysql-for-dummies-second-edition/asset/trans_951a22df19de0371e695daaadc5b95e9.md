
/* Section that requests user input of query */
@$query=stripSlashes($_POST['query']);
if (@$_POST['queryButton'] != "Edit Query")
{
    $query = " ";
}
?>

<form action="<?php echo $_SERVER['PHP_SELF'] ?>?form=yes" method="POST">
<table>
<tr>
<td align=right><b>Type in database name</b></td>
<td><input type="text" name="database" value=<?php echo @$_POST['database'] ?> ></td>
</tr>
<tr>
<td align="right" valign="top">
<b>Type in SQL query</b></td>
<td><textarea name="query" cols="60" rows="10"><?php echo $query ?></textarea>
</td>
</tr>
<tr>
<td colspan="2" align="center"><input type="submit" value="Submit Query"></td>
</tr>
</table>
</form>
</body></html>

在使用它之前，您需要更改程序的第 9、10 和 11 行。这些行是

```
$host="hostname";
$user="mysqlaccountname";
$password="mysqlpassword";
```

将 hostname 更改为 MySQL 安装的计算机的名称：例如，databasehost.mycompany.com。如果 MySQL 数据库安装在与您的网站相同的计算机上，您可以使用 localhost 作为主机名。

将 mysqlaccountname 和 mysqlpassword 更改为您由 MySQL 管理员提供的用于访问 MySQL 数据库的账户名和密码。如果您自行安装了 MySQL，则会自动安装一个名为 root 且无密码的账户。有时还会安装一个账户名和密码均为空的账户。您可以使用 root 或空白账户，但最好专门为您的 Web 数据库应用程序安装一个账户。（我在第 5 章详细讨论了 MySQL 账户和密码。）

![](img/d82df0828cfbc6d6be1e9a991861f3b7_90_0.png)

名为 root 且无密码的账户不安全。您应立即为其设置密码。账户名和密码均为空的账户安全性更差。任何人都可以无需知道账户名或密码即可访问您的数据库。如果存在此账户，您应将其删除（参见第 5 章）。

如果您的 MySQL 账户不需要密码，请在双引号之间输入空内容，如下所示：

```
$password="";
```

在 mysql_send.php 中输入正确的主机名、账户名和密码后，执行 SQL 查询的一般步骤如下：

- 1. **将浏览器指向 mysql_send.php。**
  - 您会看到图 4-1 所示的网页。
- 2. **在大型文本框中输入 SQL 查询。**
- 3. **如果 SQL 查询需要，请在第一个文本框中输入数据库名称。**

我在本章的以下各节中解释了编写特定 SQL 查询的细节。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_90_1.png)

图 4-1：
由 mysql_send.php 生成的 SQL 查询网页。

- 4. **单击提交查询按钮。**

查询被执行，并显示一个页面，展示查询结果。如果您的查询有错误，则会显示错误消息。

您可以通过在前述步骤的第 2 步中输入此测试查询来测试 mysql_send.php 程序：

```
SHOW DATABASES
```

此查询不需要您输入数据库名称，因此您可以跳过第 3 步。当您在第 4 步中单击提交查询按钮时，会显示现有数据库的列表。在大多数情况下，您会看到一个名为 Test 的数据库，该数据库在安装 MySQL 时会自动安装。此外，您可能还会看到一个名为 mysql 的数据库，MySQL 使用它来存储所需的信息，例如账户名、密码和权限。即使没有现有数据库，您的 SQL 查询也会正确执行。如果出现问题，将显示错误消息。MySQL 错误消息通常对查找问题很有帮助。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_91_0.png)

## 向 MySQL 服务器发送 SQL 查询的更快方法

安装 MySQL 时，还会安装一个名为 mysql（有时也称为终端监视器或监视器）的简单文本程序。与服务器通信的程序是客户端软件；由于此程序与 MySQL 服务器通信，因此它是客户端。当您在此客户端中输入 SQL 查询时，响应会返回到客户端并显示在屏幕上。监视器程序可以通过网络发送查询；它不必运行在数据库存储的机器上。

要使用 mysql 客户端向 MySQL 发送 SQL 查询，请按照以下步骤操作：

- 1. 找到 mysql 客户端。

默认情况下，mysql 客户端程序安装在 MySQL 安装目录下的 bin 子目录中。在 Unix/Linux 中，默认位置为 /usr/local/mysql/bin 或 /usr/local/bin。在 Windows 中，默认位置为 c:\mysql\bin。但是，客户端可能已安装在不同的目录中。或者，如果您不是 MySQL 管理员，您可能无法访问 mysql 客户端。如果您不知道 MySQL 安装在哪里或无法运行客户端，请要求 MySQL 管理员将客户端放在您可以运行的位置，或提供一份副本供您放在自己的计算机上。

- 2. 启动客户端。

在 Unix/Linux 中，输入路径/文件名（例如，/usr/local/mysql/bin/mysql）。在 Windows 中，打开命令提示符窗口，然后输入路径/文件名（例如，c:\mysql\bin\mysql.exe）。在输入路径/文件名后按 Enter，除非您使用第 3 步中显示的参数。

- 3. **如果您启动 `mysql` 客户端以通过网络访问数据库，请在 `mysql` 命令后使用以下参数：**
  - `-h host` 是 MySQL 所在机器的名称。
  - `-u user` 是您的 MySQL 账户名。
  - `-p`：此参数会提示您输入 MySQL 账户的密码。

例如，如果您位于 `mysql` 客户端所在的目录中，命令可能如下所示：

```text
mysql -h mysqlhost.mycompany.com -u root -p
```

输入命令后按 Enter。

- 4. **在提示时输入您的密码。**

`mysql` 客户端启动，您会看到类似以下内容：

```text
Welcome to the MySQL monitor. Commands end with ; or \g.
Your MySQL connection id is 459 to server version: 4.0.13
Type 'help;' or '\\h' for help. Type '\\c' to clear the buffer.
mysql>
```

- 5. **选择您要使用的数据库。**

在 `mysql` 提示符下，输入以下内容：

```text
use databasename
```

使用您要查询的数据库的名称。

- 6. **在 `mysql` 提示符下，输入您的 SQL 查询，后跟分号（;），然后按 Enter 键。**

`mysql` 客户端会继续提示输入，直到您输入分号才会执行查询。查询的响应会显示在屏幕上。

- 7. **要退出 `mysql` 客户端，请在提示符下输入 `quit`，然后按 Enter 键。**

## 构建数据库

数据库有两个部分：用于存储数据的结构和数据本身。在接下来的几个部分中，我将解释如何创建数据库结构。首先，您创建一个没有任何结构的空数据库，然后向其中添加表。

您用于操作数据库结构的 SQL 查询是 `CREATE`、`ALTER`、`DROP` 和 `SHOW`。要使用这些查询，您必须拥有具有创建、修改和删除数据库和表的权限的 MySQL 账户。有关 MySQL 账户的更多信息，请参阅第 5 章。

### 创建新数据库

要创建新的空数据库，请使用以下 SQL 查询：

```
CREATE DATABASE databasename
```

其中 databasename 是您为数据库指定的名称。例如，以下两个 SQL 查询创建了本书中使用的示例数据库：

```
CREATE DATABASE PetCatalog
CREATE DATABASE MemberDirectory
```

![](img/d82df0828cfbc6d6be1e9a991861f3b7_93_0.png)

一些 Web 主机公司不允许您创建新数据库。您只能使用一个与 MySQL 配合使用的数据库，并且只能在此数据库中创建表。您可以尝试请求另一个数据库，但需要有充分的理由。MySQL 和 PHP 不在乎您的所有表都在一个数据库中，而不是按有意义的名称组织到不同的数据库中。只是对人类来说，当项目有组织时更容易跟踪。

为了亲自确认数据库是否已创建，请使用此 SQL 查询：

```
SHOW DATABASES
```

创建空数据库后，您可以向其中添加表。（在本章后面描述了向数据库添加表。）

### 删除数据库

您可以使用此 SQL 查询删除任何数据库：

```
DROP DATABASE databasename
```

![](img/d82df0828cfbc6d6be1e9a991861f3b7_93_1.png)

请谨慎使用 DROP，因为它是不可逆的。数据库被删除后将永远消失。其中的任何数据也将随之消失。

### 向数据库添加表

您可以向任何数据库添加表，无论是您刚刚创建的新空数据库，还是已包含表和数据的现有数据库。您使用 CREATE 查询向数据库添加表。

我在第 3 章中介绍的示例数据库设计中，PetCatalog 数据库设计了三个表：Pet、PetType 和 PetColor。MemberDirectory 数据库设计了两个表：Member 和 Login。由于表是在数据库中创建的，因此您必须指定要创建表的数据库名称。也就是说，使用所示的表单时
