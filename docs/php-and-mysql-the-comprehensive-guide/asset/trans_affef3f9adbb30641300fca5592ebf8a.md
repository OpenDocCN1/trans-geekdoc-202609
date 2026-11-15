

响应本身仍需检查。`file_get_contents()` 在调用失败时返回 `false`。随后必须使用 `json_decode()` 转换响应，在本例中，数组的第一个元素即为响应。下面的清单展示了完整脚本；输出如图 27.4 所示。

```php
<?php
$method = 'square';
$a = 24;
$parameter = [$a];
$url = 'http://localhost/php/rest_server.php?method=' .
urlencode($method) . '&parameter=' . urlencode(json_encode($parameter));
$answer = file_get_contents($url);
if ($answer == false) {
$result = json_decode($answer)[0];
print "The square of $a is: ". $result;
}
?>
```

## 清单 27.2 REST 客户端 ("rest_client.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_754_0.png)

## 图 27.4 平方也可使用 REST 计算

解码 JSON 时，过去您始终需要依赖有效 JSON 或自行编写验证函数。在 PHP 8.3 中，一项新的验证函数成为 PHP 核心的一部分：`json_validate(JSON string, depth, flag)`。它包含三个参数：

- JSON 字符串是该方法的唯一必填参数，包含待验证的字符串。PHP 在此处将 UTF-8 用作字符串字符编码。
- Depth 是可选规范，表示执行验证的嵌套深度。
- 对于 flags，目前只有一个选项，即 `JSON_INVALID_UTF8_IGNORE`，用于忽略无效的 UTF-8 字符。

下面的清单展示了一个简单示例。

```php
<?php
$json = '{
"shares" : {
"Members" : 120,
"Rheinwerk" : 504
}
}'; 
var_dump(json_validate($json));
?>
```

## 清单 27.3 JSON ("json_validate.php")

在此例中，结果为 true，因为 JSON 有效。通过像下一个清单中那样进行微小更改，可以快速改变这一点。差异难以察觉；仅在 "Members" 条目后缺少一个逗号。

```php
$json = '{
    "shares" : {
        "Members" : 120
        "Rheinwerk" : 504
    }
}'; 
json_validate($json);
echo json_last_error() . " " . json_last_error_msg();
```

## 清单 27.4 JSON ("json_validate_error.php")

json_validate() 本身不返回任何错误消息。PHP 提供另外两个方法用于此目的：json_last_error() 和 json_last_error_msg()。在此示例中，json_last_error() 返回状态代码 4，而 json_last_error_msg() 返回 "Syntax error" 消息。有关 JSON 错误代码，请参见表 27.1。

| 常量 | 代码 | 说明 |
|---|---|---|
| JSON_ERROR_NONE | 0 | 没有错误。 |
| JSON_ERROR_DEPTH | 1 | JSON 超过了最大深度。 |
| JSON_ERROR_STATE_MISMATCH | 2 | 不是正确的 JSON。 |
| JSON_ERROR_CTRL_CHAR | 3 | CTRL 字符错误。 |
| JSON_ERROR_SYNTAX | 4 | 语法错误——最常见的错误类型。 |
| JSON_ERROR_UTF8 | 5 | 验证 UTF-8 字符时出错。 |
| JSON_ERROR_RECURSION | 6 | JSON 中的递归引用。 |
| JSON_ERROR_INF_OR_NAN | 7 | JSON 包含不是数字或无限的值。 |
| JSON_ERROR_UNSUPPORTED_TYPE | 8 | 值包含不支持的数据类型。 |
| JSON_ERROR_INVALID_PROPERTY_NAME | 9 | 验证属性时出错。 |
| JSON_ERROR_UTF16 | 10 | 不是正确的 UTF-16 字符。 |

表 27.1 JSON 错误代码

## 27.3 nuSOAP

nuSOAP 最令人印象深刻的在于其易用性。您会发现，可以非常快速地搭建自己的服务器。

### 27.3.1 服务器

首先，您需要一个服务器，以便测试提供方（服务器）和消费方（客户端）之间的通信。让我们分析一下代码：

- 1. 首先，您需要相应的 nuSOAP PHP 文件。它包含服务器和客户端的功能，下载并解压 ZIP 后可在 *lib* 目录中找到：

```
require_once "lib/nusoap.php";
```

- 2. 然后创建一个新的服务器对象。在此使用 register() 注册您想要使用的函数：

```
$server = new nusoap_server();
$server->register("square");
```

> **提示**
>
> 您也可以将多个函数分配给 SOAP 服务器。但请注意：如果您希望实现完全互操作性，应将自己限制为一个函数，因为某些 SOAP 实现仅能理解一个函数！Flash Web 服务扩展就是一个示例，几乎无法让它调用多个方法。

- 3. 实际的 square() 函数非常简单。它接收一个参数。然后检查是否传递了该参数且包含值。如果是，则返回平方。否则，服务器会返回 SOAP 错误，如清单 27.5 所示。

```php
function square($a) {
if ($a != null && trim($a) != "") {
    $square = $a * $a;
    return $square;
} else {
    return new soap_fault("Client", "", "No parameter");
}
}
```

- 4. 现在服务器仍需响应调用。为此，它需要调用的 POST 数据。我们使用新的 php://input 功能而非 $HTTP_RAW_POST_DATA 来读取数据。此处的检查有助于避免在直接调用时生成错误消息。使用 service(data) 方法执行服务器：

```
$data = file_get_contents("php://input") ?? "";
$server->service($data);
```

就这么多。下面的清单展示了完整代码。

```php
<?php
function square($a) {
if ($a != null && trim($a) != "") {
    $square = $a * $a;
    return $square;
} else {
    return new soap_fault("Client", "", "No parameter");
}
}

require_once "lib/nusoap.php";
$server = new nusoap_server();

$server->register("square");
$data = file_get_contents("php://input") ?? "";
$server->service($data);

?>
```

## 清单 27.5 一个 nuSOAP 服务器 ("nusoap-server.php")

**注意**

在此示例中，nuSOAP 会自动确定数据类型。不过，您也可以选择手动选取数据类型。为此，请使用 soapval(name, type, value, namespace_value, namespace_type, attributes) 函数。对于名称，也可以输入空字符串。类型即为数据类型；值为实际传输内容。如果您想创建自己的变量和数据类型并告知通信伙伴它们是什么，则应使用命名空间。

### 27.3.2 客户端

接下来我们来看要使用该服务的客户端。它再次像往常一样开始：

- 1. 首先添加 nuSOAP 库：

```
require_once "nusoap.php";
```

- 2. 接下来是客户端调用。您将服务的 URL 作为参数输入：

```
$client = new nusoap_client("http://localhost/php/nusoap_server.php");
```

> 注意
>
> nuSOAP 还提供另外两个方法，即 soap_server() 和 soapclient()，分别用于服务器和客户端。

- 3. 实际方法调用使用 call(method, parameter) 执行。参数作为数组传递：

```
$a = 36;
$answer = $client->call("square", [$a]);
```

- 4. 最后，检查是否发生任何错误。如果一切正常，则显示结果：

```
if ($error = $client->getError()) {
 print "Error: " . $error;
} elseif ($error = $client->fault) {
 print "SOAP error: " . $error;
} else {
   print "The square of $a is " . $answer;
}
```

清单 27.6 展示了完整脚本；输出如图 27.5 所示。

```php
<?php
require_once "lib/nusoap.php";

$a = 36;

$client = new nusoap_client("http://localhost/php/nusoap_server.php");
$response = $client->call("square", [$a]);

if ($error = $client->getError()) {
 print "Error: " . $error;
} elseif ($error = $client->fault) {
 print "SOAP error: " . $error;
} else {
   print "The square of $a is " . $answer;
}
?>
```

## 清单 27.6 带有 nuSOAP 的客户端 ("nusoap_client.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_759_0.png)

## 图 27.5 您已经算好了吗？

### 27.3.3 WSDL

到目前为止，nuSOAP 示例根本不需要 WSDL。但 WSDL 是一个重要元素，尤其是与其他技术实现互操作时。要创建 WSDL，您只需对脚本做一点调整：

- 1. 首先配置 WSDL。为此，为服务指定一个名称（此处为 Square）和一个命名空间：

```
$server->configureWSDL("Square", "http://www.arrabiata.de/nusoap/");
```

- 2. 接下来注册方法。此处函数名称、格式、当前时间和架构命名空间很重要：

```
$server->register("square",
  ["a" => "xsd:int"],
  ["square" => "xsd:int"],
  "http://soapinterop.org/"
);
```

清单 27.7 包含完整代码。

```php
<?php
function square($a) {
  if ($a != null && trim($a) != "") {
    $square = $a * $a;
    return $square;
  } else {
    return new soap_fault("Client", "", "No parameter");
  }
}
```

