# Manually Localizing Dates

```
<?php
$weekdays = array(
    'domingo', 'lunes', 'martes', 'miércoles',
    'jueves', 'viernes', 'sábado'
);
$months = array(
    'enero', 'febrero', 'marzo', 'abril',
    'mayo', 'junio', 'julio', 'agosto',
    'septiembre', 'octubre', 'noviembre', 'diciembre'
);
$weekday = date('w');
$month = date('n');
echo $weekdays[$weekday] . date(', j ') .
    $months[$month - 1] . date(' Y');
?>
```

If you cannot rely on setlocale(), yet want to use localized date and time values, you have to do the translations by yourself and store the results in an array. Then you can use date() to retrieve information about a date. This serves as an index for your array.

The preceding code does this for both the day of the month and the month itself. One array contains the Spanish weekdays; another one contains the month names.

Note that the value for the month is decreased by one because the array $months has no dummy element at position 0; therefore, month number one (January) has the index 0.