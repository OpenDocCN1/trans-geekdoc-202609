

## 带比较运算符的WHERE子句语法

```
WHERE expression_1 operator expression_2
```

### 比较运算符

| 运算符 | 含义 |
|---|---|
| `=` | 等于 |
| `>` | 大于 |
| `<` | 小于 |
| `<=` | 小于或等于 |
| `>=` | 大于或等于 |
| `<>` | 不等于 |

### 一个WHERE子句，用于选择满足以下条件的产品...

- **位于指定类别中**

  ```sql
  WHERE categoryID = 2
  ```

- **具有指定的名称**

  ```sql
  WHERE productName = 'Gibson Les Paul'
  ```

- **标价低于指定价格**

  ```sql
  WHERE listPrice < 499.99
  ```

- **标价大于或等于指定价格**

  ```sql
  WHERE listPrice >= 499.99
  ```

- **名称以字母A到F开头**

  ```sql
  WHERE productName < 'G'
  ```

- **在指定日期之前添加**

  ```sql
  WHERE dateAdded < '2014-01-31'
  ```

- **在指定日期当天或之后添加**

  ```sql
  WHERE dateAdded >= '2014-01-31'
  ```

- **折扣百分比不等于指定值**

  ```sql
  WHERE discountPercent <> 30
  ```

### 说明

- 如果比较结果为TRUE，正在测试的行将包含在结果集中。如果结果为FALSE或未知，则该行不会被包含。
- 要在比较中使用字符串字面量或日期字面量，请将其括在单引号中。对于数字字面量，单引号是可选的。
- 字符比较不区分大小写。
- 可以使用比较运算符比较任意两个产生相同数据类型的表达式。虽然不同的数据类型可能会被转换为可比较的数据类型，但比较可能会产生意外结果。

图18-4 — 如何使用WHERE子句选择行

## 如何使用逻辑运算符

图18-5展示了如何在WHERE子句中使用*逻辑运算符*。你可以使用AND和OR运算符将两个或多个搜索条件组合成一个*复合条件*。你也可以使用NOT运算符来否定一个搜索条件。

前两个示例说明了AND运算符和OR运算符之间的区别。使用AND运算符时，两个条件都必须为TRUE。因此，第一个示例只检索类别ID为1且折扣百分比为30的产品。而使用OR运算符时，只需其中一个条件为TRUE。因此，第二个示例检索所有类别ID为1的产品*以及*所有折扣百分比为30的产品。

第三个示例展示了一个使用NOT运算符的WHERE子句。但请注意，NOT运算符使这个子句变得比实际需要更加难以理解。因此，应避免使用该运算符。你通常可以通过重写WHERE子句来避免它，如第四个示例所示。这样，第四个示例中的条件更容易理解。

最后两个示例展示了逻辑运算符的优先级顺序。默认情况下，MySQL先计算NOT运算符，然后是AND运算符，最后是OR运算符。因此，在第五个示例中，MySQL首先计算由AND连接的两个条件。然后，它计算由OR连接的条件。

但是，如果默认的优先级顺序不符合你的需求，你可以使用括号来覆盖它。例如，在第六个示例中，语句使用括号使得由OR连接的两个条件首先被计算。

在实践中，使用逻辑运算符可能会令人困惑。不过，稍加尝试，你应该就能编写出能检索出你想要的那些行的复合条件。

### 带逻辑运算符的WHERE子句语法

```
WHERE [NOT] search_condition_1 {AND|OR} [NOT] search_condition_2 ...
```

### 使用AND运算符的搜索条件

```
WHERE categoryID = 1 AND discountPercent = 30
```

### 使用OR运算符的搜索条件

```
WHERE categoryID = 1 OR discountPercent = 30
```

### 使用NOT运算符的搜索条件

```
WHERE NOT listPrice >= 500
```

### 重写以消除NOT运算符的相同条件

```
WHERE listPrice < 500
```

### 不带括号的复合条件

```
SELECT productName, listPrice, discountPercent, dateAdded
FROM products
WHERE dateAdded > '2014-07-01' OR listPrice < 500
AND discountPercent > 25
```

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_608_0.png)

### 带括号的相同复合条件

```
SELECT productName, listPrice, discountPercent, dateAdded
FROM products
WHERE (dateAdded > '2014-07-01' OR listPrice < 500)
AND discountPercent > 25
```

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_608_1.png)

### 说明

- 你可以使用AND和OR*逻辑运算符*来创建由两个或多个条件组成的*复合条件*。使用AND运算符指定搜索必须同时满足两个条件，使用OR运算符指定搜索必须至少满足其中一个条件。
- 你可以使用NOT运算符来否定一个条件。
- 当MySQL计算复合条件时，它会按以下顺序计算运算符：(1) NOT，(2) AND，然后(3) OR。你可以使用括号来覆盖此优先级顺序，或澄清操作将被计算的顺序。

图18-5 如何使用逻辑运算符

## 如何使用IS NULL运算符

在上一章中，你了解到列可以包含NULL值。但请记住，NULL值不同于零、包含一个或多个空格（' '）的空白字符串，或不包含任何空格（''）的空字符串。相反，NULL值表示数据不适用、不可用或未知。

当数据库允许在一个或多个列中出现NULL值时，你需要知道如何在搜索条件中测试它们。为此，你可以使用IS NULL运算符，如图18-6所示。

此图使用名为orders的表来说明如何搜索NULL值，因为该表允许其shipDate列包含NULL值。第一个示例从该表中选择三列和所有行。结果集显示三行中有两行的shipDate列包含NULL值。

第二个示例展示了如何使用IS NULL运算符检索shipDate列中具有NULL值的所有行。类似地，你可以在IS NULL运算符中使用NOT运算符，如第三个示例所示。然后，所有不包含NULL值的行都会包含在查询结果中。

### 带IS NULL运算符的WHERE子句语法

```
WHERE expression IS [NOT] NULL
```

### 检索所有行

```
SELECT orderID, orderDate, shipDate
FROM orders
```

| orderID | orderDate                 | shipDate                  |
|--------:|---------------------------|---------------------------|
| 1       | 2014-05-30 09:40:28.000000 | 2014-06-01 09:43:13.000000 |
| 2       | 2014-06-01 11:23:20.000000 | NULL                      |
| 3       | 2014-06-03 09:44:58.000000 | NULL                      |

### 检索尚未发货的订单行

```
SELECT orderID, orderDate, shipDate
FROM orders
WHERE shipDate IS NULL
```

| orderID | orderDate                 | shipDate |
|--------:|---------------------------|----------|
| 2       | 2014-06-01 11:23:20.000000 | NULL     |
| 3       | 2014-06-03 09:44:58.000000 | NULL     |

### 检索已发货的订单行

```
SELECT orderID, orderDate, shipDate
FROM orders
WHERE shipDate IS NOT NULL
```

| orderID | orderDate                 | shipDate                  |
|--------:|---------------------------|---------------------------|
| 1       | 2014-05-30 09:40:28.000000 | 2014-06-01 09:43:13.000000 |

### 说明

- 如果数据库允许列中包含NULL值，你可以使用IS NULL运算符选择该列中具有或不具有NULL值的行。

图18-6 — 如何使用IS NULL运算符

