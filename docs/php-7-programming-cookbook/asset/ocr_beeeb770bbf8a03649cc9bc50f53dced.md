```
        ],
        'page' => [
            'uri' => '!^/(page)/(\\d+)/()/?$!'.
            'exec' => function ($matches) {
                include PAGE_DIR . '/page' . $matches[2] . '.php'; }
        ],
        Router::DEFAULT_MATCH => [
            'uri' => '!.*!'.
            'exec' => function ($matches) {
                include PAGE_DIR . '/sorry.php'; }
        ],
    ];
```

You can then define a router instance, supplying an initialized ServerRequest instance as the first argument:

```
    $router = new Router((new ServerRequest())
        ->initialize(), DOC_ROOT, $config);
    $execute = $router->match();
    $params  = $router->getRouteMatch('match');
```

You then need to check to see whether the request is a file or directory, and also whether the route match is /:

```
    if ($fn = $router->isFileOrDir()
        && $router->getRequest()->getUri()->getPath() != '/') {
        return FALSE;
    } else {
        include DOC_ROOT . '/main.php';
    }
```

Next, define main.php, something like this:

```
<?php // demo using middleware for routing ?>
<!DOCTYPE html>
<head>

    <title>PHP 7 Cookbook</title>
    <meta http-equiv="content-type"
          content="text/html; charset=utf-8" />
</head>
<body>
    <?php include PAGE_DIR . '/route_menu.php'; ?>
    <?php $execute($params); ?>
</body>
</html>
```