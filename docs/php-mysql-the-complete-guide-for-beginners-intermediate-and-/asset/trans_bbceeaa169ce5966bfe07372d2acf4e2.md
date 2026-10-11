
仅依赖返回值为 `NULL` 来检测错误是不安全的。例如，如果 JSON 字符串仅包含 `"null"`，即使没有发生错误，`json_decode()` 也会返回 `null`。

## 第 31.2 节：编码 JSON 字符串

[`json_encode`](http://php.net/manual/en/function.json-encode.php) 函数将 PHP 数组（或自 PHP 5.4 起实现了 `JsonSerializable` 接口的对象）转换为 JSON 编码的字符串。成功时返回 JSON 编码的字符串，失败时返回 `FALSE`。

![](Image00769.jpg)

编码过程中，PHP 数据类型字符串、整数和布尔值将转换为其 JSON 对应类型。关联数组编码为 JSON 对象，而使用默认参数调用时，索引数组编码为 JSON 数组。（除非数组键不是从 0 开始的连续数字序列，在这种情况下数组将被编码为 JSON 对象。）

![](Image00770.jpg)

输出：

![](Image00771.jpg)

```
{ "name" : "Jeff" , "age" : 20 , "active" : true , "colors" :[ "red" , "blue" ], "values" :{ "0" : "foo" , "3" : "bar" }}
```

### 参数

自 PHP 5.3 起，`json_encode` 的第二个参数是一个位掩码，可以是以下一个或多个常量。

与任何位掩码一样，它们可以通过二进制或运算符 `|` 组合。

#### PHP 5.x 版本 ≥ 5.3 [`JSON_FORCE_OBJECT`](http://php.net/manual/en/json.constants.php#constant.json-force-object)

强制创建对象而不是数组。

![](Image00772.jpg)

输出：

![](Image00773.jpg)

#### [`JSON_HEX_TAG`](http://php.net/manual/en/json.constants.php#constant.json-hex-tag)、[`JSON_HEX_AMP`](http://php.net/manual/en/json.constants.php#constant.json-hex-amp)、[`JSON_HEX_APOS`](http://php.net/manual/en/json.constants.php#constant.json-hex-apos)、[`JSON_HEX_QUOT`](http://php.net/manual/en/json.constants.php#constant.json-hex-quot)

确保编码期间进行以下转换：

| 常量 | 输入 | 输出 |
| --- | --- | --- |
| `JSON_HEX_TAG` | `<` | `\u003C` |
| `JSON_HEX_TAG` | `>` | `\u003E` |
| `JSON_HEX_AMP` | `&` | `\u0026` |
| `JSON_HEX_APOS` | `'` | `\u0027` |
| `JSON_HEX_QUOT` | `"` | `\u0022` |

![](Image00774.jpg)

```
$array = [ "tag" => "<>" , "amp" => "&" , "apos" => "'" , "quot" => "\"" ];
echo json_encode ( $array );
echo json_encode ( $array , JSON_HEX_TAG | JSON_HEX_AMP | JSON_HEX_APOS | JSON_HEX_QUOT );
```

输出：

```
{ "tag" : "<>" , "amp" : "&" , "apos" : "'" , "quot" : "\"" }
```

![](Image00775.jpg)

```
{ "tag" : "\u003C\u003E" , "amp" : "\u0026" , "apos" : "\u0027" , "quot" : "\u0022" }
```

#### PHP 5.x 版本 ≥ 5.3 [`JSON_NUMERIC_CHECK`](http://php.net/manual/en/json.constants.php#constant.json-numeric-check)

确保数字字符串转换为整数。

![](Image00776.jpg)

输出：

![](Image00777.jpg)

```
[ "23452" ,23452]
[23452,23452]
```

#### PHP 5.x 版本 ≥ 5.4 [`JSON_PRETTY_PRINT`](http://php.net/manual/en/json.constants.php#constant.json-pretty-print)

使 JSON 易于阅读。

![](Image00778.jpg)

输出：

![](Image00779.jpg)

#### [`JSON_UNESCAPED_SLASHES`](http://php.net/manual/en/json.constants.php#constant.json-unescaped-slashes)

输出中包含未转义的 `/` 正斜杠。

![](Image00780.jpg)

输出：

![](Image00781.jpg)

```
{ "filename" : "example.txt" , "path" : "\/full\/path\/to\/file" }
{ "filename" : "example.txt" , "path" : "/full/path/to/file" }
```

#### [`JSON_UNESCAPED_UNICODE`](http://php.net/manual/en/json.constants.php#constant.json-unescaped-unicode)

输出中包含 UTF8 编码字符，而不是 `\u` 编码的字符串。

![](Image00782.jpg)

输出：

![](Image00783.jpg)

#### PHP 5.x 版本 ≥ 5.5 [`JSON_PARTIAL_OUTPUT_ON_ERROR`](http://php.net/manual/en/json.constants.php#constant.json-partial-output-on-error)

遇到无法编码的值时允许编码继续进行。

![](Image00784.jpg)

输出：

![](Image00785.jpg)

```
{ "file" : null , "name" : "foo.txt" }
```

#### PHP 5.x 版本 ≥ 5.6 [`JSON_PRESERVE_ZERO_FRACTION`](http://php.net/manual/en/json.constants.php#constant.json-preserve-zero-fraction)

确保浮点数始终作为浮点数编码。

![](Image00786.jpg)

输出：

![](Image00787.jpg)

#### PHP 7.x 版本 ≥ 7.1 [`JSON_UNESCAPED_LINE_TERMINATORS`](http://php.net/manual/en/json.constants.php#constant.json-unescaped-line-terminators)

与 `JSON_UNESCAPED_UNICODE` 结合使用时，恢复旧版 PHP 的行为，不转义字符 U+2028 LINE SEPARATOR（行分隔符）和 U+2029 PARAGRAPH SEPARATOR（段分隔符）。尽管这些字符在 JSON 中有效，但它们在 JavaScript 中无效，因此 `JSON_UNESCAPED_UNICODE` 的默认行为在 7.1 版本中发生了变化。

![](Image00788.jpg)

```
$array = [ "line" => "\xe2\x80\xa8" , "paragraph" => "\xe2\x80\xa9" ];
echo json_encode ( $array , JSON_UNESCAPED_UNICODE );
echo json_encode ( $array , JSON_UNESCAPED_UNICODE | JSON_UNESCAPED_LINE_TERMINATORS );
```

输出：

![](Image00789.jpg)

![](Image00790.jpg)

## 第 31.3 节：调试 JSON 错误

当 `json_encode` 或 `json_decode` 无法解析提供的字符串时，将返回 `false`。PHP 本身不会引发任何错误或警告；责任在于用户使用 [`json_last_error()`](http://php.net/manual/en/function.json-last-error.php) 和 [`json_last_error_msg()`](http://php.net/manual/en/function.json-last-error-msg.php) 函数来检查是否发生错误，并在应用程序中做出相应处理（调试、显示错误消息等）。

以下示例展示了处理 JSON 时的常见错误，即由于传递了错误的 UTF-8 编码字符串等原因，导致 JSON 字符串解码/编码失败。

![](Image00791.jpg)

### [`json_last_error_msg`](http://php.net/manual/en/function.json-last-error-msg.php)

[`json_last_error_msg()`](http://php.net/manual/en/function.json-last-error-msg.php) 返回尝试编码/解码字符串时发生的最后一个错误的人类可读消息。

![](Image00792.jpg)

即使未发生错误，此函数始终返回 `string`。

默认的非错误字符串为 `No Error`。

如果发生其他（未知）错误，将返回 `false`。

在循环中使用时要小心，因为 [`json_last_error_msg()`](http://php.net/manual/en/function.json-last-error-msg.php) 将在每次迭代中被覆盖。

你应该仅使用此函数获取用于显示的消息，而不应在控制语句中用它进行判断。

![](Image00793.jpg)

此函数在 PHP 5.5 之前不存在。以下是一个 polyfill 实现：

![](Image00794.jpg)

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

![](Image00795.jpg)

### [`json_last_error`](http://php.net/manual/en/function.json-last-error.php)

[`json_last_error()`](http://php.net/manual/en/function.json-last-error.php) 返回一个整数，映射到 PHP 提供的预定义常量之一。

| 常量 | 含义 |
| --- | --- |
| `JSON_ERROR_NONE` | 未发生错误 |
| `JSON_ERROR_DEPTH` | 超过最大堆栈深度 |
| `JSON_ERROR_STATE_MISMATCH` | 无效或格式错误的 JSON |
| `JSON_ERROR_CTRL_CHAR` | 控制字符错误，可能编码不正确 |
| `JSON_ERROR_SYNTAX` | 语法错误（自 PHP 5.3.3 起） |

