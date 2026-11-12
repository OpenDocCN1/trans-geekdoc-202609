
在简单情况下，将一个变量复制到另一个变量时，PHP 内置的 **引用计数** 特性可防止不必要的内存使用。例如：

```php
$a = 'the quick brown fox';
$b = $a;
```

在上面的例子中，`$b` 的值不会占用额外内存，因为 PHP 内置的引用计数会隐式地将 `$b` 和 `$a` 指向内存中的同一位置，直到它们的值变得不同。这是 PHP 的内部特性，影响性能但不影响行为。我们不必太担心它。

不过，在某些情况下，使用引用 *更* 快，尤其是处理大型数组和对象时，因为无法使用 PHP 内置的引用计数，因此必须复制内容。

因此，为获得最佳性能，您应执行以下操作：

- 对于整数和字符串等简单值，应尽可能避免使用引用。
- 对于数组和对象等复杂值，应尽可能使用引用。

## 引用与 PHP 5

在 PHP 5 中，引用将不再是问题，因为 PHP 在传递对象时的默认行为将是按引用传递。如果您需要对象的副本，可以使用特殊的 `__clone` 方法来创建副本。

从本质上讲，这一变化使 PHP 与大多数面向对象编程语言（如 Java）保持一致，并肯定能大大减少围绕该主题的混淆。不过，在 PHP 5 获得广泛采用之前，了解引用的工作原理仍然很重要。

## 如何利用继承？

**继承** 是面向对象范式的基本组成部分，也是其强大功能的重要组成部分。继承是不同类之间的一种关系，其中一个类被定义为另一个类的子类或派生类。子类继承父类中定义的方法和成员变量，从而可以对父类进行“增加价值”。

查看 PHP 中继承工作原理的最简单方法是通过示例。假设我们有这个简单的类：

```php
<?php
class Hello {
    function sayHello()
    {
        return 'Hello World!';
    }
}
```

使用 extends 关键字，我们可以创建一个 Hello 的子类：

```php
class Goodbye extends Hello {
    function sayGoodbye()
    {
        return 'Goodbye World!';
    }
}
```

Goodbye 现在是 Hello 的子类。反过来说，Hello 是 Goodbye 的 **父类** 或 **超类**。现在，我们可以简单地实例化子类，并使用单个对象访问 sayHello 和 sayGoodbye 方法：

```php
$msg = &new Goodbye();
echo $msg->sayHello() . '<br />';
echo $msg->sayGoodbye() . '<br />';
?>
```

该示例展示了继承的基本工作原理，但并未体现其实际威力……这需要通过重写来实现。

## 重写

当我们在子类中定义与父类同名的函数时会发生什么？示例：

```php
<?php
class Hello {
function getMessage()
{
return 'Hello World!';
}
}

class Goodbye extends Hello {
function getMessage()
{
return 'Goodbye World!';
}
}
```

两个类都有相同的方法名 getMessage。PHP 完全接受这一点——它不会对方法被声明两次提出异议。

使用这些类时会发生以下情况：

```php
$hello = &new Hello();
echo $hello->getMessage() . '<br />';

$goodbye = &new Goodbye();
echo $goodbye->getMessage() . '<br />';
?>
```

输出如下：

```
Hello World!
Goodbye World!
```

通过 $goodbye 对象调用 getMessage 会显示 “Goodbye World！” 子类中的方法 **重写** 了父类中的方法。

您也可以让子类在内部使用父类的方法，同时对其进行重写。示例：

```php
<?php
class Hello {
function getMessage()
{
return 'Hello World!';
}
}
class Goodbye extends Hello {
function getMessage()
{
$parentMsg = parent::getMessage();
return $parentMsg . '<br />Goodbye World!';
}
}

$goodbye = &new Goodbye();
echo $goodbye->getMessage() .'<br />';
?>
```

使用 parent 关键字，我们可以调用父类的方法。

请注意，我们也可以按名称调用父类以实现完全相同的结果：

```php
class Goodbye extends Hello {
function getMessage() {
$parentMsg = Hello::getMessage();
return $parentMsg . '<br />Goodbye World!';
}
}
```

请注意，我们已将 parent 关键字替换为 Hello 类的名称。输出完全相同。但是，使用 parent 可以免去在子类中工作时记住父类名称的麻烦，并且是推荐的语法。

从非静态方法调用 parent::getMessage() 或 Hello::getMessage() 与调用静态函数不同。这是涉及继承的一种特殊情况。父类中被调用的函数仍保留对实例数据的访问权限，因此不是静态的。这可以如下演示：

```php
<?php
class A {
var $a = 1;
function printA()
{
             echo $this->a;
         }
     }
class B extends A {
    var $a = 2;
    function printA()
    {
        parent::printA();
        echo "\nWasn't that great?";
    }
}

$b = new B();
$b->printA();
?>
```

以上代码生成的输出如下：

```
2
Wasn't that great?
```

## PHP 不会级联构造函数

大多数面向对象语言（如 Java）会在运行子类中覆盖的构造函数之前，自动运行父类的构造函数。这称为级联构造函数——而 PHP 不具备此功能。

如果在子类中创建构造函数，请注意您完全覆盖了父类的构造函数，并且如果您仍希望父类处理其部分对象初始化，则必须从新构造函数中显式调用它。

覆盖声明的成员变量的方式与方法完全相同，尽管您不太可能频繁使用此功能。

## 继承实战

现在您大致了解了 PHP 中继承的用法，是时候查看一个示例，以便更好地了解如何应用继承。

以下示例为 Web 页面实现了一个简单的导航系统，生成页面顶部出现的 HTML。通过让一个类继承另一个类，在需要时可以向页面添加“面包屑”导航。

首先，StandardHeader 类负责生成页面顶部的 HTML，并提供 setHeader 和 getHeader 方法来访问存储 HTML 的变量。

```php
<?php
/**
 * A standard header for a Web page
 */
class StandardHeader {
 /**
  * The header HTML is stored here
  */
 var $Header = '';

 /**
  * The constructor, taking the name of the page
  */
 function StandardHeader($title)
 {
  $html = <<<EOD
 <html>
 <head>
  <title>$title</title>
 </head>
 <body>
  <h1>$title</h1>
 EOD;
  $this->setHeader($html);
 }

 /**
  * General method for adding to the header
  */
 function setHeader($string)
 {
  if (!empty($this->header)) {
   $this->header .= $string;
  } else {
   $this->header = $string;
  }
 }

 /**
  * Fetch the header
  */
 function getHeader()
 {
     return $this->header;
 }
}
```

现在，子类 CategoryHeader 为其父类增加了额外功能，向生成的 HTML 添加了“面包屑”链接。我们不需要重新创建 setHeader 和 getHeader 方法，因为在实例化 CategoryHeader 时，这些方法会从 StandardHeader 继承。

文件：12.php（摘录）

```php
/**
 * Subclass for dealing with Categories, building a breadcrumb
 * menu
 */
class CategoryHeader extends StandardHeader {
    /**
     * Constructor, taking the category name and the pages base URL
     */
    function CategoryHeader($category, $baseUrl)
    {
        // Call the parent constructor
        parent::StandardHeader($category);

        // Build the breadcrumbs
        $html = <<<EOD
<p><a href="{$baseUrl}">Home</a> >
        <a href="{$baseUrl}?category=$category">{$category}</a></p>
EOD;
        // Call the parent setHeader() method
        $this->setHeader($html);
    }
}
```

现在让我们使用这两个类：

文件：12.php（摘录）

```php
// Set the base URL
$baseUrl = '12.php';

// An array of valid categories
```
