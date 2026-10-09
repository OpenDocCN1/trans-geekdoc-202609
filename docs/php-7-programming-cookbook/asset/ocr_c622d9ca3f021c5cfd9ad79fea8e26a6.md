```
__DIR__ . '/' . $data[$id]);
} else {
$body['text'] = $data;
}
```

Otherwise, return a response indicating a success code 204 and the size of the request body received:

```
} elseif ($request->getMethod() == Constants::METHOD_POST) {
    $size = $request->getBody()->getSize();
    $body['text'] = $size . ' bytes of data received';
    if ($size) {
        $code = 201;
    } else {
        $code = 204;
    }
}
```

You can then catch any exceptions and report them with a status code of 500:

```
} catch (Exception $e) {
    $code = 500;
    $body['text'] = 'ERROR: ' . $e->getMessage();
}
```

The response needs to be wrapped in a stream, so you can write the body out to the temp file and create it as Stream. You can also set the Content-Type header to application/json and run getHeaders(), which outputs the current set of headers. After that, echo the body of the response. For this illustration, you could also dump the response instance to confirm it was constructed correctly:

```
try {
    file_put_contents($tempFile, json_encode($body));
    $body = new Stream($tempFile);
    $header[Constants::HEADER_CONTENT_TYPE] = 'application/json';
    $response = new Response($code, $body, $header);
    $response->getHeaders();
    echo $response->getBody()->getContents() . PHP_EOL;
    var_dump($response);
```

To wrap things up, catch any errors or exceptions using Throwable, and don't forget to delete the temp file:

```
} catch (Throwable $e) {
    echo $e->getMessage();
} finally {
    unlink($tempFile);
}
```