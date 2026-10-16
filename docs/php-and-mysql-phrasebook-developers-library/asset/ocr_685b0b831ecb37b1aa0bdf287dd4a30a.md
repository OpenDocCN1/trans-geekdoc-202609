```
```php
function add($a, $b) {
    return $a + $b;
}
?>
```
```

*A Web Service with PHP 5 SOAP (soap-php5-server.php)*

One of the key features of PHP 5 is the new SOAP extension. Because it is written in C, it is much faster than anything that is coded in PHP alone. However, the extension is relatively new, so there are still some hiccups and missing features. However, it often works well.

You have to configure PHP with --enable-soap to use the extension; Windows users have to add extension=php_soap.dll to their php.ini configuration file. Then, the extension is available, and writing a SOAP server is quite easy.

Again, it's a small number of steps: Instantiate the SoapServer class, add your function with addFunction(), and, finally, call handle().

# Automatically Generating WSDL with the PHP 5 SOAP Extension

The greatest shortcoming of PHP 5 SOAP is that there is no way to automatically generate WSDL with it. This is not often mentioned; however, it does create problems in real life. WSDL is so complicated that errors in the WSDL are hard to see and even harder to find. However, you can create such a WSDL description for a Web Service in several ways, most of which have been used in real-world projects.