
如下所示：

| 字段 | 类型 |
|---|---|
| Id | Integer |
| customers_Id | Integer |
| Day | Integer |
| Month | Integer |
| Year | Integer |

customers_Id 字段与 Customers 表中的 id 字段相同，它让我们能够在 Customers 表与 Purchases 表之间建立关系，因为读取 Purchases 表时，我们需要知道是哪位客户进行了购买。现在我们的数据库设计如图 14.34 所示。

现在，Purchases 表既包含自身唯一的 Id，也包含进行购买的客户的 Id。它还有三个字段用于存储购买日期。我们本可以使用一个日期字段，但如果将这些日期拆分为三个独立的整数字段，以后操作会更方便。然而，目前的设计还不能让我们存储当时购买了哪些产品。为此，我们需要创建一个名为 purchaseProducts 的新表。purchaseProducts 表将包含以下数据字段和类型：

| 字段 | 类型 |
|---|---|
| products_Id | Integer |
| purchases_Id | Integer |
| Quantity | Integer |
| Cost | Float |

products_Id 字段来自 Products 表的 Id 字段；它让我们能够确定购买了哪种产品。purchase_Id 是 Purchases 表的 Id 字段。

## 图 14.34 修订后的数据库设计

![](img/b2471264f405d17994ef173e4b9cec92_448_0.png)

Quantity 字段存储购买了多少件产品，Cost 字段存储价格。我们将 cost 字段同时放在这个表和 Products 表中，因为产品的价格可能会随时间变化，但我们希望记录实际购买时的价格，因此 purchaseProducts 表中包含了这个字段。现在我们的数据库设计如图 14.35 所示。

现在该使用 phpMyAdmin 在我们的 MySQL 数据库中创建这些新表了。点击屏幕左侧的数据库名称，如图 14.7 所示，输入第一个新表的名称。这个表就是 purchaseProducts，包含上述四个字段。该表没有自己的主索引，但它有来自其他表的两个索引，即 products_Id 和 purchases_Id 字段。为了指明这些字段，我们需要确保选中“Index”单选按钮。这是屏幕最右侧一排中的第二个单选按钮。如图 14.36 所示，这两个字段都应选中该单选按钮。按图中所示输入数据后，单击 Save 按钮即可创建表。

接下来，我们创建 Purchases 表：点击屏幕左侧的数据库名称，输入名称“Purchases”，并将字段数量设为 5。

点击 Go 按钮将显示 Purchases 的建表界面。按图 14.37 所示填写完成。

> 注意
> 请注意，id 字段是 auto_increment（自动递增）并且是主键。此外，customer_Id 是索引。

## 图 14.35 已添加到设计中的 purchaseProducts 表

![](img/b2471264f405d17994ef173e4b9cec92_449_0.png)

## 图 14.36 添加 purchaseProducts 表

![](img/b2471264f405d17994ef173e4b9cec92_450_0.png)

## 图 14.37 添加 Purchases 表

![](img/b2471264f405d17994ef173e4b9cec92_450_1.png)

至此，我们已经完成了数据库结构的创建，可以向这些新字段添加一些数据了。

## 我们的数据

创建数据库的下一步是为刚刚创建的表添加一些新记录。需要输入到 Purchases 表中的数据如图 14.38 所示，需要输入到 purchaseProducts 表中的数据如图 14.39 所示。请将所有数据输入到正确的数据库表中。

就是这样，我们现在已经完成了数据库结构和数据内容。在下一课中，我们将学习如何使用 PHP 脚本与 MySQL 数据库交互，提取并操作这些数据。

## 图 14.38 Purchases 表数据

| Id | customers_id | Day | Month | Year |
|---|---|---|---|---|
| 1 | 2 | 3 | 9 | 2006 |
| 2 | 4 | 6 | 9 | 2006 |
| 3 | 6 | 13 | 9 | 2006 |
| 4 | 2 | 22 | 9 | 2006 |
| 5 | 1 | 28 | 9 | 2006 |
| 6 | 9 | 1 | 10 | 2006 |
| 7 | 7 | 1 | 10 | 2006 |

## 图 14.39 purchaseProducts 表数据

| products_id | purchase_ID | Quantity | Cost |
|---|---|---|---|
| 2 | 1 | 20 | 2.99 |
| 3 | 2 | 10 | 3.50 |
| 8 | 2 | 30 | 4.50 |
| 6 | 3 | 25 | 2.50 |
| 3 | 4 | 10 | 3.50 |
| 4 | 4 | 100 | 1.50 |
| 5 | 4 | 40 | 3.00 |
| 1 | 5 | 22 | 3.99 |
| 1 | 6 | 6 | 3.99 |
| 3 | 7 | 15 | 3.50 |
| 4 | 7 | 25 | 2.00 |
| 5 | 7 | 10 | 2.50 |
| 7 | 7 | 55 | 2.50 |
| 8 | 7 | 1 | 3.99 |

## 练习

14.1 将你完成的数据库备份为 .sql 文件，并妥善保管。

## 小结

在本章中，我们首先介绍了数据库的概念。我们描述了数据库表及其字段的概念。我们考察了 MySQL 等数据库支持的不同字段类型。接着，我们介绍了 phpMyAdmin 工具，并演示了如何使用它操作 MySQL 数据库。我们通过创建“glassesrus”数据库演示了数据库的创建过程。我们探讨了如何添加、修改和删除记录，以及如何将数据库备份到转储文件。最后，我们演示了 MySQL Workbench 工具，并扩展了我们的数据库。

## 参考资料与延伸阅读

- MySQL 主页。 http://www.mysql.com/
- MySQL 文档。 http://dev.mysql.com/doc/
- PHP editors.com。使用 phpMyAdmin 学习 SQL。 http://www.php-editors.com/articles/sql_phpmyadmin.php
- phpMyAdmin 主页。 http://www.phpmyadmin.net/home_page/index.php
- 维基百科。数据库。 http://en.wikipedia.org/wiki/Database

## 将 PHP 连接到数据库

## 学习目标

- 理解如何使用 PHP 连接到 MySQL 数据库
- 理解如何从数据库读取单条记录
- 理解如何从数据库读取多条记录
- 理解如何读取符合特定要求的记录
- 理解如何对返回的记录进行排序
- 理解如何删除、插入和修改记录
- 理解如何统计符合搜索条件的记录出现次数

## 引言

在第 14 章中，我们介绍了 MySQL 关系数据库管理系统。我们展示了如何使用 MySQL 的 phpMyAdmin 界面创建新的数据库。在这些数据库中，我们创建了表，并指定了用于保存表内数据的字段名称和类型。我们需要完成这些任务，因为这是为本章即将学习的内容做的准备。

现在，我们将了解 PHP 如何与我们创建的数据库交互，从数据库中提取信息并更新数据库。我们将展示这有多么简单，以及数据库如何帮助我们构建真正动态且实用的 Web 应用程序。

## 15.1 连接到 MySQL DBMS

为了使 PHP 脚本能够访问数据库，我们需要在脚本与数据库管理系统（DBMS）之间建立连接。将 PHP 脚本连接到 DBMS 是一项

mysql_error() 函数不需要参数，并返回一个错误消息字符串。将 die() 函数与 mysql_error() 函数结合使用，形式如下：

```
die("Could not connect: " . mysql_error() )
```

将 die() 函数与 mysql_connect() 函数结合使用时，我们需要使用“or”结构，如下所示：

```
$dbLocalhost = mysql_connect("localhost", "root", "")
    or die("Could not connect: " . mysql_error() );
```

上面的代码片段现在应这样理解：“与 localhost 建立 MySQL 连接，如果连接失败，就停止脚本”。

现在，我们可以将这些函数组合成第一个 PHP 脚本，如下所示：

```
<?php
// File: example15-1.php

$dbLocalhost = mysql_connect("localhost", "root", "")
    or die("Could not connect: " . mysql_error() );

mysql_select_db("glassesrus", $dbLocalhost)
    or die("Could not find database: " . mysql_error() );
echo "<h1>Connected To Database</h1>";
?>
```

上述脚本会打开到 DBMS 服务器的连接，然后尝试选择“glassesrus”数据库，即我们在第 14 章中创建的数据库。如果任一操作出错，都会生成错误消息并终止脚本。如果一切顺利，运行上述脚本的输出将看起来似乎没有任何输出。

## 15.2 从数据库读取数据

将 PHP 连接到数据库的下一步是让 PHP 向数据库发送一条结构化查询语言（SQL）语句，以开始检索数据记录。为此，我们需要引入一个新函数 mysql_query()：

```
resourceRecords = mysql_query (query, resourceId);
```

mysql_query() 函数需要两个参数；第一个是 SQL 查询字符串（稍后会详细介绍），第二个是 mysql_connect() 函数返回的数据库资源标识符。该函数会为返回的数据返回一个资源标识符。

| 注意 | 如果查询引用的表不存在，mysql_query() 函数将会失败并返回“false”。 |

以下是该函数的一个有效用法示例：

```
$dbRecords = mysql_query("SELECT * FROM customers", $dbLocalhost)
```
