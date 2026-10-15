

## 定义 PHP 类和对象：

一个类包含一组函数和成员变量（也称为属性）。一个 PHP 类可以包含许多函数和变量，如下所示：

```php
class Teacher
{
    public $course = "Java";

    function students()
    {
        // set of statements or lines here
    }
}
```

上面的 Teacher 类包含一个成员变量（类变量或属性），即 course，和一个函数，即 students()。这里的 public 是一个访问说明符，意味着变量 $course 可以被其他类访问或使用。请注意，在声明类变量或属性之前，我们应该添加可见性关键字（public / private / protected）来定义该变量在何处可用。

## 命名类：

你为类使用的名称（上例中的 “Teacher”）：

- 不应是 PHP 保留字（关键字）。
- 应以字母或下划线开头。
- 首字母之后可以包含字母、数字或下划线。

要访问任何类的成员变量或函数，你首先需要创建该类的一个对象。示例如下：

```php
$obj = new Teacher;
```

一旦创建了类的对象，你就可以像这样访问成员变量或函数：

```php
$obj->students();
echo $obj->course;
```

请记住，要执行或查看函数的输出，你必须先调用它。函数只有在你调用它之后才会产生输出。

## 什么是构造函数？

如前所述，每个函数都需要被调用才能获得输出。但构造函数是一个不需要调用的函数，因为一旦创建了类的对象，它就会被自动调用。在 PHP 中，构造函数是通过 __construct() 方法定义的。示例如下：

**示例：PHP 构造函数**

```php
class Teacher
{
    public $course = "Java";

    function __construct()
    {
        echo "This function is constructor- default function";
    }

    function __destruct()
    {
        echo "This function is destructor will call after end of program";
    }
}

$obj = new Teacher;
```

在上面的程序中，我们创建了 2 个函数：__construct() 和 __destruct()，它们会在对象创建后自动被调用。构造函数用于初始化内存，而析构函数用于释放或取消初始化类的内存，通常是在脚本结束时。

*请注意：如果你的构造函数带有参数，你应该在创建对象时传入这些参数的值。*

## $this 关键字

`$this` 是一个伪变量，仅在方法内部可用。`$this` 用于访问当前类的属性/成员变量。换句话说，我们使用 `$this` 变量来访问当前对象。示例如下：

```php
<?php

class Users {
    public $email;
    function sendData($x)
    {
        $this -> email = $x;
    }
}
```

## PHP 中的访问说明符或可见性模式

PHP 中有 3 种可见性/访问说明符：public、private 和 protected。这些可见性与属性或成员变量一起使用，以允许从类外部访问。这些说明符在验证和限制程序中的信息方面也起着重要作用。例如，我的信用卡及其 PIN 码详细信息是私有的，我不想与他人分享。

- **公共**属性和方法可以在任何地方或类外部访问。
- **私有**属性和方法只能在类内部访问。
- **受保护**的属性可以被继承其父类的类访问。

```php
<?php
class myDetails
{
    private $pin = "1234";

    function view_details()
    {
        echo $this->pin;    // Inside class this is valid
    }
}

$ob = new myDetails;

echo $ob->pin;   // Error: cannot access outside the class
```

因此，从上面的例子可以看出，类内部的任何方法都可以访问私有属性（pin）。但是，你不能从类外部访问它。

## PHP 面向对象编程中的继承

继承是从现有类创建新类的过程。不过，除了现有基类之外，我们还可以向新创建的类添加一些额外的功能或资源。

如果你有一些类表示公共的方法或属性，这会很有用。例如，一个电子商务门户有多个类，而在每个类中你都需要一些用户信息，如电子邮件和认证密钥。因此，与其为每个类创建单独的属性，你可以创建一个主类，并允许其他类通过继承使用这些属性。

当我们说继承类时，它是指子类或派生类，而被继承的类称为父类或基类。

PHP 面向对象编程中有几种继承类型，如下所示：

- **单继承**：一个类仅被一个类继承时，称为单继承。
- **多级继承**：当一个父类被子类继承，而该子类又被另一个子类继承时，称为多级继承。
- **层次继承**：当一个父类有多个子类时，称为层次继承。

*请注意，PHP 不支持多继承；不过，PHP 中有 **Traits** 可以解决这个问题。*

Hirdesh Bhardwaj

```php
class B extends A   // First child class of A
{
    function fn1()
    {
        $this->price = 200;
        echo $this->price;
    }
}

class C extends A   // Second child class of A
{
    function fn2()
    {
        $this->price = 300;
        echo $this->price;
    }
}

$ob1 = new B;
$ob1->fn1();
echo "<br>";

$ob2 = new C;
$ob2->fn2();
```

**PHP 中的 Traits：** 既然我们已经知道 PHP 不支持多继承，那么可以使用 PHP 中的 Traits 来声明可用于多个类的方法。这样做可以减少代码重复，因为不需要一遍又一遍地重新定义相同的方法。

### 示例：在 PHP 中使用 Traits

```php
<?php
Trait A
{
    public function hello()
    {
        echo "Hello This is Trait A";
    }
}

Trait B
{
    public function test()
    {
        echo "Hello This is Trait B";
    }
}

class MyClass
{
    use A, B; // Calling Traits A and B in the class
}

$obj = new MyClass();
$obj->hello();
$obj->test(); // Calling function test
?>
```

## PHP 中的静态方法和属性

静态方法广泛用于创建辅助函数和工具函数（例如自动加载），这让你能更好地组织和调用函数。PHP 中的静态函数可以直接调用（使用解析运算符 `::`），而无需创建类的对象。`static` 关键字用于在 PHP 中定义静态函数。

### 示例

```php
class A
{
    static function fn()
    {
        echo "This is a Static Function";
    }
}

echo A::fn(); // Calling function without creating object
```

请注意，如果未声明可见性模式或访问说明符（public、private 或 protected），则可见性模式默认为 *public*。

静态方法也可以使用 **self** 关键字和 `::`（解析运算符）从同一类的其他方法中访问。

**静态属性或变量：** 就像静态函数或方法一样，你也可以使用 `::` 运算符以相同方式访问静态属性或变量。示例：

```php
<?php
class A
{
    public static $rating = 7;  // Static properties / Member variable

    public function __construct()
    {
        echo "Rating is" . self::$rating;  // Accessing static variable
    }
}
```

```php
echo A::$rating;    // Accessing static variable directly
A::$rating = 10;
new A();  // Object to call constructor
```

## PHP 中的 Getter 和 Setter

Getter 和 Setter 方法提供数据封装，因此要设置或获取数据，必须通过一个方法。

“getter” 允许你检索或“获取”给定属性。“setter” 允许你“设置”给定属性的值。

### 示例

```php
<?php

class MyClass
{
    public $greeting = "Good Morning";

    public function setProperty($x)
    {
        $this->greeting = $x;
    }

    public function getProperty()
    {
```

