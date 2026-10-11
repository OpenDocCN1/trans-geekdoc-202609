
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

Note that if the connection resource is not specified in a query call, the last connection resource will be used. If you run this script, you will get something like:

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

# Get_Temperature.php - First Example of SOAP

This section provides a tutorial example on how to use the SOAP extension to call a Web service provided by xmethods.org to get the current temperature.

To show you an example of how PHP SOAP extension can be used in a SOAP client application, here is my first SOAP PHP script, `Get_Temperature.php`:

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

Run it while your computer is connected to the Internet. You will get:

```
>php Get_Temperature.php

Returning value of getTemp() call: 52
```

Very nice. This confirms that:

*   PHP SOAP extension is easy to use. Two statements are enough to call a SOAP service.
*   Your PHP SOAP extension is installed correctly and working.
*   PHP SOAP extension supports WSDL.
*   www.xmethods.net is doing a great job for offering this demonstration SOAP service.

# Get_Temperature_Dump.php - Dumping Debugging Information

This section provides a tutorial example on how to use SOAP client functions to make Web service call on the target SOAP node and print detailed debug information.

After learning the basic functions of the `SoapClient` class, I revised my `Get_Temperature.php` client program to get more information on how SOAP Extension works, and to show you how to debug a SOAP client program. The new client program is called, `Get_Temperature_Dump.php`:

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

If you run this sample script, you will get:

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

The output is very useful. It confirms that:

*   The default SOAP version is SOAP 1.1. For SOAP 1.2, the envelope namespace should be `http://www.w3.org/2003/05/soap-envelope`, not `http://schemas.xmlsoap.org/soap/envelope/`.
*   The transportation protocol is HTTP/1.1. See the request header lines.
*   There is only one RPC function supported in this WSDL: `float getTemp(string $zipcode)`. See the `__getFunctions()` dump.
*   SOAP Extension converts my `getTemp()` RPC call nicely in a SOAP request message based on the definitions in the WSDL document.
*   The returning value is also converted properly into a "float" type of value, not a "string". The SOAP response message shows "52.0", but the print out of `$return` is "52".

# MySqlUnicode.php using php_mysql.dll Library

This section provides a tutorial example on how to send and receive non-ASCII character strings in Unicode UTF-8 encoding to and from a MySQL database server.

My is my sample script to show you how to send UTF-8 strings to a MySQL server and store them in UTF-8 encoding, `MySqlUnicode.php`:
