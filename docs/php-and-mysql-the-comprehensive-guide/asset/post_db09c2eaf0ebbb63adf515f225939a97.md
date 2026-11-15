
```php
require_once "lib/nusoap.php";
$server = new nusoap_server();

$server->configureWSDL("Square", "http://www.arrabiata.de/nusoap/");

$server->register("square",
    ["a" => "xsd:int"],
    ["square" => "xsd:int"],
    "http://soapinterop.org/"
);

$data = file_get_contents("php://input") != null ?
    file_get_contents("php://input") : "";
$server->service($data);
exit();
?>
```

### Listing 27.7 WSDL with nuSOAP ("nusoap_wsdl_server.php")

You can easily view the WSDL produced by nuSOAP. Simply append ?wsdl to the name of the script. For our example, the local address is http://localhost/php/nusoap_wsdl_service.php?wsdl (see Figure 27.7). The length of the WSDL shows that automatic generation certainly has its advantages.

![](img/ae7820c36e8f24c1623d26668b28e80e_760_0.png)

### Figure 27.6 Description of the Method

> Tip
> If you call the service without ?wsdl, you will receive an information page that refers to WSDL and also provides a description of the method (see Figure 27.6). nuSOAP has adopted this useful behavior and ?wsdl from Microsoft's ASP.NET web services.

![](img/ae7820c36e8f24c1623d26668b28e80e_761_0.png)

### Figure 27.7 The WSDL of the Server

Now let's move on to the client for the WSDL call:

- When calling the client, enter the WSDL as the URL. You must also specify that WSDL is to be used as the second parameter in the options array:

```php
$client = new nusoap_client("http://localhost/php/nusoap_wsdl_server.php?wsdl", true);
```

- Then call the method with call():

```php
$a = 48;
$result = $client->call('square', [ 'a' => $a],
                                 'http://www.arrabiata.de/nusoap/');
```

Alternatively, you can also call the method with a proxy:

```php
$proxy = $client->getProxy();
$result = $proxy->square($a);
```

- Finally, carry out error checking and output:

```php
if ($error = $client->getError()) {
    print "Error: " . $error;
} elseif ($error = $client->fault) {
    print "SOAP error: " . $error;
} else {
    print "The square of $a is " . $result;
}
```

Listing 27.8 shows the complete code. The most important changes compared to the normal client are highlighted in bold. Figure 27.8 shows the output.

```php
<?php
require_once "lib/nusoap.php";
$client = new nusoap_client(
"http://localhost/php/nusoap_wsdl_server.php?wsdl",
true);
$a = 48;
$result = $client->call('square', ['a' => $a],
'http://www.arrabiata.de/nusoap/');
if ($error = $client->getError()) {
    print "Error: " . $error;
} elseif ($error = $client->fault) {
    print "SOAP error: " . $error;
} else {
    print "The square of $a is " . $result;
}
?>
```

### Listing 27.8 The WSDL Client ("nusoap_wsdl_client.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_762_0.png)

### Figure 27.8 Now the Mental Arithmetic Becomes More Difficult ...

> Tip
> To test the error handling, simply do not pass any parameters. You can see the result in Figure 27.9.

![](img/ae7820c36e8f24c1623d26668b28e80e_763_0.png)

### Figure 27.9 The Error Message Indicates that No Parameter Was Passed.

## 27.3.4 Conclusion

nuSOAP impresses above all with its ease of use. With nuSOAP, you only have to copy one file. It is very flexible to use and does not need an installed SOAP library.

## 27.4 PHP-SOAP

PHP-SOAP is the standard web services library in PHP. At the beginning there was some discussion about this: Is a new library really necessary, or is it better to port an existing one to C? The main reason for a C-based PHP extension is performance. The new development was chosen in the end to be able to build from scratch on a greenfield site and not drag along any legacy code. In addition, libxml could be chosen as the basis, which further standardizes XML support in PHP.

### 27.4.1 Server

The server is created quickly:

- The SoapServer object contains everything important. The first parameter is for WSDL. As we are not using WSDL here, but a normal SOAP call, we pass null. The second parameter is an associative array with options:

```php
$server = new SoapServer(null, ["uri" =>
"http://www.arrabiata.de/PHP-SOAP/" ]);
```

- The square() function is used again. Only the throwing of the error changes compared to before:

```php
throw new SoapFault("Client", "No parameter");
```

- Finally, add the function to the server and start the server with handle():

```php
$server->addFunction("square");
$server->handle();
```

Listing 27.9 shows the complete script.

```php
<?php
$server = new SoapServer(null, ["uri" =>
"http://www.arrabiata.de/PHP-SOAP/" ]);

function square($a) {
    if ($a != null && trim($a) != "") {
        $square = $a * $a;
        return $square;
    } else {
        throw new SoapFault("Client", "No parameter");
    }
}

$server->addFunction("square");
$server->handle();
?>
```

### Listing 27.9 The PHP SOAP Server ("php_soap_server.php")

> Tip
> Instead of a function, you can also use a class and set it with setClass(class). You can find this variant in the materials for the book (see the Preface) under the name php_soap_server_class.php.

### 27.4.2 Client

With the client, the simple handling of PHP-SOAP is even more noticeable:

- You create the client with the SoapClient object. The first parameter here is also for WSDL. If none is available, as here, write zero. The second parameter is the associative array with the options. Of course, the `location` option, which specifies the location of the SOAP web service, is particularly important:

```php
$client = new SoapClient(null, ['location' =>
"http://localhost/php/php_soap_server.php",
'uri' => "http://arrabiata.de/PHP-SOAP/" ]);
```

- Error handling in PHP-SOAP is done with try ... catch:

```php
try {
  ... Further processing
} catch (SoapFault $ex) {
  ... Error handling
}
```

- You call the method in the try block. This is done with __soapCall(method, parameter). The parameters are specified as an array:

```php
$a = 111;
$answer = $client->__soapCall("square", [$a]);
print "The square of $a is: " . $answer;
```

- Finally, you need the code for error handling. Here we simply read the error code and associated description from the SoapFault object. Figure 27.10 shows the output:

```php
print "Error code: " . $ex->faultcode . "<br/>";
print "Error string: " . $ex->faultstring;
```

![](img/ae7820c36e8f24c1623d26668b28e80e_765_0.png)

### Figure 27.10 The Error Message if a Parameter Is Missing

The following listing shows the complete code of the client; Figure 27.11 shows the output.

```php
<?php
$client = new SoapClient(null, ['location' =>
   "http://localhost/php/php_soap_server.php",
   'uri' => "http://arrabiata.de/PHP-SOAP/" ]);
try {
  $a = 111;
  $answer = $client->__soapCall("square", [$a]);
  print "The square of $a is: " . $answer;
} catch (SoapFault $ex) {
  print "Error code: " . $ex->faultcode . "<br/>";
  print "Error string: " . $ex->faultstring;
}
?>
```

### Listing 27.10 The PHP SOAP Client ("php_soap_client.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_766_0.png)

### Figure 27.11 Diligence Task Solved by PHP-SOAP

### 27.4.3 WSDL

The use of WSDL is easily possible with PHP-SOAP. You simply insert the address of the respective WSDL into the SoapClient(WSDL, options) object and the SoapServer(WSDL, options) object. The only problem is that you need ready-made WSDL. Unlike nuSOAP and PEAR::SOAP, PHP-SOAP does not support WSDL generation. This means that you have to write the WSDL by hand or generate it in some other way.

> Note
>
> This was a hotly debated topic during the development of PHP-SOAP. The argument against WSDL support was that the generation costs performance and is in principle not the task of the SOAP/web services library.

First look at the server code. The most important new feature is the WSDL document.

```php
<?php
$server = new SoapServer("http://localhost/php/square.wsdl",
["uri" => "http://www.arrabiata.de/PHP-SOAP/"]);

class Methods {
function square($a) {
if ($a != null && trim($a) != "") {
$square = $a * $a;
return $square;
} else {
throw new SoapFault("Client", "No parameter");
}
}
}
$server->setClass("Methods");
$server->handle();
?>
```

### Listing 27.11 The PHP SOAP Server with WSDL ("php_soap_wsdl_server.php")
