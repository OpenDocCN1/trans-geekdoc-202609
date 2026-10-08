# Getting the Date and Time from PHP

For example,

```
checkdate(2, 29, 2008)
```

returns true, whereas

```
checkdate(2, 29, 2007)
```

does not.

# Formatting Timestamps

You can format a timestamp according to the system's locale (the web server's local settings) using the strftime function. This function has the following prototype:

```
string strftime ( string $format, int $timestamp )
```

The $format parameter is the formatting code that defines how the timestamp will be displayed. The timestamp parameter is the timestamp that you pass to the function. The parameter is optional. If no timestamp is passed as a parameter, the local system timestamp (at the time the script is run) is. For instance, the following code

```
<php
echo strftime('%a<br />');
echo strftime('%x<br />');
echo strftime('%c<br />');
echo strftime('%Y<br />');
?
```

displays the current system timestamp in four different formats. This code will produce output similar to the following:

+   Tuesday
02/17/15
Tue Feb 17 02:10:19 2015
2015

The complete list of formatting codes for strftime() is listed in Table 19.3.

Table 19.3 Formatting Codes for strftime()

| Code | Description |
|---|---|
| %a | Day of week (abbreviated). The range is Sun through Sat. |
| %A | Day of week. The range is Sunday through Saturday. |
| %b or %B | Month (abbreviated). The range is Jan through Dec. |
| %B | Month. The range is January through December. |
| %c | Date and time in standard format. Example: Tue Feb 17 02:13:04 2015. |