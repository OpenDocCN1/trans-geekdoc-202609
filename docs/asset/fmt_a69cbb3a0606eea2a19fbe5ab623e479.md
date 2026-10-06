
| `php_stream_eof` | `php_stream_readdir` |

| `php_stream_getc` | `php_stream_scandir` |

| `php_stream_putc` | 上下文函数 |

| `php_stream_flush` | `php_stream_context_set` |

| `php_stream_puts` | `php_stream_context_free` |

| `php_stream_stat` | `php_stream_context_alloc` |

| `php_stream_set_options` | `php_stream_context_get_option` |

| `php_stream_free` | `php_stream_context_set_option` |

| 复制 | `php_stream_context_get_link` |

| `php_stream_copy_to_mem` | `php_stream_context_set_link` |

| `php_stream_copy_to_stream` | `php_stream_context_del_link` |

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

开始之前，请确保 `php_network.h` 已包含在扩展中。

> 如果你使用的是 Linux 或 UNIX 系统，你可以安装 `tcplisten` 应用程序并将其用作调试客户端的一种方式。

连接到服务器会返回一个 `php_socket_t` 结构：

```
socklen_t size;
php_socket_t socket;
struct timeval tv;

tv.tv_sec = 10;
tv.tv_usec = 0;

socket = php_network_connect_socket_to_host("localhost", 7777, SOCK_STREAM,
    0, &tv, NULL, NULL, NULL, 0, TSRMLS_CC);
if (socket == -1) {
    /* could not connect */
}
```

前面的示例为了简单起见，硬编码为连接到 `localhost` 的 7777 端口。当然，这些值可以是可变的。连接后，就该从套接字获取流了。之后，你可以像使用普通流一样进行读写。

```
php_stream *stream;
stream = php_stream_sock_open_from_socket(socket, 0);
php_stream_write(stream, "Ping\n");
php_printf("Pong: %s", php_stream_get_line(stream, NULL, 0, NULL));
```

当然，在脚本结束时有必要关闭流并释放套接字：

```
php_stream_close(stream);
closesocket(socket);
```

## 构建服务器

PHP 最常见的情况是在本地主机上作为守护进程运行。在 Web 服务器或 Apache 环境中看到 PHP 作为服务器的情况非常罕见。看到 PHP 作为云外部连接的服务器的情况也不常见。然而，这两种情况都是完全可能的。

第一步始终是绑定到套接字。之后，根据模式的不同，将套接字设置为非阻塞可能很有用。PHP 允许套接字接受多个连接。每个连接都有自己的套接字和自己的流。本节中的简单服务器只接受一个连接，可用作上一节客户端的基础服务器。

打开套接字的代码很简单：

```
php_socket_t server;

server = php_network_bind_socket_to_local_addr("127.0.0.1", 7777,
    SOCK_STREAM, NULL, &error,
    TSRMLS_CC);
listen(server, 5);
```

之后有必要监听新的连接。这是一个阻塞套接字，因此它只是等待连接到达并按顺序执行所有操作。非阻塞套接字会创建一个循环，同时查找新连接并从现有连接读取数据。

```
socket = php_network_accept_incoming(server,
    NULL, NULL, NULL, NULL, &tv, NULL,
    &error, TSRMLS_CC);

if (socket == -1) {
    closesocket(server);
    RETURN_NULL();
}

stream = php_stream_sock_open_from_socket(socket, 0);
php_stream_write(stream, "Ping\n", 5);

char *pong;
int pong_len;
spprintf(&pong, &pong_len, "Pong: %s",
    php_stream_get_line(stream, NULL, 0, NULL));
php_stream_write(stream, pong, pong_len);
efree(pong);
```

请注意，通过向 `php_network_accept_incoming` 函数传递额外参数，你可以获得有关连接到服务器的客户端的更多信息。为了简单起见，前面的脚本全部使用 NULL。

关闭套接字和释放流的方式与之前相同。只要记住你可能同时打开多个套接字和许多流，所以一定要全部关闭。

## 错误和警告

PHP 中的所有错误和警告都通过同一个函数输出。然后引擎决定如何显示错误并记录它。你可以通过以下方式之一记录错误并将其显示到标准输出或网页上：

```
php_error(E_WARNING, "Method %s not yet implemented.", method_name);
php_error_docref(NULL, TSRMLS_CC, E_ERROR, "Could not connect to server %s:%i.",
    server_name, port_name);
```

第二个和第四个参数——前面示例中加粗的格式字符串——与 `printf` 相同，因此你可以对其进行替换。

第二个函数如果将第一个参数传递为 NULL，也会自动处理将当前函数信息放入错误中。它在适当时也会突出显示 HTML。由于增加了这些功能，第二种方法在几乎所有情况下都是首选。一个值得注意的例外是在初始化和关闭期间，此时没有任何活动的函数或页面。

错误类型的可能值如下：

- `E_ERROR`

- `E_WARNING`

- `E_NOTICE`

- `E_PARSE`

- `E_CORE_ERROR`

- `E_CORE_WARNING`

- `E_USER_ERROR`

- `E_USER_WARNING`

- `E_USER_NOTICE`

- `E_STRICT`

- `E_RECOVERABLE_ERROR`

- `E_DEPRECATED`

- `E_USER_DEPRECATED`

列表中前三个在扩展中是最常见的。虽然不常见也不推荐，但也可以直接输出到错误日志。这是通过 `php_error_log` 函数完成的：

```
php_error_log(0, "Message", NULL, NULL, TSRMLS_CC);
```

错误日志函数与 PHP 中的对应函数相同。它不会向屏幕输出任何内容，也不包含任何文件或行信息。该函数还接受所有相同的附加参数，允许错误通过电子邮件发送或输出到不同的日志文件。

前面的示例使用 0 输出到错误日志。第一个参数的其他可能选项如下：

- 值为 1：通过电子邮件发送。使用第三个参数作为电子邮件地址字符串，第四个参数作为可选邮件头。

- 值为 2：通过 TCP/IP 发送。第三个参数是 `host:port` 对。

- 值为 3：保存到第三个参数指定的文件中。

## 数组和哈希表

本章已经涵盖了 Boolean、long、double 和 string 数据类型。缺少的两个重要内容是数组和哈希表。首先，正如你可能猜到的那样，这两者是相同的。数组是按数字索引的，而纯哈希表则像关联数组一样，可以通过键引用。

尽管两者极其相似并且共享相同的数据类型，但它们各自有一组有用的函数来创建、读取和修改它们。数组稍微简单一点，因此先介绍数组。

## 构建和访问数组

有许多函数可用于构建数组。在所有情况下，首先需要获取数组的句柄。有两种可能的情况。一种是 `zval` 已存在，需要获取哈希表对象，另一种是应该创建一个新的哈希表。

在 `zval` 中创建新的数组/哈希表如下所示：

```
zval *new_array;
array_init( new_array );
```

基于 `zval` 访问像刚才创建的那样的现有哈希表如下所示：

```
HashTable *hash;
hash = Z_ARRVAL_P( new_array );
```

这是本书中第一次看到 `HashTable` 数据类型。数组在 `zval` 内部初始化，然后被哈希表检索并指向。一旦哈希表被检索或创建，就可以在其中添加或删除新值。数组有三种基本情况，它们是：

- 在特定索引处添加

- 使用特定键

- 添加到下一个可用索引

这三个函数非常相似：

```
add_assoc_double( new_array, "key_name", 3.14 );
add_index_double( new_array, 3 /* add at index 3 */, 3.14 );
add_next_index_double( new_array, 3.14 );
```

这段代码显示了每个函数的 `double` 版本。除了字符串之外，还有针对所有其他数据类型的函数。这些数据类型在本章中已经多次提到，但为了回顾，它们是：

- bool

- double

- long

- null

- resource

- string and stringl (takes a length)

- zval

此外，每个关联数组函数还都有一个扩展版本，在键之后接受一个额外的长度参数，从而允许使用二进制安全的键。到现在应该很清楚了，只要函数接受字符串长度，它总是作为整数紧跟在字符串之后传递。

所有向数组添加值的函数——直接添加 `zval` 的情况除外——都会创建一个新的 `zval`。添加值后立即尝试获取它效率很低。对于需要稍后引用创建的 `zval` 的情况，还有另一组函数：

```
zval *new_item;
add_get_next_index_double( new_array, 3.14, new_item);
```

The `add_get_*` functions exist for every type of indexing and every type of data except `zval`, where it wouldn't make any sense. Extended versions also exist that allow string lengths to be specified for associative array keys.

The downloadable code for this book has some additional examples for using arrays.

## 访问和修改哈希表

如前所述，所有数组都是哈希表，因此按定义，所有作用于哈希表的函数也适用于数组。事实上，前一节中的所有函数都只是围绕哈希表的易于使用的包装器。然而，直接访问哈希表通常很有用。

哈希表具有额外的好处，例如能够检查键是否存在，并一次性将函数应用于整个哈希。然而，也许最有用的功能是模拟 `foreach` 循环。回顾完第 2 章中的迭代器后，这段代码应该相当熟悉：

```
HashTable *hash = ...
zval **data;

for ( zend_hash_internal_pointer_reset_ex(hash, &pointer);
    zend_hash_get_current_data_ex(hash, (void **) &data, &pointer ) == SUCCESS;
    zend_hash_move_forward_ex(hash, &pointer) ) {
    /* the zval data is filled with the current hash value */
}
```

注意 `data` 变量的双指针。访问时请确保使用 `_PP` 宏，而不是以 `_P` 结尾的宏。你也可以通过使用 `zend_hash_num_elements( hash )` 来获取哈希中的元素数量。

不需要遍历哈希表来执行常见的操作，例如查找与键关联的值以及检查键是否存在。如果知道键，在哈希表中查找元素是相当简单的：

```
zend_hash_find( hash, key, strlen(key), (void **)&data );
```

`data` 就像之前一样是一个指向 `zval` 的双指针。如果知道索引，查找方式类似：

```
zend_hash_index_find( hash, 3 /* index of 3 */, (void **)&data );
```

最后，检查键是否存在的代码如下所示：

```
int exists;
exists = zend_hash_exists( hash, key, strlen(key) );
exists = zend_hash_index_exists( hash, 3 /* index of 3 */ );
```

哈希表在 PHP 中无处不在。它们是用于从全局值到许多 API 函数的返回值等一切事物的核心概念，因此非常重要的是要理解关于它们的方方面面。

## 对象和接口

本章的第一部分解释了如何使用 `CodeGen_PECL` 工具定义类。本节解释如何从头创建类和接口。

同样重要的是，本节回顾了如何检查类、在运行时修改它，以及访问其属性和方法。到本节结束时，你应该能够创建一个扩展，该扩展可以直接从传递给函数的对象中访问数据。

## 创建类

类的创建方式与基本扩展和函数非常相似。它们包含自己的方法表并有一套自己的宏；然而，其中大多数应该看起来很熟悉。

## 类定义、继承和命名空间

至少需要一个类入口指针、一个方法表和初始化代码。最佳实践是将所有初始化放在一个函数中，以便从 `MINIT` 函数调用，但也可以直接将所有代码放在 `MINIT` 中，如以下步骤所示：

- 1. 在 C 文件中定义类入口指针：

- 2. 下一步是定义方法表，它与扩展函数表有着不偶然的相似之处。即使为空，方法表也必须存在。空的方法表如下所示：

- 3. 类入口指针已定义，但目前为空。可以创建一个简单的初始化函数，然后从 `MINIT` 调用。这是一个非常简单的类，但从这里开始类只会变得更大，因此始终将功能分离出来是一个好主意。

```
static zend_class_entry *helloworld_ce_ptr = NULL;
```

类入口是一个结构，用于存储有关类的信息，以便在初始化实例和访问对象时由引擎使用。它包括用于方法和属性的多个哈希表，以及专门用于魔术方法的特殊指针。

```
static zend_function_entry helloworld_methods[] = {
  { NULL, NULL, NULL }
}
```

```
zend_class_entry ce;
INIT_CLASS_ENTRY(ce, "helloworld", helloworld_methods);
helloworld_ce_ptr = zend_register_internal_class( &ce );
```
