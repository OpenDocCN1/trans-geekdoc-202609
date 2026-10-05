with functions, there are two basic scopes: the global and the local scope. The local scope is also called a function scope.
scope1.php

```
<?php

$value = 1;

function simple() {

    var_dump($value);
}

simple();
?>
```

A variable defined outside a function body cannot be referenced within a function.
$ php scope1.php
PHP Notice: Undefined variable: value in /home/janbodnar/prog/php/functions/scope1.php on line 7
NULL

The $value variable is NULL in the simple() function.
scope2.php

```
<?php

$value = 4;

function simple() {

    $value = 3;
    echo $value, "\n";
}

simple();
```