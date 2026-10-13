
# 使用函数

# 复习与深入

前一章快速介绍了 MySQL。其重点在于两个主题：使用 MySQL 的规则和数据类型来定义数据库，以及如何与 MySQL 服务器交互。本章将转向数据库的*通用语言*：SQL。

SQL 是 Structured Query Language（结构化查询语言）的缩写，是一组专门用于与数据库交互的特殊词汇。SQL 学习和使用起来出奇地简单，却又惊人地强大。事实上，SQL 最难的地方在于如何将其潜力发挥到极致！

在本章中，你将学习创建表、填充数据以及运行其他基本查询所需的所有 SQL 知识。示例将全部使用上一章讨论的 *users* 表。此外，与上一章一样，本章假设你有权访问正在运行的 MySQL 服务器，并知道如何使用客户端应用程序与其交互。

## 创建数据库和表

SQL 的第一个合乎逻辑的用途是创建数据库。创建新数据库的语法非常简单：

```
CREATE DATABASE databasename
```

就这么简单（正如我所说，SQL 很容易学）！

`CREATE` 关键字也用于创建表：

```
CREATE TABLE tablename (  
column1name description,  
column2name description  
...)
```

正如你从该语法中所见，在命名表之后，你需要在括号内定义每一列。每一对列名和描述应由逗号与下一对分隔。如果你选择此时创建索引，可以在创建语句的末尾添加它们，但也可以稍后再添加索引。（索引将在第 6 章“数据库设计”中正式讨论，但第 4 章“MySQL 简介”已对该主题进行了介绍。）

以防你疑惑，SQL *不区分大小写*。然而，我习惯将 SQL 关键字大写，如前面的示例语法和以下步骤所示。这样做有助于将 SQL 术语与数据库、表和列名区分开来。

### 创建数据库和表

**1.** 使用你喜欢的客户端访问 MySQL。

第 4 章展示了如何使用两种最常见的界面——*mysql* 命令行客户端和 *phpMyAdmin*——与 MySQL 服务器通信。使用上一章的步骤，你现在应该已连接到 MySQL。

在本章其余部分中，大多数 SQL 示例将使用 mysql 客户端输入，但它们在 phpMyAdmin 或大多数其他客户端工具中的工作方式完全相同。

**2.** 创建并选择新数据库：

```
CREATE DATABASE sitename;  
USE sitename;
```

一个名为 *sitename* 的新数据库在 MySQL 中被创建。随后它被选中用于后续的查询。

第一行创建数据库（假设你以有权创建新数据库的用户身份连接到 MySQL）。第二行告诉 MySQL 你想从现在开始在此数据库中工作。请记住，在 mysql 客户端中，你必须用分号终止每条 SQL 命令，尽管这些分号技术上并不属于 SQL 本身的一部分。如果在 phpMyAdmin 中一次执行多个查询，它们也应用分号分隔。如果在 phpMyAdmin 中仅运行单个查询，则不需要分号。

创建和选择数据库的相同命令可以在 phpMyAdmin 的 SQL 窗口中运行。

如果你使用的是托管公司的 MySQL，他们可能会为你创建数据库。在这种情况下，只需连接到 MySQL 并选择该数据库即可。

**3.** 创建 *users* 表：

```
CREATE TABLE users (  
user_id MEDIUMINT UNSIGNED NOT NULL  
AUTO_INCREMENT,  
first_name VARCHAR(20) NOT NULL,  
last_name VARCHAR(40) NOT NULL,  
email VARCHAR(60) NOT NULL,  
pass CHAR(40) NOT NULL,  
registration_date DATETIME NOT NULL,  
PRIMARY KEY (user_id)  
);
```

此 `CREATE` SQL 命令将创建 *users* 表。

*users* 表的设计是在[第 4 章](#ch04.html#ch04)中开发的。在那里，根据许多标准确定了表中每一列的名称、类型和属性（详见该章）。在这里，这些信息被放入 `CREATE` 表语法中，以便在数据库中实际创建该表。

因为 mysql 客户端直到遇到分号（或 `\G` 或 `\g`）才会运行查询，所以你可以跨多行输入语句（在每行末尾按回车键）。这通常使查询更易于阅读和调试。在 phpMyAdmin 中，你也可以跨多行运行查询，尽管它们直到你点击“执行”才会被执行。

**4.** 确认表的存在：

```
SHOW TABLES;  
SHOW COLUMNS FROM users;
```

使用 `SHOW` 命令确认表的存在及其列。

`SHOW` 命令显示数据库中的表或表中的列名和类型。

此外，你可能会注意到 `user_id` 的默认值为 `NULL`，即使该列被定义为 `NOT NULL`。这实际上是正确的，这与 `user_id` 是自动递增的主键有关。MySQL 经常会出于更好的性能或其他原因，对列的定义进行微小更改。

在 phpMyAdmin 中，数据库的表列在浏览器窗口的左侧，数据库名称下方。点击表名可查看其列。

phpMyAdmin 显示 *sitename* 数据库包含一张名为 *users* 的表。

phpMyAdmin 在此屏幕上显示表的定义（通过点击左侧列中的表名访问）。

***

> **提示**
>
> 本章其余部分假设你正在使用 mysql 客户端或类似工具，并已使用 `USE` 选择了 *sitename* 数据库。

***

> **提示**
>
> 创建表时列出列的顺序没有功能性影响，但有关于如何排序的风格建议。我通常将主键列放在第一位，其次是任何外键列（更多相关内容见下一章），然后是其余列，最后是日期列。

***

> **提示**
>
> 创建表时，你可以选择指定其*类型*。MySQL 支持多种表类型，各有优劣。如果你不指定表类型，MySQL 将自动使用该 MySQL 安装的默认类型创建表。[第 6 章](#ch06.html#ch06)将更详细地讨论这一点。

***

> **提示**
>
> 创建表和文本列时，你可以选择指定其*排序规则*和*字符集*。当使用多种语言或非 MySQL 服务器默认语言时，两者都会发挥作用。[第 6 章](#ch06.html#ch06)也涵盖了这些主题。

***

> **提示**
>
> `DESCRIBE tablename` 与 `SHOW COLUMNS FROM tablename` 是同一条语句。

***

## 插入记录
