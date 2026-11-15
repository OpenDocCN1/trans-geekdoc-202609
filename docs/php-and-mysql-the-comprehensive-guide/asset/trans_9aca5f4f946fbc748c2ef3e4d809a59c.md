

在以下示例中，对象传递字符串 4 GHz。然后将其分配给 CPU 属性。构造方法随后输出一段文本。最后，输出 CPU 的值。

```
<?php
class Computer {
public $CPU = "The CPU";
public function __construct($value) {
$this->CPU = $value;
echo "Object instantiated<br />";
}
}
$MyComputer = new Computer("4 GHz");
echo $MyComputer->CPU;
?>
```

清单 11.13 __construct() ("constructor.php")

该清单产生以下输出：

对象已实例化
4 GHz

## 属性提升

在 PHP 8 中，构造方法中定义属性有一种简写形式，即所谓的属性提升。原理很简单：您可以直接在构造方法中定义属性，甚至可以定义为公共可用属性。

使用此表示法，上一节的清单减少了两行。以下三行：

```
public $CPU = "The CPU";
public function __construct($value) {
$this->CPU = $value;
```

变为一行：

```
public function __construct(public $CPU = "The CPU") {
```

需要注意的是，$CPU 属性的访问方式与在构造方法外部定义的属性完全相同：

```
echo $MyComputer->CPU;
```

以下清单提供完整示例。

```
<?php
class Computer {
public function __construct(public $CPU = "The CPU") {
echo "Object instantiated<br />";
}
}
$MyComputer = new Computer("4 GHz");
echo $MyComputer->CPU;
?>
```

清单 11.14 在构造方法中定义属性 ("constructor_property_promotion.php")

对于单个属性，这并不特别，但如果需要为类定义许多初始属性，您将获得更多清晰度。

## 11.3.3 析构函数

当对象被销毁时，__destruct() 析构方法始终被使用。例如，当使用 unset(object) 解除对象时，它也会作出反应（参见图 11.12）。

```
<?php
class Computer {
public $CPU = "The CPU";
public function __destruct() { echo "Destructor active"; }
}
$MyComputer = new Computer();
unset($MyComputer);
echo "$MyComputer->CPU<br />";
?>
```

清单 11.15 "__destruct()" ("objects_destructor.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_321_0.png)

图 11.12 析构函数输出其消息；"CPU" 已被销毁

## 11.3.4 private、protected 等等

private、public、static 和 protected 关键字在面向对象编程中起着重要作用。它们用于控制对属性和方法的访问。自 PHP 7.1 起，它们也被允许用于常量的访问控制。

### "private" 和 "public"

在 PHP 中，您可以将属性、常量和方法标记为 private。此类 private 属性或方法只能由对象内部的另一个方法调用，不能从外部调用。

在以下示例⁵中，CPU 属性被标记为 private。

```
<?php
class Computer {
    private $CPU = "The CPU";
    function getCPU() {
        return $this->CPU;
    }
}
$MyComputer = new Computer();
echo $MyComputer->CPU;
echo $MyComputer->getCPU();
?>
```

清单 11.16 标记为 "private" 的属性 ("private.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_322_0.png)

图 11.13 访问 private 属性会导致错误

5 视错误级别而定，此处可能会出现两个提示。

在这种情况下，由于访问 private 属性失败，脚本会产生图 11.13 所示的错误消息。getCPU() 方法展示了如何实际访问 private 属性。如果注释掉直接访问的那一行，脚本就会正常工作，如图 11.14 所示：

```
//echo $MyComputer->CPU;
```

![](img/ae7820c36e8f24c1623d26668b28e80e_323_0.png)

图 11.14 方法正确输出属性

private 也可用于方法。然后必须在另一个方法中使用该方法。请参考以下简单示例；输出如图 11.15 所示。

```
<?php
class Computer {
private function format() {
return "Hard disk formatted";
}
function start() {
return "Computer started, ".$this->format();
}
}
$MyComputer = new Computer();
echo $MyComputer->start();
?>
```

清单 11.17 标记为 "private" 的方法 ("private_method.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_323_1.png)

图 11.15 private 方法的输出通过 public 方法读取

> **注意**
> 默认情况下，每个属性或方法都是 public。但是，您还应使用 public 关键字明确将属性或方法标记为 public：

```
class Computer {
public $CPU = "The CPU";
}
```

在面向对象编程中，您应始终将属性标记为 `private`，并仅通过标记为 `public` 的方法使其可访问。这种属性封装是良好编程风格的一部分，可帮助您在脚本中保持秩序。使用对象模型⁶ 和设计模式⁷ 时也有帮助。读取属性的方法常用命名约定是 `getPropertyName()`，设置属性的方法是 `setPropertyName(Value)`。这并非强制性，而仅是一种约定。

6 对象模型对应用程序、相关类和层次结构进行建模。用于此类模型的一种语言是 UML。
7 设计模式是解决面向对象编程中常见问题的方法。它们可以在 PHP 中使用，也可以在任何其他面向对象编程语言中使用。有关此主题的更多信息，请参见第 12 章。

### "static"

用 `static` 标记的属性和方法是 *静态的*，因为它们通过类名在类外部访问。您不需要对象。以下清单及其在图 11.16 中的输出展示了一个简单示例。

```
<?php
class Computer {
static $CPU = "The CPU";
static function start() {
return "Computer is started";
}
}

echo Computer::$CPU ."<br />";
echo Computer::start();
?>
```

清单 11.18 静态属性和方法 ("static.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_324_0.png)

图 11.16 访问静态属性和方法

> **注意**
>
> 在标记为 static 的方法中，无法使用 $this，因为没有对对象的引用。但是，self 可用作晚期静态绑定的一部分。有关晚期静态绑定的更多信息，请参见第 11.3.6 节。

### "protected"

如果使用 private，则属性或方法仅适用于定义它的那个类。protected 与 private 具有相同的外部保护效果，但此类属性或方法也适用于类层次结构中的所有类。

```
<?php
class Computer {
    protected $CPU = "3 GHz Mobile";
}

class Laptop extends Computer {
    public function getCPU() {
        return "The following CPU is on board: ".$this->CPU;
    }
}

$MyLaptop = new Laptop();
echo $MyLaptop->getCPU();
?>
```

清单 11.19 "protected" 的使用 ("protected.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_325_0.png)

图 11.17 读取来自父类的 CPU

在前面的示例中，用 protected 保护的属性定义在父类中。如果反过来，整个事情也能行吗？让我们检查一下：

```
class Computer {
    public function getCPU() {
        return "The following CPU is on board: ".$this->CPU;
    }
}
```

```
class Laptop extends Computer {
 protected $CPU = "3 GHz Mobile";
}
```

答案：是的，可以。protected 为整个类层次结构（即父类和所有继承类）开放属性或方法。

> 注意
> protected 对方法的使用与对属性的使用类似。您只需在方法前写上关键字：
> protected function innerCalculation() {
>  Instructions;
> }

### "final"

用 final 标记的方法不能在子类中被重写。因此，以下代码示例会导致错误，如图 11.18 所示。

```
<?php
class Computer {
 final function start() {
 return "Computer is started";
 }
 }
 class Laptop extends Computer {
 public function start() {
 return "Laptop is started";
 }
 }
 $MyLaptop = new Laptop();
 echo $MyLaptop->start();
?>
```

清单 11.20 "final" ("final.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_326_0.png)

图 11.18 "start()" 方法不得被重写

