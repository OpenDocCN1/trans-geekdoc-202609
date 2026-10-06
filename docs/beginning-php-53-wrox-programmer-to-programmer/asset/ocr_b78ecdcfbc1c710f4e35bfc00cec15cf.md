# Appendix A: Solutions to Exercises

# # Chapter 16

# ## Exercise 1 Solution

To write a function that calculates the number of weekdays in a given month, you can use the following approach:

+   1. Calculate the total number of days in the month.
2. Loop through each day and test whether it is a weekday. If so, increment the counter.
3. Return the counter value.

Here is a solution:

```
<!DOCTYPE html PUBLIC "//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>
<title>Number of weekdays in a month</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Number of weekdays in a month</h1>
<?php

function weekdaysInMonth($year, $month) {
$date = mktime(0, 0, 0, $month, 1, $year);
$daysInMonth = date("t", $date);
$weekdays = 0;

for ($d = 1; $d <= $daysInMonth; $d++) {
$date = mktime(0, 0, 0, $month, $d, $year);
$dayOfWeek = date("w", $date);
if ($dayOfWeek != 0 && $dayOfWeek == 6) $weekdays++;
}

return $weekdays;
}

$weekdays = weekdaysInMonth(1997, 3);
echo "<p>March 1997 contained $weekdays weekdays.</p>";
?>
</body>
</html>
```

705