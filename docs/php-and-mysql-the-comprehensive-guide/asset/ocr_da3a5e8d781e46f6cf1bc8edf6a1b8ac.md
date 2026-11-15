Just as with date(), you can use a timestamp with idate() or omit it.

# GMT

GMT stands for Greenwich Mean Time. Dates in other time zones always work with a time difference. Some of the date functions are therefore also available specifically for working with GMT without a time offset. These functions are important if you want to handle the time difference manually. The following are available:

+   - gmkmktime() generates a timestamp.
+   - gmdate() returns the date and allows a format string.
+   - gmstrftime() formats with the format string that comes from C.

The parameters and results of the functions are the same as the GMT-independent originals.

# 9.2.6 Countdown: Calculate with Dates

Try to calculate how much time has passed between two dates. Okay, New Year’s Day to New Year’s Eve is too easy—but as soon as the span goes over several years, you have to include leap years, or it comes down to seconds, our mathematical cerebellum fails.

To be able to calculate with data via PHP, you need a base. This base is the timestamp from 1.1.1970 at 00:00:00. You can use it to simply subtract dates from or add dates to each other. The result is always the difference in seconds. You can then convert these seconds into any desired unit.

The following example shows a form that subtracts the current date from a date entered by a user. It then displays the result in whole days. You can see the form and the result in Figure 9.15 and Figure 9.16.

```
<?php
if (isset($_POST["submit"])) {
	$date1 = strrtotime($_POST["input"]);
	$date2 = time();
	$result = $date1 - $date2;
	if ($result > 0) {
		echo "Still ". floor($result / (60 * 60 * 24)) . " days ";
		echo "until ". date('m/d/Y', $date1);
	} else {
		echo "Your date is not in the future!";
	}
}
?>
```