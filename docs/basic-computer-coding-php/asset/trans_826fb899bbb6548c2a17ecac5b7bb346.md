

属性（property）返回子类上的属性值，而引用方法则会在子类上调用方法。

要访问被重写的方法，请使用 `parent::method()` 符号：

```
parent::birthday(); // 调用父类的
birthday( ) 方法
```

一个常见的错误是在调用被重写的方法时，硬编码了父类的名称：

```
Creature::birthday( ); 当 当 Creature
是父类时
```

这是一个错误，因为它将父类名称的知识分散到了整个派生类中。使用 `parent::` 可以将父类的相关知识集中在 `extends` 子句中。

从句（Clause）由一个主语和一个谓语组成，是表达一个完整思想的最小语法单位。

## 6.3.4 构造函数

在实例化对象时，你可以在类名后提供一个参数列表：

`$person = new Person('Fred', 35)`

这些参数被传递给类的构造函数，构造函数是一个初始化类属性的特殊函数。

构造函数是一个与其定义的类名同相同的函数。以下是 Person 类的构造函数：

```php
class Person {
    function Person ($name, $age) {
        $this->name = $name;
        $this->age = $age;
    }
}
```

## 基础计算机编程：PHP

PHP 不提供自动的构造函数链；也就是说，如果你实例化派生类的对象，只有派生类中的构造函数会被自动调用。要调用父类的构造函数，派生类中的构造函数必须显式地调用。在这个示例中，Employee 类的构造函数调用了 Person

```php
class Person {
    var $name, $address, $age;
```

## 记住

不要忘记，在类中，变量被称为“属性”（properties），函数被称为“方法”（methods）。

```php
function Person($name, $address, $age) {
    $this->name = $name;
    $this->address = $address;
    $this->age = $age;
}
```

```php
var $position, $salary;

function Employee($name, $address, $age, $position, $salary) {
    $this->Person($name, $address, $age);
    $this->position = $position;
    $this->salary = $salary;
}
```

## 6.3.5 引用

当你将一个对象赋值另一个变量时，你创建了一个副本：
`$fred = new Person;`
`$copy = $fred;`
`$fred->name("Fred");`

`print $copy->name(); // 不打印 "Fred"`

你现在有两个 Person 对象，$fred 和 $copy，它们具有独立的属性值。当你将构造函数的调用结果赋值时情况也是如此，如下所示：

`$fred = new Person;`

由 Person 构造函数创建的对象被复制了，副本存储在 $fred 中。这意味着构造函数中的 `$this` 和 $fred 实际上引用的是两个不同的对象。如果构造函数通过引用创建了 $this 的别名，它将不会为 $fred 创建别名。例如：

```php
$people = array();
class Person {
    function Person () {
        global $people;
        $people[] = &$this;
    }
}
$fred = new Person;
$fred->name = "Fred";
$barney = &new Person;
$barney->name = "Barney";
var_dump($people);
array(2) {
    [0]=>object(person)(0) {
}
    [1]=>
```

## 基础计算机编程：PHP

```php
&object(person)(1) {
  ["name"]=>
    string(6) "Barney"
}
```

$fred 是构造函数存储在 $people[0] 中对象的副本，而 $barney 是构造函数存储在 $people[1] 中对象的别名。当我们更改 $fred 的属性时，我们并没有更改 $people[0] 中的对象。然而，当我们更改 $barney 的属性时，我们正在更改 $people[1] 中的对象。要防止赋值时产生复制，请通过引用赋值：`$obj=$& new Class;`

这行代码使 $obj 成为新对象的别名，而该对象在构造函数中是 $this。如果构造函数存储了对 $this 的引用，它就会保留对 $obj 的引用。

类的文档应该说明你是否需要对其构造函数使用 `&=`。在大多数情况下，这是必要的。

## 案例研究

## Cube Evolution

Cube Evolution 是一家总部位于英国的软件公司，生产定制软件和网页设计。其产品之一是一个 Web 内容管理系统（CMS），允许个人和公司轻松地维护自己的网站。

然而，按照最初的设计，CMS 软件并不安全。任何购买系统的客户都可以轻松看到源代码并获取任何编程语言，导致公司面临软件被盗的风险。客户还可以对代码进行修改，可能导致产品故障。这可能导致公司的支持部门被修改程序的用户的电话淹没。

SourceGuardian 为 Cube Evolution 提供了一个解决方案，保护其 CMS 软件免受盗窃和篡改，同时。

## 基础计算机编程：PHP

## 总结

- 面向对象编程 (OOP)是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

## 基础计算机编程：PHP

--面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

- 面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

- 面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

- 面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

- 面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

- 面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

- 面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

- 面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

- 面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

- 面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

- 面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

- 面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

- 面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

- 面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 可见性级别：私有（private）、受保护（protected）和公共（public）。
- 构造函数和析构函数。
- 基础计算机编程：PHP

- 面向对象编程 (OOP) 是一种组织代码的方式。
- 类和对象。
- 属性。
- 方法。
- 调用方法，使用 `->` 后跟括号。
- 使用不使用数组函数查找数组中最大值的程序。
- 检查：PHP

## 练习题

1. 什么是对象？
2. 构造函数和析构函数是什么？
3. 写一个查找数组中最小值的程序。
4. 写一个不使用数组函数查找数组中最大值的程序。

## 结果

1. (b) 2. (c) 3. (d) 4. (d) 5. (d)

## 参考文献

1. Adobe Systems Incorporated. “Adobe Dreamweaver CS5 系统要求和语言”。[www-document]. 获取自：http://www.adobe.com/products/dreamweaver/tech-specs.html?promoid=DR 2011-01-29
2. Google, “Google Maps API”。[www-document]. 地址：http://maps.google.com
3. http://www.zentut.com/php-tutorial/objects-and-classes/
4. https://phpenthusiast.com/object-oriented-php-tutorials/create-classes-and-objects
5. https://www.w3resource.com/php/classes/object-oriented-programming.php
6. Jean-François P., “适用于 OpenVMS 的开源软件套件”。[地址]:http://pi-net.dyndns.org/anonymous/kits/ 2009-06-08
7. Mark D., “Unicode 接近 Web 的 50%”。[www-document]. 地址：http://googleblog.blogspot.com/2010/01/unicode-nearing-50-of-web.html. 2010-12-05
8. The MySQL Benchmark Suite。[www-document]. 地址：http://dev.mysql.com/doc/refman/5.1/en/mysql-benchmarks.html. 2011
9. W3Techs. “网站使用的字符编码情况”。[www-document]. 地址：http://w3techs.com/technologies/overview/character_encoding/all 2010-03-30

