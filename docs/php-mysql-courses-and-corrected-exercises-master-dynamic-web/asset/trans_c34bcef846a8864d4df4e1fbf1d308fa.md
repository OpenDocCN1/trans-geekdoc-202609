

记录作者 "Dupont Alice"，其标识符等于 1。

| author_id | last_name | first_name | email | password | biography |
|---|---|---|---|---|---|
| 1 | Dupont | Alice | dupont-alice@gmail.com | azerty | queuou paieopie pio piolo epiopie ioapie opicpieopi... |

然而，需要注意的是，密码以未加密的形式存储在数据库中，这代表潜在的安全风险。如果恶意人员获得对数据库的访问权限，他们将能够访问这些敏感信息。这可能会危及您应用程序用户的安全，因为密码应始终安全存储，例如使用哈希技术，即使在未经授权访问数据库的情况下也使其不可读。要解决这个问题，最常见的解决方案之一是在将密码插入数据库之前对其进行哈希处理。

让我们修改文件 author_registration.php，在数据库连接代码之前添加以下代码行：

```
// Password hash
$password_hash = password_hash($password, PASSWORD_DEFAULT);
```

这行代码是一条指令，使用 **password_hash()** 函数对从表单中检索的密码进行哈希处理。该函数接受两个参数：要哈希的密码和要使用的哈希算法。

$password: 这是包含从表单中检索的原始密码的变量。

$password_hash: 这是将包含密码哈希结果的变量。该结果是由哈希算法生成的安全且唯一的字符串。

PASSWORD_DEFAULT: 这是 PHP 提供的一个常量，表示 password_hash() 函数推荐的默认哈希算法。该常可根据 PHP 版本进行更新，以使用可用的最安全哈希算法。

接下来，我们将行：$request->bindParam(':password', $password); 替换为以下代码

```
// Use hashed password
$request->bindParam(':password', $password_hash);
```

如果您在 index.php 页面上填写表单以注册新作者，并且一切顺利，您将看到消息 "Author added successfully!"。在检查数据库中的 authors 表后，您应观察到如下示例所示的注册数据：

| author_id | last_name | first_name | email | password | biography |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Dupont | Alice | dupont-alice@gmail.com | azerty | quaeou paieopie pio pio elope loapie olapiepl... |
| 2 | Lambert | Maximilien | maximilien@gmail.com | $2y$10$uaIX80NEpRzzlMTH7Y7GuGVVZBK3ERNJD.GbUpbGsc... | Maximilien Lambert is an expert in computer techno... |

请特别注意 ID = 2 的作者的 password 列。这个值是一个长字符串，表示密码在存储到数据库之前已被哈希处理，从而增强了数据安全性。您可以继续注册其他作者。

## 选择和显示数据库数据

在本节中，我们将探讨如何使用 PHP 和 MySQL 从数据库中选择和显示数据。我们将先编写代码，选择数据库中 "authors" 表内的所有作者，然后了解如何将这些数据显示在 HTML 表中。

现在让我们在 "library" 项目目录中创建一个名为 "display_authors.php" 的新文件。以下是选择作者的代码：

```
<?php

// Database connection
$connection = new PDO("mysql:host=localhost;dbname=library", "root", "");
$connection->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

// Prepare author selection query
$query = $connection->prepare("SELECT * FROM authors");

// Execute query
$query->execute();

// Retrieve results as associative array
$authors = $query->fetchAll(PDO::FETCH_ASSOC);

?>
```

行：$query = $connection->prepare("SELECT * FROM authors"); 准备一条 SQL 查询，以选择 "authors" 表中的所有列（*）。

行：`$authors = $query->fetchAll(PDO::FETCH_ASSOC);` 将所有查询结果作为关联数组检索并将其存储在 `$authors` 变量中。

总之，在此第一步中，连接到数据库后，代码执行一条 SQL 查询以选择所有作者，检索结果并将其存储在关联数组 `$authors` 中。

现在我们可以继续将这些作者显示在 HTML 表中。

让我们按如下方式修改文件 `display_authors.php`：

```
<!DOCTYPE html> <html lang="en">
<head> <meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>List of Authors</title>
</head>

<body>
<h2>List of Authors</h2>
<?php
// Part 1 - select and retrieve all authors

$connection = new PDO("mysql:host=localhost;dbname=library", "root","");
$connection->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
$query = $connection->prepare("SELECT * FROM authors");
$query->execute();

$authors = $query->fetchAll(PDO::FETCH_ASSOC);

// Part 2 - Displaying results in an HTML table

if (count($authors) > 0) {
    echo "<table>";
    echo "<tr>
        <th>ID</th>
        <th>Last Name</th>
        <th>First Name</th>
        <th>Email</th>
        <th>Biography</th>
    </tr>";
    foreach ($authors as $author) {
        echo "<tr>";
        echo "<td>{$author['author_id']}</td>";
        echo "<td>{$author['last_name']}</td>";
        echo "<td>{$author['first_name']}</td>";
        echo "<td>{$author['email']}</td>";
        echo "<td>{$author['biography']}</td>";
        echo "</tr>";
    }
    echo "</table>";
} else {
    echo "No author found.";
}
?>
</body>
</html>
```

此代码的第 2 部分首先通过检查从 `$authors` 变量中检索的作者数量是否大于零（使用 `if (count($authors) > 0)` 条件）来确定数据库中是否存在作者。如果找到作者，代码将生成一个 HTML 表以显示每个作者的详细信息。否则，如果未找到作者，它将显示消息 "No authors found."。

在 foreach 循环中，将浏览 `$authors` 数组中的每个作者。对于每个作者，代码将生成一个新表行，其中包含作者详细信息，例如作者 ID (`$author['author_id']`)、姓氏 (`$author['last_name']`)、名 (`$author['first_name']`)、电子邮件 (`$author['email']`) 和简介 (`$author['biography']`)。这些详细信息将显示在表单元格（`<td>`）中，每个作者将显示在新表行（`<tr>`）中。

运行 `display_authors.php` 将产生类似以下的结果：

## 作者列表

| ID | 姓 | 名 | 电子邮件 | 简介 |
|---|---|---|---|---|
| 1 | Dupont | Alice | dupont-alice@gmail.com | quecou paiecopie pio pioio eiope ioapie opioiiepie ziepoi eipei pei |
| 2 | Lambert | Maximilien | maximilien@gmail.com | Maximilien Lambert 是计算机技术专家 |

为增强此表格的外观，请考虑应用 CSS 样式。首先，创建一个 style_tab.css 文件，遵循上一章中采用的步骤。接下来，通过添加以下代码行，在 display_authors.php 文件的头部（head）中引用此文件。

```
<head> <meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>List of Authors</title>
<link rel="stylesheet" href="style_tab.css">
</head>
```

接下来，您可以添加以下 CSS 样式以自定义表格的外观。

```
table {
    width: 100%;
    border-collapse: collapse;
}

th, td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: left;
}

th {
    background-color: #f2f2f2;
}
```

在此代码中，我们有：

- **表格**: 此规则定义文档中所有表格的基本样式。
  - width: 100%; 表示表格的宽度应适应其容器的宽度。
  - border-collapse: collapse; 指定表格单元格的边框应折叠形成单个边框。

- **th, td**: 此规则定义表格中标题单元格（th）和数据单元格（td）的样式。
  - border: 1px solid #ddd; 在每个单元格周围创建 1 像素的浅灰色实线边框。
  - padding: 8px; 为每个单元格添加 8 像素的内边距，以提高可读性。
