
Moreover, handle all the errors properly and direct all trace messages into system log file so that if any problem occurs, then it will be logged into system log file and you will be able to debug that problem.

## 25. PHP – Date and Time

Dates are so much part of everyday life that it becomes easy to work with them without thinking. PHP also provides powerful tools for date arithmetic that make manipulating dates easy.

### Getting the Time Stamp with time()

PHP's time() function gives you all the information that you need about the current date and time. It requires no arguments but returns an integer.

The integer returned by time() represents the number of seconds elapsed since midnight GMT on January 1, 1970. This moment is known as the UNIX epoch, and the number of seconds that have elapsed since then is referred to as a time stamp.

```php
<?php
print time();
?>
```

It will produce the following result:

![](img/b9c80e155ac304a53696823920b08082_137_0.png)

This is something difficult to understand. But PHP offers excellent tools to convert a time stamp into a form that humans are comfortable with.

### Converting a Time Stamp with getdate()

The function getdate() optionally accepts a timestamp and returns an associative array containing information about the date. If you omit the time stamp, it works with the current time stamp as returned by time().

The following table lists the elements contained in the array returned by getdate().

| Key | Description | Example |
|---|---|---|
| seconds | Seconds past the minutes (0-59) | 20 |
| minutes | Minutes past the hour (0 - 59) | 29 |
| hours | Hours of the day (0 - 23) | 22 |
| mday | Day of the month (1 - 31) | 11 |
| wday | Day of the week (0 - 6) | 4 |
| mon | Month of the year (1 - 12) | 7 |
| year | Year (4 digits) | 1997 |
| yday | Day of year (0 - 365) | 19 |
| weekday | Day of the week | Thursday |
| month | Month of the year | January |
| 0 | Timestamp | 948370048 |

Now you have complete control over date and time. You can format this date and time in whatever format you want.

### Example

Try out the following example.

```php
<?php
$date_array = getdate();
foreach ( $date_array as $key => $val )
{
   print "$key = $val<br />";
}

$formatted_date = "Today's date: ";
$formatted_date .= $date_array[mday] . "/";
$formatted_date .= $date_array[mon] . "/";
$formatted_date .= $date_array[year];

print $formatted_date;
?>
```

It will produce the following result:

```
seconds = 6
minutes = 15
hours = 11
mday = 19
wday = 2
mon = 7
year = 2016
yday = 200
weekday = Tuesday
month = July
0 = 1468926906
Today's date: 19/7/2016
```

### Converting a Time Stamp with date()

The **date()** function returns a formatted string representing a date. You can exercise an enormous amount of control over the format that date() returns with a string argument that you must pass to it.

```
date(format,timestamp)
```

The date() optionally accepts a time stamp if omitted, then current date and time will be used. Any other data you include in the format string passed to date() will be included in the return value.

The following table lists the codes that a format string can contain:

| Format | Description | Example |
|---|---|---|
| a | 'am' or 'pm' lowercase | pm |
| A | 'AM' or 'PM' uppercase | PM |
| d | Day of month, a number with leading zeroes | 20 |
| D | Day of week (three letters) | Thu |
| F | Month name | January |
| h | Hour (12-hour format - leading zeroes) | 12 |
| H | Hour (24-hour format - leading zeroes) | 22 |
| g | Hour (12-hour format - no leading zeroes) | 12 |
| G | Hour (24-hour format - no leading zeroes) | 22 |
| i | Minutes (0 - 59) | 23 |
| j | Day of the month (no leading zeroes) | 20 |
| l (Lower 'L') | Day of the week | Thursday |
| L | Leap year ('1' for yes, '0' for no) | 1 |
| m | Month of year (number - leading zeroes) | 1 |
| M | Month of year (three letters) | Jan |
| r | The RFC 2822 formatted date | Thu, 21 Dec 2000 16:01:07 +0200 |
| n | Month of year (number - no leading zeroes) | 2 |
| s | Seconds of hour | 20 |
| U | Time stamp | 948372444 |
| y | Year (two digits) | 06 |
| Y | Year (four digits) | 2006 |
| z | Day of year (0 - 365) | 206 |
| Z | Offset in seconds from GMT | +5 |

### Example

Try out the following example.

```php
<?php
print date("m/d/y G.i:s<br>", time());
print "Today is ";
print date("j of F Y, \\a\\t g.i a", time());
?>
```

It will produce following result:

07/19/16 11.15:06Today is 19 of July 2016, at 11.15 am

Hope you have a good understanding of how to format date and time according to your requirement. For your reference a complete list of all the date and time functions is given in PHP Date & Time Functions.

## 26. PHP – PHP and MySQL

PHP will work with virtually all database software, including Oracle and Sybase but most commonly used is freely available MySQL database.

### What you should already have?

- You have gone through MySQL tutorial to understand MySQL Basics.
- Downloaded and installed a latest version of MySQL.
- Created database user **guest** with password **guest123**.
- If you have not created a database, then you would need root user and its password to create a database.

We have divided this chapter in the following sections:

- **Connecting to MySQL database** - Learn how to use PHP to open and close a MySQL database connection.
- **Create MySQL Database Using PHP** - This part explains how to create MySQL database and tables using PHP.
- **Delete MySQL Database Using PHP** - This part explains how to delete MySQL database and tables using PHP.
- **Insert Data To MySQL Database** - Once you have created your database and tables, then you would like to insert your data into created tables. This session will take you through real example on data insert.
- **Retrieving Data From MySQL Database** - Learn how to fetch records from MySQL database using PHP.
- **Using Paging through PHP** - This one explains how to show your query result into multiple pages and how to create the navigation link.
- **Updating Data Into MySQL Database** - This part explains how to update existing records into MySQL database using PHP.
- **Deleting Data From MySQL Database** - This part explains how to delete or purge existing records from MySQL database using PHP.
- **Using PHP To Backup MySQL Database** - Learn different ways to take backup of your MySQL database for safety purpose.

### Connecting to MySQL Database

### Opening a Database Connection

PHP provides **mysqli_connect** function to open a database connection. This function takes five parameters and returns a MySQL link identifier on success, or FALSE on failure.

### Syntax

```
connection mysqli_connect(server,user,passwd,new_link,client_flag);
```

| Sr.No | Parameter & Description |
| :--- | :--- |
| 1 | **server** Optional – The host name running database server. If not specified, then default value is **localhost:3306**. |
| 2 | **user** Optional – The username accessing the database. If not specified, then default is the name of the user that owns the server process. |
| 3 | **passwd** Optional – The password of the user accessing the database. If not specified then default is an empty password. |
| 4 | **new_link** Optional – If a second call is made to mysqli_connect() with the same arguments, no new connection will be established; instead, the identifier of the already opened connection will be returned. |
| 5 | **client_flags** Optional – A combination of the following constants – **MYSQL_CLIENT_SSL** – Use SSL encryption; **MYSQL_CLIENT_COMPRESS** – Use compression protocol |

- **MYSQL_CLIENT_IGNORE_SPACE** – Allow space after function names
- **MYSQL_CLIENT_INTERACTIVE** – Allow interactive timeout seconds of inactivity before closing the connection

**NOTE** – You can specify server, user, passwd in **php.ini** file instead of using them again and again in your every PHP scripts. Check php.ini file configuration.

### Closing Database Connection

Its simplest function mysqli_close PHP provides to close a database connection. This function takes connection resource returned by mysqli_connect function. It returns TRUE on success or FALSE on failure.

### Syntax

```
bool mysqli_close ( resource $link_identifier );
```

If a resource is not specified, then the last opened database is closed.

### Example

Try the following example to open and close a database connection –

```php
<?php
$dbhost = 'localhost:3036';
$dbuser = 'guest';
$dbpass = 'guest123';
$conn = mysqli_connect($dbhost, $dbuser, $dbpass);
if(! $conn ) {
  die('Could not connect: ' . mysqli_error());
}
echo 'Connected successfully';
mysqli_close($conn);
?>
```

### Create MySQL Database Using PHP

### Creating a Database
