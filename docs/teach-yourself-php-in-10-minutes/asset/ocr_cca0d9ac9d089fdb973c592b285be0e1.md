**Daylight Saving Time** If you are only concerned with the date part of a timestamp, the first three arguments to `mktime` only matter if they are close to midnight at a time of the year when daylight saving time is a factor.

For instance, when the clocks are moved back one hour, that day is only 23 hours long. Adding 86,400 seconds to a timestamp that represents midnight on that day will actually move the day part of the timestamp forward two days. You can use midday instead of midnight as the time element to avoid these issues.

**Greenwich Mean Time** To obtain timestamp values that are always relative to GMTThe time in London when there is no daylight saving time adjustmentyou use `gmmktime` instead of `mktime` .

The `mktime` function is forgiving if you supply it with nonsense arguments, such as a day of the month that doesn't exist. For instance, if you try to calculate a timestamp for February 29 in a non-leap year, the value returned will actually represent March 1, as the following statement confirms:

```
echo date("d/m/Y", mktime(12, 0, 0, 2, 29, 2003));
```

You can exploit this behavior as a way of performing date and time arithmetic. Consider the following example, which calculates and displays the date and time 37 hours after midday on December 30, 2001:

```
$time = mktime(12 + 37, 0, 0, 12, 30, 2001);
echo date("d/m/Y H:i:s", $time);
```

By simply adding a constant to one of the arguments in `mktime` , you can shift the timestamp value returned by that amount. The date and time display as follows:

```
01/01/2002 01:00:00
```

The value returned in this example has correctly shifted the day, month, year, and hour values, taking into account the number of days in December and that December is the last month of the year.