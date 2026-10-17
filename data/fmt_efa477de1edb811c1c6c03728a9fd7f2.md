
```php
<?php
#- Execution_Time.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.

set_time_limit(10);
date_default_timezone_set('Europe/Paris');

$limit = 1000000;
$step = 1000;
$time_0 = time();
$sleep = 0;
$work = 0;
for ($i = $step; $i < $limit; $i += $step) {

    $time_1 = time();
    $count = find_primes($i);
    $time_2 = time();
    $work += $time_2 - $time_1;

    sleep(1);
    $sleep++;

    print("Total time: " . (time() - $time_0)
        . ", working: " . $work . ", sleeping: " . $sleep
        . ". Primes: $count, within: $i\n");
}

function find_primes($limit) {
    $count = 0;
    $i = 3;
    while ($i < $limit) {
        $isPrime = true;
        $j = 2;
        while ($j < $i) {
            $isPrime = $i % $j > 0;
            if (!$isPrime) break;
            $j++;
        }
        if ($isPrime) $count++;
        $i++;
    }
    return $count;
}
?>
```

如果您运行它，迟早会收到“Maximum execution time of 10 seconds exceeded”错误，具体时间取决于您的 CPU 速度。

```
herong$ php Execution_Time.php

Total time: 1, working: 0, sleeping: 1. Primes: 167, within: 1000
Total time: 2, working: 0, sleeping: 2. Primes: 302, within: 2000
Total time: 3, working: 0, sleeping: 3. Primes: 429, within: 3000
Total time: 4, working: 0, sleeping: 4. Primes: 549, within: 4000
Total time: 5, working: 0, sleeping: 5. Primes: 668, within: 5000
Total time: 6, working: 0, sleeping: 6. Primes: 782, within: 6000
Total time: 7, working: 0, sleeping: 7. Primes: 899, within: 7000
Total time: 8, working: 0, sleeping: 8. Primes: 1006, within: 8000
Total time: 10, working: 1, sleeping: 9. Primes: 1116, within: 9000
Total time: 11, working: 1, sleeping: 10. Primes: 1228, within: 10000
Total time: 12, working: 1, sleeping: 11. Primes: 1334, within: 11000
Total time: 14, working: 2, sleeping: 12. Primes: 1437, within: 12000
Total time: 15, working: 2, sleeping: 13. Primes: 1546, within: 13000
Total time: 17, working: 3, sleeping: 14. Primes: 1651, within: 14000
Total time: 18, working: 3, sleeping: 15. Primes: 1753, within: 15000
Total time: 20, working: 4, sleeping: 16. Primes: 1861, within: 16000
Total time: 22, working: 5, sleeping: 17. Primes: 1959, within: 17000
Total time: 24, working: 6, sleeping: 18. Primes: 2063, within: 18000
Total time: 26, working: 7, sleeping: 19. Primes: 2157, within: 19000
Total time: 28, working: 8, sleeping: 20. Primes: 2261, within: 20000
Total time: 30, working: 9, sleeping: 21. Primes: 2359, within: 21000

PHP Fatal error:  Maximum execution time of 10 seconds exceeded
  in /Users/herong/Execution_Time.php on line 36
```

从输出中可以看出，最大执行时间限制仅适用于累积的`执行时间`，而不适用于`流逝时间`。

# 类与对象简介

本章提供了关于类和对象的教程笔记和示例代码。主题包括类和对象简介；静态变量和方法；超类和子类；抽象类和方法；接口和 Trait；重载属性和方法；对象克隆和序列化；对象变量的引用或别名。

## 主题

*   什么是类
*   什么是对象
*   什么是构造函数
*   什么是静态方法
*   什么是静态变量
*   什么是超类和子类
*   什么是抽象类
*   什么是抽象方法
*   什么是接口
*   什么是 Trait
*   什么是重载属性
*   什么是重载方法
*   什么是对象属性迭代
*   什么是对象克隆
*   什么是对象序列化
*   对象变量中包含什么
*   更新共享对象的变量
*   将对象作为函数参数传递

## 核心要点

*   类是一种用户定义的数据类型，与一组预定义的属性和操作（也称为方法）相关联。
*   对象是作为类的实例创建的数据实体。
*   静态变量和方法在类级别声明，无需类的任何对象即可访问。
*   超类和子类是一对类，其中第二个类从第一个类扩展而来，以继承第一个类的所有属性和操作。
*   抽象类被认为是未完全定义的，需要被扩展为子类以完成定义。
*   抽象方法仅声明了其调用签名，没有实现代码，需要在子类中实现。
*   接口类似于一个“半”抽象类，仅声明一些抽象方法且没有属性。任何想要实现接口的类都必须实现其抽象方法。
*   Trait 是一个伪类，定义了一组属性和操作。任何类都可以使用 Trait 来继承其属性和操作。
*   重载属性通过实现 `__set()`、`__get()`、`__isset()` 和 `__unset()` 方法间接提供。
*   重载方法通过实现 `__call()` 或 `__callStatic()` 方法间接提供。
*   对象克隆可以通过使用 `clone` 操作符轻松完成。
*   对象序列化和反序列化可以通过调用 `serialize()` 和 `unserialize()` 函数轻松完成。

# PHP 教程 - Herong 的教程示例

# 类和对象简介

## 什么是类

本节描述什么是类——一种用户定义的数据类型，它与一组预定义的属性和操作（也称为方法）相关联。

**什么是类？** 类是一种用户定义的数据类型，它与一组预定义的属性和操作（也称为方法）相关联。

在 PHP 中，类是用 `class` 语句块声明的：

```php
class class_name {
   public $var_name;
   ...

   function __construct() {
      ...
   }
   public function method_name() {
      ...
   }
   ...
}
```

请注意：

*   `public $var_name` 用于声明一个公开可访问的属性。
*   `function __construct() {...}` 用于声明一个构造方法，每当从此类实例化一个新对象时，该方法将被执行。
*   `public function method_name() {...}` 用于声明一个公开可访问的方法。

下面是一个简单的 PHP 类，它没有属性，只有一个公共操作：

```php
<?php
class HelloClass {
   public function show() {
      echo "Hello world!\n";
   }
}
?>
```

## 什么是对象

本节描述什么是对象——一个作为类的实例而创建的数据实体。对象是用 `new` 运算符创建的。

**什么是对象？** 对象是一个作为类的实例而创建的数据实体。

在 PHP 中，对象是用 `new` 运算符创建的，它返回一个对象的标识符。例如，以下语句创建一个 `HelloClass` 类的对象，并将该对象的标识符赋值给变量 `$h`：

```php
$h = new HelloClass();
```

为了检索属性值或调用对象的操作，我们需要使用附加在对象标识符上的 `->` 运算符。例如，以下语句在由 `$h` 标识的对象上调用 `show()` 操作：

```php
$h->show();
```

下面是一个完整的 PHP 脚本，它定义了一个类，创建了一个对象，并在该对象上调用了一个操作：

```php
<?php
/* HelloClassDemo.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

class HelloClass {
   public function show() {
      echo "Hello world!\n";
   }
}

$h = new HelloClass();
$h->show();
?>
```

如果你运行上面的教程示例，你将得到：

```
herong> \php\php HelloClassDemo.php

Hello world!
```

## 什么是构造函数

本节描述什么是构造函数——当从类创建新对象时自动调用的特殊方法。构造函数的主要目的是为对象属性提供初始值。

**什么是构造函数？** 构造函数是当从类创建新对象时自动调用的特殊方法。构造函数的主要目的是为对象属性提供初始值。

在 PHP 中，构造方法必须命名为 `__construct()`。例如，下面的类提供了一个构造函数来初始化新对象的两个属性：

```php
<?php
/* MyMessage.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

class MyMessage {
   public $text;
   public $length;

   function __construct($t) {
      $this->text = $t;
      $this->length = strlen($t);
   }
   public function show() {
      echo $this->text . "\n";
      echo "Number of bytes in the message: " . $this->length . "\n";
   }
}

$msg = new MyMessage("Hello there!");
$msg->show();
?>
```

请注意：

*   `$this` 用作引用当前对象的内置变量。
*   `$this->text` 像变量一样用于给 `$text` 属性赋值和取值。
*   构造方法可以从 `new` 操作接收参数。

如果你运行上面的教程示例，你将得到：

```
herong> \php\php MyMessage.php

Hello there!
Number of bytes in the message: 12
```

## 什么是静态方法

本节描述什么是静态方法——一种无需任何对象即可调用以执行通用操作的特殊方法。

**什么是静态方法？** 静态方法是一种无需任何对象即可调用以执行通用操作的特殊方法。

在 PHP 中，静态方法用关键字 `static` 声明，并用类名配合 `::` 运算符调用。例如，下面的教程示例提供了一个包含两个名为 `encode()` 和 `mixer()` 的静态方法的类：

```php
<?php
/* MyEncoder.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

class MyEncoder {
   public static function encode($str) {
      return bin2hex(self::mixer($str));
   }
   private static function mixer($str) {
      $tmp = base64_encode($str);
      $arr = str_split($tmp);
      shuffle($arr);
      $tmp = implode($arr);
      return base64_decode($tmp);
   }
}

echo MyEncoder::encode("Hello world!");
?>
```

请注意 `self` 用作表示当前类的关键字。

如果你运行上面的教程示例，你将得到类似这样的结果：

```
herong> \php\php MyEncoder.php

f06f52815c9bb21d8641b746
```

## 什么是静态变量

本节描述什么是静态变量——一种在类级别声明、由该类的所有对象共享的特殊变量。

**什么是静态变量？** 静态变量是一种在类级别声明、由该类的所有对象共享的特殊变量。

在 PHP 中，静态变量用关键字 `static` 声明，并用类名配合 `::` 运算符调用。例如，下面的教程示例提供了一个包含名为 `$count` 的静态变量的类：

```php
<?php
/* MyPassGenerator.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

class MyPassGenerator {
   public static $count = 0;
   public $sequence;
   private $password;

   public function __construct() {
      self::$count += 1;
      $this->sequence = self::$count;
      $words = array_merge(range('a', 'z'), range('A', 'Z'));
      shuffle($words);
      $this->password = substr(implode($words), 0, 6);
   }
   public function getPass() {
      return $this->password;
   }
}

$first = new MyPassGenerator();
$second = new MyPassGenerator();

echo "Total # of objects: " . MyPassGenerator::$count . "\n";
echo "First object: \n";
echo "   Sequence: " . $first->sequence . "\n";
echo "   Password: " . $first->getPass() . "\n";
echo "Second object: \n";
echo "   Sequence: " . $second->sequence . "\n";
echo "   Password: " . $second->getPass() . "\n";
?>
```

请注意 `self` 用作表示当前类的关键字。

如果你运行上面的教程示例，你将得到类似这样的结果：

```
herong> \php\php MyPassGenerator.php

Total # of objects: 2
First object:
   Sequence: 1
   Password: BOYXpv
Second object:
   Sequence: 2
   Password: KRzZOS
```

## 什么是超类和子类

本节描述什么是超类和子类——第二个类从第一个类扩展而来的一对类。子类的对象继承超类的所有属性和操作。

### 什么是超类和子类？

超类和子类是一对类，其中第二个类继承自第一个类。子类的对象从超类继承所有属性和操作。

在 PHP 中，子类使用关键字 `extends` 后跟超类名称来声明。例如，下面的教程示例提供了一个从类 `MyRectangle` 扩展而来的类 `MySquare`。在这种情况下，`MyRectangle` 是超类，`MySquare` 是子类。
