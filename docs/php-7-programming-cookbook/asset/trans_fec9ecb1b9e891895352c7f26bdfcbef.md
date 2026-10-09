
## 在视图脚本中使用表情符号或 Emoji

单词 **表情符号（emoticons）** 是 *情绪（emotion）* 和 *图标（icon）* 的组合词。**Emoji** 起源于日本，是另一个更大、被广泛使用的图标集合。这些图标就是那些在具有社交网络功能的网站上非常流行的小笑脸、微型忍者和“笑到在地上打滚”的图标。然而，在 PHP 7 之前，生成这些小东西简直是一项令人沮丧的练习。

### 如何操作...

1.  首先，你需要知道你想要显示的图标的 Unicode 编码。在互联网上快速搜索一下，你就会找到几个出色的对照图表。
    以下是 *止语（hear-no-evil）*、*不看（see-no-evil）* 和 *勿言（speak-no-evil）* 三个猴子图标的编码：

    U+1F648、U+1F649 和 U+1F64A

![](img/39390f6d56c5a83b28db083a8bd5185c_280_0.png)

2.  输出到浏览器的任何 Unicode 内容都必须被正确标识。这通常通过 meta 标签来实现。你应该将字符集设置为 UTF-8。以下是一个示例：

    ```html
    <head>
        <title>PHP 7 Cookbook</title>
        <meta http-equiv="content-type"
        content="text/html;charset=utf-8" />
    </head>
    ```

3.  传统的方法是使用 HTML 来显示图标。因此，你可以这样做：

    ```html
    <table>
        <tr>
            <td>&#x1F648;</td>
            <td>&#x1F649;</td>
            <td>&#x1F64A;</td>
        </tr>
    </table>
    ```

4.  从 PHP 7 开始，你可以使用以下语法构建完整的 Unicode 字符：`"\u{xxxx}"`。这里有一个示例，使用的是与前一点相同的三个图标：

    ```php
    <table>
        <tr>
            <td><?php echo "\u{1F648}"; ?> </td>
            <td><?php echo "\u{1F649}"; ?> </td>
            <td><?php echo "\u{1F64A}"; ?> </td>
        </tr>
    </table>
    ```

![](img/39390f6d56c5a83b28db083a8bd5185c_281_0.png)

### 工作原理...

在 PHP 7 中，引入了一种新语法，允许你渲染任何 Unicode 字符。与其他语言不同，新的 PHP 语法允许使用可变数量的十六进制数字。基本格式如下：

```php
"\u{xxxx}"
```

整个结构必须使用双引号（或使用 **heredoc**）。*xxxx* 可以是 2、4、6 位或更多位的十六进制数字组合。

创建一个名为 *chap_08_emoji_using_html.php* 的文件。确保包含 *meta* 标签，以指示浏览器正在使用 UTF-8 字符编码：

```html
<!DOCTYPE html>
<html>
    <head>
        <title>PHP 7 Cookbook</title>
        <meta http-equiv="Content-type"
            content="text/html;charset=utf-8" />
    </head>
```

接下来，设置一个基本的 HTML 表格，并显示一行表情符号/Emoji：

```html
<body>
    <table>
        <tr>
            <td>&#x1F648;</td>
            <td>&#x1F649;</td>
            <td>&#x1F64A;</td>
        </tr>
        <tr>
            <td><?php echo "\u{1F648}"; ?></td>
            <td><?php echo "\u{1F649}"; ?></td>
            <td><?php echo "\u{1F64A}"; ?></td>
        </tr>
    </table>
</body>
</html>
```

这是从 Firefox 中看到的输出结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_282_0.png)

### 参见

- 要查看 Emoji 代码列表，请访问 `http://unicode.org/emoji/charts/full-emoji-list.html`

## 转换复杂字符

访问完整 Unicode 字符集的能力为渲染复杂字符开辟了诸多新的可能性，尤其是非 Latin-1 字母表中的字符。

### 如何操作...

1.  某些语言是从右向左阅读，而不是从左向右阅读。例子包括希伯来语和阿拉伯语。在本例中，我们将展示如何使用 U+202E Unicode 字符（从右向左覆盖）来显示反向文本。以下代码行会打印出 *txtet desreveR*：

    ```php
    echo "\u{202E}Reversed text";
    echo "\u{202D}"; // returns output to left-to-right
    ```

    完成时，别忘了调用从左向右覆盖字符 U+202D！

2.  另一个需要考虑的因素是使用组合字符。一个例子是 ñ（n 字母上方带有波浪线 -- 悬浮在上）。它用于诸如 *mañana*（西班牙语中的早晨或明天，视语境而定）等单词中。存在一种 *组合字符*，由 Unicode 编码 U+00F1 表示。以下是其使用示例，它输出 *mañana*：

    ```php
    echo "ma\u{00F1}ana"; // shows mañana
    ```

3.  然而，这可能会影响搜索可能性。想象一下，如果你的客户键盘上没有这个组合字符。如果他们输入 *man* 试图搜索 *mañana*，他们将无法找到结果。

4.  能够访问 *完整 Unicode* 集提供了其他可能性。你可以不使用 *组合* 字符，而是使用原始字母 n 和 Unicode *组合* 代码的组合，后者会在字母上方放置一个悬浮的波浪线。在这个 echo 命令中，输出结果与之前相同。只有单词的形成方式不同：

    ```php
    echo "man\u{0303}ana"; // also shows mañana
    ```

5.  对于重音符号也可以应用类似的方法。考虑法语单词 *élève*（学生）。你可以使用组合字符来渲染它，或者使用 *组合* 代码将重音符号悬浮在字母上方。考虑以下两个示例。两个示例产生相同的输出，但渲染方式不同。

    ```php
    echo "\u{00E9}\u{006C}\u{00E8}\ve";
    echo "e\u{0301}\u{006C}e\u{0300}ve";
    ```

### 工作原理...

创建一个名为 chap_08_control_and_combining_unicode.php 的文件。确保包含 meta 标签，以指示浏览器正在使用 UTF-8 字符编码：

```html
<!DOCTYPE html>
<html>
<head>
    <title>PHP 7 Cookbook</title>
    <meta http-equiv="content-type"
          content="text/html;charset=utf-8" />
</head>
```

接下来，设置基本的 PHP 和 HTML 以显示之前讨论的示例：

```html
<body>
<pre>
<?php
    echo "\u{202E}Reversed text"; // reversed
    //echo "\u{202D}"; // stops reverse
    echo "mañana"; // using pre-composed characters
    echo "ma\u{00F1}ana"; // pre-composed character
    echo "man\u{0303}ana"; // "n" with combining ~ character
                           (U+0303)
    echo "élève";
    echo "\u{00E9}l\u{00E8}ve"; // pre-composed characters
    echo "e\u{0301}le\u{0300}ve"; // e + combining characters
?>
</pre>
</body>
</html>
```

这是来自浏览器的输出结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_284_0.png)

## 从浏览器数据获取区域设置

为了改善网站上的用户体验，以用户区域设置（locale）可接受的形式显示信息至关重要。**区域设置（Locale）** 是一个通用术语，用于指示世界上的某个地区。IT 社区已经努力通过由语言和地区代码组成的两部分标识来编码区域设置。但当某人访问你的网站时，你如何知道他们的区域设置？也许最有用的一种技术是检查 HTTP 语言头。

### 如何操作...

1.  为了封装区域设置功能，我们将假设有一个类，`Application\I18n\Locale`。我们将让该类继承一个现有的类，`Locale`，它是 PHP `Intl` 扩展的一部分。

    > 注意
    > **I18n** 是 **国际化（Internationalization）** 的常见缩写。（数一下字母的数量！）

    ```php
    namespace Application\I18n;
    use Locale as PhpLocale;
    class Locale extends PhpLocale
    {
        const FALLBACK_LOCALE = 'en';
        // some code
    }
    ```

2.  为了了解传入请求的样子，请使用 `phpinfo(INFO_VARIABLES)`。测试完成后请立即禁用此函数，因为它会向潜在的攻击者泄露过多信息：

    ```php
    <?php phpinfo(INFO_VARIABLES); ?>
    ```

3.  区域设置信息存储在 `$_SERVER['HTTP_ACCEPT_LANGUAGE']` 中。其值将采取以下通用形式：`ll-CC,r1;q=0.n, ll-CC,r1;q=0.n`，如下表所述：

    | 缩写 | 含义 |
    |---|---|
    | ll | 表示语言的双字符小写代码。 |
    | - | 在区域设置代码 ll-CC 中分隔语言和地区。 |
    | CC | 表示地区的双字符大写代码。 |
    | , | 分隔区域设置代码和回退 **根区域设置（root locale）** 代码（通常与语言代码相同）。 |
    | r1 | 表示建议根区域设置的双字符小写代码。 |
    | ; | 分隔区域设置信息和质量。如果缺失质量值，默认为 q=1（100%）概率；这是首选。 |
    | q | 质量。 |
    | 0.n | 0.00 到 1.0 之间的某个值。将此值乘以 100 即可得到该访问者实际上偏好此语言的百分比概率。 |

4.  列出的区域设置可能不止一个。例如，网站访问者的计算机上可能安装了多种语言。PHP Locale 类恰好有一个方法，`acceptFromHttp()`，它读取 `Accept-language` 头字符串并给我们所需的设置：

    ```php
    protected $localeCode;
    public function setLocaleCode($acceptLangHeader)
    {
        $this->localeCode =
            $this->acceptFromHttp($acceptLangHeader);
    }
    ```

5.  然后我们可以定义适当的获取器。`getAcceptLanguage()` 方法返回来自 `$_SERVER['HTTP_ACCEPT_LANGUAGE']` 的值：

    ```php
    public function getAcceptLanguage()
    {
        return $_SERVER['HTTP_ACCEPT_LANGUAGE'] ??
               self::FALLBACK_LOCALE;
    }
    public function getLocaleCode()
    {
        return $this->localeCode;
    }
    ```

