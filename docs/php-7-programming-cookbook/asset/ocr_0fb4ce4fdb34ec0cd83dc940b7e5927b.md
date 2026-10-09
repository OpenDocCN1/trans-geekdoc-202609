```
$monthType = self::MONTH_3;
$across = self::DEFAULT_ACROSS)
{
    if (!$this->yearArray) $this->buildYearArray($year,
        $timeZone);
    $yMax = (int) (12 / $across);
    $width = (int) (100 / $across);
    $output = '<table>' . PHP_EOL;
    $month = 1;
    for ($y = 1; $y <= $yMax; $y++) {
        $output .= '<tr>';
        for ($x = 1; $x <= $across; $x++) {
            $output .= '<td style="vertical-align:top;'
                . ' width=' . $width . '">' 
                . $this->calendarForMonth($year, $month,
                    $timeZone, $dayType, $monthType,
                    $this->yearArray[$year][$month++]) . '</td>';
        }
        $output .= '</tr>' . PHP_EOL;
    }
    $output .= '</table>';
    return $output;
}
```

# How it works...

First of all, make sure you build the Application\Ii8n\Locale class as defined in the previous recipe. After that, create a new file, Calendar.php, in the Application\Ii8n folder, with all the methods described in this recipe.

Next, define a calling program, chap_08_html_calendar.php, which sets up autoloading and creates Locale and Calendar instances. Also be sure to define the year and month:

```
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\Ii8n\Locale;
use Application\Ii8n\Calendar;

$localeFr = new Locale('fr_FR');
$localeUs = new Locale('en_US');
$localeTh = new Locale('th_TH');
$calendarFr = new Calendar($localeFr);
$calendarUs = new Calendar($localeUs);
$calendarTh = new Calendar($localeTh);
$year = 2016;
$month = 1;
?>
```