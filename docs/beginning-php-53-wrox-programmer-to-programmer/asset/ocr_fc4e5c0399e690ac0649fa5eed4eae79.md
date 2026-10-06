# Chapter 16: PHP and the Outside World

If, when using any of PHP's date-related functions, you get an error message telling you that it is not safe to rely on the system's time zone settings, you need to configure PHP's time zone. See the "Setting Your Time Zone" section in Chapter 2 for instructions.

# Creating Your Own Timestamps

Although `time()` is useful for getting the current time, you often want to work with other dates and times. You can use various PHP functions to create timestamps for storing dates and times. The three that you're likely to use most are `time()`, `gmtime()`, and `strtotime()`.

# Creating Timestamps from Date and Time Values

The `mktime()` function returns a timestamp based on six time/date arguments, as follows:

+   - Hour (0–23)
- Minute (0–59)
- Second (0–59)
- Month (1–12)
- Day of the month (1–31)
- Year (1901–2038)

For example, the following code displays the timestamp corresponding to 2:32:12 pm on January 6, 1972:

```
echo mktime( 14, 32, 12, 1, 6, 1972 );
```

You can leave out as many arguments as you like, and the value corresponding to the current time will be used instead. For example, if the current date is December 22, 2008, the following code code displays the timestamp representing 10 am on December 22, 2008:

```
echo mktime( 10, 0, 0 );
```

If you omit all arguments, `mktime()` returns the current date and time, just like `time()`.

Incidentally, you can pass in arguments that are outside the allowed ranges, and `mktime()` adjusts the values accordingly. Passing in a value of 3 for the month and 32 for the day causes `mktime()` to return a timestamp representing April 1.

# Creating Timestamps from GMT Date and Time Values

`mktime()` assumes that the arguments you pass are in your computer's time zone — it converts the supplied time to UTC so that it can be returned as a timestamp. However, sometimes it's useful to be able to store a date and time that's already in the GMT time zone. For example, many HTTP headers and other TCP/IP protocols work with dates and times that are always in GMT.

473