Below is a basic instantiation of an HTTP server utilizing Swoole:

```
<?php
use Swoole\Http\Server;
use Swoole\Http\Request;
use Swoole\Http\Response;

$http = new Server("0.0.0.0", 9501);

$http->on("start", function (Server $server) {
    echo "Swoole server operational at http://127.0.0.1:9501\n";
});

$http->on("request", function (Request $request, Response $response) {
    $response->header("Content-Type", "text/plain");
    $response->end("Greetings from Swoole\n");
});

$http->start();
```

This code delineates a straightforward HTTP server that issues a greeting in response to incoming requests, illustrating the simplicity of asynchronous server setup with Swoole.