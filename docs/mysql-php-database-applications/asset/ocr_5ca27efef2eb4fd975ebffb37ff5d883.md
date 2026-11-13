# ## THE HEADER FILE

Many of the files in the Barnes & Noble and Babelphish applications call a header file initially. The header file, header.php, does two important things. First, it imports the critical nusoap.php file. It also specifies how the local applications deal with errors.

Here is header.php:

```
```php
<?php
.

require_once(preg_replace('/soap.*/','book.php',realpath(__FILE__)))
;
function soap_errors()
{
 $oh = set_error_handler('error_handler');
 if (empty($oh))
 {
 set_handler(0, H_ERROR);
 set_handler(E_ALL, H_LOG);
 }
 else
 {
 restore_error_handler();
 }
 }

soap_errors();

// include the class and function definitions for this application
require_once('lib/nusoap.php');
?>
```
```

# ## THE CLIENT FILE

The client file actually handles the process of instantiating a SOAP client that connects to a publicly accessible Web service providing Barnes & Noble prices (really, it just tells NuSOAP to do the dirty work). Here it is:

```
```php
<?php
// include the SOAP classes
require_once(dirname(__FILE__).'/header.php');
// define parameter array (ISBN number)
$param = array('isbn'=> '0385503954');
// define path to server application
$serverpath
='http://services.xmethods.net:80/soap/servlet/rpcrouter';
//define method namespace
$namespace="urn:xmethods-BNPriceCheck";
```
```