
这个示例展示了 Ajax 的一个非常简短的演示。此示例使用可在 www.modernmethod.com/sajax 获取的 Sajax 工具包（S 代表 simple 简单）。有许多 Ajax 库和框架可供选择，因此请随意选择你最喜欢的一个；我们在这里只选择一个简单的，以专注于 Ajax 和 PHP 的结合。

此示例的完整代码相当长，因为同时需要 PHP 和 JavaScript。首先，你需要服务器端逻辑。为此，加载了 Sajax 工具包，它作为单个 PHP 文件提供。然后你“导出”（注册）所有希望从客户端使用的 PHP 函数。以下示例包含一个生成随机 RGB 颜色的小函数：

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

*应用程序的服务器端部分（ajax.php：摘录）*

在客户端，对（PHP）函数 sajax_show_javascript() 的调用完成了大部分工作；它创建了一些 JavaScript 代码行，在后台处理对 Web 服务器的请求。然后，所有之前已注册的 PHP 函数都可以通过在函数名称前加上 x_ 来在客户端调用。你必须提供的一个参数是回调函数的名称；当服务器端响应请求时，该函数将被调用。

以下代码每五秒调用一次 randomColor() PHP 函数，然后以这种随机颜色写入文本——全部无需服务器往返！图 11.5 显示了结果：

```
<script type="text/javascript">
<?php
sajax_show_javascript();
?>
changeColor();
setInterval(changeColor, 5000);

function changeColor() {
    x_randomColor(randomColor_callback);
}

function randomColor_callback(result) {
    var text = '<span style="color: ' + result + '">A colorful acronym ...</span>';
    document.getElementById('output').innerHTML =
    text;
}
</script>
...
<div id="output"></div>
```

应用程序的客户端部分（ajax.php；摘录）

![](img/2862989e5dc7f1b1d0bc64321737f084_327_0.png)

图 11.5 文本出现，感谢 JavaScript 代码调用 PHP

## 与服务器交换数据

在前面的示例中，我们与服务器交换的数据相当简单——一个简单的字符串。然而，在实际应用中，我们需要从客户端发送到服务器并返回的往往是更复杂的数据。XML 可用作交换格式，但它臃肿，因此不适合高性能应用。PHP 的 serialize() 和 unserialize() 方法可用于将复杂信息转换为可通过 HTTP 交换的字符串，但 JavaScript 并没有内置的对应功能。

与 JavaScript 进行数据交换的事实标准是 JSON，即 JavaScript 对象表示法。非官方主页 at http://json.org/ 详细解释了该格式，但基本上 JSON 概括了 JavaScript 规范中解释数组的部分。例如，看看这个字符串：

```
[
{"url": "http:\\/\\/json.org\/", "text": "JSON"},
{"url": "http:\\/\\/php.net\/", "text": "PHP"}
]
```

这是在 JavaScript 中可用于定义包含两个关联数组（或对象，正如某些人所称，尽管这些元素实际上并不是对象）的数组的语法。现代浏览器具有将此类字符串轻松转换为真实 JavaScript 值的内置功能（并且针对旧版本也有变通方法），因此 JSON 非常适合 Ajax 应用。

从 5.2 版本开始，PHP 原生支持 JSON。函数 json_encode() 将可序列化的 PHP 值转换为 JSON，而 json_decode() 将 JSON 字符串转换回 PHP 可处理的内容。以下代码基本上创建了前面的 JSON 字符串，只是去除了缩进和额外的空白字符：

```
<?php

class LinkData {
    public $url;
    public $text;
    public function __construct($url, $text) {
        $this->url = $url;
        $this->text = $text;
    }
}

$data = array(
    new LinkData('http://json.org/', 'JSON'),
    new LinkData('http://php.net/', 'PHP')
);

echo json_encode($data);
?>
```

JSON 服务器端点（json.php）

在客户端，JavaScript 代码随后可以调用 PHP 脚本并处理数据。使用像流行的 jQuery（http://jquery.com/）这样的 JavaScript 库时，处理 JSON 数据会相当容易（参见图 11.6）。以下代码以项目符号列表的形式显示 JSON 字符串中包含的信息：

```
<script type="text/javascript" src="http://code.jquery.com/jquery-latest.js"></script>
<script type="text/javascript">
$(function() {
    $.getJSON("json.php", function(data) {
        $.each(data, function(key, value) {
            $("<a>").attr("href", value.url)
                .html(value.text)
                .wrap("<li>")
                .parent()
                .appendTo("ul");
        });
    });
});
</script>
...
<body>
    <ul></ul>
</body>
```

使用 jQuery 的 JSON 客户端（json.html）

![](img/2862989e5dc7f1b1d0bc64321737f084_330_0.png)

图 11.6 JSON 数据被解析，然后作为列表显示，感谢 jQuery 调用 PHP 代码。

## PEAR 提供什么？

除了本章中提到的几个模块外，以下 PHP 扩展和应用程序仓库（PEAR）包在通过 PHP 与他人连接时提供的功能可能很有帮助：

- PEAR 的 HTTP 类别提供了一些相关包，包括 HTTP、HTTP_Header、HTTP_Request2 和 HTTP_Server。
- 同样，你可以在 Networking 类别中找到有用的包，包括 Net_FTP、Net_IMAP 和 Net_Socket。
- PEAR 的 Services 类别包含多个类，它们为知名 Web 服务提供易于使用的接口。

## 索引

### 符号和数字

!= 运算符，比较字符串，26
[...] 特殊字符，在正则表达式中，28
*（星号），在正则表达式中，28
\（反斜杠），在正则表达式中，29
^（插入符号），在正则表达式中，27
$（美元符号），在正则表达式中，27
.（点），在正则表达式中，28
== 运算符，比较字符串，8-10，26
|（管道），在正则表达式中，28
+（加号），在正则表达式中，28
?（问号），在正则表达式中，27
$_COOKIE 数组，170
$_FILES 数组 检索上传文件信息，155
$_GET 数组
访问表单数据，126-127
图形化提交按钮，144
验证必填字段，145
预填充文本字段，131，133-134
预选单选按钮，136
预选选择列表，141-142
读取表单数据，123
$_POST 数组
访问表单数据，126-127
图形化提交按钮，144
验证必填字段，145
预填充文本字段，131，133-134
预选单选按钮，136
预选选择列表，141-142
$_REQUEST 数组，访问表单数据，126-127
401 状态码，198

### A

抽象类，104-107
access，文件访问
  PHP 内置类，221-222
  相对路径，209-210
  安全陷阱，210-211
addslashes() 函数，265
AES（高级加密标准），15
Ajax，313-316
ajax.php，314-315
array() 函数，创建数组，40
array_filter() 函数，66
array_map() 函数，62
array_multisort() 函数，54
array_rand() 函数，67-68
array_walk() 函数，64
arrays
  对元素应用效果，62-65
  转换为变量，47-48
  将字符串转换为数组，48-49
  转换为字符串，49
  创建，40-41
过滤，65-66
用于表单数据，125
循环遍历
  关联数组，43
  嵌套数组，44-47
  数值数组，41-43
嵌套，40
检索随机元素，67-68
排序
  按字母顺序，50-51
  关联数组，51-52
  自然排序，57
  嵌套数组，53-54
  嵌套关联数组，55-56
QuickSort 算法，58
特殊语言字符，59-60
ASCII 代码，保护电子邮件地址，20-22
asort() 函数，52
关联数组
  循环遍历，43
  排序，51-52
attacks，目录遍历，210-211
