```
```
'Referer: http://localhost.example'
)),
'content' => http_build_query(array(
   'param1' => 'value1',
   'param2' => 'value2'
   ))
)
));

$response = file_get_contents(
   'http://localhost.example/process',
   false,
   $context
);
?>
```
```

Here is a walk-through of this example.

+   - `'http'` is the streams wrapper being used.

+   - `'POST'` is the HTTP method of the request.

+   - The `'header'` stream context setting is populated with a string containing HTTP header key-value pairs, in this case for the Content-Type and Referer HTTP headers. The Content-Type header is used to indicate that the request body data is URL-encoded. When multiple custom headers are needed, they must be separated by a carriage return-line feed (`"\r\n"` also known as CRLF sequence). The `implode` function is useful for this if key-value pairs for headers are stored in an enumerated array.

+   - The `http_build_query` function is being used to construct the body of the request. This function can also be used to construct query strings of URLs for GET requests.

+   - `http://localhost.example/process` is the URL of the resource being requested.

+   - `file_get_contents` is called to execute the request, the options for which are passed via the context `$context` created using `stream_context_create`.

+   - The body of the response is returned and stored in the variable `$response`.