Actually, using a NuSOAP service is even easier than creating one. You just have to load the WSDL file and then get a so-called proxy class. (That's a local class that behaves just as if the Web Service is a local class, too.) So, you can call the Web Service's methods directly, and NuSOAP takes care of all the rest (including opening a connection to the remote server, assembling and parsing XML, and so on).

To do this, the soapclient class (without the underscore character) must be instantiated, and then the getProxy() method creates the proxy class. The code implements this for the demo service from the previous example. Note the URL of the WSDL file: It's the Web Service's URL plus ?wsdl appended to the end; change the URL accordingly for your system.

**NOTE:** Appending ?wsdl to the URL to get the WSDL description of a Web Service is an idea borrowed from Microsoft .NET (and now also used in other technologies). However, there the appendix is not case sensitive, whereas NuSOAP requires it to be in lowercase letters. Keep this in mind when working cross-platform.

# Creating a Web Service with the PHP 5 SOAP Extension

```
<?php
$soap = new SoapServer(null, array('uri' =>
'http://php.phrasebook.org/'));
$soap->addFunction('add');
$soap->handle();
```