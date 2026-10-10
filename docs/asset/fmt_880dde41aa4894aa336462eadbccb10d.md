
重写的 `Display()` 类似但多了一行：

`$this->DisplayMenu($this->rowbuttons);`

这一行再次调用了 `DisplayMenu()` 并创建了第二个菜单栏。

215

# 第 6 章 面对象 PHP

在类定义之外，你创建一个 `ServicesPage` 类的实例，并为其设置默认值，然后调用 `Display()`。

如你所见，图 6.2 显示了标准页面的新变体。你只需要为不同的部分编写新代码。

![](img/654520c37415debd4290b9b4aa2c03f2_215_0.png)

图 6.2 使用继承重用大部分标准页面创建服务页面

通过 PHP 类创建页面具有明显的优势。由于类为你完成了大部分工作，你创建新页面所需的很少。通过更新类，你可以同时更新所有页面。使用继承，你可以从原始类派生不同的版本，而不损害这些优势。

就像生活中的大多数事情一样，这些优势并不是免费的。从脚本创建页面比从磁盘加载静态 HTML 页面并发送到浏览器需要更多的计算资源。在繁忙的网站上，这将非常重要，你应该努力例如使用静态 HTML 页面或尽可能缓存脚本的输出，以减轻服务器负载。

在后续章节中，我们将讨论 PHP 的高级面向对象（OO）特性。

## 使用类常量

PHP

```php
<?php

class Math
{
    const pi = 3.14159;
}

echo "Math::pi = " ..Math::pi;
?>
```

你可以像示例所示，使用 `::` 运算符指定类常量所属的类，从而访问该常量。

## 实现静态方法

PHP 允许使用 `static` 关键字。它应用于方法，允许在不实例化类的情况下调用方法。这是类常量概念在方法上的等价实现。例如，考虑上一节中创建的 `Math` 类。你可以添加一个 `squared()` 函数并在不实例化类的情况下调用它，如下：

```php
<?php

class Math
{
    static function squared($input)
    {
        return $input*$input;
    }
}

echo Math::squared(8);
?>
```

注意，你不能在静态方法中使用 `$this` 关键字，因为可能没有可以引用的对象实例。

## 检查类类型和类型提示

`instanceof` 关键字允许你检查对象的类型。你可以检查一个对象是否是特定类的实例、是否继承自某个类，或者它是否

```php
($b instanceof B) 将为真。
($b instanceof A) 将为真。
($b instanceof Displayable) 将为假。
```

所有这些示例假设 `A`、`B` 和 `Displayable` 都在当前作用域内；否则将触发错误。

此外，你还可以使用类类型提示。通常在 PHP 中，当你向函数传递参数时，你不需要传递参数的类型。通过类型提示，你可以指定应该传递的类类型，如果实际传递的不是该类型，则会触发错误。这种类型检查等同于 `instanceof`。例如，考虑以下函数：

```php
function check_hint(B $someclass) {
    //...
}
```

此示例显示 `$someclass` 需要是类 `B` 的实例。如果你传递一个类 `A` 的实例，例如

```php
check_hint($a);
```

你将得到以下致命错误：

**Fatal error:** Argument 1 must be an instance of B

注意，如果你提示的是 `A` 并传递了类 `A` 和 `B` 的实例，则不会发生错误，因为 `B` 继承自 `A`。

你也可以对接口、数组和可调用（callable）使用类型提示，这意味着传递的项必须是一个函数。虽然这对接口有效，但请注意它对 trait（Traits）无效。

## 延迟静态绑定（Late Static Bindings）

在具有相同函数多个实现的继承层次中，我们可以使用延迟静态绑定来指定使用哪个类的方法。

考虑以下简单示例（基于 PHP 手册中的示例）：

```php
<?php

class A {
    public static function whichclass() {
        echo __CLASS__;
    }
}
```

```php
public static function test() {
    self::whichclass();
}
```

```php
class B extends A {
    public static function whichclass() {
        echo __CLASS__;
    }
}
```

```php
A::test();
B::test();
```

你预期输出是 B 吗？你可能会对代码输出两次 A 感到惊讶。这是因为 `A` 重写了 `whichclass()` 方法，当通过 `B` 调用 `test()` 方法时，它是在父类 `A` 的上下文中执行的。我们如何让 `test()` 使用 `B` 对 `whichclass()` 的实现，即使用我们实际使用的类内部的实现？

答案是延迟静态绑定。在之前的示例中，如果我们将此行代码：
`self::whichclass();`

改为
`static::whichclass();`

代码将不再输出 A 然后输出 B。`static` 修饰符让 PHP 使用运行时实际创建的类，这就是名称中“延迟（late）”的部分。

## 克隆对象

PHP 中也可以使用 `clone` 关键字，它允许你复制现有对象。例如，
`$c = clone $b;`

会创建一个与 `$b` 相同类的副本，并具有相同的属性值。

你也可以更改这种行为。如果你需要 `clone` 的默认行为，你需要在基类中创建一个 `__clone()` 方法。该方法类似于构造函数或析构函数，区别在于你不需要手动调用它。它在像这里使用 `clone` 关键字时被自动调用。在 `__clone()` 方法内部，你可以定义你精确所需的复制行为。

`__clone()` 的优点是它会在使用默认行为完成精确复制后被调用，因此在那个阶段，你只需要更改你想更改的内容。

为 `__clone()` 添加的最常见功能是编写代码以确保被作为引用处理的类属性被正确复制。如果你打算克隆一个包含对象的类，你可能期望得到该对象的第二个副本，而不是同一个对象的第二个引用，因此在 `__clone()` 中添加此逻辑是有意义的。

你也可以选择什么都不改，但执行某些其他操作，例如更新与类相关的底层数据库记录。

## 使用抽象类

PHP 提供了抽象类（abstract classes，不能被实例化）以及抽象方法（abstract methods，仅提供方法的签名但不提供实现）。例如，

```php
abstract class A {
    abstract function operationX($param1, $param2);
}
```

任何包含抽象方法的类本身必须是抽象的。抽象方法和类的主要用途是在类层次结构中，你想确保子类包含某些内容；这也可以通过接口（interface）实现。

```php
abstract operationX($param1, $param2);
```

## 使用 __call() 方法重载方法

我们之前查看了一些具有特殊含义的类方法，其名称以双下划线（_）开头，例如 `__get()`、`__set()`、`__construct()` 和 `__destruct()`。另一个例子是 `__call()`，它用于 PHP 实现方法重载。

方法重载在许多面向对象的语言中很常见，但在 PHP 中并不有用，因为你需要灵活的类型和（易于实现的）可选函数。要使用它，你需要实现一个 `__call()` 方法，如示例所示：

```php
public function __call($method, $p) {
    if ($method == "display") {
        if (is_object($p[0])) {
            $this->displayObject($p[0]);
        } else if (is_array($p[0])) {
            $this->displayArray($p[0]);
        } else {
            $this->displayScalar($p[0]);
        }
    }
}
```

`__call()` 方法接收两个参数。第一个包含被调用方法的名称，第二个包含传递给该方法的参数数组。你可以自己决定调用哪个方法。在这种情况下，如果传递给 `display()` 的对象，则调用底层的 `displayObject()` 方法；如果传递的是数组，则调用 `displayArray()`；如果是其他内容，则调用 `displayScalar()`。

要调用此代码，你首先需要实例化包含 `__call()` 方法的类（命名为 `overload`），然后调用 `display()` 方法，如下所示：

```php
$ov = new overload();
$ov->display(array(1, 2, 3));
$ov->display('cat');
```

第一次调用 `display()` 触发 `displayArray()`，第二次触发 `displayScalar()`。注意，你不需要 `display()` 方法的底层实现即可工作。

PHP 5.3 引入了一个名为 `__callStatic()` 的简单魔法方法。它的工作方式与 `__call()` 类似，但在通过静态上下文调用不可访问的方法时会被触发，例如：
`overload::display();`

## 使用 __autoload()

PHP 的另一个特殊函数是 `__autoload()`。它不是类方法而是一个独立函数；因此你在类声明之外声明它。如果你实现了它，当你尝试实例化一个未声明的类时，它会被自动调用。考虑此示例：

```php
function __autoload($name)
{
  include_once $name.".php";
}
```

`__autoload()` 的主要用途是尝试包含实例化所需类所需的任何文件。

## 第 6 章 面对象化的 PHP

### 实现迭代器与迭代

PHP 面对象引擎的一个特性是，你可以使用 `foreach()` 循环来遍历对象的属性，就像遍历数组一样。这里有一个示例：

```php
class MyClass {
    public $a = "5";
    public $b = "7";
    public $c = "9";
}

$x = new MyClass;
foreach ($x as $attribute) {
    echo $attribute."<br />";
}
```

如果你想实现更复杂的行为，可以实现一个迭代器（iterator）。要实现这一点，你需要让想要遍历的类实现 `IteratorAggregate` 接口，并为其提供一个名为 `getIterator` 的方法，该方法返回一个迭代器类的实例。该类必须实现 `Iterator` 接口，该接口有一系列必须实现的方法。列表 6.4 显示了一个类和迭代器的示例。

列表 6.4 iterator.php——一个示例基类和迭代器类

```php
<?php

class ObjectIterator implements Iterator {
    private $obj;
    private $count;
    private $currentIndex;
    function __construct($obj) {
        $this->obj = $obj;
        $this->count = count($this->obj->data);
    }
    function rewind() {
        $this->currentIndex = 0;
    }
    function valid() {
        return $this->currentIndex < $this->count;
    }
function key()
{
    return $this->currentIndex;
}
function current()
{
    return $this->obj->data[$this->currentIndex];
}
function next()
{
    $this->currentIndex++;
}
class Object implements IteratorAggregate
{
    public $data = array();
    function __construct($in)
    {
        $this->data = $in;
    }
    function getIterator()
    {
        return new ObjectIterator($this);
    }
}

myObject = new Object(array(2, 4, 6, 8, 10));
$myIterator = $myObject->getIterator();
for($myIterator->rewind(); $myIterator->valid(); $myIterator->next()) {
    $key = $myIterator->key();
    $value = $myIterator->current();
    echo $key.*" = =>".$value."<br />";
}
?>
```

`ObjectIterator` 类实现了 `Iterator` 接口要求的一系列函数：

- 构造函数不是必须的，但它显然是设置你计划遍历的项目数量以及指向当前数据项链接的好地方。
- `rewind()` 函数应该将内部数据指针拨回数据的开头。
- `valid()` 函数应该告诉你在数据指针当前位置是否还有更多数据。
- `key()` 函数应该返回数据指针的值。
- `value()` 函数应该返回存储在当前数据指针处的数据值。
- `next()` 函数应该让数据指针沿着数据移动。

使用像这样的迭代器类的类是，即使底层实现发生变化，数据的接口也不会发生变化。在例例中，`IteratorAggregate` 类是一个简单的数组。如果你决定将其更改为哈希表或链表，你仍然可以使用标准的 `Iterator` 来遍历它，尽管 `Iterator` 代码会发生变化。

## 生成器 (Generators)

生成器在许多方面与迭代器相似，但简单得多。其他编程语言（如 Python）也支持生成器。理解生成器的一种方式是：生成器的定义看起来像一个函数，但在运行时，它的行为像一个迭代器。

编写生成器与编写普通函数的区别在于，你不是使用 `return` 关键字将值传回给调用代码，而是使用 `yield` 关键字。这通常位于循环内部，因为你将用它来返回多个值。

你可以在 `foreach` 循环中调用生成器函数。这会创建一个 `Generator` 对象，该对象实际上保存了生成器内部的状态。在 `foreach` 循环的每次迭代中，生成器都会向前移动一次。

通过一个示例来理解这可能是最简单的。为此，请考虑一个简单的游戏实现。在这个游戏中，我们从 1 开始逐向上计数，每当我们看到 3 或 3 的倍数时，我们就改说“fizz”；每当我们看到 5 或 5 的倍数时，我们就说“buzz”。如果数字能被 3 和 5 整除，我们就说“fizzbuzz”。

我们的 `fizzbuzz` 生成器所示于列表 6.5。

列表 6.5 fizzbuzz.php 使用生成器打印 Fizzbuzz 序列

```php
<?php

function fizzbuzz($start, $end) {
  $current = $start;
  while ($current <= $end) {
    if ($current%3 == 0 && $current%5 == 0) {
      yield "fizzbuzz";
    } else if ($current%3 == 0) {
      yield "fizz";
    } else if ($current%5 == 0) {
      yield "buzz";
    } else {
      yield $current;
    }
    $current++;
  }
}

foreach(fizzbuzz(1,20) as $number) {
  echo $number.'<br />';
}
```

## 理解 PHP 中的高级对象功能

### 将类转换为字符串

如果你在类中实现一个名为 `__toString()` 的函数，当你像这样打印它时它会被调用：

```php
$p = new Printable();
echo $p;
```

`__toString()` 函数返回的内容将被 `echo` 打印。例如你可能会这样实现它：

```php
class Printable {
    public $testone;
    public $settwo;
    public function __toString() {
        return var_export($this, TRUE);
    }
}
```
