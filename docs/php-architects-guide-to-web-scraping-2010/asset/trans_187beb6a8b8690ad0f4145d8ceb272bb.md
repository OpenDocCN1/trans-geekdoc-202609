
## 警告和错误

在使用 tidy 进行网络抓取分析时，需要检查两类问题：警告和错误。与它们的 PHP 对应物类似，警告是非致命的，并且通常有某种自动化响应，tidy 会执行以处理它们。错误不一定是致命的，但表明 tidy 可能无法处理某个特定问题。

所有问题都会根据其类型存储在一个错误缓冲区中。访问该缓冲区内的信息及其相关信息，是 tidy 扩展的过程式和面向对象 API 之间存在差异的一个领域。

```php
<?php
// 过程式
$issues = tidy_get_error_buffer($tidy);

// 面向对象
$issues = $tidy->errorBuffer;
?>
```

请注意，`errorBuffer` 是 `$tidy` 对象的一个属性，而不是方法。还要注意，过程式函数和对象属性之间的命名约定略有不同，这与 API 其他大多数区域保持一致的做法形成了对比。

字符串中包含的错误缓冲区本身几乎没什么用。下面是一个代码示例，它源自 PHP 手册页面上关于 `tidy_get_error_buffer` 函数的用户贡献评论。这会将每个问题的各个组件解析到数组中，以便于访问。

```php
<?php
preg_match_all(
        '/^(?:line (?:P<line>\d+) column (?:P<column>\d+) - ?)' .
        '(?:P<type>\S+): (?:(?:(?:\d+\.?){4}):)?(?:P<message>.*)?$/m',
        $tidy->errorBuffer, // 或 tidy_get_error_buffer($tidy)
        $issues,
        PREG_SET_ORDER
);

print_r($issues);
/*
示例输出：
Array
(
    [0] => Array
        (
            [0] => line 12 column 1 - Warning: <meta> element not
                empty or not closed
            [line] => 12
            [1] => 12
            [column] => 1
            [2] => 1
            [type] => Warning
            [3] => Warning
            [message] => <meta> element not empty or not closed
            [4] => <meta> element not empty or not closed
        )
)
*/
?>
```

tidy 扩展还提供了一种方法来获取遇到的警告和错误数量，而不需要手动解析错误缓冲区。不幸的是，而且有些奇怪的是，这只在过程式 API 中受到支持。然而，通过子类化 tidy 类将其添加到面向对象 API 中是相当简单的。两者的示例如下所示。

```php
<?php
// 过程式
$warnings = tidy_warning_count($tidy);
$errors = tidy_error_count($tidy);

// 面向对象
class mytidy extends tidy {
    public function warningCount() {
        return tidy_warning_count($this);
    }
    public function errorCount() {
        return tidy_error_count($this);
    }
}
?>
```

### 输出

获取 tidy 修复文档后的结果输出相当简单。

```php
<?php
// 过程式
$output = tidy_get_output($tidy);

// 面向对象
$output = (string) $tidy;
?>
```

虽然面向对象 API 没有公开声明魔术方法 `__toString`，但它也可以强制转换为字符串，也可以使用 `echo` 语句直接输出。

### 总结

本章到此结束。此时，你应该已经将获得的文档转换为适合输入到 XML 扩展的格式。接下来的几章将专门介绍如何使用特定的扩展从修复后的文档中搜索和提取数据。

有关 tidy 扩展的 PHP 手册部分，请访问 http://php.net/tidy。

有关 tidy 库本身的文档，请访问 http://tidy.sourceforge.net/#docs。

有关 tidy 配置设置参考，请访问 http://tidy.sourceforge.net/docs/quickref.html。

## 第 10 章

## DOM 扩展

一旦检索到的标记文档被清理并通过验证，下一步就是从中提取有用的数据。为此，理想的方法是利用文档是有效标记这一事实，并应用一个 XML 扩展。PHP 有几种这样的扩展，接下来的几章将专门介绍它们。

本章的同名主题是文档对象模型（DOM）扩展。该扩展的名称来源于一种标准化的、语言无关的 API，用于导航和操作有效的、格式良好的 XML 和 HTML 文档。该标准由致力于新兴互联网相关标准的万维网联盟（W3C）维护并推荐。本章不会全面覆盖 DOM 扩展，仅涉及与网络抓取相关且必不可少的部分。

> **注意：DOM XML**
> DOM 扩展仅在 PHP 5 中可用。其 PHP 4 兼容的前身 DOM XML 扩展具有略微不同的 API，但共享许多相同的概念。本章的示例将仅限于 DOM 扩展。有关 DOM XML 扩展的等效细节，可以参考 PHP 手册的相关章节，请访问 http://php.net/manual/en/book.domxml.php。

在继续深入之前，你应该知道有两种类型的 XML 解析器：**树解析器**和**拉取解析器**。树解析器将整个文档加载到内存中，允许你在任何时候访问其任何部分并进行操作。拉取解析器逐块读取文档，并限制你只能处理当前正在读取的部分。

这两种类型的解析器共享类似 `file_get_contents` 和 `fgets` 函数之间的关系：前者允许你一次处理整个文档，并使用存储它所需的任何内存，而后者允许你一次处理文档的一部分，并在过程中使用更少的内存。

在处理相当大的文档时，较低的内存使用率通常是更可取的选择。试图一次性将巨大的文档加载到内存中，对本地系统的影响与限制客户端对 Web 服务器的影响相同：在这两种情况下，资源都被消耗，系统性能都会因压力而减弱，直到系统最终锁死或崩溃。

DOM 扩展是一个树解析器。一般来说，网络抓取并不要求能够同时访问文档的所有部分。然而，使用拉取解析器实现网络抓取所涉及的数据提取类型可能相当复杂。选择哪种扩展取决于文档的大小和复杂度。

## 加载文档

DOMDocument 类是开始使用 DOM 扩展的地方。首先要做的是实例化它，然后输入已验证的标记数据。请注意，如果加载的文档无效或格式良好，DOM 扩展在加载文档时会产生警告。为了避免这种情况，请参见上一章中关于使用 tidy 扩展的内容。如果 tidy 未能消除问题，错误可以按照下面的示例进行控制。请注意，错误会被缓冲直到手动清除，因此如果不再需要它们，请在每次加载操作后清除它们，以避免浪费内存。

```php
<?php
// 缓冲 DOM 错误，而不是将其作为警告发出
$oldSetting = libxml_use_internal_errors(true);

// 实例化一个文档容器
$doc = new DOMDocument;

// 加载已包含在字符串中的标记
$doc->loadHTML($htmlString);

// 加载保存到外部文件的标记
$doc->loadHTMLFile($htmlFilePath);

// 获取所有错误（如果需要）
$errors = libxml_get_errors();

// 只获取最后一个错误
$error = libxml_get_last_error();

// 清除来自先前操作的任何现有错误
libxml_clear_errors();

// 将错误缓冲恢复到其先前的设置
libxml_use_internal_errors($oldSetting);
?>
```

## 树术语

一旦文档被加载，下一个自然的步骤就是从中提取所需的数据。然而，这样做需要对 DOM 的结构有更深入的了解。回想之前提到的树解析器。如果你有任何计算机科学背景，你会很高兴地知道，在树解析器的语境中，“树”一词确实指的是同名数据结构。如果没有，以下是相关概念的简要说明。

**树**是一种分层结构（想想家谱），由**节点**组成，这些节点在 DOM 扩展中作为 `DOMNode` 类存在。节点之于树，就像元素之于数组：只是存在于数据结构中的项目。

每个单独的节点可以有零个或多个**子节点**，这些子节点在 `DOMNode` 类中由 `childNodes` 属性集体表示。`childNodes` 是类 `DOMNodeList` 的一个实例，这听起来正是它的样子。其他相关的 proper-

