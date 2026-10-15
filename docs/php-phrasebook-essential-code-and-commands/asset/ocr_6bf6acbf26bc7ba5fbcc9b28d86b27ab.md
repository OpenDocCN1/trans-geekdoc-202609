# Formatting a Specific Date

If you want to use another date, mktime() comes into play. This function converts a date provided by year, month, day, hour, minute, and second into an epoch value. Probably the strangest thing about this function is the order in which these parameters are passed:

+   1. Hour
+   2. Minute
+   3. Second
+   4. Month
+   5. Day
+   6. Year

You can also provide an optional seventh parameter, regardless of whether it is Daylight Savings Time (DST). This is relevant close to the change from or to DST because that does not happen at the same time over the world.

The preceding code calculates the time stamp for noon on the first day of this millennium. Because there was no year 0, this was January 1st, 2001.

> If you love collecting useless facts: On September 9, 2001, at precisely 3:46:40 a.m., the time stamp was 1,000,000,000. Therefore, mktime(3, 46, 40, 9, 9, 2001) returns 100000000000 (if your time zone is Central Europe).