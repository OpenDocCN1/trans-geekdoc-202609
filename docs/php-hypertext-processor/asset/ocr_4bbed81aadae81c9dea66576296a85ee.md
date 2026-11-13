It will produce the following result:

```
seconds = 6
minutes = 15
hours = 11
mday = 19
wday = 2
mon = 7
year = 2016
yday = 200
weekday = Tuesday
month = July
0 = 1468926906
Today's date: 19/7/2016
```

# # Converting a Time Stamp with date()

The **date()** function returns a formatted string representing a date. You can exercise an enormous amount of control over the format that date() returns with a string argument that you must pass to it.

```
date(format,timestamp)
```

The date() optionally accepts a time stamp if omitted, then current date and time will be used. Any other data you include in the format string passed to date() will be included in the return value.

The following table lists the codes that a format string can contain:

| Format | Description | Example |
|---|---|---|
| a | 'am' or 'pm' lowercase | pm |
| A | 'AM' or 'PM' uppercase | PM |
| d | Day of month, a number with leading zeroes | 20 |
| D | Day of week (three letters) | Thu |
| F | Month name | January |
| h | Hour (12-hour format - leading zeroes) | 12 |
| H | Hour (24-hour format - leading zeroes) | 22 |
| g | Hour (12-hour format - no leading zeroes) | 12 |
| G | Hour (24-hour format - no leading zeroes) | 22 |
| i | Minutes ( 0 - 59 ) | 23 |