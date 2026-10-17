
```php
<?php
#### HelloServerWsdl.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
function hello($someone) {
   return "Hello " . $someone . "! - With WSDL";
}
   ini_set("soap.wsdl_cache_enabled", "0");
   $server = new SoapServer("http://localhost/Hello.wsdl",
      array('soap_version' => SOAP_1_2));
   $server->addFunction("hello");
   $server->handle();
?>
```

程序中没有特别之处。服务器对象现在是通过 WSDL 文档的位置创建的。

以下是 WSDL 文档 `Hello.wsdl`：

```xml
<?xml version="1.0"?>
<definitions name="MyDefinition"
 targetNamespace="urn:myTargetNamespace"
 xmlns:tns="urn:myTns"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
 xmlns="http://schemas.xmlsoap.org/wsdl/">
 <message name="myRequest">
  <part name="reqParam" type="xsd:string"/>
 </message>
 <message name="myResponse">
  <part name="resParam" type="xsd:string"/>
 </message>
 <portType name="MyPortType">
  <operation name="hello">
   <input message="tns:myRequest"/>
   <output message="tns:myResponse"/>
  </operation>
 </portType>
 <binding name="MyBinding" type="tns:MyPortType">
  <soap:binding style="rpc"
   transport="http://schemas.xmlsoap.org/soap/http"/>
  <operation name="hello">
   <soap:operation soapAction=""/>
   <input>
    <soap:body use="encoded"
     namespace="urn:myInputNamespace"
     encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"/>
   </input>
   <output>
    <soap:body use="encoded"
     namespace="urn:myOutputNamespace"
     encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"/>
   </output>
  </operation>
 </binding>
 <service name="MyService">
  <documentation>Returns a greeting string.
  </documentation>
  <port name="MyPort" binding="tns:MyBinding">
   <soap:address
  location="http://localhost/HelloServerWsdl.php"/>
  </port>
 </service>
</definitions>
```

WSDL 文档看起来很复杂。但只要记住以下几点，实际上很容易理解：

*   **倒着读文档**。该文档的目标是定义一个“service”，包含两部分信息：“binding”定义和访问服务器的“url”。“binding”再通过“type”、“style”、“transportation”和“operation”来定义。以此类推。

*   大多数元素中 `name` 属性的值只是该文档内部的标识符。你可以使用任意字符串。其中一些将用于 SOAP 消息中。

*   `namespace` 属性的值也可以是任意字符串。它们只是用来区分命名空间。

要将 `HelloServerWsdl.php` 安装到 Apache 服务器，请将这两个文件复制到 Apache 文档目录：

```bash
herong> copy HelloServerWsdl.php \apache\htdocs
herong> copy Hello.wsdl \apache\htdocs
```

当然，我们需要修改 hello 客户端程序，即 `HelloClientWsdl.php`：

```php
<?php
#### HelloClientWsdl.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
   $client = new SoapClient("http://localhost/Hello.wsdl",
      array('soap_version' => SOAP_1_2,'trace' => 1 ));

   echo("\nDumping client object functions:\n");
   var_dump($client->__getFunctions());

   $return = $client->__soapCall("hello",array("world"));
   echo("\nReturning value of __soapCall() call: ".$return);

#   $return = $client->hello("world");
#   echo("\nReturning value: ".$return);

   echo("\nDumping request headers:\n"
      .$client->__getLastRequestHeaders());

   echo("\nDumping request:\n".$client->__getLastRequest());

   echo("\nDumping response headers:\n"
      .$client->__getLastResponseHeaders());

   echo("\nDumping response:\n".$client->__getLastResponse());
?>
```

准备好测试时，运行 `HelloClientWsdl.php`。你将得到：

```
Dumping client object functions:
array(1) {
  [0]=>
  string(30) "string hello(string $reqParam)"
}

Returning value of __soapCall() call: Hello world! - With WSDL

Dumping request headers:
POST /HelloServerWsdl.php HTTP/1.1
Host: localhost
Connection: Keep-Alive
Content-Type: application/soap+xml; charset=utf-8; action=""
Content-Length: 457

Dumping request:
<?xml version="1.0" encoding="UTF-8"?>
<env:Envelope
 xmlns:env="http://www.w3.org/2003/05/soap-envelope"
 xmlns:ns1="urn:myInputNamespace"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns:enc="http://www.w3.org/2003/05/soap-encoding">
 <env:Body>
  <ns1:hello
   env:encodingStyle="http://www.w3.org/2003/05/soap-encoding">
   <reqParam xsi:type="xsd:string">world</reqParam>
  </ns1:hello>
 </env:Body>
</env:Envelope>

Dumping response headers:
HTTP/1.1 200 OK
Server: Microsoft-IIS/5.1
Connection: close
Content-Type: application/soap+xml; charset=utf-8
Content-Length: 573

Dumping response:
<?xml version="1.0" encoding="UTF-8"?>
<env:Envelope
 xmlns:env="http://www.w3.org/2003/05/soap-envelope"
 xmlns:ns1="urn:myOutputNamespace"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns:enc="http://www.w3.org/2003/05/soap-encoding">
 <env:Body xmlns:rpc="http://www.w3.org/2003/05/soap-rpc">
  <ns1:helloResponse
   env:encodingStyle="http://www.w3.org/2003/05/soap-encoding">
   <rpc:result>resParam</rpc:result>
   <resParam xsi:type="xsd:string">Hello world! - With WSDL</resParam>
  </ns1:helloResponse>
 </env:Body>
</env:Envelope>
```

这里有什么有趣的地方吗？有的。WSDL 文档中定义的一些名称确实出现在了 SOAP 请求消息和响应消息中，例如：`urn:myInputNamespace`、`reqParam`、`urn:myOutputNamespace` 等。

### PHP 教程 - Herong 的教程示例

#### Web 应用本地化概述

本章提供关于 Web 应用本地化的教程示例和说明。主题包括什么是本地化；Web 应用中的软件组件；输出和输入字符串的传播路径；从 PHP 脚本输出 ASCII 字符。

> 什么是本地化 / 国际化
>
> 基于 Web 的应用程序本地化
>
> 字符串传播路径
>
> 从 PHP 脚本输出 ASCII 字符串

要点：

*   本地化主要是一个根据最终用户需求，用特定语言管理输入和输出字符串的过程。
*   在 Web 应用中，字符必须经过涉及多个程序和系统的不同路径传播。
*   ASCII 字符在不同程序和系统间传播没有问题。
*   非 ASCII 字符必须编码为安全格式，才能在不同程序和系统间传播。
*   接下来的 5 章将提供教程说明，分别处理不同领域的非 ASCII 字符：HTML 文档、PHP 字符串字面量、HTML 输入表单、PHP 字符串函数和 MySQL 数据库。

### PHP 教程 - Herong 的教程示例

#### Web 应用本地化概述

#### 什么是本地化 / 国际化

本节介绍什么是本地化和国际化。Locale 是一个定义用户界面上地理和文化特定偏好的概念。

本地化（软件本地化），有时简写为 "l10n"，是一个根据用户特定的地理和文化偏好，为其定制软件用户界面的过程。

国际化（软件国际化），有时简写为 "i18n"，是一个使软件支持本地化的过程。

用户特定的地理和文化偏好可以抽象为 locale 概念。一个 locale 通常决定用户界面的以下方面：

*   使用特定语言进行系统输出和用户输入。
*   使用特定的时区和日期/时间格式。
*   使用特定的货币和编号系统。

### 基于 Web 的应用程序本地化

#### 概述

我们知道本地化的主要任务是用本地语言与用户进行交流。这意味着软件必须以本地语言的字符呈现信息，并以本地语言的字符接收信息。

在本书的这一部分，我们将重点介绍如何以本地语言的字符呈现和管理信息。

#### 字符串传输路径

本节描述了在典型的基于 Web 的应用程序中，字符串必须经过的连接路径步骤：输出字符串来自 PHP 文件或数据库表，输入字符串来自用户的 Web 浏览器。

在典型的基于 Web 的应用程序中，字符串将从应用程序的一个部分传输到另一个部分。以下是字符串可能经过的一些路径。

##### 从 PHP 文件到 Web 浏览器

下图说明了字符串从 PHP 文件传输到浏览器屏幕必须经过的步骤。它还显示了在不同步骤中使用的计算技术：

```
A1. 来自键盘的按键序列
      |
      |- 文本编辑器
      v
A2. PHP 文件
      |
      |- PHP CGI 引擎
      v
A3. HTML 文档
      |
      |- Web 服务器
      v
A4. HTTP 响应
      |
      |- Internet TCP/IP 连接
      v
A5. HTTP 响应
      |
      |- Web 浏览器
      v
A6. 屏幕上的可视字符
```

##### 从数据库到 Web 浏览器

下图说明了字符串从数据库表传输到浏览器屏幕必须经过的步骤。它还显示了在不同步骤中使用的计算技术：

```
B1. 存储中的字节序列
      |
      |- 数据库服务器
      v
B2. 字节流
      |
      |- 数据库连接驱动程序
      v
B3. 字节流
      |
      |- PHP 应用程序
      v
B4. HTTP 响应
      |
      |- Internet TCP/IP 连接
      v
B5. HTTP 响应
      |
      |- Web 浏览器
      v
B6. 屏幕上的可视字符
```

##### 从 Web 浏览器到数据库

下图说明了字符串从 Web 浏览器传输到数据库表必须经过的步骤。它还显示了在不同步骤中使用的计算技术：

```
C1. 键盘上的按键序列
      |
      |- 语言输入工具（可选）
      v
C2. 字节序列
      |
      |- 浏览器输入表单
      v
C3: HTTP 请求
      |
      |- Internet TCP/IP 连接
      v
C4. HTTP 请求
      |
      |- Web 服务器
      v
C5. CGI 变量和输入流
      |
      |- PHP 应用程序
      v
C6. PHP 变量
      |
      |- 数据库连接驱动程序
      v
C7. 字节流
      |
      |- 数据库服务器
      v
C8. 存储中的字节序列
```

由于所有计算技术默认都使用 ASCII 编码，因此 ASCII 字符的文本可以安全地通过这些步骤，而不会出现任何问题。

然而，对于非 ASCII 字符，我们必须仔细检查每个步骤，以确保字符不会损坏，并能正确地进行编码和解码。

现在我将尝试在本章和接下来的 5 章中提供一些教程，向您展示如何在不同连接路径的不同步骤中正确处理字符。

#### 从 PHP 脚本输出 ASCII 字符串

本节提供了一个教程示例，说明如何在 PHP 脚本文件中包含输出 ASCII 字符串。ASCII 字符可以直接作为字符串字面量输入 PHP 代码段，或作为非 PHP 代码段中的文本输入。无需特殊技巧。

正如我之前提到的，ASCII 字符可以轻松地从 PHP 文件传输到浏览器，不会有任何麻烦。下面是一个仅包含 ASCII 字符的简单 PHP 文件：

```php
<?php
#### HelpASCII.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print("<html><body>\n");
   print("<b>Help</b><br/>\n");
   print("This is a very simple help page...<br/>\n");
?>
This is a very simple help page...<br/>
</body></html>
```

如果您使用浏览器查看此页面，将获得以下输出：

```
Help
This is a very simple help page...
This is a very simple help page...
```

完美，对吧？作为 PHP 字符串字面量输入的 ASCII 文本可以正确传输。作为 PHP 块外部的 HTML 静态文本输入的文本也能正确传输。

#### 在 HTML 文档中使用非 ASCII 字符
