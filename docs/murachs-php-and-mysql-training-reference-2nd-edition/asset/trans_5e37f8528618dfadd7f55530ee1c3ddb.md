

## products 表的列

| 名称 | 类型 | 排序规则 | 属性 | 可空 | 默认值 | 额外 |
|---|---|---|---|---|---|---|
| productID | int(11) |  |  | 否 | 无 | AUTO_INCREMENT |
| categoryID | int(11) |  |  | 否 | 无 |  |
| productCode | varchar(10) | latin1_swedish_ci |  | 否 | 无 |  |
| productName | varchar(255) | latin1_swedish_ci |  | 否 | 无 |  |
| listPrice | decimal(10,2) |  |  | 否 | 无 |  |

## 常见的 MySQL 数据类型

| 类型 | 描述 |
|---|---|
| CHAR | ASCII 字符集中的定长字符串。 |
| VARCHAR | ASCII 字符集中的可变长字符串。 |
| INT | 各种大小的整数值。 |
| DECIMAL | 可包含整数部分和小数部分的十进制数值。 |
| DATE、TIME、DATETIME | 日期、时间或日期和时间。 |

## 说明

-   分配给列的数据类型决定了可以存储在该列中的信息的类型和大小。
-   每个列定义还指明它是否可以包含*空值*。空值表示该列的值未知。
-   列也可以定义为具有*默认值*。这样，当向表中添加一行时，如果没有提供其他值，就会使用该默认值。
-   列也可以定义为*自增列*。自增列是一个数值列，当向表中添加一行时，其值会自动生成。
-   有关 MySQL 数据类型的更多信息，请参见第 17 章。

图 3-3 表中列的定义方式

## 获取所有列的 SELECT 语句语法

```
SELECT *
FROM table-1
[WHERE selection-criteria]
[ORDER BY column-1 [ASC|DESC] [, column-2 [ASC|DESC] ...]]
```

## 一个获取所有列的 SELECT 语句

```
SELECT * FROM products
WHERE categoryID = 2
```

| productID | categoryID | productCode | productName | listPrice |
|---:|---:|---:|---|---:|
| 7 | 2 | precision | Fender Precision | 799.99 |
| 8 | 2 | hofner | Hofner Icon | 499.99 |

## 获取选定列的 SELECT 语句语法

```
SELECT column-1 [, column-2] ...
FROM table-1
[WHERE selection-criteria]
[ORDER BY column-1 [ASC|DESC] [, column-2 [ASC|DESC] ...]]
```

## 一个获取选定列和行的 SELECT 语句

```
SELECT productName, listPrice
FROM products
WHERE listPrice < 500
ORDER BY listPrice ASC
```

| productName | listPrice |
|---|---:|
| Washburn D10S | 299.00 |
| Rodriguez Caballero 11 | 415.00 |
| Yamaha FG700S | 489.99 |
| Hofner Icon | 499.99 |

## 说明

-   SELECT 语句是一种 SQL 语句，它返回一个*结果集*（或*结果表*），其中包含指定的行和列。
-   要指定列，可以使用 SELECT 子句。
-   要指定从中检索数据的表，可以使用 FROM 子句。
-   要指定行，可以使用 WHERE 子句。
-   要指定结果集的排序方式，可以使用 ORDER BY 子句。

图 3-4 — 如何从单个表中选择数据

## 如何从多个表中选择数据

图 3-5 演示了如何使用 SELECT 语句从两个表中检索数据。这通常被称为*连接*。任何连接的结果都是一个单一的表。

*内连接*是最常见的连接类型。使用内连接时，只有当两个表中的相关列匹配时，这两个表中的行数据才会包含在结果集中。例如，在此图中，只有当 products 表中的 categoryID 列的值等于 categories 表中的 categoryID 列时，SELECT 语句才会连接 products 表和 categories 表中的行数据。换句话说，如果某个类别在 products 表中没有数据，则该类别不会添加到结果集中。

要编写内连接，可以使用 JOIN 子句指定第二个表，使用 ON 子句指定用于连接的列。如果一个表中的列与另一个表中的列同名，可以通过表名、点和列名来指定要使用的列。此图中的 ON 子句对此进行了说明。

虽然此图只展示了如何连接两个表的数据，但你可以扩展此语法以连接更多表的数据。例如，假设你想创建一个包含名为 categories、products 和 orderitems 三个表数据的结果集。在这种情况下，可以这样编写 SELECT 语句的 FROM 子句：

```
FROM categories
    INNER JOIN products
        ON categories.categoryID = products.categoryID
    INNER JOIN orderitems
        ON products.productID = orderitems.productID
```

然后，可以在 SELECT 语句的列列表中包含来自这三个表的任意列。

另一种连接类型是*外连接*。使用这种连接类型，无论另一个表中是否存在匹配的行，其中一个表中的所有行都会包含在结果集中。当你需要查看一个表中的所有记录，而不管它们在另一个表中是否有匹配项时，这会很有用。这种查询也有助于识别缺失的数据。

在*左外连接*中，第一个表（左侧的表）中的所有行都会包含在结果集中。在*右外连接*中，第二个表中的所有行都会包含在结果集中。

为了说明这一点，假设一个 SELECT 语句使用左外连接将 categories 表中的行与 products 表中的行连接起来。在这种情况下，categories 表中的所有行都会包含在结果集中——即使 categories 表中的某些行在 products 表中没有任何匹配的行。

## 连接两个表的 SELECT 语句语法

```sql
SELECT column-1 [, column-2] ...
FROM table-1
    {INNER | LEFT OUTER | RIGHT OUTER} JOIN table-2
    ON table-1.column-1 {=|<|>|<=|>=|<>} table-2.column-2
[WHERE selection-criteria]
[ORDER BY column-1 [ASC|DESC] [, column-2 [ASC|DESC] ...]]
```

## 一个从两个相关表获取数据的语句

```sql
SELECT categoryName, productName, listPrice
FROM categories
    INNER JOIN products
    ON categories.categoryID = products.categoryID
WHERE listPrice > 800
ORDER BY listPrice ASC
```

| categoryName | productName | listPrice |
|---|---|---:|
| Guitars | Gibson Les Paul | 1199.00 |
| Guitars | Gibson SG | 2517.00 |

## 说明

-   要返回包含两个表数据的结果集，你需要*连接*这些表。为此，可以使用 JOIN 子句。
-   大多数时候，你应该编写*内连接*，这样只有当第一个表中某行的键与第二个表中某行的键相等（匹配）时，才会包含该行。
-   *外连接*会返回连接中一个表中的行，即使另一个表没有包含匹配的行。当你需要查看一个表中的所有记录，而不管另一个表中是否有匹配项时，这很有用。
-   在*左外连接*中，第一个表（左侧的表）中所有行的数据都会包含在结果表中，但第二个表中只包含匹配行的数据。在*右外连接*中，情况正好相反。

## INSERT 语句的语法

```sql
INSERT INTO table-name [(column-list)]
VALUES (value-list)
```

## 一个向表中添加一行数据的语句

```sql
INSERT INTO products
    (categoryID, productCode, productName, listPrice)
VALUES
    (1, 'tele', 'Fender Telecaster', 599.00)
```

## 一个使用 MySQL NOW 函数获取当前日期的语句

```sql
INSERT INTO orders (customerID, orderDate)
VALUES (1, NOW())
```

## UPDATE 语句的语法

```sql
UPDATE table-name
SET expression-1 [, expression-2] ...
WHERE selection-criteria
```

## 一个更新一行中某一列的语句

```sql
UPDATE products
SET productName = 'Ludwig 5-Piece Kit with Zildjian Cymbals'
WHERE productCode = 'ludwig'
```

## 一个更新多行中某一列的语句

```sql
UPDATE products
SET listPrice = 299
WHERE categoryID = 1
```

## DELETE 语句的语法

```sql
DELETE FROM table-name
WHERE selection-criteria
```

## 一个从表中删除一行数据的语句

```sql
DELETE FROM products
WHERE productID = 1
```

## 一个从表中删除多行数据的语句

```sql
DELETE FROM products
WHERE listPrice > 200
```

## 说明

-   由于 INSERT、UPDATE 和 DELETE 语句会修改数据库中存储的数据，因此它们有时被称为*操作查询*。这些语句不会返回结果集，而是返回受查询影响的行数。

图 3-6 — 如何插入、更新和删除数据

