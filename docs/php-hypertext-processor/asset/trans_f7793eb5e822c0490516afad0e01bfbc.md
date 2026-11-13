

## AddModule

你必须取消注释此行才能使用 Apache 的静态模块版本。

```
AddModule mod_php4.c
```

## PHP.INI file Configuration

PHP 配置文件 php.ini 是影响 PHP 功能的最终且最直接的方法。每次初始化 PHP 时都会读取 php.ini 文件。换句话说，对于模块版本，每当重新启动 httpd 时；对于 CGI 版本，则在每次脚本执行时读取。如果您的更改没有显示出来，请记住停止并重新启动 httpd。如果仍然没有显示出来，请使用 phpinfo() 检查 php.ini 的路径。

配置文件注释详细且全面。键区分大小写，关键字值不区分；空格和以分号开头的行会被忽略。布尔值可以用 1/0、Yes/No、On/Off 或 True/False 表示。php.ini-dist 中的默认值将生成一个合理的 PHP 安装，以后可以根据需要进行调整。

这里我们将解释 php.ini 中您可能需要的重要设置，以用于您的 PHP 解析器。

### short_open_tag = Off

短开放标签如下所示：<?= ?>。如果您想使用 XML 函数，此选项必须设置为 Off。

### safe_mode = Off

如果此项设置为 On，您可能使用 --enable-safe-mode 标志编译了 PHP。安全模式最相关于 CGI 用途。请参见本章前面“CGI 编译时选项”部分中的说明。

### safe_mode_exec_dir = [DIR]

此选项仅在安全模式开启时相关；在 Unix 构建过程中也可以使用 --with-exec-dir 标志进行设置。安全模式下的 PHP 仅从此目录执行外部二进制文件。默认值为 /usr/local/bin。这与提供普通 PHP/HTML 网页无关。

### safe_mode_allowed_env_vars = [PHP_]

此选项设置用户在安全模式下可以更改的环境变量。默认值仅为以 "PHP_" 开头的变量。如果此指令为空，大多数变量均可更改。

### safe_mode_protected_env_vars = [LD_LIBRARY_PATH]

此选项设置用户在安全模式下无法更改的环境变量，即使 safe_mode_allowed_env_vars 设置得比较宽松也是如此。

### disable_functions = [function1, function2...]

PHP4 配置中一项受欢迎的新增功能，并在 PHP5 中延续，即出于安全原因禁用选定函数的功能。以前，这需要手动编辑构建 PHP 的 C 代码。文件系统、系统和网络函数可能应该是首先被禁用的，因为允许通过 HTTP 写入文件和更改系统绝不是什么安全的主意。

### max_execution_time = 30

函数 set_time_limit() 在安全模式下无效，因此这是在安全模式下使脚本超时的主要方法。在 Windows 上，您必须根据消耗的最大内存而非时间来中止。如果您使用 Apache，也可以使用 Apache 的超时设置来设置超时，但这也会应用于站点上的非 PHP 文件。

### error_reporting = E_ALL & ~E_NOTICE

默认值为 E_ALL & ~E_NOTICE，即除通知以外的所有错误。开发服务器应至少设置为默认值；只有生产服务器才应考虑更小的值。

### error_prepend_string = [""]

配合其对应项 error_append_string，此设置允许您将错误消息设置为与其他文本不同的颜色，或者按照您的需求设置。

### warn_plus_overloading = Off

如果将 + 运算符与字符串一起使用（如表单值中），此设置会发出警告。

### variables_order = EGPCS

此配置设置取代了 gpc_order。两者现在都已弃用，连同 register_globals 一起。它设置不同变量的顺序：环境变量、GET、POST、COOKIE 和 SERVER（即内置变量）。

您可以更改此顺序。变量将按从左到右的顺序依次被覆盖，最右侧的变量每次都会获胜。这意味着，如果您保留默认设置，并且碰巧为环境变量、POST 变量和 COOKIE 变量使用了相同的名称，那么在过程结束时 COOKIE 变量将拥有该名称。在现实生活中，这种情况不常发生。

### register_globals = Off

此设置允许您决定是否希望将 EGPCS 变量注册为全局变量。此功能现已弃用，并且从 PHP4.2 开始，此标志默认设置为 Off。请改用超全局数组。本书中所有主要代码清单都使用超全局数组。

### gpc_order = GPC

此设置已弃用，为 GPC。

### magic_quotes_gpc = On

此设置会转义传入的 GET/POST/COOKIE 数据中的引号。如果您使用大量可能提交给自身或其他表单并显示表单值的表单，您可能需要将此指令设置为 On，或准备在字符串类型数据上使用 addslashes()。

### magic_quotes_runtime = Off

此设置会转义传入的数据库和文本字符串中的引号。请记住，SQL 在存储字符串时会在单引号和撇号前添加反斜杠，但在返回时不会将其去除。如果此设置为 Off，则在从 SQL 数据库输出任何类型的字符串数据时，需要使用 stripslashes()。如果 magic_quotes_sybase 设置为 On，此项必须为 Off。

### magic_quotes_sybase = Off

此设置使用 Sybase 风格的单引号而不是反斜杠来转义传入的数据库和文本字符串中的单引号。如果 magic_quotes_runtime 设置为 On，此项必须为 Off。

### auto-prepend-file = [path/to/file]

如果在此处指定了路径，PHP 必须在每个 PHP 文件开头自动 include() 它。包含路径限制确实适用。

### auto-append-file = [path/to/file]

如果在此处指定了路径，PHP 必须在每个 PHP 文件结尾自动 include() 它，除非您通过使用 exit() 函数来跳过。包含路径限制确实适用。

### include_path = [DIR]

如果您设置了此值，则只能从这些目录中 include 或 require 文件。包含目录通常位于文档根目录下；如果您在安全模式下运行，这是强制性的。将此设置为 . 以便从脚本所在的同一目录包含文件。多个目录用冒号分隔：.:/usr/local/apache/htdocs:/usr/local/lib。

### doc_root = [DIR]

如果您使用 Apache，您已经在 httpd.conf 中为此服务器或虚拟主机设置了文档根目录。如果您在安全模式下使用，或者只想在站点的某一部分启用 PHP（例如，仅在 Web 根目录的一个子目录中），请在此处设置此值。

### file_uploads = [on/off]

如果您将使用 PHP 脚本上传文件，请打开此标志。

### upload_tmp_dir = [DIR]

除非您了解 HTTP 上传的影响，否则请不要取消注释此行！

### session.save-handler = files

除非在极少数情况下，否则您不会想要更改此设置。所以请不要动它。

### ignore_user_abort = [On/Off]

此设置控制当站点访问者单击浏览器的停止按钮时发生的情况。默认值为 On，这意味着脚本将继续运行直到完成或超时。如果将设置更改为 Off，脚本将中止。此设置仅在模块模式下有效，而非 CGI。

### mysqli.default_host = hostname

如果未指定其他主机，则用于连接数据库服务器的默认服务器主机。

### mysqli.default_user = username

如果未指定其他用户名，则用于连接数据库服务器的默认用户名。

### mysqli.default_password = password

如果未指定其他密码，则用于连接数据库服务器的默认密码。

## Escaping to PHP

PHP 解析引擎需要一种方法来区分页面中的 PHP 代码和其他元素。这种机制称为“转义到 PHP”。有四种方法可以实现：

### Canonical PHP tags

最通用有效的 PHP 标签样式如下：

```
<?php ... ?>
```

如果您使用此样式，可以肯定您的标签始终会被正确解释。

### Short-open (SGML-style) tags

短标签或短开放标签如下所示：

```
<? ... ?>
```

短标签，正如人们所料，是最短的选项。要启用 PHP 识别这些标签，您必须做两件事之一：

- 在构建 PHP 时选择 --enable-short-tags 配置选项。
- 将 php.ini 文件中的 short_open_tag 设置设为 on。此选项必须禁用，才能使用 PHP 解析 XML，因为相同的语法用于 XML 标签。

### ASP-style tags

ASP 风格的标签模仿活动服务器页面（Active Server Pages）用于划分代码块的标签。ASP 风格的标签如下所示：

```
<% ... %>
```

要使用 ASP 风格的标签，您需要在 php.ini 文件中设置配置选项。

### HTML script tags

HTML 脚本标签如下所示：

```
<script language="PHP">...</script>
```

