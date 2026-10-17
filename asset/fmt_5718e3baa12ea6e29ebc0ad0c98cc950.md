
作为本章中的示例 XML 文件和格式，以下代码中的 XML 重用了上一章中的 `quotes` 数据库示例。如你所见，`<quotes>` 是根元素，每个引语（包括其作者和短语诞生的年份）都包含在 `<quote>` 元素中。

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<quotes>
  <quote year="1991">
    <phrase>Hasta la vista, baby!</phrase>
    <author>Arnold Schwarzenegger</author>
  </quote>
</quotes>
```

### 示例 XML 文件（`quotes.xml`；摘录）

### 使用 SAX 解析 XML

```
$sax = xml_parser_create();
```

SAX 是一种解析 XML 文档的方法，但不用于验证。好处是，你可以在 PHP 4 和 PHP 5 中使用它而无需更改。在 PHP 4 中，SAX 解析已在所有平台上可用，因此无需单独安装。

```
<?php
// ...
$sax = xml_parser_create();
xml_parser_set_option($sax, XML_OPTION_CASE_FOLDING, false);
xml_parser_set_option($sax, XML_OPTION_SKIP_WHITE, true);
xml_set_element_handler($sax, 'sax_start', 'sax_end');
xml_set_character_data_handler($sax, 'sax_cdata');
xml_parse($sax, file_get_contents('quotes.xml'), true);
xml_parser_free($sax);
?>
```

你使用 `xml_parser_create()` 创建一个 SAX（XML 简单 API）解析器。该解析器可以查看 XML 文件并对各种事件做出反应。以下三个事件是最重要的：

- 元素的开始
- 元素的结束
- CDATA 块

然后你可以为这些元素定义处理函数，并使用它们将 XML 转换为其他内容，例如超文本标记语言（HTML）。列表 8.1 展示了这一点，并将 XML 文件的内容输出为项目符号 HTML 列表，如图 8.1 所示。函数 `xml_set_element_handler()` 设置元素的开始和结束处理程序，而 `xml_set_character_data_handler()` 设置 CDATA 块的处理程序。使用 `xml_parser_set_option()`，你可以配置处理程序，例如忽略空白并将标签名作为区分大小写处理（然后标签名不会自动转换为大写字母）。以下代码包含处理函数代码：

```
function sax_start($sax, $tag, $attr) {
    if ($tag == 'quotes') {
        echo '<ul>';
    } elseif ($tag == 'quote') {
        echo '<li>' . htmlspecialchars($attr['year']) .
            ': ';
    } elseif ($tag == 'phrase') {
        echo '"';
    } elseif ($tag == 'author') {
        echo ' (';
    }
}
function sax_end($sax, $tag) {
    if ($tag == 'quotes') {
        echo '</ul>';
    } elseif ($tag == 'quote') {
        echo '</li>';
    } elseif ($tag == 'phrase') {
        echo '"';
    } elseif ($tag == 'author') {
        echo ') ';
    }
}
function sax_cdata($sax, $data) {
    echo htmlspecialchars($data);
}
```

![](img/1e6d362f187af50011d2666ddaa68739_249_0.png)

图 8.1 从 XML 创建的 HTML。

**注意**

PHP 5.1 默认包含 `XMLReader`。它是对 `libxml2` 的包装，并模仿用于读取 XML 的 .NET 组件 `XmlTextReader` 的应用程序编程接口（API）。它比 SAX 快得多，而且更容易使用。截至本文撰写时，它还不是很稳定，但看起来很有前景。不是 PHP 5.1 标准发行版的一部分，但在 PECL 中可用的是关联模块 `XMLWriter`，它允许对 XML 进行写访问。有关这两个模块的更多信息可在其作者的演示文稿中找到，网址为 http://php5.bitflux.org/xmloncrack/。

### 在 PHP 4 中使用 DOM 读取 XML

```
domxml_open_mem(file_get_contents('quotes.xml'))
```

W3C 的文档对象模型（DOM）定义了访问 XML 结构中元素的一种统一方式。因此，使用 JavaScript 的 DOM 访问访问 HTML 页面中的元素和使用 PHP 的 DOM 访问访问 XML 文件中的元素非常相似。

```
<?php
$dom =
domxml_open_mem(file_get_contents('quotes.xml'));
echo '<ul>';
foreach ($dom->get_elements_by_tagname('quote') as
    $element) {
    $attr = $element->attributes();
    $year = htmlspecialchars($attr[0]->value);
    foreach ($element->child_nodes() as $e) {
        if (isset($e->tagname)) {
            if ($e->tagname == 'phrase') {
                $node = $e->first_child();
                $phrase = htmlspecialchars
                    ($node->node_value());
            } elseif ($e->tagname == 'author') {
                $node = $e->first_child();
                $author =
                    htmlspecialchars($node->node_value());
            }
        }
    }
    echo "<li>$author: \"$phrase\" ($year)</li>";
}
echo '</ul>';
?>
```

不幸的是，如果你使用 PHP 4，请注意 DOM 访问在版本之间发生了变化，并且在某些系统上并不稳定。Windows 用户必须在 `php.ini` 中使用 `extension=php_domxml.dll`，并且可能需要将 `iconv.dll` 复制到 Windows `system32` 文件夹中。其他系统必须使用 `--with-dom=/path/to/libxml` 重新配置 PHP。然后 `domxml_open_file()` 打开文件——使用绝对路径！更可移植的方法是使用读取字符串的 `domxml_open_mem()`。这两个函数的返回值提供了对两个方法 `get_elements_by_tagname()` 和 `get_element_by_id()` 的访问，它们返回具有特定标签名的所有节点或由其 ID 标识的特定元素。然后每个节点公开一些方法，如下所示：

- `first_child()`—第一个子节点
- `last_child()`—最后一个子节点
- `next_sibling()`—下一个节点
- `previous_sibling()`—上一个节点
- `node_value()`—节点的值

前面的代码使用 DOM 访问 XML 文件中的所有引语并输出它们。

### 在 PHP 5 中使用 DOM 读取 XML

如果你使用 PHP 5，主要优势是使用了 `libxml2`，这是一个比 `libxml` 好得多的库。它捆绑在 PHP 中，因此无需安装。然而，API 已发生巨大变化。首先，你实例化一个 `DOMDocument` 对象，然后 `load()` 一个文件或 `loadXML()` 一个字符串。所有方法名都已更改为驼峰式大小写，并且所有属性都是真正的属性，而不是像 PHP 4 中的方法。前面的代码与前一个示例中的代码做同样的事情，但可在 PHP 5 下运行。

```
<?php
$dom = new DOMDocument();
$dom->load('quotes.xml');
echo '<ul>';
foreach ($dom->getElementsByTagname('quote') as
    $element) {
    $year = $element->getAttribute('year');
    foreach (($element->childNodes) as $e) {
        if (is_a($e, 'DOMElement')) {
            if ($e->tagName == 'phrase') {
                $phrase = htmlspecialchars($e->textContent);
            } elseif ($e->tagName == 'author') {
                $author = htmlspecialchars($e->textContent);
            }
        }
    }
    echo "<li>$author: \"$phrase\" ($year)</li>";
}
echo '</ul>';
?>
```

*使用 DOM 解析 XML（`dom-read5.php`）*

请注意，列表中使用 `is_a()`，以便仅在类型为 `DOMElement` 的节点中评估标签名。这是因为空白被视为一个 DOM 节点（不过类型为 `DOMText`）。

```php
<?php
require_once 'stripFormSlashes.inc.php';
$dom = domxml_open_mem(file_get_contents
    ('quotes.xml'));
$quote = $dom->create_element('quote');
$quote->set_attribute('year', $_POST['year']);
$phrase = $dom->create_element('phrase');
$phrase->set_content($_POST['quote']);
$author = $dom->create_element('author');
$author->set_content($_POST['author']);
$quote->append_child($phrase);
$quote->append_child($author);
$root = $dom->document_element();
$root->append_child($quote);
file_put_contents('quotes.xml', $dom->dump_mem());
echo 'Quote saved.';
?>
```

*使用 DOM 创建 XML (`dom-write4.php`; 摘录)*

前面的代码将作者、引语和年份保存到 XML 文档中，并追加到已有的数据中。

### 在 PHP 5 中使用 DOM 编写 XML

```php
$dom = new DOMDocument();
```

使用 PHP 5 时，代码会略有变化，但大部分变化是改为驼峰式大小写。

```php
<?php
require_once 'stripFormSlashes.inc.php';
$dom = new DOMDocument();
$dom->load('quotes.xml');
```

```php
$quote = $dom->createElement('quote');
$quote->setAttribute('year', $_POST['year']);
$phrase = $dom->createElement('phrase');
$phraseText = $dom->
createTextNode($_POST['quote']);
$phrase->appendChild($phraseText);
$author = $dom->createElement('author');
$authorText = $dom->
createTextNode($_POST['author']);
$author->appendChild($authorText);
$quote->appendChild($phrase);
$quote->appendChild($author);
$dom->documentElement->appendChild($quote);
$dom->save('quotes.xml');
echo 'Quote saved.';
?>
```

*使用 DOM 创建 XML (`dom-write5.php`; 摘录)*

> **注意**
>
> PHP 5 的 DOM 扩展不提供类似 PHP 4 的 `set_content()` 的功能，因此你必须使用 `createTextNode()` 方法来定义节点的文本值，如前面的代码所示。

### 使用 SimpleXML

```php
$xml = simplexml_load_file('quotes.xml');
```

PHP 5.1 中最伟大的新特性之一是 SimpleXML 扩展，其灵感源自 CPAN 中的一个 Perl 模块。这种方法简单而巧妙。访问 XML 最直观的方式可能是通过面向对象编程（OOP）方法：子节点是其父节点/对象的属性，XML 属性则转换为对象属性。这使得访问 XML 变得非常容易，包括完整的迭代器支持，因此可以使用 `foreach`。

```php
<?php
$xml = simplexml_load_file('quotes.xml');
echo '<ul>';
foreach ($xml->quote as $quote) {
    $year = htmlspecialchars($quote['year']);
    $phrase = htmlspecialchars($quote->phrase);
    $author = htmlspecialchars($quote->author);
    echo "<li>$author: \"$phrase\" ($year)</li>";
}
echo '</ul>';
?>
```

*使用 SimpleXML 解析 XML (`simplexml-read.php`)*

此代码使用 `simplexml_load_file()` 加载文件——对于字符串也可以使用 `simplexml_load_string()`——然后读取其中的所有信息。

将其与 DOM 方法进行比较。SimpleXML 在某些情况下可能比 DOM 慢，但编码速度要快得多。

**注意**

写入也很容易完成。然而，不可能在没有外部帮助的情况下追加元素，例如使用 DOM 并通过 `simplexml_import_dom()` 将此 DOM 加载到 SimpleXML 中。

### 使用 XSL 和 PHP 4 转换 XML

```php
$result = $xslt->process($dom);
echo $xslt->result_dump_mem($result);
```

要在 PHP 中使用 XSL 转换（XSLT），你首先必须决定使用哪个 PHP 版本。如果是 PHP 4，你必须在 `php.ini`（Windows）中使用 `extension=php_xslt.dll`，或从 http://www.gingerall.com/ 安装 Sablotron 并使用配置开关 `-enable-xslt -with-xslt-sablot`（适用于其他系统）。

```php
<?php
    $dom =
    domxml_open_mem(file_get_contents('quotes.xml'));
    $xslt = domxml_xslt_stylesheet(
    file_get_contents('quotes.xsl'));
    $result = $xslt->process($dom);
    echo $xslt->result_dump_mem($result);
?>
```

*使用 PHP 4 的 XSLT (`xslt4.php`)*

执行转换分为四个简单的步骤：加载 XML；加载 XSLT；执行转换；最后保存结果。前一段包含这些步骤的代码；下载库中的文件 `quotes.xsl` 包含将引语 XML 转换为众所周知的 HTML 项目符号列表的标记。

### 使用 XSL 和 PHP 5 转换 XML

```php
$result = $xslt->transformToDoc($xml);
echo $result->saveXML();
```
