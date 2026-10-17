
```php
<?php
class Book {
    var $title;
    var $author;
    var $publisher;
    var $yearOfPublication;
}

$book = new Book;
```

我们创建了`Book`类的新实例，并将其赋值给`$book`变量。我们使用`new`关键字，后跟想要实例化的类名来实现。现在我们有了一个类的实例，就可以操作它的属性了。让我们先为我们的书设置属性。

### 示例 04：设置类属性

```php
<?php
// 定义 Book 类。
class Book {
    // 声明属性。
    var $title;
    var $author;
    var $publisher;
    var $yearOfPublication;
}

// 创建一个新的书籍实例。
$book = new Book;

// 设置属性。
$book->title = 'Game of Thrones';
$book->author = 'George R Martin';
```

```php
$book->publisher = 'Voyager Books';
$book->yearOfPublication = 1996;
```

你可以通过对象运算符`->`来设置类实例的属性，该运算符由一个连字符符和一个大于号符号组成。接下来，你指定想要访问的属性名称。

在上面的示例中，我们使用赋值运算符`=`来设置实例的类属性。我们也可以使用对象运算符来获取它们。让我们打印每个类属性，并在末尾加上一个换行符。

### 示例 05：获取类属性

```php
<?php
// 定义 Book 类。
class Book
{
    // 声明属性。
    var $title;
    var $author;
    var $publisher;
    var $yearOfPublication;
}

// 创建一个新的书籍实例。
$book = new Book;

// 设置属性。
$book->title = 'Game of Thrones';
$book->author = 'George R Martin';
$book->publisher = 'Voyager Books';
$book->yearOfPublication = 1996;

// 输出属性。
echo $book->title . PHP_EOL;
echo $book->author . PHP_EOL;
echo $book->publisher . PHP_EOL;
echo $book->yearOfPublication . PHP_EOL;
```

我们再次使用对象运算符`->`来输出书籍实例的属性。执行我们的代码将得到以下输出。

### 示例 06：输出

- Game of Thrones
- George R Martin
- Voyager Books
- 1996

早些时候我提到我们可以拥有类的多个实例，所以让我们定义两本书，每本书都有不同的属性。为了简化示例，我现在将省略类的声明。

### 示例 07：多个类实例

```php
<?php
class Book {
    // 声明属性
    var $title;
    var $author;
    var $publisher;
    var $yearOfPublication;
}
// 创建第一个实例
$first = new Book;

// 设置属性
$first->title = 'Game of Thrones';
$first->author = 'George R Martin';
$first->publisher = 'Voyager Books';
$first->yearOfPublication = 1996;

// 创建另一个实例
$second = new Book;

// 设置属性
$second->title = 'The Colour of Magic';
$second->author = 'Terry Pratchett';
$second->publisher = 'Colin Smythe';
$second->yearOfPublication = 1983;
```

在上面的示例中，我们创建了两个书籍实例。它们都有自己的属性值。我们所做的是创建信息的机制。我们为什么不使用数组来存储这些信息呢？

## 默认值

我们的类是实例的蓝图。有时，属性会有默认值。例如，大多数书籍是平装的（paperback）。我们将书籍标记为精装（hardback）。我们可以通过给类属性一个默认值`'Paperback'`来节省时间。让我们查看以下代码。

### 示例 08：带有默认值的类属性

```php
<?php
class Book {
    var $title;
    var $author;
    var $publisher;
    var $yearOfPublication;
    var $format = 'Paperback';
}
```

我们已经为`$format`属性赋值了默认值。这行代码以分号结束。让我们确保我们的`$format`属性设置了默认值。

### 示例 09：检查默认值

```php
<?php
// 定义 Book 类。
class Book {
    // 声明属性。
    var $title;
    var $author;
    var $publisher;
    var $yearOfPublication;
    var $format = 'Paperback';
}

// 创建一个新的书籍实例。
$book = new Book;

// 输出默认值。
echo $book->format;
```

我们只是实例化了书籍并输出了该值。我们得到了什么？

### 示例 10：输出

- Paperback

正如预期的那样！当然，我们可以随意更改这个值。默认值有助于简化创建书籍的过程。

### 示例 11：修改带有默认值的属性

```php
<?php
// 定义 Book 类。
class Book {
    // 声明属性。
    var $title;
    var $author;
    var $publisher;
    var $yearOfPublication;
    var $format = 'Paperback';
}

// 创建一个新的书籍实例。
$book = new Book;

// 修改 format 值。
$book->format = 'Hardback';

// 输出 format 值。
echo $book->format;
```

如果我们再次执行代码，将得到以下值。

### 示例 12：输出

- Hardback

太棒了！你可以为所有类型设置默认值，包括字符串、整数、浮点数，甚至是关联数组和索引数组。但有一个陷阱，记住总会有小问题。在定义默认值时，你不能将其设置为函数的结果。这是非法的。如果你尝试这样做，PHP警察会来带你。这意味着下面的操作是不可能的。

### 示例 13：非法设置默认值

```php
<?php
// 创建一个书籍类。
class Book
{
    var $bar = strtoupper('foo');
}
```

> 注意`strtoupper()`函数是一个内置 PHP 函数，用于将字符串转换为大写。所以`foo`会变成`FOO`。但在在此上下文中，为类属性设置默认值会导致语法错误。

## 方法

是时候开始使用方法（methods）了。我们把属于类的称为方法。让我们再次查看这些用词上的区别，好吗？

| 通用 | 类 |
| --- | --- |
| 变量 | 属性 |
| 函数 | 方法 |

当你在寻求帮助时，知道函数和方法的区别将与其他开发者交流变得简单得多。现在花时间学习这些名称是值得的。

如何在我们的类上定义方法呢？很简单。事实上，你已经知道这种格式了！让我们创建一个简单的函数来打招呼。

### 示例 14：创建类方法

```php
<?php
// 定义 Book 类。
class Book {
    // 声明属性。
    var $title;
    var $author;
    var $publisher;

    // 声明方法。
    function sayHello() {
        return 'Hello!';
    }
}

// 创建一个新的书籍实例。
$book = new Book();

// 修改 format 值。
$book->format = 'Hardback';

// 执行 hello 方法。
echo $book->sayHello();
```

再次，我们使用`function`关键字来定义一个新函数。其格式与我们在上一节中学到的完全相同，不同之处在于函数现在直接位于类的大括号`{ }`内部。

我们可以使用之前用于获取和设置类属性的对象`->`运算符来执行类方法。我们需要在方法名末尾添加圆括号`( )`，就像我们处理普通函数时做的那样。

### 示例 15：调用类方法

```php
<?php
echo $book->sayHello();
```

我们收到了来自类的友好的回复。

### 示例 16：输出

```
Hello!
```

太棒了！我们可以在类结构中包含任意数量的方法，放手去做，多写几个方法来学习这种语法。

## 无法触碰 $this

好吧，你实际上可以触碰`$this`。事实上，你将需要这样做。

在为类编写函数时，你可能想要访问类的属性，甚至调用其他类方法。你可以通过使用`$this`属性来实现这一点。

`$this`属性是引用当前类实例的快捷方式。你可以使用它在类方法内部访问类属性和其他方法。让我们来看这个类的实际运行。

### 示例 17：指示当前实例

```php
<?php
// 定义 Book 类。
class Book {
    // 声明属性。
    var $title;
    var $author;
    var $publisher;

    // 声明一个方法。
    function summary() {
        echo 'Title: ' . $this->title . PHP_EOL;
        echo 'Author: ' . $this->author . PHP_EOL;
        echo 'Publisher: ' . $this->publisher . PHP_EOL;
    }
}

// 创建一个新的书籍实例。
$book = new Book();

// 设置类属性。
$book->title = 'Reaper Man';
$book->author = 'Terry Pratchett';
$book->publisher = 'Victor Gollancz';

// 输出书籍摘要。
$book->summary();
```

这是一大段代码，不是吗？让我们把它拆分一下。首先我们来看`summary()`方法。

### 示例 18：检查当前实例的属性

```php
<?php
// 声明一个方法。
function summary() {
    echo 'Title: ' . $this->title . PHP_EOL;
    echo 'Author: ' . $this->author . PHP_EOL;
    echo 'Publisher: ' . $this->publisher . PHP_EOL;
}
```

在`summary`方法内部，我们为每个字段输出一个字符串标签。接下来，我们使用`$this`引用当前实例来拼接字段值，然后使用对象`->`运算符，最后是属性。最后，我们添加了 PHP 换行符以便清晰。

### 示例 19：执行 summary 方法

```php
<?php
// 创建一个新的书籍实例。
$book = new Book();

// 设置类属性。
$book->title = 'Reaper Man';
$book->author = 'Terry Pratchett';
$book->publisher = 'Victor Gollancz';

// 输出书籍摘要。
$book->summary();
```

接下来，我们创建一个新的`Book`实例并填充现有字段。在实例上调用了`summary()`方法。让我们看看执行这段代码后收到的输出。

### 示例 20：输出

```
Title: Reaper Man
Author: Terry Pratchett
Publisher: Victor Gollancz
```

我们得到了书籍的清晰表示。如你所见，通过`$this`属性正确地访问了属性。

我们还可以使用`$this`来调用实例方法。让我们来看一个例子，好吗？

### 示例 21：从类方法调用类方法

```php
<?php
// 定义 Example 类。
class Example
{
    // 第一个函数。
    function first()
    {
        return $this->second();
    }

    // 第二个函数。
    function second()
    {
        return $this->third();
    }

    // 第三个函数。
    function third()
    {
        return "Well that was rather pointless, wasn't it?";
    }
}
```

在这里，我们可以看到方法链。

- `first()`方法使用`$this`返回`second()`方法的值。
- `second()`方法使用`$this`返回`third()`方法的值。
- 最后，`third()`方法返回一个字符串值。

这在现实世界中并不是一个非常实用的例子，但它确实有助于说明函数和方法的调用可以近乎无限地进行嵌套。

> 虽然近乎无限，但受内存和 PHP 堆栈深度的限制。不过，默认情况下这是一个很大的数字，除非你在循环中出错，否则通常不会遇到任何问题。

## 构造函数

构造函数是特殊的方法。当你创建类的新实例时，它们会被调用。这为你提供了一个极佳的机会，可以将类属性设置为你其他可能无法设置的值，例如函数或方法的结果。

要定义构造函数，我们只需要一个名为`__construct()`的方法。值得注意的是，函数名的开头有两个下划线。遗憾的是，虽然 PHP 是一种极其灵活的语言，但在描述性或方便的函数命名方面往往不尽人意，`__construct()`例外。别担心！它很快就会变成你的本能。

### 示例 22：创建一个类

```php
<?php
// 定义 Panda 类。
class Panda {
    // 大写名称属性
    var $loudName;

    // 构造函数方法。
    function __construct() {
        $this->loudName = $this->makeNameLoud('Lushui');
    }

    // 名称变大方法。
    function makeNameLoud($name) {
        return strtoupper($name);
    }
}
```

我们有一个带有`makeNameLoud()`方法的类，它对字符串进行转换。我们已经发现，不能直接使用函数或方法为类属性设置默认值，相反我们使用构造函数来设置初始值。

## 继承

当一只熊猫妈妈和一只熊猫爸爸非常相爱时，它们可能会决定一起生宝宝熊猫。当然，我指的不是那些懒惰的黑白熊猫。它们并没有这种“父母”的动力。我说的是那些漂亮的红熊猫。

宝宝熊猫很可能与父母共享许多属性。不仅是它们明亮且蓬松的毛皮，还有它们的饮食习惯、睡眠模式和整体性格。它们从父母那里继承了这些属性。

如果我想上一堂生物课，我就会去买一本生物学书籍了。

看看你！你今天不是有点坐立不住了吗？

嗯，事实是，熊猫并不是唯一会继承属性的东西。你看，类也可以有父母。我不完全确定繁衍是如何发生的，但我完全可以教你它产生的结果。

让我们来看一个简单的类。

### 示例 01：一个简单的类

```php
<?php
class Panda
{
    // 属性
    var $coat = 'fluffy';
    var $colour;

    // 方法
    function getCoat()
    {
        return $this->coat;
    }

    // 方法
    function getColour()
    {
        return $this->colour;
    }
}
```

## 继承

这是我们的简单类。它有两个属性：`$coat`和`$color`。我们还有两个名为`getCoat()`和`getColour()`的类方法，它们只是返回我们的属性值。没有比这更简单的了，对吧？你可以的，伙计！

让我们挑战舒适区。尝试一些新东西。

### 示例 02：扩展类

```php
<?php
class Panda {
    // 属性
    var $coat = 'fluffy';
    var $colour;

    // 方法
    function getCoat() {
        return $this->coat;
    }

    // 方法
    function getColour() {
        return $this->colour;
    }
}
```
