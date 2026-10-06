

# 第三部分：在实践中使用 PHP

```php
$text = "Andy scored 184 points, Rachel attained 198 points and Bert scored
112 points.";

$pattern = "/\n(Andy|Rachel|Bert)\ # 仅匹配我们认识的人
(scored|attained)\\ # 两个单词，意思相同
# 得分的分数
(\d+)\n*/";

preg_match_all($pattern, $text, $matches); 

for ($i = 0; $i < count($matches[0]); $i++) {
    echo $matches[1][$i] . ", " . $matches[3][$i] . "<br/>";
}
```

这段代码产生以下输出：

Andy: 184
Rachel: 198
Bert: 112

最后，这是一个使用修饰符（modifier）的示例。这与本章之前在 `preg_replace_callback()` 中的示例相同，但重写为使用：

```php
$text = "Our high-quality mouse mat is just $3.99,
while our keyboard covers sell for $4.99 and
screen protectors for $5.99.";

echo preg_replace("/\\(\d+\)/e", "$\$ . ($1 + 1)", $text);
```

对于每个匹配项，替换字符串中的 PHP 代码将显示一个美元符号，后紧跟子模式（价格）加一。这产生了如下输出：

Our high-quality mouse mat is $4.99, while our keyboard covers sell for $5.99 and our screen protectors for $6.99.

你可以同时组合多个修饰符——只需一个接一个添加修饰符即可：

```php
$text = "Hello, World!How are you today?\n";
echo preg_match("/world!\$im", $text) . "<br/>"; // 显示 "1"
```

你可以在 http://www.php.net/manual/en/reference/pcre.pattern.modifiers.php 查看模式修饰符的完整列表。

# 使用正则表达式分割字符串

本章探索的正则表达式函数是 `preg_split()`。在第 6 章中，你学习了 `explode()` 函数，它允许你将字符串分割分为字符串数组。你传入一个分隔符（例如，逗号），目标字符串会在每个找到分隔符的地方被分割。

# 第 18 章：使用正则表达式进行字符串匹配

preg_split() 将分割进一步了一层，允许你为分隔符指定正则表达式。这在决定根据什么内容分割字符串时为你提供了更多的灵活性，并且当你需要解析人类易读格式的字符串时，它非常有用。考虑以下示例：

```php
$text = "John Steinbeck, Franz Kafka and J.R.R. Tolkien";
$authors = preg_split('/\s*&\s*/+', $text);
echo "<pre>";
print_r($authors);
echo "</pre>";
```

这段代码将输入字符串分割为各个作者姓名。该正则表达式匹配带有零或多个空白字符的逗号，或者匹配被一个或多个空白字符包围的单词 "and"。这意味着，当在输入字符串中找到这些模式之一时，字符串会被分割并产生此结果：

```
Array
(
    [0] => John Steinbeck
    [1] => Franz Kafka
    [2] => J.R.R. Tolkien
)
```

与 `explode` 一样，你可以通过向 `preg_split()` 传递整数作为第三参数来限制返回的数组元素数量。你还可以通过第四参数传递一些可选标志来控制 `preg_split()` 的行为：

- PREG_NO_EMPTY: 移除返回数组中的任何空子字符串。这对于移除不需要的子字符串很有用，你稍后就会看到它们。

- PREG_DELIM_CAPTURE: 使分隔符表达式中的任何匹配的子模式也返回到数组，同时返回字符串部分。

- PREG_SPLIT_OFFSET_CAPTURE: 它的工作方式类似于 `preg_match()` 的 PREG_OFFSET_CAPTURE 标志。设置时，`preg_split()` 返回一个二维数组，其中每个嵌套数组包含两个元素：提取的子字符串的文本和它在原始字符串中的位置。

要设置多个标志，请使用位或运算符将它们组合起来——例如：PREG_NO_EMPTY|PREG_DELIM_CAPTURE。

如果你想设置一个或多个标志且不想限制返回的元素数量，请将 -1 作为第三参数。

要查看 `PREG_SPLIT_NO_EMPTY` 有什么用，请考虑以下示例：

```php
$text = 'hello', 'goodbye';
$letters = preg_split('/, /', $text);
echo "<pre>";
print_r($letters);
echo "</pre>";
```

# 第三部分：在实践中使用 PHP

这段代码显示：

```
Array
(
  [0] =>
  [1] => hello
  [2] =>
  [3] =>
  [4] =>
  [5] => goodbye
  [6] =>
)
```

这是因为正则表达式导致任何单引号、逗号和空格字符被视为分隔符。字符串在第一个和最后一个字符的开头和结束处被分割，并且在 "hello" 和 "goodbye" 之间也被分割了三次，因为 `preg_split()` “看到”了输入字符串中单引号、逗号和空格字符之间的三个空字符串。

自然地，这些空字符串是不需要的。通过设置 PREG_SPLIT_NO_EMPTY 标志，你可以轻松地从结果数组中移除这些字符串：

```php
$text = 'hello', 'goodbye';
$letters = preg_split('/, /', $text, -1, PREG_NO_EMPTY);
echo '<pre>';
print_r($letters);
echo '</pre>';
```

这段代码产生了预期结果：

```
Array
(
  [0] => hello
  [1] => goodbye
)
```

# 尝试：输入验证

正则表达式通常用于检查输入是否正确。例如，可以使用正则表达式来判断输入是否符合格式。此示例创建了一个表单，用户可以在其中输入电子邮件地址、电话号码和产品代码（SW、MW、WW 后面跟两个数字）。

