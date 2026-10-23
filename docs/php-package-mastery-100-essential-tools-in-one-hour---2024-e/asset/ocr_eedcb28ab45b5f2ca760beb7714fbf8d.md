# 5. Slim Framework

Slim is a PHP micro framework that helps you quickly write simple yet powerful web applications and APIs. It comes with a router, middleware support, and is designed to be lightweight and easily understandable, making it ideal for projects that need a minimalistic setup.

Ex:Slim Framework

```
```php
use Psr\Http\Message\ResponseInterface as Response;
use Psr\Http\Message\ServerRequestInterface as Request;
use Slim\Factory\AppFactory;
require __DIR__ . '/../vendor/autoload.php';
$app = AppFactory::create();
$app->get('/hello/{name}', function (Request $request, Response $response, $args) {
    $name = $args['name'];
    $response->getBody()->write("Hello, $name");
    return $response;
});
$app->run();
```
```

Visiting /hello/John on your server would display: Hello, John