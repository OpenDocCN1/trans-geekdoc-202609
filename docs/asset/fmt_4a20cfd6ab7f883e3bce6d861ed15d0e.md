
* 此 WSDL 中仅支持一个 RPC 函数：`string Hello(string $helloInputPart)`。请参阅 `__getFunctions()` 转储。
* SOAP 扩展根据 WSDL 文档中的定义，将我的 `Hello()` RPC 调用完美地转换为 SOAP 请求消息。

---

## 什么是 WSDL

本节介绍什么是 WSDL——一种基于 XML 的标准，旨在描述 Web 服务的协议绑定和消息格式。

### 什么是 WSDL？

**WSDL**（Web Services Definition Language，Web 服务描述语言）是一种基于 XML 的标准，旨在描述 Web 服务的协议绑定和消息格式。WSDL 通常发音为 "Whiz-Dull"。

WSDL 文档是用 WSDL 编写的 XML 文档，用于描述 Web 服务。以下是前几节中使用的演示 Web 服务的 WSDL 文档副本。你可以通过在 Web 浏览器中访问 `http://herongyang.com/Service/Hello_WSDL_11_SOAP.wsdl` 自行下载一个：

```xml
<?xml version="1.0"?>
<wsdl:definitions xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/"
  xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
  xmlns:hy="https://www.herongyang.com/Service/"
  targetNamespace="https://www.herongyang.com/Service/">

  <wsdl:documentation>
    Hello_WSDL_11_SOAP.wsdl
    Copyright (c) 2009 HerongYang.com. All Rights Reserved.
    All rights reserved
  </wsdl:documentation>

  <wsdl:types>
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
      targetNamespace="https://www.herongyang.com/Service/">
      <xsd:element name="HelloRequest" type="xsd:string"/>
      <xsd:element name="HelloResponse" type="xsd:string"/>
    </xsd:schema>
  </wsdl:types>

  <wsdl:message name="helloInputMessage">
    <wsdl:part name="helloInputPart" element="hy:HelloRequest"/>
  </wsdl:message>
  <wsdl:message name="helloOutputMessage">
    <wsdl:part name="helloOutputPart" element="hy:HelloResponse"/>
  </wsdl:message>

  <wsdl:portType name="helloPortType">
    <wsdl:operation name="Hello">
      <wsdl:input name="helloInput"
        message="hy:helloInputMessage"/>
      <wsdl:output name="helloOutput"
        message="hy:helloOutputMessage"/>
    </wsdl:operation>
  </wsdl:portType>

  <wsdl:binding name="helloBinding" type="hy:helloPortType">
    <soap:binding transport="http://schemas.xmlsoap.org/soap/http"/>
    <wsdl:operation name="Hello">
      <soap:operation
        soapAction="https://www.herongyang.com/Service/Hello"/>
      <wsdl:input name="helloInput">
        <soap:body use="literal"/>
      </wsdl:input>
      <wsdl:output name="helloOutput">
        <soap:body use="literal"/>
      </wsdl:output>
    </wsdl:operation>
  </wsdl:binding>

  <wsdl:service name="helloService">
    <wsdl:port name="helloPort" binding="hy:helloBinding">
      <soap:address
location="https://www.herongyang.com/Service/Hello_SOAP_11.php"/>
    </wsdl:port>
  </wsdl:service>

</wsdl:definitions>
```

在学习 WSDL 规范之前，我无法很好地阅读此文档。但它似乎精确地描述了应如何使用此 Web 服务。请参阅我的另一本书：["SOAP Web Service Tutorials - Herong's Tutorial Examples"](http://herongyang.com/Web-Services/) 以获取更多关于 SOAP 和 WSDL 的信息。

---

## 在非 WSDL 模式下使用 SOAP 扩展

本节提供了一个教程示例，说明如何在不使用 WSDL 标准的情况下，使用 SOAP 客户端函数对目标 SOAP 节点进行 Web 服务调用并打印详细的调试信息。

我想我们已经在 WSDL 模式下玩得够多了。现在让我们尝试一下非 WSDL 模式。这是我的 `Get_Temperature.php` SOAP 客户端程序的第三个版本，`Hello_There_Non_WSDL.php`：

### PHP SOAP 非 WSDL 模式客户端示例

#### 代码示例：Hello_There_Non_WSDL.php

```php
<?php
#### Hello_There_Non_WSDL.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
   $client = new SoapClient(null, array(
      'location' =>
         "https://www.herongyang.com/Service/Hello_SOAP_11.php",
      'uri'      => "https://www.herongyang.com/Service/",
      'trace'    => 1 ));

   echo("\nDumping client object:\n");
   var_dump($client);

   $return = $client->__soapCall("Hello",array());
   echo("\nReturning value of __soapCall() call: ".$return);

   echo("\nDumping request headers:\n"
      .$client->__getLastRequestHeaders());

   echo("\nDumping request:\n".$client->__getLastRequest());

   echo("\nDumping response headers:\n"
      .$client->__getLastResponseHeaders());

   echo("\nDumping response:\n".$client->__getLastResponse());
?>
```

#### 运行输出

运行此示例脚本将得到以下输出：

```
Dumping client object:
object(SoapClient)#1 (4) {
  ["uri"]=>
  string(34) "https://www.herongyang.com/Service/"
  ["location"]=>
  string(51) "https://www.herongyang.com/Service/Hello_SOAP_11.php"
  ["trace"]=>
  int(1)
  ["_soap_version"]=>
  int(1)
}

Returning value of __soapCall() call:
Dumping request headers:
POST /Service/Hello_SOAP_11.php HTTP/1.1
Host: www.herongyang.com
Connection: Keep-Alive
Content-Type: text/xml; charset=utf-8
SOAPAction: "https://www.herongyang.com/Service/#Hello"
Content-Length: 399


Dumping request:
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="https://www.herongyang.com/Service/"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"
 SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
 <SOAP-ENV:Body>
  <ns1:Hello/>
 </SOAP-ENV:Body>
</SOAP-ENV:Envelope>

Dumping response headers:
HTTP/1.1 200 OK
Server: Apache
Keep-Alive: timeout=2, max=200
Connection: Keep-Alive
Transfer-Encoding: chunked
Content-Type: text/xml

Dumping response:
<soapenv:Envelope
  xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
  xmlns:hy="https://www.herongyang.com/Service/">
  <soapenv:Header/>
  <soapenv:Body>
    <hy:HelloResponse>
      Hello from server - herongyang.com.
    </hy:HelloResponse>
  </soapenv:Body>
</soapenv:Envelope>
```

#### 输出分析

输出显示：

* `Hello_There_Non_WSDL.php` 的工作方式与 WSDL 模式版本相同。
* 如果将此输出与 WSDL 输出进行比较，SOAP 扩展生成的请求头有一个区别：`SOAPAction` 不再为空。它的值为 `"https://www.herongyang.com/Service/#Hello"`。

---

## SOAP 服务器函数和示例

本章提供关于 SOAP 服务器函数和示例的教程示例和说明。主题包括 SOAP 服务器类和函数简介、SOAP 服务器示例 `HelloServer.php`、SOAP 1.1 和 1.2 的服务器示例、WSDL 模式下的服务器示例。

### 相关章节

* `SoapServer` - SOAP 服务器类和函数
* `HelloServer.php` - 第一个 SOAP 服务器应用程序
* `HelloServer12.php` - 第一个 SOAP 1.2 服务器应用程序
* `HelloServerWsdl.php` - WSDL 模式下的 SOAP 1.2 服务器应用程序

### 核心要点

* SOAP 扩展易于使用，可快速设置 SOAP 服务器以提供 Web 服务。
* SOAP 扩展支持 SOAP 1.1 和 1.2 规范。
* WSDL 文档实际上很容易理解。

### 练习

编写一个温度转换 SOAP 服务。

---

## SoapServer - SOAP 服务器类和函数

本节介绍 SOAP 扩展库中提供的 `SoapServer` 类和函数，用于编写 SOAP 服务器应用程序。

如果阅读 SOAP 扩展参考页面，你将看到 SOAP 扩展通过一个名为 `SoapServer` 的类支持 SOAP 服务器应用程序，该类提供以下函数：

* `SoapServer->__construct()` - 构造一个新的 `SoapServer` 对象
* `SoapServer->addFunction()` - 添加一个或多个处理 SOAP 请求的函数
* `SoapServer->setClass()` - 设置处理 SOAP 请求的类
* `SoapServer->handle()` - 处理 SOAP 请求
* `SoapServer->getFunctions()` - 返回已定义函数的列表
* ...

### `SoapServer->__construct()`

`SoapServer->__construct()` 允许你使用以下语法构造一个新的 `SoapServer` 对象：

```php
__construct ( mixed $wsdl [, array $options] );
```

其中 `wsdl` 指定 WSDL 文档的 URL，`options` 指定选项列表：

```php
'uri'          => "...", # SOAP 服务的命名空间
'soap_version' => SOAP_1_1 | SOAP_1_2,
'actor'        => "...", # 角色
'encoding'     => "...", # 编码名称
'classmap'     => "...", # WSDL 类型到 PHP 类的映射
...
```

请注意，`SoapServer` 对象可以通过两种模式构造：WSDL 模式和非 WSDL 模式：

```php
__construct( "..."[, array $options] ); # WSDL 模式，许多选项由 WSDL 文档提供
__construct( null, array $options );    # 非 WSDL 模式，'uri' 是必需选项
```

### `SoapServer->addFunction()`

`SoapServer->addFunction()` 允许你添加一个或多个函数来处理 SOAP 请求。要添加的函数是在当前 PHP 程序文件中定义的函数。

```php
$obj->addFunction("func");              # 添加一个函数
$obj->addFunction(array("func1",...));  # 添加多个函数
$obj->addFunction(SOAP_FUNCTIONS_ALL);  # 添加所有函数
```

### `SoapServer->setClass()`

`SoapServer->setClass()` 允许你调用指定类中的方法来处理 SOAP 请求。

```php
$obj->setClass("cls");
```

### `SoapServer->handle()`

`SoapServer->handle()` 允许你将执行控制权返回给 SOAP 扩展以处理传入的 SOAP 请求。

```php
$obj->handle();
```

### `SoapServer->getFunctions()`

`SoapServer->getFunctions()` 允许你获取已分配处理 SOAP 请求的所有函数的列表。

```php
array $a = $obj->getFunctions();
```

---

## HelloServer.php - 第一个 SOAP 服务器应用程序

本节提供关于如何编写简单 SOAP 服务器应用程序的教程示例。`HelloServer.php` 示例定义了一个 `hello()` 函数，将其添加到 SOAP 服务器，并等待客户端程序调用。

好了，现在让我们构建第一个 SOAP 服务器。我希望第一个服务器执行一个非常简单的功能：根据输入的名称返回问候字符串。以下是我的版本，名为 `HelloServer.php`：
