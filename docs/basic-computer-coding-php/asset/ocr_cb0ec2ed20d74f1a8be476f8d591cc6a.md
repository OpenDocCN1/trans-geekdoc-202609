```
static $value = 0;
$value += 1;
```

```
return $value;
}
```

```
staticfun();
staticfun();
staticfun();
staticfun();
```

```
echo staticfun(), "\n";
```

```
??>
```

After 5 consecutive calls, the $value is equal to 5.

```
$ php nonstatic.php
2
$ php static.php
6
```

# 3.1.7 PHP anonymous functions

Anonymous functions do not have a name.
anonymous.php

```
<?php
$var = function() {
```

```
echo "This is anonymous function\n";
};
```

```
$var();
```