```
* DateMath constructor
* If parameters not provided, DateMath uses current time
* <code>
* $dateMath = new DateMath(2003,8,22); // Uses 22nd August 2003
* $dateMath = new DateMath(); // Uses current date and time
* </code>
* @param int year ( e.g. 2003 )
* @param int month ( e.g. 8 for August )
* @param int day of month ( e.g. 22 )
* @param int hours ( e.g. 15 )
* @param int minutes ( e.g. 5 )
* @param int seconds ( e.g. 7 )
*/
function DateMath($y = NULL, $m = NULL, $d = NULL, $h = NULL,
$i = NULL, $s = NULL)
{
$time = time();

$y = is_numeric($y) ? $y : date('Y', $time);
$m = is_numeric($m) ? $m : date('m', $time);
$d = is_numeric($d) ? $d : date('d', $time);
$h = is_numeric($h) ? $h : date('H', $time);
$i = is_numeric($i) ? $i : date('i', $time);
$s = is_numeric($s) ? $s : date('s', $time);
$this->timeStamp = mktime($h, $i, $s, $m, $d, $y);
}

/**
* For setting a Unix timestamp
* @param int a Unix timestamp
* @return void
* @access public
*/
function setTimeStamp($timeStamp)
{
$this->timeStamp = $timeStamp;
}
```

The constructor checks to see whether you've passed any values for a date, the arguments appearing in the order year, month, day, hour, minute and finally second. Any parameter for which you fail to provide a numeric value will assume the current date or time. The constructor then turns this into a timestamp, which will make later calculations easier.

If I want to begin with a timestamp, I can use the setTimeStamp method to provide my own.