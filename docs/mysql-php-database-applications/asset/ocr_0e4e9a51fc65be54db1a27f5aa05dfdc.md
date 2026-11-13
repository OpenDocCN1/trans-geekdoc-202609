```
```php
'application', 'username', 'password', 'database'
);
$p = func_get_args();
$p = parse_arguments($p, $_simple, $_defaults);

static $dsnlist = array(
    'default' => array(
        'phptype' => 'mysql',
        . 'dbsyntax' => NULL
        . 'username' => 'nobody'
        . 'password' => 'ydobon'
        . 'protocol' => 'tcp'
        . 'hostspec' => 'localhost'
        . 'port' => NULL
        . 'socket' => NULL
        . 'database' => 'test'
    ),
    'oldcatalog' => array(
        'phptype' => 'mysql',
        . 'dbsyntax' => NULL
        . 'username' => 'nobody'
        . 'password' => 'ydobon'
        . 'protocol' => 'tcp'
        . 'hostspec' => 'localhost'
        . 'port' => NULL
        . 'socket' => NULL
        . 'database' => 'oldcatalog'
    ),
    'catalog' => array(
        'phptype' => 'mysql'
        . 'dbsyntax' => NULL
        . 'username' => 'nobody'
        . 'password' => 'ydobon'
        . 'protocol' => 'tcp'
        . 'hostspec' => 'localhost'
        . 'port' => NULL
        . 'socket' => NULL
        . 'database' => 'catalog'
    ),
    'discussion' => array(
        'phptype' => 'mysql',
        . 'dbsyntax' => NULL
        . 'username' => 'nobody'
        . 'password' => 'ydobon'
        . 'protocol' => 'tcp'
```
```