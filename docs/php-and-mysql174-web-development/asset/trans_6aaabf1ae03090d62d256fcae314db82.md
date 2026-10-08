

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

（`var_export` 函数会打印所有属性值。）

### 使用反射 API

PHP 的对象特性还包括反射 API。反射是查询类和对象以发现其结构的能力。这种能力在与未知类（例如编码脚本）交互时非常有用。

该 API 非常复杂，但我们将查看一个简单的示例来让你大致了解它的用途。考虑本章中的 `Page` 类，你可以通过反射 API 获取它的所有信息，如列表 6.6 所示：

```php
<?php

require_once("page.php");

$class = new ReflectionClass("Page");
echo "<pre>"$class."</pre>";

?>
```

在这里，你使用 `ReflectionClass` 的 `__toString()` 方法来打印这些数据。注意 `<pre>` 标签单独成行，以免混淆 `__toString()` 方法。

此代码的第一屏输出所示

## 命名空间 (Namespaces)

命名空间是一种分组类和/或函数的方法。它们可以用于将一组相关的组件汇集成为库。

在命名空间出现之前，按名称对类或函数分组的唯一选择是为它们添加前缀。例如，你可能有一个与电子邮件相关的类库，并让它们都以 `Mail` 前缀开头。命名空间为相关代码的汇集提供了更好的解决方案，此外还解决了两个常见问题。

