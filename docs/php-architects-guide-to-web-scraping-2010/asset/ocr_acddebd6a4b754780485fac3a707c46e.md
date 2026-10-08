```
`<?php
$handle = fopen('http://localhost.example', 'r');
$response = stream_get_contents($handle);
$meta = stream_get_meta_data($handle);
print_r($meta['wrapper_data']);
?>`
```

Let’s step through this.

+   * The resource $handle is created to read from the URL http://localhost.example.
* The stream_get_contents function is called to read the remaining data on the stream pointed to by the $handle resource into $response.
* The stream_get_meta_data function is called to read metadata for the stream pointed to by the $handle resource into $meta.
* The wrapper_data index of the $meta array outputs the same array as $http_response_header would within the current scope. So long as $handle is accessible within the current scope, stream_get_meta_data() can be called on it. This makes it more flexible than $http_response_header.

# ## Stream Contexts and POST Requests

Another concept introduced by streams is the context, which is basically a set of configuration options used in a streams operation. A context is created by passing an associative array of context options and their corresponding values to the stream_context_create function. One use of contexts with regard to the HTTP streams wrapper is making POST requests, as the wrapper uses the GET method by default.

```
`<?php
$context = stream_context_create(array(
  'http' => array(
    'method' => 'POST',
    'header' => implode("\r\n", array(
      'Content-Type: application/x-www-form-urlencoded',`
```