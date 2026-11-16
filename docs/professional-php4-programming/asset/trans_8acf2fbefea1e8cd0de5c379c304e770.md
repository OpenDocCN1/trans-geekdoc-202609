

通过在验证器对象之上提供一个接口，`Form` 对象基本上充当我们 `Form` 程序中其他对象的门面。

可以看出，通过将工作委托给更精细的对象，我们可以为常见问题开发出优雅的解决方案，从而创建出更具可重用性和可维护性的模块。

## 重要的启发式方法和设计决策

对象经常被设计成似乎主要存储数据，但这并不是正确的面向对象编程。使对象区别于数据结构的特征在于，它提供对该对象而言很重要的服务。让我们来看一个对象未能提供其应提供的必要服务的示例：

```
class Point
{
    var $x;
    var $y;
    var $color;

    function Point($x, $y) {$this->setX($x); $this->setY($y);}
    function setX($x) {$this->x = $x;}
    function setY($y) {$this->y = $y;}
    function setColor($color) {$this->color = $color;}
    function getX() {return $this->x;}
    function getY() {return $this->y;}
    function getColor() {return $this->color;}
    function draw() (...)
}
```

乍一看，这个类似乎是一个描述点的不错的类，但让我们看看如何使用这个点：

```
$point = new Point(100, 40);
$point->draw();

$x = $point->getX();
$x += 32;

$y = $point->getY();
$y += 96;

$point->setX($x);
$point->setY($y);

$point->draw();
```

现在，请花点时间看看能否发现这段代码的任何问题。虽然它看起来没问题，但存在一些固有的问题。为什么我们的代码在代替对象做决定？为什么我们要提供实现细节，例如 `$x = $x + 32`，而这些本可以交给对象本身？难道对象不应该知道如何自己工作吗？这个类没有定义好，因为它没有利用封装。以下是定义该类的更好方法：

```
class Point
{
   var $x;
   var $y;
   var $color;
   function Point($x = 0, $y = 0)
   {
      $this->moveTo($x, $y);
   }
   function moveTo($x, $y)
   {
      $this->x = $x;
      $this->y = $y;
   }
   function transposeX($amount)
   {
      $this->x += $amount;
   }
   function transposeY($amount)
   {
      $this->y += $amount;
   }
   function transpose($xAmount, $yAmount)
   {
      $this->transposeX($xAmount);
      $this->transposeY($yAmount);
   }
   function setColor($color) {$this->color = $color;}
   function draw() {...}
}
```

现在，让我们看看我们的代码有多整洁，以及对象的封装是如何实现的。功能与前一个示例保持相同：

```
$point = new Point(100, 40);
$point->transpose(32, 96);
$point->draw();
```

请注意，实现细节被隐藏，对象正在代替自己做出决定。通过使用程序中所有对象都必须被封装这一启发法，您将在整个程序中获得更高的可读性和可维护性。

## PHP 类函数

PHP 提供了一些函数来获取对象的类名或确定其继承关系。其中一些函数提供了绕过设计不良的面向对象代码的方法。

### get_class()

string get_class(object $obj)

PHP 包含一个名为 `get_class()` 的方法，它返回对象的类名。在调试时很有用，可以确保传递给方法的输入正确。例如，如果我们有一个虚构的方法接受一个 User 对象，那么我们可以使用此函数来帮助调试，如下面的代码片段所示：

```
function authorize($user)
{
    assert(get_class($user) == 'user');

    if ($user->department == $this->requiredDepartment) {
        return true;
    }

    return false;
}
```

在调试应用程序时，这是一种验证数据的有用方法，而不仅仅是使用 `is_object()` 函数来测试它是否为对象。在构建对象间有大量交互的应用程序时，这可以节省大量时间。

需要注意的是，PHP 会将类名转换为小写，因此请确保在字符串比较中使用类名的小写形式。在此示例中，我们将 `get_class()` 函数的结果与 `"user"` 而不是 `"User"` 进行比较。与 `"User"` 比较将失败并导致断言错误。

### get_parent_class()

string get_parent_class(object $obj)

在测试多态代码时，此函数很有用。在最终的生产阶段 Web 应用程序中不需要它，因为所有对象都应从适当的父类子类化。如果情况并非如此，则说明您的应用程序出了严重问题。以下是测试多态方法的代码：

```
function displayAll()
{
    foreach ($this->items as $item) {
        assert(get_parent_class($item) == 'Item');
        $item->display();
    }
    return false;
}
```

此函数接受一个项数组，这些项都是父类 Item 的子类型的实例，并依次显示每一项。程序会断言列表中的每一项都是 Item 类的适当子类型。这在调试期间很有用，但应在生产环境中关闭。您可以在下一章中了解有关调试的更多信息。

## PHP 的局限性

如前面章节所述，PHP 的面向对象实现存在许多局限性。在这里，我们将讨论 PHP 的几种常见局限性，例如没有静态成员、没有析构函数和没有多重继承。

### 没有静态成员

虽然 PHP 允许程序员使用类-函数调用运算符（如继承部分所示）静态调用方法，但 PHP 不允许我们指定静态成员。那么什么是静态成员呢？静态成员类似于全局变量，但它绑定到类命名空间（而非对象命名空间）。这意味着该变量由类的所有实例共享，而不是由每个实例单独使用。

那么我们为什么需要静态成员呢？原因之一是，有时让一组对象类型的实例使用同一份数据，而不是在同一个类的多个实例中复制它，这样很方便，从而节省内存。第二个原因是，我们可能希望跟踪与类的所有实例相关的属性，例如在特定时间点已实例化了多少个类对象。

虽然 Java 等许多语言支持静态成员，但 PHP 不直接支持这种类型的变量。然而，通过全局变量和静态方法的组合，我们可以实现以相同方式运行的类静态成员。让我们通过编写一个 Apple 类来说明这种技术，该类具有一个静态成员来跟踪内存中 Apple 类实例的数量：

```
<?php
// Apple.php
class Apple
{
    var $isEaten;
}
```

在我们的 Apple 类构造函数中，有以下代码，表示我们要访问全局命名空间中的变量 `$numberOfApples` 并将其加一，从而表明已实例化了一个苹果对象：

```
function Apple()
{
    global $numberOfApples;
    $numberOfApples++;
    $this->isEaten = false;
}
```

同样，我们的 `eat()` 方法会递减此处显示的全局变量 `$numberOfApples`：

```
function eat()
{
    if (!$this->isEaten) {
        global $numberOfApples;
        $numberOfApples--;
    }
    $this->isEaten = true;
}
```

```
}
function __destruct() {
    global $numberOfApples;
    --$numberOfApples;
}
```

请注意，只有在苹果尚未被吃掉时，全局变量才会递减。这为我们的类静态变量提供了一定的完整性。最后，我们定义一个 `count()` 方法来返回内存中未被吃掉的 Apple 对象的数量：

```
// Static methods
public static function count() {
    global $numberOfApples;
    return $numberOfApples;
}

$a1 = new Apple(); // sets $numberOfApples to 1
$a2 = new Apple(); // sets $numberOfApples to 2
$a3 = new Apple(); // sets $numberOfApples to 3

echo Apple::count() . "<br>"; // outputs 3

$a1->eat(); // sets $numberOfApples to 2
$a2->eat(); // sets $numberOfApples to 1

$a4 = new Apple(); // sets $numberOfApples to 2

echo Apple::count() . "<br>"; // outputs 2
```

> 虽然在代码中使用全局变量有些不被推荐，但如果您需要在 PHP 中模拟静态成员，这种方法非常有效。

如果运行代码，您将看到脚本输出值 3，然后是 2，如代码中的注释所示。这种模拟静态变量的方法很有用，但与之相关存在一些问题：

- 此方法不能防止变量在使用静态成员之外被修改，从而可能破坏成员的完整性。
- 该成员通常与类不相关联，使得追踪更加困难，并且需要额外的文档工作来传达该变量确实是静态的。
- 如果客户端不知道您的全局变量存在，他们实际上可能会擦除全局变量的内容。

这些问题是所有全局变量固有的问题，这里也没有任何例外。

