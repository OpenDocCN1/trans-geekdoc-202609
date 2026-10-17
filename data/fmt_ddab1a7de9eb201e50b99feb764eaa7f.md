
在这种方法中，如果查询字符串包含字母数字以外的任何字符，则将其移除。这种方法可以防止恶意脚本，但它可能会破坏用户的合法输入。

## 第 20 章：编写高质量代码

| 错误级别 | 值 | 描述 |
|---|---|---|
| `E_ERROR` | 1 | 致命运行时错误，无法恢复。脚本将立即停止运行 |
| `E_WARNING` | 2 | 警告（大多数错误都属于此类）。虽然脚本可以继续运行，但已经发生了可能导致后续出现问题的情况（例如除以零或尝试读取不存在的文件） |
| `E_PARSE` | 4 | 脚本无法运行，因为解析时出现问题（例如语法错误） |
| `E_NOTICE` | 8 | 这可能指示一个错误，尽管这种情况也可能发生在正常运行期间 |
| `E_CORE_ERROR` | 16 | PHP 引擎启动期间发生致命错误 |
| `E_CORE_ERROR` | 32 | PHP 引擎启动期间发生非致命错误 |
| `E_COMPILE_ERROR` | 64 | 脚本编译时发生致命错误 |
| `E_COMPILE_WARNING` | 128 | 脚本编译时发生非致命错误 |
| `E_USER_ERROR` | 256 | 与 `E_ERROR` 相同，但由脚本而非 PHP 引擎触发（参见“触发错误”） |
| `E_USER_WARNING` | 512 | 与 `E_WARNING` 相同，但由脚本而非 PHP 引擎触发（参见“触发错误”） |
| `E_USER_NOTICE` | 1024 | 与 `E_NOTICE` 相同，但由脚本而非 PHP 引擎触发（参见“触发错误”） |
| `E_STRICT` | 2048 | 严格不是错误，但在 PHP 遇到可能导致问题或不兼容的代码时触发 |
| `E_RECOVERABLE_ERROR` | 4096 | 虽然错误是致命的，但它没有让 PHP 引擎处于不稳定状态。如果你在使用 PHP 处理器，它可能仍然能够解决问题并继续 |
| `E_DEPRECATED` | 8192 | 关于未来 PHP 版本将无法使用的代码警告 |
| `E_USER_DEPRECATED` | 16384 | 与 `E_DEPRECATED` 相同，但由脚本而非 PHP 引擎触发（参见“触发错误”） |

默认情况下，只有致命错误会导致你的脚本停止运行。然而，你可以通过创建自己的错误处理器（后文章节“让你的脚本处理错误”中描述）来控制不同错误级别下的脚本行为。

## 第三部分：PHP 实践

### 触发错误

尽管 PHP 引擎每当遇到脚本遇到问题时都会触发错误，但你也可以自己触发错误。这可以帮助你的应用程序更加健壮，因为它可以在潜在问题变成严重错误之前将其标记出来。这意味着你可以生成用户友好的错误消息。

要从脚本内部触发错误，请调用 `trigger_error()` 函数，并传入你想要生成的错误消息：

```
trigger_error("Houston, we've had a problem.");
```

默认情况下，`trigger_error()` 抛出 `E_USER_ERROR`，这等同于 `E_NOTICE`（即一个相对轻微的问题）。你可以改用 `E_USER_WARNING`（更严重的问题）或 `E_USER_ERROR`（致命错误——从你的脚本中触发此错误）：

```
trigger_error("Houston, we've had a bigger problem.", E_USER_WARNING);

trigger_error("Houston, we've had a huge problem.", E_USER_ERROR);
```

考虑以下用于计算每天销售小部件数量的函数：

```php
<?php

function calcWidgetsPerDay($totalWidgets, $totalDays) {
    return ($totalWidgets / $totalDays);
}
```

```
echo calcWidgetsPerDay(10, 0);
```

如果传递的 `$totalDays` 为零，PHP 引擎会生成以下错误：

```
PHP Warning: Division by zero in mys.php on line 3
```

这条消息并不直观。考虑以下使用 `trigger_error()` 的版本：

```php
<?php

function calcWidgetsPerDay($totalWidgets, $totalDays) {
    if ($totalDays == 0) {
        trigger_error("calcWidgetsPerDay(): The total days cannot be zero", E_USER_WARNING);
        return false;
    } else {
        return ($totalWidgets / $totalDays);
    }
}
```

```
echo calcWidgetsPerDay(10, 0);
?>
```

现在脚本生成了此错误：

```
PHP Warning: calcWidgetsPerDay(): The total days cannot be zero in mys.php on line 4
```

这使得问题的原因变得清晰得多。更原始的错误触发函数是 `exit()`（以及它的别名 `die()`）。调用此函数会停止脚本，显示错误消息（如果提供了字符串）或返回错误代码（如果提供了整数）。通常情况下，使用 `trigger_error()` 更好，因为它让你能够控制错误是如何处理的。

### 控制错误消息的发送去向

当错误被抛出时，PHP 引擎会将错误消息记录在某处。你可以使用几个配置指令来控制错误消息的记录位置：

- `display_errors`: 这控制是否在浏览器中显示错误消息。设置为 `On` 显示错误，或设置为 `Off` 防止显示错误。由于错误可能包含对黑客有用的信息，你应该在网站上将 `display_errors` 设置为 `Off`。
- `log_errors`: 控制是否将错误消息记录在错误日志中。设置为 `On` 将错误记录到错误日志，或设置为 `Off` 禁用错误日志（如果你将 `display_errors` 和 `log_errors` 都设置为 `Off`，将没有任何错误发生的记录）。
- `error_log`: 指定用于记录错误的日志文件的完整路径。默认通常是系统日志（"syslog"），将消息发送到系统日志记录器（Unix 类型操作系统通常将消息记录在 `/var/log/syslog` 或 `/var/log/system.log` 中；在 Windows 上消息记录在事件日志中）。

如果你有访问 Web 服务器 `php.ini` 文件的权限，你可以在那里设置日志选项——例如：

```
display_errors = Off
```

或者，你可以在应用程序内部使用 `ini_set()` 为该应用程序设置日志选项：

```
ini_set("display_errors", "Off");
```

### 记录你自己的错误消息

除了使用 `trigger_error()` 抛出错误外，你还可以使用 `error_log()` 函数将错误消息记录到系统日志或单独的日志，或者通过电子邮件发送错误消息。

与 `trigger_error()` 不同，调用 `error_log()` 不会导致错误被 PHP 错误处理器（或你创建的自定义处理器）处理，也不会停止脚本运行。它只是将一条日志消息发送到某处。如果你想抛出错误，请使用 `trigger_error()` 而不是 `error_log()`。

`error_log()` 在自定义错误处理器函数内部也有用，如下所示：

要使用 `error_log()`，请传入你想要记录的错误消息调用它：

```
error_log("Houston, we've had a problem.");
```

默认情况下，消息被发送到 PHP 记录器，它通常会将消息添加到系统日志或 Web 服务器的错误日志中（详情请参见“控制错误消息的发送去向”）。如果你想为消息指定不同的目的地，请将整数作为第二个参数。

传递值 `1` 会导致消息通过电子邮件发送。将要发送的电子邮件地址作为第三个参数。你还可以按格式指定额外的标头：

```
error_log("Houston, we've had a problem.", 1, "joe@example.com", "Cc: bill@example.com");
```

传递值 `3` 将消息发送到日志文件：

```
error_log("Houston, we've had a problem.\n", 3, "/home/joe/custom_errors.log");
```

注意 `error_log()` 不会在日志消息末尾添加换行符 `\n`，因此如果你希望消息分行显示，你需要手动添加换行符。

`error_log()` 在记录成功时返回 `true`，如果无法记录错误则返回 `false`。

### 让你的脚本处理错误

为了获得更大的灵活性，你可以创建自己的错误处理器函数来处理脚本运行时的任何错误（无论是通过 PHP 引擎还是通过调用 `trigger_error()` 触发）。你的错误处理器可以检查错误并决定采取什么：它可能会将错误记录到文件或数据库中；向用户显示消息；尝试修复问题并清理变量和数据库连接后退出；或者完全忽略该错误。

要告诉 PHP 使用你自己的错误处理器，调用 `set_error_handler()` 并传入函数名：

```
set_error_handler("myErrorHandler");
```

你可以选择性让你的函数不处理某些类型的错误。要做到这一点，请将掩码作为第二个参数传递。例如，以下代码确保了错误处理器仅在发生 `E_WARNING` 或 `E_NOTICE` 时才被调用（所有其他错误类型都由 PHP 的默认错误处理器处理）：

```
set_error_handler ("myErrorHandler", E_WARNING | E_NOTICE );
```

在下一节“精调错误报告”中，你将学习更多关于在错误级别上使用掩码的知识。

你的错误处理函数至少需要两个参数，如下：

| 参数 | 描述 |
|---|---|
| `errno` | 错误的级别，整数形式。这对应于相应的错误级别常量（`E_ERROR`、`E_WARNING` 等） |
| `errstr` | 字符串形式的错误消息 |

PHP 引擎在调用你的错误处理函数时，会将适当的值传递给这些参数。它还可以额外包含三个可选参数：

| 参数 | 描述 |
|---|---|
| `errfile` | 发生错误的脚本文件的文件名，字符串形式 |
| `errline` | 发生错误的行号，字符串形式 |
| `errcontext` | 包含错误发生时存在的所有变量的数组。用于调试 |

一旦处理完错误，你的错误处理函数应该执行以下三个操作之一：

- 如果必要，则退出脚本（例如，如果你认为该错误是致命的）。你可以通过调用 `exit()` 或 `die()`（或什么都不调用）来实现。如果传递了可选的错误消息或错误代码进行返回
- 返回 `true`（或不返回）。如果你这样做，PHP 的错误处理器将不会被调用，PHP 引擎将尝试从错误发生点之后继续执行
- 返回 `false`。这会导致 PHP 处理器尝试处理该错误。如果你不希望你的错误处理器处理特定的错误，那么这很有用。根据你的错误处理设置，这通常会导致错误被记录。

## 第三部分：在实践中使用 PHP

这里是一个自定义错误处理器的示例。此处理器 `paranoidHandler()` 在发生任何类型的错误时（无论多么微小）都会停止脚本的执行。它还将错误的详细记录到日志 `/home/joe/paranoid_errors.log` 中：

```php
<?php

function calcWidgetsPerDay($totalWidgets, $totalDays) {
    if ($totalDays == 0) {
        trigger_error("calcWidgetsPerDay(): The total days cannot be zero", E_USER_WARNING);
        return false;
    } else {
        return ($totalWidgets / $totalDays);
    }
}

function paranoidHandler($errno, $strstr, $errfile, $errline, $errcontext) {
    $levels = array(
        E_WARNING => "Warning",
        E_NOTICE => "Notice",
        E_USER_ERROR => "Error",
        E_USER_WARNING => "Warning",
        E_USER_NOTICE => "Strict warning",
        E_RECOVERABLE_ERROR => "Recoverable error",
        E_DEPRECATED => "Deprecated feature",
        E_USER_DEPRECATED => "Deprecated feature"
    );

    $message = date("Y-m-d H:i:s") . ": " . $levels[$errno] . ": " . $strstr . " in " . $errfile . " at line " . $errline . "\n";
    $message .= "Variables:\n";
    $message .= print_r($errcontext, true) . "\n";
    error_log($message, 3, "/home/joe/paranoid_errors.log");
    die("There was a problem, so I've stopped. Please try again.");
}

set_error_handler("paranoidHandler");

calcWidgetsPerDay(10, 0);

echo "This will never printed<br />";
?>
```

当该脚本运行时，浏览器中会显示以下消息：

There was a problem, so I've stopped. Please try again.

文件 `/home/joe/paranoid_errors.log` 也包含一条类似下面的消息：

```
2009-03-02 16:46:50 - Warning: calcWidgetsPerDay(): The total days cannot be zero in myscript.php, line 5
Variables:
Array(
    [totalWidgets] => 10
    [totalDays] => 0
)
```

### 精调错误报告

通常，PHP 错误处理器报告（记录）除 `E_NOTICE` 之外的所有错误。你可以通过调用 `error_reporting()` 函数并传递一个代表你想记录的错误级别的掩码来更改此默认设置。

例如，要指定 `E_ERROR`（并忽略所有其他错误），请使用：

```
error_reporting( E_ERROR );
```

要指定多个错误级别，请使用 `|`（位或）运算符将它们连接起来：

```
error_reporting( E_ERROR | E_PARSE );
```

要报告所有错误，请使用特殊常量 `E_ALL`：

```
error_reporting( E_ALL );
```

`E_ALL` 的整数值随着 PHP 版本的增加和错误级别的增加而变化。在 PHP 5.3 中，`E_ALL` 的值为 32767。如果你想指定除特定级别以外的所有错误的错误报告，将该级别与 `E_ALL` 进行异或（XOR）：

```
error_reporting( E_ALL ^ E_USER_NOTICE );
```

要关闭所有类型的错误报告，请传递零值（注意，致命错误仍停止脚本运行）：

```
error_reporting( 0 );
```

由于错误报告级别被存储为配置指令 `error_reporting`，你也可以在 `php.ini` 中或使用 `ini_set()` 设置它，并使用 `ini_get()` 获取其当前值：

```
error_reporting( E_ERROR );
echo ini_get( "error_reporting" ); // 显示 1
```

如果你使用 `set_error_handler()` 指定了自定义错误处理器，无论 `error_reporting` 设置如何，只要发生错误，你的处理器就会被调用。决定记录哪些错误由你的错误处理器来决定。

### 使用异常对象处理错误

虽然 `trigger_error()` 和 `set_error_handler()` 等函数为你触发和处理错误提供了很大的灵活性，但它们也有局限性。例如，如果一段代码调用了一个类方法并在其中发生了错误，如果方法能够简单地通知调用代码错误，而不是通过 `trigger_error()` 抛出错误并通过中央错误处理器，那就好了。调用代码可以采取行动修正问题，使应用程序更健壮。

实现这一点的一种简单方法是让函数或方法返回一个特殊的错误值，例如 `-1` 或 `false`。调用代码可以检查返回值，如果它等于错误值，则知道发生了问题。然而，当开始深度嵌套的函数或方法调用时，这可能会变得非常麻烦，如下代码所示：

```
class Warp {
    public function setWarpFactor($factor) {
