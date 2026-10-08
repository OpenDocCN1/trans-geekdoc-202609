
# Converting Between PHP and MySQL Date Formats

- %W Week number (with the first Monday of the year being the first day of the first week).
- %x Date in standard format (without the time), such as 02/17/15.
- %X Time in standard format (without the date), such as 02:26:21.
- %y Year, in two digits, such as 15.
- %Y Year, in four digits, such as 2015.
- %z The timezone offset, such as -0500.
- %Z The timezone abbreviation, such as EST.

It is important to note that whenever it says *standard format* in Table 19.3, the formatting code gets replaced by the associated value according to the web server's locale settings. The `strftime()` function is useful for displaying dates and times in a variety of different ways to make your pages more user friendly.

# Converting Between PHP and MySQL Date Formats

Dates and times in MySQL are handled in ISO 8601 format. Times work relatively intuitively, but ISO 8601 requires you to enter dates with the first year. For example, you could enter February 17, 2015, as 2015-02-17 or 15-02-17. Dates retrieved from MySQL are also in this format by default.

Depending on your intended audience, you might not find this function very friendly. To communicate with PHP and MySQL, then, you usually need to perform some conversion. This operation can be performed at either end.

When putting dates into MySQL from PHP, you can easily put them into the correct format by using the `date()` function, as shown previously. Minor caution if you are creating from your code is that you should store the day and month with leading zeros to avoid confusing MySQL. You can use a two-digit year, but for four-digit year, two functions are `DATE_FORMAT()` and `UNIX_TIMESTAMP()`.

The `DATE_FORMAT()` function works similarly to the PHP function but uses different formatting codes. The most common thing you want to do is format a date in American format (MM-DD-YYYY) rather than the ISO format (YYYY-MM-DD) native to MySQL. You can do this by writing your query as follows:

```
SELECT DATE_FORMAT(date_column, '%Y %m %d %Y')
FROM tablename;
```

# Chapter 19 Managing the Date and Time

The format code %m represents the month as a two-digit number; %d, the day as a two-digit number; and %Y, the year as a four-digit number. A summary of the more useful MySQL format codes for this purpose is shown in Table 19.4.

Table 19.4 Format Codes for MySQL's DATE_FORMAT ()

| Code | Description |
|---|---|
| %M | Month, full text |
| %W | Weekday name, full text |
| %D | Day of month, numeric, with text suffix (for example, 1st) |
| %Y | Year, numeric, four digits |
| %y | Year, numeric, two digits |
| %a | Weekday name, three characters |
| %d | Day of month, numeric, leading zeros |
| %e | Day of month, numeric, no leading zeros |
| %m | Month, numeric, leading zeros |
| %c | Month, numeric, no leading zeros |
| %b | Month, text, three characters |
| %j | Day of year, numeric |
| %H | Hour, 24-hour clock, leading zeros |
| %k | Hour, 24-hour clock, no leading zeros |
| %h or %I | Hour, 12-hour clock, leading zeros |
| %l | Hour, 12-hour clock, no leading zeros |
| %i | Minutes, numeric, leading zeros |
| %r | Time, 12-hour (hh:mm:ss [AM|PM]) |
| %T | Time, 24-hour (hh:mm:ss) |
| %S or %s | Seconds, numeric, leading zeros |
| %p | AM or PM |
| %w | Day of the week, numeric, from 0 (Sunday) to 6 (Saturday) |

You can see the most current and complete list of format codes for MySQL's DATE_FORMAT() function at http://dev.mysql.com/doc/refman/5.6/en/date-and-time-functions.html#function_date-format.

The UNIX_TIMESTAMP() function works similarly but converts a column into a Unix timestamp. For example,

```
SELECT UNIX_TIMESTAMP(date_column)
FROM tablename;
```

returns the date formatted as a Unix timestamp. You can then do as you want with it in PHP.
You can easily perform date calculations and comparisons with the Unix timestamp. Bear in mind, a timestamp can usually represent dates only between 1902 and 2038, whereas the MySQL date type has a much wider range.

As a rule of thumb, use a Unix timestamp for date calculations and the standard date format when you are just storing or showing dates.

# Calculating Dates in PHP

A simple way to work out the length of time between two dates in PHP is to use the difference between Unix timestamps. We use this approach in the script shown in Listing 19.1.

Listing 19.1 calc_age.php—Working a Person's Age Based on Birthdate

```
<?php
// set date for calculation
$day = 18;
$month = 9;
$year = 1972;

// remember you need bday as day and year
$bdayunix = mktime(0, 0, 0, $month, $day, $year); // get ts for then
$nowunix = time(); // get ts for today
$ageunix = $nowunix - $bdayunix; // work out the difference
$age = floor($ageunix / (365 * 24 * 60)); // convert from seconds to years

echo 'Current age is ' . $age . '.';
?>
```

This script sets the date for calculating the age. In a real application, it is likely that this comes from HTML. The script begins by calling mktime() to work out the timestamp for the birthday and the current time:

```
$bdayunix = mktime(0, 0, 0, $month, $day, $year)
$nowunix = time(); // get ts for today
```

Now that dates are in the same format, you can simply subtract them:

```
$ageunix = $nowunix - bdayunix;
```

Now, the slightly tricky part: converting this time period back to a more human-friendly unit. This is not a timestamp but instead the age of the person measured in seconds. To convert back by dividing by the number of seconds in a year, you then round it using the `floor()` function because a person is not said to be, for example, 20, until the end of his twentieth year:

```
$age = floor($ageunix / (365 * 24 * 60)); // convert from seconds to years
```

Note, however, this approach is somewhat flawed because it is limited by the range of Unix timestamps (32-bit integers). Birthdates are not ideal application for timestamps. This example works on all platforms for people born from 1970 onwards. Even then, this calculation is not accurate because it does not allow for leap years and might fail if midnight on the person’s birthday is the daylight savings switcher in the local zone.

PHP has a few date manipulation functions built in, specifically `date_add()`, `date_sub()`, and `datediff()`. Obviously, you can write your own, but ensuring that you correctly account for leap years and daylight savings time can be tricky, so it is better to use what is available.

Another date calculation option that may not seem obvious is MySQL. MySQL provides an extensive range of date functions that work for times outside the range of Unix timestamps. You need to connect to a MySQL server to run your query, but you do not have to select any data from the database.

For example, the following query adds one day to the date February 28, 1700, and returns the resulting date:

```
select adddate('1700-02-28', interval 1 day);
```

The year 1700 is not a leap year, so the result is 1700-03-01. You can find an extensive syntax for describing and modifying dates and times in the MySQL manual; it is located at http://dev.mysql.com/doc/refman/5.6/en/date-time-functions.html.

Unfortunately, there is not a simple way to get the number of years between two dates, so the birthday in Listing 19.1 is still a flaky. You can get a person’s age in days very easily, and Listing 19.2 converts to age precisely.

Listing 19.2 mysql_calc_age.php—Using MySQL to Work Out a Person’s Age Based on Birthdate

```php
<?php
// set date for calculation
$day = 18;
$month = 9;
$year = 1972;

// format birthday as an ISO 8601 date
$bdayISO = date("c", mktime(0, 0, 0, $month, $day, $year));

// use mysql query to calculate an age in days
$db = mysqli_connect('localhost', 'user', 'pass');
$res = mysqli_query($db, 'select datediff(now(), $bdayISO)');
$age = mysqli_fetch_array($res);

// convert age to days in years (approximately)
echo 'Current age is '.floor($age[0]/365.25) . '.';
?>
```

After formatting the date as an ISO timestamp, you pass the time to be useful for MySQL:

```
select datediff(now(), '1972-09-18T00:00:10.00');
```

The MySQL function now always returns the current date and time. The MySQL function datediff() subtracts one date from another and returns the difference in days.

It is worth noting that you are not selecting data from a table or even choosing a database to use for this script, but you need to log in to the MySQL server with a username and password.

Because no built-in function is available for such calculations, a SQL query to calculate the exact number of years is fairly complex. Here, we take a shortcut and divide the age in days by 365.25 to give the age in years. This calculation can be one year out exactly on somebody's birthday, depending on how many years there have been in that lifetime.

# Using Microseconds

For some applications, measuring time in an ISO timestamp is not precise enough to be. If you want to measure short periods, such as the time taken to run all of a PHP script, you need to use the function microtime().

Although an optional parameter, we recommend using true to microtime(). When this optional parameter is provided, microtime() will return the time as a floating point value that is ready for whatever you have in mind. The value is the same returned by mktime(), time() and has a fractional component.

The statement

```
echo number_format(microtime(true), 5, '.', '');
```

produces something like 1424141373.59053.

On older versions, you can request the result as a float. It is provided as a string. A call to microtime() without a parameter returns a string of this form "0.8679500 1424141403". The first number is the fractional part, and the second number is the number of whole seconds elapsed since January 1, 1970.

Dealing with numbers rather than strings is more useful, so it is easiest to call microtime() with the parameter true.
