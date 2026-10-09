# How to do it...

+   1. Before anything else, it would be an excellent idea to create a class that represents an event. Ultimately you'll probably end up storing the data in such a class in a database. For this illustration, however, we will simply define the class, and leave the database aspect to your imagination. You will notice that we will use a number of classes included in the DateTime extension admirably suited to event generation:
```php
namespace Application\Libn;

use DateTime;
use DatePeriod;
use DateInterval;
use InvalidArgumentException;

class Event
{
    // code
}
```
2. Next, we define a series of useful class constants and properties. You will notice that we defined most of the properties public in order to economize on the number of getters and setters needed. The intervals are defined as `sprintf()` format strings; `%d` will be substituted for a value:
```php
const INTERVAL_DAY = 'P%dD';
const INTERVAL_WEEK = 'P%dW';
const INTERVAL_MONTH = 'P%dM';
const FLAG_FIRST = 'FIRST';       // 1st of the month
const ERROR_INVALID_END = 'Need to supply either # occurrences or an end date';
const ERROR_INVALID_DATE = 'String i.e. YYYY-mm-dd or DateTime instance only';
const ERROR_INVALID_INTERVAL = 'Interval must take the form "P\d+(D | W | M)"';

public $id;
public $flag;
public $value;
public $title;
public $locale;
public $interval;
public $description;
public $occurrences;
public $nextDate;
protected $endDate;
protected $startDate;
```