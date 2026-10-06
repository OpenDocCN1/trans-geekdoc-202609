

# 录 B：配置 PHP

; 由垃圾回收进程清理。
; http://php.net/session.gc-maxlifetime
session.gc_maxlifetime = 1440

; 注意：如果你使用子目录选项存储会话文件
;（参见上方的 session.save_path），则垃圾回收*不会*
; 自动发生。你需要通过 shell 脚本、cron 任务项或其他方法
; 自行进行垃圾回收。

; 例如，以下脚本等同于将
; session.gc_maxlifetime 设置为 1440（1440 秒 = 24 分钟）；
; /path/to/sessions; find -min +24 xargs rm

PHP 4.2 及更低版本有一个未文档的特性，允许在 register_globals
; 禁用的情况下，在全局作用域内初始化会话变量。PHP 4.3 及更高版本如果使用此特性，将向你发出警告。
; 你可以分开使用该特性和警告。目前，
; 只有在启用 bug_compat_42 的情况下才会显示警告。该特性
; 如果处理不当，会引入一些歧义。
; 建议不要在生产服务器上使用此特性。但你; 应该在开发服务器上启用此特性以及警告。如果
; 没有在开发服务器上启用此特性，在使用时将不会收到警告，
; 调试由此引起的错误可能难以追踪。

- 默认值：On
- 开发值：On
- 生产环境值：Off
; http://php.net/session.bug_compat-42
session.bug_compat_42 = On

; 此设置控制 PHP 是否会在将会话值初始化到全局空间时
;向你发出警告。在 PHP 发布这些警告之前，必须启用
; session.bug_compat_42。更多信息请参见上方指令。

- 默认值：On
- 开发值：On
- 生产环境值：Off
; http://php.net/session.bug_compat-warn
session.bug_compat_warn = On

; 检查 REFERER 以使包含 ids 的外部 URLset。
; HTTP_REFERER 必须包含此字符串，会话才
; 被视为有效。
; http://php.net/session.referer_check
session.referer_check =

; 从文件中读取的字节数。
; http://php.net/session.entropy-length
session.entropy_length = 0

; 在此处指定用于创建会话 ID。
; http://php.net/session.entropy-file
session.entropy_file = /dev/urandom
session.entropy_file =

; http://php.net/session.entropy-length

```
;session.entropy_length = 16

; 设置为 [nocache,private,public,] 来决定 HTTP 缓存方面
; 留空以避免反缓存标头。
; http://php.net/session.cache-limiter
session.cache_limiter = nocache
```

```php
; 文档在 n 分钟后过期。
; http://php.net/session.cache-expire
session.cache_expire = 180
```

```php
; 默认支持 trans sid。
; 使用 trans sid 可能会危及用户的安全。
; 请谨慎使用此选项。
; 用户可能会将包含活动会话 ID 的 URL
; 通过电子邮件/irc/等发送给他人。
; 包含活动会话 ID 的 URL 可能会存储
在公共可访问的计算机上。
; 用户可以使用浏览器历史记录或书签中的 URL
; 使用相同的会话 ID 访问你的站点。; http://php.net/session.use-trans-sid
session.use_trans_sid = 0
```

```php
; 选择一个用于生成会话 ID 的哈希函数。
; 可能的值：
; 0 (MD5 128 位)
; 1 (SHA-1 160 位)
; http://php.net/session.hash-function
session.hash_function = 0
```

```php
; 定义在将二进制数据转换为可读方法时，
; 每个字符中存储的位数。
; 可能值：
; 4 (位: 0-9, a-f)
; 5 (位: 0-9, a-v)
; 6 (位: 0-9, a-z, A-Z, "-", "*")
; 默认值：4
; 生产环境值：5
; http://php.net/session.hash-bits-per-character
session.hash_bits_per_character = 5
```

```php
; URL 重写器用于定义 HTML 标签集中的 URL。
; fieldset/ 是特殊的；如果包含了它们，重写器将
; 添加一个隐藏的 <input> 字段，其中包含否则会附加到
; URL 上的信息。如果需要符合 XHTML 标准，请删除表单条目。
; 注意，如果不存在值，所有值条目都需要一个 "="。
; 默认值："<a=href,area=href,frame=src,form=fieldset"
; 开发值："<a=href,area=href,frame=src,input=src,form=fakeentry"
; 生产环境值："<a=href,area=href,frame=src,input=src,form=fakeentry"
; http://php.net/url-rewriter.tags
url_rewriter.tags = "<a=href,area=href,frame=src,input=src,form=fakeentry"
```

```php
[mssql]
; 允许或防止持久连接。
mssql.allow_persistent = On

; 持久连接的最大数量。-1 表示无限制。
mssql.max_persistent = -1

; 持久连接的数量。-1 表示无限制。
mssql.links = -1

; 显示的最小错误严重性。
mssql.min_error_severity = 10

; 显示的最小消息严重性。
mssql.min_message_severity = 10

; 与旧版本 PHP 的兼容模式。
mssql.compatibility_mode = Off

; 连接超时
mssql.connect_timeout = 5

; 查询超时
mssql.timeout = 60

; 有效范围 0-2147483647。默认 4096。
mssql.textlimit = 4096

; 有效范围 0-2147483647。默认 4096。
mssql.textsize = 4096

; 限制记录记录。0 = 批次的所有记录。
mssql.batchsize = 0

; 指定 datetime 列
; On = 将数据转换为 SQL 设置
; Off = 返回 YYYY-MM-DD hh:mm:ss
mssql.datetimeconvert = On

; 连接服务器时使用身份认证
mssql.secure_connection = Off

; 指定最大进程数。-1 = 库 FreeTDS 默认值为 25
mssql.max_procs = -1

; 指定客户端字符集。
; 只有当使用 FreeTDS 编译时使用
mssql.charset = "ISO-8859-1"
```

```php
[Assertion]
; Assert(expr) 默认
; http://php.net/assert.active
assert.active = On

; 为每个失败的断言发出 PHP 警告。
; http://php.net/assert.warning
assert.warning = On

; 默认退出。
; http://php.net/assert.bail
assert.bail = Off

; 断言失败时调用的用户函数。
; http://php.net/assert.callback
assert.callback = 0

; 使用当前 error_reporting() 评估表达式。如果你想
; 在 eval() 之外使用 error_reporting(0)，则设置为 true。
; http://php.net/assert.quiet_eval
assert.quiet_eval = 0
```

```php
[COM]
; 包含 GUID、ID 或文件名的文件路径
; http://php.net/com.typelib-file
com.typelib_file =

; 允许 分散 COM 调用
; http://php.net/com.allow-dcom
com.allow_dcom = true

; 在 com_load() 上自动注册组件的 typelib
; http://php.net/com.autoregister-typelib
com.autoregister_typelib = true

; 注册常量大小敏感
; http://php.net/com.autoregister-casesensitive
com.autoregister_casesensitive = false

; 重复注册时显示警告
; http://php.net/com.autoregister-verbose
com.autoregister_verbose = true

; 与 COM 对象之间传递字符串时使用的默认字符集代码页。
; 默认：系统 ANSI 代码页
com.code_page =
```

```php
[mbstring]
; 内部字符表示的语言。
; http://php.net/mbstring.language
mbstring.language = Japanese

; 内部/脚本编码。
; 某些编码不能作为内部编码。
; （例如 SJIS, BIG5, ISO-2022-*）
; http://php.net/mbstring.internal-encoding
mbstring.internal_encoding = EUC-JP

; http 输入编码。
; http://php.net/mbstring.http-input
mbstring.http_input = auto

; http 输出编码，mb_output_handler 必须
; 注册为输出缓冲区
; http://php.net/mbstring.http-output
mbstring.http_output = SJIS

; 根据 mbstring.internal_encoding 设置启用
; 编码转换。设置为 On 时，输入字符将
; 转换为内部。
; 注意：对可移植库/应用程序不要使用自动转换。
; http://php.net/mbstring.encoding-translation
mbstring.encoding_translation = Off
```

```php
; 自动编码检测顺序。
; auto 意味着
; http://php.net/mbstring.detect-order
mbstring.detect_order = auto
```

```php
; 当字符无法从一个转换为另一个时使用的
; substitute_character
; http://php.net/mbstring.substitute-character
mbstring.substitute_character = none

; 用 mbstring 函数重载（替换）单字节函数。
; mail(), ereg() 等被 mb_send_mail(), mb_ereg(),
; 等重载。可能的值为 0,1,2,4 或它们的组合。
; 例如，7 表示重载所有。
; 0: 不重载
; 1: 重载 mail() 函数
; 2: 重载 str(*) 函数
; 4: 重载 ereg(*) 函数
; http://php.net/mbstring.func-overload
mbstring.func_overload = 0
```

```php
; 启用严格编码检测。
mbstring.strict_detection = Off
```

```php
; 此指令指定了激活 mb_output
; 处理器的内容类型正则模式。
; 默认值：mbstring.http_output_conv_mimetype=^(text|application/html+xml)
mbstring.http_output_conv_mimetype=
```

```php
; 允许设置脚本编码。只有当 PHP 编译了 --enable-zend-multibyte 时才会影响。
; 默认值：""
mbstring.script_encoding=
```

