

```
$MyComputer = new Computer();
echo $MyComputer->start("a stick");
?>
```

## 清单 11.6 带有返回值的方法 ("methods_return.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_313_0.png)

## 图 11.5 仅在返回值后才会产生输出

> **提示**
> 当然，为函数提到的其他细节在此也同样适用。例如，如果您需要多个返回值，可以使用数组来实现。

## "$this": 访问属性和方法

到目前为止，方法仅出现在对象之内，没有交互。然而，当方法与其他属性和方法交互时，才真正发挥作用。如果要在方法中调用同一对象的属性或方法，则需要对该对象的引用。但是，由于可以从一个类创建不同的对象，您预先不知道对象的名称。对于这种情况，有 $this 关键字，它提供对当前对象的引用。

With

```
$this->Property
```

or

```
$this->method()
```

您可以使用它们来访问类的其他属性和方法。在下面的简单实用示例中，该方法返回一个字符串，其中包含 CPU 属性的值等内容（参见图 11.6）。

```
<?php
class Computer {
public $CPU = "The CPU";
public function getCPU() {
return "The computer is equipped with a $this->CPU CPU.";
}
}
$MyComputer = new Computer();
$MyComputer->CPU = "4 GHz";
echo $MyComputer->getCPU();
?>
```

## 清单 11.7 "this" 的用法 ("methods_this.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_314_0.png)

## 图 11.6 属性已包含在使用 "$this" 的方法输出中

> **提示**
> 使用以 `get` 开头的方法读取属性是面向对象编程中的常见做法。其对应方法通常是以 `set` 开头并设置属性值的方法。

## 重载

PHP 不支持函数的经典重载。这意味着您无法创建多个各自具有不同参数的方法。但是，可以模拟重载。对于参数数量，您可以使用默认值或用于读取可变数量参数的函数来实现重载。

不过，您可以使用类型识别函数并借助情况区分来筛选不同的数据类型。以下小示例检查秒数是否指定为数字。如果是，脚本会附加带有单位的字符串。

```
class Computer {
public function shutdown($seconds) {
if (is_integer($seconds)) {
$seconds = $seconds . " seconds";
}
echo "Computer is shutting down in $seconds";
}
}
```

## 清单 11.8 使用不同数据类型的重载 ("objects_overload.php")

这种重载方法的优点在于，无论是以下调用：

```
$MyComputer = new Computer();
$MyComputer->shutdown(12);
```

还是带有单位的调用：

```
$MyComputer = new Computer();
$MyComputer->shutdown("12 seconds");
```

都会产生相同的输出，如图 11.7 所示。

![](img/ae7820c36e8f24c1623d26668b28e80e_315_0.png)

## 图 11.7 单位也被附加

> **提示**
> 您当然可以像这里所示模拟重载。这有时很实用。但是，所需的大量情况区分未必优雅。因此，您应该谨慎使用此工具。

## 11.2.4 继承

迄今为止，您只见过一个孤立的类。但在实践中，类层次结构会迅速出现。这意味着一个类会继承另一个更高级别类的属性和方法。此过程称为继承。

请考虑一个简单示例：Computer 类适用于所有计算机。但是，笔记本电脑或台式机等特殊计算机可以有自己的属性和方法。例如，笔记本电脑仍然集成显示屏。而台式机则可以（更轻松地）拆卸。

这种类层次结构也可以在 PHP 编程中表达。为此使用 extends 关键字。4 其理论用法如下：

> 4 PHP 只支持单继承。这意味着没有类可以从多个类继承。

```
class Name extends OtherClass {
    private $Property;
    public function Method() {
        instructions;
    }
}
```

新类 *扩展* 一个现有类。这意味着它采用该类的所有属性和方法，然后定义自己的属性和方法。

请考虑以下小示例。

```
<?php
class Computer {
    public $CPU = "The CPU";
    public function start() {
        return "Computer is started.";
    }
}

class Laptop extends Computer {
    public $Display = "15 inch";
}

$MyLaptop = new Laptop();
$MyLaptop->CPU = "2.5 GHz Mobile";
echo "CPU: $MyLaptop->CPU<br/>";
echo "Display: $MyLaptop->Display";
?>
```

## 清单 11.9 使用 "extends" 的继承 ("inheritance.php")

在示例中，Laptop 类扩展 Computer 类。Laptop 被赋予一个额外属性。输出（参见图 11.8）随后访问此属性，但也访问 Computer 类的父类 CPU 属性。

![](img/ae7820c36e8f24c1623d26668b28e80e_316_0.png)

## 图 11.8 脚本输出自身属性和父类属性

## 重写

通过继承，您可以在子类（继承类）中重写父类的属性和方法。为此，只需创建一个与父类中对应项同名的属性或方法即可。在以下示例中，CPU 属性和 start() 方法均被重写；图 11.9 显示了结果。

```
<?php
class Computer {
public $CPU = "The CPU";
public function start() {
return "Computer is started.";
}
}
class Laptop extends Computer {
public $CPU = "2.5 GHz Mobile";
public function start() {
return "Laptop is started.";
}
}
$MyLaptop = new Laptop();
echo "CPU: $MyLaptop->CPU<br />";
echo $MyLaptop->start();
?>
```

## 清单 11.10 重写属性和方法 ("inheritance_overwrite.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_317_0.png)

## 图 11.9 属性和方法已被重写

## 间接访问方法

如果要从方法中访问父类的方法，则需要对该类的引用。您可以实例化一个对象或使用冒号语法直接访问类，但那样您始终需要知道类的名称。更聪明的替代方案是使用 parent 关键字。这使您可以访问父类，而无需知道其名称。

```
<?php
class Computer {
    public $CPU = "The CPU";
    public function start() {
        return "Computer is started.";
    }
}
class Laptop extends Computer {
    public function start() {
        return "Laptop: " . parent::start();
    }
}
$MyLaptop = new Laptop();
echo $MyLaptop->start();
?>
```

## 清单 11.11 通过 "parent" 访问 ("inheritance_parent.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_318_0.png)

## 图 11.10 输出也基于父类的方法

> **注释**
> 在这种情况下，使用 `$this` 关键字引用类的属性不起作用，因为 `$this` 始终引用当前对象。但是，通过直接链接到类的方法，没有对象。

## 11.3 进阶

您现在了解了面向对象的基础知识。现在是时候深入了解更精细的细节了。这包括某些方法，还包括接口和抽象类。

### 11.3.1 克隆对象

PHP 按引用传递对象。这在 PHP 4 中最初有所不同，PHP 4 中将对象视为值。

> **注释** 您可以在本书资料中找到一个测试示例（参见前言）。它名为 objects_values.php。

但是，如何将对象作为值传递给函数呢？为此，您需要克隆对象。为此使用 clone 关键字。在这种情况下，会创建原始实例的副本并将其传递给函数。您可以在图 11.11 中看到结果。

```
<?php
class Computer {
public $CPU = "The CPU";
public function start() {
echo "Computer is started.";
}
}
function change($object) {
$object->CPU = "4 GHz";
echo "In the function: $object->CPU<br />";
}
$MyComputer = new Computer();
change(clone $MyComputer);
echo "Outside the function: $MyComputer->CPU";
?>
```

## 清单 11.12 "clone" 命令 ("clone.php")

但是，克隆不仅用于将对象作为值传递；还可以用于根据需要多次复制对象实例。

![](img/ae7820c36e8f24c1623d26668b28e80e_319_0.png)

## 图 11.11 函数内适用克隆对象的值；函数外适用原始对象的值

### 11.3.2 构造函数

构造函数是在创建类的对象时执行的方法。为此使用 __construct() 方法。它可以接受用于实例化对象的任何参数。

