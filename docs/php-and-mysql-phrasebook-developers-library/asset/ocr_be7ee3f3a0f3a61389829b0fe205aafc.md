```
function isLeapYear($year) {
    return ($year % 4 == 0 &&
        ($year % 100 != 0 || $year % 400 == 0));
}
```

You could also use DateTime::createFromFormat() which returns false if an error occurs. However checkdate() is probably more explicit because the name of the function describes exactly what we want to do.

# Calculating a Relative Date

```
<?php
echo 'The license you have just bought is valid till ';
$expiry = time() + 30 * 24 * 60 * 60; //30 days)
echo strftime('%c', $expiry);
?>
```

Sometimes you have the task of calculating a date that is relative to the current date (for example, 30 days from now). Of course, you could put some real work into actually calculating this value, taking into account which day it is, whether it's a leap year, and whether DST is relevant.

Far easier is the use of an epoch time stamp. Take, for instance, the aforementioned task of finding a date that lies 30 days in the future. One day has 24 hours, 1 hour has 60 minutes, and 1 minute has 60 seconds. Therefore, to get the current time stamp (using time() or date('U')), you just need to add 30 * 24 * 60 * 60, and you have the time stamp of the desired date. You can then use this time stamp to set a cookie's expiry date or just to print out some information about this date.