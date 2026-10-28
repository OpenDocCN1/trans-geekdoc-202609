
在审阅此脚本时，请注意数据库的大部分索引都基于每个表的外键。例如，由于 products 表中的 categoryID 列引用了 categories 表中的 categoryID 列，因此此脚本在 products 表的 categoryID 上创建了索引。

脚本末尾的 GRANT 语句创建了一个名为 mgs_user 的用户，密码为 pa55word。此外，它授予该用户对当前数据库中所有表的 SELECT、INSERT、UPDATE 和 DELETE 权限。因此，如果你以 mgs_user 身份连接到 MySQL，你可以操作存储在名为 my_guitar_shop2 的数据库中的任何数据。但是，你不能更改此数据库的结构。

像这样的脚本通常包含多个 INSERT 语句，用于向数据库插入初始数据。例如，即使是新数据库也应包含一些产品和类别。此外，为测试目的添加一些客户和订单通常是有意义的。在下一章中，你将学习如何编写这些 INSERT 语句。然后，如果你愿意，可以将这些 INSERT 语句添加到像这样的脚本末尾。

为了便于阅读，此脚本对所有 SQL 关键字、数据类型和列属性均使用大写。此外，它使用空格对齐数据类型和列属性。这样，你可以轻松识别列的数据类型和属性。然而，SQL 不是区分大小写的语言。因此，你可以使用任何你想要的大写约定来表示 SQL 关键字、数据类型和属性。

## 创建 my_guitar_shop2 数据库的 SQL 脚本

```
CREATE TABLE orderItems (
    itemID          INT             NOT NULL        AUTO_INCREMENT,
    orderID         INT             NOT NULL,
    productID       INT             NOT NULL,
    itemPrice       DECIMAL(10,2)   NOT NULL,
    discountAmount  DECIMAL(10,2)   NOT NULL,
    quantity        INT NOT NULL,
    PRIMARY KEY (itemID),
    INDEX orderID (orderID),
    INDEX productID (productID)
);

CREATE TABLE products (
    productID       INT             NOT NULL        AUTO_INCREMENT,
    categoryID      INT             NOT NULL,
    productCode     VARCHAR(10)     NOT NULL,
    productName     VARCHAR(255)    NOT NULL,
    description     TEXT            NOT NULL,
    listPrice       DECIMAL(10,2)   NOT NULL,
    discountPercent DECIMAL(10,2)   NOT NULL        DEFAULT 0.00,
    dateAdded       DATETIME        NOT NULL,
    PRIMARY KEY (productID),
    INDEX categoryID (categoryID),
    UNIQUE INDEX productCode (productCode)
);

CREATE TABLE categories (
    categoryID      INT             NOT NULL        AUTO_INCREMENT,
    categoryName    VARCHAR(255)    NOT NULL,
    PRIMARY KEY (categoryID)
);

CREATE TABLE administrators (
    adminID         INT             NOT NULL        AUTO_INCREMENT,
    emailAddress    VARCHAR(255)    NOT NULL,
    password        VARCHAR(255)    NOT NULL,
    firstName       VARCHAR(255)    NOT NULL,
    lastName        VARCHAR(255)    NOT NULL,
    PRIMARY KEY (adminID)
);

-- Create a user and grant privileges to that user
GRANT SELECT, INSERT, UPDATE, DELETE
ON *
TO mgs_user@localhost
IDENTIFIED BY 'pa55word';
```

- 3. 使用 phpMyAdmin 通过剪切和粘贴这些语句到 phpMyAdmin 中来测试它们。
- 4. 编写选择数据库的 USE 语句。
- 5. 编写 CREATE TABLE 语句以在 ap 数据库中创建以下表：

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_597_0.png)

创建这些表时，请确保使用正确的数据类型并为每个表标识主键。此外，请确保为每个主键自动生成值。对于每个列，请包含你认为必要的任何 UNIQUE、NOT NULL 或 DEFAULT 属性。
- 6. 使用 phpMyAdmin 运行脚本。然后，查看数据库的结构。

## 向脚本添加语句以创建一些索引和用户

- 7. 在脚本末尾添加 CREATE INDEX 语句，为 invoices 和 lineItems 表的外键创建索引。此外，编写一个 CREATE INDEX 语句为 invoiceNumber 列创建索引。
- 8. 在脚本末尾添加一个 GRANT 语句，创建一个名为 ap_user 且密码为“sesame”的用户，并授予该用户从数据库中任何表中选择、插入或更新数据的权限。但是，不要允许该用户删除数据库中的任何数据。
- 9. 测试整个 ap.sql 脚本以确保其正确运行。

## 如何从单个表中选择数据

首先，你需要学习如何编写从单个表中检索数据的 SELECT 语句。一旦掌握这些技能，你就可以将其应用于多个表和更复杂的查询。

## 如何从表中选择列

图 18-1 展示了 SELECT 语句的基本语法。这里，大写字母的单词是关键字，你必须完全按所示拼写，尽管你可以使用任何你喜欢的大写形式。

此语法摘要已简化，以便你能专注于 SELECT 语句的四个主要子句：SELECT 子句、FROM 子句、WHERE 子句和 ORDER BY 子句。这里，SELECT 子句指定要检索的列。FROM 子句指定要从中检索数据的基表或表。WHERE 子句指定要检索的行。而 ORDER BY 子句指定如何排序行。

图中第一个 SELECT 语句从 products 表中检索所有行和列。此语句使用星号 (*) 通配符表示应检索所有列，并且省略了 WHERE 子句，因此检索的行没有任何条件。该图以 phpMyAdmin 显示的方式展示了此语句的结果集。然而，为了节省空间，该图仅显示了该语句检索到的十行中的前三行。

请注意，此语句不包含 ORDER BY 子句。如果没有 ORDER BY 子句，你无法确定行呈现的顺序。它们可能按你期望的顺序出现，也可能不按。结果，如果顺序对你很重要，你应包含 ORDER BY 子句。

第二个语句从 products 表中检索选定的列。为此，该语句使用 SELECT 子句指定列。与第一个语句一样，此语句不包含 WHERE 子句，因此检索所有行。然而，此语句确实包含 ORDER BY 子句。该子句按 listPrice 列以升序对行进行排序。

第三个语句的工作方式与第二个语句类似。然而，第三个语句使用 WHERE 子句仅检索标价小于 450 的产品。

第四个语句展示了 WHERE 子句的另一种变体。在这种情况下，此语句仅检索标价小于 10 的产品。由于 products 表中没有任何行的价格如此之低，因此结果集为空。

## SELECT 语句的简化语法

```sql
SELECT select_list
FROM table_source
[WHERE search_condition]
[ORDER BY order_by_list]
```

## 从表中检索所有行和列

```sql
SELECT * FROM products
```

| productID | categoryID | productCode | productName | description | listPrice | discountPercent | dateAdded |
|---:|---:|---|---|---|---:|---:|---|
| 1 | 1 | strat | Fender Stratocaster | The Fender Stratocaster is the electric guitar design... | 699.00 | 30.00 | 2013-10-30 09:32:40.0000000 |
| 2 | 1 | les_paul | Gibson Les Paul | This Les Paul guitar offers a carved top and... | 1199.00 | 20.00 | 2013-12-05 18:33:13.0000000 |
| 3 | 1 | sg | Gibson SG | This Gibson SG electric guitar takes the... | 2517.00 | 2.00 | 2014-02-04 11:04:31.0000000 |

(10 行中的 3 行)

## 检索三列并按价格排序

```sql
SELECT productID, productName, listPrice
FROM products
ORDER BY listPrice
```

| productID | productName | listPrice |
|---:|---|---:|
| 5 | Washburn D10S | 299.00 |
| 6 | Rodriguez Caballero 11 | 415.00 |
| 4 | Yamaha FG700S | 485.99 |
| 8 | Hohner HC? | 499.00 |
| 1 | Fender Stratocaster | 699.00 |
| 9 | Ludwig 5-piece Drum Set with Cymbals | 699.99 |

(10 行中的 6 行)

## 检索指定价格范围内的行

```sql
SELECT productID, productName, listPrice
FROM products
WHERE listPrice < 450
ORDER BY listPrice
```

| productID | productName | listPrice |
|---:|---|---:|
| 5 | Washburn D10S | 299.00 |
| 6 | Rodriguez Caballero 11 | 415.00 |

## 检索空结果集

```sql
SELECT productID, productName, listPrice
FROM products
WHERE listPrice < 10
```

图 18-1 如何从表中选择列
