```
<?php
// Include DateMath class
require_once 'DateTime/DateMath.php';

// Build an array for the next ten years
$thisyear = date('Y');
$years = range($thisyear, $thisyear + 10);

// Find the leap years
foreach ($years as $year) {
    $dateMath = new DateMath($year, 1, 1, 0, 0, 0);
    if (!$dateMath->isLeapYear()) {
        echo $year . ' is not a leap year<br/>';
    } else {
        echo $year . ' is a leap year!<br/>';
    }
}
?>

```

This identifies which of the next ten years are and are not leap years:

2003 is not a leap year
2004 is a leap year!
2005 is not a leap year
2006 is not a leap year
2007 is not a leap year
2008 is a leap year!
2009 is not a leap year
2010 is not a leap year
2011 is not a leap year
2012 is a leap year!
2013 is not a leap year

# Day of the Year

Another feature of date tells us what day of the year it is:

```
/**
 * Returns the day of the year
 * @return int numeric day of year e.g. 81
 * @access public
 */
function dayOfYear()
```