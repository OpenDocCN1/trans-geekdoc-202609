
`json_encode` 函数将 PHP 数组（或自 PHP 5.4 起实现了 `JsonSerializable` 接口的对象）转换为 JSON 编码的字符串。成功时返回 JSON 编码的字符串，失败时返回 `FALSE`。

![](img/Image00769.jpg)

编码过程中，PHP 数据类型字符串、整数和布尔值将转换为其 JSON 对应类型。关联数组编码为 JSON 对象，而使用默认参数调用时，索引数组编码为 JSON 数组。（除非数组键不是从 0 开始的连续数字序列，在这种情况下数组将被编码为 JSON 对象。）

![](img/Image00770.jpg)

输出：

![](img/Image00771.jpg)

```
{ "name" : "Jeff" , "age" : 20 , "active" : true , "colors" :[ "red" , "blue" ], "values" :{ "0" : "foo" , "3" : "bar" }}
```

### 参数

自 PHP 5.3 起，`json_encode` 的第二个参数是一个位掩码，可以是以下一个或多个常量。

与任何位掩码一样，它们可以通过二进制或运算符 `|` 组合。

#### PHP 5.x 版本 ≥ 5.3 `JSON_FORCE_OBJECT`

强制创建对象而不是数组。

![](img/Image00772.jpg)

输出：

![](img/Image00773.jpg)

#### `JSON_HEX_TAG`、`JSON_HEX_AMP`、`JSON_HEX_APOS`、`JSON_HEX_QUOT`

确保编码期间进行以下转换：

| 常量 | 输入 | 输出 |
| --- | --- | --- |
| `JSON_HEX_TAG` | `<` | `\u003C` |
| `JSON_HEX_TAG` | `>` | `\u003E` |
| `JSON_HEX_AMP` | `&` | `\u0026` |
| `JSON_HEX_APOS` | `'` | `\u0027` |
| `JSON_HEX_QUOT` | `"` | `\u0022` |

![](img/Image00774.jpg)

```
$array = [ "tag" => "<>" , "amp" => "&" , "apos" => "'" , "quot" => "\"" ];
echo json_encode ( $array );
echo json_encode ( $array , JSON_HEX_TAG | JSON_HEX_AMP | JSON_HEX_APOS | JSON_HEX_QUOT );
```

输出：

```
{ "tag" : "<>" , "amp" : "&" , "apos" : "'" , "quot" : "\"" }
```

![](img/Image00775.jpg)

```
{ "tag" : "\u003C\u003E" , "amp" : "\u0026" , "apos" : "\u0027" , "quot" : "\u0022" }
```

#### PHP 5.x 版本 ≥ 5.3 `JSON_NUMERIC_CHECK`

确保数字字符串转换为整数。

![](img/Image00776.jpg)

输出：

![](img/Image00777.jpg)

```
[ "23452" ,23452]
[23452,23452]
```

#### PHP 5.x 版本 ≥ 5.4 `JSON_PRETTY_PRINT`

使 JSON 易于阅读。

![](img/Image00778.jpg)

输出：

![](img/Image00779.jpg)

#### `JSON_UNESCAPED_SLASHES`

输出中包含未转义的 `/` 正斜杠。

![](img/Image00780.jpg)

输出：

![](img/Image00781.jpg)

```
{ "filename" : "example.txt" , "path" : "\/full\/path\/to\/file" }
{ "filename" : "example.txt" , "path" : "/full/path/to/file" }
```

#### `JSON_UNESCAPED_UNICODE`

输出中包含 UTF8 编码字符，而不是 `\u` 编码的字符串。

![](img/Image00782.jpg)

输出：

![](img/Image00783.jpg)

#### PHP 5.x 版本 ≥ 5.5 `JSON_PARTIAL_OUTPUT_ON_ERROR`

遇到无法编码的值时允许编码继续进行。

![](img/Image00784.jpg)

输出：

![](img/Image00785.jpg)

```
{ "file" : null , "name" : "foo.txt" }
```

#### PHP 5.x 版本 ≥ 5.6 `JSON_PRESERVE_ZERO_FRACTION`

确保浮点数始终作为浮点数编码。

![](img/Image00786.jpg)

输出：

![](img/Image00787.jpg)

#### PHP 7.x 版本 ≥ 7.1 `JSON_UNESCAPED_LINE_TERMINATORS`

与 `JSON_UNESCAPED_UNICODE` 结合使用时，恢复旧版 PHP 的行为，不转义字符 U+2028 LINE SEPARATOR（行分隔符）和 U+2029 PARAGRAPH SEPARATOR（段分隔符）。尽管这些字符在 JSON 中有效，但它们在 JavaScript 中无效，因此 `JSON_UNESCAPED_UNICODE` 的默认行为在 7.1 版本中发生了变化。

![](img/Image00788.jpg)

```
$array = [ "line" => "\xe2\x80\xa8" , "paragraph" => "\xe2\x80\xa9" ];
echo json_encode ( $array , JSON_UNESCAPED_UNICODE );
echo json_encode ( $array , JSON_UNESCAPED_UNICODE | JSON_UNESCAPED_LINE_TERMINATORS );
```

输出：

![](img/Image00789.jpg)

![](img/Image00790.jpg)

### 第 31.3 节：调试 JSON 错误

当 `json_encode` 或 `json_decode` 无法解析提供的字符串时，将返回 `false`。PHP 本身不会引发任何错误或警告；责任在于用户使用 `json_last_error()` 和 `json_last_error_msg()` 函数来检查是否发生错误，并在应用程序中做出相应处理（调试、显示错误消息等）。

以下示例展示了处理 JSON 时的常见错误，即由于传递了错误的 UTF-8 编码字符串等原因，导致 JSON 字符串解码/编码失败。

![](img/Image00791.jpg)

#### `json_last_error_msg`

`json_last_error_msg()` 返回尝试编码/解码字符串时发生的最后一个错误的人类可读消息。

![](img/Image00792.jpg)

即使未发生错误，此函数始终返回 `string`。

默认的非错误字符串为 `No Error`。

如果发生其他（未知）错误，将返回 `false`。

在循环中使用时要小心，因为 `json_last_error_msg()` 将在每次迭代中被覆盖。

你应该仅使用此函数获取用于显示的消息，而不应在控制语句中用它进行判断。

![](img/Image00793.jpg)

此函数在 PHP 5.5 之前不存在。以下是一个 polyfill 实现：

![](img/Image00794.jpg)

```
if (! function_exists ( 'json_last_error_msg' )) {
     function json_last_error_msg () {
         static $ERRORS = array (
             JSON_ERROR_NONE => 'No error' ,
             JSON_ERROR_DEPTH => 'Maximum stack depth exceeded' ,
             JSON_ERROR_STATE_MISMATCH => 'State mismatch (invalid or malformed JSON)' ,
             JSON_ERROR_CTRL_CHAR => 'Control character error, possibly incorrectly encoded' ,
             JSON_ERROR_SYNTAX => 'Syntax error' ,
             JSON_ERROR_UTF8 => 'Malformed UTF-8 characters, possibly incorrectly encoded'
         );
         $error = json_last_error ();
```

![](img/Image00795.jpg)

#### `json_last_error`

`json_last_error()` 返回一个整数，映射到 PHP 提供的预定义常量之一。

| 常量 | 含义 |
| --- | --- |
| `JSON_ERROR_NONE` | 未发生错误 |
| `JSON_ERROR_DEPTH` | 超过最大堆栈深度 |
| `JSON_ERROR_STATE_MISMATCH` | 无效或格式错误的 JSON |
| `JSON_ERROR_CTRL_CHAR` | 控制字符错误，可能编码不正确 |
| `JSON_ERROR_SYNTAX` | 语法错误（自 PHP 5.3.3 起） |

##### JSON 错误常量

| 常量 | 描述 |
| :--- | :--- |
| `JSON_ERROR_UTF8` | UTF-8 字符格式错误，可能编码不正确（自 PHP 5.5.0 起） |
| `JSON_ERROR_RECURSION` | 待编码的值中存在一个或多个递归引用 |
| `JSON_ERROR_INF_OR_NAN` | 待编码的值中存在一个或多个 NAN 或 INF 值 |
| `JSON_ERROR_UNSUPPORTED_TYPE` | 给定了一个无法编码的类型的值 |

# 第 31 章：JSON 处理（续）

### 第 31.4 节：在对象中使用 `JsonSerializable`

**PHP 5.x 版本 ≥ 5.4**

当你构建 REST API 时，可能需要减少传递给客户端应用程序的对象信息量。为此，本例演示了如何使用 `JsonSerializable` 接口。

在本例中，类 `User` 实际上扩展了一个假设的 ORM 的数据库模型对象。

![Image00796.jpg](img/Image00796.jpg)

#### `jsonSerialize`

通过提供 `jsonSerialize()` 方法，向类添加 `JsonSerializable` 实现。

![Image00797.jpg](img/Image00797.jpg)

#### `json_encode`

现在在你的应用程序控制器或脚本中，当将对象 `User` 传递给 `json_encode()` 时，你将获得 `jsonSerialize()` 方法返回的 JSON 编码数组，而不是整个对象。

![Image00798.jpg](img/Image00798.jpg)

将返回：

![Image00799.jpg](img/Image00799.jpg)

*属性值示例。*

这既减少了从 RESTful 端点返回的数据量，又允许从 JSON 表示中排除对象属性。

##### 配合 `json_encode` 使用私有和受保护属性

为了避免使用 `JsonSerializable`，也可以使用私有或受保护属性来隐藏 `json_encode()` 输出中的类信息。该类随后无需实现 `\JsonSerializable`。

![Image00800.jpg](img/Image00800.jpg)

![Image00801.jpg](img/Image00801.jpg)

### 第 31.5 节：JSON 头部与返回响应

通过添加内容类型为 JSON 的头部：

![Image00802.jpg](img/Image00802.jpg)

![Image00803.jpg](img/Image00803.jpg)

该头部的存在是为了让你的应用程序能够检测返回了什么数据以及应如何处理它。请注意：内容头部只是关于返回数据类型的信息。

如果你使用的是 UTF-8，可以使用：

![Image00804.jpg](img/Image00804.jpg)

#### jQuery 示例

![Image00805.jpg](img/Image00805.jpg)

## 第 32 章：SOAP 客户端

### 参数详情

| 参数 | 描述 |
| :--- | :--- |
| `$wsdl` | WSDL 的 URI，若使用非 WSDL 模式则为 `NULL` |
| `$options` | `SoapClient` 的选项数组。非 WSDL 模式要求设置 `location` 和 `uri`，所有其他选项均为可选。可能的值见下表。 |

### 第 32.1 节：WSDL 模式

首先，创建一个新的 `SoapClient` 对象，传入 WSDL 文件的 URL，并可选择性地传入一个选项数组。

![Image00806.jpg](img/Image00806.jpg)

![Image00807.jpg](img/Image00807.jpg)

### 第 32.2 节：非 WSDL 模式

这与 WSDL 模式类似，不同之处在于我们将 `NULL` 作为 WSDL 文件传入，并确保设置了 `location` 和 `uri` 选项。

![Image00808.jpg](img/Image00808.jpg)

### 第 32.3 节：类映射

在 PHP 中创建 SOAP 客户端时，你也可以在配置数组中设置 `classmap` 键。此 `classmap` 定义了 WSDL 中定义的哪些类型应映射到实际的类，而不是默认的 `StdClass`。这样做的原因是你可以获得这些类的字段和方法调用的自动补全功能，而不必猜测常规 `StdClass` 上设置了哪些字段。
