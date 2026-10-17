
似乎有 3 种流行的 PHP SOAP 实现：`PEAR SOAP`、`NuSOAP` 和 `PHP Group SOAP Extension`。

`PHP Group SOAP Extension` 5.0.4 似乎支持 SOAP 1.2。但它默认使用 SOAP 1.1。

## WSDL 和 SOAP 概述

*   WSDL 是一种基于 XML 的标准，旨在描述 Web 服务的协议绑定和消息格式。
*   WSDL 文档确实有助于简化 SOAP 调用的设置过程。但即使没有 WSDL 文档，进行 SOAP 调用也并不难。
*   `www.xmethods.net` 为提供此演示 SOAP 服务做出了巨大贡献。

---

## PHP 的 SOAP 实现

本节介绍 SOAP 协议及 PHP 的 SOAP 实现。`PEAR::Package::SOAP`、`NuSOAP` 和 `php_soap.dll`（来自 PHP Group）似乎是 3 种不同的 SOAP 实现。

### 什么是 SOAP？

**SOAP**（简单对象访问协议）是一种基于 XML 的协议，旨在在分布式应用环境中交换结构化信息。

如果你在网上用 "PHP Implementation of SOAP" 作为关键词搜索，可能会发现以下实现：

*   `php.net/manual/en/book.soap.php` 上的 PHP SOAP 扩展。
*   NuSOAP - PHP 的 SOAP 工具包，位于 `http://sourceforge.net/projects/nusoap/`。当前版本：2011-01-13 发布的 0.9.5 版。
*   `http://pear.php.net/package/SOAP` 上的 `PEAR::Package::SOAP`。它已不再可用。

PHP SOAP 扩展包含在 PHP 发行包中：

```
herong> dir \php\ext\php_soap.dll

12/05/2018  09:38 PM           247,808 php_soap.dll
```

---

## 开启默认 SOAP 扩展

本节提供一个教程示例，说明如何开启默认发行包中包含的 SOAP 扩展 - 在 `php.ini` 文件中设置 `extension=php_soap.dll`。

PHP 发行包自带一个默认的 SOAP 扩展库。但它不会自动开启。我用 `phpinfo()` 函数做了以下测试，看看 SOAP 是否已开启：

```
herong> type PhpInfo.php
   <?php phpinfo();?>

herong> php PhpInfo.php > PhpInfo.txt

herong> find /i "soap" PhpInfo.txt
---------- PHPINFO.TXT

herong> php -v
PHP 7.3.0 (cli) (built: Dec  6 2018 01:54:19) ( ZTS MSVC15 ...
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.3.0-dev, Copyright (c) 1998-2018 Zend Technologies
```

所以在我的默认安装中 SOAP 功能不可用，该安装是 PHP Group 提供的 PHP 7.3.0。

接下来我通过编辑 `\php\php.ini` 并更新以下行来开启 SOAP 扩展：

```
; Directory in which the loadable extensions (modules) reside.
extension_dir = "ext"
...

#### PHP 7
extension=soap

#### PHP 5
extension=php_soap.dll
```

我又检查了一遍：

```
herong> php PhpInfo.php > PhpInfo.txt

herong> find /i "soap" PhpInfo.txt

---------- PHPINFO.TXT
soap
Soap Client => enabled
Soap Server => enabled
soap.wsdl_cache => 1 => 1
soap.wsdl_cache_dir => /tmp => /tmp
soap.wsdl_cache_enabled => 1 => 1
soap.wsdl_cache_limit => 5 => 5
soap.wsdl_cache_ttl => 86400 => 86400
```

很酷。现在出现了一些与 SOAP 相关的设置。

为了查看是谁开发的这个实现，我右键点击文件 `\php\ext\php_soap.dll`，选择属性。弹出的窗口告诉我：

```
Internal Name: php_soap.dll
File Version: 7.3.0
Copyright (c) 1997-2018 The PHP Group
```

然后我浏览了位于 `\php\html\intro.soap.html` 的已安装文档，获得了以下信息：

*   **SOAP 函数**
*   **简介**
*   **SOAP 扩展可用于编写 SOAP 服务器和客户端。它支持 SOAP 1.1、SOAP 1.2 和 WSDL 1.1 规范的子集。**

---

## Hello_There.php - SOAP 第一个示例

本节提供一个教程示例，说明如何使用 SOAP 扩展调用 `herongyang.com` 提供的 Web 服务以获取问候消息。

为了向你展示 PHP SOAP 扩展如何在 SOAP 客户端应用程序中使用，这是我的第一个 SOAP PHP 脚本 `Hello_There.php`：

```php
<?php
#### Hello_There.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
   $client = new SoapClient
      ("http://herongyang.com/Service/Hello_WSDL_11_SOAP.wsdl");
   echo("\nReturning value of Hello() call: ".$client->Hello());
?>
```

在你的电脑连接互联网时运行它。你将得到：

```
herong> php Hello_There.php

Returning value of Hello() call:
      Hello from server - herongyang.com.
```

非常好。这证实了：

*   PHP SOAP 扩展易于使用。两条语句足以调用 SOAP 服务。
*   你的 PHP SOAP 扩展安装正确且工作正常。
*   PHP SOAP 扩展支持 WSDL。

---

## SoapClient - SOAP 客户端类和函数

本节介绍 SOAP 扩展库中提供的 `SoapClient` 类和函数，用于编写 SOAP 客户端应用程序。`__soapCall()` 允许你在目标 SOAP 节点上进行 RPC 函数调用。

如果你阅读 SOAP 扩展参考页，你会看到 SOAP 扩展通过一个名为 `SoapClient` 的类支持 SOAP 客户端应用程序，该类提供以下函数：

*   `SoapClient->__construct()` - 构造一个新的 `SoapClient` 对象
*   `SoapClient->__soapCall()` - 调用一个 SOAP 函数
*   `SoapClient->__getFunctions()` - 返回 SOAP 函数列表
*   `SoapClient->__getLastRequestHeaders()` - 返回最后的 SOAP 请求头
*   `SoapClient->__getLastRequest()` - 返回最后的 SOAP 请求
*   `SoapClient->__getLastResponseHeaders()` - 返回最后的 SOAP 响应头
*   `SoapClient->__getLastResponse()` - 返回最后的 SOAP 响应
*   ...

`SoapClient->__construct()` 允许你用以下语法构造一个新的 `SoapClient` 对象：

```
__construct ( mixed wsdl [, array options] );
```

其中 "wsdl" 指定 WSDL 文档的 URL，"options" 指定选项列表：

```
'location'     => "...", # 发送请求的 URL
'uri'          => "...", # SOAP 服务的命名空间
'soap_version' => SOAP_1_1 | SOAP_1_2,
'trace'        => 0 | 1,
...
```

请注意 `SoapClient` 对象可以用两种模式构造：WSDL 模式和非 WSDL 模式：

```
__construct( "..."[, array options] ); # WSDL 模式，许多选项
   # 由 WSDL 文档提供
__construct( null, array options ); # 非 WSDL 模式，'location'
   # 和 'uri' 是必需选项。
```

`SoapClient->__getFunctions()` 允许你获取目标节点支持的函数列表。此函数仅在 WSDL 模式下有效：

```
array $a = $obj->__getFunctions();
```

`SoapClient->__soapCall()` 允许你在目标 SOAP 节点上进行 RPC 函数调用。

```
$obj->__soapCall(string func_name[, array arguments [, ...]]);
```

请注意在 WSDL 模式下，你也可以将 RPC 调用作为 `SoapClient` 对象上的本地方法进行：

```
$obj->func_name(arg1, arg2, ...);
```

`SoapClient->__getLastRequestHeaders()` 允许你检索最后执行的 SOAP 请求的 HTTP 请求头行。此函数仅在 `SoapClient` 对象以 "trace=1" 选项创建时有效。

```
string $s = $obj->__getLastRequestHeaders();
```

`SoapClient->__getLastRequest()` 允许你检索最后执行的 SOAP 请求的 SOAP 请求消息。此函数仅在 `SoapClient` 对象以 "trace=1" 选项创建时有效。

```
string $s = $obj->__getLastRequest();
```

`SoapClient->__getLastResponseHeaders()` 允许你检索最后执行的 SOAP 请求的 HTTP 响应头行。此函数仅在 `SoapClient` 对象以 "trace=1" 选项创建时有效。

```
string $s = $obj->__getLastResponseHeaders();
```

### SoapClient->__getLastResponse()

`SoapClient->__getLastResponse()` 允许你检索最后执行的 SOAP 请求的 SOAP 响应消息。仅当 `SoapClient` 对象是使用 `trace=1` 选项创建时，此函数才有效。

```php
string $s = $obj->__getLastResponse();
```

---

## Hello_There_Dump.php - 调试 SOAP 消息

本节提供了一个教程示例，说明如何使用 SOAP 客户端函数对目标 SOAP 节点进行 Web 服务调用并打印详细的调试信息。

在学习了 `SoapClient` 类的基本函数后，我修改了我的 `Hello_There.php` 客户端程序，以获取更多关于 SOAP 扩展如何工作的信息，并向你展示如何调试 SOAP 客户端程序。新的客户端程序名为 `Hello_There_Dump.php`：

```php
<?php
#### Hello_There_Dump.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
   $client = new SoapClient
      ("http://herongyang.com/Service/Hello_WSDL_11_SOAP.wsdl",
      array('trace' => 1));

   echo("\nDumping client object:\n");
   var_dump($client);

   echo("\nDumping client object functions:\n");
   var_dump($client->__getFunctions());

   $return = $client->Hello();
   echo("\nReturning value of Hello() call: ".$return);

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

如果你运行此示例脚本，将得到：

```
Dumping client object:
object(SoapClient)#1 (3) {
  ["trace"]=>
  int(1)
  ["_soap_version"]=>
  int(1)
  ["sdl"]=>
  resource(6) of type (Unknown)
}

Dumping client object functions:
array(1) {
  [0]=>
  string(36) "string Hello(string $helloInputPart)"
}

Returning value of Hello() call:
      Hello from server - herongyang.com.

Returning value of __soapCall() call:
      Hello from server - herongyang.com.

Dumping request headers:
POST /Service/Hello_SOAP_11.php HTTP/1.1
Host: www.herongyang.com
Connection: Keep-Alive
User-Agent: PHP-SOAP/7.3.0
Content-Type: text/xml; charset=utf-8
SOAPAction: "https://www.herongyang.com/Service/Hello"
Content-Length: 235


Dumping request:
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="https://www.herongyang.com/Service/">
 <SOAP-ENV:Body>
  <ns1:HelloRequest/>
 </SOAP-ENV:Body>
</SOAP-ENV:Envelope>

Dumping response headers:
HTTP/1.1 200 OK
Server: Apache
X-Powered-By: PHP/7.2.14
Keep-Alive: timeout=2, max=199
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

该输出非常有用。它确认了：

*   默认 SOAP 版本为 SOAP 1.1。对于 SOAP 1.2，信封命名空间应为 `http://www.w3.org/2003/05/soap-envelope`，而非 `http://schemas.xmlsoap.org/soap/envelope/`。
*   传输协议为 HTTP/1.1。请参阅请求标头行。
