ReactPHP is accessible through Composer, simplifying its integration into PHP projects.

```
composer require react/event-loop
```

An example HTTP server crafted using ReactPHP is shown below:

```
<?php
require __DIR__ . '/vendor/autoload.php';

$loop = React\EventLoop\Factory::create();
$server = new React\Http\Server($loop, function (Psr\Http\Message\ServerRequestInterface
    $request) {
    return new React\Http\Message\Response(
        200,
        ['Content-Type' => 'text/plain'],
        "ReactPHP welcomes you\n"
    );
});

$socket = new React\Socket\Server('0.0.0.0:9501', $loop);
$server->listen($socket);

echo "ReactPHP server active at http://127.0.0.1:9501\n";
$loop->run();
```