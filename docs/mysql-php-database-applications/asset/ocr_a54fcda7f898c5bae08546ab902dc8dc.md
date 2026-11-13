| Indicator | Meaning |
| :--- | :--- |
| l (lowercase l) | Day of the week, textual, long; for example, Friday |
| L | Boolean for whether it is a leap year; 0 or 1 |
| m | Month; 01 to 12 |
| M | Month, textual, three letters; for example, Jan |
| n | Month without leading zeros; 1 to 12 |
| s | Seconds; 00 to 59 |
| S | English ordinal suffix, textual, two characters; for example, th, nd |
| t | Number of days in the given month; 28 to 31 |
| T | Time-zone setting of this machine; for example, MDT |
| U | Seconds since the epoch (midnight, January 1, 1970) |
| w | Day of the week, numeric; 0 (Sunday) to 6 (Saturday) |
| Y | Year, four digits; for example, 1999 |
| y | Year, two digits; for example, 99 |
| z | Day of the year; 0 to 365 |
| Z | Time-zone offset in seconds; -43200 to 43200 |

For example, if you want to print the date in the format, June 5, 2003 4:22 pm, this would do the trick:

```
echo date("F d, Y g:i a");
```

MKTIME() This function is most useful for calculating valid dates.

```
int mktime (int hour, int minute, int second, int month, int day,
int year [, int is_dst])
```

For example, say you have a form that collects a date – maybe the current month,
day, and year. You want to calculate and set a due date exactly 30 days from the
date submitted.