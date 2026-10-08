code (though it is more noticeable in a high load environment). On the negative side, you have to either know C or depend on the community to deliver patches in a timely fashion for any issues that may arise. This also applies to extensions written in C that will be covered in subsequent sections.

The streams wrapper is part of the PHP core and as such has no installation re-quirements beyond that of PHP itself.

# Simple Request and Response Handling

Here's a simple example of the HTTP streams wrapper in action.

```
<?php
$response = file_get_contents('http://localhost.example');
print_r($http_response_header);
?>
```

There are a few things to note.

+   * The **allow_url_fopen** PHP configuration setting must be enabled for this to work, which it is in most environments.
* In this example, the **file_get_contents** function call is equivalent to making a GET request for the specified URL 'http://localhost.example'.
* **$response** will contain the response body after the call to the **file_get_contents** function completes.
* **$http_response_header** is implicitly populated with the HTTP response status line and headers after the **file_get_contents** call because it uses the HTTP streams wrapper *within the current scope*.

While this example does work, it violates a core principle of good coding prac-tices: no unexpected side effects. The origin of **$http_response_header** is not en-tirely obvious because PHP populates it implicitly. Additionally, it's more restric-tive because the variable is only populated within the scope containing the call to **file_get_contents**. Here's a better way to get access to the same data from the re-sponse headers.