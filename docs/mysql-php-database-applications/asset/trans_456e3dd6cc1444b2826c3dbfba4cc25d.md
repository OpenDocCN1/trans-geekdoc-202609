

## SOAP 概述

归根结底，SOAP 确实配得上它的首字母缩写：它确实很简单。SOAP 消息本质上是应用了一些特殊标签的文本段落，在某种程度上类似于 HTML 文档。

SOAP 规范既不关心传输事务（那是 HTTP 和 SMTP 规范的职责），也不关心 SOAP 消息可以携带什么内容的规则（反正也不多；这取决于构建使用 SOAP 的应用程序的开发人员）。SOAP 定义主要涉及携带对象提供服务的函数调用以及将结果返回给调用程序的文档结构。

您可以将 SOAP 事务分为请求和响应。客户端通过发送给服务器的 SOAP 消息说些类似“首席执行官的内腿长是多少？”的话。当然，这假设服务器有一个查询或以其他方式提供老板内腿长度的函数。

服务器随后执行被调用的函数，并返回某个值或一系列值。它可能只返回整数 34，或者返回整数 34 以及字符串 inches，以明确使用的单位。

现在是时候来看看 SOAP 消息本身了。虽然 SOAP 规范包含大量特殊功能（例如附件）的信息，但 SOAP 消息本质上是信封及其内容。本章中我们创建的应用程序不需要除这些关键功能之外的其他 SOAP 功能。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_565_0.png)

您可以在网上查看完整的 SOAP 1.2 规范：http://www.w3.org/TR/soap12-part0。（顺便说一句，不要去 http://www.soap.org 期望找到关于 SOAP 协议的信息。该网站由产科麻醉学与围产期医学会运营——“庆祝产科麻醉学150年以上”）。

## SOAP 信封

信封包围消息有效载荷（或正文），并用于定义整个 SOAP 消息中使用的 XML 命名空间。

由于它是 XML 文档，SOAP 文本以其 XML 编码和版本声明开头：

```
<?xml version='1.0' encoding='UTF-8'?>
```

然后是带有 SOAP-ENV 命名空间标识符的开头 Envelope 标签。确实，开头 Envelope 标签主要用于定义 SOAP 消息中使用的四个命名空间中的三个。以下是开头 Envelope 标签：

```
<SOAP-ENV:Envelope
xmlns:SOAP-ENV="http://www.w3.org/2001/09/soap-encoding"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns:xsd="http://www.w3.org/2001/XMLSchema">
```

虽然 XML 命名空间的复杂性超出了本书的范围，但请了解该代码段中定义的三个命名空间的作用如下：

- SOAP-ENV – 提供此 SOAP 消息中 Envelope 和 Body 元素的定义。SOAP 1.2 规范为 http://www.w3.org/2001/09/soap-encoding。该 URL 在 Microsoft Internet Explorer 中可轻松呈现；其他浏览器可能需要您下载 XML 并在文本查看器（例如 vi、emacs 或 Windows Notepad）中查看。
- xsi – xsi 架构定义函数调用的各个方面，例如作为参数发送的值。
- xsd – xsd 架构处理数据类型，例如整数、日期、字符串和布尔值。

开头 Envelope 标签之后是整个 Body 元素（将在下一节讨论）。在 SOAP 消息结束时，在 Body 元素之后，您会找到一个带有命名空间标识符的闭合 Envelope 标签，如下所示：

```
</SOAP-ENV:Envelope>
```

现在让我们继续了解 Body 元素。

## SOAP 正文

SOAP 信封内部是 SOAP 正文，即拥有 SOAP 的核心所在——有效载荷。正文以带有 SOAP-ENV 命名空间标识符的开头 Body 标签开始：

```
<SOAP-ENV:Body>
```

接下来是 SOAP 消息的核心内容——在这里是一个函数调用。您正在调用的函数的名称就是调用它的元素名称。命名空间标识符（传统上为 ns1）位于函数名称之前，如下所示：

```
<ns1:getInseam
xmlns:ns1="urn:referenceToWebService"
SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
```

那其他的那些东西都是什么意思？嗯，命名空间定义说明了函数 getInseam() 在网络上的位置。SOAP-ENV:encodingStyle 值进一步标准化了简单和复杂数据类型在 SOAP 事务双方呈现的方式。

接下来的问题是您想检索谁的内腿长度。此说明符应作为参数呈现给函数，也就是说，在对函数的传统（进程内）调用中，语法看起来类似这样：

```
GetInseam("Joe Bloggs")
```

在 SOAP 中，您被迫以略有不同的方式处理事务。请记住，您已经位于 getInseam 元素内部，这意味着您已经明确了 getInseam 是您正在调用的函数。您现在需要指定参数。出于逻辑考虑，您可以使用一个名称与远程类中指定的参数名称匹配的元素来完成此操作：

```
<person xsi:type="xsd:string">Joe Bloggs</person>
```

完成此操作后，您还需要关闭 getInseam 元素和 Body 元素：

```
</ns1:getInseam>
</SOAP-ENV:Body>
```

所有这些在实际中是什么样子的？下一节将介绍一个请求/响应对，其中调用并响应了 getInseam()。

## 典型的请求/响应对

SOAP 事务由请求和响应组成，在很多方面与使用浏览器订购网页时的请求和响应类似。请记住，SOAP 传输只不过是经过 XML 标记的文本段落，以便服务于特殊的 SOAP 目的。

## 请求

以下是完整的请求：

```
<?xml version='1.0' encoding='UTF-8'?>
<SOAP-ENV:Envelope
xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<SOAP-ENV:Body>
<ns1:getInseam
xmlns:ns1="urn:referenceToWebService"
SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"
<person xsi:type="xsd:string">Joe Bloggs</person>
</ns1:getInseam>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

请求在最简单的情况下，就是信封内部的 Body 元素。如果您愿意，可以使事情更复杂——规范允许（其中包括）一个补充的 Header 元素，用于描述多个 SOAP 消息之间的关系或描述消息应如何路由。

## 响应

从格式上看，响应与请求非常相似。它们具有完全相同的信封格式，正文仅在所发送元素的名称上有所不同。通常，这与请求中指定的元素名称相同，并附加了 Response。

以下是与您之前的请求匹配的完整响应：

```
<?xml version='1.0' encoding='UTF-8'?>
<SOAP-ENV:Envelope
xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<SOAP-ENV:Body>
<ns1:getInseamResponse
xmlns:ns1="urn:referenceToWebService"
SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"
<return xsi:type="xsd:float">34.0</return>
</ns1:getInseamResponse>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

不太复杂，对吧？Joe Bloggs 的内腿长度为 34。那可能是 34 英寸。然而，Joe 可能是一个内腿长度为 34 厘米的孩子吗？此响应无法让我们得知。

要将复杂数据结构编码为 SOAP 消息（请求和响应），您需要深入研究规范。下一节将介绍如何将数组编码为 SOAP 消息。

## 复杂数据类型

复杂数据类型是多部分数据类型。数组是复杂数据类型的一个示例，其中成员通过编号访问。结构体，正如你们

