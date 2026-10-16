
```php
function isLeapYear($year) {
    return ($year % 4 == 0 &&
        ($year % 100 != 0 || $year % 400 == 0));
}
```

You could also use `DateTime::createFromFormat()` which returns false if an error occurs. However `checkdate()` is probably more explicit because the name of the function describes exactly what we want to do.

## Calculating a Relative Date

```php
<?php
echo 'The license you have just bought is valid till ';
$expiry = time() + 30 * 24 * 60 * 60; // 30 days
echo strftime('%c', $expiry);
?>
```

Sometimes you have the task of calculating a date that is relative to the current date (for example, 30 days from now). Of course, you could put some real work into actually calculating this value, taking into account which day it is, whether it's a leap year, and whether DST is relevant.

Far easier is the use of an epoch time stamp. Take, for instance, the aforementioned task of finding a date that lies 30 days in the future. One day has 24 hours, 1 hour has 60 minutes, and 1 minute has 60 seconds. Therefore, to get the current time stamp (using `time()` or `date('U')`), you just need to add `30 * 24 * 60 * 60`, and you have the time stamp of the desired date. You can then use this time stamp to set a cookie's expiry date or just to print out some information about this date.

If you are using the DateTime class, you can also use the `add()` and `sub()` methods, which are covered in more detail in the “Calculating the Difference between Two Dates” section, later in this chapter.

## Creating a Sortable Time Stamp

```php
<?php
function timestamp($t = null) {
    if ($t == null) {
        $t = time();
    }
    return date('YmdHis', $t);
}

echo 'Time stamp: ' . timestamp(time());
?>
```

Using date values with a database is not always clever. Different language versions of the database, its drivers, or the underlying operating system could cause some trouble when the regional date formats do not fit together.

A potential alternative is the use of time stamps. Several different formats are available, but most of them have the following structure: year-month-day hours-minutes-seconds. Using this value order, the string representation of the date can be easily sorted, which allows using it in databases.

To create such a time stamp, just a special call to `date()` is required. In the preceding code, this is encapsulated in a function for easy reuse.

**TIP:** This format is also used by MySQL for the representation of its TIMESTAMP data type.

## Converting a String into a Date

```php
<?php
echo 'Yesterday: ' . date('r', strtotime('Yesterday')) . '<br />';
echo 'Today: ' . date('r', strtotime('Today')) . '<br />';
echo 'Tomorrow: ' . date('r', strtotime('Tomorrow')) . '<br />';
echo 'In one week: ' . date('r', strtotime('+1 week')) . '<br />';
echo 'One month before: ' . date('r', strtotime('-1 month')) . '<br />';
echo 'Last Sunday: ' . date('r', strtotime('Last Sunday')) . '<br />';
echo 'Next fantasy day: ' . var_export(@date('r', strtotime('Next fantasy day')), true);
?>
```

Previously, you saw a numeric representation of a date—either a triplet of day, month, and year, or a time stamp value. This time, you can go the other way and convert a string representation of a date/time value into an epoch value or something else that is usable within PHP and its date/time functions.

The whole magic is put into the PHP function `strtotime()`. According to the documentation, it “parses about any English textual date/time description into a UNIX time stamp.” It sounds amazing, and it is amazing. The basis for this is the GNU date syntax; the code at the beginning of this phrase shows some examples for `strtotime()`.

**NOTE:** At the time of this writing, `strtotime()` shows some strange behavior when a relative date is calculated and a change from or to DST is imminent. Also at the time of this writing, PHP's date/time functions are about to be rewritten and amended.

## Determining Sunrise and Sunset

```php
<?php
echo 'Sunrise: ' .
    date_sunrise(time(), SUNFUNCS_RET_STRING, 48,
    11.5, 90, 1) . '<br />';
    echo 'Sunset: ' .
    date_sunset(time(), SUNFUNCS_RET_STRING, 48,
    11.5, 90, 1);
?>
```

Depending on the current location and date, the times for sunrise and sunset can drastically vary. However, formulas exist for determining this value depending on latitude and longitude, and PHP has this functionality integrated into its core starting with PHP 5. All you are required to do is call `date_sunrise()` and `date_sunset()`. Both functions expect a number of parameters:

- A time stamp (epoch value) of the date for which to determine the sunrise/sunset.
- The desired format for the return value. `SUNFUNCS_RET_DOUBLE` returns the time as a float value (between 0 and 23.99), `SUNFUNCS_RET_STRING` returns it as a string (between 00:00 and 23:59), and `SUNFUNCS_RET_TIMESTAMP` returns an epoch value.
- The latitude (northern latitude; use negative values for a southern latitude).
- The longitude (eastern longitude; use negative values for a western longitude).
- The zenith of the sunrise (in degrees).
- The offset (in hours) to GMT.

So, the preceding code calculates the sunrise and sunset for Munich, Germany, which resides at about 48° Northern latitude, 11° 30′ eastern longitude, for the current day. I checked it: It worked!

## Using Date and Time for Benchmarks

```php
<?php
// ...

$start = microtimestamp();
$s = "";
for ($i=0; $i < 100000; $i++) {
    $s .= "$i";
}
$end = microtimestamp();
echo 'Using double quotes: ' . ($end-$start) . '<br />';

$start = microtimestamp();
$s = '';
for ($i=0; $i < 100000; $i++) {
    $s .= $i;
}
$end = microtimestamp();
echo 'Using no quotes: ' . ($end-$start) . '<br />';
?>
```

![](img/2862989e5dc7f1b1d0bc64321737f084_100_0.png)

Figure 3.3 Measuring the performance of two pieces of code

**TIP:** You can replace the `microtimestamp()` function with the following code:

```php
function microtimestamp() {
    return microtime(true);
}
```

The function `microtime()` returns a float value of the current microtime when the parameter `true` is provided (this was added in PHP 5). However, this is reportedly slower than using `gettimeofday()`, which just executes the underlying gettimeofday system call.

## Using Form Fields for Date Selection

```php
<form method="post" action="">
<select name="day"><?php
    for ($i = 1; $i <= 31; $i++) {
        echo "<option value=\"$i\">$i</option>\n";
    }
?>
</select>
<select name="month"><?php
for ($i = 1; $i <= 12; $i++) {
    $monthname = date('F', mktime(12, 0, 0, $i, 1, 2012));
    echo "<option value=\"$i\">$monthname</option>";
}
?></select>
<select name="year"><?php
for ($i = 2012; $i <= 2015; $i++) {
    echo "<option value=\"$i\">$i</option>";
}
?></select>
</form>
```

If you want to offer an HTML form to select a date, like many hotel- and flight-booking services offer, you can use the various parameters of `date()`; loop through all months of the year; and, thus, create a selection list of days, months, and years. The preceding code contains the syntax for this; see Figure 3.4 for the result.

![](img/2862989e5dc7f1b1d0bc64321737f084_101_0.png)

Figure 3.4 The month names were automatically generated.

## Create Self-Updating Form Fields for Date Selection

```php
<?php
if (isset($_POST['month']) &&
    is_numeric($_POST['month']) &&
    ((int)$_POST['month'] >= 1 &&
    (int)$_POST['month'] <= 12)) {
    $month = (int)$_POST['month'];
} else {
    $month = date('n');
}
if (isset($_POST['year']) &&
    is_numeric($_POST['year']) &&
    ((int)$_POST['year'] >= 2012 &&
    (int)$_POST['year'] <= 2015)) {
    $year = (int)$_POST['year'];
} else {
    $year = date('Y');
}
?>
<form method="post" action="<?php echo
htmlspecialchars($_SERVER['PHP_SELF']); ?>">
    $maxdays = date('t', mktime(12, 0, 0, $month, 1,
$year));
    for ($i = 1; $i <= $maxdays; $i++) {
        if (isset($_POST['day']) && $_POST['day'] ==
$i) {
            $sel = ' selected';
        } elseif ($i == date('j')) {
            $sel = ' selected';
        } else {
            $sel = '';
        }
    }
    echo "<option value=\"$i\"$sel>$i</option>\n";
```
