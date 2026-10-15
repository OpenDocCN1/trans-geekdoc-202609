# Automatically Generating WSDL with NuSOAP

or not. This is because when it is not set, the user has made a GET request, so there might be a chance that he just wants the WSDL description.

```
```php
<?php
    require_once 'nusoap.php';

    $soap = new soap_server;
    $soap->configureWSDL('AddService', 'http://php.
        phrasebook.org/');
    $soap->wsdl->schemaTargetNamespace = 'http://
        soapinterop.org/xsd/';
    $soap->register(
        'add',
        array('a' => 'xsd:int', 'b' => 'xsd:int'),
        array('c' => 'xsd:int'),
        'http://soapinterop.org/'
    );
    $soap->service(isset($HTTP_RAW_POST_DATA) ?
        $HTTP_RAW_POST_DATA : '');

    function add($a, $b) {
        return $a + $b;
    }
?>
```
```

*A WSDL-enabled Web Service with NuSOAP (wsdl-nusoap-server.php)*

Back to the WSDL: Figure 9.3 shows the Web Service in the browser when called using GET. A click on the link shows some information about the add() method. In Figure 9.4, you see what happens when you append ?WSDL to the URL of the script (or click on the WSDL link): The WSDL for the service is automatically generated. Imagine if you had to do this manually...