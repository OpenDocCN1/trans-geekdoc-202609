| Format String | Description |
|---|---|
| B | Swatch Internet Time — a time-zone-free, decimal time measure. See http://en.wikipedia.org/wiki/Swatch_Internet_Time for details |
| d | Day of the month |
| h | Hours (in 12-hour format) |
| H | Hours (in 24-hour format) |
| i | Minutes |
| I | 1 if DST (Daylight Saving Time) is in effect, 0 otherwise |
| L | 1 if the date is in a leap year, 0 otherwise |
| M | Month number (1–12) |
| s | Seconds |
| t | The number of days in the month (28, 29, 30, or 31) |
| U | The timestamp |
| w | The day of the week, as a number (0 is Sunday) |
| W | The week number within the year (counting from 1) |
| Y | The year as a two-digit number |
| y | The year as a four-digit number |
| z | The day number within the year (0 is January 1) |
| Z | The offset of the computer's time zone from UTC (in seconds) |

As you can see, you can use idate() to retrieve all sorts of useful information from a date. Here's an example:

```
```php
$d = strtotime( "February 18, 2000 7:49am" );

// Displays "The year 2000 is a leap year."
echo "The year " . idate( "Y", $d );
echo " is " . ( idate( "L", $d ) ? "" : "not" ) . " a leap year.<br />";

// Displays "The month in question has 29 days."
echo " The month in question has " . idate( "t", $d ) . " days.<br />";
```
```