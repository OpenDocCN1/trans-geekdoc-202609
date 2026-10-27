
这是我目前拥有的 方法：

```
public function getCaliber() { return $this->caliber; $this->notForRifle = false; return(round($this->weight,0)); }
```

## 创建 getBulletType 方法

下一个我们需要添加的方法是一个可以让我们确定枪支子弹类型的方法。该方法的语法如下：`public function getBulletType()`，它返回一个包含子弹类型的整数。

这是我目前创建的内容：

```
public function getBulletType() { return $this->bulletType; }
```

## 创建 getChainMethod 方法

下一个我们将添加的方法将允许我们检查武器的链条。该方法的语法如下：`public function getChainMethod()`，它返回一个整数表示是否有链条，以及一个包含链条长度的整数。

这是我目前拥有的内容：

```
public function getChainMethod() { return $this->chain; $this->lengthOfChain = ($this->chain + 50); return(round($this->lengthOfChain,0)); }
```

## 创建 getCup 方法

下一个我们将添加的方法可以让我们弄清楚枪支有什么样的杯。该方法的语法如下：`public function getCup()`，它返回一个包含枪支杯的整数。

这是我目前拥有的内容：

```
public function getCup() { return $this->cup; }
```

## 创建 getDistance 方法

下一个我们将实现的方法将允许我们弄清楚武器距离多远。该方法的语法如下：`public function getDistance()`，它返回一个包含武器距离（以米为单位）的整数。

这是我目前拥有的内容：

```
public function getDistance() { return $this->distance; }
```

## 创建 GetMaxCapacity 方法

下一个我们将实现的方法将允许我们检查枪支的弹药容量是否达到最大容量。该方法的语法如下：`public function getMaxCapacity()`，它返回一个包含枪支弹药最大容量的整数。

这是我目前拥有的内容：

```
public function getMaxCapacity() { return $this->maxAmmo; }
```

## 创建 GetName 方法

如果你打开浏览器，将其指向我的主页 http://danielperrett.com，然后打开浏览器的 JavaScript 控制台（或开发者工具），你会看到 the_construct 函数在页面加载时已被调用。

但这是怎么可能的？我上面写的字符串甚至还不存在！实际上，它确实存在，就在这句话的上方。网页函数就是创建该字符串的东西，它随后调用 the_construct 并创建一个类的实例。然后该字符串被输出到浏览器。

请注意（在调用之后）函数在 "the_construct" 之前有一个制表符。这可以用来快速查看类中存在哪些函数。你可能还会注意到 "the_construct" 是斜体的。这表示该函数不是类级函数，而是实例级函数，或在创建类的实例时运行的函数。

这很简单，而且完全不需要参数。你可能会想知道如果需要发送参数，例如也许是类名，the_construct 会是什么样子。

示例：

该函数将接受一个名为 $params 的 2 个参数数组并对其进行操作。它从 $params (1) 中获取第一个参数，从 $params (2) 中获取第二个参数。

然后它使用第一个元素作为构造函数名称、第二个元素作为构造函数值来创建 "the_class" 的一个实例。

然后它输出构造函数名称及其值。

这是创建来自一个类的对象/实例的另一个示例，但这次使用的是接受参数的构造函数。这在需要传入数据时很有用，例如也许是用户登录的信息。你可以做一个非常基本的构造函数，接受 "username" 和 "password"，它会在登录时被调用，然后可以将值赋给 username 和 password 变量。

它展示了如何创建一个名为 "the_construct_user" 的单独构造函数，该构造函数接受 username 和 password 参数。

代码展示了用户登录页面时会发生什么。它像之前一样使用 my_string 类，然后创建另一个名为 "my_construct" 的类的实例，并传入一些参数。

然后 the_class 的实例将被输出。

但这是怎么做到的？它创建了 my_construct 的一个新实例，该实例调用 the_construct 并传入用户名、密码和另一个参数。然后参数被传递到构造函数。请注意，"the_construct" 再次是斜体的。了解函数的调用位置至关重要，以便理解它们在做什么（尤其是在它们返回一个值时）。

## PHP 的 The_Destruct 函数

析构函数是面向对象编程中的一个重要概念。它是 PHP 内置的一种快速简便的销毁类实例的方式。当对象不再有引用时，析构函数会在作用域的最后一行自动调用。

析构函数可以在构造函数之前或之后使用，但不能在构造函数内部使用。它们不需要在任何地方声明或定义，因为它们默认就存在。

注意：析构函数在对象被销毁时被调用；因此，可能调用一个析构函数，该析构函数反过来递归地调用另一个析构函数。这对于以受控方式实现抛出异常的构造函数很有用。

析构函数通常与 finalize 函数一起使用，以便在对象被销毁时执行适当的清理。它不一定必须被调用，但最好在每个需要被销毁的类上调用 finalize 函数。

这里有一个示例：

```
```php
<?php class Cat { // ... public function __destruct() { echo 'Cat is being destroyed ...'; } } $cat = new Cat(); $cat->methodOne(); // outputs "Cat is being destroyed" $cat->methodTwo(); // outputs "Cat is being destroyed"
```
```

这个示例解释了析构函数是如何为我们调用的，但对 methodTwo 的最后一次调用不是必需的。

析构函数可以被根类之下的所有类重写。这对于清理数据库连接、临时文件等外部资源很有用。

此函数在对象被销毁时会自动调用（对于对象类型的“静态”内存）。例如，在对象被清理或以其他方式清理之后。

对该函数的调用如果析构函数被调用则返回 true，否则返回 false。因此，检查析构函数是否被调用的一种简单方法是检查 $this->destruct(); 是否返回 true。在 PHP <= 5.2 中，在对象被一起删除的罕见情况下，例如会话处理器保存对象时，它会返回 true。

## 使用 PHP 的 The_Destruct 函数

在 PHP 中创建对象而不定义析构函数是初学者常犯的错误。很容易忘记定义析构函数，而当对象已被创建但未定义析构函数时，更可能出现真正的错误。对象的构造函数不适用于递归；它只会被调用一次。开发人员必须记住调用

在 PHP 中，你可以使用 3 种类型的继承：

类：类是定义其子类的结构的模板。子类继承父类的所有方法和变量。

超类：超类是扩展另一个类的类。它具有父类的所有属性和方法。父类的属性和方法不会被超类继承。超类可以覆盖父类的任何函数（方法）或变量。

接口：接口是可互换性的模型，即一组与行为相关的属性。接口不包含实现细节，也不提供特定功能。

## 继承类

PHP 中基本上存在两种继承：

实现继承：子类从父类继承行为。

行为继承：子类继承实现细节，但可以选择用自己的实现覆盖这些实现。实现继承本质上是 PHP 中的默认行为。在任何情况下，超类都继承自基类（父类）的所有属性和方法，并且不会有派生类（子）添加的任何新属性或函数。

继承类的语法是：

```
class Superclass{ }
class Child extends SuperClass{ }
```

下面的示例展示了 PHP 中继承的演示。在此示例中，类 "Child" 从父类 "Person" 继承变量 $age 和方法 "showAge"。将添加到此类的任何新变量或方法都应放在其超类声明之后。这是一种确保新变量和方法不会被父类的变量和方法覆盖的方式。

请注意，子类是在类声明开始处使用 "extends" 声明的。这使得子类成为一个子类，并继承父类的所有属性和方法。PHP 将超类称为“基类”。由于基类总是在类中排第一，因此它被称为“the base”或“the superclass”。在为继承属性设置值的语句中，父类是“基类”。

```
<?php class Person { var $name; var $age; function showAge(){ echo($this->name, $this->age); } } class Child extends Person{ function showAge() { echo("Child: $this->age"); } } ?>
```
