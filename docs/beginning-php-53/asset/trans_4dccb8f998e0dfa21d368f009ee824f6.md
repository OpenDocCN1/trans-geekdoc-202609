
; 以下是其搜索顺序的摘要：
; 1. SAPI 模块特定位置。
; 2. PHPRC 环境变量。（从 PHP 5.2.0 开始）
; 3. Windows 上的一些预定义注册表项（从 PHP 5.2.0 开始）
; 4. 当前工作目录（CLI 除外）
; 5. Web 服务器的目录（针对 SAPI 模块），或 PHP 目录
; （否则在 Windows 中）
; 6. 来自 --with-config-file-path 编译时选项的目录，或
; Windows 目录 (C:\windows 或 C:\winnt)
; 有关更具体的信息，请参阅 PHP 文档。
; http://php.net/configuration.file

; 文件的语法极其简单。空格和
; 以分号开头的行会被静默忽略（你可能已经猜到了）。
; 节标题（例如 [Foo]）也会被静默忽略，尽管
; 它们在未来可能有特定含义。

; 在节标题 [PATH=/www/mysite] 之后的指令仅
; 应用于 /www/mysite 目录中的 PHP 文件。在节标题 [HOST=www.example.com] 之后的
; 指令仅应用于从 www.example.com 提供的 PHP 文件。在这些
; 特殊节中设置的指令不能被用户定义的 INI 文件或
; 运行时设置覆盖。目前，[PATH=] 和 [HOST=] 节仅在
; CGI/FastCGI 下工作。
; http://php.net/ini.sections

; 指令使用以下语法指定：
; directive = value
; 指令名称*区分大小写* - foo=bar 与 FOO=bar 不同。
; 指令是用于配置 PHP 或 PHP 扩展的变量。
; 不存在名称验证。如果 PHP 找不到预期的
; 指令，因为它未设置或拼写错误，将使用默认值。

; 值可以是字符串、数字、PHP 常量（例如 E_ALL 或 M_PI）、
; INI 常量之一（On、Off、True、False、Yes、No 和 None）或表达式
; （例如 E_ALL & ~E_NOTICE）、带引号的字符串（"bar"），或对
; 先前设置的变量或指令的引用（例如 ${foo}）

; INI 文件中的表达式仅限于位运算符和
; 括号：
; - | 按位或
; - & 按位与
; - ~ 按位非
; - ! 布尔非

; 布尔标志可以使用值 1、On、True 或 Yes 打开。
; 可以使用值 0、Off、False 或 No 关闭。

; 空字符串可以通过在等号
; 后不写任何内容来表示，或通过使用 None 关键字：

```
; foo =     ; sets foo to an empty string
; foo = None        ; sets foo to an empty string
; foo = "None"      ; sets foo to the string 'None'
;
; If you use constants in your value, and these constants belong to a
; dynamically loaded extension (either a PHP extension or a Zend extension),
; you may only use these constants *after* the line that loads the extension.
```

## php.ini 选项

在 PHP 5.3 之前，如果你希望在以 CGI 或 FastCGI 应用程序运行的 PHP 引擎中配置按目录设置的 PHP，那很不幸，因为这类设置不支持 .htaccess 文件。在 5.3 版本中此问题已得到解决：现在，在 CGI 或 FastCGI 下运行时，可以将设置存储在文件夹中的 .user.ini 文件内，其工作方式与常规 .htaccess 文件类似。（有关更多详细信息，请参见本附录开头。）

配置文件的 php.ini 选项部分为该功能设置了各种选项。

```
;;;;;;;;;;;;;;;;;;;;
; php.ini Options ;
;;;;;;;;;;;;;;;;;;;;
;
; Name for user-defined php.ini (.htaccess) files. Default is ".user.ini"
;user_ini.filename = ".user.ini"
;
; To disable this feature set this option to empty value
;user_ini.filename =
;
; TTL for user-defined php.ini files (time-to-live) in seconds. Default is
; 300 seconds (5 minutes)
;user_ini.cache_ttl = 300
```

## 语言选项

php.ini 的语言选项部分包含 PHP 引擎和语言的一些常规设置。设置包括是否启用输出缓冲（output_buffering）以及是否使用 HTTP 压缩压缩页面（zlib.output_compression）。

```
;;;;;;;;;;;;;;;;;;;;
; Language Options ;
;;;;;;;;;;;;;;;;;;;;
;
; Enable the PHP scripting language engine under Apache.
; http://php.net/engine
engine = On
```

```
; This directive determines whether or not PHP will recognize code between
; <? and ?> tags as PHP source which should be processed as such. It's been
; recommended for several years that you not use the short tag "short cut" and
; instead to use the full <?php and ?> tag combination. With the wide spread use
; of XML and use of these tags by other languages, the server can become easily
; confused and end up parsing the wrong code in the wrong context. But because
; this short cut has been a feature for such a long time, it's currently still
; supported for backwards compatibility, but we recommend you don't use them.
; Default Value: On
; Development Value: Off
; Production Value: Off
; http://php.net/short-open-tag
short_open_tag = Off
```

```
; Allow ASP-style <% %> tags.
; http://php.net/asp-tags
asp_tags = Off
```

```
; The number of significant digits displayed in floating point numbers.
; http://php.net/precision
precision = 14
```

```
; Enforce year 2000 compliance (will cause problems with non-compliant browsers)
; http://php.net/y2k-compliance
y2k_compliance = On
```

```
; Output buffering is a mechanism for controlling how much output data
; (excluding headers and cookies) PHP should keep internally before pushing that
; data to the client. If your application's output exceeds this setting, PHP
; will send that data in chunks of roughly the size you specify.
; Turning on this setting and managing its maximum buffer size can yield some
; interesting side-effects depending on your application and web server.
; You may be able to send headers and cookies after you've already sent output
; through print or echo. You also may see performance benefits if your server is
; emitting less packets due to buffered output versus PHP streaming the output
; as it gets it. On production servers, 4096 bytes is a good setting for
; performance
; reasons.
; Note: Output buffering can also be controlled via Output Buffering Control
; functions.
; Possible Values:
;   On = Enabled and buffer is unlimited. (Use with caution)
;   Off = Disabled
;   Integer = Enables the buffer and sets its maximum size in bytes.
; Note: This directive is hardcoded to Off for the CLI SAPI
; Default Value: Off
; Development Value: 4096
; Production Value: 4096
; http://php.net/output-buffering
output_buffering = 4096
```

```
; You can redirect all of the output of your scripts to a function. For
; example, if you set output_handler to "mb_output_handler", character
; encoding will be transparently converted to the specified encoding.
; Setting any output handler automatically turns on output buffering.
; Note: People who wrote portable scripts should not depend on this ini
; directive. Instead, explicitly set the output handler using ob_start().
; Using this ini directive may cause problems unless you know what script
; is doing.
; Note: You cannot use both "mb_output_handler" with "ob_iconv_handler"
; and you cannot use both "ob_gzhandler" and "zlib.output_compression".
; Note: output_handler must be empty if this is set 'On' !!!!
; Instead you must use zlib.output_handler.
; http://php.net/output-handler
;output_handler =
```

; 使用 zlib 库进行透明输出压缩
; 此选项的有效值为 'off'、'on' 或用于压缩的特定缓冲区大小（默认值为 4KB）
; 注意：由于压缩的性质，生成的分块大小可能会有所不同。PHP
; 作为压缩的结果，输出每个几百字节的分块。如果你希望为了更好的
; 性能而使用较大的分块大小，请此外启用 output_buffering。
; 注意：你需要使用 zlib.output_handler 而不是标准的
; output_handler，否则输出将损坏。
; http://php.net/zlib.output-compression
zlib.output_compression = Off

; http://php.net/zlib.output-compression-level
;zlib.output_compression_level = -1

; 如果在此处激活了 zlib.output_compression，则无法指定其他输出处理程序。
; 此设置与 output_handler 作用相同，但顺序不同。
; http://php.net/zlib.output-handler
;zlib.output_handler =

; 隐式刷新指示 PHP 在每个输出块后自动刷新输出层。
; 这相当于在每次调用 print() 或 echo() 以及每个 HTML 块后调用
; PHP 函数 flush()。启用此选项会带来严重的性能
; 影响，通常仅建议用于调试目的。
; http://php.net/implicit-flush
; 注意：此指令对于 CLI SAPI 硬编码为 On
implicit_flush = Off

; 如果反序列化器找到应实例化的未定义类，则将调用 unserialize 回调函数（以未定义类的
; 名称作为参数）。如果指定的函数未定义，或该函数未包含/实现缺失的类，则会出现警告。
; 因此，只有在确实想实现此类
; 回调函数时才设置此项。
unserialize_callback_func =

; 序列化浮点数和双精度数时，在小数点后存储 serialize_precision 个有效数字。
; 默认值确保使用 unserialize 解码浮点数时，数据将保持不变。
serialize_precision = 100

; 此指令允许启用和禁用 PHP 在函数调用时按引用传递值时会发出的警告。
; 在函数调用时按引用传递值是一个弃用的特性，将被删除
