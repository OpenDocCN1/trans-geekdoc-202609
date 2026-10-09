
if ($next) {  
    if ($callDateTime->format('Y-m-d') ==
        $eventObj->nextDate->format('Y-m-d')) {  
        $dayObj->events[$eventObj->id] = $eventObj;  
        $eventObj->nextDate = $next;  
    }
}
return $dayObj;

> Note that we do not do a direct comparison of the two objects. Two reasons for this: first of all, one is a DateTime instance, the other is an IntlCalendar instance. The other, more compelling reason, is that it’s possible that hours:minutes:seconds were included when the DateTime instance was obtained, resulting in actual value differences between the two objects.

1. Now we need to add a call to `processEvents()` in the `buildMonthArray()` method so that it looks like this:

```php
while ($dow <= $maxDaysInMonth) {  
    for ($dow = 1; $dow <= 7; $dow++) {  
        // add this to the existing code:  
        $dayObj = $this->processEvents(new Day($value, $cal));  
        $monthArray[$weekOfYear][$dow] = $dayObj;  
    }
}
```

2. Finally, we need to modify `getWeekDaysRow()`, adding the necessary code to output event information inside the box along with the date:

```php
protected function getWeekDaysRow($type, $week)  
{  
    $output = '<tr style="height:' . $this->height . ';">';  
    $width = (int) (100/7);  
    foreach ($week as $day) {  
        $events = '';  
        if ($day->events) {  
            foreach ($day->events as $single) {  
                $events .= '<br>' . $single->title;  
                if ($type == self::DAY_FULL) {  
                    $events .= '<br><i>' . $single->description . '</i>';  
                }
            }
        }
    }
    $output .= '<td style="vertical-align: top; width:' . $width . '%">'
. $day . $events . '</td>';
    $output .= '</tr>' . PHP_EOL;
    return $output;
}
```

## How it works...

To tie events to the calendar, first code the `Application\I18n\Event` class described in steps 1 to 10. Next, modify `Application\I18n\Calendar` as described in steps 11 to 14. You can then create a test script, `chap_08_recurring_events.php`, which sets up autoloading and creates `Locale` and `Calendar` instances. For the purposes of illustration, go ahead and use 'es_ES' as a locale:

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../..');
use Application\I18n\{ Locale, Calendar, Event };

try {
$year = 2016;
$localeEs = new Locale('es_ES');
$calendarEs = new Calendar($localeEs);
```

Now we can start defining and adding events to the calendar. The first example adds an event that lasts 3 days and starts on 8 January 2016:

```php
// add event: 3 days
$title = 'Conf';
$description = 'Special 3 day symposium on eco-waste';
$startDate = '2016-01-08';
$event = new Event($title, $description, $startDate,
Event::INTERVAL_DAY, 1, 2);
$calendarEs->addEvent($event);
```

Here is another example, an event that occurs on the first of every month until September 2017:

```php
$title = 'Pay Rent';
$description = 'Sent rent check to landlord';
$startDate = new DateTime('2016-02-01');
$event = new Event($title, $description, $startDate,
    Event::INTERVAL_MONTH, '2017-09-01', NULL, Event::FLAG_FIRST);
$calendarEs->addEvent($event);
```

You can then add sample weekly, bi-weekly, monthly, and so on events as desired. You can then close the try...catch block, and produce suitable display logic:

```php
} catch (Throwable $e) {
$message = $e->getMessage();
}
?>
<!DOCTYPE html>
<head>
<title>PHP 7 Cookbook</title>
<meta http-equiv="content-type" content="text/html;charset=utf-8" />
<link rel="stylesheet" type="text/css" href="php7cookbook_html_table.css">
</head>
<body>
<h3>Year: <?= $year ?></h3>
<?= $calendarEs->calendarForYear($year, 'Europe/Berlin',
  Calendar::DAY_3, Calendar::MONTH_FULL, 2); ?>
<?= $calendarEs->calendarForMonth($year, 1 , 'Europe/Berlin',
  Calendar::DAY_FULL); ?>
</body>
</html>
```

Here is the output showing the first few months of the year:

![](img/39390f6d56c5a83b28db083a8bd5185c_319_0.png)

## See also

- For more information on `IntlCalendar` field constants that can be used with `get()`, please refer to this page: `http://php.net/manual/en/class.intlcalendar.php#intlcalendar.constants`

# Handling translation without gettext

Translation is an important part of making your website accessible to an international customer base. One way this is accomplished is to use the PHP `gettext` functions, which are based on the **GNU** `gettext` operating system tools installed on the local server. `gettext` is well documented and well supported, but uses a legacy approach and has distinct disadvantages. Accordingly, in this recipe, we present an alternative approach to translation where you can build your own *adapter*.

Something important to recognize is that the programmatic translation tools available to PHP are primarily designed to provide limited translation of a word or phrase, referred to as the `msgid` (**message ID**). The translated equivalent is referred to as the `msgstr` (**message string**). Accordingly, incorporating translation typically only involves relatively unchanged items such as menus, forms, error or success messages, and so on. For the purposes of this recipe, we will assume that you have the actual web page translations stored as blocks of text.

> If you need to translate entire pages of content, you might consider using the Google Translate API. This is, however, a paid service. Alternatively, you could outsource the translation to individuals with multi-lingual skills cheaply using Amazon Mechanical Turk. See the See Also section at the end of this recipe for the URLs.

## How to do it...

1. We will once again use the Adapter software design pattern, in this case to provide alternatives to the translation source. In this recipe, we will demonstrate adapters for `.ini` files, `.csv` files, and databases.
2. To begin, we will define an interface that will later be used to identify a translation adapter. The requirements for a translation adapter are quite simple, we only need to return a message string for a given message ID:

```php
namespace Application\I18n\Translate\Adapter;

interface TranslateAdapterInterface
{
  public function translate($msgid);
}
```

3. Next we define a trait that matches the interface. The trait will contain the actual code required. Note that if we fail to find the message string, we simply return the message ID:

```php
namespace Application\I18n\Translate\Adapter;

trait TranslateAdapterTrait
{
  protected $translation;
  public function translate($msgid)
  {
    return $this->translation[$msgid] ?? $msgid;
  }
}
```

4. Now we're ready to define our first adapter. In this recipe, we'll start with an adapter that uses an .ini file as the source of translations. The first thing you'll notice is that we use the trait defined previously. The constructor method will vary between adapters. In this case, we use `parse_ini_file()` to produce an array of key/value pairs where the key is the message ID. Notice that we use the `$filePattern` parameter to substitute the locale, which then allows us to load the appropriate translation file:

```php
namespace Application\I18n\Translate\Adapter;

use Exception;
use Application\I18n\Locale;

class Ini implements TranslateAdapterInterface
{
    use TranslateAdapterTrait;
    const ERROR_NOT_FOUND = 'Translation file not found';
    public function __construct(Locale $locale, $filePattern)
    {
        $translateFileName = sprintf($filePattern,
            $locale->getLocaleCode());
        if (!file_exists($translateFileName)) {
            error_log(self::ERROR_NOT_FOUND . ': ' . $translateFileName);
            throw new Exception(self::ERROR_NOT_FOUND);
        } else {
            $this->translation = parse_ini_file($translateFileName);
        }
    }
}
```

5. The next adapter, `Application\I18n\Translate\Adapter\Csv`, is identical, except that we open the translation file and loop through using `fgetcsv()` to retrieve the message ID / message string key pairs. Here we show only the difference in the constructor:

```php
public function __construct(Locale $locale, $filePattern)
{
    $translateFileName = sprintf($filePattern,
        $locale->getLocaleCode());
    if (!file_exists($translateFileName)) {
        error_log(self::ERROR_NOT_FOUND . ': ' . $translateFileName);
        throw new Exception(self::ERROR_NOT_FOUND);
    } else {
        $fileObj = new SplFileObject($translateFileName, 'r');
        while ($row = $fileObj->fgetcsv()) {
            $this->translation[$row[0]] = $row[1];
        }
    }
}
```
