
$this->name = $name;

    return $this;
}
}

class Address
{
    protected $address = '';

    public function getAddress() : string
    {
        return $this->address;
    }

    public function setAddress(string $address)
    {
        $this->address = $address;
        return $this;
    }
}

![](img/39390f6d56c5a83b28db083a8bd5185c_106_0.png)

3.  类名不区分大小写。重复定义会被标记为错误。在此示例中，在文件 `TwoClass.php` 中，我们定义了两个类，`TwoClass` 和 `twoclass`：

```php
<?php
class TwoClass
{
    public function showOne()
    {
        return 'ONE';
    }
}

// 在解析第二个类定义时会发生致命错误
class twoclass
{
    public function showTwo()
    {
        return 'TWO';
    }
}
```

4.  PHP 7.1 解决了关键词 `$this` 使用中不一致的行为。虽然在 PHP 7.0 和 PHP 5.x 中是允许的，但从 PHP 7.1 开始，如果将 `$this` 用于以下任何用途，现在都会产生错误：
- 作为参数
- 作为静态变量
- 作为全局变量
- 作为 `try...catch` 块中使用的变量
- 作为 `foreach()` 中使用的变量
- 作为 `unset()` 的参数
- 作为变量（即，`$a = 'this'; echo $sa`）
- 通过引用间接使用

5.  如果你需要创建对象实例，但不想定义一个离散的类，可以使用内置于 PHP 中的通用 `stdClass`。`stdClass` 允许你在定义类时即时定义属性，而无需定义一个继承自 `stdClass` 的离散类：
`$obj = new stdClass();`

6.  此设施在 PHP 中的许多不同位置都有使用。例如，当你使用 PHP 数据对象（PDO）进行数据库查询时，一种获取模式是 `PDO::FETCH_OBJ`。此模式返回 `stdClass` 的实例，其中的属性代表数据库表的列：
`$stmt = $connection->pdo->query($sql);`
`$row = $stmt->fetch(PDO::FETCH_OBJ);`

## 工作原理...

取前面代码片段中所示的 `Test` 类示例，并将代码放在名为 `Test.php` 的文件中。创建另一个名为 `chap_04_oop_defining_class_test.php` 的文件。添加以下代码：

```php
require __DIR__ . '/Test.php';

$test = new Test();
echo $test->getTest();
echo PHP_EOL;
```

`$test->setTest('ABC');`
`echo $test->getTest();`
`echo PHP_EOL;`

输出将显示 `$test` 属性的初始值，然后是调用 `setTest()` 修改后的新值：

![](img/39390f6d56c5a83b28db083a8bd5185c_108_0.png)

下一个示例要求你在单个文件 `NameAddress.php` 中定义两个类，`Name` 和 `Address`。你可以使用以下代码调用和使用这两个类：

```php
require __DIR__ . '/NameAddress.php';

$name = new Name();
$name->setName('TEST');
$addr = new Address();
$addr->setAddress('123 Main Street');

echo $name->getName() . ' lives at ' . $addr->getAddress();
```

> 虽然 PHP 解释器不会生成错误，但通过定义多个类，文件的逻辑纯粹性受到了损害。此外，文件名与类名不匹配，这可能会影响自动加载的能力。

此示例的输出如下所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_109_0.png)

步骤 3 也展示了在一个文件中有两个类定义。然而，在这种情况下，目的是演示 PHP 中的类名不区分大小写。将代码放入文件 `TwoClass.php`。当你尝试包含该文件时，会生成错误：

![](img/39390f6d56c5a83b28db083a8bd5185c_109_1.png)

为了演示 `stdClass` 的直接使用，创建一个实例，为属性赋值，并使用 `var_dump()` 显示结果。若要查看 `stdClass` 在内部如何使用，使用 `var_dump()` 显示 PDO 查询的结果，其中获取模式设置为 `FETCH_OBJ`。

输入以下代码：

```php
$obj = new stdClass();
$obj->test = 'TEST';
echo $obj->test;
echo PHP_EOL;

include (__DIR__ . './../Application/Database/Connection.php');
$connection = new Application\Database\Connection(
    include __DIR__ . DB_CONFIG_FILE);

$sql = 'SELECT * FROM iso_country_codes';
$stmt = $connection->pdo->query($sql);
$row = $stmt->fetch(PDO::FETCH_OBJ);
var_dump($row);
```

输出如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_110_0.png)

## 参见...

有关 PHP 7.1 中关于关键词 `$this` 改进的更多信息，请参阅 https://wiki.php.net/rfc/this_var。

## 扩展类

开发人员使用面向对象编程（OOP）的主要原因之一是其能够重用现有代码，同时添加或覆盖功能。在 PHP 中，使用关键词 `extends` 来建立类之间的父/子关系。

## 操作步骤...

1.  在子类中使用关键词 `extends` 来设置继承。在以下示例中，`Customer` 类扩展 `Base` 类。`Customer` 的任何实例都将继承可见的方法和属性，在本例中为 `$id`、`getId()` 和 `setId()`：

```php
class Base
{
    protected $id;
    public function getId()
    {
        return $this->id;
    }
    public function setId($id)
    {
        $this->id = $id;
    }
}

class Customer extends Base
{
    protected $name;
    public function getName()
    {
        return $this->name;
    }
    public function setName($name)
    {
        $this->name = $name;
    }
}
```

2.  你可以强制任何使用你类的开发人员定义一个方法，方法是将其标记为抽象。在此示例中，`Base` 类将 `validate()` 方法定义为抽象。之所以必须是抽象的原因是因为从父类 `Base` 的角度来看，不可能确切确定子类是如何被验证的：

```php
abstract class Base
{
    protected $id;
    public function getId()
    {
        return $this->id;
    }
    public function setId($id)
    {
        $this->id = $id;
    }
    public function validate();
}
```

> 如果类包含一个**抽象方法**，该类本身必须声明为抽象类。

3.  PHP 仅支持单重继承。下一个示例展示了一个类 `Member`，它继承自 `Customer`。`Customer` 反过来继承自 `Base`：

```php
class Base
{
    protected $id;
    public function getId()
    {
        return $this->id;
    }
    public function setId($id)
    {
        $this->id = $id;
    }
}

class Customer extends Base
{
    protected $name;
    public function getName()
    {
        return $this->name;
    }
    public function setName($name)
    {
        $this->name = $name;
    }
}

class Member extends Customer
{
    protected $membership;
    public function getMembership()
    {
        return $this->membership;
    }
    public function setMembership($memberId)
    {
        $this->membership = $memberId;
    }
}
```

4.  为了满足类型提示，可以使用目标类的任何子类。在以下代码片段中显示的 `test()` 函数要求一个 `Base` 类的实例作为参数。继承链中的任何类都可以作为参数接受。传递给 `test()` 的其他任何内容都会抛出 `TypeError`：

```php
function test(Base $object)
{
    return $object->getId();
}
```

## 工作原理...

在第一点中，定义了一个 `Base` 类和一个 `Customer` 类。为了演示，将这两个类定义放在单个文件 `chap_04_oop_extends.php` 中，并添加以下代码：

```php
$customer = new Customer();
$customer->setId(100);
$customer->setName('Fred');
var_dump($customer);
```

注意 `$id` 属性以及 `getId()` 和 `setId()` 方法是从父类 `Base` 继承到子类 `Customer` 的：

![](img/39390f6d56c5a83b28db083a8bd5185c_113_0.png)

为了说明抽象方法的使用，假设你希望为任何扩展 `Base` 的类添加某种验证功能。问题在于，无法知道在继承类中可能会验证什么。唯一确定的是，你必须具备验证功能。

采用前面解释中提到的相同的 `Base` 类并添加一个新方法 `validate()`。将该方法标记为*抽象*，并且不要定义任何代码。注意当子类 `Customer` 扩展 `Base` 时发生了什么。

![](img/39390f6d56c5a83b28db083a8bd5185c_114_0.png)

如果你随后将 `Base` 类标记为*抽象*，但未在子类中定义 `validate()` 方法，则会生成*相同的错误*。最后，直接在子类 `Customer` 中实现 `validate()` 方法：

```php
class Customer extends Base
{
    protected $name;
    public function getName()
    {
        return $this->name;
    }
    public function setName($name)
    {
        $this->name = $name;
    }
    public function validate()
    {
        $valid = 0;
        $count = count(get_object_vars($this));
    }
}
```

