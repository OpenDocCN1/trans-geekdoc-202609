

面向对象范式也支持多态性的概念。多态性是指若干相关的类都拥有一个同名方法的特性。例如，我们可以创建多个类，它们负责在屏幕上绘制不同的形状。所有形状都有一个名为 `draw()` 的方法，用于将它们显示出来。程序员可以调用其中任意一个类的 `draw()` 方法，并知道该方法会显示对应的形状。不过，最终生成的图像会因发送消息的形状类不同而有所差异。

创建类并不是事情的终点。类实际上是一种模板，它定义了可以保存哪些信息以及能够执行哪些操作。类本质上是一种精密的“变量类型”。正如变量被设计为保存特定类型的数据，并且你可以对特定变量执行某些操作一样，我们可以构建包含特定数据（保存在数据成员中）的类，并为其关联相应的方法，从而以不同方式操作这些数据。然而，在使用变量之前，你需要创建该变量的实例，对于类也是如此。类是模板，要使用它，你必须用一些具体数据创建该类的一个实例。类的实例称为对象。

大多数面向对象编程语言都会实现前面描述的特性。不过，根据你使用的编程语言不同，所使用的术语也会有所差异。例如，类方法、函数和过程都用于描述同一事物。同样，数据成员、字段和变量这些术语也意味着相同的东西。

## 16.2 PHP 与面向对象

PHP 保持了简单性，并与 PHP 语言的其他方面保持一致。在定义类时，程序员需要指定该类所包含的数据成员和方法（变量和函数）。类的实例被称为对象。

### 创建类

用于定义类的关键字是 `class`。其后紧跟类名，类名可以是任何不是 PHP 保留字的名称。类名后面是一对花括号，其中包含类的数据成员和方法的定义：

```
class name {
}
```

如果我们要创建一个名为 `person` 的类，那么可以这样开头：

```
class person {
}
```

这个类目前还做不了任何事情，因为我们还没有为这个类分配任何方法或数据成员。在这样做之前，我们需要了解数据成员和方法的可见性。

### 可见性

方法或数据成员的可见性可以通过在声明前加上以下关键字来定义：

```
public
protected
private
```

`public`（公共）项可以在任何地方访问，既能在类内部也能在类外部访问。`protected`（受保护）将访问限制为继承该类的类以及定义该项的原始类。`private`（私有）将方法或数据成员的可见性仅限制为定义该成员的类。

如果我们在类中包含一些数据成员，通常会将它们设置为私有，因为我们希望利用面向对象范式的封装特性。

### 类的数据成员和方法

以下脚本展示了我们的类及其中定义的一些数据成员。所有类成员都必须放在类定义内部，即起始花括号和结束花括号之间：

```
class person {
    private $strFirstname = "Simon";
    private $strSurname = "Stobart";
}
```

类也可以关联方法。每个类方法的定义方式与在类外部定义的函数完全相同。类方法必须定义为 `public`、`private` 或 `protected`。

考虑我们包含两个成员函数的类：

```
class person {
    private $strFirstname = "Simon";
    private $strSurname = "Stobart";

    function getFirstname() {
    }
    function getSurname() {
    }
}
```

注意
类成员在声明中未指定任何可见性时，默认定义为 `public`。这就是为什么上面示例中的两个方法看起来没有指定可见性，但实际上它们是公共的。

目前这些函数没有任何代码，因此还不会执行任何操作。我们希望它们能够分别返回数据成员 `$strFirstname` 和 `$strSurname` 的值。你可能会认为可以直接在 `getFirstname()` 方法中写入一个这样的返回语句：

```
function getFirstname() {
    return $strFirstname;
}
```

不幸的是，这行不通。如果我们将变量 `$strFirstname` 定义为 `getFirstname()` 方法的一部分，上面的代码片段是没问题的。但事实并非如此，它是一个数据成员（定义在类内部但任何类方法之外）。要解决这个问题，我们需要引入一个名为 `$this` 的新伪变量。

### $this

伪变量 `$this` 是对调用对象的引用（通常是方法或数据成员所属的对象）。要访问类的数据成员，我们使用 `$this`，后面跟运算符 `->`，然后是变量名，例如：

```
$this->strFirstname;
```

| 注意 | 请注意 `$` 符号位于 `this` 前面，而不是紧跟数据成员名称之前。 |
|------|------------------------------------------------------------|

我们现在可以修改类方法，使其正确使用 `$this` 伪变量，如下所示：

```
class person {
    private $strFirstname = "Simon";
    private $strSurname = "Stobart";

    function getFirstname() {
        return $this->strFirstname;
    }
    function getSurname() {
        return $this->strSurname;
    }
}
```

现在，我们有了一个包含两个数据成员和两个方法的类。这些方法被设计为返回各自数据成员的值。然而，如果你在浏览器中查看上述脚本的输出，你会非常失望，因为什么都不会显示。这是因为虽然我们正确创建了一个类，但我们并没有使用它。我们现在需要做的是创建该类的一个实例，即对象。

### 使用类

要使用我们的 `person` 类，我们需要创建该类的一个对象。为此，我们需要使用关键字 `new`。必须创建一个新对象并将其赋值给一个变量：

```
variable = new class
```

所以，以我们的示例类为例，我们可以这样写：

```
$objSimon = new person();
```

上面的代码基本上表示我们希望创建一个名为 `$objSimon` 的变量，类型为 `person`。这等同于创建一个新变量：

```
$strName;
```

现在，如果你还记得我们的类有两个方法：`getFirstname()` 和 `getSurname()`。要调用这些方法，我们使用以下语法：

```
objectName->methodName()
```

因此，在我们的示例类中，我们可以写以下任意一种：

```
$objSimon->getFirstname();
$objSimon->getSurname();
```

为了访问方法返回的值，我们需要输出结果或将返回的值复制到变量中。以下脚本包含了我们完整的类、创建的对象以及对象方法的调用：

```
<?php
// File: example16-1.php

class person {
    private $strFirstname = "Simon";
    private $strSurname = "Stobart";

    function getFirstname() {
        return $this->strFirstname;
    }
    function getSurname() {
        return $this->strSurname;
    }
}
$objSimon = new person;
echo "<p>Firstname: " . $objSimon->getFirstname() . "</p>";
echo "<p>Surname: " . $objSimon->getSurname() . "</p>";
?>
```

上述脚本的输出如图 16.2 所示。

这样就可以了。如果我想更改数据成员 `$strFirstname` 和 `$strSurname` 的值，我们可以尝试这样写：

```
$objSimon->strFirstname = "Tim";
```

不幸的是，这会产生一条错误信息，因为数据成员 `strFirstname` 被定义为 `private`（私有），因此无法在类外部访问。为了允许我们修改对象的数据成员值，我们需要编写一些方法来实现这一点。

