

```php
echo "<h2>Consuming an apple...</h2>";
$apple = new Fruit;
$apple->consume();

echo "<h2>Consuming a grape...</h2>";
$grape = new Grape;
$grape->consume();

?>
</body>
</html>
```

你可以在图 8-6 中看到此脚本的输出。请注意，对于 Grape 对象，调用的是被覆盖的方法 peel() 和 slice()，而对于 Fruit 对象，则调用的是父类的 peel() 和 slice() 方法。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_235_0.png)

图 8-6

## 保留父类的功能

偶尔，你希望在子类中覆盖父类的方法，但同时也要使用父类方法中的某些功能。你可以通过在子类的方法中调用父类的被覆盖方法来实现这一点。要调用被覆盖的方法，请在方法名之前写上 parent::：

```
parent::someMethod();
```

沿用之前的 Fruit 和 Grape 示例，假设你想创建一个扩展 Fruit 类的 Banana 类。通常，你像吃其他水果一样吃香蕉，但你还需要先将香蕉从一串香蕉中掰下来。因此，在 Banana 类中，你可以覆盖父类的 consume() 方法以包含掰下香蕉的功能，然后在 Banana 类的 consume() 方法中调用被覆盖的 consume() 方法来完成消耗过程：

```php
class Banana extends Fruit {
    public function consume() {
        echo "<p>I'm breaking off a banana...</p>";
        parent::consume();
    }
}

$banana = new Banana;
$banana->consume();
```

此代码产生以下输出：

```
I'm breaking off a banana...
I'm peeling the fruit...
I'm slicing the fruit...
I'm eating the fruit. Yummy!
```

## 使用 final 类和方法阻止继承和覆盖

到现在你可能已经意识到，通过继承来扩展类是面向对象编程（OOP）更强大的特性之一。一般来说，允许以这种方式（由你或其他程序员）扩展你的类并没有问题。

然而，偶尔能够锁定一个类以防止其被继承是很有用的。同样，你可能想要锁定类中的一个或多个方法，以防止它们在子类中被覆盖。通过这样做，你知道你的类——或类中的方法——始终会以完全相同的方式行为。

你可以在类或方法定义之前添加关键字 final 来锁定该类或方法。例如，下面是如何创建一个 final 类：

```php
final class HandsOffThisClass {
    public $someProperty = 123;
    public function someMethod() {
        echo "A method";
    }
}

// Generates an error:
// "Class ChildClass may not inherit from final class (HandsOffThisClass)"
class ChildClass extends HandsOffThisClass {
}
```

同样，下面是如何创建一个 final 方法：

```php
class ParentClass {
    public $someProperty = 123;
    public final function handsOffThisMethod() {
        echo "A method";
    }
}

// Generates an error:
// "Cannot override final method ParentClass::handsOffThisMethod() "
```

```php
class ChildClass extends ParentClass {
    public function handsOffThisMethod() {
        echo "Trying to override the method";
    }
}
```

你可能不需要经常创建 final 类或方法；通常，允许你的类被扩展更好，因为这会使你的代码更加灵活。

## 使用抽象类和抽象方法

能够从父类创建新子类固然很好，但如果子类的功能与父类大相径庭，事情可能会失控。有时，最好能为子类的行为制定一些基本规则。抽象类和抽象方法正好允许你这样做。

为了说明类抽象，请回想一下你之前创建的 `Shape` 类示例。请记住，你创建了一个包含一些基本功能的通用 `Shape` 父类，然后用 `Circle` 和 `Square` 子类扩展了 `Shape` 类。

现在，`Circle` 和 `Square` 都包含一个 `getArea()` 方法，用于计算形状的面积，无论形状类型如何。你可以利用此事实来创建一个通用的 `ShapeInfo` 类，其中包含一个名为 `showInfo()` 的方法，用于显示给定形状的颜色和面积：

```php
class ShapeInfo {
    private $_shape;

    public function setShape($shape) {
        $this->_shape = $shape;
    }

    public function showInfo() {
        echo "<p>The shape's color is " . $this->_shape->getColor();
        echo ", and its area is " . $this->_shape->getArea() . "</p>";
    }
}
```

下面是如何使用 ShapeInfo 来显示正方形的颜色和大小：

```php
$mySquare = new Square;
$mySquare->setColor("green");
$mySquare->makeHollow();
$mySquare->setSideLength(3);
$info = new ShapeInfo();
$info->setShape($mySquare);
$info->showInfo(); // Displays "The shape's color is green, and its area is 9. "
```

你可能在想这与抽象类有什么关系。好吧，假设另一个程序员基于你的 Shape 类创建了一个名为 Rectangle 的新子类：

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

    public function setWidth($width) {
        $this->_width = $width;
    }

    public function setHeight($height) {
        $this->_height = $height;
    }
}
```

注意缺少了什么吗？如果你尝试将 Rectangle 对象与 ShapeInfo 类的 showInfo() 方法一起使用，会发生什么？

```php
$myRect = new Rectangle;
$myRect->setColor("yellow");
$myRect->fill();
$myRect->setWidth(4);
$myRect->setHeight(5);
$info = new ShapeInfo();
$info->setShape($myRect);
$info->showInfo();
```

答案是你会得到以下错误：

```
Call to undefined method Rectangle::getArea()
```

我们这位勇敢的程序员忘记在他的 Rectangle 类中创建 getArea() 方法。或者他可能没有意识到自己应该这样做。毕竟，他怎么知道 Rectangle 对象需要与你的 ShapeInfo 类一起使用呢？

这时就需要用到抽象类和抽象方法了。通过将父类设为抽象类，你规定了子类必须包含哪些方法。当你在父类中声明一个抽象方法时，你并不会在方法中实际插入任何代码；相反，这留给子类去实现。你指定子类必须做什么，而不是如何去做。

要声明一个抽象方法，只需使用 abstract 关键字，如下所示：

```
abstract public function myMethod($param1, $param2);
```

如你所见，你也可以可选地指定方法必须包含的任何参数。但是，你不会包含实现方法的任何代码，也不会指定方法必须返回什么类型的值。

如果你将类的一个或多个方法声明为抽象方法，则还必须将整个类声明为抽象类：

```php
abstract class MyClass {
    abstract public function myMethod($param1, $param2);
}
```

你不能直接实例化抽象类——也就是说，不能直接从中创建对象：

```
// Generates an error: "Cannot instantiate abstract class MyClass"
$myObj = new MyClass;
```

因此，当你创建一个抽象类时，你本质上是在创建一个模板，而不是一个完整的类。你在说，任何子类都必须实现抽象类中的任何抽象方法（除非这些子类本身也被声明为抽象类）。

顺便说一句，你可以在抽象类中混合抽象方法和非抽象方法。因此，你的抽象类可以定义所有可能子类共有的行为，同时将其余方法留为抽象方法，由子类实现。

*抽象类的对立面——即实现其父抽象类所有方法的类——称为具体类。*

现在回到 Shape 示例。通过将 Shape 类创建为抽象类，你可以添加抽象 getArea() 方法的声明，确保 Shape 的所有子类都必须实现 getArea()：

```php
abstract class Shape {
    private $_color = "black";
    private $_filled = false;

    public function getColor() {
        return $this->_color;
    }
}
```

