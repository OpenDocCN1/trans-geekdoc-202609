

# MySqlLoop.php

```php
<?php
#  MySqlLoop.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   $con = mysql_connect('localhost');
   $rs = mysql_query('DROP DATABASE MyBase');
   $rs = mysql_query('CREATE DATABASE MyBase');
   $rs = mysql_query('USE MyBase');
   print "Creating a table...\n";
   $rs = mysql_query('CREATE TABLE MyTable (ID INTEGER,'
      .' Value INTEGER)');
   $n = 100;
   $i = 0;
   print "Inserting some rows to the table...\n";
   while ($i < $n) {
      $rs = mysql_query('INSERT INTO MyTable VALUES ('.$i.', '
         .rand(0,$n-1).')');
      $i++;
   }
   print "Query some rows from the table...\n";
   $rs = mysql_query('SELECT * FROM MyTable WHERE ID < 10');
   print "   ".mysql_field_name($rs,0)."   "
      .mysql_field_name($rs,1)."\n";
   while ($row = mysql_fetch_array($rs)) {
      print "    ".$row[0].'   '.$row[1]."\n";
   }
   mysql_free_result($rs);
   mysql_close($con);

function mysqli_field_name($result, $field_offset) {
   $properties = mysqli_fetch_field_direct($result, $field_offset);
   return is_object($properties) ? $properties->name : null;
}
?>
```

请注意，如果在查询调用中未指定连接资源，则将使用最后一个连接资源。如果运行此脚本，您将获得类似如下的输出：

```
Creating a table...
Inserting some rows to the table...
Query some rows from the table...
   ID   Value
    0   14
    1   91
    2   84
    3   16
    4   88
    5   51
    6   12
    7   19
    8   39
    9   5
```

# Get_Temperature.php - SOAP 的第一个示例

本节提供了一个教程示例，介绍如何使用 SOAP 扩展调用 xmethods.org 提供的 Web 服务以获取当前温度。

为了向您展示 PHP SOAP 扩展如何在 SOAP 客户端应用程序中使用，这是我的第一个 SOAP PHP 脚本 `Get_Temperature.php`：

```php
<?php
#  Get_Temperature.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   $client = new SoapClient
      ("http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl");
   echo("\nReturning value of getTemp() call: ".
      $client->getTemp("12345"));
?>
```

在您的计算机连接互联网的情况下运行它。您将得到：

```
>php Get_Temperature.php

Returning value of getTemp() call: 52
```

非常好。这证实了：

*   PHP SOAP 扩展易于使用。两条语句足以调用 SOAP 服务。
*   您的 PHP SOAP 扩展已正确安装并正常工作。
*   PHP SOAP 扩展支持 WSDL。
*   www.xmethods.net 为提供此演示 SOAP 服务做出了巨大贡献。

# Get_Temperature_Dump.php - 转储调试信息

本节提供了一个教程示例，介绍如何使用 SOAP 客户端函数对目标 SOAP 节点进行 Web 服务调用并打印详细的调试信息。

在学习了 `SoapClient` 类的基本功能后，我修改了 `Get_Temperature.php` 客户端程序，以获取有关 SOAP 扩展工作原理的更多信息，并向您展示如何调试 SOAP 客户端程序。新的客户端程序称为 `Get_Temperature_Dump.php`：

```php
<?php
#  Get_Temperature_Dump.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   $zip = "123456";
   $client = new SoapClient
      ("http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl",
      array('trace' => 1));

   echo("\nDumping client object:\n");
   var_dump($client);

   echo("\nDumping client object functions:\n");
   var_dump($client->__getFunctions());

   $return = $client->getTemp($zip);
   echo("\nReturning value of getTemp() call: ".$return);

   $return = $client->__soapCall("getTemp",array($zip));
   echo("\nReturning value of __soapCall() call: ".$return);

   echo("\nDumping request headers:\n"
      .$client->__getLastRequestHeaders());

   echo("\nDumping request:\n".$client->__getLastRequest());

   echo("\nDumping response headers:\n"
      .$client->__getLastResponseHeaders());

   echo("\nDumping response:\n".$client->__getLastResponse());
?>
```

如果您运行此示例脚本，将得到：

```
Dumping client object:
object(SoapClient)#1 (3) {
  ["trace"]=>
  int(1)
  ["_soap_version"]=>
  int(1)
  ["sdl"]=>
  resource(5) of type (Unknown)
}

Dumping client object functions:
array(1) {
  [0]=>
  string(30) "float getTemp(string $zipcode)"
}

Returning value of getTemp() call: 52

Returning value of __soapCall() call: 52

Dumping request headers:
POST /soap/servlet/rpcrouter HTTP/1.1
Host: services.xmethods.net
Connection: Keep-Alive
User-Agent: PHP SOAP 0.1
Content-Type: text/xml; charset=utf-8
SOAPAction: ""
Content-Length: 510
Cookie: JSESSIONID=uuqkGDvtzw_IPlMLsodnVX9j;

Dumping request:
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="urn:xmethods-Temperature-Demo"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"
 SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
 <SOAP-ENV:Body><ns1:getTemp>
  <zipcode xsi:type="xsd:string">123456</zipcode>
 </ns1:getTemp></SOAP-ENV:Body>
</SOAP-ENV:Envelope>

Dumping response headers:
HTTP/1.1 200 OK
Server: Enhydra-MultiServer/3.1.1b1
Status: 200
Content-Type: text/xml; charset=utf-8
Servlet-Engine: Enhydra Application Server/3.1.1b1 (JSP 1.1;
   Servlet 2.2; Java 1.4.2_03; Linux 2.4.7-10smp i386;
   java.vendor=Sun Microsystems Inc.)
Content-Length: 470
X-Cache: MISS from www.xmethods.net
Keep-Alive: timeout=15, max=99
Connection: Keep-Alive

Dumping response:
<?xml version='1.0' encoding='UTF-8'?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<SOAP-ENV:Body>
<ns1:getTempResponse xmlns:ns1="urn:xmethods-Temperature-Demo"
SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<return xsi:type="xsd:float">52.0</return>
</ns1:getTempResponse>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

该输出非常有用。它证实了：

*   默认 SOAP 版本为 SOAP 1.1。对于 SOAP 1.2，信封命名空间应为 `http://www.w3.org/2003/05/soap-envelope`，而不是 `http://schemas.xmlsoap.org/soap/envelope/`。
*   传输协议为 HTTP/1.1。请参阅请求标头行。
*   此 WSDL 中仅支持一个 RPC 函数：`float getTemp(string $zipcode)`。请参阅 `__getFunctions()` 转储。
*   SOAP 扩展根据 WSDL 文档中的定义，将我的 `getTemp()` RPC 调用很好地转换为 SOAP 请求消息。
*   返回值也被正确转换为“float”类型的值，而不是“string”。SOAP 响应消息显示“52.0”，但 `$return` 的打印输出为“52”。

# MySqlUnicode.php 使用 php_mysql.dll 库

本节提供了一个教程示例，介绍如何以 Unicode UTF-8 编码向 MySQL 数据库服务器发送和接收非 ASCII 字符串。

这是我的示例脚本，向您展示如何将 UTF-8 字符串发送到 MySQL 服务器并以 UTF-8 编码存储，`MySqlUnicode.php`：

