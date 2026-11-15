As an alternative to real dates, also references of the following type are possible:

```
$date = "last Sunday";
```

This refers, for example, to the previous Sunday.

> > **Note**
> >
> > Fortunately, there is a system: The syntax of the possible date specifications in `strtotime()` follows the GNU guidelines. You can find these at `http://s-rs.co/v602213`. References to previous or upcoming weekdays are summarized there—for example, under **7.7 Relative Items in Date Strings**.

# # Validity of Data

The Gregorian calendar,<sup>1</sup> which we use today, is often a little complicated. The concept of leap years in particular often causes some confusion. With `checkdate(month, day, year)`, PHP offers a check function. It requires all three parameters and then checks whether the date is a correct Gregorian date.

The function knows three conditions to return `true` for a valid date:

+   - The year must be between 1 and 32767. Years before the birth of Christ cannot be calculated. Of course, this method does not make much sense for dates before the introduction of the Gregorian calendar, as it also calculates a leap year for this time.
+   - The month must be between 1 and 12.
+   - The day must have existed in the month in the year.

This function does not fail with 1900 or 2000. The year 1900 is not a leap year, as 1900 is divisible by 100—but 2000 is, as it is divisible by 400.<sup>2</sup>

```
<?php
$day = 29;
$month = 2;
$year = 2000;
if (checkdate($month, $day, $year)) {
echo "Valid!";
```

1 Our calendar was originally created by Gaius Julius Caesar, the general and consul who sealed the end of the Roman Republic. However, the Julian calendar named after him had some weaknesses, which were finally addressed in the Gregorian calendar by Pope Gregory XIII in 1582 with the support of the astronomer Lilius.

2 The Julian calendar had a year length of 365.25 days (normally 365; 366 every four years). As this was not entirely astronomically correct, there were shifts. Pope Gregory XIII dropped the days between October 5, 1582, and October 14, 1582 (inclusive), and then introduced the following rule: All years divisible by 100 are not leap years. However, since this also had to be corrected a little, years divisible by 400 are leap years after all.