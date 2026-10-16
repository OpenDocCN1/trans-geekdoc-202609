
```
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>

<?php

if ($db = ibase_connect('/CHRISTIAN2003/tmp/quotes.gdb', 'user', 'password')) {

    $result = ibase_query($db, 'SELECT * FROM quotes');

    while ($row = ibase_fetch_object($result)) {

        printf(

'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',

htmlspecialchars($row->ID),

htmlspecialchars($row->QUOTE),

htmlspecialchars($row->AUTHOR),

htmlspecialchars($row->YEAR)

);

}

ibase_close($db);

} else {

echo '<tr><td colspan="4">Connection failed.</td></tr>';

}

?>
</table>
```

从InterBase/Firebird检索数据（`ibase_fetch.php`；摘录）

无论你使用`ibase_query()`还是`ibase_execute()`，最终都会有一个结果集的句柄，你可以使用`ibase_fetch_assoc()`（返回关联数组）或`ibase_fetch_object()`（返回对象）对其进行迭代。此代码使用后一种方法。

请记住，Firebird和InterBase以大写形式返回列名，因此对象属性（以及关联数组中的键）也是大写的。

### 通过`PDO`连接

```
try {
$db = new PDO('sqlite:PDOquotes.db');
}
```

```
<?php
try {
  $db = new PDO('sqlite:PDOquotes.db');
  echo 'Connected to the database.';
} catch (PDOException $ex) {
  echo 'Connection failed: ' . htmlspecialchars($ex->getMessage());
}
?>
```

通过`PDO`连接（`pdo_connect.php`）

`PDO`是PHP Data Objects的缩写，是由一些PHP核心开发者推动的新成果，也是PHP 5.1的关键特性之一。PHP中有几个抽象类，但`PDO`最终将成为官方标准。从PHP 5.3开始，`PDO`是PHP核心的一部分，因此Windows用户不需要在`php.ini`中引用特定的DLL。（在旧版PHP中，`extension=php_pdo.dll`可以实现这一点。）

除了可以使用`PDO`本身之外，还必须加载用于目标数据库的驱动程序。截至撰写本文时，可用的驱动程序如下：

- `PDO_CUBRID` 用于Cubrid
- `PDO_DBLIB` 用于Microsoft SQL Server（基于旧的`ext/mssql`扩展）
- `PDO_FIREBIRD` 用于InterBase/Firebird
- `PDO_IBM` 用于DB2
- `PDO_INFORMIX` 用于Informix
- `PDO_MYSQL` 用于MySQL 3.x–5.x
- `PDO_OCI` 用于Oracle
- `PDO_ODBC` 用于ODBC
- `PDO_PGSQL` 用于PostgreSQL
- `PDO_SQLITE` 用于SQLite版本2和3
- `PDO_SQLSRV` 用于Microsoft SQL Server（基于新的`ext/sqlsrv`扩展）
- `PDO_4D` 用于4D

为了尽可能使其可移植且易于部署，下面的示例使用SQLite驱动程序；但其他驱动程序和数据库系统也同样出色。无论你选择哪个系统，请在`php.ini`中下载并安装驱动程序。如果使用的是PHP 5.3之前的版本，请确保在`PDO`之后加载驱动程序——在新版PHP中，无需特意加载`PDO`。

`PDO`提供了一种面向对象的方法。你只需要一个合适的数据源名称（DSN）、一个用户和一个密码（可能还有其他选项）。前面的代码连接/创建了一个SQLite版本3文件。

### 通过`PDO`发送SQL

```
$stmt = $db->prepare($sql);
$stmt->execute();
```

```
<?php
try {
    $db = new PDO('sqlite:PDOquotes.db');
    $sql = 'INSERT INTO quotes (quote, author, year)
VALUES (:quote, :author, :year)';
    $stmt = $db->prepare($sql);
    $stmt->bindValue('quote', $_POST['quote']);
    $stmt->bindValue('author', $_POST['author']);
    $stmt->bindValue('year',
    intval($_POST['year']));
```

```
$stmt->execute();
echo 'Quote saved.';
} catch (PDOException $ex) {
echo 'Connection failed: ' .
htmlspecialchars($ex->getMessage());
}
?>
```

通过`PDO`发送SQL（`pdo_execute.php`：摘录）

要通过 `PDO` 发送 SQL，必须使用 `query()` 方法执行语句。像往常一样，你需要一种转义特殊字符的方法。这再次可以通过预处理语句来完成。首先，可以使用名为 `prepare()` 的方法解析 SQL 查询，其中占位符以冒号开头。然后，`bindValue()` 方法将值绑定到占位符名称（`bindParam()` 也可用，但需要可能被引用的值）。最后，`execute()` 方法将语句发送到数据库。

### 通过 `PDO` 检索查询结果

```
$result = $db->query();
$result->fetch(PDO::FETCH_ASSOC);
```

```
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
try {
$db = new PDO('sqlite:PDOquotes.db');
$result = $db->query('SELECT * FROM quotes');
while ($row = $result->fetch(PDO::FETCH_ASSOC)) {
```

```
printf(
    '<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
    htmlspecialchars($row['id']),
    htmlspecialchars($row['quote']),
    htmlspecialchars($row['author']),
    htmlspecialchars($row['year'])
);
}
} catch (PDOException $ex) {
    echo 'Connection failed: ' .
    htmlspecialchars($ex->getMessage());
}
?>
</table>
```

### 通过 `PDO` 检索数据（`pdo_fetch.php`；摘录）

最后，使用 `PDO` 读取 SQL 查询的结果采用标准方法：向服务器发送 `SELECT` 查询，然后使用 `while` 循环遍历结果。这里的迭代使用 `fetch()` 方法完成。你可以提供诸如 `PDO::FETCH_ASSOC`（返回关联数组）或 `PDO::FETCH_OBJ`（返回对象）等常量作为参数。或者，你可以使用 `fetchAll()` 方法并获取数组的数组，以便一次性获得所有数据。

此代码使用 `fetch()` 和 `PDO::FETCH_ASSOC` 从数据源读取所有数据。

**注意：** 截至本文撰写时，`PDO` 尚不能被视为稳定；因此，`PDO` 的 API 或行为将来可能会发生变化。此外，如果你尝试使用 `PDO`，请注意它尚未被证明像 PHP 本身一样可靠。

### PEAR 提供了什么？

以下 PHP 扩展和应用程序仓库（PEAR）软件包（其中之一）提供了数据库抽象层和其他用于数据库访问的实用功能：

- `DB_DataObject` 可以从对象创建 SQL。
- `MDB_QueryTool` 在构建 SQL 查询方面提供一些帮助。
- `MDB2` 是一个功能非常丰富的数据库抽象层。

如果你使用 Symfony 或 Zend Framework 等框架，你在那里也会有额外的数据库访问选项。

## 第10章 使用 XML

在炒作之后，可扩展标记语言（XML）现在几乎在任何地方都被真正使用。备受关注的应用是 Web 服务，这项技术在第 9 章“使用其他数据库”中有详细介绍。然而，XML 也可用于其他地方。它是存储任何类型数据的良好格式。

使用 XML 背后的任务始终相同：从 XML 读取数据并向其中写入数据。因此，本章重点介绍这些任务并展示如何实现它们。

不幸的是，PHP 4 的 XML 支持 somewhat 有限。一些扩展被证明并不十分稳定。随着 PHP 5 和重新设计的 XML 支持，这一情况发生了巨大变化。因此，我们在本章（以及本书其余部分）中完全省略了 PHP 4。在 PHP 5.1 和 5.2 中，添加了一些新功能，本章也涵盖了这些功能。

作为本章中的示例 XML 文件和格式，以下代码中的 XML 重用了前一章中的 `quotes` 数据库示例。如你所见，`<quotes>` 是根元素，每个 `quote`（包括其作者和短语创造年份）包含在 `<quote>` 元素中。

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<quotes>
<quote year="1991">
<phrase>Hasta la vista, baby!</phrase>
<author>Arnold Schwarzenegger</author>
</quote>
</quotes>
```

示例 XML 文件（`quotes.xml`；摘录）

### 使用 SAX 解析 XML

```
$sax = xml_parser_create();
xml_parser_set_option($sax, XML_OPTION_CASE_FOLDING, false);
xml_parser_set_option($sax, XML_OPTION_SKIP_WHITE, true);
xml_set_element_handler($sax, 'sax_start',
'sax_end');
xml_set_character_data_handler($sax, 'sax_cdata');
xml_parse($sax, file_get_contents('quotes.xml'), true);
xml_parser_free($sax);
```

简单的 XML API（SAX）是一种解析 XML 文档的方法，但不用于验证它们。

你使用 `xml_parser_create()` 创建 SAX 解析器，可选择提供编码作为参数。此解析器可以查看 XML 文件并对各种事件做出反应。以下三个事件是最重要的：

- 元素的开始
- 元素的结束
- CDATA 块

然后你可以为这些元素定义处理函数，并使用它们将 XML 转换为其他内容，例如超文本标记语言（HTML）。以下列表展示了这一点，并将 XML 文件的内容作为项目符号 HTML 列表输出，如图 10.1 所示。函数 `xml_set_element_handler()` 设置元素的开始和结束的处理程序，而 `xml_set_character_data_handler()` 设置 CDATA 块的处理程序。通过 `xml_parser_set_option()`，你可以配置处理程序，例如忽略空白并将标签名称作为区分大小写处理（然后标签名称不会自动转换为大写字母）。以下代码包含处理函数的代码：

```
function sax_start($sax, $tag, $attr) {
    if ($tag == 'quotes') {
        echo '<ul>';
    } elseif ($tag == 'quote') {
        echo '<li>' . htmlspecialchars($attr['year']) . '
        ': ';
    } elseif ($tag == 'phrase') {
        echo '"';
    } elseif ($tag == 'author') {
        echo ' (';
    }
}
```

```
}
function sax_end($sax, $tag) {
    if ($tag == 'quotes') {
        echo '</ul>';
    } elseif ($tag == 'quote') {
        echo '</li>';
    } elseif ($tag == 'phrase') {
        echo '"';
    } elseif ($tag == 'author') {
        echo ') ';
    }
}

function sax_cdata($sax, $data) {
    echo htmlspecialchars($data);
}
```

![](img/2862989e5dc7f1b1d0bc64321737f084_293_0.png)

图 10.1 从 XML 创建的 HTML

### 使用 `XMLReader` 解析 XML

```
echo '<ul>';
$xml = new XMLReader();
$xml->open('quotes.xml');
```

```
while ($xml->read()) {
    if ($xml->nodeType == XMLReader::ELEMENT) {
        if ($xml->localName == 'phrase') {
            $xml->read();
            echo '<li>' . htmlspecialchars($xml->value) . 
                '<\/li>';
        }
    }
}
echo '<\/ul>';
```

使用 `XMLReader` 解析 XML（`xmlreader.php`）

`XMLReader` 是 Microsoft .NET 中 `XmlTextReader` 接口的克隆，从 5.1.0 版本开始成为 PHP 发行版的一部分，并且默认激活。乍一看，它看起来与 SAX 解析器相似，但存在一个根本区别：SAX 是基于事件的解析器，而 `XMLReader` 使用一个光标遍历 XML 文件中的所有元素。

要使用 `XMLReader`，你实例化 `XMLReader` 类，然后打开文件（`open()` 方法）。常用的模式使用 `while` 循环和 `read()` 方法遍历所有元素。

在该循环中，你可以确定光标到达的节点的类型（`nodeType` 属性），然后相应地采取行动（例如，通过读取标签名称 [`localName` 属性] 并访问文本节点的值 [`value` 属性]）。

前面的代码再次从 XML 文档中读取所有短语并将其作为项目符号列表输出。

### 使用 DOM 读取 XML

```
<?php
$dom = new DOMDocument();
$dom->load('quotes.xml');
echo '<ul>';
foreach ($dom->getElementsByTagName('quote') as $element) {
    $year = $element->getAttribute('year');
    foreach (($element->childNodes) as $e) {
        if ($e instanceof DOMElement) {
            if ($e->tagName == 'phrase') {
                $phrase = htmlspecialchars($e->textContent);
            } elseif ($e->tagName == 'author') {
                $author = htmlspecialchars($e->textContent);
            }
        }
    }
    echo "<li>$author: \"$phrase\" ($year)</li>";
}
echo '</ul>';
?>
```
