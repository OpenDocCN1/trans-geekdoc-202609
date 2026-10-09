

## 构建对象转数组水合器

本食谱是*创建数组转对象水合器*食谱的逆向操作。在这种情况下，我们需要从对象属性中提取值，并返回一个关联数组，其中键将是列名。

### 操作方法...

- 1. 为了进行说明，我们将在前面食谱中定义的 `Application\Generic\Hydrator\GetSet` 类的基础上进行构建：

```php
namespace Application\Generic\Hydrator;
class GetSet
{
    // code
}
```

- 2. 在前面食谱中定义的 `hydrate()` 方法之后，我们定义一个 `extract()` 方法，该方法接受一个对象作为参数。其逻辑与使用 `hydrate()` 时类似，不同之处在于我们这次是搜索 `getXXX()` 方法。同样，使用 `preg_match()` 来匹配方法前缀及其后缀，随后假设该后缀即为数组键：

```php
public static function extract($object)
{
    $array = array();
    $class = get_class($object);
    $methodList = get_class_methods($class);
    foreach ($methodList as $method) {
        preg_match('/^(get)(.*)$/', $method, $matches);
        $prefix = $matches[1] ?? '';
        $key    = $matches[2] ?? '';
        $key = strtolower(substr($key, 0, 1)) . substr($key, 1);
        if ($prefix == 'get') {
            $array[$key] = $object->$method();
        }
    }
    return $array;
}
```

> 请注意，为了方便起见，我们将 `hydrate()` 和 `extract()` 定义为了静态方法。

### 工作原理...

定义一个名为 `chap_11_object_to_array.php` 的调用程序，该程序设置自动加载并使用相应的类：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\Entity\Person;
use Application\Generic\Hydrator\GetSet;
```

接下来，定义一个 `Person` 实例，并为其属性设置值：

```php
$obj = new Person();
$obj->setFirstName('Li\'lAbner');
$obj->setLastName('Yokum');

$obj->setAddress('1DirtStreet');
$obj->setCity('Dogpatch');
$obj->setState('Kentucky');
$obj->setPostalCode('12345');
$obj->setCountry('USA');
```

最后，以静态方式调用新的 `extract()` 方法：

```php
$a = GetSet::extract($obj);
var_dump($a);
```

输出显示在下面的截图中：

![](img/39390f6d56c5a83b28db083a8bd5185c_418_0.png)

## 实现策略模式

通常，运行时条件会迫使开发人员定义执行相同任务的多种方法。传统上，这涉及一个巨大的 if/elseif/else 命令块。您要么在 if 语句内部定义大块逻辑，要么创建一系列函数或方法以启用不同的方法。策略模式试图通过让主要类封装代表解决同一问题不同方法的一系列子类来使这一过程形式化。

### 操作方法...

- 1. 在这个说明中，我们将使用之前定义的 GetSet 水合器类作为一种策略。我们将定义一个主要的 `Application\Generic\Hydrator\Any` 类，该类将消耗 `Application\Generic\Hydrator\Strategy` 命名空间中的策略类，包括 `GetSet`、`PublicProps` 和 `Extending`。

- 2. 我们首先定义反映可用内置策略的类常量：

```php
namespace Application\Generic\Hydrator;
use InvalidArgumentException;
use Application\Generic\Hydrator\Strategy\ { GetSet, PublicProps, Extending };
class Any
{
    const STRATEGY_PUBLIC = 'PublicProps';
    const STRATEGY_GET_SET = 'GetSet';
    const STRATEGY_EXTEND = 'Extending';
    protected $strategies;
    public $chosen;
```

- 3. 然后我们定义一个构造函数，将所有内置策略添加到 `$strategies` 属性中：

```php
public function __construct()
{
    $this->strategies[self::STRATEGY_GET_SET] = new GetSet();
    $this->strategies[self::STRATEGY_PUBLIC] = new PublicProps();
    $this->strategies[self::STRATEGY_EXTEND] = new Extending();
}
```

- 4. 我们还添加了一个 `addStrategy()` 方法，允许我们在不重新编码类的情况下覆盖或添加新策略：

```php
public function addStrategy($key, HydratorInterface $strategy) 
{
    $this->strategies[$key] = $strategy;
}
```

- 5. `hydrate()` 和 `extract()` 方法只是调用所选策略的相应方法：

```php
public function hydrate(array $array, $object)
{
    $strategy = $this->chooseStrategy($object);
    $this->chosen = get_class($strategy);
    return $strategy::hydrate($array, $object);
}

public function extract($object)
{
    $strategy = $this->chooseStrategy($object);
    $this->chosen = get_class($strategy);
    return $strategy::extract($object);
}
```

- 6. 棘手的地方在于确定应选择哪种水合策略。为此，我们定义了 `chooseStrategy()`，该方法接受一个对象作为参数。我们首先通过获取类方法列表进行一些侦探工作。然后我们扫描该列表，查看是否存在任何 `getX()` 或 `setX()` 方法。如果存在，我们选择 `GetSet` 水合器作为所选策略：

```php
public function chooseStrategy($object)
{
    $strategy = NULL;
    $methodList = get_class_methods(get_class($object));
    if (!empty($methodList) && is_array($methodList)) {
        $getSet = FALSE;
        foreach ($methodList as $method) {
            if (preg_match('/^(get|set).*$/', $method)) {
                $strategy = $this->strategies[self::STRATEGY_GET_SET];
                break;
            }
        }
    }
```

- 7. 仍然在我们的 `chooseStrategy()` 方法中，如果没有 getter 或 setter，我们接下来使用 `get_class_vars()` 来确定是否存在可用属性。如果存在，我们选择 `PublicProps` 作为我们的水合器：

```php
if (!$strategy) {
    $vars = get_class_vars(get_class($object));
    if (!empty($vars) && count($vars)) {
        $strategy = $this->strategies[self::STRATEGY_PUBLIC];
    }
}
```

- 8. 如果以上方法都失败，我们回退到 `Extending` 水合器，该水合器返回一个简单地继承对象类的新类，从而使得任何公共或受保护属性可用：

```php
if (!$strategy) {
    $strategy = $this->strategies[self::STRATEGY_EXTEND];
}
return $strategy;
}
```

- 9. 现在我们将注意力转向策略本身。首先，我们定义一个新的 `Application\Generic\Hydrator\Strategy` 命名空间。

- 10. 在新命名空间中，我们定义一个接口，允许我们识别任何可以被 `Application\Generic\Hydrator\Any` 消耗的策略：

```php
namespace Application\Generic\Hydrator\Strategy;
interface HydratorInterface
{
    public static function hydrate(array $array, $object);
    public static function extract($object);
}
```

- 11. GetSet 水合器与前两个食谱中定义的完全相同，唯一的增加是它将实现新的接口：

```php
namespace Application\Generic\Hydrator\Strategy;
class GetSet implements HydratorInterface
{
    public static function hydrate(array $array, $object)
    {
        // defined in the recipe:
        // "Creating an Array to Object Hydrator"
    }
    public static function extract($object)
    {
        // defined in the recipe:
        // "Building an Object to Array Hydrator" 
    }
}
```

- 12. 下一个水合器只是读取和写入公共属性：

```php
namespace Application\Generic\Hydrator\Strategy;
class PublicProps implements HydratorInterface
{
    public static function hydrate(array $array, $object)
    {
        $propertyList = array_keys(
            get_class_vars(get_class($object)));
        foreach ($propertyList as $property) {
            $object->$property = $array[$property] ?? NULL;
        }
        return $object;
    }

    public static function extract($object)
    {
        $array = array();
        $propertyList = array_keys(
            get_class_vars(get_class($object)));
        foreach ($propertyList as $property) {
            $array[$property] = $object->$property;
        }
        return $array;
    }
}
```

- 13. 最后，`Extending` 是水合器的瑞士军刀，它继承对象类，从而提供对属性的直接访问。我们进一步定义魔术 getter 和 setter 以提供对属性的访问。

- 14. `hydrate()` 方法是最困难的，因为我们假设没有定义 getter 或 setter，并且属性也没有定义为公共可见性级别。因此，我们需要定义一个继承要水合的对象的类的新类。我们通过首先定义一个将用作构建新类模板的字符串来实现这一点：

```php
namespace Application\Generic\Hydrator\Strategy;
class Extending implements HydratorInterface
{
    const UNDEFINED_PREFIX = 'undefined';
```

