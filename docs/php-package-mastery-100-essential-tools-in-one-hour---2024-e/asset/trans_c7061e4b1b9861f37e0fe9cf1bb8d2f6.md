

服务器处理 `example.jpg`，将其调整为 300x200 像素，并将图像直接输出到浏览器。

在这段代码片段中，我们首先引入 Composer 的自动加载文件，使 Glide 库在我们的脚本中可用。我们使用 Glide 的 ServerFactory 创建一个图像处理服务器。create 方法配置了源图像路径和缓存目录路径。PsrResponseFactory 用于生成符合 PSR-7 标准的响应，促进 PHP HTTP 消息实现之间的互操作性。$request 变量表示当前 HTTP 请求，由全局变量创建。$response 变量是一个符合 PSR-7 标准的响应对象实例。我们使用 Glide 服务器的 outputImage 方法处理名为 `example.jpg` 的图像。该方法参数包括图像文件名、图像处理参数数组（本例中设置宽度为 300 像素、高度为 200 像素）以及请求和响应对象。Glide 随后根据这些参数处理图像，并将结果直接发送到浏览器。此示例演示了如何在 PHP 应用程序中使用 Glide 动态处理图像，例如在将图像发送给客户端之前即时调整大小，从而减少预处理或存储多种图片尺寸的需求。

在上述代码示例中，我们首先引入由 Composer 生成的自动加载文件。该自动加载文件负责加载依赖项中的所有必要类，包括 Symfony 的 VarDumper 组件。然后，我们使用 VarDumper::dump() 方法打印数组的可读版本。该数组本身包含字符串和整数的混合，以及一个嵌套的爱好数组。当我们调用 VarDumper::dump($array); 时，它会输出数组的结构化视图，清晰地显示其键、值和结构。这对于开发人员在调试复杂数据结构时极为有用，因为它有助于快速识别变量的内容和结构。

## 28. PsySH

PsySH 是 PHP 的运行时开发者控制台、交互式调试器和 REPL（读取-求值-输出循环）。它允许开发人员在命令行中交互式地执行 PHP 代码，是调试和开发的重要工具。

### 示例：PsySH

```shell
// 这是你需要在终端中运行的命令，不是 PHP 脚本。
// 确保 PsySH 已通过 Composer 全局安装或在你的项目中安装。
// 然后直接输入：
psysh
```

```text
Psy Shell v0.x.x (PHP x.x.x — cli) by Justin Hileman
>>>
```

要使用 PsySH，首先需要确保它已通过 Composer 在系统全局或特定 PHP 项目中安装。安装完成后，你可以在终端中输入 psysh 启动 PsySH shell。

## 29. GuzzleHttp

GuzzleHttp 是一个 PHP HTTP 客户端，使发送 HTTP 请求变得简单，并轻松集成 Web 服务。

### 示例：GuzzleHttp

```php
// 通过 Composer 安装 GuzzleHttp
composer require guzzlehttp/guzzle:~6.0
// 使用 GuzzleHttp 发送 GET 请求的示例 PHP 代码
require 'vendor/autoload.php';
$client = new \GuzzleHttp\Client();
$response = $client->request('GET',
'https://api.github.com/repos/guzzle/guzzle');
echo $response->getStatusCode(); // 200
echo $response->getBody();
```

200

来自 GitHub API 关于 Guzzle 仓库的响应主体。

## 30. PHPMailer

PHPMailer 是一个用于 PHP 的邮件创建和传输类，支持 SMTP 和其他邮件传递方式。

### 示例：PHPMailer

```php
// 通过 Composer 安装 PHPMailer
composer require phpmailer/phpmailer

// 使用 PHPMailer 发送邮件的示例 PHP 代码
require 'vendor/autoload.php';
$mail = new PHPMailer\PHPMailer\PHPMailer();
$mail->isSMTP();
$mail->Host = 'smtp.example.com';
$mail->SMTPAuth = true;
$mail->Username = 'your_email@example.com';
$mail->Password = 'your_password';
$mail->SMTPSecure = 'tls';
$mail->Port = 587;
$mail->setFrom('from@example.com', 'Mailer');
$mail->addAddress('recipient@example.com', 'Recipient Name');
$mail->Subject = 'Here is the subject';
$mail->Body = 'This is the HTML message body **in bold!**';
$mail->AltBody = 'This is the body in plain text for non-HTML mail clients';
if(!$mail->send()) {
    echo 'Message could not be sent.';
    echo 'Mailer Error: ' . $mail->ErrorInfo;
} else {
    echo 'Message has been sent';
}
```

### 消息已发送

此示例演示了 PHPMailer 的使用，这是一个强大的、功能完整的 PHP 脚本发送邮件库。首先，我们使用命令 `composer require phpmailer/phpmailer` 通过 Composer 安装 PHPMailer，该命令会将库及其依赖项下载到我们的项目中。代码片段展示了如何使用 PHPMailer 发送电子邮件。我们首先创建 `PHPMailer\PHPMailer\PHPMailer` 类的实例。然后，我们配置它使用 SMTP 发送邮件，这涉及指定 SMTP 服务器详细信息、身份验证凭据和加密协议（本例中为 TLS）。`setFrom` 方法指定发件人的电子邮件地址和姓名，而 `addAddress` 方法添加收件人。你可以多次调用 `addAddress` 来添加多个收件人。Subject、Body 和 AltBody 属性分别设置邮件的主题、HTML 正文和纯文本正文。纯文本正文用于不支持 HTML 的电子邮件客户端。send 方法尝试发送邮件。如果成功，则返回 true，我们打印确认消息。如果失败，则返回 false，我们打印错误消息以及来自 PHPMailer 的错误信息。此示例突出了 PHPMailer 简化 PHP 中电子邮件发送的能力，包括配置 SMTP 设置、设置邮件内容和处理错误。PHPMailer 还支持许多此处未展示的其他功能，例如附件、自定义标头等。

## 31. Aura.Sql

Aura.Sql 是 PDO 类的扩展，为数据库交互提供高级功能，例如延迟连接、数组引用、查询构建和分析器。它旨在通过为常见任务和查询提供便捷方法来增强 PDO 的使用。

### 示例：Aura.Sql

```php
require 'vendor/autoload.php';
// 为 MySQL 创建一个新的 Aura.Sql 实例。
$pdo = new Aura\Sql\ExtendedPdo('mysql:host=localhost;dbname=test', 'username', 'password');
// 使用数组引用的查询示例
$query = "SELECT * FROM users WHERE id IN (:user_ids)";
$result = $pdo->fetchAll($query, ['user_ids' => [1, 2, 3]]);
echo json_encode($result);
?>
```

来自 "users" 表中 ID 为 1、2 和 3 的用户数据的 JSON 表示。

在上面的示例中，我们首先引入 vendor/autoload.php 文件，该文件由 Composer 生成，用于自动加载依赖项。然后我们使用数据库连接详细信息实例化一个 ExtendedPdo 对象。Aura.Sql 扩展了 PHP 原生的 PDO 类，在保持 PDO 简单性的同时增加了更多功能。fetchAll 方法用于执行 SELECT 查询并获取所有匹配的行。查询包含一个占位符 :user_ids，这是我们想要选择的用户 ID 数组。Aura.Sql 的 ExtendedPdo 类允许我们直接为查询中的占位符传递数组，它将处理数组到适合 SQL 执行的字符串的转换和引用。此功能对于需要基于值列表过滤结果的查询特别有用，避免了手动拼接和引用数组值到 SQL 字符串中。最后，我们使用 json_encode 将结果集转换为 JSON 字符串以进行显示。这是在构建需要返回易于被 JavaScript 和其他语言消费的数据格式的 Web 应用程序或 API 时的常见做法。

