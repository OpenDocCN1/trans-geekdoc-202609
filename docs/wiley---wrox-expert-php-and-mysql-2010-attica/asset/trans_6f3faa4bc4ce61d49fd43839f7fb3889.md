
然而，可以使用一些内置定义手动传递 TSRMLS。你已在之前的章节中在解析参数时做过此操作。以下是需要记住的四个定义：

-   **TSRMLS_D** 用于函数定义内部。
-   **TSRMLS_DC** 用于函数定义内部，当没有其他参数时。
-   **TSRMLS_C** 用于函数调用。
-   **TSRMLS_CC**，**TSRMLS_C** 的对应项，用于没有其他参数时的函数调用。

主要区别在于其中两个——以 DC 和 CC 结尾的——各自以逗号开头，意在将其与前面的参数分隔开。关于全局变量的章节对 TSRMLS 系列定义有更多信息。

## 输入/输出

本章已通过函数参数和返回值涵盖了输入和输出。本节涵盖来自其他来源的输入和输出。具体来说，以 PHP 方式进行的标准输出、错误和警告，以及文件和网络连接。

### 标准输出

到目前为止，本章重点介绍了向 PHP 提供反馈的两种方法。第一种是通过引用传递的参数，第二种是返回值。另一种提供反馈的方法是通过标准输出。

用于标准输出的函数众多。你最常使用的是 php_printf，它的行为与 PHP 中的对应函数类似。例如：

```
php_printf("The value of some_zval is: %s", Z_STRVAL_P(some_zval));
```

php_printf 函数接受与 PHP 和 C 中的对应函数相同的所有值。或者，当不需要变量替换时，你也可以使用以下方式：

```
php_write( Z_STRVAL_P(some_zval), Z_STRLEN_P(some_zval) );
```

使用这两个函数，可以向标准输出流写入任何内容。但有时为了调试并查看变量的当前值，需要更有结构的数据。 这种数据可能难以格式化。Zend 为此提供了一些函数：

-   **zend_print_zval** 将 zval 作为第一个参数，将缩进量（long）作为第二个参数。它输出 zval 的平面表示，并为无法优雅显示的复杂类型打印文本描述。
-   **zend_print_zval_r** 递归打印 zval。其输出与 PHP 中的 print_r 相同。

### 文件和流

输入和输出应始终通过 PHP 函数处理。其主要原因之一是 PHP 对脚本可以打开的流类型施加了限制。这些限制可以被 C 脚本轻易规避，从而引入安全问题。

另一个重要原因是 PHP 具有流包装器。流包装器使 PHP 能够透明地打开从文件系统到 HTTP 和 FTP 的各种流类型。

### 基本流

所有 PHP 流函数都遵循 php_stream_ 的模式。文件 I/O 可能是最常见的任务之一。 一个将 zval 写入由用户提供的文件名标识的文件的简单函数如下所示：

```
char *filename;
int filename_len;
php_stream *stream;
zval *val;

if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "sz/", &filename,
    &filename_len, &val ) == FAILURE) {
    RETURN_FALSE;
}

stream = php_stream_open_wrapper_ex(filename, "w+",
    ENFORCE_SAFE_MODE | REPORT_ERRORS, NULL, NULL );

if ( stream ) {
    convert_to_string(val);
    php_stream_write(stream, Z_STRVAL_P(val), Z_STRLEN_P(val));

    php_stream_close(stream);
}
```

在对流执行任何操作之前，特别是关闭流时（这会导致尝试释放未打开的文件而出现段错误），对流进行验证非常重要。

前述代码示例中突出显示了标志。你可以使用标志来禁用安全功能或启用对文件的额外检查。一些可用标志列在表 8-2 中：

#### 表 8-2：基本流中的标志

| 标志 | 描述 |
|------|-------------|
| IGNORE_PATH | 评估为 0，表示不应使用搜索路径。如果与其他标志结合使用，此标志毫无意义；它只是使操作的意图更清晰。 |

#### 表 8-2（续）

| 标志 | 描述 |
|------|-------------|
| USE_PATH | 如果在相对路径中找不到文件，则表示应使用包含搜索路径。 |
| IGNORE_URL | 忽略任何 URL 路径。 |
| ENFORCE_SAFE_MODE | 告诉引擎是否检查安全模式限制。 |
| REPORT_ERRORS | 表示应将流错误报告在错误日志中。警告仍发送到标准输出。 |
| STREAM_MUST_SEEK | 表示对流而言寻址是必需的，但写入流不是必需的。 |
| STREAM_WILL_CAST | 如果流将被强制转换为 FILE* 或 socket，则应使用。它关闭缓冲，因此如果不打算强制转换流，则省略该标志实际上意味着更好的性能。 |
| STREAM_OPEN_FOR_INCLUDE | 由 require 和 include 调用使用。在许多扩展中不太可能需要它。 |
| STREAM_USE_URL | 仅使用 URL。尝试打开任何非 URL 的内容都会导致错误。 |
| STREAM_ONLY_GET_HEADERS | 使流仅返回标头。它仅与具有标头的包装器（如 HTTP）相关。 |
| STREAM_DISABLE_OPEN_BASEDIR | 忽略对基本目录的限制（PHP 脚本通常不允许打开不在基本目录下的文件）。 |
| STREAM_OPEN_PERSISTENT | 创建或打开持久文件流。 |
| STREAM_DISABLE_URL_PROTECTION | 忽略可能禁用通过流打开 URL 的任何 PHP 配置。 |
| STREAM_ASSUME_REALPATH | 表示给定以打开文件的路径确实是真实的，并且不会尝试计算真实路径或检查搜索路径。 |

流 API 实现了 C 标准 I/O 库以及许多其他有助于简化开发的函数。流也可以作用于目录。所有基本流函数都列在表 8-3 中。

#### 表 8-3：流函数

| 创建流 | 复制（续） |
|---|---|
| php_stream_open_wrapper | php_stream_copy_to_stream_ex |
| php_stream_open_wrapper_ex | 包装器 |
| php_stream_from_persistent_id | php_register_url_stream_wrapper |
| 流操作 | php_unregister_url_stream_wrapper |
| php_stream_close | php_register_url_stream_wrapper_volatile |
| php_stream_read | php_unregister_url_stream_wrapper_volatile |
| php_stream_get_line | php_stream_locate_url_wrapper |
| php_stream_get_record | php_stream_wrapper_log_error |
| php_stream_write | 目录 |
| php_stream_seek | php_stream_mkdir |
| php_stream_tell | php_stream_rmdir |
| php_stream_rewind | php_stream_opendir |
| php_stream_eof | php_stream_readdir |
| php_stream_getc | php_stream_scandir |
| php_stream_putc | 上下文函数 |
| php_stream_flush | php_stream_context_set |
| php_stream_puts | php_stream_context_free |
| php_stream_stat | php_stream_context_alloc |
| php_stream_set_options | php_stream_context_get_option |
| php_stream_free | php_stream_context_set_option |
| 复制 | php_stream_context_get_link |
| php_stream_copy_to_mem | php_stream_context_set_link |
| php_stream_copy_to_stream | php_stream_context_del_link |

### 使用上下文

此外，流 API 还提供了一些使读取结构化数据变得更容易的函数。其中很大一部分功能涉及上下文。上下文允许将特定信息传递给包装器。

上下文的一种用途是为 HTTP 流包装器提供额外数据。下一个示例使用上下文为 HTTP 请求指定用户代理：

```c
char *filename, *mode, *agent;
int filename_len, mode_len;
php_stream *stream;
php_stream_context *context = NULL;

if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "ss",
    &filename, &filename_len, &mode, &mode_len ) == FAILURE) {
    RETURN_FALSE;
}

MAKE_STD_ZVAL(mode);
ZVAL_STRING(mode,"r",0);

MAKE_STD_ZVAL(agent);
ZVAL_STRING(agent,"Expert PHP and MySQL book",0);

context = php_stream_context_alloc();
php_stream_context_set_option(context, "http", "user_agent", agent);

stream = php_stream_open_wrapper_ex(filename, mode,
    ENFORCE_SAFE_MODE | REPORT_ERRORS, NULL, context);

if ( stream ) {
    ...

    php_stream_close(stream);
    php_stream_context_free(context);
}
```

不同类型的包装器具有不同的上下文选项。HTTP 包装器包括设置标头、代理、超时、post 数据和最大重定向次数的选项。

包装器有时也会在主流之外返回数据。例如，HTTP 的信息包括服务器发送的所有标头。由于包装器数据经常使用哈希表，因此在“数组和哈希表”部分中进行了介绍。

### 网络

跨平台的网络可能很困难。幸运的是，PHP 已拥有强大的 TCP/IP 通信库集合。结合流 API，PHP 扩展可以满足其所有网络需求。网络 API 由 HTTP 和 FTP 流包装器使用。

### 构建客户端

PHP 既可以作为客户端也可以作为服务器。充当客户端更为常见。构建客户端的第一步是创建套接字。之后可以从套接字获取流。

本节构建一个非常简单的客户端，它首先连接到端口，然后转储一个字符串并监听响应。它打印响应然后断开连接。

开始之前，请确保 php_network.h 已包含在扩展中。
