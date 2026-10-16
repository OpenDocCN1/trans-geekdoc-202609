# Formatting DateTime Objects

The new date- and time-handling approach introduced in PHP 5.2 uses the DateTime class to represent a date value. There are several ways to create a class instance, but probably the most convenient one is to provide a date in a given format and tell PHP in turn which format you have been using. The formatting symbols are those from Table 3.1. Here is an example:

```
$d = DateTime::createFromFormat('d.m.Y', '21.11.2012');
```

The variable $d now holds a date that represents the 21st of November, 2012.

After we have acquired such a date and worked with it (see some of the other phrases in this chapter), we can format the date as a string, using the same formatting characters as before, plus the format() method:

```
echo $d->format('Y-m-d');
```

**NOTE:** Apart from the object-oriented programming (OOP) application programming interface (API), PHP's DateTime features are also available using a procedural interface. The preceding lines of code could also look like this— although we prefer the OOP syntax in this chapter:

```
$d = date_create_from_format('d.m.Y', '10.11.2012');
echo date_format($d, 'Y-m-d');
```

# Automatically Localizing Dates

```
<?php
setlocale(LC_TIME, 'en_US');
echo strftime('In (American) English: %c<br />');
setlocale(LC_TIME, 'en_GB');
```