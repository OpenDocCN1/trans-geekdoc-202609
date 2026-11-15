

请参考以下完整清单。

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP->my_table;
    $result = $db->find([
        "name1" => "value1", "name2" => "value2"
    ]);
    echo "<table><tr><th>name1</th><th>name2</th></tr>";
    foreach ($result as $id => $row) {
        printf("<tr><td>%s</td><td>%s</td></tr>",
            htmlspecialchars($row["name1"]),
            htmlspecialchars($row["name2"]));
    }
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 24.5 查询并输出集合数据 ("mongo-read.php")

> **注意**
> 
> 如果你只期望查询返回一条数据记录（或只需要所有返回文档中的第一条），请使用 `findOne()` 而非 `find()`。语法保持不变。

最后有个重要提示：如果你想使用文档的 ID 作为搜索条件，则必须小心。如图 24.6 所示，存在一个 ID——不是作为简单的字符串值，而是作为 `ObjectID` 类型的对象。因此，在比较条件时，你还必须指定一个 `ObjectID` 实例，包括完整的命名空间。相关属性称为 `_id`：

```php
$result = $db->find([ "_id" => new MongoDB\BSON\ObjectID("abc123") ]);
```

## 24.2.4 刷新

要更新现有条目，MongoDB 使用 `updateOne()` 和 `updateMany()` 方法，具体取决于你只想更改一条还是多条数据记录。作为 `updateOne()` 的替代方案，你也可以使用 `replaceOne()`。此方法替换完整的数据记录；而 `updateOne()` 则可以在不破坏现有数据的前提下添加额外字段。这些函数首先期望类似 find() 和 findOne() 的搜索条件，然后是要用于替换找到记录的新文档。语法有些特殊：$set 数组键用于指定值的写入。MongoDB 还在此提供了一些其他选项，例如用于更新的特殊运算符。在下面的清单中，我们将简单地插入另一条数据记录。

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP->my_table;
    $db->updateOne(
        ["name1" => "value1"], //Search criterion
        ["\$set" => ["name1" => "value3", "name2" => "value4"]] //New document
    );
    $result = $db->find();
    echo "<table><tr><th>name1</th><th>name2</th></tr>";
    foreach ($result as $id => $row) {
        printf("<tr><td>%s</td><td>%s</td></tr>",
            htmlspecialchars($row["name1"]),
            htmlspecialchars($row["name2"])
        );
    }
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 24.6 更新集合数据 ("mongo-update.php")

图 24.8 显示了结果。

![](img/ae7820c36e8f24c1623d26668b28e80e_694_0.png)

图 24.8 数据已更新

## 24.2.5 删除

最后，数据也可以从 MongoDB 数据库中删除。在之前的解释之后，该过程可能不再是什么大惊喜。deleteOne() 方法负责删除一条数据记录，而 deleteMany() 则一次性删除多条数据记录。搜索条件再次作为参数期望。清单 24.7 包含完整代码。

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP->my_table;
    $db->deleteOne(
        ["name1" => "value3"] //search criterion
    );
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 24.7 删除集合数据 ("mongo-delete.php")

这就是对 MongoDB PHP 控制的初步了解。http://php.net/mongodb 上的在线手册包含完整且详细的 API 描述。

## 24.3 应用示例

为结束本章——以及整个数据库部分——我们基于 MongoDB 实现了众所周知的留言本示例。应用程序的基本结构保持不变，但数据库通信是根据前面页面的信息进行的。只更改了少数细节。

### 24.3.1 创建数据内存

我们假设应用程序的默认值：运行的 MongoDB 实例位于当前服务器上，使用默认端口，且无需额外身份验证。我们在 PHP 数据库（可能已从前面的示例中存在）中创建一个新的留言本集合一次。正如已讨论的，我们不需要数据库架构。

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP;
    $db->createCollection("guestbook");
    echo "Database created.<br />";
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 24.8 集合已创建 ("gb-create.php")

### 24.3.2 输入数据

创建数据存储后，我们使用常用的 HTML 界面进行数据输入。有一个特殊功能：MongoDB 基于 UTF-8 工作，因此我们相应地使用 utf8_encode() 对输入进行编码。² 从此我们创建一个简单的关联数组，然后直接将其发送到 MongoDB：

```php
$data = [
    "heading" => utf8_encode($_POST["Heading"]),
    "entry" => utf8_encode($_POST["Comment"]),
    "author" => utf8_encode($_POST["Name"]),
    "email" => utf8_encode($_POST["Email"]),
    "date" => time()
];
$result = $db->insertOne($data);
```

插入后，我们可以使用 getInsertedId() 方法来确定生成的自动值。如前面所述，这属于 ObjectID 类型。但是，字符串表示形式即为 ID 值本身，因此我们可以像下面这样将其追加到 URL 中：

```php
$id = $result->getInsertedId();
echo "Entry added. <a href=\"gb-edit.php?id=$id\">Edit</a>";
```

请参考以下完整清单。

```php
<html>
<head>
    <title>Guestbook</title>
</head>
<body>
    <h1>Guestbook</h1>
<?php
if (isset($_POST["Name"]) &&
    isset($_POST["Email"]) &&
    isset($_POST["Heading"]) &&
    isset($_POST["Comment"])) {
    require_once __DIR__ . "/vendor/autoload.php";

    try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP->guestbook;
    $data = [
        "heading" => utf8_encode($_POST["Heading"]),
        "entry" => utf8_encode($_POST["Comment"]),
        "author" => utf8_encode($_POST["Name"]),
        "email" => utf8_encode($_POST["Email"]),
        "date" => time()
    ];
    $result = $db->insertOne($data);
    $id = $result->getInsertedId();
    echo "Entry added.
    <a href=\"gb-edit.php?id=$id\">Edit</a>";
    } catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
    }
}
?>
<form method="post" action="">
Name <input type="text" name="Name" /><br />
Email address <input type="text" name="Email" /><br />
Heading <input type="text" name="Heading" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"></textarea><br />
<input type="submit" name="Submit" value="Submit" />
</form>
</body>
</html>
```

² 在完全依赖 UTF-8 的系统上，此步骤可能不是必需的。在这种情况下，你可以删除对 utf8_encode() 的调用——以及下一个清单中 utf8_decode() 的调用。

清单 24.9 可以输入数据 ("gb-enter.php")

### 24.3.3 输出数据

输出所有数据是小菜一碟——即使与其他数据库系统相比也是如此：find() 返回所有文档，我们通过 foreach 遍历它们。我们仍需考虑的唯一事项是使用 utf8_decode() 对数据进行 UTF-8 解码。

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
require_once __DIR__ . "/vendor/autoload.php";
try {
$conn = new MongoDB\Client();
$db = $conn->PHP->guestbook;
$result = $db->find();
foreach ($result as $id => $row) {
printf("<p><a href=\"mailto:%s\">%s</a> wrote on at %s:</p>
<h3>%s</h3><p>%s</p><hr noshade=\"noshade\" />",
urlencode(utf8_decode($row["email"])),
htmlspecialchars(utf8_decode($row["author"])),
htmlspecialchars(date("Y-m-d, H:i", $row["date"])),
htmlspecialchars(utf8_decode($row["heading"])),
nl2br(htmlspecialchars(utf8_decode($row["entry"])))
);
}
} catch (Exception $ex) {
echo "Error: " . $ex->getMessage();
}
?>
</body>
</html>
```

清单 24.10 输出留言本数据 ("gb-show.php")

### 24.3.4 删除数据

要删除数据，我们需要 `deleteOne()` 方法和一个相应的查询。但是，在此处，我们想展示 MongoDB PHP 库 API 的另一个方法：`findOneAndDelete()`。这个名字显然不言自明。由于删除时通过 GET 参数传递 ID，我们可以这样表述：

```php
$db->findOneAndDelete(["_id" => new MongoDB\BSON\ObjectID($_GET["id"])]);
```

与本书中介绍的其他数据库系统相比，一个重要的变化是 ID 的验证。它不完全是数值，而是由字母和数字组成。使用 `ctype_alnum()`，我们可以检查是否只使用了这些字符。

以下清单显示了删除掩码的完整代码。

