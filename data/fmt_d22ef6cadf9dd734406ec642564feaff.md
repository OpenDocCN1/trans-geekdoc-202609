
# 第 14 章 - PHP 样式

## 极大化 PHP

![](img/5b1cb1f01df587629b18337140fcfc04a_318_0.png)

图 14-4：提交后的极大化 PHP

这种极大化样式受到 C 程序员的青睐，因为它与你在那种编程语言中执行任务的方式非常相似。除非你有大量的练习来编写生成 HTML 的代码而不是直接编写 HTML，否则这种模式可能看起来很笨拙且容易出错。因为 HTML 和 PHP 整合得如此紧密，你可以让每一行 HTML 都依赖于你尽可能塞进 PHP 中的许多条件。另一方面，使用这种样式时，视觉效果和感觉的变化并不那么容易。

![](img/5b1cb1f01df587629b18337140fcfc04a_319_0.png)

记住在这种样式下转义双引号和美元符号。如果你想让你的 HTML 源代码对人类可读，请记住在返回 HTML 的函数中使用适当的换行符（`\n`）、回车（`\r`）和制表符（`\t`）。

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

## 中等 PHP

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

正如所预期的，这是一种折中样式。HTML 部分（除头部外）被定义为一个函数，而 PHP 处理部分被定义为第二个函数。简单的控制（封装在 HTML 头部和页脚中）测试是运行第一个函数还是两个函数。这种模式可能没有其他模式那样清晰，看起来可能杂乱，但从某种意义上说，它充分利用了 PHP 的独特能力。PHP 相当于是混合体——既不是 C 也不是 Perl，但深受它们的影响——也许最好的样式是混合样式。

## 分离代码与设计

本章开头的 WYSIWYG 代码之所以难看，因为它违反了代码与设计分离的原则。这些编辑器内部从不具备那种美感，它们关注的是页面的外观而不是其逻辑结构。随着 HTML 的演进，分离代码和设计将成为强制性要求，而不仅仅是建议，因为功能上的重大进展（如 XML）需要更好的代码。本章中的许多主题对代码与设计的分离有明显的影响。正如从我们的“中等 PHP”示例所示，自定义函数可以是一个非常灵活且强大的工具，有助于让 PHP 比基于标签的脚本更好。

## PHP 中的层叠样式表

如你所知，有四种通用的方法可以将样式应用于你的页面：

- 在单个标签上应用 CSS 格式
- 使用 `<STYLE>` 标签
- 使用 `<LINK>` 标签
- `@import`

## 函数

毫无疑问，有四种通用的方法可以将样式应用于你的页面：

1. 在单个标签上应用 CSS 格式
2. 使用 `<STYLE>` 标签
3. 使用 `<LINK>` 标签
4. `@import`

## 模板和页面

毫无疑问，有四种通用的方法可以将样式应用于你的页面：

1. 在单个标签上应用 CSS 格式
2. 使用 `<STYLE>` 标签
3. 使用 `<LINK>` 标签
4. `@import`

## 总结

毫无疑问，有四种通用的方法可以将样式应用于你的页面：

1. 在单个标签上应用 CSS 格式
2. 使用 `<STYLE>` 标签
3. 使用 `<LINK>` 标签
4. `@import`

# 第 15 章 PHP 常见陷阱 (Gotchas)

尽管我们试图提供清晰的指令，但你无疑已经严格遵守了它们，然而仍然可能出现许多潜在的故障。本章将根据症状列出一些最常见的问题，并给出常见的原因。

## 本章内容

- 与安装相关的问题
- 空白页和不完整的页面
- 解析错误 (Parse errors)
- 权限问题
- 未定义的变量
- 函数问题
- 数学问题
