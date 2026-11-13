
要为 PHP 设置指定新值，请使用 `php_value`，后跟来自 `php.ini` 的指令以及新值。`.htaccess` 文件中的以下行将 `max_execution_time` 的新值设置为 60 秒：

```
`php_value max_execution_time 60`
```

**使用 .htaccess** 更改 `php.ini` 和 `.htaccess` 中的配置设置时，请注意语法差异。在 `php.ini` 中，指令名称和值之间必须有等号。在 `.htaccess` 中，值紧跟在指令名称后面，没有等号。

`.htaccess` 中所做的更改仅适用于其所在目录及其子目录。`.htaccess` 中的任何设置都会覆盖全局 `php.ini` 以及父目录中 `.htaccess` 文件中的任何设置。

## 动态配置

您可以使用 `ini_set` 函数即时更改在 `php.ini` 中设置的指令值。它接受两个参数：指令名称和新值。使用 `ini_set` 更改设置时，返回值是该指令的先前设置。

以下示例将当前脚本的 `memory_limit` 设置更改为运行可能比平时需要更多资源的代码部分：

```
$limit = ini_set("memory_limit", "128M");
// Execute code that requires this setting
ini_set("memory_limit", $limit);
```

先前的值保存到变量中，并在密集型代码执行完毕后恢复。

要查找任何 `php.ini` 设置的当前值而不更改它，请使用 `ini_get` 函数。

## 配置指令

本课无法详细介绍 `php.ini` 中的每个配置指令。数量实在太多。但是，在接下来的章节中，您将了解一些最常用设置的工作原理。如需完整参考，请参阅 www.php.net/manual/en/ini.php。

### 配置 PHP 环境

以下章节列出了一些影响 PHP 运行环境的常见配置指令。以下章节中列出的每个指令均附带 PHP 5 发行版 `php.ini` 文件中的默认条目，其中设置了默认值。

### PHP 标记样式

这些指令允许您选择 PHP 脚本中可使用哪些标记样式：

- **short_open_tag = On** `short_open_tag` 指令启用或禁用 `<?` 开始标记的使用。如果关闭此设置，您的脚本必须使用完整的 `<?php` 标记。

由于 `<?` 在嵌入网页时可能有其他含义，您应尽量避免使用 `short_open_tag`，并且在未来的 PHP 版本中，它可能默认被禁用。

- **asp_tags = Off** `asp_tags` 样式的 PHP 标记以 `<%` 开头，以 `%>` 结尾。如果要使用此样式，必须在 `php.ini` 中启用它。

### 系统资源限制

以下指令允许您管理 PHP 脚本可用的系统资源：

- **max_execution_time = 30**；`max_execution_time` 指令指定脚本可以运行的最大总秒数。超过此时间后，将发生错误，脚本执行停止。

除非您有运行缓慢脚本的特定需求而需要更高的值，否则不应更改此值。脚本中的意外无限循环会消耗大量系统资源，而 `max_execution_time` 是防止此类问题的安全措施。

如果网页加载需要 30 秒或更长时间，访问者可能不会等待其完成，除非他们请求的特定信息他们了解可能需要一些时间才能生成。

- **memory_limit = 8M** 每个 PHP 脚本都有内存使用限制，以确保其执行的工作不会失控并以负面方式影响系统。大多数脚本仅使用极少量的内存；要了解具体用量，可以调用 `memory_get_usage` 函数。

`M` 后缀表示兆字节数值；`K` 或 `G` 后缀也可使用，分别表示千字节或千兆字节。如果您确定要完全删除内存限制，可以将 `memory_limit` 设置为 `1`。

## 表单处理

可以使用这些指令更改 PHP 与 Web 表单交互的方式：

- **magic_quotes** `magic_quotes` 设置指示 PHP 自动限定引号，以便它们可以安全地用作字符串值。默认值如下：

```
magic_quotes_gpc = On
magic_quotes_runtime = Off
magic_quotes_sybase = Off
```

`magic_quotes_gpc` 设置适用于从表单发布的数据和 cookie 值中的数据。(`gpc` 代表 `GET`、`POST` 和 `COOKIE` 数据。) `magic_quotes_runtime` 指令告诉 PHP 对脚本生成的数据（例如数据库查询或主机命令）中的引号进行限定。

通常，引号用反斜杠字符限定，但某些数据库（尤其是 Sybase）使用另一个引号字符。启用 `magic_quotes_sybase` 设置后，限定的引号将显示为 `''` 而不是 `\'`。

- **register_globals = Off** 自 PHP 4.2 版本起，`register_globals` 设置默认已禁用。启用后，此选项会导致 PHP 创建包含与超全局变量 `$_ENV`、`$_GET`、`$_POST`、`$_COOKIE` 和 `$_SERVER` 相同信息的全局变量。变量名对应于每个超全局数组中的键名。

- **variables_order = "EGPCS"** `variables_order` 指令确定从超全局变量注册全局变量的顺序。启用 `register_globals` 并使用默认顺序时，名为 `email` 的 cookie 注册时间晚于同名的表单发布值，因此脚本中的 `$email` 包含 cookie 的值。

由于 `register_globals` 创建的值不按来源区分，强烈建议您使用超全局数组；使用超全局数组时，您可以确定 `$_POST["email"]` 是表单提交的值，但 `$email` 可能来自多个来源之一。

- **register_long_arrays = On** 较旧的 PHP 版本使用名为 `$HTTP_GET_VARS`、`$HTTP_POST_VARS`、`$HTTP_SERVER_VARS` 等的数组，而不是较新的超全局数组。`register_long_arrays` 指令决定是否创建带有这些名称的数组。出于向后兼容性，此功能默认保持启用状态。

## 包含文件

可以使用 `include_path` 指令提供一个位置列表，用于查找在 `include` 或 `require` 语句中引用的文件。在 Linux/Unix 系统上，位置用冒号分隔；在 Windows 系统上，用分号分隔。

通常需要确保包含文件存储在 Web 服务器无法直接访问的目录中。以下示例定义了一个包含路径，其中包含与 Web 根目录 /home/chris/public_html 并列的目录：

```
php_value include_path ../home/chris/include
```

句号字符 (.) 用于表示当前工作目录，在此示例中，它的优先级高于定义的包含目录。在这种情况下，如果 include 语句在两个位置都找到匹配文件，将使用工作目录中的文件。这种配置允许您在整个服务器上使用共享库文件，但在必要时可为某些脚本覆盖它们。

`auto_prepend_file` 和 `auto_append_file` 指令允许您指定在每个 PHP 脚本开头和结尾自动添加的文件。给定的文件名在 include_path 中查找，也可以给出文件的完整路径。

`auto_prepend_file` 的常见用法是在脚本输出之前自动包含部分 HTML 布局，以便所有页面看起来一致。由于 `auto_prepend_file` 是 PHP 功能，只有由 PHP 解析的文件才会在前面加上该文件；静态 HTML 页面不会。

![](img/2edc6e6954e3485ad7d94117645931d8_249_0.png)

> **HTTP 标头** 向浏览器发送任何输出后，您就无法使用 header 函数发送 HTTP 标头，也无法使用任何需要发送标头的其他 PHP 函数（例如会话控制函数或 cookie）。因此，如果您想发送自定义 HTTP 标头，则由 auto_prepend_file 包含的任何脚本都不得产生任何输出。

## 错误日志

如在第 22 课“错误处理”中所学，PHP 允许您配置错误报告的严格程度及其报告方式。

`error_reporting` 指令的值是一个位掩码，由第 22 课表 22.1 中的值组成。您可以使用逻辑运算符按如下方式组合值：

```
error_reporting = E_ALL & ~E_NOTICE & ~E_STRICT
```

`display_errors` 和 `log_errors` 指令分别确定错误是写入屏幕显示还是 Web 服务器日志文件。

默认设置如下，错误显示在屏幕上而不写入文件：
