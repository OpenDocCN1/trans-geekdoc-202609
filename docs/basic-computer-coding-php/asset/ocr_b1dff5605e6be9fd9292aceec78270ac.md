# Example #11. Some string examples

```
<?php
// Get the first character of a string
$str = ‘This is a test.’;
$first = $str[0];
```

```
// Get the third character of a string
$third = $str[2];
```

```
// Get the last character of a string
$str = ‘This is still a test.’;
$last = $str[strlen($str)-1];
```

```
// Modify the last character of a string
$str = ‘Look at the sea’;
$str[strlen($str)-1] = ‘e’;
```

As of PHP 5.4 string offsets have either to be integers or integer-like strings, otherwise a warning will be thrown. Previously an offset like “foo” was silently cast to 0.

# Example #12. Differences between PHP 5.3 and PHP 5.4

```
<?php
$str = ‘abc’;
```

```
var_dump($str['1.0']);
var_dump(isset($str['1.0']));
```

```
var_dump($str['x']);
```