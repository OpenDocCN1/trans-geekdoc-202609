
如果满足所有条件，即所有必填字段均已填写且电子邮件地址有效，则从变量 `$lastname`、`$firstname`、`$email` 和 `$country` 中获取表单数据。最后，执行一个数据处理示例，出于演示目的显示这些变量的值。

如果请求方法不是 POST，即数据未通过表单提交，则显示“Error: Access not authorized”（错误：未授权访问）错误消息。

请注意，PHP 中的 `filter_var` 函数用于使用特定过滤器过滤变量。它接受两个参数：要过滤的变量和要应用的过滤器。

在此示例中，`FILTER_VALIDATE_EMAIL` 用作过滤器，用于检查变量是否包含有效的电子邮件地址。此过滤器旨在根据标准格式规范验证电子邮件地址。如果变量不包含有效的电子邮件地址，`filter_var` 函数返回 false，否则返回该电子邮件地址。

总之，`filter_var($_POST["email"], FILTER_VALIDATE_EMAIL)` 检查变量 `$_POST["email"]` 是否根据标准格式标准包含有效的电子邮件地址。如果是，则返回该电子邮件地址，否则返回 false。

## 在 PHP 中使用 GET 方法检索数据

GET 方法常用于将表单数据发送到 PHP 脚本，方法是将数据附加到 URL 后面，特别是在数据不敏感且不包含机密信息时。此数据在浏览器 URL 中可见，可在服务器端检索和处理。

要在 PHP 中检索通过 GET 方法发送的数据，我们使用 `$_GET` 超全局变量。此超全局变量包含一个关联数组，存放 URL 中传递的参数。参数使用 URL 中定义的名称进行检索。

我们将探讨如何使用 `$_GET` 检索 URL 参数值，以及如何在 PHP 脚本中使用它们执行各种操作。

为此，我们回到前面的示例。在 `form.php` 文件中，将 method 属性的 "post" 方法替换为 "get"。在 `processingform.php` 中，将所有 `$_POST` 出现替换为 `$_GET`。

### form.php

```php
<?php

 // 检查是否已通过 POST 发送数据

 if ($_SERVER["REQUEST_METHOD"] == "GET") {

 // 检索表单数据

 $name = $_POST["lastname"];

 firstname = $_POST["firstname"];

 $email = $_POST["email"];

 country = $_POST["country"];

 // 数据处理示例（显示）

 echo "Name : " . $name . "<br>";

 echo "First name : " . $firstname . "<br>";

 echo "Email : " . $email . "<br>";

 echo "Country : " . $country . "<br>";

 }else{

 // 如果请求方法不是 POST，则显示错误消息

 echo "Error: Access not authorized.";

 }

?>
```

### Processingform.php

```php
<?php

 // 检查是否已通过 POST 发送数据

 if ($_SERVER["REQUEST_METHOD"] == "GET") {

 // 检查 $_GET 中是否有预期数据

 if (empty($_GET["lastname"])) {

 echo "Please enter your last name!";

 } elseif (empty($_GET["firstname"])) {

 echo "Please enter your first name!";

 } elseif (empty($_GET["email"]) || !filter_var($_GET["email"], FILTER_VALIDATE_EMAIL)) {

 echo "Please enter a valid email!";

 } elseif (empty($_GET["country"])) {

 echo "Please select your country!";

 } else {

 // 检索表单数据

 $lastname = $_GET["lastname"];

 $firstname = $_GET["firstname"];

 $email = $_GET["email"];

 $country = $_GET["country"];

 // 数据处理示例（显示）

 echo "Last Name : " . $lastname . "<br>";

 echo "First Name : " . $firstname . "<br>";

 echo "Email : " . $email . "<br>";

 echo "Country : " . $country . "<br>";

 }

 } else {

 // 如果请求方法不是 POST，则显示错误消息

 echo "Error: Access not authorized";

 }

?>
```

当你填写表单并点击“Send”（发送）按钮提交时，将获得类似如下的结果：

![Image](images/image-120.png)

请注意，你的表单内容已通过浏览器的 URL 地址传输。换句话说，GET 方法将数据作为查询字符串发送在 URL 中，使其易于查看和共享。

然而，重要的是要注意，不建议使用 GET 方法发送敏感数据（如密码），因为该数据在 URL 中可见，可能被第三方拦截。在这种情况下，首选 POST 方法，因为它在 HTTP 请求体中发送数据，可见性较低。

此外，与 POST 方法相比，GET 方法有几个局限性：

**数据大小限制**：通过 GET 方法传输的数据大小受限，因为它包含在 URL 中。这对于大量或敏感数据可能是个问题。

**数据安全性**：由于数据在 URL 中可见，第三方可以轻松拦截和读取。这可能会危及密码或个人信息等敏感数据的安全性。

**特殊字符限制**：URL 中的某些特殊字符必须进行编码，如果处理不当，可能导致错误或数据丢失。

**浏览器缓存**：通过 GET 方法传输的数据可能被浏览器缓存，如果用户共享包含敏感数据的 URL，可能导致机密性问题。

总之，虽然 GET 方法简单易用，适合少量非敏感数据，但在安全性、数据大小和特殊字符处理方面存在显著局限性。对于敏感或大量数据，建议使用 POST 方法。

# 第 8 章：图像和文件

图像和文件操作是现代 Web 开发的重要组成部分。在本章中，我们将重点关注两个主要方面：发送和显示图像及文件，以及在服务器上管理这些文件。

首先，我们将探讨从 HTML 表单向 PHP 服务器发送图像和文件的过程。我们将了解如何在服务器端处理这些数据，检查文件类型和大小，然后将其保存在服务器上。接下来，我们将学习如何在网页中显示这些图像，使用适当的 HTML 标签。

随后，我们将研究服务器端的文件管理。我们将介绍创建、读取、写入和删除文件等常见操作。我们将了解如何操作目录、列出文件以及其他文件管理操作。

本章将带你深入了解 PHP 中的图像和文件操作，为你提供在 Web 应用程序中有效管理多媒体资源和文件所需的知识和技能。

## 发送和显示图像或文件

使用表单发送和显示图像或文件的过程可分为几个阶段：

*   **创建上传表单**：首先，你需要创建一个 HTML 表单，允许用户从其设备选择并上传文件到服务器。你可以使用类型为 "file" 的 `<input>` 标签来创建用于选择文件的表单字段。
*   **表单处理**：用户提交表单后，文件数据被发送到服务器。你随后需要创建 PHP 代码来处理这些数据。此代码可以集成在同一个表单脚本中，也可以位于独立的 PHP 脚本中。该代码必须检查文件是否已正确发送、是否符合你定义的文件大小和类型限制，然后将其保存在服务器上。
*   **在网页上显示图像**：图像发送并保存在服务器上后，你可以使用 HTML 的 `<img>` 标签在网页上显示它。你必须在 `<img>` 标签的 "src" 属性中指定图像的路径。

### 创建发送表单

以下是说明该过程的代码示例：

在 `index.php` 文件中，创建以下表单：

```html
<!DOCTYPE html>
<html lang="en">

<head>

 <meta charset="UTF-8">

 <title>Image submission form</title>

</head>

<body>
```
