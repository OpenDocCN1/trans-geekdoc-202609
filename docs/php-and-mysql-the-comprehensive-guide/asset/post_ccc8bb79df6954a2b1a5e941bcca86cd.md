
![](img/ae7820c36e8f24c1623d26668b28e80e_285_0.png)

## Figure 9.12 Formatted Date, Timestamp, and Part of the Date

**Note**
A similar and sometimes useful function is `date_parse_from_format()`. It allows a format to be specified and a string containing the date as the second value. This then becomes an associative array with the date components.

Another option is the `strtotime(date, reference)` auxiliary function, which automatically converts a date in English format into a timestamp. Optionally, you can specify a reference time as a timestamp. This completes any missing information.

The question now is which data is converted correctly. Consider the following simple test script, the output of which you can see in Figure 9.13.

```php
<?php
$date = " July 18 2014";
$timestamp = strtotime($date);
echo $timestamp . "<br />";
$weekday = date("l", $timestamp);
echo "The birthday was a " . $weekday . ".";
?>
```

## Listing 9.19 “strtotime()” (“strtotime.php”)

![](img/ae7820c36e8f24c1623d26668b28e80e_285_1.png)

## Figure 9.13 Timestamp and Part of the Date

As an alternative to real dates, also references of the following type are possible:

```
$date = "last Sunday";
```

This refers, for example, to the previous Sunday.

> > **Note**
> >
> > Fortunately, there is a system: The syntax of the possible date specifications in `strtotime()` follows the GNU guidelines. You can find these at `http://s-rs.co/v602213`. References to previous or upcoming weekdays are summarized there—for example, under **7.7 Relative Items in Date Strings**.

## Validity of Data

The Gregorian calendar,<sup>1</sup> which we use today, is often a little complicated. The concept of leap years in particular often causes some confusion. With `checkdate(month, day, year)`, PHP offers a check function. It requires all three parameters and then checks whether the date is a correct Gregorian date.

The function knows three conditions to return `true` for a valid date:

- The year must be between 1 and 32767. Years before the birth of Christ cannot be calculated. Of course, this method does not make much sense for dates before the introduction of the Gregorian calendar, as it also calculates a leap year for this time.
- The month must be between 1 and 12.
- The day must have existed in the month in the year.

This function does not fail with 1900 or 2000. The year 1900 is not a leap year, as 1900 is divisible by 100—but 2000 is, as it is divisible by 400.<sup>2</sup>

```php
<?php
$day = 29;
$month = 2;
$year = 2000;
if (checkdate($month, $day, $year)) {
echo "Valid!";
} else {
    echo "Oops, $year is unfortunately not a leap year!";
}
?>
```

<sup>1</sup> Our calendar was originally created by Gaius Julius Caesar, the general and consul who sealed the end of the Roman Republic. However, the Julian calendar named after him had some weaknesses, which were finally addressed in the Gregorian calendar by Pope Gregory XIII in 1582 with the support of the astronomer Lilius.

<sup>2</sup> The Julian calendar had a year length of 365.25 days (normally 365; 366 every four years). As this was not entirely astronomically correct, there were shifts. Pope Gregory XIII dropped the days between October 5, 1582, and October 14, 1582 (inclusive), and then introduced the following rule: All years divisible by 100 are not leap years. However, since this also had to be corrected a little, years divisible by 400 are leap years after all.

## Listing 9.20 "checkdate()" ("checkdate.php")

The preceding script correctly returns Valid!.

## 9.2.5 Format Date

In most cases, you, your database, or the users of your website have a specific idea of what a date should look like. You can easily realize this with DateTime and format(), but also with date() and getdate(). Ahead you will find some examples and tricks for how to format dates quickly.

### "strftime()"

The strftime(format, timestamp) function formats an arbitrary date in a given format. If you do not specify a timestamp, the current date is used as usual. Attention, the function is deprecated since PHP 8.1.

> **Tip**
> The counterpart to strftime() is strptime(). It converts a date produced by strftime() into an array.

strftime() works in the background with a C library.<sup>3</sup> The abbreviations for individual elements always begin with %. Unfortunately, the designations differ significantly from those in date().

For example, the following line displays the complete month name:

```
echo strftime("%B");
```

> **Note**
> Depending on the C library used, there may be differences from system to system. The PHP function reference reveals the common denominator (http://s-prs.co/v602272); otherwise, you can find further information in the reference of the respective C library. For Windows, for example, see http://s-prs.co/v602214.

<sup>3</sup> This is easy to explain: PHP is written in the C programming language and therefore also uses C libraries and adopts some special features.

### "setlocale()"

If you format a date with strftime(), you can also do this with special local time settings. The setlocale(category, local setting) function sets one or any number of local settings for a specific category. The category can be the decimal separator (LC_NUMERIC), everything (LC_ALL), or the time (LC_TIME). As a local setting, enter de_DE for the German language area, for example. You can separate multiple entries with commas or pack them into an array. A German month is output by the following example (see Figure 9.14), in which the local settings are separated by commas.

```php
<?php
setlocale(LC_TIME, "de_DE", "de", "ge");
echo strftime("In month %B");
?>
```

## Listing 9.21 "setlocale()" ("setlocale.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_288_0.png)

## Figure 9.14 The Month in German with "setlocale()" — But with Deprecated function strftime()

> **Note**
> 
> With date_default_timezone_get(), you can read the default time zone, and set it with date_default_timezone_set().

### "idate()"

The idate(format, timestamp) function returns an element of a date. You can therefore only specify an abbreviation for format. This abbreviation is one from the list for date(). However, idate() only uses those that return an integer. This is precisely the special feature of idate() — hence the i (for integer) in front of date() :

```
echo idate("m");
```

Just as with date(), you can use a timestamp with idate() or omit it.

### GMT

GMT stands for Greenwich Mean Time. Dates in other time zones always work with a time difference. Some of the date functions are therefore also available specifically for working with GMT without a time offset. These functions are important if you want to handle the time difference manually. The following are available:

- gmkmktime() generates a timestamp.
- gmdate() returns the date and allows a format string.
- gmstrftime() formats with the format string that comes from C.

The parameters and results of the functions are the same as the GMT-independent originals.

## 9.2.6 Countdown: Calculate with Dates

Try to calculate how much time has passed between two dates. Okay, New Year’s Day to New Year’s Eve is too easy—but as soon as the span goes over several years, you have to include leap years, or it comes down to seconds, our mathematical cerebellum fails.

To be able to calculate with data via PHP, you need a base. This base is the timestamp from 1.1.1970 at 00:00:00. You can use it to simply subtract dates from or add dates to each other. The result is always the difference in seconds. You can then convert these seconds into any desired unit.

The following example shows a form that subtracts the current date from a date entered by a user. It then displays the result in whole days. You can see the form and the result in Figure 9.15 and Figure 9.16.

```php
<?php
if (isset($_POST["submit"])) {
	$date1 = strtotime($_POST["input"]);
	$date2 = time();
	$result = $date1 - $date2;
	if ($result > 0) {
		echo "Still ". floor($result / (60 * 60 * 24)) . " days ";
		echo "until ". date('m/d/Y', $date1);
	} else {
		echo "Your date is not in the future!";
	}
}
?>
