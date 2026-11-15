

## 第 15 章：利用 PEAR 让工作更轻松

implode() 在第 6 章中已有解释，关于正则表达式及其替代方案的更多内容可参见第 18 章。

还需要注意回调规则类型的两种用法。username 字段通过调用 checkDuplicateUsername() 函数进行验证（你稍后就会看到）；如果所选用户名是唯一的，该函数返回 true，如果用户名已存在于数据库中，则返回 false。emailAddress 字段的检查方式类似，使用 checkDuplicateEmailAddress() 回调函数：

```
$form->addRule( "username", "A member with that username already exists in the database. Please choose another username.", "callback",
"checkDuplicateUsername" );
$form->addRule( "emailAddress", "A member with that email address already exists in the database. Please choose another email address, or contact the webmaster to retrieve your password.", "callback",
"checkDuplicateEmailAddress" );
```

接下来是刚才描述的两个回调函数。checkDuplicateUsername() 期望传入要检查的用户名。它调用 Member::getByUsername() 尝试检索同名的现有成员。返回值被强制转换为布尔值：如果返回 Member 对象，则强制转换为 true，否则结果为 false。然后使用 !（非）运算符对该值取反，以获得函数返回的正确值：

```
return ! (boolean) Member::getByUsername( $value );
```

checkDuplicateEmailAddress() 的工作方式大致相同，调用 Member::getByEmailAddress() 查找具有相同电子邮件地址的现有成员：

```
return ! (boolean) Member::getByEmailAddress( $value );
```

processForm() 函数比第 14 章中的对应函数简单得多，因为检索和验证提交的表单数据的所有繁重工作已由 HTML_QuickForm 完成。该函数只需获取一个提交的表单字段值关联数组（由 HTML_QuickForm 对象传递给它），添加一个值为 password1 字段的新密码字段，并根据当前日期创建 joinDate 字段。然后将此完整的字段数组传递给 Member 构造函数以创建 Member 对象，再通过调用其 insert() 方法将其添加到数据库中：

```
function processForm( $values ) {
$values[ "password" ] = $values[ "password1" ];
$values[ "joinDate" ] = date( "Y-m-d" );
$member = new Member( $values );
$member->insert();
}
```

得益于使用 HTML_QuickForm 完成大量繁重工作（显示表单、收集和验证提交的数据、报告错误），这个重写的 register.php 脚本优雅且易于阅读。而且，它只有 96 行代码，而原脚本有 127 行。这就是可复用代码的力量！

### 总结

在本章中，你探索了 PEAR，即 PHP 扩展和应用程序库：一个庞大的免费可复用代码集合，你可以将其纳入自己的 PHP 项目中。通过使用 PEAR 包，你的 Web 应用程序构建在预先编写、经同行评审、经过充分测试的代码基础之上，这能节省大量编码和查错时间。

在学习本章过程中，你：

- 研究了 PEAR 包管理器
- 学习了如何安装和删除 PEAR 包，以及如何处理依赖项
- 编写了一个脚本，使用 PEAR Net_UserAgent_Detect 包检测访问者的浏览器和操作系统
- 使用 HTML_Table 包生成斐波那契数字表
- 学习了如何使用强大的 HTML_QuickForm 包生成、处理和验证 Web 表单
- 重写了前一章的注册脚本以使用 HTML_QuickForm，从而得到一个更清晰、更简短且更易于维护的脚本

本章让你领略了 PEAR 的强大与实用。尝试完成以下练习，以便习惯于编写基于 PEAR 的应用程序，别忘了访问 http://pear.php.net/packages.php 的包仓库获取其他想法。你可以在附录 A 中找到这些练习的解答。

在下一章中，你将探索从 PHP 脚本处理外部世界的方式，包括与 Web 服务器通信、发送电子邮件以及处理日期和时间。

### 练习

1. 下载并安装 Numbers_Roman PEAR 包，并使用它编写一个脚本，将 1 到 100 的整数显示为罗马数字。
2. 使用 Numbers_Roman 和 HTML_QuickForm 编写一个罗马数字与阿拉伯数字转换器。用户可以以罗马数字或阿拉伯数字格式输入数字，然后单击“转换”按钮。随后脚本将以替代格式显示该数字。

## PHP 与外部世界

你在这本书中使用过的大多数 PHP 应用程序与外部世界的交互都很有限。通常，Web 浏览器请求一个 URL，运行一个 PHP 脚本，脚本将一些 HTML 标记返回给浏览器。

然而，PHP 所能做的远不止处理浏览器请求和返回 HTML。通过使用各种内置 PHP 函数和变量，PHP 脚本可以了解其运行环境的大量信息，处理不同类型的内容，并与 Web 浏览器以外的实体通信。

在本章中，你将了解 PHP 脚本与外部世界交互的一些常见方式：

- **日期和时间处理：** 许多 PHP 脚本需要处理当前日期和时间，以及操作生日和注册日期等日期。由于日期和时间比较难以处理，PHP 提供了许多日期和时间函数来帮助你

- **使用 HTTP 标头：** PHP 允许你直接访问和操作 HTTP 标头。这样，你的脚本可以从浏览器获取更多信息，还可以执行其他功能，例如 URL 重定向和向浏览器发送非 HTML 内容

- **读取服务器信息：** 通过使用 `$_SERVER` 超全局数组，你的应用程序可以提取关于 Web 服务器和当前运行脚本的各种有用信息

- **发送电子邮件：** PHP 包含内置 `mail()` 函数，让你可以在 PHP 应用程序中撰写和发送电子邮件

学完本章后，你将能够为 PHP 应用程序添加更多有用功能。

### 使用日期和时间

Web 应用程序经常需要处理日期和时间。例如，应用程序可能需要跟踪页面访问时间、处理从 Web 表单输入的日期（如出生日期），或者将 MySQL 数据库返回的日期字段以人性化的方式格式化，以便在 Web 页中显示。

尽管日期和时间乍看之下似乎是处理起来相当简单的概念，但实际上，它们对计算机来说可能相当棘手。闰年、时区以及一个月天数不固定等问题，在存储、检索、比较、添加和减去日期时都可能引发各种问题。

为此，PHP 提供了一些日期和时间相关函数，让你的工作更轻松。

### 了解时间戳

大多数计算机将日期和时间存储为 UNIX 时间戳，或简称时间戳。_时间戳_ 是一个整数，保存的是 1970 年 1 月 1 日午夜 UTC 与要存储的日期和时间（同样为 UTC）之间的秒数。例如，格林尼治标准时间（GMT）“2007 年 2 月 14 日 16:48:12”由 UNIX 时间戳 `1171471692` 表示，因为 2007 年 2 月 14 日 16:48:12 恰好是在 1970 年 1 月 1 日午夜之后的 1,171,471,692 秒。

> UTC 代表协调世界时。在大多数情况下，你可以将其视为格林尼治标准时间（GMT）的等效值。

你可能在想，为什么计算机要以如此奇怪的格式存储日期和时间。事实上，时间戳是表示日期和时间的一种非常有用的方式。首先，因为时间戳只是一个整数，计算机很容易存储它。其次，当日期和时间只是整数时，很容易进行操作。例如，要给时间戳添加一天，只需将一天的秒数（即 86,400 秒）加到该值上即可。不管该时间戳表示的是月末或年末的日期，你都可以通过向时间戳值添加 86,400 秒来添加一天。

绝大多数 PHP 日期和时间函数都使用时间戳——即使不是显式使用，内部肯定也会用到。

### 获取当前日期和时间

计算机（包括 Web 服务器以及你自己的 PC）使用内置时钟记录当前日期和时间。你可以使用 PHP `time()` 函数访问该时钟的值，该函数仅将当前日期和时间作为时间戳返回：

```php
echo time(); // Displays e.g. "1229509316"
```

虽然 `time()` 本身用处不大，但你可以将其与其他 PHP 函数结合使用，来显示当前时间并将日期和时间与当前日期和时间进行比较，等等。

