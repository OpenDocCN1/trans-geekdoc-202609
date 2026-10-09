
const TEMP_PREFIX = 'TEMP_';
const ERROR_EVAL = 'ERROR: unable to evaluate object';
public static function hydrate(array $array, $object)
{
    $className = get_class($object);
    $components = explode('\\', $className);
    $realClass = array_pop($components);
    $nameSpace = implode('\\', $components);
    $tmpClass = $realClass . self::TEMP_SUFFIX;
    $template = 'namespace '
        . $nameSpace . '{ '
        . 'class ' . $tmpClass
        . ' extends ' . $realClass . ' '
}

15. Continuing in the hydrate() method, we define a $values property, and a constructor that assigns the array to be hydrated into the object as an argument. We loop through the array of values, assigning values to properties. We also define a useful getArrayCopy() method, which returns these values if needed, as well as a magic __get() method to simulate direct property access:

```
. '{ '
.   ' protected $values; '
.   ' public function __construct($array) '
.   ' { $this->values = $array; '
.     ' foreach ($array as $key => $value) '
.     ' $this->$key = $value; '
.   ' } '
.   ' public function getArrayCopy() '
.   ' { return $this->values; } '
. '}
```

16. For convenience we define a magic __get() method, which simulates direct variable access as if they were public:

```
. ' public function __get($key) '
. ' { return $this->values[$key] ?? NULL; } '
```

17. Still in the template for the new class, we define also a magic __call() method, which simulates getters and setters:

```
. ' public function __call($method, $params) '
. ' { '
.   ' preg_match("/^([get|set]_)(.*?)/i", '
.     '$method, $matches); '
.   ' $prefix = $matches[1] ?? ""; '
.   ' $key    = $matches[2] ?? ""; '
.   ' $key    = strtolower(substr($key, 0, 1)) '
.     ' . substr($key, 1); '
```

18. Continuing in the `__call` method, we handle the logic for getters and setters, and then close the class definition. We also append the code to end the namespace:

```
. ' if ($prefix == "get") { '
. ' return $this->values[$key] ?? NULL; '
. ' } else { '
. ' $this->values[$key] = $params[0]; '
. ' } '
. '} '
. ' ' // ends namespace ' . PHP_EOL
```

19. Finally, still in the template for the new class, we add a function, in the global namespace, that builds and returns the class instance:

```
. 'namespace { '
. 'function build($array) '
. '{ return new ' . $namespace . '\\' . $tempClass . '($array); } '
. '} ' // ends global namespace ' . PHP_EOL;
```

20. Still in the hydrate() method, we execute the completed template using eval(). We then run the build() method defined just at the end of the template. Note that as we are unsure of the namespace of the class to be populated, we define and call build() from the global namespace:

```
try {
    eval($template);
} catch (ParseError $e) {
    error_log(__METHOD__ . ': ' . $e->getMessage());
    throw new Exception(self::ERROR_EVAL);
}
return \build($array);
```

21. The extract() method is much easier to define as our choices are extremely limited. Extending a class and populating it from an array using magic methods is easily accomplished. The reverse is not the case. If we were to extend the class, we would lose all the property values, as we are extending the class, not the object instance. Accordingly, our only option is to use a combination of getters and public properties:

```
public static function extract($object)
{
    $array = array();
    $class = get_class($object);
    $methodList = get_class_methods($class);
    foreach ($methodList as $method) {
        preg_match('/^(get)(.*)?$/i', $method, $matches);
        $prefix = $matches[1] ?? '';
        $key    = $matches[2] ?? '';
        $key    = strtolower(substr($key, 0, 1))
                 . substr($key, 1);
        if ($prefix == 'get') {
            $array[$key] = $object->$method();
        }
    }
    $propertyList = array_keys(get_class_vars($class));
    foreach ($propertyList as $property) {
        $array[$property] = $object->$property;
    }
    return $array;
}
```

## How it works...

You can begin by defining three test classes with identical properties: firstName, lastName, and so on. The first, Person, should have protected properties along with getters and setters. The second, PublicPerson, will have public properties. The third, ProtectedPerson, has protected properties but no getters nor setters:

```php
<?php
namespace Application\Entity;

class Person
{
    protected $firstName   = '';
    protected $lastName    = '';
    protected $address     = '';
    protected $city        = '';
    protected $stateProv   = '';
    protected $postalCode  = '';
    protected $country     = '';

    public function getFirstName()
    {
        return $this->firstName;
    }

    public function setFirstName($firstName)
    {
        $this->firstName = $firstName;
    }

    // be sure to define remaining getters and setters
}
```

```php
<?php
namespace Application\Entity;

class PublicPerson
{
    private $id = NULL;
    public $firstName = '';
    public $lastName    = '';
    public $address     = '';
    public $city        = '';
    public $stateProv   = '';
    public $postalCode  = '';
    public $country     = '';
}
```

```php
<?php
namespace Application\Entity;

class ProtectedPerson
{
    private $id = NULL;
    protected $firstName   = '';
    protected $lastName    = '';
    protected $address     = '';
    protected $city        = '';
    protected $stateProv   = '';
    protected $postalCode  = '';
    protected $country     = '';
}
```

You can now define a calling program called chap_11_strategy_pattern.php, which sets up autoloading and uses the appropriate classes:

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../..');
use Application\Entity\{ Person, PublicPerson, ProtectedPerson };
use Application\Generic\Hydrator\Any;
use Application\Generic\Hydrator\Strategy\{ GetSet, Extending,
    PublicProps };
```

Next, create an instance of `Person` and run the setters to define values for properties:

```php
$objj = new Person();
$objj->setFirstName('Li\'lAbner');
$objj->setLastName('Yokum');
$objj->setAddress('1 Dirt Street');
$objj->setCity('Dogpatch');
$objj->setStateProv('Kentucky');
$objj->setPostalCode('12345');
$objj->setCountry('USA');
```

Next, create an instance of the `Any` hydrator, call `extract()`, and use `var_dump()` to view the results:

```php
$hydrator = new Any();
$b = $hydrator->extract($objj);
echo "\nChosen Strategy: " . $hydrator->chosen . "\n";
var_dump($b);
```

Observe, in the following output, that the `GetSet` strategy was chosen:

![](img/39390f6d56c5a83b28db083a8bd5185c_427_0.png)

> **Note**
> Note that the `id` property is not set as its visibility level is private.

Next, you can define an array with the same values. Call `hydrate()` on the `Any` instance, and supply a new `PublicPerson` instance as an argument:

```php
$a = [
    'firstName'  => 'Li\'lAbner',
    'lastName'   => 'Yokum',
    'address'    => '1 Dirt Street',
    'city'       => 'Dogpatch',
    'stateProv'  => 'Kentucky',
    'postalCode' => '12345',
    'country'    => 'USA'
];

$p = $hydrator->hydrate($a, new PublicPerson());
echo "\nChosen Strategy: " . $hydrator->chosen . "\n";
var_dump($p);
```

Here is the result. Note that the *PublicProps* strategy was chosen in this case:

![](img/39390f6d56c5a83b28db083a8bd5185c_428_0.png)

Finally, call `hydrate()` again, but this time supply an instance of *ProtectedPerson* as the object argument. We then call `getFirstName()` and `getLastName()` to test the magic getters. We also access first and last names as direct variable access:

```php
$q = $hydrator->hydrate($a, new ProtectedPerson());
echo "\nChosen Strategy: " . $hydrator->chosen . "\n";
echo "Name: {$q->getFirstName()} {$q->getLastName()}\n";
echo "Name: {$q->firstName} {$q->lastName}\n";
var_dump($q);
```

Here is the last output, showing that the *Extending* strategy was chosen. You'll also note that the instance is a new *ProtectedPerson_TEMP* class, and that the protected properties are fully populated:

![](img/39390f6d56c5a83b28db083a8bd5185c_429_0.png)

## Defining a mapper

A **mapper** or **data mapper** works in much the same manner as a hydrator: converting data from one model, be it array or object, into another. A critical difference is that the hydrator is generic and does not need to have object property names pre-programmed, whereas the mapper is the opposite: it needs precise information on property names for both models. In this recipe we will demonstrate the use of a mapper to convert data from one database table into another.

### How to do it...

1. We first define a `Application\Database\Mapper\FieldConfig` class, which contains mapping instructions for individual fields. We also define appropriate class constants:

```php
namespace Application\Database\Mapper;
use InvalidArgumentException;
class FieldConfig
{
    const ERROR_SOURCE =
        'ERROR: need to specify destTable and/or source';
    const ERROR_DEST = 'ERROR: need to specify either '
        . 'both destTable and destCol or neither';
```
