solution, we’ll make a new version of the previous example, but this time, below the table for the month, we’ll display another table for the day, containing hours. We’ll add the following code below that used to generate the monthly calendar.

First, create a new Day object, using whatever the current values are from the $_GET variables. We also need to initialize the $_GET variable for an hour (if it hasn't already been set), because we want the current hour, or an hour the user has selected, to appear highlighted in the schedule.

```
```php
// Create a new day
$day = new Day($_GET['y'], $_GET['m'], $_GET['d']);

// Initialize the current hour
if (!isset($_GET['h'])) $_GET['h'] = date('H');

$sHours = array(new Hour($_GET['y'], $_GET['m'], $_GET['d'],
    $_GET['h']));

// Build the hour list for that day
$day->build($sHours);

$calendar .= "<br />\n";
$calendar .= "<table class=\"cal\" width=\"450\">\n";
$calendar .= "<caption>Your schedule for "
    . date('l', $day->thisDay(true)) .
    "</caption>\n";
```
```

Because this will be an office application, we limit the hours displayed to office hours. You've effectively seen the rest of the methods here previously.

```
```php
$alt = '';

// Loop through the hours
while ($hour = $day->fetch()) {
    // Set a range for the hours; only between 8am and 6pm
    if ($hour->thisHour() < 8 || $hour->thisHour() > 18) {
        continue;
    }

    // For alternating row colors
    $alt = $alt == "cal_row" ? "cal_row_alt" : "cal_row";

    // If it's the current day, highlight it
```
```