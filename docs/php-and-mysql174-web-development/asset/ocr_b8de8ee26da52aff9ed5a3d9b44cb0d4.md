# Calculating Dates in MySQL

down by using the `floor()` function because a person is not said to be, for example, 20, until
the end of his twentieth year:

```
$age = floor($ageunix / (365 * 24 * 60 * 60)); // convert from seconds to years
```

Note, however, this approach is somewhat flawed because it is limited by the range
Unix timestamps (32-bit integers). Birthdates are not an ideal application for
timestamps. This example works on all platforms for people born from 1970 onwards.
Windows cannot manage timestamps prior to 1970. Even then, this calculation is not always
accurate because it does not allow for leap years and might fail if midnight on the person’s
birthday is the daylight savings switcher in the local time zone.

PHP has a few date manipulation functions built in, specifically `date_add()`, `date_sub()`, and
date_diff()`. Obviously, you can write your own, but ensuring that you correctly account for
leap years and daylight savings time can be tricky, so be tricky to use what is available.

Another date calculation option that may not seem immediately obvious is MySQL.
MySQL provides an extensive range of date functions that work for times outside
the range of Unix timestamps. You need to connect to a MySQL server to run your
query, but you do not have to select any data from the database.

For example, the following query adds one day to the date February 28, 1700, and returns the
resulting date:

```
select adddate('1700-02-28', interval 1 day);
```

The year 1700 is not a leap year, so the result is 1700-03-01.

You can find an extensive syntax for describing and modifying dates and times described in
the MySQL manual; it is located at http://dev.mysql.com/doc/refman/5.6/en/date-time-functions.html

Unfortunately, there is not a simple way to get the number of years between two dates, so the
birthday in Listing 19.1 is still a flaky you. You can get a person’s age in days very
easily, and Listing 19.2 converts to age precisely.

Listing 19.2 mysql_calc_age.php—Using MySQL to Work Out a Person’s Age Based on Birthdate

```
<?php
// set date for calculation
$day = 18;
$month = 9;
$year = 1972;

// format birthday as an ISO 8601 date
$bdayISO = date("c", mtime(0, 0, 0, $month, $day, $year));
```