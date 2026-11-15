

例如，`Car` 类可能仅表明汽车应该有颜色，而特定的 `myCar` 对象可能是红色的。

类与对象的区别常常让初次接触 OOP 的人感到困惑。将类视为在设计应用程序时创建的东西，而对象是在应用程序实际运行时创建和使用的，这很有帮助。

## 属性

在 OOP 术语中，类或对象的特征称为其 *属性*。属性很类似于普通变量，因为它们具有名称和值（可以是任何类型）。有些属性允许更改其值，而有些则不允许。例如，`Car` 类可能具有 `color` 和 `weight` 等属性。虽然可以通过重新喷漆来改变汽车的颜色，但汽车的重量（不包括货物或乘客）是一个固定值。

## 方法

类的行为——即与类关联的动作——称为其 *方法*。方法与函数非常相似；事实上，你在 PHP 中使用 `function` 语句来定义方法。

与函数一样，有些方法作用于作为参数传递给它们的外部数据，但对象的方法也可以访问对象的属性。例如，`Car` 类的 `accelerate` 方法可能会检查 `fuel` 属性，以确保有足够的燃料来移动汽车。然后，该方法可能会更新对象的 `velocity` 属性，以反映汽车已加速的事实。

类的方法连同其属性，统称为类的 *成员*。

## 在 PHP 中创建类和对象

虽然类和对象背后的理论可能相当复杂，但在 PHP 中创建类和对象实际上非常简单。如你所想象，你需要先创建一个类，然后再创建属于该类的对象。要创建一个类，你使用 PHP 的 `class` 关键字。这是一个非常简单的类：

```
class Car {
// Nothing to see here; move along
}
```

这段代码只是定义了一个名为 `Car` 的类，它什么也不做——它只是包含一个注释。(你很快就会向类添加一些功能。) 请注意，类定义由 `class` 关键字、类名、组成类的代码构成，并用花括号 ({ }) 包围。

*一个常见的编码标准是类名以大写字母开头，尽管你不必这样做。最重要的是保持一致。你可以在第 20 章中了解更多有关编码标准的信息。*

既然你已经定义了一个类，就可以基于该类创建对象了。要创建一个对象，请使用 `new` 关键字，后跟要基于它创建对象的类的名称。然后，你可以将此对象分配给一个变量，就像分配任何其他值一样。

下面是一个展示如何创建对象的示例：

```
class Car {
// Nothing to see here; move along
}

$beetle = new Car();
$mustang = new Car();

print_r( $beetle ); // Displays "Car Object ( )"
print_r( $mustang ); // Displays "Car Object ( )"
```

这段代码首先像以前一样定义了空的 `Car` 类，然后创建 `Car` 类的两个新实例——即两个 `Car` 对象。它将一个对象分配给名为 `$beetle` 的变量，将另一个对象分配给名为 `$mustang` 的变量。请注意，虽然两个对象基于同一个类，但它们彼此独立，并且各自存储在自己的变量中。

一旦对象被创建，就使用 `print_r()` 显示它们的内容。你还记得从第 6 章中学到的，`print_r()` 可用于输出数组的内容。它也可以用于输出对象，这对于调试面向对象代码非常有用。在这种情况下，`Car` 类是空的，因此 `print_r()` 仅显示对象基于 `Car` 类这一事实。

> 在第 7 章中，你学习了 PHP 如何按值将变量传递给函数和从函数接收变量，并按值将它们分配给其他变量，除非你明确指示按引用传递或分配它们。此规则的例外是对象，对象始终按引用传递。

## 创建和使用属性

既然你知道如何创建类，就可以开始向其中添加属性了。类属性与变量非常相似；例如，对象的属性可以存储单个值、一组值，甚至另一个对象。

## 了解属性可见性

在深入研究在 PHP 中创建属性之前，值得了解一下类的一个重要概念，即 _visibility_。PHP 中类的每个属性都可以具有三种可见性级别之一，即 public、private 和 protected：

- 公共属性可以被任何代码访问，无论该代码是在类内部还是外部。如果属性被声明为 public，则其值可以从脚本中的任何位置读取或更改。
- 类的私有属性只能被类内部的代码访问。因此，如果你创建一个声明为 private 的属性，只有同一类内部的方法可以访问其内容。(如果你尝试在类外部访问该属性，PHP 会生成一个致命错误。)
- 受保护的类属性有点像私有属性，因为它们不能被类外部的代码访问，但有一个微妙的区别：任何继承自该类的类也可以访问这些属性。(你将在本章后面了解继承。)

一般来说，尽可能避免创建公共属性是个好主意。相反，更安全的做法是创建私有属性，然后创建允许类外部代码访问这些属性的方法。这意味着你可以精确控制类属性的访问方式。你将在本章后面了解更多有关此概念的信息。不过，在接下来的几个部分中，你将主要使用公共属性，因为它们最容易理解。

## 声明属性

要向类添加属性，首先写入关键字 public、private 或 protected——具体取决于你想给属性赋予的可见性级别——后跟属性名称（前面带有 $ 符号）：

```
class MyClass {
    public $property1;     // This is a public property
    private $property2;    // This is a private property
    protected $property3;  // This is a protected property
}
```

顺便说一句，你也可以在声明属性时对其进行初始化，就像对变量所做的那样：

```
class MyClass {
    public $widgetsSold = 123;
}
```

在这种情况下，每次从 MyClass 创建新对象时，该对象的 $widgetsSold 属性默认值为 123。

## 访问属性

创建类属性后，可以使用以下语法在调用代码中访问相应对象的属性值：

```
$object->property;
```

也就是说，你写出存储对象的变量名，后跟由连字符 (-) 和大于号 (>) 组成的箭头符号，后跟属性名。(请注意，属性名称前面没有 $ 符号。)

下面是一个展示如何定义属性并设置和读取其值的示例：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Defining and Using Object Properties</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Defining and Using Object Properties</h1>

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

echo "<h2>Some properties:</h2>";
echo "<p>The Beetle's color is " . $beetle->color . ".</p>";
echo "<p>The Mustang's manufacturer is " . $mustang->manufacturer . ".</p>";
echo "<h2>The $beetle Object:</h2><pre>";
print_r( $beetle );
echo "</pre>";
echo "<h2>The $mustang Object:</h2><pre>";
print_r( $mustang );
echo "</pre>";
?>
</body>
</html>
```

你可以在图 8-1 中看到此脚本的输出。脚本定义了一个名为 Car 的类，具有两个公共属性 $color 和 $manufacturer。然后它创建一个新的 Car 对象并将其分配给名为 $beetle 的变量，并将 $beetle 的 $color 和 $manufacturer 属性分别设置为 "red" 和 "Volkswagen"。接下来，脚本创建另一个 Car 对象，将其分配给 $mustang，并将其 $color 属性设置为 "green"，将其 $manufacturer 属性设置为 "Ford"。

现在两个对象已创建并设置了属性，脚本显示了几个属性的值：$beetle 对象的 $color 属性 ($beetle->color) 和 $mustang 对象的 $manufacturer 属性 ($mustang->manufacturer)。最后，脚本使用 print_r() 显示这两个对象；请注意 print_r() 显示对象属性的方式与其显示数组键和值的方式非常相似。

