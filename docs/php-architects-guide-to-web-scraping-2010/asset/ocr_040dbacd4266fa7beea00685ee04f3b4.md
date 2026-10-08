**PEAR Developments**
At the time of writing, efforts are being put into PEAR 2, the successor to the current incarnation of the PEAR project. This will include a newer package distribution system and ports or revamps of many existing packages to bring them up-to-date with features available in PHP 5. However, because there is currently little in the way of stable ported code for PEAR 2, coverage in this book will be limited to PEAR 1.

# Requests and Responses

There are two ways to perform HTTP requests with the related PEAR components: HTTP_Request and HTTP_Client. The latter composes the former to add capabilities such as handling redirects and persisting headers, cookie data, and request parameters across multiple requests. Here's how to perform a simple request and extract response information when using HTTP_Request directly.

```
<?php
require_once 'HTTP/Request.php';

$request =& HTTP_Request('http://localhost.example');
$request->setMethod(HTTP_REQUEST_METHOD_GET);
$request->setURL('http://localhost.example');
$response = $request->sendRequest();
?>
```

+   - The HTTP_Request constructor has two parameters, both of which are optional. The first is a string containing the URL for the request; note that the setURL method is an alternative way to specify a value for this. The second is a parameters array, which will be discussed later.
- By default, the GET method is used. setMethod is used to change this using constants, the names for which are formed by prefixing the desired request method with HTTP_REQUEST_METHOD_ as in HTTP_REQUEST_METHOD_GET.