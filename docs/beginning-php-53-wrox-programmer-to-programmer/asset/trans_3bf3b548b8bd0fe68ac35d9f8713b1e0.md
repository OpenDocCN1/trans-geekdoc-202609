

## 第8 章：对象

通过创建抽象类，你可以使用 `Shape` 来定义子类的行为：

```php
$mySquare = new Square();
$mySquare->setColor("green");
$mySquare->makeHollow();
$info = new Shape();
$info->setShape(); 
```

你可能会问，抽象类有什么用？想象一下，你有一个 `Shape` 类，它定义了方法但没有具体实现，而子类 `Rectangle` 必须必须实现这些方法：

```php
abstract class Shape {
    private $_color = "black";
    private $_filled = false;

    public function getColor() {
        return $this->color;
    }

    public function setColor($color ) {
        $this->_color = $color;
    }

    public function isFilled() {
        return $this->_filled;
    }

    public function fill() {
        $this->_filled = true;
    }

    public function makeHollow() {
        $this->_filled = false;
    }

    abstract public function getArea();
}
```

现在，你可以使用继承自 `Shape` 类的任何类，并确保该子类实现了 `getArea()`。

因此，当程序员尝试在没有 `getArea()` 方法的情况下添加 `Rectangle` 类时，会生成错误：

Class Rectangle contains 1 abstract method and must therefore be declared abstract or implement the remaining methods (Shape::getArea)

这应该足以提醒程序员在类中添加所需的 `getArea()` 方法：

```php
class Rectangle extends Shape {
    private $_width = 0;
    private $_height = 0;

    public function getWidth() {
        return $this->_width;
    }

    public function getHeight() {
        return $this->_height;
    }

    public function setWidth($width ) {
        $this->_width = $width;
    }

    public function setHeight($height ) {
        $this->_height = $height;
    }

    public function getArea() {
        return $this->_width * $this->_height;
    }
}
```

## 第二部分：语言

这就是抽象类和方法发挥作用的地方。通过将父类声明为抽象类，你定义了所有子类必须遵循的规则。

此外，你可以在抽象类中混合抽象方法和非抽象方法。抽象类可以定义所有子类共有的行为，将剩余的方法留给子类来实现。

> 抽象类的反面——即实现了父类所有方法的类被称为具体类。

回到 `Shape` 类。通过将 `Shape` 类创建为抽象类，你可以为抽象 `getArea()` 方法添加声明，从而确保 `Shape` 的所有子类都实现 `getArea()`。

当你声明一个方法是抽象的时，使用 `abstract` 关键字如下：

```php
abstract class MyClass {
    abstract public function myFunction($param1, $param2);
}
```

不能直接实例化抽象类——即不能从它创建对象：

```php
// 生成错误：Cannot instantiate abstract class MyClass
$myObj = new MyClass();
```

因此，当你创建一个抽象类时，你实际上是在创建一个模板，而不是一个完整的类。你在要求子类实现任何抽象方法（除非这些子类本身也被声明为抽象）。

顺便提一下，如果你声明一个方法是抽象的，你不需要为该方法指定返回类型：

```php
abstract function getArea();
```

你可以指定方法所需的返回值。如果你在父类中声明抽象方法，你不需要为其包含任何代码：

```php
abstract function getArea();
```

