

# 附录 B：配置 PHP

; 此项功能已存在很长时间，目前为了向后兼容性仍然支持，
; 但我们建议不要使用它们。
; 默认值：On
; 开发值：Off
; 生产环境值：Off
; http://php.net/short-open-tag
short_tag = Off

; 允许 ASP 风格的 <% % 标签。
; http://php.net/asp-tags
asp_tags = Off

; 浮点数显示的有效数字位数。
; http://php.net/precision
precision = 14

; 强制遵守 year 2000 标准（将导致不符合规范的浏览器出现问题）
; http://php.net/y2k-compliance
y2k_compliance = On

; 输出缓冲是一种控制 PHP 在将数据推送到客户端之前，
; 在内部保留多少输出数据（排除头部和 cookie）的机制。
; 如果你的应用程序输出超过了此设置，PHP 将
; 以你指定的大致大小分块发送。
; 开启此项并设置最大缓冲区可能会对你的应用程序和
; Web 服务器产生一些有趣的副作用。
; 你可能可以在通过 print 或 echo 输出内容后仍然发送头部和 cookie。
; 如果你的服务器向缓冲输出发送的数据包少于 PHP 获取输出时即进行流式输出，你可能会看到性能上的收益。
; 在生产服务器上，4096 字节是一个性能良好的设置。

; 注意：输出缓冲也可以通过输出缓冲控制函数进行控制。
; 可值：
; On = 启用并限制缓冲区。（请谨慎使用）
; Off = 禁用
; Integer = 启用缓冲区并设置其以字节为单位的最大大小。
; 注意：此指令在 CLI API 中被硬编码为 Off。
; 默认值：4096
; 开发值：4096
; 生产环境值：4096
; http://php.net/output-buffering
output_buffering = 4096

; 你可以将脚本的所有输出重定向到一个函数。
; 例如，如果你将输出处理器设置为 "mb_output_handler"，则
; 字符编码将透明地转换为指定的编码。
; 设置任何输出处理器都会开启输出缓冲。
; 注意：编写可移植脚本的人不应依赖此 ini 指令。
; 反之，请使用 ob_start() 显式设置输出。
; 除非你知道脚本在做什么，否则使用此 ini 指令可能会问题。

* 注意

# 附录 B：配置 PHP

```
; 注意：不能同时使用 "mb_output_handler" 和 "ob_iconv_handler"
; 不能同时使用 ob_gzhandler 和 "zlib.output_compression"
; 注意：如果此项设置为 'On' 则 output_handler 必须为空 !!!!
; 反之你必须使用 zlib.output_handler。
; http://php.net/output-handler
; output_handler =
```

```
; 使用 zlib 库进行透明化输出压缩
; 此选项的有效值为 'off'、'on' 或用于压缩的特定缓冲区大小
;（默认值为 4KB）
; 注意：由于压缩的性质，块大小可能会有所不同。PHP
; 压缩的结果输出几百字节的块：
; 如果你倾向于使用更大的块大小以获得更好的性能，
; 请额外启用 enable_buffering。
; 注意：你需要使用 zlib.output_handler 而不是标准的
; output_handler，否则输出将损坏。
; http://php.net/zlib.output-compression
zlib.output_compression = Off
```

```
; http://php.net/zlib.output-compression-level
; zlib.output_compression_level = -1
```

```
; 如果此处激活了 zlib.output_compression，则无法指定任何 
; 输出处理器。此设置与 output_handler 作用相同，但
; 顺序不同。
; http://php.net/zlib-output-handler
; zlib.output_handler =
```

```
; 隐式刷新 (implicit_flush) 告诉 PHP 在每个输出块之后
; 自动刷新输出层。这等同于在每次调用
; PHP() 之后、每次调用 print() 或 echo() 以及每个
; 每个 HTML 块之后调用该函数。开启此选项会对性能
; 产生严重影响，且仅用于调试目的。
; http://php.net/implicit-flush
; 注意：此指令在 CLI API 中是硬编码的
implicit_flush = =
```

```
; 如果反序列化时发现一个需要被实例化的未定义
; 类，则会调用反序列化回调函数（将未定义的类
; 名作为参数传递）。如果指定的函数未定义，或者该函数
; 没有包含/实现缺失的类，则会出现警告。
; 只有当你确实想实现这样一个
; 回调函数时，才设置此项；
unserialize_callback_func =
```

```
; 当浮点数和双精度数被序列化时，serialize_precision 决定
; 浮点数后的有效数字。默认值确保了当在不使用
; unserialize 解码浮点数时，数据将保持不变。
serialize_precision = 100
```

```
; 此指令允许你启用或禁用 PHP 当你在函数调用时
; 通过引用传递值时发出的警告。在函数调用时
; 通过引用传递值是一个已弃用的功能，将被移除

# 附录 B：配置 PHP

; - 默认值：Off
; 如果你在函数调用时通过引用传递值。在函数调用时
; 通过引用传递值是一个已弃用的功能，将被移除。

```
; http://php.net/output-handler
output_handler =
; 此指令允许你出于安全考虑禁用某些函数。
; 它接收一个逗号分隔的名称列表。
```

