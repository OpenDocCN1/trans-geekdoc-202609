![](bbox=[0.138, 0.1, 0.666, 0.19])

Figure 10.1 The Array with the Location and the Position in the String

The fourth parameter, String position, defines the string or position from which the search starts. Consider the modified example:

```
```php
$text = "Hello all!";
$reg = "/ll/";
preg_match($reg, $text, $parts, PREG_OFFSET_CAPTURE, 5);
```
```

The regular expression finds the second occurrence of 11, as it only searches from the fifth position in the string. Figure 10.2 shows the result.

![](bbox=[0.138, 0.405, 0.666, 0.505])

Figure 10.2 Here You Can See Start Position 7

preg_match() only ever finds the first occurrence of a search string. A more flexible option is preg_match_all(). You can see its output in Figure 10.3.

```
```php
<?php
$text = "Hello all!";
$reg = "/ll/";
preg_match_all($reg, $text, $parts, PREG_OFFSET_CAPTURE);
print_r($parts);
?>
```
```

Listing 10.3 "preg_match_all()" ("preg_match_all.php")

![](bbox=[0.138, 0.755, 0.77, 0.87])

Figure 10.3 "preg_match_all()" Finds Both Occurrences