# Basic Computer Coding: PHP

```
echo $value, "\n";
```

```
?>
```

In this example, we have two variables with the same name. They do not collide because they exist in different scopes.

```
$ php scope2.php
```

```
3
```

```
4
```

The value is 3 inside the function and 4 outside the function.
In the next example, we will modify a value inside the function.

```
scope3.php
```

```
<?php
```

```
$value = 1;
```

```
function simple() {
```

```
global $value;
```

```
$value = 2;
```

```
}
```

```
echo $value, "\n";
```

```
simple();
```

```
echo $value, "\n";
```

```
?>
```

We use the global keyword to reference a variable defined outside
the body of the function.

```
$ php scope3.php
```

```
1
```

```
2
```

The $value was successfully modified inside the simple () function.
In this part of the PHP tutorial, we covered PHP functions.