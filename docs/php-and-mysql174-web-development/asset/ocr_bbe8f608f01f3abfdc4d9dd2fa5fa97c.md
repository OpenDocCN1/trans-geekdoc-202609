SELECT UNIX_TIMESTAMP(date_column)
FROM tablename;

returns the date formatted as a Unix timestamp. You can then do as you want with it in PHP.
You can easily perform date calculations and comparisons with the Unix timestamp. Bear in
mind, a timestamp can usually represent dates only between 1902 and 2038,\ whereas the MySQL date type has a much wider range.

As a rule of thumb, use a Unix timestamp for date calculations and the standard date format
when you are just storing or showing dates.

# Calculating Dates in PHP

A simple way to work out the length of time between two dates in PHP is to use the difference
bween Unix timestamps. We use this approach in the script shown in Listing 19.1.

Listing 19.1 calc_age.php—Working a Person's Age Based on Birthdate

```
<?php
// set date for calculation
$day = 18;
$month = 9;
$year = 1972;

// remember you need bday as day month and year
$bdayunix = mktime(0, 0, 0, $month, $day, $year); // get ts for then
$nowunix = time(); // get unix ts for today
$ageunix = $nowunix - $bdayunix; // work out the difference
$age = floor($ageunix / (365 * 24 * 60 * 60)); // convert from seconds to years

echo 'Current age is ' . $age . '.';
?>
```

This script sets the date for calculating the age. In a real, it is likely that this in-
might come from an HTML form. The script begins by calling mktime() to work out
the timestamp for the birthday and for the current time:

```
$bdayunix = mktime(0, 0, 0, $month, $day, $year)
$nowunix = time(); // get unix ts for today
```

Now that dates are in the same format, you can simply subtract them:

```
$ageunix = $nowunix - $bdayunix;
```

Now, the slightly tricky part: converting this time period back to a more human-friendly unit
of measure. This is not a timestamp but instead the age of the person measured in seconds. You
can convert back by dividing by the number of seconds in a year. You then round it