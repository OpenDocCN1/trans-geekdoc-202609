NOTE: At the time of this writing, strtot ime() shows some strange behavior when a relative date is calculated and a change from or to DST is imminent. Also at the time of this writing, PHP's date/time functions are about be rewritten and amended.

# Determining Sunrise and Sunset

```
<?php
echo 'Sunrise: ' .
    date_sunrise(time(), SUNFUNCS_RET_STRING, 48,
    11.5, 90, 1) . '<br />';
    echo 'Sunset: ' .
    date_sunset(time(), SUNFUNCS_RET_STRING, 48,
    11.5, 90, 1);
?>
```

Depending on the current location and date, the times for sunrise and sunset can drastically vary. However, formulas exist for determining this value depending on latitude and longitude, and PHP has this functionality integrated into its core starting with PHP 5. All you are required to do is call date_sunrise() and date_sunset(). Both functions expect a number of parameters:

+   - A time stamp (epoch value) of the date for which to determine the sunrise/sunset.
+   - The desired format for the return value. SUNFUNCS_RET_DOUBLE returns the time as a float value (between 0 and 23.99), SUNFUNCS_RET_STRING returns it as a string (between 00:00 and 23:59), and SUNFUNCS_RET_TIMESTAMP returns an epoch value.