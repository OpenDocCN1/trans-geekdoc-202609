```
echo '<h1>', $params[Validator::KEY_TEXT], '</h1>';
echo '<pre>', var_dump($inbound), '</pre>';
exit;
}
return $next($request,$response);
}
}
```

You will now need to add the new class to the middleware pipeline. Modify config/autoload/middleware-pipeline.global.php as follows. Modifications are shown in bold:

```
<?php
use Zend\Expressive\Container\ApplicationFactory;
use Zend\Expressive\Helper;
return [
'dependencies' => [
'invokables' => [
App\Action\SessionValidateAction::class =>
App\Action\SessionValidateAction::class,
],
'factories' => [
Helper\ServerUrlMiddleware::class =>
Helper\ServerUrlMiddlewareFactory::class,
Helper\UrlHelperMiddleware::class =>
Helper\UrlHelperMiddlewareFactory::class,
],
],
'middleware_pipeline' => [
'always' => [
'middleware' => [
Helper\ServerUrlMiddleware::class,
],
'priority' => 10000,
],
'routing' => [
'middleware' => [
ApplicationFactory::ROUTING_MIDDLEWARE,
Helper\UrlHelperMiddleware::class,
App\Action\SessionValidateAction::class,
ApplicationFactory::DISPATCH_MIDDLEWARE,
],
'priority' => 1,
],
```