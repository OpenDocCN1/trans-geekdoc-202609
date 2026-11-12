

```php
// Get the file extension
$fileExtension = strtolower(pathinfo($filePath, PATHINFO_EXTENSION));
```

```php
// Check file MIME type
$fileMimeType = mime_content_type($_FILES["file"]["tmp_name"]);
$allowedMimeTypes = array('image/jpeg', 'image/png', 'application/pdf');
if (!in_array($fileMimeType, $allowedMimeTypes)) {
    echo "Error: File type not allowed.";
    return;
}
```

```php
// Check file extension
$allowedExtensions = array('jpg', 'jpeg', 'png', 'pdf');
if (!in_array($fileExtension, $allowedExtensions)) {
    echo "Error: File extension not allowed.";
    return;
}
```

```php
// Move uploaded file to destination directory
if (move_uploaded_file($_FILES["file"]["tmp_name"], $filePath)) {
    echo "File uploaded successfully.";
} else {
    echo "Error uploading file.";
}
} else {
    echo "Error: " . $_FILES["file"]["error"];
}
?>

<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Secure File Upload</title>
</head>
<body>
    <h2>Secure File Upload</h2>
    <form action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]); ?>" method="post" enctype="multipart/form-data">
        <label for="file">Select a file:</label>
        <input type="file" id="file" name="file" accept="image/jpeg, image/png, application/pdf">
        <button type="submit">Upload</button>
    </form>
</body>
</html>
```

这段 PHP 代码确保了上传文件到服务器时的安全性。其详细工作原理如下：

- 1. 代码首先检查表单是否已提交，使用 $_SERVER["REQUEST_METHOD"] == "POST" 确保仅在提交表单时进行处理。
- 2. 接下来，它使用 $_FILES["file"]["error"] == UPLOAD_ERR_OK 检查文件上传过程中未出现问题。这确保了文件已成功上传，然后再进行进一步检查。
- 3. 它使用预定义目录和上传文件的名称（使用 basename($_FILES["file"]["name"])）来确定文件的目标路径。
- 4. 接下来，它使用 mime_content_type($_FILES["file"]["tmp_name"]) 检查上传文件的 MIME 类型，并将其与授权 MIME 类型列表（$allowedMimeTypes）进行比较。这确保仅允许上传指定的文件类型。

请注意，MIME（多用途互联网邮件扩展）类型是一种标准化标识符，用于指定文件的内容类型。它告诉服务器如何根据文件类型处理文件内容。例如，MIME 类型 "text/html" 表示该文件是 HTML 文档，而 "image/jpeg" 表示它是 JPEG 格式的图像。Web 服务器使用 MIME 类型来确定如何将文件内容提供给 Web 浏览器或其他应用程序。

- 5. 代码还使用 pathinfo($filePath, PATHINFO_EXTENSION) 检查文件扩展名，并将其与允许的扩展名列表（$allowedExtensions）进行比较。这通过确保上传的文件具有正确的扩展名，增加了一层额外的安全性。
- 6. 如果 MIME 类型和文件扩展名有效，则使用 move_uploaded_file() 将文件移动到目标目录。否则，将显示适当的错误消息，以告知用户上传文件时遇到的任何问题。
- 7. 最后，将显示一个 HTML 表单，以允许用户选择并上传文件。该表单通过 POST 方法且 enctype="multipart/form-data" 将数据发送到当前 PHP 脚本 ($_SERVER["PHP_SELF"])，从而实现文件上传。

这段代码通过检查上传文件的 MIME 类型和扩展名来增强上传文件的安全性，从而大大降低了恶意或危险文件被上传到服务器的风险。

## 结论

本章关于 PHP 安全性的内容强调了保护 Web 应用免受各种恶意威胁和攻击的至关重要性。我们深入探讨了安全性的各个方面，首先从 SQL 注入攻击开始，这是 Web 应用最常见且潜在最具破坏性的威胁之一。通过了解攻击者如何利用安全漏洞来操纵 SQL 查询并危及数据库数据，开发人员可以实施预防措施，例如使用预处理语句和绑定参数来防范这些攻击。

我们还探讨了跨站脚本（XSS），这是另一种主要威胁，允许攻击者将恶意 JavaScript 代码注入到 Web 页面中，从而危及最终用户的安全。通过使用特殊字符转义和用户输入验证等技术，开发人员可以降低 XSS 被利用的风险，并保护用户免受攻击。

还讨论了跨站请求伪造（CSRF），强调了伪造请求的潜在危险，这些请求利用用户信任在网站上执行未经授权的操作。通过使用防 CSRF 令牌和验证服务器端请求，开发人员可以降低此风险并保证用户操作的完整性。

最后，我们探讨了与文件下载相关的风险，强调了攻击者可利用来在服务器上执行恶意代码的潜在漏洞。通过对允许的文件类型施加严格限制、检查 MIME 签名并限制下载权限，开发人员可以降低这些漏洞被利用的风险并保护系统完整性。

综上所述，PHP 安全性是现代 Web 开发的重要方面。通过了解各种威胁并在整个开发过程中实施强大的安全实践，开发人员可以创建安全可靠的 Web 应用程序，保护用户的敏感数据并保障安全可靠的用户体验。

## PHP 中的面向对象编程

面向对象编程（OOP）是一种基于创建和操作对象的基本编程范式。在 PHP 中，OOP 提供了一种强大的结构化和组织代码的方式，实现了更高的可重用性、模块化以及对数据和功能的更高效管理。

过程式编程与面向对象编程（OOP）之间的区别在于它们对代码结构采用了根本不同的方法。在过程式编程中，程序围绕函数构建，数据通常可直接访问和操作。而在面向对象编程中，代码则围绕称为对象的实体进行组织。这些对象封装了数据（称为属性或特性）以及作用于这些数据的功能（称为方法）。

需要注意的是，OOP 并不本身是一种新的编程语言，而是一种在现代应用程序开发中广泛使用的编程范式。这种方法为设计和管理代码提供了更有组织的结构，将其划分为具有特定特征和行为的可重用对象。

至于 PHP，这是一种流行且灵活的编程语言，它为 OOP 提供了原生支持。这使开发人员能够使用 OOP 概念创建更强大、更可扩展的应用程序。

简而言之，OOP 提供了一种替代且高效的代码组织方式，其中一切都被视为对象。每个对象都具有用于存储数据的属性和用于对该数据执行操作的方法。这种方法促进了代码的可重用性、模块化和可维护性，使其成为许多软件开发项目的有吸引力的选择。

在本节中，我们将详细探讨 PHP 中 OOP 的基本原则以及良好的开发实践。以下是我们将涵盖的主题概述：

- 第 1 章：类和对象：本章通过介绍类和对象的概念，为 PHP 中的 OOP 奠定了基础。读者将学习如何定义类、创建对象实例以及访问它们的属性和方法。
- 第 2 章：封装和数据建模：本章探讨了 PHP 中的封装概念，并展示了如何使用类建模数据。
- 第 3 章：PHP 中的继承：本章探讨了 PHP 中的继承，允许您创建类层次结构以重用和扩展代码。
- 第 4 章：接口和抽象类：本章介绍了 PHP 中的接口和抽象类。您将学习如何使用接口定义契约以及如何创建抽象类以定义多个类共有的方法。
- 第 5 章：异常处理：本章涵盖了 PHP 中的异常处理，使您能够在应用程序中以干净高效的方式处理错误和异常情况。

