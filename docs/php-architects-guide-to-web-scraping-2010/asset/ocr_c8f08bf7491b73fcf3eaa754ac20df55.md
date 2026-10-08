+   sendRequest intuitively dispatches the request and obtains the response. It returns either true to indicate that that request succeeded or an error object (of the PEAR_Error class by default) if an issue occurred.

Issues that cause errors include environmental requirements of the component not being met or the target of the request exceeding the redirect limit. PEAR::isError is used to determine if the sendRequest call resulted in an error. If the request is sent successfully, several methods of the request object are available to extract response information.

```
<?php
if (!PEAR::isError($response)) {
  $code = $request->getResponseCode();
  $reason = $request->getResponseReason();
  $body = $request->getResponseBody();
  $cookies = $request->getResponseCookies();
  $headers = $request->getResponseHeader();
  $contentType = $request->getResponseHeader('Content-Type');
}
?>
```

Here are a few specifics about the response information methods.

+   getResponseCode returns an integer containing the HTTP status code.

+   getResponseReason returns a string containing a description that corresponds to the HTTP status code.

+   getResponseCookies returns false if no cookies are set; otherwise it returns an enumerated array of associative arrays each of which contains information for an individual cookie such as its name, value, and expiration date.

+   getResponseHeader will return an associative array of all headers indexed by header name (in all lowercase) if no parameter is passed to it; otherwise, it takes a single string parameter containing a specific header name for which it will return the value.

sendRequest does not modify any parameters set by you that are specific to the request (as opposed to the response). That is, request instances can be reused and