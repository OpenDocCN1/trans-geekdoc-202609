To create a timestamp from a GMT date and time, use gmktime(). This works in exactly the same way as mktime(), except that it expects its arguments to be in GMT. For example, let's say the computer running your PHP script is in the Indianapolis time zone, which is 5 hours behind GMT, and that it is running the following code:

```
$localTime = mktime( 14, 32, 12, 1, 6, 1972 );
$gmTime = gmktime( 14, 32, 12, 1, 6, 1972 );
```

After this code has run, $localTime holds the timestamp representing Jan 6, 1972 at 7:32:12 pm GMT / UTC (which is 2:32 pm on the same day Indianapolis time). Meanwhile, $gmTime holds the timestamp for 2:32:12 pm GMT /UTC; in other words, no time zone conversion has taken place.

mktime() and other date-related functions use the time zone set by the date.timezone directive in the php.ini file (see Chapter 2 for details). However you can, if desired, change the time zone used by your PHP script with the date_default_timezone_set() function. See the PHP manual at http://www.php.net/date_default_timezone_set for more details on this function.

# Creating Timestamps from Date and Time Strings

mktime() is great if you already have the individual numeric values for the date and time you want to store. However, often your PHP script will receive a date or time as a string. For example, if your script works with emails, it may need to handle message dates, which are normally represented in the following format:

```
Date: Mon, 22 Dec 2008 02:30:17 +0000
```

Web server logs tend to use a format such as the following:

```
15/Dec/2008:20:33:30 +1100
```

Alternatively, your script might receive a user-input date along the lines of:

```
15th September 2006 3:12pm
```

Although you can use PHP's powerful string manipulation functions (see Chapter 5) and regular expressions (see Chapter 18) to split such strings into their component parts for feeding to mktime(), PHP provides a useful function called strtotime() to do the hard work for you. strtotime() expects a string representing a date, and attempts to convert the string into a timestamp:

```
$timestamp = strtotime( "15th September 2006 3:12pm" );
```

You can pass in dates and times in practically any human-readable format you like. Here are some examples of valid date/time strings that you can pass to strtotime():

| Date/Time String | Meaning |
|---|---|
| 6/18/99 3:12:28pm | 3:12:28 pm on June 18th, 1999 |
| 15th Feb 04 9:30am | 9:30 am on February 15th, 2004 |
| February 15th 2004, 9:30am | 9:30 am on February 15th, 2004 |