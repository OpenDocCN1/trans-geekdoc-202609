
通过使用此错误处理模式，与 SQL 查询执行相关的错误将自动转换为 `PDOException` 异常，从而使得在代码中使用 `try-catch` 块进行处理变得更加容易。这使得错误处理更加明确和高效。

最后，我们显示一条消息，指示数据库连接已成功建立，或者在发生连接问题时显示错误消息。

如果您通过执行 `index.php` 脚本来测试此代码，并且连接成功，您将获得以下结果：

![Image](images/image-148.png)

但是，如果数据库连接信息中发生错误，您将收到类似于以下结果的消息：

![Image](images/image-149.png)

## 结论

本章让我们详细了解了使用 PHP 连接 MySQL 数据库的过程。我们深入探讨了 `PDO` 对象方法。我们学习了如何有效地配置和处理连接错误。我们还探讨了数据库设计中主键和外键的概念，以及在 phpMyAdmin 中创建数据库和表的实际步骤。最后，我们查看了一个数据库连接和错误处理的具体示例。本章是理解 PHP Web 开发背景下 MySQL 数据库管理的第一步。在后续章节中，我们将研究用于数据库管理的 SQL 查询。

# 第 11 章：从数据库插入、检索和显示数据

在本章中，我们将介绍使用 PHP 和 `PDO` 扩展从 MySQL 数据库插入、检索和显示数据所涉及的各个步骤。我们将探讨用于插入新数据的 SQL 查询，以及用于执行这些查询并在 Web 应用程序中高效显示结果的 `PDO` 方法。

我们将探讨用于执行 SQL 插入查询并将新数据插入数据库的 `PDO` 方法。这将包括使用带参数的预处理 SQL 查询以及使用 `execute()` 执行查询。

我们将讨论从数据库检索已插入数据并在 Web 应用程序中显示它的各种技术。这还将包括使用循环遍历结果记录并以 HTML 表格及其他展示格式显示数据。

本章将通过开发一个迷你图书馆项目来讲解，并将为您提供关于如何在 PHP Web 应用程序中使用 `PDO` 扩展插入、检索和显示 MySQL 数据库数据的实用且深入的理解，同时专注于安全性和良好的开发实践。

## 使用 SQL 进行数据插入

为了演示将数据插入 MySQL 数据库的过程，我们将为“library”（图书馆）数据库中的“authors”（作者）表创建一个美观的插入表单。第一步是在 `index.php` 文件中创建插入表单，我们将使用 CSS 代码来美化表单。我假设您了解 CSS 基础知识，如果不了解，我建议您参阅我的书籍“HTML & CSS: from Beginner to Expert”（HTML 与 CSS：从入门到精通）。

### 插入表单 (index.php)

```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Author Inscription</title>
<link rel="stylesheet" href="style.css">
</head>
<body>
 <form action="author_registration.php" method="POST">
 <h2>Author registration</h2>
 <input type="text" name="lastname" placeholder="Last Name"><br>
 <input type="text" name="firstname" placeholder="First Name"><br>
 <input type="email" name="email" placeholder="Email"><br>
 <input type="password" name="password" placeholder="Password"><br>
 <textarea name="biography" placeholder="biography"></textarea><br>
 <input type="submit" value="Save">
 </form>
</body>
</html>
```

此 HTML 代码创建了一个作者注册表单，包含姓氏、名氏、电子邮件和密码字段。提交表单时，数据通过 `POST` 方法发送到 `author_registration.php` 文件页面。表单使用外部样式表 `style.css` 进行美化，代码行如下：

```
<link rel="stylesheet" href="style.css">
```

### CSS 样式表

接下来，我们创建一个新的 `style.css` 文件，并在其中放入以下代码以美化表单：

```
body {
 font-family: Arial, sans-serif;
 background-color: #f4f4f4;
 margin: 0;
 padding: 0;
 display: flex;
 justify-content: center;
 align-items: center;
 height: 100vh;
}
form {
 background-color: #fff;
 padding: 20px;
 border-radius: 8px;
 box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
 width: 400px;
 margin: auto; /* Ajout de cette ligne */
}
input {
 width: calc(100% - 20px);
 padding: 10px;
 border: 1px solid #ccc;
 border-radius: 4px;
 margin-bottom: 15px;
}
textarea {
 width: calc(100% - 20px);
 padding: 10px;
 border: 1px solid #ccc;
 border-radius: 4px;
 margin-bottom: 15px;
}
input[type="submit"] {
 background-color: #007bff;
 color: #fff;
 border: none;
 padding: 10px 20px;
 cursor: pointer;
 border-radius: 4px;
 display: block;
 margin: 0 auto;
}
input[type="submit"]:hover {
 background-color: #0056b3;
}
```

表单的 `action` 属性指向一个名为 `author_registration.php` 的文件路径，该文件负责检索表单提交的数据并将其插入 `library` 数据库的 `authors` 表中。让我们在 `library` 项目的根目录下创建此文件。

运行 `index.php` 将显示以下表单：

![Image](images/image-150.png)

### 数据处理与插入

#### author_registration.php

```
<?php
 // Retrieve form data
 $lastname = $_POST['lastname'];
 $firstname = $_POST['firstname'];
 $email = $_POST['email'];
 $password = $_POST['password'];
 $biography = $_POST['biography'];
 // Database connection
$connection = new PDO("mysql:host=localhost;dbname=library", "root","");
 $connection->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
 // Prepare insertion request
 $request = $connection->prepare("INSERT INTO authors (last_name, first_name, email, password, biography) VALUES (:lastname, :firstname, :email, :password, :biography)");
 // Bind values to query parameters
 $request->bindParam(':lastname', $lastname);
 $request->bindParam(':firstname', $firstname);
 $request->bindParam(':email', $email);
 $request->bindParam(':password', $password);
 $request->bindParam(':biography', $biography);
 // Execute query
 $result = $request->execute();
 // Verify successful insertion
 if ($result) {
 echo "Author is registered successfully!";
 } else {
 echo "Error registered author.";
 }
?>
```

此 PHP 代码首先通过 `POST` 方法检索从前一个 HTML 表单传输的数据。接下来，使用提供的凭据（主机名、数据库名、用户名和密码）通过 `PDO` 对象建立与 MySQL 数据库的连接。

接下来，使用 `INSERT INTO` 语句准备一个插入 SQL 查询，以向 `authors` 表添加新行。`lastname`、`firstname`、`email` 和 `password` 字段的值使用 `bindParam()` 方法绑定到查询参数。

值绑定到参数后，使用 `execute()` 方法执行查询，并将执行结果存储在 `$result` 变量中。

最后，代码通过验证 `$result` 的值来检查插入是否成功。如果为真，则显示一条消息，指示作者已成功注册。否则，显示一条错误消息，指示注册作者时出现问题。

详细解释：
