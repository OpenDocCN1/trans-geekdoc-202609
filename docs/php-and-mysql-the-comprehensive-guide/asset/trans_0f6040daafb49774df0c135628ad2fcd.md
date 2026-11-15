

- PHP 8 自动为使用 `__toString()` 的类添加新的 `__Stringable` 接口（`https://wiki.php.net/rfc/stringable`）。
- PHP 8.1 添加了将属性声明为 `readonly` 的选项。在 PHP 8.2 中，`readonly` 也成为了类级别的选项。
- 从 PHP 8.1 开始，对象也可以用作静态变量、参数默认值，以及属性的全局常量和参数。
- 在 PHP 8.1 中，动态设置的属性被归类为已弃用。不过，可以通过设置 `#[AllowDynamicProperties]` 特性专门为某个类允许此行为。
- 从 PHP 8.1 开始，类中的常量也可以标记为 `final`。
- 从 PHP 8.3 开始，常量也可以使用数据类型进行类型声明。
- 在 PHP 8.3 中，`#[Override]` 特性允许你标记一个（顾名思义）重写另一个方法的方法。

## 11.2 类和对象：基本概念

顾名思义，_对象_ 是面向对象编程的核心。最好将对象视为某种真实存在的事物。例如，你桌上或桌下的电脑就是一个对象。现在，用编程语言无法完全描述一台电脑。即使是电脑的三维模型也无法涵盖其所有方面。例如，缺少了风扇特有的嗡嗡声。

但是，面向对象编程的目的并不是精确描述，而是使用相关对象的某些方面。对象由多个 _属性_ 组成。例如，电脑的一个属性可以是所使用的 CPU。对象还具有 _方法_。与函数类似，方法包含功能，并为对象提供该功能。例如，电脑可以具有 `start()` 方法。由于有圆括号，你已经可以看出属性和方法之间的区别了。

但这与 _类_ 这个术语有什么关系呢？类定义了对象的结构。_结构_ 是指对象的属性和方法。这意味着 `computer` 类为所有单个电脑定义了属性和方法。然而，属性尚未赋值。类仅指定结构。特定的电脑（例如你的个人电脑）则是一个对象（参见图 11.1）。

对象是类的 _实例_。可以说实例“属于”类，并且对象必须相应地 _实例化_。当然，可以从一个类实例化任意数量的对象。这是面向对象编程灵活性的一部分。

![](img/ae7820c36e8f24c1623d26668b28e80e_308_0.png)

**图 11.1 类与对象的关系**

### 11.2.1 PHP 中的类和对象

目前为止，这全都是理论。现在让我们来看一些代码，以便你能更好地了解面向对象编程。以下代码创建一个类，该类具有一个 CPU 属性和一个 `start()` 方法：

```php
class Computer {
    public $CPU = "The CPU";
    public function start() {
        echo "Computer started";
    }
}
```

表示类的 class 关键字至关重要。¹ 属性使用 public 关键字定义并赋予值。在此上下文中，public 表示该属性可以从类外部访问。² 你可以为每个对象调整此值。方法的定义方式与函数完全相同。

你现在必须创建（或实例化）此类的一个对象才能使用它。这涉及 new 关键字：

```php
$MyComputer = new Computer();
```

新对象被赋值给一个变量。语法如下：

```php
$Object = new Class();
```

1 类也有命名空间。它们用于在命名空间内组织不同的类。这样做的目的是提供更好的概览。有关详细信息，请参阅第 11.5 节。

2 将在 11.3.4 节中详细介绍。

要访问方法或属性，PHP 对方法使用以下语法：

```php
$Object->Method();
```

对属性则如下：

```php
$Object->Property;
```

然后像这样调用 `Computer` 类的 `start()` 方法：

```php
$MyComputer->start();
```

![](img/ae7820c36e8f24c1623d26668b28e80e_309_0.png)

**图 11.2 方法返回输出**

> 注意
>
> PHP 使用一种有些不寻常的语法，即减号加上大于号——也就是箭头 (`->`）。相比之下，基于 C 的语言通常对方法使用点语法：
> Object.method()
> 对属性则为：
> Object.property
>
> 不过，转换并不太复杂。在这方面，即使是新手也应该能够很好地应对 PHP 语法。

### 11.2.2 属性

属性可以读取和更改。以下脚本读取一个属性并将其输出。

```php
<?php
class Computer {
public $CPU = "The CPU";
public function start() {
echo "Computer started";
}
}

$MyComputer = new Computer();
echo $MyComputer->CPU;
?>
```

**列表 11.1 读取属性 ("properties.php")**

因此，输出结果是屏幕上显示的文本 "The CPU"。

> 注意
>
> public 关键字将属性定义为公开。要以绝对纯净的面向对象方式工作，不应直接读取属性，而应将其定义为 private（第 11.3.4 节），然后使用方法读取它。PHP 4 仍保留旧的 var 关键字，其功能等同于 public，但不应再使用。

要更改属性，只需使用赋值运算符 (=) 为其分配新值。以下脚本更改电脑的 CPU 属性，并在更改前后输出其值，如图 11.3 所示。

```php
<?php
class Computer {
public $CPU = "The CPU";
public function start() {
echo "Computer started";
}
}

$MyComputer = new Computer();
echo $MyComputer->CPU . "<br />";
$MyComputer->CPU = "3 GHz";
echo $MyComputer->CPU;
?>
```

**列表 11.2 更改属性的值 ("properties_change.php")**

![](img/ae7820c36e8f24c1623d26668b28e80e_310_0.png)

**图 11.3 "CPU" 属性的值已更改**

> 注意
>
> 属性的值仅更改相应对象的值。其他对象仍具有类中指定的属性值：

```php
$MyComputer = new Computer();
$MyComputer->CPU = "3 GHz";
$MyLaptop = new Computer();
echo $MyLaptop->CPU;
```

以上代码将输出 The CPU，因为仅更改了 MyComputer 对象的值，而未更改 MyLaptop 对象的值。

### 11.2.3 方法

方法可以包含任意数量的功能。如已所示，访问方式与属性非常相似。但是，使用方法可以做更多事情。

#### 方法的参数

方法可以接受任意参数（参见图 11.4）。其工作方式与函数相同。

```php
<?php
class Computer {
public function shutdown($seconds) {
echo "Computer will shut down in $seconds seconds";
}
}

$MyComputer = new Computer();
$MyComputer->shutdown(12);
?>
```

**列表 11.3 将值传递给方法 ("methods_parameters.php")**

![](img/ae7820c36e8f24c1623d26668b28e80e_311_0.png)

**图 11.4 带有参数值的消息**

与函数一样，你也可以为参数指定默认值。请参考以下简单示例。

```php
<?php
class Computer {
 function shutdown($seconds = 20) {
 echo "Computer will shut down in $seconds seconds";
 }
}
$MyComputer = new Computer();
$MyComputer->shutdown();
?>
```

**列表 11.4 带有默认值的方法 ("methods_parameters_default_value.php")**

该函数现在输出电脑将在 20 秒后关闭。默认情况下，参数按值传递。对象是唯一的例外：它们按引用传递。要将其他参数按引用传递，请在参数名前使用 &。

```php
<?php
class Computer {
 public function shutdown(&$seconds) {
 echo "Computer will shut down in $seconds seconds";
 }
}
$duration = 12;
$MyComputer = new Computer();
$MyComputer->shutdown($duration);
?>
```

**列表 11.5 方法参数作为引用 ("methods_parameters_asreference.php")**

#### 返回值

与函数的相似之处不仅如此。方法可以像函数一样使用 return 返回值。图 11.5 显示了以下示例的结果。

```php
<?php
class Computer {
 public function start($medium) {
 return "The computer starts from $medium";
 }
}
```

