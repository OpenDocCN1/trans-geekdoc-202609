

# PHP 核心编程

```php
highlight_file(__FILE__);
?>
```

# 布尔型 highlight_string(string code)

`highlight_string` 函数使用语法高亮将 PHP 代码字符串打印到浏览器。

```php
<?php
// 创建一些代码
$code = "print(\a string\\";
// 高亮示例代码
highlight_string($code);
?>
```

# 字符串 get_html_translation_table (integer table)

使用 `get_html_translation_table` 获取 `htmlentities` 和 `htmlspecialchars` 使用的表。默认情况下返回前者，但如果 `table` 为 1，则返回 `htmlspecialchars` 使用的表。

```php
<?php
$trans = get_html_translation_table(HTML_ENTITIES);
print("<pre>");
var_dump($trans);
print("</pre>\n");
?>
```

# 整数 get_magic_quotes_gpc

`get_magic_quotes_gpc` 函数返回 `magic_quotes_gpc` 指令设置，该设置控制用户提交的数据中哪些引号会被自动转义。

```php
<?php
if(get_magic_quotes_gpc() == 1)
{
    print("magic_quotes_gpc is on");
}
else
{
    print("magic_quotes_gpc is off");
}
?>
```

# 整数 get_magic_quotes_runtime()

`get_magic_quotes_runtime` 函数返回 `magic_quotes runtime` 指令，该指令控制从数据库检索出的的数据中引号是否会被自动转义。你可以使用 `set_magic_quotes_runtime` 来更改其值。

```php
<?
if(get_magic_quotes_runtime() == 1)
{
    print("magic_quotes_runtime is on");
} else
{
    print("magic_quotes_runtime is off");
}
?>
```

# 字符串 get_parent_class(object variable)

`get_parent_class` 函数返回对象的父类名。

```php
<?
class animal
{
    var $name;
}
class dog extends animal
{
    var $owner;
}

$gus = new dog();
$gus->name = "Gus";
// Gus 类型为 dog，dog 的类型是
print($gus->name . " is of type "
get_class($gus) . ",", which is of type ".
get_parent_class($gus) . "BR\n");
?>
```

# 整数 getlastmod()

# PHP 核心编程

`getlastmod` 函数返回执行脚本最后修改的日期。该日期以自 1970 年 1 月 1 日起的秒数形式返回。这与对当前文件调用 `filetime` 相同。

```php
<?php
printf("This script was last modified %s",
    date("m/d/y", getlastmod()));
?>
```

# 整数 getmyinode()

`getmyinode` 函数返回执行脚本的 inode。在 Windows 下，始终返回 0。你可以使用 `fileinode` 获取任何文件的 inode。

```php
<?php
print(getmyinode());
?>
```

# 整数 getmypid()

`getmypid` 函数返回 PHP 引擎的进程标识符。在 Windows 98 下可能不返回任何内容。

```php
<?php
print(getmypid());
?>
```

# 整数 getmyuid()

`getmyuid` 函数返回脚本所有者的用户标识符。

```php
<?php
    print(getmyuid());
?>
```

# 数组 getrusage(integer children)

`getrusage` 函数是同名 C 函数的封装。它报告调用进程所用资源的信息。如果 `children` 参数为 `I`，则使用 `RUSAGE_CHILDREN` 常量调用该函数。你可能需要阅读手册页（man page）以获取更多信息。

```php
<?
// 显示使用的 CPU 时间
$rusage = getrusage(0);
print($rusage["ru utime_tv_sec"] . " seconds used");
?>
```

# 布尔型 headers_sent()

如果 HTTP 头部已发送，`headers_sent` 函数返回 TRUE。头部位于任何内容之前，执行打印语句或在 PHP 标签之外放置文本会导致头部发送。在发送后尝试向栈中添加头部会导致错误。

```php
<?
if(headers_sent())
{
    print("Can't add more headers!BR\n");
} else
{
    header("X-Debug: It's OK to send a header");
}
?>
```

# 布尔型 leak(integer variable)

`leak` 函数故意泄漏内存。它主要用于测试 PHP 自身的垃圾回收例程。如果你在进行压力测试，也可以用它来模拟大量的内存占用。

```php
<?
// 泄漏 8 兆
leak(8388608);
?>
```

# 布尔型 method_exists(object variable, string method)

当指定的方法在指定的对象中存在时，`method_exists` 返回 TRUE。

```php
<?
class animal {
    var $name;
}

class dog extends animal {
    var $owner;
    function speak() {
        print("woof!");
    }
}

$gus = new dog;
$gus->name = "Gus";

if(method_exists($gus, "speak")) {
    $gus->speak();
}
?>
```

# identifier identifier, integer option, integer facility

`openlog` 函数开始连接系统日志并调用 C 的 `openlog` 函数。并不是强制要求在 `syslog` 之前调用 `openlog`，但它可以用于更改 `syslog` 函数的行为。你可能需要参考 `openlog` 的手册页获取更多详情。在 Windows 上，使用了仿真代码来模拟 UNIX 功能。

`identifier` 参数将添加到发送到系统日志的任何消息开头。这通常是正在执行的进程或任务名称。

`option` 参数是一个逻辑或运算符，用于组合选项。表 8.10 列出了所有可用值。在 Windows 下，只有 `LOG_PID` 选项有效。

表 8.10. openlog 选项

| 常量 | 描述 |
| --- | --- |
| LOG_PID | 向每条消息添加进程。 |
| LOG_CONS | 如果消息无法发送到日志，将其发送到系统控制台。 |
| LOG_ODELAY | 延迟记录直到第一次调用 `syslog`。默认为真。 |
| LOG_NDELAY | 立即打开日志。不要等待第一次调用 `syslog`。 |
| LOG_NOWAIT | 不等待子进程。不建议使用此标志。 |
| LOG_PERROR | 也将所有消息记录到 stderr。 |

# PHP 核心编程

`facility` 参数为错误来源设置默认值——即报告来自系统的哪个部分。在 Windows 下会忽略该参数。表 8.11 列出了所有可用的设施。

参见 `syslog` 的用法示例。

表 8.11. openlog 设施

| 常量 | 设施 |
| --- | --- |
| LOG_AUTH | 授权 |
| LOG_AUTHPRIV | 授权权限 |
| LOG_CRON | 定时任务 |
| LOG_DAEMON | 守护进程 |
| LOG_KERN | 内核 |
| LOG_LPR | 打印机 |
| LOG_MAIL | 邮件 |
| LOG_NEWS | 新闻 |
| LOG_SYSLOG | 系统日志 |
| LOG_USER | 用户 |
| LOG_UUCP | UNIX 到 UNIX 协议 |

# phpcredits(integer flags)

`phpcredits` 函数打印关于 PHP 项目主要贡献者的信息。如果遗漏了可选的 `flags` 参数，则将提供所有信息。否则，你可以使用表 8.12 中列出的标志来选择特定的信息集。`PHP_PAGE` 常量会导致感谢被定义 HTML 页面的最小标签包围。

图 8-9. phpcredits。

# PHP 核心编程

![](img/58e6a0f5d6a8a1d4645d8c07b3bf1e3_192_0.png)

```php
// 显示完整感谢
phpcredits();
```

表 8.12. phpcredits 标志
| | |
| CREDITS_FULLPAGE | |
| CREDITS_GENERAL | |
| CREDITS_MODULES | |
| CREDITS_DOCS | |

# 布尔型 phpinfo(integer flags)

`phpinfo` 函数向浏览器发送大量的诊断信息并返回 TRUE。`flags` 参数不是必须的。默认返回所有信息。你可以使用表 8.13 中列出的标志配合按位或运算符来选择特定的信息。

完整的信息集将包含

PHP 版本

Web 服务器的操作系统

编译到 PHP 可执行文件中的扩展

每个配置变量

每个环境变量

如果作为 Apache 模块运行时的 Apache 变量

# HTTP 头部

| 表 8.13. phpcredits 标志 |
|------|
| INFO_GENERAL | |
| INFO_CREDITS | |
| INFO_CONFIGURATION | |
| INFO_MODULES | |
| INFO_ENVIRONMENT | |
| INFO_VARIABLES | |
| INFO_LICENSE | |

调用 `phpinfo` 是了解哪些环境变量可用的好方法。

```php
<?php
phpinfo();
?>
```

# 字符串 phpversion()

`phpversion` 函数返回执行脚本的 PHP 版本的字符串。

```php
<?php
print("PHP version" . phpversion() . "<BR>n");
?>
```

# print_r(expression)

`print_r` 函数打印表达式的值。如果表达式是字符串、整数或双精度浮，则将其简单表示形式发送到浏览器。如果表达式

