Core PHP Programming

```
?>
```

# value jdayofweek(integer julian_day, integer mode)

The jdayofweek function returns an integer or a string, depending on the mode. Modes are listed in Table 11.5.

```
<?\n$jdc = gregoriantojd(1,1,1);
print(jdayofweek($jdc, 1));
?>
```

Table 11.5. Calendar Day Modes

| Mode | Description |
|---|---|
| 0 | Return the day of the week as a number from 0 to 6, zero being Sunday. |
| 1 | Return the day of the week as a name using the English name from the Gregorian calendar. |
| 2 | Returns the abbreviated name of the day of the week using the English name from the Gregorian calendar. |

# string jdayname(integer julian_day, integer mode)

The jdayname function returns the name of the month for a particular day. The mode argument specifies which calendar to draw month names from. Modes are listed in Table 11.6.

```
<?\n$jdc = gregoriantojd(1,1,1800);
print(jdayname($jdc, 0) "<BR\n\";
print(jdayname($jdc, 1) "<BR\n\";
print(jdayname($jdc, 2) "<BR\n\";
print(jdayname($jdc, 3) "<BR\n\";
print(jdayname($jdc, 4) "<BR\n\";
print(jdayname($jdc, 5) "<BR\n\";
?>
```

# string jdtofrench(integer julian_day)

The jdtofrench function returns the date on the French Republican calendar for a Julian Day Count.

```
<?\njjdc = gregoriantojd(1,1,1800);
```