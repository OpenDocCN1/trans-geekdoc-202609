

## 使用 PHP 面向对象编程

代码继续自上一步：

```php
if (!empty($this->id) && is_int($this->id)) $valid++;
if (!empty($this->name)
  && preg_match('/[a-z0-9]/i', $this->name)) $valid++;
return ($valid == $count);
}
```

然后你可以添加以下过程式代码来测试结果：

```php
$customer = new Customer();

$customer->setId(100);
$customer->setName('Fred');
echo "Customer [id]: {$customer->getName()}" .
     " [{$customer->getId()}]\n";
echo ($customer->validate() ? 'VALID' : 'NOT VALID');
$customer->setId('XXX');
$customer->setName('$%E&*(');
echo "Customer [id]: {$customer->getName()}" .
     " [{$customer->getId()}]\n";
echo ($customer->validate() ? 'VALID' : 'NOT VALID');
```

输出结果如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_115_0.png)

为了展示单行继承，请在前面步骤 1 中显示的 Base 和 Customer 第一个示例中添加一个新的 Member 类：

```php
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

创建一个 Member 实例，并注意在以下代码中，所有属性和方法都可以从每个继承的类中访问，即使它们不是直接继承的：

```php
$member = new Member();
$member->setId(100);
$member->setName('Fred');
$member->setMembership('A299F322');
var_dump($member);
```

输出结果如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_116_0.png)

现在定义一个函数 test()，它接受一个 Base 实例作为参数：

```php
function test(Base $object)
{
    return $object->getId();
}
```

请注意，Base、Customer 和 Member 的实例都可以作为参数接受：

```php
$base = new Base();
$base->setId(100);

$customer = new Customer();
$customer->setId(101);

$member = new Member();
$member->setId(102);

// 所有 3 个类都适用于 test()
echo test($base)      . PHP_EOL;
echo test($customer)  . PHP_EOL;
echo test($member)    . PHP_EOL;
```

输出结果如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_117_0.png)

然而，如果你试图使用不在继承链中的对象实例来运行 test()，则抛出 TypeError：

```php
class Orphan
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
try {
    $orphan = new Orphan();
    $orphan->testid(103);
    echo test($orphan) . PHP_EOL;
} catch (TypeError $e) {
    echo 'Does not work!' . PHP_EOL;
    echo $e->getMessage();
}
```

我们在下图中可以观察到这一点：

![](img/39390f6d56c5a83b28db083a8bd5185c_118_0.png)

## 使用静态属性和方法

PHP 允许你在不创建类实例的情况下访问属性或方法。用于此目的的关键词是 **static**。

### 操作步骤...

- 1. 最简单的情况是，在声明普通属性或方法时，在声明可见性级别后添加 *static* 关键词。使用 *self* 关键词在内部引用该属性：

```php
class Test
{
    public static $test = 'TEST';
    public static function getTest()
    {
        return self::$test;
    }
}
```

- 2. *self* 关键词会早期绑定，这在访问子类中的静态信息时会导致问题。如果你绝对需要访问来自子类的信息，请在使用 *self* 的地方使用 *static* 关键词。这个过程被称为 **Late Static Binding**（晚静态绑定）。

- 3. 在以下示例中，如果你 `echo Child::getEarlyTest()`，输出将是 **TEST**。如果另一方面你运行 `Child::getLateTest()`，输出将是 **CHILD**。原因是 PHP 在使用 *self* 时会绑定到 *最早* 的定义，而对于 *static* 关键词使用的是 *最新* 的绑定：

```php
class Test2
{
    public static $test = 'TEST2';
    public static function getEarlyTest()
    {
        return self::$test;
    }
    public static function getLateTest()
    {
        return static::$test;
    }
}

class Child extends Test2
{
    public static $test = 'CHILD';
}
```

- 4. 在许多情况下，**工厂**设计模式与静态方法结合使用，根据给定的不同参数生成对象实例。在本例中，定义了一个静态方法 `factory()`，它返回一个 PDO 连接：

```php
public static function factory(
        $driver, $dbname, $host, $user, $pwd, $options = [])
{
    $dsn = sprintf('%s:dbname=%s;host=%s',
        $driver, $dbname, $host);
    try {
        return new PDO($dsn, $user, $pwd, $options);
    } catch (PDOException $e) {
        error_log($e->getMessage());
    }
}
```

### 工作原理...

你可以使用**类解析运算符** "::" 来引用静态属性和方法。给定前面显示的 Test 类，如果你运行此代码：

```php
echo Test::$test;
echo PHP_EOL;
echo Test::getTest();
echo PHP_EOL;
```

你将看到此输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_120_0.png)

为了说明晚静态绑定，基于前面显示的 Test2 和 Child 类，尝试此代码：

```php
echo Test2::$test;
echo PHP_EOL;
echo Child::$test;
echo PHP_EOL;
echo Child::getEarlyTest();
echo PHP_EOL;
echo Child::getLateTest();
echo PHP_EOL;
```

输出说明了 *self* 和 *static* 之间的区别：

![](img/39390f6d56c5a83b28db083a8bd5185c_121_0.png)

最后，为了测试前面显示的 factory() 方法，将代码保存为 `Application\Database` 文件夹中 `Connection.php` 文件中的 `Application\Database\Connection` 类。然后你可以尝试此操作：

```php
include __DIR__ . '/../Application/Database/Connection.php';
use Application\Database\Connection;
$connection = Connection::factory(
    'mysql', 'php\'cookbook\'', 'localhost', 'test', 'password'
);
$stmt = $connection->query('SELECT name FROM iso_country_codes');
while ($country = $stmt->fetch(PDO::FETCH_COLUMN))
    echo $country . ' ';
```

你将看到从示例数据库中拉取的国家列表：

![](img/39390f6d56c5a83b28db083a8bd5185c_121_1.png)

### 参见

有关晚静态绑定的更多信息，请参见 PHP 文档中的此说明：

```text
http://php.net/manual/en/language.oop5.late-static-bindings.php
```

## 使用命名空间

对高级 PHP 开发至关重要的一点是命名空间的使用。任意定义的命名空间成为类名的前缀，从而避免了意外类重复的问题，并赋予你极大的开发自由度。使用命名空间的另一个好处是，假设它匹配目录结构，它有助于自动加载，如 *第 1 章，构建基础* 中所述。

### 操作步骤...

- 1. 要在命名空间内定义一个类，只需在代码文件的顶部添加 `namespace` 关键词：

```php
namespace Application\Entity;
```

![](img/39390f6d56c5a83b28db083a8bd5185c_122_0.png)

> **最佳实践**
> 与每个文件只应有一个类的建议一样，每个文件也应只有一个命名空间。

- 2. 在 `namespace` 关键词之前，应该出现的唯一 PHP 代码是注释和/或 `declare` 关键词：

```php
<?php
declare(strict_types=1);
namespace Application\Entity;
/**
 * Address
 */
class Address
{
  // some code
}
```

- 3. 在 PHP 5 中，如果你需要访问外部命名空间中的类，你可以在前面添加一个仅包含命名空间的 `use` 语句。然后你需要在这个命名空间内为任何类引用添加命名空间最后一个组件作为前缀：

```php
use Application\Entity;
$name = new Entity\Name();
$addr = new Entity\Address();
$prof = new Entity\Profile();
```

- 4. 或者，你可以明确指定所有三个类：

```php
use Application\Entity\Name;
use Application\Entity\Address;
use Application\Entity\Profile;
$name = new Name();
$addr = new Address();
$prof = new Profile();
```

- 5. PHP 7 引入了一种称为 `group use` 的语法改进，大大改善了代码可读性：

```php
use Application\Entity\ {
    Name,
    Address,
    Profile
};
$name = new Name();
$addr = new Address();
$prof = new Profile();
```

- 6. 如第 1 章 *构建基础* 中所述，命名空间是**自动加载**过程的组成部分。此示例显示了一个演示自动加载器，它回显传入的参数，然后尝试基于命名空间和类名包含一个文件。这假设目录结构与命名空间匹配：

```php
function __autoload($class)
{
    echo "Argument Passed to Autoloader = $class\n";
    include __DIR__ . '/../' . str_replace(
        '\\', DIRECTORY_SEPARATOR, $class) . '.php';
}
```

