```
<?php
    $weekdays = array(
        'domingo', 'lunes', 'martes', 'miércoles',
        'jueves', 'viernes', 'sábado'
    );
    $months = array(
        'enero', 'febrero', 'marzo', 'abril',
        'mayo', 'junio', 'julio', 'agosto',
        'septiembre', 'octubre', 'noviembre',
        'diciembre'
    );
    $weekday = date('w');
    $month = date('n');
    echo $weekdays[$weekday] . date(', j ') .
        $months[$month - 1] . date(' Y');
?>
```

*Localizing Dates Manually (localdate.php)*

The preceding code does this for both the day of the month and the month itself. One array contains the Spanish weekdays; another one contains the month names.

Note that the value for the month is decreased by 1 because the array $months has no dummy element at position 0; therefore, month number one (January) has the index 0.

# Using the Current Date the U.S./U.K./European Way

```
<?php
    echo 'US format: ' . date('m/d/Y<br />');
    echo 'UK format: ' . date('d/m/Y<br />');
    echo 'German format: ' . date('d.m.Y<br />');
    echo 'International format: ' . date('Y-m-d');
?>
```