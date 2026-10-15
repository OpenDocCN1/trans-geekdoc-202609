“January”, or “Janvier” rather than “01”), two-digit years (does “12” refer to 2012 or 1912?), and ambiguous ordering of months and days (does “12” refer to the twelfth day of the month or December?)

If we know the way the data is stored, we can use {lubridate} functions to process the data into YYYY-MM-DD. These three very different date formats can be transformed into a consistent format:

```
ymd("1973-10-22")
```

## [1] "1973-10-22"

```
mdy("October 22nd, 1973")
```

## [1] "1973-10-22"

```
dmy("22-Oct-1973")
```

## [1] "1973-10-22"

A third manner in which dates can be stored is with a truncated representation. For example, total sales for the entire month might be recorded as a single value associated with “Jan 2017” or “2017-01”, or a quarterly measurement might be “2017-Q1”.

```
# month
ym("1973-10")
```

## [1] "1973-10-01"

```
my("Oct 1973")
```

## [1] "1973-10-01"

```
# quarter
yq("1973-Q1")
```