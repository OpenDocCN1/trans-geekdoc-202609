
放入一个类中。然后，setClass() 为 SOAP 扩展提供要使用的类的名称。

```
<?php
$soap = new SoapServer(
    'AddService.wsdl',
    array('uri' => 'http://php.phrasebook.org/')
);
$soap->setClass('ServiceClass');
$soap->handle();

class ServiceClass {
    function add($a, $b) {
        return $a + $b;
    }
}
?>
```

## 使用 PHP 5 的 SOAP 扩展消费 Web 服务

只要您有 WSDL 描述，消费再次变得很容易。此代码调用 Web 服务，并且还捕获任何错误，这得益于 PHP 5 的 try-catch 机制。

```
<?php
$soap = new SoapClient('AddService.wsdl');
try {
    $result = $soap->add(47, 11);
    echo "47 + 11 = $result";
} catch (SoapFault $e) {
    echo "Error: {$e->faultstring}";
}
?>
```

## 提示

为了提高性能，PHP 5 的 SOAP 扩展默认缓存 WSDL。以下是 php.ini-recommended 中的标准设置：

```
[soap]
; Enables or disables WSDL caching feature.
soap.wsdl_cache_enabled=1
; Sets the directory name where SOAP extension will put cache files.
soap.wsdl_cache_dir="/tmp"
; (time to live) Sets the number of seconds
; while cached file will be used
; instead of original one.
soap.wsdl_cache_ttl=86400
```

在开发 Web 服务并且可能更改 WSDL 时，这当然是显而易见的。因此，在开发期间将 soap.wsdl_cache_enabled 设置为 Off，但在生产服务器上将其打开。

## 使用有史以来最糟糕的缩写：AJAX

Wikipedia 列出了“Ajax”一词十多种不同的含义，包括荷兰的一支足球球队、荷马《伊利亚特》中的两个人物以及一种家用清洁产品。然而，自几个月前以来，AJAX 也代表“异步 JavaScript + XML”。该技术远非新事物（底层技术，即 JavaScript 中的 XML HTTP 请求，受最近版本的 Internet Explorer 以及包括 Firefox、Safari 和 Konqueror 在内的 Mozilla 浏览器支持——此外，对于此，XML 根本不是必需的），但只有在创造了这个真正愚蠢的术语之后，人们才真正开始使用它。

基本原则是 JavaScript 现在能够调用远程服务器然后处理其返回值，而无需重新加载整个页面。当然，这与 PHP 关系不大；然而，一些 AJAX 类使从 PHP 中使用 AJAX 变得非常容易。

本书的这一最后章节展示了“AJAX”的一个非常简短的演示。本章节使用 Sajax 工具包（S 代表 simple）可在 http://www.modernmethod.com/sajax/ 获取。

此示例的完整代码相当长，因为同时需要 PHP 和 JavaScript。首先，我们需要服务器端逻辑。为此，加载了 Sajax 工具包，它作为单个 PHP 文件提供。然后我们“导出”（注册）所有希望从客户端使用的 PHP 函数。以下示例有一个小型函数，用于生成随机 RGB 颜色。

```
<?php
    require_once 'Sajax.php';

    sajax_init();
    sajax_export('randomColor');
    sajax_handle_client_request();

    function randomColor() {
        $color = '#';
        for ($i=0; $i<3; $i++) {
            $color .= dechex(rand(0, 255));
        }
        return $color;
    }
?>
```

*服务器端应用程序部分（ajax.php；摘录）*

在客户端，对 (PHP) 函数 `sajax_show_javascript()` 的调用完成了大部分工作——它创建了一些 JavaScript 代码行，在后台处理对 Web 服务器的请求。然后，所有之前注册的 PHP 函数都可以在客户端通过在函数名称前加上 `x_` 来调用。作为参数，您必须提供回调函数的名称；当服务器端响应请求时，该函数将被调用。

以下代码每五秒调用一次 `randomColor()` PHP 函数，然后以此随机颜色写入文本——全部无需服务器往返！图 9.5 显示了结果。

```
<script language="JavaScript" type="text/javascript">
    <!--
<?php
    sajax_show_javascript();
?>
    changeColor();
    setInterval('changeColor()', 5000);

    function changeColor() {
        x_randomColor(randomColor_callback);
    }

    function randomColor_callback(result) {
        var text = '<span style="color: ' + result + '">What a dumb acronym ...</span>';
        document.getElementById('output').innerHTML =
            text;
    }
//--></script>
...
<div id="output"></div>
```

客户端应用程序部分（ajax.php；摘录）

![](img/1e6d362f187af50011d2666ddaa68739_292_0.png)

Figure 9.5  使用 JavaScript 和 PHP 显示的文本。

## PEAR 提供了什么？

除了本章提到的几个模块外，以下 PEAR 包在通过 PHP 与他人连接时提供的功能可能有所帮助：

- PEAR 的 HTTP 类别提供了一些相关包，包括 HTTP、HTTP_Client、HTTP_Header、HTTP_Request 和 HTTP_Server。
- 同样，您可以在 Networking 类别中找到有用的包，包括 Net_FTP、Net_IMAP 和 Net_Socket。
- PEAR 的 Services 类别包含多个类，它们为众所周知的 Web 服务提供易于使用的接口。

## 索引

### 符号

- *(asterisk), 25
- *(星号), 25
- \ (backslash), 26
- \ (反斜杠), 26
- ^ (caret), 24
- ^ (插入符号), 24
- $ (dollar sign), 25
- $ (美元符号), 25
- . (dot), 26
- . (点), 26
- " (double primes), 69
- " (双引号), 69
- | (pipe), 25
- | (管道), 25
- ? (question mark), 25
- ? (问号), 25
- [...] special character, 25
- [...] 特殊字符, 25
- + (plus sign), 25
- + (加号), 25
- !== operator, 23
- !== 运算符, 23
- == operator, 6
- == 运算符, 6
- === compare operator, 23
- === 比较运算符, 23
- === operator, 6-7
- === 运算符, 6-7
- 401 status code, 165
- 401 状态码, 165

### A

- access
  - file access
    - PHP built-in class, 191-192
    - PHP 内置类, 191-192
    - relative paths for, 179-180
    - 相对路径, 179-180
    - security traps, 181
    - 安全陷阱, 181
- addslashes() function, 228
- addslashes() 函数, 228
- Advanced Encryption Standard (AES), 13
- 高级加密标准 (AES), 13
- AJAX, 285-287
- AJAX, 285-287
- ajax.php, 286-287
- ajax.php, 286-287
- array() function, 37
- array() 函数, 37
- arrays
  - applying effects to elements, 59-62
  - 对元素应用效果, 59-62
  - converting
    - strings to, 45-46
    - 字符串到数组, 45-46
    - into strings, 46
    - 转为字符串, 46
    - into variables, 45
    - 转为变量, 45
  - creating, 37-38
  - 创建, 37-38
  - filtering, 62-63
  - 过滤, 62-63
  - looping through
    - associative arrays, 40-41
    - 关联数组, 40-41
    - nested arrays, 41-44
    - 嵌套数组, 41-44
    - numerical arrays, 39-40
    - 数值数组, 39-40
  - nesting, 38
  - 嵌套, 38
  - random elements, getting, 63-64
  - 获取随机元素, 63-64
  - randomizing elements, 64
  - 随机化元素, 64
  - sorting
    - alphabetically, 47-48
    - 按字母顺序, 47-48
    - associative arrays, 49-50
    - 关联数组, 49-50
    - natural sorting, 54-55
    - 自然排序, 54-55
    - nested arrays, 50-51
    - 嵌套数组, 50-51
    - nested associative arrays, 52-54
    - 嵌套关联数组, 52-54
    - QuickSort algorithm, 56
    - QuickSort 算法, 56
    - special language characters, 57-58
    - 特殊语言字符, 57-58
- array_filter() function, 62-63
- array_filter() 函数, 62-63
- array_map() function, 59
- array_map() 函数, 59
- array_multisort() function, 51
- array_multisort() 函数, 51
- array_rand() function, 63-64
- array_rand() 函数, 63-64
- array_walk() function, 61
- array_walk() 函数, 61
- arsort() function, 49
- arsort() 函数, 49
- ASCII codes, protecting email addresses, 17-19
- ASCII 代码，保护电子邮件地址, 17-19
- asort() function, 49
- asort() 函数, 49
- associative arrays
  - looping through, 40-41
  - 循环遍历, 40-41
  - sorting, 49-50
  - 排序, 49-50
- attacks
  - directory traversal, 181
  - 目录遍历, 181
- Auth package PEAR), 167
- Auth 包 PEAR), 167
- authentication
  - session management, 162-163
  - 会话管理, 162-163
  - without sessions, 164
  - 无会话, 164

### B-C

- basename() function, 180
- basename() 函数, 180
- bzclose() function, 195-196
- bzclose() 函数, 195-196
- Bzip2 archives, 194-196
- Bzip2 归档, 194-196
- bzopen() function, 195-196
- bzopen() 函数, 195-196
- bzread() function, 196
- bzread() 函数, 196
- bzwrite() function, 195-196
- bzwrite() 函数, 195-196
- check boxes, preselecting, 107
- 复选框，预选, 107
- checkdate() function, 76
- checkdate() 函数, 76
- checksumming strings, 14, 16
- 字符串校验和, 14, 16
- chr() function, 18
- chr() 函数, 18
- closing
  - files, 172
  - 文件, 172
  - sessions, 153
  - 会话, 153
- compareChar() function, 58
- compareChar() 函数, 58
- comparing strings, 6
- 比较字符串, 6
- compress.bz2://, 194-196
- compress.bz2://, 194-196
- compress.zlib://, 193
- compress.zlib://, 193
- compression
  - Bzip2 archives, 194-196
  - Bzip2 归档, 194-196
  - streams, 192-194
  - 流, 192-194
  - ZIP archives, 193-194
  - ZIP 归档, 193-194
- configureWSDL() method, 271
- configureWSDL() 方法, 271
- connecting to
  - Firebird, 231-232
  - Firebird, 231-232
  - FTP servers, 260-262
  - FTP 服务器, 260-262
  - MSSQL/MSDE, 226-227
  - MSSQL/MSDE, 226-227
  - MySQL, 201
  - MySQL, 201
  - MySQLi, 202-203
  - MySQLi, 202-203
  - Oracle, 221-222
  - Oracle, 221-222
  - PostgreSQL, 216
  - PostgreSQL, 216
  - SQLite, 211-212
  - SQLite, 211-212
- converting
  - arrays
    - into strings, 46
    - 转为字符串, 46
    - into variables, 45
    - 转为变量, 45
  - data types, 31-32
  - 数据类型, 31-32
  - strings
    - into arrays, 45-46
    - 转为数组, 45-46
    - into dates, 79-80
    - 转为日期, 79-80
    - into HTML, 9-11
    - 转为 HTML, 9-11
- $_COOKIE array, 133
- $_COOKIE 数组, 133
- Cookie HTTP header, 131
- Cookie HTTP 头, 131
- cookies, 130-132
  - creating, 133, 135
  - 创建, 133, 135
  - deleting, 139
  - 删除, 139
  - domains, setting, 140-142
  - 设置域, 140-142
  - expiry date, setting, 131, 136-138
  - 设置过期日期, 131, 136-138
  - limitations, 130
  - 限制, 130
  - magic quotes, removing, 135
  - 移除 magic quotes, 135
  - prefilling form data from, 102-103
  - 从中预填充表单数据, 102-103
  - raw cookie data, sending, 135
  - 发送原始 cookie 数据, 135
  - reading out, 133
  - 读取, 133
  - saving
    - HTML form data into, 98-100
    - HTML 表单数据到其中, 98-100
  - language preferences, 146-148
  - 语言偏好, 146-148
  - multiple values, 144
  - 多个值, 144
  - specification, 131
  - 规范, 131
  - testing browser support, 142-143
  - 测试浏览器支持, 142-143
- cookietest.php, 142-143
- cookietest.php, 142-143
- copy() function, 190
- copy() 函数, 190
- count() function, 39-41
- count() 函数, 39-41
- Cross-Site Scripting (XSS) attacks
  - HTML markup, removing, 9-11
- 跨站脚本 (XSS) 攻击
  - 移除 HTML 标记, 9-11
- crypt() function, 12-13
- crypt() 函数, 12-13
- CSV files, 182-185
- CSV 文件, 182-185
