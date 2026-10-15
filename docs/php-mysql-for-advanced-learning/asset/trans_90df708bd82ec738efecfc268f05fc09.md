
<form name="form1" method="post" action="form-sanitize.php">

    电子邮件地址： <br/>

    <input type="text" name="email" value="<?php echo $_POST['email']; ?>" size="50"/>

    <br/><br/>

    主页： <br/>

    <input type="text" name="homepage" value="<?php echo $_POST['homepage']; ?>" size="50" /> <br/>

    <br/>

    <input type="submit" />

</form>

为了确保数据格式正确，需要对其进行验证

```
<?php

    if (isset($_POST['email'])) {

        $email = filter_var($_POST['email'], FILTER_SANITIZE_EMAIL);

        if (filter_var($email, FILTER_VALIDATE_EMAIL)) {

            echo "$email is a valid email address.<br/><br/>";

        } else {

            echo "$email is <strong>NOT</strong> a valid email address.<br/><br/>";
```

Hirdesh Bhardwaj

```
}
}

if (isset($_POST['homepage'])) {

    $homepage = filter_var($_POST['homepage'],
    FILTER_SANITIZE_URL);

    if (filter_var($homepage, FILTER_VALIDATE_URL)) {

        echo "$homepage is a valid URL.<br/><br/>";

    } else {

        echo "$homepage is <strong>NOT</strong> a valid URL.<br/><br/>";

    }

}

?>
```

<form name="form1" method="post" action="form-validate.php">

电子邮件地址： <br/>

<input type="text" name="email" value="<?php echo $_POST['email']; ?>" size="50"/> <br/><br/>

<input type="text" name="homepage" value="<?php echo $_POST['homepage']; ?>" size="50" /> <br/>

<input type="submit" />

</form>

## Notes :

## MySQL / MariaDB 简介

PHP MariaDB 正式名称为 PHP MYSQL，于 2009 年开发，与 MySQL API 和命令高度兼容且完全匹配。MySQL 的原始开发者在 Oracle 收购 MySQL 引发担忧后创建了 MariaDB。MariaDB（及其前身 MySQL）在全球已使用超过 20 年

## 关系数据库简介：

数据库是一组相关文件的集合。数据库及其控制数据库的工具称为数据库管理系统（DBMS）。大多数数据库今天都是关系数据库，因为它们处理包含相关字段的表。

那么让我们了解一些与数据库相关的术语：

- 数据库 – 数据库是包含相关数据表的 数据源。
- 表 – 表，如电子表格或 Excel 表格，以表格方式包含数据。
- 列 – 列是一种结构，用于保存一种类型的数据。
- 行 – 行，有时也称为元组或记录，是对相关数据进行分组的结构。
- 主键 – 这指的是唯一、标识的值。该值在表中不能重复，且表中只能有一个主键。

**外键** – 外键充当两个表之间的链接或接口。

**复合键** – 复合键是指引用多个列的键。

## MySQL / MariaDB 中的数据类型：

### 数值数据类型：

**INT（整数）：** Int 数据类型表示正常大小的整数。因此它可以简单地用于存储数值。还有 BIGINT、MEDIUMINT、SMALLINT 和 TINYINT，它们表示不同范围的整数值。

**DECIMAL：** Decimal 数据类型表示具有特定浮点值的数字。最大允许值为 65，最大小数位数为 30。还有 FLOAT 和 DOUBLE 用于存储带浮点数的数值。

**BOOLEAN：** 该数据类型将值 0 与“false”关联，将值 1 与 true 关联。

### 日期和时间数据类型：

**DATE：** DATE 数据类型以“YYYY-MM-DD”格式表示日期。

**TIME：** TIME 数据类型以 "hh:mm:ss" 格式表示时间。

**DATETIME：** DATETIME 数据类型以“YYYY-MM-DD HH:MM:SS”格式表示日期和时间。

**TIMESTAMP：** 该数据类型表示“YYYY-MM-DD HH:MM:SS”格式的时间戳。它主要用于插入记录插入/更新和删除过程中的当前日期和时间。

### 字符串数据类型

**CHAR：** 该数据类型表示定长字符串。默认值是 1。

**VARCHAR：** 该数据类型表示长度为 0 到 65535 的变长字符串。

**TEXT：** 该数据类型表示最大长度为 65,535 个字符的文本列。还有一些文本数据类型是 MEDIUMTEXT、LONGTEXT 和 TINYTEXT。

**ENUM：** ENUM 数据类型表示字符串对象，仅允许从给定列表中选择一个值。

**SET：** SET 数据类型表示字符串对象，具有来自给定列表的零个或多个值。

## MySQL / MariaDB 表的类型

现在你了解了一些表的一般特性，你应该知道有不同类型的表。

当前版本的 Mysql 中有一些主要类型的表：

MyISAM- 默认表，通常足以满足用户的需求。它支持所有字段类型和参数。

ISAM- 它与 MyISAM 表相同，只是它无法处理大于 4GB 的数据，这意味着它在操作系统之间不可移植。此表类型在 PHP5 中不再可用。

HEAP - 这些主要用于临时表，它们不支持 MyISAM 表的常见功能，例如 auto_increment 和 blob/text 列等。

当你处理日志数据并且不想长期存储时，可以使用它。

InnoDB- 被认为是“事务安全”的，这意味着你可以从崩溃中恢复数据。

## 一些流行的 MySQL 命令

- CREATE：创建新的数据库和表
- ALTER：修改现有表
- SELECT：显示你想要的数据
- DELETE：从表中擦除或删除数据
- INSERT INTO...：将值放入表中
- UPDATE：让你修改已存在表中的数据

Hirdesh Bhardwaj

DROP：删除整个表或数据库

## 使用 MySQL / MariaDB 数据库

在使用 PHP 实现 Mysql 之前，让我们通过 MYSQL 控制台探索数据库和表的基本概念。

- 打开 XAMPP 控制面板并启动 Apache 和 MYSQL\Mariadb 服务
- 打开命令提示符（在运行选项中输入 cmd）并使用 cd 命令复制粘贴你的 MYSQL/Mariadb 路径，如 cd C:\xampp\mysql\bin
- 要打开 MYSQL 环境，输入 mysql.exe –u root
  （这里 root 是你的 Mysql 数据库的用户名。如果你的 Mysql 有密码，则输入 mysql.exe –u root –p mypassword）
- 一旦你的 MYSQL 欢迎屏幕打开，你就可以开始使用 Mysql / MariaDB 环境工作了。

## MySQL 常用命令

### 打开 MySQL 或 MariaDB 中存在的数据库列表

```
show databases;
```

### 创建名为 "Chanchal" 的新数据库

```
create database Chanchal;
```

### 使用或进入新创建的名为 "Chanchal" 的数据库

```sql
use Chanchal;
```

### 检查当前数据库中有多少个表？

```sql
show tables;
```

### 向表中插入记录，如列中所示，即 name、email 和 phone

```sql
insert into users(name,email,phone) values ('chanchal', 'chanchal@gmail.com', '878787');
```

![](img/9ab4a56a650535285811bb802190e58f_72_0.png)

### 显示名为 Users 的表中的所有记录

```sql
SELECT * FROM users order by name DESC;
```

### 从表中仅显示选择的列 Name 和 Phone

```sql
SELECT name,phone FROM users;
```

Hirdesh Bhardwaj

![](img/9ab4a56a650535285811bb802190e58f_73_0.png)

### 按 ID 列以升序显示所有记录

```sql
SELECT * FROM users order by id ASC;
```

### 使用 where 子句过滤记录

```sql
SELECT * FROM users WHERE name='chanchal' ;  ( Exact Match)
```

OR

```sql
SELECT * FROM users WHERE id >3;  (Using comparison operator)
```

## MySQL 中的聚合函数

聚合函数对多行执行计算，使我们能够轻松地从数据库或表中生成汇总数据。

Mysql 中的一些聚合函数，如 SUM、COUNT、MAX、MIN 和 AVG

**SUM 函数：** SUM 函数返回数值列的总和。让我们计算表中工资的总金额。

### 示例：

```sql
SELECT SUM(salary) as 'Total Salary' from mytable;
```

**COUNT 函数：** COUNT 函数返回列中行或记录的计数。让我们统计在 IT 部门工作的员工总数。

### 示例：

```sql
SELECT COUNT(name) from mytable where dept='IT';
```

**DISTINCT 关键字：** DISTINCT 关键字允许我们省略重复项并从列中返回唯一记录。同样也可以通过分组（Group By 子句）将相似值组合在一起实现。

### 示例：

```sql
SELECT DISTINCT (city) FROM mytable;
```
