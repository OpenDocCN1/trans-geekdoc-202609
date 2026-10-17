
# 运行时内存使用量

运行时使用的确切内存量可以通过调用 `memory_get_usage()` 来确定。它返回当前正在运行的脚本所分配的内存字节数。自 PHP 5.2 起，它有一个可选的布尔参数，用于获取总分配的系统内存，而不是 PHP 正在活跃使用的内存。

![](img/Image01656.jpg)

| `memory_get_peak_usage` |
| --- |

`memory_get_usage` 给出的是运行那一刻的内存使用量。在对该函数的调用之间，您可能会在内存中分配和释放其他内容。要获取截至某一时刻使用的最大内存量，请调用 `memory_get_peak_usage()`。

![](img/Image01657.jpg)

请注意，该值只会增加或保持不变。

# 第 97.3 节：使用 XHProf 进行性能分析

[XHProf](https://github.com/phacility/xhprof) 是一个 PHP 性能分析器，最初由 Facebook 编写，旨在为 XDebug 提供一个更轻量级的替代方案。

安装 xhprof PHP 模块后，可以从 PHP 代码中启用/禁用性能分析：

![](img/Image01658.jpg)

| `doSlowOperation` |
| --- |

返回的数组将包含有关在 `doSlowOperation()` 内部访问的每个函数的调用次数、CPU 时间和内存使用量的数据。

| `xhprof_sample_enable` | `()` / `xhprof_sample_disable` |
| --- | --- |

`xhprof_sample_enable()` 可用作更轻量级的选项，它仅记录一小部分请求的性能分析信息（且格式不同）。

XHProf 有一些（大多未记录在案的）辅助函数来显示数据（[参见示例](https://github.com/phacility/xhprof/blob/master/examples/sample.php)），或者您可以使用其他工具来可视化它（platform.sh 博客[有一个示例](https://platform.sh/2015/07/29/flamegraphs/)）。

# 第 98 章：多进程处理

## 第 98.1 节：使用内置 fork 函数进行多进程处理

您可以使用内置函数将 PHP 进程作为 fork 运行。如果不需要线程之间相互通信，这是实现并行工作的最简单方法。

这允许您将耗时的任务（如将文件上传到另一台服务器或发送电子邮件）放到另一个线程中，以便您的脚本加载得更快并能利用多核，但请注意，这不是真正的多线程，主线程无法知晓子线程在做什么。

请注意，在 Windows 下，这将为您启动的每个 fork 弹出另一个命令提示符窗口。

**master.php**

![](img/Image01659.jpg)

**worker.php**

![](img/Image01660.jpg)

## 第 98.2 节：使用 fork 创建子进程

PHP 拥有用于创建子进程的内置函数 `pcntl_fork`。`pcntl_fork` 与 Unix 中的 fork 相同。它不接受任何参数，并返回一个整数，可用于区分父进程和子进程。

请参考以下代码进行说明：

![](img/Image01661.jpg)

正如您所见，`-1` 表示 fork 出错，子进程未被创建。子进程创建后，我们有两个具有独立 PID 的进程在运行。

| `pcntl_wait` | `(` | `$status` |
| --- | --- | --- |

此处的另一个考虑因素是僵尸进程或失效进程，即父进程在子进程之前结束。为防止僵尸子进程，只需在父进程末尾添加 `pcntl_wait($status)`。

![](img/Image01662.jpg)

`pcntl_wait` 会挂起父进程的执行，直到子进程退出。

还值得注意的是，僵尸进程无法使用 SIGKILL 信号杀死。

## 第 98.3 节：进程间通信

进程间通信允许程序员在不同进程之间进行通信。例如，假设我们需要编写一个可以运行 bash 命令并打印输出的 PHP 应用程序。我们将使用 `proc_open`，它将执行命令并返回一个可用于通信的资源。以下代码展示了一个从 PHP 在 bash 中运行 `pwd` 的基本实现：

![](img/Image01663.jpg)

`proc_open` 使用 `$descriptor` 作为描述符规范来运行 bash 命令。之后，我们使用 `is_resource` 来验证进程。完成后，我们可以根据描述符规范生成的 `$pipes` 开始与子进程交互。

之后，我们可以简单地使用 `fwrite` 写入子进程的 stdin。在本例中是 `pwd` 后跟回车符。

最后，使用 `stream_get_contents` 读取子进程的 stdout。

![](img/Image01664.jpg)

请始终记得使用 `proc_close()` 关闭子进程，这将终止子进程并返回退出状态码。

# 第 99 章：多线程扩展

## 第 99.1 节：入门

| `pthreads` - ext |
| --- |

要开始多线程编程，您需要 PHP 的 `pthreads` 扩展，可以通过以下方式安装：

![](img/Image01665.jpg)

| `php` | `.` | `ini` |
| --- | --- | --- |

并将条目添加到 `php.ini`。

一个简单的示例：

![](img/Image01666.jpg)

## 第 99.2 节：使用池和工作者

![](img/Image01667.jpg)

池化提供了 Worker 功能的更高层抽象，包括 pthreads 所需方式的引用管理。来源：[`php.net/manual/en/class.pool.php`](http://php.net/manual/en/class.pool.php)

池和工作者提供了更高层级的控制，并简化了多线程的创建。

![](img/Image01668.jpg)

![](img/Image01669.jpg)

# 第 100 章：安全的“记住我”功能

我一直在寻找这个主题，直到发现了 ircmaxell 的这篇帖子 [`stackoverflow.com/a/17266448/4535386`](https://stackoverflow.com/a/17266448/4535386)，我认为它值得更多的关注。

## 第 100.1 节：“保持登录状态” - 最佳方法

存储包含三部分的 cookie。

![](img/Image01670.jpg)

然后，进行验证：

![](img/Image01671.jpg)

# 第 101 章：安全

由于大多数网站运行在 PHP 上，应用程序安全是 PHP 开发人员保护其网站、数据和客户的重要课题。本主题涵盖 PHP 中的最佳安全实践，以及常见漏洞和弱点，并附带 PHP 示例修复方案。

## 第 101.1 节：PHP 版本泄露

默认情况下，PHP 会向外界透露您正在使用的 PHP 版本，例如：

![](img/Image01672.jpg)

要修复此问题，您可以更改 `php.ini`：

![](img/Image01673.jpg)

或者更改 header：

## 第 101.2 节：跨站脚本攻击 (XSS)

### 问题

跨站脚本攻击是指 Web 客户端非预期地执行远程代码。如果 Web 应用程序接受用户输入并直接将其输出到网页上，则可能会暴露于 XSS 攻击之下。如果输入包含 HTML 或 JavaScript，当 Web 客户端渲染此内容时，远程代码即可被执行。

例如，如果第三方网站包含一个 JavaScript 文件：

![](img/Image01677.jpg)

而某 PHP 应用程序直接输出传入给它的字符串：

![](img/Image01678.jpg)

| `<script src = "http://example.com/runme.js"> </script>` |
| --- |

如果未经检查的 GET 参数包含 `>`，则 PHP 脚本的输出将变为：

![](img/Image01679.jpg)

第三方 JavaScript 将会运行，用户将在网页上看到 "I'm running"（我正在运行）。

### 解决方案

作为一条通用规则，**永远不要信任来自客户端的输入**。每一个 GET、POST 和 Cookie 值都可能是任意内容，因此都应当经过验证。在输出这些值中的任何一个时，请对其进行转义，以免它们以意想不到的方式被解析执行。

请记住，即使在最简单的应用程序中，数据也会被四处移动，很难追踪所有来源。因此，**始终转义输出**是一项最佳实践。

PHP 提供了几种根据上下文转义输出的方法。

#### 过滤函数

[PHP 的过滤函数](http://php.net/manual/en/ref.filter.php)允许以[多种方式](http://php.net/manual/en/filter.filters.php)对传入 PHP 脚本的输入数据进行[清理](http://php.net/manual/en/filter.filters.sanitize.php)或[验证](http://php.net/manual/en/filter.filters.validate.php)。它们在保存或输出客户端输入时非常有用。

#### HTML 编码

`htmlspecialchars` 会将任何 "HTML 特殊字符" 转换为其 HTML 实体编码，这意味着它们随后不会被作为标准 HTML 处理。使用此方法修复我们之前的示例：

![](img/Image01680.jpg)

将输出：

![](img/Image01681.jpg)

```
<div> &lt; script src= &quot; http://example.com/runme.js &quot;&gt;&lt; /script &gt; </div>
```

| `<div>` |
| --- |

`>` 标签内的所有内容将不会被浏览器解释为 JavaScript 标签，而是作为简单的文本节点。用户将安全地看到：

![](img/Image01682.jpg)

#### URL 编码

当输出动态生成的 URL 时，PHP 提供了 `urlencode` 函数以安全地输出有效的 URL。因此，例如，如果用户输入的数据成为另一个 GET 参数的一部分：

![](img/Image01683.jpg)

任何恶意输入都将被转换为编码后的 URL 参数。

#### 使用专业的外部库或 OWASP AntiSamy 列表

有时您可能希望允许发送 HTML 或其他类型的代码输入。您将需要维护一个授权词汇列表（白名单）和一个未授权词汇列表（黑名单）。

您可以从 [OWASP AntiSamy 网站](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) 下载标准列表。每个列表都适用于特定类型的交互（eBay API、tinyMCE 等）。并且它们是开源的。

存在一些库可用于过滤 HTML 并防止一般情况下的 XSS 攻击，其表现至少与 AntiSamy 列表相当，且使用非常简便。例如 [HTML Purifier](http://htmlpurifier.org/)。

## 第 101.3 节：跨站请求伪造

### 问题

| `delete.php?accnt=12` |
| --- |

跨站请求伪造 (CSRF) 可强制最终用户在不知情的情况下向 Web 服务器生成恶意请求。此攻击向量可在 POST 和 GET 请求中均被利用。假设 URL 端点 `/delete.php` 根据 GET 请求的 `accnt` 参数删除账户。现在，如果一位已认证用户在任何其他应用程序中遇到以下脚本：

![](img/Image01684.jpg)

```
<img src = "http://domain.com/delete.php?accnt=12" width = "0" height = "0" border = "0" >
```

该账户将被删除。

### 解决方案

解决此问题的常用方法是使用 CSRF 令牌。CSRF 令牌被嵌入请求中，以便 Web 应用程序能够信任该请求来自预期来源，且属于应用程序正常工作流的一部分。首先，用户执行某项操作（如查看表单），触发创建一个唯一令牌。

实现此功能的示例表单可能如下所示：

![](img/Image01685.jpg)

随后，服务器可在表单提交后根据用户会话验证该令牌，从而排除恶意请求。

#### 示例代码

以下是基本实现的示例代码：

![](img/Image01686.jpg)

![](img/Image01687.jpg)

已有许多库和框架提供了各自的 CSRF 验证实现。虽然这是 CSRF 的简单实现，但您需要编写一些代码以动态重新生成 CSRF 令牌，防止 CSRF 令牌被窃取和固定。

## 第 101.4 节：命令行注入

### 问题

正如 SQL 注入允许攻击者在数据库上执行任意查询一样，命令行注入允许某人在 Web 服务器上运行不受信任的系统命令。如果服务器安全配置不当，这将使攻击者完全控制系统。

假设某脚本允许用户列出 Web 服务器上的目录内容。

![](img/Image01688.jpg)

（在实际应用中，应使用 PHP 的内置函数或对象来获取路径内容。此示例仅用于简单的安全演示。）

| `tmp`。但由于允许任意输入，路径可能是 `; rm -fr` |
| --- |

人们期望获得的路径参数类似于 `//tmp`。

Web 服务器将执行命令：

![](img/Image01689.jpg)

并尝试从服务器根目录删除所有文件。

### 解决方案

| `escapeshellarg()` 或 `escapeshellcmd()` |
| --- |

所有命令参数必须使用 `escapeshellarg()` 进行转义。这会使参数变得不可执行。对于每个参数，输入值也应经过验证。

在最简单的情况下，我们可以用以下方式保护示例：

![](img/Image01690.jpg)

![](img/Image01691.jpg)

沿用之前尝试删除文件的示例，执行的命令变为：

![](img/Image01692.jpg)

该字符串仅作为参数传递给 `ls`，而不是终止 `ls` 命令并运行 `rm`。

应注意，上述示例现在虽免受命令注入攻击，但**不**防目录遍历。要修复此问题，应检查规范化路径是否以期望的子目录开头。

PHP 提供了多种执行系统命令的函数，包括 `exec`、`passthru`、`proc_open`、`shell_exec` 和 `system`。所有这些函数的输入都必须经过仔细验证和转义。

## 第 101.5 节：剥离标签

如果您知道如何使用，[`strip_tags`](http://php.net/manual/en/function.strip-tags.php) 是一个非常强大的函数。作为预防跨站脚本攻击的方法，有更好的方法，如字符编码，但在某些情况下剥离标签很有用。

### 基本示例

![](img/Image01693.jpg)

原始输出：

![](img/Image01694.jpg)

### 允许标签

| `<b>` |
| --- |

假设您想允许某个特定标签但不允许其他标签，则可在函数的第二个参数中指定。此参数是可选的。在我的示例中，我只希望 `>` 标签被保留通过。

![](img/Image01695.jpg)

原始输出：

![](img/Image01696.jpg)

#### 注意事项

##### HTML 注释和 PHP 标签

HTML 注释和 PHP 标签也会被剥离。这是硬编码的，无法通过 `allowable_tags` 更改。

| `<br>` | `>` | `<br/>` |
| --- | --- | --- |

在 PHP 5.3.4 及更高版本中，自闭合 XHTML 标签会被忽略，因此在 `allowable_tags` 中应仅使用非自闭合标签。例如，要同时允许 `<br>` 和 `<br/>`，应使用：

```
allowable_tags = "<br><br/>"
```

## 第 101.6 节：文件包含

### 远程文件包含

远程文件包含（也称为 RFI）是一种允许攻击者包含远程文件的漏洞类型。

此示例注入了一个包含恶意代码的远程托管文件：

```
include($_GET['file']);
```

### 本地文件包含

本地文件包含（也称为 LFI）是通过 Web 浏览器在服务器上包含文件的过程。

```
include("includes/" . $_GET['page'] . ".php");
```

### RFI 和 LFI 的解决方案

建议仅允许包含你批准的文件，并仅限于这些文件。

```
$allowed = array('page1', 'page2', 'page3');
if (in_array($_GET['page'], $allowed)) {
    include($_GET['page'] . '.php');
}
```

## 第 101.7 节：错误报告

默认情况下，如果脚本中发生意外情况，PHP 会直接在页面上输出错误、警告和通知消息。这对于解决脚本的特定问题很有用，但同时也会输出你不想让用户知道的信息。

因此，在生产环境中，避免显示那些会泄露服务器信息（例如目录树）的消息是一种良好的实践。在开发或测试环境中，这些消息可能仍然有利于显示以进行调试。

### 快速解决方案

你可以将它们关闭，使消息完全不显示，但这会使调试脚本变得更难。

```
ini_set('display_errors', 0);
```

或直接在 `php.ini` 中更改它们：

```
display_errors = 0
```

### 错误处理

一个更好的选择是将这些错误消息存储在一个更有用的地方，比如数据库：
