
*   `month`：当前月份的全称（例如 "February"）
*   `0`：表示当前日期的 Unix 时间戳

这些元素提供了当前日期和时间的精确细节。

*   PHP 的 `time()` 函数返回自 1970 年 1 月 1 日午夜 UTC（Unix 时间）以来经过的秒数。它不接受任何参数。

示例：

```php
$current_time = time();
echo "The time in seconds since the Unix epoch: $current_time";
```

运行此代码将返回自 01/01/1970 以来的当前时间（以秒为单位）：

![Image](images/image-111.png)

此函数常用于测量持续时间、计算时间间隔或进行其他基于时间的操作。

*   PHP 中的 **`strtotime()` 函数** 用于将文本日期解析为 Unix 时间戳值，表示自 1970 年 1 月 1 日 00:00:00 UTC（Unix 时间）以来经过的秒数。以下是其用法的一些示例：

```php
$date_text = "2023-08-29";
$timestamp = strtotime($date_text);
echo "The timestamp for the date $date_text is: $timestamp";
```

此代码将产生类似以下的结果：

![Image](images/image-112.png)

计算两个特定日期之间时间的示例：

您可以使用 `strtotime()` 函数获取这些日期的时间戳，然后减去相应的时间戳以获得以秒为单位的差值。然后您可以根据需要将此差值转换为天、小时、分钟等。

以下是计算 02/15/1996 和 08/29/2024 之间持续时间的示例：

```php
// 开始日期的时间戳 (02/15/1996 00:00:00)
$departure_date = strtotime("1996-02-15");
// 到达日期的时间戳 (29/08/2024 00:00:00)
$arrival_date = strtotime("2024-08-29");
// 计算以秒为单位的差值
$difference_seconds = $arrival_date - $departure_date;
// 显示以秒为单位的持续时间
echo "Duration in seconds between 02-15-1996 and 08-29-2024: $difference_seconds";
```

此代码将产生类似以下的结果：

![Image](images/image-113.png)

## 结论

重要的是要注意，PHP 提供了大量预定义函数来完成多种任务，从数学运算和字符串操作到数组操作以及日期/时间管理等。要在一本书中详尽涵盖所有这些函数是不可能的。

本章的目的是为您提供 PHP 内置不同函数类别的代表性示例，以便您了解它们的基本用法和操作。必须注意的是，目的不是让您死记硬背所有函数，而是让您熟悉它们的存在和实用性。

作为开发人员，培养在需要使用特定函数时搜索和查阅 PHP 官方文档或其他在线资源的能力至关重要。这是软件开发过程不可或缺的一部分，将使您能够自行探索 PHP 语言提供的特性和可能性。

# B 部分

# 高级数据管理与浏览器交互

在本部分中，我们将探讨数据操作和浏览器交互的高级方面。我们将深入研究高级技术，使您能够创建更动态、更具交互性的 Web 应用程序。

**第 7 章**：本章我们将介绍使用 GET 和 POST 方法处理来自浏览器的数据。我们将学习如何从表单检索数据，并在 PHP 脚本中使用这些数据，以在 Web 应用程序中创建交互功能。

**第 8 章：** 图像与文件：本章重点介绍 Web 应用程序中图像和文件等多媒体资源的管理。它探讨了在服务器端存储、加载和操作图像及文件的最佳实践。

**第 9 章：** 会话与 Cookie 管理：本章探讨 Web 应用程序中用户会话状态的管理机制。它详细介绍了使用 Cookie 存储客户端信息，以及服务器端会话管理技术。

# 第 7 章

# 浏览器数据处理 (GET, POST)

到目前为止，我们已经探讨了许多构成我们未来学习基础的基本概念。如果这是您第一次涉足服务端编程，起初感到有些迷茫是正常的。您也可能无法完全掌握变量、条件、循环、函数、数组等的用处。这是可以理解的，因为到目前为止，我们主要使用的是自己定义的值。换句话说，在示例中，我们用预定值初始化了变量。

然而，在后续课程中，我们将使用那些我们不预先自行定义值的变量。例如，我们将学习如何检索用户通过表单输入的信息，届时您将完全理解我们迄今所学内容的重要性。

本书的这一章重点介绍来自浏览器的数据处理，特别强调 GET 和 POST 方法。当我们与网站交互时，经常会传输信息，如表单参数或 URL 标识符。这些数据对于个性化用户体验、执行搜索或管理用户会话等至关重要。

本章将为您提供在 PHP 项目中有效操作浏览器数据所需的知识，为创建更动态、更具交互性的 Web 应用程序铺平道路。

## 在 PHP 中传输和处理表单数据

要检索用户在表单中输入的数据，主要有两种方法：

第一种方法是创建两个单独的文件：一个包含表单的 HTML 文件，和一个负责处理该表单提交数据的 PHP 文件。

第二种方法是将 HTML 表单代码和 PHP 处理代码结合在一个 PHP 文件中。

最初，我们将专注于第一种配置，即使用两个单独的文件。第一个文件（例如命名为 `form.php`）将包含表单，而第二个文件（例如命名为 `processingform.php`）将负责处理该表单传输的数据。

![Image](images/image-114.png)

在 `ebbokphp` 目录中，创建这两个文件：

![Image](images/image-115.png)

### 创建表单

让我们在 `form.php` 文件中创建一个表单：

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Form </title>
</head>
<body>
<form action="processingform.php" method="post">
 <fieldset>
 <legend>Personal information:</legend>
 <label for="lastname">Last Name:</label><br>
 <input type="text" id="lastname" name="lastname"><br>
 <label for="firstname">First Name:</label><br>
 <input type="text" id="firstname" name="firstname"><br>
 <label for="email">Email address:</label><br>
 <input type="email" id="email" name="email"><br>
 <label for="country">Country:</label><br>
 <select id="country" name="country">
 <option value="France">France</option>
 <option value="Morocco">Morocco</option>
 <option value="Spain">Spain</option>
 <option value="Canada">Canada</option>
 <option value="Belgium">Belgium</option>
 </select><br><br>
 <input type="submit" value="Send">
 </fieldset>
 </form>
</body>
</html>
```

该表单设计了一个标题为 "Personal information" 的 `fieldset`，并包含以下字段："Last name"、"First name"、"Email address" 和 "Country"。

**Input** 字段是用于输入用户数据的表单元素。`type` 属性定义字段类型，例如 "text" 用于 "Last name" 和 "First name" 等文本字段，"email" 用于电子邮件地址字段。`id` 属性用于关联相应的标签，而 `name` 属性对于在表单提交时识别字段数据至关重要。

