However, if you replace the (==) operator with the (===) operator, code execution will display 0, which corresponds to the Boolean value **false** of the $result variable.

```
```php
<?php
$a = 5;
$b = "5";
$result = ($a == $b);
echo $result;
?>
```
```

# **Example of the difference operator :**

```
```php
<?php
$a = 5;
$b = 10;
$result = ($a != $b);
echo $result;
?>
```
```

Execution of this code displays the value 1, which corresponds to the Boolean value true (the value stored in the variable $result), since the variables $a and $b have different values.

# **Example of the strict difference operator (!=) :**