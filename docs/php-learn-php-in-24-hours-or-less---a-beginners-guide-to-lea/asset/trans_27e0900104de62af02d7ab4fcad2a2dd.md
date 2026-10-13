
# PHP 类与对象进阶

## 静态属性

在 PHP 中，你可以使用类来声明属性。一个类的所有实例都拥有该类属性的各自副本。不过，你也可以为类分配**静态属性**。与普通属性不同，静态属性仅属于包含它的类。因此，程序员将静态属性称为“类属性”。要定义静态属性，请使用以下语法：

```php
class YourClass {
    static $sampleStaticVariable;
    static $sampleInitializedStaticVariable = 1;
}
```

访问静态属性时，应指明其名称及所属类。语法如下：

```php
YourClass::$sampleInitializedStaticVariable++;
print MyClass::$sampleInitializedStaticVariable;
```

运行上述脚本，屏幕将显示 `2`。

若要在类的方法内部访问成员，可使用 `self` 前缀指定属性。该前缀告知 PHP 你引用的是该属性所属的方法。语法如下：

```php
class YourClass {
    static $sampleInitializedStaticVariable = 1;
    function yourMethod() {
        print self::$sampleInitializedStaticVariable;
    }
}
$object = new YourClass();
$object->yourMethod();
```

此例将在屏幕上输出 `1`。

## 静态方法

PHP 允许将方法声明为静态。从本质上讲，静态方法仅属于包含它的类。处理此类方法时不能使用 `$this` 变量，而应使用 `self` 关键字。由于静态方法不与任何对象关联，你可以通过 `ClassName::method()` 语法在无需实例化的情况下调用它。当然，也可以在对象实例中通过 `$this->method()` 调用。请分析以下示例：

```php
class Printer {
    static function printMessage() {
        print "Hi, how are you?";
        self::printTabHere();
    }
    static function printTabHere() {
        print "\t";
    }
}
Printer::printMessage();
```

此例将在屏幕上输出 `Hi, how are you?` 及一个制表符。尽管这是一个基础示例，但它表明：即使没有类的实例，也可以在类内部通过类名调用方法（即 `printMessage()`）；此外，还演示了如何使用静态方法触发另一个方法。

## 类常量

PHP 用户早已使用全局常量。你可以使用 `define()` 定义全局常量（这在本书第一章已学习）。当前 PHP 版本支持增强的封装性以及在类中定义常量。就像静态成员一样，类常量属于类本身。此类常量**完全区分大小写**。

下面的脚本演示如何声明并访问类常量：

```php
class ColorEnumeration {
    const YELLOW = "Yellow";
    const ORANGE = "Orange";
    const PINK = "Pink";
    function showPink() {
        print self::PINK;
    }
}
print ColorEnumeration::YELLOW;
$object = new ColorEnumeration();
$object->showPink();
```

此例演示了从方法内部（使用 `self`）和通过类名（即 `ColorEnumeration`）两种方式访问类常量的技巧。

请记住：一旦定义了常量，就无法更改或删除它。程序员在处理枚举或配置值时会使用常量。在这些场景下，永久存储数据是必须的。

## 克隆对象

创建新对象时，返回的值作为该对象的句柄或标识号。以下代码说明了这一概念：

```php
class YourClass {
    public $sample_variable = 2;
}
$object_1 = new YourClass();
$object_2 = $object_1;
$object_2->sample_variable = 3;
print $object_1->sample_variable;
```

因为 `$object_1` 是一个对象的句柄，`$object_2` 将成为另一个句柄。因此，修改后者将会修改这些变量所指向的同一个对象。运行上述脚本，屏幕将显示 `3`。

在某些情况下，你确实需要复制一个对象。如何完成此任务？在 PHP 中，需要使用 `clone` 结构。这个预装的操作符会自动生成一个对象的实例。新实例将拥有原对象的所有属性。此外，你可以使用 `__clone()` 方法对新对象执行修改。

> **重要提示**：复制引用会产生另一个引用。这种方式无法获得“深度”复制。这意味着，如果你复制一个指向另一个变量的引用，生成的对象也将指向该变量。

## 多态

有人认为多态是面向对象编程最关键的方面之一。由于可以在代码中使用继承和类，描述现实场景变得简单。PHP 代码不再只是数据和函数的简单集合。多态能为你做很多事。例如，它可以帮助你通过复用代码完成项目，或以最少的控制语句编写强大的程序。请分析以下示例：

```php
class Dog {
    function arf() {
        print "arf";
    }
}
class Bird {
    function tweet() {
        print "tweet";
    }
}
function giveTheSound($object) {
    if ($object instanceof Dog) {
        $object->arf();
    } else if ($object instanceof Bird) {
        $object->tweet();
    } else {
        print "The object is invalid";
    }
    print "\n";
}
giveTheSound(new Dog());
giveTheSound(new Bird());
```

运行此脚本，屏幕将显示：

```
arf
tweet
```

假设你需要通过添加更多动物来扩展上例。你需要为每种新动物创建一个 `else if` 块。因此，你要创建这些动物的新实例并编写更多语句来调用它们的声音。

多态可以简化上述任务。从本质上讲，此特性允许你将一个类的内容传递给其他类。在这里，你可以将一个类的属性和方法传递给你想创建的新类。

此时，你需要创建一个名为 `Animals` 的类，并建立这个父类与其具体对象之间的关系。可以通过输入 `extends`（即另一个 PHP 关键字）来执行此继承。语法如下：

```php
class ChildClass extends ParentClass {
    // ...
}
```

让我们使用“继承”重写前面的代码：

```php
class Animals {
    function giveSound() {
        print "The program must re-implement this method in the inheriting classes.";
    }
}
class Dog extends Animals {
    function giveSound() {
        print "arf";
    }
}
class Bird extends Animals {
    function giveSound() {
        print "tweet";
    }
}
function rightSound($object) {
    if ($object instanceof Animals) {
        $object->giveSound();
    } else {
        print "The object is invalid";
    }
    print "\n";
}
rightSound(new Dog());
rightSound(new Bird());
```

输出如下：

```
arf
tweet
```

采用这种方法，无论你想向代码中添加多少动物，都无需修改 `rightSound()`。因为 `instanceof Animals` 涵盖了你可能添加的任何动物。

# 第 5 章：如何处理异常

程序员认为异常处理是软件开发中最困难的部分。通常，错误（如网络故障、数据库故障、程序 Bug 等）给程序开发人员带来严重问题。例如，开发人员需要针对发生的错误做出决策、插入检查以防止故障、并调用正确的函数进行管理。此外，程序员还需要确保程序在处理错误后能正常工作。
