
## 如何设置 PDO 的错误模式

图19-5展示了如何设置PDO的错误模式。默认情况下，PDO在连接数据库时使用“异常”模式。因此，如果连接数据库时出现错误，PDO会发出标准的PHP警告信息，并抛出一个可以捕获和处理的异常。

然而，在此之后，PDO在执行SQL语句时默认使用“静默”错误模式。因此，如果执行SQL语句时出错，PDO不会抛出异常，也不会发出标准的PHP警告。相反，它会在数据库对象（对于动态SQL语句）或语句对象（对于预处理SQL语句）中设置错误。然后，要查看错误，你可以对数据库或语句对象使用errorCode和errorInfo方法。但这要求你在每次数据库调用后检查错误。

由于“静默”模式不会发出PHP警告，因此它比其他两种模式更难调试。因此，在进行测试和调试时，你通常会希望使用另外两种模式之一。这样，如果遇到错误，PDO会发出传统的PHP警告，PHP会在你的网页上显示该警告。这样你就能轻松查看错误信息并调试问题。但是，你通常不希望向生产应用程序的用户显示这些错误信息。

对于新的Web应用程序，使用“异常”错误模式是合理的。这种错误模式允许你使用try/catch语句捕获PDO抛出的任何异常。由于这种方法不需要你在每次数据库调用后检查错误，它提供了一种灵活的错误处理方式。此外，如果你捕获所有可能抛出的异常并妥善处理，这在生产应用程序中也能很好地工作。

该图中的第一个示例展示了如何使用PDO类设置错误模式。此处，代码创建了一个选项数组。该数组包含一个元素，将PDO对象的错误模式属性设置为“异常”模式。然后，代码将该数组作为可选的第四个参数传递给PDO类的构造函数。虽然此示例只设置了一个选项，但如有必要，你可以在选项数组中包含多个选项。

第二个示例展示了设置错误模式的另一种方式。这种技术允许你在创建PDO对象后设置错误模式。要做到这一点，可以使用PDO对象的setAttribute方法，将错误模式属性设置为正确的错误模式。

第三个示例展示了如何使用try/catch语句捕获在执行SQL语句时可能抛出的PDOException对象。此处，SELECT语句错误地引用了“product”表而不是“products”表。因此，当代码尝试执行预处理的SELECT语句时，它会抛出PDOException。然后，执行跳转到catch块中。在catch块内，代码使用异常的getMessage方法获取错误信息。然后，它显示该消息并退出脚本。

## PDO的三种错误模式

| 名称 | 描述 |
|---|---|
| `ERRMODE_SILENT` | 这是默认的错误模式。PDO在数据库或语句对象中设置错误，但不会发出PHP警告消息或抛出异常。要访问错误，你可以对数据库或语句对象使用errorCode()和errorInfo()方法。但这要求你在每次数据库调用后检查错误代码。 |
| `ERRMODE_WARNING` | PDO设置错误，并且不像“静默”模式那样抛出异常，但会发出PHP警告消息。此设置适用于测试和调试。 |
| `ERRMODE_EXCEPTION` | PDO与“静默”模式一样设置错误，并抛出一个PDOException对象，该对象反映错误代码和错误消息。此设置也适用于测试和调试，并且使你可以更轻松地构建错误处理代码。 |

### 如何使用PDO类的构造函数来设置错误模式

```php
$dsn = 'mysql:host=localhost;dbname=my_guitar_shop';
$username = 'mgs_user';
$password = 'pa55word';
$options = array(PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION);

try {
    $db = new PDO($dsn, $username, $password, $options);
} catch (PDOException $e) {
    $error_message = $e->getMessage();
    echo "<p>Error connecting to database: $error_message </p>";
    exit();
}
```

### 如何使用setAttribute方法设置错误模式

```php
$db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
```

### 如何使用try/catch语句捕获PDOException对象

```php
try {
    $query = 'SELECT * FROM product';
    $statement = $db->prepare($query);
    $statement->execute();
    $products = $statement->fetchAll();
    $statement->closeCursor();
} catch (PDOException $e) {
    $error_message = $e->getMessage();
    echo "<p>Database error: $error_message </p>";
    exit();
}
```

### 说明

- 当你使用PDO执行SQL语句时，可以在三种错误模式中选择。在这些错误模式中，我们推荐“异常”错误模式。

图19-5 如何设置PDO的错误模式

## PDO中的模型

图19-6展示了与名为my_guitar_shop2的数据库配合使用的模型代码。该模型使用预处理语句，并使用“异常”错误模式。在下一章中，你将看到如何在Product Manager应用程序中使用此模型。不过现在，你可以重点关注它提供的用于检索、添加、更新和删除categories和products表中数据的函数。

该图首先展示了database.php文件的代码。虽然这些代码在技术上并不属于模型的一部分，但我将其包含在此处，因为它创建了模型中的函数所使用的数据库连接变量($db)。该代码使用名为my_guitar_shop2的数据库，并将错误模式设置为“异常”模式。因此，如果PDO在执行SQL语句时遇到错误，它会抛出异常。

database.php文件还定义了一个名为display_db_error的函数，模型中的其他函数使用该函数向用户显示数据库错误。首先，此函数使用global关键字获取$app_path变量。db_error.php文件的页眉需要此变量，你将在下一章中进一步了解它的工作原理。然后，此函数显示db_error.php文件并退出脚本。

category_db.php文件包含get_categories函数，该函数从数据库返回一个分类的二维数组。此外，它包含get_category方法，该方法返回指定类别的一维数组。这两种方法都使用预处理语句。它们使用statement对象的fetchAll和fetch方法返回数组。它们还使用try/catch语句来捕获和处理发生的任何错误。如果发生错误，它们会调用database.php文件中的display_db_error函数来显示错误并退出脚本。

返回数组而不是PDOStatement对象的好处在于，它将数据库层（模型）与表示层（视图）分离开来。另一种方法是返回PDOStatement对象。虽然这种方法将数据库层（模型）与表示层（视图）混合在一起，但对于大型结果集，它可能运行得更高效。不过，在这种情况下，categories表足够小，返回二维数组几乎没有什么缺点。

product_db.php文件包含用于检索、添加、更新和删除数据库中产品的函数。这些函数大部分与category_db.php文件中的函数工作方式相同。

前两个函数用于检索产品数据。这里，get_products_by_category函数返回指定类别ID的产品二维数组。然后，get_product函数返回带有指定产品ID的产品的一维数组。

接下来的三个函数允许用户添加、更新和删除产品。首先，add_product函数接受六个参数。然后，它将这些参数绑定到INSERT语句中的命名参数，并执行该语句。最后，它返回MySQL在数据库中插入行时自动生成的产品ID。

update_product函数接受七个参数，它将这些参数绑定到UPDATE语句中的命名参数，并执行该语句。然后，它返回受UPDATE语句影响的行数。由于每个产品都有唯一的产品ID，如果指定了现有的产品ID，该函数返回1。否则，返回0。因此，调用此函数的代码可以检查此值并采取适当的操作。

delete_product函数接受产品ID作为参数，它将该参数的值绑定到DELETE语句中的命名参数，并执行该语句。与update_product函数一样，如果删除了一行，此函数返回1；如果没有删除任何行，则返回0。
