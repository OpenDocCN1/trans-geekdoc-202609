
此标志将 XML-RPC 和 SOAP 实现构建入 PHP。XML-RPC 包现在随 PHP 绑定，因此你不需要指定目录。要了解更多基于 XML 的服务，请参阅第 41 章。

## `--with-dom=[DIR]`

此标志使用 `libxml` 库构建 DOM 支持。`DIR` 路径应指向你的 `libxml` 安装位置；如果你不设置该值，它默认为 `usr`。你可以从 `www.php.org` 下载并学习更多关于 XML 的信息。常见的共享库（如 `libjpeg`）可能会导致 PHP 出现致命问题，除非你在编译时处理了它们。在这种情况下，你可能需要使用 Apache 选项。

## `--enable-decimal`

此选项在 PHP 版本中构建数学支持。你必须在 `php.ini` 中设置所有。

## `--enable-calendar`

此选项在 PHP 版本中构建日历支持。

## `--enable-math`

此选项在 PHP 版本中构建高精度数学支持。

## `--config-file-path=[DIR]`

此选项允许指定 `php.ini` 的位置。

## `--enable-url-includes`

此选项允许 PHP 包含远程 HTTP 服务器的文件，如 `include(remotehost.php)`。这种功能需要谨慎处理。除非，如果你想读取其他 HTTP 服务器的文件，**不要**设置此标志。

## `--disable-url-fopen`

此标志关闭了打开远程 HTTP 服务器文件的能力，如 `fopen(remotehost.php)`。

# 第 30 章 ✦ 配置

## `--with-exec-dir=[DIR]`

另一个与安全模式相关的编译时选项是 `--with-exec-dir`。此选项将默认的安全模式执行目录设置为 `/usr/local/bin`，但可以通过 `php.ini` 中的 `safe_mode_exec` 指令对其进行更改。请记住，在安全模式下，你只能从这一个目录运行程序。

## `--enable-discard-path`

如果你想将 CGI 版本的 PHP 放在 Web 树之外，并像处理 Perl CGI 脚本那样（例如在每个脚本的第一行使用 `#!/usr/local/bin/php`），你需要指定此编译标记。你还必须将所有 PHP CGI 脚本设置为可执行文件。

## `--enable-force-cgi-redirect`

此标记是 CGI 模块的一种安全措施。它防止浏览器直接调用 CGI-bin 文件，从而绕过 Apache 安全设置。这是一个 Apache 特有的配置指令；如果你运行在不同的 Web 服务器上或作为独立程序运行，则无需启用它。

## Apache 配置文件

如果 PHP 以模块形式或 CGI 使用，Apache 的基本文件服务能力将由 Apache 的配置文件决定。最近版本的 Apache Server 的主文件是用于全局设置的 `httpd.conf` 以及用于每个目录访问设置的 `.htaccess`。旧版本的 Apache 将 `.htaccess` 分为三个（`access.conf`、`httpd.conf` 和 `rmf.conf`），用户仍然倾向于这种安排。

在 PHP3 中，存在一些 Apache 配置指令可以替代每个 `php.ini`。例如，与其其在 `php.ini` 的第一个实质性行中设置 `Engine = On`，你可以在 `.htaccess` 中放入 `php3_engine_on` 以实现类似的效果。然而，PHP 配置指令的数量在不断增加，人们认为过多的标记在 Apache 的命名空间下过于拥挤。因此，命名方案已经泛化，以包含以下四个可配置的指令：

- `php_value name value`：设置变量值。
- `php_flag name off`：设置布尔值。
- `php_admin_name name value`：设置变量值。只能在主 Apache 配置文件中使用，不能在 `.htaccess` 中。
- `php_admin_flag name off`：设置布尔值。只能在主 Apache 配置文件中使用，不能在 `.htaccess` 中。

例如，针对 GET、POST 和 COOKIE 变量魔术引号。你可以像这样使用带有名的 `php_flag`：

```
php_flag magic_quotes_gpc off
```

如果这些太复杂了，别担心：新式的 Apache 配置命名无论如何只适用于可以在 `php.ini` 中更改的设置。

Apache 服务器有自己一套非常强大但稍显复杂的配置系统。可以在 Apache 网站了解更多信息：`www.apache.org`。

以下标题描述了 `httpd.conf` 中直接影响 PHP 无法在其他地方设置的设置。

## 高级功能与技术

### `Timeout`（超时）

此值设置了任何 HTTP 请求超时前的默认秒数。如果你将 PHP 的 `max_execution_time` 设置得比此值更长，PHP 将继续运行，但用户可能会看到 404 错误。在安全模式下，此值将被忽略；你必须使用 `php.ini` 中的 `timeout` 值。

### `DocumentRoot`（文档根目录）

`DocumentRoot` 指定了服务器上所有 HTTP 进程的根目录。它看起来像：

```
/usr/local/apache_1.3/htdocs
```

在 Windows 上看起来像这样：

```
DocumentRoot "C:/Program Files/Apache/htdocs/"
```

文档根可以是任何目录——它需要位于 Apache 安装目录。你可以使用 `php.ini` 中的 `doc_root` 设置指定此目录的子目录作为 PHP 文档根。在这种情况下，HTML 文件将从 Apache 文档根及其子目录提供，但 PHP 将仅在指定的 PHP 目录及其子目录中解析。

### `AddType`（添加类型）

需要在此设置 PHP 文件的 MIME 类型以便进行解析。记住，你可以将任何文件扩展名与 PHP 关联；许多管理员为了兼容性设置了 `.php3` 和 `.html` 类型——但如果你想，可以处理 `filename.asp` 或 `filename.jsp` 等解析文件。你还可以为不同版本的 PHP 添加多个类型。以下是 `AddType` 行的示例；第一行是 PHP 4 最常用的，但你可以根据需要添加任意数量。

```
AddType application/x-httpd-php .php
AddType application/x-httpd-php .php5
AddType application/x-httpd-php .php3 .shtml
AddType application/x-httpd-php .html
```

你也可以通过 `.htaccess` 按目录设置此项，只需向 `.htaccess` 中添加类型行即可。PHP 文件将仅在服务器的某一个目录（例如某个文件夹）中进行解析。或者，你可以设置一个包含带有旧扩展名文件的存档目录——只需在该目录中，Apache 允许这样做。

### `Action`（动作）

对于通常用于 Windows 的 Apache CGI 版本，必须设置此行。对于 PHP 模块版本不需要设置此行。

```
Action application/x-httpd-php "php.exe"
```

### `LoadModule`（加载模块）

对于带有共享支持的 Windows 版本，你必须取消此行的注释：

```
LoadModule php_module modules/php.dll
```

或 Unix 变：

```
LoadModule php_module modules/mod_php.php
```

### `AddModule`（添加模块）

对于静态版本的 Apache，你必须取消此行的注释。

```
AddModule mod_php.c
```

## `php.ini`

PHP 配置文件 `php.ini` 是访问 PHP 功能的最终且最直接的方式。文件的结构经常发生变化，所以如果你还没有费心阅读每一行，现在可能是个好机会。如果你的更改没有显示，请记住停止并重启 Apache；检查 PHP 期望找到 `php.ini` 的路径。

> 注意 如果 PHP 找不到 `php.ini` 会发生什么？在 Windows 下，直到 PHP 的最终发布版本，你通常会收到“无法解析配置文件”的错误。在 Unix 下以及现在作为 ISAPI 模块时，有趣的是，你不会收到任何警告或错误——PHP 带有默认设置运行，就像你更改了 `php.ini-dist` 中的设置一样。只有当你想要更改默认设置时才需要安装 `php.ini`。该配置文件注释详尽且彻底。键对大小敏感，以分号开头的行会被忽略。布尔值由 `1/0`、`Yes/No`、`On/Off` 或 `True/False` 表示。`php.ini-dist` 中的默认值将产生一个合理的安装，并可以进行微调。以下是 `php.ini` 中在 PHP 手册配置页中未完全记录的设置。

### `short_open_tag = Off`

短标签看起来像这样：`<?php`。如果你想使用 `<?php`，必须将此项设置为 `Off`。

### `safe_mode = Off`

如果此项设置为 `On`，则可能配合 `--enable-safe-mode` 标志使用。安全模式在编译 Apache 时最相关。

### `safe_mode_exec_dir = [DIR]`

此选项在安全模式下仅从此目录执行二进制文件。默认是 `/usr/local/bin`。

### `safe_mode_allowed_env_vars = [PHP_]`

此选项设置安全模式下用户可以更改的环境变量。默认是以 PHP 开头的变量。

### `safe_mode_protected_env_vars = [LD_LIBRARY_PATH]`

此选项设置安全模式下无法更改的环境变量，即使 `safe_mode_allowed_env_vars` 设置得很宽松。

### `disable_functions = [function1, function2, function3...]`

PHP5 增加的一个功能是出于安全考虑禁用某些函数。这需要对制作 PHP 的 C 代码进行修改。文件、系统和网络函数应该是最先被禁用的，允许在安全模式下写入文件和更改系统。

### `max_execution_time = 30`

在安全模式下，`set_time_limit()` 不起，因此这是让脚本超时的主要方法。在 Windows 上，你必须根据最大消耗而非时间来终止。如果你使用 Apache，也可以使用 Apache 超时设置，但那适用于站点上的非 PHP 文件。

### `error_reporting = E_ALL & ~E_NOTICE`

默认是 `E_ALL&NOTICE`，除通知外的所有错误。开发服务器应该设置为最小默认；只有生产服务器应该考虑较小的值。

### `error_prepend_string = "[font color=ff0000]"`

与其对应的 `error_append_string`，这允许让错误消息的颜色与其他文本或你拥有的颜色不同。我们建议将值设置为 `<span>`（当然，`error_prepend_string` 设置为 `<span>`）以获得特殊效果！默认结果是红色错误消息。如果你想使用它们，请记住取消注释——默认是注释掉的。

### `warn_plus_overloading = Off`

此设置在字符串中使用 `+` 运算符（例如表单值）时发出警告。

### `variables_order = EPGCS`

此配置设置 `gpc_order`。两者现在都随 `register_global` 变量废弃：ENVIRONMENT、GET、POST、COOKIE 和 SERVER。你可以更改此顺序。变量将从左到右依次覆盖，最右侧的胜出并命名。

### `register_globals = Off`

此设置允许你决定是否希望将 EGPC 变量注册为全局变量。该设置已废用，在 PHP 4.2 中，此标志默认设置为 `Off`。请改用超全局数组。书中所有的主要代码列表都使用了超全局数组。

### `gpc_order = G`

已废用。

### `magic_quotes_gpc = On`

此设置会对传入的 GET/POST/COOKIE 数据进行转义。如果你使用了许多可能提交到自身或其他地方并显示表单值的表单，你可能需要将此指令设置为 `On`，或者准备对字符串类型的数据使用 `addslashes()`。

### `magic_quotes_runtime = Off`

此设置会对数据库和文本字符串中的引号进行转义。记住，SQL 在存储字符串时会对引号和单引号添加反斜杠，并在返回它们时不会删除它们。如果此设置为 `Off`，那么当你从 SQL 数据库中获取任何类型的字符串数据时，你需要使用 `stripslashes()`。如果 `magic_quotes_sybase` 设置为 `On`，

### `magic_quotes_sybase = Off`

此设置使用 Sybase 风格的引号而非反斜杠来转义数据库和文本字符串中的引号。如果 `magic_quotes_runtime` 设置为 `On`，则此处必须为 `Off`。

### `auto-prepend-file = [path/to/file]`

如果在该处指定路径，PHP 必须在每个 PHP 文件的开头自动 `include()` 它。包含路径限制。

### `auto-append-file = [path/to/file]`

如果在此处指定路径，PHP 必须在每个 PHP 文件的末尾自动 `include()` 它——除非你使用 `exit()` 函数进行转义。包含路径限制有效。

### `include_path = [DIR]`

如果你设置了此项，将仅允许从这些目录包含或引入文件。包含目录通常位于你的文档根目录下；如果你运行在安全模式，这是强制性的。将其设置为 `.` 以包含与脚本相同目录的文件。如果只想在 Web 根目录的部分站点（例如仅在一个子目录中）启用 PHP，可以设置。多个目录之间用冒号分隔：`:/usr/local/apache/htdocs/usr/`

### `doc_path = [DIR]`

如果你使用 Apache，你已经在 `httpd.conf` 中为此服务器或虚拟主机设置了文档根。如果你在使用安全模式或仅在网站的部分区域启用 PHP（例如仅在 Web 根目录的一个子目录下），请设置此值。

### `upload_tmp_dir = [DIR]`

除非理解 HTTP 上传的影响，否则不要取消此行的注释

### `session.save_handler = files`

有关此设置的详情请参见第 24 章。在少数情况下，你可能希望更改此设置。

### `ignore_user_abort = [On/Off]`

此设置控制网站访问者点击浏览器“停止”按钮时发生什么。默认是 `On`，这意味着脚本将继续运行完成或超时。如果设置改为 `Off`，脚本将终止。此设置仅在模块模式下有效，CGI无效。

## 提高 PHP 性能

关于 Web 性能有两种观点。第一种观点是 PHP 脚本性能，理论上的 Web 服务器端、时钟速度、服务器内存以及几乎所有其他与吞吐量输入无关的内容——那么为什么要纠结这些事情呢？另一种观点是，在执行时间上缩短几微秒是非常有快感的。对于第一种观点的程序员来说，本节基本上没有用处。

在提高性能之前，你必须先测量它。商业性能分析工具刚刚进入市场——我们在第 32 章中讨论过。相对少数 PHP 用户使用它们。因此，我们默认使用经典的编程指标：测量微秒。

编写一个这样的函数：

```php
function exec_time() {
    $mtime = explode(" ", microtime(true));
    $msec = (double)$mtime[0];
    $sec = (double)$mtime[1];
    return $sec + $msec;
}
```

此函数将 `microtime` 输出格式化为双精度浮以便于法。将其粘贴或包含在你想测量的脚本顶部。现在将你的脚本主体分成若干部分，并在战略点散布调用，如下：

```php
<?php
$start_db_call = exec_time();
$db = mysql_select_db("test");
$result = mysql_query("SELECT * FROM user
    WHERE ID=1");
while ($row = mysql_fetch_array($result)) {
    echo $row[0];
}
$end_db_call = exec_time();
$runtime = $end_db_call - $start_db_call;
echo "Database call and took " $runtime " seconds";
?>
```
