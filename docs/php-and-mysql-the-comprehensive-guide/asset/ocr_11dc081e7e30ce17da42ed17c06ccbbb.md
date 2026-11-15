elements of the date are output: d stands for the day (preceded by 0), m for the month (as a number preceded by 0), and Y for the four-digit year. Figure 9.8 shows the output.

```
<?php
$today = date("m/d/Y");
echo $today;
?>
```

# Listing 9.12 "date()" ("date.php")

![](bbox=[0.14, 0.255, 0.655, 0.365])

# Figure 9.8 The Current Date, Clearly Formatted

The slashes between the individual date elements are simply output by date(). If you want to output one of the symbols that actually corresponds to a date element, then you must escape it with a backslash (\), also known as an escape character. But be careful: the format

```
$today = date("\D\a\t\e: d.m.Y");
```

only outputs Da : 27.12.2024 as \t is a tabulator and \e is escape in strings. You must do this instead:

```
$today = date("\D\a\t\e\\t\e: d.m.Y");
```

So date() is not suitable for longer texts. Here you can either use DateTime, several date() calls, or the associative array of getdate().

Table 9.2 offers a list of all available symbols with the corresponding explanation.

| Icon | Examples | Description |
| :--- | :--- | :--- |
| a | am, pm | _am_ and _pm_ or, in the full Latin, _ante meridiem_ and _post meridiem_. |
| A | AM, PM | _AM_ and _PM_ in capital letters. |
| B | 045 | _Swatch Internet Time_, in which a day consists of 1,000 _beats_ from 000 to 999.
000 is midnight at the Swiss headquarters of Swatch. The aim of this system of time — apart from marketing — is to create a standardized time system for chats, appointments, and so on. |

# Table 9.2 The Format Specifications for "date()"