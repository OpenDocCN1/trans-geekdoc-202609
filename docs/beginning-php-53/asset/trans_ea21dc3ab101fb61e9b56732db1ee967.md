

```php
<?php
$myNumber = 123.45;
printf( "Binary: %b<br/>", $myNumber );
printf( "Character: %c<br/>", $myNumber );
printf( "Decimal: %d<br/>", $myNumber );
printf( "Scientific: %e<br/>", $myNumber );
printf( "Float: %f<br/>", $myNumber );
printf( "Octal: %o<br/>", $myNumber );
printf( "String: %s<br/>", $myNumber );
printf( "Hex (lower case): %x<br/>", $myNumber );
printf( "Hex (upper case): %X<br/>", $myNumber );
?>
</body>
</html>
```

可以在图 5-3 中查看结果。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_128_0.png)

图 5-3

## 指定符号

默认情况下，printf() 在负数前面显示减号（ - ），但不会在正数前面显示加号（ + ）。要更改 printf() 的行为，使其始终显示符号，请在类型说明符前面使用符号说明符 +。示例如下：

```php
printf( "%d<br/>", 123 ); // Displays "123"
printf( "%d<br/>", -123 ); // Displays "-123"
printf( "%+d<br/>", 123 ); // Displays "+123"
printf( "%+d<br/>", -123 ); // Displays "-123"
```

## 填充输出

您可以在格式化参数的左侧（默认）或右侧添加字符，以将其填充到固定宽度。如果您想在数字前添加前导零，或通过空格填充来水平对齐多个字符串，这非常有用。

要添加填充，请在转换说明中插入一个 _填充说明符_，位于类型说明符之前。填充说明符由一个零（用零填充）或空格字符（用空格填充）组成，后跟要将结果填充到的字符数。`printf()` 然后根据需要添加尽可能多的零或空格，以使结果达到正确宽度。

例如，以下代码显示各种数字，必要时使用前导零，以确保结果始终为六位长度：

```
printf( "%06d<br/>", 123 ); // Displays "000123"
printf( "%06d<br/>", 4567 ); // Displays "004567"
printf( "%06d<br/>", 123456 ); // Displays "123456"
```

填充说明符可以在需要的地方添加字符，但它永远不会截断输出。因此 `printf( "%06d", 12345678 )` 显示 "12345678"，而不是 "345678"。

此示例使用前导空格填充各种字符串，以确保它们右对齐：

```
print "<pre>";
printf( "% 15s\n", "Hi" );
printf( "% 15s\n", "Hello" );
printf( "% 15s\n", "Hello, world!" );
print "</pre>";
```

结果如下：

```
Hi
Hello
Hello, world!
```

您也可以省略零或空格，只指定一个数字，在这种情况下，`printf()` 将使用空格进行填充。

您不仅限于零和空格。要使用您自己的填充字符，请插入一个撇号（ ' ），后跟字符，而不是零或空格：

```
printf( "%'#8s", "Hi" ); // Displays "######Hi"
```

如果您想在右侧而不是左侧添加填充——即结果左对齐而不是右对齐——请在填充字符和宽度说明符之间添加减号（ - ）符号：

```
printf( "%'-#8s", "Hi" ); // Displays "Hi######"
```

当使用 `f` 或 `F` 显示浮点数时，填充行为会有所不同。有关更多详细信息，请参阅“指定数字精度”。

## 指定数字精度

使用 `f` 或 `F` 类型说明符显示浮点数时，可以使用 _精度说明符_ 来指示将数字四舍五入到多少位小数。要添加精度说明符，请在类型说明符之前插入一个句点（ `.` ），后跟要使用的小数位数：

```
printf( "%f<br />", 123.4567 ); // Displays "123.456700" (default precision)
printf( "%.2f<br />", 123.4567 ); // Displays "123.46"
printf( "%.0f<br />", 123.4567 ); // Displays "123"
printf( "%.10f<br />", 123.4567 ); // Displays "123.4567000000"
```

您可以将填充说明符与精度说明符一起使用，在这种情况下，整个数字将被填充到所需长度（包括小数点后的数字以及小数点本身）：

```
echo "<pre>";
printf( "%.2f<br />", 123.4567 ); // Displays "123.46"
printf( "%012.2f<br />", 123.4567 ); // Displays "000000123.46"
printf( "%12.4f<br />", 123.4567 ); // Displays " 123.4567"
echo "</pre>";
```

顺便说一句，如果在格式化字符串时使用精度说明符，`printf()` 会将字符串截断为那么多字符：

```
printf( "%.8s\n", "Hello, world!" ); // Displays "Hello, w"
```

## 交换参数

您可能已经注意到，传递给 `printf()` 的其他参数的顺序必须与格式字符串中的转换说明的顺序匹配。通常这不是问题，但偶尔您可能需要更改转换说明的顺序，却无法更改参数的顺序。

例如，假设您的格式字符串存储在单独的文本文件中，而不是嵌入在 PHP 代码中。如果您想更改脚本显示输出的方式（例如，如果您正在为应用程序创建不同的“皮肤”，或者正在创建英文、法文和德文版本的应用程序），这很方便。假设以下格式字符串保存在名为 `template.txt` 的文件中：

```
You have %d messages in your %s, of which %d are unread.
```

您的 PHP 代码可能会使用此 `template.txt` 文件向用户显示消息，如下所示（在真实世界的 PHP 应用程序中，`$mailbox`、`$totalMessages` 和 `$unreadMessages` 值可能会从数据库中获取）：

```
$mailbox = "Inbox";
$totalMessages = 36;
$unreadMessages = 4;
printf( file_get_contents( "template.txt" ), $totalMessages, $mailbox,
$unreadMessages );
```

这段代码将显示以下消息：

```
You have 36 messages in your Inbox, of which 4 are unread.
```

如果你想知道，file_get_contents() 会读取文件并将其内容作为字符串返回。
您将在第 11 章中详细了解它。

现在，假设您正在为不同市场为您的应用程序“换肤”，并想改用以下 template.txt 文件而不是：

```
Your %s contains %d unread messages, and %d messages in total.
```

格式字符串包含相同的转换说明，但顺序不同。这将导致以下消息，显然是胡说八道：

```
Your 36 contains 0 unread messages, and 4 messages in total.
```

通常，解决此问题的唯一方法是更改 PHP 代码中参数的顺序以匹配，如果您只是换肤，这太过繁琐。

这时参数交换就派上用场了。使用此技术，您可以指定每个转换说明引用哪个参数。其工作原理如下：在每个百分号（ % ）符号之后，添加要引用的参数的位置（1 是格式字符串之后的第一个参数，2 是第二个参数，依此类推），后跟美元符号（ $ ）。因此，您可以编辑 template.txt 文件，并将格式字符串更改为以下内容：

```
Your %2$s contains %3$d unread messages, and %1$d messages in total.
```

现在，尽管您没有动过 PHP 脚本，消息会正确显示：

```
Your Inbox contains 4 unread messages, and 36 messages in total.
```

## 存储结果而不是打印它

printf() 很好，但如果您想将结果存储在变量中以供以后使用呢？您在创建字符串时可能还没准备好显示它。这时 sprintf() 函数就很有用了。sprintf() 的行为与 printf() 完全相同，区别在于它返回生成的字符串而不是打印它。例如：

```php
<?php
$username = "Matt";
$mailbox = "Inbox";
$totalMessages = 36;
$unreadMessages = 4;
$messageCount = sprintf( file_get_contents( "template.txt" ), $totalMessages,
$mailbox, $unreadMessages );
?>
```

```
<p>Welcome, <?php echo $username?>.</p>
<p class="messageCount"><?php echo $messageCount?></p>
```

printf() 的另一个变体是 fprintf()，它将生成的字符串写入打开的文件。要使用它，请传递文件句柄，然后是格式字符串，然后是其余参数。有关文件和文件句柄的更多信息，请参见第 11 章。

