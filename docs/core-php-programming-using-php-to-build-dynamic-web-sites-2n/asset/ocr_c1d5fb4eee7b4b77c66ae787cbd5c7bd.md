# Core PHP Programming

The gmdate function operates identically to the date function except that, rather than return the time for the local time zone, Greenwich Mean is returned.

```
<?php
print("Local: ");
print (date("h:i A 1"));
print (date("F ds, Y"));
print("<BR>\n");

print("GMT: ");
print (gmdate("h:i A 1"));
print (gmdate("F ds, Y"));
print("<BR>\n");
?>
```

# string strftime(string format, integer timestamp)

The strftime function operates identically to strftime except that the timestamp is translated into Greenwich Mean Time. The same format codes defined in Table 11.4 are used in the format argument.

```
<?php
print(strftime("%%A, %%c", mtime(0, 0, 0, 1, 1970)));
?>
```

Table 11.4. Codes Used by strftime
| Code | Description |
| %%a Abbreviated weekday name |
| %%A Full weekday name |
| %%b Abbreviated month name |
|%%B Full month name |
|%%c Preferred date and time representation |
|%%d Two-digit day of the month with zero-fill |
|%%H Hour on the 24-hour clock with zero-fill |
|%%I Hour on the 12-hour clock |
|%%j Three-digit day of the year with zero-fill |
|%%m Month number from 1 to 12 |
|%%M Minutes |
|%%p Equivalent representation of am or pm |
|%%S Seconds |
|%%U Week number with week starting with the first Sunday of the year |
|%%W Week number with week starting with the first Monday of the year |

IT-SC book 310