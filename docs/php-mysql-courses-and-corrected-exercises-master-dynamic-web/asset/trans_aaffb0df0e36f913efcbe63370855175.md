

从变量 $lastname、$firstname、$email 和 $country 中检索。最后，执行一个数据处理示例，其中显示这些变量的值以供演示。

如果请求方法不是 POST，即数据未通过表单提交，则会显示错误消息“错误：未授权访问”。

请注意，PHP 中的 filter_var 函数用于使用特定过滤器过滤变量。它接受两个参数：要过滤的变量和要应用的过滤器。

在此示例中，FILTER_VALIDATE_EMAIL 被用作过滤器，以检查变量是否包含有效的电子邮件地址。此过滤器旨在根据标准格式规范验证电子邮件地址。如果变量不包含有效的电子邮件地址，filter_var 函数返回 false，否则返回电子邮件地址。

总之，filter_var($_POST["email"], FILTER_VALIDATE_EMAIL) 检查变量 $_POST["email"] 是否根据标准格式标准包含有效的电子邮件地址。如果是，则返回电子邮件地址，否则返回 false。

## 在 PHP 中使用 GET 方法检索数据

GET 方法通常用于通过将数据附加到 URL 的方式，将表单数据发送到 PHP 脚本，尤其是当数据不敏感且不包含机密信息时。此数据在浏览器 URL 中可见，并可以在服务器端检索和处理。

要在 PHP 中检索通过 GET 方法发送的数据，我们使用 $_GET 超全局变量。此超全局变量包含 URL 中传递的参数的关联数组。参数使用 URL 中定义的名称进行检索。

我们将探讨如何使用 $_GET 检索 URL 参数值，以及如何在 PHP 脚本中使用它们来执行各种操作。

为此，我们返回到之前的示例。在 form.php 文件中，将 method 属性的 "post" 方法替换为 "get"。在 processingform.php 中，将所有 $_POST 的出现替换为 $_GET。

## form.php:

```php
<?php

// Check whether data has been sent via POST
if ($_SERVER["REQUEST_METHOD"] == "GET") {

    // Retrieve form data
    $name = $_POST["lastname"];
    $firstname = $_POST["firstname"];
    $email = $_POST["email"];
    $country = $_POST["country"];

    // Example of data processing (display)
    echo "Name : ". $name . "<br>";
echo "First name : " . $firstname . "<br>";
echo 'Email : ' . $email . "<br>";
echo "Country : " . $country . "<br>";
}else{
// Display an error message if the request method is not POST
echo "Error: Access not authorized.";
}
?>
```

## Processingform.php:

```php
<?php
// Check whether data has been sent via POST
if ($_SERVER["REQUEST_METHOD"] == "GET") {
// Check if expected data is available in $_GET
if (empty($_GET["lastname"])) {
echo "Please enter your last name!";
} elseif (empty($_GET["firstname"])) {
echo "Please enter your first name!";
} elseif (empty($_GET["email"]) || !filter_var($_GET["email"], FILTER_VALIDATE_EMAIL)) {
echo "Please enter a valid email!";
} elseif (empty($_GET["country"])) {
echo "Please select your country!";
} else {
    // Retrieve form data
    $lastname = $_GET["lastname"];
    $firstname = $_GET["firstname"];
    $email = $_GET["email"];
    $country = $_GET["country"];

    // Example of data processing (display)
    echo "Last Name : ". $lastname ."<br>";
    echo "First Name : ". $firstname ."<br>";
    echo "Email : ". $email ."<br>";
    echo "Country : ". $country ."<br>";
}
} else {
    // Display an error message if the request method is not POST
    echo "Error: Access not authorized";
}
?>
```

当您填写表单并点击“发送”按钮提交时，您将得到类似于以下的结果：

![](img/caba2aa22f5409ba73dea47176330677_285_0.png)

请注意，表单的内容已通过浏览器的 URL 地址传输。换句话说，GET 方法将数据作为 URL 中的查询字符串发送，从而方便查看和共享。

然而，需要注意的是，不建议使用 GET 方法发送敏感数据，例如密码，因为这些数据在 URL 中可见，并可能被第三方拦截。在这种情况下，POST 方法更可取，因为它将数据发送在 HTTP 请求的正文中，从而降低可见性。

此外，与 POST 方法相比，GET 方法有几个局限性：

- **数据大小限制** : 通过 GET 方法传输的数据大小受到限制，因为它包含在 URL 中。这对于大量或敏感数据可能是个问题。

- **数据安全性**：由于数据在 URL 中可见，因此很容易被第三方拦截和读取。这可能会危及密码或个人信息等敏感数据的安全性。

- **特殊字符限制**：某些特殊字符必须在 URL 中进行编码，如果处理不当，可能会导致错误或数据丢失。

**浏览器缓存：** 通过 GET 方法传输的数据可能会被浏览器缓存，如果用户共享包含敏感数据的 URL，可能会导致机密性问题。

总之，虽然 GET 方法使用简单且适合少量非敏感数据，但在安全性、数据大小和特殊字符处理方面存在显著局限性。对于敏感或大量数据，我们建议使用 POST 方法。

## 第 8 章

## 图像和文件

图像和文件操作是现代 Web 开发的重要组成部分。在本章中，我们将重点介绍两个主要方面：发送和显示图像和文件，以及在服务器上管理这些文件。

首先，我们将探讨从 HTML 表单向 PHP 服务器发送图像和文件的过程。我们将了解如何在服务器端处理这些数据，检查文件类型和大小，然后将它们保存在服务器上。接下来，我们将了解如何使用适当的 HTML 标签在网页中显示这些图像。

接下来，我们将了解服务器端的文件管理。我们将探讨创建、读取、写入和删除文件等常见操作。我们将了解如何操作目录、列出文件以及其他文件管理操作。

本章将带您深入探讨 PHP 中的图像和文件操作，为您提供有效管理 Web 应用程序中多媒体资源和文件所需的知识和技能。

## 发送和显示图像或文件

使用表单发送和显示图像或文件的过程可以分为几个阶段：

- 创建上传表单：首先，您需要创建一个 HTML 表单，以允许用户从其设备选择并上传文件到服务器。您可以使用类型为 "file" 的 `<input>` 标签来创建用于选择文件的表单字段。

- 表单处理：用户提交表单后，文件数据将发送到服务器。然后，您需要创建 PHP 代码来处理这些数据。此代码可以集成到同一表单脚本中，也可以在独立的 PHP 脚本中。此代码必须检查文件是否已正确发送，是否遵守您定义的文件大小和类型限制，然后将其保存在服务器上。

- 在网页上显示图像：图像发送并保存在服务器上后，您可以使用 HTML 的 `` 标签在网页上显示它。您必须在 `` 标签的 "src" 属性中指定图像的路径。

### 创建发送表单

以下是一个代码示例，用于说明该过程：

在 index.php 文件中，创建以下表单：

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Image submission form</title>
</head>
<body>
<form action="" method="post" enctype="multipart/form-data">
  <label for="file">Select an image to send:</label>
  <input type="file" name="file" id="file" capture="Select File">
  <input type="submit" value="Send">
</form>
</body>
</html>
```

此 HTML 表单用于允许用户将文件（尤其是图像）发送到 Web 服务器。

`<form action="" method="post" enctype="multipart/form-data">`: 此 `<form>` 标签定义表单的开始。action 属性指定数据处理脚本的 URL（在此情况下为空，以提交到同一页面），而 method 属性指定用于发送数据的 HTTP 方法，在此情况下为 "post"。**enctype** 属性定义表单的内容类型，在发送文件时为 "multipart/form-data"。

以下是表单的概览：

