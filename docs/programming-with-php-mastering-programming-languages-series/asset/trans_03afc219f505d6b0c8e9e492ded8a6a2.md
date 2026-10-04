

## 读取和操作 PHP Cookie

进入 PHP 读取 Cookie 时，通过 `$_COOKIE` 超全局数组访问。这允许你检索存储在 Cookie 中的数据：

```php
$username = $_COOKIE['username'];
```

### 更新和删除 Cookie

Cookie 可以通过再次设置新值来更新。要删除 Cookie，可以将其过期时间设置为过去的日期，从而使其无效：

```php
setcookie('username', '', time() - 3600, '/');
```

### 使用场景

Cookie 通常用于记住登录会话、存储用户偏好以及跟踪用户行为以进行分析。它们提供了一种在不同用户访问之间持久化数据的手段。

### 安全注意事项

虽然 Cookie 很有用，但如果处理不当也会带来安全风险。开发人员必须谨慎对待在 Cookie 中存储敏感信息，并实施安全措施以防止会话劫持或跨站脚本 `XSS` 攻击等潜在威胁。

理解如何在 PHP 中创建和管理 Cookie 对于构建交互式且用户友好的 Web 应用程序至关重要。Cookie 使开发人员能够增强用户体验、保留用户偏好并提供个性化内容，最终使网站更具吸引力和动态性。

## 安全的会话和 Cookie 处理实践

会话管理和 Cookie 处理是 Web 开发的关键方面，必须遵循安全实践来保护用户数据并确保应用程序的完整性。在 PHP 的上下文中，以下是保护会话和 Cookie 的最佳实践：

### 使用 HTTPS

始终使用 HTTPS 来加密客户端和服务器之间传输的数据。这确保会话数据和 Cookie 在传输过程中保持机密。

```php
// Force HTTPS in PHP
if ($_SERVER["HTTPS"] != "on") {
    header("Location: https://" . $_SERVER["HTTP_HOST"] . $_SERVER["REQUEST_URI"]);
    exit();
}
```

### 设置 Secure 和 HTTP-only 标志

创建 Cookie 时，设置 `secure` 标志以确保它们仅通过安全连接传输，并设置 `HTTP-only` 标志以防止 JavaScript 访问。这降低了跨站脚本 `XSS` 攻击的风险。

```php
setcookie('session_id', $sessionId, time() + 3600, '/', '', true, true);
```

### 实现会话再生

定期再生会话 ID 以减轻会话固定攻击。这可以使用 `session_regenerate_id()` 函数完成。

```php
session_regenerate_id(true);
```

### 验证用户输入

始终验证和清理用户输入，以防止恶意数据存储在会话或 Cookie 中。使用 `filter_input()` 和 `htmlspecialchars()` 等函数。

```php
$username = filter_input(INPUT_POST, 'username', FILTER_SANITIZE_STRING);
```

### 使用安全存储

在服务器上安全存储会话数据和 Cookie。避免将敏感信息存储在客户端 Cookie 中。

### 定期审查和更新

保持 PHP 环境和库为最新状态，以解决可能随时间出现的任何安全漏洞。

通过遵循这些安全的会话和 Cookie 处理实践，你可以保护应用程序和用户数据免受常见的 Web 安全威胁，确保更安全、更可靠的用户体验。

## Module 19: Introduction to PHP Functions and Libraries

### Streamlining Code for Efficiency with PHP Functions and Libraries

在课程 "Programming with PHP" 中，模块 "Introduction to PHP Functions and Libraries" 代表你成为熟练 PHP 开发人员之旅中的关键一步。本模块让你沉浸在函数和库的世界中，使你能够在 PHP 应用程序中创建模块化、高效且可重用的代码。

#### The Role of Functions

函数是代码模块化的构建块，允许你将特定任务或操作封装为可重用单元。在本模块中，你将探索 PHP 中函数的重要性，了解如何定义、声明和调用它们。函数有助于简化你的代码、提高其可读性并增强其可维护性。

#### Leveraging PHP Libraries

除了函数之外，你还将深入 PHP 库的世界。这些是预写函数和类的集合，扩展了 PHP 的功能并为常见任务提供现成解决方案。你将学习如何在项目中集成和使用库，节省宝贵的开发时间和精力。

#### Creating Efficient and Maintainable Code

能够使用函数和库是创建高效、可维护和可重用代码的关键。通过掌握本模块，你将具备开发不仅功能齐全而且结构良好且易于维护的 PHP 应用程序的能力。函数和库帮助你模块化代码库、促进代码重用并减少冗余。

#### Elevating Your Code Efficiency

当你开始本模块时，你将对 PHP 中的函数和库获得深刻理解，这些是优化 PHP 开发的基本要素。"Introduction to PHP Functions and Libraries" 成为增强你的 PHP 开发技能并创建在效率和模块化方面出色的应用程序的门户。加入我们，踏上这一变革之旅，探索 PHP 函数和库的世界，释放代码优化和重用的全部潜力。

## 使用内置 PHP 函数：strlen, strpos 等

在 PHP 中，内置函数是简化常见编程任务并增强代码可重用的强大工具。本节介绍一些在 Web 开发和数据操作中常用的基本 PHP 函数，包括 `strlen` 和 `strpos`。

### strlen - String Length

`strlen` 函数用于确定给定字符串的长度（字符数）。它对于验证输入长度或截断文本等任务特别有用。

```php
$text = "Hello, world!";
$length = strlen($text); // $length is now 13
```

### strpos - String Position

`strpos` 函数帮助你在字符串中查找子字符串的位置。它返回子字符串首次出现的索引，如果未找到则返回 `false`。

```php
$text = "The quick brown fox";
$position = strpos($text, "brown"); // $position is now 10
```

### str_replace - String Replacement

`str_replace` 允许你在给定文本中将子字符串的出现替换为另一个字符串。它对于执行文本替换和转换非常方便。

```php
$text = "I love PHP programming!";
$newText = str_replace("PHP", "JavaScript", $text);
// $newText is now "I love JavaScript programming!"
```

### ucwords - Uppercase Words

`ucwords` 将字符串中每个单词的首字母大写。它通常用于格式化名称或标题。

```php
$text = "john doe";
$formattedText = ucwords($text); // $formattedText is now "John Doe"
```

这些只是众多内置 PHP 函数中的几个示例。利用这些函数可以显著简化你的代码并使其更高效。了解何时以及如何使用它们是任何 PHP 开发人员的宝贵技能。

## 创建自定义 PHP 函数

在 PHP 中，自定义函数对于封装可重用代码块、促进代码组织和提高可维护性至关重要。本节探讨自定义 PHP 函数的创建，使你能够构建模块化和高效的代码。

### Function Declaration

要创建自定义函数，使用 `function` 关键字，后跟函数名和用于参数的括号（如有），然后用大括号括起函数的代码。

```php
function greet($name) {
    echo "Hello, $name!";
}
```

### Function Invocation

定义后，你可以通过使用其名称并传递所需参数来调用自定义函数。这促进了代码重用和可读性。

```php
greet("Alice"); // Output: Hello, Alice!
greet("Bob");   // Output: Hello, Bob!
```

### Return Values

函数可以使用 `return` 语句返回值。这允许你捕获和使用函数调用的结果。

```php
function add($a, $b) {
```
