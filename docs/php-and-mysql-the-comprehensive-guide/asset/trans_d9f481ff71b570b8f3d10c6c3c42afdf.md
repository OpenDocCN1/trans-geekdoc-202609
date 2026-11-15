

但它可以比使用 `mysqli_real_escape_string()` 更简单——同样安全，使用所谓的参数化查询。诀窍是你只需在 SQL 命令中输入占位符，然后将值绑定到占位符。PHP 或 MySQL 会完全自动处理特殊字符的正确转换，因此你不再需要担心此问题。参数化 SQL 语句如下所示：

```
INSERT INTO my_table (field) VALUES (?)
```

必须使用 `mysqli_prepare()` 准备此命令，并将命令对象作为返回值接收：

```
$command = mysqli_prepare($db, "INSERT INTO my_table (field) VALUES (?)");
```

使用 `mysqli_stmt_bind_param()` 函数（或者，如果你偏好 OOP 访问，使用命令对象的 `bind_param()` 方法），可以将值绑定到占位符。为此，首先需要一个包含所用数据类型的字符串参数。共有四种可能性：

- b: 数据类型 BLOB  
- d: 数据类型 double  
- i: 数据类型 integer  
- s: 数据类型 string  

字符串 "dis" 表示你有三个占位符：第一个是浮点数，第二个是整数，第三个字符串。顺序很重要；必须按照参数在 SQL 命令中出现的顺序指定参数。使用三个参数，编写如下：

```
mysqli_stmt_bind_param(
    $command,
    "dis",
    $doubleparam,
    $intparam,
    $stringparam
);
```

在我们的示例中，要简单一些，因为 SQL 命令中只有一个占位符：

```
mysqli_stmt_bind_param($command, "s", $value);
$value = "The value";
```

> **注意**  
> 因为参数值是 *按引用* 传递的，你无法直接在 `mysqli_stmt_bind_param()` 中传递值，而需要一个变量。

最后，执行 SQL 命令：使用 OOP 访问时，使用 `execute()` 方法；在过程式方法中，通过调用 `mysqli_stmt_execute()` 函数。

完整示例在以下清单中提供。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    $sql = "INSERT INTO table (field) VALUES (?)";
    $command = mysqli_prepare($db, $sql);
    mysqli_stmt_bind_param($command, "s", $value);
    $value = "value3";
    if (mysqli_stmt_execute($command)) {
        echo "Data entered.<br />";
    } else {
        echo "Error!";
    }
    mysqli_close($db);
} else {
    echo "Error!";
}
?>
```

清单 19.5 使用占位符填充表格（"mysqli-query-placeholder.php"）

为进行对比，以下是基于 OOP API 的清单。

```php
<?php
try {
    $db = new MySQLi("localhost", "user", "password", "PHP");
    $sql = "INSERT INTO my_table (field) VALUES (?)";
    $command = $db->prepare($sql);
    $command->bind_param("s", $value);
    $value = "value3";
    $command->execute();
    echo "Data entered.<br />";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 19.6 使用占位符填充表格（"mysqli-query-placeholder-oop.php"）

## 19.2.3 返回值

当查询的返回值很重要时，事情变得有趣起来。MySQL 像大多数其他数据库一样，使用逐行遍历结果列表的策略。当前行的数据随后以特定形式可用。每种特殊数据形式都有一个单独的函数。

要查询带返回值，也使用 `mysqli_query()`。此函数返回一个结果句柄（而 `query()` 方法返回类型为 `mysqli_result` 的对象），然后可使用它来访问结果列表中的数据。例如，可以使用 `mysqli_fetch_assoc()` 函数或 `fetch_assoc()` 方法。这同时执行两项任务：

- 它将结果列表的指针移动到下一行。  
- 它将当前行的数据确定为关联数组（以字段名作为键）。

如果没有下一行，函数返回 `false`。因此，该函数非常适合在 `while` 循环中使用：

```
while ($row = mysqli_fetch_assoc($result)) {
// Processing the result data
}
```

以下完整清单显示测试表中所有数据的输出（参见图 19.9）。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    $sql = "SELECT * FROM my_table";
    if ($result = mysqli_query($db, $sql)) {
        echo "<ul>";
        while ($row = mysqli_fetch_assoc($result)) {
            echo "<li>" . htmlspecialchars($row["id"]) .
            ": " . htmlspecialchars($row["field"]) . "</li>" ;
        }
        echo "</ul>";
    }
    mysqli_close($db);
} else {
    echo "Error!";
}
?>
```

清单 19.7 所有查询数据作为关联数组（"mysqli-read-associative.php"）

使用 OOP 接口时，代码的基本顺序不变。

```php
<?php
try {
    $db = new MySQLi("localhost", "user", "password", "PHP");
    $sql = "SELECT * FROM my_table";
    $result = $db->query($sql);
    echo "<ul>";
    while ($row = $result->fetch_assoc()) {
        echo "<li>" . htmlspecialchars($row["id"]) .
            ": " . htmlspecialchars($row["field"]) . "</li>";
    }
    echo "</ul>";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 19.8 所有查询数据作为关联数组（"mysqli-read-associative-oop.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_571_0.png)

图 19.9 小而强大：测试表

除了通过关联数组访问外，还有几种替代方案——例如，通过对象访问。在这种情况下，字段名是行对象的属性。相关函数称为 `mysqli_fetch_object()`，方法称为 `fetch_object()`。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    $sql = "SELECT * FROM my_table";
    if ($result = mysqli_query($db, $sql)) {
        echo "<ul>";
        while ($row = mysqli_fetch_object($result)) {
            echo "<li>" . htmlspecialchars($row->id) .
                ": " . htmlspecialchars($row->field) . "</li>";
        }
        echo "</ul>";
    }
    mysqli_close($db);
} else {
    echo "Error!";
}
?>
```

清单 19.9 所有查询数据作为对象（"mysqli-read-object.php"）

当然，在下一个清单中我们也再次查看 OOP 版本——如果我们已经在使用对象，这很好。

```php
<?php
try {
    $db = new MySQLi("localhost", "user", "password", "PHP");
    $sql = "SELECT * FROM my_table";
    $result = $db->query($sql);
    echo "<ul>";
    while ($row = $result->fetch_object()) {
        echo "<li>" . htmlspecialchars($row->id) .
            ": " . htmlspecialchars($row->field) . "</li>";
    }
    echo "</ul>";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 19.10 所有查询数据作为对象（"mysqli-read-object-oop.php"）

最后但同样重要的是，应介绍第三种方法（别担心，还有其他方法）：读取为数值数组。例如，如果需要读取结构未知的表，这很有用。或者如果你有类似 `SELECT COUNT()` 的查询，很难确定列名（除非使用别名）。此时，可以通过数值索引轻松访问表数据。此方法也非常快。相应的 PHP 函数称为 `mysqli_fetch_row()`，方法类似于 `fetch_row()`。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    $sql = "SELECT * FROM my_table";
    if ($result = mysqli_query($db, $sql)) {
        echo "<ul>";
        while ($row = mysqli_fetch_row($result)) {
            echo "<li>" . htmlspecialchars($row[0]) .
                ": " . htmlspecialchars($row[1]) . "</li>";
        }
        echo "</ul>";
    }
    mysqli_close($db);
} else {
    echo "Error!";
}
?>
```

清单 19.11 所有查询数据作为数值数组（"mysqli-read-array.php"）

当然，使用 OOP 编程接口仍然可以做到这一点。

```php
<?php
try {
    $db = new MySQLi("localhost", "user", "password", "PHP");
    $sql = "SELECT * FROM my_table";
    $result = $db->query($sql);
    echo "<ul>";
    while ($row = $result->fetch_row()) {
        echo "<li>" . htmlspecialchars($row[0]) .
             ": " . htmlspecialchars($row[1]) . "</li>";
    }
    echo "</ul>";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 19.12 所有查询数据作为数值数组（"mysqli-read-array-oop.php"）

> **注意**  
> 正如前面所述，读取数据还有其他选项，将稍后介绍。`mysqli_fetch_array()` 函数和 `fetch_array()` 方法将当前行读取为数组，是 `mysqli_fetch_assoc()` 和 `mysqli_fetch_row()` 的一种混合体。此函数可以返回关联数组、数值数组，甚至两者皆可。可以通过给函数传递第二个参数（数组类型）来控制其行为。mysqli 扩展为此提供了以下常量选项：
>
> - MYSQLI_ASSOC  
>   关联数组  
> - MYSQLI_BOTH  
>   关联数组和数值数组（默认行为）

