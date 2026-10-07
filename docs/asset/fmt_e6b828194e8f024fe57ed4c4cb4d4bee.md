
这段代码定义了一个 `Car` 类，然后创建了它的实例，即 `$beetle` 和 `$mustang`。一旦对象被创建，你就可以访问它们的属性。

## 第 8 章：对象

这个示例展示了如何定义属性，然后设置并读取它们：

```php
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>
  <title>定义和使用对象属性</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>定义和使用对象属性</h1>
<?php
class Car {
  public $color;
  public $manufacturer;
}
$beetle = new Car();
$beetle->color = "red";
$beetle->manufacturer = "Volkswagen";
$mustang = new Car();
$mustang->color = "green";
$mustang->manufacturer = "Ford";
echo "<h2>一些属性：</h2>";
echo "<p>甲虫汽车的颜色是 " . $beetle->color . "</p>";
echo "<p>野马汽车的制造商是 " . $mustang->manufacturer . "</p>";
echo "<h2>$beetle 对象：</h2><pre>";
print_r($beetle);
echo "</pre>";
echo "<h2>$mustang 对象：</h2><pre>";
print_r($mustang);
echo "</pre>";
?>
</body>
</html>
```

你可以从图 8-1 中看到此脚本的输出。该脚本定义了一个名为 `Car` 的类，它包含两个公共属性：`color` 和 `manufacturer`。它创建了一个新的 `Car` 对象并将其赋值给变量 `$beetle`，然后将 `$beetle` 的 `$color` 和 `$manufacturer` 属性分别设置为 "red" 和 "Volkswagen"。下一个脚本创建了另一个 `Car` 对象，将其赋值给 `$mustang`，并将它的 `$color` 属性设置为 "green"，将 `$manufacturer` 属性设置为 "Ford"。

现在两个对象已经创建且属性也已设置，脚本显示了两个属性的值：`$beetle` 对象的 `$color` 属性（`$beetle->color`）以及 `$mustang` 对象的 `$manufacturer` 属性（`$mustang->manufacturer`）。最后，它使用 `print_r()` 显示这两个对象，请注意 `print_r()` 显示对象属性的方式与其显示数组键和值的方式非常相似。

# 第二部分：学习语言

## 定义和使用对象属性

一些属性：

甲虫汽车的颜色是红色。

野马汽车的制造商是福特。

### `$beetle` 对象：

```
Car Object
[color] => red
manufacturer => Volkswagen
```

### `$mustang` 对象：

```
Car Object
[color] => green
manufacturer => Ford
```

完成

图 8-1

## 静态属性

你在上一章中遇到了静态函数变量。你也可以也可以以类似的方式创建静态属性，只需在属性名称之前添加 `static` 关键字即可：

```php
class MyClass {
    public static $myProperty;
}
```

类的静态成员独立于从该类派生的任何特定对象。要访问静态属性，你需要编写类名，后跟两个冒号 (`::`)，然后是属性名称（前面带有一个 `$` 符号）：

```php
MyClass::$myProperty = 123;
```

这是一个使用 `Car` 类的示例：

```php
class Car {
    public $color;
    public $manufacturer;
    static public $numberSold = 123;
}
```

```php
Car::$numberSold++;
echo Car::$numberSold; // 显示 "124"
```

## 第 8 章：对象

在 `Car` 类中，声明了一个静态属性 `$numberSold` 并将其初始化为 123。然后，在类定义外部，该静态属性递增，并显示了它的新值 124。

当你想要记录一个与特定类相关但与特定对象无关的持久值时，静态属性是非常用的。你可以将它们类为类的全局变量。静态属性的妙处在于，类外的代码不需要创建类的实例（即对象）即可访问该属性。

## 类常量

你在第 3 章中了解到可以创建常量——这些在脚本运行期间持有固定值的特殊标识符。PHP 还允许在类内部创建常量。要定义类常量，请使用 `const` 关键字，如下：

```php
class MyClass {
 const MYCONST = 123;
}
```

对于普通常量，使用全大写字母命名类是一个良好习惯。

与静态属性类似，你通过类名和 `::` 运算符访问类常量：

```php
echo MyClass::MYCONST;
```

当你需要定义特定于该类的固定值或设置配置选项时，类常量非常有用。例如，对于 `Car` 类可以定义类常量来表示不同类型的汽车，然后在创建 `Car` 对象时使用这些常量：

```php
class Car {
 const HATCHBACK = 1;
const STATION_WAGON = 2;
const SUV = 3;
public $model;
public $color;
public $manufacturer;
public $type;
}
```

```php
$myCar->model = "Dodge";
```

```php
$myCar->manufacturer = "Chrysler";
```

```php
$myCar->type = "Hatchback";
```

```php
$myCar->color = "Blue";
```

## 使用方法

到目前，你创建的类和对象主要由属性组成。当你开始为类添加方法时，它们就会变得强大。

## 方法可见性

在前面的章节中，你了解到属性可以有三种可见性：`public`、`private` 和 `protected`。方法也是如此。如果方法被声明为 `public`，类外的代码可以调用它。如果方法被声明为 `private`，类内部的方法可以调用它。最后，`protected` 方法可以被继承该类的方法调用。

## 创建方法

要在类中添加方法，使用 `public`、`private` 或 `protected` 关键字，然后是 `function` 关键字，后面是方法名，最后是括号。你可以在大括号内包含方法的代码：

```php
class MyClass {
public function aMethod() {
    // (在此处编写代码)
}
}
```

你可以省略 `public`、`private` 或 `protected` 关键字。如果你这样做，默认是 `public`。

## 第 8 章：对象

## 调用方法

要调用对象的方法，只需编写对象的名称、与用于属性相同的箭头 (`->`)，然后是方法名和括号：

```php
$object->method();
```

这是一个简单的示例，创建了一个包含方法的类，然后从该类创建一个对象并调用对象的方法：

```php
class MyClass {
    public function hello() {
        echo "Hello, World!";
    }
}
$obj = new MyClass();
$obj->hello(); // 显示 "Hello, World!"
```

## 添加参数和返回值

与你在上一章学习的函数一样，你可以为方法添加参数，以便它可以处理参数。方法还可以返回结果，就像函数一样。

添加参数和返回值的方式与函数非常相似。要添加参数，请在方法的括号内指定参数名称：

```php
public function aMethod($param1, $param2) {
    // (在此处编写代码)
}
```

要从方法返回值——或者简单地退出方法——使用 `return` 关键字：

```php
public function aMethod($param1, $param2) {
    // (在此处编写代码)
    return true;
}
```

## 从方法访问对象属性

虽然你可以通过参数和返回值方便地在方法之间传递值，但当对象尽可能自包含时，OOP 的威力才能得以实现。这意味着对象的方法理想情况下应该主要与其自身的属性工作，而不是依赖外部数据来完成工作。

# 第二部分：学习语言

要从同一个对象的方法内部访问该对象的属性，你需要使用特殊名称 `$this`，如下：

```php
$this->property;
```

例如：

```php
class MyClass {
    public $greeting = "Hello, World!";
    public function hello() {
        echo $this->greeting;
    }
}
```

```php
$obj = new MyClass;
$obj->hello(); // 显示 "Hello, World!"
```

在这个示例中，创建了一个名为 MyClass 类，它包含一个属性 `$greeting` 和一个方法 `hello()`。该方法使用 `echo` 来显示通过 `$this->greeting` 访问的 `$greeting` 属性的值。在类定义之后，脚本从该类创建了一个对象 `$obj`，并调用该对象的 `hello()` 方法来显示问候语（greeting）。

请注意，`hello()` 方法内部的 `$this` 指向的是正在调用 `hello()` 方法的那个特定对象——在本例中，就是存储在 `$obj` 中的对象。如果从同一个类中创建了另一个对象 `$obj2` 并调用它的 `hello()` 方法，那么 `$this` 将会指向 `$obj2`，因此 `$this->greeting` 将指向 `$obj2` 的 `$greeting` 属性。

顺便说一下，你也可以使用 `$this` 在同一个对象的另一个方法内部调用对象的方法：

```php
class MyClass {
    public function getGreeting() {
        return "Hello, World!";
    }
    public function hello() {
        echo $this->getGreeting();
    }
}
$obj = new MyClass;
$obj->hello(); // 显示 "Hello, World!"
```

在这里，`hello()` 方法使用 `$this->getGreeting()` 调用同一个对象中的 `getGreeting()` 方法，并使用 `echo` 显示返回的问候字符串。

## 第8章：对象

## 尝试一下：一辆行驶的汽车

下面的示例展示了如何通过类添加几个方法来让它真正变得有用。将脚本保存为文档根目录下的 `car_simulator.php`，然后在你的的 Web 浏览器中运行它。图 8-2 显示了结果。

```php
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/DTD/html-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <title>A Simple Car Simulator</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
  <h1>A Simple Car Simulator</h1>
</body>
</html>
<?php
```
