

}
}

## Interfaces

接口定义是为了为实现者提供一组共同的函数名。不同的实现者可以根据自己的需求实现这些接口。可以这么说，接口是由开发者实现的骨架。

As of PHP5, it is possible to define an interface, like this:

```php
interface Mail {
    public function sendMail();
}
```

Then, if another class implemented that interface, like this:

```php
class Report implements Mail {
    // sendMail() Definition goes here
}
```

## Constants

常量在某种程度上类似于变量，因为它持有一个值，但更像是一个函数，因为常量是不可变的。一旦声明了常量，它就不会改变。声明一个常量很容易，如本版本的 MyClass 中所示：

```php
class MyClass {
    const requiredMargin = 1.7;
    function __construct($incomingValue) {
        // Statements here run every time
        // an instance of the class
        // is created.
    }
}
```

在这个类中，requiredMargin 是一个常量。它使用关键字 const 声明，在任何情况下都不能更改为 1.7 以外的值。请注意，常量名没有像变量名那样的前导 $。

## Abstract Classes

抽象类是不能实例化、只能被继承的类。使用关键字 abstract 声明抽象类，如下所示：

```php
abstract class MyAbstractClass {
   abstract function myAbstractFunction() {
   }
}
```

从抽象类继承时，子类必须定义父类声明中标记为 abstract 的所有方法；此外，这些方法必须使用相同的可见性定义。

请注意，抽象类内部的函数定义也必须以关键字 abstract 开头。在非抽象类中定义抽象函数是不合法的。

## Static Keyword

将类成员或方法声明为 static 可以在无需实例化类的情况下访问它们。声明为 static 的成员无法通过已实例化的类对象访问（尽管可以访问静态方法）。

Try out the following example:

```php
<?php
class Foo
{
   public static $my_static = 'foo';
   public function staticValue() {
      return self::$my_static;
   }
}
print Foo::$my_static . "\n";
$foo = new Foo();
print $foo->staticValue() . "\n";
```

## Final Keyword

PHP 5 引入了 final 关键字，通过在定义前加上 final 来防止子类重写方法。如果类本身被定义为 final，则不能被继承。

The following example results in Fatal error: Cannot override final method BaseClass::moreTesting()

```php
<?php
class BaseClass {
   public function test() {
      echo "BaseClass::test() called<br>";

   }

   final public function moreTesting() {
       echo "BaseClass::moreTesting() called<br>";
   }
}

class ChildClass extends BaseClass {
    public function moreTesting() {
        echo "ChildClass::moreTesting() called<br>";
    }
}

?>
```

## Calling parent constructors

与其为子类编写一个全新的构造函数，不如通过显式调用父类的构造函数，然后为实例化子类执行任何必要的额外操作来编写它。以下是一个简单示例：

```php
class Name
{
    var $_firstName;
    var $_lastName;
    function Name($first_name, $last_name)
    {
        $this->_firstName = $first_name;
        $this->_lastName = $last_name;
    }

    function toString() {
        return($this->_lastName .", ". $this->_firstName);
    }
}

class NameSub1 extends Name
{
    var $_middleInitial;

    function NameSub1($first_name, $middle_initial, $last_name) {
        Name::Name($first_name, $last_name);
        $this->_middleInitial = $middle_initial;
    }

    function toString() {
        return(Name::toString() . " " . $this->_middleInitial);
    }
}
```

在此示例中，我们有一个父类（Name），它有一个两参数构造函数；还有一个子类（NameSub1），它有一个三参数构造函数。NameSub1 的构造函数通过使用 :: 语法显式调用其父构造函数（传递其中两个参数），然后设置一个额外字段来工作。同样，NameSub1 定义其非构造函数 toString() 函数，以它重写的父函数为基础。

**注意：** 构造函数可以与类同名定义。上面的示例中已定义。

将 PHP 最简单地理解为可嵌入 HTML 文档的解释型 C。该语言本身非常类似 C，只是带有无类型变量、大量内置的 Web 特定库，并且一切都直接钩入您喜爱的 Web 服务器。

语句和函数定义的语法应该很熟悉，只是变量总是以 $ 开头，并且函数不需要单独的原型。

这里列出了 PHP 与 C 的一些相似之处和不同之处。

### Similarities

相似之处

- **语法：** 总的来说，PHP 语法与 C 相同：代码对空格不敏感，语句以分号结束，函数调用结构相同（my_function(expression1, expression2)），花括号（{ 和 }）将语句组合成块。PHP 支持 C 和 C++ 风格的注释（/* */）以及 //），还支持 Perl 和 shell 脚本风格（#）。

- **运算符：** 赋值运算符（=、+=、*= 等）、布尔运算符（&&、||、!）、比较运算符（<、>、<=、>=、==、!=）以及基本算术运算符（+、-、*、/、%）在 PHP 中的行为与 C 中相同。

- **控制结构：** 基本控制结构（if、switch、while、for）的行为与 C 中相同，包括支持 break 和 continue。一个显著的区别是，PHP 中的 switch 可以接受字符串作为 case 标识符。

- **函数名称：** 浏览文档时，您会看到许多看起来与 C 函数相同的函数名称。

### Differences

不同之处

- **美元符号：** 所有变量都以 $ 开头。变量不需要在赋值前提前声明，并且没有固有类型。

- **类型：** PHP 只有两种数值类型：integer（对应 C 中的 long）和 double（对应 C 中的 double）。字符串长度任意。没有单独的字符类型。

- **类型转换：** 类型不在编译时检查，运行时通常也不会出现类型错误。相反，变量和值会根据需要自动跨类型转换。

- **数组：** 数组的语法表面上与 C 的数组语法相似，但实现完全不同。它们实际上是关联数组或哈希表，索引可以是数字或字符串。不需要提前声明或分配。

- **没有结构体类型：** PHP 中没有 struct，部分原因是数组和对象类型合在一起使其变得多余。PHP 数组的元素不需要是一致的类型。

- **没有指针：** PHP 中没有可用的指针，尽管无类型变量起到了类似的作用。PHP 支持变量引用。您也可以在某种程度上模拟函数指针，即函数名称可以存储在变量中，并通过变量而非文字名称来调用。

- **没有原型：** 函数不需要在定义其实现之前声明，只要函数定义可以在当前代码文件或包含的文件中找到。

- **内存管理：** PHP 引擎实际上是一个垃圾回收环境（引用计数），在小脚本中不需要进行任何释放。您可以自由分配新结构，例如新字符串和对象实例。在 PHP5 中，可以为对象定义析构函数，但没有 free 或 delete。析构函数在对象的最后一个引用消失、内存被回收之前被调用。

- **编译和链接：** PHP 脚本没有单独的编译步骤。

- **宽松性：** 总体而言，PHP 比 C 更宽容（尤其是在其类型系统中），因此会让您犯下新的错误。意外结果比错误更常见。

