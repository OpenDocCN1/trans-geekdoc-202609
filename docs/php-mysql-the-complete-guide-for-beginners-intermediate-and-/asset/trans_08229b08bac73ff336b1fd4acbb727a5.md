

# 第 101.2 节：跨站脚本攻击 (XSS)

## 问题

跨站脚本攻击是指 Web 客户端非预期地执行远程代码。如果 Web 应用程序接受用户输入并直接将其输出到网页上，则可能会暴露于 XSS 攻击之下。如果输入包含 HTML 或 JavaScript，当 Web 客户端渲染此内容时，远程代码即可被执行。

例如，如果第三方网站包含一个 JavaScript 文件：

![](Image01677.jpg)

而某 PHP 应用程序直接输出传入给它的字符串：

![](Image01678.jpg)

| `<script src = "http://example.com/runme.js"> </script>` |
| --- |

如果未经检查的 GET 参数包含 `>`，则 PHP 脚本的输出将变为：

![](Image01679.jpg)

第三方 JavaScript 将会运行，用户将在网页上看到 "I'm running"（我正在运行）。

## 解决方案

作为一条通用规则，**永远不要信任来自客户端的输入**。每一个 GET、POST 和 Cookie 值都可能是任意内容，因此都应当经过验证。在输出这些值中的任何一个时，请对其进行转义，以免它们以意想不到的方式被解析执行。

请记住，即使在最简单的应用程序中，数据也会被四处移动，很难追踪所有来源。因此，**始终转义输出**是一项最佳实践。

PHP 提供了几种根据上下文转义输出的方法。

### 过滤函数

[PHP 的过滤函数](http://php.net/manual/en/ref.filter.php)允许以[多种方式](http://php.net/manual/en/filter.filters.php)对传入 PHP 脚本的输入数据进行[清理](http://php.net/manual/en/filter.filters.sanitize.php)或[验证](http://php.net/manual/en/filter.filters.validate.php)。它们在保存或输出客户端输入时非常有用。

### HTML 编码

`htmlspecialchars` 会将任何 "HTML 特殊字符" 转换为其 HTML 实体编码，这意味着它们随后不会被作为标准 HTML 处理。使用此方法修复我们之前的示例：

![](Image01680.jpg)

将输出：

![](Image01681.jpg)

```
<div> &lt; script src= &quot; http://example.com/runme.js &quot;&gt;&lt; /script &gt; </div>
```

| `<div>` |
| --- |

`>` 标签内的所有内容将不会被浏览器解释为 JavaScript 标签，而是作为简单的文本节点。用户将安全地看到：

![](Image01682.jpg)

### URL 编码

当输出动态生成的 URL 时，PHP 提供了 `urlencode` 函数以安全地输出有效的 URL。因此，例如，如果用户输入的数据成为另一个 GET 参数的一部分：

![](Image01683.jpg)

任何恶意输入都将被转换为编码后的 URL 参数。

### 使用专业的外部库或 OWASP AntiSamy 列表

有时您可能希望允许发送 HTML 或其他类型的代码输入。您将需要维护一个授权词汇列表（白名单）和一个未授权词汇列表（黑名单）。

您可以从 [OWASP AntiSamy 网站](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) 下载标准列表。每个列表都适用于特定类型的交互（eBay API、tinyMCE 等）。并且它们是开源的。

存在一些库可用于过滤 HTML 并防止一般情况下的 XSS 攻击，其表现至少与 AntiSamy 列表相当，且使用非常简便。例如 [HTML Purifier](http://htmlpurifier.org/)。

# 第 101.3 节：跨站请求伪造

## 问题

| `delete.php?accnt=12` |
| --- |

跨站请求伪造 (CSRF) 可强制最终用户在不知情的情况下向 Web 服务器生成恶意请求。此攻击向量可在 POST 和 GET 请求中均被利用。假设 URL 端点 `/delete.php` 根据 GET 请求的 `accnt` 参数删除账户。现在，如果一位已认证用户在任何其他应用程序中遇到以下脚本：

![](Image01684.jpg)

```
<img src = "http://domain.com/delete.php?accnt=12" width = "0" height = "0" border = "0" >
```

该账户将被删除。

## 解决方案

解决此问题的常用方法是使用 CSRF 令牌。CSRF 令牌被嵌入请求中，以便 Web 应用程序能够信任该请求来自预期来源，且属于应用程序正常工作流的一部分。首先，用户执行某项操作（如查看表单），触发创建一个唯一令牌。

实现此功能的示例表单可能如下所示：

![](Image01685.jpg)

随后，服务器可在表单提交后根据用户会话验证该令牌，从而排除恶意请求。

### 示例代码

以下是基本实现的示例代码：

![](Image01686.jpg)
![](Image01687.jpg)

已有许多库和框架提供了各自的 CSRF 验证实现。虽然这是 CSRF 的简单实现，但您需要编写一些代码以动态重新生成 CSRF 令牌，防止 CSRF 令牌被窃取和固定。

# 第 101.4 节：命令行注入

## 问题

正如 SQL 注入允许攻击者在数据库上执行任意查询一样，命令行注入允许某人在 Web 服务器上运行不受信任的系统命令。如果服务器安全配置不当，这将使攻击者完全控制系统。

假设某脚本允许用户列出 Web 服务器上的目录内容。

![](Image01688.jpg)

（在实际应用中，应使用 PHP 的内置函数或对象来获取路径内容。此示例仅用于简单的安全演示。）

| `tmp`。但由于允许任意输入，路径可能是 `; rm -fr` |
| --- |

人们期望获得的路径参数类似于 `//tmp`。

Web 服务器将执行命令：

![](Image01689.jpg)

并尝试从服务器根目录删除所有文件。

## 解决方案

| `escapeshellarg()` 或 `escapeshellcmd()` |
| --- |

所有命令参数必须使用 `escapeshellarg()` 进行转义。这会使参数变得不可执行。对于每个参数，输入值也应经过验证。

在最简单的情况下，我们可以用以下方式保护示例：

![](Image01690.jpg)
![](Image01691.jpg)

沿用之前尝试删除文件的示例，执行的命令变为：

![](Image01692.jpg)

该字符串仅作为参数传递给 `ls`，而不是终止 `ls` 命令并运行 `rm`。

应注意，上述示例现在虽免受命令注入攻击，但**不**防目录遍历。要修复此问题，应检查规范化路径是否以期望的子目录开头。

PHP 提供了多种执行系统命令的函数，包括 `exec`、`passthru`、`proc_open`、`shell_exec` 和 `system`。所有这些函数的输入都必须经过仔细验证和转义。

# 第 101.5 节：剥离标签

如果您知道如何使用，[`strip_tags`](http://php.net/manual/en/function.strip-tags.php) 是一个非常强大的函数。作为预防跨站脚本攻击的方法，有更好的方法，如字符编码，但在某些情况下剥离标签很有用。

## 基本示例

![](Image01693.jpg)

原始输出：

![](Image01694.jpg)

## 允许标签

| `<b>` |
| --- |

假设您想允许某个特定标签但不允许其他标签，则可在函数的第二个参数中指定。此参数是可选的。在我的示例中，我只希望 `>` 标签被保留通过。

![](Image01695.jpg)

原始输出：

![](Image01696.jpg)

## 注意事项

