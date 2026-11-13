# # Date Formats

PHP does not have a native date data type, so in order to store date values in a script, you must first decide on the best way to store these values.

# ## Do-It-Yourself Date Formats

Although you often see dates written in a structured format, such as 05/03/1974 or 2001-12-31, these are not ideal formats for working with date values. However, the latter of these two is more suitable than the first because the order of its components is from most significant (the year) to the least significant (the day), so values can be compared using the usual PHP operators.

As a string, 2002-01-01 is greater than 2001-12-31 , but because comparisons are performed more efficiently on numbers than on strings, this could be written better as just 20020201 , where the format is YYYYMMDD . This format can be extended to include a time portionagain, with the most significant elements firstas YYYYMMDDHHMMSS , for example.

However, date arithmetic with this format is nearly impossible. While you can add one to 20040501 , for instance, and find the next day in that month, simply adding one to 20030531 would result in a nonsense date of May 32.

# ## Unix Timestamp Format

The Unix timestamp format is an integer representation of a date and time. It is a value that counts the number of seconds since midnight on January 1, 1970.

**The Unix Epoch** A timestamp with integer value zero represents precisely midnight, Greenwich Mean Time (GMT), on January 1, 1970. This date is known as the *Unix Epoch* .

Right now, we have a 10-digit date and time timestamp. To find the current timestamp, you use the time function:

```
`echo time();`
```

The Unix timestamp format is useful because it is very easy to perform calculations on because you know that the value always represents a number of seconds. For example, you can just add 3,600 to a timestamp value to increase the time by one hour or add 86,400 to add one daybecause there are 3,600 seconds in an hour and 86,400 seconds in a day.