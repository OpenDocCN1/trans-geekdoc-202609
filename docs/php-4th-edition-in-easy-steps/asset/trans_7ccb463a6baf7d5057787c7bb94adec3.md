
可见变量数为零。暂时将其访问说明符更改为 `public`，即可看到它变为 3 ——封装的实际效果。

## 属性提升

![image](images/pg114_1.jpg)

创建声明属性然后在构造函数中为其赋值的典型语法相当冗长：

```
class ClassName
{
access-specifier type $property ;
function __construct( type $arg )
{
$this->property = $arg ;
}
}
```

幸运的是，这可以通过在构造函数方法的参数前添加其中一个访问说明符（`public`、`private` 或 `protected`）来简化。这会“提升”参数，使得以参数名称命名的属性会自动添加到类中，并在构造函数方法体中对这些属性进行转发赋值。构造函数属性提升是从构造函数声明并分配类属性的简写语法。无需先声明属性，因此语法现在看起来像这样：

```
class ClassName
{
function __construct ( access-specifier type $property ) { }
}
```

![image](images/hot.jpg)

在构造函数中提升类属性的能力是 PHP 8 中引入的一个很棒的新特性。

构造函数的函数体仍然可以包含要执行的语句，并且属性可以像往常一样使用类的 setter 和 getter 方法访问。

![image](images/1v.jpg)开始一个 PHP 脚本，使用一条语句声明一个使用标准属性的类

```
<?php
class Paint_1
{
private string $color ;
function construct( string $hue = ‘Blue’ )
{
$this->color = $hue ;
}
public function setColor( string $c ){ $this->color = $c ; }
public function getColor(){ return $this->color ; }
}
```

![image](images/commonv.jpg)

`promoter.php`

![image](images/2v.jpg)接下来，在脚本中添加一条语句来创建该类的实例

```
$pot_1 = new Paint_1() ;
```

![image](images/3v.jpg)现在，添加语句来调用类方法

```
echo $pot_1->getColor().'<br>' ;
echo $pot_1->setColor( 'Yellow' ) ;
echo $pot_1->getColor().'<hr>' ;
```

![image](images/4v.jpg)然后，使用提升属性的简化语法声明一个类似的类

```
class Paint_2
{
function __construct( private string $color = ‘Red’ ) { }
public function setColor( string $c ){ $this->color = $c ; }
public function getColor(){ return $this->color ; }
}
```

![image](images/5v.jpg)接下来，在脚本中添加一条语句来创建类似类的实例

```
$pot_2 = new Paint_2() ;
```

![image](images/6v.jpg)最后，添加语句来调用类似类的类方法

```
echo $pot_2->getColor().'<br>' ;
echo $pot_2->setColor( 'Green' ) ;
echo $pot_2->getColor() ;
?>
```

![image](images/7v.jpg)将文档保存在 Web 服务器的 `/htdocs` 目录中，命名为 `promoter.php`，然后通过 HTTP 打开页面，查看标准属性和提升属性的输出

![image](images/pg115_1.jpg)

![image](images/forget.jpg)

只有 `__construct()` 方法可以拥有提升的属性。

![image](images/hot.jpg)

技术上可以混合使用标准属性和提升属性，但这可能会产生不清晰的代码 —— 只使用一种技术。

## 继承属性

![image](images/pg116_1.jpg)

PHP 类可以像前面的示例那样作为全新类创建，也可以从现有类“派生”。重要的是，派生类继承自其派生的父类（基类）的成员 —— 除其自身成员之外。

从基类继承成员的能力允许创建共享某些通用属性的派生类，这些属性已在基类中定义。例如，“Polygon”基类可能定义 `width` 和 `height` 属性，这些属性对所有多边形都是通用的。“Rectangle”和“Triangle”类可以从 Polygon 类派生 —— 继承 `width` 和 `height` 属性，以及定义其独特特征的自身成员。

![image](images/pg116_2.jpg)

继承的优点极其强大，是面向对象编程（OOP）的第二个原则。

派生类声明在其类名后添加 `extends` 关键字，后跟其派生的类名：

![image](images/1v.jpg)开始一个 PHP 脚本，通过声明一个名为“Polygon”的基类，该基类有两个由构造函数初始化的私有变量，并有两个公共 getter 方法

```
<?php
class Polygon
{
private $width , $height ;
function __construct( int $w = 4 , int $h = 5 )
{
$this->width = $w ;
$this->height = $h ;
}
public function getWidth() { return $this->width ; }
public function getHeight() { return $this->height ; }
}
```

![image](images/commonv.jpg)

`inheritance.php`

![image](images/2v.jpg)在 Polygon 类之后，声明一个派生自 Polygon 类并添加唯一方法的“Rectangle”类

```
class Rectangle extends Polygon
{
public function area()
{
return ( $this->getWidth() * $this->getHeight() ) ;
}
}
```

![image](images/3v.jpg)在 Rectangle 类之后，声明一个派生自 Polygon 类并添加唯一方法的“Triangle”类

```
class Triangle extends Polygon
{
public function area()
{
return ( $this->getWidth() * $this->getHeight() / 2 ) ;
}
}
```

![image](images/4v.jpg)在 Triangle 类之后，添加两条语句，使用默认值创建每个派生类的实例

```
$rect = new Rectangle() ;
$trio = new Triangle() ;
```

![image](images/5v.jpg)最后，添加两条语句来输出每个派生类的唯一方法返回的值

```
echo 'Rectangle Area : '.$rect->area().'<hr>' ;
echo 'Triangle Area : '.$trio->area() ;
?>
```

![image](images/6v.jpg)将文档保存在 Web 服务器的 `/htdocs` 目录中，命名为 `inheritance.php`，然后通过 HTTP 打开页面，查看继承成员的输出

![image](images/pg117_1.jpg)

![image](images/snake.jpg)

不要混淆类实例和派生类 —— 实例是类的副本，而派生类是从其派生的基类继承属性的新类。

![image](images/forget.jpg)

在 PHP 中，派生类始终依赖于单个基类 —— 不支持多重继承。

## 拥抱多态

![image](images/pg116_1.jpg)

面向对象编程（OOP）的三大基石是封装、继承和多态。在前面的页面中，我们已经看到数据如何封装在 PHP 类中，以及派生类如何继承其基类的属性，因此我们现在可以探索多态这一最后基石原则。

术语“多态”（源自希腊语，意为“多种形式”）描述了根据上下文为实体分配不同含义或目的的能力。例如，在现实世界中，每个人都知道如何使用按钮（实体）——你只需对其施加压力。然而，该按钮的作用取决于它连接的是什么（上下文），但结果不会影响按钮的使用方式。

在面向对象编程的世界中，多态允许类在共享通用接口的同时具有不同的功能。接口不需要知道它使用的是哪个类，因为它们就像现实世界的按钮一样，都以相同的方式使用，但可以产生不同的上下文结果。以这种方式拥抱多态使程序员能够创建可互换的对象，这些对象可以根据需求而不是条件测试来选择。

PHP 接口类似于类，但使用 `interface` 关键字声明，并且只能包含方法定义，不能包含要执行的任何方法语句，像这样：
