![](bbox=[0.142, 0.1, 0.658, 0.245])

# Figure 9.12 Formatted Date, Timestamp, and Part of the Date

**Note**
A similar and sometimes useful function is `date_parse_from_format()`. It allows a format to be specified and a string containing the date as the second value. This then becomes an associative array with the date components.

Another option is the `strtotime(date, reference)` auxiliary function, which automatically converts a date in English format into a timestamp. Optionally, you can specify a reference time as a timestamp. This completes any missing information.

The question now is which data is converted correctly. Consider the following simple test script, the output of which you can see in Figure 9.13.

```
```php
<?php
$date = " July 18 2014";
$timestamp = strtotime($date);
echo $timestamp . "<br />";
$weekday = date("l", $timestamp);
echo "The birthday was a " . $weekday . ".";
?>
```
```

# Listing 9.19 “strtotime()” (“strtotime.php”)

![](bbox=[0.142, 0.695, 0.658, 0.84])

# Figure 9.13 Timestamp and Part of the Date