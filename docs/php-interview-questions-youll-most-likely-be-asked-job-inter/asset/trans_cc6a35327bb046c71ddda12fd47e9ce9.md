

PHP 内置支持 FTP。ftp_connect、ftp_login、ftp_put、ftp_close 是一些相关函数。也可以使用 PHP cURL 代替。

## 123: 可以使用 PHP 解析 CSV 吗？PHP 对这些有内置支持吗？

答：
PHP 内置支持解析 CSV。它具有 fgetcsv 和 fputcsv 等函数，用于读写 CSV 文件。

## 124: 如何在 PHP 中获取图像大小？

答：
可以在 PHP 中使用 getimagesize() 函数来获取图像大小。

## 125: PHP 脚本有执行时间限制吗？

答：
PHP 脚本的默认时间限制为 30 秒。可以使用 set_time_limit 函数设置时间限制，或在 PHP.ini 中定义 max_execution_time 值。

## 126: PHP 比 C++ 快吗？为什么？

答：
不，PHP 比经过优化的 C++ 程序慢，因为 PHP 是脚本语言且是解释型的，因此比经过优化的 C++ 代码稍慢一些。

## 127: 如果在脚本开始输出数据后才将头信息发送到浏览器，该怎么办？

答：
可以使用 PHP 的输出控制函数来实现此目的。这不会影响使用 header() 和 setcookie() 函数发送的头信息。

## 128: PHP 可与 Oracle 配合使用吗？

答：
可以使用 OCI 将 PHP 与 Oracle 集成。

## 129: 如何得知 PHP.ini 文件的位置？

答：
可以使用 PHPinfo() 函数查找 PHP.ini 文件的位置。

## 130: 如何在运行时增加内存容量？

答：
可以使用 ini_set('memory_limit', '15M') 适当设置内存。

## 131: 如何在 PHP 中处理 Unicode 字符？

答：
PHP 具有 Utf8_encode() 和 utf8_decode() 等函数，可用于读写 Unicode 字符。

## 132: 如何判断请求是通过 SSL 发送的？

答：
可以测试 $_SERVER['HTTPS'] 的值，如果为‘ON’，则表明请求是通过 SSL 发送的。

## 133: 如何使用 PHP 发送 XML-RPC 请求？

答：
XML-RPC 允许 PHP 向 Web 服务器发起函数调用，即使这些服务器不使用 PHP。检索到的数据随后会自动转换为 PHP 变量，供您的应用程序使用。PHP 内置支持 XML-RPC。

## 134: 如何使用 PHP 读取环境变量？

答：
可以使用 $_ENV 超全局变量读取环境变量。例如 $_ENV['user']

## 135: 什么是按引用返回？这样做有什么好处？

答：
按引用返回可以避免创建重复变量。此处需要使用 =& 而不是通常的赋值运算符 (=)。

## 136: PHP 中如何对数组进行序列化？

答：
PHP 使用 serialize() 和 unserialize 函数来处理序列化。

## 137: 什么是 SQL 注入？

答：
这是一种针对不验证用户提供数据的脚本的攻击类型。当未过滤的数据被传递到 SQL 查询时，会允许用户执行任意 SQL 命令，这是不安全的。

## 138: 在“$a$b”和 $a.$b 之间，哪个速度更快，为什么？

答：
$a.$b 速度更快，因为字符串连接比变量替换更快。

## 139: 如何使用 PHP 构建 HTML 表单？

答：
有一个 PEAR 包，其中包含 HTML_QuickForm 类，可用于构建表单。

## 140: 是否有用于以表格形式显示数据的 PEAR 类？

答：
PEAR 的 HTML_Table 类可用于以表格形式显示数据。

## 141: 如何在网页上显示 PHP 源代码？

答：
可以使用 highlight_string 和 highlight_function 函数以整洁的格式显示 PHP 源代码。

## 142: 如果需要使用 PHP 配置文件（.ini），需要采取什么预防措施？

答：
应避免将配置文件存储在 Web 根目录中。如果必须如此，则需要使用 .htaccess 文件进行保护，并注明谁可以访问该文件。此外，敏感数据应始终加密。

## 143: 什么是电子邮件注入攻击？

答：
当黑客使用电子邮件表单以非预期方式发送电子邮件时，就会发生电子邮件注入攻击。这可能会产生多种影响，例如消耗带宽、被列为垃圾邮件发送者而被拦截等。

## 144: 为网站设置 HTTP 身份验证是否需要 PHP？

答：
不需要，为网站设置 HTTP 身份验证不需要 PHP。

## 145: 如何防止 Web 浏览器缓存网页？

答：
可以使用 PHP 的 header 函数来指定相关网页的缓存副本始终已过期。

## 146: 如何在 PHP 中获取信号量 ID？

答：
PHP 有一个 sem_get() 函数用于获取信号量 ID。

## 147: 如何在 PHP 中绘制一条线？

答：
可以使用 PHP 的 ImageLine() 函数来绘制一条线。

## 148: 如何查找 PEAR 包的信息？

答：
可以使用以下命令查找 PEAR 包的信息 - “Pear remote-info Net_Ping”

## 149: 什么是 PHPDoc？

答：
PHPDoc 是一个用于自动生成 PHP 代码 API 文档的工具。

## 150: 如何考虑夏令时？

答：
可以使用 Zoneinfo 库来正确计算夏令时的影响。

## 151: PHP.ini 中哪一行配置用于启用/禁用 PHP 的文件上传？

答：
此行用于启用 PHP 中的文件上传 - File_uploads = ON。需要在 PHP.ini 中启用此项。

## 152: 什么是 log4PHP？

答：
log4PHP 是 Apache 软件基金会为 PHP 提供的日志框架。

## 153: Web 服务器信息存储在 PHP 的哪里？

答：
$_SERVER 是一个保留的 PHP 变量，包含所有 Web 服务器信息。

## 154: 列出 PHP 中的超全局变量。

答：
$GLOBALS、$_SERVER、$_POST、$_GET、$_FILES、$_COOKIE、$_SESSION、$_REQUEST、$_ENV 是 PHP 中的超全局变量。

## 155: 当 PHP 作为 CGI 运行时，是否提供 HTTP 身份验证？

答：
不，此功能仅在作为 Apache 模块运行时可用。

## 156: 如何使用 PHP 发送电子邮件？

答：
PHP 包含一个名为 mail() 的函数用于发送电子邮件。这使用 SMTP 邮件服务器来发送消息。

## 157: PHP 与 PHP/FI 2.0 有何关系？

答：
PHP 是 PHP/FI 2.0 的继任者。

## 158: 可以使用 PHP 访问 Microsoft Access 数据库吗？

答：
需要安装 Microsoft 的 ODBC 驱动程序才能使用 PHP 访问 Microsoft Access 数据库。

## 159: $_SERVER['HTTP_REFERER'] 可以为空吗？

答：
可以，$_SERVER['HTTP_REFERER'] 可以为空，因为并非所有浏览器都会设置此项。且仅在引荐来源为链接时才需要设置。

## 160: PHP 中有哪些开源购物车可用？

答：
Fishcart、PHPhop、oscommerce 是一些可用的开源购物车。

## 161: md5() 和 crc32() 之间的基本区别是什么？

答：
md5() 生成的哈希长度为 160 位，而 crc32() 为 32 位。

## 162: md5()、crc32()、sha1() 中哪个生成更安全的哈希？

答：
Md5() 生成的哈希比其他更安全。

## 163: 为什么有时更倾向于使用 crc32() 和 sha1() 而不是 md5()？

答：
为了节省空间和计算时间，有时更倾向于使用 crc32() 而不是 md5()。

## 164: 什么是 phpBB？

答：
phpBB 是一个用 PHP 编写的互联网论坛程序（公告板）。它是免费软件。

## 165: 如何避免 PHP_SELF 漏洞？

答：
可以使用 htmlentities() 函数避免 PHP_SELF 漏洞，该函数对 HTML 实体进行编码。这样，用户就无法利用 PHP_SELF 变量，脚本也得到了净化。

## 166: 可以在运行时覆盖 PHP.ini 文件中定义的值吗？

答：
可以使用 ini_set 函数在运行时覆盖 PHP.ini 值。

## 167: PHP 是否支持图形？可以使用 PHP 绘制多边形吗？

答：
可以使用 ImagePolygon、ImageFilledPolygon 等函数在 PHP 中绘制多边形。

## 168: 什么是 PHP 加速器？

答：
PHP 加速器用于提升 PHP 脚本的性能。

