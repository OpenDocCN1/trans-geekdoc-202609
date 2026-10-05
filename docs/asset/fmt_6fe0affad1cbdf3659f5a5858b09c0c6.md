
```php
// Example PHP code for JWT token-based authentication

require 'vendor/autoload.php'; // 引入 JWT 库

use Firebase\JWT\JWT;

$key = 'your-secret-key'; // 用于签名 JWT 的密钥

$token = null;

$headers = apache_request_headers();

if (isset($headers['Authorization'])) {
    $matches = [];

    if (preg_match('/Bearer (.+)/', $headers['Authorization'], $matches)) {
        $token = $matches[1];
    }
}

if (!$token) {
    http_response_code(401);
    echo json_encode(['error' => 'Unauthorized']);
    exit;
}

try {
    $decoded = JWT::decode($token, $key, ['HS256']);
    // 令牌有效且 $decoded 包含用户信息
} catch (Exception $e) {
    http_response_code(401);
    echo json_encode(['error' => 'Token is invalid']);
    exit;
}
```

### 授权 (Authorization)

授权决定了客户端可以在你的 API 资源上执行的操作。它是关于根据客户端的身份和权限控制对特定端点或数据的访问。

授权的一种常用方法是基于角色的访问控制 (RBAC)。在 RBAC 中，用户或客户端被分配角色，每个角色拥有一组关联权限。例如，你可能有“管理员（admin）”、“用户（user）”和“访客（guest）”等角色。管理员可以执行所有操作，用户拥有有限的权限，而访客的权限受到严格限制。

这里是一个 PHP 中 RBAC 的简化示例：

```php
// Example PHP code for role-based authorization

function checkPermission($userRole, $requiredPermission) {
    $roles = [
        'admin' => ['create', 'read', 'update', 'delete'],
        'user' => ['read'],
        'guest' => [],
    ];
    if (in_array($requiredPermission, $roles[$userRole])) {
        return true; // 用户有权限
    }
    return false; // 用户没有权限
}

$userRole = 'user'; // 获取用户的角色
if (checkPermission($userRole, 'read')) {
    // 用户被授权读取
} else {
    http_response_code(403);
    echo json_encode(['error' => 'Access denied']);
    exit;
}
```

在你的 API 中同时实现认证（authentication）和授权（authorization）至关重要，以确保只有经过授权的用户才能访问特定资源并执行某些操作。这些安全措施有助于保护你的 API 及其数据免受未经的访问和滥用。

---

## 第 15.5 节：API 文档与测试

在本节中，我们将讨论在使用 PHP 构建 RESTful API 时，API 文档和测试的重要性。良好的文档和充分的测试是维护成功且开发者友好 API 的关键方面。

### API 文档

API 文档为使用你 API 的开发者提供了参考和指南。它提供了有关可用端点、请求和响应格式、认证方法、错误处理和用法示例的详细信息。文档良好的 API 更于开发者理解并将其集成到应用程序中。

#### API 文档工具

有多种工具可以根据你的 PHP 代码和注解自动生成 API 文档。一个流行的选择是 [Swagger](https://swagger.io/)，它允许你使用 JSON 或 YAML 文件描述你的 API。随后 Swagger UI 可以根据此描述生成交互式文档。

另一个工具是 [API Blueprint](https://apiblueprint.org/)，它使用类似 Markdown 的格式来描述你的 API。你可以使用 Aglio 等工具从 API Blueprint 文件生成 HTML 文档。

这里是一个使用 Swagger 的 API 文档示例：

```yaml
swagger: "2.0"
info:
  version: "1.0.0"
  title: "Sample API"
paths:
  /users:
    get:
      summary: "获取用户列表"
      responses:
        200:
          description: "成功响应"
```

### API 测试

测试你的 API 对于确保其正确性、可靠性和安全性至关重要。它涉及向你的 API 端点发送请求并验证它们是否产生了预期的结果。测试有助于在开发早期识别并修复问题，减少 bug 进入生产环境的风险。

#### API 测试类型

1. **单元测试 (Unit Testing)**：单元测试专注于孤立测试 API 的单个组件或函数。你可以使用针对 PHP 的 PHPUnit 等测试框架为 API 的函数和方法编写单元测试。

2. **集成测试 (Integration Testing)**：集成测试检查你的 API 的不同部分如何协同工作。它们验证了你的 API 端点、数据库交互和外部服务的集成是否运行正常。

3. **功能测试 (Functional Testing)**：功能测试确保你的 API 从终端用户的角度行为符合预期。这些测试向你的 API 端点发送 HTTP 请求，并根据预期结果验证响应。

4. **负载测试 (Load Testing)**：负载测试评估你的 API 在高流量和高负载下的性能。Apache JMeter 或 Gatling 等工具可以进行此类测试。

良好的文档和测试不仅让你的 API 用户受益，也有助于其长期维护。

---

# 第 16 章：PHP 与邮件处理

## 16.1 节：使用 PHP 发送邮件

通过编程发送电子邮件是 Web 开发中的常见任务。PHP 提供了内置函数和库来轻松发送邮件。在本节中，我们将探索如何使用 PHP 发送邮件。

### 发送简单邮件

要使用 PHP 发送基础邮件，可以使用 `mail()` 函数。这里是一个示例：

```php
$to = "recipient@example.com";
$subject = "Hello, World!";
$message = "这是一封通过 PHP 发送的测试邮件。";
// 额外的头
$headers = "From: sender@example.com\r\n";
$headers .= "Reply-To: sender@example.com\r\n";
$headers .= "CC: cc@example.com\r\n";
$headers .= "BCC: bcc@example.com\r\n";
// 发送邮件
$mailSent = mail($to, $subject, $message, $headers);

if ($mailSent) {
    echo "邮件发送成功。";
} else {
    echo "邮件发送失败。";
}
```

在示例中，我们指定了收件者邮箱地址、邮件主题、消息主体以及额外的头部。`mail()` 函数发送邮件，并检查是否发送成功。

### 发送 HTML 邮件

你可以使用 PHP 发送 HTML 格式的邮件以创建丰富的邮件内容。这里是一个示例：

```php
$to = "recipient@example.com";
$subject = "HTML 邮件示例";
// HTML 消息
$message = "<html><body>";
$message .= "<h1>你好，世界！</h1>";
$message .= "<p>这是一封通过 PHP 发送的 HTML 邮件。</p>";
$message .= "</body></html>";
// 针对 HTML 内容额外头部
$headers = "MIME-Version: 1.0\r\n";
$headers .= "Content-type: text/html; charset=utf-8\r\n";
$headers .= "From: sender@example.com\r\n";
// 发送 HTML 邮件
$mailSent = mail($to, $subject, $message, $headers);

if ($mailSent) {
    echo "HTML 邮件发送成功。";
} else {
    echo "HTML 邮件发送失败。";
}
```

在本示例中，我们将 `Content-type` 头部设置为 HTML 以指示邮件包含 HTML 内容。`message` 变量包含 HTML 内容，我们像以前一样使用 `mail()` 函数。

### 发送附件

PHP 允许你发送邮件附件。你可以结合 `mail()` 函数与 `PHPMailer` 等其他库来发送发送带附件的邮件。这是一个基础示例：

```php
use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\Exception;

require 'vendor/autoload.php';

// 创建 PHPMailer 实例
$mail = new PHPMailer(true);

try {
    // 服务器设置
    $mail->isSMTP();
    $mail->Host = 'smtp.example.com';
    $mail->SMTPAuth = true;
    $mail->Username = 'your_username';
    $mail->Password = 'your_password';
    $mail->SMTPSecure = 'tls';
    $mail->Port = 587;

    // 收件者
    $mail->setFrom('sender@example.com', 'Sender Name');
    $mail->addAddress('recipient@example.com', 'Recipient Name');

    // 附件
    $mail->addAttachment('path/to/attachment.pdf', 'Attachment.pdf');

    // 内容
    $mail->isHTML(true);
    $mail->Subject = 'Email with Attachment';
    $mail->Body = 'Please find the attachment.';
    $mail->send();
    echo 'Email sent successfully.';
} catch (Exception $e) {
    echo 'Email sending failed: ' . $mail->ErrorInfo;
}
```

在本示例中，我们使用 `PHPMailer` 库发送带附件的邮件。你需要配置 SMTP 设置并提供附件。使用 PHP 发送邮件是 Web 应用程序的一项关键功能，用于与用户通信、发送通知等。无论你需要发送纯文本还是 HTML 格式的带附件邮件，PHP 都提供了有效完成此任务的工具。

在处理 Web 应用程序中的邮件时，发送邮件附件是一个常见需求。PHP 提供了相对简单的库和函数。在本节中，我们将探索如何使用 PHP 将文件附加到邮件中。

### 使用 `mail()` 函数附加文件

你可以使用 PHP `mail()` 函数将文件附加到邮件。为了实现这一点，你需要设置额外的头部来指定附件属性。这是一个示例：

```php
$to = "recipient@example.com";
$subject = "Email with Attachment";
$message = "Please find the attachment.";

// 文件附件
$file_path = "path/to/attachment.pdf";
$file_name = "Attachment.pdf";
$file_data = file_get_contents($file_path);
$file_encoded = chunk_split(base64_encode($file_data));

// 额外头部
$headers = "From: sender@example.com\n";
$headers .= "MIME-Version: 1.0\n";
$headers .= "Content-Type: multipart/mixed; boundary=\"boundary\"\n";

// 消息
$email_message = "--boundary\n";
$email_message .= "Content-Type: text/plain; charset=\"utf-8\"\n";
$email_message .= "Content-Transfer-Encoding: 7bit\n\n";
$email_message .= $message . "\n";
$email_message .= "--boundary\n";
$email_message .= "Content-Type: application/pdf; name=\"$file_name\"\n";
$email_message .= "Content-Transfer-Encoding: base64\n";
$email_message .= "Content-Disposition: attachment; filename=\"$file_name\"\n\n";
$email_message .= $file_encoded;
$email_message .= "--boundary--";

// 发送邮件
$mailSent = mail($to, $subject, $email_message, $headers);

if ($mailSent) {
    echo "Email with attachment sent successfully.";
} else {
    echo "Email with attachment failed.";
}
```

在本示例中，我们首先读取要附加的文件（`attachment.pdf`）并使用 `base64` 对内容进行编码。然后设置相应的头部以指示邮件包含附件。最后，我们构建包含附件的邮件并使用 `mail()` 函数发送它。

### 使用 PHPMailer 处理附件

在 PHP 中处理附件的更方便的方法是使用 `PHPMailer` 等库。以下是使用 `PHPMailer` 附加文件的基础示例：

```php
use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\Exception;

require 'vendor/autoload.php';

// 创建 PHPMailer 实例
$mail = new PHPMailer(true);

try {
    // 服务器设置
    $mail->isSMTP();
    $mail->Host = 'smtp.example.com';
    $mail->SMTPAuth = true;
    $mail->Username = 'your_username';
    $mail->Password = 'your_password';
    $mail->SMTPSecure = 'tls';
    $mail->Port = 587;

    // 收件者
    $mail->setFrom('sender@example.com', 'Sender Name');
    $mail->addAddress('recipient@example.com', 'Recipient Name');

    // 附件
    $mail->addAttachment('path/to/attachment.pdf', 'Attachment.pdf');

    // 内容
    $mail->isHTML(true);
    $mail->Subject = 'Email with Attachment';
    $mail->Body = 'Please find the attachment.';
    $mail->send();
    echo 'Email with attachment sent successfully.';
} catch (Exception $e) {
    echo 'Email sending attachment failed: ' . $mail->ErrorInfo;
}
```

在本示例中，我们使用 `PHPMailer` 发送带附件的邮件。`PHPMailer` 简化了将文件附加到邮件的过程，并为邮件处理提供了更高级的功能。处理邮件附件是 Web 应用程序通过邮件发送文件和文档的关键方面。无论你选择使用内置的 `mail()` 函数还是 `PHPMailer` 等库，PHP 都提供了高效处理附件的活性。

---

## 16.3 节：PHP 邮件库和框架
