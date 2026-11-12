![](bbox=[0.133, 0.18, 0.222, 0.255])

This code puts the following string inside $now_string:

```
The current time is 10:30.
```

The percent symbol is the special character that tells strftime to look at the following character to figure out a replacement. But what if you want a percent character to appear in the string? Then use %%, like so:

```
$now_string = strftime("% % % % %H:%M % % % %", @now);
```

This yields the following output:

```
% % % 10:30 % % %
```

Here is a list of the more useful characters you can use:

+   * %a: Weekday name in three letters.
+   * %A: Full weekday name.
+   * %b: Month name in three letters.
+   * %B: Full month name.
+   * %c: A general format for the entire time. (Try it.)
+   * %C: The century number. I'm not sure why you'd use this, but it's available if you need it.
+   * %d: The number of the day in the month, ranging from 01 to 31. (Single digits start with a leading zero.)
+   * %e: The number of the day in the month, ranging from 1 to 31. (Single digits have no leading zero.)
+   * %H: The hour in a 24-hour range, with a leading zero on single digits (00 to 23).
+   * %I: The hour in a 12-hour range, with a leading zero on single digits (00 to 11).
+   * %j: The number of the day within the year (range 001 to 366).
+   * %k: The hour in a 24-hour range, without a leading zero on single digits (0 to 23).
+   * %l: The hour in a 12-hour range, without a leading zero on the single digits (0 to 11).
+   * %m: The number of the month (0 to 11). Remember that January is 0, not 1.