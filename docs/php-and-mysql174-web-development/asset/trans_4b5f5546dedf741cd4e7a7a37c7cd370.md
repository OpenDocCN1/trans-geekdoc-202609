

```php
class B extends A
{
    function __construct()
    {
        $this->operation1();
        $this->operation2();
        $this->operation3();
    }
}
$b = new B;
```

这段代码在类 A 中创建了三种类型的操作：公共、保护和私有。B 继承自 A。在 B 的构造函数中，你尝试调用父类的操作。

这一行
`$this->operation1();`

会产生致命错误，如下：
**Fatal error**: Call to private method A::operation1() from context 'B'

此示例表明私有操作不能从子类中调用。如果你注释掉这一行，其他的函数调用将正常工作。受保护函数被继承了，但只能在子类内部使用（如此处所示）。如果你尝试在文件末尾添加行
`$b->operation2();`

你将得到以下错误：
**Fatal error**: Call to protected method A::operation2() from context ''

然而，你可以从类外部调用 operation3()，如下：
`$b->operation3();`
你可以进行此调用，是因为它被声明为公共。

## 重写 (Overriding)

在本章中，我们展示了一个子类声明了新的属性和操作。重定义相同的属性和操作也是有效的，有时是有用的。你可能这样做是为了给子类中的属性提供与其父类中相同属性不同的默认值，或者给子类中的操作提供与其父类相同操作不同的功能。这种行为被称为重写（overriding）。

例如，假设你有一个类 A：

```php
class A
{
    public $attribute = 'default value';
```

## 在 PHP 中实现继承

```php
function operation()
{
    echo 'Something<br />';
    echo 'The value of $attribute is '. $this->attribute.'br />';
}
```

如果你想更改 $attribute 的默认值并为 operation() 提供新功能，你可以创建如下类 B，它重写了 $attribute 和 operation()：

```php
class B extends A {
    public $attribute = 'different value';
    function operation() {
        echo 'Something else<br />';
        echo 'The value of $attribute is '. $this->attribute.'br />';
    }
}
```

声明 B 不会影响 A 的原始定义。现在考虑以下代码行：
`$a = new A();`
`$a->operation();`

这些行创建了一个类型 A 对象并调用它的 operation() 函数。这产生了：
Something
The value of $attribute is default value

证明了创建 B 并没有改变 A。如果你创建一个类型 B 的对象，将得到不同的输出。

这段代码
```php
$b = new B();
$b->operation();
```

产生了：
Something else
The value of $attribute is different value

正如在子类中提供新的属性或操作不会影响父类一样，在子类中重写属性或操作也不会影响父类。

子类将继承其父类的所有属性和操作，除非你提供了替换方案（replacements）。如果你提供了替换定义，它将具有优先级并重写原始定义。

## 第 6 章 面对象化 PHP

`parent` 关键字允许你调用父类中操作的原始版本。例如，要从类 B 调用 A::operation，你将使用

```php
parent::operation();
```

然而，产生的输出是不同的。虽然你从父类调用了该操作，但 PHP 使用的是当前类的属性值。因此，你得到了如下输出：

```
Something
The value of $attribute is different value
```

继承可以是深层级的。你可以想象地声明一个类 C 继承自 B，因此继承了 B 以及 B 的父类 A。类 C 可以再次从其父类继承哪些属性和操作来进行重写和替换。

## 使用 final 防止继承和重写

PHP 使用 `final` 关键字。当你在函数声明前面使用此关键字时，该函数不能在任何子类中被重写。例如，你可以将其添加到上一个示例中的类 A 中，如下所示：

```php
class A {
    public $attribute = 'default value';
    final function operation() {
        echo 'Something<br/>';
        echo 'The value of $attribute is ' . $this->attribute.'<br/>';
    }
}
```

使用这种方法可以防止你在类 B 中重写 operation()。如果你尝试这样做，将得到以下错误：

```
Fatal error: Cannot override final method A::operation()
```

你还可以使用 `final` 关键字来防止类完全被子类化。要防止类 A 被子类化，你可以如下所示添加：

```php
final class A {...}
```

如果你随后尝试继承 A，你将得到类似下面的错误：

```
Fatal error: Class B may not inherit from final class (A)
```

## 理解多重继承

少数面向对象的语言（特别是 C++、Python 和 Smalltalk）支持真正的多重继承，但大多数语言一样，PHP不支持。这意味着每个类只能继承一个父类。对于多少个类共享同一个父类没有限制。这似乎并不显而易见。图 6.1 显示了名为 A、B 和 C 的三个类可以继承的三种不同方式。

![](img/654520c37415debd4290b9b4aa2c03f2_204_0.png)

图 6.1 PHP 不支持多重继承

左侧组合显示 C 继承 B，B 又继承 A。每个类至少有一个父类，因此这是有效的继承。

中间组合显示 B 和 C 都继承 A。每个类最多有一个父类，因此这是有效的继承。

右侧组合显示 C 同时继承 A 和 B。在这种情况下，C 有两个父类，因此是无效的。

从维护的角度来看，多重继承可能极其混乱，因此开发了各种机制来利用多重继承的优势，而不付出维护成本。PHP 支持两种此类多重继承的机制：接口（interfaces）和特质（traits）。

## 实现接口

如果你需要实现多重继承中的功能，你可以在 PHP 中通过接口来实现。它们被视为多重继承的变通方案，与包括 Java 在内的面向对象语言支持的接口实现相似。

接口的概念是它指定了一组实现接口的类必须实现的函数。例如，你可能决定有一组类能够显示自己。与其拥有一个供继承并重写的 display() 函数的父类，不如实现如下接口：

```php
interface Displayable {
    function display();
}
```

```php
class webPage implements Displayable
{
    function display() {
        // ...
    }
}
```

这个示例说明了间接的多重继承，因为 webPage 类可以继承一个类并实现一个多个接口。如果你没有实现接口中指定的方法（在本例中为 display()），你将得到致命错误。

## 使用 Traits

Traits 是一种获取多重继承优点而无需承担相关痛苦的方法。在 trait 中，你可以将可能在多个类中重用的功能组合在一起。类可以组合多个 traits，traits 之间也可以互相继承。Traits 是代码复用的极佳构建模块。

接口和 traits 的关键区别在于 traits 包含了实现，而不仅仅是指定一个必须实现的接口。

创建方式与类相同，但使用 `trait` 关键字，例如：

```php
trait logger
{
    public function logmessage($message, $level='DEBUG')
    {
        // 将 $message 写入日志
    }
}
```

使用这个 trait，你可以这样写代码：

```php
class fileStorage
{
    use logger;

    function store($data) {
        // ...
        $this->logmessage($msg);
    }
}
```

fileStorage 类可以通过声明自己的方法来覆盖 logmessage() 方法，但你需要注意的是，如果 fileStorage 类从父类继承了 logmessage() 方法，默认情况下，trait 的 logmessage() 方法将

