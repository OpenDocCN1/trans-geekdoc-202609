3. After that, we define a very simple method to return a row of week dates. Note that we take advantage of `Day::__invoke()` using `$day()`:

```
protected function getWeekDaysRow($week)
{
    $output = '<tr style="height: ' . $this->height . ';">';
    $width = (int) (100/7);
    foreach ($week as $day) {
        $output .= '<td style="vertical-align:top;'
                  . "width=" . $width . "%">"
                  . $day() . '</td>';
    }
    $output .= '</tr>' . PHP_EOL;
    return $output;
}
```

4. And finally, a method that puts the smaller methods together to generate a calendar for a single month. First we build the month array, but only if `$yearArray` is not already available:

```
public function calendarForMonth($year,
                                  $month,
                                  $timeZone = NULL,
                                  $dayType = self::DAY_3,
                                  $monthType = self::MONTH_FULL,
                                  $monthArray = NULL)
{
    $first = 0;
    if (!$monthArray)
        $monthArray = $this->yearArray[$year][$month]
                     ?? $this->buildMonthArray($year, $month, $timeZone);
```

5. The month needs to be decremented by 1 as `IntlCalendar` months are 0-based: `Jan = 0`, `Feb = 1`, and so on. We then build an `IntlCalendar` instance using the time zone (if any), and the locale. We next create a `IntlDateFormatter` instance to retrieve the month name and other information according to locale:

```
$month--;
$cal = IntlCalendar::createInstance(
        $timeZone, $this->locale->getLocaleCode());
$cal->set($year, $month, 1);
$formatter = $this->getDateFormatter();
$formatter->setPattern($monthType);
```