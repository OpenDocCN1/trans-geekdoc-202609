# # Working with Dates and Times

Web applications frequently need to deal with dates and times. For example, an application might need to track page access times, handle a user-entered date (such as a date of birth) from a Web form, or format a date field returned from a MySQL database in a human-friendly way so that it can be displayed in a Web page.

Though dates and times may, on the surface, seem like fairly simple concepts to work with, in fact they can be quite tricky for computers to handle. Issues such as leap years, time zones, and the fact that the number of days in a month is variable can cause all sorts of problems when it comes to storing, retrieving, comparing, adding, and subtracting dates.

To this end, PHP gives you a few date — and time — related functions to make your life easier.

# # Understanding Timestamps

Most computers store dates and times as UNIX timestamps, or simply timestamps. A _timestamp_ is an integer that holds the number of seconds between midnight UTC on January 1, 1970 and the date and time to be stored (also in UTC). For example, the date and time “February 14, 2007 16:48:12” in the GMT time zone is represented by the UNIX timestamp `1171471692`, because February 14, 2007 16:48:12 is exactly 1,171,471,692 seconds after midnight on January 1, 1970.

> _UTC stands for Universal Time Coordinated. For most purposes you can consider it to be equivalent to Greenwich Mean Time (GMT)._

You’re probably wondering why computers store dates and times in such a strange format. In fact, timestamps are a very useful way of representing dates and times. First of all, because a timestamp is simply an integer, it’s easy for a computer to store it. Secondly, it’s easy to manipulate dates and times when they’re just integers. For example, to add one day to a timestamp, you just add the number of seconds in a day (which happens to be 86,400 seconds) to the value. It doesn’t matter if the timestamp represents a date at the end of a month or a year; you can still add one day just by adding 86,400 seconds to the timestamp value.

The majority of PHP date and time functions work with timestamps — if not explicitly, then certainly internally.

# # Getting the Current Date and Time

Computers — including Web servers, as well as your own PC — keep track of the current date and time using a built-in clock. You can access this clock’s value with the PHP `time()` function, which simply returns the current date and time as a timestamp:

```
```php
echo time(); // Displays e.g. "1229509316"
```
```

Although not particularly useful in its own right, you can use `time()` in combination with other PHP functions to display the current time and compare dates and times against the current date and time, among other things.