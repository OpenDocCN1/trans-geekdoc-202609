
# PHP 教程 - Herong 的教程示例

## 类和对象简介

### 什么是类

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

### 什么是对象

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

### 什么是构造函数

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

### 什么是静态方法

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

### 什么是静态变量

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

echo "Total # of objects: ". MyPassGenerator::$count ."\n";
echo "First object: \n";
echo "   Sequence: " . $first->sequence ."\n";
echo "   Password: " . $first->getPass() ."\n";
echo "Second object: \n";
echo "   Sequence: " . $second->sequence ."\n";
echo "   Password: " . $second->getPass() ."\n";
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

### 什么是超类和子类

本节描述什么是超类和子类——第二个类从第一个类扩展而来的一对类。子类的对象继承超类的所有属性和操作。

