

## 第 I.3 章：文件操作

- 4 ASP.NET 编程
- 5 Java 编程
- 6 Perl 编程
- 7 C++ 编程
- 8 Pascal 编程
- 9 Fortran 编程
- 10 汇编编程

编写一个脚本从该文件中输出随机一行。

### I.3.16. 编辑文件

编写一个脚本，将 `text.txt` 文件（见列表 I.3.2）中索引为 7 的行替换为 C/C++ 编程。

### I.3.17. 打乱文本文件行

编写一个脚本，随机更改 `text.txt` 文件（见列表 I.3.2）中行的顺序。此外，创建一个脚本按索引值对文件内容进行排序，另一个脚本按字母顺序对记录进行排序。

### I.3.18. 向文件中添加记录

编写一个脚本计算 `text.txt` 文件（见列表 I.3.2）中的最大索引值，并向其添加新行（例如 Visual Basic 编程），为其分配一个等于当前索引加一的索引值。

### I.3.19. 输出页面

编写一个脚本，每页三行输出 `text.txt` 文件（见列表 I.3.2）中的行，并提供页面导航功能（图 I.3.7）。

![](img/a893312ec68b8170fe567f785e95c06e_39_0.png)

图 I.3.7. 页面导航

### I.3.20. 基于文件的注册系统

开发一个在文件中存储注册用户信息的系统。该数据文件的每行都必须对应一个单独的用户，并采用以下格式：

用户名::密码::邮箱::网址

用户名、密码、邮箱地址和主页必须用两个冒号（::）分隔。系统不允许注册已存在相同用户名的用户。此外，开发一个用于查看注册用户信息的脚本。

### I.3.21. 输出随机文件

假设你有一个包含图像文件的目录。编写一个脚本，在加载页面时显示随机的图像。

### I.3.22. 确定图像创建日期

无论 JPEG 图像是如何创建的，它必须包含图像创建日期。编写一个脚本从 JPEG 文件中自动提取此日期。

### I.3.23. 将内容从一个目录复制到另一个目录

编写一个脚本，将目录及其所有嵌套目录的内容复制到另一个目录。

### I.3.24. 破解留言板

列表 I.3.3 包含了向留言板添加新消息的脚本。利用此代码包含的漏洞删除该脚本所在目录中的所有文件。然后修正代码以消除允许入侵者在服务器上执行第三方代码的漏洞。

> 列表 I.3.3 显示的脚本可以在附带光盘的 `/scripts/3/3.24/1.php` 文件中找到。

#### 列表 I.3.3. 可破解留言板的漏洞代码

```php
<?php
// 表单处理器
if(!empty($_POST['name']) && !empty($_POST['msg'])) {
    $msg = "<tr><td>".\$_POST['name']."</td></tr>";
    $msg = "<tr><td>".\$_POST['msg']."</td></tr>";
    // 打开文件并向其添加新记录。
    $fd = fopen("msg.txt", "a");
    if($fd) {
        fwrite($fd, $msg);
        fclose($fd);
    }
    // 输出已添加到文本文件的消息
    echo "<table>";
if(file_exists("msg.txt")) include "msg.txt";
```

```php
echo "</table>";
?>
<form method="post">
<table align="center">
<tr>
<td>Name</td>
<td><input type="text" name="name"></td>
</tr>
<tr>
<td colspan="2">Message<br>
<textarea cols="42" rows="5" name="msq"></textarea></td>
</tr>
<tr>
<td><input type="submit" value="Add"></td>
</tr>
</table>
</form>
```

## 第 I.4 章：MySQL 与 SQL 注入

![](img/a893312ec68b8170fe567f785e95c06e_42_0.png)

MySQL 数据库管理系统因其高性能、通过开源许可分发以及在主机提供商中的普及而成为事实上的标准。在开发 Web 应用时使用数据库可以显著提高性能。然而，粗率使用 MySQL 会引入严重的漏洞。这些漏洞被称为 SQL 注入。

### I.4.1. 用户注册系统

创建一个存储注册用户信息的系统（图 I.4.1）。用户列表表可以在 `/scripts/4` 目录下找到。

![](img/a893312ec68b8170fe567f785e95c06e_43_0.png)

图 I.4.1. 用户注册

#### 列表 I.4.1. 用户列表表

```sql
CREATE TABLE userslist (
id int(11) NOT NULL AUTO_INCREMENT,
name varchar(255) NOT NULL,
pass varchar(255) NOT NULL,
email varchar(255) NOT NULL,
url varchar(255) NOT NULL,
    PRIMARY KEY (id)
) ENGINE=MyISAM;
```

- id
- name
- pass
- email
- url

### I.4.2. 输出随机文件

列表 I.4.2 显示的脚本提供了用户信息。代码可以在 `/scripts/4` 目录下找到。

#### 列表 I.4.2. 用户列表表

```php
<?php
// 建立数据库连接
require_once("config.php");
// 请求用户列表
```

