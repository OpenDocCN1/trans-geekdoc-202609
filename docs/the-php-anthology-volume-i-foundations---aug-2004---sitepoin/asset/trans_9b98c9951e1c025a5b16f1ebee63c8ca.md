

* @var string
 */
var $AllowedTags = '<a><b><strong><i><em><u>';

/**
 * Instance of native XML parser
 * @access private
 * @var resource
 */
var $parser;

/**
 * String of allowed tags
 * @access private
 * @var string
 */
var $post = '';

/**
 * Used to store any XML error string
 * @access private
 * @var string
 */
var $error = '';

/**
 * Constructs FormFilter
 * @access public
 */
function FormFilter()
{
    $this->parser = xml_parser_create();
    xml_set_object($this->parser, $this);
    xml_set_element_handler($this->parser, 'open', 'close');
    xml_set_character_data_handler($this->parser, 'data');
}

/**
 * Constructs FormFilter
 * @param string data to filter
 * @return string filter data
 * @access public
 */
function filter($post)
{
    $this->post = '';
$post = strip_tags($post, $this->allowedTags);
$post = '<?xml version="1.0"?><post>' . $post . '</post>';
if (!xml_parse($this->parser, $post, true)) {
    $this->error = 'Post data is not well formed: ' .
    xml_error_string(xml_get_error_code($this->parser)) .
    ' on line ' . xml_get_current_line_number($this->parser);
    return false;
}
return $this->post;
}

/**
 * Returns any XML errors
 * @return string XML error
 * @access public
 */
function getError()
{
    return $this->error;
}

在FormFilter类的构造函数中，我们首先要做的是创建原生Expat解析器的实例，并告诉它要使用哪些回调函数（有关此内容将在第2卷第2章中详细介绍）。完成这些后，我们提供filter方法来“筛选”包含HTML的字符串。首先，我们移除除$allowedTags成员变量中定义的标签之外的所有内容。然后，我们需要将XML处理指令预置到字符串开头，并确保整个内容被包装在根XML节点中；这样做是为了防止解析器对字符串格式不正确提出警告。

如果在解析过程中遇到问题，错误消息将被本地存储，并通过getError方法提供。一旦解析完成，我们将帖子返回给调用filter方法的代码。

真正的工作发生在XML处理程序中：

文件：TextManipulation/FormFilter.php（在SPLIB中）（节选）

```
/**
 * Sax Open TagHandler
 * @param XML_HTMLSax
 * @param string tag name
 * @param array attributes
 * @return void
 * @access private
 */
function open(&$parser, $tag, $attrs)
{
    switch ($tag) {
    case 'A':
    if (isset($attrs['HREF']) &&
    Validate::url($attrs['HREF'])) {
    $this->post .= '<a href="' . $attrs['HREF'] .
    '" target="_blank">';
    } else {
    $this->post =
    '<a href="javascript;" target="_blank">';
    }
    break;
    case 'B':
    case 'STRONG':
    $this->post .= '<strong>';
    break;
    case 'I':
    case 'EM':
    $this->post .= '<em>';
    break;
    }
}

/**
 * Sax Close TagHandler
 * @param XML_HTMLSax
 * @param string tag name
 * @param array attributes
 * @return void
 * @access private
 */
function close(&$parser, $tag)
{
    switch ($tag) {
    case 'A':
    $this->post .= '</a>';
    break;
    case 'B':
    case 'STRONG':
    $this->post .= '</strong>';
    break;
    case 'I':
    case 'EM':
    $this->post .= '</em>';
    break;
    }
}

/**
 * Sax Data Handler
 * @param XML_HTMLSax
 * @param string data inside tag
 * @return void
 * @access private
 */
function data(&$parser, $data)
{
	$this->post .= $data;
}
}
```

解析器在读取XML文档时会调用这些处理程序方法。查看open方法，你可以看到我们如何处理不同的标签名称。特别是，当我们收到a标签时，我们使用PEAR::Validate来检查URL是否有效。还要注意，我们将b和i转换为strong和em。这里遇到的任何其他未明确标识的属性都会被简单地丢弃。

请注意，在这个示例中，使用strip_tags实际上是多余的，因为处理程序方法也会忽略任何未明确标识的标签。当然，我们在这里将自己限制在只有少数几个HTML标签。处理其他标签（例如列表）通常需要更复杂的代码，增加了我们可能允许意外HTML标签的风险。strip_tags函数充当我们的保险单。

使用XML扩展的一个好处是，我们要求用户提交格式正确的XML。这样做的好处是，例如未关闭的a标签不会被接受。但这也意味着，某些标签（例如br，如果允许的话）如果不按照XML标准编写，就会出现问题。

以下是该类在实际中的示例：

```
File: 12.php

<?php
// Include PEAR::Validate
require_once 'Validate.php';

// Include PEAR::XML_HTMLSax
require_once 'TextManipulation/FormFilter.php';

// Include file to strip quotes if needed
require_once 'MagicQuotes/strip_quotes.php';

// If the form is submitted...
if (isset($_POST['submit'])) {
    // Instantiate the form filter
    $FormFilter = &new FormFilter();

    // Filter the message
    if (FALSE === ($filtered_message =
        $FormFilter->filter($_POST['message']))) {
        $filtered_message = $FormFilter->getError();
    }
}
?>
<!DOCTYPE html "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Form HTML Filter</title>
<meta http-equiv="Content-Type"
    content="text/html; charset=iso-8859-1" />
</head>
<body>
<p><b>Add your comment:</b></br />
<form action="<?php echo $_SERVER['PHP_SELF']; ?>" method="POST">
<textarea cols="40" rows="5" name="message"></textarea><br />
<input type="submit" name="submit" value=" Post " />
</form></p>
<p>Allowed tags: <code>&lt;code&gt;&lt;a&gt; &lt;b&gt; &lt;strong&gt; &lt;i&gt; &lt;em&gt;</code></p>
<?php
    if (isset ( $filtered_message )) {
        echo ( "<p>Your post:</b><br />\n<code>\n".
            htmlspecialchars($filtered_message)."</code>\n" );
    }
?>
</body>
</html>
```

通过测试，你会发现这段代码只允许我们在类中标识的那些元素。

## 延伸阅读

- URL 编码: http://www.blooberry.com/indexdot/html/topics/urlencoding.htm

这对于URL编码是一个有用的参考。

- HTML实体参考: http://www.htmlhelp.com/reference/html40/entities/

收藏这个方便的参考，用于查找在HTML中具有特殊含义的字符。

- PCRE教程: http://codewalkers.com/tutorials/30/2.html

在本教程中，你将找到一些关于Perl兼容正则表达式的有用且实用的帮助。

## 6 日期和时间

如果一周有十天，那该多好？一小时有100分钟呢？一年有十个月？

日期和时间可能是你习以为常的东西。你每天都在处理它们，可能并不知道大脑用来计算还要等多久才到周五的巧妙数学算法。只有当你开始编程时，你才会意识到，这些年来你一直习以为常的东西在代码中处理起来并不像你预期的那么简单。怪罗马人吧！

在日常生活中，我们习惯于使用十进制（基数为十）的数字，这些数字针对处理十的倍数进行了优化（十个一组成十，十个十成一百，十个一百成一千，等等）。不谈数学课，日期和时间的问题在于它们不能分解为十的整组：

- 一秒中有1000毫秒。没问题。
- 一分钟中有60秒。
- 一小时中有60分钟。
- 一天中有24小时。

那么，给定一个以毫秒为单位的值，你如何计算天数呢？这需要一连串的长除法！而这仅仅是时间——那日期呢？

- 一周中有七天（你的周是从周日还是周一开始？）
- 一个月中你有……嗯……你不知道确切的天数或周数；它取决于月份（别让我提闰年！）
- 一年中有12个月。

当然，这太简单了。那要不要更难一点？你通常需要能够以多种格式表示日期，例如“Tuesday 18th March, 2003”、“03/18/03”（美国格式）、“18/03/03”（欧洲格式）、“18th Mar 2003”和“20030318”（MySQL风格的时间戳），更不用说“1047942000”（Unix时间戳）了！

你计划如何显示从数据库获取并按日期排序的文章列表？如果你想呈现更复杂的内容，例如在线日历，又该如何？在应用程序中处理日期和时间时，需要考虑很多问题。

PHP确实让处理时间和日期尽可能轻松，这要归功于date等强大的函数。但在PHP程序员职业生涯早期，制定处理日期和时间的正确策略非常重要。从第一天就采取正确的方法，就可以避免以后不得不编写极其复杂的代码来修复新手时犯下的错误。在本章中，我们将探讨可以采用的策略，并解决在日期和时间方面可能遇到的一些常见问题。

## 如何在MySQL中存储日期？

乍一看，在MySQL中存储日期的最简单方法似乎是直接将它们按网页上显示的样子存入，例如“18th March 2003”。警告——这是走向严重脱发之路的第一步。在针对MySQL运行的SQL语句中，WHERE子句不会允许你执行这样的操作：

```
SELECT * FROM table WHERE date > '14th February 2003'
```

存储日期信息的更好方法是使用时间戳。时间戳是以可用于求解的格式标识日期和时间的数字。

