

![](img/1ddec54918a4802eb9b4febec3d4e7f6_209_0.png)

图 8-1

## 静态属性

在上一章中，你遇到了静态函数变量。你也可以以类似的方式创建静态类属性，只需在属性名称前添加 static 关键字即可：

```
class MyClass {
    public static $myProperty;
}
```

类的静态成员与从此类派生的任何特定对象无关。要访问静态属性，请写出类名，后跟两个冒号 (::)，再后跟属性名称（前面带有 $ 符号）：

```
MyClass::$myProperty = 123;
```

以下是使用 Car 类的示例：

```
class Car {
    public $color;
    public $manufacturer;
    static public $numberSold = 123;
}
```

```
Car::$numberSold++;
echo Car::$numberSold; // Displays "124"
```

在 `Car` 类中，声明了一个名为 `$numberSold` 的静态属性，并将其初始化为 `123`。然后，在类定义之外，对该静态属性进行自增，并显示其新值 `124`。

当你想要记录一个与特定类相关但又与特定对象无关的持久值时，静态属性非常有用。你可以将它们视为类的全局变量。静态属性的好处在于，类外部的代码不需要创建类的实例（即对象）即可访问该属性。

## 类常量

在第 3 章中，你学习了如何创建常量——即在脚本运行过程中保存固定值的特殊标识符。PHP 还允许你在类中创建常量。要定义类常量，请使用关键字 `const`，如下所示：

```
class MyClass {
    const MYCONST = 123;
}
```

与普通常量一样，类常量名称的命名惯例是使用全大写字母。

像静态属性一样，你可以通过类名和 `::` 运算符来访问类常量：

```
echo MyClass::MYCONST;
```

当你需要定义与特定类相关的固定值或配置选项时，类常量非常有用。例如，对于 `Car` 类，你可以定义类常量来表示各种车型，然后在创建 `Car` 对象时使用这些常量：

```
class Car {
    const HATCHBACK = 1;
    const STATION_WAGON = 2;
    const SUV = 3;

    public $model;
    public $color;
    public $manufacturer;
    public $type;
}

$myCar = new Car;
$myCar->model = "Dodge Caliber";
$myCar->color = "blue";
$myCar->manufacturer = "Chrysler";
$myCar->type = Car::HATCHBACK;

echo "This $myCar->model is a ";
switch ( $myCar->type ) {
    case Car::HATCHBACK:
        echo "hatchback";
        break;
case Car::STATION_WAGON:
    echo "station wagon";
    break;
case Car::SUV:
    echo "SUV";
    break;
}
```

在此示例中，Car 类包含三个类常量——HATCHBACK、STATION_WAGON 和 SUV——它们分别被赋值为 1、2 和 3。这些常量在设置和读取 $myCar 对象的 $type 属性时被使用。

## 使用方法

到目前为止，你创建的类和对象大多只包含属性。因此，它们除了作为花哨的关联数组外，并没有多大用处。当你开始向类添加方法时，它们才变得真正强大。对象随后成为一个精心封装的功能块，既包含数据，也包含用于处理该数据的方法。

如前所述，方法很像函数，只不过它绑定到特定的类。

### 方法可见性

本章前面你学到，属性可以有三种可见性级别：public、private 和 protected。

方法也是如此。类中的所有方法都可以被同一个类中的其他方法调用。如果方法被声明为 public，则类定义之外的任何代码也可能调用该方法。但是，如果方法被声明为 private，则只有同一个类中的其他方法才能调用它。最后，protected 方法可以被类中的其他方法或继承自该类的类中的方法调用。

### 创建方法

要向类添加方法，请使用 public、private 或 protected 关键字，接着是 function 关键字，然后是方法名，再是括号。然后将方法的代码放在花括号中：

```
class MyClass {
    public function aMethod() {
        // (do stuff here)
    }
}
```

你可以选择省略 public、private 或 protected 关键字。如果这样做，则默认为 public。

## 调用方法

要调用对象的方法，只需写出对象的名称，然后是用于访问属性的相同箭头 (->)，接着是方法名及其括号：

```
$object->method();
```

以下是一个简单示例，它创建一个带有方法的类，然后从该类创建一个对象并调用该对象的方法：

```
class MyClass {

    public function hello() {
        echo "Hello, World!";
    }
}

$obj = new MyClass;
$obj->hello(); // Displays "Hello, World!"
```

## 添加参数和返回值

与你在上一章中学习的函数一样，你可以向方法添加参数，以便它可以接受用于处理的参数。方法也可以像函数一样返回值。

你添加参数和返回值的方式与函数非常相似。要添加参数，请在方法名称后的括号中指定参数名：

```
public function aMethod( $param1, $param2 ) {
    // (do stuff here)
}
```

要从方法返回值——或者仅仅是立即退出方法——请使用 return 关键字：

```
public function aMethod( $param1, $param2 ) {
    // (do stuff here)
    return true;
}
```

## 从方法访问对象属性

虽然你可以很高兴地使用参数和返回值向方法传递值并从方法接收值，但当对象尽可能自包含时，面向对象编程（OOP）的强大之处才会体现出来。这意味着，对象的方法理想情况下应主要使用对象的属性，而不是依赖外部数据来完成工作。

要在同一个对象的方法内部访问该对象的属性，你可以使用特殊变量名 $this，如下所示：

```
$this->property;
```

例如：

```
class MyClass {
    public $greeting = "Hello, World!";
    public function hello() {
        echo $this->greeting;
    }
}
```

```
$obj = new MyClass;
$obj->hello(); // Displays "Hello, World!"
```

在此示例中，创建了一个名为 MyClass 的类，带有一个属性 $greeting 和一个方法 hello()。该方法使用 echo 显示通过 $this->greeting 访问的 $greeting 属性的值。在类定义之后，脚本从该类创建一个对象 $obj，并调用该对象的 hello() 方法来显示问候语。

请注意，hello() 方法内部的 $this 指的是正在调用 hello() 方法的特定对象——在此例中，即存储在 $obj 中的对象。如果从同一个类创建另一个对象 $obj2 并调用其 hello() 方法，那么 $this 将改为指向 $obj2，因此 $this->greeting 将指向 $obj2 的 $greeting 属性。

顺便说一句，你也可以使用 $this 从同一个对象的另一个方法中调用该对象的方法：

```
class MyClass {
    public function getGreeting() {
        return "Hello, World!";
    }
    public function hello() {
        echo $this->getGreeting();
    }
}
```

```
$obj = new MyClass;
$obj->hello(); // Displays "Hello, World!"
```

在这里，hello() 方法使用 $this->getGreeting() 调用同一对象中的 getGreeting() 方法，然后使用 echo 显示返回的问候字符串。

## 试一试：一辆能动的汽车

以下示例展示了向类添加几个方法如何真正使其变得有用。
将脚本保存为文档根目录下的 car_simulator.php，然后在 Web 浏览器中运行它。图 8-2 显示了结果。

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>A Simple Car Simulator</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>A Simple Car Simulator</h1>

<?php

class Car {
public $color;
public $manufacturer;
public $model;
private $_speed = 0;

public function accelerate() {
if ( $this->_speed >= 100 ) return false;
$this->_speed += 10;
return true;
}

public function brake() {
if ( $this->_speed <= 0 ) return false;
$this->_speed -= 10;
return true;
}

public function getSpeed() {
return $this->_speed;
}
}

$myCar = new Car();
$myCar->color = "red";
$myCar->manufacturer = "Volkswagen";
$myCar->model = "Beetle";

echo "<p>I'm driving a $myCar->color $myCar->manufacturer $myCar->model.</p>";

echo "<p>Stepping on the gas...<br />";

while ( $myCar->accelerate() ) {
echo "Current speed: " . $myCar->getSpeed() . " mph<br />";
}
```

