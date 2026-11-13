

```
return instance;
}

public function exampleName():String
{
    return "Joey";
}
}
```

本类的大部分内容与之前的示例相同，只是添加了 getInstance 方法。该方法用于确保始终使用类的唯一实例。对该类的任何调用都通过 getInstance 方法完成，例如：

```
import User;

trace("Example Call: " + User.getInstance().exampleName());
```

首次引用该类时会生成唯一实例。从那时起的任何调用都只需返回现有实例即可。这确保对该类的所有更改都会被所有调用者看到。该类背后的关键在于静态方法和属性，它们基本上在方法和调用者之间设置了一个门槛。所有经过 getInstance 的调用还允许你对所有调用进行授权检查。

> **注意** 单例应仅在需要时使用。将你创建的每个类都变成单例不是一种好的做法；事实上，大多数程序只有一个存储所有必要信息的单例。

## Getter 和 Setter

你可能注意到，很多类的使用都集中在来回传递数据上。从某种意义上说，这几乎就是所有编程的本质。Getter 和 Setter 的理念是为了访问私有属性。事实上，可以肯定地说，你的大多数属性都会是私有的，因为这本质上就是类的概念。下面是一个 Getter 和 Setter 的示例，以类骨架为例：

```
class People
{
    private var _person:String;
    public function get person():String
    {
        return _person;
    }
    public function set person(u:String):void
    {
        if(u.length > 0 && u.length < 25)
        {
            _person = u;
        }
    }
}
```

上述代码只是返回私有 `_person` 属性的当前值。或者，对 `person` 的调用会在新值长度至少为 1 且不超过 25 个字符时修改该私有属性。你可以向这些 Setter 添加任何级别的安全性或数据修改。使用 Setter 的优势在于能够锁定对私有属性的访问，这也称为封装。这确保代码不会因传入错误数据而损坏，或者更糟糕的是，由于类公开而导致系统被攻破。

既然你了解了什么是 Getter 和 Setter，大概也想知道如何调用它们。这可以通过访问公共变量来完成，例如：

```
var people:People = new People();
people.person = "Timmy";
trace("The new person is: " + people.person);
```

与编程的大多数方面一样，开发者有责任确定何时何地使用 Getter/Setter 是个好主意。确定这一点的最简单方法是先创建一个合适的应用程序大纲。

## 在 PHP 中使用类

既然你已经了解了什么是面向对象编程（OOP）及其工作原理，下一步就是了解 Flash 和 PHP 之间的类差异

首先，以下是 PHP 中类的快速示例：

```
<?php
class Example
{
public $sample = "Hello, World!";
function Example()
{
return $sample;
}
}
?>
```

这就是在 PHP 中设置类的基本方式。主要方面是以 public、private 或 protected 开头的属性定义。属性仍然需要 $，就像标准 PHP 代码一样。唯一的真正区别是 PHP 不声明返回类型。事实上，PHP 并不严格关心变量持有的类型，这实际上不是一件好事。开发者可能会失去知道变量持有什么类型数据的能力。

## 在 PHP 中导入类

在 PHP 中导入类是通过使用 include 或 require 加载文件来完成的。使用 include 会尝试加载文件，但如果找不到文件会继续执行。另一方面，require 也会查找文件，但如果找不到文件，会以致命错误退出脚本，如图 10.1 所示。使用 require 可以在找不到正确文件时停止脚本。以下是通过 require 加载类的示例：

```
<?php

if(!file_exists('Interface.php'))
{
    print "Class 'Interface' not loaded, exiting script!";
}
@require('Interface.php');

class Example
{
    function Example()
    {
        $i = new iExample();

        print "My i: " . $i->sample();
    }
}

$example = new Example();

?>
```

使用 if 语句先检查文件是否存在，因为 require 会产生致命错误，这意味着脚本将无法报告任何适当的错误消息。如果出于某种原因找不到文件，消息会发送到浏览器，脚本在到达 require 行时会静默结束。使用 @ 可以静默内部错误，这些错误往往会造成安全问题，因为它们会显示关键文件路径。隐藏错误的另一种方法是禁用错误报告，这在第 13 章中有说明。

## 图 10.1

以下是在浏览器中显示的错误消息，这是由于找不到类所致。

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_248_0.png)

在 PHP 中，方法使用以下方式访问：

```
$instance->methodName();
```

但是，当你想要访问同一类中的方法时，可以将实例变量替换为 `$this`。因此，假设你想要访问 `Speak` 类中的 `helloWorld` 方法，它看起来会像这样：

```
$this->helloWorld();
```

你也可以使用作用域解析运算符（也称为 Paamayim Nekudotayim，意为双冒号）来访问方法和属性。区别在于不使用 `$this`，而是使用实际的类名。这种方法使代码更易于阅读。

```
Speak::helloWorld();
```

## 多个类

PHP 允许一个类脚本包含多个类。这既是好主意也是坏主意，因为一个文件中包含太多类会导致臃肿且难以管理的代码。另一方面，将所有类放在一个文件中使分发更加容易。我相信你正在问自己：一个文件中究竟如何定义多个类？以下是一个伪类包的示例。

```
<?php

class Animals
{
    function Animal ()
    {
    }
    public function speak($word)
    {
        print $word;
    }
}

class Dog extends Animals
{
    function Dog($word)
    {
        $this->speak($word);
    }
}

// Create a new Dog
$dog = new Dog("Hello... Woof!" );

?>
```

事实上，PHP 并不遵循所有标准的 OOP 实践，但随着新版本的开发，我认为这种情况会改变。目前，你可以创建自己的包版本并获得相同的基本功能。需要注意的是，伪包不提供与真正的包相同级别的隔离和安全性，但通过一些创造性编程和正确创建类，你可以保持代码安全。

> 有关代码安全性的更多深入信息，请参见第 6 章。

就本书所需的程度而言，关于在 PHP 中使用和理解类的内容就这些。当然，你可以扩展这些新获得的知识，开始探索 PHP 中类的更高级方面。

> PHP 提供了大量“魔术”方法和属性，使使用类更加有趣且不那么痛苦。

## 在 Flash 中使用类

如前所述，Flash 和 PHP 中的类在大多数方面都很相似。让我们看看如何在 ActionScript Flash 中使用和修改类。

## 导入

如果找不到类，在 ActionScript 中导入类就不那么宽容了。事实上，当你导出电影时运行的编译器如果找不到类会停止。基本上这意味着如果类未加载，你不需要错误消息，因为电影永远无法被普通公众看到。

这个编译器检查的例外情况是如果类是动态的，这意味着其整体结构可以改变，但这超出了本书的范围。现在回到导入类，设置方法如下：

```
import com.organization.project.Example;
var example:Example = new Example();
trace("Call a method: " + example.methodName());
```

你可能注意到了使用 import 而不是 require 或 include。前面示例中另一个明显的区别是 :Example 类型定义。这实际上不是必需的，但在电影编译或运行时它允许更好的错误检查。

## 文档类

文档类用作应用程序的主类。你可以将其视为时间轴类，类似于过去在电影第 1 帧添加基本代码的日子。那些日子已经过去了，这也是件好事。但是，使用文档类时有一些需要知道的事项，如图 10.2 所示。首先，看看文档类是什么样子：

```
package
{
import flash.display.MovieClip;
public class DocRoot extends MovieClip
{
function DocRoot()
{
trace("I am the Document Class");
}
}
}
```

