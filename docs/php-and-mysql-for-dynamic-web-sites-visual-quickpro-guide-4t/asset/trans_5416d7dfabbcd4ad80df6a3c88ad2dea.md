

现在已经设置了密码，你需要在连接命令中添加 `-p` 标志。你将看到 `Enter password:` 提示符，输入刚刚创建的密码即可。

### 通过 phpMyAdmin 为 root 用户分配密码

1.  在 Web 浏览器中打开 phpMyAdmin。
    详细说明请参阅前面的步骤。
2.  在主页上，单击“Privileges”（权限）选项卡。
    你始终可以单击左上角的主页图标返回主页。
3.  在用户列表中，单击 root 用户所在行的“Edit Privileges”（编辑权限）图标 ![Image](graphics/circle-b.jpg)。
    ![Image](graphics/20_figure_14_b.jpg)
    ![Image](graphics/circle-b.jpg)phpMyAdmin 中显示的 MySQL 用户列表。
4.  使用页面下方的“Change Password”（更改密码）表单 ![Image](graphics/circle-c.jpg) 来修改密码。
    ![Image](graphics/20_figure_15_c.jpg)
    ![Image](graphics/circle-c.jpg)phpMyAdmin 中用于更新 MySQL 用户密码的表单。
5.  如有必要，在 phpMyAdmin 的配置文件中更改 root 用户的密码。
    更改 root 用户密码的结果很可能是 phpMyAdmin 被拒绝访问 MySQL 服务器。这是因为 phpMyAdmin 在本地服务器上通常以 root 用户身份连接到 MySQL，且 root 用户的密码被硬编码在配置文件中。完成步骤 1-4 后，在 phpMyAdmin 目录中找到 `config.inc.php` 文件——通常位于 `/Applications/MAMP/bin/phpMyAdmin` (Mac OS X 配合 MAMP) 或 `C:\xampp\phpMyAdmin` (Windows 配合 XAMPP)。用任意文本编辑器或 IDE 打开该文件，并将下面这行代码修改为使用新密码：

```
$cfg['Servers'][$i]['password'] = 'the_new_password';
```

    然后保存文件，并在 Web 浏览器中重新加载 phpMyAdmin。

### 创建用户和权限

在 MySQL 成功启动并运行后，且为 root 用户设置好密码后，你可以添加其他用户。为了提高数据库的安全性，你应该始终创建新用户来访问数据库，而不是一直使用 root 用户。

MySQL 权限系统的设计是为了确保对特定数据库上的特定命令拥有适当的权限。例如，这项技术使得 Web 主机提供商可以让多个用户访问多个数据库而无需担心。MySQL 系统中的每个用户可以在特定主机（计算机）上拥有对特定数据库的特定权限。root 用户——指 MySQL 的 root 用户，而非系统的——拥有最高权限，用于创建子用户，尽管子用户也可以被赋予类似 root 的权限（但这不建议）。

当用户尝试对 MySQL 服务器执行某项操作时，MySQL 首先检查该用户是否有权连接到服务器（基于用户名、用户的主机、用户的密码以及 `mysql` 数据库 `user` 表中的信息）。其次，MySQL 检查该用户是否有权在特定数据库上运行特定的 SQL 语句——例如，选择数据、插入数据或创建新表。**[表 A.1](#app01.html#app01table01)** 列出了大多数可按用户设置的各种权限。

**表 A.1. MySQL 权限**

![Image](graphics/atab01.jpg)

在 MySQL 中设置用户和权限有多种方法，但我将从讨论 `GRANT` 命令开始。语法如下：

```
GRANT privileges ON database.* TO 'username'@'hostname' IDENTIFIED BY 'password';
```

对于该语句的 *privileges*（权限）部分，你可以列出来自[表 A.1](#app01.html#app01table01) 的特定权限，或者使用 `ALL` 来允许所有权限（这不明智）。语句中的 `database.*` 部分指定了用户可以操作的数据库和表。你可以使用 `database.tablename` 语法指定特定表，或使用 `*.*` 允许访问所有数据库（同样不明智）。最后，你可以指定用户名、主机名和密码。

用户名的最大长度为 16 个字符。创建用户名时，请务必避免空格（改用下划线），并注意用户名区分大小写。

主机名是允许用户连接的计算机。这可以是域名，如 `www.example.com`，也可以是 IP 地址。通常指定 `localhost` 作为主机名，意味着 MySQL 用户必须从运行 MySQL 数据库的同一台计算机上连接。要允许任何主机，请使用主机名通配符（`%`）：

```
GRANT privileges ON database.* TO 'username'@'%' IDENTIFIED BY 'password';
```

但这也不推荐。在创建用户时，最好明确且严格地限定范围。

密码没有长度限制，但同样区分大小写。密码在 MySQL 数据库中是加密存储的，这意味着无法以明文格式恢复它们。省略 `IDENTIFIED BY 'password'` 子句将导致该用户无需输入密码即可登录（这同样应避免）。

作为该过程的示例，你将创建两个拥有特定权限的新用户，作用于一个名为 `temp` 的新数据库。请记住，你只能对现有数据库授予用户权限。接下来的步骤也将展示如何创建数据库。

### 创建新用户

1.  以 root 用户身份登录 MySQL 客户端。
    使用[第 4 章](#ch04.html#ch04)中解释的步骤执行此操作（如果你还不知道怎么做）。你必须以具有创建数据库和其他用户权限的用户身份登录。
2.  创建 `temp` 数据库：

```
CREATE DATABASE temp;
```

    使用上述语法创建数据库非常简单。只要你以拥有适当权限的用户身份连接，此命令即可生效。
3.  创建一个在 `temp` 数据库上拥有基本权限的用户 ![Image](graphics/circle-d.jpg)：

```
GRANT SELECT, INSERT, UPDATE, DELETE
ON temp.*
TO
'webuser'@'localhost'
IDENTIFIED BY 'BroWs1ng';
```

    ![Image](graphics/20_figure_16_d.jpg)
    ![Image](graphics/circle-d.jpg)创建一个可在一个数据库上执行基本任务的用户。
    通用的 `webuser` 用户可以浏览记录（从表中 `SELECT`）、添加（`INSERT`）、修改（`UPDATE`）或 `DELETE` 记录。该用户只能从 `localhost`（同一台计算机）连接，且只能访问 `temp` 数据库。
4.  应用更改 ![Image](graphics/circle-e.jpg)：

```
FLUSH PRIVILEGES;
```

    ![Image](graphics/20_figure_17_e.jpg)
    ![Image](graphics/circle-e.jpg)在尝试使用新创建的用户访问 MySQL 之前，别忘了这一步。
    刚才所做的更改不会生效，直到你告诉 MySQL 重置可接受的用户和权限列表，这正是该命令的作用。忘记这一步，然后无法使用新创建的用户访问数据库，是一个常见错误。

***

**提示**

任何名称以 `test_` 开头的数据库，均可被任何有权连接到 MySQL 的用户修改。因此，除非确实只是实验用途，请小心不要创建以此方式命名的数据库。

***

***

**提示**

`REVOKE` 命令用于移除用户和权限。

***

***

### 在 phpMyAdmin 中创建用户

要在 phpMyAdmin 中创建用户，首先单击 phpMyAdmin 主页上的“Privileges”（权限）选项卡。在“Privileges”页面上，单击“Add A New User”（添加新用户）。填写“Add A New User”表单以定义用户的名称、主机、密码和权限。然后单击“Go”（执行）。这将创建一个拥有全局权限但无数据库特定权限的用户。

在生成的页面上，选择要应用用户权限的数据库，然后单击“Go”。在下一页中，选择该用户在该数据库上应拥有的权限，然后再次单击“Go”。这完成了为该用户在该数据库上创建权限的过程。请注意，此过程允许你轻松地为用户在不同数据库上分配不同的权限。

