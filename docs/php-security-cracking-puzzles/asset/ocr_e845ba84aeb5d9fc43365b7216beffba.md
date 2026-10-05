# Listing II.3.29. Outputting pages

```
<?php
// The file's name
$filename = "text.txt";
// Setting the number of records per page
$pnumber = 3;
// Opening the source file for reading
$buffer = file_get_contents($filename);

// Finding all lines using a regular expression
preg_match_all("#(\d+) ([^\n]+)(\
|$) #/u",
$buffer,
$out,
PREG_PATTERN ORDER);

// Forming a temporary array
for($i = 0; $i < count($out[1]); $i++) {
	$temp[] = trim($out[2][$i]);
}

// Checking whether the current page number was passed
if(isset($_GET['page'])) $page = $_GET['page'];
else $page = 1;
// The number of pages
$total = count($temp);
$number = (int)($total/$pnumber);
if((float)($total/$pnumber) - $number != 0) $number++;

$start = ($page - 1) *$pnumber + 1;
$end = $page*$pnumber + 1;
if($end > $total) $end = $total;

// Displaying the contents of the pages
for($i = $start; $i < $end; $i++) {
	echo $temp[$i]."<br>";
}

// Outputting pages
```