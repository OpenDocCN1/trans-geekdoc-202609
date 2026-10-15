# TIP

Why was 2000 a leap year, but 2100 not? The definition says: If a year is divisible by 4 and is either not divisible by 100 or is divisible by 400, it is a leap year and February has 29 days (this is because the Earth needs approximately 365.25 days to revolve around the sun). If you want to determine whether a given year is a leap year, this function comes in handy:

```
function isLeapYear($year) {
    return ($year % 4 == 0 &&
        ($year % 100 != 0 || $year % 400 == 0));
}
```

Sometimes, you have the task of calculating a date that is relative to the current date, for example, “30 days from now.” Of course, you could put some real work into actually calculating this value, taking into account which day it is, whether it’s a leap year, and whether DST is relevant.

Far easier is the use of an epoche time stamp. Take, for instance, the aforementioned task of finding a date that lies 30 days in the future. One day has 24 hours, one hour has 60 minutes, and one minute has 60 seconds. Therefore, to get the current time stamp (using time() or date('U')), you just need to add 30 * 24 * 60 * 60, and you have the time stamp of the desired date. This time stamp can then be used to set a cookie’s expiry date or just to print out some information about this date.