| Symbol | Description |
|---|---|
| T | Time zone of server (for example, CET) |
| U | Epoch value (seconds since January 1st, 1970, midnight GMT) |
| w | Day of week (from 0 [Sunday] to 6 [Saturday]) |
| W | Week number (according to ISO 8601, from 1 to 53) |
| y | Year (2 digits) |
| Y | Year (4 digits) |
| z | Day of year (from 0 to 365) |
| Z | Time zone difference to UTC (in seconds) |

**NOTE:** Almost all the formatting symbols shown in Table 3.1 are available since PHP 3. There are only two exceptions: Using w for determining the week number of a date was added in PHP 4.1.0, and using c for retrieving the ISO 8601 representation for a date (for example, 2006-06-30T12:34:56+01:00) came in PHP 5.

The function `date()` is very powerful and offers a broad range of ways to use it. However, especially if you have localized content, you need some good phrases. In this chapter, you will find many of them.

The newer way of date and time handling in PHP uses, among other classes, DateTime. We use this class and some related ones in selected phrases in this chapter, as well.

PHP's date and time features have their own section in the PHP manual. You can find more information about DateTime and friends at http://php.net/datetime.