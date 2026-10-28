

## 如何获取和修改数据

连接到数据库后，你可以使用该连接执行 SELECT 语句来检索数据，以及执行 INSERT、UPDATE 和 DELETE 语句来修改数据。

执行 SQL 语句有两种方式。你可以使用预处理语句，也可以使用动态语句。对于生产环境的应用，你通常会使用*预处理*语句，因为它们既能提升数据库性能，也能增强安全性。因此，本章只介绍如何使用预处理语句。不过，如果你想了解更多，第 19 章会介绍动态语句的工作原理。

### 如何执行 SELECT 语句

图 4-3 展示了如何准备并执行 SELECT 语句。为此，你需要调用 PDO 对象的 `prepare` 方法来准备查询，并返回一个 PDOStatement 对象。然后，你可以调用 PDOStatement 对象的 `execute` 方法来执行该语句。

对于 SELECT 语句，执行该语句会将结果集存储到 PDOStatement 对象中。例如，第一个示例准备并执行了一条获取 products 表中所有列和行的 SELECT 语句。

当然，大多数预处理语句会包含一个或多个参数。因此第二个示例展示了如何使用*命名参数*。命名参数以冒号（:）开头，后跟参数名。在此示例中，命名参数为 `:category_id`。

在查询中编写命名参数后，你可以使用 PDOStatement 对象的 `bindValue` 方法将值绑定到参数。在此示例中，`bindValue` 语句将 `$category_id` 变量中的值绑定到名为 `:category_id` 的参数。不过，如有必要，你可以在 SQL 语句中包含多个参数，并使用多条 `bindValue` 语句将多个变量绑定到其对应的参数。

#### PDO 类中用于准备 SQL 语句的一个方法

| 方法 | 描述 |
| --- | --- |
| `prepare($sql_statement)` | 准备指定的 SQL 语句以供执行，并返回一个 PDOStatement 对象。在 SQL 语句中，你可以使用冒号（:）向语句添加参数。 |

#### PDOStatement 类中用于执行语句的两个方法

| 方法 | 描述 |
| --- | --- |
| `bindValue($param, $value)` | 将指定值绑定到预处理语句中的指定参数。 |
| `execute()` | 执行预处理语句。 |

#### 如何执行没有参数的 SQL 语句

```php
$query = "SELECT * FROM products";
$statement = $db->prepare($query);
$statement->execute();
```

#### 如何执行带参数的 SQL 语句

```php
$query = "SELECT * FROM products
             WHERE categoryID = :category_id";
$statement = $db->prepare($query);
$statement->bindValue(':category_id', $category_id);
$statement->execute();
```

#### 说明

-   要准备一条 SQL 语句，你需要使用 PDO 对象的 `prepare` 方法。它只需要一个参数，即要执行的 SQL 语句。
-   要执行一条 SQL 语句，你需要使用 PDOStatement 对象的 `execute` 方法。
-   要标识 SQL 语句中的参数，你可以编写冒号（:）后跟参数名。
-   要将变量绑定到参数，你可以使用 PDOStatement 对象的 `bindValue` 方法。
-   如果 SQL 语句是返回结果集的 SELECT 语句，`execute` 方法会将结果集存储到 PDOStatement 对象中。然后，你可以使用接下来两个图中的技术从 PDOStatement 对象获取数据。

图 4-3   如何执行 SELECT 语句

### 如何处理结果集的第一行

如果 SELECT 语句返回的结果集只包含一行，你可以使用 PDOStatement 对象的 `fetch` 方法从该行获取数据，如图 4-4 所示。该方法返回结果集中下一行的数组。

数组可以存储一个或多个元素。要引用数组中的元素，你需要使用标识所需元素的索引。该索引可以是字符串值（如第二个示例所示），也可以是数值（如第三个示例所示）。如果使用数值索引，请确保第一列使用索引 0，第二列使用索引 1，依此类推。

在第一个示例中，第一条语句定义了一条返回单行结果集的 SELECT 语句。第二条语句调用 PDO 对象的 `prepare` 方法，返回该预处理语句的 PDOStatement 对象。第三条语句调用 PDOStatement 对象的 `bindValue` 方法，将一个变量绑定到产品 ID 的参数上。第四条语句调用 PDOStatement 对象的 `execute` 方法，将结果集存储到 PDOStatement 对象中。第五条语句调用该语句的 `fetch` 方法，获取结果集中第一行（也是唯一一行）的数组，并将其存储到名为 `$product` 的变量中。最后，第六条语句调用 `closeCursor` 方法关闭游标并释放到服务器的连接。

正如 `fetch` 方法的描述所示，该方法实际上返回结果集中的下一行。因此，如果结果集包含多行，你可以使用该方法一次获取一行。不过，通常你会使用 `foreach` 语句来获取包含多行的结果集中的所有行，如下一个图所示。

#### PDOStatement 类的另外两个方法

| 方法 | 描述 |
| --- | --- |
| `fetch()` | 返回结果集中下一行的数组。该数组同时以列名的字符串索引和列位置的数值索引进行索引。如果没有可用的数组，此方法返回 FALSE 值。 |
| `closeCursor()` | 关闭游标并释放到服务器的连接，以便可以发出其他 SQL 语句。 |

#### 返回单行结果集的代码

```php
$query = 'SELECT productCode, productName, listPrice
          FROM products
          WHERE productID = :product_id';
$statement = $db->prepare($query);
$statement->bindValue(':product_id', $product_id);
$statement->execute();
$product = $statement->fetch();
$statement->closeCursor();
```

#### 使用字符串索引访问各列的代码

```php
$product_code = $product['productCode'];
$product_name = $product['productName'];
$product_list_price = $product['listPrice'];
```

#### 使用数值索引访问各列的代码

```php
$product_code = $product[0];
$product_name = $product[1];
$product_list_price = $product[2];
```

#### 说明

-   *数组*可以存储一个或多个*元素*。
-   要引用数组中的元素，你需要使用*索引*。如果使用数值索引，0 表示第一个元素，1 表示第二个元素，依此类推。
-   你可以使用 PDOStatement 对象的 `fetch` 方法获取结果集第一行（或下一行）的数组。然后，你可以使用列名或数值索引访问存储在该行中的数据。
-   你将在第 11 章了解更多关于数组的内容。

图 4-4 — 如何处理结果集的第一行

### 如何处理结果集中的所有行

#### PDOStatement 类的另一个方法

| 方法 | 描述 |
| --- | --- |
| `fetchAll()` | 返回包含结果集中所有行的数组。 |

#### 一个返回两行或更多行结果集的查询方法

```php
$query = 'SELECT productCode, productName, listPrice
    FROM products
    WHERE categoryID = :category_id';
$statement = $db->prepare($query);
$statement->bindValue(":category_id", $category_id);
$statement->execute();
$products = $statement->fetchAll();
$statement->closeCursor();
```

#### 如何使用 foreach 语句在 HTML 表格中显示结果集

```php
<?php foreach ($products as $product) { ?>
<tr>
    <td><?php echo $product['productCode']; ?></td>
    <td><?php echo $product['productName']; ?></td>
    <td><?php echo $product['listPrice']; ?></td>
</tr>
<?php } ?>
```

#### foreach 语句的另一种语法，在 PHP 标签内效果更好

```php
<?php foreach ($products as $product): ?>
<tr>
    <td><?php echo $product['productCode']; ?></td>
    <td><?php echo $product['productName']; ?></td>
    <td><?php echo $product['listPrice']; ?></td>
</tr>
<?php endforeach; ?>
```

#### 说明

-   当 PDOStatement 对象包含结果集时，你可以使用 `fetchAll` 方法返回包含该结果集的数组。然后，你可以使用 `closeCursor` 方法关闭与数据库的连接。
-   要遍历数组中的元素，你可以使用*foreach*语句定义*foreach*循环，每次循环处理数组中的一个元素。
-   *foreach*语句的第二种语法更便于与其他控制语句配合使用，因为它不需要使用花括号。
-   当你将第二种语法与其他控制语句一起使用时，需要在每个控制语句起始子句后编写冒号，并以相应的结束语句结束每个控制语句。例如，使用 `endif` 语句结束 `if` 语句。

图 4-5   如何处理结果集中的所有行

