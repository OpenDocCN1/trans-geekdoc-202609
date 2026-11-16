

```
public static function printArray($var, $title = true) {

    $string = '<table border="1">';
    if ($title) {
        $string .= "<tr><td><b>Key</b></td><td><b>Value</b></td></tr>\n";
    }

    if (is_array($var)) {
        foreach($var as $key => $value) {
            $string .= "<tr>\n";
            $string .= "<td><b>$key</b></td><td>";

            if (is_array($value)) {
                $string .= Debugger::printArray($value, false);
            } elseif (gettype($value) == 'object') {
                $string .= "Object of class " . get_class($value);
            } else {
                $string .= "$value";
            }

            $string .= "</td></tr>\n";
        }
    }

    $string .= "</table>\n";
    return $string;
}
?>
```

文件顶部定义的五个常量用于定义调试级别，其工作方式与 class.Logger.php 中的日志级别常量完全相同。debug() 方法期望在全局命名空间中找到一个名为 $cfg 的数组，该数组包含一个定义整个应用程序当前调试级别的 DEBUG_LEVEL 元素。

默认情况下，调试级别为 DEBUG_INFO，尽管 debug() 的第三个参数允许您将其设置为任何级别。这样，您可以通过简单修改 $cfg['DEBUG_LEVEL'] 来显示想要多多或少少的调试信息。

$key 参数是调试数组中信息的可选标签。虽然它在参数列表中排在第二位，但它将出现在 debugPrint() 最终生成的表格的最左侧列。

debugPrint() 函数只是将会话中的调试信息传递给 printArray() 方法，后者完成所有真正繁重的工作。在打印调试信息后，debugPrint() 会清空会话数组，以便为下一次页面视图清除调试信息。

printArray() 接受至少一个维度的数组，并打印一个显示该数组内容的 HTML 表。多维数组得到了正确处理。对象仅打印其类名。

以下代码展示了该类的使用方法：

```
<?php

require_once( 'class.Debugger.php' );
require_once( 'class.Config.php' );

Config::addConfig( 'DEBUG_LEVEL', DEBUG_INFO );

$myData = array();
$myData[] = 'hello';
$myData[] = array( 'name' => 'Bob',
        'colors' => array( 'red', 'green', 'blue' ) );

Debugger::debug( $myData, 'my data' );
$x = 5 + 8;
Debugger::debug( $x, 'x' );

Debugger::debugPrint();

?>
```

通过查看 Figure 9-1 中的屏幕输出，可以更容易地理解此示例，该图显示了 debugPrint() 函数的输出。

![](img/a1b732997d9cb194dceec0570dc79710_231_0.png)

Figure 9-1: debugPrint() 函数的屏幕输出

## Summary

`Logger` 类可以扩展以支持将日志信息记录到几乎任何可想象的数据存储库中。只需创建并使用最能支持您需求的后端即可。对于大多数用途，`fileLoggerBackend` 类应该是最合适的，但使用数据库也有某些明确的优势。

`Debugger` 类提供了与 `Logger` 类类似的功能，但允许信息显示在屏幕上并存储在会话中以供显示，即使原始页面请求不包含任何输出。

在第 10 章中，您将学习如何使用 PHP 6 编写和交互 Web 服务，这使您能够与第三方提供的数据和功能进行交互。

## Writing and Using Web Services

在使用 PHP 构建应用程序时，可用的模块和 PEAR 包数量庞大，您可能会觉得 PHP 几乎无法在短时间内实现相当复杂的业务需求。从图像处理和复杂的日期/时间运算到事务性数据库交互，PHP 确实大量开箱即用。但是，您可能希望在应用程序中提供一些功能，却无法实现，要么是因为您缺乏数据且获取数据过于麻烦（例如，为整个互联网开发自己的搜索引擎），要么是因为应用程序逻辑远比项目预算所允许的要复杂得多（例如，创建交互式地理信息系统应用程序）。

幸运的是，许多应用程序提供商通过应用程序编程接口 (API) 暴露其应用程序的功能，该接口允许以无标记的方式交换数据。通常，这涉及通过 HTTP 进行调用，使用按照某些规则和标记格式构建的请求，并以结构化的方式接收响应，通常是 XML，但也常为其他格式（CSV、JSON 等等）。由于此响应是结构化数据，而不是包含 HTML 或其他样式化输出的数据，您可以以任何喜欢的方式使用和显示它。

如果您的应用程序是 HTML，则将输出转换为 HTML。如果您的应用程序是 Flash，则可以以最适合您的 Flash 应用程序的方式输出。此外，您与 Web 服务的交互不需要向用户产生任何输出，而是可用于填充或增强数据库中的数据（例如，使用地理定位服务获取位置列表的纬度和经度值）。

利用另一应用程序的 Web 服务 API，使您能够将该应用程序与您自己的数据和功能创建“混搭”（mashups）。本章描述了与 Web 服务 API 交互的多种方法，包括一些更流行的商业服务，例如 Google 和 Yahoo!。您将学习如何结合它们的数据来创建自己的应用程序。最后，您将学习如何将您应用程序的功能暴露给他人，以便他们可以利用您的应用程序，并且您还将发现如何从这种方法中受益。

与 Web 服务 API 交互存在众多不同的标准。“Web 服务”这一术语绝不意味着特指其中任何一种。该术语仅暗示通过 HTTP 对另一应用程序进行远程调用的概念。通信的实际性质由几种既定数据交换协议之一管理，通常由 W3C 监督。本章介绍了 Web 服务中几种最流行的协议。

### SOAP

简单对象访问协议 (SOAP) 是 Web 服务协议中最强大的一种，允许发现应用程序功能、自动确定数据类型、数据验证功能以及复杂的请求-响应数据结构。SOAP 使用 XML 架构进行数据交换，通常作为通信协议的 HTTP 上层（尽管也有主要是理论上的使用 SMTP 或其他协议作为通信层的实现）。

所有这些强大功能的缺点是，相当复杂（意味着灵活且可能复杂）的请求-响应结构功能意味着数据结构 *必然* 复杂（意味着难以理解且难以实现）。因此，已开发了许多 PHP 包，它们作为 XML 数据结构和 HTTP 交互实际实现的包装器。

XML 是一个庞大的主题，本章并未详细介绍。您应具备基本的 XML 知识才能理解和使用本章。如果您不熟悉 XML 但希望打下良好的基础，您可能想查看 *Beginning XML, Fourth Edition* (Wiley, 2007)。本章的下一部分将探讨如何在 PHP 6 中使用 SOAP 实现基于 XML 的 Web 服务。

### SOAP and PHP 6

SOAP 是一种与平台无关的消息协议——也就是说，它乐于使用各种互联网协议，例如 HTTP、SMTP，甚至 MIME。您已经知道它将 XML 作为其信息交换方法的一部分，这里要注意的是，Web 服务描述语言 (WSDL) 也被用来让您的生活更轻松。本讨论探讨了如何使用将由 SOAP 访问的服务。WSDL 以及 SOAP 的所有其他方面，将在本章稍后部分更详细地探讨。

SOAP 做什么？简单的答案是，它使您能够在去中心化的分布式环境中传递结构化、类型化数据。这意味着您可以将数据中心运行 PHP 应用程序的 GNU/Linux 服务器上的请求传递到另一大洲的 Solaris 机器上的 J2EE 应用程序，并期待一个完全连贯的响应。使用 SOAP，过去许多数据转换和系统集成问题得以解决，并且适用于所有带有可行 XML 解析器的平台的远程过程调用机制可用且文档齐全。（目前，几乎每个会以企业能力部署的主要平台都具有 XML 解析功能和可用的 HTTP 实现。）

