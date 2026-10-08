
# 第 9 章

# Tidy 扩展

至此，你应该已经完成了网络爬虫流程中的检索阶段，原始的响应体已准备就绪，等待进一步分析。恭喜你在整个过程中达到了半程里程碑。

虽然其他响应格式也是可能的，但你极有可能正在处理基于标记的语言，例如 **HTML** 或 **XHTML**。因此，本章及后续章节将专门讨论这些格式。通常情况下，所使用的语言是 HTML。

有许多可用的专注于 XML 的 PHP 扩展可以处理标记语言，这些将在后续章节中审查。虽然这些扩展确实提供了一些对 HTML 的支持，并且在处理格式错误的标记时也有一定的宽容度，但格式良好的 XHTML 才是它们的理想输入。鉴于此，分析过程的第一步是对响应体进行必要的清理，以最大程度地减少在后续分析过程中可能遇到的问题数量。

## 验证

万维网联盟（W3C）提供了一个标记验证服务，旨在促进对 Web 标准的遵守。你可以通过访问 `http://validator.w3.org` 来访问此服务。它接受通过 URL、文件上传或直接输入方式提交的标记进行测试。这将让你了解你的文档是否存在标记格式问题，如果存在的话，具体是什么问题。

## Tidy

清理标记格式错误有两种方式。一种是手动方式，涉及使用基本的字符串操作函数或正则表达式函数，但这种方式很快就会变得杂乱且难以管理。另一种方式更为自动化，涉及使用 tidy 扩展来定位和修正标记问题。虽然这个过程是可配置的，但显然它缺乏手动处理时的那种细粒度控制。

本章的大部分内容将侧重于使用 tidy 来修正标记问题。对于那些 tidy 无法令你满意地处理的问题，前面提到的涉及字符串和正则表达式函数的方法是你的替代方案。正则表达式将在后续章节中更详细地介绍。

tidy 扩展提供两种 API 风格：过程式和面向对象的。两者提供的功能大多等效（相关差异将在后文说明），选择使用哪一种纯属个人偏好。尽管两种 API 风格都使用 tidy 类的对象，但为了语法的一致性，建议在可行范围内尽量只使用一种风格。本章中的代码示例将同时使用这两种风格。

## 输入

在修正一组标记数据中的标记问题之前，必须将数据解析到一个 tidy 对象中。通常情况下，当标记数据准备被解析时，它已经包含在一个字符串中，但也可能存储在一个外部文件中。请参阅下文，了解如何处理这两种情况的示例。

```php
<?php
// 过程式
$tidy = tidy_parse_string($string, $config);
$tidy = tidy_parse_file($filename, $config);

// 面向对象
$tidy = new tidy;
$tidy->parseString($string, $config);
$tidy->parseFile($filename, $config);
?>
```

## 配置

与 cURL 扩展类似，tidy 扩展在很大程度上依赖于配置概念；因此，上述示例中的所有调用都包含 $config 参数。与大多数其他扩展不同，此参数实际上可以是两种形式之一：一个由设置-值对组成的关联数组，或者指向外部配置文件的路径。

配置文件格式与 CSS 样式表中的单独样式设置有些相似。一个示例如下所示。非开发人员不太可能需要访问这些配置设置，也不会像使用 tidy 访问 PHP 源代码那样访问它们。因此，将配置分离到外部配置文件中，其唯一的作用实际上是为了避免使源代码被设置项弄乱。此外，由于配置文件是从磁盘读取的，在高使用率下可能会带来性能方面的顾虑。

```
// 单行注释
/* 多行注释 */
indent: false /* 设置: 值 */
wrap: 78
```

当使用面向对象的 API 时，使用配置文件的替代方案是子类化 tidy 类，并覆盖其 parseString 和 parseFile 方法，以自动包含特定的配置设置值。这种方法允许轻松复用 tidy 配置。

```php
<?php
class mytidy extends tidy {
    private $._default = array(
        'indent' => false,
        'wrap' => 78
    );
```

```php
public function parseFile($filename, $config, $encoding, $use_include_path=false) {
    return parent::parseFile(
        $filename,
        array_merge($this->_default, $config),
        $encoding,
        $use_include_path
    );
}

public function parseString($filename, $config, $encoding, $use_include_path=false) {
    return parent::parseString(
        $filename,
        array_merge($this->_default, $config),
        $encoding,
        $use_include_path
    );
}
?>
```

- `array_merge` 用于将 `$_default` 属性中的默认参数值合并到指定的 `$config` 数组中。在原始 `$config` 数组中指定的任何参数都将优先于在 `$_default` 中指定的对应参数。
- `parseFile` 和 `parseString` 将修改后的 `$config` 参数以及其他提供的参数传递到 tidy 类中各自的方法，并返回相应的返回值。

## 选项

Tidy 包含大量配置选项，其中只有少数几个与本书的上下文相关。

两个选项涉及适用于网络爬虫的输出格式：`output.html` 和 `output.xhtml`。两者都指定为布尔值。这些选项是互斥的，意味着在任何给定时间只能将其中一个设置为 `true`。通常 `output.xhtml` 更可取，但可能并不总是可行。重要的是将 tidy 的输出与原始文档进行比较，以确认修正文档格式错误没有导致数据丢失。

根据使用时的配置，文档编码可能是后来会出现问题的领域之一。例如，XMLReader 扩展内部使用 UTF-8 编码，如果你的输入文档的编码与此冲突，可能会产生问题。`input-encoding` 和 `output-encoding` 可用于控制各自的假设编码。

其他选项主要用于调试目的，在生产环境中通常应将其关闭。这是一个子类化 `tidy` 类以控制默认选项值的好理由，以便可以轻松访问两组不同的配置，用于不同的开发环境。

这三个选项是 `indent`、`indent-spaces` 和 `indent-attributes`。其中的第一个，`indent`，是一个布尔值，指示 tidy 是否应应用缩进，以使元素之间的层级关系在视觉上更突出。`indent-spaces` 是一个整数，表示用于表示单级缩进的空格字符数量，默认为 2。最后，`indent-attributes` 是一个布尔值，指示元素内的每个单独属性是否应在新行开始。

说到属性，`sort-attributes` 可以设置为 `alpha`，以便按字母顺序对元素属性进行排序。默认设置为 `none`，这将禁用排序。

如果文档中的行往往很长且难以阅读，`wrap` 选项可能很有用。它是一个整数，表示 tidy 在强制换行前每行应允许的最大字符数。默认设置为 68，可以将其设置为 0 来完全禁用。

没有空行来分隔代码块也可能使标记难以阅读。`vertical-space` 是一个布尔值，旨在通过添加空行来提高可读性。默认情况下它是禁用的。

## 调试

尽管 tidy 做得很好，但它并不总能清理文档。当使用 tidy 修复文档时，检查其遇到的问题是通常是个好主意。

