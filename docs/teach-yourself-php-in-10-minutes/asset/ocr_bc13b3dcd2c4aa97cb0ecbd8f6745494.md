# # Working with Timestamps

There are times when using your own date format is beneficial, but in most cases a timestamp is the best choice. Let's look at how PHP interacts with the timestamp date format.

# ## Formatting Dates

In Lesson 1, "Getting to Know PHP," you used the date function to display the current date by passing a format string as the argument, such as in the following example:

```
echo date("j F Y H:i:s");
```

The date displayed looks something like this:

```
12 November 2004 10:23:55
```

The optional second argument to date is a timestamp value of the date that you want to display. For example, to display the date when a timestamp first requires a 10-digit number, you could use the following:

```
echo date("j F Y H:i:s", 1000000000);
```

The list of format codes for the date function is shown in Table 9.1 .

# ### Table 9.1. Format Codes for date

| Code | Description |
| --- | --- |
| a | Lowercase am or pm |
| A | Uppercase AM or PM |
| d | Two-digit day of month, 0131 |
| D | Three-letter day name, MonSun |
| F | Full month name, JanuaryDecember |
| g | 12-hour hour with no leading zero, 112 |