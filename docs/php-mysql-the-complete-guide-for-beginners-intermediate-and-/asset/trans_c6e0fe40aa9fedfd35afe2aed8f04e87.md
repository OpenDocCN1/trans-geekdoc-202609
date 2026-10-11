
这些变量是从运行 PHP 解析器的环境导入到 PHP 的全局命名空间中的。许多变量由运行 PHP 的 Shell 提供，不同的系统可能运行不同种类的 Shell，因此无法提供一份确定的列表。请参阅您的 Shell 文档以获取已定义环境变量的列表。

其他环境变量包括 CGI 变量，无论 PHP 是作为服务器模块还是 CGI 处理器运行，这些变量都会被放置在那里。

`$_ENV` 中存储的任何内容都来自 PHP 运行所在的环境。

| php | | . | ini |
| --- | --- | --- | --- |

只有当 `variables_order` 允许时，`$_ENV` 才会被填充。

请参阅 [此回答](http://stackoverflow.com/questions/3780866/why-is-my-env-empty/27077452#27077452) 以获取更多关于为什么 `$_ENV` 未被填充的信息。

## 第 4.2 节：PHP5 超全局变量

以下是 PHP5 超全局变量

`$GLOBALS`

`$_REQUEST`

`$_GET`

`$_POST`

`$_FILES`

`$_SERVER`

`$_ENV`

`$_COOKIE`

`$_SESSION`

`$GLOBALS`：此超全局变量用于访问全局变量。

`$_REQUEST`：此超全局变量用于收集通过 HTML 表单提交的数据。

`$_GET`：此超全局变量用于收集通过带有 get 方法的 HTML 表单提交的数据。

`$_POST`：此超全局变量用于收集通过带有 post 方法的 HTML 表单提交的数据。

`$_FILES`：此超全局变量保存通过 HTTP Post 方法上传的文件信息。

`$_SERVER`：此超全局变量保存关于脚本、HTTP 头部和服务器路径的信息。

`$_ENV`：此超全局变量保存 PHP 运行所在的 Shell 环境变量详情。

`$_COOKIE`：此超全局变量用于通过给定的键检索 Cookie 值。

`$_SESSION`：此超全局变量用于设置和检索存储在服务器上的会话值。

# 第 5 章：输出变量的值

要构建动态且交互式的 PHP 程序，输出变量及其值非常有用。PHP 语言允许多种值输出方法。本主题涵盖在 PHP 中打印值的标准方法以及这些方法可以使用的场景。

## 第 5.1 节：echo 和 print

| echo | | ( | "test" |
| --- | --- | --- | --- |

[echo](http://php.net/manual/en/function.echo.php) 和 [print](http://php.net/manual/en/function.print.php) 是语言结构，而非函数。这意味着它们不像函数那样要求参数周围必须有括号（尽管可以给几乎任何 PHP 表达式加上括号，因此 `echo("test")` 也不会造成任何伤害）。它们输出变量、常量或表达式的字符串表示形式。它们不能用于打印数组或对象。

### echo 的简写语法

当在 [PHP 标签之外](http://php.net/manual/en/language.basic-syntax.phpmode.php) 时，默认可用 echo 的简写语法，使用 `<?=` 开始输出，`?>` 结束。例如：

```
<?= "Hello World" ?>
```

注意没有终止的 `;`。之所以有效，是因为结束 PHP 标签充当了单条语句的终止符。因此，按照惯例，在这种简写语法中省略分号。

### print 的优先级

虽然 print 是语言结构，但它具有像运算符一样的优先级。它位于 `=`、`+=`、`-=`、`*=`、`**=`、`/=`、`.=`、`%=`、`&=` 和 `and` 运算符之间，并具有左结合性。示例：

```
print "hello " . print "world";
```

带括号的相同示例：
```
print "hello " . (print "world");
```
```
echo '1' . print ( '2' + 3); //输出 511
```

### echo 和 print 的区别

简而言之，主要有两个区别：

*   `print` 只接受一个参数，而 `echo` 可以有多个参数。
*   `print` 返回一个值，因此可以作为表达式使用。

## 第 5.2 节：输出数组和对象的结构化视图

| [print_r](http://php.net/manual/en/function.print-r.php) |
| --- |

`print_r()` - 为调试输出数组和对象

[print_r](http://php.net/manual/en/function.print-r.php) 将以人类可读的格式输出数组或对象。

您可能有一个是数组或对象的变量。尝试用 echo 输出它会抛出错误：

| Notice | | : | | Array to string conversion |
| --- | --- | --- | --- | --- |

。您可以改用 `print_r` 函数来转储该变量的人类可读格式。

```
$myarray = array('a', 'b', 'c');
print_r($myarray);
```

```
Array
(
    [0] => a
    [1] => b
    [2] => c
)
```

```
$myobj = new stdClass();
$myobj->foo = 'bar';
print_r($myobj);
```

```
stdClass Object
(
    [foo] => bar
)
```

此外，`print_r` 的输出可以作为字符串捕获，而不仅仅是直接输出。例如，以下代码会将 `$myarray` 的格式化版本转储到一个新变量中：

```
$output = print_r($myarray, true);
```

请注意，如果您在浏览器中查看 PHP 的输出，且其被解释为 HTML，则换行符将不会显示，输出将难以阅读，除非您执行类似以下的操作：

```
echo '<pre>' . print_r($myarray, true) . '</pre>';
```

或者，您可以告诉浏览器您输出的是纯文本，而非 HTML：

```
header('Content-Type: text/plain');
print_r($myarray);
```

| [var_dump](http://php.net/manual/en/function.var-dump.php) |
| --- |

`var_dump()` - 输出关于参数内容的可读调试信息，包括其类型和值

输出比 `print_r` 更详细，因为它还会输出变量的类型及其值，以及其他信息，如对象 ID、数组大小、字符串长度、引用标记等。

您可以使用 `var_dump` 为调试输出更详细的版本。

```
$myarray = array('a', 'b', 'c');
var_dump($myarray);
```

输出更详细：

```
array(3) {
  [0]=>
  string(1) "a"
  [1]=>
  string(1) "b"
  [2]=>
  string(1) "c"
}
```

注意：如果您在开发环境中使用 xDebug，`var_dump` 的输出默认会被限制/截断。请参阅 [官方文档](https://xdebug.org/docs/display) 了解更多关于更改此选项的信息。

| [var_export](http://php.net/manual/en/function.var-export.php) |
| --- |

`var_export()` - 输出有效的 PHP 代码

`var_export()` 转储项目的 PHP 可解析表示形式。

```
$myarray = array('a', 'b', 'c');
var_export($myarray);
```

```
array (
  0 => 'a',
  1 => 'b',
  2 => 'c',
)
```

要将内容放入变量，可以执行以下操作：

```
$array_export = var_export($myarray, true);
$string_export = var_export($mystring, true);
$int_export = var_export($myint, true);
```

之后，您可以这样输出：

```
printf('$myarray = %s; %s', $array_export, PHP_EOL);
printf('$mystring = %s; %s', $string_export, PHP_EOL);
printf('$myint = %s; %s', $int_export, PHP_EOL);
```

这将产生以下输出：

```
$myarray = array (
  0 => 'a',
  1 => 'b',
  2 => 'c',
);
$mystring = 'foo';
$myint = 123;
```

## 第 5.3 节：使用 echo 进行字符串拼接

您可以在输出时使用 [拼接来连接字符串](https://secure.php.net/manual/en/language.operators.string.php) "首尾相连"（例如使用 `echo` 或 `print`）。

您可以使用 `.`（句点）拼接变量。

```
echo "Hello " . $name . "!";
```

与拼接类似，`echo`（不带括号时）可以使用逗号（`,`）将字符串和变量组合在一起（连同其他任意表达式）。

```
echo "Hello ", $name, "!";
```

```
echo "The sum is ", 1 + 2, ".";
```

### 字符串拼接 vs 向 echo 传递多个参数

向 `echo` 命令传递多个参数在某些情况下比字符串拼接更有优势。参数按传入的顺序写入输出。

```
echo "Hello ", $name, "!"; // 更快，无拼接开销
echo "Hello " . $name . "!"; // 先拼接，再输出
```
