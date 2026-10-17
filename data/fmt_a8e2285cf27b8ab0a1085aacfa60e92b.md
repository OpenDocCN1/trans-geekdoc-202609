
```php
<?php
$cat = function () {
    echo 'Oh long Johnson!';
}
```

在这里我们将匿名函数（或“闭包”）赋值给变量`$cat`。该函数返回与流行迷因相关的字符串。

注意我们在函数后面添加了分号。这是因为它是赋值语句的一部分，就像任何其他单行 PHP 代码一样。

现在我们把这个闭包捕获在变量中，我们可以像调用任何其他函数一样调用它！例如：

### 示例 03：执行赋值的闭包

```php
<?php
$cat();
```

我们只需在变量上加上括号，代码就会执行。

### 示例 04：输出

```
Oh long Johnson!
```

### 将函数传递给函数...

闭包出现在 PHP 5.3 中，这意味着它们相当新了！它们是 PHP 世界的游戏规则改变者，因为它们允许你将小逻辑段传递给函数。没错，你可以将闭包传递给函数。让我们来看看实际操作。

噢，顺便说一下，我确实提到过可以类型提示`Closure`？只需在参数之前放置`Closure`即可确保只将闭包作为参数传递给方法。如果你对闭包调用`get_type()`，你将得到值`closure`。它是 PHP 中的一个复杂对象。稍后我们会看到其他此类型的对象。

## 闭包 (Closures)

### 示例 06：两个闭包

```php
<?php
// 创建一个数学函数。
function math(Closure $type, $first, $second) {
  // 使用参数执行闭包
  return $type($first, $second);
}

// 创建一个加法闭包。
$addition = function ($first, $second) {
  // 将值相加。
  return $first + $second;
};

// 创建一个减法闭包。
$subtraction = function ($first, $second) {
  // 将值相减。
  return $first - $second;
};
```

我们定义了两个绑定到变量`$addition`和`$subtraction`的闭包。它们接收两个参数，并对值进行减法或加法。让我们尝试在`math()`函数中使用它们吧，好吗？

### 示例 07：将闭包传递给函数

```php
<?php
// 创建一个数学函数。
function math(Closure $type, $first, $second) {
  // 使用参数执行闭包
  return $type($first, $second);
}

// 创建一个加法闭包。
$addition = function ($first, $second) {
// 将值相加。
return $first + $second;
}
// 创建一个减法闭包。
$subtraction = function ($first, $second) {
// 将值相减。
return $first - $second;
}
// 执行数学函数。
echo math($addition, 2, 2);
echo PHP_EOL; // 换行！
echo math($subtraction, 5, 3);
```

> `PHP_EOL`是一个常量，它会被替换为与当前操作系统兼容的换行符。它超级好用！

我们调用了两次`math()`函数，每次都分配了一个不同的闭包，提供了整数，并使用`PHP_EOL`常量用换行符将两次调用分开。让我们看看输出结果。

### 示例 08：输出

太棒了！通过向我们的`math()`函数传递不同的闭包，我们改变了它的工作方式。作为作业，你为什么不尝试修改上面的代码，以包含乘法和除法功能呢？这里有一个提示，你会需要更多闭包！

## 15. 包含 (Includes)

你已经学习 PHP 一段时间了，现在是时候谈谈你的未来了。你和 PHP 处于一段稳密的关系中。你拥有一对情侣装的家居睡袍。你可能已经在考虑结婚了。你可能想用 PHP 编写未来的应用程序，不是吗？

## 包含 (Include)

如果你必须反复不断地编写相同的代码，那将太糟糕了，不是吗？我的意思是，写起来很有趣，但它会慢慢磨灭你的耐心。想象你有以下函数。

### 示例 01：一个熟悉的函数

```php
<?php

function welcome($name) {
    return "Welcome, {$name}!";
}
```

啊！`welcome()`函数。它永远不会过时！我们在许多应用程序中都会需要它。毕竟，如果我们不欢迎用户，他们可能会对我们生气！我们可以使用`include`语句让这段代码具有某种程度的可重用性。

首先，让我们把函数放在它自己的文件中。我们将将其命名为`welcome.php`。我们会在里面放入相同的代码。

### 示例 02：它又在这里

```php
<?php

function welcome($name) {
    return "Welcome, {$name}!";
}
```

现在，让我们创建一个新文件，命名为`program.php`。我们将此文件放在`welcome.php`文件旁边。我们想在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 03：包含文件

```php
<?php
include 'welcome.php';
echo welcome("World");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 04：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Alice");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 05：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Bob");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 06：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Charlie");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 07：包含文件

```php
<?php
include 'welcome.php';
echo welcome("David");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 08：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Eve");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 09：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Frank");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 10：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Grace");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 11：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Heidi");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 12：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Ivan");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 13：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Judy");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 14：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Karl");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 15：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Mallory");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 16：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Niaj");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 17：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Oscar");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 18：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Peggy");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 19：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Quinn");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 20：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Trent");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 21：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Ursula");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 22：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Vivian");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 23：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Xavier");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 24：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Yara");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 25：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Zane");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

## 包含 (Include)

如果你必须反复不断地编写相同的代码，那将太糟糕了，不是吗？我的意思是，写起来很有趣，但它会慢慢磨灭你的耐心。想象你有以下函数。

### 示例 01：一个熟悉的函数

```php
<?php

function welcome($name) {
    return "Welcome, {$name}!";
}
```

啊！`welcome()`函数。它永远不会过时！我们在许多应用程序中都会需要它。毕竟，如果我们不欢迎用户，他们可能会对我们生气！我们可以使用`include`语句让这段代码具有某种程度的可重用性。

首先，让我们把函数放在它自己的文件中。我们将将其命名为`welcome.php`。我们会在里面放入相同的代码。

### 示例 02：它又在这里

```php
<?php

function welcome($name) {
    return "Welcome, {$name}!";
}
```

现在，让我们创建一个新文件，命名为`program.php`。我们将此文件放在`welcome.php`文件旁边。我们想在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 03：包含文件

```php
<?php
include 'welcome.php';
echo welcome("World");
```

我们使用`include`语句让这段代码具有某种程度的可重用性。在这个文件中使用`welcome()`函数，所以让我们包含`welcome.php`文件。困惑吗？让我们看看`program.php`文件。

### 示例 04：包含文件

```php
<?php
include 'welcome.php';
echo welcome("Alice");
```

## 类

- 标题。
- 作者。
- 出版者。
- 出版年份。

让我们在我们的`Book`类中反映这些属性。开始吧！

### 示例 02：类属性

```php
<?php
class Book {
    var $title;
    var $author;
    var $publisher;
    var $yearOfPublication;
}
```

属于类的变量被称为“类属性”（class properties）。目前，我们将使用`var`关键字并结合典型的变量表示法来定义类属性。不用太担心`var`关键字，我们稍后会查看一些替代方案。

我们现在准备好开始操作我们的类了。

## 实例

我们定义的类实际上是一个蓝图。我们可以使用它来创建一个`Book`对象的新实例。这里的关键词是`new`。实例是我们可以使用的类实体。我们可以拥有同一个类的多个实例。这用文字描述很难解释清楚，所以让我们来看一个代码示例。

### 示例 03：创建类的实例
