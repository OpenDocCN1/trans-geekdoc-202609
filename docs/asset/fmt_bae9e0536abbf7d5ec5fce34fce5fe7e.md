
程序员经常用来定位那 10% 的技术称为性能分析器（profiler）。性能分析器是一种在代码运行时进行跟踪的工具，记录每个函数调用的时间，并产生一个整洁的总结。遗憾的是，目前 PHP 还没有性能分析工具（尽管以后版本可能会有）。目前最好的办法是穷人性能分析技术：在不同位置打印 `microtime()` 的值来查看时间流向哪里。

# 关注数据库查询

尽管这涉及到对书中后续部分的展望，但你应该意识到数据库查询通常是 PHP 网站最大的时间耗费点。特别是如果你的数据库网站没有进行大量的计算密集型工作，你的第一眼应该是查询，下一个任务应该是尝试识别一个耗时的查询。一旦确定了罪魁查询，有很多技术可以加速它，其中许多与 PHP 无关。

有关优化数据库网站的细节，请参阅第 23 章。

# 关注内层循环

假设你有一个嵌入循环结构的页面，如下所示：

```php
for ($x = 0; $x < 100; $x++) {
  do_X();
  for ($y = 0; $y < 100; $y++) {
    do_XY();
    for ($z = 0; $z < 100; $z++) {
      do_XYZ();
    }
  }
}
```

除非你有非常有好的理由认为相反，否则你的优化重点应该放在 `do_XYZ()` 函数（它将执行 1,000,000 次）上，而不是另外两个函数（执行 10,000 次和 100 次）。

# 简洁的副作用

在我们讨论如何编写更简洁的代码之前，让我们先说，我们认为简洁是一种被高估的美德，原因如下。

# 简洁很少意味着高效

虽然在 PHP 引擎的内部某些地方，你编写代码的字符确实被一个接一个地消耗，因此在理论上代码花费更多时间，但在实践中，基于 Zend 的 PHP4 解析引擎如此快速，以至于这并不重要。对于额外变量赋值消耗的时间或空间，或者额外函数调用的开销，也是如此。

## 简洁性与可读性之间的权衡

请记住，你省略的每一个按键，都可能是那个让别人看出你在写代码时到底在想什么的关键。例如，看看这个简洁得惊叹的函数：

```php
function sieve($sn) {
    for ($i = 2; $i <= sqrt($sn); $i++) {
        for ($j = $i * $i; $j < $sn; $j += $i) {
            $array[$j] = TRUE;
        }
    }
    $plist = array();
    for ($i = $sn; $i > 1; $i--) {
        if (!isset($array[$i]))
            $plist[] = $i;
        }
    }
    return($plist);
}
```

显然，这实现了埃拉托尼筛法，而 `$plist` 是一个小于 `$sn` 的所有质数的列表。显而易见。

那么，为什么程序员追求简洁呢？第一个原因是为了节省时间（但仅仅是实际编写代码的时间）。第二个原因（我们只是在半开玩笑）是他们担心其他程序员（可能是受过 C 语言训练的）走过来，嘲笑他们，并指出他们的代码本可以用一半的空间写完。

## 简洁性技巧

如果你编写的代码可以适应更小的空间，请尝试以下技术。

### 我们同时返回返回值和副作用

利用“赋值的值即所赋值的值”这一事实是一个非常常见的技巧，如下伪代码所示：

```php
while ($next = GetNextOne())
    DoSomethingWith($next);
```

其中 `GetNextOne()` 是某个函数，它按顺序返回有用值，并在用完后返回一个假值。当返回假值时，`$next` 为 false，`while` 循环终止。

### 自增和赋值运算符

自增运算符（`++` 和 `--`）缩短了涉及对变量加减 1 的语句，而复合赋值运算符（`+=`, `*=`, `-=` 等）让某些类型的赋值更加简洁。

自增运算符和算术赋值运算符在第 10 章中介绍过，复合字符串赋值运算符（`.=`）已在第 9 章介绍过。

通常这些运算符会与之前的技巧结合使用，如下：

```php
while ($count--)
DoSomething($count);
```

这（假设 `$count` 开始为正整数）将在值为 1 时最后一次调用该函数。

### 重用函数

这是简洁性有益的用例之一，因为函数本身就是有益的。如果你能识别出页面中重复的代码段，尝试用调用封装该代码的单个函数来替换每一处。你的代码将由于重复部分的而变短，而且可能更易维护。

### 布尔值没有问题

初级程序员往往对布尔值有一种奇特的不信任，没有意识到它们可以像任何其他类型的值一样自由传递。这导致代码浪费了大量空间，如下：

```php
function DivisibleBy($num1, $num2)
{
    if ($num1 % $num2 == 0)
        return(TRUE);
    else
        return(FALSE);
}
/* 使用函数 */
if (DivisibleBy(9, 3))
    $divisible_result = TRUE;
else
    $divisible_result = FALSE;
    if ($divisible_result == TRUE)
        print("It's divisible!<BR>");
    else
        if ($divisible_result == FALSE)
            print("It's not divisible!<BR>");
```

更简洁的版本看起来像：

```php
function DivisibleByBetter($num1, $num2)
{
    return ($num1 % $num2 == 0);
}

/* 使用函数 */
if (DivisibleByBetter(9,3))
    print("It's divisible!<BR>\n");
```

你显然可以更进一步，直接去掉函数，如下所示：

```php
if (9 % 3 == 0)
    print("It's divisible!<BR>\n");
```

但（再次强调）函数是好的——一个解释性的函数名本身就是一段文档，而且你写的任何函数都给了你重用的机会，这让你的代码更具维护性。

### 使用短路布尔表达式

在执行其他测试之前，某些类型的布尔测试是不安全的。人们很想通过 `if` 结构隔离有问题的测试来解决这个问题。例如，假设你想打印两个绑定为整数的变量的比例，但仅当它们绑定为整数时，且仅当比例大于二时。此外，你还避免除零警告。你可能会笨拙地写成：

```php
if (IsSet($x))
  if (IsSet($y))
    if (Is_Integer($x))
      if (Is_Integer($y))
        if ($y != 0)
          if ($x / $y > 2)
            print("Ratio is " . ($x / $y));
```

你可以同样保持谨慎但少打一些字，如下：

```php
if (IsSet($x) && IsSet($y) && Is_Integer($x) && Is_Integer($y) && $y != 0 && $x / $y > 2)
    print("Ratio is " . ($x / $y));
```

测试将从左到右应用，如果任何测试失败，其右侧的测试将不会执行。

## HTML 模式还是 PHP 模式？

结合 PHP 和 HTML 有多种方法，功能上几乎相同。你的选择取决于外部因素，例如特定团队的工作流。

演示所有方法最简单的方法是将脚本以“最小 PHP”、“最大 PHP”和“中等 PHP”风格编写。记住，这些都是正确的，且返回相同的结果。风格上的决定只是偏好问题，有时会有细微的功能差异。

在下面的示例中，电子邮件地址是一个虚拟值——如果你想在具有 Sendmail 能力的 PHP 服务器上测试此，请更改它。

最小 PHP：

```html
<HTML>
<HEAD>
<TITLE>MorningService.html</TITLE>
<STYLE type="text/css">
<!--
</STYLE>
</HEAD>
<BODY>
```

```php
print("BODY (color: #000000; font-family: times; font-size: 12 pt)\n");
print("H1 (margin-top: 10; margin-bottom: 10; color: red; font-family: cursive; font-size: 16 pt; font-weight: bold)\n");
print("A (color:red)\n");
print("<A>");
print("</STYLE>");
print("</HEAD>");
print("<BODY>");
print("<CENTER><H1>Hotel California</H1></CENTER>");
print("<P>Thank you for staying at the Hotel California</B></P>");

/* The following test uses the value of the form's SUBMIT
button to check if the user is viewing the page for the first
time (in which case we won't send a message to the desk clerk)
or submitting/editing a previous request. */
if(!isset($Submit)) {
    /* These empty variables will cause the form below to print
    without visible values. */
    $Room = "";
    $WakeupTime = "";
    $Newspaper = "";
    print("<P>Please indicate what we can do to make your morning
shine a little more brightly.\n");
    print("You may change the values in the form below and resubmit
it.\n");
}
```

图 14-4：提交后的极大化 PHP

这种极大化风格受到 C 程序员的青睐，因为它与你在那种编程语言中执行任务的方式非常相似。除非你有大量的练习来编写生成 HTML 的代码而不是直接编写 HTML，否则这种模式可能看起来很笨拙且容易出错。因为 HTML 和 PHP 整合得如此紧密，你可以让每一行 HTML 都依赖于你尽可能塞进 PHP 中的许多条件。另一方面，使用这种样式时，视觉效果和感觉的变化并不那么容易。

记住在这种样式下转义双引号和美元符号。如果你想让 HTML 源代码对人类可读，请记住在返回 HTML 的函数中使用适当的换行符（`\n`）、回车（`\r`）和制表符（`\t`）。

中等 PHP：

```php
<?php
function display_form() {
?>
<CENTER><H1>Hotel California</H1></CENTER>
<P>Thank you for staying at the Hotel California!<BR>
Please indicate what we can do to make your morning sun shine a little more brightly.
<FORM METHOD="POST" ACTION="<?php echo($PHP_SELF); ?>">
<P>Room number <INPUT TYPE="TEXT" NAME="Room" SIZE=10>
<P>Do you want a wake-up call?<BR>
If so, please input a time <B>in 24-format (HH:MM)</B>
<INPUT TYPE="TEXT" NAME="WakeupTime" SIZE=10><BR>
<P>Select a newspaper: <SELECT NAME="Newspaper" SIZE=1>
<OPTION VALUE=0>deliver the...</OPTION>
<OPTION VALUE=1>USA Today</OPTION>
<OPTION VALUE=2>New York Times</OPTION>
<OPTION VALUE=3>Wall Street Journal</OPTION>
</SELECT>
<P><INPUT TYPE="Submit" Name="Submit" Value="Send">
```

```php
function display_form() {
    global $Newspaper, $WakeupTime, $Room;
    if($Newspaper == 0 && $WakeupTime == "") {
        print("<P>I'm sorry, you haven't told us to do anything!");
    }
    elseif($Newspaper == 0 && $WakeupTime != "") {
        mail("deskclerk@hotel.com", "$Room", "Wakeup at $WakeupTime");
        print("<P>Your wakeup call has been recorded. Sleep tight!");
    }
    elseif($Newspaper > 0) {
        mail("deskclerk@hotelcali.com", "$Room", "Wakeup at $WakeupTime and delivery $Newspaper");
        print("<P>Your wakeup call and newspaper preference have been recorded. Sleep tight!");
    }
}
```

```html
<HTML>
<HEAD>
<TITLE>MorningService.php</TITLE>
<STYLE TYPE="text/css">
BODY (color: #000000; font-family: times; font-size: 12 pt)
H1 (margin-top: 10; margin-bottom: 10; color: red; font-family: cursive; font-size: 16 pt; font-weight: bold)
A:link (color: red)
</STYLE>
</HEAD>
<BODY>
<?php
if(isset($Submit)) {
    $room = "";
    $WakeupTime = "";
    $Newspaper = "";
    display_form();
} else {
    process_form();
    print("<P>You may change the values in the form below and resubmit it.\n");
    display_form();
} ?>
</BODY></HTML>
```

正如所预期的，这是一种折中样式。HTML 部分（除头部外）被定义为一个函数，而 PHP 处理部分被定义为第二个函数。简单的控制（封装在 HTML 头部和页脚中）测试是运行第一个函数还是两个函数。这种模式可能没有其他模式那样清晰，看起来可能杂乱，但从某种意义上说，它充分利用了 PHP 的独特能力。PHP 相当于是混合体——既不是 C 也 Perl，但深受它们的影响——也许最好的样式是混合样式。

## 分离代码与设计

本章开头的 WYSIWYG 代码之所以难看，因为它违反了代码与设计分离的原则。这些编辑器内部从不具备那种美感，它们关注的是页面的外观而不是其逻辑结构。随着 HTML 的演进，分离代码和设计将成为强制性要求，而不仅仅是建议，因为功能上的重大进展（如 XML）需要更好的代码。本章中的许多主题对代码与设计的分离有明显的影响。正如从我们的“中等 PHP”示例所示，自定义函数可以是一个非常灵活且强大的工具，有助于让 PHP 比基于标签的脚本更好。

## PHP 中的层叠样式表

如你所知，将样式应用于页面有四种方法：

- 在单个标签上应用 CSS 格式
- 使用 `<STYLE>` 标签
- 使用 `<LINK>` 标签
- `@import`

毫无疑问，有四种通用的方法可以将样式应用于你的页面：

- 在单个标签上应用 CSS 格式
- 使用 `<STYLE>` 标签
- 使用 `<LINK>` 标签
- `@import`

毫无疑问，有四种通用的方法可以将样式应用于你的页面：

- 在单个标签上应用 CSS 格式
- 使用 `<STYLE>` 标签
- 使用 `<LINK>` 标签
- `@import`

毫无疑问，有四种通用的方法可以将样式应用于你的页面：

- 在单个标签上应用 CSS 格式
- 使用 `<STYLE>` 标签
- 使用 `<LINK>` 标签
- `@import`
