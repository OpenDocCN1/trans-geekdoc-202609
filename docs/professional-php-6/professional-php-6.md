# PHP 6 高级指南






## 面向对象编程简介

面向对象（OO）软件开发对主要编写过程式代码的开发人员来说可能是一个令人困惑的话题，但并不一定如此。在本章中，你将探讨 OO 背后的一些基本理论，并学习其（有时令人生畏的）多音节术语。你还将了解为什么应该对 OO 技术感兴趣，它们如何大大提高开发复杂应用程序的速度，以及你可以多么容易地修改这些应用程序。

接下来的几章将扩展这里提出的想法，并让你熟悉一些稍微高级一点的主题。如果你已经在 PHP 6 之外接触过 OO 开发，你可能可以跳过本章和下一章。然而，这些材料是很好的复习，因此建议你通读全文。

### 什么是面向对象编程？

面向对象编程（OOP）要求你以不同的方式思考如何构建应用程序。对象使你能够更紧密地在代码中模拟应用程序设计用于处理的现实世界任务、流程和理念。与其将应用程序视为将数据块从一个函数传递到下一个函数的控制流程，OOP 方法使你能够将应用程序建模为一组协作对象，这些对象独立处理某些活动。

作为类比，当房屋在建造时，水管工处理管道，电工处理电线。水管工不需要知道卧室的电路是 10 安培还是 20 安培。他们只需关心自己的活动。总承包商确保每个分包商完成需要完成的工作，但不一定对每个任务的细节感兴趣。OOP 方法与此类似，每个对象向其他对象隐藏其实现细节。它如何完成工作与系统的其他组件无关。重要的是对象能够提供的服务。

类和对象的概念，以及你在软件开发中如何利用这些想法，是 OOP 背后的基本理念。从某种意义上讲，这与过程式编程相反，过程式编程是使用函数和全局数据结构的编程。正如你将看到的，OO 方法相对于过程式编程提供了显著的优势，并且（随着首次出现在 PHP5 并在 PHP6 中进一步改进的 OO 支持的新实现）还带来了一些较大的性能提升。

### OOP 优势

OOP 的主要优势之一是将单个业务需求转换为单个代码模块的简便性。由于 OOP 方法使你能够基于现实世界对象的想法来建模应用程序，你通常可以在人、事物和概念与等效类之间识别出直接的相关性。这些类与它们所代表的现实世界概念具有相同的属性和行为，这有助于你快速识别必须编写什么代码以及应用程序的不同部分必须如何交互。

OOP 的第二个优势是代码复用。你经常需要在同一应用程序的不同位置使用相同类型的数据。例如，一个使医院能够管理其患者记录的应用程序肯定需要一个名为 Person 的类。许多参与患者护理的人员——患者、医生、护士、医院管理人员、保险索赔人员等等。在患者护理的每个步骤中，该患者的记录都需要注明哪个人正在执行给定动作（例如开药、清洁伤口或向保险公司寄账单），并验证该人是否有权执行该动作。通过定义一个名为 Person 的通用类，涵盖这些人员共有的所有属性和方法，你将获得大量代码复用，这在过程式编程方法中并不总是可能的。

其他应用程序呢？你能想到多少应用程序，在某个时刻处理有关个人的信息？可能相当多。编写良好的 Person 类可以轻松地从一个项目复制到另一个项目，几乎不需要更改，立即为你提供之前为处理有关个人的信息而开发的所有丰富功能。这是 OO 方法最大的优势之一——在给定应用程序内部以及跨不同项目之间进行代码复用的机会。

OOP 的另一个优势来自类的模块化。如果你在 Person 类中发现错误，或者想要添加或更改该类的功能方式，你只有一个地方需要去。该类的所有功能都包含在单个文件中。依赖于 Person 类的应用程序的任何进程都会立即受到对其更改的影响。这可以大大简化查找错误的过程，并使功能添加成为相对无痛的任务。

### 现实世界示例

它们在较小的应用程序中可能看起来微不足道，但在更复杂的软件架构中，模块化的好处可能是巨大的。本书的一位作者参与了一个涉及 200,000 多行过程式 PHP 代码的项目。轻易就有 65% 的修复错误的时间都用于发现某些函数的位置并确定哪些数据与哪些函数交互。随后，该软件在 OO 架构中的重写导致了代码量的显著减少。如果应用程序从一开始就以这种方式实现，不仅会从一开始就减少开发时间，而且还会发现更少的错误（代码量越小，问题出现的机会越少），并加快错误修复的周转时间。

由于 OO 方法很容易适应清晰记录应用程序结构的系统（参见第 2 章），当你刚加入开发团队时，了解现有应用程序的结构要容易得多。此外，你还有一个框架来帮助你确定可能开发的新功能的适当位置。

较大的项目通常拥有一个多团队的软件开发团队，通常由能力不一的程序员组成。在这里，OO 方法相对于过程式方法也具有显著优势。对象向其用户隐藏其实现细节。与其需要理解复杂的数据结构和业务逻辑的所有怪癖，团队初级成员可以（只要有少量文档）开始使用由更有经验的成员创建的对象。对象本身负责触发数据或系统状态的更改。

当之前提到的大型应用程序仍然使用过程式代码编写时，软件开发团队的新成员通常需要长达两个月的时间才能了解足够的应用程序知识以提高生产力。在使用对象重建软件后，团队新成员通常只需几天时间就能开始对代码库进行重大添加。他们能够快速使用即使是最复杂的对象，因为他们不需要完全理解对象内部所包含的功能是如何实现的。

现在你已经很好地了解了为什么应该考虑将 OO 范式作为你首选的编程方法，你应该阅读接下来的几个部分，以更好地理解 OO 背后的基本概念。如果一切顺利，在接下来两章的过程中，你将开始亲自看到这种方法的好处。

### 理解 OOP 概念

本节介绍面向对象编程的主要概念并探讨它们如何交互；第 3 章探讨在 PHP6 中实现它们的具体细节。本章涵盖以下主题：

- 类 — 对象的“蓝图”以及定义属性和方法的实际代码
- 对象 — 类的运行实例，包含应用程序运行所需的所有内部数据和状态信息
- 继承 — 定义一种类作为另一种类的子类型的能力（很大程度上就像正方形是一种矩形）
- 多态性 — 允许将类定义为多个类别类别的成员（就像汽车既是“带发动机的东西”又是“带轮子的东西”）





- Interfaces — 指定对象能够执行某项操作的一种方式，而无需实际定义如何执行（例如，狗和人类都是“会走路的东西”，但它们的做法截然不同）
- Encapsulation — 对象保护其内部数据访问的能力

如果上述任何术语看起来难以理解，请不要担心。后续内容将阐明一切。你新获得的知识甚至可能彻底改变你进行软件开发项目的方式。

## 类

在现实世界中，对象具有特征和行为。汽车有颜色、重量、制造商和一定容量的油箱。这些是它的特征。汽车可以加速、停车、转向信号和按喇叭。这些是它的行为。所有汽车共有这些特征和行为。虽然同一个停车场里的两辆特定汽车可能颜色不同，但所有汽车都有颜色。利用一种称为类的构造，OOP使你能够建立汽车具有所有这些特征的概念。类是一段代码单元（由变量和函数组成），用于描述集合中所有成员的特征和行为。名为Car的类将描述所有汽车共有的属性和方法。

在OO术语中，类的特征称为其属性。属性有名称和值。有些允许更改其值；有些则不允许。例如，在Car类中，你可能会拥有颜色和重量等属性。虽然可以通过重新喷漆来改变汽车的颜色，但汽车的皮重（不包括货物或乘客）是一个固定值。

有些属性表示对象的状态。状态是指那些因某些事件而改变，但不一定能够直接自行修改的特征。在模拟车辆性能的应用程序中，Car类可能有一个名为velocity的属性。汽车的速度不是可以自行更改的值，而是发送到发动机的燃油量、该发动机的性能特征以及汽车行驶地形的副产品。

类的行为称为其方法。类的方法在语法上等同于传统过程式代码中的函数。就像函数一样，方法可以接受任意数量的参数，每个参数可以是任何有效的数据类型。有些方法作用于作为参数传递给它们的外部数据，但它们也可以作用于其对象的属性，无论是使用这些属性来指导方法所采取的操作（例如，名为accelerate的方法检查剩余燃油量以确定汽车是否能够加速），还是通过修改汽车速度等值来改变对象的状态。

## 对象

首先，你可以将类视为构建对象的蓝图。就像可以根据同一张蓝图建造许多房屋一样，你可以从其类中构建多个对象实例；但蓝图并不指定墙壁颜色或地板类型等细节。它仅仅指定这些东西将会存在。类的工作方式大体相同。类指定对象将具有的行为和特征，但不一定指定这些特征的值。对象是使用类提供的蓝图构建的具体实体。房子的想法类似于类。你的房子（房子想法的一个特定实例）类似于对象。

有了蓝图和一些建筑材料，你就可以建造房屋。在OOP中，当你使用类来构建对象时，这个过程称为实例化。实例化对象需要两件事：

- 用于加载对象的内存位置。这由PHP自动为你处理。
- 将填充属性值的数据。这些数据可以来自数据库、纯文本文件、另一个对象或其他来源。

类永远不能拥有属性值或状态。只有对象可以。你必须先使用蓝图建造房屋，然后才能给它贴墙纸或安装乙烯基外墙板。同样，你必须先从类中实例化对象，然后才能与其属性交互或调用其方法。类在设计时被操作，当时你对方法或属性进行更改。对象在运行时被操作，当时将值分配给其属性，并调用其方法。何时使用“类”一词以及何时使用“对象”这一问题常常让初学者感到困惑。

对象实例化后，即可用于实现应用程序的业务需求。让我们看看如何在PHP中具体操作。

## 创建类

从简单示例开始，将以下内容保存到名为class.Demo.php的文件中：

```php
<?php
class Demo {
}
?>
```

搞定——这就是Demo类。虽然目前还不算激动人心，但这是在PHP中声明新类的基本语法。使用关键字class让PHP知道你即将定义一个新类。接着跟上类名和花括号，以指示该类代码的开始和结束。

为组织源代码文件建立明确定义的约定非常重要。一个很好的经验法则是将每个类放入其自己的文件中，并将该文件命名为class.[ClassName].php。

你可以像这样实例化Demo类型的对象：

```php
<?php
require_once( 'class.Demo.php' );

$objDemo = new Demo();
?>
```

要实例化对象，首先确保PHP知道在哪里可以找到类声明，方法是包含包含你的类的文件（本示例中的class.Demo.php）；然后调用new运算符并提供类名，后跟左括号和右括号。该语句的返回值被赋给一个新变量，本示例中为$objDemo。现在你可以调用$objDemo对象的方法并检查或设置其属性的值——如果它实际上有任何属性的话。

尽管你创建的类目前还没有什么作用，但它仍然是一个有效的类定义。

## 添加方法

如果Demo类无法做任何事情，那就不是特别有用，所以让我们看看如何创建方法。请记住，类的方法基本上就是一个函数。通过在类的花括号内编写函数，你正在向该类添加方法。以下是示例：

```php
<?php

class Demo {
    function sayHello($name) {
        print "Hello $name!";
    }
}

?>
```

源自你的类的对象现在能够向任何调用sayHello方法的人打印问候语。要在$objDemo对象上调用该方法，你需要使用->运算符来访问新创建的函数：

```php
<?php

require_once('class.Demo.php');

$objDemo = new Demo();

$objDemo->sayHello('Steve');

?>
```

对象现在能够打印友好的问候语。->运算符用于访问对象的所有方法和属性。

> 对于曾在其他编程语言中接触过OOP的读者，请注意，->运算符始终用于访问对象的方法和属性。PHP在其OO语法中根本不使用点运算符（.）。

## 添加属性

向类添加属性与添加方法同样简单。你只需在类内部声明一个变量来保存属性的值。在过程式代码中，当你想要存储某个值时，会将该值赋给变量。在OOP中，当你想要存储属性的值时，你也使用变量。这个变量在类声明的顶部声明，位于括起类代码的花括号内。变量的名称就是属性的名称。如果变量名为$color，你将拥有一个名为color的属性。

打开class.Demo.php文件并添加以下高亮代码：

```php
<?php
class Demo {
  public $name;
  function sayHello() {
    print "Hello $this->name!";
  }
}
?>
```

这个名为$name的新变量，就是你在Demo类中创建名为name的属性所需的全部内容。要访问此属性，你使用与前面示例相同的->运算符，并附上属性名。重写后的sayHello方法展示了如何访问此属性的值。

创建一个名为testdemo.php的新文件并添加以下内容：

```php
<?php
require_once('class.Demo.php');
$objDemo = new Demo();
$objDemo->name = 'Steve';
$objAnotherDemo = new Demo();
$objAnotherDemo->name = 'Ed';
$objDemo->sayHello();
$objAnotherDemo->sayHello();
?>
```

保存文件，然后在Web浏览器中打开它。字符串“Hello Steve!”和“Hello Ed!”将打印到屏幕上。

关键字public用于让类知道你希望从类外部访问以下变量。类的一些成员变量仅供类本身使用，不应对外部代码开放；这些变量声明为private或protected（稍后将详细介绍）。在此示例中，你希望能够设置和检索name属性的值。请注意，sayHello方法的工作方式已经发生了变化。它不再接受参数，而是现在从属性中获取name值。

你使用变量$this，以便对象可以获取有关其自身的信息。例如，你可能有多个类的对象，并且因为你无法预先知道对象变量的名称，$this变量使你能够引用当前实例。





在之前的示例中，第一次调用 sayHello 打印 "Steve"，第二次调用打印 "Ed"。这是因为 $this 变量允许每个对象访问其自身的属性和方法，而不必知道在外部应用程序中代表它的变量的名称。此前，你已了解某些属性会影响特定方法的行为，例如 Car 类的 accelerate 方法需要检查剩余燃料量的示例。accelerate 内部的代码会使用类似 $this->amountOfFuel 的代码来访问此属性。

> 访问属性时，只需要一个 $。语法是 $obj->property，而不是 $obj->$property。这一事实常常让初学者感到困惑。属性变量声明为 public $property，并使用 $obj->property 来访问。

除了存储类属性值的变量之外，还可以声明其他变量以供类的内部操作使用。这两种数据统称为类的内部成员变量。其中一些以属性的形式对类外部的代码可访问。另一些不可访问，且严格用于内部维护。例如，如果 Car 类出于某种原因需要从数据库获取信息，它可能会在内部成员变量中保存数据库连接句柄。这个数据库连接句柄显然不是汽车的属性，而是类执行某些操作所需要的东西。

## 保护对成员变量的访问

如前示例所示，你可以将 name 属性的值设置为几乎任何你想要的内容——包括对象、整数数组、文件句柄或任何其他无意义的值。但是，在设置 name 属性时，你没有机会进行任何类型的数据验证或更新任何其他值。

为解决此问题，请始终以名为 get[ 属性名 ] 和 set[ 属性名 ] 的函数形式实现你的属性。此类函数称为访问器方法，如下示例所示。

按如下所示修改 class.Demo.php：

```
<?php
class Demo {
  private $_name;

  public function sayHello() {
    print "Hello " . $this->getName() . "!";
  }

  public function getName() {
    return $this->_name;
  }

  public function setName($name) {
    if(!is_string($name) || strlen($name) == 0) {
      throw new Exception("Invalid name value!");
    }

    $this->_name = $name;
  }
}
?>
```

按如下所示修改 testdemo.php：

```
<?php
require_once('class.Demo.php');
$objDemo = new Demo();
$objDemo->setName('Steve');
$objDemo->sayHello();
$objDemo->setName(37); //would trigger an error
?>
```

如你所见，`name` 的成员访问级别已从 `public` 更改为 `private`，并加上了下划线前缀。下划线是推荐的命名约定，用于指示私有成员变量和函数；然而，这仅是一种约定——PHP 并不强制要求。关键字 `private` 保护对象外部的代码不得修改此值。私有内部成员变量不可从类外部访问。因为你无法直接访问这些变量，所以被迫使用 `getName()` 和 `setName()` 访问器方法来获取此信息，确保你的类在允许设置值之前可以先检查该值。

在此示例中，如果为 `name` 属性提供了无效值，则会抛出异常。
此外，已为函数添加了 `public` 访问说明符。`public` 是未显式设置可见性的任何成员变量或函数的默认可见性级别，但最好始终显式声明类中所有成员的可见性。

成员变量或方法可以有三种不同的可见性级别：public、private 和 protected。`Public` 成员可被任何代码访问。`Private` 成员仅可被类本身访问。这些通常用于内部维护，可能包括数据库连接句柄或配置信息等内容。`Protected` 成员可被类本身及其继承的类访问。（继承将在本章后面详细定义和讨论。）

为所有属性创建访问器方法，以后添加数据验证或新业务逻辑，或对对象进行其他更改时会容易得多。即使你的应用程序当前的业务需求不涉及对某个属性进行数据验证，你也应该使用 `get` 和 `set` 函数实现该属性，以便将来可以添加验证或业务逻辑功能。

> 始终为你的属性使用访问器方法。将来对业务逻辑和数据验证要求的更改将更容易实现。

## 初始化对象

对于你创建的许多类，在首次实例化该类的对象时，你需要进行一些特殊设置。例如，你可能需要从数据库获取一些信息或初始化某些属性值。通过创建名为 _构造函数_ 的特殊方法，在 PHP 中使用名为 `__construct()` 的函数来实现，你可以执行实例化对象所需的任何活动。PHP 将在实例化对象时自动调用此特殊函数。

例如，你可以按如下方式重写 `Demo` 类：

```
<?php
class Demo {
    private $name;
    public function __construct($name) {
        $this->name = $name;
    }
    function sayHello() {
        print "Hello $this->name!";
    }
}
?>
```

当你实例化 `Demo` 类的新对象时，`__construct` 函数将自动调用。请注意，你需要更新 `testdemo.php`，在构造函数中传递名称，而不是在设置器方法中传递。

*在 PHP 4 中，对象构造函数是与类同名的函数。PHP 5 版本更改为使用统一的构造函数方案。为保持向后兼容性，PHP 首先会查找名为 `__construct` 的函数，但如果找不到，仍会查找与类同名的函数（如前示例中的 `public function Demo()`）。尽管这种向后兼容性在 PHP 6 中得以保留，但无法保证未来版本会继续保留。*

如果你有一个不需要运行任何特殊初始化代码的类，则无需创建构造函数。如你在 `Demo` 类的第一个版本中所见，PHP 会自动完成创建该对象所需的操作。仅在需要时才创建构造函数。

## 销毁对象

你创建的对象变量在请求的页面运行完成、变量超出作用域或被显式设置为 null 时，将从系统内存中移除。在 PHP 6 中，你可以捕获对象的销毁并在发生时采取措施。为此，请创建一个名为 `__destruct`、无参数的函数。在对象销毁之前，如果该函数存在，会自动调用它。

调用此函数可让你有机会执行任何最后的清理工作（例如关闭类可能打开的文件句柄或数据库连接），或在对象销毁前可能需要的任何其他最后维护工作。

下面的示例从数据库获取对象的属性。如果对象的任何属性发生更改，它们会在对象销毁时自动保存回数据库。这消除了显式调用保存方法的必要性。析构函数还会关闭打开的数据库连接句柄。

与本书中的大多数数据库示例一样，此示例使用 PostgreSQL 作为其平台。作者坚信，PostgreSQL 的高级功能、事务支持和强大的存储过程机制使其成为 MySQL 和其他开源关系数据库管理系统（RDBMS）在大规模企业软件开发中的优越替代方案。如果你不



拥有一个可供使用的 PostgreSQL 环境，或者如果您偏爱 MySQL（如许多人所做），请随意为您使用的数据库平台做出相应的修改。

使用以下 SQL 语句创建名为 "widget" 的表：

```sql
CREATE TABLE "widget" (
    "widgetid" SERIAL PRIMARY KEY NOT NULL,
    "name" varchar(255) NOT NULL,
    "description" text
);
```

插入一些数据：

```sql
INSERT INTO "widget" ("name", "description")
VALUES('Foo', 'This is a footacular widget!');
```

创建一个名为 class.Widget.php 的文件，并输入以下代码：

```php
<?php

class Widget {

    private $id;
    private $name;
    private $description;
    private $hDB;
    private $needsUpdating = false;

    public function __construct($widgetID) {
        //The widgetID parameter is the primary key of a
        //record in the database containing the information
        //for this object

        //Create a connection handle and store it in a private member variable
        //This code assumes the DB is called "parts"
        $this->hDB = pg_connect('dbname=parts user=postgres');
        if(! is_resource($this->hDB)) {
            throw new Exception('Unable to connect to the database.');
        }

        $sql = "SELECT \"name\", \"description\" FROM widget WHERE widgetid = 
        $widgetID";
        $rs = pg_query($this->hDB, $sql);
        if(! is_resource($rs)) {
            throw new Exception("An error occurred selecting from the database.");
        }

        if(! pg_num_rows($rs)) {
            throw new Exception('The specified widget does not exist!');
        }
        $data = pg_fetch_array($rs);
        $this->id = $widgetID;
        $this->name = $data['name'];
        $this->description = $data['description'];
    }

    public function getName() {
    	return $this->name;
    }

    public function getDescription() {
    	return $this->description;
    }

    public function setName($name) {
    	$this->name = $name;
    	$this->needsUpdating = true;
    }

    public function setDescription($description) {
    	$this->description = $description;
    	$this->needsUpdating = true;
    }

    public function __destruct() {
    	if($this->needsUpdating) {
    		$sql = 'UPDATE "widget" SET ';
    		$sql .= "\"name\" = '" . pg_escape_string($this->name) . "', ";
    		$sql .= "\"description\" = '" . 
    		pg_escape_string($this->description) . "'";
    		$sql .= "WHERE widgetID = " . $this->id;

    		$rs = pg_query($this->hDB, $sql);
    	}

    	//We're done with the database. Close the connection handle.
    	pg_close($this->hDB);
    }
}
?>
```

该对象的构造函数使用默认超级用户账户 *postgres* 打开到名为 *零件* 的数据库的连接。此连接句柄保存在私有成员变量中，以便日后使用。
作为参数传递给构造函数的 ID 值用于构建 SQL 语句，以获取数据库中指定主键的小部件信息。然后将数据库中的数据分配给私有成员变量，以供 `get` 和 `set` 函数使用。请注意，如果出现任何问题，构造函数会抛出异常，因此请务必将任何尝试构造 `Widget` 对象的操作包裹在 `try...catch` 块中。

两个访问器方法 `getName()` 和 `getDescription()` 使您能够获取私有成员变量的值。同样，`setName()` 和 `setDescription()` 方法使您能够为这些变量赋予新值。请注意，当赋予新值时，`needsUpdating` 值会被设置为 `true`。如果没有任何更改，则无需更新。

要测试这一点，请创建一个名为 `testWidget.php` 的文件，内容如下：

```php
<?php
require_once('class.Widget.php');

try {
  $objWidget = new Widget(1);
  print "Widget Name: " . $objWidget->getName() . "<br>\n";
  print "Widget Description: " . $objWidget->getDescription() . "<br>\n";
  $objWidget->setName('Bar');
  $objWidget->setDescription('This is a bartacular widget!');
} catch (Exception $e) {
  die("There was a problem: " . $e->getMessage());
}
?>
```

在 Web 浏览器中访问此文件。第一次运行时，输出应类似于以下内容：

```
Widget Name: Foo
Widget Description: This is a footacular widget!
```

任何后续调用应显示如下：

```
Widget Name: Bar
Widget Description: This is a bartacular widget!
```

看看这种技术有多么强大。您可以从数据库中获取一个对象，更改该对象的属性，并且只需在 testWidget.php 中几行代码即可自动将更改的信息写回数据库。如果没有任何更改，则无需返回数据库，因此可以减轻数据库服务器的负载并提高应用程序的性能。

对象的使用者不一定需要了解其内部工作原理。如果软件开发团队的高级成员编写了 Widget 类，他或她可以将此对象交给初级成员（也许对 SQL 了解不多），团队的初级成员可以在不知数据来源或如何保存更改的情况下使用此对象。事实上，您可以将数据源从 PostgreSQL 数据库更改为 MySQL 数据库甚至 XML 文件，而初级团队成员无需知晓，也不必触碰任何使用此类的代码。

## 继承

如果您要创建一个应用程序来处理汽车经销商的库存，您可能需要 Sedan、PickupTruck 和 MiniVan 等类，这些类对应经销商库存中的同类汽车。您的应用程序不仅需要显示库存中有多少此类物品，还需要报告这些车辆的特性，以便销售人员可以将信息提供给客户。

# 第一部分：专业开发基础

轿车是四门汽车，您可能需要记录后排空间和后备箱容量。皮卡没有后备箱，但有一定容量的货厢，卡车本身具有拖曳能力（可以安全携带的货物最大重量）。对于小货车，您可能需要列出滑动门的数量（一扇或两扇）以及车内座位数。

然而，这些车辆实际上只是不同类型的汽车，因此在您的应用程序中会共享许多特性（例如颜色、制造商、型号、年份、车辆识别号等）。为确保每个类都具有这些相同属性，您可以将创建这些属性的代码复制到包含类定义的每个文件中。如前所述，面向对象编程方法的优势之一是代码复用。因此，您不需要复制代码，而是可以通过一种称为继承的过程来重用这些类的属性和方法。继承是一个类能够承担父类的方法和属性的能力。

继承使您能够定义一个基类，在此示例中为 Automobile。您可以说其他类也是 Automobile 的一种，因此拥有所有 Automobile 都具有的相同属性和方法。因为 Sedan 是一种 Automobile，所以它会自动继承 Automobile 类定义的所有内容，而无需您复制任何代码。这样，您只需编写 Sedan 类中不与所有汽车共享的附加属性和方法。换句话说，您需要完成的工作仅剩下定义差异；类之间的相似之处则从基类继承而来。

代码复用是一项好处，但使用继承的第二大优势还在于此。假设您有一个名为 Customer 的类，带有 buyAutomobile 方法。该方法将接受一个参数，即 Automobile 类的一个对象，其内部操作将打印记录销售所需的文件，并从库存系统中减少相关汽车。因为所有 Sedan、PickupTruck 和 MiniVan 都是 Automobile，您可以将这些类的对象传递给期望 Automobile 的函数。由于这三种特定类型都从更通用的父类继承，您知道它们都将具有相同的基础属性和方法集。只要您只需要所有 Automobile 共有的方法和属性，就可以接受任何继承自 Automobile 的类的对象。

请以猫为例。所有猫共享某些属性。它们吃、睡、呼噜呼噜和捕猎。它们还具有共享属性——体重、毛色、胡须长度和奔跑速度。然而，狮子有一定长度的鬃毛（至少雄狮有），并且会咆哮。猎豹有斑点。家猫既没有鬃毛也没有斑点，然而这三种动物都是猫。

在 PHP 中，您通过使用 extends 关键字来指定一个类是另一个类的子集，这告诉 PHP 您正在声明的类应继承其父类的所有属性和方法，并且您正在为该类添加功能或提供一些额外的专业化。

如果您必须设计一个处理动物园动物的应用程序，您可能需要 Cat、Lion 和 Cheetah 类。在编写任何代码之前，请使用统一建模语言（UML）图规划您的类层次结构，以便在编写代码和类文档时有据可依。（UML 在第 2 章中会更详细地讨论，因此如果您不完全理解此处显示的内容，请勿担心。）您的类图应指示一个父类 Cat，带有从中继承的 Lion 和 Cheetah 子类。图 1-1 显示了该图。





![](img/a1b732997d9cb194dceec0570dc79710_30_0.png)

## 图 1-1：猫类的类图

Lion 类和 Cheetah 类都继承自 Cat 类，但 Lion 类还包含属性 maneLength 和方法 roar()，而 Cheetah 类则添加了属性 numberOfSpots。

Cat 类（即 class.Cat.php）应按如下实现：

```php
<?php

class Cat {
    public $weight;    //in kg
    public $furColor;
    public $whiskerLength;
    public $maxSpeed;   //in km/hr

    public function eat() {
        //code for eating...
    }

    public function sleep() {
        //code for sleeping...
    }

    public function hunt(Prey $objPrey) {
        //code for hunting objects of type Prey
        //which we will not define...
    }

    public function purr() {
        print "purrrrrr..." . "\\n";
    }
}
?>
```

这个简单的类设置了所有猫共有的属性和方法。若要创建 Lion 和 Cheetah 类，你可以将 Cat 类的所有代码复制到名为 Lion 和 Cheetah 的类中。但这会带来两个问题。

- 首先，如果你在 Cat 类中发现了一个 bug，你必须记得也在 Lion 和 Cheetah 类中修复它。这会给你带来更多工作，而不是减少工作（而减少工作本应是面向对象方法的主要优势之一）。
- 其次，假设你有一个其他类（可能是 CatLover）的方法，其样子如下：

```
public function petTheKitty(Cat $objCat) {
    $objCat->purr();
}
```

虽然抚摸狮子或猎豹可能并不十分安全，但如果它们让你靠近到足以抚摸，它们也会发出咕噜声。你应该能够将 Lion 类或 Cheetah 类的对象传递给 petTheKitty() 函数。

因此，你必须采用另一种方法来创建 Lion 和 Cheetah 类，即使用继承。通过使用 extends 关键字并指定被扩展的类名，你可以轻松创建两个新类，它们具有普通猫的所有相同属性，但提供一些额外功能。请参考此示例，你可以将其输入到 class.Lion.php 中：

```php
<?php
require_once('class.Cat.php');

class Lion extends Cat {
    public $maneLength; //in cm

    public function roar() {
        print "Roarrrrrrrr!";
    }
}

?>
```

好了！Lion 类扩展 Cat 类后，你现在可以执行类似以下的操作：

```php
<?php
include('class.Lion.php');

$objLion = new Lion();
$objLion->weight = 200; //kg = 450 lbs.
$objLion->furColor = 'brown';
$objLion->maneLength = 36; //cm = 14 inches
$objLion->eat();
$objLion->roar();
$objLion->sleep();

?>
```

如所示，你可以调用父类 Cat 的属性和方法，而无需重写所有那些代码。请记住，extends 关键字告诉 PHP 自动包含 Cat 的所有功能，以及任何 Lion 特有的属性或方法。它还告诉 PHP，Lion 对象也是一个 Cat 对象，因此你现在可以使用 Lion 类的对象调用 petTheKitty() 函数，尽管该函数的声明将 Cat 用作参数提示：

```php
<?php
    include('class.Lion.php');

    $objLion = new Lion();
    $objPetter = new CatLover();
    $objPetter->petTheKitty($objLion);
?>
```

这样一来，你对 Cat 类所做的任何更改都会自动被 Lion 类继承。Bug 修复、对函数内部的更改，以及新方法和属性，都会传递给父类的子类。在一个大型、设计良好的对象层次结构中，这可以使 Bug 修复和增强功能的添加变得非常容易。对一个父类的微小更改可能对整个应用程序产生重大影响。

在下一个示例中，你将看到如何使用自定义构造函数来扩展和特化类。创建一个名为 class.Cheetah.php 的新文件，并输入以下内容：

```php
<?php
require_once('class.Cat.php');

class Cheetah extends Cat {
    public $numberOfSpots;

    public function __construct() {
        $this->maxSpeed = 100;
    }
}
?>
```

将以下代码输入到 testcats.php 中：

```php
<?php
require_once('class.Cheetah.php');

function petTheKitty(Cat $objCat) {
    if($objCat->maxSpeed < 5) {
        $objCat->purr();
    }
    else {
        print "Can't pet the kitty - it's moving at " .
            $objCat->maxSpeed . " kilometers per hour!";
    }
}

$objCheetah = new Cheetah();
petTheKitty($objCheetah);

$objCat = new Cat();
petTheKitty($objCat);
?>
```

Cheetah 类添加了一个名为 numberOfSpots 的新公共成员变量，以及父类 Cat 中不存在的构造函数。现在，当你创建一个新的 Cheetah 时，maxSpeed 属性（从 Cat 继承）将初始化为每小时 100 公里（约 60 英里），这是猎豹在短距离内的近似最大速度。请注意，由于未指定 Cat 类的默认值，在 petTheKitty() 函数中 maxSpeed 计算结果为 0（实际上是 null）。就像养过家猫的人都知道的那样，它们花在睡觉上的时间意味着它们的最大速度可能接近 0！

通过添加新函数、属性，甚至构造函数和析构函数，父类的子类可以轻松扩展其功能，并以最少的代码向你的应用程序添加新功能和能力。

> 当你可以说一个类是另一个类的特殊类型时，请使用继承来最大化代码复用的潜力，并提高应用程序的灵活性。

### 重写方法

仅因为子类继承自父类，并不意味着子类必然需要使用父类的函数实现。例如，如果你正在设计一个需要计算不同几何图形面积的应用程序，你可能会有名为 Rectangle 和 Triangle 的类。这两种图形都是多边形，因此这些类将继承自名为 Polygon 的父类。

Polygon 类将具有一个名为 numberOfSides 的属性和一个名为 getArea 的方法。所有多边形都有可计算的面积；然而，计算该面积的方法对于不同类型的多边形可能不同。（存在任何多边形面积的通用方程，但它通常不如此处使用的简单多边形的特定形状方程高效。）矩形面积的公式是 w * h，其中 w 是矩形的宽度，h 是高度。三角形面积计算为 0.5 * h * b，其中 h 是底边为 b 的三角形的高度。图 1-2 显示了两种多边形的面积。

![](img/a1b732997d9cb194dceec0570dc79710_33_0.png)

图 1-2：两个多边形的面积

对于你创建的每个 Polygon 子类，你可能希望用特定于多边形类类型的方程来替换面积方法的默认实现。通过为该类重新定义该方法，你可以提供自己的实现。

# 第 1 章：面向对象编程简介

对于 `Rectangle` 类，你将创建两个新属性 `height` 和 `width`，并重写 `Polygon` 类对 `getArea()` 方法的实现。对于 `Triangle` 类，你可能会添加属性来存储三个角度、高度和底边段长度的信息，并重写 `getArea()` 方法。通过使用继承和重写父类的方法，你可以允许子类对这些方法的实现进行专门化。

接受 `Polygon` 作为参数并需要打印该多边形面积的函数，将自动调用传递给它的 `Polygon` 子类（即 `Rectangle` 或 `Triangle`）的 `getArea()` 方法。面向对象语言在运行时自动确定调用哪个 `getArea()` 方法的能力被称为多态性。多态性是应用程序根据其作用的特定对象执行不同操作的能力。在这种情况下，这意味着调用不同的 `getArea()` 方法。

> 当父类的实现与子类所需的实现不同时，请在子类中重写方法。这允许你对该子类的活动进行专门化。

有时，你希望保留父类提供的实现，但也要在子类的方法中执行一些额外活动。例如，如果你有一个管理非营利组织的应用程序，你可能会有一个名为 `Volunteer` 的类，它具有一个名为 `signUp()` 的方法；该方法将使志愿者能够报名参加社区服务项目，并将用户添加到该活动的志愿者列表中。

不过，你可能会有一些有限制的用户（例如有犯罪背景），这应阻止他们报名参加某些项目。在这种情况下，多态性使你能够创建一个名为 `RestrictedUser` 的类，其中包含重写的 `signUp()` 方法，该方法首先检查用户账户上的限制与项目属性是否冲突，如果限制不允许用户参与某项特定活动，则阻止用户报名。如果限制不禁止他们参与，那么你应该调用父类的操作以完成他们的注册。

当你重写父类的方法时，不一定需要完全重写该方法。你可以继续使用父类提供的实现，但为子类添加额外的专门化。这样，你既可以复用代码，又可以根据业务规则提供所需的定制。

一个类继承另一个类的方法和属性的能力是面向对象系统最引人注目的特性之一，它使你能够在应用程序中获得极高的效率和灵活性。

在下一个示例中，你将创建两个类 — `Rectangle` 和 `Square`。正方形是一种特殊的矩形。你能用矩形做的任何事情，都可以用正方形做；然而，由于矩形有两个不同的边长，而正方形只有一个，因此你需要以不同的方式处理某些事情。





创建名为 class.Rectangle.php 的文件并添加以下代码：

```php
<?php
class Rectangle {
public $height;
public $width;

public function __construct($width, $height) {
$this->width = $width;
$this->height = $height;
}

public function getArea() {
return $this->height * $this->width;
}
}
?>
```

这是一个用于建模矩形的类的相当直接的实现。构造函数接受宽度和高度参数，面积函数通过将两者相乘来计算矩形的面积。

现在，请看这里显示的 class.Square.php：

```php
<?php
require_once('class.Rectangle.php');

class Square extends Rectangle {
public function __construct($size) {
$this->height = $size;
$this->width = $size;
}

public function getArea() {
return pow($this->height, 2);
}
}
?>
```

此代码同时重写了构造函数和 getArea() 方法。要使矩形成为正方形，所有四边长度必须相同。因此，构造函数只需要一个参数。如果向函数传递多个参数，则第一个参数之后的任何值都会被忽略。

> 如果向用户定义的函数传递的参数数量多于函数声明中设置的参数数量，PHP 不会引发错误。在少数情况下，这实际上是所需的行为。如果要了解更多信息，请参阅内置 func_get_args() 函数的 PHP 文档。

getArea() 函数也被重写了。Rectangle 类中的实现对于 Square 对象也会返回完全正确的结果。重写该方法是为了提高应用程序性能（尽管在此情况下，性能收益微乎其微）。对于 PHP 来说，获取一个属性并计算其平方比获取两个属性并将它们相乘更快。

通过重写构造函数、析构函数和方法，可以更改子类运行的某些方面。

### 保留父类的功能

有时，您希望保留父类提供的功能。您不需要完全重写函数；只需向其中添加一些内容即可。您可以将父方法中的所有代码复制到子类的方法中，但如前面所述，OOP 提供了比仅仅复制代码行更好的方法来做到这一点。

要调用父类提供的功能，请使用语法 `parent::[function name]`。当您只想向方法添加其他行为时，首先调用 `parent::[function name]`，然后添加您的其他代码。以这种方式扩展函数时，始终在做其他任何事情之前先调用父类上的方法。这样做可确保对父类操作的任何更改都不会破坏您的代码。

> > 由于父类可能期望对象处于某个状态，或者可能更改对象的状态、覆盖属性值或操作对象的内部数据，因此在扩展继承的方法时，始终在添加您自己的代码之前先调用父类方法。

以下示例包含两个类：`Customer` 和 `SweepstakesCustomer`。一家超市有一个应用程序，在运行某些促销活动时，会不时切换收银机应用程序中使用的类。每位进店的顾客都有自己的 ID 值（来自数据库）以及一个客户编号（表示在他或她之前有多少位顾客来过超市）。对于这些抽奖活动，第一百万位顾客将赢得奖品。

创建名为 `class.Customer.php` 的文件并添加以下代码：

```php
<?php

class Customer {
public $id;
public $customerNumber;
public $name;

public function __construct($customerID) {
//fetch customer information from the database
//
//We're hard coding these values here, but in a real application
//these values would come from a database
$data = array();
$data['customerNumber'] = 1000000;
$data['name'] = 'Jane Johnson';

//Assign the values from the database to this object
$this->id = $customerID;
$this->name = $data['name'];
$this->customerNumber = $data['customerNumber'];
}
}
?>
```

现在创建一个名为 class.SweepstakesCustomer.php 的文件并输入此代码：

```php
<?php
require_once('class.Customer.php');

class SweepstakesCustomer extends Customer {
    public function __construct($customerID) {
        parent::__construct($customerID);

        if($this->customerNumber == 1000000) {
            print "Congratulations $this->name! You're our " .
            "millionth customer!" .
            "You win a year's supply of frozen fish sticks!";
        }
    }
}
?>
```

### 继承的工作原理

Customer 类根据客户 ID 从数据库初始化值。您很可能会从忠诚度计划刷卡中检索客户 ID，此类刷卡在大型连锁杂货店中很常见。有了客户 ID，您可以从数据库中获取客户的个人数据（此示例中只是硬编码），以及一个表示在该客户之前有多少顾客进入商店的整数值。将所有这些信息存储在公共成员变量中。

SweepstakesCustomer 类为构造函数添加了一些额外功能。您首先通过调用 parent::__construct 并传递它期望的参数来调用父类的构造函数功能。然后查看 customerNumber 属性。如果该数字是第一百万，则告知该客户他或她已赢得奖品。

要了解如何使用此类，请创建一个名为 testCustomer.php 的文件并输入以下代码：

```php
<?php
require_once('class.SweepstakesCustomer.php');
//since this file already includes class.Customer.php, there's
//no need to pull that file in, as well.

function greetCustomer(Customer $objCust) {
    print "Welcome back to the store $objCust->name!";
}

//Change this value to change the class used to create this customer object
$promotionCurrentlyRunning = true;
if ($promotionCurrentlyRunning) {
$objCust = new SweepstakesCustomer(1000000);
} else {
$objCust = new Customer(1000000);
}
greetCustomer($objCust);
?>
```

在浏览器中运行 testCustomer.php，先将 $promotionCurrentlyRunning 变量设置为 false，然后设置为 true。当值为 true 时，将显示奖品消息。

## 接口

有时，您会有一组类，它们不一定通过继承关系相关。您可能拥有完全不同的类，只是碰巧共享一些共同行为。例如，罐子和门都可以打开和关闭，但除此之外毫无关系。无论什么样的罐子或门，都可以执行这些活动，但它们之间没有其他共同点。

### 接口的作用

在 OOP 中也能看到同一概念。接口使您能够指定对象能够执行某个功能，但不一定告诉您对象如何执行。接口是不相关对象之间执行共同功能的契约。实现此接口的对象向其用户保证，它能够执行接口规范定义的所有功能。自行车和足球是完全不同的东西，但体育用品店库存系统中表示这些物品的对象必须能够与该系统交互。

通过声明接口并在对象中实现它，您可以将完全不同的类交给共同函数。以下示例演示了相当平淡的门和罐子比喻。

创建名为 interface.Openable.php 的文件：

```php
<?php
interface Openable {
public function open();
public function close();
}
?>
```

就像您将类文件命名为 class.[class name].php 一样，您应该对接口使用相同的命名约定，并将它们命名为 interface.[interface name].php。

您使用与类类似的语法声明接口 Openable，只是将 class 关键字替换为 interface。接口没有成员变量，也不指定其任何成员函数的实现。





因为未指定任何实现，你将这些函数声明为 `abstract`。这样做会告诉 PHP，任何实现此接口的类都有责任提供函数的实现。如果你未能提供接口中 *所有* 抽象方法的实现，PHP 将引发运行时错误。你不能有选择地只实现其中一些抽象方法；你必须提供它们全部的实现。

### 接口的工作原理

`Openable` 接口是与应用程序其他部分的契约，规定任何实现此接口的类都将提供两个名为 `open()` 和 `close()` 的方法，且不接受参数。有了这一商定好的方法集，你可以允许非常不同的对象传入同一个函数，而无需它们之间存在继承关系。

创建以下文件，命名为 `class.Door.php`：

```php
<?php

require_once('interface.Openable.php');

class Door implements Openable {

    private $_locked = false;

    public function open() {
        if($this->_locked) {
            print "Can't open the door. It's locked.";
        } else {
            print "creak...<br>";
        }
    }

    public function close() {
        print "Slam!<br>";
    }

    public function lockDoor() {
        $this->_locked = true;
    }

    public function unlockDoor() {
        $this->_locked = false;
    }
}
?>
```

现在创建一个名为 `class.Jar.php` 的文件：

```php
<?php

require_once('interface.Openable.php');

class Jar implements Openable {
    private $contents;
    public function __construct($contents) {
        $this->contents = $contents;
    }

    public function open() {
     print "the jar is now open<br>";
    }

    public function close() {
     print "the jar is now closed<br>";
    }
}
?>
```

要使用这些文件，请在同一目录中创建一个名为 `testOpenable.php` 的新文件：

```php
<?php
 require_once('class.Door.php');
 require_once('class.Jar.php');

 function openSomething(Openable $obj) {
 $obj->open();
 }

 $objDoor = new Door();
 $objJar = new Jar("jelly");

 openSomething($objDoor);
 openSomething($objJar);
 ?>
```

由于 `Door` 类和 `Jar` 类都实现了 `Openable` 接口，你可以将两者都传递给 `openSomething()` 函数。由于该函数仅接受实现 `Openable` 接口的对象，你知道可以在其中调用 `open()` 和 `close()` 函数。但是，你不应尝试在 `openSomething()` 函数中访问 `Jar` 类的 `contents` 属性或使用 `Door` 类的 `lock()` 或 `unlock()` 函数，因为该属性和这些方法不属于接口。接口契约保证你拥有 `open()` 和 `close()`，而除此之外别无他物。

通过在应用程序中使用接口，你可以允许完全不同且无关的对象相互通信，并保证它们能够按照接口中规定的条款进行交互。接口是提供某些方法的契约。

# 封装

如前章所述，对象使你能够向对象的使用者隐藏其实现细节。你无需知道前面提到的 `Volunteer` 类是将信息存储在数据库、纯文本文件、XML 文档还是其他数据存储机制中，才能调用 `signUp()` 方法。同样，你也无需知道对象中关于志愿者的信息是实现为单个变量、数组甚至其他对象。

这种隐藏实现细节的能力被称为 *封装*。一般来说，封装指两个概念：保护类的内部数据免受该类外部代码的访问，以及隐藏实现细节。

*封装* 一词字面意思是放入胶囊或外部容器中。设计良好的类在其内部周围提供一个完整的外壳，并向类外部的代码呈现一个与这些内部细节完全分离的接口。这样一来，你将获得两个优势：

- 你可以随时更改实现细节，而不会影响使用你类的代码。
- 因为你知道，除非你知晓，否则类外部的任何东西都无法意外修改由你的类构建的对象的状态或属性值，所以你可以信任对象的状态及其属性值是有效且合理的。

类的成员变量及其函数具有可见性。*可见性* 指的是类外部的代码可以看到什么。如前章所述，*私有* 成员变量和函数对类外部的代码不可访问，并用于类的内部实现。*受保护* 成员变量和函数仅对类的子类可见。*公共* 成员变量和函数可供类内部或外部的任何代码使用。

一般来说，类的所有内部成员变量都应声明为私有。类外部的代码若需要访问这些变量，应通过访问器方法进行。你不会让一个想让你尝试新食物的人蒙住你的眼睛并强行喂食你；你需要能够检查该物品并决定是否允许它进入你的身体。同样，当对象希望允许类外部的代码更改属性或以其他方式影响其内部数据时，通过将对该数据的访问封装在一个公共函数中（并保持内部数据为私有），你就有机会验证这些更改并接受或拒绝它们。

例如，如果你正在为银行构建一个处理客户账户详细信息的应用程序，你可能会有一个名为 *账户* 的对象，其中包含名为 `totalBalance` 的属性以及名为 `makeDeposit()` 和 `makeWithdrawal()` 的方法。总余额属性应为只读。影响余额的唯一方法是进行取款或存款。如果 `totalBalance` 属性被实现为公共成员变量，你可以编写代码来增加该变量的值，而无需实际存款。这种方法显然对银行不利。

相反，你应该将此属性实现为私有成员变量，并提供一个名为 `getTotalBalance()` 的公共方法，该方法返回该私有成员变量的值。由于存储账户余额的变量是私有的，你无法直接操纵它；并且由于影响账户余额的唯一公共方法是 `makeWithdrawal()` 和 `makeDeposit()`，如果你想增加账户的值，就必须实际进行存款。

通过允许你隐藏实现细节并保护对内部成员变量的访问，面向对象软件开发方法为你提供了一个灵活、稳定的应用程序。

*封装内部数据和方法实现使面向对象软件系统能够保护和控制对数据的访问并隐藏实现细节。*

## PHP 6 中面向对象的变化

PHP 对对象的支持可以追溯到 PHP 3。最初从未打算支持类或对象的概念，但几乎作为事后添加的有限支持被加入，以便为关联数组提供“语法糖”（引用 Zeev Suraski 的话）。PHP 中的对象支持最初设计为一种方便地对数据和函数进行分组的方式，但仅包含了传统上与完整面向对象编程语言相关的功能的一个小子集。随着 PHP 流行度的提高，OO 方法在大型应用程序中变得越来越普遍。然而，糟糕的内部实现变得具有局限性。

最重要的是，不支持真正的封装。你无法指定成员变量或方法为私有或受保护。一切都是公共的——正如你所看到的，这可能会带来问题。

此外，不支持抽象接口或方法。无法将方法和成员变量声明为静态。没有析构函数。所有这些概念对任何具有其他 OOP 语言背景的人都很熟悉，PHP 对象模型中缺乏这些功能可能会使从 Java（支持所有这些理念）等语言过渡到 PHP 变得困难。对于有 PHP 4 经验的人，表 1-1 列出了 PHP 中的一些新功能。

### 表 1-1: 从 PHP 4 到 PHP 5 和 6 的对象模型演变

| 新特性 | 优势 |
| :--- | :--- |
| 私有、受保护的成员变量和方法 | PHP 中现在可以实现真正的封装和数据保护。 |
| 改进的解引用支持 | 诸如 `$obj->getSomething()->doSomething()` 之类的语句现在成为可能。 |
| 静态成员变量和方法 | 可以静态调用的方法现在清晰可辨。类级常数有助于控制全局命名空间的污染。 |
| 统一构造函数 | 所有类构造函数现在都称为 `__construct()`。这有助于封装重写的子类构造函数，并在多个类涉及继承树时更容易更改继承。 |
| 析构函数支持 | 通过 `__destruct()` 方法，PHP 中的类现在可以拥有析构函数。此功能允许在对象销毁时执行操作。 |
| 对抽象类和接口的支持 | 你可以在父类中定义必需的方法，同时将实现推迟到子类。抽象类不能实例化；只有其非抽象子类可以。 |
| 参数类型提示 | 你可以为期望对象的函数参数指定类。`function foo(Bar $objBar) { ...` 允许你确定参数的数据类型是你所期望的。 |





object model that appeared starting in PHP 5. For those already familiar with OOP in PHP 5, little has changed in version 6.

## 摘要

在本章中，你探索了面向对象编程（OOP）的概念。类被展示为创建对象的蓝图。对象是从类定义中创建的运行时数据和函数的捆绑。它们具有称为_属性_的特征和称为_方法_的行为。属性可以被视为变量，方法可以被视为函数。

有些类共享一个共同的父类型。例如，正方形（子类）是矩形（父类）的一种。当你声明一个类是父类的子类型时，它会继承父类的方法和属性。你可以选择重写继承的方法。如果你选择，可以完全重新实现该方法，或者继续使用父类的实现，但也添加特定于子类的专用化（或者根本不重写该方法）。

封装是OOP的一个重要概念。它指的是类保护对其内部成员变量的访问，并保护该类的用户免受其实现细节影响的能力。成员方法和属性有三个可见性级别：私有、受保护和公有。私有成员只能由类的内部操作使用。受保护的成员对子类可见。公有成员可以由类外部的代码使用。

PHP 5和Zend Engine 2的引入使PHP中的面向对象（OO）支持经历了重大改进。自PHP 5版本以来的新功能和显著性能改进，并在PHP 6中进一步增强，使PHP成为一门真正的面向对象语言。

第2章讨论了统一建模语言（UML），这是一种用于绘制OO软件架构的系统，将为你提供描述和规划甚至最复杂应用程序架构的工具。

## 统一建模语言（UML）

如果你是小型项目中唯一的程序员，在纸上画一个小草图或者将设计完全留在脑海中通常就足够了。一个独自编程的程序员通常可以这样毫无问题地完成项目。

然而，假设你接手了一个需要两个开发人员的较大项目。你负责设计系统，第二个开发人员在那里帮助你编写代码。你如何将该系统的设计传达给另一个人？你可以用文字描述需要哪些类，并提供系统如何为最终用户和内部运行的描述。过一段时间，你可能会最终得到大量描述系统的文本。如果你想象一个更大的项目，你会很快意识到纯粹用文字描述一个大型软件系统是不切实际的；如果你创建了自己设计的图表，那么你还会有额外的任务，即向团队的其他成员解释你的符号系统。

统一建模语言（UML）的设计就是为了解决这个问题。UML主要是一种标准图表语言，每种图表都适合描述软件设计的特定领域。UML让每个人都以相同的方式“谈论”系统，并提供了一种可视化系统的强大方法。

在本章中，你将通过设计和开发一个名为BandSpy的假设性乐队跟踪系统。在此过程中，你将了解UML图表及其在流程中的位置。

### 需求收集

以下是本章的假设情景。一家唱片公司的客户联系了你，要求开发一个基于Web的系统来跟踪该客户代表的乐队。在一次初步电话交谈中，客户解释说，BandSpy应使Web用户能够查看公司代表的不同乐队的详细信息，并了解即将举行的音乐会。唱片公司的某人应该能够向系统添加新乐队、编辑现有乐队信息，并为乐队预订新的音乐会演出。尽管你与客户的交谈是非正式的，但它开启了软件设计的一个关键部分：需求收集阶段。在此阶段，你需要确定软件到底需要做什么才能满足其用户。

### 采访客户

在电话上，你与客户约定见面。经过一段时间的相互了解后，会议深入讨论了系统。与会者是Bill（公司老板）、Jane（运营经理）和Tom（公司的“电脑专家”）。

在最初的采访中，了解相关人员的角色非常重要。你可以推断出，与会者对软件的工作原理有一定兴趣。然而，这种兴趣不一定总是对项目的结果有益。

在需求收集期间需要识别的关键人员是对领域（即软件将要建模的领域）有详细了解的人。这可能包括以前手动做现在软件将自动化处理的事情的人，也可能是了解业务运作方式以及软件必须做什么才能正确建模的人。此人通常被称为领域专家。

在采访过程中，Jane说了大部分话。她描述了他们希望系统能实现什么，以及公司目前如何处理这一过程。很可能Jane是你的领域专家。在后续采访中，直接与她交谈将很有用。Bill大部分时间保持沉默；他可能有其他事情要处理。Tom提到他将是实际将数据输入系统的人。你注意到你可能需要花一点时间向他解释管理工具的使用。

在会议过程中，你记下了Jane所说的系统必须做的事情，并得出了以下列表：

- [ ] 用户可以访问BandSpy网站并浏览乐队信息。乐队信息包括乐队类型、乐队中的音乐家以及他们演奏的乐器。
- [ ] 用户可以查看即将举行的演出信息，这些演出可能包括一个或多个乐队。
- [ ] 网站管理员可以添加关于乐队的新信息。
- [ ] 网站管理员可以编辑现有乐队信息。
- [ ] 网站管理员可以添加新演出。添加新演出包括预订场地和生成门票。场地预订和门票均由独立的第三方公司处理。这些公司拥有你需要通过BandSpy软件通知的预订系统。

既然你有了需求列表，是时候开始使用UML图表了。

### 用例图

用例图从用户的任务导向视角展示系统。一个用例代表用户试图使用系统完成的任务。图2-1显示了一个非常简单的用例图，用于用户访问BandSpy网站并浏览乐队信息。

![](img/a1b732997d9cb194dceec0570dc79710_46_0.png)

棒人图形称为参与者，气泡称为用例。线条表示该参与者可以执行关联的用例。在用例图中，参与者通常是与人相关的角色，尽管它可以代表作用于你系统的外部系统。

请注意，用例“浏览乐队信息”比较笼统。这里不需要高度详细。你只需要能够涵盖系统应能处理的所有用例。如果需要，用例可以分解为各自的场景。场景是构成用例的一系列步骤。例如，前一个用例的场景如下：

- 1. 用户访问BandSpy网站。
- 2. 用户使用菜单导航网站。
- 3. 用户查看乐队/音乐家/音乐会信息。

图2-2显示了管理任务的用例图。

![](img/a1b732997d9cb194dceec0570dc79710_46_1.png)





行政用例是管理员在使用 BandSpy 系统时可能尝试的独立任务。客户提到，他希望网站的管理部分需要密码保护的登录。因为登录系统可以被视为一项任务本身，你可以使用包含关系来显示此用例是另外三个用例的一部分。图 2-3 显示了包含关系的使用，由虚线表示。

![](img/a1b732997d9cb194dceec0570dc79710_47_0.png)

图 2-3：用例图中指示包含关系

用例图中可能出现多个角色。通常，不同的角色可能共享一个用例。图 2-4 显示了 BandSpy 系统的完整用例图。因为管理员和普通用户都可以查询乐队信息，因此他们共享该用例。此外，该用例显示非人角色（场地预订系统）正在执行更新即将演出信息的任务。

![](img/a1b732997d9cb194dceec0570dc79710_48_0.png)

图 2-4：显示多个角色共享一个常见任务

## 类图

虽然用例图提供了一种有用的方式来表达系统对各种角色将具备的功能，但它们对解释软件的内部工作原理帮助不大。此时，你可以开始使用其他 UML 图表，以及你对对象的知识，来更详细地定义这些内部工作原理。

## 对领域建模

在与客户的访谈完成，且用例已最终确定后，你可以继续进行设计软件以对领域建模的过程。这意味着的一件事是开发系统，使其类紧密模仿现实中所代表的事物。例如，在此示例应用程序中，用户可以查看不同类型音乐家的信息，因此最好有一个 `Musician` 类，或者更好的做法是，有一个 `Musician` 接口，所有不同类型的音乐家都可以实现它。

类图可能是最重要的图表，用于使用和理解。它们在细节和灵活性之间取得了良好的平衡。它们提供了你所建模领域的描述，并允许关于类的精确方法和属性的细节程度各异——从非常高层次到非常具体。此外，它们对于描述有趣的面向对象（OO）概念（例如设计模式）也很有用，这些内容将在第 4 章中介绍。

图 2-5 显示了类图的基础知识。矩形中的顶部框显示类的名称。中间框显示其 *属性*，底部框显示其 *操作*。在 PHP 中，“属性”和“操作”这两个术语分别转换为 `Musician` 类中的成员变量和方法。

![](img/a1b732997d9cb194dceec0570dc79710_49_0.png)

图 2-5：类图

属性类型在冒号后指示。在这个简单示例中，所有属性类型都是字符串。减号（–）表示属性是类的私有成员。操作前面的加号（+）表示它们是公共的。如果操作返回值，其类型显示在冒号后。同样，在这个示例中，它们都是字符串。

以下是类图中显示的 `Musician` 的 PHP 代码。将其键入名为 `class.Musician.php` 的文件中：

```
class Musician {
private $last;
private $first;
private $bandName;
private $type;
function __construct($last, $first, $musicianType) {
$this->last = $last;
$this->first = $first;
$this->type = $musicianType;
}
public function getName() {
echo $this->first . $this->last;
}
public function getBand() {
echo $this->bandName;
}
public function getMusicianType() {
echo $this->type;
}
public function setName($first, $last) {
$this->first = $first;
$this->last = $last;

}

public function setBand($bandName) {
  $this->bandName = $bandName;
}
public function setMusicianType($musicianType) {
  $this->type = $musicianType;
}
}
```

## 关系

如果你的应用程序只有一个类，绘制图表可能帮助不大。因为 BandSpy 系统需要不止一个类，你必须考虑对象之间将如何相互作用。在之前的示例中，字符串被用作所有成员变量的数据类型。通常，这不是个好主意。如果音乐家是乐队的一部分，那么你可能不仅想要乐队的名称，这是合理的。例如，你可能想要乐队的其他成员、他们演奏的音乐类型等等。这种思考方式将指导你在软件设计阶段。某些成员变量需要更高的复杂度，因此必须拆分为它们自己的类。

### 关联

如果你查看图 2-6，可以看到 bandName 属性已移动到 Band 类的属性中。此外，请注意，此图并未显示类中的每个属性和方法。

![](img/a1b732997d9cb194dceec0570dc79710_50_0.png)

图 2-6：关联 Musician 类和 Band 类

使用类图时，只需显示在图表上下文中重要的内容。私有成员变量的简单访问器方法被假定存在，因此被省略。当类图不完整时，可以使用省略号 (...) 来显示某些信息是故意省略的。

连接两个类的线是一种称为关联的关系。在这个示例中，关联是一对多——一个 Band 可能拥有多个 Musicians，或者反过来，多个 Musicians 可以在一个 Band 中，这由关联下方的 * 和 1 表示。

关联线还可以显示可导航性。在这个示例中，没有任何箭头的线表明可以双向移动，也称为双向可导航性。换句话说，每个类都对另一个类持有内部引用。如果关联仅允许单向导航，则称为单向可导航性。图 2-7 显示了 Musician 类和 Instrument 类之间的关系。Musician 类可以访问其内部集合中的任何 Instruments，但 Instrument 不知道哪个 Musician 拥有它。

![](img/a1b732997d9cb194dceec0570dc79710_51_0.png)

### 实现和泛化

如前所述，创建一个所有其他音乐家类型类都可以实现的 Musician 接口是一个更好的主意。这样，你可以派生出其他类（例如 Guitarist 和 Drummer），这些类遵循 Musician 在系统中的行为规则。只要遵循 Musician 接口的契约，你就可以确信你的派生类将正确协同工作。

当你想要指示接口以及实现它的类时，你会在它们之间显示一种称为实现的关系。虚线表示实现，末端有一个指向接口的空心箭头。UML 图中的接口与标准类图类似，但显示时在接口名称上方使用带双书名号的单词 interface。图 2-8 显示了两个类，Drummer 和 Guitarist，实现了 Musician 接口。

![](img/a1b732997d9cb194dceec0570dc79710_51_1.png)

当你想要指示来自抽象类或另一个具体类的继承时，可以使用泛化。泛化与实现相同，只是线不是虚线。图 2-8 还显示了将 Guitarist 子类化以创建 RockGuitarist 和 ClassicalGuitarist 类的过程。

### 组合

通常，类的有用关系并非基于关联或继承，而是基于类的分组方式。考虑鼓组的示例。在此示例应用程序中，Instrument 接口在 Guitar 或 Piano 等具体类中实现，如图 2-9 所示。此外，DrumSet、Drum 和 Cymbal 类也实现了它。带有黑色菱形的线条的新表示法指示 DrumSet 是 Drum 和 Cymbal 类的组合。DrumSet 的一个实例将包含 Drum 和 Cymbal 类的实例。





![](img/a1b732997d9cb194dceec0570dc79710_52_0.png)

图 2-9: 表示合成

合成是一种受两条规则约束的严格关系。首先，合成的部分不能在其他地方共享。换句话说，属于 `DrumSet` 实例的 `Drum` 实例不能属于任何其他 `DrumSet`。第二条规则是，当删除 `DrumSet` 实例时，其合成部分也应被删除。

合成的一种更通用的类型称为 *聚合*。聚合的表示法与合成相同，只不过菱形是空心的。聚合允许共享其他类的实例，因此在删除自身时不需要删除这些实例。

## 实现

现在你已经了解了类图的基础知识，请查看基于刚才介绍的一些概念的示例代码。将所有这些代码保存到名为 `test_music.php` 的单个文件中：

```php
<?php
interface Band {
    public function getName();
    public function getGenre();
    public function addMusician(Musician $musician);
    public function getMusicians();
}

interface Musician {
    public function addInstrument(Instrument $instrument);
    public function getInstruments();
    public function assignToBand(Band $band);
    public function getMusicianType();
}

interface Instrument {
    public function getName();
    public function getCategory();
}

class Guitarist implements Musician {
    private $last;
    private $first;
    private $musicianType;
    private $instruments;
    private $bandReference;

    function __construct($first, $last) {
        $this->last = $last;
        $this->first = $first;
        $this->instruments = array();
        $this->musicianType = "guitarist";
    }

    public function getName() {
        return $this->first . " " . $this->last;
    }

    public function addInstrument(Instrument $instrument) {
        array_push($this->instruments, $instrument);
    }

    public function getInstruments() {
        return $this->instruments;
    }

    public function getBand() {
        return $this->bandReference;
    }

    public function assignToBand(Band $band) {
        $this->bandReference = $band;
    }

    public function getMusicianType() {
        return $this->musicianType;
    }

    public function setMusicianType($musicianType) {
        $this->musicianType = $musicianType;
    }
}

class LeadGuitarist extends Guitarist {
    function __construct($last, $first) {
        parent::__construct($last, $first);
        $this->setMusicianType("lead guitarist");
    }
}

class RockBand implements Band {
    private $bandName;
    private $bandGenre;
    private $musicians;

    function __construct($bandName) {
        $this->bandName = $bandName;
        $this->musicians = array();
        $this->bandGenre = "rock";
    }

    public function getName() {
        return $this->bandName;
    }

    public function getGenre() {
        return $this->bandGenre;
    }

    public function addMusician(Musician $musician) {
        array_push($this->musicians, $musician);
        $musician->assignToBand($this);
    }

    public function getMusicians() {
        return $this->musicians;
    }
}

class Guitar implements Instrument {

    private $name;
    private $category;

    function __construct($name) {
        $this->name = $name;
        $this->category = "guitar";
    }

    public function getName() {
        return $this->name;
    }

    public function getCategory() {
        return $this->category;
    }
}

// Test Objects
$band = new RockBand("The Variables");
$bandMemberA = new Guitarist("Jack", "Float");
$bandMemberB = new LeadGuitarist("Jim", "Integer");

$bandMemberA->addInstrument(new Guitar("Gibson Les Paul"));
$bandMemberB->addInstrument(new Guitar("Fender Stratocaster"));
$bandMemberB->addInstrument(new Guitar("Hondo H-77"));

$band->addMusician($bandMemberA);
$band->addMusician($bandMemberB);

foreach($band->getMusicians() as $musician) {
    echo "Musician ".$musician->getName()."<br>";
    echo "is the ".$musician->getMusicianType()."<br>";
    echo "in the ".$musician->getBand()->getGenre()." band <br>";
    echo "called ".$musician->getBand()->getName()."<br>";

    foreach($musician->getInstruments() as $instrument) {
        echo "And plays the ".$instrument->getName()."";
        echo $instrument->getCategory()."<br>";
    }
    echo "<p>";
}
?>
```

虽然这个示例很简单，但它说明了面向对象编程（OOP）的一个重要方面。请注意，在最后测试对象时没有出现条件分支。在调用其方法之前，你不需要知道自己正在处理哪种类型的 Musician 或 Instrument。由于遵循了接口规则，你可以相信这些对象都会针对其实现作出恰当且唯一的响应。如前所述，这被称为多态。任何时候，如果需要添加另一种类型的 Musician，你可以直接编写新类，在标准 Musician 接口背后定义其行为。

## 活动图

简在之前的会议中提到，BandSpy 应用程序在添加新演出时需要与另外两个第三方系统对接——票务系统和场地预订系统。为了了解完成此任务所需的事件顺序，你可以绘制活动图。当你需要了解用例中正在进行的活动流程时，活动图非常有用。在此示例中，用例是 BandSpy 管理员预订演出。

与简的进一步交谈表明，BandSpy 系统不仅需要向场地预订系统发送消息，还需要从两个系统接收返回信息。场地系统将发送确认场地可用的消息，而票务系统将传输票务信息（例如定价）。如果管理员尝试预订不可用日期或时间的场地，场地系统会向 BandSpy 指明此事实。管理员将收到通知，并可以尝试预订其他日期。

图 2-10 显示了此处描述过程的活动图。活动图始于一个名为起始点的实心黑色圆圈。从该点开始，流程遵循箭头（称为转换）进入表示活动的圆角矩形。

![](img/a1b732997d9cb194dceec0570dc79710_56_0.png)

图 2-10: 活动图

黑色空心菱形表示 *决策点*。顾名思义，基于某个决策或条件，转换流程会拆分。在图中，决策是场地在请求日期是否可用。

决策之后，名为 *分支* 的大型黑色条将流程拆分到两个不同的活动。在场地系统中，会生成确认并发送回 BandSpy 系统，同时启动票务系统为活动生成票据。来自票务系统和场地系统的信息都会发送回 BandSpy，并在另一个名为 *合并* 的黑色条处汇合。合并表示两个外部系统的消息都必须到达合并点，活动图才能进入最后一步：存储和更新有关新演出的信息。

划分各系统特定活动的三个大矩形称为 *泳道*。虽然泳道不是强制性的，但在涉及多个系统时，它们通常有助于澄清图表。

## 序列图

你可能已经注意到，BandSpy 应用程序有一个类层次结构。*Band* 类包含 *Musicians*，而 *Musicians* 拥有 *Instruments*，这些 *Instruments* 可能是其他 *Instruments* 的合成。在使用应用程序期间，消息通过对象关系传递。你可以将方法调用视为一种消息，即一个对象可能会对另一个对象进行调用。例如，如果 *Band* 的实例需要知道其 *Musicians* 正在演奏哪些 *Instruments*，它会向其所有 *Musicians* 发送调用 *getInstruments()* 的消息。换句话说，*Band* 正在其所有 *Musicians* 上调用 *getInstruments()* 方法。

可视化消息在不同对象之间如何移动很有用，UML 提供了另一种专门表示这种移动的图表：*序列图*。

序列图通常可以与单个用例相关联。之前关于用例的讨论中包含一个名为“浏览乐队信息”的一般用例。为了说明序列图，你可以将“浏览乐队信息”用例细分为更具体的用例。图 2-11 显示了“用户”角色的一些更具体的用例。

![](img/a1b732997d9cb194dceec0570dc79710_57_0.png)

图 2-11: 针对用户的更具体的用例




对于“按乐队查找乐器”用例，序列图应显示参与的所有对象以及它们之间传递的消息以完成任务。图 2-12 显示了序列图。

![](img/a1b732997d9cb194dceec0570dc79710_58_0.png)

图 2-12：序列图

顶部的框显示序列中涉及的对象实例。通常，带有下划线名称的框表示实例，而不是类。从对象下降的虚线是对象的生命线。在此示例中，生命线不表示任何对象的创建或删除——在执行此用例之前，所有对象都已存在。但是，可以通过使用“create”消息并在对象生命线底部放置一个大 X 来指示对象的实例化，以显示其删除。

垂直矩形显示对象的激活时间，即对象参与特定操作执行的时间段。在此示例中，时间以垂直方向表示，因此对象的激活时间越长（由代表它的矩形长度表示），它参与操作的时间就越长。

此图还引入了应用程序中的另一个对象，即 System 对象。在 BandSpy 应用程序中，System 对象将接收来自 Web GUI 的所有消息，而不是允许它直接与您的其他对象交互。这样，应用程序就有一个单一的入口点。

箭头表示消息。它们以对象的相应方法名称命名，但不必太正式，可以直接为消息使用非方法式的名称。逐条查看消息，序列如下：

- 1. 用户通过输入乐队名称请求查看特定乐队的所有乐器。
- 2. System 对象通过在自身实用方法上执行自调用来查找乐队引用。
- 3. System 对象使用找到的乐队引用，并在其上调用 getBandMembers 方法。
- 4. Band 对象调用其分配的音乐家的 getInstruments 方法。
- 5. Musician 对象在其分配的每个乐器上调用 getName 方法。
- 6. 乐器名称将返回到 System 对象以供用户显示。

## 状态图

当您想要显示单个对象在其生命周期中的状态变化时，状态图非常有用。状态变化可以是成员变量的简单差异，也可以是更复杂的行为，例如轮询外部源的响应。

在 BandSpy 中，Performance 类有一个值得用状态图记录的生命周期。创建新的 Performance 对象时，必须联系场地预订系统并等待确认。如果来自场地系统的响应表示预订有效，则必须永久存储该性能。如果预订未被接受，Performance 对象应通知系统，然后销毁。在图 2-13 中，一个状态图显示了该对象的各种状态。

![](img/a1b732997d9cb194dceec0570dc79710_59_0.png)

实心圆表示对象生命周期的开始，箭头表示从一个状态到另一个状态的转换。在新的 `Performance` 初始化并向场地系统发送消息后，等待确认状态将一直轮询，直到从场地系统收到回复。

图 2-13 中的一个新符号是一个 *注释*，指示等待确认状态应等待一分钟以接收来自场地系统的回复。在希望添加此类额外信息的任何 UML 图中，都可以使用 *注释*。

## 组件和部署图

本章讨论的最后一个图是 *组件图*，它提供了软件的高层次抽象视图。对于 BandSpy 组件图，大部分代码都减少到 Web 服务器上的单个组件。从技术上讲，Web 服务器等元素是另一种称为 *部署图* 的 UML 图的一部分。部署图显示应用程序基础设施的一些物理元素（例如应用程序运行的不同服务器）。

![](img/a1b732997d9cb194dceec0570dc79710_60_0.png)

图 2-14：部署图

组件是节点内较小的矩形。虚线箭头是 *依赖*。BandSpy Web GUI 依赖于 Web 服务器上的 BandSpy 应用程序。不过，反过来不成立；另一个客户端可以访问系统。实线表示节点之间的连接——例如，通过 HTTP 通信的 Web 浏览器。

小圆圈是一种用于显示接口的速记形式。如前所述，此示例应用程序具有一个所有客户端都必须使用的 `System` 接口。场地预订系统节点内显示了另一个接口。管理该系统的公司已为您提供了可使用的公共方法列表。您不需要了解场地系统的任何内部工作原理；只需了解预订系统中使用的应用程序编程接口 (API) 的方法即可。

## 摘要

UML 为您提供了一种标准化、灵活的语言来设计和建模您的软件。本章讨论了以下 UML 图：

- [ ] 用例图
- [ ] 类图
- [ ] 活动图
- [ ] 序列图
- [ ] 状态图
- [ ] 组件和部署图

您还学习了一些关于软件架构的概念，例如领域建模和需求收集。

请记住，不需要使用每种图。用例图和类图几乎总是有用，但其他图不值得为软件中的每个类或用例绘制。只有当您想更好地了解单个用例中的流程时，才需要活动图。如果您有一个对象，其状态在一个或多个用例中以复杂方式发生变化，并且您需要说明它将如何工作，请使用状态图。通常需要一些序列图，但不要尝试为应用程序中每个实例之间传递的每条消息绘制图表。

第 4 章讨论软件设计模式，这是一种描述可重用对象关系的方法，可用于解决软件开发中的各种问题。由于每种设计模式都使用 UML 类图来描述，因此当您学习到该章节时，您将处于良好的学习状态。

第 3 章开始探讨如何实际实现本章和第 1 章中检查的概念，以制作可用的 PHP 代码。您将使用类图来描述将要编写的代码，因此您将开始了解它们的用途，以及为什么在设计应用程序架构时它们是一个值得利用的重要工具。

## 将对象投入工作

既然您已从第 1 章中很好地了解面向对象 (OO) 基础知识，让我们继续深入，更复杂地探讨如何使用 OO 技术构建真实应用程序。

本章中的示例应用程序是一个联系人管理器，旨在管理有关个人和组织的数据，并使用户能够查找和编辑与它们关联的联系信息。本章的讨论旨在让您全面了解创建可用 OO 应用程序背后的问题。在此过程中，本章还演示了 OO 范式背后的主要原则（例如代码重用、封装、继承和，当然，抽象）如何应用。

### 创建联系人管理器

联系人管理应用程序使用户能够跟踪个人和组织、他们的联系信息（例如地址、电子邮件和电话号码）以及它们之间的关系。这基本上就是 Microsoft Outlook 地址簿所做的事情。

以下是您可能期望从这类程序中获得的快速高级描述：

- [ ] 应用程序将在数据库中跟踪有关个人和组织的信息，并在 Web 页面上显示它。
- [ ] 联系人可以拥有零个或多个地址、电子邮件地址和电话号码。
- [ ] 个人只有一个雇主（一个组织）。
- [ ] 组织有零个或多个员工（个人）。




你现在可以看看如何使用 UML 开始构建这个解决方案。不过，在开始之前，有一点需要明确：本章演示了在设计应用程序时，随着你发现实现解决方案的新且更好的方法，你的思路可能会如何演变。因此，本章更应被视为示例应用程序的渐进式演进和开发，而非其代码的简单列举。像这样的具体示例可以帮助你更好地理解面向对象编程（OOP）的原理是如何工作的。

## 联系人管理器 UML 图

启动你选择的 UML 绘图应用程序，创建一个名为 ContactManager.[extension] 的新文件，其中 [extension] 是你应用程序的默认文件扩展名（例如，使用 Dia 创建的图表为 .dia，等等）。

首先，为你想要表示的不同类型的联系人信息创建类。对于这个示例应用程序，这些是地址、电子邮件地址和电话号码类——但你可以为所需的任何类型的联系人信息创建类。

## 表 3-1 联系人信息类

| 类 | 属性 |
| :--- | :--- |
| Address | street1<br>street2<br>city<br>state<br>zip（邮政编码）<br>type（家庭、工作，等等） |
| Email | email<br>type |
| PhoneNumber | number<br>extension<br>type |

这些类仅用于存储和显示数据，因此此时无需定义任何方法，类符号的第三部分为空。所有属性均为公共属性，因此都以加号作为前缀。图 3-1 展示了这些类当前的 UML 表示。

![](img/a1b732997d9cb194dceec0570dc79710_64_0.png)

图 3-1：基本联系人类型

接下来，你应该规划 Individual 和 Organization 类。一个个体拥有名、姓、雇主、职位、唯一标识符（数据库中的 id 字段）以及一个集合（电子邮件、地址和电话号码）。你还必须能够添加联系类型。图 3-2 展示了带有 Individual 类的 UML 图。

![](img/a1b732997d9cb194dceec0570dc79710_64_1.png)

图 3-2：Individual 类和联系类型

一个组织拥有名称、唯一标识符、联系类型的集合（与个体类似）、用于添加它们的方法以及员工集合。图 3-3 展示了带有 Organization 类的 UML 图。

![](img/a1b732997d9cb194dceec0570dc79710_65_0.png)

图 3-3：Individual 和 Organization 联系类型

该图显示 Individual 和 Organization 类共享许多相同的属性和方法。这通常表明，你可以通过使用继承来节省大量工作并提高应用程序的灵活性。你可以创建另一个类（本示例中的 Entity），在其中合并 Individual 和 Organization 类共有的功能，然后使它们共享相同的代码。在 UML 图中，你仅在实际实现属性和方法的类上标注它们。在这种情况下，你必须将 Individual 和 Organization 类的所有共同属性和方法移动到表示 Entity 类的符号中，如图 3-4 所示。仅当子类重写实现时，才将它们重复在子类中（子类从其父类继承成员）。

| Address |
|---------|
| +street1 |
| +street2 |
| +city |
| +state |
| +zip |
| +type |

| Email |
|-------|
| +email |
| +type |

| PhoneNumber |
|-------------|
| +number |
| +extension |
| +type |

| Entity |
|--------|
| +name |
| +id |
| +addresses: Address |
| +phoneNumbers: PhoneNumber |
| +emails: EmailAddress |
| +addEmail(objEmail:EmailAddress) |
| +addAddress(objAddress:Address) |
| +addPhone(objPhone:PhoneNumber) |

| Individual |
|------------|
| +firstname |
| +lastname |
| +name |
| +employer: Organization |
| +title |

| Organization |
|--------------|
| +employees: Individual |

**图 3-4：Entity 类，Individual 和 Organization 的通用超类**

在这种情况下，`Entity` 类的 `name` 属性在 `Individual` 类中被重写。当你检索 Individual 的 `name` 属性时，你将返回“lastname, firstname”。这样，你可以将 `Organization` 或 `Individual` 类交给一个函数，该函数只需打印一个名称，而无需使用单独的函数。

UML 还定义了用于指示关系的符号。在本示例中，你需要某种东西来显示 `Individual` 和 `Organization` 类继承自 `Entity` 类。如你所见，UML 规范将此关系称为 *泛化*，并使用从子类指向父类的开放箭头来指示它，如图 3-5 所示。

![](img/a1b732997d9cb194dceec0570dc79710_67_0.png)

图 3-5：泛化，由开放箭头指示

现在很明显，Individual 和 Organization 类继承自 Entity 类。使用连接器来指示继承，使你可以一眼看出图表中类之间的关系。

还需要展示另一种连接类型——Entity 类使用 Address、Email 和 PhoneNumber 类。UML 规范将此关系称为 composite，你通过在附加到类使用者一端的线上使用黑色菱形来指示它，如图 3-6 所示。被使用的类还具有一个称为多重性（即使用的数量）的属性。在本示例中，一个实体可能拥有零个、一个或多个任何联系类型，因此你在最靠近被使用项目的连接器线上写上 0..*，以指示一个类可能拥有 0 个或多个其所指向的类。

图 3-6 也展示了这种表示法。通过在图中揭示这种关系，你可以清楚地看到应用程序的哪些部分会受到另一部分更改的影响。在这里，对 Email、Address 或 PhoneNumber 类的更改将影响 Entity、Individual 和 Organization 类。

![](img/a1b732997d9cb194dceec0570dc79710_68_0.png)

图 3-6：Composite，通过在线段末端使用黑色菱形指示

一个 Entity 拥有一个 PhoneNumber、一个 Email 和一个 Address；在这三种情况下，它都可能拥有零个或多个该项目。因为 Individual 和 Organization 继承自 Entity，所以它们两者也都拥有零个或多个联系类型。

这就是目前为止所理解的应用程序基本结构。当然，你可以通过思考如何在现实中实际实现它来对其进行很多改进。关于这一点有几点重要事项需要注意。在下一节中，你将开发该应用程序。本章稍后将展示更多 UML，以便你清楚了解最终产品的样子。

回顾第 1 章中关于封装的讨论，将数据保护在私有成员变量中，并使用访问器方法来提供对这些属性的访问，这始终是个好主意。还要记住，使用 __get 和 __set 会使此过程更加容易。只需查看本章前面显示的类图，你就可以看到所有类都有相当简单的属性要求。因为你了解继承以及如何在 PHP 中利用它，所以你可以将功能从仅与 Entity 类绑定中解耦，并创建一个类，使你能够在其他类中重用其代码——实际上，为所有类共有的功能添加另一层抽象，以便更好地使用。这个父类将被称为 PropertyObject。

在现实世界中，出于良好实践的考虑，处理数据时你可能也希望添加一层抽象。为此，创建一个 DataManager 类可能是个好主意。还需要考虑的一点是，目前你没有统一的数据验证设施，因此需要一个可验证对象的接口。下面是接口的代码：

```
<?php
interface Validator {
    public function validate();
}
?>
```



将文件命名为 interface.Validator.php。现在与新的 PropertyObject 类一起使用它，该类将在下一节中展示。

## PropertyObject 类

以下代码展示了如何将 Validator 接口与 PropertyObject 类集成。将代码输入到名为 class.PropertyObject.php 的文件中：

```php
<?php
require_once('interface.Validator.php');

abstract class PropertyObject implements Validator {
	protected $propertyTable = array(); //stores name/value pairs
				//that hook properties to
				//database field names
	protected $changedProperties = array(); //List of properties that
				//have been modified

	protected $data; //Actual data from
				//the database

	protected $errors = array(); //Any validation errors
				//that might have occurred
	public function __construct($arData) {
		$this->data = $arData;
	}

	public function __get($propertyName) {
		if(!array_key_exists($propertyName, $this->propertyTable)) {
			throw new Exception("Invalid property " . $propertyName . "!");
		}
		if(method_exists($this, 'get' . $propertyName)) {
			return call_user_func(array($this, 'get' . $propertyName));
		} else {
			return $this->data[$this->propertyTable[$propertyName]];
		}
	}

	public function __set($propertyName, $value) {
		if(!array_key_exists($propertyName, $this->propertyTable)) {
			throw new Exception("Invalid property " . $propertyName . "!");
		}
		if(method_exists($this, 'set' . $propertyName)) {
			return call_user_func(array($this, 'set' . $propertyName), $value);
		} else {

			//If the value of the property really has changed
			//and it's not already in the changedProperties array,
			//add it.
			if($this->propertyTable[$propertyName] != $value &&
			!in_array($propertyName, $this->changedProperties)) {
				$this->changedProperties[] = $propertyName;
			}
			//Now set the new value
			$this->data[$this->propertyTable[$propertyName]] = $value;
		}
	}
	public function validate() {
	}
}
?>
```

仔细看看这里发生了什么。你创建了四个受保护的成员变量。受保护的成员变量只对类的子类可见；对使用这些对象的代码不可见。

$propertyTable 将包含可读属性名与数据库中字段名之间的映射。数据库字段的常见命名约定涉及使用前缀来指示数据类型。例如，entities.sname1 可能是 entities 表中类型为 string 的字段，包含名字。然而，sname1 并不是一个对象属性的友好名称，因此提供一种机制将数据库字段命名约定转换为友好属性名称是很有用的。

$changedProperties 是一个数组，存储已修改的属性名称列表。

$data 将是数据库字段名和值的关联数组。该数组将提供给构造函数，其数据结构直接来自 pgsql_fetch_assoc()。这种方法使直接从数据库查询构建有用对象变得更容易，您将很快看到。

最后一个成员变量 $errors 将包含一个字段名和错误消息的数组，以防 validate 方法（Validate 接口要求）失败。

该类被声明为抽象类有两个原因。首先，PropertyObject 类本身并不十分有用。扩展 PropertyObject 的类在可以使用其方法之前仍有一些工作要做。其次，您尚未提供所需方法 validate() 的实现。由于您仍在 PropertyObject 中将该方法标记为抽象，因此也必须将类本身标记为抽象，迫使所有继承类实现该函数。任何尝试使用扩展 PropertyObject 但不实现该函数的类都会导致运行时错误。

接下来，您将看到大大简化的构造函数。构造函数仅接受来自数据库查询的关联数组，并将其分配给受保护的成员变量 $data。PropertyObject 的大多数子类需要覆盖构造函数并做一些更有趣的事情。

最后，请注意 __get() 和 __set() 访问器方法的内部实现。由于您在 $data 成员中存储数据，必须能够将属性名映射到数据库中的实际字段名。包含以下代码的行正是这样做的：

```
$this->data[$this->propertyTable[$propertyName]]
```

通过使用数据库字段名而不是属性名来获取和分配 $data 成员的值，您正在实现一种数据持久性形式。

如果您对 $data 和 $propertyTable 成员的工作原理尚不清楚，请不要担心。一旦您看到示例，就会明白。

## 联系人类型类

有了 PropertyObject 类，您就可以开始使用它了。以下文件针对 Address、Email 和 PhoneNumber 类。

在代码中，您将看到一个名为 DataManager 的类的引用，它将是您需要使用的所有数据库函数的包装类。此包装类使您能够有一个集中位置来存放所有数据交互代码。您将很快检查该类。

将以下代码（Address 类）输入到名为 class.Address.php 的文件中：

```php
<?php
require_once('class.PropertyObject.php');

class Address extends PropertyObject {
    function __construct($addresssid) {
        $arData = DataManager::getAddressData($addresssid);

        parent::__construct($arData);

        $this->propertyTable['addresssid'] = 'addresssid';
        $this->propertyTable['id'] = 'addressid';
        $this->propertyTable['entityid'] = 'entityid';
        $this->propertyTable['address1'] = 'saddress1';
        $this->propertyTable['address2'] = 'saddress2';
        $this->propertyTable['city'] = 'scity';
        $this->propertyTable['state'] = 'cstate';
        $this->propertyTable['zipcode'] = 'postalcode';
        $this->propertyTable['type'] = 'stype';
    }

    function validate() {
        if(strlen($this->state) != 2) {
            $this->errors['state'] = 'Please choose a valid state.';
        }

        if(strlen($this->zipcode) != 5 &&
           strlen($this->zipcode) != 10) {
            $this->errors['zipcode'] = 'Please enter a 5- or 9-digit zip code';
        }

        if(!$this->address1) {
            $this->errors['address1'] = 'Address 1 is a required field.';
        }

        if( !$this->city ) {
            $this->errors['city'] = 'City is a required field.';
        }

        if(sizeof($this->errors)) {
            return false;
        } else {
            return true;
        }
    }

    function __toString() {
        return $this->address1 . ', ' .
            $this->address2 . ', ' .
            $this->city . ', ' .
            $this->state . ', ' . $this->zipcode;
    }
}
?>
```

由于 PropertyObject 类承担了大部分工作，Address 类中只需要实现两个方法（__toString() 实现纯属为了好玩）。在构造函数中，您第一次看到了 $propertyTable 数组的工作原理。类中所需属性的列表是在应用程序初始架构过程中创建的 Address 类 UML 图中指定的（本章开头）。

基于此对象的属性，您还可以对数据库表的结构做出一些决定。通常，每个属性都需要一个字段；并且因为这个类需要与 Entity 类关联，您需要存储对父 Entity 的某些引用。使用以下 SQL 语句创建 Entity 和 Address 表：

```sql
CREATE TABLE "entity" (
    "entityid" SERIAL PRIMARY KEY NOT NULL,
    "name1" varchar(100) NOT NULL,
    "name2" varchar(100) NOT NULL,
    "type" char(1) NOT NULL
);

CREATE TABLE "entityaddress" (
    "addressid" SERIAL PRIMARY KEY NOT NULL,
    "entityid" int,
    "saddress1" varchar(255),
    "saddress2" varchar(255),
    "scity" varchar(255),
    "cstate" char(2),
    "spostalcode" varchar(10),
    "stype" varchar(50),
    CONSTRAINT "fk_entityaddress_entityid"
    FOREIGN KEY ("entityid") REFERENCES "entity"("entityid")
);
```





一个命名得当的数据库字段会使用一个字符前缀来指示其数据类型，让你知道该字段中存放什么类型的数据。命名规范对数据库设计和对你的代码同样重要。

Address 类中的 propertyTable 数组用于将友好的属性名称（例如 city、state 和 zip code）映射到不太友好的数据库字段名称（例如 scity、cstate 和 postalcode）。请注意，你可以在 propertyTable 中将多个属性名称映射到同一个数据库字段名称。此映射使你可以通过 $objAddress->addressid 或 $objAddress->id 来引用地址的主键。

关于 Address 类令人兴奋的是，绝大部分代码都用于实现业务逻辑和数据验证。这里几乎没有多余的代码。它唯一的职责是填充自身并验证其自身内容。其他所有内容都留给 DataManager 类（稍后你将详细了解）和 PropertyObject。

以下是 Email 类的代码，应该非常熟悉。将其输入到名为 class.EmailAddress.php 的文件中：

```php
<?php
require_once('class.PropertyObject.php');
class Email extends PropertyObject {
    function __construct($emailid) {
        $arData = DataManager::getEmailData($emailid);
        parent::__construct($arData);
        $this->propertyTable['emailid'] = 'emailid';
        $this->propertyTable['id'] = 'emailid';
        $this->propertyTable['entityid'] = 'entityid';
        $this->propertyTable['email'] = 'semail';
        $this->propertyTable['type'] = 'stype';
    }
    function validate() {
        if(!$this->email) {
            $this->errors['email'] = 'You must set an email address.';
        }
        if(sizeof($this->errors)) {
            return false;
        } else {
            return true;
        }
    }
    function __toString() {
        return $this->email;
    }
}
?>
```

此文件中的辅助代码非常少；它只是从数据库获取数据并设置 propertyTable。其他所有内容都是数据验证。同样，UML 图是决定 Email 类属性及相应数据库表结构的指南。

entityemail 表的数据库表如下：

```sql
CREATE TABLE "entityemail" (
 "emailid" SERIAL PRIMARY KEY NOT NULL,
 "entityid" int,
 "semail" varchar(255),
 "stype" varchar(50),
 CONSTRAINT "fk_entityemail_entityid"
 FOREIGN KEY ("entityid") REFERENCES "entity"("entityid")
 );
```

PhoneNumber 类的工作方式与 Address 和 Email 非常相似。以下是要输入到 class.PhoneNumber.php 中的代码：

```php
<?php
 require_once('class.PropertyObject.php');
 class PhoneNumber extends PropertyObject {
 function __construct($phoneid) {
    $arData = DataManager::getPhoneNumberData($phoneid);
    parent::__construct($arData);
    $this->propertyTable['phoneid'] = 'phoneid';
    $this->propertyTable['id'] = 'phoneid';
    $this->propertyTable['entityid'] = 'entityid';
    $this->propertyTable['number'] = 'snumber';
    $this->propertyTable['extension'] = 'sextension';
    $this->propertyTable['type'] = 'stype';
 }
 function validate() {
    if(!$this->number) {
    $this->errors['number'] = 'You must supply a phone number.';
    }
    if(sizeof($this->errors)) {
    return false;
    } else {
    return true;
    }
 }
 function __toString() {
    return $this->number .
    ($this->extension ? ' x' . $this->extension : '');
 }
 }
 ?>
```

以下是创建 entityphone 表的 SQL 语句：

```sql
CREATE TABLE "entityphone" (
 "phoneid" SERIAL PRIMARY KEY NOT NULL,
 "entityid" int,
 "snumber" varchar(20),
 "sextension" varchar(20),
 "stype" varchar(50),
 CONSTRAINT "fk_entityemail_entityid"
 FOREIGN KEY ("entityid") REFERENCES "entity"("entityid")
 );
```

## DataManager 类

现在让我们来看看 DataManager 类。它以及本章（以及本书其余部分）中的其他数据库代码示例使用 PostgreSQL，尽管像这样的类也可以与 MySQL、Oracle 或任何其他 RDBMS 配合使用。第 6 章探讨了处理数据库抽象的更复杂的方法，但目前让我们使用 PHP PostgreSQL 函数来保持简单。

DataManager 类的主要职责是将所有数据访问代码放在一个位置，以便以后更容易更改数据库类型或连接参数。该类的所有方法都已声明为静态，因为该类不依赖任何成员变量。请注意 getConnection() 中使用了静态函数变量。这是用于确保在单个页面请求期间只打开一个数据库连接。建立数据库连接会带来许多开销，因此消除不必要的连接有助于提高性能。创建名为 class.DataManager.php 的文件并输入以下类代码：

```php
<?php

require_once('class.Entity.php'); //this will be needed later
require_once('class.Individual.php');
require_once('class.Organization.php');

class DataManager {

 private static function _getConnection() {
   static $hDB;

   if(isset($hDB)) {
     return $hDB;
   }

   $hDB = pg_connect("host=localhost port=5432 " .
     "dbname=[your db name] user=[your user name]
     password=[your password]");
   or die("Failure connecting to the database!");
   return $hDB;
 }

 public static function getAddressData($addressID) {
   $sql = "SELECT * FROM \"entityaddress\" WHERE\"addressid\" = $addressID";
   $res = pg_query(DataManager::_getConnection(), $sql);
   if(! ($res && pg_num_rows($res))) {
       die("Failed getting address data for address $addressID");
   }

   return pg_fetch_assoc($res);
 }

 public static function getEmailData($emailID) {
     $sql = "SELECT * FROM \"entityemail\" WHERE\"emailid\" = $emailID";
     $res = pg_query(DataManager::_getConnection(), $sql);
     if(! ($res && pg_num_rows($res))) {
     die("Failed getting email data for email $emailID");
     }

     return pg_fetch_assoc($res);
 }

 public static function getPhoneNumberData($phoneID) {
     $sql = "SELECT * FROM \"entityphone\" WHERE \"phoneid\" = $phoneID";
     $res = pg_query(DataManager::_getConnection(), $sql);
     if(! ($res && pg_num_rows($res))) {
     die("Failed getting phone number data for phone $phoneID");
     }

     return pg_fetch_assoc($res);
 }
 }
?>
```

DataManager 类提供用于填充 PropertyObject 子类的 $data 成员的数据结构。单独的函数返回每种类型的数据。本章稍后你将向此类添加一些新函数。请注意，传递给 pg_connect 的值不需要方括号。方括号中的所有值（包括括号本身）都应替换为你服务器的相应连接详细信息。

该类的所有方法都声明为静态。请记住，静态方法是要求所有成员变量也为静态的方法。你无需实例化静态类即可使用其方法。这种方法在多种场景下很有意义。假设有一个名为 Math 的类，它公开了 squareRoot()、power() 和 cosine() 等方法，并具有包括数学常数 e 和 pi 在内的属性。该类的所有实例都执行相同的数学运算。2 的平方根不会改变；4 的三次方始终是 64；而这两个常数，嗯，是常量。无需为此类创建单独的实例，因为它的状态和属性永远不会改变。以这种方式实现的名为 Math 的类应该允许以静态方式调用其所有函数。

DataManager 类大致相同。所有函数都是自包含的。没有非静态成员变量可供函数交互。该类不公开任何属性。因此，你可以使用静态方法运算符 :: 来调用该类的方法。由于你创建的所有方法都是静态的，你永远不需要使用 $obj = new DataManager() 实例化对象，然后使用类似 $obj->getEmail() 的语法调用方法。相反，你可以使用简单的语法 DataManager::getEmail()。





## 实体、个人和组织类

在所有辅助类就绪后，你可以转向应用程序的核心：`Entity` 类及其子类。

首先，请确保在修改对象层次结构时更新 UML 图，以便跟踪你（或开发团队）正在做什么。你已创建 `PropertyObject` 类并让所有类从中继承，只有一个例外——新的 `DataManager` 类，它不继承自任何类，而仅提供数据抽象功能。`PropertyObject` 实现了一个名为 `Validator` 的抽象接口。图 3-7 显示了更新后的图。

![](img/a1b732997d9cb194dceec0570dc79710_77_0.png)

### 图 3-7：更新后的 UML 图

现在你可以开始开发 Entity、Individual 和 Organization 类了。以下代码展示了名为 class.Entity.php 的完全实现的 Entity 类：

```php
<?php
require_once('class.PropertyObject.php');
require_once('class.PhoneNumber.php');
require_once('class.Address.php');
require_once('class.EmailAddress.php');

abstract class Entity extends PropertyObject {
private $emails;
private $addresses;
private $phonenumbers;

public function __construct($entityID) {
$arData = DataManager::getEntityData($entityID);

parent::__construct($arData);

$this->propertyTable['entityid'] = 'entityid';
$this->propertyTable['id'] = 'entityid';
$this->propertyTable['name1'] = 'sname1';
$this->propertyTable['name2'] = 'sname2';
$this->propertyTable['type'] = 'ctype';
$this->_emails = DataManager::getEmailObjectsForEntity($entityID);
$this->_addresses = DataManager::getAddressObjectsForEntity($entityID);
$this->_phonenumbers = DataManager::getPhoneNumberObjectsForEntity($entityID);
}

function setID($val) {
throw new Exception('You may not alter the value of the ID field!');
}

function setEntityID($val) {
$this->setID($val);
}

function phonenumbers($index) {
if(!isset($this->_phonenumbers[$index])) {
throw new Exception('Invalid phone number specified!');
} else {
return $this->_phonenumbers[$index];
}
}

function getNumberOfPhoneNumbers() {
return sizeof($this->_phonenumbers);
}

function addPhoneNumber(PhoneNumber $phone) {
    $this->_phonenumbers[] = $phone;
}

function addresses($index) {
    if(!isset($this->_addresses[$index])) {
        throw new Exception('Invalid address specified!');
    } else {
        return $this->_addresses[$index];
    }
}

function getNumberOfAddresses() {
    return sizeof($this->_addresses);
}

function addAddress(Address $address) {
    $this->_addresses[] = $address;
}

function emails($index) {
    if(!isset($this->_emails[$index])) {
        throw new Exception('Invalid email specified!');
    } else {
        return $this->_emails[$index];
    }
}

function getNumberOfEmails() {
    return sizeof($this->_emails);
}

function addEmail(Email $email) {
    $this->_emails[] = $email;
}

public function validate() {
    //Add common validation routines
}

?>
```

通过将所有访问器方法功能移至父类 PropertyObject，你简化了 Entity 类，并确保它只专注于实现实体所需的代码。

Entity 类被声明为抽象类，因为它本身并无用处。所有实体要么是 Individual（个人），要么是 Organization（组织）。你不希望能够实例化 Entity 类的对象。将其声明为抽象类可防止该类被实例化。

你已添加对 DataManager::getEntityData() 和 get[x]ObjectsForEntity() 的几个新函数的请求。getEntityData() 返回实例化实体所需的数据，就像你已经见过的用于联系类型的函数一样。以下是 class.DataManager.php 中新函数的代码：

```php
// top of file omitted for brevity
...
die("Failed getting phone number data for phone $phoneID");
}
return pg_fetch_assoc($res);
}

public static function getEntityData($entityID) {
    $sql = "SELECT * FROM \"entity\" WHERE \"entityid\" = $entityID";
    $res = pg_query(DataManager::getConnection(), $sql);
    if (!($res && pg_num_rows($res))) {
        die("Failed getting entity $entityID");
    }
    return pg_fetch_assoc($res);
}

public static function getAddressObjectsForEntity($entityID) {
    $sql = "SELECT \"addressid\" from \"entityaddress\" WHERE " .
        "\"entityid\" = $entityID";
    $res = pg_query(DataManager::getConnection(), $sql);
    if(!$res) {
        die("Failed getting address data for entity $entityID");
    }
    if(pg_num_rows($res)) {
        $objs = array();
        while($rec = pg_fetch_assoc($res)) {
            $objs[] = new Address($rec['addressid']);
        }
        return $objs;
    } else {
        return array();
    }
}

public static function getEmailObjectsForEntity($entityID) {
    $sql = "SELECT \"emailid\" from \"entityemail\" " .
        "WHERE \"entityid\" = $entityID";
    $res = pg_query(DataManager::getConnection(), $sql);
    if(!$res) {
        die("Failed getting email data for entity $entityID");
    }
    if(pg_num_rows($res)) {
        $objs = array();
        while($rec = pg_fetch_assoc($res)) {
            $objs[] = new EmailAddress($rec['emailid']);
        }
        return $objs;
    } else {
        return array();
    }
}

public static function getPhoneNumberObjectsForEntity($entityID) {
    $sql = "SELECT \"phoneid\" from \"entityphone\" " .
        "WHERE \"entityid\" = $entityID";
    $res = pg_query(DataManager::getConnection(), $sql);

    if (!$res) {
        die("Failed getting phone data for entity $entityID");
    }

    if(pg_num_rows($res)) {
        $objs = array();
        while($rec = pg_fetch_assoc($res)) {
            $objs[] = new PhoneNumber($rec['phoneid']);
        }
        return $objs;
    } else {
        return array();
    }
}
```

这些函数接受一个实体 ID 值。它们查询数据库，以确定相关实体是否存在任何电子邮件、地址或电话号码。如果存在，则函数会通过将每个 ID 传递给相应对象类型的构造函数，构建一个 EmailAddress、Address 或 PhoneNumber 对象数组。然后，该数组被传回 Entity 对象，并在适当的私有成员变量中存储。

Entity 类承担了所有繁重工作，剩下的工作就相当简单了。你只需实现 Individual 和 Organization 类。创建一个名为 class.Individual.php 的文件，并输入以下内容：

```php
<?php
require_once('class.Entity.php');
require_once('class.Organization.php');

class Individual extends Entity {

    public function __construct($userID) {
        parent::__construct($userID);

        $this->propertyTable['firstname'] = 'name1';
        $this->propertyTable['lastname'] = 'name2';
    }

    public function __toString() {
        return $this->firstname . ' ' . $this->lastname;
    }

    public function getEmployer() {
        return DataManager::getEmployer($this->id);
    }

    public function validate() {
        parent::validate();

        //add individual-specific validation
    }

}
?>
```

简短明了。继承使这变得容易。Individual 类设置了几个新属性，使访问个人的名和姓更加容易，而无需使用 Entity 类中定义的相当难看的 name1 和 name2 属性。它还定义了一个新方法 getEmployer()，该方法需要 DataManager 中的一个新函数。一旦你有了 Organization 类（如以下代码所示），就可以访问该函数。创建一个名为 class.Organization.php 的文件，并将此代码输入其中：

```php
<?php

require_once('class.Entity.php');
require_once('class.Individual.php');

class Organization extends Entity {

    public function __construct($userID) {
        parent::__construct($userID);
        $this->propertyTable['name'] = 'name1';
    }

    public function __toString() {
        return $this->name;
    }

    public function getEmployees() {
        return DataManager::getEmployees($this->id);
    }

    public function validate() {
        parent::validate();

        //do organization-specific validation
    }

}
?>



再次强调，这是一个相当简单的类，得益于继承的强大功能。你声明一个名为 name 的属性，这样更容易获取组织拥有的唯一名称（sname2 属性对组织未使用）。

要向 DataManager 类添加 getEmployer() 和 getEmployees() 函数，请将以下代码追加到 class.DataManager.php 文件末尾：

```
public static function getEmployer($individualID) {
    $sql = "SELECT \"organizationid\" FROM \"entityemployee\" . "
        "WHERE \"individualid\" = $individualID";
    $res = pg_query(DataManager::getConnection(), $sql);
    if(! ($res && pg_sql_num_rows($res))) {
        die("Failed getting employer info for individual $individualID");
    }

    $row = pg_sql_fetch_assoc($res);

    if($row) {
        return new Organization($row['organizationid']);
    } else {
        return null;
    }
}

public static function getEmployees($orgID) {
    $sql = "SELECT \"individualid\" FROM \"entityemployee\" . "
        "WHERE \"organizationid\" = $orgID";
    $res = pg_sql_query(DataManager::getConnection(), $sql);

    if(! ($res && pg_sql_num_rows($res))) {
        die("Failed getting employee info for org $orgID");
    }
    if(pg_sql_num_rows($res)) {
        $objs = array();
        while($row = pg_sql_fetch_assoc($res)) {
            $objs[] = new Individual($row['individualid']);
        }
        return $objs;
    } else {
        return array();
    }
}
```

这两个函数依赖于名为 entityemployee 的表的存在，如以下代码所示。该表将个人与雇佣他们的组织关联起来。例如，同一家公司的员工会有不同的个人 ID，但相同的组织 ID。

```
CREATE TABLE "entityemployee" (
    "individualid" int NOT NULL,
    "organizationid" int NOT NULL,
    CONSTRAINT "fk_entityemployee_individualid"
    FOREIGN KEY ("individualid") REFERENCES "entity"("entityid"),
    CONSTRAINT "fk_entityemployee_organizationid"
    FOREIGN KEY ("organizationid") REFERENCES "entity"("entityid")
);
```

还需要最后一个函数才能使整个系统工作 — DataManager 中用于列出数据库中所有实体的方法。它名为 getAllEntitiesAsObjects()，用于完成你对对象所需的所有工作。将此方法添加到 class.DataManager.php 中：

```
public static function getAllEntitiesAsObjects() {
$sql = "SELECT \"entityid\", \"type\" from \"entity\"";
$res = pg_sql_query(DataManager::getConnection(), $sql);
if(!$res) {
die("Failed getting all entities");
}
if(pg_sql_num_rows($res)) {
$objs = array();
while($row = pg_sql_fetch_assoc($res)) {
if($row['type'] == 'I') {
$objs[] = new Individual($row['entityid']);
} elseif ($row['type'] == 'O') {
$objs[] = new Organization($row['entityid']);
} else {
die("Unknown entity type {$row['type']} encountered!");
}
}
return $objs;
} else {
return array();
}
}
```

DataManager 使你能够枚举系统中的所有联系人。它检查 entity 表中 ctype 字段的值，以确定条目是 Individual 还是 Organization，然后实例化相应类型的对象并将其添加到函数返回的数组中。

## 使用系统

到现在，你可以看到 OOP 方法的真正威力。名为 test.php 的以下代码将显示数据库中所有联系人的视图，包括它们的所有联系信息：

```
<?php
require_once('class.DataManager.php'); //everything gets included by it
function println($data) {
print $data . "<br>\n";
}

$arContacts = DataManager::getAllEntitiesAsObjects();

foreach($arContacts as $objEntity) {

	if(get_class($objEntity) == 'Individual') {
		print "<h1>Individual - {$objEntity->__toString()}</h1>";
	} else {
		print "<h1>Organization - {$objEntity->__toString()}</h1>";
	}

	if($objEntity->getNumberOfEmails()) {
		//We have emails! Print a header
		print "<h2>Emails</h2>";

		for($x=0; $x < $objEntity->getNumberOfEmails(); $x++) {
			println({$objEntity->emails($x)->__toString()}); $x++
		}
	}

	if($objEntity->getNumberOfAddresses()) {
		//We have addresses!
		print "<h2>Addresses</h2>";

		for($x=0; $x < $objEntity->getNumberOfAddresses(); $x++) {
			println({$objEntity->addresses($x)->__toString()});
		}
	}

	if($objEntity->getNumberOfPhoneNumbers()) {
		//We have phone numbers!
		print "<h2>Phones</h2>";

		for($x=0; $x < $objEntity->getNumberOfPhoneNumbers(); $x++) {
			println({$objEntity->phonenumbers($x)->__toString()});
		}
	}

	print "<hr>\n";

} //End foreach

?>
```

你可以将数据输入自己的表中，因为这将帮助你弄清楚一切如何协同工作。你可能想尝试模仿图 3-8 所示的结果（通过在浏览器中导航到 test.php）。

![](img/a1b732997d9cb194dceec0570dc79710_86_0.png)

## 图 3-8：示例应用程序的结果

仅需 50 行代码（包括空行），你就可以显示系统中关于实体的几乎所有内容。这里未显示雇主和员工；再次，这是留给你尝试的练习。test.php 中调用 get_class 函数的那行代码会给你一些想法，帮助你弄清楚正在处理哪个类，从而知道是应该在 Individual 上调用 getEmployer()，还是在 Organization 上调用 getEmployees()。

## 总结

UML 图是规划复杂（甚至不太复杂）应用程序的必备工具。设计得当的图表能让你以纯文本无法实现的更清晰方式记录复杂系统。当你将类图作为常规软件开发流程的一部分时，更容易看出类和数据库表应如何设计。

充分利用 PHP6 中的 OO 特性，有助于快速开发应用程序，并建立一个更易于维护、提供更高灵活性和可扩展性、并减少实现业务需求所需代码总量的代码库。

通过将软件架构分为业务逻辑层（如 `Individual` 类）和数据访问层（如 `DataManager` 类），你可以轻松更改底层数据源、表结构或查询，而不会干扰应用程序的其余部分。负责实现业务逻辑的对象不会被数据访问机制所杂乱，后者的存在可能会混淆和模糊业务规则。

第 4 章探讨了思考软件架构的新方法，该方法提高了代码的可重用性和可维护性，并在设计类时提供了不同层次的抽象。

## 设计模式

在本书的前面章节中，你了解到对象可以通过继承从父对象派生。你还了解到对象可以包含对其他对象的引用（例如，DrumSet 对象持有 Drum 对象）。通常，从其他对象组合对象的技术被称为对象组合。

继承和对象组合都是设计面向对象（OO）软件的强大工具，允许各种各样的设计选择。当然，拥有众多选择并不总是使决策更容易。你会如何设计应用程序，使其易于维护和扩展？你会如何编写一个组件，让团队的其他成员能够通过简单的界面使用？编写软件时，你可以凭借经验、智慧、运气、大量含咖啡因的饮料，或以上因素的任何组合，独自解决某些问题。

你可能已经重复使用过自己的现有代码来解决问题。也许你有一个用于连接数据库的标准脚本。设计模式略有不同，因为它们不仅仅是关于重用代码；它们比这更抽象、更具普遍性。同一设计模式可能出现在完全不同类型的软件中。设计模式关乎重用组织和组合的理念，而不仅仅是重用相同的执行。了解模式后，你将能够识别它在哪里有用。然后你可以继续实现它，因为这是一个被认可的解决方案。

设计模式是解决特定问题的一种特定方式。在本书中，它代表对象或一组对象的结构方式，以及它们如何与模式中的其他对象协作和通信。每个模式都有一个描述性名称（例如 Observer 或 Observable），每个模式都有一个可以在类图中展示的特定设计。

初学模式时可能会感到困惑。如果这个初始描述似乎不够清晰，请不要担心。你将在本章中学习五种不同的模式，并基于前几章中看到的一些代码进行构建。





## 组合模式

你在第 2 章的 `Instrument` 接口中已经初步接触过一种模式——组合模式。请再次查看图 4-1 中的类图。

![](img/a1b732997d9cb194dceec0570dc79710_89_0.png)

图 4-1：表示组合对象的用例图

图 4-1 显示，`DrumSet` 对象可以由 `Drum` 和 `Cymbal` 对象组成。可以将 `Drum` 和 `Cymbal` 视为 `DrumSet` 对象的子对象。`DrumSet` 可以由任意数量的 `Drums` 和 `Cymbals` 组成。不过需要注意的是，`DrumSet` 及其子对象的类型相同，即均为 `Instrument`。当客户端对象与 `DrumSet` 交互时，它使用的接口与与其子对象交互时相同。这种关系被称为 _组合模式_。

图 4-2 展示了组合模式的一般情况。

![](img/a1b732997d9cb194dceec0570dc79710_89_1.png)

图 4-2：组合模式的一般情况

组合模式包含两部分：组件抽象类和组合，组合是组件类的具体实现。所有组合对象都派生自抽象组件类。任何组件都可以包含其他组件。包含其他组件的组件可以视为组合。没有子对象的组件可以视为空组合。

- 某些组合的实现会区分组合对象和叶子对象。叶子对象是不能包含子对象的组件。为简化此示例，所有组件都能充当组合。

从一般情况回过头来，有必要对设计进行修改，将 `Instrument` 接口改为抽象类。接口和抽象类相似之处在于，两者都不能直接用于实例化对象。关键区别在于，抽象类可以包含一些完全实现的方法，而接口只有方法声明。

当你希望在所有子类中保持相同的方法，但又有一些可以由子类共享的通用功能时，应使用抽象类。当子类中大多数或所有方法的实现会有所不同时，应使用接口。图 4-3 展示了新的类图。请注意，抽象类图以斜体表示。

![](img/a1b732997d9cb194dceec0570dc79710_90_0.png)

**图 4-3：新类图**

关联线表示，抽象乐器类的每个具体实例可以包含任意数量（包括零个）其他抽象乐器类实例。

## 实现

以下 PHP 代码展示了组合模式的实现：

```php
<html>
<body>
<head>
<style>
body { font: 12px verdana; font-weight: bold; }
td { font: 11px verdana; }
</style>
</head>

<?php

abstract class AbstractInstrument {

    private $name;
    private $category;
    private $instruments = array();

    public function add(AbstractInstrument $instrument) {
        array_push($this->instruments, $instrument);
    }

    public function remove(AbstractInstrument $instrument) {
        array_pop($this->instruments);
    }

    public function hasChildren() {
        return (bool)(count($this->instruments) > 0);
    }

    public function getChild($i) {
        return $this->instruments[$i];
    }

    public function getDescription() {
        echo "- one " . $this->getName();
        if ($this->hasChildren()) {
            echo " which includes<br>";
            foreach($this->instruments as $instrument) {
                echo "<table cellspacing=5 border=0><tr><td>&nbsp; &nbsp; &nbsp;
                </td><td>";
                $instrument->getDescription();
                echo "</td></tr></table>";
            }
        }
    }

    public function setName($name) {
        $this->name = $name;
    }

    public function getName() {
        return $this->name;
    }

    public function setCategory($category) {
        $this->category = $category;
    }

    public function getCategory() {
        return $this->category;
    }
}

class Guitar extends AbstractInstrument {
    function __construct($name) {
        parent::setName($name);
        parent::setCategory("guitars");
    }
}

class DrumSet extends AbstractInstrument {
    function __construct($name) {
        parent::setName($name);
        parent::setCategory("drums");
    }
}

class SnareDrum extends AbstractInstrument {
    function __construct($name) {
        parent::setName($name);
        parent::setCategory("snare drums");
    }
}

class BaseDrum extends AbstractInstrument {
    function __construct($name) {
        parent::setName($name);
        parent::setCategory("base drums");
    }
}

class Cymbal extends AbstractInstrument {
    function __construct($name) {
        parent::setName($name);
        parent::setCategory("cymbals");
    }
}

$drums = new DrumSet("tama maple set");
$drums->add(new SnareDrum("snare drum"));
$drums->add(new BaseDrum("large bass drum"));

$cymbals = new Cymbal("zildjian cymbal set");
$cymbals->add(new Cymbal("small crash"));
$cymbals->add(new Cymbal("large high hat"));
$drums->add($cymbals);

$guitar = new Guitar("gibson les paul");

echo "List of Instruments: <p>";
$drums->getDescription();
$guitar->getDescription();

?>

</body>
</html>
```

请注意，所有具体乐器（例如 DrumSet 和 Guitar）都派生自 AbstractInstrument 类。同时还要注意，所有子类都继承了抽象类中的已实现方法。要实现 getDescription() 方法，需要检查当前乐器是否有子对象。如果有，则递归调用该方法，直到遍历完整个树。图 4-4 显示了 composite.php 的输出。

![](img/a1b732997d9cb194dceec0570dc79710_93_0.png)

图 4-4：composite.php 的输出

此代码清单展示了多个类定义的组合、演示这些类用法的代码以及内联 HTML。这样做纯粹是为了避免本书过于冗长。
在你的代码中，希望为每个类建立单独的文件，并将业务逻辑与类定义分开。你将在第 13 章了解有关这种做法的设计模式。

历史上（在 PHP 4 中），& 符号会导致对象（在此示例中，类型为 AbstractInstrument）按引用传递：

```php
public function add(AbstractInstrument &$instrument) {
}
```

这一点很重要，否则函数内部将使用完全新的本地副本。
但是，由于 PHP 6 自动按引用传递对象，因此不需要 &。出于本次讨论的目的，这种行为是我们想要的，因为你确实想操作原始对象，而不是它的副本。图 4-5 显示了在组装好乐器及其子乐器后，先前代码的对象图。对象图与类图类似，不同之处在于它们显示带有下划线名称的对象实例。此外，它们表示系统在某一时刻的对象关系。

![](img/a1b732997d9cb194dceec0570dc79710_94_0.png)

图 4-5：对象图

在此示例中，具体乐器类之间并没有太大差异，只是在 Guitar 类中重写了 getDescription() 方法。不过，请考虑一下，如果你需要添加方法来联系制造商以获取库存信息会怎样。如果每个制造商都有偏好的系统联系方式，你可以在 contact() 方法中指定。你首先需要向 AbstractInstrument 添加一个抽象方法，然后在每个子类中实现它。添加抽象方法可确保你不会忘记在子类中实现它。如果不这样做，将会报错。

如果你确定不需要向乐器添加其他功能，可以直接创建一个继承自 AbstractInstrument 的 GenericInstrument 类。这样，当你创建（例如）一个镲片时，会使用如下代码：

```php
$cymbals = new GenericInstrument("zildjian cymbal set");

```





这里的关键点是，任何访问 `Instrument` 接口的对象（无论是你、另一位程序员还是应用程序的其他部分）都不需要知道它是如何实现的。调用 `getDescription()` 会返回 `Instrument` 的树状结构描述，无论它是否有子项，或者其子项是否又有子项，以此类推。该方法的调用者不需要知道它是否有子项。

由于所有乐器对象的接口相同，但它们的响应方式不同，因此乐器对象可以被视为 *多态*。多态的基本描述是 *相同的接口，不同的实现*，或者更广义地说，*相同的接口，不同的行为*。

## 考虑事项

此处描述的组合模式非常灵活。对哪个乐器可以有子项没有限制。考虑添加以下行：

```
$cymbals->add(new Cymbal("large high hat"));
$drums->add($cymbals);
$cymbals->add($drums);
$guitar = new Guitar("gibson les paul");
```

将已经属于鼓的镲片添加到鼓中会创建循环引用。调用 `getDescription()` 时，类似这样的行可能会导致 Web 服务器崩溃。你可能希望防范此类错误。一种策略是在 `add()` 方法中检查被添加的乐器是否已经包含对调用该方法的对象的引用。如果是，你可以报告错误。

你也可能希望尝试无法向其中添加内容的乐器组。一种方法是分别进入每个类定义并覆盖 `add()` 方法，使其不执行任何操作。另一种方法是创建一个新的抽象类，所有单乐器都从中继承。这个抽象类可以有一个 `add()` 方法，该方法要么不执行任何操作，要么报告错误。这更符合之前讨论的组合模式，其中两个类从 `Component` 继承。一个是不能有子项的 `Leaf`，另一个是可以有子项的 `Composite`。其类图如图 4-6 所示。

![](img/a1b732997d9cb194dceec0570dc79710_95_0.png)

**图 4-6：** 显示从 `Component` 继承的两个类的类图

另一个需要考虑的问题是限制某些乐器被添加到组合中。也许你不希望允许将 `Guitar` 对象添加到 `DrumSet`。在这种情况下，你可以根据 `category` 属性定义某些合法类型以实现主谓一致：尝试实现其中任何或所有功能都值得自己动手试一试。

## 观察者模式

通常，你的应用程序中会有一些随时间变化的数据。例如，假设你有一些 GUI 组件需要显示这些数据，并在数据变化时更新数据。你会如何处理？一种解决方案可能是将新更新的数据传递给 GUI 组件的一个方法，以便它能够重绘信息。这种方法的一个问题是要记住每次数据更新时都要这样做。如果不清楚数据会更新多频繁，以及你是否希望 GUI 在数据变化时自动更新，该怎么办？

观察者模式通过使用两个接口：`Observer` 和 `Observable` 来解决这个问题。正如其名称所示，`Observer` “观察” `Observable` 以查看它是否发生变化。

*保持人类感官的主题，`Observer` 有时也被称为 `Listener`，但本章我们将沿用前者名称。*

在最基本的实现中，`Observable` 可以添加 `Observers`。然后 `Observable` 负责在其状态发生任何变化时通知它们，而 `Observer` 负责对变化做出反应。在这个示例中，数据是 `Observable`，GUI 组件是 `Observers`。如果数据发生变化，这些变化将自动反映在任何作为数据 `Observer` 的 GUI 组件中。图 4-7 演示了观察者模式。

![](img/a1b732997d9cb194dceec0570dc79710_96_0.png)

图 4-7：观察者模式

## 小部件

延续之前的示例，你将使用观察者模式来处理在网页图形元素中显示某些乐器价格信息的问题。首先，你必须定义一些简单的图形组件。这些组件将是基本的 HTML 表格结构，其功能将封装在一个对象中。此类组件通常使用通用术语 _小部件_ 来指代。

小部件必须显示相同的乐器信息。对于本示例，该信息仅为乐器的名称和价格。

### 设计小部件

图形小部件将有两项职责。它需要绘制自己的 HTML 以便在网页上显示，并且需要更新它显示的数据。你可能已经注意到（来自图 4-7），`Observer` 接口中定义了一个 `Update` 方法。

每个小部件都是一个 `Observer`。被观察的项目是表示乐器名称和价格信息的数据。数据源是 `Observable`。

因此，所有小部件都应该实现 `Observer` 接口。此外，每个小部件都应该继承一个定义了一些小部件对象之间共享功能的抽象类。这是同时使用接口和抽象类的一个示例。由于 `update()` 方法对所有小部件都相同，因此可以在 `abstract` 类中实现它。类图如图 4-8 所示。

![](img/a1b732997d9cb194dceec0570dc79710_97_0.png)

现在，所有小部件的具体实现都将继承自 AbstractWidget 类。AbstractWidget 类反过来实现 Observer 接口。请注意，AbstractWidget 类图中的 update() 方法未显示为斜体。这意味着该方法实际上在该点已实现。# 符号表示 internalData 属性是受保护的。这意味着 AbstractWidget 的子类可以访问它。如果它是私有的，子类将无法访问它。

请查看名为 abstract_widget.php 的文件中的以下 Widget 代码：

```
<?php
interface Observer {
public function update(Observable $subject);
}

abstract class Widget implements Observer {
protected $internalData = array();
abstract public function draw();
public function update(Observable $subject) {
$this->internalData = $subject->getData();
}
}

class BasicWidget extends Widget {
function __construct() {
}

public function draw() {
$html = "<table border=1 width=130>";
$html .= "<tr><td colspan=3 bgcolor=#cccccc>
<b>Instrument Info</b></td></tr>";
$numRecords = count($this->internalData[0]);
for($i = 0; $i < $numRecords; $i++) {
$instms = $this->internalData[0];
$prices = $this->internalData[1];
$years = $this->internalData[2];
$html .= "<tr><td>$instms[$i]</td><td> $prices[$i]</td>
<td>$years[$i]</td></tr>";
}

$html .= "</table><br>";
echo $html;
}
}

class FancyWidget extends Widget {
function __construct() {
}

public function draw() {
$html = "<table border=0 cellpadding=5 width=270>
<tr><td colspan=3 bgcolor=#cccccc>
<b><span>Our Latest Prices</span></b>
</td></tr>
<tr><td><b>instrument</b></td>
<td><b>price</b></td><td><b>date issued</b></td>
</td></tr>";
$numRecords = count($this->internalData[0]);
for($i = 0; $i < $numRecords; $i++) {
    $instrms = $this->internalData[0];
    $prices = $this->internalData[1];
    $years = $this->internalData[2];
    $html .= "<tr><td>$instrms[$i]</td><td>
    $prices[$i]</td><td>$years[$i]
    </td></tr>";
}
$html .= "</table><br>";
echo $html;
}}
?>
```

# 第一部分：专业开发基础

有两个具体的 `Widget` 实现：`FancyWidget` 和 `BasicWidget`。两者都实现了它们所继承的 `abstract` 父类要求的 `draw()` 方法，但实现方式不同。两者还从父类继承了 `update()` 方法。

你可能会想知道使用 `Observer` 接口有什么好处，因为你本来就可以将单一方法放在子类中。早期的 PHP 版本没有直接的方法来确保方法参数是某种类型。PHP 5 中首次出现的名为 `class type hints` 的功能，作为一种保证以参数形式传递正确类型对象的方法。在以下函数声明中，作为参数传递的引用必须是 `Observer` 类型，否则会报错：

```
public function addObserver(Observer $observer) {

```

如果某个特定方法将 `Observer` 作为参数（就像 `Observable addObserver()` 方法的情况一样），你知道将 `Widget` 传递给它是安全的。这是因为所有 `Widget` 对象都是 `Observer` 类型。所有小部件都继承自实现 `Observer` 的 `AbstractWidget`。因此，小部件本身也是该类型。

另一个问题是：为什么不只是要求 `addObserver()` 方法接受 `Widget` ？这样，你也可以摒弃 `Observer` 接口。然而，假设你想创建另一种不是 `Widget` 的 `Observer` 类型。那么类类型提示将阻止你将任何其他类型的对象传递给 `addObserver()` 方法。





## 数据源

DataSource 对象封装了一组乐器的名称、价格和发行日期。它也是可观察对象。Observer 中的关键方法是 addObserver() 和 notifyObserver()。任何需要“观察” DataSource 的 Observer（在此例中，即任何 Widget）都可以使用 addObserver() 将其添加到其中。以下代码构成了 observable.php：

```
<?php
abstract class Observable {
    private $observers = array();
    public function addObserver(Observer $observer) {
        array_push($this->observers, $observer);
    }
    public function notifyObservers() {
        for ($i = 0; $i < count($this->observers); $i++) {
            $widget = $this->observers[$i];
            $widget->update($this);
        }
    }
}
class DataSource extends Observable {
    private $names;
    private $prices;
    private $years;
    function __construct() {
        $this->names = array();
        $this->prices = array();
        $this->years = array();
    }
    public function addRecord($name, $price, $year) {
        array_push($this->names, $name);
        array_push($this->prices, $price);
        array_push($this->years, $year);
        $this->notifyObservers();
    }
    public function getData() {
        return array($this->names, $this->prices, $this->years);
    }
}
?>
```

`addRecord()` 方法允许您将新乐器添加到 `DataSource` 对象的内部存储中。不过要注意，`addRecord()` 方法还多做了一件事：

```
$this->notifyObservers();
```

每当 `DataSource` 对象的内部数据被更改时，它都会通知其所有观察者。观察者是使用前面提到的 `addObserver()` 方法添加的。添加观察者后，它会存储在内部 `$observers` 数组中。当调用 `notifyObservers()` 时，该方法会遍历 `$observers` 数组，并为数组中存储的每个 `Observer` 调用 `update()` 方法。

`update` 方法的唯一参数是 `Observable` 对象本身的副本：

```
$widget->update($this);
```

这样，`Widget`（即 `Observer`）就可以获取 `DataSource`（即 `Observable`）最新状态的副本。请注意，`Widget` 是按值传递的——即 `DataSource` 的副本，而不是实际引用。这样一来，`DataSource` 的内部信息就不会被共享。

## 连接观察者和可观察对象

既然你前面已经完成了所有困难的工作，回报就是一个易于使用且灵活的系统，用于将 `Observer` `Widget` 连接到 `Observable` `DataSource`。请看以下示例，文件名为 `widget.php`：

```
<?php
require_once("observable.php");
require_once("abstract_widget.php");

$dat = new DataSource();
$widgetA = new BasicWidget();
$widgetB = new FancyWidget();

$dat->addObserver($widgetA);
$dat->addObserver($widgetB);

$dat->addRecord("drum", "$12.95", 1955);
$dat->addRecord("guitar", "$13.95", 2003);
$dat->addRecord("banjo", "$100.95", 1945);
$dat->addRecord("piano", "$120.95", 1999);

$widgetA->draw();
$widgetB->draw();

?>
```

你只需创建 `DataSource` 和 `Widget` 对象。然后可以将 `Widget` 对象添加为 `DataSource` 的观察者。现在，你可以随心所欲地向 `DataSource` 对象添加所需数量的记录，而无需担心更新小部件——这一切都会自动完成。最后，当你在小部件上调用 `draw()` 时，它们将使用正确的数据显示自身。

如果你正在设计桌面应用程序，可以在 Observer 的 `update()` 方法中包含一个 `redraw()` 函数。这样一来，你就不需要显式调用 `draw()`，而是让组件在 `DataSource` 更新时自动重绘自身。在纯服务器端 Web 应用程序中，除非重新加载页面，否则无法重绘组件。

观察者模式的另一个酷功能是，你可以定义多个 DataSources。你只需告诉 DataSource 你希望哪个小部件监听它，就可以在不同 DataSources 之间重复使用同一个小部件。图 4-9 显示了运行前面代码的结果。

| 乐器信息 | | |
|---|---|---|
| 鼓 | $12.95 | 1955 |
| 吉他 | $13.95 | 2003 |
| 班卓琴 | $100.95 | 1945 |
| 钢琴 | $120.95 | 1999 |

| 乐器 | 价格 | 发行日期 |
|---|---|---|
| 鼓 | $12.95 | 1955 |
| 吉他 | $13.95 | 2003 |
| 班卓琴 | $100.95 | 1945 |
| 钢琴 | $120.95 | 1999 |

图 4-9：运行 widget.php 的结果

## 注意事项

当你有一个希望连接到不同表示形式的数据源时，观察者模式非常有用。本章的示例使用了一个简单的 DataSource 对象，但你可以创建更复杂的数据源，例如从数据库或 XML 文件中检索数据的数据源。你可以设计一个 Widget，它可以观察 XML DataSource 或数据库 DataSource。只要 DataSource 对象具有相同的接口，它如何检索数据就不重要了。

本示例中的 Widgets 被编码为显示具有三列的表格（如图 4-9 所示），但它们可以更灵活。如果你想发挥创意，可以尝试重新设计它们，以便它们可以显示任意数量的列。你也可以尝试使用一个小帮助对象，而不是使用数组，在 Observable 和 Observer 之间传输信息。

## 装饰器模式

为观察者模式创建的两个具体小部件具有不同的外观。如果你需要添加新样式的小部件，你将子类化 Widget 并实现 draw() 方法以编写 HTML。例如，假设你需要为所有现有小部件添加一个功能，比如边框。你可以进入每个 draw() 方法并向每个方法添加一些更多 HTML，但这样一来边框将被硬编码，所有小部件都将被迫带有边框。或者，你可以创建现有具体小部件的新子类集合，在 draw() 方法中实现边框。如果你只有两个小部件（如 `Observer` 示例中所示），这可能是一个选项——你最终会得到四个小部件。但是，如果你一开始就有五个小部件，这可能看起来就没有那么吸引人了。突然间你要担心很多小部件类。

处理此类情况的另一种方法是，不需要为每个要添加边框的小部件创建新子类：使用装饰器模式可以在不使用继承的情况下向现有对象添加功能或特性。图 4-10 显示了装饰器模式的类图。

![](img/a1b732997d9cb194dceec0570dc79710_103_0.png)

图 4-10：装饰器模式的类图

类图表明 `Decorator` 也是一种 `Widget`。这很好，因为你不想改变访问 `Widget` 的方式，无论它是否被装饰。请看以下 `Decorator`（保存为 `border_decorator.php`）的代码，它在 `Widget` 周围绘制边框：

```
<?php
require_once("abstract_widget.php");

class BorderDecorator extends Widget {
    private $widget;

    function __construct(Widget $widget) {
        $this->widget = $widget;
    }

    public function draw() {
        echo "<table border=0 cellpadding=1 bgcolor=#3366ff>";
        echo "<tr bgcolor=#ffffff><td>";
        $this->widget->draw();
        echo "</td></tr></table>";
    }

    public function update(Observable $subject) {
        $this->widget->update($subject);
    }
}
?>
```

此示例将所有类和接口移到各自的文件中，并使用 `require_once` 导入它们。`draw()` 方法生成一些 HTML 来绘制表格。请注意，在绘制这个边框表格的过程中，`draw()` 方法调用了构造函数中传入的 `Widget` 的 `draw()` 方法。正因为如此，`Widget` 周围会有额外的“装饰”——即边框。以下是使用 `Decorator` 的示例：

```
$widgetA = new BorderDecorator(new BasicWidget());
```

设置装饰器模式后，你只需将其传递一个 `Widget` 对象。然后你可以像使用普通小部件一样使用被装饰的 `Widget`。图 4-11 显示了应用了 `BorderDecorator` 的 `BasicWidget` 对象。

| | 乐器信息 | |
|---|---|---|
| 鼓 | $12.95 | 1955 |
| 吉他 | $13.95 | 2003 |
| 班卓琴 | $100.95 | 1945 |
| 钢琴 | $120.95 | 1999 |

图 4-11：应用了 BorderDecorator 的 BasicWidget





## 实现

为了适配装饰器模式，Widget 对象的实现中有一些小的（但重要的）变化。首先，抽象 Widget 类（abstract_widget.php）中受保护的 InternalData 数组已更改为存储在 $subject 变量中的对 DataSource 对象的私有引用，如下所示：

```php
abstract class Widget implements Observer {
    private $subject;
    abstract public function draw();
    public function update(Observable $subject) {
        $this->subject = $subject;
    }
    public function getSubject() {
        return $this->subject;
    }
}
```

接下来，在每个具体 Widget 类中实现的 draw() 方法期间，Widget 通过调用其继承的 getSubject() 方法来访问其 subject：

```php
public function draw() {
    $data = $this->getSubject()->getData();
    $numRecords = count($data[0]);
    $html = "<table border=1 width=130>";
    $html .= "<tr><td colspan=3 bgcolor=#cccccc>";
    <b>Instrument Info</b></td></tr>";
    for($i = 0; $i < $numRecords; $i++) {
        $instms = $data[0];
        $prices = $data[1];
        $years = $data[2];
        $html .= "<tr><td>$instms[$i]</td><td> $prices[$i]
        </td><td>$years[$i]</td></tr>";
    }
    $html .= "</table>";
    echo $html;
}
```

最后，由于 Decorator 类是实际被指定为 DataSource 对象观察者的类，因此在调用 Decorator 的 update() 方法时，它必须反过来将 DataSource 传递给其 Widget 对象。这样 Widget 对象就可以访问数据：

```php
public function update(Observable $subject) {
    $this->widget->update($subject);
}
```

## 使用装饰器

在开发完装饰器类后，你会发现这是一种非常灵活且强大的模式。它不仅易于使用，而且不同的装饰器可以组合起来，为同一 widget 提供多种效果。装饰器甚至可以按不同顺序应用。下面是另一个装饰器类。将文件另存为 closebox_decorator.php：

```php
<?php require_once("abstract_widget.php");

class CloseBoxDecorator extends Widget {

    private $widget;

    function __construct(Widget $widget) {
        $this->widget = $widget;
    }

    public function draw() {
        print '<table border=0 cellspacing=1 bgcolor="#666666">';
        print '<tr bgcolor=#666666>';
        print '<td align=right>';
        print '<table width=10 height=10 bgcolor="cccccc">';
        print '<tr><td><b>x</b></td></tr>';
        print '</table>';
        print '</td>';
        print '</tr>';
        print '<tr bgcolor=#ffffff>';
        print '<td>';

        $this->widget->draw();

        print '</td>';
        print '</tr>';
        print '</table>';
    }

    public function update(Observable $subject) {
        $this->widget->update($subject);
    }
}
```

前面的装饰器应用了一个带有关闭框的简单菜单栏。将两个 Widget 与两个装饰器组合起来很容易。将以下文件另存为 decorator.php：

```php
<?php
require_once("abstract_widget.php");
require_once("closebox_decorator.php");
require_once("border_decorator.php");
require_once("observable.php");

$dat = new DataSource();
$widgetA = new BasicWidget();
$widgetB = new FancyWidget();
$widgetB = new BorderDecorator($widgetB);
$widgetB = new CloseBoxDecorator($widgetB);

$widgetA = new CloseBoxDecorator($widgetA);
$widgetA = new BorderDecorator($widgetA);

$dat->addObserver($widgetA);
$dat->addObserver($widgetB);

$dat->addRecord("drum", "$12.95", 1955);
$dat->addRecord("guitar", "$13.95", 2003);
$dat->addRecord("banjo", "$100.95", 1945);
$dat->addRecord("piano", "$120.95", 1999);

$widgetB->draw();
echo "<br>";
$widgetA->draw();
?>
```

请注意，第一个 Widget 的装饰器按一种顺序应用，而第二个 Widget 的装饰器按相反顺序应用。图 4-12 显示了此代码的结果。

![](img/a1b732997d9cb194dceec0570dc79710_107_0.png)

图 4-12: decorator.php 代码的结果

## 注意事项

本节中的所有装饰器都有硬编码的颜色值。你完全可以修改它们以使其更灵活。BorderDecorator 类可以更改以允许指定边框宽度和颜色。你可以使用一些 JavaScript 来使 CloseBoxDecorator 在单击关闭框时实际隐藏自身。为了提高代码的可维护性，你可以（并且可能应该）使用模板系统将 HTML 标记与类定义分离。

请记住，装饰器模式不必仅限于纯图形元素。对于 Widgets 来说，装饰器模式生成了额外的 HTML 以更改其外观。你可以改用某种数据结构，并使用 Decorator 向其添加额外信息。例如，如果你有一个 XML 片段，可以使用 Decorator 将其嵌入到更大的 XML 结构中。

## 外观模式

理解外观模式的最佳方法是查看系统在使用外观之前和之后的组件图。

图 4-13 显示了网站前端与 Web 服务器上应用程序的通信。在图的右侧，前端代码正在访问应用程序中的各种对象。在左侧，显示外观，前端仅与外观对象通信，外观对象反过来将职责委托给内部对象。

![](img/a1b732997d9cb194dceec0570dc79710_108_0.png)

图 4-13: 网站前端与 Web 服务器上应用程序的通信

假设你设计了一个小型 Web 应用程序。随着时间的推移，客户不断向其中添加新功能，应用程序中的类数量逐渐增加。你网站上的某些页面开始对各种对象进行大量调用。此类页面可能类似于以下示例：

```php
$dbManager = new DBManager();
$userArray = $dbManager->getNewUsers();
$mailer = new Mailer();
$stats = new StatLog();

for ($i = 0; $i < count($userArray); $i++) {
    $user = $userArray[$i];
    $userPref = $user->getMailPreference();
    $userMail = $user->getEmail();

    if ($userPref == true) {
        $mailer->sendMailToUser($userMail);
    } else {
        $stats->storeUnmailedUser($user->getID());
    }
}
```

上述假设代码将向希望接收邮件的新用户发送电子邮件。如果他们不想接收邮件，其 userID 将被发送到管理用户统计信息的应用程序部分。尽管这段代码并不算太糟糕，但如果你需要混入大量 HTML 并获取信息以向用户报告，它可能会变得难以处理。以下是使用外观模式的另一个版本：

```php
Application::mailNewUsers();
```

现在，只要需要此功能，前端就只需从外观（在此例中为 Application 类）请求即可。来自网站前端的所有消息都经过 Application 类，而永远不会直接与系统中的其他对象交互。Application 对象的方法可以是静态的，因为你甚至不需要 Application 类的实例。

请注意，Application 类的客户端不需要知道其内部工作原理。这（除了代码更整洁之外）的一个好结果是，它使前端表示与后端功能分离。你的应用程序与特定的 HTML 表示绑定得越少，它在其他地方可重用的可能性就越大。第 13 章中对这种良好设计实践有更多讨论。

## 构建者模式

如果回顾组合模式，你会注意到组成组合的对象是手动创建的，如以下示例所示：

```php
$drums = new DrumSet("tama maple set");
$drums->add(new SnareDrum("snare drum"));
$drums->add(new BaseDrum("large bass drum"));
```



```php
$cymbals = new Cymbal("zildjian cymbal set");
$cymbals->add(new Cymbal("small crash"));
$cymbals->add(new Cymbal("large high hat"));
$drums->add($cymbals);
```

创建这个 DrumSet 组合体的代码并不特别复杂，但是如果你需要为许多不同的 Musician 对象创建 Instrument 或 Instrument 组合体对象，而这些 Musician 对象本身又是 Band 对象的组合体，该怎么办呢？

编写创建新对象并添加它们的代码并非不可能，但如果你有几个乐队，每个乐队里有几个音乐家，每个音乐家都有自己的一套乐器，这可能会开始变得乏味。如果你需要根据用户的操作（或许通过 GUI）来创建乐队，那么这可能会开始变得困难——特别是如果你必须为每种类型的乐队（包含所需的音乐家和乐器）进行硬编码的话。

## Implementation

假设你需要创建一个向导，为最终用户生成一个 Band。用户将从风格列表中选择（例如摇滚、乡村、萨尔萨、重金属等等），然后生成的 Band 将被返回，并与其音乐家及其乐器一起组装。图 4-14 展示了建造者模式的类图。

![](img/a1b732997d9cb194dceec0570dc79710_110_0.png)

**图 4-14：建造者模式的类图**

在本示例中，建造者模式创建的 Band 仅包含两种 Musician——吉他手和鼓手：

```php
<?php
interface Builder {
public function buildDrummer();
public function buildGuitarist();
}
?>
```

每次实例化具体构建器类时，它都会创建一个 `Band` 对象。请查看 `RockBandBuilder` 类的以下代码：

```php
<?php
require_once("interface_builder.php");
require_once("class_rockband.php");
require_once("class_musician.php");
require_once("class_instrument.php");

class RockBandBuilder implements Builder {

    private $band;

    function __construct($name) {
        $this->band = new RockBand($name);
    }

    public function getBand() {
        return $this->band;
    }

    public function buildDrummer() {
        $musician = new Musician("rock drummer");
        $drumset = new Instrument("rock drum kit");
        $drumset->add(new Instrument("cymbal"));
        $drumset->add(new Instrument("bass drum"));
        $drumset->add(new Instrument("snare drum"));
        $musician->addInstrument($drumset);
        $this->band->addMusician($musician);
    }

    public function buildGuitarist() {
        $musician = new Musician("rock guitarist");
        $guitar = new Instrument("electric guitar");
        $musician->addInstrument($guitar);
        $this->band->addMusician($musician);
    }
}
?>
```

请注意 `RockBandBuilder` 中构造函数的实现创建了一个 `RockBand`。类似地，`CountryBandBuilder` 的构造函数创建了一个 `CountryBand`，如下所示，位于文件 countryband_builder.php 中：

```php
<?php
require_once("interface_builder.php");
require_once("class_musician.php");
require_once("class_countryband.php");
require_once("class_instrument.php");

class CountryBandBuilder implements Builder {

    private $band;

    function __construct() {
        $this->band = new CountryBand();
    }

    public function getBand() {
        return $this->band;
    }

    public function buildDrummer() {
        $musician = new Musician("washboard player");
        $drument = new Instrument("washboard");
        $musician->addInstrument($drument);
        $this->band->addMusician($musician);
    }

    public function buildGuitarist() {
        $musician = new Musician("country guitarist");
        $guitar = new Instrument("acoustic guitar");
        $musician->addInstrument($guitar);
        $this->band->addMusician($musician);
    }

}
?>
```

查看 RockBandBuilder 中的 buildDrummer() 方法。现在将其与 CountryBandBuilder 中的方法进行比较。请注意，每个方法不仅创建 Musician 对象，还为该音乐家创建乐器。由于 Builder 接口，两个构建器都需要实现 buildDrummer() 和 buildGuitarist() 方法，但它们以完全不同的方式构建 Musician，包括属于该音乐家的 Instrument 对象。

你可能已经注意到，Musician 和 Instrument 类不再被子类化为特定子类型（例如 Guitarist）。这表明构建器可以实现为创建不同的对象（如构造函数中所示），或者使用不同的参数和操作创建相同的对象（如 buildDrummer() 方法中所示）。

## The Director

建造者模式的最后一个重要方面称为导演者（Director）。导演者负责调用构建器的方法来创建最终产品，在此例中该产品是一个 Band 对象。在本示例中，导演者将是 Application 对象，类似于外观模式讨论中描述的对象。Application 类如下所示，位于名为 application.php 的文件中：

```php
<?php

class Application {

    public static function createBand(Builder $builder) {

        $builder->buildGuitarist();
        $builder->buildDrummer();

        return $builder->getBand();
    }
}
?>
```

Application 类具有一个名为 createBand 的方法，它以构建器作为参数。然后 Application 调用传递的构建器对象的创建方法。这里有两点需要注意。首先，Application 决定要调用构建器的哪些方法。其次，它不关心传递给它的是哪种类型的构建器。

最后，以下是如何一起使用 Application（又称导演者）和构建器。只需创建相应构建器对象的实例，并将其传递给 Application 的 createBand 方法：

```php
$builder = new RockBandBuilder();
$band = Application::createBand($builder);
```

Application 对象和构建器协同工作，逐步构建正确的 Band 对象。Band 对象在构建器中进行操作和存储，直到由 getBand 方法请求。

## Considerations

建造者模式对于组装组合体和层级对象结构（例如 Band->Musician->Instrument 结构）非常有用。虽然让构建器返回完成的对象很有用，但不要忘记，构建器返回的 Band 对象仍然与你手动创建的任何 Band 对象相同。这意味着它在构建后仍然可以被修改。

可以修改导演者类以允许不止一种创建方法。在 Application 对象的示例中，你只有一个方法 createBand，但使用相同的构建器调用不同配置的方法是可能的。例如，你可以拥有 createTrio 之类的方法。通过传递不同的构建器对象，相同的方法将组装摇滚三重奏或乡村三重奏。

## Summary

本章演示了五种不同的设计模式：

- 组合模式
- 观察者模式
- 装饰者模式
- 外观模式
- 建造者模式

虽然每种模式处理不同的设计问题，但它们都有一个共同特点。在开发和实现模式的工作完成后，实际使用它的代码非常简单且灵活。模式使开发者和软件设计师能够仅用一个术语就共享复杂的想法。它们也是可重用的想法。相同的设计模式可以在非常不同类型的软件中成为解决方案。通常，你会看到设计模式被融入到语言或框架中——所以如果你了解它们，你就会明白它们应该如何在该语言中工作。

此处介绍的五种模式只是存在的设计模式中很小的一部分。你应该继续自行探索设计模式——它们是认真开发者的绝佳工具。关于设计模式的奠基之作是 Erich Gamma、Richard Helm、Ralph Johnson 和 John M. Vlissides 撰写的 *Design Patterns: Elements of Reusable Object-Oriented Software*（Addison-Wesley，1994 年出版）。该书大部分示例使用 C++ 以及相对晦涩的语言 Smalltalk，但其描述的设计模式适用于任何语言的开发者。该书影响深远——通常被称为“GOF”书，即“四人帮”的简称，指的是四位作者。专业的 PHP 开发者可以从理解设计模式的力量以及在规划任何应用程序架构时从中获得具体示例的益处。

第 5 章将探讨 `Collection` 类，这是本书讨论的一系列实用类中的第一个，你可以将其作为应用程序开发工具包的一部分使用。





## 集合

现在您已经学习了 PHP 中面向对象（OO）应用程序设计的方方面面，您可能会急于立即开始编写应用程序。凭借您新获得的知识，您当然准备好这样做，但您几乎可以肯定会走最长的路才能到达目的地。在途中，您可以采用多种捷径，这些捷径由一系列实用工具和可重用类组成，共同构成一个功能极其强大、易于使用的开发工具包。本书将逐个向您介绍一些有用的工具包组件，并通过实际示例向您展示它们有多有用。您工具包中的第一个类称为 Collection，您将在本章中了解它。

Collection 类是传统数组数据类型的面向对象替代方案。与数组类似，它包含成员变量，但这些变量通常是其他对象，而不是字符串、整数等更简单的数据类型。然后，该类提供简单的方法，使您能够添加成员变量、删除成员变量，并在应用程序中获取它们用于使用。如您在本章中将看到，与使用简单数组存储一系列实例化对象相比，它具有许多优势。

与本书中许多章节一样，在本章中，您不仅会使用该类本身的代码，还将看到它是如何根据将要确定的原始设计要求组装而成的。在过程中，还将讨论使用回调进行延迟实例化等主题，以及如何使用 Collection 类以及未来可以对其进行哪些可能的改进。

## Collection 类的用途

应用程序经常包含一组其他对象的对象。例如，如果您正在为大学教务处构建应用程序，则需要 Student 类和 Course 类。Student 对象可能与多个 Course 对象相关联。构建这一点最明显的方法是将 Course 对象数组作为 Student 对象的成员变量，如下所示：

```
/* student class */
class Student {
    public $courses = array();
    // ... other methods/properties
}
/* using the student class */
$objStudent = new Student(1234); //constructor not shown above
foreach($objStudent->courses as $objCourse) {
    print $objCourse->name;
}
```

当然，如果最明显的方法就是最好的方法，那么本书就不需要这一章了。前一种方法有几个问题：

- 将 Course 对象数组作为公共成员变量暴露出来违反了封装性。没有机会验证对数组的更改，也无法在必要时更改 Student 对象的状态。
- 从这个实现中并不明显课程将如何在数组中索引，以及如何遍历该数组以查找您可能感兴趣的特定 Course 对象。
- 最重要的是，为了确保 courses 数组可供任何可能想要使用 Student 对象的代码访问，您必须在获取学生信息的同时从数据库中拉取所有课程信息。这意味着即使您只想打印学生的姓名，也必须获取有关课程的所有信息，这不必要地增加了数据库服务器的负载并拖慢了整个应用程序。

Collection 类旨在解决所有这些问题。它为数组提供了一个面向对象的包装器，并实现了一种启用延迟实例化的机制。延迟实例化会将集合成员的创建推迟到实际需要时才进行。之所以称为“延迟”，是因为对象会自行决定何时实例化其组件对象，而不是在实例化时创建它们。当您创建 Student 对象时，不应同时创建 Course 对象。只有在您首次尝试访问课程时，才应该创建它们，并且这应该自动发生，而不需要您做任何特殊操作。

Collection 类的功能要求如下：

- 1. 围绕对象数组建立包装器。
- 2. 提供以可预测且明显的方式添加、删除和获取成员对象的方法。
- 3. 使您能够轻松确定集合中存在多少个成员对象。
- 4. 使您能够使用延迟实例化来节省系统资源。

## 设计 Collection 类

在编写任何代码之前，您应确保已仔细规划将要创建的类。根据前一个列表中第 1、2 和 3 项的书面功能要求，您可以建立一个类图，如图 5-1 所示。

| Collection |
|---|
| -成员 |
| +addItem() |
| +removeItem() |
| +getItem() |
| +length() |

图 5-1：类图

为了以“可预测且明显”的方式处理添加、删除和获取成员的操作，必须允许此对象的用户在添加对象时指定有用的键名。键的工作方式就像关联数组中的字符串索引一样，指定集合中将存储成员对象的位置。随后可以使用该键来检索或删除对象。沿用前面的教务处应用程序示例，每个课程的键可能是课程代码（例如，入门计算机科学课程的 CS101）。在某些情况下，您没有可使用的有意义的键值。在这种情况下，集合应该能够自行确定有效键。图 5-2 显示了更新后的 UML 图。

| Collection |
|---|
| -成员 |
| +addItem(obj:mixed, key:String=null) |
| +removeItem(key:String) |
| +getItem(key:String) |
| +length() |

图 5-2：更新后的 UML 图

addItem() 的 obj 参数是要添加到集合的项目。此项目通常是对象，但可以是任何有效的数据类型。addItem()、removeItem() 和 getItem() 的 key 参数是一个字符串（在 addItem() 中为可选），表示键。

本章稍后，在建立操作集合内容的基本代码后，您将参考此图来了解延迟实例化代码的工作方式。最后需要注意的一点是，length() 仅返回集合中当前的项目数。

## Collection 类基础

根据图 5-2 中的 UML 图，`Collection` 类的骨架如下：

```php
<?php
class Collection {
    private $_members = array();

    public function addItem($obj, $key = null) {
    }

    public function removeItem($key) {
    }

    public function getItem($key) {
    }

    public function length() {
    }
}
?>
```

本章稍后的讨论将假设代码位于名为 `class.Collection.php` 的文件中。`$_members` 变量提供了一个位置，用于存储集合的成员对象。`addItem()` 使您能够向集合添加新对象。`removeItem()` 删除对象。`getItem()` 返回对象，而 `length()` 返回集合中的项目数。`Collection` 类不需要构造函数。

## addItem 方法

向集合添加新对象时，该对象将插入到 `$_members` 数组中 `$key` 指定的位置。如果未提供键，您将允许 PHP 自行选择一个。如果尝试使用已存在的键将对象添加到集合中，则应抛出异常以防止意外覆盖信息：

```php
class Collection {
    private $_members = array();

    public function addItem($obj, $key = null) {
        if ($key) {
            //Throw exception if this key is already in use.
            if (isset($this->_members[$key])) {
                throw new KeyInUseException("Key \"$key\" already in use!");
            } else {
                $this->_members[$key] = $obj;
            }
        }
    }
}
```


} else {
        $this->_members[] = $obj;
        }
    }
}
```

与本书中使用的大多数 Exception 子类一样，KeyInUseException 没有方法体，而是继承了 PHP 6 自带的默认 Exception 类的所有内容：

```
class KeyInUseException extends Exception
```

KeyInUseException 类提供了一种机制，让对象的使用者知道他们是否可能通过多次指定同一个键来覆盖信息。键的值被用作 $_members 数组中的索引。如果未指定键，PHP 会为该元素选择一个数字索引。无论哪种情况，对象都会被插入到数组的该位置。

Collection 的子类可以使用类型提示重写 addItem() 方法，以确保添加的项目是所需集合的正确类型。以下是一个示例：

```
<?php
class CourseCollection extends Collection {
public function addItem(Course $obj, $key = null) {
parent::addItem($obj, $key);
}
}
?>
```

使用此技术，只需很少的代码，就可以创建强制执行集合成员数据类型的子类。

## removeItem 和 getItem 方法

removeItem() 和 getItem() 方法接受一个键作为参数，指示正在删除或获取的项目。如果提供了无效键，应抛出异常：

```
public function removeItem($key) {
if(isset($this->_members[$key])) {
unset($this->_members[$key]);
} else {
throw new KeyInvalidException("Invalid key \"$key\"!");
}
}
public function getItem($key) {
if(isset($this->_members[$key])) {
return $this->_members[$key];
} else {
throw new KeyInvalidException("Invalid key \"$key\"!");
}
}
```

KeyInvalidException 类与 KeyInUseException 类一样简单：

```
class KeyInvalidException extends Exception { }
```

## 其他方法

由于 addItem() 方法的 $key 参数是可选的，你不一定知道集合中每个项目使用的键。名为 keys() 的函数允许你将这些键的列表提供给可能需要它们的任何外部代码。键将作为数组返回：

```
public function keys() {
    return array_keys($this->_members);
}
```

你可能想知道集合中有多少个项目。PHP 的 sizeof 函数返回数组中的元素数量，因此你将使用它来实现 length() 方法：

```
public function length() {
    return sizeof($this->_members);
}
```

因为 getItem() 在传递无效键时会抛出异常，你需要一种方法来确定给定键是否存在于集合中。exists() 方法允许你在调用 getItem() 之前进行检查：

```
public function exists($key) {
    return (isset($this->_members[$key]));
}
```

这种方法允许你使用 try ... catch 块来捕获无效键，或者在调用 getItem() 之前调用 exists() 方法，具体取决于哪种方法更方便。

现在你已经将所有基本方法添加到类中，可以继续了解 Collection 类的使用方法了。

## 使用 Collection 类

要按当前状态使用 Collection 类，请创建一个名为 class.Collection.php 的文件，并将 Collection 类的代码保存其中。为 KeyInvalidException 和 KeyInUseException 类创建文件。请务必将 require_once 语句添加到 class.Collection.php 的顶部，以引入这些异常类。将以下代码保存到 testCollection.php 中：

```
<?php
require_once('class.Collection.php');

/* a silly class for testing */
class Foo {
    private $_name;
    private $_number;
    public function __construct($name, $number) {
        $this->name = $name;
        $this->number = $number;
    }
    public function __toString() {
        return $this->name . ' is number ' . $this->number;
    }
}

$colFoo = new Collection();
$colFoo->addItem(new Foo("Steve", 14), "steve");
$colFoo->addItem(new Foo("Ed", 37), "ed");
$colFoo->addItem(new Foo("Bob", 49));

$objSteve = $colFoo->getItem("steve");

print $objSteve; //prints "Steve is number 14"
$colFoo->removeItem("steve"); //deletes the 'steve' object

try {
    $colFoo->getItem("steve"); //throws KeyInvalidException
} catch (KeyInvalidException $kie) {
    print "The collection doesn't contain anything called 'steve'";
}

?>
```

这个示例目前可能并不特别有趣，但它应该能让你了解 Collection 类的使用方法。下一节将讨论如何处理延迟实例化，这是该类的主要优势之一。

## 实现延迟实例化

请回顾，延迟实例化是指 Collection 类推迟创建其成员直到需要时才创建的能力。在本章开头讨论的注册系统应用程序中，一个 Student 对象与多个 Course 对象相关联。当你想要使用 Student 对象来显示学生姓名时，你不需要该学生课程的任何信息。但是，为了保持一致的接口，Course 对象应作为 Student 对象的成员变量可用。

为了在显示给定学生的课程列表时保持简单，软件接口应该允许你编写如下代码：

```
<?php

$objStudent = StudentFactory::getStudent(12345); //12345 is the student ID
print "Name: " . $objStudent->name . "<br>\n";
print "Courses: <br>\n";
foreach($objStudent->courses as $objCourse) {
    print $objCourse->coursecode . " - " . $objCourse->name . "<br>\n";
}

?>
```

目前，只需要知道 `StudentFactory` 是一个带有静态方法 `getStudent` 的类，该方法根据给定的 ID 返回一个新的学生对象。它在数据库中完成所有繁重的工作。
你可以假设 `Student` 类构造函数负责填充课程列表；但是，如果你只是按姓名列出学生（如下一个示例所示），就不应该承担获取不需要的课程的开销。再次假设 `StudentFactory` 是一个为你查询数据库的类，用于创建 `Student` 对象。在这种情况下，你可以通过按姓氏搜索来检索学生集合：

```
<?php

$colStudents = StudentFactory::getByLastName("Smith");
print "<h1>Students With the Last Name 'Smith'</h1>";
foreach($colStudents as $objStudent) {
    print $objStudent->name . "<br>\n";
}
?>
```

在这种情况下，获取课程信息将完全没必要，因为你只是显示姓名，但你如何在不强制进行数据库活动的情况下保持 `Student` 类的简单接口？

你可以添加诸如 `$objStudent->loadCourses()` 之类的方法，该方法会填充集合，并且必须在与 `courses` 集合交互之前调用，但这不够直观，并且会使接口变得杂乱。你可以采用以下方式：

```
CourseFactory::getCoursesForStudent($objStudent)
```

这将返回给定学生的一组课程，但同样，刚加入你开发团队的人可能不明显意识到必须调用这样的函数才能获取给定学生的 `Course` 对象。

有一种更好的方法，它涉及使用回调。

## 回调

如果你曾经做过任何 JavaScript 编程，并为某个对象的 `onclick` 事件分配了一些活动，那么你已经使用了回调。_回调_是一种巧妙的编程技巧，你告诉应用程序在发生某个事件时执行一个函数。该事件不在你的控制之中——你不一定知道它何时会发生。你告诉应用程序在该事件发生时（如果发生）处理执行该函数。

在 JavaScript 中，许多时候会为表单创建一个 `onSubmit` 事件处理程序，以便在用户尝试提交该表单时进行客户端数据验证。你不知道用户何时会提交表单，甚至用户是否会提交。在指定事件处理程序后，JavaScript 引擎会处理其余事宜。你也可以在服务器端应用程序开发中使用此技术。



当你为教务处应用程序设计 `Student` 类时，你不知道使用该类的代码何时或是否会访问 `course` 集合。因为获取 `Course` 对象伴随着相当大的开销，这是利用回调的好时机。你需要能够告诉 `course` 集合：“如果有人试图与你通信，你需要先填充你自己。”

然而，因为 `Collection` 类是可复用工具包中的通用成员，你不希望在类中硬编码函数名称（这显然限制了类的可复用性），并且你不希望每次使用它时都要创建 `Collection` 的新子类（因为这是在给你增加工作，而不是减少工作）。相反，你应该能够提供过程式函数的名称，或提供对对象的引用并指定要调用的对象上的方法来填充集合。要做到这一点，你需要了解一个特殊的内置 PHP 函数。

## 使用 call_user_func

当你想要调用函数时，通常会调用函数的字面名称。但是，PHP 还允许你使用字符串变量来调用函数（以及对象上的方法）。以下是完全合法的 PHP 代码：

```php
<?php
$myFunc = "pow";
print $myFunc(4, 2); //prints 16, or pow(4, 2)
?>
```

PHP 会计算变量名并执行该名称的函数。这对编译好的核心函数和用户定义的函数都适用。你可以对对象的方法使用同样的技巧，如下所示：

```php
<?php
$myMethod = 'sayHello';
$obj = new Person();
$obj->$myMethod();
?>
```

假设你有一个名为 `Person` 的类，其中有一个名为 `sayHello()` 的方法，这将可以正常工作。（你也可以用这种方式调用静态方法，即 `Person::$myMethod()`。）

这种技巧唯一的问题是，并不明显 `$obj->$myMethod()` 正在调用 `$obj->sayHello()`。如果 `$myMethod` 的值作为参数传递给某个包装函数，这会更加令人困惑。PHP 提供了一个内置方法来做同样的事情，方式不那么令人困惑且更加透明。

函数 `call_user_func()` 接受一个必需参数来定义要调用的函数，以及零个或多个附加参数，这些参数将作为参数传递给用户定义的函数。函数定义如下：

```
mixed call_user_func ( callback function [, mixed parameter [, mixed ...]])
```

`callback` 函数参数的值有以下三种形式之一：

- `string $functionName` — 对应要调用的过程式函数名称的字符串
- `array(object $object, string $functionName)` — 由一个已实例化的对象和一个字符串组成的数组，该字符串对应要在该对象上调用的方法名称
- `array(string $className, string $functionName)` — 由一个类名和一个字符串组成的数组，该字符串对应该类的 `static` 方法名称

以下是使用此函数的一些示例：

```php
<?php

class Bar {

private $_foo;

public function __construct($fooVal) {
$this->_foo = $fooVal;
}

public function printFoo() {
print $this->_foo;
}

public static function sayHello($name) {
print "Hello there, $name!";
}

}

//procedural function - not part of the Bar class
function printCount($start, $end) {
for($x = $start; $x <= $end; $x++) {
print "$x ";
}
}

/* ex. 1 */
/*prints 1 2 3 4 5 6 7 8 9 10 */
call_user_func('printCount', 1, 10);

/* ex. 2 */
/*calls $objBar->printFoo() */
$objBar = new Bar('elephant');
call_user_func(array($objBar, 'printFoo'));

/* ex. 3 */
/*calls Bar::sayHello('Steve') */
call_user_func(array('Bar', 'sayHello'), 'Steve');

/* ex. 4 */
//This throws a fatal error "Using $this when not
//in object context" because the function call
//is Bar::printFoo, which is not a static method
call_user_func(array('Bar', 'printFoo'));
?>
```

第一个调用 `call_user_func` 的示例很简单直接。你将过程式函数的名称作为字符串传递，并提供它所期望的两个参数。

在第二个示例中，你将一个数组作为第一个参数传递。因为该数组的第一个元素是一个对象，所以在该对象上调用方法 `printFoo()`。

在第三个和第四个示例中，数组的第一个元素是一个字符串。因此，PHP 尝试在指定的类上静态调用该方法。如果该方法不存在，或依赖于非静态类变量（即 `$this`），那么你将遇到致命的运行时错误。当你尝试静态调用 `printFoo()` 时，最后一行就是这种情况。

术语提醒：静态方法是不依赖于非静态类成员变量且无需先实例化该类的对象即可调用的方法。调用语法是 `ClassName::methodName()`。关键字 `$this` 对静态调用的方法不可用。

## 实现回调

你可以使用 `call_user_func` 在你的类中创建一个回调。通过创建一个允许与 `call_user_func` 相同类型参数的方法，你可以允许类外部的代码指定在类中发生某些事件时要调用的函数或方法。

要在你的类中创建一个回调，请执行以下步骤：

- 1. 确定你的类将引发哪些事件。
- 2. 对于每个事件，创建一个 `on[EventName]` 方法，该方法接受两个参数：
  - 函数的名称
  - 可选，一个对象（已实例化的对象变量）或类名（字符串）
- 3. 对于每个事件，在你的类中创建一个私有成员变量，以将这些参数存储为字符串（如果未提供对象或类名），或存储为数组（如果第二个参数有值）。
- 4. 在类中应触发这些回调的每个点上，查询第 3 步中创建的私有成员变量，看它是否已设置。如果是，则调用 `call_user_func()`，并传入该变量的值。

以下示例展示了如何在名为 `Dog` 的类中创建一个 `onspeak()` 事件。创建一个名为 `onspeak()` 的函数，它接受一个字符串形式的函数名称以及可选的对象或类名。构建应传递给 `call_user_func()` 的字符串或数组，并测试该值以确保其可调用。如果是，则将该值存储在私有成员变量中以供后续使用。查看 `bark()` 方法以了解该值是如何使用的：

```php
<?php
class Dog {
    private $_onspeak;

    public function __construct($name) {
        $this->_name = $name;
    }

    public function bark() {
        if(isset($this->_onspeak)) {
            if(! call_user_func($this->_onspeak)) {
                return false;
            }
        }

        print "Woof, woof!";
    }

    public function onspeak($functionName, $objOrClass = null) {
        if($objOrClass) {
            $callback = array($objOrClass, $functionName);
        } else {
            $callback = $functionName;
        }

        //make sure this stuff is valid
        if(!is_callable($callback, false, $callableName)) {
            throw new Exception("$callableName is not callable " .
                "as a parameter to onspeak");
            return false;
        }

        $this->_onspeak = $callback;
    }
} //end class Dog

//procedural function
function isEveryoneAwake() {
    if(time() < strtotime("today 8:30am") ||
        time() > strtotime("today 10:30pm")) {
        return false;
    } else {
        return true;
    }
}

$objDog = new Dog('Fido');
$objDog->onspeak('isEveryoneAwake');

$objDog->bark(); //polite dog

$objDog2 = new Dog('Cujo');
$objDog2->bark(); //always barks!

//Throws exception when onspeak is called.
$objDog3 = new Dog('Lassie');
$objDog3->onspeak('nonExistentFunction', 'NonExistentClass');
$objDog3->bark();
?>
```

isEveryoneAwake() 函数会检查当前时间是否在上午 8:30 到晚上 10:30 之间。如果是，则返回 true，允许狗狗叫。如果不是，则返回 false，使狗狗保持安静。（如果现实中的狗狗也能用回调来编程就好了。）此方法仅对 $objDog 有效，因为 $objDog2 未设置回调。

注意在 onspeak() 中使用 is_callable() 函数。这也是一个内置的 PHP 函数，就像 call_user_func() 一样。它基本上是对传递给 onspeak() 方法的参数进行的一种健全性检查。当你向 $objDog3->onspeak() 传递参数时，不存在的函数和类会导致抛出异常。

## Collection 类中的 setLoadCallback 方法

既然你已经了解了回调的工作原理，你需要了解如何在 Collection 类中使用它们来赋予该类的一项更重要的优势——懒加载实例化。

考虑教务处应用程序中的 Student 类。你希望能够保留本章开头看到的非常简单的接口，其中课程是 Student 对象的一个成员变量，但你不应该在每次获取 Student 对象时都承受获取课程列表的开销。相反，你需要在 Collection 类上启用一个回调，以便在允许任何外部代码与其交互之前先调用某个函数。

对 addItem()、getItem()、length()、exists() 和 keys() 的每次调用都应首先确保集合已加载，如果未加载，则调用可能指定的任何回调函数。回调中指定的函数负责填充集合。你还需要某种标志来指示回调是否已被调用。该标志将防止不必要的重复尝试加载已加载的集合，因为这可能会对性能产生不利影响。

以下代码显示了完整的 Collection 类，其中包含实现该类懒加载实例化功能所需的修改（已高亮显示）：

```php
<?php
class Collection {

private $_members = array(); //collection members
private $_onload; //holder for callback function
private $_isLoaded = false; //flag that indicates whether the callback
//has been invoked




```php
public function addItem($obj, $key = null) {
    $this->_checkCallback(); //_checkCallback is defined a little later
    if($key) {
        //Throw exception if this key is already in use.
        if(isset($this->_members[$key])) {
            throw new KeyInUseException("Key \"$key\" already in use!");
        } else {
            $this->_members[$key] = $obj;
        }
    } else {
        $this->_members[] = $obj;
    }
}
```

```php
public function removeItem($key) {
    $this->_checkCallback();
    if(isset($this->_members[$key])) {
        unset($this->_members[$key]);
    } else {
        throw new KeyInvalidException("Invalid key \"$key\"!");
    }
}
```

```php
public function getItem($key) {
    $this->_checkCallback();
    if(isset($this->_members[$key])) {
        return $this->_members[$key];
    } else {
        throw new KeyInvalidException("Invalid key \"$key\"!");
    }
}
```

```php
public function keys() {
    $this->_checkCallback();
    return array_keys($this->_members);
}
```

```php
public function length() {
    $this->_checkCallback();
    return sizeof($this->_members);
}

public function exists($key) {
    $this->_checkCallback();
    return (isset($this->_members[$key]));
}
```

/**
 * Use this method to define a function to be
 * invoked prior to accessing the collection.
 * The function should take a collection as a
 * its sole parameter.
 */
public function setLoadCallback($functionName, $objOrClass = null) {
    if($objOrClass) {
        $callback = array($objOrClass, $functionName);
    } else {
        $callback = $functionName;
    }

    //make sure the function/method is valid
    if(!is_callable($callback, false, $callableName)) {
        throw new Exception("$callableName is not callable " .
        "as a parameter to onload");
        return false;
    }
    $this->_onload = $callback;
}

/**
 * Check to see if a callback has been defined and if so,
 * whether or not it has already been called. If not,
 * invoke the callback function.
 */
private function _checkCallback() {
    if(isset($this->_onload) && !$this->_isLoaded) {
        $this->_isLoaded = true;
        call_user_func($this->_onload, $this);
    }
}
?>

setLoadCallback() 函数允许你提供一个函数的名称，以及可选的类名或对象变量名，这些将被调用以填充此集合。如果向集合提供了回调，则 $_onload 私有成员变量将填充为要传递给 call_user_func 的字符串或数组。请注意，就像之前使用 Dog 类的示例中一样，这里有一些健全性检查，以确保回调是可调用的。

`Collection` 类的所有其他方法在函数声明的第一行都添加了 `$this->_checkCallback()` 这一行。添加此行会强制集合检查是否存在尚未调用的回调，并会导致调用该函数。在调用回调函数之前，你会设置一个标志以确保仅调用该函数一次。请注意对 `$this->_isLoaded` 的检查。任何用作 `Collection` 类加载回调的函数都应期望恰好一个参数，其类型为 `Collection`。对当前集合（使用 `$this` 变量）的引用通过以下行传递给回调函数：

```
call_user_func($this->_onload, $this)
```

这使得回调函数能够直接操作导致调用该函数的集合对象。以下示例展示了在实际情况中这是如何工作的。

创建一个名为 `NightClub` 的类。这个类具有一个 `name` 属性和一组 `Singer` 对象。有时你只需显示俱乐部的名称。有时你希望对歌手集合做些什么。因此，你使用集合对象的 `setLoadCallback()` 方法，以确保不会执行任何不必要的代码。

以下是 `NightClub` 和 `Singer` 类。将文件命名为 `club_singer.php`：

```php
<?php
require_once("class.Collection.php");

class Singer {
public $name;

public function __construct($name) {
$this->name = $name;
}
}

class NightClub {
public $name;
public $singers;

public function __construct($name) {
$this->name = $name;
$this->singers = new Collection();
$this->singers->setLoadCallback('loadSingers', $this);
}

public function loadSingers(Collection $col) {
print "We're loading the singers!<br>\n";
// these would normally come from a database
$col->addItem(new Singer('Frank Sinatra'));
$col->addItem(new Singer('Dean Martin'));
$col->addItem(new Singer('Sammy Davis, Jr.'));
}
}
?>
```

请注意 loadSingers() 方法中的 print 语句。将此放在这里仅用于演示目的。运行以下代码（如果希望，可以将其添加到前面代码的底部），你会看到 print 语句不会出现在屏幕上：

```php
<?php
$objNightClub = new NightClub('The Sands');
print "Welcome to " . $objNightClub->name . ".<br>\n";
?>
```

现在再试一次，这次对 $singers 集合执行一些操作：

```php
<?php
$objNightClub = new NightClub('The Sands');
print "Welcome to " . $objNightClub->name . ".<br>\n";
print "We have " . $objNightClub->singers->length() . " singers " .
       "for your listening pleasure this evening.";
?>
```

运行此代码应该产生以下输出：

```
Welcome to The Sands.
(We're loading the singers!)
We have 3 singers for your listening pleasure this evening.
```

正如你所见，这使得使用歌手集合变得极其简单。如果你创建 NightClub 类，可以将该类交给软件开发团队中资历较浅的成员，他们可以使用该类来显示示例中所示的屏幕输出，而无需了解集合是如何或何时加载的。此外，你还能确保应用程序不会占用比绝对必要更多的系统资源。

下一节将回到注册办公室的示例，并展示如何将所有这些应用于实际应用程序中。

### 使用 Collection 类

如前所述，本章中注册办公室应用程序涉及一个名为 Student 的类，其中包含一组 Course 对象。这两个类都很简单。UML 类图如图 5-3 所示。

![](img/a1b732997d9cb194dceec0570dc79710_131_0.png)

图 5-3：UML 类图

# 第一部分：专业开发基础

当然，`Course` 类也应该有一个 `students` 集合，但代码会非常相似，因此在你了解如何为 `Student` 类实现 `courses` 集合后，可以更新 UML 图并添加必要的代码，以支持 `Course` 类上的 `students` 集合。

对于 `Collection` 类，我们将使用与之前 `NightClub` 对象示例中完全相同的代码，因此如果你已经创建了该类，则无需做任何更改。如果你尚未创建包含该类的文件并想亲自尝试该示例，请立即创建。

从图 5-3 所示的 UML 图中可以看出，`Course` 类非常简单，只包含名称、课程代码和 ID。课程代码是课程标识符，例如入门计算机科学课程的 CS101。名称是课程的全称。ID 是数据库中的数字主键。在实际应用程序中，你可能希望能够访问先决条件列表（另一个集合）、课程大纲、讲师信息等等。同样，这些留作你自己完成的练习。

查看代码：

```php
<?php
class Course {
    private $_id;
    private $_courseCode;
    private $_name;

    function __construct($id, $courseCode, $name) {
        $this->_id = $id;
        $this->_courseCode = $courseCode;
        $this->_name = $name;
    }

    public function getName() {
        return $this->_name;
    }

    public function getID() {
        return $this->_id;
    }

    public function getCourseCode() {
        return $this->_courseCode;
    }

    public function __toString() {
        return $this->_name;
    }
}
?>
```

根据类图，课程有两个属性：`$id` 和 `$name`。由于应用程序的这一部分不应允许修改类的名称或 ID，因此使用私有成员变量来存储这些值，并通过 `getID()` 和 `getName()` 方法检索它们。当你构建允许修改这些值的应用程序部分（课程管理工具）时，


你可以添加 setID() 和 setName() 方法。这些方法可能应该利用某种安全机制，以确保没有未经授权的个人修改课程的属性。

这段代码还包含一个 __toString() 方法。这种“魔术”方法可以由 PHP 6 中的任何对象定义。它使你能够编写如下代码：

```php
print "This course is called " . $objCourse . "<br>";
```

$objCourse 显然不是字符串，但由于定义了特殊的 __toString() 方法，当 PHP 尝试将变量从对象强制转换为字符串时，将使用该方法的返回值。

由于课程集合应该始终仅由 Course 对象组成，请创建一个名为 CourseCollection 的 Collection 子类。重写 addItem() 方法以包含类型提示，这样只有 Course 对象才能添加到集合中：

```php
<?php
require_once('class.Collection.php');

class CourseCollection extends Collection {
public function addItem(Course $obj, $key = null) {
parent::addItem($obj, $key);
}
}
?>
```

这使得 PHP 可以进行一些类型检查，以确保课程集合中的所有内容都正是你所期望的——一个 Course 对象。

Student 类具有 $id 和 $name 属性，分别表示该学生的唯一标识符和名称。它还必须有一个名为 $courses 的属性，这是学生当前注册的课程集合：

```php
<?php
class Student {
private $_id;
private $_name;

public $courses;

public function __construct($id, $name) {
$this->_id = $id;
$this->_name = $name;

$this->courses = new CourseCollection();
$this->courses->setLoadCallback('_loadCourses', $this);
}

public function getName() {
return $this->_name;
}

public function getID() {
    return $this->_id;
}

private function _loadCourses(Collection $col) {
    $arCourses = StudentFactory::getCoursesForStudent($this->_id, $col);
}

public function __toString() {
    return $this->_name;
}
}
?>
```

与 Course 类一样，将 $id 和 $name 属性实现为私有成员变量，并提供 getID() 和 getName() 函数。暂时将 $courses 成员保留为公共成员变量。请注意，此类还创建了 __toString() 方法。这使得显示任何对象（在这里是学生姓名）的最常见字符串表示变得更容易一些。

在构造函数中，调用 setLoadCallback() 并传入加载方法 __loadCourses() 的名称以及该方法所在对象的引用（即 $this）。

_loadCourses() 方法以 Collection 作为其唯一参数（如 setLoadCallback() 函数所要求），并使用 StudentFactory 类（下文将讨论）的静态方法。该方法需要学生 ID，并传入一个 Collection 对象以加载课程。

StudentFactory 类包含两个静态方法，用于完成加载数据库中学生和课程信息的所有工作。对于此应用程序，必须在数据库中创建三个表：student、course 和 studentcourse。前两个表的用途应该很明显——用于存储学生和课程的基本信息。第三个表有两个字段：studentid 和 courseid。它在学生和课程之间建立关联。

以下 SQL 语句适用于 PostgreSQL（本书示例的首选数据库服务器）；但只需稍作修改，也可以在大多数 RDBMS 中工作：

```sql
CREATE TABLE "student" (
    "studentid" SERIAL NOT NULL PRIMARY KEY,
    "name" varchar(255)
);

CREATE TABLE "course" (
    "courseid" SERIAL NOT NULL PRIMARY KEY,
    "coursecode" varchar(10),
    "name" varchar(255)
);

CREATE TABLE "studentcourse" (
    "studentid" integer,
    "courseid" integer,
    CONSTRAINT "fk_studentcourse_studentid"
    FOREIGN KEY ("studentid") REFERENCES "student"("studentid"),
    CONSTRAINT "fk_studentcourse_courseid"
    FOREIGN KEY ("courseid")
    REFERENCES "course"("courseid")
);

CREATE UNIQUE INDEX "idx_studentcourse_unique" ON
"studentcourse"("studentid", "courseid");
```

请确保创建了外键，并且不要忽略 studentcourse 表的唯一约束。学生不应能够为同一课程注册两次，该约束在数据库级别强制执行此事实。

向每个表中插入一些示例数据。以下类似的语句应该足以用于此练习：

```sql
INSERT INTO "student"(name) VALUES('Bob Smith'); -- studentid 1
INSERT INTO "student"(name) VALUES('John Doe'); -- studentid 2
INSERT INTO "student"(name) VALUES('Jane Baker'); -- studentid 3

INSERT INTO "course"("coursecode", "name")
VALUES('CS101', 'Intro to Computer Science'); -- courseid 1
INSERT INTO "course"("coursecode", "name")
VALUES('HIST369', 'British History 1945-1990'); -- courseid 2
INSERT INTO "course"("coursecode", "name")
VALUES('BIOS546', 'Advanced Genetics'); -- courseid 3

INSERT INTO "studentcourse"("studentid", "courseid") VALUES(1, 1);
INSERT INTO "studentcourse"("studentid", "courseid") VALUES(1, 2);
INSERT INTO "studentcourse"("studentid", "courseid") VALUES(1, 3);
INSERT INTO "studentcourse"("studentid", "courseid") VALUES(2, 1);
INSERT INTO "studentcourse"("studentid", "courseid") VALUES(2, 3);
INSERT INTO "studentcourse"("studentid", "courseid") VALUES(3, 2);
```

最后六条语句应根据 student 和 course 表插入语句生成的 studentid 和 courseid 值进行调整。

在创建数据库表并填充示例数据后，你可以编写和测试 StudentFactory 类。该类有两个静态方法：getStudent() 和 getCoursesForStudent()。前者负责在给定学生 ID 时创建 Student 对象。后者为给定学生填充课程集合。

以下代码没有演示任何特定数据库函数的使用，因此一些伪代码用于替代对实际数据库函数的调用。第 6 章将向你展示如何使用 PHP 数据对象（PDO）数据库抽象函数。目前，你可以随意用 pg_connect、pg_query 等显式调用（或适用于你的数据库类型的相应 PHP 函数）替换：

```php
<?php
class StudentFactory {
    public static function getStudent($id) {
        $sql = "SELECT * from "student" WHERE "studentid" = $id";
        $data = $db->select($sql); //pseudo code. Assume it returns an
        //array containing all rows returned
        //by the query.

        if(is_array($data) && sizeof($data)) {
            return new Student($data[0]['studentid'], $data[0]['name']);
        } else {
            throw new Exception("Student $id does not exist.");
        }
    }

    public static function getCoursesForStudent($id, $col) {
        $sql = "SELECT "course"."courseid",
        "course"."coursecode",
        "course"."name"
        FROM "course", "studentcourse" WHERE
        "course"."id" =
        "studentcourse"."courseid" AND
        "studentcourse"."studentid" = $id";

        $data = $db->select($sql); //same pseudo code in getStudent()

        if(is_array($data) && sizeof($data)) {
            foreach($data as $datum) {
                $objCourse = new Course($datum['courseid'], $datum['coursecode'],
                $datum['name']);
                $col->addItem($objCourse, $objCourse->getCourseCode());
            }
        }
    }
}
?>
```

getStudent() 方法返回填充了相应数据的新 Student 对象。如果数据库中不存在具有该 ID 的学生，则会抛出异常。所有对 StudentFactory::getStudent() 的调用都应包装在 try...catch 语句中。

getCoursesForStudent() 方法从 _loadCourses() 中接收 $courses 集合。数据库查询从 course 表中选择所有数据，使用隐式连接到 studentcourse 表以获取与指定学生关联的课程。

根据从数据库返回的数据（如果有），将新的 Course 对象添加到集合中。请注意，在将 Course 添加到课程集合时，你使用 coursecode 值作为键。




由于 PHP 6 中所有对象均按引用传递，您可以在 `getCoursesForStudent()` 内更改集合的内容，并在 `Student` 对象的 `$courses` 变量中看到这些变化生效。如果“按引用传递”这个短语对您来说不太熟悉，请参见第 4 章中关于按值传递与按引用传递函数参数之间差异的讨论。

要最终将所有这些好东西派上用场，请尝试以下代码：

```php
<?php
$studentID = 1; //use a valid studentID value from your student table
try {
    $objStudent = StudentFactory::getStudent($studentID);
} catch (Exception $e) {
    die("Student #$studentID doesn't exist in the database!");
}

print $objStudent . ($objStudent->courses->exists('CS101') ? ' is ' : ' is not ') .
    'currently enrolled in CS101';
//displays: "Bob Smith is enrolled in CS101"
?>
```

在已部署的应用程序中，如果找不到指定的学生，您应该采取比突然终止应用程序更优雅的做法，但这能让您明白为什么必须使用 `try...catch` 语句。

获取 `$objStudent` 后，这段代码会显示一条简单消息，告知该学生是否已注册 CS101。调用 `exists()` 方法后，`courses` 集合会从数据库中填充，这要归功于 `StudentFactory`。由于添加 `Course` 对象到集合时使用了课程代码作为键，您可以将课程代码（`'CS101'`）作为参数传递给 `exists()`。

## 改进集合类

您可能在想，`Collection` 类还能如何改进。它如何能更强大、更有用或更有趣呢？问题是，您目前还没有一种简单的方法来遍历整个集合（例如显示课程列表）。现在，您只能直接跳转到那些您已知在集合中的项目。显然，在开始使用集合之前，您并不总是知道集合的内容是什么，因此您需要一种方法来编写如下代码：

```php
<?php
$objStudent = StudentFactory::getStudent(1);
foreach ($objStudent->courses as $objCourse) {
    print $objStudent . ' is currently enrolled in ' . $objCourse . "<br>\n";
}
?>
```

如果您现在尝试运行这段代码，要么会得到一个错误，要么看不到任何内容（取决于 `error_reporting` 级别），因为 `$objStudent->courses` 不是数组（它是一个 `Collection`）。在 PHP 4 中，可用作 `foreach` 语句操作数的唯一数据类型是数组。随着 PHP 5 的发布（并在 PHP 6 中继续沿用），您有了两个新的内置接口，`Iterator` 和 `IteratorAggregate`，它们使您能够在对象上使用 `foreach`，前提是这些对象实现了这些接口。

## 总结

`Collection` 类是传统数组的一种非常有用的面向对象替代方案，您可以在几乎要构建的任何应用程序中有效地使用它。它提供了对其成员的精心管理以及一致的 API，这使得编写使用该类的代码变得容易。

对 `Collection` 进行子类化并重写 `addItem()` 方法以在第一个参数中包含类型提示，可让您控制添加到集合中的对象类型。虽然这并非严格必要，但这种方法提供了额外的错误检查层次。

通过将对 `addItem()`、`getItem()` 和 `removeItem()` 的所有调用都包装在 `try...catch` 块中，您可以完全控制这些方法中可能发生的任何错误。请务必使用比示例中所示的 `die()` 调用更优雅的方式来处理这些错误。

回调是一种非常强大的技术，您可以使用它来实现惰性实例化，这可以节省系统资源，并确保您只操作绝对必要的数据。当您拥有复杂的对象层次结构时，可以使用回调来自动处理子对象的实例化，并推迟创建当前应用程序活动不绝对必要的那些对象。请务必了解此工作原理，并看看能否为这种技术找到其他用途。

第 6 章介绍了一个强大的数据库抽象扩展，这是作者访问关系数据库并避免与使用 PHP 的本机 PostgreSQL（或 MySQL、Oracle 或其他）函数相关的一些陷阱的首选方式。

## 使用 PDO 进行数据库抽象

您将要构建的几乎每个严肃的 Web 应用程序都会使用某种数据存储机制。这种数据存储通常用于存储应用程序设置、用户注册、动态内容——基本上是应用程序中任何将是动态的内容（即，它可能会在某个阶段发生变化，无论是由于您的某个用户的操作，还是由于拥有该应用程序的业务发生变化所致）。

对于除非常小型应用程序以外的所有应用程序，数据存储的公认选择通常是关系数据库管理系统（RDBMS）。其优势显而易见：可扩展性、易于查询、可靠性、韧性、数据完整性——还有更多。如果您希望除 PHP 以外的任何东西能够访问您的数据，这也是几乎必不可少的。通过为您的数据使用与平台无关的容器，您就不会人为地限制自己，例如，如果您有一天确定一个 .NET 应用程序也可能需要使用该数据。

诚然，“PHP 和数据库”的组合如此普及，以至于几乎所有初学者的书籍都在第一章就介绍 MySQL 数据库。LAMP（Linux、Apache、MySQL 和 PHP）这个缩写近年来不断出现——在 Google 上搜索“PHP and MySQL”短语可获得超过 200 万个结果。

不幸的是，与 PHP 中的许多事情一样，大多数人在 PHP 教育早期学习使用数据库的方式很少被视为最佳实践。构建可伸缩、可扩展、易于移植且易于维护的应用程序需要一种不同的方法。

在本章中，您将学习到正是这样。您将从回顾 PHP 的数据库支持开始，并提醒自己自多年前 PHP 推出以来数据库连接一直是如何处理的。通过考虑假设性示例，您将了解这种方法的局限性。然后，您将认识 PHP 数据对象（PDO），并学习 PDO 如何提供一种更适合企业级的方法。

### PHP 与数据库

自 PHP 3 初期以来，PHP 对关系数据库管理系统（RDBMS）享有广泛支持。与一些较旧的 Web 应用程序开发技术（尤其是 PERL）并非专门为此构建，以及一些其他技术（尤其是 Java）在 Web 开发之外拥有更广泛的吸引力不同，PHP 专门用于构建数据库驱动的 Web 应用程序。

### PHP 的数据库支持

开箱即用，PHP 可以支持 20 多种不同的关系数据库管理系统（RDBMS），各个供应商经常发布他们自己的 PHP 扩展。所有流行的版本都得到了支持，包括——也许最重要的是——四大数据库：MySQL、Oracle、SQL Server 和 PostgreSQL。

尽管很有用，但 PHP 中的数据库支持被视为扩展。这意味着它不被视为核心语言的一部分，因此必须在编译期间（在 UNIX 平台上）或运行时（在 Windows 平台上）通过在 php.ini 中启用相应的 DLL 来启用。

启动每个受支持的关系数据库管理系统（RDBMS）的技术在给定的 PHP 安装中各不相同。以下网址涉及非常有用的 php.net 参考网站：

- [ ] MySQL — http://uk.php.net/manual/en/mysql.installation.php
- [ ] PostgreSQL — http://uk.php.net/manual/en/pgsql.installation.php
- [ ] MS SQL Server — http://uk.php.net/manual/en/mssql.installation.php
- [ ] Oracle — http://uk.php.net/manual/en/oci8.setup.php

您可以通过使用 phpinfo() 语句轻松确定 PHP 安装中启用了哪些数据库支持。

打开您喜欢的文本编辑器，新建一个名为 phpinfo.php 的 PHP 文档。输入以下内容：

```php
<?php
phpinfo();
?>
```

现在启动 Web 浏览器并将其指向您刚刚创建的脚本。运气好的话，您将看到 PHP 配置的完整详细信息。使用浏览器的搜索功能，根据情况查找字符串 mysql、postgresql、mssql 或 oci8。如果您找到带有该标题的部分，那么您的 PHP 构建很可能已启用对该数据库的支持。

如果没有，是时候重新安装了。幸运的是，您会在附录 D 中找到相关信息，您将在其中了解在 Linux、Mac OS X 甚至 Windows 上安装 PHP 和 Apache 的最佳实践。

### PHP 与 PostgreSQL

这是本书中第一个涵盖数据库连接的章节。几乎每个后续章节都会以某种方式涉及它——考虑到这是一本关于 PHP 企业级开发的书，这也不足为奇。





这就是为什么此刻就必须理解这个重要主题的原因。你为项目选择的数据库平台取决于多个重要因素，而一名真正的专业人士几乎肯定会在他或她的职业生涯中某个时间点上使用之前提到的所有四个平台。

话虽如此，也会有些时候选择完全开放，最终取决于个人偏好。本书的作者在这种情况下更倾向于 PostgreSQL。它免费、快速、支持良好、可扩展、可伸缩且可靠，并拥有一个企业级功能集，在功能上略胜 MySQL 一筹。毫无疑问，这种观点与常见做法相悖，但同样，在企业中使用 PHP 的想法本身也是如此。

这里要记住的关键是，你要意识到这只是一种 *个人偏好*；归根结底，*这并不重要*。关于任何事情（操作系统、编程语言、Web 服务器、数据库）的计算机相关的宗教战争都极其令人厌倦，是青春痘少年程序员的标志，而非专业人士。每一个倡导平台 X 的所谓专家，你都会找到另一个倡导平台 Y 的人，而且此人很可能同样能滔滔不绝地侃侃而谈。

所以，坦率地说，*放下执念*。本章（实际上，本书的其余部分）将向你展示，为何开发得当的 PHP 应用程序是“数据库无关”的——正如它们是“Web 服务器无关”和“操作系统无关”的。本书不是关于“LAMP”或“LAPP”；如果你将命名法推演到其自然结论，本书实际上讲的是“XXXP”——也就是，纯 PHP。

不过，本书中你遇到的示例将使用 PostgreSQL。有关其安装和配置的更多信息，请参阅附录 D。如果这个选择让你极度困扰，作者恳请你为了本书提供的更广泛的教育而忍一忍——然后在自己的项目中随意使用 *任何你喜欢的东西*。正如本章和下一章所示，你不需要做太多更改就能进行切换。

## 回顾

让我们回顾一下 PHP 自诞生以来数据库连接的工作方式。以下内容假设你已安装正常工作的 PHP 并启用了 PostgreSQL 支持，且同一台机器上已安装正常工作的 PostgreSQL。

在控制台中按如下方式在 PostgreSQL 中创建新数据库：

```
$ /usr/local/pgsql/bin/createdb chaptersix
CREATE DATABASE
```

此语法假设 PostgreSQL 安装在 Linux 或其他 UNIX 平台的 /usr/local/pgsql 目录中。如果你在 Windows 或 Mac OS X 上运行，情况可能会有所不同。PostgreSQL 安装程序可能已将 bin 目录添加到你的路径中。如果是这样，你可以直接输入 createdb chaptersix。

CREATE DATABASE 消息表明数据库已从控制台成功创建。很好，但你的应用程序必须能够连接到该数据库。你的应用程序不会从控制台运行，因此它需要自己的登录凭据进行身份验证。因此，创建一个名为 chaptersix 的新用户，该用户可以连接到你的新数据库：

```
$ /usr/local/pgsql/bin/createuser -P chaptersix
Enter password for new role:
Enter it again:
Shall the new role be a superuser? (y/n) n
Shall the new role be allowed to create databases? (y/n) n
Shall the new role be allowed to create more new roles? (y/n) n
CREATE ROLE
```

在第一个提示符处，为新角色输入密码。就本测试而言，我们也将其设为 chaptersix。不完全安全，但用于测试目的足够了。

自然后来，后三个提示符都应该得到否定的回答。这不是什么特殊类型的用户；因此它只需要最低权限。

现在你有了一个空数据库，以及应用程序可以使用的登录凭据。让我们创建一个示例表：

```
$ /usr/local/pgsql/bin/psql chaptersix
Welcome to psql 8.2.4, the PostgreSQL interactive terminal.

Type:  \copyright for distribution terms
       \h for help with SQL commands
       \? for help with psql commands
       \g or terminate with semicolon to execute query
       \q to quit

chaptersix=# CREATE TABLE "user" (
chaptersix(#  "id" SERIAL PRIMARY KEY NOT NULL,
chaptersix(#  "username" character varying(32),
chaptersix(#  "password_hash" character varying(32),
chaptersix(#  "first_name" character varying(64),
chaptersix(#  "last_name" character varying(64));
NOTICE:  CREATE TABLE will create implicit sequence "user_id_seq" for serial column
             "user.id"
NOTICE:  CREATE TABLE / PRIMARY KEY will create implicit index "user_pkey" for
             table "user"
CREATE TABLE
```

如果从上述快照中不清楚，以下是你在 PostgreSQL 控制台中输入的内容：

```
CREATE TABLE "user" (
  "id" SERIAL PRIMARY KEY NOT NULL,
  "username" character varying(32),
  "password_hash" character varying(32),
  "first_name" character varying(64),
  "last_name" character varying(64));
```

因为你创建的用户没有权限，所以它对刚才创建的表没有访问权限。你必须告诉 PostgreSQL，允许名为 chaptersix 的用户访问名为 chaptersix 的数据库，并且该用户对该数据库中的关系拥有完全读写权限。

假设你仍在 PostgreSQL 控制台会话中（除非你输入 \q 并按 Enter 退出了），你可以运行以下两个 SQL 语句来设置所需的权限：

```
chaptersix=# GRANT ALL PRIVILEGES ON "user" TO "chaptersix";
GRANT
chaptersix=# GRANT ALL PRIVILEGES ON "user_id_seq" TO "chaptersix";
GRANT
```

请注意，你必须同时授予数据库表及其关联序列的权限。

最后，为了本练习的目的，让我们向刚创建的表中插入一些数据。PostgreSQL 允许你使用 COPY 语句批量插入数据，但对于输入测试数据，它比较挑剔。相反，让我们仅使用一些老派的 INSERT 语句将四行测试数据插入数据库，如下所示：

```
INSERT INTO "user"("username", "password_hash", "first_name", "last_name")
VALUES ('ed', md5('berkhamsted'), 'Ed', 'Lecky-Thompson');
INSERT INTO "user"("username", "password_hash", "first_name", "last_name")
VALUES ('steve', md5('newyork'), 'Steve', 'Nowicki');
INSERT INTO "user"("username", "password_hash", "first_name", "last_name")
VALUES ('marie', md5('leicester'), 'Marie', 'Ellis');
INSERT INTO "user"("username", "password_hash", "first_name", "last_name")
VALUES ('harriet', md5('cambridge'), 'Harriet', 'Frankland');
```

假设一切顺利无误，你应该会看到以下消息的四个实例：

```
INSERT 0 1
```

现在你已经使用完 PostgreSQL 控制台。你可以输入 \q 并按 Enter 键退出它。

现在你已经设置好了数据库，配置了用户，并且测试表和数据也都准备就绪。是时候重新熟悉 PHP 如何与数据库协同工作了。启动你的文本编辑器，敲出以下代码。将其命名为 dbtest.php 并放在 Web 服务器文档根目录的某个位置：

```
<?php
$objHandle = pg_connect("host=localhost port=5432 dbname=chaptersix user=chaptersix
         password=chaptersix");

if (!$objHandle) {
    echo "An error occurred connecting.\n";
    exit;
}
$objResult = pg_query($objHandle, "SELECT * FROM \"user\"");
if (!$objResult) {
    echo "An error occurred querying.\n";
    exit;
}
$arRowHash = pg_fetch_all($objResult);
for ($i=0; $i>=sizeof($arRowHash)-1; $i++) {
    print "Row $i<br />\n";
foreach ($arRowHash[$i] as $key => $value) {
    print " - Column $key, value $value<br />\n";
};
pg_close($objHandle);
?>
```

在 Web 浏览器中打开上述代码，你会看到以下输出：

```
Row 0
- Column id, value 1
- Column username, value ed
- Column password_hash, value fb097067945b57d5943bf9a49b7b7f12
- Column first_name, value Ed
- Column last_name, value Lecky-Thompson
Row 1
- Column id, value 2
- Column username, value steve
- Column password_hash, value 369389d19e24204b4927e30dd7c39efc
- Column first_name, value Steve
- Column last_name, value Nowicki
Row 2
- Column id, value 3
- Column username, value marie
- Column password_hash, value 16ba4bec9c54a088c9762527601b355a
- Column first_name, value Marie
- Column last_name, value Ellis
Row 3
- Column id, value 4
- Column username, value harriet
- Column password_hash, value efa93cabd5de7d42d6a31d41c33043ab
- Column first_name, value Harriet
- Column last_name, value Franklin
```

如果你反而看到一个刻意捕获的错误消息，请检查 PHP 错误日志以找出原因。你可能忘记正确设置权限，或者可能未启动 PostgreSQL 以允许来自外部数据源的 TCP/IP 连接。有关所需的 PostgreSQL 设置，请参阅附录 D。

希望一切顺利，并且上述代码看起来相当直接。它当然不应该是你以前没遇到过的东西。

这里基本上调用了四个过程式函数：pg_connect、pg_query、pg_fetch_all 和 pg_close。它们基本上按名称所暗示的方式工作。前缀 pg_ 表示它们是 PostgreSQL 特定函数；同样地，MySQL 特定函数以 mysql_ 开头，Oracle 的以 oci_ 开头，SQL Server 的以 mssql_ 开头。

## 问题

坦率地说，这种状况是一团糟。PHP 非常独特，因为它几乎没有预定义的类。几乎每个方法都存在于一种全局命名空间中。它不是父类的一部分，这意味着它实际上是一个“函数”。这是 PHP 3 的遗留问题，当时对 OOP 的支持，嗯，



有限。这意味着PHP想要支持的每个数据库都会在这个全局命名空间中创建至少30个左右的函数。

情况更糟。看看`mysql_query`和`pg_query`的语法。你会期望它们是一样的，对吧？错的，如下所示：

```
resource mysql_query ( string $query [, resource $link_identifier ] )
resource pg_query ( resource $connection , string $query )
```

没错。尽管这两个方法在功能上基本相同，但它们的参数顺序不同。

这增加了困难。PHP有出色的数据库支持（在支持的平台广度和深度方面），但实现糟糕（主要是历史原因）。由于这种混乱的不一致性，以这种官方认可的方式构建的PHP数据库驱动应用程序成为维护的主要头痛问题——而且无法扩展或移植。

## 包装器类

为了解决这种差异，并为在全局命名空间中创建的大量数据库函数带来一些秩序，近年来，各种第三方开发者尝试围绕这些数据库方法创建包装器类。

一个很好的例子是MDB2，它是PEAR仓库的一部分。（有关更多信息和全面文档，请参阅`http://pear.php.net/package/MDB2`。）

使用MDB2的典型会话可能如下所示。不需要尝试运行——这只是一个说明：

```
<?php
require_once 'MDB2.php';
$dsn = 'pgsql://chaptersix:chaptersix@localhost/chaptersix';

$mdb2 = MDB2::factory($dsn);

if (PEAR::isError($mdb2)) {
    echo ($mdb2->getMessage().' - '.$mdb2->getUserinfo());
}

$query = 'SELECT * FROM "user"';
$result = $mdb2->query($query);

if (PEAR::isError($result)) {
    echo ($result->getMessage().' - '.$result->getUserinfo());
    exit();
}

while ($array = $result->fetchRow()) {
    var_dump($array);
};

$result->free();
?>
```

你可能可以猜到输出。所有此类类所做的就是为现有的PHP全局方法提供一个接口——但平台之间具有一定程度的一致性。

作为PEAR类，这意味着这个MDB2包是半官方的——但重点在于“半”。它还不够普遍，这意味着在任何给定项目中使用的包装器选择（如果确实使用过的话）可能是不可预测的。你们中有多少人偶然遇到过某个名为`DatabaseConnection`或类似类的旧版PHP项目？也许这是原作者自己酿造的？

## 总结

要回顾这个问题：PHP的数据库支持是一团糟——一个混乱的静态方法集合，位于全局命名空间中，这是由于过去几年中语言发展太快、作者太多而产生的。

这种混乱表现为方法上的不一致，使得数据库之间的移植性几乎无从谈起。有人可能会争辩“这无关紧要”——但不要被骗了。它很重要。你可能对你当前选择的RDBMS充满信心，但如果其制造商被一家决定停止开发它的大公司收购呢？如果同一款RDBMS的新版本改变了它的工作方式呢？移植性——以及一致性——很重要。这就是为什么Java有Java Database Connectivity (JDBC)，而.NET有ADO.NET。即使是备受批评的Coldfusion也有类似的东西，以Coldfusion数据源的形式。

最终，与PHP中许多事情一样，一群出于好意（但欠妥当）的第三方开发者试图自己解决问题——并且在某种程度上使问题更糟。几乎每个PHP开发者都认识到，按官方文档的方法与常识相悖；但每个人都有自己独特的方法，导致一堆业余类来为PHP的数据库函数提供更清晰的接口。有些不错，有些不怎么样，但没有一个是官方的，因此也没有一个获得广泛使用。

幸运的是，PHP 6为我们带来了一个解决方案。

## 数据库抽象

刚才讨论的方法通常被称为*数据库抽象*。在最简单的层面上，这涉及任何减少数据库特定代码出现点数量的技术。

通过减少这些接触点的频率，应用程序变得更易于维护（因为简单数据库操作所需的代码更少）且更具可移植性（因为可能需要更改代码的地方减少了），从而简化了迁移。

## 需要什么

需要的是一种通用的、经PHP官方认可的数据库抽象方法。需要的是一种能实现一致性和可移植性目标，同时提供所有开发者都能团结一致的通用认可方法的东西。

考虑到.NET和Java 2 Enterprise Edition (J2EE)等其他平台已经拥有成熟的数据库抽象机制，采用类似他们公认相当精巧的方法也是可取的。

## 介绍PDO

幸运的是，自PHP 5.2（以及由此推论的PHP 6）起，PHP社区获得了PHP数据对象（PDO）。

PDO提供了一种与数据库无关的机制，用于在PHP中连接、读取和操作多种RDBMS平台。它使开发人员能够在每个数据库平台上采用一致的方法，从而简化可移植性和可扩展性，并消除对临时性第三方抽象层的需求。

## 开始使用PDO

对于熟悉传统数据库连接方法的PHP开发人员来说，PDO的方法起初可能显得有些不寻常。事实上，其特定技术在其他开发平台及其抽象层中经常出现。.NET、J2EE甚至PERL等其他平台几乎坚持使用各自的抽象层。PHP几乎是独一无二的，在官方文档中推荐使用“原始”连接技术。因此，对其他语言开发人员来说可能是司空见惯的事情，对初次接触PDO的PHP开发人员来说似乎特别不寻常。

不过，请放心。PDO方法的每个方面都有其充分的理由；随着你在本章其余部分遇到该层，很快就会明白为何采用某些技术和方法。

## 启用PHP支持

本章前面，你已经了解如何在PHP中启用数据库支持：

- 在UNIX平台上，在安装期间编译相关库
- 在Windows平台上，在`php.ini`中启用适当的DLL

不幸的是，仅仅为你选择的RDBMS启用数据库支持并不会启用PDO本身，也不会启用该平台的PDO支持。因此，你必须进一步配置PHP才能享受与所选数据库的PDO连接。

有一个“陷阱”需要注意。PDO支持并不*取代*传统的PHP数据库支持。它只是为其提供了一个额外的接口。因此，你仍必须为你的数据库平台启用基础支持。以下是一个检查清单：

- 启用基础PostgreSQL支持 — `with-pgsql`
- 启用PDO支持 — `enable-pdo=shared`
- 在PDO上启用PostgreSQL — `with-pdo-pgsql=/usr/local/pgsql`

有关启用PDO以及你的RDBMS所需支持的完整说明，可以在www.php.net/manual/en/pdo.installation.php找到。你也可以参考附录D，其中包含为Mac、Windows和Linux平台启用带PDO的PostgreSQL支持的最佳实践PHP和Apache安装方法。

## 连接和断开连接

检查你的PHP安装是否正确配置为与PDO和你选择的数据库平台一起工作的最佳方法是尝试快速连接。

目前，你不会用PDO做任何工作——只是立即连接和断开：

```
<?php
$strDSN = "pgsql:dbname=chaptersix;host=localhost;port=5432;user=chaptersix;
   password=chaptersix";

// Let's connect
try {
   $objPDO = new PDO($strDSN);
   print "Successfully connected ....\n";
} catch (PDOException $e) {
   echo "An error occurred connecting: " . $e->getMessage() . "\n";
   exit(0);
}

// Let's disconnect
$objPDO = NULL;
print "Successfully disconnected.\n";
?>
```

此示例使用你在本章前面填充的同一测试PostgreSQL数据库。如果你仍然设置并运行它，你应该看到以下输出：

```
Successfully connected ... Successfully disconnected.
```

如果有什么不对劲，你应该看到类似以下由PDO生成的错误消息：

```
An error occurred connecting: SQLSTATE[08006] [7] FATAL: database "chaptersix" does not exist
```

该消息直接来自相关的RDBMS，因此希望它相对容易追踪。同样，如果本章前面的示例对你有效，并且你已正确启用PDO支持，那么此示例理应毫无问题地运行。

## 使用PDO

既然你现在已通过PDO成功连接到简单的PostgreSQL数据库，是时候深入了解一下引擎盖下发生了什么了。





## The PDO Class

You probably noticed in the previous example that there’s no “connect” method in PDO, nor is there any “disconnect” method. This is quite deliberate. The act of instantiating a new instance of the global PDO class establishes a connection to the database. Disconnecting happens automatically at the end of the script or, alternatively, when the class is destroyed by setting it to null.

As a result, connecting to the database is as simple as the following:

```
$objPDO = new PDO($strDSN);
```

Disconnecting is as simple as this:

```
$objPDO = NULL;
```

As such, the PDO class itself is best described as a symbolic representation of a database connection; an instance of the class can only exist once a connection has been established.

You'll doubtlessly notice the single parameter you are passing to the constructor of the PDO class. This is known as a database source name (DSN). This is a concatenated string that describes the protocol, hostname, username, password, port, and database name. In some cases, other parameters can be passed, and in other cases, parameters can be omitted and the default assumed (such as in the case of TCP/IP port, which in the case of PostgreSQL is usually 5432).

PDO supports a handful of formats for valid DSN strings, but the following is the most common:

```
protocol:key=value;key=value;key=value [etc]
```

Here, protocol refers to the PDO driver to use — pgsql for PostgreSQL, mysql for MySQL, mssql for MS SQL Server, and oci for Oracle.

Each key/value pair is used to specify a particular attribute for the connection. They are many and varied, but the following are most commonly used:

- host — Hostname of the database (or IP address)
- user — Username
- password — Password (plain text)
- port — TCP/IP port (only supported if not connecting to localhost)
- dbname — Database name

For a full list of parameters for the database of your choice, refer to the PHP manual’s database of supported drivers at www.php.net/manual/en/pdo.drivers.php. After choosing your driver, you will see a list of supported parameters enumerated.

## Executing Queries

So far, you’ve learned how to connect and disconnect using the PDO driver, and you should understand how to pass connection parameters to customize your connection.

Now you can see how to execute a simple query using your instantiated PDO object. The following snippet of code should be inserted between your simple connection and disconnection code:

```
// Let's interrogate the database
$i = 0;
$strQuery = "SELECT * FROM `user`";
$objStatement = $objPDO->query($strQuery);
foreach ($objStatement as $arRow) {
    print "Row $i<br />\n";
    foreach ($arRow as $key => $value) {
        if (!is_numeric($key)) print " - Column $key, value $value<br />\n";
    };
    $i++;
};
```

If all goes well, then you should be able to see exactly the same output you generated earlier in the chapter using procedural database connectivity.

It’s worth taking a little time to understand what’s happening here. It will make your life considerably easier when you get into the more advanced material later in this chapter.

The query() method of the PDO class quickly and “unfussily” executes the query specified and returns an instantiated class of type PDOStatement. The beauty of the PDOStatement class is that it implements the interface known as Traversable; that means it supports direct iteration. Therefore, you can execute a foreach() statement on an instance without worrying about how the class works under the hood.

Well, that is, almost. Iterating over the class results in associative arrays, each one equaling one row of output; but each associative array entry contains both key/value and index/value data. That’s why you need the is_numeric() clause to filter out the index/value stuff — try removing it and see what happens.

The preceding illustrates two points. First, it is hoped that it shows you that interrogating a database using PDO need not necessarily be any more code-intensive than using procedural code. Second, it also demonstrates that this quick-and-dirty approach doesn’t exactly give you much flexibility.

What would happen if, rather than iterate directly over the PDOStatement object returned directly, you intercepted it, and worked with it in a little more detail?

## The PDOStatement Class

The PDOStatement class represents a single statement to be executed against a given session within PDO, both before the query in question has been executed and afterward.

Instances of PDOStatement are never created directly. Instead, the PDO class itself provides the prepare() method, which generates an instance of PDOStatement. In turn, the mechanisms for interrogating the return data held by PDOStatement are considerably more sophisticated than simply using direct iteration over the class instance.

Modify the preceding block of code to read as follows:

```
// Let's interrogate the database
$i = 0;
$strQuery = "SELECT * FROM `user`";
$objStatement = $objPDO->prepare($strQuery);
$objStatement->execute();
while ($arRow = $objStatement->fetch(PDO::FETCH_ASSOC)) {
    print "Row $i<br />\n";
    foreach ($arRow as $key => $value) {
    print " - Column $key, value $value<br />\n";
    };
    $i++;
};
```

Refresh the page. You should see a familiar sight — yes, that’s right, exactly the same output as before.

However, you’re being a little smarter here by making two big changes. First, rather than call the query() method of the PDO class, you’re calling the prepare() method. The key difference is that although an instance of PDOStatement is being returned, the query is not yet being executed. In the preceding example, you’re executing the query more or less immediately; but as you’ll see shortly, by separating out the preparation of the statement and the execution of the query, you’re allowing yourself an opportunity to further manipulate the statement prior to execution.

The second big change you’re making is to use the fetch() method of PDOStatement to fetch each row returned by the database one at a time, rather than use foreach() to iterate over the instance of PDOStatement itself. This gives you the flexibility to pass a parameter — a constant, namely PDO::FETCH_ASSOC. This means the data returned is an associative array containing only key/value data — not mixed with index/value data as before.

Notice, too, that it’s easy to return just one row at a time. The fetch() method returns false as soon as there are no further rows to return. A similarly structured method fetchAll() enables you to return all rows at once in a single array of associative arrays.

## Prepared Statements

One of the core uses of prepared statements is to provide a convenient mechanism to pass variable parameters into SQL queries.

A classic example is a scenario in which you may want to retrieve information on a particular row or rows by using a WHERE clause. Naturally, this is technically possible without using any SQL-specific techniques:

```
// Let's interrogate the database
$i = 0;
$strUsername = 'ed';
$strQuery = "SELECT * FROM `user` WHERE username = '$strUsername'";
$objStatement = $objPDO->prepare($strQuery);
$objStatement->execute();
while ($arRow = $objStatement->fetch(PDO::FETCH_ASSOC)) {
	print "Row $i<br />\n";
	foreach ($arRow as $key => $value) {
		print " - Column $key, value $value<br />\n";
	};
	$i++;
};
```

As you'd expect, this code returns just the row you want — in the example data, the row for the user named 'ed'.

In the preceding example, though, you are relying on PHP to merge the variable parameter (in this case, the username) with the hard-coded SQL (the statement). An alternative approach is to use the database engine to undertake the “merge.” Try the following:

```
// Let's interrogate the database
$i = 0;
$strUsername = 'ed';
$strQuery = "SELECT * FROM `user` WHERE username = :username";
$objStatement = $objPDO->prepare($strQuery);
$objStatement->bindParam(':username', $strUsername, PDO::PARAM_STR);
$objStatement->execute();
while ($arRow = $objStatement->fetch(PDO::FETCH_ASSOC)) {
	print "Row $i<br />\n";
	foreach ($arRow as $key => $value) {
		print " - Column $key, value $value<br />\n";
	};
	$i++;
};
```

The results should be exactly the same — only data about the username 'ed' is returned. In this case, as promised, the SQL engine is undertaking the merge.

Notice that the SQL query string being passed to the prepare() method contains an unquoted parameter prefixed with a colon — namely, :username. This indicates to the PDO engine that you plan to fill that in a bit later.

The bindParam() method does just that — takes a variable and passes it to the PDO engine, telling it where to tie it into the original SQL statement. The constant PDO::PARAM_STR tells the PDO engine that the parameter being passed is a string. This is important, because the onus is on the PDO engine and the RDBMS to apply the quotes necessary to construct the final SQL.





`bindValue()` 方法的工作原理类似，但它不会将 PHP 变量作为参数接受——相反，它需要的是硬编码值。同样，如果你尝试将硬编码值传递给 `bindParam()`，它会失败——它需要的是按引用传递的变量。

采用这种方法有四个主要好处。

- 首要（也是最重要）的是抽象的好处。如果 MS SQL 倾向于使用方括号（`[` 和 `]`）来表示参数化，而 PostgreSQL 倾向于使用单引号（`'` 和 `'`），那么这就引入了可移植性的天然屏障。由 PDO 和数据库本身来处理这些数据库特有的细节，就移除了这一特定屏障。

- 第二个问题是特别热门的安全话题——具体来说，就是易受 SQL 注入攻击。向数据库传递 HTTP `POST` 或 `GET` 参数作为语句输入参数的 Web 应用程序特别容易受到此类攻击。输入参数可能会被恶意操纵，以尝试执行非原意的恶意查询。更多信息，请参阅信息丰富的 Wikipedia 文章 `http://en.wikipedia.org/wiki/SQL_injection`。

  避免 SQL 注入的一种解决方案是 _转义_——即预解析 HTTP `POST` 和 `GET` 参数，以转义 SQL 中具有特殊含义的字符（如方括号和单引号）。然而，这并非万无一失，尤其是在使用不寻常的非 ASCII 字符集（如 Unicode）时。

  这也引入了可移植性问题——比较使用反斜杠（`\'`）转义单引号的数据库与使用双写入（`''`）转义单引号的数据库。

  使用参数化预处理语句可以一劳永逸地解决此问题。值的转义（包括按需要用分隔符封装）完全由 PDO 和数据库本身处理。因此，开发者不再需要在整个过程中承担缓解 SQL 注入的责任——对于大型项目来说，这甚至对经验丰富的开发者来说也是一大福音。

- 最后，还有性能问题。通过使用单个预处理语句，底层数据库可以知道，应用程序中的热门查询（例如前面展示的示例）在结构上始终是相同的，每次仅更改一个参数或一组参数。这使数据库自身的缓存和内存管理技术能够自我优化，以便每次都能让这些查询尽可能快地执行。当参数在数据库引擎感知之外传递时，此类优化无法发生。

## 仅写语句

在前面的示例中，你已经学习了如何使用 PDO 通过 `SELECT` 语句从数据库提取数据；但自然，并非所有语句都会返回数据——`UPDATE`、`DELETE` 和 `INSERT` 语句即是例示。

不过，你的技巧应该与之前大致相同：

```php
$strQuery = "INSERT INTO \"user\" (\"username\", \"password\" VALUES
                 (:username, :password)";
$strUsername = 'newuser';
$strPassword = 'mypassword'
$objStatement = $objPDO->prepare($strQuery);
$objStatement->bindParam(':username', $strUsername, PDO::PARAM_STR);
$objStatement->bindParam(':password', $strPassword, PDO::PARAM_STR);
$blSuccess = $objStatement->execute();
```

请注意，在执行查询时，你会捕获返回参数。这使你能够对执行是否成功进行一些非常基本的错误检查。如你所料，这对于企业级应用程序来说远远不够。在本章后面，你将学习 PDO 的一些专用错误处理技术。

## 事务与提交

如你可能料到的那样，默认情况下，PDO 假设对数据库的写入操作应自动提交。在前面的示例中，数据库中的插入操作会立即发生——即在对 PDOStatement 对象调用 execute() 语句后立即发生。

当然，这并不总是可取的。大多数数据库都支持事务，这意味着多个数据库操作可以作为单个操作提交，并且如果某个条件满足（或不满足），则可以整体取消。经典示例是两个银行账户之间的资金转账。从发送方账户提取资金以及向接收方账户存入资金必须是原子性的——即，要么两者都发生，要么两者都不发生。换句话说，如果从发送方账户扣除资金后，发生了阻止向接收方账户记账的故障，那么原始的从发送方移除资金的操作也应被取消。

事务控制是针对 PDO 类的实例进行的——而不是 PDOStatement。可能的操作有三个：启动新事务、提交（完成）事务和回滚（取消）事务。这些操作是通过 PDO 的 beginTransaction()、commit() 和 rollBack() 方法实现的。请查看以下代码片段：

```php
<?php
$objPDO = new PDO($strDSN);
$objPDO->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

try {
  // begin the transaction
  $objPDO->beginTransaction();

  $objPDO->exec($strQuery1);
  $objPDO->exec($strQuery2);

  // commit the transaction
  $objPDO->commit();
} catch (Exception $e) {
  // rollback the transaction
  $objPDO->rollBack();
  echo "Failed: " . $e->getMessage();
}
?>
```

此示例假设已建立与 $strDSN 所描述的 DSN 的连接。随后，一个事务开始，它封装了由 $strQuery1 和 $strQuery2 所描述的两个相互依赖的查询。

如果在任何阶段发生任何错误，将生成异常，从而阻止执行任何进一步的代码。自事务启动以来执行的所有事务都将被回滚（即撤销）。

事务本身是一个庞大的话题，完整的讨论超出了本章的范围。然而，你无疑会在整个编程生涯中再次遇到它们，因此希望本节能成为一个有用的入门指南。

## 常量

在本章中，你已经看到许多对 PDO 类公开的静态常量的引用——例如 PDO::PARAM_STR、PDO::ERRMODE_EXCEPTION、PDO::FETCH_ASSOC 等。

这些常量用于定义列数据类型、指定不同的获取模式、设置操作属性和特性，以及更改行检索光标行为。

完整的常量列表可在 www.php.net/manual/en/pdo.constants.php 上找到。

## 错误处理

任何企业级应用程序都需要卓越的异常处理（此处为双关语）。虽然你可以在 PHP 代码中使用简单技术来缓解日常事件引起的错误（例如用户未能正确输入密码），但也要确保你能优雅地应对应用程序与底层数据库通信过程中可能出现的任何意外情况。这包括首次无法连接数据库、身份验证失败、缺少关系（表和/或列）、违反约束等——任何 PHP 无法自行知晓的事项。

如何处理错误的存在取决于你——但目标是优雅降级。在第 20 章中，你将了解更多有关质量保证及其在应用程序中重要性的内容。你用于在应用程序中处理异常的机制在实现高度质量方面起着重要作用。

默认情况下，PDO 以所谓的静默模式运行。这意味着，如果你不使用 PDO 或 PDOStatement 上的 errorCode() 和 errorInfo() 方法显式查找错误，则不会检测到错误。

`errorCode()` 方法将返回一个五字符错误码——例如 45S02，它反映了 PDO 实例或 `PDOStatement` 实例上最后一次操作的所谓 `SQLSTATE`。你选择的数据库应该在其自身文档中提供 `SQLSTATE` 值列表；PostgreSQL 在 www.postgresql.org/docs/8.2/static/errcodes-appendix.html 提供了一个列表。

`errorInfo()` 方法将返回更多详细信息。你会得到一个三元素数组。第一个元素包含与 `errorCode()` 相同的信息；第二个包含任何驱动程序特定的（例如 PostgreSQL 特定的）错误码；第三个包含来自数据库本身的人类可读错误消息。

这两种方法都很有用，但它们要求你（作为开发者）在几乎每个阶段测试错误。这对于生产级应用程序来说并不十分合适，并会迅速导致难以维护的代码。你应该相反地告诉 PDO 在每次遇到问题时抛出异常——并由你自己捕获该异常。这使你作为开发者拥有权力，以你认为合适的宽松或严厉程度来处理该错误。然而，这也让你承担责任，确保捕获每个可能的错误。任何未捕获的异常都会导致一个巨大的、丑陋的 PHP 错误——这不是你希望用户看到的东西。

你可以通过以下方式告诉 PDO 以这种方式工作：

```php
$objPDO->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
```

这需要在实例化 PDO 类后尽快调用，甚至在尝试第一个查询准备之前。

因此，任何 PDO 使用都必须包裹在 try/catch 对中。以下是你可以自行尝试的完整示例：

```php
<?php
$strDSN = "pgsql:dbname=chaptersix;host=localhost;port=5432;user=chaptersix;
        password=chaptersix";

// Let's connect
try {
    $objPDO = new PDO($strDSN);
    $objPDO->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

// Let's interrogate the database
$i = 0;
$strQuery = "SELECT * FROM \"usdrs\"";
$objStatement = $objPDO->prepare($strQuery);
$objStatement->execute();
while ($arRow = $objStatement->fetch(PDO::FETCH_ASSOC)) {
    print "Row $i<br />\n";
    foreach ($arRow as $key => $value) {
        print " - Column $key, value $value<br />\n";
    };
    $i++;
};
// Let's disconnect
```





```php
$objPDO = NULL;

} catch (PDOException $e) {
echo "An error occurred connecting: " . $e->getMessage() . "<br />\n";
list($strCode, $strCode2, $strInfo) = $objPDO->errorInfo();
print "PDO: - Code was '$strCode',<br /> - Driver code was '$strCode2',<br /> - Info string was '$strInfo',";
if ($objStatement instanceof PDOStatement) {
list($strCode, $strCode2, $strInfo) = $objStatement->errorInfo();
print "<br /><br />PDO Statement: - Code was '$strCode',<br /> - Driver code was '$strCode2',<br /> - Info string was '$strInfo'";
};
exit(0);
}
?>
```

运行这段代码（其中包含一个故意的错误），你应该会看到类似这样的内容：

```
An error occurred connecting: SQLSTATE[42P01]: Undefined table: 7 ERROR:
relation "udser" does not exist

PDO: - Code was '00000',
- Driver code was '7',
- Info string was 'ERROR: relation "udser" does not exist'

PDO Statement: - Code was '42P01',
- Driver code was '7',
- Info string was 'ERROR: relation "udser" does not exist'
```

希望这种详尽的输出能让你非常轻松地看到捕获的错误——你只是拼写错了。修复它，刷新页面，你应该会看到一些非常熟悉的输出。

这个示例在捕获错误时已经崩溃并终止。当然，在你的企业级、实际应用程序中，你会希望比这聪明一点。与其简单地将可用信息倾倒到屏幕上，你最好使用 switch() 语句或类似结构来决定显示哪条错误消息——如果你确实要显示错误消息的话。

最后再提醒一句：不要向用户透露太多信息。从可用性角度来看，这不仅乏味且无用（用户为什么要关心缺少哪个表？），而且还会将你的数据库架构暴露给外界。从安全角度看，最好避免这种情况。

## 高级 PDO 技术

到目前为止，你已经了解了 PDO 的基础知识。希望你现在有信心在项目中使用它，以取代传统的过程式连接或第三方非官方封装类。

不过，还有几个主题值得讨论。不要指望这里有太多细节——它们本身就是庞大的主题，其中一些你会在本书后面部分更详细地学到。不过，通过在这里初步了解每个主题，你可以明白为什么随着项目复杂性的增加，你不应该被诱惑回到糟糕的习惯中。

## 大对象

编程界一直在争论是否应该在数据库中存储大对象。术语 *大对象 (LOB)* 通常指给定行中任何一个列值超过大约 4,098 字节的情况。

这可能是纯文本。例如，你可能会在数据库中存储代表 HTML 邮件正文的复杂 HTML 片段。同样，它也可能是二进制数据。例如，你可能希望在数据库中存储一个用户上传的大图像。

争论的原因在于，在结构化环境中存储和提供本质上是一块非结构化数据所涉及的巨大处理负担。例如，在渲染网页的过程中显示用户上传的图像。如果该网页可以简单地从 Web 服务器的文件系统中检索该图像，那么这就很容易。但是，如果该网页必须从 PHP 脚本中检索图像，而该脚本又必须从数据库中检索二进制数据，那么这就不那么容易了。

不过，通常可以实现折中方案。例如，你可以使用数据库存储此类大对象的“主副本”，然后使用离线生成脚本创建存储在文件系统中的缓存。这让你两全其美：使用单一数据库存储所有可变数据，但使用文件系统和简单 Web 服务器来提供静态内容。

数据库中存储大对象的机制因平台而异。幸运的是，每个 PDO 驱动程序都知道将数据写入和读取数据库的最佳方式，并会为你处理好这一切。

PDO::PARAM_LOB 常量提供了一种整洁的方式来处理来自受 PDO 支持的数据库的大对象返回数据，如下例所示。这表示可用于将图像直接输出到 HTML 标签中的脚本代码：

```php
<?php
$db = new PDO($strDSN);

$stmt = $db->prepare("SELECT \"bindata\" FROM \"jpeg_image\" WHERE id = :imageid");
$stmt->bindParam(':imageid', $_GET['id'], PDO::PARAM_INT);
$stmt->execute();
$stmt->bindColumn(1, $binData, PDO::PARAM_LOB);
$stmt->fetch(PDO::FETCH_BOUND);

header("Content-Type: image/jpeg");
fpassthru($binData);
exit(0);
?>
```

如果将此脚本命名为 dumpimage.php，你可以使用如下图像标签来调用它：

```html
<img src="dumpimage.php?id=12345" />
```

请注意，你以通常的方式绑定表示图像标识符的输入参数，并小心使用常量 PDO::PARAM_INT 告诉 PDO 它必须是整数。同样请注意，你使用了 PDOStatement 的一个名为 bindColumn() 的方法。这种方法的不同寻常之处在于，它允许后续调用 fetch() 填充给定的 PHP 变量，而无需进一步说明。

在这种情况下，使用 bindColumn() 告诉 PDO，其返回数据的第一个（最左侧）列应填充到 PHP 变量 $binData 中——每使用 fetch() 调用一行填充一次。通过指定数据类型 PDO::PARAM_LOB，fetch() 方法将使用 PHP 对大对象的最接近近似——即流——将该数据存储在该变量中。

PHP 中的文件流可以使用 fpassthru() 直接发送到标准输出——这正是你用来将图像二进制数据直接输出到浏览器的方法，但要记得先发送合适的 MIME 类型作为标头。

值得注意的是，PHP 假设你使用的是数据库首选的大对象隐喻。如果不是（例如，如果你将 Base64 编码的数据作为字符串存储），那么这种技术将失败。在 PostgreSQL 中，大对象是使用对象标识符 (OID) 引用实现的，并且在很大程度上由数据库“幕后”处理。比你所希望的更多阅读材料可在 www.postgresql.org/docs/8.1/static/largeobjects.html 上找到。

## 数据库特定函数

当特定请求在使用的数据库平台上无法完成时，PDO 会尽力模拟该行为（或优雅地失败）。诚然，某些数据库行为确实特定于该平台。因此，PDO 试图提供通用实现，却在 20 个 RDBMS 中有 19 个失败，这将是愚蠢的。

出于这个原因，PDO 和 PDOStatement 类的某些方法仅在使用特定驱动程序实例化 PDO 时才可用。

例如，在 PostgreSQL 中创建大对象（如刚才讨论的）是通过从中央大对象仓库分配新 OID 实现的，该仓库跨越多个表和数据库，因此本质上是每个安装唯一的。这种行为可以说非常小众，因此 PDO 公开了一个仅限 PostgreSQL 的方法 PDO::pgsqlLobCreate() 来实现它。有关完整语法，请参见 www.php.net/manual/en/function.pdo-pgsqllobcreate.php。

这是一种合理的方法。然而，无论 PDO 的初衷多么良好，完美的数据库抽象在某种程度上都是海市蜃楼，你将在下一节中看到这一点。当方法论确实特定于某个平台时，开发人员已分配了一个唯一方法来实现它。

因此，特定于驱动程序的单独方法和常量可以在 www.php.net/manual/en/pdo.drivers.php 上找到的 PDO 驱动程序函数参考中找到。如果你选择的数据库经常有非传统的倾向，请务必查阅它。

## 持久连接

一般来说，每次将 PDO 类的实例作为对象创建时，都会与数据库形成一个新的 TCP/IP 连接。相应地，当该对象被销毁时，此连接会关闭。

对于高流量连接，这并不总是可取的。使用持久连接意味着 PHP 会在脚本终止后保持已建立的连接打开。当脚本再次运行时 in



另一个会话中，现有的空闲连接会被“劫持”以立即使用。这就像一直保持电话拨通到你最喜欢的披萨店，然后在饿的时候只需将听筒举到耳边。

这样做可以带来性能优势。因为打开和关闭套接字会带来开销，保持连接打开就消除了这种开销。

使用持久连接非常简单，如下所示：

```
<?php
$objPDO = new PDO($strDSN, NULL, NULL, array(
    PDO::ATTR_PERSISTENT => true
);
?>
```

注意 DSN 后面的空白参数。如果你在 DSN 中填写了用户名和密码，则不需要这些参数（通常用于指定用户名和密码）。第四个参数（驱动程序特定参数的数组）包含了将 PDO::ATTR_PERSISTENT 设置为 true 的参数。

请注意一个缺点和一个先决条件。缺点是这些连接被 PHP“保留”，这意味着其他应用程序（包括你可能需要定期用来执行批处理任务的命令行 PHP 脚本）无法使用这些连接与你的数据库通信。先决条件是，为了在脚本执行之后维持连接，PHP 必须作为 Web 服务器模块运行，而不是 CGI 脚本。但是，如果你遵循附录 D 中的安装说明，那么这不应该成为问题。

## 存储过程

许多数据库平台支持存储过程。这意味着某些常见的过程和函数可以直接编码到数据库架构中，而不是在应用程序开发语言（例如 PHP）中开发。例如，getNearestStore() 之类的方法可以直接从 SQL 语法中调用，而无需在 PHP 中构建多个查询来达到同样的效果。

这种方法有某些优势。某些 RDBMS 可以智能地缓存调用存储过程时涉及的数据集。因此，后续对这些存储过程的调用可以获得性能优势。此外，如果其他平台（例如 .NET 应用程序或 PERL 脚本）需要访问相同的数据并执行相同的过程，则可以节省代码。

调用存储过程与调用任何 SQL 语句没有区别。语法取决于所涉及的 RDBMS。MySQL 使用 CALL() 语句；PostgreSQL 只是像调用内置函数一样调用该函数。传递参数的方式完全相同，如下所示：

```
$iUserID = 12345;
$objStatement = $objPDO->prepare("SELECT getNearestStore(:userid)");
$objStatement->bindParam(":userid", $iUserID, PDO::PARAM_INT);
// call the stored procedure
$objStatement->execute();
```

请记住，存储过程会严重限制数据库可移植性——这是 PDO 项目的关键目标之一。为此，请谨慎且明智地使用它们。

## 单例实例化

在典型的 PHP 项目中，只需要一个到一个数据库的连接。因此，在给定的请求中不应该实例化多个 PDO 类实例——毕竟，一个实例等于一个连接。

然而，遵循这条规则可能颇具棘手。当你开始构建越来越复杂的项目时，你会发现数据库访问需求分散在多个类中。如果每个类的每个方法都需要访问数据库，那么如何在这些类之间共享对单个连接的访问呢？

答案是单例类，即带有单个工厂方法的类，用于为你的应用程序返回 PDO 实例。这个方法非常聪明。它会判断是否已经向应用程序返回了 PDO 实例。如果没有，则创建一个新的 PDO 实例并返回其引用。如果有，则返回现有实例的引用：

```
<?php
class PDOFactory {
    public static function GetPDO($strDSN, $strUser, $strPass, $arParms) {
        $strKey = md5(serialize(array($strDSN, $strUser, $strPass, $arParms)));
        if (!($GLOBALS["PDOS"][$strKey] instanceof PDO)) {
            $GLOBALS["PDOS"][$strKey] = new PDO($strDSN,
                $strUser, $strPass, $arParms);
        };
        return($GLOBALS["PDOS"][$strKey]);
    }
}
?>
```

这个类使你能够创建新的 PDO 实例，而无需担心重复连接。只要每次提供的 DSN、用户名、密码和参数数组都相同，你就永远不会得到重复项——只会得到原始实例。

因此，在代码中，请查找以下内容：

```
$objPDO = new PDO($strDSN, NULL, NULL, array(PDO::ATTR_PERSISTENT => true));
```

不要使用前面的语法，而要使用以下内容：

```
$objPDO = PDOFactory::GetPDO($strDSN, NULL, NULL, array(PDO::ATTR_PERSISTENT => true));
```

效果是一样的——你得到一个 PDO 对象实例——但你保证在每次脚本执行中不会得到超过一个实例，无论你从哪个类请求该实例。

## PDO 的局限性

在本章到目前为止，你一直以相当正面的眼光看待 PDO——这是一种简单、直接且官方认可的机制，无论你选择哪种 RDBMS，都可以在 PHP 应用程序中提供统一的数据库抽象。

然而，从实现跨平台真正可移植性的目标来看，可以公平地说 PDO 有其局限性。理解并识别它能在哪里（以及不能在哪里）帮助你，是真正 PHP 专业人士的标志。如你在后续章节中所见，有超越数据库抽象范畴的技术可以促进可移植性和可扩展性。

### 查询语法

请考虑以下 SQL 查询：

```
SELECT TOP 10 * FROM [user]
```

现在考虑这个查询：

```
SELECT * FROM "user" LIMIT 10;
```

这两个查询表面上显然不同。但是，正如你可能猜到的，它们在各自的数据库中执行时会产生相同的输出。第一个查询是 Transact-SQL，因此与 MS SQL Server 和 Sybase 兼容。后者是 PostgreSQL——或者 MySQL。

然而，差异更深层。请考虑以下内容：

```
SELECT * FROM user
```

现在考虑这个：

```
SELECT * FROM "user"
```

前者和后者在 MySQL 中都是完全允许的。然而，只有后者在 PostgreSQL 中是允许的，因为 "user" 是保留字，所以需要引号——而非可选。到现在为止，你无疑已经看出了这一点。虽然 SQL 在各种 RDBMS 之间允许很大的共同性，但每种 SQL 方言都有细微差别。PDO 可以处理转义和添加引号等小的差异，但无法处理语法上的根本差异。

这种缺陷自然限制了可移植性——这正是 PDO 的整体目的。

### 功能模拟

同样，某些 RDBMS 支持其他 RDBMS 所没有的完整功能集。一个典型例子是事务支持——它在旧版本的 MySQL 以及 SQLite 和 Access 等平面文件数据库中明显缺失。

PDO 会尽力模拟目标 RDBMS 所不具备的软件级功能。不幸的是，当它无法做到这一点时，很少会抛出错误——相反，它只是不起作用。一个很好的例子是 PDO::lastInsertId() —— 这是一个有用的方法，旨在返回应用程序执行的最后一条 INSERT 语句分配的自增数值标识符。遗憾的是，如果数据库驱动程序不支持此方法，则你可能无法获得有意义或一致的结果。

这里的教训是，在尝试之前，要 _非常确定_ 你的 RDBMS 支持你要尝试的操作。如果不支持，则你可能不会发现抛出了预期的错误；相反，PDO 可能会试图提供帮助，但最终会让过程变得非常令人困惑。

## 非 SQL 数据源

最后，值得提及 _数据源_ 的概念。PDO 假设你的应用程序可能使用的任何数据源都是传统的现成数据库（例如 PostgreSQL 或 Oracle），或者是平面文件解决方案（例如 Access 或 SQLite）。然而，越来越多的情况下，情况并非总是如此；应用程序经常使用通过某种形式的 Web 服务运行的远程数据源。

一个很好的例子是一家从小做起的企业——可能只运行一个 PostgreSQL 或 MySQL 数据库——然后决定将其业务模式特许给加盟商。为该小型企业提供支持的相同代码可能需要在加盟商中推广，但不是使用简单安装的 RDBMS，而是使用提供对同一近似数据模型分布式访问的中央 Web 服务。

在这种情况下，PDO 未能达到预期。没有机制可以将使用 PDO 与传统数据库的用法迁移到这里描述的更分布式模型。编写自己的 PDO 驱动程序当然是可能的，但不能在 PHP 中完成。需要对 PHP 核心进行 C++ 补丁，随之而来的还有可维护性相关的所有固有困难。

## 超越 PDO

值得提及的最后一点是——PDO 并不 _为你编写 SQL_。这是刻意为之。参考 `www.php.net/manual/en/intro.pdo.php` 上的 PDO 文档，你会清楚地看到 PDO 将其自身宣传为“数据访问抽象”，而非“数据库抽象”。

这听起来可能只是语义问题，但这种区别很重要。PDO 仍然要求你对所选 RDBMS 具有近乎百科全书式的了解——包括它的特性、具体功能和局限性。这也许不是坏事，但你可能会发现，不得不反复编写重复的 SQL 语句来执行简单的操作（如创建、读取、更新和删除实体）会让你感到沮丧。

别担心。在第 7 章中，你将学习对象关系映射（ORM）以及它如何通过为你构建常见 SQL 查询来为你节省大量时间。




## 摘要

本章为您介绍了 PHP 数据对象（PDO）。您了解了 PDO 如何在保证应用程序在看似迥异的数据库平台之间具有可移植性和可扩展性方面发挥重要作用。

您首先回顾了 PHP 的基本数据库支持，通过创建、连接、读取和操作简单的 PostgreSQL 数据库。通过假设性示例，您了解了 PHP 内置的过程式数据库访问如何限制应用程序的可扩展性和可移植性；甚至了解了第三方出于好意（但最终徒劳无功）的尝试如何试图解决该问题。

您了解了在 PHP 6 中进行数据库访问的“官方方式”——即 PDO。从头开始，您学习了如何使用首选的 PHP 技术重新创建您在 PHP 4 和 5 中习惯使用的简单数据访问技术。

最后，您接受了 PDO 为开发人员提供的一些高级机制的速成课程，目的是在本书后面部分更详细地学习每种技术。您还了解了 PDO 的一些局限性（在某些情况下并非无关紧要），这些局限性表明它只能部分解决当前问题。

第 7 章同样重要。您将了解对象关系映射（ORM），它使您在构建常见数据库应用程序时能够编写更少的 SQL。您可能之前不知不觉地接触过它，但 PDO 的强大功能使其能够比历史上更进一步。您新获得的 PDO 知识将使您对 ORM 能为您的应用程序带来什么以及为什么它如此重要有了新的认识。

# 第二部分

## 学习高级开发技术

- 第 7 章：对象关系映射
- 第 8 章：事件驱动编程
- 第 9 章：日志记录和调试
- 第 10 章：编写和使用 Web 服务
- 第 11 章：与用户通信
- 第 12 章：会话和身份验证
- 第 13 章：应用程序架构
- 第 14 章：PHP 应用程序框架

## 对象关系映射

第 6 章向您介绍了 PHP 数据对象（PDO），它为企业级 PHP 应用程序提供了一种简单的数据库抽象形式，以实现更高的可移植性、可扩展性和易维护性。

然而，本章末尾描述了 PDO 的一些局限性。正如您所发现的，PDO 永远不会为您生成 SQL 语句；它仍然依赖于您作为开发人员，从头开始编写每一条语句。这有时是非常可取的，尤其是出于性能原因；但大多数情况下，它最终会违反企业级开发的一条金科玉律：*不要重复自己*（DRY，简写）。

在本章中，您将看到，即使是使用数据库存储业务数据的相对简单的应用程序，也面临代码重复的风险，以及随之而来的诸多风险。您将看到，使用进一步的抽象——对象关系映射（ORM）——可以最大限度地减少实现最常见数据库操作所需编写的代码量。

通过了解 ORM 背后的原理，当您被介绍到企业级 PHP 6 工具包的关键部分 `DataBoundObject` 时，您不仅会了解它的作用，还会了解它在内部的工作原理。这是一个重要章节，在完全消化之前请勿继续。

### 类的类型

本书前几章为您提供了面向对象编程（OOP）原理的速成课程。您对这些章节的理解取决于您是否熟悉其他开发语言（如 Java 2 企业版（J2EE）和 .NET）中的对象。如果您熟悉，希望您能快速浏览前几页并了解“PHP 是如何做到的”。如果您不熟悉，希望您现在不仅完全精通如何在 PHP 中编写 OOP 代码，还精通为什么您*应该*这样做。

在本章中，您将处理一种特定的类——*业务类*。出于这个原因，了解您在 PHP 编程生涯中会遇到（或编写）的各种类之间的差异是有价值的。毕竟，您必须能够识别何时实际适合使用 ORM 模型（仅适用于业务类）。

### 实用类

OOP 开发的首要指导原则之一是“一切都应是对象”。换句话说，使用过程式代码——即在全局命名空间中包含函数——的想法应该被扔进您的大脑废纸篓。

这使开发人员面临一个两难困境。如果不再允许拥有函数集，那么所有那些执行加密、发送电子邮件、执行数学运算等操作的有用代码片段放在哪里呢？

答案是将它们包装在*帮助类*（也称为*实用类*）中。这样一来，您就可以将具有共同目的的方法分组在一个单独的类中，通常（但不总是）作为静态方法。例如，一个名为 `EncryptString()` 的单个全局函数可以由名为 `Encryption` 的类中的静态方法替代，因此使用 `Encryption::EncryptString()` 而不是 `EncryptString()` 来调用。

PHP 是相对较少的现代开发语言之一，在全局命名空间中拥有如此专用的方法——即不在任何类之外。PHP 中真正的 OOP 拥护者往往对这一事实深恶痛绝，并大力编写包装类以尝试消除对全局方法的需求——例如，名为 `String` 的类，以便可以使用 `$objString->getLength()` 代替 `strlen($strVar)`。

本书并没有走得那么远。毕竟，作者很高兴编写 `base64_encode($s)` 而不是 `Convert.ToBase64String(System.Text.Encoding.ASCII.GetBytes(s))`（向 .NET 致敬）；但您肯定会发现，本书确实主张将常见的开发者编写的方法分组在单个类中。

值得注意的是，这些类通常是“无数据状态”的。也就是说，它们不会在外部数据源（如文件系统、Web 服务或至关重要的数据库）中创建、读取、更新或删除数据。如果您发现自己需要一个类来执行此类操作，那么业务类是更好的选择。

### 业务类

作为一条规则，*业务类*是一个类（或实例化后的*业务对象*），它代表您的应用程序设计支持的单个（通常可更改）实体。请注意，“业务”一词具有误导性——毕竟，并非所有应用程序都是为企业编写的——但这些类无疑代表了由您的应用程序创建、读取、更新或删除的“事物”。

开发人员经常引用电子商务网站的示例，该网站有生成订单的用户，订单由购物车中装满商品的购物车以及用于支付该购物车中商品的信用卡交易组成。在这句话中，您可以找到五个潜在的业务类：

- 表示网站上用户的 `User` 类
- 表示由“用户”下订单的 `Order` 类
- 表示“用户”可能作为其“订单”一部分购买的商品的 `Product` 类
- 表示可能（也可能不会）在某个时点形成“订单”的商品临时存储区域的 `Cart` 类
- 表示用于支付“订单”的信用卡支付的 `CardPayment` 类

正如您所看到，这五个类中的每一个都在应用程序内部工作之外具有语义含义。您可以轻松地向企业中的非技术业务人员解释什么是“用户”或“订单”，而不会有太大困难。“业务对象”一词就源于此，尽管有些人使用术语*领域对象*。

### 业务对象详解

既然您大致了解了什么是业务对象，以及在应用程序中可能在哪里使用它，那么值得了解如何在实践中实现一个。在本节中，您将看到一个旨在表示系统用户的简单类的演进。

### 设计

在动手编码之前，最好先在纸上设计类。`User` 类表示假设应用程序中的单个注册用户。作为一个简单的应用程序，注册时只需要提示输入几个字段：

- 名
- 姓
- 用户名
- 密码（以加密形式存储）
- 电子邮件地址

不过，您可能希望存储每个用户的更多信息：

- 上次登录日期
- 上次登录时间
- 创建帐户日期
- 创建帐户时间

有了这个设计，您可以轻松为您的类制作早期原型。




## 原型设计

你现在可以构建一个表示设计的非常简单的类。以下源代码演示了 User 类的早期原型——你可能希望将其命名为 userv1.php，以便与本章后续构建的版本区分开来：

```php
<?php
class User {
    private $FirstName;
    private $LastName;
    private $Username;
    private $Password;
    private $EmailAddress;

    private $DateLastLogin;
    private $TimeLastLogin;
    private $DateAccountCreated;
    private $TimeAccountCreated;

    public function __call($strFunction, $arArguments) {
        $strMethodType = substr($strFunction, 0, 3);
        $strMethodMember = substr($strFunction, 3);
        switch ($strMethodType) {
            case "set":
                return($this->SetAccessor($strMethodMember,
                    $arArguments[0]));
                break;
            case "get":
                return($this->GetAccessor($strMethodMember));
        };
        return(false);
    }

    private function SetAccessor($strMember, $strNewValue) {
        if (property_exists($this, $strMember)) {
            if (is_numeric($strNewValue)) {
                eval('$this->' . $strMember . ' = ' . $strNewValue
                    . ';');
            } else {
                eval('$this->' . $strMember . ' = "' . $strNewValue
                    . '"');
            };
        } else {
            return(false);
        };
    }

    private function GetAccessor($strMember) {
        if (property_exists($this, $strMember)) {
            eval('$strRetVal = $this->' . $strMember . ';');
            return($strRetVal);
        } else {
            return(false);
        };
    }
}
?>
```

当然，没有 PHP 代码来测试，新创建的原型类没多大用处。以下是一个可以在 Web 浏览器中快速调用的示例：

```php
<?php
require("user1.php");

$objUser = new User();
$objUser->setFirstName("Ed");
$objUser->setLastName("Lecky-Thompson");
$objUser->setUsername("ed");

print "First name is " . $objUser->getFirstName() . "<br />";
print "Last name is " . $objUser->getLastName() . "<br />";
print "Username is " . $objUser->getUsername() . "<br />";
?>
```

尝试上面这段代码。你需要将其保存与类相同的目录中——希望你能看到以下相当可预测的输出：

```
First name is Ed
Last name is Lecky-Thompson
Username is ed
```

这里你已经做了一些相当巧妙的事情，因此有必要逐步过一遍类，以确保一切都说得通。

首先，请注意，本章前面讨论的所有成员变量都声明为 private 而非 public：

```php
private $FirstName;
private $LastName;
private $Username;
private $Password;
private $EmailAddress;

private $DateLastLogin;
private $TimeLastLogin;
private $DateAccountCreated;
private $TimeAccountCreated;
```

这是一种良好的做法。你不希望外部代码直接触摸或检查成员变量，因为这会将控制权从魔法发生的地方（即你的类）夺走。因此，你使用访问器方法。这些方法让你能够通过命名得当的方法来访问每个成员变量，就像你在前面的测试中看到的那样。例如，要获取“姓氏”属性（名为 LastName 的成员变量），你使用名为 getLastName() 的方法。同样，要设置它，你会使用 setLastName()。

然而，有这么多成员变量，为每个变量编写两个访问器方法会很麻烦——所以你不这么做。你利用了一种名为对象重载的 PHP 特性，它使你能够描述当代码调用一个（表面上）不存在的方法时 PHP 应该表现出的行为。

这两个物理方法 SetAccessor() 和 GetAccessor() 在所有虚拟访问器方法与你希望这些访问器方法被使用时的行为之间提供了一个有用的“映射”。在这里，并没有发生什么巧妙的事情。这些方法只是为公共成员变量提供了一个公共接口，并使用 PHP 的 eval() 函数即时编写 PHP 代码；但正如你很快将看到的，这两个方法提供了一个有用的“陷阱”，其他代码可以作为设置和获取的一部分在其中执行。

## 添加数据绑定

你的类可以工作，你已经编写了一个简短的测试来向自己证明这一点。你甚至通过定义重载的虚拟访问器方法，为自己省去了维护上的麻烦。如果将来需要添加一个额外的成员变量，你只需将其添加到类定义中，无需额外代码。

然而，至关重要的是，你的类缺少一些东西——数据绑定。目前，一旦创建新用户，它仅在该 HTTP 请求的生命周期内存在。假设用户的注册需要持续比这更长的时间，你就需要将用户存储在数据库中。

当然，做到这一点的方法是创建一个与你的对象匹配（或映射）的数据库表（或关系）。突然间，本章的标题——“对象关系映射”——有点意义了。

在创建表之前，必须先创建一个数据库来存储它。如果你严格遵循第 6 章，那么这项任务不太可能让你遇到任何问题：

```
$ /usr/local/pgsql/bin/createdb chapterseven
CREATE DATABASE
```

接下来，创建一个同名用户来访问数据库：

```
$ /usr/local/pgsql/bin/createuser -P chapterseven
Enter password for new role:
Enter it again:
Shall the new role be a superuser? (y/n) n
Shall the new role be allowed to create databases? (y/n) n
Shall the new role be allowed to create more new roles? (y/n) n
CREATE ROLE
```

如前所述，打开 PostgreSQL 控制台以创建相关数据库表：

```
$ /usr/local/pgsql/bin/psql chapterseven
Welcome to psql 8.2.4, the PostgreSQL interactive terminal.

Type:  \copyright for distribution terms
       \h for help with SQL commands
       \? for help with psql commands
       \g or terminate with semicolon to execute query
       \q to quit

chapterseven=# CREATE TABLE "system_user" (
chapterseven(#  "id" SERIAL PRIMARY KEY NOT NULL,
chapterseven(#  "first_name" character varying(64),
chapterseven(#  "last_name" character varying(128),
chapterseven(#  "username" character varying(32),
chapterseven(#  "md5_pw" character varying(32),
chapterseven(#  "email_address" character varying(128),
chapterseven(#  "date_last_login" date,
chapterseven(#  "time_last_login" time,
chapterseven(#  "date_account_created" date,
chapterseven(#  "time_account_created" time
chapterseven(# );
NOTICE:  CREATE TABLE will create implicit sequence "system_user_id_seq" for
         serial column "system_user".id
NOTICE:  CREATE TABLE / PRIMARY KEY will create implicit index "system_user_pkey"
         for table "system_user"
CREATE TABLE
chapterseven=#
```

最后一步是授予用户 ‘chapterseven’ 对表 ‘system_user’ 的全部访问权限。因此，在 PostgreSQL 控制台中仍使用以下命令：

```
chapterseven=# GRANT ALL PRIVILEGES ON "system_user" TO "chapterseven";
GRANT
chapterseven=# GRANT ALL PRIVILEGES ON "system_user_id_seq" TO "chapterseven";
GRANT
```

一切就绪。无需创建任何测试数据。你将在本章后面遇到的测试代码会为你创建一个测试条目。

## 数据要求

在遇到更多代码之前，值得详细考虑你希望从数据绑定的 User 类中得到什么。

听说过“CRUD”吗？它代表“创建、读取、更新和删除”——指的是你通常对数据绑定对象执行的四种最常见的数据操作：

- 创建 —— 显然，你希望能够通过创建类的新实例来在数据库表中创建新的用户实例。通常，你会使用各种访问器方法设置一些属性，然后调用某种方法将新对象提交到数据库，在此过程中生成相应的 INSERT 语句。





- [ ] **读取** — 你还会有兴趣能够创建 `User` 对象的新实例，这些实例代表数据库中已有的用户。例如，你可能知道你感兴趣的用户的 `id` 是 345 — 也许通常称为“用户 345”。你需要一些机制，使用该标识符实例化类，填充其属性使其反映底层数据库表条目，并使用访问器方法来检索这些属性。

- [ ] **更新** — 与前面定义的读取功能类似，你希望你的业务对象允许更新现有用户的当前属性。因此，以与先前描述的完全相同的方式实例化一个新用户后，你希望提供访问器方法来启用属性的更新，并且至关重要的是，有一种机制可以将所有这些更改提交到数据库。

- [ ] **删除** — 最后，会有这样的时候：所涉及的用户将不再需要，因此底层数据库表条目也不再需要。因此，需要一种机制来销毁对象和底层数据库表条目，前提是相关对象实例代表了一个合法的数据库条目。

## 关系映射

你会注意到，在示例原型类中，你为 `User` 对象的每个属性都提供了虚拟访问器方法 — 例如，`SetFirstName()`、`SetLastName()`、`GetFirstName()`、`GetLastName()` 等等。

这是一种良好的实践。你过去可能见过的某些替代方法使用名为 `GetField()` 和 `SetField()` 的泛型方法，它们将数据库列名作为字符串参数。虽然这足够灵活，但远非理想。任何数据库抽象的目的是消除程序员对底层数据库知识的依赖。这种方法需要知道数据库列名，而这些列名未必与你的成员变量名相同。例如，比较 `SetFirstName()` 与 `SetField("first_name")`。

事实上，为成员属性和数据库列名使用相同的名称通常是不可取的。许多 RDBMS 不赞成在关系名中使用大写字母，但在 PHP 变量和成员名中使用大写可以大大提高可读性，特别是在变量名中的每个独立英文单词的首字母大写时（一种称为 _StudleyCaps_ 的技术）。

因此，在你的数据绑定业务对象中必须有一种机制，将列名 _映射_ 到类成员变量。这样，当你的类执行 `INSERT`、`UPDATE`、`SELECT` 和 `DELETE` 语句时，它可以轻松地在列名和数据库表列名之间进行转换，反之亦然。

## 一个可运行的业务对象

根据前面的讨论，下一步是构建原型的完全可运行版本，它本身绑定到底层数据库，但在表面上几乎以完全相同的方式工作。

关键词是 _almost_。你会注意到添加了一个构造函数，允许调用者（如果已知）传递数字标识符。这使得类可以实例化以表示数据库中现有的用户，而不是全新的用户。然后，该标识符存储在一个名为 ‘id’ 的新成员变量中。构造函数还设置关系映射，该映射将关系名映射到成员变量名。

此外，注意使用 `Save()` 方法来提交更改（根据需要执行 `INSERT` 或 `UPDATE`）；以及使用 `MarkForDeletion()` 方法来允许销毁。

### 初识代码

你可以输入下面的类代码并将其保存为 `userv2.php`。这是一段很长的代码，因此请小心，确保在代码跨越本书页面宽度的地方不要意外引入任何回车或换行符：

```php
<?php
class User {
    private $ID;
    private $objPDO;
    private $strTableName;
    private $arRelationMap;
    private $blForDeletion;
    private $FirstName;
    private $LastName;
    private $Username;
    private $Password;
    private $EmailAddress;
    private $DateLastLogin;
    private $TimeLastLogin;
    private $DateAccountCreated;
    private $TimeAccountCreated;
    public function __construct(PDO $objPDO, $id = NULL) {
        $this->strTableName = "system_user";
        $this->arRelationMap = array(
            "id" => "ID",
            "first_name" => "FirstName",
            "last_name" => "LastName",
            "username" => "Username",
            "md5_pw" => "Password",
            "email_address" => "EmailAddress",
            "date_last_login" => "DateLastLogin",
            "time_last_login" => "TimeLastLogin",
            "date_account_created" => "DateAccountCreated",
            "time_account_created" => "TimeAccountCreated"
        );
        $this->objPDO = $objPDO;
        if (isset($id)) {
            $this->ID = $id;
            $strQuery = "SELECT ";
            foreach ($this->arRelationMap as $key => $value) {
                $strQuery .= "`" . $key . "`, ";
            }
            $strQuery = substr($strQuery, 0, strlen($strQuery) - 1);
            $strQuery .= " FROM " . $this->strTableName . " WHERE `id` = :eid";
            $objStatement = $this->objPDO->prepare($strQuery);
            $objStatement->bindParam(':eid', $this->ID, PDO::PARAM_INT);
            $objStatement->execute();
            $arRow = $objStatement->fetch(PDO::FETCH_ASSOC);
            foreach ($arRow as $key => $value) {
                $strMember = $this->arRelationMap[$key];
                if (property_exists($this, $strMember)) {
                    if (is_numeric($value)) {
                        eval('$this->' . $strMember . ' = ' . $value . ';');
                    } else {
                        eval('$this->' . $strMember . ' = \'' . $value . '\';');
                    }
                }
            }
        }
    }

    public function Save() {
        if (isset($this->ID)) {
            $strQuery = 'UPDATE "' . $this->strTableName . '" SET ';
            foreach ($this->arRelationMap as $key => $value) {
                eval('$actualVal = &$this->' . $value . ';');
                if (isset($actualVal)) {
                    $strQuery .= "`" . $key . "` = :" . $value . ", ";
                }
            }
            $strQuery = substr($strQuery, 0, strlen($strQuery) - 2);
            $strQuery .= ' WHERE "id" = :eid';
            $objStatement = $this->objPDO->prepare($strQuery);
            $objStatement->bindValue(':eid', $this->ID, PDO::PARAM_INT);
            foreach ($this->arRelationMap as $key => $value) {
                eval('$actualVal = &$this->' . $value . ';');
                if (isset($actualVal)) {
                    if ((is_int($actualVal)) || ($actualVal == NULL)) {
                        $objStatement->bindValue(':' . $value, $actualVal, PDO::PARAM_INT);
                    } else {
                        $objStatement->bindValue(':' . $value, $actualVal, PDO::PARAM_STR);
                    }
                }
            }
            $objStatement->execute();
        } else {
            $strValueList = "";
            $strQuery = 'INSERT INTO ' . $this->strTableName . " (";
            foreach ($this->arRelationMap as $key => $value) {
                eval('$actualVal = &$this->' . $value . ';');
                if (isset($actualVal)) {
                    $strQuery .= "`" . $key . "`, ";
                    $strValueList .= ":" . $value . ", ";
                }
            }
            $strQuery = substr($strQuery, 0, strlen($strQuery) - 2);
            $strValueList = substr($strValueList, 0, strlen($strValueList) - 2);
            $strQuery .= ") VALUES (";
            $strQuery .= $strValueList;
            $strQuery .= ");";
            $objStatement = $this->objPDO->prepare($strQuery);
            foreach ($this->arRelationMap as $key => $value) {
                eval('$actualVal = &$this->' . $value . ';');
                if (isset($actualVal)) {
                    if ((is_int($actualVal)) || ($actualVal == NULL)) {
                        $objStatement->bindValue(':' . $value, $actualVal, PDO::PARAM_INT);
                    } else {
                        $objStatement->bindValue(':' . $value, $actualVal, PDO::PARAM_STR);
                    }
                }
            }
            $objStatement->execute();
            $this->ID = $this->objPDO->lastInsertId($this->strTableName . "_id_seq");
        }
    }

    public function MarkForDeletion() {
        $this->blForDeletion = true;
    }

    public function __destruct() {
        if (isset($this->ID)) {
            if ($this->blForDeletion == true) {
                $strQuery = 'DELETE FROM ' . $this->strTableName . ' WHERE "id" = :eid';
                $objStatement = $this->objPDO->prepare($strQuery);
                $objStatement->bindValue(':eid', $this->ID, PDO::PARAM_INT);
                $objStatement->execute();
            }
        }
    }
}
```





}
public function __call($strFunction, $arArguments) {
    $strMethodType = substr($strFunction, 0, 3);
    $strMethodMember = substr($strFunction, 3);
    switch ($strMethodType) {
        case "set":
            return($this->SetAccessor
            ($strMethodMember, $arArguments[0]));
            break;
        case "get":
            return($this->GetAccessor($strMethodMember));
    };
    return(false);
}

private function SetAccessor($strMember, $strNewValue) {
    if (property_exists($this, $strMember)) {
        if (is_numeric($strNewValue)) {
            eval('$this->' . $strMember .
            ' = ' . $strNewValue . ';');
        } else {
            eval('$this->' . $strMember .
            ' = "' . $strNewValue . '";');
        }
    } else {
        return(false);
    }
}

private function GetAccessor($strMember) {
    if (property_exists($this, $strMember)) {
        eval('$strRetVal = $this->' . $strMember . ';');
        return($strRetVal);
    } else {
        return(false);
    }
}
?>

## 确保满足要求

前面这段代码相当令人生畏，也是你迄今为止在这本书中遇到的最长的一段代码。不用担心；你将在接下来的章节中更详细地了解它的工作原理。现在，重要的是先尝试运行它，以确保它满足你之前草拟的所有要求——即 CRUD（创建、读取、更新和删除）。

## 创建

尝试运行以下代码。要使其正常工作，你需要 user2.php（之前创建）和 pdoFactory.php（在第 6 章中找到）。

```
<?php

require("user2.php");
require("pdoFactory.php");

print "Running...<br />";

$strDSN = "pgsql:dbname=chapterseven;host=localhost;port=5432";
$objPDO = PDOFactory::getPDO($strDSN, "chapterseven", "chapterseven",
array());
$objPDO->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
$objUser = new User($objPDO);

$objUser->setFirstName("Steve");
$objUser->setLastName("Nowicki");
$objUser->setDateAccountCreated(date("Y-m-d"));

print "First name is " . $objUser->getFirstName() . "<br />";
print "Last name is " . $objUser->getLastName() . "<br />";

print "Saving...<br />";

$objUser->Save();

print "ID in database is " . $objUser->getID() . "<br />";

?>
```

希望你看到以下输出：

```
Running...
First name is Steve
Last name is Nowicki
Saving...
ID in database is 1
```

同时查看数据库。你应该能看到以下条目：

```
chapterseven=# SELECT first_name, last_name, date_account_created FROM
"system_user" WHERE id=1;
 first_name | last_name | date_account_created
----------------+------------+---------------------
Steve | Nowicki | 2008-05-26
(1 row)
```

请注意，你没有指定每一列，但这没关系。因为其他列没有 NOT NULL 约束，它们实际上是可选的，并且被留空。

## 读取

下面是一段更简单的代码，它使用了你刚刚插入的记录：

```
<?php
require("user2.php");
require("pdoFactory.php");
print "Running...<br />";
$strDSN = "pgsql:dbname=chapterseven;host=localhost;port=5432";
$objPDO = PDOFactory::getPDO($strDSN, "chapterseven", "chapterseven",
    array());
$objPDO->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
$objUser = new User($objPDO, 1);
print "First name is " . $objUser->getFirstName() . "<br />";
?>
```

输出应正是你所期望的：

正在运行...
名是 Steve

通过向对象传递 ID '1'，它会自动用该 ID 表示的表中的数据填充——在这里，就是你的好朋友 Steve。

## 更新

这里是另一段你可以尝试的代码，演示如何在数据库中更新 Steve 的条目：

```
<?php
require("user2.php");
require("pdoFactory.php");
print "Running...<br />";
$strDSN = "pgsql:dbname=chapterseven;host=localhost;port=5432";
$objPDO = PDOFactory::getPDO($strDSN, "chapterseven", "chapterseven",
    array());
$objPDO->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
$objUser = new User($objPDO, 1);
$objUser->setFirstName("Steven");
$objUser->Save();
?>
```

试试看。你不会看到太多有趣的输出，但你应该能看到底层数据库表已被更新，Steve 现在被称为 Steven，如下所示：

```
chapterseven=# SELECT first_name, last_name, date_account_created FROM
"system_user" WHERE id=1;
 first_name | last_name | date_account_created
------------+-----------+---------------------
 Steven     | Nowicki   | 2008-05-26
(1 row)
```

在此会话中，你可以进行多次更新——更新一列、所有列，或介于两者之间的任何内容。

## 删除

在你了解底层类的工作原理之前，这里还有一段最后的代码供你尝试：

```
<?php
require("user2.php");
require("pdoFactory.php");
print "Running...<br />";
$strDSN = "pgsql:dbname=chapterseven;host=localhost;port=5432";
$objPDO = PDOFactory::getPDO($strDSN, "chapterseven", "chapterseven",
 array());
$objPDO->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
$objUser = new User($objPDO, 1);
$objUser->MarkForDeletion();
?>
```

在浏览器中运行此代码。同样，你不会看到太多有趣的输出，但你应该能观察到在底层数据库中，Steve 已彻底消失：

```
chapterseven=# SELECT first_name, last_name, date_account_created FROM
"system_user" WHERE id=1;
 first_name | last_name | date_account_created
------------+-----------+---------------------
(0 rows)
```

练习到此为止。现在是学习一些理论的时候了。

## 了解其工作原理

希望你现在已经向自己证明了该类可以正常工作并且工作良好。这是一段大量的代码，但使用该类的代码却很小且轻量。在 PHP 最佳实践中，这一点至关重要：将内容保存在可重用的类中，并将复杂性隔离在常规应用程序逻辑之外。

以下讨论假设你了解本章前面介绍的类的第一个版本在实际中是如何工作的。如果那部分说不清楚，那么在继续之前，最好先回顾一下相关材料。

## 新成员变量

你应该注意，以下成员变量已添加到类中：

```
private $ID;
private $objPDO;
private $strTableName;
private $arRelationMap;
private $blForDeletion;
```

所有这些成员变量都声明为私有，因为它们不应该在类本身之外被访问或修改。

成员变量 $ID 顾名思义，存储分配给数据库表中行的唯一标识符。在整个类中，假设它是数字，会自动递增，并且在表中名为 'id'。如果不是，那么根据需要调整该类应该足够容易。

PDO 对象的实例存储在 $objPDO 中。它在构造函数中首次传入，并在整个类生命周期内作为成员变量保留。在你自己的应用程序中，你可能希望使用 PDOFactory 类生成 PDO 对象的单例实例，以避免对同一 DSN 进行冗余的多次连接。然后，在实例化业务类时，可以将该实例传递给它们。

由于表名不能从类名推断（例如，在此例中，类名是 'User'，但表名为 'system_user'），因此有必要使用一个成员变量专门用于存储相应数据库表的名称。这在构造函数中被不可分割地设置。

一个关联数组 $arRelationMap 用于将表名（作为数组键）映射到成员变量名（作为数组值）。成员变量名存储时不带前面的美元符号。同样，这在构造函数中设置。

最后，一个简单的布尔标志用于指示对象是否已被标记为永久销毁。当设置为 true 时，类的析构函数将在底层数据库中调用物理删除。当然，在实际中，企业级应用程序很少要求永久销毁业务记录（例如出于采用《萨班斯-奥克斯利法案》等原因）。但是，你可以决定更改析构函数中的行为——例如，在记录上设置“禁用”标志，或以其他方式禁止其将来包含在常规选择中。

## 构造函数

添加标准构造函数，可在实例化类的对象时自动执行多个操作。





首先，如前所述，定义了表名和关系映射。虽然这里是硬编码，但在更复杂的应用程序中，这些内容可能存储在单独的 PHP 结构中，甚至是 XML 中，以便于维护。

构造函数允许传入 `PDO` 对象的实例，该实例以引用方式存储在对象的成员变量集中。它还允许传入一个 ID（表示现有用户的数字标识符），尽管这是可选的。但是，如果传入了 ID，则会立即查询数据库以检索该记录的当前列值。然后，这些列值用于填充表示业务对象属性的成员变量。

此查询是通过逐步构建 `SELECT` 语句来执行的。首先，将关键字 `SELECT` 后跟一个由逗号分隔的列名列表追加。然后丢弃最后多余的逗号。接着追加关键字 `FROM`，随后跟表名，以及一个 `WHERE` 子句，要求查询由问题中的 ID 值表示的记录。请注意 `WHERE` 子句中参数化查询参数的使用；遗憾的是，此技术不能可靠地用于填充表名和列名（关系名）。

执行查询后，结果会通过相关的访问器方法逐步填充类的属性。此时，该类可被视为‘已加载’，后续对 ‘`get`’ 访问器方法的任何调用都将返回预期值。

## `Save()` 方法

`Save()` 方法是一个附加方法，旨在让你作为开发者，将对内存中类所做的更改提交到底层数据库。

这是一种半智能方法，它会判断是需要构建 `INSERT` 语句（如果是新对象且尚未分配 ID，确实如此），还是需要构建 `UPDATE` 语句（如果是现有对象）。无论哪种情况，列值都使用参数化查询语法（但不包括表名或列名）。

如果生成了 `INSERT` 语句，则使用 PDO 的 `lastInsertId()` 方法来捕获刚插入行的 ID。在使用 PostgreSQL 时，必须向该方法传递与表 ID 关联的序列名称，通常形式为 `tablename_id_seq`。确定该 ID 后，将其存储在对象的 `"ID"` 属性中，并可以使用 `getID()` 如同获取其他属性一样进行检索。

## `MarkForDeletion()` 方法

该访问器方法允许将类对象标记为在销毁时永久删除。析构函数会执行这一操作。

## 析构函数

析构函数仅在对象通过 `MarkForDeletion()` 方法标记为销毁时，删除底层数据库表项，除此之外不执行其他操作。

## 局限性

希望到现在，你已经梳理完该类，并使用这里提供的示例向自己证明它确实可行。此外，其优势应该很明显。一个相对复杂的类意味着你的应用程序代码可以保持轻量、简单且可移植。

然而，这种方法有一些局限性。

### 对数据库的影响

使用现有 ID 实例化该类以进行读取、更新或删除时，会自动执行 `SELECT` 查询，将底层数据库表项的内容直接传输到类对象中。这通常是可取的，但并非总是如此。

考虑一个工厂类中生成 `User` 对象集合或数组的假设方法。例如，你的 `Product` 类可能有一个名为 `GetOrderingUsers()` 的方法，用于返回所有订购过该产品的用户。结果可能是大约一百个 `User` 对象的数组。这固然很好，但你一次性需要所有 100 个对象的可能性有多大？几乎没有——你更可能每次分五个左右对其进行分页。

然而，仅通过使用现有 ID 创建对象，就迫使生成 `SELECT` 查询。因此，在前面的示例中，100 个 `SELECT` 查询会一次性对数据库造成压力，使其中 95 个完全多余。

数据库查询代价高昂，因此任何可以将其最小化的措施都应该（并且必须）采取。

### 不必要的查询

创建 `User` 的全新实例时，构建的 `INSERT` 语句相当智能，它只包含已设置的列；例如，不设置 `date created` 属性，则它不会出现在 `INSERT` 语句中。

不幸的是，这种技术依赖于使用 `isset()` 方法来确定属性是否已赋值。处理全新对象时这没问题；但使用现有 `User` 时，从数据库读取时会为每个属性赋值。结果是，调用 `isset()` 时会简单地回答“是的！”；因此，调用 `Save()` 会生成一个 `UPDATE` 语句，更新表中的每一列——无论该列是否实际更改。这不仅是浪费，而且如果在初始 `SELECT` 和最终执行的 `UPDATE` 之间，其他连接到数据库的应用程序提交了对其他列的更改，还可能产生不良影响。

### 代码重复

最后，再次阅读该类的源代码。该类中有多少部分实际上是特定于 `User` 对象及/或其底层表的？并不多。

因此，这段复杂代码将为应用程序中的每个业务对象重复多次，这违背了广受尊重的 DRY（不要重复自己）哲学。

## 更智能的方法

请注意，在本章中，你实际上一直在构建一个稻草人——也就是说，只为了一举推倒而构建东西。别担心。你将在本节看到，迄今为止编写的 80% 代码可以重复用于形成业务对象的第三个版本，以及一个你可以添加到工具箱中的可移植、可重用的通用类。

### 惰性实例化

你在上一节中了解到，实例化时立即执行 `SELECT` 查询会对底层数据库造成不必要的压力。解决此问题的方法被称为 `lazy instantiation`。

这意味着该类被设计为接受与之前构造函数完全相同的输入参数，但经过工程设计，以推迟因该实例化而产生的行为，直到最后一刻。

在实践中，这意味着故意将 `SELECT` 查询推迟到第一次执行 `‘get‘` 访问器调用时。那时，可以准确推断出查询绝对必要，并立即执行。此后，在类的整个生命周期内，无需再次执行该查询。

### 属性监控

过于积极的 `UPDATE` 语句无谓地针对所有列触发的问题应该容易修复。所需要的只是维护一个自类首次实例化以来已更新的列的寄存器（以数组堆栈的形式）。

在调用 `Save()` 方法时，可以查询此寄存器，从而构建的 `UPDATE` 语句被故意精简为仅包含已修改的列。

### 可重用性

最后，鼓励可移植性并最小化（甚至消除）不必要代码重复的最简单方法是，有意地将与特定业务对象无关的代码抽象化。

然后可以将该代码放入 `abstract class` 中，并为每个独特情况进行 `extend`，扩展仅包含与特定实体相关的内容——在此例中为 `User`。

### `DataBoundObject` 类

考虑到所有这些，本节将向你介绍一个新类 `DataBoundObject`，它将你已经编写的大部分代码提取出来，放入一个抽象且可重用的包中，你可以为自己的业务对象创建其子类。

它还解决了你创建的 `User` 类第二个版本的另外两个关键局限性——即对底层数据库的影响以及不必要的激进查询所带来的风险。




## 设计

在直接深入代码之前，值得思考一下生成一个合适的可重用类以满足商定的需求所涉及的内容。

通过生成一个 *抽象类*，你既在提供子类无需复制的最终方法（并且，可选地，通过 'final' 关键字，无法重载），还在声明子类 *必须* 实现的某些方法。

因此，值得考虑哪些方法和成员变量是 *通用的*（即，它们可以在抽象类中完全定义）以及哪些是 *类特定的*（因此，你期望子类来定义）。把它看作离婚协议后的财产分配；你在问，*谁得到什么？*

就成员变量而言，原始 `User` 类中的以下内容可以保留在抽象父类中：

```
private $ID;
private $objPDO;
private $strTableName;
private $arRelationMap;
private $blForDeletion;
```

这些成员变量中没有什么是类特定的；因此，它们将构成新抽象类的一部分。

相反，请考虑以下内容：

```
private $FirstName;
private $LastName;
private $Username;
private $Password;
private $EmailAddress;

private $DateLastLogin;
private $TimeLastLogin;
private $DateAccountCreated;
private $TimeAccountCreated;
```

这些变量合起来构成了 `User` 特定的成员变量，因此，应该牢固地位于子类中。

就方法而言，在 `User` 类中定义的所有方法已经完全是通用的，因为它们依赖于描述表及其列的其他成员变量。但是，构造函数中某些硬编码的细节必须移动到子类中；为此，可以在父类中定义新的抽象方法，以便在子类中进行所需实现。

牢记这一点，是时候见识一下这个类本身了。

## 代码

以下是这个类的全部代码。你应该将其保存为 databoundobject.phpm：

```php
<?php

abstract class DataBoundObject {
    protected $ID;
    protected $objPDO;
    protected $strTableName;
    protected $arRelationMap;
    protected $blForDeletion;
    protected $blIsLoaded;
    protected $arModifiedRelations;

    abstract protected function DefineTableName();
    abstract protected function DefineRelationMap();

    public function __construct(PDO $objPDO, $id = NULL) {
        $this->strTableName = $this->DefineTableName();
        $this->arRelationMap = $this->DefineRelationMap();
        $this->objPDO = $objPDO;
        $this->blIsLoaded = false;
        if (isset($id)) {
            $this->ID = $id;
        }
        $this->arModifiedRelations = array();
    }

    public function Load() {
        if (isset($this->ID)) {
            $strQuery = "SELECT ";
            foreach ($this->arRelationMap as $key => $value) {
                $strQuery .= "\"" . $key . "\",";
            }
            $strQuery = substr($strQuery, 0, strlen($strQuery) - 1);
            $strQuery .= " FROM " . $this->strTableName . " WHERE \"id\" = :eid";
            $objStatement = $this->objPDO->prepare($strQuery);
            $objStatement->bindParam(":eid", $this->ID, PDO::PARAM_INT);
            $objStatement->execute();
            $arRow = $objStatement->fetch(PDO::FETCH_ASSOC);
            foreach($arRow as $key => $value) {
                $strMember = $this->arRelationMap[$key];
                if (property_exists($this, $strMember)) {
                    if (is_numeric($value)) {
                        eval('$this->' . $strMember . ' = ' . $value . ';');
                    } else {
                        eval('$this->' . $strMember . ' = "' . $value . '";');
                    }
                }
            }
        }
        $this->blIsLoaded = true;
    }

    public function Save() {
        if (isset($this->ID)) {
            $strQuery = 'UPDATE ' . $this->strTableName . ' SET ';
            foreach ($this->arRelationMap as $key => $value) {
                eval('$actualVal = &$this->' . $value . ';');
                if (array_key_exists($value, $this->arModifiedRelations)) {
                    $strQuery .= '`' . $key . '`= :' . $value . ',';
                }
            }

            $strQuery = substr($strQuery, 0, strlen($strQuery)-2);
            $strQuery .= ' WHERE "id" = :eid';
            unset($objStatement);
            $objStatement = $this->objPDO->prepare($strQuery);
            $objStatement->bindValue(':eid', $this->ID, PDO::PARAM_INT);
            foreach ($this->arRelationMap as $key => $value) {
                eval('$actualVal = &$this->' . $value . ';');
                if (array_key_exists($value, $this->arModifiedRelations)) {
                    if ((is_int($actualVal)) || ($actualVal == NULL)) {
                        $objStatement->bindValue(':' . $value, $actualVal,
                        PDO::PARAM_INT);
                    } else {
                        $objStatement->bindValue(':' . $value, $actualVal,
                        PDO::PARAM_STR);
                    }
                }
            }

            $objStatement->execute();
        } else {
            $strValueList = "";
            $strQuery = 'INSERT INTO ' . $this->strTableName . '(';
            foreach ($this->arRelationMap as $key => $value) {
                eval('$actualVal = &$this->' . $value . ';');
                if (isset($actualVal)) {
                    if (array_key_exists($value, $this->arModifiedRelations)) {
                        $strQuery .= '`' . $key . '`,';
                        $strValueList .= ':' . $value . ",";
                    }
                }
            }

            $strQuery = substr($strQuery, 0, strlen($strQuery) - 2);
            $strValueList = substr($strValueList, 0, strlen($strValueList) - 2);
            $strQuery .= ") VALUES (";
            $strQuery .= $strValueList;
            $strQuery .= ")";

            $objStatement = $this->objPDO->prepare($strQuery);
            foreach ($this->arRelationMap as $key => $value) {
                eval('$actualVal = &$this->' . $value . ';');
                if (isset($actualVal)) {

                if (array_key_exists($value, $this->arModifiedRelations)) {
                    if ((is_int($actualVal)) || ($actualVal == NULL)) {
                        $objStatement->bindValue
                            (':' . $value, $actualVal, PDO::PARAM_INT);
                        } else {
                        $objStatement->bindValue
                            (':' . $value, $actualVal, PDO::PARAM_STR);
                        }
                    };
                };
            };

            $objStatement->execute();
            $this->ID = $this->objPDO->lastInsertId($this->strTableName . "_id_seq");
        }
    }

    public function MarkForDeletion() {
        $this->blForDeletion = true;
    }

    public function __destruct() {
        if (isset($this->ID)) {
            if ($this->blForDeletion == true) {
                $strQuery = 'DELETE FROM ' . $this->strTableName . ' WHERE
                    "id" = :eid';
                $objStatement = $this->objPDO->prepare($strQuery);
                $objStatement->bindValue(':eid', $this->ID, PDO::PARAM_INT);
                $objStatement->execute();
            };
        }
    }

    public function __call($strFunction, $arArguments) {
        $strMethodType = substr($strFunction, 0, 3);
        $strMethodMember = substr($strFunction, 3);
        switch ($strMethodType) {
            case "set":
                return($this->SetAccessor($strMethodMember, $arArguments[0]));
                break;
            case "get":
                return($this->GetAccessor($strMethodMember));
        };
        return(false);
    }

    private function SetAccessor($strMember, $strNewValue) {
        if (property_exists($this, $strMember)) {
            if (is_numeric($strNewValue)) {
                eval('$this->' . $strMember . ' = ' . $strNewValue . ';');
            } else {
                eval('$this->' . $strMember . ' = "' . $strNewValue . '";');
            }
            $this->arModifiedRelations[$strMember] = "1";
        } else {
            return(false);
        }
    }

    private function GetAccessor($strMember) {
        if ($this->blIsLoaded != true) {
            $this->Load();
        }
        if (property_exists($this, $strMember)) {
            eval('$strRetVal = $this->' . $strMember . ';');
            return($strRetVal);
        } else {
            return(false);
        }
    }
}
?>
```

正如你所见，代码变得相当长，因此在将代码输入编辑器时，请比以前更加小心，确保没有错误的换行进入。

## 示例实现

自然，抽象类如果没有与原始类相对应的实现就不太有用——也就是说，`User` 对象的新版本。你可以将以下代码命名为 userv3.phpm：

```php
<?php

class User extends DataBoundObject {

        protected $FirstName;
        protected $LastName;
        protected $Username;
        protected $Password;
        protected $EmailAddress;

        protected $DateLastLogin;
        protected $TimeLastLogin;
```




protected $DateAccountCreated;
protected $TimeAccountCreated;

protected function DefineTableName() {
    return("system_user");
}

protected function DefineRelationMap() {
    return(array(
        "id" => "ID",
        "first_name" => "FirstName",
        "last_name" => "LastName",
        "username" => "Username",
        "md5_pw" => "Password",
        "email_address" => "EmailAddress",
        "date_last_login" => "DateLastLogin",
        "time_last_login" => "TimeLastLogin",
        "date_account_created" => "DateAccountCreated",
        "time_account_created" => "TimeAccountCreated"));
}

?>

这一切都很好，但你还必须向自己证明，你的用户对象的第三个版本与第二个版本的工作方式完全相同——至少就其对外界的接口而言。这个全功能示例展示了创建、读取、更新和删除。

```php
<?php
require("pdofactory.phpm");
require("databoundobject.phpm");
require("userv3.phpm");

print "Running...<br />";

$strDSN = "pgsql:dbname=chapterseven;host=localhost;port=5432";
$objPDO = PDOFactory::GetPDO($strDSN, "chapterseven", "chapterseven",
    array());

$objPDO->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
$objUser = new User($objPDO);

$objUser->setFirstName("Steve");
$objUser->setLastName("Nowicki");
$objUser->setDateAccountCreated(date("Y-m-d"));

print "First name is " . $objUser->getFirstName() . "<br />";
print "Last name is " . $objUser->getLastName() . "<br />";

print "Saving...<br />";

$objUser->Save();

$id = $objUser->getID();

print "ID in database is " . $id . "<br />";

print "Destroying object...<br />";
unset($objUser);

print "Recreating object from ID $id<br />";
$objUser = new User($objPDO, $id);

print "First name is " . $objUser->getFirstName() . "<br />";
print "Last name is " . $objUser->getLastName() . "<br />";

print "Committing a change.... Steve will become Steven, Nowicki will become Nowickcow<br />";
$objUser->setFirstName("Steven");
$objUser->setLastName("Nowickcow");
print "Saving...<br />";
$objUser->Save();

?>
```

试一下，确保将其保存到与所需类相同的目录中。你应该会看到类似于以下的输出：

```
Running...
First name is Steve
Last name is Nowicki
Saving...
ID in database is 167
Destroying object...
Recreating object from ID 167
First name is Steve
Last name is Nowicki
Committing a change.... Steve will become Steven, Nowicki will become Nowickcow
Saving...
```

正如你所见，新形成的轻量级 User 类与你的第二个版本的工作方式完全相同，但它小得多，更易于移植，并且不会受到前面章节中指出的相同问题的影响，你将在后续讨论中亲自验证这一点。

## 了解其工作原理

由于代码之间有大量相似之处，希望快速浏览一遍不会显得太令人生畏。

首先，请注意该类被声明为抽象类：

```
abstract class DataBoundObject {
```

这告诉 PHP 期望有一个或多个抽象方法——这些方法将在父类中定义但不实现。这使你可以规定这些方法的参数数量和顺序，并强制要求任何扩展该抽象类的子类都必须实现这些方法。

接下来，你会看到声明了一些受保护的成员变量：

```
protected $ID;
protected $objPDO;
protected $strTableName;
protected $arRelationMap;
protected $blForDeletion;
protected $blIsLoaded;
protected $arModifiedRelations;
```

这些非类特定的变量将对象与底层关系数据库关联。请注意新增了一个保存数据库表名的变量，以及一个关联数组，用于指示子对象生命周期内哪些字段已被修改。

此外，成员变量被声明为受保护。这意味着，虽然在类外部不可公开访问，但它们可供父类的子类访问。

定义了两个抽象方法：

```
abstract protected function DefineTableName();
abstract protected function DefineRelationMap();
```

这些方法必须在子类中实现，其任务仅仅是设置表名和关系映射。

构造函数实际上会调用这两个方法，并（理所当然地）假设子类已实现它们：

```
public function __construct(PDO $objPDO, $id = NULL) {
    $this->strTableName = $this->DefineTableName();
    $this->arRelationMap = $this->DefineRelationMap();
    $this->objPDO = $objPDO;
    $this->blIsLoaded = false;
    if (isset($id)) {
        $this->ID = $id;
    };
    $this->arModifiedRelations = array();
};
```

你会注意到，构造函数与之前一样，接受一个 PDO 实例以及可选的标识符，该标识符表明相关实体已存在于数据库中。构造函数还将“加载”状态设置为 false，表示尚未从底层数据库读取任何数据。修改关系数组也会被重置。

新的 Load() 方法借用了之前位于构造函数中的代码，这些代码用于在实例化类时传入标识符的情况下，用数据库中的数据填充对象。通过将此类代码放入单独的方法中，它不再在实例化时自动调用。

```
public function Load() {
    if (isset($this->ID)) {
    $strQuery = "SELECT ";
    foreach ($this->arRelationMap as $key => $value) {
    $strQuery .= "\"" . $key . "\",";
    }
    $strQuery = substr($strQuery, 0, strlen($strQuery)-1);
    $strQuery .= " FROM " . $this->strTableName . " WHERE
    \"id\" = :eid";
    $objStatement = $this->objPDO->prepare($strQuery);
    $objStatement->bindParam(':eid', $this->ID,
    PDO::PARAM_INT);
    $objStatement->execute();
    $arRow = $objStatement->fetch(PDO::FETCH_ASSOC);
    foreach ($arRow as $key => $value) {
    $strMember = $this->arRelationMap[$key];
    if (property_exists($this, $strMember)) {
    if (is_numeric($value)) {
    eval('$this->' . $strMember .
    ' = ' . $value . ';');
    } else {
    eval('$this->' . $strMember .
    ' = "' . $value . '"');
    }
    }
    };
    $this->blIsLoaded = true;
    }
}
```

加载完成后，“bIsLoaded”标志将被设置为 true。这样可以防止类在子对象的剩余生命周期内不必要地调用 Load() 方法。

Save() 方法与原始数据启用的 User 类几乎保持不变。唯一的关键区别在于测试给定属性是否已被修改：

```
if (array_key_exists($value, $this->arModifiedRelations)) {
    $strQuery .= "" . $key . " = :$value, ";
}
```

这样一来，如果某个字段未被修改，则它不会包含在生成的 UPDATE 或 INSERT 语句中。当然，在填充预处理语句参数时也会应用相同的测试：

```
if (array_key_exists($value, $this->arModifiedRelations)) {
if ((is_int($actualVal)) || ($actualVal == NULL)) {
$objStatement->bindValue(':'.$value, $actualVal, PDO::PARAM_INT);
} else {
$objStatement->bindValue(':'.$value, $actualVal, PDO::PARAM_STR);
};
};
```

以这种方式进行两次测试非常重要；如果你尝试将值绑定到不存在的参数，PDO 会严格报错：

标记删除的方法、析构函数和 __call() 重载方法均与原始 User 类保持不变。

两个访问器方法已略作调整：

```
private function SetAccessor($strMember, $strNewValue) {
    if (property_exists($this, $strMember)) {
        if (is_numeric($strNewValue)) {
            eval('$this->' . $strMember . ' = ' .
            $strNewValue . ';');
        } else {
            eval('$this->' . $strMember . ' = "' .
            $strNewValue . '"');
        };
        $this->arModifiedRelations[$strMember] = "1";
    } else {
        return(false);
    };
}
```

请注意，修改关系映射现已调整，以指示相关关系已被修改。Save() 将使用这些数据，根据需要构建更简洁的 UPDATE 或 INSERT 语句：

```
private function GetAccessor($strMember) {
    if ($this->blIsLoaded != true) {
        $this->Load();
    }
    if (property_exists($this, $strMember)) {
        eval('$strRetVal = $this->' . $strMember . ';');
        return($strRetVal);
    } else {
        return(false);
    };
}
```

最后，正如你从前面的代码中所见，'get' 访问器也进行了一小处修改。类会被测试以确定“加载”标志是否设置为 true。如果不是，则在尝试求值并返回属性之前会先调用 Load() 方法。

那这个类本身呢？如 userv3.phpm 中的代码所示，它已变得更小了。首先请注意，它继承自 DataBoundObject：

```
class User extends DataBoundObject {
```

因此，你的应用程序必须确保不仅为该类本身存在 require() 语句，同样重要的是，也要为 DataBoundObject 类存在 require() 语句。





各个成员变量基本保持不变：

```
protected $FirstName;
protected $LastName;
protected $Username;
protected $Password;
protected $EmailAddress;
protected $DateLastLogin;
protected $TimeLastLogin;
protected $DateAccountCreated;
protected $TimeAccountCreated;
```

注意，这些变量被声明为‘protected’——这一点很重要，因为它允许父类直接访问和操作这些变量。

最后，您可以看到两个至关重要的抽象方法的实现：

```
protected function DefineTableName() {
    return("system_user");
}

protected function DefineRelationMap() {
    return(array(
        "id" => "ID",
        "first_name" => "FirstName",
        "last_name" => "LastName",
        "username" => "Username",
        "md5_pw" => "Password",
        "email_address" => "EmailAddress",
        "date_last_login" => "DateLastLogin",
        "time_last_login" => "TimeLastLogin",
        "date_account_created" => "DateAccountCreated",
        "time_account_created" => "TimeAccountCreated") );
}
```

这些方法在父类中被声明为抽象方法，因此在子类中，您有义务使用相同的方法名提供实现（请记住PHP区分大小写）。这两个方法都不接受任何参数。相反，将返回两个简单值——一个是表示底层数据库表名的字符串，另一个是将关系名称映射到PHP成员变量的简单关联数组。

## 益处

在结束之前，值得花一分钟反思本章所讨论方法的好处。您能够做到的是构建一个可重用、可移植、支持PDO的工具包类，让您能够片刻之间创建数据绑定的业务对象。

事实上，示例`User`类本身不包含一行SQL——它不需要这样做，因为所有标准CRUD（创建、读取、更新、删除）方法都可以按需为您生成。您的代码不仅更加轻量，您的应用程序也更具可移植性。如果您以后决定从例如MySQL移植到PostgreSQL，或者反过来，也几乎不需要做任何更改。

“抽象类”方法也很巧妙。在子类中可以做什么，您完全不受限制。前面的示例很简单，但您自然也可以添加自己的方法——其中一些可能会使用比简单CRUD操作更复杂的SQL。此外，没有什么能阻止您将关系映射委托给比PHP更易读的东西——例如XML文档。

在包含20个或更多业务对象的大型项目中，ORM开始变得非常有意义。您会疑惑自己以前是如何离开它而生存的。

## 摘要

在这个至关重要的章节中，您接触到了数据库抽象的进一步层次——即对象关系映射（ORM）。在正式接触您在企业级PHP项目中可能遇到的两种类（即业务对象和实用工具类），并学习了如何帮助识别每种类的方法之后，您接触了一个表示假设商业实体的无状态业务对象的简单示例。

在理解此类业务对象在功能层面如何工作但不保留数据之后，您接触了一种通过绑定到数据库关系（即关系数据库中的特定表）来保留数据的传统方法，并了解了它如何能够以大多适合企业级项目的方式使您对象的属性持久化，并促进持久化。

最后，通过认识到您业务对象的局限性，您构建并检查了一个可重用、可直接用于工具包的企业类，用于在您自己的项目中开发支持数据的对象。通过保持与业务特定类相同的接口，您向自己证明，将业务特定问题抽象为工具包就绪模块的子类，可以解决常见的业务问题。

在第8章中，您将发现，尽管PHP最初是作为过程式Web应用程序开发语言开发的，但它也非常适合开发事件驱动的应用程序。

## 事件驱动编程

有时，从*事件*以及如何最好地处理它们的角度来考虑应用程序很有用，而不是从传统的面向对象（OO）角度来审视该应用程序的架构设计。这并不是说您必须完全摒弃OOP方法来实现事件处理，而是要围绕与应用程序相关的事件来构建类。这种方法相当激进，但对于许多应用程序，您可能会发现它为整个项目的软件架构提供了一种极其强大的机制。

事件几乎无时无刻不在发生，事件驱动编程的一些最佳示例就是您每天使用的应用程序，例如管理电子邮件或编写文本。对于传统桌面GUI应用程序的最终用户来说，事件处理至关重要，因为这些应用程序旨在一直潜伏，直到用户执行某个操作，然后相应地做出反应。当然，如今许多基于Web的应用程序也是如此。

用户采取的几乎所有操作，甚至应用程序本身采取的操作，都可以被视为事件。一个并非由用户发起事件的比较牵强的示例是您机器的时钟。如果您想创建一个根据时间执行各种操作的应用程序，您可以将某些时间变化捕获为事件，并将其发送给相应处理它的代码段。

无论需要做什么，应用程序都有多种方式来实现解决方案，PHP 6在这方面也不例外。当然，没有新的扩展或库来处理事件，因为处理事件的方式更多是关于您如何“思考”设计应用程序，而不是关于您如何实际实现它。换句话说，它们不需要任何特殊的底层技术。让我们来看看在PHP中处理事件的一种方法。

### 理解事件

事件是应用程序可以做出反应的任何发生的事情。您几乎肯定已经编写过以某种方式处理事件的应用程序。当发生某事或某个条件突然满足时，决定在代码中采取什么操作（无论多么微不足道）都是一种事件处理形式。例如，假设您已实现了一个包含多条记录的数据库，并希望客户能够通过Web界面处理这些记录。您可能会意识到用户至少必须能够查看和更新记录，因此您可能的反应是创建用于查看和编辑记录的函数。

决定调用哪个函数完全取决于用户提供的输入。因此，您开发的界面需要呈现各种选项，并使用户能够决定想要哪些选项。用户决定后，应用程序必须通过调用正确的函数来相应地响应，这些函数将处理请求。

通常，您可能会创建一个带有两个按钮的主页，一个用于查看记录，另一个用于编辑记录。以下代码片段可能足以用作处理该选择的机制：

```
switch($_GET['action']) {
 case "edit_record":
 edit_record();
 break;
 case "view_record":
 view_record();
 break;
 }
```

如您所见，上述代码片段旨在解释来自`$_GET`（即用户请求）的信息，并根据用户请求的内容决定采取什么响应。就这样——您已经处理了由用户单击按钮这一简单动作触发的事件。

这一原则适用于您能想象到的几乎任何事件。对于使用Outlook或类似软件的人来说，系统生成的事件很常见。关于会议和截止日期的警报会基于特定事件的触发（例如，系统时钟达到某个时间）不断弹出。

当然，您如何实现处理事件的代码取决于您自己。使用switch语句并非唯一方式；任何类型的循环都能让您响应事件。在前面的示例中，if/else块同样有效。

您可能在想，关于事件的大惊小怪到底是怎么回事。毕竟，您到目前为止看到的似乎足够简单。为什么不能就此作罢呢？迄今讨论内容的问题是，如果您的应用程序在初次开发运行后发生变化或增长，您很容易最终得到一团混乱。起初只是一个简单的if语句，可能会发展到巨大的程度，使得将来任何试图理解它的尝试都变得极其困难。随着应用程序需求变得更加复杂，这有明显的影响。因此，您只应将先前提到的简单方法用于非常简单的需求，在这些需求中，您可以确信代码绝不会在任何时候发展成一套完整的企业级应用程序。

### 使用OOP处理事件

要在您自己的PHP应用程序中实现有效的事件驱动解决方案，最好是退后一步，从高层次角度确定这些应用程序应该如何运作。一种更复杂的实现事件的方法将使您能够更轻松地控制其行为



完全如你所愿，万一有需要的话。创建面向事件驱动编程的面向对象（OO）解决方案就是答案。

使用类和对象不仅有助于你保持代码整洁，还能让你构建易于扩展的架构。在当今的应用程序开发中，可扩展性是一个值得追求的目标，因此这是一件好事。还有许多其他好处，本章稍后将详细探讨。此外，考虑采用面向对象方法应该让你意识到，可能存在一个适合事件驱动模型的设计模式。

让我们构建一幅图景，了解使用面向对象方法实现恰当事件处理所需的内容。之后，你可以判断是否存在一个（或多个）适合此模型的模式。

## 设计事件驱动解决方案

设计任何事件驱动应用程序时，需要遵循三个主要步骤：

- 1. 首先确定你将如何捕获应用程序必须处理的事件。很难以抽象的方式讨论这一点，因为你捕获这些事件的方法取决于你试图捕获的确切事件类型。

- 2. 你需要一种方法来决定如何处理捕获的事件。根据你考虑的具体应用程序，在早期阶段可能值得提出一些问题。例如，值得确定将有多少个不同的事件源向你的事件处理程序发送事件。此外，你必须决定应用程序将处理单一事件类还是多个不同的事件类，以及如果需要，处理程序将如何有效地区分它们。

- 3. 最后，在确定适用于你应用程序的事件并决定如何处理它们之后，你必须设计必要的处理程序，以执行应用程序响应每个事件所需的任何任务。事件可能引发的响应类型几乎是无限的——从将用户引导到新页面，到更新记录，再到触发更多事件。所有这些都可以被视为恰当的响应。

实际上，刚才描述的就是使用反应器（或调度器类）来获取事件，并确保由正确的处理程序来处理它。让我们进一步探讨这个想法。

延续最初的示例，假设此应用程序的用户想要以某种形式编辑或查看记录。你可以预期，作为用户从表单返回的输入的结果，将请求类似下面的URL：

```
http://myserver/interface.php?event=edit
```

从URL中可以清楚地看出，触发的事件是一个编辑事件，无论这意味着什么。通过将此事件传递给调度器类，由调度器根据应用程序的要求决定调用哪些处理程序。在调度器确定要调用哪个处理程序（在此示例中，通过检查`$_GET`或`$_POST`数组键关联的值）之后，请求的实际处理由相关的处理程序完成，而不是由调度器完成。

处理程序本身就是一种面向对象编程实践。事实上，在你的应用程序中实现单个处理程序的一种有效方法是扩展一个通用的父`handler`类。使用继承可以轻松实现新处理程序，因为所有事件处理程序共享的功能可以隐藏在父类内部。例如，建立数据库连接的代码可以提供给可能需要访问此类连接的`handler`子类。

你可以先通过绘制图8-1所示的活动图，来映射此示例的预期操作流程。

![](img/a1b732997d9cb194dceec0570dc79710_200_0.png)

图8-1：用于映射预期操作流程的活动图。

这是一个相当简单的表示，但为了本示例的目的，你无需担心实现背后的细节。诚然，基于这幅图，这里可能会涉及几乎无限数量的考虑因素——安全性、数据库、处理程序注册和多个事件源只是你在这个阶段可能需要考虑的一些有效因素。

话虽如此，你现在已经具备了一个基本模型，可以据此工作，因此请查看图8-2所示的类图，该图是根据这些预期需求推导出来的。

![](img/a1b732997d9cb194dceec0570dc79710_201_0.png)

这里无需过于关注驱动用户界面的代码，因为此类选择最好由最终用户而非软件架构师做出。相反，应专注于在类图中表示调度器和处理程序。该应用程序在功能方面仅提供了最基本的骨架。相反，此示例专注于事件驱动范式及其带来的优势。

## 实现解决方案

回顾类图，你正在使用接口来实现每个事件处理程序。使用接口来强制每个处理程序中存在某些方法，对本示例至关重要，而且总体上是一种良好实践，因为它标准化了构建处理程序的方式。这一点很重要，因为你的应用程序可能会发展到第三方开发者想要添加自己的功能的程度。拥有接口能促进代码的“即插即用”特性——也就是说，使你的代码更具可扩展性。

除了可扩展性之外，还有其他几个优势有待获得。在本节介绍各个类之后，讨论将探讨使用此模型实现精细化安全性有多容易。首先，让我们逐个类查看代码。

### class.Dispatcher.php

首先，`Dispatcher`类的代码如下：

```php
<?php
require_once('class.Event_Handler.php');
require_once('class.Handler_View.php');
require_once('class.Handler_Edit.php');

class Dispatcher
{
	private $handle;

	function __construct($event_handle) {
		$this->handle = $event_handle;
	}

	function handle_the_event() {
		$name = "handler_{$this->handle}";
		if (class_exists("$name")) {
			$handler_obj = new $name($this->handle);
			$response = $handler_obj->handled_event();
			return $response;
		} else {
			echo "I can't handle this!";
		}
	}
}
?>
```

至关重要的是，构造函数负责捕获事件句柄并在类中保留它，以便稍后用于决定采取什么操作。事件句柄可能作为事件处理程序处理的一部分需要，因此让我们将此值传递给你可能调用的任何处理程序。当然，处理程序可能还需要其他信息。

作为本应用程序的一部分，在查询数据库中现有记录时，用户可能希望仅返回某个范围内的记录。当出现这种情况时，你可以简单地将分隔符参数作为事件的一部分来捕获，如下面的URL所示：

`http://myserver/interface.php?event=edit&first=2&last=7`

作为构造函数的一部分，填充一个合适的数组（例如`$event_parameters`）是一件足够简单的工作。然后可以将这些值传递给处理程序，处理程序使用它们仅返回指定范围内的记录。就本示例而言，我们只需发送实际的事件句柄即可。

`handle_the_event()`函数依赖于你和你的开发团队为任何新的事件处理程序类遵循特定的命名约定。如果有人想要为此应用程序添加功能，他或她需要知道每个处理程序的名称采用以下形式：

```php
class Handler_(Unique_Event_Handle)
{
	//Handle the event with handle Unique_Event_Handle
}
```

在这种情况下，你只有两个事件处理程序：`Handler_View`和`Handler_Edit`。我们`Dispatcher`类中的`handle_the_event()`方法在创建相关处理程序对象的实例之前，会检查该处理程序是否存在于PHP命名空间中。如果不存在，它会承认：

```
echo "I can't handle this!";
```

请注意，处理程序的实例化将事件句柄传递给构造函数，以防需要。同样，你也可以在这里传递一个值数组供处理程序处理使用，如下所示：

```
$handler_obj = new $name($this->handle);
```

*不要过于关注处理程序的操作——你只是想将在调度器中收集的任何信息传递给正确的处理程序，而无需担心它实际会如何处理这些信息。*

下一步是调用`handled_event()`方法，以提取处理程序可能因处理事件而产生的任何响应：

```
$response = $handler_obj->handled_event();
```

如你在类图中已经看到，`handled_event()`函数的存在和精确格式是通过使用接口来强制执行的。其结果是，调度器可以安全地在其已实例化的处理程序上调用`handled_event()`方法以检索响应，即使该方法只是返回`NULL`。一旦处理程序（如有）的响应已返回，调度器的工作就完成了。

现在，让我们看看处理程序这边的情况。

### interface.Handled.php

该接口确保你在可能开发的任何处理程序类中实现`handled_event()`函数。如前所述，这从调度器的角度来看很重要，但如果你确实打算迎接更大的挑战，这就是你可以强制执行任何其他可能与你的事件处理程序相关的重要方法存在的地方。此类方法随后可以在父处理程序中实现并被子类覆盖，或者简单地声明为抽象，将实现直接交给子处理程序。如以下接口代码所示，就本示例而言，你只需要求`handled_event()`方法的存在：

```php
<?php
interface Handled {
    function handled_event();
}
?>
```

`handled_event()`方法本身由你应用程序的父事件处理程序类或其子类实现。让我们先看看父事件处理程序类。





## class.Event_Handler.php

父级事件处理器类实际上更多是一个实用工具类，用于指定如何处理应用程序中可能发生的低级别事件。在此示例中，它创建一个数据库连接。common_db.inc 文件包含一个 db_connect() 函数，用于创建数据库连接——非常直接，而此类方法的具体实现留给你来完成。不过，如果你要构建规模较大的应用程序，应对这类挑战的最佳方式是使用数据库抽象层，如第 6 章所述。

当然，你可以根据要解决问题的性质，在此添加任意数量的合适方法。目前，以下是简单类 class.Event_Handler.php 的代码：

```php
<?php
require_once ("interface_Handled.php");
require_once('common_db.inc');

abstract class Event_Handler
{
    function dbconn(){
        $link_id = db_connect('sample_db');
        return $link_id;
    }

    abstract function handled_event();
}
?>
```

由于你不太可能知道每个事件将要执行什么操作，因此将 handled_event() 函数声明为抽象函数，以便各个子级处理器类可以按需自行实现。为了支持此机制，你会注意到整个类已被声明为抽象类。这对应用程序本身没有实际影响，因为你永远不会直接实例化此类——分发器将确定并直接实例化相应的子级事件处理器。

## class.Handler_View.php

这个子级处理器快速演示了你可以在典型处理器中有用地执行的代码类型。请注意，你必须提供 handled_events() 的实现，因为它已在父级处理器类中声明为抽象方法。以下代码演示了如何查看直接从数据库中提取的几条记录：

```php
<?php
require_once('class.Event_Handler.php');

class Handler_View extends Event_Handler
{
    private $handle;

    function __construct($event_handle){
        $this->handle = $event_handle;
    }

    function handled_event(){
        echo "The event, $this->handle, is now handled. <BR>
It is, I promise!<BR><BR>Your records are as follows: <BR> <BR>";
        $id = parent::dbconn();
        $result = pg_query($id, "SELECT * FROM user");
        while($query_data = pg_fetch_row($result)) {
            echo $query_data[1], " is a ", $query_data[4], "<br>";
        }
    }
}
?>
```

当然，此处提取的实际数据并不重要——这只是一个示例。如果你想尝试，只需将其连接到自己的示例数据库并按需查询，修改 SQL 语句即可。

请注意，在构造函数中，处理器仍然通过将传递给它的事件句柄保存到局部私有成员变量中来保留该句柄。在这个示例中，它实际上没有被使用，但它确实演示了如果有必要，你可以将此类参数传递给处理器。

## class.Handler_Edit.php

让我们来看看另一个子级处理器。这个编辑处理器的演示在被调用时仅向用户返回一条消息：

```php
<?php
require_once('class.Event_Handler.php');
class Handler_Edit extends Event_Handler {
    private $handle;
    function __construct($event_handle) {
        $this->handle = $event_handle;
    }
    function handled_event() {
        echo "This is event $this->handle, which is now handled - no kidding! <BR>";
    }
}
?>
```

和往常一样，你捕获事件句柄并将其本地存储。在这种情况下，处理器确实会在事件处理中使用它。诚然，handled_event() 方法的实现并无特别之处；它只是返回一条消息，确认事件已得到处理。

设置工作基本就绪。现在让我们来探讨修改应用程序是多么容易，并能以很少的努力获得出色的结果。

## 实现安全

假设你想要根据使用应用程序的人来限制其功能——这并非罕见的需求。具有此类需求的应用程序可能类似于一个 wiki，它应允许某些可信来源随意编辑内容，但将其他人限制为仅读取（而非更改）内容。

首先，在成功验证用户后，让应用程序创建一个新会话。然后，你可以用有关用户是谁的相关详细信息填充会话变量。在这种情况下，你使用一个包含用户姓名的会话变量。这意味着你现在几乎可以从应用程序中的任何地方访问当前用户的详细信息，包括在事件处理器内部。你可以使用这些信息来决定是否允许事件发生。

为希望限制使用的每个子级事件处理器类添加以下方法。如你所见，该方法只是检查会话中当前保存的作者姓名，如果提供的姓名不可接受，该方法将认为用户无权执行请求的操作：

```php
function secure_handler() {
    if ($_SESSION['name'] == "David") {
        $this->handled_event();
    } else {
        echo "Sorry ${_SESSION['name']} you are not authorized!";
    }
}
```

你需要更改分发器中的一行，以确保在处理事件时仅使用安全方法。打开文件并找到以下行：

```php
$response = $handler_obj->handled_event();
```

将上述行更改为：

```php
$response = $handler_obj->secure_handler();
```

你还需要确保坚持最初设定的设计原则，通过使用接口来强制执行子级处理器中此方法的存在。这意味着父级处理器至少必须包含 secure_handler() 函数的抽象表示。

向接口添加以下行：

```php
abstract function secure_handler();
```

无法确切知道每个事件需要哪个权限级别；不同事件之间可能会有所不同。因此，父级事件处理器不会直接实现安全处理器本身。相反，与先前讨论的常规处理器方法类似，它通过再次将方法声明为抽象方法，将其实现的责任交给其子类：

```php
abstract function secure_handler();
```

现在，每个子级事件处理器都需要根据接口实现 handled_event() 和 secure_handler() 方法。为了确定是否允许事件发生，每个事件处理器的 secure_handler() 方法可以从管理员持有的文件中检索其自身的权限设置。该文件当然会被加密（或至少存放在某个安全的地方），并且很可能由 wiki 管理员编辑，以便他或她可以更改哪些处理器可供哪些用户使用。

以下是一个小示例用户界面，它将使用安全的、面向事件的应用程序：

```php
<?php
require_once ('class.Dispatcher.php');
session_start();
?>
<html>
<head>
<title>Secure, Event Driven Record Viewer!</title>
</head>
<body>
<form method="GET" ACTION="?=<?=$_SERVER['PHP_SELF']?>">
<input type="submit" name="event" value="View" />
<input type="submit" name="event" value="Edit" />
</form>
</body>
</html>
<?php
function handle() {
$event = $_GET['event'];
$disp = new dispatcher($event);
$disp->handle_the_event();
}
$_SESSION['name'] = "Horatio";
handle();
?>
```

会话变量通常在用户登录期间设置，但为了简洁起见，让我们假设 Horatio 想要进入——因此此处硬编码了这一点。举例来说，让我们检查一下是否允许 Horatio 使用编辑功能。如果 Horatio 单击编辑按钮，你理所当然地期望看到图 8-3 所示的输出。




![](img/a1b732997d9cb194dceec0570dc79710_208_0.png)

图 8-3：如果 Horatio 单击“Edit”按钮，输出如下。

由此可见，Horatio 尝试编辑记录的行为被阻止了，因为只有 David 可以编辑记录。

现在，这种方法的威力应该变得更加清晰了。您已经通过安全性的示例了解了修改应用程序有多容易，但这种方法可以应用于可能出现的任何数量的新需求。

## 暂停思考

设计一个架构良好的、企业级的、事件驱动的应用程序时，必须仔细考虑许多问题。例如，对事件处理方法的改进可能包括某种处理程序注册机制。这意味着，当用户登录网站时（在此情况下，登录将是应用程序捕获的一个事件），应用程序可以自动检查哪些处理程序可供用户使用。这是通过使用默认处理程序实现的，默认处理程序从数据库中检索用户允许的处理程序列表，并将该信息返回到表现层。

拥有这些信息后，表现层就知道要为用户呈现哪些按钮。管理员将获得许多按钮，而访问者可能只有一个“View”按钮。如果访问权限仅限于“View”按钮，则不受信任的用户恶意修改其无权访问的任何内容的可能性很小。

在为下一个大合同使用此方法之前，需要考虑的第二个问题（与第一个问题密切相关）是如何让调度程序首先包含正确的 PHP 项目文件。因为调度程序实例化事件处理程序，所以必须包含正确的类。在本示例中，您只需包含所需的每个处理程序类。对于更大的应用程序，这种方法会很浪费，因为您可能会包含一百个类，但只使用其中一个。

纠正此问题的一种方法是将某些处理程序标记为默认可用，其余处理程序则按用户提供。数据库中存储的每个用户将（在其他属性中）包含一个字段，其中包含可供该用户使用的处理程序列表。可以使用此信息在向用户界面添加相关按钮的同时，自动将相关处理程序包含到调度程序中。

最后，您的各种事件可能由不同实体触发，因此您可能希望添加功能来确定是哪个实体在调用该事件，并根据该判断返回相应的响应。例如，如果您希望根据调用事件的实体，以机器可读的 XML 格式或人类可读的 HTML 格式返回某些数据，这将非常有用。

一个可能令您感兴趣的设计模式是反应器模式。它处理多源、企业级事件处理，如果您认真打算使用事件，这绝对值得一看。请记住，可能存在一个符合您需求的设计模式。反应器模式与您在本章中所做的工作非常相似，但增加了功能，使您的处理程序能够轻松区分事件来源。有关更多信息，请参阅 Douglas C. Schmidt、Michael Stal、Hans Rohnert 和 Frank Buschmann 合著的《面向模式的软件架构，第 2 卷：并发和网络对象模式》（Wiley, 2000）。

## 摘要

本章作为 PHP 中事件驱动编程的介绍。您现在应该很好地了解如何使用简单的 OOP 实现事件驱动范式。

创建事件驱动的应用程序是针对特定问题的工作，应高度关注目标应用程序运行的环境。事件驱动编程在计算的许多领域都有应用，但良好的候选者通常是具有图形用户界面的程序。

最后，通过本章的讨论，您已经了解如何通过使用事件驱动编程范式来设计应用程序，从而有效地补充 OOP 固有的威力和优雅性。

第 9 章将探讨在应用程序中实现有效的日志记录和调试机制，以帮助您和您的开发团队在项目的开发和测试阶段。

## 日志记录和调试

在您构建的每个应用程序中，强大的日志记录和调试机制可以节省您数小时的工作，避免尝试追踪可能出现的问题。

日志可用于帮助您分析无法通过 Web 服务器日志获得的历史使用模式，例如服务器负载、执行的特定 SQL 语句或否则不会被捕获的应用程序特定消息。

调试机制使您可以检查变量的值，查看正在执行哪些条件循环，或以其他方式确定应用程序在运行时的状态，而无需在代码中散布需要在部署前删除的 `print` 语句。在阅读完本章的代码后，您将拥有一组类，这些类应该成为您参与的每个项目的一部分。

## 创建日志记录机制

日志记录的主要目的是使您能够了解应用程序在过去某个时间点的运行情况或性能表现。编写良好的日志将使您能够对系统行为进行历史分析，以确定是否需要进行更改。

## 简单文件日志记录

处理日志记录的最简单方法是将信息写入文件。通常，运行 Web 服务器进程的用户 ID 没有写入文件系统所需的访问权限，除了临时目录（大多数 UNIX 系统上的 /tmp），但这不一定是保存重要应用程序日志文件的最佳位置。为了允许 Web 服务器用户写入文件，请创建一个专用目录来存储日志文件：

在应用程序文档根目录之上创建一个名为 logs 的文件夹，并确保 Web 服务器用户对该文件夹具有写入权限。（在 UNIX 系统上，使用 chmod 744 和 chown nobody，或您的 Apache 用户的名称。Windows 用户应查阅其 Windows 版本的相关文档。）

```
/www
|
+-----.mysite
|
+----htdocs
|     |
|     +----images
|     |
|     +----css
|
+----.logs
```

## 示例文件系统布局

要在 PHP 中写入文件，请使用 fopen() 获取文件句柄并指定要以写入方式打开文件。使用 fwrite() 将数据写入文件，并使用 fclose() 关闭文件。以下代码定义并演示了一个名为 logMessage() 的简单方法，该方法使用这些基本方法向预定义日志文件写入内容：

```php
<?php
function logMessage($message) {
    $LOGDIR = '/www/mysite/logs/'; //chmod 744 and chown nobody
    $LogFile = $LOGDIR . 'mysite.log';
    $hFile = fopen($LogFile, 'a+'); //open for appending, create
                                     //the file if it doesn't exist

    if (! is_resource($hFile)) {
        printf("Unable to open %s for writing. Check file permissions.", $LogFile);
        return false;
    }

    fwrite($hFile, $message);
    fclose($hFile);

    return true;
}

logMessage("Hello, log!\n");
?>
```

如果运行此代码，并且在 $LOGDIR 目录上正确设置了所有权限，您应该会在 mysite.log 文件中看到消息 Hello, log!。对于最基本的需求，此函数可能就足够了；但对于实际应用程序，您将希望跟踪的内容不仅仅是消息。日志应是“可机器解析”的文件，这意味着您应该能够使用分析其中包含的信息的单独应用程序来处理日志数据。日志应包括每条消息的日期和时间、消息的严重性或重要性的某种指示，以及关于生成消息的应用程序模块的备注。

## Logger 类

以下代码示例中的类提供了一种 OO 机制，用于生成比前一节代码创建的日志文件更详细的日志文件。创建一个名为 class.Logger.php 的文件。该文件将包含 Logger 类，该类使您能够以制表符分隔的格式将信息写入服务器上的文本文件，跟踪时间戳、日志级别（即消息的严重性）、消息本身以及可选的模块名称。模块名称可以是任何有助于标识生成消息的应用程序部分的字符串。Logger 类的代码如下：

```php
<?php
class Logger {
    private $hLogFile;
    private $logLevel;

    // Log Levels. The higher the number, the less severe the message
    // Gaps are left in the numbering to allow for other levels
    // to be added later
    const DEBUG = 100;
    const INFO = 75;
    const NOTICE = 50;
    const WARNING = 25;
    const ERROR = 10;
    const CRITICAL = 5;

    // Note: private constructor. Class uses the singleton pattern
    private function __construct() {
        // This is pseudo code that fetches a hash of configuration information
        // Implementation of this is left to the reader, but should hopefully
        // be quite straightforward.
        $cfg = Config::getConfig();

        /* If the config establishes a level, use that level,
        otherwise, default to INFO */
        $this->logLevel = isset($cfg['LOGGER_LEVEL']) ?
            $cfg['LOGGER_LEVEL'] :
            Logger::INFO;

        // We must specify a log file in the config
        if (! isset($cfg['LOGGER_FILE']) && strlen($cfg['LOGGER_FILE'])) {
            throw new Exception('No log file path was specified ' .
                'in the system configuration.');
        }
    }
}
?>
```




```php
$logFilePath = $cfg['LOGGER_FILE'];

//Open a handle to the log file.  Suppress PHP error messages.
//We'll deal with those ourselves by throwing an exception.
$this->hLogFile = @fopen($logFilePath, 'a+');

if(! is_resource($this->hLogFile)) {
    throw new Exception("The specified log file $logFilePath " .
        'could not be opened or created for ' .
        'writing.  Check file permissions.');
}

//Set encoding type to ISO-8859-1
stream_encoding($this->hLogFile, 'iso-8859-1');
}

public function __destruct() {
    if(is_resource($this->hLogFile)) {
        fclose($this->hLogFile);
    }
}

public static function getInstance() {
    static $objLog;

    if(!isset($objLog)) {
        $objLog = new Logger();
    }

    return $objLog;
}

public function logMessage($msg, $logLevel = Logger::INFO, $module = null) {
    if($logLevel > $this->logLevel) {
        return;
    }

    /* If you haven't specified your timezone using the
     * date.timezone value in php.ini, be sure to include
     * a line like the following.  This can be omitted otherwise.
     */
    date_default_timezone_set('America/New_York');

    $time = strftime('%x %X', time());
    $msg = str_replace("\t", ' ', $msg);
    $msg = str_replace("\n", ' ', $msg);

    $strLogLevel = $this->levelToString($logLevel);

if(isset($module)) {
    $module = str_replace("\t", '', $module);
    $module = str_replace("\n", '', $module);
}

//logs: date/time loglevel message modulename
//separated by tabs, new line delimited
$LogLine = "$time\t$strLogLevel\t$msg\t$module\n";
fwrite($this->hLogFile, $LogLine);
}

public static function levelToString($LogLevel) {
    switch ($LogLevel) {
        case Logger::DEBUG:
            return 'Logger::DEBUG';
            break;
        case Logger::INFO:
            return 'Logger::INFO';
            break;
        case Logger::NOTICE:
            return 'Logger::NOTICE';
            break;
        case Logger::WARNING:
            return 'Logger::WARNING';
            break;
        case Logger::ERROR:
            return 'Logger::ERROR';
            break;
        case Logger::CRITICAL:
            return 'Logger::CRITICAL';
            break;
        default:
            return '[unknown]';
    }
}

?>

```

这个类看起来应该足够简单。请注意，你创建了一个私有构造函数，以避免在页面请求执行期间多次打开文件句柄。`getInstance()` 方法允许使用该类的代码获取其实例。这被称为 *单例* 模式，你在第 4 章中首次见过。

文件的前几行建立了一些日志级别常量。这些常量使你能够控制记录哪些信息。在开发应用程序的第一个版本时，为了调试目的，你可能希望记录大量信息来帮助跟踪错误。当应用程序最终投入生产时，你希望记录较少信息以节省系统资源。记录较少信息还能提高信噪比，即在给定数量的日志行中包含更多有用信息。当应用程序在生产环境中运行时，开发期间使用的大部分调试信息在尝试跟踪问题时将没什么用，这使得在日志中找到这些问题更加困难。

在构造函数中，从全局配置信息数组中获取了两个信息：日志文件名和当前调试级别。对于本示例，你可以假设每个应用程序只有一个日志文件。本章稍后你将学习如何扩展此类，以提供更多功能和更大的灵活性，关于信息记录的位置。

将日志级别存储在一个私有成员变量中，稍后将用于确定写入日志文件的信息。会检查日志文件名以确保其有值，并且 Web 服务器用户确实可以打开或创建日志文件以进行追加。fopen() 的 a+ 参数意味着 "以追加模式打开此文件，如果不存在则创建它"。将文件句柄作为另一个私有成员变量存储。如果出于任何原因无法创建有效的文件句柄，构造函数会抛出异常。

任何尝试调用 Logger::getInstance() 的操作都应包裹在 try...catch 块中，因为可能会因日志文件权限不正确或存储该日志文件的卷上磁盘空间不足而导致失败。如果发生这种情况，整个应用程序不应因日志记录器而停止工作。你应该捕获此异常并采取适当措施，例如向系统管理员发送电子邮件。（有关可使用的健壮电子邮件类，请参见第 11 章。）

这个类还带有一个析构函数，如果文件句柄是打开状态，则将其关闭。如果文件路径无效，则文件句柄不会是有效资源。尽管异常是在构造函数中抛出的，但当对象从内存中释放时，仍然会调用析构函数。因此，添加了一些代码，以确保在尝试关闭最初从未成功打开的文件句柄时不会产生另一个错误。

Logger 类中的 getInstance() 方法具有一个静态变量，用于在多次调用 getInstance() 方法之间存储该类的实例。第一次调用该方法时，该变量为 null，从而创建 Logger 的新实例。如果日志文件路径无效，则异常会冒泡到此方法。在对该方法的后续调用中，变量将存储在第一次调用期间创建的引用，并返回该原始实例。在这里使用单例模式，可以在创建和销毁 Logger 类实例时节省打开和关闭文件句柄所需的系统资源。

logMessage() 方法完成所有艰苦的工作。它接受消息文本、日志级别和可选的模块名。如果当前系统范围的日志级别配置参数（在构造函数中分配给私有成员变量 $logLevel）至少与该函数第二个参数中指定的日志级别一样大，则会创建一条日志条目。如果当前应用程序日志级别小于第二个参数中指定的级别，则不会创建任何条目。这样，你可以控制写入日志的内容。

对于发送到 logMessage() 方法的每条消息，都应提供一个日志级别以指示消息的严重性。例如，如果你只是为了调试目的将某个变量的内容打印到日志中，那么 logMessage() 的第二个参数应该是 Logger::DEBUG。然后，在将代码部署到生产服务器时，你应该将 $cfg['LOGGER_LEVEL'] 参数设置为 Logger::WARNING 或更高级别。这样将阻止调试消息被打印到日志中，节省 CPU 周期，并将日志内容限制在不同严重程度的错误上。

logMessage() 方法在第 84 行使用 PHP 的 strftime() 函数生成时间戳，该函数将格式字符串作为第一个参数，UNIX 时间戳作为第二个参数。代码示例中使用的格式字符串采用系统默认的短日期表示（%x）和系统默认的时间表示（%X）。例如，对于位于美国的服务器，strftime('%x %X', time()) 的输出格式为 07/14/2008 03:55:25（即 2008 年 7 月 14 日凌晨 3:55:25）。如果你的计算机位于世界其他地方，日期表示将按你所在位置进行相应显示（在这种情况下，这很可能是 14/07/2008）。

> 如果要更精确地控制日志中时间戳的格式，请参阅 www.php.net/strftime 上 `strftime()` 函数的文档。如果你的日志需要比一秒更高的时间分辨率，可以使用 `microtime()` 函数获取毫秒。同样，请参阅文档以了解如何使用该函数的更多信息。

请注意，PHP 6 在确定当前时区方面比早期版本更严格。Web 服务器通常不与程序员位于同一时区，且许多服务器没有为其所在位置设置正确的时区。因此，每个应用程序都应在 `php.ini` 中指定其时区，或通过使用 `date_default_timezone_set()` 函数来指定，后一种选项通常作为每个页面请求开始时应用程序配置的一部分调用（而不是像示例代码中那样按特定函数基础调用）。

在创建时间戳的文本表示后，`logMessage()` 必须对消息进行一些格式化。因为你希望创建易于机器读取的日志文件，所以用制表符（`\t`）分隔日志每行中的字段。每条日志条目由换行符（`\n`）分隔。因此，必须移除消息中可能存在的任何制表符或换行符，因为这些会损坏日志文件，并使日志分析器难以解析。将制表符替换为四个空格（大多数文本编辑器中制表符占用的默认字符数），并将换行符替换为空格。如果 `$module` 参数有值，则也应进行相同的替换。如果正在记录的信息中制表符和换行符具有意义且无法丢弃，请考虑将它们替换为标准约定 `\t` 和 `\n`，这样在分析数据时可以还原原始值。

这里唯一有趣的是将数值日志级别常量转换为字符串。因为 PHP 将常量视为其实际数值，所以没有简单的方法将常量的名称转换为该常量名称的字符串表示。因此，字符串表示被硬编码到 `levelToString()` 方法中。`switch` 语句遍历常量并返回常量的名称。虽然 `break` 语句在技术上并非必要，但为了清晰起见而添加了它们。实际上并非必要的是将此方法声明为 static，但由于它不依赖于任何成员变量，并且你可能需要在此类之外的代码中打印日志级别，因此将方法声明为 static 可以轻松编写如 `echo Logger::levelToString($cfg['LOGGER_LEVEL'])` 之类的代码。

以下代码示例展示了如何在实际应用程序中使用 Logger 类：

```
<?php
require_once('class.Config.php');
require_once('class.Logger.php');

//Again, the implementation of this class is left to the user, but an
//example of how it could work will be provided in the code download
//that accompanies the book on wrox.com
Config::addConfig('LOGGER_FILE', '/var/log/myapplication.log');
Config::addConfig('LOGGER_LEVEL', Logger::INFO);

$log = Logger::getInstance();
```





if(isset($_GET['fooid'])) {
    //not written to the log - the log level is too high
    $log->logMessage('A fooid is present', Logger::DEBUG);
    //LOG_INFO is the default so this would get printed
    $log->logMessage('The value of fooid is ' . $_GET['fooid']);
} else {
    //This will also be written, and includes a module name
    $log->logMessage('No fooid supplied',
        Logger::CRITICAL,
        "Foo Module");
    throw new Exception('No fooid id!');
}
?>

如果设置了 `$_GET['fooid']`，则会进行两次对 `logMessage()` 的调用，但由于配置的日志级别，只有一条消息会实际写入文件。日志内容将类似如下：

```
03/17/04 03:58:42   Logger::INFO   The value of fooid is 25
```

在此处，您可以看到时间戳、消息的日志级别以及消息本身。

如果未设置 `$_GET['fooid']`，则会看到以下日志条目：

```
03/19/04 05:30:07   Logger::CRITICAL   No fooid passed from
http://localhost/testLogger.php   Foo Module
```

在此示例中，`testLogger.php` 页面未能将 `fooid` 传递给调用记录器的页面，因此 `Logger::CRITICAL` 错误被写入了文件。

## 扩展 Logger 类

将日志记录到文本文件是存储日志数据的一种非常有用的方法。有成千上万的实用程序可用于解析和分析这些数据——从简单的 UNIX 实用程序（例如 `sed` 和 `grep`）到花费数万美元的复杂商业日志分析软件包。然而，有时文本文件并不是最方便的存储介质。您可能希望使用关系数据库或与平台的系统记录器集成，以集中管理所有应用程序日志。此外，目前为止开发的 `Logger` 类无论在应用程序的哪个位置调用，都只能写入单个文件。在多种情况下，您可能希望为应用程序的不同部分或不同任务保留独立的日志。在本节中，您将扩展 `Logger` 类，以便它能与任何数据存储介质集成，并在单个应用程序中支持多个日志。

在第 6 章中，您学习了如何通过简单更改 PDO 类的连接字符串来连接到完全不同的数据库后端。通过使用 "mysql:host=localhost;dbname=mydb" 进行连接，您可以连接到本地计算机上运行的 MySQL 数据库并使用名为 "mydb" 的数据库。要连接到 PostgreSQL 数据库，连接字符串类似于 "mysql:host=localhost;dbname=yourdb"，它连接到本地计算机上的 PostgreSQL 数据库实例并使用名为 "yourdb" 的数据库。使用这种通用的连接字符串语法建立连接后，无论连接到哪种 RDBMS，PDO 类的其他使用方式均相同。您可以使用非常类似的结构，使 Logger 类能够连接到任何类型的存储介质。

增强型 Logger 类的目标是使用类似的语法来建立到日志数据存储介质的连接。由于您可以使用不同的存储介质，因此还应该能够为应用程序的不同部分存储不同的日志。新的 Logger 类应支持某种形式的日志连接“注册表”。例如，您应该能够有一个名为“errors”的日志和一个名为“queries”的日志，它们将分别存储错误消息和 SQL 语句。以下示例代码展示了您应该能够使用重新设计的类执行的操作：

```
<?php
Logger::register('errors', 'file:///var/log/error.log');
Logger::register('app',
    'pgsql://postgres@db/errors?table=applog&timestamp=datalog&' .
    'msg=smsg&level=slevel&module=smod');

$objQLog = Logger::getInstance('app');

$sql = "SELECT * FROM foo";
$objQLog->logMessage("Selecting all foos");

try {
    Database->getInstance()->select($sql);
} catch (DBQueryException $e) {
    $objErrLog = Logger::getInstance('errors');
    $objErrLog->logMessage($e->getMessage(), LOGGER_CRITICAL);
}
?>
```

在展示驱动它的新类之前先展示这段代码可能会有些令人困惑，但有时，先了解您希望如何使用类，会使设计类变得更容易。在实际应用程序中，您会将前两行放在一个全局包含的文件中。这两行建立了两个不同的日志：

- app——app 日志将其日志消息存储在 PostgreSQL 数据库中，表名为 applog，并使用为时间戳、消息、日志级别和模块指定的字段名。
- errors——错误日志将是位于 /var/log/error.log 的文本文件。

在应用程序的主体部分，您会将大部分消息存储在 app 日志中以供日后分析。发生的任何错误都将存储在 errors 日志中，该日志是一个文本文件。之所以对错误使用文本文件，是因为其中一种错误可能是无法连接到数据库。

## 解析连接字符串

创建新 `Logger` 类的第一步是能够解析形式为 `scheme://user:password@host:port/path?query#fragment` 的字符串，以便实现此目的。`parse_url()` 函数接受这种通用形式的字符串，并返回包含 URL 中现有元素的数组。（数组键与前面字符串中使用的名称相同。）如果一个或多个元素不存在，则不会向数组中添加带有该键的任何项目（而不是为该键添加 null 条目。）

请参阅以下示例：

```php
$url = "ftp://anonymous@ftp.gnu.org:21/pub/gnu/gcc";
$arParts = parse_url($url);
var_dump($arParts);

//prints out:
Array (
    [scheme] => ftp
    [user] => anonymous
    [host] => ftp.gnu.org
    [port] => 21
    [path] => /pub/gnu/gcc
)
```

请注意，密码、查询和片段键不会出现在数组中，因为它们在 URL 中也没有出现。

## 重新设计 Logger 以使用连接字符串

`Logger` 将使用此数组中的 `scheme` 部分来确定要使用的日志后端。`register()` 方法用于建立新连接，并以规范名称和 URL 作为参数。由于示例代码中 `register()` 方法是以静态方式调用的，您需要使用某种中间函数，使 `register()` 和 `getInstance()` 方法都能访问同一组信息。

以下代码展示了新的 `register()` 方法以及重新设计的 `getInstance()` 方法和构造函数。事实上，此代码示例代表了新 `Logger` 类的全部内容。更改过的部分已加以突出显示。将这些更改保存到 `class.Logger-enhanced.php`：

```php
<?php

class Logger {
private $LogFile;
private $logLevel;

// Log Levels. The higher the number, the less severe the message
// Gaps are left in the numbering to allow for other levels
// to be added later
const DEBUG    = 100;
const INFO     = 75;
const NOTICE   = 50;
const WARNING = 25;
const ERROR = 10;
const CRITICAL = 5;

//Note: private constructor. Class uses the singleton pattern
private function __construct() {

}

public static function register($logName, $connectionString) {

    $urlData = parse_url($connectionString);

    if(! isset($urlData['scheme'])) {
        throw new Exception("Invalid log connection string $connectionString");
    }

    @include_once('Logger/class.' .
        $urlData['scheme'] . 'LoggerBackend.php');

    $className = $urlData['scheme'] . 'LoggerBackend';

    if(! class_exists($className)) {
        throw new Exception('No logging backend available for ' .
            $urlData['scheme']);
    }

    $objBack = new $className($urlData);

    Logger::manageBackends($logName, $objBack);
}

public static function getInstance($name) {
    return Logger::manageBackends($name);
}

private static function manageBackends(
    $name,
    LoggerBackend $objBack = null) {

    static $backEnds;

    if(! isset($backEnds)) {
        $backEnds = array();
    }

    if($objBack == null) {
        //we must be retrieving
        if(isset($backEnds[$name])) {
            return $backEnds[$name];
        } else {
```






```
throw new Exception("The specified backend $name was not " .
    'registered with Logger.');
}

} else {
    //we must be adding
    $backEnds[$name] = $objBack;
}
}
```

```php
public static function levelToString($logLevel) {
    switch ($logLevel) {
        case Logger::DEBUG:
            return 'Logger::DEBUG';
            break;
        case Logger::INFO:
            return 'Logger::INFO';
            break;
        case Logger::NOTICE:
            return 'Logger::NOTICE';
            break;
        case Logger::WARNING:
            return 'Logger::WARNING';
            break;
        case Logger::ERROR:
            return 'Logger::ERROR';
            break;
        case Logger::CRITICAL:
            return 'Logger::CRITICAL';
            break;
        default:
            return 'unknown';
    }
}
?>
```

在前面的代码中，Logger 引入了定义名为 LoggerBackend 的抽象类的文件，该类作为执行向给定日志机制写入实际工作的那些类的基类。Logger 的构造函数现在为空，但仍声明为私有，以防止在 getInstance() 方法之外实例化它。

新的静态方法 register() 负责根据第二个参数中指定的 URL 的方案部分实例化一个 LoggerBackend 对象。为此，它会调用 parse_url() 来确定方案。如果 URL 中没有方案，register() 会抛出一个异常。如果存在方案，则尝试 include_once 一个名为 Logger/class.[scheme]LoggerBackend.php 的文件，并通过传递 $urlData 数组来实例化其中包含的类。如果找不到文件，代码会抛出一个异常。这里使用 include_once 而不是 require_once，因为如果使用 require_once 且找不到文件，则会抛出致命异常，并且应用程序执行将终止。

如果指定的 LoggerBackend 类已正确实例化，则将新实例连同传递给 register() 第一个参数中指定的规范名称一起传递给私有函数 manageBackends()。此函数存在的原因是 Logger 的所有公共方法现在都是静态的。因此，该类无法使用任何成员变量来存储已实例化的后端对象。

manageBackends() 包含一个替代类成员的静态变量。如果函数有两个参数，它会使用 $name 参数作为键将 LoggerBackend 对象存储在 $backEnds 数组中。如果只指定一个参数（即 $name 参数），manageBackends() 将返回存储在 $name 中的 LoggerBackend 对象（如果存在）。

新的 getInstance() 方法不再返回 Logger 对象，而是返回一个已实例化的 LoggerBackend。它通过仅用一个参数调用 manageBackends() 来实现此目的，该参数是所请求的特定日志的规范名称。如果指定的日志之前未注册，或在 register() 期间无法实例化，manageBackends() 会抛出一个异常，该异常会向上冒泡到 getInstance()。

### LoggerBackend 类

manageBackends()、register() 和 getInstance() 方法均与 LoggerBackend 对象交互。该类提供一个具体构造函数（存在且可调用的构造）以及一个名为 logMessage() 的抽象方法，您可能还记得它来自原始 Logger 类。后者方法在参数数量和类型方面与前面展示的代码保持不变。

但是，在 LoggerBackend 类中，logMessage() 方法是抽象的——没有实际的函数体，只有必须由继承自 LoggerBackend 的类实现的函数声明。该类的构造函数获取 parse_url() 的数组输出，并将其存储在受保护的成员变量中。LoggerBackend 类未定义其他方法。

将以下内容保存为 Logger/class.LoggerBackend.php：

```php
<?php
abstract class LoggerBackend {
	protected $urlData;

	public function __construct($urlData) {
		$this->urlData = $urlData;
	}

	abstract function logMessage($message, $logLevel = Logger::INFO, $module);
}
?>
```

类本身应声明为抽象类，因为它包含一个抽象方法，并且 LoggerBackend 的实例没有实际用途。只有 LoggerBackend 的子类才会执行任何实际工作。

### 子类化 LoggerBackend

为了让改进后的 Logger 类能够执行任何操作，您需要创建至少一个 LoggerBackend 的子类。由于您已有可将信息记录到文件的代码，因此这将是要首先创建的最简单的 LoggerBackend 子类。

# 第二部分：学习高级开发技术

创建一个名为 class.fileLoggerBackend.php 的文件（注意文件名中的大小写），并输入以下代码：

```php
<?php

require_once('class.LoggerBackend.php');

class fileLoggerBackend extends LoggerBackend {

    private $logLevel;
    private $hLogFile;

    public function __construct($urlData) {

        parent::__construct($urlData);

        $this->logLevel = Config::getConfig('LOGGER_LEVEL');

        $logFilePath = $this->urlData['path'];

        if(! strlen($logFilePath)) {
            throw new Exception('No log file path was specified '
                .'in the connection string.');
        }

        print "Logging data to $logFilePath";

        //Open a handle to the log file.  Suppress PHP error messages.
        //We'll deal with those ourselves by throwing an exception.
        $this->hLogFile = @fopen($logFilePath, 'a');

        if(! is_resource($this->hLogFile)) {
            throw new Exception("The specified log file $logFilePath "
                .'could not be opened or created for '
                .'writing. Check file permissions.');
        }

        //Set encoding type to ISO-8859-1
        stream_encoding($this->hLogFile, 'iso-8859-1');
    }

    public function logMessage($msg, $logLevel = LOGGER_INFO, $module = null) {
        if($logLevel > $this->logLevel) {
            return;
        }

        /* If you haven't specified your timezone using the
        date.timezone value in php.ini, be sure to include
        a line like the following.  This can be omitted otherwise.
        */
        date_default_timezone_set('America/New_York');
        $time = strftime('%x %X', time());
        $msg = str_replace("\t", ' ', $msg);
        $msg = str_replace("\n", '', $msg);

        $strLogLevel = Logger::levelToString($logLevel);

        if(isset($module)) {
            $module = str_replace("\t", ' ', $module);
            $module = str_replace("\n", ' ', $module);
        }

        //logs: date/time loglevel message modulename
        //separated by tabs, new line delimited
        $logLine = "$time\t$strLogLevel\t$msg\t$module\n";
        fwrite($this->hLogFile, $logLine);

    }
}
?>
```

这段代码的大部分内容您应该都很熟悉。它几乎是逐字从原始 `Logger` 类中摘录的。`fileLoggerBackend` 类将响应使用 `file://` 方案注册的日志。它将日志写入 `parse_url()` 数组的路径组件中指定的文件。要注册此类型的日志，URL 应类似于 `file:///var/log/app.log`。请注意，这些组件是 `file://`（以两个正斜杠结尾）和 `/var/log/app.log`（以一个正斜杠开头）。文件方案中有三个初始正斜杠。

要使用此后端，您可以编写如下代码（就像您在本节开头看到的一样）：

```php
<?php
require_once('class.Logger.php');
Logger::register('app', 'file:///var/log/applog.log');
$log = Logger::getInstance('app');
$log->logMessage('This is a new log message!', LOGGER_CRITICAL, 'test');
?>
```

这将一个名为 'app' 的 `fileLoggerBackend` 注册到 `Logger` 类中，该后端将写入文件 `/var/log/applog.log`。

### 将日志记录到数据库表

您可以使用此相同的 `LoggerBackend` 子类化过程，为记录到任何可想象的数据存储库创建一种机制。以下代码显示了一个 PostgreSQL 后端，但相同的原则可用于记录到任何数据库平台。

此类的构造函数明显更长。连接参数以及写入信息的数据库中的字段名称都应能在连接字符串中表示，对于可选项应有合理的默认值。因此，代码必须在构建连接字符串和字段名称之前检查是否设置了某些值。所有这些代码

## 第二部分：学习高级开发技术

这非常有趣，但所有内容都包含在此处，以展示如何解析连接字符串以实现灵活的 PostgreSQL 日志记录机制。此代码应保存在 Logger/class.pgsqlLoggerBackend.php：

```php
<?php

require_once('class.LoggerBackend.php');

class pgsqlLoggerBackend extends LoggerBackend {

private $logLevel;
private $Conn;
private $table = 'logdata';
private $messageField = 'message';
private $logLevelField = 'loglevel';
private $timestampField = 'logdate';
private $moduleField = 'module';

public function __construct($urlData) {
parent::__construct($urlData);

$this->logLevel = Config::getConfig('LOGGER_LEVEL');

$host = $urlData['host'];
$port = $urlData['port'];
$user = $urlData['user'];
$password = $urlData['pass'];
$arPath = explode('/', $urlData['path']);
$database = $arPath[1];

if(!strlen($database)) {
throw new Exception('pgsqlLoggerBackend: Invalid connection string. '
'No database name was specified');
}

$connStr = '';
if($host) {
$connStr .= "host=$host ";
}

if($port) {
$connStr .= "port=$port ";
}
if($user) {
$connStr .= "user=$user ";
}

if($password) {
$connStr .= "password=$password ";
}
$connStr .= "dbname=$database";

//Suppress native errors. We'll handle them with an exception
$this->hConn = pg_connect($connStr);

if(! is_resource($this->hConn)) {
    throw new Exception("Unable to connect to the database using $connStr");
}

//Take the query string in the form var=foo&bar=blah
//and convert it to an array like
// array('var' => 'foo', 'bar' => 'blah')
//Be sure to convert urlencoded values
$QueryData = $urlData['query'];
if(strlen($QueryData)) {
    $arTmpQuery = explode('&',$QueryData);

    $arQuery = array();
    foreach($arTmpQuery as $QueryItem) {
        $arQueryItem = explode('=', $QueryItem);
        $arQuery[urldecode($arQueryItem[0])] = urldecode($arQueryItem[1]);
    }
}

/* None of these items is mandatory. The defaults are
   established in the private member declarations at the top
   of the class. These variables establish the name of the
   table and the names of the fields within that table
   that store the various elements of the log entry.
*/

if(isset($arQuery['table'])) {
    $this->table = $arQuery['table'];
}

if(isset($arQuery['messageField'])) {
    $this->messageField = $arQuery['messageField'];
    if(isset($arQuery['logLevelField'])) {
        $this->logLevelField = $arQuery['logLevelField'];
    }
}

if(isset($arQuery['timestampField'])) {
    $this->timestampField = $arQuery['timestampField'];
}
if(isset($arQuery['moduleField'])) {
    $this->moduleField = $arQuery['moduleField'];
}
}

public function logMessage($msg, $logLevel = Logger::INFO, $module = null) {
    if($logLevel <= $this->logLevel) {
    $strLogLevel = Logger::levelToString($logLevel);

    $msg = pg_escape_string($msg);

    if(isset($module)) {
    $module = "" . pg_escape_string($module) . "";
    } else {
    $module = 'NULL';
    }
    }

    $arFields = array();
    $arFields[$this->messageField] = "" . pg_escape_string($msg) . "";
    $arFields[$this->logLevelField] = pg_escape_string($logLevel);
    $arFields[$this->timestampField] = "CURRENT_TIMESTAMP";
    $arFields[$this->moduleField] = $module;

    $sql = 'INSERT INTO ' . $this->table;
    $sql .= ' (' . join(', ', array_keys($arFields)) . ')';
    $sql .= ' VALUES (' . join(', ', array_values($arFields)) . ')';

    pg_exec($this->hConn, $sql);
    }
}
?>
```

在构造函数中，该类解析 URL 的查询部分，以确定表名以及存储日志信息的字段名称。假设将使用类似以下的 SQL 语句创建表。字段名称无关紧要（因为它们在连接字符串中是可配置的），但表中的数据类型应相同（或兼容的数据类型）：

```sql
create table logdata (
   message text,
   loglevel smallint,
   logdate timestamp,
   module varchar(255)
);
```

要使用新的 PostgreSQL 日志记录器，代码应类似于以下内容：

```php
<?php
require_once('class.Config.php');
require_once('class.Logger-enhanced.php');
Config::addConfig('LOGGER_LEVEL', Logger::INFO);

Logger::register('app', 'pgsql://steve:pass@localhost/mydb?table=logdata');

$log = Logger::getInstance('app');

if(isset($_GET['fooid'])) {
    //not written to the log - the log level is too high
    $log->logMessage('A fooid is present', Logger::DEBUG);

    //LOG_INFO is the default, so this would get printed
    $log->logMessage('The value of fooid is ' . $_GET['fooid']);
} else {
    //This will also be written and includes a module name
    $log->logMessage('No fooid supplied',
                     Logger::CRITICAL,
                     "Foo Module");

    throw new Exception('No foo id!');
}
?>
```

传递给 `Logger::register()` 的连接字符串指定了一个名为 `app` 的日志，该日志连接到运行在 `localhost` 上的 PostgreSQL 数据库。`LoggerBackend` 以用户 `steve` 的身份连接到名为 `mydb` 的数据库。写入日志条目的表称为 `logdata`。如果您未指定这些参数中的任何一个，将使用作为类私有成员变量声明的默认值。当然，此后端可以轻松修改以支持任何有 PHP 模块的数据库类型（包括 MySQL 和 SQL Server）。

此示例使用了原生 PostgreSQL 函数，而非利用 PDO。您也可以构建一个 PDO 后端，使用传递给 `Logger::register` 的适当结构化连接字符串连接到任何有可用驱动程序的数据库，格式为 `pdo://user:pass@hostname/database?driver=[pdo driver name]`。

## 创建调试机制

虽然像您刚刚创建的这样强大的日志记录机制在灵活性和存储方面几乎有无限的可能性，但有时将调试消息打印到浏览器窗口要方便得多，而不必仔细查看大型日志文件；但就像 `Logger` 类旨在防止部署前必须手动删除的数十条 `print` 语句一样，调试机制使开发人员能够以这种方式将消息打印到屏幕上，以便在部署时可以轻松删除。

`Debugger` 类将调试消息存储在会话中，然后在页面请求结束时将它们打印在屏幕底部。这将调试输出集中到屏幕上的一个位置，使查找您要查找的特定输出变得更加容易。它还使您能够打印大量数据而不干扰用户界面的结构，并使禁用调试输出变得容易。

之所以将此信息存储在会话中，是因为并非每个页面请求都会生成输出。例如，当通过发布表单将信息保存到数据库时，通常应发出 302 重定向，以防止用户在浏览器上按下重新加载按钮时修改数据。302 重定向是指浏览器发出的 HTTP 响应代码，当您发出诸如 header('Location: [url]') 之类的代码时。

Debugger 有两个主要功能：

- DEBUG 函数将带有可选键和调试级别的条目写入会话中的调试数组。调试级别的工作方式与 Logger 类中的日志级别相同。日志级别值越低，优先级越高。
- debug_print 函数应在每个生成输出的页面底部调用。它从会话中获取数组并生成包含数组内容的 HTML 表。打印完成后，它会从会话中删除该信息。这样，不生成输出的页面请求仍会保留其调试信息。

此类的代码如下。将此类命名为 Debugger.php：

```php
<?php

define('DEBUG_INFO', 100);
define('DEBUG_SQL', 75);
define('DEBUG_WARNING', 50);
define('DEBUG_ERROR', 25);
define('DEBUG_CRITICAL', 10);

session_start();

class Debugger {

    public static function debug($data, $key = null, $debugLevel = DEBUG_INFO) {

        if(! isset($_SESSION['debugData'])) {
            $_SESSION['debugData'] = array();
        }

        if($debugLevel <= Config::getConfig('DEBUG_LEVEL') ) {
            $_SESSION['debugData'][$key] = $data;
        }
    }

    public static function debugPrint() {
        $arDebugData = $_SESSION['debugData'];
        print Debugger::printArray($arDebugData);

        $_SESSION['debugData'] = array();
    }
}
```





```
public static function printArray($var, $title = true) {

    $string = '<table border="1">';
    if ($title) {
        $string .= "<tr><td><b>Key</b></td><td><b>Value</b></td></tr>\n";
    }

    if (is_array($var)) {
        foreach($var as $key => $value) {
            $string .= "<tr>\n";
            $string .= "<td><b>$key</b></td><td>";

            if (is_array($value)) {
                $string .= Debugger::printArray($value, false);
            } elseif (gettype($value) == 'object') {
                $string .= "Object of class " . get_class($value);
            } else {
                $string .= "$value";
            }

            $string .= "</td></tr>\n";
        }
    }

    $string .= "</table>\n";
    return $string;
}
?>
```

文件顶部定义的五个常量用于定义调试级别，其工作方式与 class.Logger.php 中的日志级别常量完全相同。debug() 方法期望在全局命名空间中找到一个名为 $cfg 的数组，该数组包含一个定义整个应用程序当前调试级别的 DEBUG_LEVEL 元素。

默认情况下，调试级别为 DEBUG_INFO，尽管 debug() 的第三个参数允许您将其设置为任何级别。这样，您可以通过简单修改 $cfg['DEBUG_LEVEL'] 来显示想要多多或少少的调试信息。

$key 参数是调试数组中信息的可选标签。虽然它在参数列表中排在第二位，但它将出现在 debugPrint() 最终生成的表格的最左侧列。

debugPrint() 函数只是将会话中的调试信息传递给 printArray() 方法，后者完成所有真正繁重的工作。在打印调试信息后，debugPrint() 会清空会话数组，以便为下一次页面视图清除调试信息。

printArray() 接受至少一个维度的数组，并打印一个显示该数组内容的 HTML 表。多维数组得到了正确处理。对象仅打印其类名。

以下代码展示了该类的使用方法：

```
<?php

require_once( 'class.Debugger.php' );
require_once( 'class.Config.php' );

Config::addConfig( 'DEBUG_LEVEL', DEBUG_INFO );

$myData = array();
$myData[] = 'hello';
$myData[] = array( 'name' => 'Bob',
        'colors' => array( 'red', 'green', 'blue' ) );

Debugger::debug( $myData, 'my data' );
$x = 5 + 8;
Debugger::debug( $x, 'x' );

Debugger::debugPrint();

?>
```

通过查看 Figure 9-1 中的屏幕输出，可以更容易地理解此示例，该图显示了 debugPrint() 函数的输出。

![](img/a1b732997d9cb194dceec0570dc79710_231_0.png)

Figure 9-1: debugPrint() 函数的屏幕输出

## Summary

`Logger` 类可以扩展以支持将日志信息记录到几乎任何可想象的数据存储库中。只需创建并使用最能支持您需求的后端即可。对于大多数用途，`fileLoggerBackend` 类应该是最合适的，但使用数据库也有某些明确的优势。

`Debugger` 类提供了与 `Logger` 类类似的功能，但允许信息显示在屏幕上并存储在会话中以供显示，即使原始页面请求不包含任何输出。

在第 10 章中，您将学习如何使用 PHP 6 编写和交互 Web 服务，这使您能够与第三方提供的数据和功能进行交互。

## Writing and Using Web Services

在使用 PHP 构建应用程序时，可用的模块和 PEAR 包数量庞大，您可能会觉得 PHP 几乎无法在短时间内实现相当复杂的业务需求。从图像处理和复杂的日期/时间运算到事务性数据库交互，PHP 确实大量开箱即用。但是，您可能希望在应用程序中提供一些功能，却无法实现，要么是因为您缺乏数据且获取数据过于麻烦（例如，为整个互联网开发自己的搜索引擎），要么是因为应用程序逻辑远比项目预算所允许的要复杂得多（例如，创建交互式地理信息系统应用程序）。

幸运的是，许多应用程序提供商通过应用程序编程接口 (API) 暴露其应用程序的功能，该接口允许以无标记的方式交换数据。通常，这涉及通过 HTTP 进行调用，使用按照某些规则和标记格式构建的请求，并以结构化的方式接收响应，通常是 XML，但也常为其他格式（CSV、JSON 等等）。由于此响应是结构化数据，而不是包含 HTML 或其他样式化输出的数据，您可以以任何喜欢的方式使用和显示它。

如果您的应用程序是 HTML，则将输出转换为 HTML。如果您的应用程序是 Flash，则可以以最适合您的 Flash 应用程序的方式输出。此外，您与 Web 服务的交互不需要向用户产生任何输出，而是可用于填充或增强数据库中的数据（例如，使用地理定位服务获取位置列表的纬度和经度值）。

利用另一应用程序的 Web 服务 API，使您能够将该应用程序与您自己的数据和功能创建“混搭”（mashups）。本章描述了与 Web 服务 API 交互的多种方法，包括一些更流行的商业服务，例如 Google 和 Yahoo!。您将学习如何结合它们的数据来创建自己的应用程序。最后，您将学习如何将您应用程序的功能暴露给他人，以便他们可以利用您的应用程序，并且您还将发现如何从这种方法中受益。

与 Web 服务 API 交互存在众多不同的标准。“Web 服务”这一术语绝不意味着特指其中任何一种。该术语仅暗示通过 HTTP 对另一应用程序进行远程调用的概念。通信的实际性质由几种既定数据交换协议之一管理，通常由 W3C 监督。本章介绍了 Web 服务中几种最流行的协议。

### SOAP

简单对象访问协议 (SOAP) 是 Web 服务协议中最强大的一种，允许发现应用程序功能、自动确定数据类型、数据验证功能以及复杂的请求-响应数据结构。SOAP 使用 XML 架构进行数据交换，通常作为通信协议的 HTTP 上层（尽管也有主要是理论上的使用 SMTP 或其他协议作为通信层的实现）。

所有这些强大功能的缺点是，相当复杂（意味着灵活且可能复杂）的请求-响应结构功能意味着数据结构 *必然* 复杂（意味着难以理解且难以实现）。因此，已开发了许多 PHP 包，它们作为 XML 数据结构和 HTTP 交互实际实现的包装器。

XML 是一个庞大的主题，本章并未详细介绍。您应具备基本的 XML 知识才能理解和使用本章。如果您不熟悉 XML 但希望打下良好的基础，您可能想查看 *Beginning XML, Fourth Edition* (Wiley, 2007)。本章的下一部分将探讨如何在 PHP 6 中使用 SOAP 实现基于 XML 的 Web 服务。

### SOAP and PHP 6

SOAP 是一种与平台无关的消息协议——也就是说，它乐于使用各种互联网协议，例如 HTTP、SMTP，甚至 MIME。您已经知道它将 XML 作为其信息交换方法的一部分，这里要注意的是，Web 服务描述语言 (WSDL) 也被用来让您的生活更轻松。本讨论探讨了如何使用将由 SOAP 访问的服务。WSDL 以及 SOAP 的所有其他方面，将在本章稍后部分更详细地探讨。

SOAP 做什么？简单的答案是，它使您能够在去中心化的分布式环境中传递结构化、类型化数据。这意味着您可以将数据中心运行 PHP 应用程序的 GNU/Linux 服务器上的请求传递到另一大洲的 Solaris 机器上的 J2EE 应用程序，并期待一个完全连贯的响应。使用 SOAP，过去许多数据转换和系统集成问题得以解决，并且适用于所有带有可行 XML 解析器的平台的远程过程调用机制可用且文档齐全。（目前，几乎每个会以企业能力部署的主要平台都具有 XML 解析功能和可用的 HTTP 实现。）





以下是实现 PHP 中 SOAP 的不同库：

- The PHP 6 SOAP extension — 随 PHP 6 一起提供
- PEAR::SOAP — http://pear.php.net/package/SOAP
- NuSOAP — http://sourceforge.net/projects/nusoap/

根据你个人偏好，可以随意选择。就本章而言，我们将仅介绍随 PHP 6 一起提供的 SOAP 扩展的用法。该扩展已针对 PHP 6 进行了全面重构。由于它是用 C 实现的，因此速度会比用早期 PHP 版本实现的其他模块快得多。

## PHP 6 SOAP 扩展

截至撰写本文时，你必须手动将 SOAP 扩展添加到 php.ini 文件中（Windows 系统为 extension=php_soap.dll），或者在 Linux 系统中使用 --enable-soap 进行编译。此外，请注意，许多在线资料称 SOAP 扩展默认启用，但当前使用的 PHP 6 快照并未默认启用它。等到这本书上架时，默认策略可能会发生变化，因此请查看 PHP 发行版的 phpinfo() 输出，以确定是否需要手动启用 SOAP。

关于在 PHP 6 中配置 SOAP，有几点需要注意。使用 SOAP 的最大缺点之一是，你最终取决于服务器互联网连接的速度，因为发出请求的 SOAP 客户端必须先下载 WSDL 文档，才知道如何向目标服务发起函数调用。显然，在慢速连接（或者更重要的是，高延迟或“ping 时间”的连接）上下载文件，可能会成为特定任务执行时间的最大瓶颈。

解决方案以 PHP 配置设置的形式提供，使你能够指定是否缓存 WSDL 页面、缓存位置以及使用缓存文件的时长。这意味着你的应用程序执行时间仅在下载 WSDL 时“计费”一次；之后，你将使用缓存版本。

如果你认为这将显著提升应用程序的性能，可以将以下行添加到 php.ini 文件中（替换为你认为必要的值）：

```
; SOAP
;Boolean parameter to indicate whether caching should occur
soap.wsdl_cache_enabled = "1"
;directory where files are to be cached
soap.wsdl_cache_dir = "/tmp/wsdlcache"
;time, given in seconds, to use the cached copy - ttl = time to live
soap.wsdl_cache_ttl = "86400"
```

PHP 6 提供的函数名义上可分为三类。主要两类是 SoapClient 和 SoapServer 函数，第三类处理杂项函数。这些内容将在接下来的几个部分中简要介绍，但如需更全面的覆盖，请参阅 www.php.net/soap 的文档。

### SoapClient 函数

秉承面向对象的所有原则，可用的 SOAP 函数通过 SOAP 对象公开，你可以按如下方式实例化一个通用的 SoapClient 对象：

```
$client = new SoapClient (mixed wsdl [, array options]);
```

第一个参数可以为 null 值（如果你不使用 WSDL），也可以为要使用的 WSDL 文档的统一资源标识符（URI）。随后的 options 参数应作为数组传递，可用于提供代理设置或规定 SOAP 客户端应遵循的 SOAP 规范。例如，要创建一个使用编码 SOAP 消息和 RPC 风格的 SOAP 客户端，可以使用以下代码：

```
$client = new SoapClient (null,
 array ('location' => "http://localhost/my_soap.php",
 'uri' => "http://my_uri/",
 'style' => SOAP_RPC, 'use' => SOAP_ENCODED));
```

实例化 SOAP 客户端后，PHP 6 提供了多种可在结果客户端对象上调用的方法。其中较重要的方法如下：

- __call — 使用此方法可直接进行 SOAP 调用。通常，你可以直接将 SOAP 函数作为 SoapClient 方法调用，但例如在传输 SOAP 头部和尾部时，这可能会派上用场。
- __getFunctions — 这将公开给定 Web 服务提供的函数。
- __getLastRequest — 正如名称所暗示的，你可以检索 SOAP 客户端发出的上一个请求，但前提是你的 SoapClient 实例是在 options 数组参数中将 trace 选项设置为 true 的情况下创建的。
- __getLastResponse — 同样，你可以使用此方法确定 SOAP 客户端接收的上一个响应，前提是你的 SoapClient 已启用 trace 选项。
- __getTypes — 这将返回一系列 SOAP 类型（即由 Web 服务定义和实现的结构和对象）。仅当你的 SoapClient 在 WSDL 模式下实例化（即，第一个参数提供了 WSDL URI）时，才能使用此方法。

你将稍后学习如何创建和使用 SOAP 客户端。目前，让我们继续探索 PHP 6 提供的其他 SOAP 功能。

### SoapServer 函数

当然，从客户端访问信息并不是开发者使用 SOAP 的唯一方式。提供服务器是 Web 服务待办事项列表中的首要任务，PHP 6 提供了一些方法来创建 SOAP 服务器。

与 SoapClient 类似，你有一个构造函数可用于按如下方式创建 SoapServer 对象：

```
$server = new SoapServer (mixed wsdl [, array options])
```

你可以在第一个参数中指定要使用的 WSDL 文档，也可以将其留为 null。如果第一个选项为 null，你必须以与 SoapClient 大致相同的方式，在 options 数组中设置 uri 选项。以下是可用的服务器方法：

- addFunction — 这允许添加函数来处理 SOAP 请求。
- getFunctions — 这将返回服务器上可用的函数列表。
- handle — 这从单个 soap_request 参数或（在其缺失时）全局变量 $HTTP_RAW_POST_DATA 获取值，并处理给定请求，向客户端返回响应。
- setClass — 这允许将 PHP 方法（和整个类）添加到服务器中，以便处理 SOAP 请求。
- setPersistence — 假设你已使用 setClass 添加服务器功能，这可用于在会话中延续请求之间的数据。

### 其他函数

最后几个 SOAP 函数涉及几个不同的问题，最重要的是异常处理。你可以按如下方式创建 SoapFault 对象，以便从服务器返回故障响应：

```
$fault = new SoapFault (string faultcode, string faultstring [,
string faultactor [, mixed detail [, string faultname
[, mixed headerfault]]]]);
```

如果 SoapClient 的 exceptions 选项设置为 0，请求的方法在出现任何失败时都会返回 SoapFault 对象。牢记这一点，你可以使用以下函数（仅一个函数，不属于任何类）来测试函数调用是否失败：

```
is_soap_fault ($methodresult)
```

如果传入的 result 参数确实是 SoapFault 对象的实例，则此函数返回 true。

除这些与异常相关的问题外，PHP 6 的 SOAP 扩展还实现了 SoapVar 对象，可用于在非 WSDL 模式下设置类型属性。它的实例化方式如下：

```
$type = new SoapVar ( mixed data, int encoding [, string type_name [, string
type_namespace [, string node_name [, string node_namespace]]]]);
```

正如名称所暗示的，SoapHeader 使你能够在客户端和服务器之间传递原始 SOAP 头部。这可以通过 __call() 或 __handle() 函数完成：

```
client->__call("myFunction", null, null,
new SoapHeader('http://thenamespace.org/mynamespace/', 'myExample',
'an example'));
```

最后，你还可以使用 `SoapParam` 对象，从不在 WSDL 模式下的客户端传递名称和值对作为 SOAP 参数。例如，要向 SOAP 服务器的方法调用提供参数，你可以说类似这样的内容：

```
$client->__call ("getSoapMethod", array(new SoapParam($value, "name")));
```

至此，你现在对第一个捆绑 SOAP 扩展如何使用 SOAP 有了简要了解。你可以使用此知识来创建一个示例 SOAP 客户端，以及一个简单的 SOAP 服务器。

## 创建 SOAP 客户端

本节中的示例利用 `Amazon.com` 公开的 Web 服务功能。你可以使用 Amazon 的 SOAP API 获取 `Amazon.com` 上出售的任何商品的价格、描述、图片和相关项目等信息。请注意，Amazon 已使事情变得相当简单，因为它提供了适当 WSDL 文档的 URI（请参见以下代码片段），正如你所知，这将告诉你的 SOAP 客户端如何使用该服务。

回顾本章前面的内容，在创建新的 `SoapClient` 对象时，你可以选择是否使用 WSDL 模式。由于你有一个 WSDL 链接，让我们使用它。将此代码保存到 `soap.php`：

```
<?php
$client = new SoapClient(
 "http://webservices.amazon.com/AWSECommerceService/AWSECommerceService.wsdl");
?>
```

基本上就是这样。如果你选择不使用 WSDL 模式，或者无法使用，则需要添加 location、URI、style 等数组选项。

假设 Web 服务正常运行，那么你的工作就完成了。从网站，你可以点击 Analyze WSDL 链接查看服务定义，但我们还是使用一些原生的 PHP 6 函数来确定如何使用此服务。

做到这一点的最佳方法是简单地将 `__getFunctions()` 函数的输出转储到屏幕上，如下所示：

```
<?php
$client = new SoapClient(
 "http://webservices.amazon.com/AWSECommerceService/AWSECommerceService.wsdl");
var_dump($client->__getFunctions());
?>
```

将此代码另存为 `soap_functions.php` 并在浏览器中访问它。你将看到类似图 10-1 的内容。





![](img/a1b732997d9cb194dceec0570dc79710_239_0.png)

**图 10-1: 列出 Amazon.com SOAP API 中的可用函数**

此输出表明你有许多可用的方法。其中最立即有用的是 ItemSearch。在调用 Amazon SOAP API 中的任何函数之前，你必须通过访问 http://aws.amazon.com/ 并点击“立即注册”按钮来注册一个免费的 Amazon Web Services (AWS) 账户，以获取新账户。一旦你拥有 AWS 访问 ID，你可以查询服务器以获取有关 PHP 6 图书的详细信息：

```php
<?php
$client = new SoapClient(
    "http://webservices.amazon.com/AWSECommerceService/AWSECommerceService.wsdl"
);
$request = array(
    'SearchIndex' => 'Books',
    'Keywords' => 'PHP 6'
);

$params = array(
    'AWSAccessKeyId' => '[your Amazon AWS Access Key]',
    'Operation' => 'ItemSearch',
    'Request' => $request
);

$out = $client->ItemSearch($params);

foreach($out->Items->Item as $item) {
    print '<a href="' . $item->DetailPageURL . '">' .
        $item->ItemAttributes->Title . "</a><br>\n";
}
?>
```

将此代码保存为 php6_books.php 并在浏览器中打开它。如果一切正常，你将看到类似图 10-2 的内容。

![](img/a1b732997d9cb194dceec0570dc79710_240_0.png)

**图 10-2: Amazon.com SOAP API 搜索输出**

*在本书付梓时，指定查询的搜索结果可能会更多或更少。*

如你所见，只需几行代码即可轻松获取 Amazon 产品目录中任何商品的详细信息。当然，底层还有一些更多内容。让我们更详细地看看这里发生了什么。

## 透视底层

尽管 PHP 6 的 SOAP 扩展编程接口使用简单，但为了确保所有通信都正确进行，需要做大量工作。理解 WSDL 文档在此过程中的作用很重要，因为这决定了客户端和服务器之间将如何进行通信。基本上，你可以将 WSDL 视为一种基于 XML 的可扩展手段，用于定义 Web 服务为一组可操作于 *消息* 的 *端点*。

本讨论详细审查了前一示例中使用的 WSDL 文档，并查看了为了获取图书价格而在客户端和服务器之间传递的请求和响应 SOAP 消息。

### WSDL 文档

WSDL 文档被分为多个部分，这些部分共同构成了该 Web 服务的客户端和服务器必须遵循的通信协议。WSDL 文档的结构包含几个主要组件，以及一些稍微次要的组件。以下元素并非在所有场景中都必须包含：

- `definitions` — 根元素。这定义了名称和目标命名空间。
- `types` — 这描述了要使用的数据类型。它不是必需的，如果未定义任何类型，则默认为 W3C XML Schema 规范。
- `message` — 这描述了请求或响应消息。
- `portType` — 这定义（或描述）了一个操作，通常由请求和响应消息组合而成——即一个往返。
- `bindings/operation` — 这描述了消息的传输方式。它包含绑定和消息编码样式等元素。
- `service` — 正如其名称所暗示的，这提供了所需服务的地址。
- `documentation` — 这仅允许服务提供商提供其服务的描述。
- `import` — 这使你能够将 WSDL 文档解耦为不同的元素，以便它们可以存储在不同的文档中，并在需要时导入。

本章不会花太多时间讨论 WSDL，但要深入了解它，请访问 www.w3.org/TR/wsdl。

从下面的第一段 XML 可以看出，你定义了所使用的 XML 版本（1.0），然后声明 `definitions` 元素。`definitions` 元素始终是根元素，然后定义文档中使用的命名空间：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<definitions xmlns="http://schemas.xmlsoap.org/wsdl/"
xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
xmlns:xs="http://www.w3.org/2001/XMLSchema"
xmlns:tns="http://webservices.amazon.com/AWSECommerceService/2008-10-06"
targetNamespace="http://webservices.amazon.com/AWSECommerceService/2008-10-06">
```

Amazon WSDL 文档的下一部分定义了请求和响应中使用的各种数据类型。从图 10-1 的函数列表中，你可以看到函数 `ItemSearch` 接受一个类型为 `ItemSearch` 的单个参数。该类型的定义可在 WSDL 文档中找到：

```xml
<xs:element name="ItemSearch">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="MarketplaceDomain" type="xs:string"
        minOccurs="0"/>
      <xs:element name="AWSAccessKeyId" type="xs:string" minOccurs="0"/>
      <xs:element name="SubscriptionId" type="xs:string" minOccurs="0"/>
      <xs:element name="AssociateTag" type="xs:string" minOccurs="0"/>
      <xs:element name="XML Escaping" type="xs:string" minOccurs="0"/>
      <xs:element name="Validate" type="xs:string" minOccurs="0"/>
      <xs:element name="Shared" type="tns:ItemSearchRequest"
        minOccurs="0"/>
      <xs:element name="Request" type="tns:ItemSearchRequest"
          minOccurs="0" maxOccurs="unbounded"/>

</xs:sequence>
</xs:complexType>
</xs:element>
```

请注意，Request 元素（即 php6_books.php 中用于提供搜索查询的元素）是另一个名为 ItemSearchRequest 的自定义数据类型，在 WSDL 文件中指定如下：

```xml
<xs:complexType name="ItemSearchRequest">
    <xs:sequence>
        <xs:element name="Actor" type="xs:string" minOccurs="0"/>
        <xs:element name="Artist" type="xs:string" minOccurs="0"/>
        <xs:element name="Availability" minOccurs="0">
        <xs:simpleType>
            <xs:restriction base="xs:string">
                <xs:enumeration value="Available"/>
            </xs:restriction>
        </xs:simpleType>
        </xs:element>
    </xs:element>
    <xs:element ref="tns:AudienceRating" minOccurs="0"
        maxOccurs="unbounded"/>
    <xs:element name="Author" type="xs:string" minOccurs="0"/>
    <xs:element name="Brand" type="xs:string" minOccurs="0"/>
    <xs:element name="BrowseNode" type="xs:string" minOccurs="0"/>
    <xs:element name="City" type="xs:string" minOccurs="0"/>
    <xs:element name="Composer" type="xs:string" minOccurs="0"/>
    <xs:element ref="tns:Condition" minOccurs="0"/>
    <xs:element name="Conductor" type="xs:string" minOccurs="0"/>
    <xs:element name="Count" type="xs:positiveInteger" minOccurs="0">
    <xs:annotation>
        <xs:appinfo>
            <aws:se:restricted
            xmlns:aws-se="http://webservices.amazon.com/AWS-SchemaExtensions"/>
            <aws-se:excludeFrom>public</aws-se:excludeFrom>
            <aws-se:excludeFrom>partner</aws-se:excludeFrom>
        </aws:se:restricted>
        </xs:appinfo>
    </xs:annotation>
    </xs:element>
    <xs:element name="Cuisine" type="xs:string" minOccurs="0"/>
    <xs:element ref="tns:DeliveryMethod" minOccurs="0"/>
    <xs:element name="Director" type="xs:string" minOccurs="0"/>
    <xs:element name="FutureLaunchDate" type="xs:string" minOccurs="0"/>
    <xs:element name="ISPUPostalCode" type="xs:string" minOccurs="0"/>
    <xs:element name="ItemPage" type="xs:positiveInteger" minOccurs="0"/>
    <xs:element name="Keywords" type="xs:string" minOccurs="0"/>
    <xs:element name="Manufacturer" type="xs:string" minOccurs="0"/>
    <xs:element name="MaximumPrice" type="xs:nonNegativeInteger"
minOccurs="0"/>
    <xs:element name="MerchantId" type="xs:string" minOccurs="0"/>
    <xs:element name="MinimumPrice" type="xs:nonNegativeInteger"
minOccurs="0"/>
    <xs:element name="MusicLabel" type="xs:string" minOccurs="0"/>
    <xs:element name="Neighborhood" type="xs:string" minOccurs="0"/>
    <xs:element name="Orchestra" type="xs:string" minOccurs="0"/>
    <xs:element name="PostalCode" type="xs:string" minOccurs="0"/>
    <xs:element name="Power" type="xs:string" minOccurs="0"/>
    <xs:element name="Publisher" type="xs:string" minOccurs="0"/>
    <xs:element name="ResponseGroup" type="xs:string" minOccurs="0"
maxOccurs="unbounded"/>
    <xs:element name="ReviewSort" type="xs:string" minOccurs="0"/>
    <xs:element name="SearchIndex" type="xs:string" minOccurs="0"/>
    <xs:element name="Sort" type="xs:string" minOccurs="0"/>
    <xs:element name="State" type="xs:string" minOccurs="0"/>
    <xs:element name="TagPage" type="xs:positiveInteger" minOccurs="0"/>
    <xs:element name="TagsPerPage" type="xs:positiveInteger"
minOccurs="0"/>
    <xs:element name="TagSort" type="xs:string" minOccurs="0"/>
    <xs:element name="TextStream" type="xs:string" minOccurs="0"/>
    <xs:element name="Title" type="xs:string" minOccurs="0"/>
    <xs:element name="ReleaseDate" type="xs:string" minOccurs="0"/>
</xs:sequence>
</xs:complexType>
```

当然，你并没有创建包含所有这些参数的数据结构。你仅使用了强制性的 SearchIndex 元素和 Keywords 元素来定义搜索条件。你可以针对所使用的搜索条件进行非常具体的设置，指定出版商、价格范围和其他详细信息。显然，其中一些元素（例如 Cuisine 和 MusicLabel）不适用于图书，而是适用于 Amazon 产品目录中的其他商品。

接下来在 WSDL 文档中是消息元素。此部分提供请求和响应消息名称，并指定它们将使用的类型（有关与 SOAP 扩展一起使用的定义类型列表，请参阅 www.php.net/manual/en/ref.soap.php 中的文档）。以下是 ItemSearch 函数的消息定义：

```xml
<message name="ItemSearchRequestMsg">
<part name="body" element="tns:ItemSearch"/>
</message>

<message name="ItemSearchResponseMsg">
<part name="body" element="tns:ItemSearchResponse"/>
</message>
```





portType 元素定义了名为 ItemSearch 的函数，它由前面代码片段中指定的输入和输出消息组成：

```
<portType name="AWSECommerceServicePortType">
[snip]
<operation name="ItemSearch">
<input message="tns:ItemSearchRequestMsg"/>
<output message="tns:ItemSearchResponseMsg"/>
</operation>
[snip]
</portType>
```

portType 元素的 name 属性指定了在每个 portType 部分中定义的操作所要使用的可用绑定。AWSECommerceServicePortType 在 WSDL 文档较后的位置由一个 binding 元素定义：

```
<binding name="AWSECommerceServiceBinding"
type="tns:AWSECommerceServicePortType">
<soap:binding style="document" transport=
"http://schemas.xmlsoap.org/soap/http"/>
[snip]
<operation name="ItemSearch">
<soap:operation soapAction="http://soap.amazon.com"/>
<input>
<soap:body use="literal"/>
</input>
<output>
<soap:body use="literal"/>
</output>
</operation>
[snip]
</binding>
```

绑定定义指定了发送请求和接收响应时所使用的传输方式（在此例中为 HTTP，即最常见的 SOAP 传输协议）。

绑定名称引用了一个服务，该服务定义了向远程服务器发送请求时所要使用的特定 URL：

```
<service name="AWSECommerceService">
<port name="AWSECommerceServicePort" binding=
"tns:AWSECommerceServiceBinding">
<soap:address location="http://soap.amazon.com/onca/soap?Service=
AWSECommerceService"/>
</port>
</service>
</definitions>
```

通过浏览 WSDL 文档，你可以确定每个函数所需的参数及其返回类型。理解如何读取 WSDL 文档非常重要，以便你能更有效地调试远程系统返回的通信问题和错误消息。然而，对于常规操作，PHP 可以通过为你解释 WSDL 文档，让你免于在大量 XML 中艰难跋涉。

现在让我们看看请求和响应是如何形成的。你应该已经从 WSDL 文档中有所了解，但 PHP 在此可以提供进一步的帮助。

## 请求和响应信封

PHP 6 SOAP 扩展提供了一些可用于查看客户端请求和响应的函数。打开本章前面提到的 php6_books.php 文件，并按如下方式修改它：

```
<?php

$client = new SoapClient(
	"http://webservices.amazon.com/AWSECommerceService/AWSECommerceService.wsdl",
	array('trace' => 1));

$request = array(
	'SearchIndex' => 'Books',
	'Keywords' => 'PHP 6'
);

$params = array(
	'AWSAccessKeyId' => '[your Amazon AWS Access Key]',
	'Operation' => 'ItemSearch',
	'Request' => $request
);

$out = $client->ItemSearch($params);

foreach($out->Items->Item as $item) {
	print '<a href="' . $item->DetailPageURL . '">' . $item->ItemAttributes->Title . "</a><br/>\n";
}

print "<pre>" . htmlentities(print_r($client->__getLastRequest(), true)) . "
</pre>\n";
print "<pre>" . htmlentities(print_r($client->__getLastResponse(), true)) . "
</pre>\n";
?>
```

这将给出图 10-3 中所示的输出。

![](img/a1b732997d9cb194dceec0570dc79710_246_0.png)

图 10-3: 请求和响应 XML

使用此输出，你可以准确地看到发送到 Web 服务器的内容以及其生成的 XML 响应的完整内容。你可以非常容易地将 WSDL 文档中定义的消息传输方式与 SOAP 扩展生成的实际 WSDL 文档联系起来。例如，你可以看到关键字和搜索索引选项是作为字符串发送的：

```
<?xml version="1.0"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
xmlns:ns1="http://webservices.amazon.com/AWSECommerceService/2008-10-06">
<SOAP-ENV:Body>
  <ns1:ItemSearch>
    <ns1:AWSAccessKeyId>[Your Key]</ns1:AWSAccessKeyId>
    <ns1:Request>
      <ns1:Keywords>PHP 6</ns1:Keywords>
      <ns1:SearchIndex>Books</ns1:SearchIndex>
    </ns1:Request>
  </ns1:ItemSearch>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

接下来，你有由 Web 服务服务器返回的响应信封（这里太长，不便重印）。同样，你可以非常容易地将其与 WSDL 文档联系起来。例如，你会注意到，标题是 ItemAttributes 元素的一部分，并且是一个字符串。

尚未介绍的是，如果指定了无效的 `SearchIndex` 或发生其他错误时会发生什么。当然，你必须实现某种形式的错误处理。有几种方法可以做到这一点，你可以选择最适合你的应用程序的方法。正如你可能猜到的，你可以使用 PHP 6 的 SOAP 实现来使事情变得更加健壮。

### SOAP 客户端中的异常处理

如前面讨论中回顾的那样，一个 `SoapFault` 对象可供你使用。打开你的 `soap.php` 文件，并按以下代码片段所示修改它以使用无效的函数名（将其保存为 `soapfaults.php`）：

```
<?php
$client = new SoapClient(
    "http://webservices.amazon.com/AWSECommerceService/
    AWSECommerceService.wsdl",
    array('trace' => 1, 'exceptions' => 0));

$request = array(
    'SearchIndex' => 'Books',
    'Keywords' => 'PHP 6'
);

$params = array(
    'AWSAccessKeyId' => '[Your Key]',
    'Operation' => 'ItemSearch',
    'Request' => $request
);

$out = $client->ItemSearchError($params);

if(is_soap_fault($out)) {
    print "Something went wrong!<br>\n";
    print $out->faultstring;
    exit;
} else {
    foreach($out->Items->Item as $item) {
        print '<a href="'. $item->DetailPageURL . '">'.
            $item->ItemAttributes->Title .
            "</a><br>\n";
    }
}
?>
```

将 `exceptions` 数组选项设置为 `0` 意味着如果出错，`SoapClient` 对象将自动返回一个 `SoapFault` 对象。使用 `is_soap_fault` 函数来确定返回的值是否为 `SoapFault` 对象。

`SoapFault` 类公开了属性 `faultcode`（一个数字）和 `faultstring`（一个字符串），详细说明了确切的问题。你应该得到与图 10-4 所示类似的结果，它（非常正确地）解释了你请求了一个无效的方法。

![](img/a1b732997d9cb194dceec0570dc79710_248_0.png)

**图 10-4: 使用 SOAP 扩展检查错误**

如果你希望将 PHP 6 异常与 `try...catch` 一起使用，则将 `exceptions` 参数设置为 `1`。
显然，实现异常处理的方法有很多，你应该选择与你的应用程序整体相匹配的方法。本节的目的仅仅是提醒你注意可用的功能。

## 创建 SOAP 服务器

大多数时候，你会想要创建一个为客户端提供有用服务的服务器，这可以是任何东西，范围从图书价格报价到员工信息再到域名验证。在本节中，你将创建一个可以与客户端连接以接收简短消息的服务器。本讨论使用一个简短的 WSDL 文档来描述 SOAP 应用程序的两个部分如何通信。（你之前已经见过 WSDL 文档的实际应用，因此这里不会再详细讨论。）

## 创建和注册函数

这个简单的示例从客户端接收一个 `name` 字符串，并返回一条消息，表明你应该庆幸 SOAP 如此可靠。打开一个名为 `soapserver.php` 的新代码文件：

```
<?php function sayHello($name) {
    $salutation = "You, $name, will be delighted to know I am working!";
    return $salutation;
}

$server = new SoapServer ("greetings.wsdl");
$server->addFunction("sayHello");
$server->handle();
?>
```

虽然这个示例实际上是一个简单的“hello world”示例，但要开发出真正有用的东西，你不需要走得太远。例如，如果你希望 Web 服务返回数据库中的结果，你只需将返回相关结果的几个函数替换到 SOAP 服务器文件中，将函数添加到服务器，快速修改 WSDL 以反映这些更改，然后就可以开始了。

前面的代码有一个名为 `sayHello()` 的函数，这是这个初创服务提供的唯一方法。然后，可以引用 `greetings.wsdl` 文档（稍后定义）创建服务器，使用 PHP 6 的 `addFunction()` 方法（在前一节“SoapServer Functions”中讨论过）添加 `sayHello()` 函数，然后由 `handle()` 处理请求和响应的繁重工作。从服务器的角度来看，你只需要这些。

### 创建 WSDL 文档

为了让服务对客户端运行良好，你只需要通过 WSDL 文档告诉潜在客户端他们可以如何与服务器通信。这里不会重述 WSDL 的整个概念，但以下是可用于此简单 Web 服务的一个很好示例。自然，它名为 `greetings.wsdl`：

```
<?xml version="1.0" encoding="UTF-8" ?>
<definitions name="greetings"
 targetNamespace="http://server.local/sayHello"
 xmlns:tns="http://server.local/sayHello"
 xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
 xmlns:xs="http://www.w3.org/2001/XMLSchema"
 xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/"
 xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/"
 xmlns="http://schemas.xmlsoap.org/wsdl/">

<message name="sayHelloRequest">
 <part name="name" type="xsd:string" />
</message>
<message name="sayHelloResponse">
 <part name="salutation" type="xsd:string" />
</message>

<portType name="sayHelloPortType">
 <operation name="sayHello">
 <input message="tns:sayHelloRequest"/>
 <output message="tns:sayHelloResponse"/>
 </operation>
</portType>

<binding name="sayHelloBinding" type="tns:sayHelloPortType">
 <soap:binding style="rpc"
 transport="http://schemas.xmlsoap.org/soap/http"/>
 <operation name="sayHello">
 <soap:operation soapAction="" />
```



```
<input>
<soap:body use="encoded" namespace=""
encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" />
</input>
<output>
<soap:body use="encoded" namespace=""
encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" />
</output>
</operation>
</binding>
<documentation>This is Wiley's SOAP server Example</documentation>
<service name="sayHelloService">
<port name="sayHelloPort" binding="sayHelloBinding">
<soap:address location="http://server.local/soap/soapserver.php" />
</port>
</service>
</definitions>
```

这样一来，你就准备就绪了。不过请记住，必须将地址位置 URI 设置为适合你环境的正确值。

现在，所要做的就是使用新服务器。下面这个名为 soapclient.php 的文件即实现了该功能：

```php
<?php $client = new SoapClient("greetings.wsdl");
print_r($client->sayHello("Steve"));
?>
```

浏览该文件将显示略显简略（但相当准确）的结果，如图 10-5 所示，具体结果取决于你替换的名称。

![](img/a1b732997d9cb194dceec0570dc79710_250_0.png)

图 10-5：浏览 soapclient.php 的结果

显然，这个示例非常简单，单独使用时并不十分有用，但希望它能让你了解如何实现自己的 SOAP 服务器。你可以暴露应用程序中对他人有用的任何方面，或者你希望通过 Ajax 或 Flash 访问的任何方面。在典型的 MVC 架构应用程序中，你会创建一个单独的控制器来处理 SOAP 输入和输出，相应的视图使用 SOAP 扩展呈现，以自动生成 XML 输出。除此之外，你可以完全复用模型类中封装的应用程序逻辑，这使得你能够为许多应用程序创建 Web 服务 API，而只需投入较少的额外代码或时间。

虽然 SOAP 是 Web 服务的鼻祖，能够实现数据类型、函数及其返回类型的完全自动发现，但在实际中，这种自动发现实际上很少发生。通常，你知道想要哪些函数、在哪里找到它们以及它们的返回值。这种知识来自阅读 API 文档，而不是编写代码来自动发现这些信息。

大型 Web 服务 API 的 WSDL 文档复杂度可能成为理解其提供功能的障碍。此外，下载 WSDL 文件的步骤（即使已缓存在服务器硬盘上）也会为每个请求增加额外的计算时间。对于你可能向远程 Web 服务（或服务）发出的许多（通常相当简单）请求，如果希望在自己的应用程序中公开这些服务，SOAP 请求的开销就有点过于沉重了。幸运的是，有用于实现 Web 服务客户端和服务器的替代架构。其中最流行的一种称为表现层状态转移（REST）。

## REST

REST 最初由 Roy Fielding（HTTP 规范的主要作者之一）在其 2000 年的博士论文中正式描述，REST 对 Web 服务采用了完全不同的方法。它不使用 SOAP 的 WSDL 文档和 XML 信封结构的所有开销和复杂性，而是使用 GET、POST、PUT 和 DELETE 等主要 HTTP 动词来请求和操作资源，这些资源由明确标识所请求资源的 URL 唯一标识。

为了展示典型 REST 请求可能的样子，请考虑一个在线书店应用程序。要访问 ISBN 为 0470395097 的图书的资源描述符，你可以使用类似 http://example.com/books/0470395097 的 URL。通常，你期望这将返回一份包含图书详细信息的 XML 文档，尽管 REST 架构中未定义返回数据类型。这样的 URL 可以返回图像、HTML 文档、CSV 文件或任何其他数据类型。

由于所有 REST 操作都遵循简单的 URL 结构来标识要创建、读取、更新或删除的资源，通过查看要获取的资源的 URL，你可以很容易地理解自己正在获取什么。更易于使用的 REST 接口采用整洁简单的 URL 结构，如示例所示。其他接口，例如 Amazon REST 接口（稍后将讨论），使用略显“丑陋”的语法，涉及查询字符串参数，但基本思路是相同的。

## REST 与 PHP 6

由于 REST 在其核心只不过是简单的 HTTP 交互，因此没有类似 SOAP 那样的 PHP 扩展用于 REST。事实上，REST 是一种架构设计，而不是像 SOAP 那样的协议。在 PHP 中实现 REST 的最简单方法是使用 curl 扩展来自己实现客户端和服务器组件。你可以更底层地使用 socket 函数，但 curl 扩展使事情容易得多。

典型 REST 操作的返回值通常（但不一定是）XML 文档。让我们使用 simplexml 扩展来解析和操作发送和接收的数据。这是在 PHP 6 中处理 XML 远远最简单的方法。

> 如果你不熟悉此扩展中的函数，请参阅 http://php.net/simplexml 上的文档。

SOAP 扩展使用相对复杂（但标准化）的 XML 信封结构和返回值，这些在 WSDL 文档中预定义。相比之下，REST 舍弃了信封和 WSDL 文件的开销和复杂性；但权衡是，开发人员必须比使用 SOAP 扩展时更贴近 XML。了解如何创建和解析 XML 文档是专业开发人员的基本技能，也是理解本章其余部分大部分讨论所必需的。

## 实现 REST 客户端

让我们回到 Amazon.com API 来举 REST 的示例，因为 Amazon 方便地同时提供 SOAP 和 REST API。值得注意的是，更简单的 REST 接口占 Amazon Web Services 系统请求的 85% 以上，而 SOAP 仅占其余 15%。你很快就会明白为什么这么多开发人员更喜欢 REST 接口。

Amazon REST 接口的完整文档可在 http://aws.amazon.com/documentation/ 找到。简而言之，与 SOAP 接口一样，Amazon REST API 要求你获得 AWS 访问 ID。所有请求都从同一基础 URL 发出，该 URL（与之前伪示例中更简单的 URL 结构不同）使用参数化查询。

下面的简单示例展示了如何使用 REST API 对 PHP 6 图书执行 ItemSearch。请注意，它使用 PHP curl 扩展，必须在你的 PHP 安装中启用。将以下代码输入 php6_books.php：

```php
<?php
//Base URL for all AWS REST operations
define('AWS_BASE_URL',
 'http://ecs.amazonaws.com/onca/xml?Service=AWSECommerceService');
//AWS Access Key ID
define('AWS_ACCESS_KEY_ID', '[Your AWS Key]');

$params = array();
$params['Operation'] = 'ItemSearch';
$params['SearchIndex'] = 'Books';
$params['Keywords'] = 'PHP 6';

//Construct the URL
$url = AWS_BASE_URL . '&AWSAccessKeyId=' . AWS_ACCESS_KEY_ID;
foreach($params as $name => $value) {
    //Need to URL encode in case there are spaces or other funny chars
    //in the values
    $value = urlencode(unicode_encode($value, 'ISO-8859-1'));
    $url .= "&$name=$value";
}

$hc = curl_init($url);
curl_setopt($hc, CURLOPT_RETURNTRANSFER, 1);
$xml = curl_exec($hc);

$out = new SimpleXMLElement($xml);

foreach($out->Items->Item as $item) {
    print '<a href="' . $item->DetailPageURL . '">' .
        $item->ItemAttributes->Title . "</a><br>\n";
}

?>
```

这个代码示例与同名的 SOAP 示例非常相似，但它使用了更熟悉的 curl 扩展和基本 XML 处理，而不是许多开发人员可能不熟悉的 SOAP 扩展。取决于你如何配置 PHP，如果该函数允许 HTTP 请求（这是一个 php.ini 设置），你也可以简单地使用 file_get_contents($url) 来获取 XML。这个示例还有一个好处，就是你可以通过将 $url 值输入 Web 浏览器并在浏览器窗口中查看输出来轻松调试问题。SOAP 扩展让你与远程服务器的实际交互保持足够远的距离，以至于调试基本连接问题通常可能既困难又耗时。

返回的 XML 结构缺少 SOAP 事务的外部信封部分，但除此之外是相同的。因此，本节不包括讨论对 Items 的迭代，因为代码是相同的。

## 构建 REST 服务器

使用 REST 架构创建服务也比使用 SOAP 扩展简单得多，后者涉及向 SOAP 扩展注册函数。下面的示例架构使用 $_SERVER 的 PATH_INFO 值来获取 PHP 文件名之后、查询字符串之前（即 URL 中 ? 之前）的任何内容：

```php
<?php

$DEFAULT_ACTION = 'badAction';

$pathInfo = isset($_SERVER['PATH_INFO']) ? $_SERVER['PATH_INFO'] : '';
```





```
$pathParts = explode('/', substr($pathInfo, 1));
$Action = isset($pathParts[0]) ? $pathParts[0] : $DEFAULT_ACTION;

if(function_exists($action)) {
	$action($pathParts);
} else {
	badAction();
}

//REST functions
function badAction($parts = null) {
	print 'The function specified is invalid';
}

function sayHello($parts) {
	$name = isset($parts[1]) ? $parts[1] : 'undefined';
	$xml = new SimpleXMLElement('<message>Hello, ' . $name . '</message>');
	header('Content-Type: text/xml');
	print $xml->asXML();
}

?>
```

要调用该服务，示例 URL 可能是 `http://server.local/rest/restserver.php/sayHello/Steve`，将产生以下输出：

```
<?xml version="1.0"?>
<message>Hello, Steve</message>
```

请注意，附加参数已在 URL 中提供，而不是将其追加到查询字符串中。这并非必需，如果您偏好，可以随意使用查询字符串参数；但更简洁的 URL 结构赏心悦目，并使 API 更易于记录。

## 总结

利用 Web 服务的能力使您能够包含其他应用程序的数据和功能，并为您的应用程序提供原本可能无法包含的额外、强大的功能。将您的应用程序功能暴露给他人，可以增加代码的整体实用性，并可能为您的网站带来流量。

第 11 章将探讨生成电子邮件和其他与用户通信的更好方式。

## 与用户通信

归根结底，Web 是一种简单的通信方式。最终用户请求一个页面，后台发生某些事情，Web 服务器作为响应返回一些内容。这用一句精辟的话概括了 HTTP 协议；但如果你仅仅局限于通过 HTTP 协议与用户交谈，你就会错过构成真正出色用户界面的重要部分。

在本章中，你将了解用户通信的构建块，以及它如何转化为自然的 PHP 对象层次结构。你将看到如何扩展和开发此层次结构以支持几乎任何形式的电子通信。你还将查看实现某些 PHP 未提供且你在日常开发中可能会发现有用的功能的实际示例。

也许最重要的是，你将学习为什么首先应该与你的用户通信。

## 为什么要通信？

在 Web 的早期，远在 PHP 问世之前，用户体验——即使用你的网站对用户产生的情感影响——在很大程度上是不重要的。内容是关键。事实上，内容就是一切。Web 只不过是一本带有方便标签以便于翻页的杂志。

不再如此。Web 越来越被接受为实现瘦客户端应用程序的绝佳机制，从娱乐门户的简单 Webmail 功能到大公司的复杂多用户库存控制网络。这种巨大的灵活性和覆盖范围，归根结底，就是你最初决定学习 PHP 的原因。

不幸的是，将 Web 作为实现瘦客户端解决方案的手段并非一帆风顺。许多作者（也许出于最良好的意图）省略了提供当今过去那些使瘦客户端架构可用的关键功能的现代等效物。

其中最大的一项是能够在当前用户界面之外与用户通信。考虑一个抽象示例。电话的当前用户界面由话筒和听筒组成，但所有电话都包含铃声，以便你知道何时有来电。这是通知用户事件的示例。

第二个示例是传真机。许多传真机在传真发送成功时会打印送达报告。该报告是辅助于构成当前用户界面的键盘和 LCD 显示器，是让用户保持知情的示例。

最后一个示例。如果你曾经通过电话申请过银行贷款，你无疑会发现，在几分钟内获得贷款是非常容易的（尽管，今天，也许不像上一版本书出版时那么容易了）。尽管如此，银行仍会将需要签署的文件寄送到你的登记家庭住址。即使你在电话中原则上获得批准，在签署并寄回他们寄给你的文件之前，资金也不会进入你的支票账户。这是使用与用户的通信作为一种安全形式、一种验证形式的示例。

还有其他示例，但本章将探讨这里提到的示例如何影响现实世界，以及你如何通过 OOP 机制对它们采取行动。

## 与用户通信的理由

通知、告知和验证——让我们拿这三个示例，尝试将它们应用到 Web 中。这样，你可以发现为什么你可能希望你的应用程序通知、告知或验证你的用户。

## 通知

可能会出现许多场景，你希望通过 Web 浏览器以外的方式向用户通知某些事情。如果你记住 HTTP 是一种所谓的无状态协议，这个问题尤其相关。要让 Web 浏览器在那里等待某事发生，然后再通知用户，并不特别容易。你可以用各种方式做到这一点，但没有一种特别漂亮。

想象一下，你的应用程序有一个复杂的报告系统，使用户能够请求生成关于各种业务细节的报告。特别是如果这些报告对 SQL 要求极高，那么离线生成这些报告（即独立于用户 Web 浏览器发起的请求）是一个强有力的论点。这样，用户在查看报告时就不会面临任何过长的 HTTP 请求。

简单地说，不能保证用户不会在等待页面生成两分钟时放弃并点击停止按钮。在现实场景中，用户将使用 Web 浏览器订购报告，并理解系统会在报告准备好时通知他们（可能是通过电子邮件或其他机制）。

在另一个示例中，想象一个订阅型网站设置为每月第一天自动向用户的信用卡收费。如果因为用户的信用卡在当月账单过程中被拒绝，用户就无法登录网站，那将不是很好的客户服务。相反，你会发出所谓的“异常通知”——即由于发生非同寻常（通常是不好的）事情而发生的通知。在这种情况下，这将以电子邮件的形式，邀请用户登录并提供另一张有效信用卡的详细信息。

当然，通知不限于电子邮件。全世界数据中心的运营商都喜欢使用短信通知发送到他们的手机上，以便在他们身处何处时都能得知关键服务器或进程是否宕机。在美国之外，这些短信在很大程度上取代了寻呼机。

## 信息

向用户传达信息与通知略有不同，因为它不一定是事件驱动的。相反，这是一种完全预期的通信，旨在更新用户关于某事状态的信息。将报纸送到你门廊上的预期到达，与电视节目中紧急警报系统发布的突然通知进行对比。你期待报纸的到来，但关于坦帕湾即将到来的暴风雪的通知却有点出乎意料。

让用户保持知情的一个好例子是来自订阅型网站的每周通讯。这可以是通过汇总当周新闻故事摘录自动生成的东西，也可以是由编辑团队整理的东西。无论哪种方式，你都在让用户保持最新状态。

另一个好例子是在线“电子零售商”的订单更新。如果你订购的书籍在七天内还没有送达，你可能会担心，而一封解释书籍仍在订购中的电子邮件无疑会让你放心。同样，这不是通知。没有任何变化。没有任何新信息。这只是一个旨在让你放心的快速更新。

这种通信方式完全可以适应其他信息传递方式——传真、短信、邮寄，随你挑。你很快就会发现，你之前可能认为完全不同的各种通信媒体，实际上几乎是相同的（至少从软件架构的角度来看）。

## 验证

验证通常是一种为了再次通信而进行的一次性通信方式。你验证某个目标地址，以便在需要再次使用时能够确保其准确性。或者，你可能拥有用户想要的某些信息，但为了双重确认请求用户的身份，你将只将该信息发送到用户的登记地址。

本章前面提到的银行贷款示例代表了更严肃的一面。毕竟，银行希望验证你的正确地址，以便在你还款拖延时派人收回抵押物。然而，许多网站正是以这种方式验证电子邮件地址，以便以后用于直接营销。做到这一点的简单方法是将激活链接（通常是数据库中存储在用户记录上的某种唯一密钥）发送到用户提供的电子邮件地址。用户必须点击链接以激活其会员资格。

类似的方法可以用于为忘记密码的用户抛出一条“救命绳”，但通常通过电子邮件透露他们的密码既不是好主意，也不可行。你不应该以未加密或任何可逆形式存储用户密码，也不应该以明文通过电子邮件传输它们。你当然可以为他们提供一个高度混淆的链接（通常是有限时效的），以便获得暂时访问你的网站的权限，从而设置新密码。





在欧洲（现在通过手机和电子邮件与网站访客进行沟通已日益普遍），有些网站会将激活码以短文本消息的形式发送到用户注册时提供的手机号码。然后，用户必须在网站上输入该激活码，以证明其提供的号码有效。

顺便提一下，这种短信服务（SMS）发送代码的技术实际上可以作为一种穷人的双层身份验证形式。系统上的身份验证通常由以下三个密钥中的一个或多个提供。这些是 *你是谁*（指纹、虹膜扫描，甚至来源IP地址），《你知道的》（密码），和 *你拥有的*（密钥或令牌）。每个都是一个 *因素*。公认的做法是，守护任何类型敏感数据的任何系统都应实现多于一个这样的机制。通过在输入用户名和密码时向已注册的手机发送唯一代码，就提供了这种额外的保护层。

## 跳出Web浏览器思考

通过认识到替代通信机制（尤其是电子邮件）的潜力，您可以为网站用户提供远更出色的用户体验。在下一节中，您将探讨如何在PHP中实现这一点（当然，除了`mail()`函数）。

> 也许值得强调的是，在PHP代码中使用`mail()`函数发送电子邮件，相当于六岁孩子的纸杯电话相对于数字电话的水平。它绝不应该出现在严肃的生产网站上。

## 通信类型

在深入研究通信代码之前，先暂时抽离一下问题。这样做可以帮助你更好地把握眼前明显的出站通信类层次结构，你需要自己编写它，因为PHP没有提供它。所有通信都有哪些共同点？

## 所有通信都有 ...

你可以相当合理地说，所有通信都有以下内容：

- 收件人 — 一个或多个接收通信的人员。此通信可以采用电子邮件地址、传真号码、手机号码、邮政地址、邮政信箱、信箱格等形式。
- 消息 — 您要发送的实际正文。消息可以以纯文本或HTML（用于电子邮件）、信纸大小的位图（用于传真）、160个字符的文本（用于短消息）、11 KHz音频流（用于自动电话呼叫）等形式传输。

## 并非所有通信都有 ...

另一方面，你也必须了解各种通信类型之间的差异。并非所有通信都有以下内容：

- 主题 — 通常，只有电子邮件有主题。
- 内容变体 — 如今电子邮件通常将HTML和纯文本版本交织在一个MIME包中发送（关于这一点稍后详述）。
- 附件 — 这些特定于电子邮件和短消息。
- 抄送和密抄收件人的显示或区分 — 如果你将传真、短消息或信件发送给多个人，除非你列出清单并在正文中添加，否则没人会知道还有谁收到了消息。

## 收件人呢？

电子邮件的收件人与短消息的收件人完全是两种不同类型的收件人。请查看表 11-1 所示的比较。

| 通信类型 | 收件人组件 | 格式 |
|---|---|---|
| 电子邮件 | 姓名 | 字符串 |
| | 地址 | 符合RFC 822规范的字符串 |
| 发往手机的SMS短信 | 号码 | 字符串，由加号、国家代码和本地号码组成 |
| 传真 | 号码 | 字符串，由电信公司可识别的电话号码组成 |
| 信件 | 姓名 | 字符串 |
| | 门牌号 | 整数 |
| | 街道 | 字符串 |
| | 城镇/城市 | 字符串 |
| | 州 | 字符串 |
| | 邮编 | 符合美国邮政服务ZIP格式的字符串 |

### 收件人类：OOP思维的快速测试

所有消息都有收件人（而且通常不止一个）。鉴于这些收件人明显比字符串更复杂，最好有一个类来表示它们，并提供诸如`isValid()`之类的有用方法来确定收件人是否有效。

困难显而易见。当需要处理如此大量的数据变化时，如何有效地实现这样的类？

你可以创建一个涵盖所有可能场景的单个`Recipient`类，但这不太符合OOP规范，因为大量成员方法和变量特定于一种通信形式，与其他形式无关。解决方案必须是拥有一种通用的`Recipient`类，每种特殊情况都有其自己的类；但是，如何将这些特殊情况收件人与主`Recipient`类关联起来呢？

首先，拒绝使用传统的类继承。尽管在技术上可行，但这仍然是对OOP设计的误用。超类（即被扩展以形成子类的类）本身必须是一个独立的类。`Ford`是超类`Car`的子类，尽管`Ford`可能包含额外的或甚至重载的方法或成员变量，但`Car`的某些特性表明它本身（或曾经）是一个有用的对象。它有自己的方法（如`Drive`和`Shift`）和自己的成员变量（如`Registration`和`Color`），并且这些不太可能被重载。特定类型的收件人（例如电子邮件收件人）可能拥有自己的成员变量和方法，就像`Ford`一样，但它不会从父级通用收件人超类继承任何内容。从前面展示的表 11-1 中一目了然，通用收件人不能有任何有用的成员变量或方法。因此，你必须拒绝使用类继承。

如果你考虑全局，答案就显而易见了。你的通信框架可能需要这些收件人对象提供什么？实际上，你可以将其限制为仅两个方法，即通信框架将访问的`isValid()`和`getStringRepresentation()`。这两个方法将根据上下文返回框架可用的字符串表示。任何其他方法（例如`setHouseNumber`）仅供你的应用程序用于填充收件人。你可以相当肯定地说，通信框架永远不会触碰它们。

因此，任务可以总结如下：创建一种手段，使代表不同通信媒体类型收件人的多个不同类能够被外部其他类的框架普遍访问，这样以后可以在不修改该外部框架的情况下添加其他不同的类。

解决方案是为通用收件人类（实际上根本不是一个类）创建一个`interface`。该接口为这两个关键方法（`isValid()`和`getStringRepresentation()`）提供定义，各个收件人对象必须如所示提供这些方法。

考虑以下代码片段，它提供了这样的通用接口。你可能希望此时将此代码保存为`recipient.php`：

```php
<?php
interface Recipient {
    public function isValid();
    public function getStringRepresentation();
}
?>
```

你可能会想实现一个抽象收件人类以达到几乎完全相同的效果，但这将再次暴露糟糕设计的丑陋面目。同样，请记住，你所理解的收件人没有有用的属性和有用的方法。当你只想为其他类提供一种共同手段来与一组不相关的类进行交互时，试图以任何暗示类状态的方式扩展它都是愚蠢的。如果你对各种收件人类缺乏共性有疑问，请参阅表 11-1。

## 电子邮件收件人类

看看如何实现这一点。你不会复现每种收件人类型，所以先看一个简单的——电子邮件收件人类。你可以将此代码保存为`emailrecipient.php`——在本章中你还会用到它。首先声明一个实现先前声明的 Recipient 接口的类：

```php
<?php
class EmailRecipient implements Recipient {
```

添加一些成员变量来存储电子邮件收件人的重要属性。如表 11-1 所示，电子邮件收件人既有收件人姓名，也有收件人地址：

```php
private $recipient_name;
private $recipient_address;
```

现在必须为 Recipient 接口中声明的每个方法提供实现。实际上，只有两个方法。第一个方法将在使用它的应用程序设置好收件人后验证收件人。在输入 preg_match() 检查的正则表达式时要小心——它需要在编辑器中占据一行：

```php
public function isValid() {
    if (preg_match("/^[\\<>\\r\\n]{1,}$/", $this->recipient_name)) {
        return(false);
    };
    if (preg_match("/^([A-Z0-9._%+-]+)(@)([A-Z0-9._%+-]{2,4})$/i", $this->recipient_address)) {
        return(true);
    } else {
        return(false);
    };
}
```

这里的做法很简单。对收件人执行几次正则表达式匹配。首先，验证收件人姓名，确保其由一个或多个有效字符组成。然后，根据正则表达式检查电子邮件地址，以确保其符合 RFC 822 格式。





接下来，你必须提供某种方式来获取收件人的智能（即，可直接使用）字符串表示：

```php
public function getStringRepresentation() {
    $strMyRepresentation = "";
    if ($this->recipient_name) {
        $strMyRepresentation .= $this->recipient_name . " ";
    };
    $strMyRepresentation .= "<" . $this->recipient_address . ">";
    return($strMyRepresentation);
}
```

因为电子邮件地址广泛接受的格式是 First Name Last Name <user@example.com>，所以这里采用该格式。

类的其余部分专门用于访问器方法——即，用于获取和设置电子邮件收件人各种属性的方法。如所示，你已在构造函数中提供了一种简单的方式来设置所有这些内容。对于其他收件人（例如传统邮件信件的收件人），这样做可能会很麻烦：

```php
public function __construct($strRecipientAddress, $strRecipientName = "") {
    $this->recipient_name = $strRecipientName;
    $this->recipient_address = $strRecipientAddress;
}
public function setRecipientName($strRecipientName) {
    $this->recipient_name = $strRecipientName;
}
public function setRecipientAddress($strRecipientAddress) {
    $this->recipient_address = $strRecipientAddress;
}
public function getRecipientName() {
    return($this->recipient_name);
}
public function getRecipientAddress() {
    return($this->recipient_address);
}
```

这就结束了电子邮件收件人类，它是通用 Recipient 接口的一个实现。如果你想在此阶段将其保存为 emailrecipient.php，也不会有人因此责备你。

尽管你尚未到达通信框架部分，但可以使用以下示例代码片段来测试此功能。你可能希望将其命名为 test1.php，以便完成后可以在浏览器中打开它：

```php
<?php
require("recipient.php");
require("emailrecipient.php");

$objEmailRecipient = new EmailRecipient("fiona@example.com", "Fiona Chow");
if ($objEmailRecipient->isValid()) {
    print "Recipient is valid! ";
    print "The string representation of this recipient would be: " .
        htmlentities($objEmailRecipient->getStringRepresentation()));
} else {
    print "Recipient is not valid!";
};
?>
```

这将产生以下输出：

```
Recipient is valid! The string representation of this recipient would be:
Fiona Chow <fiona@example.com>
```

如果你更详细地看一下 `EmailRecipient` 类，就会发现它有多简单。这两个私有成员变量专属于此类，构造函数以及（有些多余的）`setRecipientName` 和 `setRecipientAddress` 访问器方法及其（不那么多余的）`get` 对应方法也是如此。

因为你已声明该类实现 `Recipient` 接口，因此有义务提供该接口中所述的两个方法。如果不提供，PHP 会有用地返回一条错误消息。

在 `getStringRepresentation` 方法中，你只需将各部分粘合在一起，即可形成收件人姓名和电子邮件地址的符合 RFC822 标准的可用表示形式。你可以直接将其放入 SMTP 会话中。

在 `isValid` 方法中，你会检查收件人姓名中是否有可能混淆 SMTP 服务器的不良字符。然后，你会根据正则表达式检查电子邮件地址的基本语法有效性。

## 其他实现

你刚刚实现了一个 `EmailRecipient` 类，以简洁地封装电子邮件收件人的概念。其他类型的通信有其自身的收件人类型，每个都需要 `Recipient` 接口的实现。

你可以遵循非常类似的过程来实现此类替代收件人类型。首先，确保存在足够的成员变量来存储该收件人类型的每个属性，并且你有合适的 `Get` 和 `Set` 访问器方法来读写这些成员变量。其次，实现 `Recipient` 接口要求的强制方法：验证器方法和字符串表示方法。

## 通信类

尽管收件人在本质上各不相同，但通过对任何和所有收件对象进行精简的接口访问，你可以大大简化你的通信类。

通信对象字面上就是如此——无论采用何种方法的单次通信。我们并不特别在意是哪种方法，甚至也不会提及可能的方法有哪些。

通信类本身永远不会被实例化。相反，它将由代表要使用的特定通信形式的类扩展：`EmailCommunication`、`SMSCommunication` 等等。

然而，与通用收件人构造不同，它将拥有自己的实用方法。因此，它确实将是一个真正的类，而不仅仅是一个接口。但是，一个方法——`send`——将被声明为抽象方法，因此仅在子类中实现。

`Communication` 的子类当然可以拥有自身的方法和成员变量，以补充其超类中的方法和成员变量。这可能的一个用途是以某种方式操纵 `Communication` 的消息属性的方法。一个例子是在 `SMSCommunication` 中加载位图 (.BMP) 文件的方法，以将其作为蜂窝电话运营商徽标发送，替代标准文本消息。

## 使用集合存储收件人

无论你的类代表哪种通信类型，前面的讨论应该已经清楚，它总会有某种收件人。因此，需要一个受保护的成员变量（不是私有的——它需要可由子对象访问）来存储此类收件人。数组是一个明显的选择，但它灵活性很小，并且需要你编写大量代码。

然而，在第 5 章中，你已了解集合的概念——本质上是一种面向对象的机制，用于将一组对象存储为单个变量。以下类是你在该章中遇到的 Collection 类的精简版。它将使本章其余代码更易于跟随。你应该将以下内容另存为 `collection.php` 并暂时保留——你很快就会用到它：

```php
<?php
class Collection implements Iterator {
    protected $_members = array();     //collection members in a linear array
    protected $_keys = array();        //names of keys in numeric order to match
                                        //linear array
    protected $position = 0;           //current position

    public function __construct() {
        $this->position = 0;
        $this->_members = array();
        $this->_keys = array();
    }

    public function rewind() {
        $this->position = 0;
    }

    public function current() {
        return($this->_members[$this->position]);
    }

    public function addItem($obj, $key = NULL) {
        $this->_members[] = $obj;
        if (!$key) {
            $key = sizeof($this->_members) - 1;
        }
        $this->_keys[] = $key;
        $this->position = sizeof($this->_members);
    }
    public function key( ) {
        return($this->_keys[$this->position]);
    }
    public function next( ) {
        ++$this->position;
    }
    public function valid( ) {
        return(isset($this->_members[$this->position]));
    }
    public function length( ) {
        return sizeof($this->_members);
    }
    public function exists($key) {
        // resolve key to index
        $idx = -1;
        for ($i=0; $i<=sizeof($this->_keys)-1; $i++) {
        if ($this->_keys[$i] == $key) {
            $idx = $i;
        };
        }
        if ($idx == -1) {
            return(false);
        };
        return (isset($this->_members[$idx]));
    }
}
?>
```

有了集合类，你可以编写一个通信类来使用它。

## 通信类本身

查看以下代码，你应将其另存为 communication.php。请注意，它使用了你刚刚编写的简单集合类，以存储其收件人集合：

```php
<?php
abstract class Communication {
protected $arRecipientCollection;
private $strMessage;
```



protected $strErrorMessage;
protected $errorCode;

abstract public function send();
public function __construct() {
  $this->strMessage = "";
}

public function addRecipient($objRecipient, $strIdentifier = "") {
  $strRecipient = $objRecipient->getStringRepresentation();
  if (!$strIdentifier) {
    $strIdentifier = $strRecipient;
  };
  $this->arRecipientCollection->addItem($objRecipient, $strIdentifier);
}

public function removeRecipient($strIdentifier) {
  $this->arRecipientCollection->removeItem($strIdentifier);
}
protected function _setMessage($strMessage) {
  $this->strMessage = $strMessage;
}

protected function _getMessage() {
  return($this->strMessage);
}

public function getErrorMessage() {
  return($this->strErrorMessage);
}

public function getErrorCode() {
  return($this->errorCode);
}
} ?>

由此可见，你将收件人集合声明为 protected。这意味着虽然它不能从应用程序的代码中随意修改，但可以被 Communication 类的子类随意修改——这是一件好事。

你可能已经注意到，这些示例大胆地将传递给 addRecipient 的收件人对象添加到收件人集合中，即使你完全不知道该对象是什么类型，也同样不知道 arRecipientCollection 是什么类型的集合。你可能会认为这是运行时错误的温床，但实际上是由子类初始化集合，它会将其变成自己想要的任何类型的集合。只要作为收件对象传递的任何内容支持先前开发的接口，并且与子类要求的类型相同，就不会有问题。

将对象的字符串表示作为集合的合适键。message 属性保持为 private，只能通过 _setMessage 和 _getMessage 进行操作，且仅可从子类访问。暂时无需担心错误消息和错误代码成员变量。你稍后会了解它们。

在实际中如何使用这个？很简单，你扩展它以形成一个有用的子类。在下一节中，你将查看 `EmailCommunication`，正如名称所暗示的，它用于向一个或多个 `EmailRecipient` 对象发送消息。

## 向您的用户发送电子邮件

EmailCommunication 是 Communication 的子类。首先，你需要一种简单的方法来强制超类的收件人集合仅包含 `EmailRecipient` 对象。你可以通过稍微重构 Collection 类来形成一个名为 `EmailRecipientCollection` 的子类来实现这一点。从定义上讲，它只能由 `EmailRecipient` 成员组成：

```php
<?php
class EmailRecipientCollection extends Collection {
    public function addItem(EmailRecipient $obj, $key = null) {
        parent::addItem($obj, $key);
    }
}
?>
```

请注意，这不提供任何新功能。它仅通过类类型提示（Class Type Hints）来强制新成员必须遵守的类类型。

现在 PHP 已理解这个类并将其保存为 emailrecipientcollection.php，你可以实现 `EmailCommunication` 类本身了。

## 构建测试版本

最好先构建一个功能精简的实现来测试 OOP 接口。毕竟，如果你能把这做好，其余部分应该相当简单。通过使用一些策略性的输出，你可以了解发生了什么，并确认逻辑是否有效。

在确定逻辑，因此 OOP 集成和接口都能正确工作后，你可以专注于实现——也就是说，将电子邮件发送出去。

以相当标准的方式开始类，声明它及其两个属性：一个是可见地址，另一个是可见抄送地址的集合。你无需担心盲抄送地址；它们不可见，因此可以完全由父类 `Communication` 处理：

```php
<?php
class EmailCommunication extends Communication {
    private $objApparentPrimaryRecipient;       // Visible To: address
    private $arObjApparentSecondaryRecipients;  // Visible Cc: address(es)
```

接下来，提供设置电子邮件主要收件人的方法。请注意，该类向父类的主收件人集合（通用）添加收件人，同时设置主要可见收件人（特定于 `EmailCommunication` 类）：

```php
public function setPrimaryRecipient($objRecipient) {
if (!($this->arRecipientCollection->exists(
$objRecipient->getStringRepresentation()))) {
parent::addRecipient($objRecipient);
}
$this->objApparentPrimaryRecipient = clone $objRecipient;
}
```

添加和删除抄送（Cc：）收件人的方法大致相同。同样，你需要同时操作父集合和本地可见收件人数组：

```php
public function addCarbonRecipient($objRecipient) {
if (!($this->arRecipientCollection->exists(
$objRecipient->getStringRepresentation()))) {
parent::addRecipient($objRecipient);
};
if (!($this->arObjApparentSecondaryRecipients->exists(
$objRecipient->getStringRepresentation()))) {
$this->arObjApparentSecondaryRecipients->addItem(
$objRecipient, $objRecipient->getStringRepresentation());
};
}
public function removeCarbonRecipient($objRecipient) {
if (!($this->arRecipientCollection->exists(
$objRecipient->getStringRepresentation()))) {
parent::removeRecipient($objRecipient);
};
if (($this->arObjApparentSecondaryRecipients->exists(
$objRecipient->getStringRepresentation()))) {
$this->arObjApparentSecondaryRecipients->removeItem(
$objRecipient->getStringRepresentation());
};
}
```

添加和删除盲收件人的原理相同，只是你不要触碰可见收件人列表：

```php
public function addBlindRecipient($objRecipient) {
if (!($this->arRecipientCollection->exists(
$objRecipient->getStringRepresentation()))) {
parent::addRecipient($objRecipient);
}
}
public function removeBlindRecipient($objRecipient) {
if (!($this->arRecipientCollection->exists(
$objRecipient->getStringRepresentation()))) {
parent::removeRecipient($objRecipient->getStringRepresentation());
}
}
```

现在将注意力转向构造函数，它必须将超类集合初始化为适当类型的集合，并将本地可见收件人集合初始化为另一个相同类型的集合（尽管内容不一定相同）。请注意，完成后你也要调用父类构造函数：

```php
public function __construct() {
  // Superclass collection
  $this->arRecipientCollection = new EmailRecipientCollection();
  // Local collection of visible (CC:) recipients
  $this->arObjApparentSecondaryRecipients = new EmailRecipientCollection();
  parent::__construct();
}
```

接下来是测试用的 send 方法，用于确保你的类能正确工作：

```php
public function send() {
  print "ACTUAL RECIPIENTS<BR><BR>";
  foreach ($this->arRecipientCollection as $strRecipientIdentifier =>
  $objEmailRecipient) {
  print "NAME: " . $objEmailRecipient->getRecipientName() . "<BR>";
  print "EMAIL ADDRESS: " . $objEmailRecipient->
  getRecipientAddress() . "<BR>";
  };
  print "<BR><BR>APPARENTLY TO RECIPIENT<BR><BR>";
  print "NAME: " . $this->objApparentPrimaryRecipient->
  getRecipientName() . "<BR>";
  print "EMAIL ADDRESS: " . $this->
  objApparentPrimaryRecipient->getRecipientAddress() . "<BR>";
  print "<BR><BR>APPARENT SECONDARY RECIPIENTS<BR><BR>";
  foreach ($this->arObjApparentSecondaryRecipients as
  $strRecipientIdentifier => $objEmailRecipient) {
  print "NAME: " . $objEmailRecipient->getRecipientName() . "<BR>";
  print "EMAIL ADDRESS: " . $objEmailRecipient->
  getRecipientAddress() . "<BR>";
  };
}
```

让我们更详细地检查前面的代码。首先，注意成员属性：

```php
private $objApparentPrimaryRecipient; // Visible To: address
private $arObjApparentSecondaryRecipients; // Visible Cc: address (es)
```

这两个成员属性除了继承自 Communication 超类的主收件人列表之外还存在。它们代表一个 EmailRecipient 对象，表示电子邮件直接发送给谁（“To:”行），以及一个表示任何抄送（Cc：）地址的 EmailRecipients 集合。严格来说，这两个成员属性并不重要于确定谁会收到消息。这仍然由超类中的集合处理。然而，它们的存在是为了格式化电子邮件，以便“主”收件人和“Cc:”收件人出现在消息标头的正确位置。





构造方法负责设置这两个额外的私有成员变量，并顺便调用父类构造方法。

用于添加和移除主接收人、抄送接收人和密送接收人的各种方法的工作方式大体相同。它们在执行相关操作前，会检查集合中是否存在该键（键为接收人对象的字符串表示）对应的对象。这是通过使用 `collection` 对象提供的 `exists` 方法来实现的。

看看一些测试地址，以证明它能正常工作。然后你可以回头查看实际发送邮件的方式。要执行以下代码，你需要 `require()` 本章迄今开发的所有类。将此文件命名为 `test2.php`，以便在 Web 浏览器中查看：

```php
<?php
require("collection.phpm");
require("communication.phpm");
require("emailcommunication.phpm");
require("recipient.phpm");
require("emailrecipient.phpm");
require("emailrecipientcollection.phpm");
$objEmail = new EmailCommunication;
$objEmailRecipient = new EmailRecipient("ed@example.com",
 "Ed Lecky-Thompson");
$objEmailCCRecipient = new EmailRecipient("ted@example.com",
 "Ted Lecky-Thompson");
$objEmailBCCRecipient = new EmailRecipient("zed@example.com",
 "Zed Lecky-Thompson");
$objEmail->setPrimaryRecipient($objEmailRecipient);
$objEmail->addCarbonRecipient($objEmailCCRecipient);
$objEmail->addBlindRecipient($objEmailBCCRecipient);
$objEmail->send(); ?>
```

运行上述代码。你应该会得到如下所示的输出：

```
ACTUAL RECIPIENTS

NAME: Ed Lecky-Thompson
EMAIL ADDRESS: ed@example.com
NAME: Ted Lecky-Thompson
EMAIL ADDRESS: ted@example.com
NAME: Zed Lecky-Thompson
EMAIL ADDRESS: zed@example.com

APPARENTLY TO RECIPIENT

NAME: Ed Lecky-Thompson
EMAIL ADDRESS: ed@example.com

APPARENT SECONDARY RECIPIENTS

NAME: Ted Lecky-Thompson
EMAIL ADDRESS: ted@example.com
```

这看起来相当不错。从代码中可以看出，Ed 是这封电子邮件的主接收人，Ted 被抄送，Zed 被密送。当 Ed 收到邮件时，他能在 To: 行看到自己的名字，在 Cc: 行看到 Ted 的名字。Ed 不知道 Zed 收到了邮件。当 Ted 收到邮件时，他会看到差不多同样的内容。同样，他不知道 Zed 被密送了这封重要邮件。当 Zed 收到邮件时，他不会在任何地方看到自己的名字，但他能推断出自己一定是在原始邮件中被密送的。

这个虚拟测试实现的输出表明代码是正确的。实际接收人列表显示了电子邮件的所有三个真实接收人。主接收人是正确的，抄送接收人也列出正确。

## 传达消息

要使 `EmailCommunication` 类正常工作，你必须做几件事。

首先，你必须构建电子邮件的正文，并将其放入 `message` 成员变量中。简单的纯文本电子邮件包含两部分：标头和正文。幸运的是，两者之间仅由一个空行分隔，并无更复杂的内容。标头包含发件人地址、收件人地址、主题、Cc: 地址以及大量其他细节。

现在，添加两个成员变量：一个用于主题行，一个用于发件人。发件人同样可以是 `EmailRecipient` 对象，因为发件人和接收人一样，都有姓名和地址：

```php
private $objApparentSender; // Visible From: address
private $strSubjectLine; // Subject line
```

使用一些基本方法，将允许类的用户设置这些属性。

暂且假设你处理的是纯文本电子邮件。你添加一个简单的方法，以允许公开设置 message 属性。message 属性与电子邮件正文同义，因为标头将单独管理：

```php
public function setSubject($strSubject) {
	$this->strSubjectLine = $strSubject;
}

public function setMessageBody($strMessageBody) {
	$this->setMessage($strMessageBody);
}

public function setSender($objSender) {
	$this->objApparentSender = $objSender->__clone();
}
```

现在剩下要做的就是将 `send()` 方法转换为能够组装标头和正文、将它们粘合在一起，并将其发送到互联网上的内容。

该如何操作呢？最简单的方法是使用 PEAR 的 `Net_SMTP` 包，它与这种设置非常契合，同时也再次说明了 PEAR 在避免应用程序开发中重复造轮子方面为何如此有用。`Net_SMTP` 包可能已经在你的 PHP 环境中安装。如果没有，请以常规方式安装。

## 第二部分：学习高级开发技术

使用 Net_SMTP 包的基本语法很简单。你可以直接把组装好的消息原样交给它，无需更改。只需告诉它与邮件服务器通信时要使用的操作数。邮件服务器最低需要一个发件人和一个接收人列表。服务器不会查看你的标头。这就是密送能够工作的原因。虽然服务器被告知将消息投递给该接收人，但接收人永远不会出现在标头的任何位置。

以下示例逐步展示了 Net_SMTP 的基本用法，假设完成的消息在 $full_message_content 中，而接收人数组存在于 $rcpt 中：

```php
if ( ! $smtp = new Net_SMTP("mail") ) {
    die("Unable to instantiate Net_SMTP object\n");
}
```

首先，使用你的 SMTP 服务器名称实例化 Net_SMTP 类的一个新实例，如果出于某种原因无法做到，则终止：

```php
if (PEAR::isError($e = $smtp->connect())) {
    die($e->getMessage() . "\n");
}
```

接下来，确保你可以连接到刚才指定的 SMTP 服务器；如果不能，则终止：

```php
if (PEAR::isError($smtp->mailFrom("sender@example.com"))) {
    die("Unable to set sender\n");
}
```

在这里，发件人被设置为 sender@example.com：

```php
foreach($rcpt as $recipient) {
    if (PEAR::isError($res = $smtp->rcptTo($rcpt))) {
        die("Unable to add recipient: " . $res->getMessage() . "\n");
    }
}
```

现在遍历你的接收人数组，将每个接收人添加到 Net_SMTP 类实例中，如果任何单个接收人无法添加，则终止：

```php
if (PEAR::isError($smtp->data($full_message_content))) {
    die("Unable to send data\n");
}
$smtp->disconnect();
```

最后，发送你的消息并与 SMTP 服务器断开连接。

请注意，此示例使用 mail 作为远程 SMTP 服务器的主机名。如果你在 Linux 或类似系统上运行，可以将主机名 mail 的引用添加到 /etc/hosts 文件中，指向 127.0.0.1，一切都会开箱即用地正常工作。否则，你必须找到最近的友好 SMTP 服务器来为你中继，并改用该服务器。

现在请看以下包含通过 `Net_SMTP` 进行 SMTP 发送的完整 `EmailCommunication` 类：

```php
class EmailCommunication extends Communication {
private $objApparentSender; // Visible From: address
private $strSubjectLine; // Subject line
private $objApparentPrimaryRecipient; // Visible To: address
private $arObjApparentSecondaryRecipients; // Visible Cc: address(es)

public function __construct() {
// Superclass collection
$this->arRecipientCollection = new EmailRecipientCollection();
// Local collection of visible (CC:) recipients
$this->arObjApparentSecondaryRecipients = new EmailRecipientCollection();
parent::__construct();
}

public function setPrimaryRecipient($objRecipient) {
if (!($this->arRecipientCollection->exists(
$objRecipient->getStringRepresentation()))) {
parent::addRecipient($objRecipient);
}
$this->objApparentPrimaryRecipient = clone $objRecipient;
}

public function addCarbonRecipient($objRecipient) {
if (!($this->arRecipientCollection->exists(
$objRecipient->getStringRepresentation()))) {
parent::addRecipient($objRecipient);
};
if (!($this->arObjApparentSecondaryRecipients->exists(
$objRecipient->getStringRepresentation()))) {
$this->arObjApparentSecondaryRecipients->addItem(
$objRecipient, $objRecipient->getStringRepresentation()));
};
}

public function removeCarbonRecipient($objRecipient) {
if ($this->arRecipientCollection->exists(
$objRecipient->getStringRepresentation()))) {
parent::removeRecipient($objRecipient);
};
if (($this->arObjApparentSecondaryRecipients->exists(
$objRecipient->getStringRepresentation()))) {
$this->arObjApparentSecondaryRecipients->removeItem(
$objRecipient->getStringRepresentation()));
};
}

public function addBlindRecipient($objRecipient) {
if (!($this->arRecipientCollection->exists(
```



$objRecipient->getStringRepresentation()))) {
    parent::addRecipient($objRecipient);
}
}

public function removeBlindRecipient($objRecipient) {
    if (!($this->arRecipientCollection->exists(
        $objRecipient->getStringRepresentation()))) {
        parent::removeRecipient($objRecipient->getStringRepresentation());
    }
}

public function setSubject($strSubject) {
    $this->strSubjectLine = $strSubject;
}

public function setMessageBody($strMessageBody) {
    $this->_setMessage($strMessageBody);
}

public function setSender($objSender) {
    $this->objApparentSender = $objSender->__clone();
}

public function send() {

    // Establish headers
    $strHeaders .= "From: " .
        $this->objApparentSender->getStringRepresentation() . "\n";
    $strHeaders .= "To: " .
        $this->objApparentPrimaryRecipient->getStringRepresentation() . "\n";
    foreach ($this->arObjApparentSecondaryRecipients as $strRecipientIdentifier =>
        $objEmailRecipient) {
        $strHeaders .= "Cc: " . $objEmailRecipient->getStringRepresentation() . "\n";
    }
    $strHeaders .= "Date: " . date('D, M j H:i:s T Y O') . "\n";

    // Establish body
    $strBody = $this->_getMessage();

    // Pull together to form complete email, correctly formatted
    $strFullEmail = $strHeaders . "\n" . $strBody;

if (!($smtp = new Net_SMTP("mail"))) {
    $this->strErrorMessage = "Unable to instantiate Net_SMTP object";
    $this->errorCode = 1;
    return(false);
}

if (PEAR::isError($e = $smtp->connect())) {
    $this->strErrorMessage = $e->getMessage();
    $this->errorCode = 2;
    $smtp->disconnect();
    return(false);
}

if (PEAR::isError($smtp->mailFrom(
    $this->objApparentSender->getStringRepresentation())))) {
    $this->strErrorMessage = "Unable to set sender";
    $this->errorCode = 3;
    $smtp->disconnect();
    return(false);
}

// Send to each recipient
foreach ($this->arRecipientCollection as $strRecipientIdentifier =>
    $objEmailRecipient) {
    $strThisAddress = $objEmailRecipient->getRecipientAddress();
    if (PEAR::isError($res = $smtp->rcptTo($strThisAddress))) {
        $this->strErrorMessage = "Unable to add recipient " . $strThisAddress;
        $this->errorCode = 4;
        $smtp->disconnect();
        return(false);
    }
};

if (PEAR::isError($smtp->data($strFullEmail))) {
    $this->strErrorMessage = "Unable to send data to server";
    $this->errorCode = 5;
    $smtp->disconnect();
    return(false);
}
$smtp->disconnect();
return(true);
}
};

请注意这种方法的几点。首先，当收件人被添加为主要收件人或抄送（Cc）列表的成员时，可以将收件人添加到父类持有的集合中，然后在添加到表面收件人列表之前克隆收件人对象。这一步并非至关重要，但这意味着你可以在 `EmailRecipient` 类中实现自己的 `clone()` 方法（如果需要），以修改制作此副本时采取的行为。

其次，本示例使用 `Communication` 父类的错误代码和错误消息成员变量。这些变量可通过公共函数访问。你可以使用它们来调试应用程序。电子邮件有时是一种不可预测的现象，失败可能由多种场景导致，包括无法连接到 SMTP 服务器、被拒绝向特定 IP 地址发送电子邮件的权限，或者收件人被 SMTP 服务器直接拒绝。

第三，代码 `date("D, M j H:i:s T Y O")` 用于构建电子邮件标头的日期属性。快速查看 PHP 文档会提醒你，这会生成格式为 `Tue, Jul 20 22:58:58 BST 2004 +0100` 的时间戳，这是电子邮件标头所需的格式。

要测试最终可用的类，可以编写类似以下代码：

```php
$objEmail = new EmailCommunication;
$objEmailRecipient = new EmailRecipient("ed@example.com", "Ed Lecky-Thompson");
$objEmailCCRecipient = new EmailRecipient("cc@example.com", "Ted Lecky-Thompson");
$objEmailSender = new EmailRecipient("info@example.com", "Test Sender");
$objEmail->setPrimaryRecipient($objEmailRecipient);
$objEmail->setSender($objEmailSender);
$objEmail->setMessageBody("Hello, \n\nThis is a short test email.\n\nGoodbye!");
$objEmail->setSubject("Test Subject");
$objEmail->addCarbonRecipient($objEmailCCRecipient);
$objEmail->addBlindRecipient($objEmailBCCRecipient);

if ($objEmail->send()) {
    print "DONE! All went well! Mail sent successfully.";
} else {
    print "Sorry, didn't send mail successfully.";
};
```

## 精明使用模板

在第 13 章中，我们讨论了如何通过模型-视图-控制器（MVC）范式将应用程序逻辑与显示逻辑分开，这通常是一个非常好的主意，值得在你自己的应用程序架构中采用。

第 13 章还介绍了一个名为 Smarty 的包，它可以帮助你实现这一目标，并描述了它在传统 Web 应用程序实现中的用处。Smarty 还有一个常被忽略的用途：它可以生成模板驱动的电子邮件输出。

如你所知，十有八九，你发送给用户的电子邮件都大同小异。可能只有几个标签、“亲爱的”之后的名字，或者账户号码会发生变化，除此之外没什么不同。

将变量拼接到字符串中对于较小的操作是可行的，但当这些电子邮件变得越来越大、越来越难以处理，甚至包含打印的数组结构时，事情就会变得困难。解决方案是使用 TemplatedEmailCommunication 类。

TemplatedEmailCommunication 类充分利用了 Smarty。如果你还没有读过第 13 章，现在正是绝佳时机。你需要知道 Smarty 的工作原理才能实现这一点。

你即将创建的类实际上扩展了 EmailCommunication，因此请先确保它可以正常运行；同时还需要安装并配置好 Smarty：

```php
class TemplatedEmailCommunication extends EmailCommunication {

    private $path_to_template_file;
    private $objSmarty;

    public function __construct($strPathToTemplateFile) {
        $this->objSmarty = new Smarty;
        $this->path_to_template_file = $strPathToTemplateFile;
        parent::__construct();
    }

    public function setParameter($strParameter, $strValue) {
        $this->objSmarty->assign($strParameter, $strValue);
    }

    public function parse() {
        $this->setMessageBody($this->objSmarty->fetch($this
            ->path_to_template_file));
    }
}
```

前面的代码简单但有效。现在尝试以下代码。它需要指向一个简单的 Smarty 模板，因此请先创建一个名为 `test.tpl` 的模板文件，如下所示：

Name: {$name}
Favorite Food: {$favefood}

接下来，输入以下 PHP 代码。确保它与 Smarty 模板位于同一目录中，或修改第一行以指向正确的路径。你会发现它与上次使用 `EmailCommunication` 时非常相似，但代码中的差异已为你突出显示：

```php
$objEmail = new TemplatedEmailCommunication("test.tpl");
$objEmail->setParameter("name", "Ed");
$objEmail->setParameter("favefood", "Steak");
$objEmail->parse();

$objEmailRecipient = new EmailRecipient("ed@example.com", "Ed Lecky-Thompson");
$objEmailSender = new EmailRecipient("info@example.com", "Test Sender");
$objEmail->setPrimaryRecipient($objEmailRecipient);
$objEmail->setSender($objEmailSender);
$objEmail->setSubject("Test Subject");

if ($objEmail->send()) {
    print "DONE! All went well! Mail sent successfully.";
} else {
    print "Sorry, didn't send mail successfully.";
};
```

这会在发送的电子邮件正文中生成以下输出：

名称: Ed
喜欢的食物: Steak

如你所见，`parse()` 方法为你构建了电子邮件正文。Smarty 根据你提供的两个参数解析了模板；但你没有使用传统的 `display()` 方法，而是使用 `fetch()` 将其输出捕获到字符串中。然后你将消息正文设置为该字符串，就可以发送电子邮件了。

请注意，通过扩展 `EmailCommunication` 类，你不仅在收件人管理和 SMTP 连接方面避免了重复造轮子，还将 `TemplatedEmailCommunication` 类控制在几行代码之内，使其更容易进行修改和调整。





当然，这里演示的仅仅是 Smarty 可能实现的功能的一小部分，但它确实显示了 Smarty 适配电子邮件是多么容易。

## 使用 MIME

你可能已经注意到，迄今为止本章几乎专门讨论的是简单的纯文本电子邮件。这些更容易处理，但不可避免地，会出现发送 HTML 电子邮件，甚至可能是模板化 HTML 电子邮件的情况。附件呢？你如何处理它们？MIME 是答案，而且这是一个庞大的话题。

幸运的是，PEAR 在很大程度上已经涵盖了这一点。有关更多详细信息，请参阅 http://pear.php.net/package/Mail_Mime。建议的方法是扩展 EmailCommunication 以形成 RichEmailCommunication，它具有 setHTMLContent、setPlainTextContent、addAttachment 等附加方法。

本次讨论不会深入细节；但如果你掌握了本章内容，可能可以毫不费力地将 MIME 功能集成到你已经构建的类中。从 http://pear.php.net/package/Mail_Mime 下载并安装 PEAR 包，并彻底阅读文档。构建相关的新 RichEmailCommunication 类应该足够简单。

你可以在 Usenet comp.mail.mime FAQ 中了解更多关于 MIME 的信息，其最新版本可在新闻组中找到，并在 Web 上复制，例如 www.uni-giessen.de/faq/archiv/mail.mime-faq.part1-9/。

## 其他通信子类

本章坚定地专注于电子邮件，仅仅是因为它是 Web 上与用户通信的最常见形式。它是免费的，而且每个人都知道基础知识。

但是，Communication 类的整个重点在于它可以扩展为几乎任何东西——传真、短信、语音呼叫。本节描述了实现此类设施的几种方法。

## 短信文本传输

在过去一年左右，出现了一批网关提供商，他们会收取少量费用代表你发送消息。他们不使用物理蜂窝电话发送消息，而是使用直接链接到蜂窝网络，从而节省时间和金钱。

接口通常通过 SOAP（在第 10 章中介绍）或甚至只是简单的 HTTP POST。如果你好奇，可以在 Web 上搜索“SMS 网关”。

更即时的替代方案是通过串行电缆连接到你的蜂窝电话（如果你的手机支持）。同样，Web 上有更多关于以这种方式与手机通信的 API 的详细信息。诀窍是将其视为调制解调器；Hayes 兼容的 AT 命令集非常适合此类通信。你可以在 www.cellular.co.za/sms_at_commands.htm 上找到更多信息。

## 传真

与其物理渲染传真页并通过调制解调器发送，不如使用当今存在的众多电子邮件到传真网关之一，这是一个更简单的解决方案。其中大多数会接受作为附件发送到特殊电子邮件地址的 `TIFF` 或类似文件，并代表你发送传真。通过使用 PHP 的内置图形函数，你应该能够即时生成 `TIFF`，将其电子邮件发送到这样的接收地址，并创建即时的、动态生成的传真。

此类服务的一个示例是 eFax。有关更多信息，请参见 `www.efax.com`。

## 其他注意事项

在结束本章之前，还有几件事值得考虑。如果你正在构建使用户通信的企业级应用程序，这样的小细节可以决定用户体验是非常流畅（会让用户想要再次使用）还是草率不成熟。

## 阻塞活动

*阻塞* 指的是过程式代码中必须在其他任何代码完成之前完成的活动。如果该活动需要一段时间，那么不幸的是，其他一切都必须等待。

发送电子邮件正是如此的活动。发送电子邮件（如本章前面所示）是一项密集型活动：连接到 SMTP 服务器，等待身份验证，传递消息正文，并等待服务器接受。取决于服务器的繁忙程度，这可能需要从几毫秒的分数到——等等——可能四五秒不等。

那四五秒钟被添加到 HTTP 请求中——这是毫无疑问的。如果用户的 HTTP 请求生成了一封电子邮件，那么在电子邮件发送和请求完成之前，该用户都会感受到这种延迟。最好，用户可能会觉得出了问题；最坏的情况是，用户会点击停止按钮并放弃。

还要记住，SMTP 服务器有时会出现故障或不可用。如果你依赖该服务器可用来实现某些重要功能（例如忘记密码电子邮件），那么 SMTP 服务器宕机基本上也会使该功能不可用。

这不仅仅是电子邮件。如果你使用 GSM 调制解调器发送短信，如果有人拔掉那个调制解调器的电源线怎么办？如果你发送传真，如果你的传真服务宕机了怎么办？列表还在继续。

## 维护任务队列

解决这个难题实际上出奇地简单。回到某个你知道*不会*阻塞——或者至少不应该阻塞的东西。它是你的数据库，可能构成了你应用程序的支柱。

创建一个简单的表格来存储需要发送的电子邮件。它可能看起来像这样：

```
CREATE TABLE "scheduled_email" (
    "id" SERIAL PRIMARY KEY NOT NULL,
    "subject_line" character varying(256) NOT NULL,
    "sender_name" character varying(256) NOT NULL,
    "sender_address" character varying(256) NOT NULL,
    "recipient_name" character varying(256) NOT NULL,
    "recipient_address" character varying(256) NOT NULL,
    "reply_to_name" character varying(256) NOT NULL,
    "reply_to_address" character varying(256) NOT NULL,
    "html_content" text,
    "text_content" text,
    "status" character varying(1) NOT NULL
);
```

希望这些列大多不言自明。也许唯一需要解释的是名为 status 的列。

想法很简单。当你想发送电子邮件时，不要直接连接到 SMTP 服务器。相反，在表 scheduled_email 中创建一个条目，将状态标志设置为 N——表示“尚未处理”。

就这些——你的代码所做的全部。所需要的只是一个简单的 INSERT 语句到你的数据库，这应该只需要几分之一秒。阻塞问题消失了。

当然，你仍然需要实际发送电子邮件。这时就用到了你的处理器脚本。编写一段简单的 PHP 代码，查找 scheduled_email 表中状态为 N 的条目。然后，对于每个条目，通过 SMTP 发送电子邮件。对于每封已处理的电子邮件，将其状态设置为 C，表示“已完成”。这样，你的脚本下次运行时就不会意外重复发送。

该脚本必须放在你系统的计划任务系统中——Mac OS X 和 UNIX 上的 cron，Windows 上的计划任务。设置每分钟运行一次，处理任何“尚未处理”的条目。

但是，要小心确保同一时间只有一个副本的脚本在运行。否则，你可能会发现两个脚本实例试图为你发送同一封电子邮件。你也可以减轻这种情况。考虑在开始发送之前将电子邮件的状态设置为 S（表示“已开始”）。这样，即使两个副本的脚本同时开始运行，它们也没有机会同时尝试发送同一封电子邮件。

你在这里所做的净效果是，将一项不可预测的任务（发送电子邮件的行为）替换为可预测的任务（向数据库插入记录）。不可预测的任务被保持在离线状态，远离用户的 Web 浏览器。

## 可投递性

过去几年最热门的话题之一是垃圾邮件和废邮件。最近的估计表明，每天通过互联网发送的数亿封电子邮件中，多达 75% 是垃圾邮件。这不仅给最终用户带来巨大困扰，还浪费带宽和 CPU 时钟周期，而这两者都需要花费钱。





因此，人们努力尽可能限制可疑垃圾邮件的投递。最突出的就是垃圾邮件过滤器——不仅包括大多数现代电子邮件客户端内置的过滤器，还包括安装在主要ISP电子邮件基础设施边缘的过滤器，以及主要基于Web的电子邮件提供商（如Hotmail、Gmail和Yahoo!）的过滤器。

这些垃圾邮件系统在判定他们认为是垃圾邮件的内容时变得越来越激进。当然，它们使用传统的贝叶斯算法来检查主题行和邮件正文中是否存在“垃圾邮件”相关词汇——“refinance”、“pills”、“meds”等等。这些属性的存在会增加一个“分数”——如果分数超过某个阈值，则该邮件会被标记为垃圾邮件。越来越多的ISP还在使用精巧的检查，一旦通过，就能迅速降低该分数。因此，合法发件人可以更可靠地让邮件送达，即使其特征本可能被视为“垃圾邮件”。

对于企业Web应用程序开发者来说，这当然很重要。例如，如果你在定期发送电子邮件通讯，你最不希望的就是你的邮件被误判为垃圾邮件而被拦截。这种情况比你想象的更容易发生。例如，如果你是一家大型零售银行，向客户发送关于优秀抵押贷款优惠的电子邮件，也很容易进入垃圾邮件箱。

考虑到这一点，你可以使用哪些技术来告诉那些垃圾邮件过滤器你是合法发件人——并且无论发生什么（在合理范围内），他们都应该让你通过？

### SPF 记录

发件人策略框架（SPF）记录允许向发送电子邮件的域名的DNS记录中注入额外信息，以指定哪些物理服务器可以代表该域名发送电子邮件。

这意味着收件邮件服务器可以快速检查发件人域名是否可能是合法的，或者是否被伪造。如果是合法的，相应的SPF记录会将该域名与发送服务器“绑定”。这种匹配通常不是垃圾邮件的特征。发件人域名通常完全是虚假的，或者至少与发送邮件服务器无关——尤其是众所周知，“开放中继”源源不断地提供了90%的垃圾邮件。

更多信息请参见 http://en.wikipedia.org/wiki/Sender_Policy_Framework。

### 发件人ID

发件人ID（Sender ID）像SPF记录一样注入到发送域的DNS记录中。语法有细微差别，但大致提供相同的目的。它告诉收件人有关所涉域名的信息，以及哪些服务器可能被用于合法地通过该域发送电子邮件。它在精确语法和实现上与SPF记录不同。就所有实际目的而言，它是一款竞争产品。

大多数域名选择同时实现这两种格式以确保最佳兼容性。有关更多信息，请参见 http://en.wikipedia.org/wiki/Sender_ID。

### 域名密钥和DKIM

域名密钥识别邮件（DKIM）为电子邮件发送系统提供了一种在头部级别对电子邮件进行数字签名的机制。该签名可以针对该域的官方DNS记录进行双重检查，以评估其是否真实。这种机制并不能保证电子邮件不是垃圾邮件，但确实使其可以非常轻松地被追溯。为此，如果ISP收到针对某个域名的过多投诉，则可以封锁该域名及其域名密钥。因此，在收到电子邮件时，ISP可以验证发件域的真实性，并查询其内部记录以确定其是否此前曾被举报为垃圾邮件发件人。如果是的话，该消息可能会被拒绝。

有关更多信息，请参见 http://en.wikipedia.org/wiki/DomainKeys_Identified_Mail。

### 广播电子邮件提供商

如果所有这些听起来很麻烦，你说得对——确实如此。当今从你自己的Web或应用程序服务器使用标准SMTP是一条艰难的道路。只需要一个过于热心的用户点击“这是垃圾邮件”按钮，你的声誉就会荡然无存。除非你准备好坐在那里监控垃圾邮件反馈循环——对ISP发来的每一个案例进行争议——否则还有更好的方法。

在过去几年中，一种新型的广播电子邮件提供商应运而生。这些公司只有一个目的，且只有一个目的：代表客户发送（合法的）批量电子邮件，速度尽可能快，成本尽可能低，投递成功率尽可能高。

这些广播电子邮件是作为营销活动的一部分发送的——例如，来自你网站的每周通讯——但你完全没有理由不能使用同一家提供商来发送你的触发式电子邮件。这样，你的触发式电子邮件（例如订单确认等等）将与你的广播电子邮件来自同一个域名，此前描述的所有投递技术都已建立并就位。

广播电子邮件提供商还会为你处理监控工作。他们将处理任何垃圾邮件投诉，并监控任何经常被标记为垃圾邮件的特定邮件副本。你还可以利用一些非常精细的关于打开率、点击率等等的报告。

大多数广播电子邮件提供商提供API，以便你能从自己的应用程序发送此类触发式电子邮件。一个很好的例子是eCircle，（www.ecircle.com/en/home.html），它提供同步和异步API，甚至提供PHP代码示例。你可以在 http://developer.ecircle-ag.com/ 上获取更多详细信息。电子邮件起价为每千封几美元，因此只要你每月不处理数百万封电子邮件，就会发现这笔额外投资是值得的。

### 摘要

在本章中，你学习了如何与用户沟通，不仅是通过Web浏览器，更是通过现代最重要的媒介：电子邮件。

你很早就通过研究用户沟通如何在优雅的类层次结构中表示，而摆脱了PHP的mail()函数。你还作为该层次结构的一部分创建了EmailRecipient和EmailCommunication类，它们足够强大和稳定，可用于日常使用。

你学习了Smarty如何在帮助你生成模板驱动的电子邮件方面发挥重要作用，以及关于所讨论类框架的一些更高级的可能性。

在第12章中，你将接触到构建企业PHP应用程序的两个最重要的概念：会话和身份验证。

# 12 会话和身份验证

尽管近年来PHP取得了进步，使其成为今天功能齐全的面向对象（OO）Web应用程序开发平台，但它仍然依赖（与其他同类语言一样）基础知识。也就是说，它依赖于HTTP协议，以及Web上任何交互性的最基本构建块：HTTP提供的通用网关接口（CGI）功能。

当人们谈论HTTP时，他们经常将其描述为*无状态*——这意味着从一个用户请求到下一个请求，不会保留任何“内存”。请求是通过`GET`或`POST`发出的，数据被返回，请求完成——就Web服务器而言，请求被遗忘。

如果你试图构建模拟等效桌面应用程序功能的复杂Web应用程序，这种特性就没多大用处。你必须能够跟踪用户的先前操作（而不仅仅是他们此刻正在做什么），才能产生有意义的输出。

幸运的是，PHP提供了一种绕过此问题的方法：*会话*。这种技术使你能够在用户的一个请求到下一个请求之间维护某些有状态信息。这非常自然地引出了会话处理最常见和最有用的应用之一——身份验证和用户状态持久性。

本章前半部分讨论了PHP的内置会话处理功能。你会发现，虽然（表面上）可用的功能可能看起来很基本，但它可以扩展和调整，以提供极大的灵活性（包括与第三方数据库集成）。你还将学习会话安全的方方面面，以便你可以设计出能够挡住黑客的会话架构。





在本章的后半部分，你将学习如何将会话管理知识应用于开发工具包中的一个核心组件：一个可复用、可扩展且高度安全的会话管理和身份验证类，它可以部署在几乎所有企业级 PHP 应用中。

## 会话简介

在深入了解 PHP 中会话的工作原理及其能为应用带来的好处之前，让我们先来看看会话的一般概念。它们是什么，如何工作，又为什么如此重要？

### HTTP 的工作原理

请思考 Web 请求实际是如何工作的。当用户的 Web 浏览器发出请求时，它会向 Web 服务器呈现以下核心信息（以及其他一些细节）：

- 请求方法（GET 或 POST 之一）及所使用的协议版本（1.0 或 1.1）
- 所需的实际文档（例如，/index.php）
- 请求文档的服务器主机名（这一点很重要，因为许多网站都托管在拥有单一 IP 地址的单一服务器上）
- 以 URL 编码格式提交的 GET 或 POST 请求参数（例如，foo=bar、username=fred、password=letmein）
- 浏览器类型（即用户代理，本质上包括变体、平台和版本）
- 客户端机器上存储的、之前由客户端当前正在请求的服务器颁发的所有 Cookie

如果想实际看到这一过程，可以 telnet 到你选择的 Web 服务器的 80 端口，然后发出类似下面这样的请求：

```
GET /pub/WWW/TheProject.html HTTP/1.1
User-Agent: CERN-LineMode/2.15 libwww/2.17b3
Host: www.w3.org
```

最简单的方法是将这段代码粘贴到你选择的文本编辑器中，随心所欲地修改它，然后一次性在控制台粘贴。作为对你请求的响应，Web 服务器会返回一个合适的 Web 页面，你应该能在 Telnet 会话中看到它。

如果你觉得很难看出这个协议如何能不是无状态的，那你并不迟钝——毕竟，在给定请求发生时，服务器完全不知道之前的请求中发生了什么。

这种方法会带来问题，因为虽然 Web 服务器将用户的请求视为无状态的，但用户并非如此。用户非常清楚在上次请求页面时做了什么，并且（相当合理地）期望 Web 服务器也记得。一个典型的例子是，当访问某个特定页面资源需要用户名和密码时。用户期望只输入一次这些信息，而不需要再次输入。如果用户需要请求网站上另一个受限页面，应用程序应该记住这些信息，而不再询问。

毕竟，几十年来计算机的工作方式通常就是这样。在 Web 应用程序中镜像这种功能，对于用户的集体理智至关重要。

在 Web 的早期，这种功能有时是通过服务器检查连接用户的远程 IP 地址与数据库进行比对来实现的。当用户首次登录时，会记录 IP 地址，并在一定时间范围内，假设来自该 IP 的后续请求都来自同一用户。

在没有防火墙、网络地址转换（NAT）、代理服务器或其他此类烦人干扰的互联网时代，这倒也没什么。当然，今天的互联网已经大不相同了。一些消费级 ISP 实际上会在用户向你的网站发出的每个请求中呈现完全不同的外部代理服务器地址——这是它们自身代理负载均衡技术的副作用。

解决该问题的另一个常见方法是使用 HTTP 身份验证，它不依赖于请求之间一致的 IP 地址。如果你曾经访问过某个网站，并且看到过类似图 12-1 所示的对话框，那么你就遇到过 HTTP 身份验证。

![](img/a1b732997d9cb194dceec0570dc79710_285_0.png)

图 12-1：HTTP 身份验证对话框

HTTP 身份验证从 Web 的早期就已提供，它允许将 Web 服务器上的某些文件和目录限制为仅特定用户组可用。传统上，这个用户列表是一个简单的纯文本文件，包含用户名和（几乎未加密的）密码对；但最近的进步使得 Apache 能够直接查询 MySQL 数据库以获取这些信息。

这种方法效果不错，在为 Web 服务器上的给定目录颁发用户名和密码后，对该目录或其子目录中的任何文件的后续请求（无论是什么文件）都会自动连同该用户名和密码一起提交给 Web 服务器。

然而，在构建 PHP 应用程序时，这种方法用处不大。人们很少希望保护特定的脚本，甚至是目录。更有可能的需求是，以一种在 PHP 中被识别和理解，但不一定在 Apache 中被识别和理解的方式来限制功能。尽管从 PHP 内部复制模拟此功能所需的 HTTP 头部是可行的，但出于多种原因，这样做很少被推荐：

- 你几乎无法控制这个框的外观，所以这并不是一种用户友好的方法。
- 你无法询问任何其他信息（例如，提出一个安全问题，如“你母亲的娘家姓是什么？”）
- 你无法在请求上存储除用户登录身份之外的任何信息。

列表远不止于此。幸运的是，还有一个第三种、且远为理想的解决方案：使用会话。

## 会话的定义

严格来说，会话被定义为单个用户从单个计算机在单个 Web 应用程序上，在指定时间间隔内发出的一系列连续 HTTP 请求。

会话背后的一般方法是，用户发出的第一个请求会生成一个新会话，如果尚未存在会话的话。后续请求被视为该会话的一部分，除非它们发生在某个任意的时间段之外（会话超时周期）。

因此，会话和请求之间存在可验证的关系。多个请求可以产生一个会话，因此一个会话可以属于多个请求。从数据库术语来看，这是一种一对多关系。你很快就会看到，可以将其相当整洁地封装在类层次结构中。

会话通常用于确定应用程序当前连接的用户（如果有）。用户首次成功登录后，应用程序的数据库应将用户的用户 ID 与该会话关联，这样任何使用该会话的后续请求都被理解为由该用户而非其他用户发出。

会话的核心是会话标识符。它会唯一标识会话，该会话可能与数百个其他用户会话并发存在。当首先生成会话 ID 并发送到客户端时，会话标识符既要唯一，又要足够晦涩，以防潜在的敌对第三方轻易“捏造”出另一个有效的会话 ID。例如，虽然颁发 1、2、3、4 等会话编号肯定满足唯一性要求，但未能满足安全性要求，因为分配到会话编号 3 的用户可以简单地突然声称自己是会话编号 4，并因此可能访问另一个用户的账户。

会话标识符通常是由数字和字母组成的 32 字符字符串。这就是 PHP 的内置会话处理（本章后面将讨论）生成会话标识符的方式。因此，一个用户偶然撞上另一个用户的有效会话 ID 的可能性不大，除非通过暴力破解——而本章后面你还将学习几种简单的方法来防止这种情况发生。





## 会话的持续化

在用户的第一个请求被发出，并为该请求生成了会话标识符后，你面临着确保该会话标识符在随后的每个请求中都被延续的挑战。

实现此目的有两种方法：URL 重写和 Cookie。一个不错的起点是先了解这两者的原理，暂时不深入探讨 PHP 自身的会话处理机制。

## URL 重写

这是会话持续化最简单的形式。它涉及确保每一个链接、表单目标和 JavaScript 重定向都被处理，以便按情况将会话标识符作为 GET 或 POST 参数包含在内。

请参考以下示例。为了论证起见，假设 PHP 决定使用以下会话标识符：

```
abcde1234567890abcde1234567890ab
```

假设你希望 Web 浏览器在每个后续请求中都发出此会话标识符。在你的 HTML 中，无论何处都有锚链接，你都必须安排 PHP 对其进行处理，使其

```
<A href="mybasket.php">Go to my basket</A>
```

变成

```
<A href="mybasket.php?session_id=abcde1234567890abcde1234567890ab">Go to my basket</A>
```

显然，你不会将此硬编码到 HTML 中。相反，你会想出一些巧妙的方法，使用正则表达式之类的方式，在生成 HTML 时动态地将此类会话标识符注入其中。

同样有必要让 PHP 对表单目标进行处理，使其

```
<FORM method="POST" action="mybasket.php">
```

变成

```
<FORM method="POST" action="mybasket.php">
<INPUT type="HIDDEN" name="session_id" value="abcde1234567890abcde1234567890ab">
```

你的 PHP 甚至可能需要更新你可能拥有的任何 JavaScript，以使

```
window.location.replace("index.php")
```

变成

```
window.location.replace("index.php?session_id=abcde1234567890abcde1234567890ab")
```

的确，可能会有漏掉 URL 的罕见情况，从而导致会话丢失。URL 重写最令人不快的地方在于，如果在某个请求中丢失了会话，它将永远丢失，因此彻底性至关重要；但这并非唯一的陷阱。

以这种方式添加书签怎么办？如果你添加当前页面的书签，也会记录会话标识符，而下次登录时它将不再有效。因此，添加书签时必须手动删除会话标识符。

最大且最普遍的陷阱在于，当人们尝试将链接复制并粘贴给朋友和同事时。普通用户 Joe User 根本不会想到，在将你网站上某个页面的链接通过电子邮件或即时消息发送给朋友，或粘贴到他的 Facebook 页面之前，先去除会话标识符。因此，当他的朋友点击链接时，取决于你实施的安全级别，将会发生以下两种情况之一：要么朋友将完全访问用户的原始登录，要么系统会因潜在的安全漏洞而出错，因为用户声称自己是有效会话的合法所有者，但未提供与该会话关联的其他凭据。

还有一个更好的方法，但它也并非毫无争议（这些争议大多是毫无根据的）——使用 Cookie。

## Cookie

虽然从理论上讲，URL 重写是会话持续化最简单的形式，但使用 Cookie 在所需代码量方面甚至更简单。

Cookie 是 Web 浏览器随页面 HTML 输出发送的小片段信息。Web 浏览器被指示记录该信息，然后在向该 Web 服务器发出的每个后续请求中主动提供它。

与变量类似，Cookie 具有名称和值。有些还有有效期（持续时间）和作用域（哪个服务器或哪些服务器应接收它）。在向 Web 服务器发出的每个请求中，用户的 Web 浏览器会提供该 Web 服务器域作用域内、尚未过期的任何 Cookie 的名称和值。过期的 Cookie 会被 Web 浏览器自动删除，但如果有必要，活跃的 Cookie 也可以被 Web 服务器立即删除。

实现很简单。与之前的示例一样，假设会话标识符如下：

```
abcde1234567890abcde1234567890ab
```

在会话中，用户 Web 浏览器发出的第一个请求时，必须将此会话标识符推送到用户的 Web 浏览器，以便浏览器知道在后续请求中提供它。因此，会向用户的 Web 浏览器发送一个 Cookie，指示其将值 abcde1234567890abcde1234567890ab 保存到适当命名的标识符中。

在向 Web 服务器发出的每个后续请求中，PHP 会查找提供有效会话标识符的 Cookie，该有效性仍需根据某些外部规则集和/或有效会话数据库进行检查。如果 Web 浏览器发送的 Cookie 中包含有效会话标识符，PHP 可以假定这是正确的会话标识符，并照常继续执行脚本。如果未提供任何会话标识符，或提供的会话标识符被视为无效，则会生成一个新的会话标识符，并像上一步一样作为 Cookie 发送。

此循环在用户会话的剩余时间里，从一个请求延续到下一个请求。

为 Cookie 命名时，应坚持使用易于识别的名称，例如 `session_id`。作用域应限制在你自己的 Web 服务器上（或者，在紧急情况下，限制在域上），有效期应等于你认为用户在网站上需要的最长停留时间。例如，如果你认为典型用户使用网站的时间不会超过半小时，那么设置 30 分钟的有效期并不是个坏主意。

历史上，关于 Cookie 使用的隐私问题一直存在争议。这部分争议在很大程度上源于反对者的无知、一些极其糟糕的网站设计实例（通常由本应更懂行的代理机构和品牌所为），以及或许还有某些不道德的网站运营商。

尽管存在争议，但任何用户都绝无理由担心通过 Cookie 发出简单的会话标识符。但是，请务必确保将 Cookie 的作用域限制在你的服务器上，仅限你的服务器，以免它无意中被发送到可能试图将其用于跟踪目的的任何其他网站。此外，在你的网站上发布一份清晰简洁的隐私政策也是合理的，向用户说明你所使用的 Cookie 的目的，以及你为保护用户隐私和安全所采取的措施。

此外，请记住，Cookie 应仅用于存储会话标识符，绝不应存储与该会话关联的任何数据。此类数据存储在你的服务器上，得到妥善保护，避免被他人窥视。会话标识符在你的应用程序上下文之外没有意义，因此风险很小。这有点像丢了你家的钥匙。如果你愚蠢到在钥匙上贴了一个写着地址的标签，那你最好尽快换掉锁。如果你没有这样做，那就没什么好担心的。

尽管如此，正如下一节所解释的，确实存在一些潜在的陷阱。

## 会话安全

会话标识符本身真的安全吗？当然，将会话标识符作为识别网站上登录用户的唯一手段，存在一些风险，但幸运的是，你可以采取一些对策来帮助尽量降低这些风险。

### 猜测有效会话

如果你的网站上的恶意访问者碰巧伪造了一个有效的会话标识符，他或她可以劫持另一位访问者的会话。毕竟，如果用户 A 一直在使用会话标识符 X 发出请求，然后恶意用户 B 也使用会话标识符 X 发出请求，你的网站会认为用户 B 是用户 A，并且用户 B 将能够访问用户 A 能访问的所有内容，可能会暴露敏感信息。

要实现这种情景，潜在黑客需要猜出一个有效的会话标识符。在现实世界中，这样做的可能性有多大？

考虑你的 32 字符十六进制字符串。它可以以多种方式生成，但假设它在很大程度上是随机的。有 32 个字节，每个字节有 16 个可能的字符（a 到 f，以及 0 到 9），你的会话标识符有 16^32 个可能的组合。这是一个大数字——太



## 第二部分：学习高级开发技术

big to print here. It would take an awfully long time for a potential hacker to cycle through all possible session identifiers — 00000000000000000000000000000000, 00000000000000000000000000000001, 00000000000000000000000000000002, and so on, all the way up to ffffffffffffffffffffffffffffffff. Even if you could manage to test 100 per second by using multiple computers, it would take you 107,902,830,708,060,141,889,705,291,549 years. The Arizona Cardinals might have won the Super Bowl by then.

然而，如果标识符不仅仅是随机的十六进制数字，而是一个10位数字的MD5序列化呢？如果黑客确实知道这个事实，只需遍历10,000,000,000个组合即可，因为任何给定数字的MD5哈希值都是一个固定答案。编写一个脚本（也许甚至用PHP）在循环中尝试每个数字的MD5序列化，直到找到一个实际可用的，这是一件非常简单的事情。

Consider what might happen if the user requested an “update my details” page (mydetails.php). This page behaves in one of two ways, depending on whether a valid session was issued with the request:

- If a valid session is issued and the session is known to be logged in, then the page displays the user’s details, and allows the user to reset his or her password (among other things).
- If a valid session is not issued, then the page issues a 302 redirect to a login page (with a view that, once the correct username and password is given, a session is issued, and the user permitted to update his or her details as originally planned).

The mischievous script would have to iterate through these 10 billion combinations while making an HTTP request to mydetails.php with each one. If it gets a 302 redirect, it ignores it and moves on. If it gets the contents of the “my details” page, it resets the user’s password to 12345 by submitting the form on the page, making a note of the username, and moving on to the next session.

Leave this running for a few weeks, and it can absolutely be guaranteed that the script would have chanced upon a few valid sessions during its run. It may even have alerted the hacker via e-mail or an SMS text message when it struck a user account whose password it managed to reset. Keep in mind that with a fast connection (and the ability to run multiple instances of this script across multiple servers), a really determined hacker can get through many thousands of session identifiers every second.

If the hacker didn’t know how your session identifiers were formed, you would be fairly safe. Using a random number between two limits is a pretty bad idea, however, even if the hacker didn’t know what those limits were. It would be a simple matter to write a script to bombard your site with cookie-less requests, each of which would generate a new session. Soon enough, the laws of probability would dictate that your hacker would be furnished with a complete database of all feasible MD5-encoded session identifiers (all 10 billion, in the previous example). The hacker wouldn’t be able to reverse-engineer these to work out how they were formed, but doing so isn’t necessary. The hacker can simply feed the list of pre-hashed identifiers into his or her brute-force script — something known as a dictionary attack.

The only way to prevent such analysis is to ensure that sessions are single use. This means that the same session identifier will never be generated twice, or at least not within a considerable time span of its first generation. A good way to do this is to construct your session identifier based on a combination of a random number and the current timestamp. That way, any script constructed to fish for a complete database of session identifiers will be practically useless, because its database of valid session identifiers will (theoretically) grow to near-infinity.

### Obliterating Session Guessing

One simple way to completely obliterate session guessing is to send as a second cookie a supplemental key alongside the session identifier. This key would be completely random and generated at the time the session is formed. There would be no obvious link between the two. The key associated with that session would be stored in the database.

With each request, both the session identifier cookie and the session key cookie would be transmitted. Even if the session offered is valid, PHP would still check that the key transmitted matches the key originally issued and, if not, immediately cancel and invalidate the session. By canceling the session offered, any attempt to force further possible combinations of key against that session would be pointless, because the first wrong key issued would invalidate that session anyway. The only downside to this approach is that your legitimately logged-in user would be logged out as the session was cancelled, but it’s better to be inconvenienced and safe than hacked.

For true randomness when generating such keys, try to avoid using any kind of randomization whose seed is based on the system clock. Using truly random seeds such as processor temperature, server process identifiers, and network interface statistics produce a more satisfactory random number. Sequential digits of pi also work well, provided you never use the same digit again.

### Discovery of Valid Sessions

Discovery of valid sessions is a less prominent threat, but a more difficult one to protect against. Essentially, the risk is that a malicious third party can somehow gain access to the cookies on your legitimate user’s machine, and use them to gain access to the user’s session.

Unfortunately, this technique is not immune to the session key methodology discussed previously. If a hacker can gain access to the session cookie, the secondary key cookie is just as easily obtainable.

There are a few scenarios in which this could happen:

- A session cookie is “mis-issued” by your site so that its scope is broader than it needs to be. A malicious Web site within that overly broad scope then visited by the user would be made privy to that session cookie, too. The operators of that site could then use the cookie to hijack your session on the original site. The user does not even necessarily have to visit a malicious site. Literally millions of pieces of HTML spam e-mail every day are sent out containing images, the purpose of which is simply to cause its recipient to make a Web request, with the hope that session cookies from other poorly constructed sites will be offered accidentally.
- A physical intrusion to the machine could allow access to the cookies stored on it, from which data on valid sessions could be extracted.
- An intrusion to the machine that somehow modifies the `HOSTS` file could redirect traffic supposedly for your site’s hostname to a third-party site. This third-party site may even relay the genuine data from your Web server, such that the user is none the wiser. It would, crucially, collect the session identifier for later use.
- A poorly configured network could allow session identifiers to be sniffed in HTTP traffic by malicious systems administrators on-site.
- A malicious employee of an ISP that employs proxy servers (transparent or otherwise) could easily enable transmitted session identifiers to be logged.

The first of these scenarios is easy to overcome. When issuing cookies from your site, always get the scope correct — same hostname, same protocol (HTTP or HTTPS), and same directory. This most basic of errors is exploited with such frequency only because of the frequency with which it is made in the first place.

A physical intrusion is almost impossible to guard against. Any physical exploitation is attributable more to lackluster physical security of the location from which the site is being accessed than to anything else. Good session practice (see the following section) can help minimize the risk of this kind of occurrence.

Another major problem is the modification of the HOSTS file of a machine allowing name servers to be overridden transparently. It is remarkable there are not more e-mail worms in circulation that exploit this, but it is only a matter of time. The HOSTS file exists on almost every variant of Windows imaginable, and on Mac OS X and other UNIX platforms, too. Unless a tight local administration rights policy has been set up, users can modify it themselves. An e-mail worm distributed as an attachment (as are most modern worms) exploiting this vulnerability would work as follows:

- The user regularly visits www.myfictionalbank.com to use an online checking account management facility. This resolves to 10.123.123.123.
- An attachment (which might be .vbs, .src, .pif or any of the other numerous file extensions that still aren’t universally blocked by e-mail clients) has a viral payload that creates an entry in your HOSTS file pointing to a malicious foreign IP address, which is actually a server owned by the hacker. The IP address is 192.168.123.123, and is probably located somewhere in Eastern Europe.
- The next time the user logs into his or her online banking account, he or she enters www.myfictionalbank.com and appears to get the account login page as normal. In fact, the connection is being made to the malicious Web server. The malicious server, in turn, makes a real-time HTTP connection to the real bank’s Web server and mirrors every request made by the user, as if a marionette. It retransmits all the data returned by the real bank’s Web server. The only data not relayed back in this way is that generated when the user’s session details (immediately after login) are instantly recorded by the malicious relay server, which then seizes control of the session, denying the real user any further access. In just a few seconds, several thousands of dollars of the user’s hard-earned cash are on their way to Eastern Europe.

Of course, a scam like this wouldn’t last long. The bank would get wind of it pretty quickly and block off the malicious server’s IP address, or take other steps to make such a scam impossible; but it does serve to illustrate just how easily this kind of attack can be pulled off.

On-site exploitation is as big a threat as exploitation from Eastern Europe, particularly in big companies. Many corporate networks may be switched at their most central point, but when floor socket availability starts to get tight, most systems administrators slap in a hub. It’s cheap and quick, and the two PCs on that hub can immediately sniff each other’s traffic. If a savvy user is on the same hub as a colleague whose session the user wishes to seize, some simple traffic-sniffing software can retrieve those session identifiers.





最后，请记住，如今许多 ISP 都使用透明代理服务器。也就是说，所有 HTTP 流量都会被拦截并通过标准代理服务器中继，而无需用户明确知晓（且无需用户进行任何配置）。表面上，这是为了通过在 ISP 处缓存常请求的页面和图像来提升性能，使它们距离用户仅一跳之遥。更真实的原因是，在当前形势下，ISP 压力越来越大，需要记录客户在网上的非常详细的行为日志。这并非出于商业原因，而是为了在执法机构要求时移交这些信息。滥用此设施的潜力显而易见。如果 Cookie 被记录，对于无所事事的系统管理员来说，查获它们不过是小事一桩。

## 良好的会话实践

如你所见，物理获取会话标识符（以及会话密钥，如果可用的话）很难防范。防止此类利用的最有效屏障是物理的、政治的或经济的。它们当然与 PHP 无关。

尽管如此，如果你希望将这些理论漏洞被实际利用的风险降到最低，可以在代码中做几个巧妙的事情。

### 使用会话超时

首先，最重要的是使用会话超时。这些与会话过期时间*不同*。向用户颁发 Cookie 时，你几乎肯定会为其设置一个过期时间，但这无法防范用户离开计算机并忘记退出登录的情况。使用会话超时涉及记录每个请求针对会话的时间戳，然后针对该会话的每个后续请求，测量自上次请求以来的已用时间。如果超过五分钟或十分钟，*强烈*建议你撤销会话并要求用户重新登录。

这是一个非常有效的措施。之前描述的许多攻击都依赖于在用户结束会话后不久就能利用该会话。通过将机会窗口缩短到仅几分钟，你降低了这些攻击的有效性。

会话超时的实现与 Cookie 无关。相反，你实现用于处理会话的代码负责测量请求之间的时间间隔，并确定因超时何时撤销会话。本章后面你将了解到 `HTTPSession` 类，它可以实现此功能。

### 使用较短的过期时间

会话 Cookie 中设置较短的过期时间确实有道理。用户不介意偶尔被要求重新登录，因此设置大约一小时的过期时间是可以的。如果你这样做，请务必构建应用程序的其余部分，以尽量减少对用户的打断。例如，如果你正在构建 Webmail 应用程序，当用户正在发送电子邮件时，不要指示代码随意结束用户的会话。尽量富有同理心地设计。

如前所述，本章后面你将看到如何有效实现较短的 Cookie 过期时间。

### 检查用户代理一致性

你可以进行的一项简单检查是将用户的 Web 浏览器用户代理与会话一起记录。这是由 Web 浏览器发出的用于标识制造商、浏览器名称、版本和平台的字符串。它绝不是该计算机特有的，但由于正在使用的不同浏览器和浏览器版本非常多，任何两台计算机都很可能生成略有不同的用户代理字符串。

通过确保针对会话的后续请求携带与原始请求相同的用户代理，你为防止会话劫持提供了额外的防线。有趣的是，Internet Explorer 生成的用户代理字符串可以在 Windows 注册表中修改。系统管理员可以利用这一事实，使其网络上的工作站拥有特定于组织的用户代理字符串。这进一步增强了这种安全机制的实用性。

### 不要害怕要求用户重新登录

如果你即将允许用户下订单，或查看和更新其详细信息，不要害怕要求再次输入用户名和密码。这样，即使黑客成功接管会话，造成的损害也将在某种程度上受到限制。许多大型商业网站都采用这种做法，如果谨慎使用，用户不会对此请求感到太恼火。

### 监控异常流量

如果你胆子特别大，可以构建一些算法来监控针对特定会话的异常流量，以确定多次使用。如何定义“异常流量”存在争议，但例如，如果任何一秒钟内发出的请求超过一个，你可以发出警报，并因此取消会话。或者，你可以将站点的物理导航映射到可能的用户路径，并确保用户会话发出的请求遵循其中一条路径。

例如，在电子商务网站上，如果用户通过一个请求索引特定产品类别，那么他或她极不可能立即选择 *该类别之外* 产品的“查看产品”页面。要做到这一点，他或她必须是从书签或第三方链接访问的，或者手动输入了 URL。但是，如果你的算法不够可靠，误报率很容易开始让用户不满。

### 监控 IP 地址的异常差异

虽然根据 IP 地址的一致性来确定会话的有效性并不合法，但仍有可能通过监控其差异来检测一些可能的入侵尝试。负载均衡代理服务器可能会在每个请求时更改 IP 地址，但更改幅度如何？除了最后两个八位组外，其他部分更改的可能性极低。可以肯定的是，请求肯定会留在同一网段内（即从请求到请求，网段的所有者保持一致）。检查这一点的一个好方法是实时查询 RIPE、ARIN 等。

在你的应用程序中，你只需设计一种低开销的方式来检查网段所有者，如果可能的话，利用某种缓存技术。如果同一会话的请求似乎来自不同的所有者，那么发出警报并销毁会话是值得的。

### 避免在客户端存储会话变量

会话的一个明显好处是能够将相关变量的值与会话关联起来。例如，这些变量可能是购物篮的内容，或搜索表单的填充内容。

尽管如此，最好避免在客户端存储这些信息。一方面，这会让隐私活动人士非常不安。另一方面，这些变量的值可能会在你的代码控制之外被修改（无论是恶意的还是意外的）。

每个 HTTP 请求上传那么多数据可能效率相当低。请记住，大多数宽带连接是非对称的，即上传速度慢于下载速度。因此，如果你在客户端存储了 16KB 的会话变量，这会使每个请求增加一秒左右。这听起来可能不算多，但很快就会让用户抓狂，所以以这种方式使用 Cookie 不是好做法。

你只需要在客户端存储会话标识符（以及补充安全密钥，如果使用的话）。将其他所有内容存储在服务器端某个远离危险的地方，并将这些变量与相关的会话标识符关联起来。

### 考虑使用第二重安全因素

一些零售银行已开始为部分消费者网上银行业务采用双因素身份验证。第二个因素通常以智能卡读卡器以及邮寄给客户的卡片形式出现。

虽然大多数网上银行业务可以不使用它来完成（以限制不便），但某些关键活动（通常是向全新收款人转账）需要输入由卡片读卡器生成的一次性代码。这确保了银行的操作者持有卡片读卡器本身。在之前描述的许多情况下，这不太可能发生；因此，欺诈机会大大减少，且对最终用户仅带来最小不便。

本章这一部分的教训是，100% 的安全性永远遥不可及。然而，你总是可以采取一些措施来尽量减少自身风险。

## PHP 如何实现会话

PHP 使你能够在应用程序中实现高效的会话管理基础架构，但你必须亲自完成大部分困难的工作。

如本节所示，PHP 内置的会话处理并不真正适合企业级应用程序。幸运的是，它已被设计得足够可扩展，为你编写自己的更强大解决方案提供了良好的开端。





## 基本 PHP 会话

输入以下代码并将其保存为 firstpage.php：

```php
<?php
session_start();
$_SESSION['favorite_artist'] = 'Tori Amos';
?>
Currently, my favorite artist is Tori Amos. It may also interest you to know that my identifier for this browser session, as allocated by PHP, is
<?=session_id()?>.
<BR><BR>
<A href="secondpage.php">Go to the second page</A>
```

现在开始一段全新的代码。将此命名为 secondpage.php：

```php
<?php
session_start();
?>
Having checked, I can tell you that my favorite artist is still
<?=$_SESSION['favorite_artist']?>. At the moment, my identifier for this browser session, as allocated by PHP, is<?=session_id()?>.
<BR><BR>
<A href="firstpage.php">Go back to the first page</A>
```

运行其中的第一个，你应该会得到一些可预测的输出。假设你最喜欢的艺术家是 Tori Amos，PHP 已为你分配了一个会话标识符，如以下输出所示：

Currently, my favorite artist is Tori Amos. It may also interest you to know that my identifier for this browser session, as allocated by PHP, is balq167mlgor56oqjlc5eldca2. Go to the second page

你可以看到会话标识符长度为 26 个字符。PHP 实际上使用了完整的字母表，以及 0–9。这使得可能的会话标识符数量增加到 36^26。如果你单击链接转到第二页，你应该会看到类似这样的内容：

Having checked, I can tell you that my favorite artist is still Tori Amos. At the moment, my identifier for this browser session, as allocated by PHP is balq167mlgor56oqjlc5eldca2. Go back to the first page

此处需注意两点重要事项。会话标识符是相同的，第二个脚本似乎记住了你的音乐偏好。

这种结果以直接的方式获得。首先，使用 session_start() 告诉 PHP 启用会话，且要在脚本的第一个 HTML 字符之前很久使用。使用 session_start() 很重要，因为发送到 Web 浏览器的会话数据必须放在 HTTP 标头中，而一旦使用任何 HTML（甚至空白字符），就会阻止这种情况发生。

其次，通过向 `$_SESSION` 全局关联数组（或 *哈希*）添加内容来注册会话变量。这可以放在脚本中的任何位置，因为它不会向 Web 浏览器发送任何内容。它只是在服务器端做个记录，你很快就会看到。

在第二页上，像在第一页上一样调用 `session_start()` 来启用会话管理，但现在你可以像在第一页上写入一样从 `$_SESSION` 读取。不出所料，Tori Amos 的值已成功从一个页面保留到下一个页面。这个值已与会话标识符不可分割地关联，这就是服务器记住它的原因。

PHP 如何从第一页记住会话标识符到第二页？查看你服务器上的 `/tmp`。使用 `ls` 对所有以 `sess_`（单词 sess 后跟下划线）开头的文件进行目录列表：

```
$ cd /tmp
$ ls -la sess_*
```

希望你会看到类似这样的目录列表：

```
-rw-r--r-- 1 nobody users 33 2008-08-17 15:23 sess_balq167m1g0r56oqjlc5e1dca2
```

注意一个名为 `sess_` 后跟上一示例中分配给你的会话 ID 的文件。使用你选择的编辑器打开它：

```
pico -w sess_balq167m1g0r56oqjlc5e1dca2
```

你应该会看到类似这样的内容：

```
favorite_artist|s:9:"Tori Amos";
```

对于 Windows 用户，PHP 会话最可能存储在 `C:\\TEMP` 中，但这取决于你如何配置 PHP 和 Apache（或你选择的 Web 服务器）。如果找不到任何文件，可以使用 Windows 内置的搜索功能查找以 `sess_`（会话，后跟下划线）开头的文件。不要忘记包含隐藏文件和文件夹。找到会话后，可以使用记事本或类似的文本编辑器打开它。

会话文件的输出看起来非常直接。希望你注意到你创建的会话变量及其以简单“键-值”对形式的纯文本内容。

实际上，显示的内容可能会让你感到眼熟。这是 PHP 函数 `serialize()` 的输出，即 PHP 数据结构的字符串表示。

无论你在 `$_SESSION` 变量中创建的数据结构多么复杂或大，PHP 都会默认将其内容存储在此文件中。存储此类文件的位置以及存储时间，都是可以在 `php.ini` 中更改的设置。

原生 PHP 会话基本就这么多。现在让我们来看看它们的一些局限性，以了解为什么它们不能用于企业环境。

### 基本 PHP 会话的局限性

以这种方式实现会话存在几个关键问题，其中大部分都与 PHP 在磁盘上存储会话数据的方式有关。

如果你有多台 Web 服务器通过负载均衡设备以轮询方式在它们之间分配流量来处理请求，该怎么办？你将不得不实现某种共享的 `/tmp`（使用 NFS），这将慢得令人绝望。

其次，如果你在共享 Web 服务器上运行（例如，与托管公司一起），`/tmp` 的目录列表对所有人都是可读的，即使其文件内容不可读。鉴于 PHP 将会话标识符用作文件名的一部分，该 Web 服务器上的恶意用户可以非常轻松地获取创建的所有会话标识符的完整列表，以及它们的创建时间。这将再次为轻松的会话劫持敞开大门，如前所述。

第三，这种会话处理实现并不十分安全。前面讨论的任何额外安全措施都未被采用，在这种状态下也很难采用它们。因此，就使用会话的生产 Web 站点的安全环境而言，原生状态下的 PHP 会话处理确实不是一个可行的选择。

第四个限制是速度。通过在磁盘上存储会话数据，PHP 几乎需要在每个请求中读写磁盘。这会让磁盘一直很忙（实际上是不必要地忙），并减慢所有相关方的请求速度。因此，单台服务器能够维持的流量水平会降低，可能会增加你对更高硬件预算的风险。

最后，鉴于你将应用程序的其余数据存储在数据库中，你必然会有时需要构建同时查询会话变量和数据库表的查询。由于会话数据完全在数据库之外，你必须先使用 PHP 提取该数据，然后将其注入 SQL 语句。与执行单个 SQL 查询来提取所需数据相比，这种方法与严重的性能影响相关。例如，在生产服务器上，这可能会变得相当严重。解决此问题的方法是将 PHP 会话管理与数据库集成。

### 创建身份验证类

在本章的最后部分，你将学习如何将 PHP 的会话处理技术调整为与 PostgreSQL 数据库通信，该数据库将用于存储迄今存储在磁盘上的会话数据。同时，你将组合一个类来处理用户身份验证，你应该能够在任何项目中重用它。

### 将 PHP 会话管理连接到数据库

让 PHP 使用数据库而不是服务器的磁盘来存储其数据，比你想象的要容易得多。以下示例使用 PostgreSQL，但这种方法可以轻松适应 MySQL、XML 扁平文件或任何你偏好的方式。

这一切的关键只有一个 PHP 函数：session_set_save_handler。如果你查看该函数的 PHP 手册参考条目，可以非常清楚地看到其语法：

```
bool session_set_save_handler ( string open, string close, string read, string write, string destroy, string gc)
```

其理念很简单。在任何使用会话的页面上使用 session_start() 之前调用此函数。该函数指示 PHP 在发生某些会话行为时调用哪些自定义函数（例如，启动会话、结束会话、读取、写入或销毁会话时）。关于传递给这些方法的参数以及它们必须返回的值，有一些要求。这些在 PHP 手册的 session_set_save_handler 页面上有详细说明，但以下部分介绍了基础知识。

#### open() 函数

每当调用 session_start() 时，就会调用 open() 函数。PHP 传递两个值：如果会话要保存在磁盘上，它认为会话应存储的路径（在本次讨论中可以忽略）以及它用于会话的 cookie 名称（例如，PHPSESSID）。它需要返回 true 值，才能让 PHP 认为会话已成功创建。

#### close() 函数

close() 函数（不要与 destroy() 函数混淆）在任何使用会话处理的 PHP 脚本执行结束时有效调用。就你的目的而言，它除了返回 true 值之外不需要做任何其他事情，尽管如果不再使用数据库连接，关闭它可能会不错。在大多数生产环境中，你将使用一个已为其他目的打开的全局可访问的数据库句柄，因此你无疑会在脚本结束时有代码来再次关闭它。因此，在实践中，此函数只需要返回 true 值。

#### read() 函数

每当尝试从 $_SESSION 哈希中检索变量时，就会使用 read() 函数。它将会话标识符作为其唯一操作数，并期望返回 $_SESSION 整体的序列化表示。你实际上不会在类中使用此函数，因为你将进行自己的会话变量处理。

#### write() 函数

每当尝试更改或添加到 $_SESSION 时，就会使用 write() 函数。它将会话标识符，后跟 $_SESSION 的预序列化表示，作为其两个参数。它期望如果数据成功提交则返回 true。即使未注册会话变量，也会调用此方法，而且这是首次向你揭示生成的会话 ID。

#### destroy() 函数

每当代码中使用 session_destroy 函数时，就会调用 destroy() 函数。执行时必须返回 true。





## gc() 函数

gc()（垃圾清理）函数应能够接受“会话 cookie 的最长生存期”参数作为其唯一操作数，并清除任何超过该生存期的会话。完成后应返回 true。此函数似乎在 open() 之前被调用，以便 PHP 在会话被使用前清除任何过期会话。

## HTTPSession 类简介

HTTPSession 类是实现面向对象会话管理的便捷方式，同时也可为你的应用程序提供基本身份验证方法。在此，你将使用先前讨论的 session_set_save_handler() 方法，实现自己的方法来替换 PHP 的方法。

它将是一个完全自包含的类，向你的应用程序主体隐藏所有 PHP 的 session_ 函数。

它还提供会话变量处理功能，可绕过 PHP 自身的处理方式。与将多个变量存储在单个序列化哈希中不同，你的方法将为每个变量使用单独的表行。这可以极大地加快访问速度。但是请注意，先前的会话处理指令方法并非设计用于处理类方法，因此在实现时需要相当巧妙。

## 数据库架构

该类依赖于三个表的存在。重建这些表的 SQL（PostgreSQL 方言）位于以下代码中。在继续之前，请先创建包含这些表的新数据库。

```sql
CREATE TABLE http_session (
	"id" SERIAL PRIMARY KEY NOT NULL,
	"ascii_session_id" character varying(32),
	"logged_in" bool,
	"user_id" int4,
	"last_impression" timestamp,
	"created" timestamp,
	"user_agent" character varying(256)
);

CREATE TABLE "user" (
	"id" SERIAL PRIMARY KEY NOT NULL,
	"username" character varying(32),
	"md5_pw" character varying(32),
	"first_name" character varying(64),
	"last_name" character varying(64)
);
```

你可以根据需要自定义用户表。你可能希望存储的内容不仅仅是名和姓。请注意，还包含一个名为 last_impression 的列。它用于存储用户上次针对其会话留下印象（即请求页面）的时间和日期。这用于计算会话超时。

```sql
INSERT INTO "user"(username,md5_pw,first_name,last_name) VALUES
('ed','827ccb0eea8a706c4c34a165891f84e7b', 'Ed', 'Lecky-Thompson');
```

```sql
CREATE TABLE "session_variable" (
	"id" SERIAL PRIMARY KEY NOT NULL,
	"session_id" int4,
	"variable_name" character varying(64),
	"variable_value" text
);
```

正如你所见，会话是按标准串行 ID 索引存储的，而不是按 PHP 生成的会话 ID 存储的。这使得查看会话变量时索引速度快得多（数字的索引效果始终优于字符串）。

此时创建一个测试用户是值得的（例如，用户名 'ed'，密码 '12345'）。你需要知道该密码的 MD5 表示形式才能将其输入数据库。当然，在现实世界中，你会有一个应用程序来完成此操作，但目前，以下是使后面示例正常工作所需的 SQL：

首先，请查看类 HTTPSession.phppm 的完整代码。别担心。在你试用之后，你将逐一了解所有内容，包括如何指示 `session_set_save_handler` 使用类方法。

## 代码：HTTPSession.phppm

请记住，使用 php 扩展名是为了明确将其标识为一个类，而非模板或独立的可执行脚本。

请注意，此类中的长 SQL 语句必须输入在同一行；不得换行到多行。如果你使用 www.wrox.com 上提供的代码，则不会有问题。

```php
<?php
class HTTPSession {
    private $php_session_id;
    private $native_session_id;
    private $dbhandle;
    private $logged_in;
    private $user_id;
    private $session_timeout = 600; # 10 minute inactivity timeout
    private $session_lifespan = 3600; # 1 hour session duration

    public function __construct() {
        # Connect to database
        $this->dbhandle = pg_connect("host=db dbname=prophp6 user=ed") or die
        ("PostgreSQL error:--> " . pg_last_error($this->dbhandle));
        # Set up the handler
        session_set_save_handler(
            array(&$this, '_session_open_method'),
            array(&$this, '_session_close_method'),
            array(&$this, '_session_read_method'),
            array(&$this, '_session_write_method'),
            array(&$this, '_session_destroy_method'),
            array(&$this, '_session_gc_method')
        );
        # Check the cookie passed - if one is passed, and if it looks wrong we'll
        # scrub it right away
        $strUserAgent = $_SERVER["HTTP_USER_AGENT"];
        if ($_COOKIE["PHPSESSID"]) {
            # Security and age check
            $this->php_session_id = $_COOKIE["PHPSESSID"];
            $stmt = "select id from \"http_session\" where ascii_session_id = '" .
                $this->php_session_id . "' AND ((now()) - created) < '" .
                $this->session_lifespan . " seconds') AND user_agent = '" .
                $strUserAgent . "' AND (now()) - last_impression) <= '" .
                $this->session_timeout . " seconds' OR last_impression IS NULL)";
            $result = pg_query($stmt);
            if (pg_num_rows($result) == 0) {
                # Set failed flag
                $failed = 1;
                # Delete from database - we do garbage cleanup at the same time
                $maxlifetime = $this->session_lifespan;
                $result = pg_query("DELETE FROM \"http_session\"
                WHERE (ascii_session_id = '" . $this->php_session_id . "') OR (now() - created > '" . $maxlifetime . " seconds')");
                # Clean up stray session variables
                $result = pg_query("DELETE FROM \"session_variable\" WHERE
                session_id NOT IN (SELECT id FROM \"http_session\")");
                # Get rid of this one... this will force PHP to give us another
                unset($_COOKIE["PHPSESSID"]);
            }
        }
        # Set the life time for the cookie
        session_set_cookie_params($this->session_lifespan);
        # Call the session_start method to get things started
        session_start();
    }

    public function Impress() {
        if ($this->native_session_id) {
            $result = pg_query("UPDATE \"http_session\" SET last_impression = now()
            WHERE id = " . $this->native_session_id);
        }
    }

    public function IsLoggedIn() {
        return($this->logged_in);
    }

    public function GetUserID() {
        if ($this->logged_in) {
            return($this->user_id);
        } else {
            return(false);
        }
    }

    public function GetUserObject() {
        if ($this->logged_in) {
            if (class_exists("User")) {
                $objUser = new User($this->user_id);
                return($objUser);
            } else {
                return(false);
            }
        }
    }

    public function GetSessionIdentifier() {
        return($this->php_session_id);
    }

    public function Login($strUsername, $strPlainPassword) {
        $strMD5Password = md5($strPlainPassword);
        $stmt = "select id FROM \"user\" WHERE username = '$strUsername'
            AND md5_pw = '$strMD5Password'";
        $result = pg_query($stmt);
        if (pg_num_rows($result) > 0) {
            $row = pg_fetch_array($result);
            $this->user_id = $row["id"];
            $this->logged_in = true;
            $result = pg_query("UPDATE \"http_session\" SET logged_in = true,
                user_id = " . $this->user_id . " WHERE id = " .
                $this->native_session_id);
            return(true);
        } else {
            return(false);
        }
    }

    public function LogOut() {
        if ($this->logged_in == true) {
            $result = pg_query("UPDATE \"http_session\" SET logged_in = false,
                user_id = 0 WHERE id = " . $this->native_session_id);
            $this->logged_in = false;
            $this->user_id = 0;
            return(true);
        } else {
            return(false);
        }
    }

    public function __get($nm) {
        $result = pg_query("SELECT variable_value FROM session_variable WHERE
            session_id = " . $this->native_session_id . " AND
            variable_name = '" . $nm . "'");
        if (pg_num_rows($result) > 0) {
            $row = pg_fetch_array($result);
            return(unserialize($row["variable_value"]));
        } else {
            return(false);
        }
    }

    public function __set($nm, $val) {
        $strSer = serialize($val);
        $stmt = "INSERT INTO session_variable(session_id, variable_name,
            variable_value) VALUES(" . $this->native_session_id .
            ", '$nm', '$strSer')";
        $result = pg_query($stmt);
    }

    private function _session_open_method($save_path, $session_name) {
        # Do nothing
        return(true);
    }

    private function _session_close_method() {
        pg_close($this->dbhandle);
        return(true);
    }

    private function _session_read_method($id) {
        # We use this to determine whether or not our session actually exists.
        $strUserAgent = $_SERVER["HTTP_USER_AGENT"];
        $this->php_session_id = $id;
        # Set failed flag to 1 for now
        $failed = 1;
        # See if this exists in the database or not.
        $result = pg_query("select id, logged_in, user_id from \"http_session\"
            where ascii_session_id = '$id'");
        if (pg_num_rows($result) > 0) {
            $row = pg_fetch_array($result);
            $this->native_session_id = $row["id"];
            if ($row["logged_in"] == "t") {
                $this->logged_in = true;
                $this->user_id = $row["user_id"];
            } else {
                $this->logged_in = false;
            }
        } else {
            $this->logged_in = false;
        }
    }
}
```



```
## We need to create an entry in the database
$result = pg_query("INSERT INTO http_session(ascii_session_id,
logged_in,user_id, created, user_agent) VALUES
('$id','f',0,now(),'$strUserAgent')");

## Now get the true ID
$result = pg_query("select id from \"http_session\" where
ascii_session_id = '$id'");

$row = pg_fetch_array($result);
$this->native_session_id = $row["id"];
};
// Just return empty string
return("");
}

public function _session_write_method($id, $sess_data) {
return(true);
}

private function _session_destroy_method($id) {
$result = pg_query("DELETE FROM \"http_session\" WHERE
ascii_session_id = '$id'");
return($result);
}

private function _session_gc_method($maxlifetime) {
return(true);
}

}
?>
```

## 测试 HTTPSession 类的代码

在阅读代码之前，先为一个想象中的用户登录和退出测试一下该类。以下简单脚本展示了该类的实际运行情况：

```
<?php
require_once("HTTPSession.phpm");
$objSession = new HTTPSession();
$objSession->Impress();
?>
HTTPSession Test Page
<HR>
<B>Current Session ID: </B> <?=$objSession->GetSessionIdentifier(); ?><BR>
<B>Logged in? </B> <?=(($objSession->IsLoggedIn() == true) ?
"Yes" : "No")?><BR>
<BR><BR>
Attempting to log in ...
<?php
$objSession->Login("ed", "12345");
?>
<BR><BR>
<B>Logged in? </B> <?=($objSession->IsLoggedIn() == true) ?
"Yes" : "No") ?><BR>
<B>User ID of logged in user: </B> <?=$objSession->GetUserID(); ?><BR>

<BR><BR>
Now logging out...
<?php
    $objSession->Logout();
?>

<BR><BR>

<B>Logged in? </B> <?=($objSession->IsLoggedIn() == true) ?
"Yes" : "No") ?><BR>
<BR><BR>
```

运行此脚本后，您应该看到类似以下的输出：

```
HTTPSession Test Page
Current Session ID: 51bd591g054sn3bp2dsur4pme3
Logged in? No

Attempting to log in ...

Logged in? Yes
User ID of logged in user: 1

Now logging out ...
Logged in? No
```

如果在 Web 浏览器中多次点击“刷新”，您应该会反复看到相同的输出。会话标识符会持续存在，因此保持不变。

如果您想亲自验证会话的登录状态是否确实被保持，请尝试注释掉 Logout 行（即 `<?php $objSession->Logout(); ?>`），然后点击“刷新”。您应该会看到页面顶部的“Logged in?”语句反复返回 Yes。

查看数据库也很有价值。只要用户成功登录，该标志就会在数据库表中的会话上设置，并保持到会话本身被删除或显式调用 Logout 方法为止：

```
prophp5=# SELECT * FROM http_session ;
```

| id | ascii_session_id | logged_in | user_id | last_impression | created | user_agent |
|---|---|---|---|---|---|---|

现在尝试会话变量功能：

```
<?php
require_once("HTTPSession.phpm");

$objSession = new HTTPSession();
$objSession->Impress();
?>
HTTPSession Variable Test Page
<HR>
<B>Current Session ID: </B> <?=$objSession->GetSessionIdentifier();?><BR>
<B>Logged in? </B> <?=(($objSession->IsLoggedIn() == true) ? "Yes" : "No")?><BR>
<BR><BR>
<B>Current value of TESTVAR:</B> [<?=$objSession->TESTVAR?>]<BR>
<BR><BR>
Setting TESTVAR to 'foo'
<BR><BR>
<?php
$objSession->TESTVAR = 'foo';
?>
<B>Current value of TESTVAR:</B> [<?=$objSession->TESTVAR?>]<BR>
<BR><BR>
```

运行此脚本（暂时只运行一次），您将看到类似以下的内容：

```
HTTPSession Variable Test Page

Current Session ID: 51bd591g054sn3bp2dsur4pme3
Logged in? No

Current value of TESTVAR: []

Setting TESTVAR to 'foo'
Current value of TESTVAR: [foo]
```

点击“刷新”，您将看到 TESTVAR 的值被持续保存。顶部的当前值语句也将显示 foo：

```
HTTPSession Variable Test Page

Current Session ID: 51bd591g054sn3bp2dsur4pme3
Logged in? No

Current value of TESTVAR: [foo]

Setting TESTVAR to 'foo'
Current value of TESTVAR: [foo]
```

快速查看数据库中的 session_variable 表，可以看到实际存储的内容：

```
prophp5=# SELECT * FROM session_variable;
```

| id | session_id | variable_name | variable_value |
|---|---|---|---|
| 6 | 168 | TESTVAR | s:3:"foo"; |

可以看出，使用序列化来存储数据与 PHP 的做法一致。不过，与 PHP 不同的是，您为每个变量使用一行。这样可以让多个变量分别序列化，针对单个会话存储。在 PHP 原生会话变量处理中，所有变量都被合并在一个关联数组中，然后再进行序列化。这可能带来非常严重的性能影响。序列化和反序列化都有相当大的开销，而在字符串处理方面，PHP 也不是世界上最快的语言——这个荣誉大概属于 PERL。基于此，此次做出了刻意违背常规的决定。

显然，HTTPSession 类非常易于使用，但让我们更详细地看一下类本身，以便既理解其背后的逻辑，又能充分准备在生产应用中部署它。

## HTTPSession 类的工作原理

首先来看类的私有成员变量，如表 12-1 所示。

### 表 12-1 私有成员变量

| 变量 | 用途 |
| :--- | :--- |
| php_session_id | PHP 生成的 32 字符会话 ID |
| native_session_id | 用于在数据库中标识会话的原生会话 ID。此 ID 永远不会发送到 Web 浏览器，仅用于数据库实体关系目的。 |
| dbhandle | 数据库连接句柄。在生产环境中，这通常会在其他地方声明为全局资源，HTTPSession 类会像使用其他资源一样使用它。 |
| logged_in | 此会话是否为已登录会话？如果为 true，则将提供用户 ID。 |
| user_id | 当前已登录用户的 ID（来自数据库表） |
| session_timeout | 非活动超时。如果两次报告的页面展示之间超过此时间，则会话将被销毁。以秒为单位，因此 600 = 10 分钟。 |
| session_lifespan | 会话的最大生存期。此值提供给 PHP 用于设置 Cookie，也用于垃圾清理 SQL，以保持数据库中没有僵死会话。同样以秒为单位，因此 3600 = 1 小时。 |

### 构造函数

您希望类可以即插即用。这样程序员只需实例化一次，然后就无需再关心它了。

构造函数会执行以下操作：

- 设置数据库连接。在生产环境中，这通常由另一个类处理。
- 告诉 PHP 如何在自定义类中处理会话事件（稍后将详细讨论）
- 在 PHP 有机会获取会话标识符之前，检查客户端是否提供了现有会话标识符（如果用户正处于会话中而不是启动新会话，则会发生这种情况）。它还会对年龄、非活动状态以及报告的 HTTP 用户代理的一致性执行各种检查。如果检查失败，则将其彻底移除（以及发现的任何垃圾数据），以便 PHP 可以从头开始颁发新会话。
- 设置会话生存期参数（PHP 在颁发 Cookie 时会遵守此参数）
- 告诉 PHP 按正常方式启动会话

请注意 session_set_save_handler 使用的有趣语法：

```
session_set_save_handler(
 array(&$this, '_session_open_method'),
 array(&$this, '_session_close_method'),
 array(&$this, '_session_read_method'),
 array(&$this, '_session_write_method'),
 array(&$this, '_session_destroy_method'),
 array(&$this, '_session_gc_method')
 );
```

尽管基本缺乏文档，但此方法的参数不一定非要是表示当前 PHP 作用域内过程式函数名的字符串。

相反，您可以传递一个包含两个组件的数组。第一个是对类实例的引用（在此例中，&$this 指向该类的当前实例）。第二个是该类的方法名。

### session_read_method() 处理程序

由于这是 PHP 自身会话管理在确定有效会话 ID（通过生成全新会话或 Web 浏览器提交仍然有效的 Cookie）后调用的第一个方法，因此您使用此方法来确保会话数据库保持完全最新。

如果 PHP 提供的 32 字符会话标识符确实存在于数据库中，则会根据数据库记录更新类成员变量（logged_in 和 user_id）。如果不存在，则将使用默认值插入记录。

### Impress() 函数

此方法触碰会话，以指示发生了新的页面展示。通常，任何使用会话类的页面在实例化该类后立即都会调用此方法。





数据库中的最后印象列用于确定会话超时，因此如果你希望特定页面计入用户累计的非活动超时，调用此方法非常重要。

如果你在页面顶部使用任何形式的 `include()` 或 `require()` 语句来引入代码库（或者，确实，其他 `include()` 或 `require()` 语句），你可以考虑将会话调用和印象放置在这个文件中。这样，你就永远不会忘记包含它们。

## The IsLoggedIn() 函数

此方法仅根据私有成员变量报告，该会话在其生命周期内是否进行过成功登录，且该登录未通过 `logout()` 被撤销。

## The GetUserID() 和 GetUserObject() 函数

如果用户已登录，则这两个函数分别返回已登录用户的 ID（来自数据库中定义的用户表）以及，如果可能，用户类的实例化对象（如果存在的话）。

本章未对其一定义，因为这略超出会话管理的范围，但对于任何严肃的生产应用程序，你几乎肯定都会想要开发一个，因为你几乎肯定会频繁地读写当前登录用户的属性。

该类假设你的 `User` 类（无论其内部如何工作）是在外部使用用户 ID 作为构造函数的唯一操作数来实例化的。因此，这与第 7 章，“Object-Relation Mapping” 中关于 `DataBoundObject` 的讨论配合良好，尽管你还需要传递一个与该类使用的数据库凭据匹配的 PDO 实例。

## The GetSessionIdentifier() 函数

此方法返回 32 字符的 PHP 会话标识符，而不是内部（数据库）标识符。这是应用程序中更可能使用的属性，因为内部标识符对 PostgreSQL 才真正有意义，且从不暴露给应用程序或 Web 浏览器。

## The __get() 和 __set() 重载方法

利用 PHP 6 对表面公共成员变量的检查和赋值进行重载的支持，这些重载方法提供了其自身的会话变量功能。简单来说，为给定会话设置变量只需向会话类中适当命名的成员变量赋值即可。同样，读取它只需直接读取，就像读取公共声明的成员变量一样。

PHP 会自动意识到这不是原生成员变量，因此会调用相关的 `__get()` 或 `__set()` 来分别获取或设置会话变量表中的值。这意味着你不能使用与会话类中任何方法或成员同名的会话变量。例如，名为 `user_id` 的会话变量名是不行的。

## 性能注意事项

请注意，虽然前面的会话类是数据库驱动的，但它不使用 PHP 数据对象（PDO），正如你在第 6 章中发现的，PDO 肯定是 PHP 6 中管理数据库通信的首选机制。这是一个经过深思熟虑的决定。PDO 有性能开销。单独来看，这些开销微乎其微（肉眼不可见），但尽管如此，提供那层抽象以保持代码整洁优雅本身就有开销——如果有一样东西需要尽可能快地运行，那就是会话管理。不要忘记，在启用会话的应用程序中，*每个 HTTP 请求*都会调用会话类，因此每个请求都会访问数据库。如果再加上 PDO 的额外开销，每个请求上的那些微小秒数很快就会累积起来。

解决方案是忍一忍，接受从架构上讲这并不十分“干净”，但要明白它有性能收益。毕竟，如果你的网站慢得要命，没有人会使用它，即使它构建得再好。你的用户不关心架构；他们只会看到网站很慢，然后再也不回来了。

## 替代存储

使用数据库存储会话数据当然很有吸引力。它具有可扩展性——你可以使用同一数据库服务器添加更多服务器，或添加相互复制的更多数据库服务器。它易于调试——如果你不确定为什么某事无法工作，只需查看会话表即可。它使编写查询变得容易——你可以在 `INNER JOIN` 中使用会话表来编写精简的单 SQL 查询。它也比使用平面文件（PHP 的默认解决方案）快得多。

然而，如果你追求的是原始速度，那么无论是磁盘还是数据库都不是办法——内存才是。如果你的应用程序要成为下一个 Facebook，这或许值得研究。内存当然是超快的；而且如果你使用与应用程序服务器相同的内存来存储会话数据，它将比数据库或磁盘快得多。不过，请记住，这种方法并不完全满足可扩展性测试。如果多台服务器都在使用自己的内存来存储会话数据，你就无法在它们之间进行负载均衡——而且服务器断电时内存总会丢失。调试也是一件麻烦事，因为不像 SQL 数据库的控制台那样，没有轻松的人类方式来访问 `memcached` 服务器。

不过，如果你想尝试，请随意。这是要添加到你工具箱中的另一种技术。你寻找的解决方案几乎肯定会使用 `memcached`。你可以从 `www.danga.com/memcached/` 下载它，但你还需要事件通知库 `libevent`，来自 `www.monkey.org/~provos/libevent/`，必须先安装它。

`memcached` 提供了一种几乎傻瓜式的键值数据库服务器。给它一个键和一个值，它就会将该值与该键关联存储。再次给它该键，它就会告诉你针对该键存储的值。就这些——没有查询，没有表，没有用户名和密码，当然也没有巧妙的存储过程。因为它很简单，所以速度极快，你会发现的。只需启动 `memcached` 服务器，告诉它可以消耗多少宝贵的物理 RAM（通常不超过已安装内存的 25 %）即可开始。

PHP 有（某种程度上）针对 `memcached` 服务器读写的内置支持——有关更多信息，请参阅 `http://uk.php.net/manual/en/ref.memcache.php`。你必须先安装一个 PECL 模块并告知 `php.ini`——但一旦完成，你就会发现可以用于连接、断开连接、读取和写入 `memcached` 服务器的简单方法。

一些示例代码可在 `www.php.net/manual/en/function.session-set-save-handler.php` 中找到，但最佳方法可能是修改本章中的 `HTTPSession` 类，以同时支持数据库和 `memcached` 作为存储机制。这样，你可以简单地切换开关来在数据库存储和内存存储之间选择，并保持客户端代码一致。

## 综合起来

本章构建的 `HTTPSession` 类是一个完全可复用、模块化的组件。它可以轻松包含在几乎任何需要维护会话数据的项目中，并支持注册用户的身份验证。

本讨论为 PHP 自身的会话管理提供了面向对象的接口，并用更灵活的变体替换了其会话变量功能，即每个变量都分别存储，以便提高速度和代码的整洁性。

与你自己的应用程序集成应该是最直接的。你可能会发现需要扩展其功能以适应你自己的需求，但因为它是一个自包含的类，所以这比扩展 PHP 原生的会话管理要容易得多。

还值得指出的是，从本章前面部分引入的唯一额外安全机制是用户代理检查。如果你需要更强的安全性，可能希望探索集成其他安全功能，如前面讨论过的 IP 方差分析。

## 总结

在本章中，你学习了会话：为什么它们有用，如何在你的应用程序中最好地实现它们，以及如何通过一些战略性安全措施来避免通常与会话相关的一些安全陷阱。

你还学习了 PHP 对会话的传统实现，以及为什么它在很大程度上不适合专业软件架构师。你研究了如何轻松扩展和调整它，使其功能更强大、可扩展性更好。

最后，你利用这些知识构建了一个单一的、模块化的、自包含的 `HTTPSession` 类，可以轻松集成到你的未来应用程序中。你还简要地研究了使用数据库存储会话相关的性能注意事项，并探索了使用内存存储作为替代方案的可能性。

说到未来的应用程序，你几乎准备好开始一个案例研究了。在接下来的几章中，你将学习如何将过去 12 章中积累的工具最好地用于应用程序的设计——这种技术被称为应用程序架构。

第 13 章讨论了良好应用程序设计的基础——也就是说，面对一组功能需求，如何最好地应用最佳实践业务分析技术来设计健壮、可扩展且安全的软件架构。





## 应用架构

PHP 最初出现在 20 世纪 90 年代下半叶时，一场小规模的革命发生了。高度交互且功能丰富的 Web 应用程序，曾经是能够委托昂贵开发公司或雇佣庞大内部团队的大公司的专属领地，如今却到处涌现。突然，一些看似精巧的交互式 Web 内容——远超传统（且如今大多被遗忘）的留言簿 CGI 脚本——开始出现在一些非常意想不到的地方。

这场革命背后的一个驱动因素是 PHP 极高的可访问性和浅层学习曲线。不仅仅是“hello world”程序实现起来清新易懂。即使是像数据库集成这样传统上复杂的过程，也只需几行代码就能实现。这与臭名昭著的难以处理的 PERL 以及被大肆吹嘘（但通常晦涩难懂）的 Java Servlet 引擎形成鲜明对比。

然而，问题在于这种可访问性很快被滥用。在某些情况下，这导致缺乏经验的开发人员构建了复杂的应用程序。在另一些情况下，以前专注的专业人士（或许可以理解）面对 PHP 提供的简单性所带来的巨大诱惑，略微放松了自己的传统标准。

这种开发方式所带来的风险显而易见。这种滥用导致了规模惊人的不可维护的应用程序，以及大量有据可查的不稳定性、不可靠性甚至可被利用的安全漏洞案例。

尽管 Java 和 .NET 等许多编程语言通过其设计强制执行良好的编程实践，但 PHP 需要自律。经验丰富的 PHP 专业人士与业余程序员之间的区别正在于此——自律。正是这种自律使得良好的项目规划成为必要；而项目规划的很大一部分是应用架构。

在本章中，你将学习良好应用架构的基础，以及为什么被称为 MVC 的方法是你在编程中值得使用的优秀方法。你将构建一个有用的工具包来处理 MVC 原则的一些核心部分，并学习如何在应用程序中使用它们。最后，你将了解两种在应用程序中实现模板使用的有效方法，以及如何将模板与刚刚接触的 MVC 工具包结合使用。

## MVC 简介

M 代表模型，V 代表视图，C 代表控制器——但这一切究竟意味着什么？MVC 最好被描述为一种通常称为设计模式的东西，即针对特定上下文中反复出现的问题的可重用解决方案的描述。设计模式存在的目的，是为了以一致的方式应对大型应用程序设计时面临的挑战。通过以经过验证的方式处理架构，可以实现最佳实践。

在这种情况下，问题在于如何最佳地将程序的用户界面（视图）、实际执行复杂思考的业务和实用类（模型）以及其内部处理和决策（控制器）分离开来，使其代表三个独立且可分离的组件。解决方案（你可能已经猜到）是 MVC。

为什么需要这种方法？

首先，分离带来了可互换性。通过保持三个组件分离，但又让它们以一致的方式相互通信，你可以在需要时替换任何组件。例如，如果你需要重新构建 Web 应用程序以在 PDA 而不是 Web 浏览器上运行，你可以将视图组件替换为专为 PDA 渲染内容（而非 Web 浏览器）的组件。如果你需要通过语音输入而非鼠标点击来接受数据，你可以将同一个组件替换为使用 VoiceXML 的组件。

其次，如果逻辑在合理的位置进行分离，那么调试以捕捉难以追踪的错误，以及发布后的维护编程，都将变得简单得多。使用面向对象编程（本书前几章有详细介绍）的理由同样适用于此。与其只有少数几个代码臃肿的庞大文件，不如拥有大量相互通信的小组件要好得多。通过这种方式分离组件，复杂的软件架构可以变得简单得多。

最后，你可能希望为单模型应用程序实现多个控制器和视图。以之前的 PDA 示例为例，如果你选择 MVC 架构，你可以实现必要的控制器和视图以支持传统 Web 浏览器、PDA、手机、语音、平板电脑甚至旧版浏览器——所有这些都将使用同一个模型，即使它们使用不同的视图和控制器。如果没有 MVC，你将发现自己无法重用模型背后的代码，并且将背负着不必要的重复所带来的所有问题。

正如你所看到的，MVC 是一种很棒的设计模式，也是你应尽可能使用的一种。接下来的章节将逐一探讨三个组件，它们如何相互交互，以及最重要的是，MVC 在 PHP Web 应用架构中的位置。

## 模型

模型是你应用程序的核心。一般来说，它指的是你开发的一组类，用于处理应用程序行为中涉及的各种过程。它关注的是检索输出背后的数据（可能来自数据库），以及根据用户输入操作数据。它直接连接到控制器，对视图没有可见性（也看不到）。控制器为模型提供指令；视图将从控制器检索到的数据操作成可供人类使用的输出。

判断你的模型是否符合上述要求的关键测试是问自己：*我的模型类中有 Web 特定的内容吗？*如果有，那么你做错了。有关页面、用户流、导航、Cookie、会话——所有与 Web 相关的内容——都应明确位于你的控制器中。任何涉及用户输入（或输出呈现）的内容都应在你的视图中。

如果你可以取出构成模型的类，将其放入命令行应用程序、后台守护进程甚至桌面应用程序中，而无需任何更改，那么你可以确定你做得对。

## 视图

视图位于应用程序的前端。它展示用户请求的来自控制器的数据，或者控制器认为用户需要知道的信息。它允许用户通过其用户界面（通常是链接和表单输入）向控制器反馈。

在实践中，视图由一系列 HTML 页面模板组成，或者是应用程序适合的任何标记语言——例如，移动应用程序的无线标记语言（WML）。视图中通常包含有限的后端逻辑来控制条件（事物是否应该显示）、动态内容区域（例如，在导航栏中显示用户的用户名）和循环（用于显示数据表）。不应该直接引用类，*当然*也不应该与数据库通信。

至关重要的是，视图和模型之间没有直接关联。为了访问模型中包含的繁重工作，视图必须向控制器发出命令。控制器随后会在必要时将该消息传递给模型。

## 控制器

MVC 范式的第三个元素是控制器。这最好被视为用户在你的应用程序中的旅程的拥有者。当用户请求页面时，该请求会通过控制器。控制器随后会根据需要将数据传入（并从）模型检索数据，然后通过视图将该信息返回给用户。

实际上，控制器是一种抽象形式。视图用页面、导航、点击、表单输入等术语进行交流（非常“Web”的东西），而模型则用获取属性、设置属性、执行任务等术语进行交流（非常“业务”的东西）。两者之间必须有一个转换层——而控制器正是做这件事的。

在实践中，应用程序的控制器由一系列可执行脚本组成（就本书而言，是 PHP 脚本），Web 应用程序中的页面可以向这些脚本发送 `GET` 或 `POST` 请求。控制器根据用户当前所在的页面、用户在该页面上的操作、页面条件（例如表单输入状态）、外部条件（例如会话数据）以及无数其他因素，决定如何处理每个请求。然后，它会根据需要与模型进行通信，随后将用户引导至另一个视图状态。




图 13-1 显示了控制器在您的应用程序中的作用。

![](img/a1b732997d9cb194dceec0570dc79710_316_0.png)

图 13-1 模型-视图-控制器 (MVC) 范式

## Web 应用程序中的 MVC

MVC 并非新概念。确实，有些人认为它是 *输入、处理和输出 (IPO)* 模型的演进，而该模型是过去那些线性、纯文本应用程序的最佳实践模型。MVC 在 Web 环境中的应用相对简单。

模型由您的一组类表示，假设您在应用程序中遵循了面向对象的方法。在任何 Web 语言中，这些类都会与任何外部数据源执行核心通信，做出关键的应用程序决策，并对输入和输出执行解析和处理。

视图由 Web 浏览器表示，或者更确切地说是其中显示的内容。在发出请求（无论是简单的页面请求还是更新或查询数据库的指令）后，由模型确定的输出实际上是由 Web 浏览器显示的。

也许令人困惑的是，控制器也由 Web 浏览器表示，或者更确切地说是用户在其中的操作。无论是一系列链接还是复杂的表单，用户浏览器发出的 `GET` 和 `POST` 请求都代表了最初将数据放入模型的努力。这些操作通过控制器传递。

## PHP 中的 MVC

如前所述，PHP 的简单性和易访问性很容易被滥用，以至于应用程序变得难以维护。具体来说，这种滥用表现为将模型、视图和控制器合并到单个 PHP 脚本中。事实上，_脚本_ 这个术语仅在这种方法中才合适。在合适的 MVC 应用程序中，没有脚本，只有组件。

### 不该怎么做

让任何经验不足的 PHP 开发人员创建一个留言簿应用程序，他或她可能会想到一个单一文件。该文件将命名为 `guestbook.php`，并处理显示现有条目和向数据库添加新条目。逐行查看代码，它可能如下所示：

- 1. 查看传递给它的 `GET` 参数，以确定显示留言簿的哪一页。
- 2. 如果未指定页面，则决定显示第 1 页。
- 3. 检查是否传递了名为 `NewGuestBookEntry` 的参数。如果是，检查其是否符合各种有效性约束（长度和内容）并将其写入数据库。如果不是，写入错误消息并退出。
- 4. 从数据库中获取与此页码匹配的当前留言簿条目。
- 5. 将它们写入 HTML 表中（直接嵌入脚本中）。
- 6. 写出指向同一脚本的 HTML 表单，允许用户添加条目。

这种方法有许多问题，更何况使用 `GET` 而不是 `POST` 来更改数据库。（严格来说，相关的 RFC 指出这是一个糟糕的主意。）

如果回想一下支持 MVC 的原因——例如互换控制器和视图、维护和初始开发的简便性，以及多个同时存在的控制器和视图——你会发现在这三种情况中我们都会遇到困难。

相反，让我们看看一种更成熟的开发方法，它使您能够遵循 MVC 设计模式。

### 正确做法：MVC 方法

PHP 中 MVC 的第一条规则是 _拆分您的文件_。完成此任务有多种可能的方法，但许多人倾向于实际使用不同的文件扩展名来表示 MVC 模式中的不同角色，然后在适当的时候使用 `require_once` 将它们链接在一起。

不应遵循将文档化的做法，即将要 `include` 或 `require` 的文件命名为 `.inc` 扩展名，因为这无法告诉您文件的内容，从而鼓励文件之间的角色重叠。

您可以尝试类似表 13-1 所示的方法。

### 表 13-1 建议的文件命名方法

| 扩展名 | 组件 | 角色 |
|---|---|---|
| .php | 控制器 | 行为逻辑——模型与视图之间的通信基础设施 |
| .phpm | 模型 | PHP 类——应用程序的核心 |
| .phtml | 视图 | 用户输入结果的呈现以及使用户能够进行进一步输入的界面 |

“视图”一词有些误导，因为 Web 浏览器当然不仅用于呈现输出，还用于接受输入。在此情况下，视图代表您的应用程序的用户界面——通常是 HTML。

如果您不确定哪些代码应该出现在哪些模块中，可以依靠以下几条规则来确保您遵循此方法：

- [ ] .php (控制器)永远不应包含 SQL 查询或 HTML。
- [ ] .phpm (类)永远不应包含 HTML。
- [ ] .phtml (模板)永远不应包含 SQL 查询，并且只能包含非常基本的 PHP (for/if/while)。

这种分离所实现的是一种非常原始的模板化形式，称为 _原生模板_。在这种设置中，PHP 用于在单独的模板文件（在此情况下为 .phtml 文件）中呈现应用程序的输出。该输出由控制器（.php 文件）将用户输入呈现给类（.phpm 文件）来决定。

实际实现如下：

- 1. .php 文件是 `GET` 或 `POST` 请求的实际接收者（因此，无需重新配置 Apache 以支持这些新扩展名）。
- 2. .php 文件是所有 `require()` 语句的所在地，这些语句用于导入构成模型所需的类（每个类存储在 .phpm 文件中）。
- 3. .php 控制器检查 `GET` 和 `POST` 参数中的输入并确定行动方案。它将这些数据（以原始或处理后的形式）传递给这些类的方法，这些类已在上一步中通过包含使其可用。
- 4. 相关类解析输入数据，根据需要更新和查询数据库或其他数据源，并将数据返回到 .php 文件。
- 5. .php 文件随后检查来自这些类的输出。它可以根据该输出做出决策，以某种处理状态传递输出，或者原样传递。然而，交付始终是通过构建单个超变量（通常是哈希或关联数组）来完成的，该变量包含未格式化的、您想要显示给用户的输出。
- 6. .php 文件随后包含适当的 .phtml 文件，这实际上接管了执行。
- 7. .phtml 文件遍历该超变量，以合适的形式显示它，并呈现所需的任何新用户输入组件，从而向用户展示完成的 Web 页面。

这听起来可能比实际更复杂；事实上，这是一个非常简单的过程。您将在本章后面看到一些示例，展示如何最好地实现这种原生模板化。目前，您将查看一些工具包类，这些类可以通过极大地简化前面列出的某些步骤，帮助您在 PHP 中使用 MVC 设计模式。

本章稍后，您将了解此工具包如何与刚才讨论的原生模板技术很好地集成。

## MVC 迷你工具包

您即将遇到的迷你工具包使坚持 MVC 设计模式变得容易得多。该工具包仅涉及 MVC 三要素中的控制器元素。您在第 7 章中已经查看过模型方面的内容。稍后您将遇到一个名为 Smarty 的现成 PEAR 包，它允许有效地实现视图组件。

### 工具包介绍

迷你工具包使您能够以一致、干净、清晰的方式处理视图和模型之间的连接。其核心是一个请求对象，它旨在为用户对您的应用程序的输入提供更面向对象的视角。除了提供常规的直接询问用户输入的手段外，它还支持对每个参数应用约束的概念，因此您可以轻松地在代码中指定您愿意接受和不愿意接受的内容。

当然，这种错误检查做法对您来说几乎肯定不是新鲜事。然而，约束的概念使您能够通过为控制器开发提供通用方法来分离视图和模型。因为模型现在可以假设其输入在预期参数范围内，您可以将此类代码从模型中的方法中清晰地分离出来，放心地知道它已被您的 MVC 设计模式中的控制器审查过。

这是一种完全合适的方法。毕竟，健全性检查不是模型功能的核心。通过将此类检查的责任留在模型本身之外，您还可以为与同一模型通信的不同控制器和不同视图应用不同的规则。这与 MVC 背后的哲学非常一致。

您可能希望扩展或修改这些类以更好地适应您自己的需求。这里提供的是一个非常基本的实现。例如，您可能希望检查添加方法的可行性，以使用隐藏表单参数自动延续 GET 和 POST 变量，而无需转向会话变量。这对于在搜索结果数据集中向前和向后分页，并在每次请求新页面时保持搜索条件可能很有用。此类功能可以轻松集成到请求对象本身中。在第 14 章中，您将遇到一些已经这样做的 PHP 框架。




此外，此处提供的预打包约束类型并非详尽无遗。然而，快速浏览一下代码应该能让你非常清楚，如果应用程序需要，添加自己的约束类型是多么容易。

## 常量

你确实需要定义若干常量，以便你的类能够无缝协同工作。这些常量定义了三种参数类型（GET、POST 和 Cookies），以及你可以应用的各种约束类型。如前所述，你可以随意定义可能适合你应用程序的其他约束，只要记得在 Request 类中实现它们即可。

请检查以下代码，并将其保存为名为 constants.phpm 的文件：

```
<?php // Constants

define(VERB_METHOD_COOKIE, 1);
define(VERB_METHOD_GET, 2);
define(VERB_METHOD_POST, 4);
define(CT_MINLENGTH, 1);
define(CT_MAXLENGTH, 2);
define(CT_PERMITTEDCHARACTERS, 3);
define(CT_NONPERMITTEDCHARACTERS, 4);
define(CT_LESSTHAN, 5);
define(CT_EQUALTO, 6);
define(CT_MORETHAN, 7);
define(CT_NOTEQUALTO, 8);
define(CT_MUSTMATCHREGEXP, 9);
define(CT_MUSTNOTMATCHREGEXP, 10);
?>
```

请注意定义这些常量时的两种编号方案。其中一种是 _指数序列_，用于定义 HTTP 请求中提供的三个参数动词；另一种是纯 _顺序序列_，用于定义约束类型。

采用两种不同方法的原因，简要涉及了 _位逻辑_ 的特性。由于此主题在本书其他地方未曾涉及，让我们在此简要了解一下。

请考虑以下代码片段：

```
$var3 = ($var1 && $var2);
```

这里的条件语句明确要求 $var1 为真（字面意义上，或作为某个非零或非空值），且 $var2 为真（使用 && 运算符的传统用法来表达布尔逻辑）。如果两者都为真，$var3 也将为真。这非常基础，但还有一种第二种比较逻辑，使用相同的基本运算符 AND 和 OR。

请考虑以下内容：

```
$var3 = ($var1 & $var2);
```

请注意这个单个与号。这表示你想执行位运算（而非布尔运算）来进行比较。接下来发生的情况（假设 $var1 和 $var2 是整数）是，每个值的相应二进制位将受到传统布尔比较的影响（1 表示真，0 表示假）。如果 $var1 为 34 且 $var2 为 11，则适用以下情况：

```
34       =   00100010
11       =   00001011
34 & 11  =   00000010   =   2
```

因此，34 和 11 的位运算结果为 2，因为只有在“2”这一列中，两个数字的对应位都为 1。

这与常量有什么关系？简单来说，它使你能够将常量组合成一个单一值（该值由其组成常量的算术和构成），并随后轻松确定这些组成常量是什么。

如果每个常量代表二进制数中单个位的递增十进制值（本质上是 2 的幂），那么将它们相加后，得到的二进制数将具有值为 1 的位，表示求和中包含的那些常量：

```
CONST_A =   1   =   00000001
CONST_B =   2   =   00000010
CONST_C =   4   =   00000100
CONST_D =   8   =   00001000
CONST_E =   16  =   00010000
```

例如，假设你想定义一个由常量 B、D 和 E 组合而成的参数（不管这意味着什么）。只需将 2、8 和 16 相加得到 26。请看一下 26 的二进制形式，以及其组成部分：

```
CONST_B =   2   =   00000010
CONST_D =   8   =   00001000
CONST_E =   16  =   00010000
CONST_B+D+E =   26  =   00011010
```

请注意，你可以清楚地识别出组合的组成常量是 B、D 和 E；但是如何在代码中测试这一点呢？

从命令行（而不是 Web 浏览器）输入并运行以下代码。通常，你只需在命令提示符下输入 php 即可，但如果 PHP 可执行文件不在你的路径中，你需要先找到它——在 UNIX 上可以尝试 /usr/local/php/bin：

```
<?php
define('CONST_A', 1);
define('CONST_B', 2);
define('CONST_C', 4);
define('CONST_D', 8);
define('CONST_E', 16);

$myCombinedConstant = CONST_B + CONST_D + CONST_E;

if ($myCombinedConstant & CONST_A) {
    print "Combined constant contains A\n";
};
if ($myCombinedConstant & CONST_B) {
    print "Combined constant contains B\n";
};
if ($myCombinedConstant & CONST_C) {
    print "Combined constant contains C\n";
};
if ($myCombinedConstant & CONST_D) {
    print "Combined constant contains D\n";
};
if ($myCombinedConstant & CONST_E) {
    print "Combined constant contains E\n";
};
?>
```

按 Ctrl+D（UNIX）或 Ctrl+Z（Windows）结束脚本的输入。你将看到类似于以下内容的输出：

```
Combined constant contains B
Combined constant contains D
Combined constant contains E
```

你可能已经推断出，确定组合常量是否包含特定原始常量的测试方法，就是对该原始常量执行位运算 `AND`。只有当相关位在原始常量和正在测试的组合常量中都被设置时，这才会产生非零（即 `true`）值。

请注意，这种策略已被采用于表示请求方法的常量中，但未用于表示约束类型的常量。这是因为代码未来某个阶段可能允许将请求方法作为参数的组合传递给方法。然而，约束类型的性质意味着一个约束对象只有一个约束类型。因此，要组合约束，必须组合它们的对象（而非其背后的常量）。同样，请注意，这些常量已采用线性（1、2、3、4、5）编号系统，因为它们永远不会像本节描述的那样相互相加。

## Request 类

`request` 对象本身表示用户为生成页面而发出的请求。那些曾在 .NET 中工作过的人可能熟悉使用预实例化对象来访问参数，但这个 `Request` 类更为复杂一些。

与 .NET 不同，你必须自己实例化 `request` 对象，但你会发现编写的构造函数不需要参数。它会自行相当成功地检查现有的（且全局可访问的）`$_REQUEST`、`$_COOKIE`、`$_POST` 和 `$_GET` 散列，以填充其各种成员变量。

你可以立即开始使用 `request` 对象。通过使用提供的各种方法来检索参数，你可以构建应用程序。不过，这样做忽略了由 `Constraint` 类及其孪生类 `ConstraintFailure` 提供的非常有用的语法验证方法。

请详细检查以下名为 request.phpm 的源代码：

```
<?
require_once("constants.phpm");
require_once("constraint.phpm");
require_once("constraintfailure.phpm");
class request {
    private $_arGetVars;
    private $_arPostVars;
    private $_arCookieVars;
    private $_arRequestVars;
    private $_objOriginalRequestObject;

    private $_blIsRedirectFollowingConstraintFailure;

    private $_blRedirectOnConstraintFailure;
    private $_strConstraintFailureRedirectTargetURL;
    private $_strConstraintFailureDefaultRedirectTargetURL;

    private $_arObjParameterMethodConstraintHash;
    private $_arObjConstraintFailure;
    private $_hasRunConstraintTests;

    function __construct($check_for_cookie = true) {
    // Import variables
    global $_REQUEST;
    global $_GET;
    global $_POST;
    global $_COOKIE;
    $this->_arGetVars = $_GET;
    $this->_arPostVars = $_POST;
    $this->_arCookieVars = $_COOKIE;
    $this->_arRequestVars = $_REQUEST;
    if ($check_for_cookie) {
    if ($this->_arCookieVars["phprqcOriginalRequestObject"]) {
    $cookieVal = $this->_arRequestVars["phprqcOriginalRequestObject"];
    $this->_blIsRedirectFollowingConstraintFailure = true;
    if (strlen($cookieVal) > 0) {
    $strResult = setcookie ("phprqcOriginalRequestObject", "",
    time() - 3600, "/", "");
    $origObj = unserialize(stripslashes($cookieVal));
    $this->_objOriginalRequestObject = &$origObj;
    $this->_arRequestVars["phprqcOriginalRequestObject"] = "";
    $this->_arGetVars["phprqcOriginalRequestObject"] = "";
    $this->_arPostVars["phprqcOriginalRequestObject"] = "";
    };
    $this->_blIsRedirectOnConstraintFailure = true;
    } else {
    $this->_blIsRedirectOnConstraintFailure = false;
    };
    } else {
```





```php
$this->_blIsRedirectOnConstraintFailure = false;
}

$this->_arObjParameterMethodConstraintHash = Array();
$this->_arObjConstraintFailure = Array();
$this->_blHasRunConstraintTests = false;
}

function IsRedirectFollowingConstraintFailure() {
    return($this->_blIsRedirectOnConstraintFailure);
}

function GetOriginalRequestObjectFollowingConstraintFailure() {
    if ($this->_blIsRedirectOnConstraintFailure) {
        return($this->_objOriginalRequestObject);
    };
}

function SetRedirectOnConstraintFailure($blTrueOrFalse) {
    $this->_blRedirectOnConstraintFailure = $blTrueOrFalse;
}

function SetConstraintFailureRedirectTargetURL($strURL) {
    $this->_strConstraintFailureRedirectTargetURL = $strURL;
}

function SetConstraintFailureDefaultRedirectTargetURL($strURL) {
    $this->_strConstraintFailureDefaultRedirectTargetURL = $strURL;
}
function GetParameterValue($strParameter) {
    return($this->_arRequestVars[$strParameter]);
}

function GetParameters() {
    return($this->_arRequestVars);
}

function GetCookies() {
    return($this->_arCookieVars);
}

function GetPostVariables() {
    return($this->_arPostVars);
}

function GetGetVariables() {
    return($this->_arGetVars);
}

function AddConstraint($strParameter, $intMethod, $objConstraint) {
    $newHash["PARAMETER"] = $strParameter;
    $newHash["METHOD"] = $intMethod;
    $newHash["CONSTRAINT"] = $objConstraint;
    $this->_arObjParameterMethodConstraintHash[] = $newHash;
}

function TestConstraints() {
    $this->_blHasRunConstraintTests = true;
    $anyFail = false;
    for ($i=0; $i<=sizeof($this->_arObjParameterMethodConstraintHash) -1; $i++) {
        $strThisParameter =
            $this->_arObjParameterMethodConstraintHash[$i] ["PARAMETER"];
        $intThisMethod = $this->_arObjParameterMethodConstraintHash[$i] ["METHOD"];
        $objThisConstraint =
            $this->_arObjParameterMethodConstraintHash[$i] ["CONSTRAINT"];
        $varActualValue = "";
        if ($intThisMethod == VERB_METHOD_COOKIE) {
            $varActualValue = $this->_arCookieVars[$strThisParameter];
        }
        if ($intThisMethod == VERB_METHOD_GET) {
            $varActualValue = $this->_arGetVars[$strThisParameter];
        }
        if ($intThisMethod == VERB_METHOD_POST) {
            $varActualValue = $this->_arPostVars[$strThisParameter];
        }
        $intConstraintType = $objThisConstraint->GetConstraintType();
        $strConstraintOperand = $objThisConstraint->GetConstraintOperand();
        $thisFail = false;
        $objFailureObject = new constraintfailure($strThisParameter,
            $intThisMethod, $objThisConstraint);
        switch ($intConstraintType) {
        case CT_MINLENGTH:
            if (strlen((string)$varActualValue) < (integer) $strConstraintOperand) {
                $thisFail = true;
            };
            break;
        case CT_MAXLENGTH:
            if (strlen((string)$varActualValue) > (integer) $strConstraintOperand) {
                $thisFail = true;
            };
            break;
        case CT_PERMITTEDCHARACTERS:
            for ($j=0; $j<strlen($varActualValue)-1; $j++) {
                $thisChar = substr($varActualValue, $j, 1);
                if (strpos($strConstraintOperand, $thisChar) === false) {
                    $thisFail = true;
                };
            };
            break;
        case CT_NONPERMITTEDCHARACTERS:
            for ($j=0; $j<strlen($varActualValue)-1; $j++) {
                $thisChar = substr($varActualValue, $j, 1);
                if (! (strpos($strConstraintOperand, $thisChar) === false)) {
                    $thisFail = true;
                };
            };
            break;
        case CT_LESSTHAN:
            if ($varActualValue >= $strConstraintOperand) {
                $thisFail = true;
            }
            break;
        case CT_MORETHAN:
            if ($varActualValue <= $strConstraintOperand) {
                $thisFail = true;
            }
            break;
        case CT_EQUALTO:
            if ($varActualValue != $strConstraintOperand) {
                $thisFail = true;
            }
            break;
        case CT_NOTEQUALTO:
            if ($varActualValue == $strConstraintOperand) {
                $thisFail = true;
            }
            break;
        case CT_MUSTMATCHREGEXP:
            if (!preg_match($strConstraintOperand, $varActualValue)) {
                $thisFail = true;
            }
            break;
        case CT_MUSTNOTMATCHREGEXP:
            if (preg_match($strConstraintOperand, $varActualValue)) {
                $thisFail = true;
            }
            break;
        }
        if ($thisFail) {
            $anyFail = true;
            $this->_arObjConstraintFailure[] = $objFailureObject;
        }
    }

    if ($anyFail) {
        if ($this->_blRedirectOnConstraintFailure) {
            $targetURL = $_ENV["HTTP_REFERER"];
            if (!$targetURL) {
                $targetURL = $this->_strConstraintFailureDefaultRedirectTargetURL;
            }
            if ($this->_strConstraintFailureRedirectTargetURL) {
                $targetURL = $this->_strConstraintFailureRedirectTargetURL;
            }
            if ($targetURL) {
                $objToSerialize = $this;
                $strSerialization = serialize($objToSerialize);
                $strResult = setcookie ("phprqcOriginalRequestObject",
                    $strSerialization, time() + 3600, "/");
                header("Location: $targetURL");
                exit(0);
            }
        }
    }
    return(!($anyFail)); // Returns TRUE if all tests passed, otherwise returns FALSE
}
function GetConstraintFailures() {
    if (!$this->_blHasRunConstraintTests) {
        $this->TestConstraints();
    };
    return($this->_arObjConstraintFailure);
}
?>
```

请查看表 13-2 中列出的每个成员变量。这些变量均为私有，并提供了访问器方法来获取或设置其有用值。已采用匈牙利命名法——即，在变量名开头包含一个提示，指示每个成员变量应包含的数据类型。

## 表 13-2 成员变量

| 成员变量 | 作用 |
|---|---|
| `$_arGetVars` | `$_GET` 的副本，一个关联数组，包含在此请求中传递的 HTTP `GET` 变量 |
| `$_arPostVars` | `$_POST` 的副本，一个关联数组，包含在此请求中传递的 HTTP `POST` 变量 |
| `$_arCookieVars` | `$_COOKIE` 的副本，一个关联数组，包含在此请求中传递的预先存在的 Cookie |
| `$_arRequestVars` | `$_REQUEST` 的副本，一个关联数组，将 `GET` 和 `POST` 变量以及 Cookie 合并在一起。如果存在同名的 `GET`/`POST` 变量或 Cookie，优先级由 `PHP.INI` 决定。 |
| `$_objOriginalRequestObject` | 如果用户因传递了未通过约束测试的参数而被 `request` 对象重定向回原始页面，此处将包含所提供的原始请求对象的副本。 |
| `$_blIsRedirectFollowingConstraintFailure` | 布尔变量，用于确定此 `request` 是否是在约束测试失败后的重定向结果中创建的。 |
| `$_blRedirectOnConstraintFailure` | 如果约束测试失败，`request` 对象是否应自动将浏览器重定向回原始页面或其他 URL？ |

## 表 13-2（续）

| 成员变量 | 作用 |
|---|---|
| `$_strConstraintFailureRedirectTargetURL` | 如果约束测试失败且 `_blRedirectOnConstraintFailure` 设置为 true，此变量指定请求对象是否应被重定向到特定 URL。如果留空，将使用引用 URL。 |
| `$_strConstraintFailureDefaultRedirectTargetURL` | 如果未设置 `_strConstraintFailureRedirectTargetURL`，`_blRedirectOnConstraintFailure` 设置为 true，且没有可用的引用 URL，此变量指定浏览器应重定向到的 URL。 |
| `$_arObjParameterMethodConstraintHash` | 约束数组，其索引包含哈希中的三个键控组件：约束应用的参数名称；预期传递此参数的方法（作为常量）；以及表示要应用的测试的约束对象。 |
| `$_arObjConstraintFailure` | 约束失败对象数组，前提是任何约束已失败且测试已运行。 |
| `$_blHasRunConstraintTests` | 布尔变量，指示是否已在此请求对象上运行约束测试。 |

表 13-3 显示了请求对象提供的方法。

## 表 13-3 请求对象提供的方法

| 方法 | 作用 |
|---|---|
| `__construct` | 实例化请求对象。不接受任何必需参数。相反，它会查询 `$_REQUEST`、`$_POST`、`$_GET` 和 `$_COOKIE`，并根据需要填充成员变量（参见表 13-2）。此外，还会检查名为 `phpqcOriginalRequestObject` 的 Cookie 是否存在。如果存在，则假设另一个请求对象作为约束测试失败后回传的结果被传回。在此阶段会将该 Cookie 设为 null，以防在重新创建原始请求对象时出现无限循环。然后，其内容会通过 `stripslashes` PHP 函数反序列化为一个新请求对象，并通过 `GetOriginalRequestObjectFollowingConstraintFailure` 访问器方法（本表中详述）使其可供查询。 |





| Method | Role |
| :--- | :--- |
| IsRedirectFollowingConstraintFailure | 如果当前显示的页面是因约束测试失败而发出的 302 重定向自动加载的，则此方法返回 true。 |
| GetOriginalRequestObjectFollowingConstraintFailure | 如果当前显示的页面是因约束测试失败而发出的 302 重定向自动加载的，则此方法返回调用该页面时存在的请求对象，即在约束测试失败之前的请求对象。 |
| SetRedirectOnConstraintFailure | 接受 `true` 或 `false` 作为参数，此方法使您能够告知 `request` 对象在任何约束测试失败时是否应执行 302 重定向。该重定向的目标通过 `SetConstraintFailureRedirectTargetURL` 和 `SetConstraintFailureDefaultRedirectTargetURL` 方法设置。 |
| SetConstraintFailureRedirectTargetURL | 设置约束失败后 302 重定向的目标。如果未设置，则使用引用页面（通常是所需目标），如果不可用，则使用默认 URL（通过 `SetConstraintFailureDefaultRedirectTargetURL` 方法设置）。 |
| SetConstraintFailureDefaultRedirectTargetURL | 如果未使用前述访问器方法设置目标 URL，则在因约束测试失败而需要引用时，使用引用页面。如果没有可用的引用页面（例如，用户通过书签访问），则改用此方法指定的默认 URL。 |
| GetParameterValue | 返回指定参数的值。该值直接从 `$_REQUEST` 获取，因此 GET 变量、POST 变量和 COOKIE 变量的搜索优先级取决于 PHP 的整体配置。 |
| GetParameters | 返回参数哈希——本质上是 `$_REQUEST` 的直接副本 |
| GetCookies | 返回 Cookie 哈希——本质上是 `$_COOKIE` 的直接副本 |
| GetPostVariables | 返回 `POST` 变量哈希——本质上是 `$_POST` 的直接副本 |
| GetGetVariables | 返回 `GET` 变量哈希——本质上是 `$_GET` 的直接副本 |
| `AddConstraint` | 向此请求添加一个约束。约束应用于单个参数，并指定必须满足的条件，才能视为该约束已满足。<br>此方法将参数名、传递方法（作为常量 `VERB_METHOD_GET`、`VERB_METHOD_POST` 或 `VERB_METHOD_COOKIE`）和约束对象（稍后讨论）作为其参数。添加约束后，无法移除。多个约束可应用于单个参数。 |
| `TestConstraints` | 依次测试每个约束，并通过填充成员变量 `$_arObjConstraintFailure` 记录任何失败的约束，可使用 `GetConstraintFailure` 访问。如果 `$_blRedirectOnConstraintFailure` 设置为 `true`，它会首先发出一个作为当前 `request` 对象序列化表示的临时 Cookie，然后自动重定向到相应的 URL。 |
| `GetConstraintFailures` | 当对 `TestConstraints()` 的调用指示一个或多个约束失败时，此方法将返回一个 `ConstraintFailure` 对象数组，表示所有此类失败。此方法需要从原始 `request` 对象访问，该对象可使用 `GetOriginalRequestObject() FollowingConstraintFailure` 访问（如前所述，在本表中）。 |

不用担心如果表 13-3 中的理论不太清楚。本章稍后，您将找到一个实际示例，展示如何在现实世界中使用此类及其余工具包。到那时一切都会变得清晰。

现在让我们来看看 `Constraint` 类及其近亲 `ConstraintFailure` 类。

## Constraint 类

`Constraint` 类仅作为面向对象的封装器存在。它不关心测试约束是否通过所需的代码。正如您刚才所见，这是由 `request` 对象处理的。

在名为 `constraint.php` 的文件中输入以下代码：

```php
<?php
require_once("constants.php");
class constraint {
   private $_intConstraintType;
   private $_strConstraintOperand;

   function __construct($intConstraintType, $strConstraintOperand) {
       $this->_intConstraintType = $intConstraintType;
       $this->_strConstraintOperand = $strConstraintOperand;
   }

   function GetConstraintType() {
       return($this->_intConstraintType);
   }

   function GetConstraintOperand() {
       return($this->_strConstraintOperand);
   }
}
?>
```

请注意，构造函数将约束类型（从枚举为常量的约束类型中选择一个）作为其第一个参数，将操作数作为其第二个参数。操作数的含义取决于约束类型。其解释由 `request` 对象在其实现每种约束类型时决定。例如，对于 CT_MAXLENGTH 约束，操作数应包含参数的最大长度。对于 CT_PERMITTEDCHARS 约束，操作数应包含一个字符串，其中包含参数中可能存在的所有允许字符。

为适应这种灵活性，操作数是一个字符串。但是，在进行测试时，它将被转换回其最合适的本地形式。

请注意，您不会在约束对象中存储正在测试的参数名。约束只是一个条件，可以使用 `request` 对象中的方法将其应用于任何（甚至多个）参数。出于此原因，为了整齐地封装任何给定的约束失败，还必须存储引发失败的参数和传递方法。这是通过 `ConstraintFailure` 类的实例完成的。

## ConstraintFailure 类

每当特定约束失败时，都会实例化一个 `ConstraintFailure` 对象。其构造函数期望参数名、传递方法（`VERB_METHOD_GET`、`VERB_METHOD_POST` 或 `VERB_METHOD_COOKIE`）以及导致失败的原始约束对象。

在正常使用中，将使用 `GetFailedConstraintObject` 方法通过先前描述的原生 `Constraint` 类方法来确定失败的约束的性质。

查看名为 `constraintfailure.php` 的文件中的以下代码：

```php
<?php
require_once("constants.php");
require_once("constraint.php");
class constraintfailure {
    private $_strParameterName;
    private $_intVerbMethod;
    private $_objFailedConstraintObject;

    function __construct($strParameterName, $intVerbMethod,
                $objFailedConstraintObject) {
        $this->__strParameterName = $strParameterName;
        $this->__intVerbMethod = $intVerbMethod;
        $this->__objFailedConstraintObject = $objFailedConstraintObject;
    }

    function GetParameterName() {
        return($this->__strParameterName);
    }

    function GetVerbMethod() {
        return($this->__intVerbMethod);
    }

    function GetFailedConstraintObject() {
        return($this->__objFailedConstraintObject);
    }
};
?>
```

此类整齐地封装了由于用户对页面的输入未满足您的验收标准而发生的失败。

如前面的代码所示，它包含失败的参数名、传递参数的方法（GET、POST 或 Cookie）以及失败的约束（表示为约束对象）测试。

此对象的实例可以通过 `GetConstraintFailures` 方法从 `Request` 类中检索，前提是 `Request` 类已在由约束失败引起的重定向后的 302 重定向上下文中实例化。

## 使用工具包

既然您已经了解了构成工具包的基本类，那么值得看看如何在现实世界应用程序中实现它。

在本示例中，您还将看到本章前面定义的 MVC 方法的一个实际案例——即使用原生 PHP 模板。（本章稍后的“真正的模板”部分将详细介绍其工作原理。）

假设您有一个由两个页面组成的搜索引擎：用于输入搜索词的搜索页面和用于显示结果的搜索词页面。

### search.php

初始搜索控制器有以下任务：

- 加载所有必要的组件。
- 定义模板文件 (search.phtml)。





- 定义一个关联数组（`$displayHash`），用于存储由模板文件（视图）渲染的内容。
- 检查该页面是否是在约束检查失败导致的转介后到达的（而不仅仅是用户第一次请求）：
  - 如果是，设置 `$displayHash` 的一部分以指示此情况，并从当前的 `request` 对象（该对象已通过临时 cookie 提供）中检索原始失败的请求对象。
  - 从检索到的 `request` 对象中获取一个 `constraintfailure` 对象数组。
  - 遍历这些 `constraintfailure` 对象，在 `$displayHash` 中填充一个新组建的数组，其中包含每个失败的类型。
- 立即渲染模板文件（require 模板文件）。

search.php 的代码（不是 search.phtml —— 后面会讲到）如下所示：

```
<?php
require_once("constants.php");
require_once("request.php");
require_once("constraint.php");
require_once("constraintfailure.php");

$strTemplateFile = "search.phtml";

$displayHash = Array();

$objRequest = new request();
$blHadProblems = ($objRequest->IsRedirectFollowingConstraintFailure());

$displayHash["HADPROBLEMS"] = $blHadProblems;

if ($blHadProblems) {
$objFailingRequest =
$objRequest->GetOriginalRequestObjectFollowingConstraintFailure();
$arConstraintFailures = $objRequest->GetConstraintFailures();
$displayHash["PROBLEMS"] = Array();
for ($i=0; $i<sizeof($arConstraintFailures)-1; $i++) {
$objThisConstraintFailure = &$arConstraintFailures[$i];
$objThisFailingConstraintObject =
$objThisConstraintFailure->GetFailedConstraintObject();
$intTypeOfFailure = $objThisFailingConstraintObject->GetConstraintType();
switch ($intTypeOfFailure) {
case CT_MINLENGTH:
$displayHash["PROBLEMS"][] = "Your search term was too short.";
break;
case CT_MAXLENGTH:
$displayHash["PROBLEMS"][] = "Your search term was too long.";
break;
case CT_PERMITTEDCHARACTERS:
$displayHash["PROBLEMS"][] = "Your search term contained characters
I didn't understand.";
break;
};
};
};
require_once($strTemplateFile);
exit(0);
?>
```

请注意末尾的 exit 语句。虽然这并非绝对必要，但它可以防止你在模板获取控制权后意外编写代码。

现在让我们来看看模板本身。

## search.phtml

模板的唯一职责是智能地渲染 `$displayHash` 的内容，并添加合适的周围 HTML。请注意，你不需要将 `$displayHash` 声明为全局变量。require 模板的操作会将其粘附到原始脚本的末尾。PHP 解释器在执行时将其视为一个单一脚本。

在此特定模板中，除了渲染创建搜索表单所需的简单 HTML 外，你还必须渲染因刚刚发生的搜索失败而生成的任何错误消息。

值得注意的是，以下 HTML 非常非常简单——绝非使用了所有最新 CSS 的精美语义 XHTML。希望你已经意识到，这仅仅是为了示例的清晰度。在你自己的应用程序中，模板无疑会大得多且更加复杂。

将以下内容另存为 `search.phtml`（而不是已经创建的 `search.php`）：

```
<html>
<head>
<title>Ed's Search Page</title>
</head>
<body>
<H1>Ed's Search Page</H1>
<hr>
You can search for types of steak here.
<BR><BR>
<? if ($displayHash["HADPROBLEMS"]) { ?><BR>
<B>Sorry, there <?=(sizeof($displayHash["PROBLEMS"]) > 1) ? "were problems" : "was a problem"?> with your search!</B>
<? for ($i=0; $i<sizeof($displayHash["PROBLEMS"])-1; $i++) { ?>
<?=$displayHash["PROBLEMS"][$i]?>
<? } ?>
<? } ?>
<FORM METHOD="POST" ACTION="searchresults.php">
<TABLE BORDER="0">
</TR>
            <TD>Type of Steak</TD>
            <TD><INPUT TYPE="TEXT" NAME="typeOfSteak"></TD>
        </TR>
        </TABLE><BR>
        <INPUT TYPE="SUBMIT">
        </FORM>

        </body>
        </html>
```

请注意 PHP 有多简单，其中包含非常基本的语句，例如 `if` 和 `for`。原则上，如果你在模板文件中编写的代码复杂度更高，那么它很可能位置不对，应该放在控制器页面（`.php`）或某个类（`.php`）中。

本章后面你将了解在模板中使用这些简单语句的一种替代方法，一种根本不使用 PHP 的方法：`true templating`。

如果在浏览器中运行 `search.php`，你应该会看到它成功渲染了标准搜索表单，如图 13-2 所示。

![](img/a1b732997d9cb194dceec0570dc79710_335_0.png)

图 13-2 search.php 的标准搜索表单

显然，搜索页面需要一个目标。这是通过两个不同的文件提供的：控制器和模板。

## searchresults.php

搜索结果页面将是搜索页面的直接目标，其任务是判断其输入是否可接受。

它的任务*不是*告知用户输入不可接受。相反，用户将通过 302 HTTP 重定向被*返回*到原始搜索页面，然后由该页面说明不足之处。

> 请勿直接在 Web 浏览器中运行此代码。它期望从搜索页面调用。

以下示例中适用的条件与传递给脚本的唯一搜索参数有关——即用户提供的搜索字符串。它必须包含 4 到 11 个字符，且必须是字母，而不是数字：

```
<?
require_once("constants.php");
require_once("request.php");
require_once("constraint.php");
require_once("constraintfailure.php");

$strTemplateFile = "searchresults.phtml";

$displayHash = Array();
session_start();

if ($_POST) {
    $objRequest = new request();
    $objRequest->SetRedirectOnConstraintFailure(true);

    $objConstraint = new constraint(CT_MINLENGTH, "3");
    $objRequest->AddConstraint("typeofSteak", VERB_METHOD_POST, $objConstraint);
    $objConstraint = new constraint(CT_MAXLENGTH, "12");
    $objRequest->AddConstraint("typeofSteak", VERB_METHOD_POST, $objConstraint);
    $objConstraint = new constraint(CT_PERMITTEDCHARACTERS,
    "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz");
    $objRequest->AddConstraint("typeofSteak", VERB_METHOD_POST, $objConstraint);

    $objRequest->SetConstraintFailureDefaultRedirectURL("/search.php");
    $objRequest->TestConstraints();

    # If we've got this far, tests have been passed - perform the search.
    $displayHash["RESULTS"] = Array();
    $arSteaks = array("fillet", "rump", "sirloin", "burnt");

    for ($i=0; $i<sizeof($arSteaks)-1; $i++) {
        if (! (strpos (trim(strtolower ($arSteaks[$i])),
        strtolower (trim($objRequest->GetParameterValue("typeofSteak")))))
        == false) {
            array_push($displayHash["RESULTS"], $arSteaks[$i]);
        }
    };

    $_SESSION['dh'] = $displayHash;
    header("Location: searchresults.php");
    exit(0);
}
} else {
    $displayHash = $_SESSION['dh'];
    require_once($strTemplateFile);
    exit(0);
};
?>
```

请注意，$displayHash 模板内容变量在 request 对象重新实例化时再次被定义。

首先，控制器测试它是否是因 HTTP POST 调用的。如果是，则对输入的每个约束都定义为 constraint 对象的一个新实例。然后使用 AddConstraint 添加它，指定传递方法（在此示例中为 POST）和参数名作为额外操作数。

为了消除引荐页面必须可用的需求，你需要指定一个默认 URL（即原始搜索页面）。如果你正在尝试此示例，则需要相应调整本章脚本的路径。

随后调用一个方法：TestConstraints()。这将执行验证你所表达的所有约束是否已满足所需的测试。如果有任一约束未满足，则它会被添加到该 request 对象中包含的约束失败数组中。

在这些测试结束时，如果任何测试导致失败，则该 request 对象获授权强制用户返回搜索页面，这是由使用 SetRedirectOnConstraintFailure() 导致的。首先，它将此页面上 request 对象的当前状态序列化为一个快照，然后将其作为 cookie 推送到浏览器。当用户返回搜索页面时，该 cookie 将由 request 对象解析以确定出了什么问题。

如果发生重定向，则根本不会显示模板。结果，用户根本不会意识到他们已经访问了第二个页面。这改善了用户体验。用户不会感觉自己已经“离开”了原始搜索页面。因此，他们会立即意识到有什么不对劲。

假设测试通过，搜索可以继续。在示例中，请注意搜索机制非常简单。在现实场景中，无疑会使用外部类来执行搜索。

在搜索结果变量填充后，它会暂时存储在会话中。然后发出重定向以使用 HTTP GET 重新加载页面。重新加载时，可以通过从会话中恢复 display hash 的值来显示模板。请注意，重新加载时不会执行验证和搜索，因为 `if ($_POST)` 条件求值为 false。





## searchresults.phtml

以下搜索结果模板极其简单。它仅显示搜索结果。示例中未提供显示“你的搜索未产生任何结果”消息的功能。但是，实现这样一条消息相对简单。

```
<html>
<head>
<title>Ed's Search Page</title>
</head>
<body>
<H1>Search Results</H1>
<hr>
Here are the results of your search.
<UL>
<? for ($i=0; $i<=sizeof($displayHash["RESULTS"])-1; $i++) { ?>
<LI><?=$displayHash["RESULTS"][$i]?><LI>
<? } ?>
</UL>
<? ?>
</body>
</html>
```

## 试一试！

假设你已输入前四个文件的代码，可以再次打开搜索页面（search.php）（如前所述）并输入一些搜索词。

首先，尝试一个应该可以正常工作的示例。将 fil 作为搜索词输入，然后单击提交查询按钮。这应该会将 fillet 作为搜索结果返回，如图 13-3 所示。

![](img/a1b732997d9cb194dceec0570dc79710_338_0.png)

图 13-3 将“fillet”作为搜索结果返回

如果上述操作正常，那么是时候尝试该工具包的真正用途了：处理提供错误输入时的情况。尝试将 fi 作为搜索词提供。它只有两个字符长度，因此应该会失败，如图 13-4 所示。

![](img/a1b732997d9cb194dceec0570dc79710_339_0.png)

图 13-4 输入搜索词失败的尝试

如你所见，你会立即被重定向回搜索页面，并显示一条错误消息。

searchresults.php 对你的搜索参数运行了三个约束测试，其中有一个失败了。那一次失败导致弹回搜索页面，但在此之前，已对你生成的请求对象进行了快照序列化。

在将你重定向回原页面之前，该快照会作为 Cookie 立即发送到你的浏览器。随后，搜索页面检测到该 Cookie 的存在，并知道你因失败而被重定向回它。接着，它会读取嵌入在该对象中的约束失败信息，并一次显示一条给你。

尝试输入一个过长的字符串（myfavoritesteak）或包含无效字符的词（例如 11431），你将看到类似的失败消息。输入类似 my 1st choice 的内容（违反多个约束），你应该会受到两次批评。

## 关于 PRG 的一句话

在继续之前，值得花点时间探索一下你在之前的示例中未曾意识到已实现的东西——一种名为 post-redirect-get（PRG，即“POST-重定向-GET”）的设计模式。

在原始 HTTP 协议中，HTTP GET 旨在显示页面内容或信息，而 HTTP POST 旨在执行某些操作（尤其是修改数据的操作）。因此，几乎所有 <form> 实现都会使用 HTTP POST。仅用于处理简单逻辑（如分页）的表单才会使用 GET。作为经验法则，任何更改远程主机数据或需要进行大量处理的操作都应使用 HTTP POST。

不过，HTTP GET 和 HTTP POST 都可以以完全相同的方式向 Web 浏览器发送输出。HTTP POST 导致向 Web 浏览器发送输出是完全可行的——但如果你在这样的页面上单击刷新（或按 F5）会发生什么呢？图 13-5 正好说明了这一点。

![](img/a1b732997d9cb194dceec0570dc79710_340_0.png)

图 13-5 尝试刷新页面时出现的错误消息

图 13-5 所示的对话框非常烦人，但它的存在是为了保护用户免受自身操作的影响。谁能说如果页面被重新提交会发生什么？如果这是“添加到购物车”页面，商品可能会被添加到购物车多次。如果这是“支付订单”页面，订单可能会被支付多次。

使用 PRG，该对话框永远不会出现。每个 HTTP POST（无论多么微不足道）都会导致随后的 HTTP GET，通过 302 重定向发起——在实践中，这通常通过 PHP 中的 header() 函数实现。这会指示浏览器请求不同的页面，而不是呈现任何输出。你可以将页面的输出暂时存储在会话中，或者在紧急情况下甚至存储在客户端 Cookie 中。不要将其呈现到浏览器，因为发送哪怕一个字节的 HTML 都会使重定向变得不可能。

整个过程对最终用户几乎不可见，但这意味着，如果用户在 HTTP POST 之后刷新页面，用户刷新的实际上是随后的 HTTP GET，而不是 POST 本身。这个 GET 应该是无害的。它应该以平实的方式简单呈现输出。因此，刷新并无大碍。

有关此内容的更多信息，请使用 Google 搜索“post-redirect-get”，或访问 http://en.wikipedia.org/wiki/Post/Redirect/Get。

## 实际应用中的工具包

到本章为止，你已经构建了一个微型工具包，使你能够在使用 MVC 设计模式开发项目时轻松处理请求和约束。你还学习了一种在原生 PHP 中使用模板的简单方法。

你在此创建的请求对象中的内置约束相对简单，而且坦白说，在控制页面中使用原生 PHP 也可以很容易地实现它们。约束在变得复杂时才真正发挥作用，例如当需要查询数据源以确定有效性时。在这种情况下，将请求对象“泛型化”然后扩展它以形成多个请求对象（可能每个页面一个）来处理不同的约束范围可能是有意义的。

本章稍后，你将了解 Smarty——一种完全不同的模板处理方式。

## 真正的模板处理

你现在已经接触了“原生”PHP 模板，但什么是“真正的”模板，它又有何不同？

### 原生 PHP 模板回顾

本章前面部分让你熟悉了 MVC 的概念。到现在，你应该意识到，在处理大型 PHP 项目时，使用某种形式的模板是有道理的。

到目前为止，你所看到的所有模板处理都围绕着一个原则：填充一个多维内容哈希，然后使用简单的 PHP 语句（如 `if`、`for`、`while` 或其他）将 HTML（或其他标记语言）注入该内容中。

然而，要求你在模板中自律且仅使用某些 PHP 关键字这一事实本身，就指出了这种方法中非常明显的陷阱。任何依赖自律而非强制执行硬性规则的事物都容易被滥用。

### 原生模板处理的陷阱

第一个也是最明显的问题是，你正在使用一种非常强大的语言（PHP）来完成一项非常简单的工作（输出内容）。不过，问题并非性能问题。简单来说，使用 PHP 来处理内容呈现，就给你的项目引入了另一个可能出错的点。

想想你在编写大型类时遇到的常见问题——拼写错误、变量名拼写错误，或是在高度嵌套的 `for` 循环中意外重复使用计数器变量。如果你也将 PHP 用于模板处理，所有这些问题都同样会存在。

第二个（或许更严重）的问题在考虑大型项目时会变得显而易见。在 PHP 项目中使用 MVC 的一个巨大优势是，视图（即所需的任何模板）可以委派给精通设计和 HTML 的开发人员，而他们可能不太精通 PHP。这使得相对昂贵的软件架构师和工程师可以专注于驱动项目模型的繁重 PHP 工作，而较便宜的 Web 开发人员则可以专注于界面。

生成有效、语义化且可访问的 XHTML/CSS 本身正在迅速成为一门艺术，因此这不仅在经济和商业上合情合理，还能让个人发挥各自的长处。很少有 PHP 大师对 IE6 怪异模式的细微差别有百科全书式的了解。

但是，如果你选择使用 PHP 模板，Web 开发人员别无选择，只能用 PHP 编写。坦白说，他们需要了解的 PHP 不多。这类 PHP 很容易列入速查表。问题不在于学习曲线，而在于危险性。毕竟，PHP 不会限制 Web 开发人员在模板中可以或不可以使用的内容。相反，他们必须自我约束。无限循环、危险的系统调用以及其他潜在的严重错误，都只差一个微小的拼写错误。

如果有办法能让 Web 开发人员使用任意语言中的灵活标签来呈现页面输出，而不是使用 PHP，那么这个问题就可以轻松解决。Smarty 正是这样一个解决方案。





## 基于 Smarty 模板的真正模板化

Smarty 是一个 PHP 包，使开发人员能够轻松为模板准备输出，然后让模板自行以其认为合适的方式显示它。

Smarty 独特之处在于，它不仅提供简单的“转储值”方法论，还允许循环、条件语句和多维数组的遍历。简而言之，它复制了原生 PHP 模板化中使用的所有传统简单 PHP 方法，且完全不使用 PHP。

Smarty 的另一个巨大优势是其速度。信不信由你，它实际上通过从模板创建原生 PHP 来工作。然后会缓存该原生 PHP，因此如果后续请求中模板未更改，模板本身就不必再次翻译成 PHP。它直接从缓存中提取并执行。在那次初始执行之后，根本没有速度损失。

## 安装 Smarty

安装 Smarty 非常直接。但是，与许多其他模板引擎不同，它不是传统的 PEAR 包，因此您需要手动下载和安装。

目前，Smarty 位于 www.smarty.net。

以下说明假设您运行的是 Mac OS X、UNIX 或 Linux。如果您运行的是 Windows，说明可在 http://smarty.incutio.com/?page=SmartyInstallationWindows 上找到。下载后，请解压：

```
root@linuxvm:~# tar -xzvf Smarty-2.6.2.tar.gz
Smarty-2.6.2/
Smarty-2.6.2/COPYING.lib
Smarty-2.6.2/.cvsignore
Smarty-2.6.2/BUGS
Smarty-2.6.2/Demo/
Smarty-2.6.2/demo/
...
Smarty-2.6.2/misc/smarty_icon.README
Smarty-2.6.2/misc/smarty_icon.gif
root@linuxvm:~#
```

接下来，您必须将 Smarty 提供的库移动到 PHP 可以看到的位置。通常，您只需将 libs/ 子文件夹的全部内容复制到 /usr/local/lib/php，如下所示：

```
root@linuxvm:~/Smarty-2.6.2# cp -r libs/ /usr/local/lib/php
```

接下来，您必须将应用程序连接到 Smarty 以使用它。在应用程序中将使用 Smarty 的 PHP 文件正下方，您必须创建名为 templates、templates_c、cache 和 configs 的目录：

```
root@linuxvm:~# cd public_html/tests/prophp6/mvc/
root@linuxvm:~/public_html/tests/prophp6/mvc# mkdir templates_c
root@linuxvm:~/public_html/tests/prophp6/mvc# mkdir configs
root@linuxvm:~/public_html/tests/prophp6/mvc# mkdir templates
root@linuxvm:~/public_html/tests/prophp6/mvc# mkdir cache
```

幸运的是，Smarty 理解现实世界项目的需求，在这些项目中，诸如此类的配置步骤可能并非总是可行（例如，当您的 PHP 脚本位于多个目录中时）。您也可以在 PHP 代码中手动指定这些文件夹的位置。您将在本章后面学习如何操作。

接下来，您需要为这两个文件夹设置一些权限：template_c 和 cache。将这些文件夹的所有权设置为 Web 服务器的用户名。在大多数情况下，这是 nobody 用户，但也可能是 apache 或其他用户。如果您不确定，可以通过发出以下命令来检查：

```
ps auxw | grep httpd | grep -v grep | awk '{print $1}' | tail -1
```

这里重要的是，该用户及其所属组可以自由读写这些文件夹。按如下方式设置权限：

```
chown nobody.users ./cache
chown nobody.users ./template_c
chmod 770 ./cache
chmod 770 ./template_c
```

模式 770 表示这些文件夹的所有者可以读取、写入和执行内容，而其他任何人都不能。如果这让您困扰，且您无法在此机器上成为 root，则可以改用 775，这允许其他人读取和写入访问。然而，您完全有理由认为这是一个安全风险。

## 使用 Smarty

典型的 Smarty 实现由一个以 .php 结尾的控制器（与之前类似）以及一个代表视图的模板文件（此次以 .tpl 结尾）组成。

### smartytest.php

请看下面这个非常简单的示例：

```
<?
require('Smarty.class.php');

$objSmarty = new Smarty;
$strTemplate = "smartytest.tpl";

$objSmarty->assign("test_variable", "This is the value of my test variable");

$objSmarty->display($strTemplate);
?>
```

您还必须为该脚本输入模板代码，该代码必须位于您在下面创建的名为 template 的文件夹中。

### smartytext.tpl

请看下面的代码：

```
<html>
<head>
<title>Untitled</title>
</head>

<body>
This is my template!<BR>
The value of the variable is: {$test_variable}

</body>
</html>
```

您可能已经猜到，运行 smartytest.php（进而调用输出模板 smartytest.tpl）的输出类似于以下内容：

```
This is my template!
The value of the variable is: This is the value of my test variable
```

如您所见，您已向 Smarty 模板对象分配了名为 test_variable 的变量，其输出已通过在模板本身中使用语法{$test_variable}成功呈现。

这足够简单，但您如何表达数组、有条件地显示内容，并利用前面讨论过的原生 PHP 模板化中传统可用的所有功能呢？

### Smarty 中的线性数组

将线性数组推送到 Smarty 然后递归其内容相对简单。请考虑 PHP 控制脚本中的以下代码：

```
$objSmarty->assign("FirstName",array("John", "Mary", "James", "Henry"));
```

如您所见，您可以以与分配普通字符串完全相同的方式向 Smarty 模板对象分配 PHP 变量。要呈现它，您通常使用等效于 for 循环的 Smarty 结构，如下所示：

```
{section name=x loop=$FirstName}
{$FirstName[x]}<BR>
{/section}
```

输出相当可预测：

```
John
Mary
James
Henry
```

### Smarty 中的关联数组

您可以以与处理线性数组非常相似的方式处理关联数组（哈希）。请考虑向 Smarty 模板提供数据的以下控制代码：

```php
$arHash["Name"] = "Ed";
$arHash["Age"] = 27;
$arHash["Location"] = "London";
$objSmarty->assign("Writer", $arHash);
```

同样，分配的方法看起来非常相似。以下展示了如何现在在模板中呈现输出：

```
The author of this chapter is ({$Writer.Name}), ({$Writer.Age}) years of age,
currently residing in ({$Writer.Location}).
```

请注意简单语法 ({$X.Y})，其中 X 是 Smarty 变量的名称，Y 是分配给它的哈希中的键。这将产生以下输出：

```
The author of this chapter is Ed, 27 years of age, currently residing in London.
```

### Smarty 中的条件语句

如果您希望仅在满足特定条件时才显示内容，该怎么办？在显示错误消息时，这对您尤其有用。您只希望在确定发生错误时才显示错误。

您按如下方式在控制器中分配变量：

```php
$objSmarty->assign("isError", 1);
$objSmarty->assign("ErrorText", "You did not specify a search term.");
```

以下模板逻辑可以支持此功能：

```
{if $isError == 1}
The following error occurred: {$ErrorText}
{/if}
```

如您所见，条件表达式与您在 PHP 中用于执行测试的表达式非常相似。如果 isError 设置为 1，这将仅呈现介绍性文本和错误本身：

```
The following error occurred: You did not specify a search term.
```

为了验证这一点，请将控制器中 isError 的分配更改为 0。输出根本不会呈现。

不过，这有点麻烦。在原生 PHP 模板化中，您可能只需检查是否已定义错误消息。在 Smarty 中也可以这样做：

```
{if $ErrorText}
The following error occurred: {$ErrorText}
{/if}
```





这完全消除了明确告知 Smarty 是否存在错误的必要。它可以通过查看条件中的非空值来自行判断。

## 使用 Smarty 重写 search.php

现在你可以用稍微复杂一点的例子将这些技能付诸实践。使用 Smarty，你可以非常轻松地重写本章第一部分中的 search.php 和 search.phtml 对。

查看 search.php 中你正在创建的内容，以便知道你需要使用 Smarty 复现什么。目前，当内容到达 search.phtml 时，$displayHash 变量可能包含以下内容：

- HADPROBLEMS —— 一个真/假变量，同样，你可以将其表示为 Smarty 中的普通变量

- PROBLEMS —— 一个字符串数组，每个字符串都是一个已经遇到的问题，仅在 HADPROBLEMS 设置为 true 时才会被输出

快速修改 search.php，使其如下所示。阴影区域表示从原始版本修改或添加的代码：

```php
require_once("constants.php");
require_once("request.php");
require_once("constraint.php");
require_once("constraintfailure.php");
```

```php
$strTemplateFile = "s_search.tpl";
require("Smarty.class.php");
$objSmarty = new Smarty;
```

```php
$objRequest = new request();
$blHadProblems = ($objRequest->IsRedirectFollowingConstraintFailure());
```

```php
if ($blHadProblems) {
$objSmarty->assign("HADPROBLEMS", "true");
};
```

```php
if ($blHadProblems) {
$objFailingRequest =
$objRequest->GetOriginalRequestObjectFollowingConstraintFailure();
$arConstraintFailures = $objFailingRequest->GetConstraintFailures();
$problemArray = Array();
for ($i=0; $i<sizeof($arConstraintFailures)-1; $i++) {
$objThisConstraintFailure = &$arConstraintFailures[$i];
$objThisFailingConstraintObject =
$objThisConstraintFailure->GetFailedConstraintObject();
$intTypeOfFailure = $objThisFailingConstraintObject->GetConstraintType();
switch ($intTypeOfFailure) {
case CT_MINLENGTH:
$problemArray[] = "Your search term was too short.";
break;
case CT_MAXLENGTH:
$problemArray[] = "Your search term was too long.";
break;
case CT_PERMITTEDCHARACTERS:
$problemArray[] = "Your search term contained characters I
didn't understand.";
break;
}
```

```php
if ($problemArray) {
$objSmarty->assign("PROBLEMS", $problemArray);
}
$objSmarty->display($strTemplateFile);
```

在 templates 子文件夹中创建一个名为 s_search.tpl 的相应模板文件：

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
<title>Ed's Search Page</title>
</head>
<body>
<H1>Ed's Search Page</H1>
<hr>
You can search for types of steak here.
<BR><BR>
{if $HADPROBLEMS}
<B>Sorry, there were problems with your search!</B>
{section name=x loop=$PROBLEMS}
({$PROBLEMS[x]})
{/section}
{/if}
<FORM METHOD="GET" ACTION="searchresults.php">
<TABLE BORDER="0">
<TR>
<TD>Type of Steak</TD>
<TD><INPUT TYPE="TEXT" NAME="typeOfSteak"></TD>
</TR>
</TABLE><BR>
<INPUT TYPE="SUBMIT">
</FORM>
</body>
</html>
```

运行修改后的 search.php 并尝试像之前一样生成错误。你会发现，在接收到此类错误时，输出几乎完全相同，因此模板转换已取得圆满成功。

然而，还有一个小问题。如果你只生成一个错误，你仍然会收到一条消息，指出你的搜索“存在问题”，而不是“存在一个问题”。

在原生的 .PHTML 原生 PHP 模板中，你使用以下代码处理了这个问题：

```php
<B>Sorry, there
<?= (sizeof($displayHash["PROBLEMS"]) > 1) ? "were problems" : "was a problem") ?>
with your search!</B>
```

幸运的是，你也可以在 Smarty 中处理这个问题。你只需要测量数组的大小并相应调整输出，就像在原生 PHP 中做的那样：

```smarty
<B>Sorry, there {if $PROBLEMS[1]}were problems{else}was a problem{/if}
with your search!</B>
```

然而，这里有些小小的作弊行为。在 Smarty 中，没有不调用 PHP 代码的方法来测量数组的大小，因此代码只是检查数组中是否存在第二个元素。如果存在，用户将看到复数文本。否则，用户将看到单数文本。

如果你修改模板以使用这段新代码，你应该会发现脚本的输出现在与你在本章前半部分使用原生 PHP 模板时完全相同。当然，你也可以使用相同的技术重写 searchresults.php 和 searchresults.phtml。为什么不现在就试试呢？

## 高级 Smarty

既然你已经熟悉了 Smarty 的基本用法，那么值得更详细地了解它提供的一些更高级功能。

### 运行时配置

如本节开头所述，你可能会发现自己面临以下情况：在每个存放 .php 文件的位置下创建子文件夹是不希望的。幸运的是，Smarty 允许你在运行时指定这些位置：

```php
$smarty->template_dir = '/web/www.mydomain.com/smarty/guestbook/templates/';
$smarty->compile_dir = '/web/www.mydomain.com/smarty/guestbook/templates_c/';
$smarty->config_dir = '/web/www.mydomain.com/smarty/guestbook/configs/';
$smarty->cache_dir = '/web/www.mydomain.com/smarty/guestbook/cache/';
```

### 多维数组

多维数组可以以与其一维对照物（无论是关联数组、线性数组还是混合数组）大致相同的方式处理：

```php
$multiArray = Array(Array("x","o","x"),Array("o","x","x"),
Array("o","o","x")); $objSmarty->assign("TicTacToeBoard", $multiArray);
```

将其绑定到以下模板：

```smarty
<TABLE BORDER="1">
{section name=y loop=$TicTacToeBoard}
<TR>
{section name=x loop=$TicTacToeBoard[y]}
<TD>{$TicTacToeBoard[y][x]}</TD>
{/section}
</TR>
{/section}
</TABLE>
```

这就是预期的、熟悉的井字棋棋盘，X 从左到右对角线获胜。

### 变量修饰符

模板设计师可以使用变量修饰符对收到的变量进行非常简单的修改：

```php
$smarty->assign('bookTitle', "Professional PHP5");
```

将其与以下模板代码配对：

```smarty
{$bookTitle|replace:"PHP5":"PHP6"}
```

输出非常符合预期。

### 函数

Smarty 在其语言中定义了一些函数。它认为有些是内置的——也就是说，无法修改或覆盖。Smarty 中提供的函数其实更好地描述为方法，因为它们通常不对输入执行任何操作，这与你刚刚遇到的修饰符不同（例如 replace，它在呈现前会更改其输入）。

一个非常有用的例子是 strip 函数，它使你能够整齐地排列带有正确制表符和间距的 HTML，并确信任何多余的空格在发送到浏览器之前都会被剔除。这使得模板非常易于维护：

```smarty
{strip}
<table border="0">
<tr>
<td>
Here is some content.
</td>
</tr>
</table>
{/strip}
```

对于人类来说，这要容易阅读得多。然而，当 HTML 发送到浏览器时，它在幕后的样子远不如它对用户的显示方式重要。{strip} 标签会为你移除任何可能干扰输出的空白：

```html
<table border="0"><tr><td>Here is some content.</td></tr></table>
```

### 捕获输出

有时，你可能不想简单地将解析后的模板输出直接吐到屏幕，而是想将其捕获到变量中。例如，如果你想使用 Smarty 渲染 XML 内容，然后将其通过 XSL 样式表来实际呈现到 Web 浏览器，这将特别有用。或者，你可能根本不想传递渲染后的内容。例如，你可能正在发送 HTML 电子邮件。在这里，Smarty 非常有用，正如你在第 11 章中可能发现的那样：

```php
// capture the output
$strOutput = $objSmarty->fetch("index.tpl");
```

只需将渲染后的模板输出 HTML 赋值给变量 $strOutput，然后你就可以对其做任何你想做的事情。

### 包含其他模板

Smarty 甚至允许你包含其他模板，这些模板将以正常方式解析。你可以使用此功能在页面中添加常见的页眉和页脚：

```smarty
{include file="header.tpl"}
```

### 进一步阅读

Smarty 的功能非常强大，远超本章的范围。然而，在接触了一些标准用法示例后，你现在应该已经具备足够的能力去探索其更多功能。

明显的起点是 Smarty 参考网站 www.smarty.net/manual/en/。所有修饰符、函数，甚至晦涩的配置参数都在此处完整记录。方便的是，文档分为两个部分，分别面向程序员（编写 PHP 的人）和 HTML 模板开发人员。

### 何时使用 Smarty 而非传统模板

决定使用 Smarty 而不是传统的原生 PHP 模板不应轻率对待。虽然 Smarty 显然是简单模板的绝佳工具，但其功能仍只是大型项目可能所需功能的一个子集。

尽管它可以通过使用 {php} 和 {/php} 标签与原生 PHP 扩展，但这样做从一开始就违背了使用安全模板的初衷。事实上，Smarty 自己的网站表示，“将 PHP 代码嵌入模板中是强烈不建议的。”

与你在项目中合作的其他开发人员的技能和经验很可能是决定性因素。如果你是项目中唯一的工程师，使用原生模板几乎肯定更好。反之，如果项目需要许多设计师和 HTML 专家处理你脚本的输出，Smarty 模板则是一个更安全的选择，因为它允许这些人按照自己的意愿操作你应用程序的显示逻辑，而无需触碰其背后的 PHP 代码。





## 一点建模工作

迄今，本章已考察了控制器（处理用户在网站上的旅程及其所有相关逻辑的部分）和视图（前端处理输出数据显示和输入数据捕获的部分）；但你尚未详细考察模型。

这是一个有意识的决定。模型是真正独立于你选择的控制器实现或模板系统的部分。这无关紧要；它不应该改变。你的模型应由一套可重用、模块化的类组成——这些智能的构建块可以根据需要随时插入或移出你的项目。

在第 7 章中，你了解到构成应用程序模型的类大致可分为实用工具类（执行诸如发送电子邮件、处理外部数据提供程序等有用操作的类）和业务对象（代表应用程序中有用实体的类，如订单、客户、产品等）。

命名上的差异颇具启示性：实用工具类和业务对象。作为经验法则，实用工具类从不实例化。它是静态使用的，因为按其定义，一个实例与另一个实例之间不应该有任何区别。相反，业务对象几乎总是被实例化（尽管它可能具有静态方法），因为通常在底层数据源中记录了一个或多个实例。换句话说，你的应用程序通常会有许多 "用户"，但只有一个 "电子邮件发送设施"。

本章前面你学到，如果 MVC 分离做得恰到好处，理论上你可以将业务类和实用工具类放入完全不同的应用程序中——甚至不是基于 Web 的应用程序——它们仍然可以工作。碰巧的是，你可能想这样做有一个充分的理由，它就叫做单元测试。

## 单元测试简介

确保组件精确地按你想要的方式运行是应用程序开发的重要步骤。正如你在本书其他部分已学到的，在将组件集成到更大的应用程序之前，对其进行测试至关重要。始终围绕核心组件编写应用程序。永远不要围绕你的应用程序编写核心组件。

对于稍微复杂一些的类（甚至是多个类的层次结构），制定合适的测试策略可能看起来相当棘手。通过 var_dump() 输出大块数据或使用错误日志的诱惑可能难以抗拒，但你应该抵制，因为使用预先编写的单元测试框架可以节省大量时间。不仅如此，连贯、彻底且专业的测试方法是你可以主动向客户（或老板）展示的东西，而有数百个 error_log() 语句则不是。

下面是一个快速检查清单。以下方法是否让你觉得眼熟？

- 1. 编写类。
- 2. 编写一个简短的测试脚本，它 `requires` 该类，实例化它，调用一些方法，并输出一些结果。
- 3. 运行脚本。
- 4. 将脚本的输出与你预期的（在你脑海中）进行核对。
- 5. 如果输出看起来良好，则继续。否则，调整类并重复步骤 3 和 4，直到输出似乎正常工作。
- 6. 可能在许多周之后，将组件集成到主应用程序中。

这听起来几乎滑稽，但这种过程实际上比你想象的更普遍。以这种方式进行组件测试的问题在于它既不彻底也不系统。换句话说，你不仅可能只测试了组件的一小部分，而且花费的时间也比真正需要的要长。此外，如果你确实发现了问题，你的简短测试脚本在追踪问题时帮助不大。你每次测试都必须决定测试是否成功。

幸运的是，还有另一种方法。修改组件测试工作流，使其更像这样：

- 1. 设计类的接口（但不是实现）。
- 2. 为（空）类创建测试套件，并检查测试是否通过。
- 3. 编写类的实现。
- 4. 再次运行测试套件。
- 5. 修复导致意外结果的任何错误，然后返回步骤 4。
- 6. 将组件集成到其他应用程序中。

接下来，你将更详细地查看这些步骤，以发现“测试套件”究竟指什么。测试用例的概念将在本章稍后介绍。

## 设计类的接口

首先，让我们回顾一些面向对象编程（OOP）原则。在 OOP 设计中，通常认为对象层次结构中最重要的部分是接口，最不重要的部分是实现。

这可能听起来很奇怪，但请这样想。如果你正在设计一个用户类，你脑海中实际上在想什么？

> "我需要 username、first name、last name 和 encrypted password 属性，还需要方法来告诉我的应用程序该用户属于哪些安全组，以及一个方法来计算距离上次登录过去了多久，以及……"

你甚至没有意识到自己很聪明。你在向自己列举对象的方法和成员变量。这就是对象建模的业务分析。你并不是试图计算距离用户上次登录过去了多久。事实上，可能有不止一种方法来做这件事。这其实不重要。无论你采用哪种方式，都不会影响你的接口。

事实上，你的应用程序类套件的接口是主观的。也就是说，将纸质规格转换为带有方法和成员变量的类层次结构需要一定的分析技能。相反，使这些方法按承诺的方式工作是客观的。它要么按预期工作，要么不工作。作为 PHP 专业人员，你可能更希望有一名初级软件工程师（如果你有幸手下有这样的人）来处理这些细节，以便你可以在顶层做出重大决策。

以单元测试友好型工作流的方式来处理这个问题很简单。在类的第一个草稿中，将所有方法完全留空。在开闭花括号之间只使用空白。你将在本章稍后详细了解这一点。

## 为你的类创建测试套件

有了要测试的骨架类，继续创建你的测试套件并不是个坏主意。现在，你将学习理论。使用特定测试框架实现这一点的具体细节将在本章稍后介绍。

测试套件的功能是为测试你的类提供一个简单的黑盒解决方案。当被调用时，它直接钩入你的类的重要功能，执行一系列测试，然后说明这些测试是否成功。它真是一个开箱即用的工具。

理解这些测试的性质很重要。你通过扩展所谓的测试用例类来实现测试套件。这作为你选择使用的单元测试框架的一部分提供（在此情况下，是 PHPUnit，它将在本章稍后详细介绍）。你必须小心处理扩展类中的某些管理细节（主要涉及指导测试单元如何实例化和销毁测试类）；之后，就由你来为测试类中的每个实际方法提供测试方法。

测试方法必须按照单元测试框架的要求命名，以便它知道作为测试套件运行时行为的一部分执行它们。它们负责测试测试类的核心功能。

每个测试方法都遵循相同的基本模式：

- 1. 确定测试类方法的某些输入参数。
- 2. 根据这些输入参数，确定（作为人类！）测试类方法预期返回的结果。
- 3. 调用该方法（带有这些输入参数）并捕获结果。
- 4. 断言结果等于预期结果。

你不需要担心做任何其他事情。你应该假设你的单元测试框架提供的测试套件功能知道在断言为真或为假时该怎么做。这一点对于 PHPUnit 尤其正确，你很快就会遇到它。

通过创建你的测试用例类，你实际上为你的测试套件提供了操作模式——即运行机制。

此时，你将第一次运行你的黑盒并观察它惨遭失败。它当然会失败，因为你的类中还没有任何实现，因此按定义，返回的任何值都不会是预期（或“断言”）的值。然而，你至少应该能够大致了解当实现处理完成后测试结果会是什么样子。





## 编写类的实现

不要更改类的接口，直接编写代码使其正常工作。在编写过程中无需测试任何东西；这就是测试套件的用途。不过，你可以在编写过程中进行语法检查，以确保没有拼写错误。测试套件主要用于排查逻辑错误，而非编译错误。

如果你以前没遇到过，可以在命令行中使用带 `-l` 参数的 `php` 进行语法检查，后跟要检查语法的类或脚本的文件名。

如果你的类需要与数据库交互，在完成实现之前，检查一下任何数据库 SQL 查询也并非坏主意。由于 PHP 与数据库服务器没有紧密集成，现在排查格式错误的 SQL 语法可能比在发现测试套件在一个或多个方法上失败后更容易。此外，请记住，由于数据库中的数据可以独立于代码更改，你很难准确预测查询数据库的方法的预期输出。

请看下面从典型用户类中摘取的示例查询：

```php
$sql = "SELECT group_id FROM user_group WHERE user_id = $user_id";
```

将 `$user_id` 替换为一个合理的值，并在 PostgreSQL（或其他）控制台中确认查询正常工作。如果正常，你就大功告成了。

假设你的 PHP 语法和 SQL 查询都没问题，并且已实现所有方法，那么就可以开始测试了。

## 第二次运行

再次启动你的测试套件黑盒。既然已经实现了你的类，与上次运行相比，这次测试结果应该会更理想。如果你的类没有通过所有测试，是时候使用传统的调试技术回溯步骤了。

当你的测试套件以 100% 的成功率运行后，你可以完全确信你的类已准备好投入生产环境，并相应地将其集成到主应用程序中。

## PHPUnit 简介

PHPUnit 由 Sebastian Bergmann 开发，是目前可用的少数 PHP 单元测试框架之一。你可能会更喜欢 PHPUnit，因为它免费、易于使用，而且最重要的是，可从 PEAR 获得。

也许令人困惑的是，PHP 有两个可用的包，都名为 PHPUnit，并且都执行基本相同的任务。事实上，它们甚至共享类似的实现。本章考察的实现由 Sebastian Bergmann 开发，更适合 PHP 6。

PHPUnit 包实际上是一套类，而不是单个类。本章重点介绍其测试用例和测试套件功能。当然，PHPUnit 还有更多内容。如果你感兴趣，读完本章后，可以访问 www.sebastian-bergmann.de/PHPUnit/ 了解更多详细信息。

拥有 Java 背景的读者可能已经将其与 JUnit（www.junit.org）进行了比较，这样做是正确的；PHPUnit 实际上是基于 JUnit 松散开发的。因此，本章的许多内容对你来说可能已经很熟悉。你可能不熟悉的是，这种强大的方法在 PHP 6 中可以如此轻松地应用。

## 安装 PHPUnit

一个不错的起点是将 PHPUnit 添加到你的 PHP 环境中。它不属于 PEAR 基础类，因此你需要自行安装。即使你以前安装过，现在检查一下是否正在运行最新版本也并非坏主意。

使用标准 PEAR 语法安装 PHPUnit。如果你运行的是最新版本，PEAR 会告诉你。如果不是，或者你没有安装，你将看到类似下面的输出（在类 UNIX 环境中）：

```
root@genesis:~# pear install PHPUnit
downloading PHPUnit-0.6.2
...done: 11,551 bytes
install ok: PHPUnit 0.6.2
root@genesis:~#
```

如果你想（或需要）手动安装（例如，在没有服务器 root 权限的生产环境中），只需访问 PEAR 包页面 www.phpunit.de/。下载并解压缩存档到适当位置。一切安装正确后，你可以安全地继续。

## 测试用例

本节将介绍如何使用 PHPUnit 创建测试用例。假设你有一个保存在单独文件 testclass.php 中的测试类。由于你目前仍在研究 PHPUnit 的理论，该类中包含什么在这个阶段并不重要。目前，类似下面的内容就足够了：

```php
<?php
class TestClass {
    private $testVar;

    function myMethod($strParam) {
        $this->testVar = $strParam;
        return('expected result');
    }
};
```

你现在可以在单独的 PHP 文件 testcase.php 中创建测试用例。测试用例的前两行应包含必要的 PHPUnit 类和测试类文件：

```php
require_once("testclass.php");
require_once('PHPUnit.php');
```

假设你使用 PEAR 安装了 PHPUnit，它应该能够正常找到 PHPUnit.php。如果不是，并且你不得不手动安装，那么你可能需要指示 PHP 指向正确的文件，如下所示：

```
require_once("/home/ed/myphplibs/PHPUnit.php");
```

在这种情况下，PHPUnit 安装在 /home/ed/myphplibs 中。

现在看看如何扩展 PHPUnit_TestCase 类来创建你自己的测试用例，下面是一些伪代码：

```php
class MyTestCase extends PHPUnit_TestCase
{
    var $objMyTestClass;

    function __construct($name) {
        $this->PHPUnit_TestCase($name);
    }

    function setUp() {
        $this->objMyTestClass = new TestClass();
    }

    function tearDown() {
        unset($this->objMyTestClass);
    }

    function testMyMethod() {
        $actualResult = $this->objMyTestClass->myMethod('parameter');
        $expectedResult = 'expected result';
        $this->assertTrue($actualResult == $expectedResult);
    }
}
```

你可以逐步查看这段代码。考虑第一行代码：

```php
class MyTestCase extends PHPUnit_TestCase
```

你可以随意命名该类。但是，请确保它扩展了 PHPUnit_TestCase。

接下来，看看这一行：

```php
var $objMyTestClass;
```

你扩展的测试用例类只需要一个成员变量，即测试类的一个实例。但是，在更复杂的情况下，你可能希望使用同一类的多个实例，甚至多个类。不过，出于简单起见，请尽量将任何给定测试用例中涉及的类数量保持在最低限度。当然，你绝不应该将不相关的类放在同一个测试用例中。

考虑这段代码：

```php
function __construct($name) {
    $this->PHPUnit_TestCase($name);
}
```

这是你扩展的测试用例类的构造函数。它的唯一工作是调用其父构造函数。但是，请注意非可选的 $name 参数，它由测试套件类使用。

现在看看下面这段代码：

```php
function setUp() {
    $this->objMyTestClass = new TestClass();
}

function tearDown() {
    unset($this->objMyTestClass);
}
```

这两个方法最好描述为虚拟构造函数和析构函数。它们在各种测试函数执行之前和之后被调用。通常，它们的唯一工作是将你的测试类的一个工作实例实例化到你之前定义的成员变量中。

下面的代码定义了测试用例的真正核心内容：

```php
function testMyMethod() {
    $actualResult = $this->objMyTestClass->myMethod('parameter');
    $expectedResult = 'expected result';
    $this->assertTrue($actualResult == $expectedResult);
}
```

在这里，你为要测试的测试类中的每个方法声明一个方法。该方法必须以 test 开头，才能由测试套件自动执行。你应该将方法命名为 test，后跟测试类中真实方法的名称。这样，如果你需要再次查看测试用例，事情会清晰得多。

该方法的具体功能很大程度上取决于你。但是，归根结底，你将做四件事：

- 1. 声明（即硬编码）或确定要传递给测试类方法的测试参数
- 2. 基于该参数声明或确定 *预期* 结果
- 3. 带有该参数调用方法并捕获实际结果
- 4. 将实际结果与你的假设进行比较





## 测试套件

该比较应使用 PHPUnit 提供的众多断言方法之一来完成。正是这些断言使得测试套件能够报告测试结果。本质上，将要报告的正是你断言的准确性。

有众多断言方法可用——assertEquals、assertTrue、assertFalse、assertNotNull、assertNull、assertSame、assertNotSame、assertType 和 assertRegExp。它们基本上都完全符合你从名称中所期望的功能。然而，如果你感到好奇并需要权威解释，请查看 /usr/local/lib/php/PHPUnit/Assert.php 或你安装 PHPUnit 的目录中的 Assert.php 文件。

你可能会奇怪，为什么需要这么多断言方法。难道所有比较都可以使用 assertEquals 并大量使用适当的内置 PHP 函数来处理吗？确实如此。所有的变体其实只是为了方便，让你的代码稍微容易阅读一些，并让你能够避免使用双重否定等等。在 PHPUnit 的后续版本中，断言实际上会在任何失败的测试中提供断言特定的详细信息（例如在 assertType 中显示相关的两种类型，以及在比较两个字符串时哪些字符实际上不匹配）。

开发好你的测试用例类后，在测试套件中使用它其实是一个相对简单的机制。

你可以将以下内容命名为 testsuite.php：

```php
<?php
require_once 'testcase.php';
require_once 'PHPUnit.php';

$objSuite = new PHPUnit_TestSuite("MyTestCase");
$strResult = PHPUnit::run($objSuite);

print $strResult->toString();
?>
```

将 MyTestCase 替换为你的测试用例类的实际名称。如果你从命令行运行（而不是使用 Web 浏览器），如果一切正常，你会得到类似这样的输出：

```
TestCase objMyTestClass->myMethod() passed
```

如果事情没有成功，输出会如下所示：

```
TestCase objMyTestClass->myMethod() failed: expected true, actual false
```

请注意，如果你想在 Web 浏览器而不是命令行中运行，应该在输出字符串上使用 toHTML 而不是 toString 方法，以便将回车转换为 <br /> 等等。

## 为何费心？

乍一看，可能难以看出使用这种测试方法相较于更粗糙的方法（例如涉及服务器错误日志的方法，如前面有些轻蔑地描述的那种）所带来的巨大优势。以下各部分将描述为什么你应该使用单元测试框架。

## 回归测试

你将要处理的绝大多数代码，在某个阶段都需要演进。未必是你来维护它，但可以相当肯定的是，它不会长时间保持原样。

例如，你可能需要重构现有方法，使其提供与之前完全相同的功能，但性能大幅提升。做到这一点的唯一方法是完全重写该方法，保持接口不变，但使用优化后的内部算法。在这种情况下，你的测试套件非常有用。只需在新算法开发前后运行它，并确认两次结果相同即可。

更可能的情况是，你的类需要扩展一个新方法以支持某些新的业务需求。即使在此时，未经修改的测试套件也是有用的。你可以确保新方法不会以任何方式影响其他方法的功能。验证这一点后，你可以简单地扩展测试用例类来测试新方法。

无论哪种情况，你都可以看出，使用单元测试框架进行这种测试（通常称为回归测试）是非常合理的。

## 框架可用性

你的测试用例类可能比你想象的用途更广泛。你开发的其他具有相似或相同接口功能的类，可以使用现有的测试套件快速且可靠地进行测试。

特别是，你可能继承了会覆盖其父类功能的类。或者，利用 PHP 6 的对象模型，你可能拥有实现抽象接口的类。一个很好的例子是表示存储在数据库中的实体的对象，它们几乎肯定会有 getProperty 和 setProperty 方法，等等，如你在第 7 章中所见。几乎不需要或无需调整，你就可以使用标准测试套件来对这类通用类的功能提供即时且可靠的评论。

## 可演示的质量保证

专业软件开发环境通常包含一个复杂的层级结构，涉及任何给定项目中的个人——从项目经理一直到首席架构师、软件工程师、设计师以及其他人。

在这种环境下，每天会产生成千上万行代码。项目的首席架构师根本无法测试其开发人员生产的每一个组件。借助这种结构化的测试方法，管理界的流行语 *授权* 成为可实现的现实。也就是说，可以安全地信任工程师测试他们自己的代码，因为这种方法鼓励了一种在其他更随意的组件测试技术中往往缺失的彻底性。首席架构师可以轻松地在所有组件生产中标准化质量保证，并因此对其团队的产出充满更大的信心。

这种过程的正式性质很可能会被对项目进展有浓厚兴趣的非技术人员（例如项目经理和客户经理）所看好。

## 减少功能测试的负担

通常人们说，项目生命周期中最不性感的部分是功能测试。无论此说法是否公平，它无疑是一项必须承担并预算的额外成本。

通过要求开发团队承担其自身组件的功能测试，对已完成应用程序进行穷尽和广泛的功能测试的需求可以大大降低。然而，它并未完全消除；正如你将在第 20 章中学到的，它仍然至关重要。

## 在隔离中开发模型

在典型的 Web 应用程序开发项目中，构建本身最具争议的方面往往是外观和感觉以及用户旅程——换句话说，往往是信息架构（“wireframes”），站点地图和页面处理最后被签署。因为这些共同形成一个依赖，阻碍任何完成 HTML 的开发，软件工程师常常无所事事地等待，想知道何时才能开始。

然而，关于用户旅程、页面布局、站点地图、导航或创意实施的争论，不一定意味着业务对象的决策不能在单独的开发分支中进行。例如，如果你知道用户注册是完成的应用程序的一个需求，并且你可以对注册期间所需的字段做出有根据的猜测，那么你有能力推断出必须构建一个名为 `User` 的业务类（可能是一个数据绑定对象，如第 7 章中所述），以及一个名为 `Registration` 的实用类。

此外，你可能还能推断出这些类应该具有哪些成员变量和方法。在测试套件中隔离开发这些方法，对其进行测试，并有信心在项目计划的其他元素就位后，可以将它们“放入”应用程序中。

## 总结

在本章中，你学习了模型-视图-控制器（MVC）设计模式及其在健全应用程序架构中的重要性。

除了学习 MVC 方法背后的理论之外，你还接触到了两种非常不同的遵循该方法的方式。首先，你遇到了一个 MVC 工具包，它使你能够在项目中实现 `request` 和 `constraint` 对象层次结构，以更好地强制执行模型、视图和控制器之间的分离。





接着，你了解了模板的概念，以及它如何以及为何被证明是 MVC 最佳实践合规的优秀示例。你还接触了 post-redirect-get (PRG)，并了解了最佳 MVC 实现为何会使用它。

你还详细了解了 Smarty 模板，并了解了如何在几分钟内轻松地将原生 PHP 模板转换为 Smarty 模板，以及 Smarty 的某些高级功能如何为除最复杂项目外的所有项目提供有效的模板选择。

最后，你了解了模型在 MVC 范式中的作用，以及单元测试如何为独立开发模型提供有用的机制。

在第 14 章中，你将了解一些现成的开箱即用工具包，（除其他功能外）它们试图提供开箱即用的 MVC 类架构。这与你在本章中“自己动手”的方法完全不同，但，正如你将看到的，它确实有其好处。

## 14

### PHP 应用程序框架

正如书名所示，这是一本专业书籍，面向那些希望以编写 PHP 代码为职业的开发者——或者那些希望“以专业人士的方式”来做的爱好者。

几乎所有 Web 应用程序开发语言——.NET、经典 ASP、ColdFusion、JSP 等等——都有此类书籍，因为对于每一种语言，都有必要区分“如何入门”和“如何正确地做”。

然而，PHP 可能比任何其他开发语言更需要此类书籍。正如本书多次提到的那样，PHP 的最大优势之一也是其最大弱点之一——即其简单性和浅陋的学习曲线。像一辆强大的欧洲跑车，在错误的人手中，它非常危险。因此，贯穿本书，我们一直竭力展示每种编程学科中的最佳实践——对象和类、数据库抽象、事件驱动编程、日志和调试、与用户通信，以及更多内容。

本章将向你介绍一种极其有用的事物：应用程序框架的概念，它通过强迫你从一开始就做对事情，为你省去了很多麻烦。不要误解，之前的 13 章对于让你了解“原因”以及“如何做”至关重要——但现在你知道了“原因”，你可以让别人为你处理最佳实践，从而让自己的生活轻松得多。

### 框架简介

简单来说，框架是一组预先准备好的代码，为你提供了一幅预先绘制好的铅笔草图，你可以在其上绘制完成的应用程序。在某些情况下，框架只是一组 PHP 类。此时，作为开发者，你有责任正确地使用它们。在其他情况下，与应用程序服务器实现了更紧密的关系，这意味着合规性被强制执行，而非仅仅被请求。

大量框架已进入市场。几乎全部都是免费的。有些维护得比其他更好。有些支持得比其他更好。关键的是，只有一个得到了 PHP 开发社区名义上的认可。不过，在每种情况下，它们都试图解决若干核心目标——有些框架实现的比其他更多。

### 应用程序结构

如果你不幸曾为维护目的而遇到过初级开发者的 PHP 项目，你无疑不确定究竟该从何入手。此外，你无疑发现了大量文件和文件夹，没有明显的东西存放位置，有些代码在类中，有些不在；有些 HTML 保存在模板中，有些是从代码中编写的；有些图片在数据库中，另一些在磁盘上——轻描淡写地说，这可能不是一段愉快的记忆。

PHP 将应用程序的结构和布局留给开发者，这在某种程度上是一把双刃剑。在正确的人手中，它允许巨大的灵活性。开始项目不需要像 Ruby on Rails (RoR) 那样的“脚手架”，因此从一开始就没有施加任何约束。在错误的人手中（或缺乏全面的架构文档时），这可以理解地导致混乱。

许多应用程序框架试图通过向开发者强加半严格的应用程序结构来纠正这一问题。这可以简单到指定的目录层次结构——也许为实用工具类、模板和业务对象各分配一个文件夹。在更复杂的层面上，它可以深入参与 HTTP 请求级别，并通过一组必须符合预定义结构的类“路由”请求。

这对于那些将模型-视图-控制器（MVC）贯彻到底的框架尤其适用。在这样的框架中，不允许对 /admin/edituser.php?id=12345 发出 HTTP 请求。相反，等效的请求，例如 /user/edit/12345，可能会自动调用“user”类的“edit”方法——该类必须实现一个非常特定的接口。

这种方法相当激进。它完全摒弃了 PHP 作为线性脚本语言的概念，而将应用程序划分为由用户行为驱动的组件部分。正如你将在本章后面看到的，这可以加快代码编写速度并减少不必要的重复——但对于高级开发者来说，这也可能有点过于限制。

### 代码与显示逻辑分离

即使 PHP 框架选择不实现前一节讨论的那种激进的 MVC 方法，几乎所有框架也都会坚持将代码和显示逻辑分开，这是本书一贯推崇的最佳实践。

这可以通过多种不同的方式实现。有些只是将脚本分为两组 PHP 代码（一组用于行为逻辑，另一组用于混杂 HTML 的显示逻辑）。其他人会使用现成的模板平台，例如 Smarty。还有人会“自行构建”模板系统。

只有在你确信自己愿意终身使用该框架时，才应该寻找使用专有模板系统的框架，因为单个模板的可移植性可能无法实现。在做出此决定时，你应理解，某些 PHP 框架是出于热情而非金钱而开发的，并不一定会永远维护或支持。

### 验证

验证用户输入是否符合预定义约束对任何应用程序（无论大小）都至关重要。某些要求无疑很容易自行实现——例如检查电子邮件地址是否有效。其他要求则更复杂——也许需要防止在数据库表中创建重复记录。

无论需求如何，验证用户输入的一致且易于维护的方法都是必须的。与其自行开发，不如使用许多框架提供的自身实现，涵盖约束类定义、错误输入报告、故障堆栈和约束多态性。

在简单的项目中，大部分功能可能永远不会被使用，但这种统一的方法提供了某种程度的可扩展性和可维护性，而这只是“自行临时拼凑”无法做到的。

自然，如果你有自己的一套验证类并且依赖甚深，大多数框架也不会回避使用它们来替代随附的类。

### URL 重写

毫无疑问，随着 Web 应用程序变得更加复杂，构成所有 HTTP GET 请求的 URL 也变得更加臃肿、冗长且不美观。

这不仅仅是美观问题。长而复杂的 URL 确实存在实际问题。当 URL 过长时，用户通过即时通讯、电子邮件或 Facebook 向朋友和同事复制粘贴 URL 时经常会出错。当 URL 需要仅凭记忆引用时，可记忆性成为一个问题。搜索引擎偏好简短、人类可读且与其中包含的内容相关的 URL。此外，复杂的“技术型”URL 有助于暴露应用程序的内部工作原理——这对黑客来说是个诱惑。

因此，许多框架提供某种 URL 重写机制——要么是静态的（例如，作为开发者，你可以指定 /Home 实际上代表 /home.php），要么是动态的（如前面讨论 MVC 时提到的）。

这通常通过与 Web 服务器的紧密合作来实现。毕竟，是 Web 服务器首先拦截 HTTP 请求，然后再将其交给 PHP。因此，如果不进行服务器级别的更改，几乎不可能实现前面讨论的效果。通常，使用 Apache 时，这是通过 mod_rewrite 完成的。

幸运的是，作为开发者，你不需要过多思考此事。大多数提供 URL 重写的框架要么会为你配置 Web 服务器，要么会提供简单的逐步说明供你遵循。不过，你确实需要考虑部署到生产环境时这可能带来的影响——这是一个我们稍后将再次讨论的话题。





## 表单持久性

当你最初开始构建 Web 应用程序时，当你意识到 HTML 支持大量类似 Windows 的表单控件（文本框、单选按钮、复选框、下拉列表等等），而 HTTP 不支持在请求之间持久化这些控件的值或状态时，你可能曾经历短暂、轻微的沮丧。

因此，即使有最出色的验证（如前面讨论过的），确保这些控件的值在请求之间被持久化的责任仍然在开发者身上，这样如果用户被“退回”到一个有错误的表单（例如，缺少必填字段），他们迄今输入的所有内容都会被保留——正如他们所期望的那样。

这意味着文本框包含用户输入的文本，单选按钮和复选框的选择状态与用户所选完全一致，下拉列表会展开到（如你所料）用户选择的选项。

这不仅对表单验证很重要。在某些 Web 应用程序中，即使用户导航到另一个页面，保留一个值可能也很有价值。例如，一个复杂的“高级搜索”页面可能包含多个表单控件。如果用户想稍微修改搜索条件来生成全新的结果集，期望他们重新输入每一个标准，这实在太不近人情了。通过在会话中存储表单状态数据，可以实现更“类似 Windows”的体验。

当然，自己实现这个效果是完全可能的。的确，当你刚开始使用 PHP 时，你可能曾写入一些过程化代码来实现这个。随着你的进步，你可能编写了自己的库以供定期重复使用。（你现在有多少个这样的库？很可能是几个。）

大多数框架开箱即用提供此类功能——的确，这是更难关闭的功能之一。因此，如果你打算使用本章讨论的框架之一，最好放弃自己的实现，改用官方认可的方式。

## 对象关系映射

本书前面向你介绍了对象关系映射（ORM）的概念。你会记得，在构建带有对象模型（包含一组“业务对象”——代表数据库中存储的实体实例的类）的应用程序时，它提供了一层抽象。

通过使用 ORM，常见的数据库功能（例如创建、读取、更新和删除）可以在不编写任何 SQL 的情况下执行。ORM 层会为你处理这些。这不仅意味着你最终编写的代码更少（从而加快开发速度并减少错误），还增加了迁移到其他数据库平台的可移植性，而这通常不切实际或无法实现。

你还学习过 DataBoundObject —— 一个你可以扩展的抽象类，用于提供简单的业务对象实现，该实现与底层数据库表无缝连接。如你所料，大多数 PHP 应用程序框架都认识到这种方法的好处，因此为你提供了类似的东西——他们自己的实现——被命名为 GenericObject、DataObject 或 ActiveRecord 之类的简洁抓耳的名称。它们的设计目的大致相同，尽管很少有实现像 DataBoundObject 那样在架构上正确，因为它们不一定充分利用了 PHP 6 的完整功能集。

与这些框架中的许多事物一样，你没有义务使用它们预提供的实现——除非，也就是说，你打算使用模型和视图密不可分的 MVC 框架之一，这是你稍后将了解更多的内容。

### 数据库抽象

在第 6 章中，你被介绍了 PHP 数据对象（PDO），并被重点告知为什么它是一件好事。因此，希望你已经完全认同数据库抽象的概念，以及为什么 PDO —— 数据库抽象的官方 PHP 认可机制 —— 是首选之路。

遗憾的是，许多 PHP 框架仍然选择提供自己的抽象类。他们可能出于最好的初衷，但通过试图迫使作者违背 PHP 普遍接受的原则，他们正在鼓励糟糕的代码。你应该站在道德高地上，抵制此类自制的抽象层。坚持使用 PDO，并把框架中自带的任何东西扔进垃圾桶。

### 实用工具类

你将遇到的大多数（如果不是全部）PHP 框架都会包含一些实用工具类，这些类似乎并不适合任何地方。这些类执行有用的库功能，例如加密、发送电子邮件、验证用户等等——这些（可以说）本应在一开始就内置到 PHP 语言中。

你可能随着时间的推移积累了自己的代码库，所以如果放弃它转而使用他人代码的想法让你感到有些不自在，你不必一定要放弃。库代码往往是非常个人化的东西，使用框架不熟悉的库代码库有点像穿别人的鞋子——它们可能功能正常，但就是感觉不对。

还要记住，框架提供的实用工具类最好也只是事后添加的——最坏的情况是，从框架作者自己的个人集合中扔进来的东西。

### 用例场景

在了解一些框架竞争者之前，让我们先考虑一下可能从框架处理中受益的示例应用程序。

接下来的应用程序有一个简单的任务：使用户能够注册公司的电子邮件通讯。它必须验证名、姓和电子邮件地址；确保记录不存在于数据库中；如果发生任何验证错误，则抛出错误；并在用户成功注册后向其致谢。这是一个常见的 PHP 应用程序，但请考虑你面临的以下挑战：

- 验证名、姓和电子邮件地址
- 创建表示通讯订阅者的业务对象
- [ ] 在接受提交之前确保订阅者不存在
- [ ] 向用户报告错误，并允许他们更正
- [ ] 持久化表单数据
- [ ] 使用数据库抽象以确保可移植性
- [ ] 将业务逻辑与显示逻辑分开

如果你已经详细读完了本书的其余部分，这些挑战都应该相对简单——这当然都已经涵盖了；但是，当你意识到要构建一个毕竟相当简单的应用程序需要做这么多工作时，你叹一口气也是情有可原的。

在接下来的章节中，你将看到三个 PHP 应用程序框架的示例。在其中一个中，你将实现一个完全完整的应用程序，它做的正是前面讨论过的事情。在其他框架中，你将看到一个简短的概述，以便你自己尝试它们。

它们都试图通过采用本章前面介绍的一些技术，使之前提到的那些头疼问题变得容易应对得多。它们各有优劣。本章稍后，你将看到在决定为自己的企业项目部署哪个框架时必须考虑的各种因素。

### 底层数据库

在探索这些框架时，准备好一个示例数据库及其中的示例数据库表是有价值的。为了延续前面建议的示例需求，你可以创建一个包含公司通讯订阅者详细信息的单个数据库表。

在开发服务器上启动控制台，并创建一个名为 `newsletter` 的数据库：

```
$ /usr/local/pgsql/bin/createdb newsletter
CREATE DATABASE
```

创建该数据库后，创建一个名为 `newsletter`、可以连接到该数据库的用户。出于本章的目的，使用密码 `password`。对于生产环境，你可能想选择更安全的密码（只是个想法）。以下是代码：

```
$ /usr/local/pgsql/bin/createuser newsletter -P
Enter password for new role:
Enter it again:
Should the new role be a superuser? n
Should the user be allowed to create databases? n
Should the user be allowed to create more new roles? N
CREATE ROLE
```

太好了。现在在 PostgreSQL 控制台中打开数据库并创建表。你需要的 SQL 语法如下：

```
CREATE TABLE "subscriber" (
 "id" SERIAL PRIMARY KEY NOT NULL,
 "first_name" character varying (128),
```


```
"last_name" character varying (255),
"email_address" character varying(256) NOT NULL,
"date_of_signup" date NOT NULL,
"time_of_signup" time NOT NULL,
"remote_addr" character varying(15) NOT NULL
);

GRANT ALL PRIVILEGES ON "subscriber" TO "newsletter";
GRANT ALL PRIVILEGES ON "subscriber_id_seq" TO "newsletter";

CREATE UNIQUE INDEX "em_unq_idx" ON "subscriber" ("email_address");
```

末尾的唯一索引并非严格必要，因为作为数据输入验证的一部分，您会进行常识性检查以确保当前订阅者不存在；但从“双重保险”的角度来看，这很好。如果您将来希望扩展应用程序以允许来自第三方来源的数据操作，则可以保证订阅者数据库的唯一性。

## 示例应用程序

示例数据库就位后，现在是时候开始查看一些单独的框架了。它们都追求几乎相同的目标，但实现方式略有不同。就像“拳击裤”与“三角裤”与“光屁股”之间的选择一样，很多时候这归结于个人偏好。

让我们先来看看一个用专门为 PHP 6 开发的新 PHP 框架 Ulysses 编写的完整应用程序。

## 介绍 Ulysses

Ulysses 是一个开源的面向对象 PHP 应用程序开发框架，根据 BSD（伯克利）许可证免费提供。这意味着无论您的项目的最终目标是什么（利他、商业，或十足的梅菲斯托式），它都可以免费下载、使用和部署。支持和文档可按商业基础获得。

## 安装 Ulysses

要下载 Ulysses，请访问项目网站 www.ulyssesframework.com。您将被重定向到 SourceForge 上的项目主页，可以在那里下载最新版本。

将下载的 .tgz 文件移动到 /usr/local/lib/php —— 或您通常存放 PHP 库的任何位置。然后，使用以下标准语法对其解压：

```
tar -xzvf ulysses-3.0.23.tar.gz
```

# 第二部分：学习高级开发技术

您应该会看到创建了一个文件夹 /usr/local/lib/php/ulysses，里面包含大量类和助手文件。

Ulysses 仅兼容 Apache Web 服务器，并且必须以特定方式配置使用该框架的虚拟主机，以便启用您稍后将遇到的“短”URL。Apache 还必须编译支持 mod_rewrite。如果您遵循附录 D 中讨论的最佳实践安装，则会满足此条件。如果没有，请参阅 http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html（适用于 Apache 1.3.x）或 http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html（适用于 Apache 2.x），了解如何安装的详细信息。

Ulysses Web 应用程序基于“每个虚拟主机一个”的基础运行——您无法在单个主机上运行多个网站。虚拟主机条目将类似于以下内容。如果您要创建全新的虚拟主机，应将此类条目放在 Apache 配置文件 (httpd.conf) 的最末尾：

```
<VirtualHost>
ServerName newsletter.example.com
ServerAdmin ed@example.com
CustomLog /home/ed/logfile_newsletter common
ErrorLog /home/ed/errlog_newsletter
DocumentRoot /home/ed/public_html/newsletter
Alias /ulysses/ "/usr/local/lib/php/ulysses/"
RewriteEngine on
RewriteRule ^(/)(|([A-Z]{1,})(.*)$ /ulysses/php/controller.php?page=$2$3 [QSA,PT]
RewriteRule ^/$ /Home [QSA,L,R]
</VirtualHost>
```

以下是四个至关重要的行：

```
Alias /ulysses/ "/usr/local/lib/php/ulysses/"
RewriteEngine on
RewriteRule ^(/)(|([A-Z]{1,})(.*)$ /ulysses/php/controller.php?page=$2$3 [QSA,PT]
RewriteRule ^/$ /Home [QSA,L,R]
```

第一行将虚拟目录映射到 PHP 框架的路径。第二行启用 Apache URL 重写引擎。第三行和最后一行告诉 Apache 将任何以大写字母开头的请求重定向到 Ulysses 框架的核心控制器。

这意味着以下形式的请求将被重定向到 Ulysses 引擎：

```
http://www.example.com/Home
```

但是，以下形式的请求不会：

```
http://www.example.com/home
```

这意味着图片、CSS 样式表以及所有静态内容都不会通过引擎提供服务——只要您不使用大写字母开头命名目录即可。

最后一行会将对 /（例如 http://www.example.com/）的请求指向应用程序的“起始”servlet，通常称为 Home。

## 使用 Ulysses

在 Web 服务器上安装 Ulysses 后，从此时起，它可用于您的所有 PHP 项目——您不必再次安装它。现在是时候开始利用它提供的代码库了。

为您的示例应用程序创建一个项目文件夹。如前面引用的虚拟主机示例所示，您使用了 /home/ed/public_html/newsletter —— 因此，只需创建一个与您为应用程序创建的虚拟主机相匹配的文件夹即可。

虽然 Ulysses 不强制执行特别严格的目录结构，但有几个文件夹是您必须创建的：

- /your/web/root/tpl
- /your/web/root/phpm
- /your/web/root/phpm/business
- /your/web/root/phpm/utility
- /your/web/root/phpm/controls
- /your/web/root/phpm/custom
- /your/web/root/phpm/settings

您可能创建的任何其他文件夹（用于图片、CSS 样式表、JavaScript 等）完全由您决定。

但是，请记住以下事项：

- [ ] 您必须将页面模板（通常包含 HTML）放在 tpl 下。
- [ ] 您必须将业务对象放在 phpm/business 下，实用程序类放在 phpm/utility 下。
- [ ] 您必须将应用程序设置放在 phpm/settings 下。

遵循这些简单规则，您应该就没问题了。

## 设置

您需要在 phpm/settings 下创建几个文件。这些文件定义了应用程序的根数据库（尽管您可以定义任意多个），以及内置会话类将保存其会话的目录位置。

按如下所示创建 phpm/settings/constants.phpm：

```
<?
define("BASE_SESSION_PATH", "/tmp");
?>
```

出于本练习的目的，您将会话存储在磁盘上——如果您一直从第一页跟随本书学习，您就会知道这种做法不被推荐。当然，您也可以使用 TMPFS 或 RAM 驱动器——在部署到生产服务器时，这是一个更好的选择。或者，您可以用自己的会话类替换 Ulysses 的会话类，该类使用数据库或 memcache。

现在，您需要告诉应用程序在哪里找到数据库。按如下所示创建 `phpm/settings/dbaccess.phpm`：

```
<?
// Definitions for connecting to a postgreSQL database.
define("DATABASE_USERNAME", "newsletter");
define("DATABASE_PASSWORD", "password");
define("DATABASE_HOSTNAME", "localhost");
define("DATABASE_BASENAME", "newsletter");
define("DATABASE_DRIVER", "pgsql");
define("PDO_DSN", DATABASE_DRIVER . ":dbname=" . DATABASE_BASENAME .
    ";user=" . DATABASE_USERNAME . ";password=" . DATABASE_PASSWORD .
    ";host=" . DATABASE_HOSTNAME);
?>
```

如果您偏离了本章前面建议的数据库名、用户名或密码，您需要在此处更改。当然，由于使用了 PDO，您也可以同样轻松地在此处指定 MySQL 数据库。

最后，您需要告诉 Ulysses 包含这些数据库设置，因此按如下所示创建 `phpm/requires.phpm`。（Ulysses 会自动为每个页面加载此类。）

```
<?
require("$appDir/phpm/settings/dbaccess.phpm");
?>
```

不要担心您尚未定义变量 `$appDir` —— 您不需要定义，因为 Ulysses 会自行解析。

## 业务对象

在这个假设的应用程序中，只需要一个业务对象——一个代表您的新闻通讯订阅数据库中订阅者的对象。Ulysses 建议您将 `DataBoundObject` 用作“活动记录”模式类——但在实践中，您可以使用任何您喜欢的类。不过，`DataBoundObject` 现成包含在内。

您可以将以下代码保存为 `phpm/business/subscriber.phpm`：

```
<?php
class Subscriber extends DataBoundObject {
    protected $FirstName;
    protected $LastName;
    protected $EmailAddress;
}
```




protected $DateOfSignup;
protected $TimeOfSignup;
protected $RemoteAddr;

protected function DefineTableName() {
    return("subscriber");
}

protected function DefineRelationMap() {
    return(array(
        "id" => "ID",
        "first_name" => "FirstName",
        "last_name" => "LastName",
        "email_address" => "EmailAddress",
        "date_of_signup" => "DateOfSignup",
        "time_of_signup" => "TimeOfSignup",
        "remote_addr" => "RemoteAddr")
    );
}
}
?>

如果你读过第7章，这段代码应该看起来相当简单明了——你创建了一个名为 `Subscriber` 的业务对象，它与数据库中的表 `subscriber` 相关联，并且你已经映射好了必要的列。

不过，缺少一个方法。这个应用程序的一个核心要求是“不允许重复”——也就是说，某人只能注册一次。因此，你应该添加一个标准静态方法，用于检查指定电子邮件地址是否存在：

```
static function checkExists($strEmail) {
    $strEmail = strtolower($strEmail);
    $strSQL = "SELECT \"id\" FROM \"subscriber\" WHERE
    lower(\"email_address\") = :email";
    $objPDO = PDOFactory::GetPDO();
    $objStatement = $objPDO->prepare($strSQL);
    $objStatement->bindParam(':email', $strEmail, PDO::PARAM_STR);
    $objStatement->execute();
    $arRow = $objStatement->fetch(PDO::FETCH_ASSOC);
    $id = $arRow["id"];
    return ($id > 0);
}
```

将此方法添加到你的类并保存。每当用户输入电子邮件地址时，你都会调用此方法，以确保该地址不存在。如果存在，则此方法将返回 `true`，你的应用程序将拒绝保存该记录（并相应通知用户）。

你还必须让 Ulysses 知道你的 `subscriber` 类，因此修改 `phpm/requires.php` 并添加以下行：

```
require("$appDir/phpm/business/subscriber.phpm");
```

这样一来，每当向 Ulysses 引擎发出 HTTP 请求时，都会加载该业务类。

## Servlets

在 Ulysses 框架中，HTTP GET 和 POST 请求是发送到 *Servlet* 的。如果你熟悉 Java，那么这对你来说早已是家喻户晓的现象。它是一个带有两个强制抽象方法的类：一个用于处理 GET 请求，另一个用于处理 POST 请求。

实际上，对你的 Web 服务器发起的指向 *www.example.com/Home* 的请求将查找名为 *HomeServlet* 的 Servlet。发起的指向 *www.example.com/Signup* 的请求将查找名为 *SignupServlet* 的 Servlet，依此类推。

每个 Servlet 被设计为在使用 HTTP GET 调用时自动查找与该 Servlet 匹配的页面模板。任何使用 HTTP POST 调用的 Servlet 的预期行为都是通过 HTTP GET 将用户重定向到另一个 Servlet —— 这是本书前面讨论过的一种最佳实践模型，称为 Post-Redirect-Get (PRG)。

你现在可以创建第一个 Servlet 了。按如下所示创建 *phpm/servlets/homeservlet.phpm*：

```
<?

class HomeServlet Extends Servlet {

    public function __construct($objSmarty, $objSession, $queryStringParms,
        $strPageIdentifier) {

        parent::__construct($objSmarty, $objSession, $queryStringParms,
        $strPageIdentifier);
        }

    public function _doGet($objSmarty, $objSession, $queryStringParms) {
    }

    public function _doPost($objSmarty, $objSession, $queryStringParms) {
    }
}

?>
```

没什么复杂的，对吧？这被称为 *空 Servlet* —— 除了尝试加载相应的页面模板并显示它之外什么也不做的 Servlet —— 前提是使用 HTTP GET 调用它。如果使用 HTTP POST，Ulysses 引擎将自动导致浏览器再次使用 HTTP GET 请求该页面。

你现在可以创建一个配套的虚拟模板。创建以下模板并将其保存为 tpl/home.tpl。注意大小写——模板必须始终以小写字母开头，而相应的类必须以大写字母开头：

```
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
<head>
</head>
<body>
<h1>Home Page</h1>
</body>
</html>
```

创建好 Servlet 和模板后，你现在应该能够在虚拟主机上请求 URL /Home（注意大写字母），并看到完全符合预期的结果——一个空页面，只有标题 “Home Page。”

这不太令人兴奋，所以让我们改变一下。在 Ulysses 中，你使用控件向页面添加元素——这有点像你在 Visual Basic 中可能使用过的控件。控件用于文本框和单选按钮等输入字段，也用于显示动态信息的标签。控件必须在 Servlet 和模板中都声明——在模板中，这样 Ulysses 引擎就知道在哪里将它们与你的 HTML 结合；在 Servlet 中，这样它们才能被声明为类。

起初，所有页面控件都是类这一做法可能显得极端，但当你考虑到类可以被重写和扩展时，这就开始说得通了。不喜欢自带的文本框类吗？只需扩展它并重写你喜欢的任何方法即可。

修改你刚才创建的主页 Servlet (servlets/homeservlet.php)，使其如下所示。（你将在构造函数和成员变量声明空间中添加额外的代码。）

```
<?
class HomeServlet Extends Servlet {
public $objTitle;
public $objFirstName;
public $objLastName;
public $objEmail;
public $objStatusLabel;
public $objSuccessLabel;

public $objFirstNameLabel;
public $objLastNameLabel;
public $objEmailLabel;

public function __construct($objSmarty, $objSession, $queryStringParms,
$strPageIdentifier) {

$this->objTitle = new Title("Email Bulletin Signup", "default");
$this->objFirstName = new TextBox("firstname");
$this->objLastName = new TextBox("lastname");
$this->objEmail = new TextBox("email");

$this->objStatusLabel = new Label("status");
$this->objSuccessLabel = new Label("success");

$this->objFirstNameLabel = new Label("firstnamelabel", "First Name");
$this->objLastNameLabel = new Label("lastnamelabel", "Last Name");
$this->objEmailLabel = new Label("emaillabel", "Email Address *");

parent::__construct($objSmarty, $objSession, $queryStringParms,
    $strPageIdentifier);
}

public function _doGet($objSmarty, $objSession, $queryStringParms) {
}

public function _doPost($objSmarty, $objSession, $queryStringParms) {
}
}
?>
```

你还必须修改你创建的那个极其简单的模板。现在就这么做，用以下内容替换 HTML：

```
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
<head>
<tpl:title id="default" />
<style type="text/css">
.erroneous { color: red; }
</style>
</head>
<body>
<h1>Signup</h1>
<tpl:if $success neq "">
<div id="submission">
<p class="successText">
<tpl:label id="success" />
</p>
<p class="summaryText">
You can unsubscribe
at any time by using the
link at the top of the emails
we'll send you.
</p>
<p class="summaryText">
Why not visit our company web site?
<a href="http://www.example.com">Click here</a>
to go there now.
</p>
</div>
<tpl:else>
<p>
Hello; we'd very much like for you to sign up to our
email newsletter.
</p>
<p>
We won't sell your email address and it's easy to
unsubscribe (just click on the link at the top of one
of our emails).
</p>
<form method="post" action="/Signup">
<label for="firstname"><tpl:label id="firstname" /></label>
<tpl:textbox id="firstname" /><br />
<label for="lastname"><tpl:label id="lastname" /></label>
<tpl:textbox id="lastname" /><br />
<label for="email"><tpl:label id="emaillabel" /></label>
<tpl:textbox id="email" /><br />
<input type="submit" value="Sign Up" />
<tpl:if $status neq "">
<p class="errorText"><tpl:label id="status" /></p>
</p>
</tpl:if>
<br /><br />
<i>* Required Field</i>
</form>
</tpl:if>
</body>
</html>
```

启动 Web 浏览器并将其指向虚拟主机上的 /Home。你应该会看到类似图 14-1 的内容。

好吧，它不怎么好看，但多少还是符合你对通讯注册页面的预期的。





![](img/a1b732997d9cb194dceec0570dc79710_377_0.png)

图 14-1 通讯报注册页面示例

如果您再次查看该 servlet，应该不难弄清楚幕后发生了什么：

```
$this->objTitle = new Title("Email Bulletin Signup", "default");
$this->objFirstName = new TextBox("firstname");
$this->objLastName = new TextBox("lastname");
$this->objEmail = new TextBox("email");
$this->objStatusLabel = new Label("status");
$this->objSuccessLabel = new Label("success");
$this->objFirstNameLabel = new Label("firstnameLabel", "First Name");
$this->objLastNameLabel = new Label("lastnameLabel", "Last Name");
$this->objEmailLabel = new Label("emaillabel", "Email Address *");
```

这些行中的每一行都表示页面上的一个控件声明。声明标题控件（模拟 HTML 标题标签）的语法很简单——先是标题文本，然后是标识符：

```
$this->objTitle = new Title("Email Bulletin Signup", "default");
```

模板中的对应条目也很简单：

```
<tpl:title id="default" />
```

Ulysses 框架在解析模板时，将查找相应 servlet 中声明的 Title 类的实例，提取其文本值，并渲染必要的 HTML 标题标签：

```
<title>Email Bulletin Signup</title>
```

其他控件的工作方式类似。本示例中声明了标签和文本框。请注意，标签不一定需要初始值——如果您使用标签（可能）按条件显示错误消息，这很有用。状态标签和成功标签的工作方式完全如此——模板中的条件语法确保它们仅在非空时显示：

```
<tpl:if $status neq "">
    <p class="errorText">
    <tpl:label id="status" />
    </p>
</tpl:if>
```

这种模板语法对您来说可能很熟悉。确实，应该熟悉——它只是披着外衣的 Smarty 模板引擎，您在本书前面已经遇到过它。

## 处理用户输入

如果您尝试按原样提交数据采集表单，将遇到 404 错误——原因很简单：表单的目标不存在。请查看模板：

```
<form method="post" action="/Signup">
```

正如您所见，表单正尝试发送到 /Signup，这意味着必须创建一个名为 SignupServlet 的 servlet，并填充其 __doPost() 方法。

该 servlet 承担两个功能：验证用户输入，如果通过，则将条目保存到数据库中。它只有一个最终行动方案：将控制权交还给原始提交 servlet。在此过程中，它可以与即将交还控制权的 servlet“对话”，设置标签和文本框等页面控件的值。

以下代码构成了 php/servlets 中的 signupservlet.php。没有对应的模板，因为该 servlet 没有 GET 方法：

```php
<?
class SignupServlet Extends Servlet {
    public function __construct($objSmarty, $objSession, $queryStringParms,
        $strPageIdentifier) {
    }
    public function __doGet($objSmarty, $objSession, $queryStringParms) {
        header("Location: /Home");
        exit(0);
    }
    public function __doPost($objSmarty, $objSession, $queryStringParms) {
        $objServlet = Servlet::GetReferringServlet();
    }
    # Validate
    $strFN = $objServlet->objFirstName->GetValue();
    $strLN = $objServlet->objLastName->GetValue();
    $strEM = $objServlet->objEmail->GetValue();

    $objServlet->objEmailLabel->strCSSClass = "";

    if (strlen($strEM) < 1) {
        $objServlet->objEmailLabel->strCSSClass = "erroneous";
    };

    try {
        if (strlen($strEM) < 1) {
            throw new Exception("Sorry, you didn't fill in all
            required fields. Please try again.");
        };
        if (Subscriber::checkExists($strEM) == true) {
            $objServlet->objEmailLabel->strCSSClass = "erroneous";
            throw new Exception("Sorry, a subscriber by this
            address already exists. Please try again.");
        };
        if (preg_match('/^[a-z0-9!#$%&*+==?^_`{|}~-]+(\.[a-z0-9!#$%&*+==?^_`{|}~-]+)*@([a-z0-9]+.)+[a-z]{2,6})$/ix', $strEM) <= 0) {
            $objServlet->objEmailLabel->strCSSClass = "erroneous";
            throw new Exception("Sorry, that email address isn't
            valid. Please try again.");
        };
    } catch (Exception $e) {
        $objServlet->objStatusLabel->SetCaption($e->getMessage());
        $objServlet->redirectTo();
    };

    # TODO - Save here

}
?>
```

您会注意到这里有一个 TODO。如果所有验证都成功，您想将记录保存到数据库中。您稍后会填写这部分。目前，为清晰起见，省略了它。

### 持久性

您首先会注意到，没有显式代码来处理文本框等用户输入控件的持久性。好消息是——不需要。Ulysses 框架会为您处理此问题。一旦您提交页面，其全部内容（或状态）就会被捕获并保存在会话中。如果用户出于任何原因返回该页面，表单将以提交时的完全相同状态出现。

这对于非用户可修改的控件（例如标签）同样适用。如果标签的值（即内容）在 servlet 本身或外部 servlet 中被修改（这是完全允许的），则该值将在该用户会话的剩余时间内保留。

在应用程序开发过程中，您可能时常会觉得这令人沮丧。您可能希望将页面“重置”到其自然状态，而不让测试输入弄乱文本框。实现此目的的最简单方法是什么？只需清除浏览器的 cookie。您的会话将丢失，会生成一个新会话，页面将重置为“自然”状态。

### 验证

在注册过程中，会对用户输入执行几项检查。唯一的非可选字段是电子邮件地址；名和姓被视为可选。因此，所有检查都涉及电子邮件地址字段——是否存在、是否有效，以及最重要的是，是否已经提交过？

只有通过所有三项检查，才会保存用户的输入。否则，用户会受到适当的告诫，并要求更正。

您首先会注意到，用户输入的值不是通过 $_POST 检索的。相反，Ulysses 让您访问外部 servlet 的控件，如下所示：

```
$objServlet = Servlet::GetReferringServlet();
$strFN = $objServlet->objFirstName->GetValue();
$strLN = $objServlet->objLastName->GetValue();
$strEM = $objServlet->objEmail->GetValue();
```

这很有用，因为有时您可能不想要原始 POST 数据。由于您可以访问页面控件暴露的任何方法，您不仅限于 GetValue()。事实上，该方法可以被重载，这意味着其值返回的方式可以在控件类本身中细化——而不是在您的 servlet 中。

Ulysses 不提供任何特殊的验证例程。您可以自己编写，也可以使用众多可用的 PEAR 类之一来完成此任务。在此示例中，验证非常简单，以至于使用本机 PHP 代码来检查电子邮件地址是否有效、是否已提供，以及是否不在数据库中。

如果这些检查中的任何一项失败，将抛出异常。捕获异常后，原始 servlet 的状态标签将设置为传递给异常的错误消息。然后调用其 redirectTo() 方法，这会将用户弹回主页：

```
} catch (Exception $e) {
    $objServlet->objStatusLabel->SetCaption($e->getMessage());
    $objServlet->redirectTo();
};
```

当主页重新加载时，更新后的状态标签会向用户指示存在问题，并邀请用户更正提交。

请注意 CSS 类如何用于突出显示填写错误的字段：

```
`$objServlet->objEmailLabel->strCSSClass = "erroneous";`
```

这使得电子邮件地址标签以红色突出显示，让用户一眼就能看出错误所在。

### 快速检查

在继续之前，请尝试使用空电子邮件地址字段提交表单，以验证代码是否有效。您应该会看到类似于图 14-2 的内容。

![](img/a1b732997d9cb194dceec0570dc79710_381_0.png)

图 14-2 未填写电子邮件地址的表单提交结果

在屏幕上查看时，“电子邮件地址”字段会以红色突出显示，并显示一条告诫用户的消息。

单击浏览器中的刷新，您会发现页面状态仍然保留——并且，重要的是，表单不会重新提交。

### 保存输入

请记住前面看到带有 `TODO` 注释的 servlet 代码块？如果提交成功（即所有验证检查都通过），本该在此处保存订户。




您现在可以将该代码插入，用以下内容替换该注释。只有在未触发导致 servlet 提前终止的异常时，才会执行此代码：

```
$objSubscriber = new Subscriber(PDOFactory::getPDO());
$objSubscriber->setDateOfSignup(date("Y-m-d"));
$objSubscriber->setTimeOfSignup(date("H:i:s"));
$objSubscriber->setRemoteAddr($_SERVER["REMOTE_ADDR"]);
$objSubscriber->setEmailAddress($strEM);
$objSubscriber->setFirstName($strFN);
$objSubscriber->setLastName($strLN);
$objSubscriber->Save();
$subID = $objSubscriber->getID();
if ($subID <= 1) {
    $objServlet->objStatusLabel->SetCaption("Sorry, a technical
    fault meant we couldn't save
    your details. Please try again
    in a minute or two.");
    $objServlet->redirectTo();
} else {
    $objServlet->objStatusLabel->SetCaption("");
    $objServlet->objSuccessLabel->SetCaption("Thank you,
    your details have been saved. Your
    subscriber ID is ".
    sprintf("%08d", $subID) . ".");
    $objServlet->redirectTo();
};
```

如果您阅读过第 7 章，那么前面的代码应该很容易理解。您正在创建 `Subscriber` 类的新实例，设置其属性并保存它。请注意，您正在使用 PDOFactory 来检索 PDO 对象的实例。PDOFactory 包含在 Ulysses 框架中，因此您不需要在代码中显式 `include()` 或 `require()` 它。当不带参数调用时，Ulysses 提供的 PDOFactory 变体将使用您先前在 `phpm/settings/dbaccess.phpm` 中定义的数据库设置，因此现在是一个很好的时机来再次检查您是否正确输入了它们。

保存后，代码会通过测试其 ID 来检查数据库中是否创建了有效条目。有两种可能的路径，如下所示。如果不成功（即未保存），则源 servlet 的状态将设置为错误消息，并执行重定向。如果成功（即已保存），则源 servlet 的状态将设置为空白（即无错误），并将 `success` 文本标签设置为祝贺消息。

## 返航

最后，您可以通过填写没有任何错误的表单并提交它，向自己证明一切都能正常工作。

您应该会看到类似图 14-3 的内容。

您可能需要检查底层的 PostgreSQL 数据库，以确保记录已成功写入，并且数据库中的 ID 与屏幕上显示的一致（图 14-3 中为 52）。

## 快速摘要

好吧，这就是全部了——Ulysses 框架概览。请回想本章早些时候您考虑过的大多数框架的关键特性。Ulysses 在每种情况下能多大程度地符合要求？

# 第二部分：学习高级开发技术

![](img/a1b732997d9cb194dceec0570dc79710_383_0.png)

图 14-3 提交正确表单后的结果

- *应用程序结构* — Ulysses 使用类似于 Java servlet 的 servlet 隐喻。这样做，它将 PHP“脚本”的原始概念丢进了垃圾桶——并在过程中强制执行严格的结构。对于实用程序类和业务目标等内容，有一些强制性的目录组织要求，但程度不像某些其他框架那样限制。

- *代码与显示逻辑分离* — Ulysses 应用程序中的每个 servlet 都有对应的模板。事实上，此类模板大致基于 Smarty 平台。由于模板是通过在页面上放置控件来构建的，因此该模板范式被严格执行。确实，任何尝试将 HTML 代码放入 servlet 中的行为都会导致解析器错误。

- *验证* — 这是 Ulysses 较弱的一个方面。没有内置的验证系统——相反，您被鼓励自己编写或使用 PEAR。话虽如此，页面控件隐喻使验证变得异常容易，并且得益于 servlet 隐喻，向用户展示错误的过程也少得很多麻烦。

- *URL 重写* — Ulysses 不仅内置了 URL 重写，而且与许多其他框架不同，它是非可选且完全透明的。这确保了一定程度的安全性。用户无法尝试自行调用控制器 PHP 脚本，许多跨站点脚本（XSS）漏洞也因此被彻底消除。

- *表单持久化* — 这是 Ulysses 的强项：它是完全自动的。每个向另一个 servlet 提交表单的页面 servlet 都会在提交时自动保存其状态。这意味着每个文本框、标签、复选框、单选按钮、下拉列表——实际上任何控件——的值都将保存到用户会话中。即使用户随后导航到另一个页面，然后再返回表单录入页面，该状态也会被透明地保留。

- 对象关系映射 — Ulysses 逐字复制了您之前在这本书中遇到的 DataBoundObject 类——它包含在您之前下载的归档文件中。话虽如此，您可以自由使用自己的类。与许多框架不同，业务对象与页面逻辑没有不可分割的绑定，因此如果您希望使用 PEAR 的 active record 类，可以轻松做到。

- 数据库抽象 — 作为一个特定于 PHP 6 的框架，Ulysses 本身不提供任何数据库抽象层。PHP 6 的最佳实践是使用 PDO，这正是您被期望去做的。如果出于某种原因，您更喜欢使用另一层，或干脆不使用任何层，那也没关系——同样，Ulysses 不会过度介入数据库访问。

- 实用程序类 — 最后，Ulysses 在提供实用程序或“助手”类方面表现如何？表现不佳，但这是出于设计考虑。这是一个异常轻量级的框架，仅 18KB，因此，作者被鼓励要么编写自己的类，要么使用 PEAR 仓库。

## 其他一些竞争者

您现在已经详细了解了 Ulysses 框架，并构建了一个展示其一些精巧功能的示例应用程序。确实，这是本书作者最喜欢的框架——我们自己每天都在使用的框架。它确实做得很出色，但考虑到您最终仍需编写大量代码，有时您可能会觉得它有点过于轻量。这种“轻量化”赋予了您巨大的灵活性——但有些人可能更喜欢真正的“点射式”编码。

此外，虽然 Ulysses 可免费下载，但免费文档并不存在。它仅提供给商业客户，并附带电话和电子邮件支持——这意味着您需要付费购买。

最后，虽然它在世界各地被大量使用，但 Ulysses 并未获得官方 PHP 社区内任何人的官方认可——这意味着，偶尔，客户的 IT 部门可能会对其选择皱起眉头。

考虑到这三个因素，公平起见，值得再看看另外两个框架。您不会遇到与刚才查看 Ulysses 时同样详尽的内容，但在接下来的两种情况下，您都被邀请作为练习重新创建示例新闻通讯注册应用程序。这应该能让您了解自己更喜欢哪个。

当然，外面还有数以百计的其他框架。一个出色的在线资源 www.phpframeworks.com 维护着最常用框架的最新数据库。如果您有时间，欢迎随时尝试。

## Prado

Prado 框架（www.pradossoft.com）专为 PHP 5 设计，编写本文时尚未提供 PHP 6 版本。不过，它应该完全向后兼容。

它是一个基于组件且事件驱动的框架，与 Ulysses 有一些相似之处，并且是大型数字广告公司在其自身开发中使用的最流行框架之一。因此，它也是渴望的年轻软件工程师简历中最常见的框架之一。




Prado 使用一种“脚手架”应用程序，如果你曾经接触过 Ruby on Rails，这可能对你来说并不陌生。该应用程序在你选择的目录中创建一个骨架应用程序，这是你用来构建自己的项目的基础。它包含一个控制器 — `index.php` — 生成在你的应用程序根目录中，用于渲染每个页面。

就像 Ulysses 有 servlet 的概念一样，Prado 也有自己对请求的比喻 — `pages`。每个页面由一个 `.page` 文件（即其 HTML 模板）和一个 `.php` 文件（包含页面本身的逻辑）组成。

Prado 页面模板使用页面组件 — 按钮、标签、文本框等。不过，与 Ulysses 不同，这些组件是事件驱动的。也就是说，每个组件都会绑定一个事件来处理诸如 `onclick` 之类的事件 — 很像 Visual Basic 应用程序。这种绑定在模板中进行，但实际的事件代码放在代码隐藏文件中（即该页面对应的 `.php` 类）。

与 Ulysses 类似，可以从事件中修改控件的状态，从而延续 Visual Basic 风格的快速应用程序开发比喻。在 Prado 中，这被推向了更极端的程度。页面上的文本链接甚至可以被赋予 `onClick` 事件，与 ASP.NET 一样。旧的 `GET` 和 `POST` 模式基本上被淘汰了。

这种方法的一点缺点是，Web 根本不是为事件驱动编程设计的。因此，Prado 可以“监听”的许多事件（如同在 .NET 中一样）严重依赖 JavaScript 的使用。这可能会影响你网站对残障人士的可访问性，并可能对搜索引擎优化和收藏产生影响 — 这只是需要注意的一点。

话虽如此，Prado 功能强大、简单易学。它也是构建应用程序最快速的方式之一。它不如 Ulysses 那么轻量级，也没有如此复杂的页面状态管理技术，但可以说它的使用更为广泛 — 在选择框架时这是一个重要的考虑因素。

一个简短的“hello world”演示影片可以在 `www.pradosoft.com/docs/movies/HelloWorld.mov`（QuickTime 格式）中找到，值得一看。

## Zend Framework

Zend 框架 (`http://framework.zend.com/`) 是 PHP 最接近官方认可框架的东西。这是因为它来自 Zend，即编写 PHP 核心引擎的那些人。把框架组装起来的人也参与了 PHP 的开发 — 所以他们知道自己在说什么。

Zend 框架可被称为“传统”MVC 框架。如果你曾经使用过 Java，很可能也用过 Struts。Zend 框架与 Struts 有明显的相似之处，这绝非巧合。它的设计初衷是易于采用，这意味着过去使用过此类传统 MVC 框架的人应该能够毫无困难地上手。相反，那些只熟悉 Ulysses 或 Prado 的人会觉得它更具挑战性，因为它不是事件驱动的，也没有简单的“页面和页面组件”模型。

在 Zend 框架中，一个 *前端控制器*（实际上由两个文件组成：一个主索引页面和一个引导程序）处理所有 HTTP 请求 — 没有例外。作为其逻辑的一部分，它检查 URL 并尝试将控制权移交给进一步的 *页面控制器*。因此，一个应用程序由多个页面控制器组成，它们都处理站点功能的不同部分。这就是 MVC 范式中“控制器”部分的含义。

Zend 框架中的模板实际上只是 PHP 文件 — 只是带有 `.phtml` 扩展名以避免混淆。因此，在这样的模板中，完整的 PHP 功能都可供你使用 — 这是一把上了膛的枪，为了遵循最佳实践，必须极其小心地对待。这就是 MVC 范式中的“视图”。

“模型”才是有争议的地方 — 你或多或少被迫使用 Zend 的内置功能来将类映射到数据库表。它与你在本书前面遇到的 ORM 完全不同，而且肯定可能不合你的口味。

Zend 框架算得上是一个庞然大物 — 提供了丰富的验证、持久化、ORM 以及更多功能。可以公平地说，它是企业级的 — 外面有许多大型应用程序正在使用它 — 而且因为它来自 Zend，它基本上会长期存在，并且在过程中得到良好维护。

有两个重大缺点。首先，要么采用 Zend 的方式，要么走人。与 Ulysses 和 Prado 不同，很难摆脱官方认可的 Zend 框架路线 — 所以，例如使用自己的 ORM 类绝对不行。其次，不要以为不写代码就能节省宝贵的时间 — 你做不到。Zend 应用程序按 KLOC 计量（千行代码）是最大的一些。Zend 框架更多的是关于强制执行“做事方式”，而不是为你提供有用的捷径来实现即时应用程序满足感。

这绝对是一种需要培养的口味，因此，与往常一样，最好的建议是亲自试试。`http://framework.zend.com/docs/quickstart` 处的快速入门指南应该提供你重新创建本章前面遇到的新闻通讯应用程序所需的一切。来杯浓咖啡，开始吧。

## 部署注意事项

请记住，大多数 PHP 框架（包括本章中提到的所有框架）通常都有相当深入的服务器集成要求。这意味着它们可能需要安装到 root 拥有的目录中（例如 `/usr/local/lib/php`）、更改 Apache 或全局 PHP 配置，或安装 PEAR 或 PECL 依赖项。

这基本上排除了在共享托管环境中使用框架；但是，随着虚拟专用服务器价格从每月 20 美元起，这可能不是什么大问题。

不过，请考虑两件事。第一（也是最重要的是），版本管理的乐趣。更勤奋的框架作者会保持他们的框架是最新的，在这样做的同时，通常每几周就会发布一个新版本 — 有时伴有新功能，是的，但通常伴有错误修复。你显然希望保持最新，但如果框架的新版本“破坏”了你的代码怎么办？还要考虑，如果你的开发环境运行的版本与生产环境不同，你将如何应对 — 你是否会遇到 *在我机器上可以运行* 的情景？如果你有一个要部署的新版本应用程序，它使用了较新版本的框架；你会先部署哪个到生产环境？是新的框架版本，还是你的新代码？很可能，你必须在做这两件事时让整个网站暂时停机几分钟。

对于较大的项目，还要考虑你可能根本无法完全控制生产环境。这在部署到由大型公司运营的生产环境时尤其正确，这些公司的 IT 部门通常希望保留对所有 Web 应用程序托管的控制权。你可能以前遇到过这种棘手的状况 — 也许你在 Linux 上开发，而你的客户使用 Solaris 服务器。使用 PHP 框架增加了一个全新的维度。你需要提前向客户说明你关于安装所选框架、Apache 和 PHP 配置更改以及 PEAR 类安装的要求。当然，这都可以做到 — 这只是要添加到你的待办事项清单中的一件事。

说了这么多，你的客户的 IT 部门可能会如释重负地听到你使用的是行业认可的框架。如果他们将来继承你的应用程序，这将使他们更容易维护。

## 摘要

在这个关键章节中，你被介绍了 Web 应用程序开发框架的概念 — 特别是那些为使用本书讨论的一些最佳实践方法来开发 PHP 应用程序提供开箱即用工具包的框架。

你了解了框架提供的设施 — 强制结构、数据库抽象、表单验证、MVC 路由和 ORM。此外，你了解了使用框架而非自己开发的好处，尤其是对于较大的项目。然后你遇到了几种现成的框架，它们都是免费的，并学习了如何在其中实现一个简单的 Web 应用程序。在这样做的过程中，你看到了每种框架的优缺点，很可能得出的结论是“没有一种是完美的”。

尽管如此，每一个都比试图重新发明轮子要好。因此，请记住这一点，你应该考虑在任何中大型 PHP 应用程序中部署它们 — 特别是拥有大型分散开发团队的应用程序。

在第 15 章中，你将开始动手实践 — 也是时候了。你将以最引人入胜的方式将过去 14 章的理论付诸实践 — 一个真实的、活生生的项目。那么，欢迎来到小部件的精彩世界。





# 第三部分

## 真实世界案例研究

- 第15章：项目概览
- 第16章：项目管理
- 第17章：项目规划
- 第18章：系统架构
- 第19章：构建应用程序
- 第20章：质量保证与测试
- 第21章：部署

## 项目概览

在本书的前两部分中，你学习了在 PHP 中构建企业级 Web 应用程序的基础知识。

你从第一章开始，全面了解面向对象编程（OOP），不仅学习了为什么它是大型项目的正确方法，还了解 PHP 6 提供了相对健壮的实现供你使用。随后，你转向数据库，了解 PDO 如何提供一种数据库抽象层，而 ORM 提供了另一种。最后，你学习了有效软件架构的原则，包括如何最佳实现会话管理和模型-视图-控制器（MVC）项目布局。

希望在学习过程中，你注意到各章中散布着大量简短示例，用以演示正在讨论的概念。如果你当时没有尝试那些示例，现在强烈建议你马上去试试。你会发现，当到编写软件的时候，这样做能让知识点更好地掌握。

不要自欺欺人——编写软件是件困难的事。如果它很简单，你就不会费心阅读本书，而我们此刻早已被机器奴役了——所以请庆幸这并非一件轻而易举的任务。

为什么软件开发会很困难？它不需要购买颜料或画布，几乎不受物理约束。它本应是终极的空白画布。然而，你最大的障碍之一，就是在逻辑上把自己逼入绝境。本质上，你自己的头脑就是你最大的敌人之一。

另一个限制是时间。虽然从技术上讲几乎没有什么是超出你能力范围的，但作为凡人，你不可能在短短两周内亲手创造出像 GNU/Linux 操作系统整体那样强大而灵活的东西。

此外，这个软件是为谁编写的？是你自己？你的朋友？一个非常常见的场景是为客户编写定制软件。本章中用作示例的虚构客户名为“小部件世界”。它所呈现的场景非常普遍，因为大多数软件并非面向消费者编写，而是为了满足企业、政府和其他组织的规格要求。

本章假设你是一个普通开发人员，在一家普通公司从事一个普通项目，服务于普通客户。不过，为求简单，这个示例项目具有一些也许不常见的特征：

- 你正在开发一个新产品。（一种更常见的场景是要求你修改当前现有的系统。）
- 你独自工作（因为你是独自阅读这段文字）。在现实世界中，你很可能会与其他开发人员紧密合作或进行对接。

### 小部件世界

小部件世界设计、生产并销售小部件。它拥有一支专注且分布式的销售团队，团队成员遍走全球，参加最新的小部件展览会，并主动接触小部件友好型企业。小部件世界采用传统的冷电话推销方式，并建立起基层郊区小部件仓库销售聚会网络。

小部件世界也是自身成功的受害者。像许多企业一样，它没有为两位数增长做计划，并且未能让销售团队及时获得有关销售机会和最新小部件技术的信息。它也无法从销售人员那里快速、及时地获取反馈，以便抓住小部件时尚趋势。

小部件世界无法雇佣足够多的暑期实习生来操作电话和传真机，以保持小部件业务的运转。小部件大师深知小部件世界需要提高效率。因此，在研究了商业产品后，小部件大师决定委托编写一款名为小部件世界销售自动化工具（WW-SFAT）的专用软件。

虽然小部件大师掌握着预算权，但她利用小部件市场部来预测最新趋势，进而帮助规划小部件世界的发展路线图。

小部件市场人员依赖区域小部件销售经理（东部和西部）为他们提供最新信息。小部件市场人员还会让经理们了解相对于竞争对手的小部件定价。

区域小部件销售经理通过及时提供有关小部件热点的信息来奖励和激励其小部件销售人员。他们还设定销售配额、发放奖金支票，并确保所有销售人员都竭尽全力让每台桌面上都摆放一台小部件。

WW-SFAT经理是一个新设立的职位，汲取了小部件市场部和区域小部件经理的意见。WW-SFAT经理负责制定一套流程及配套软件，以解决自动化简化小部件世界销售团队日常运营流程的问题。

WW-SFAT经理还被赋予了重大（且至关重要）的“一锤定音”权力——WW-SFAT经理的决定即为最终决定。这项权力对项目的成功至关重要，因为它限制了所需会议和文档的数量。WW-SFAT经理还致力于与你紧密合作开展本项目。由于你对小部件或销售一无所知，并且负责简化小部件世界销售团队现有的基于纸质的电话和传真销售人员及联系人跟踪系统，你心中充满了疑问。图 15-1 显示了当前使用的跟踪表格。

![](img/a1b732997d9cb194dceec0570dc79710_391_0.png)

图 15-1：当前的小部件世界跟踪表格

你可能会产生以下一些疑问：

- "您希望以12小时制还是24小时制查看时间？"
- "不同时区是否重要？"
- "X 的报告应在什么日期前提交？"
- "如果 X 的报告在*不*按要求日期前提交，会发生什么？"
- "费用如何报销？"
- "联邦里程报销标准变更频率是多少？"
- "联邦里程报销是否需要具有历史性？是否需要追溯？"

### 小部件世界版图

以下讨论详细说明了小部件世界版图的构成。这些包括技术层、财务层和政治层，以及你在其中的角色。

### 技术层

如果你一直密切关注，你会注意到信息需要从小部件销售人员向上流向小部件大师，然后再向下传递。在此例中，信息流绝对是双向的：

- 小部件市场部需要按地区汇总的销售信息。
- 小部件销售经理需要跟踪其人员的各个方面。

### 财务层

该项目应通过提高员工效率为小部件世界节省资金，这正是小部件大师愿意在该项目上投资的根本原因。然而，目前尚难判断什么能更快地节省资金——是向小部件世界销售人员提供更多信息，还是从他们那里接收更多信息。

### 政治层

一位小部件区域经理私下不信任小部件市场部。他认为，小部件市场部会利用他提供的信息作为提前让他退休的工具。小部件销售人员欢迎使用硬数据来展示其工作努力程度——这能让区域经理保持诚实，并表明谁是基于裙带关系而非绩效获得晋升。小部件市场人员希望制作带有精美图表的新闻稿，以便向高尔夫伙伴展示。

### 你

你是通过回应当地报纸上一则“小部件世界需要销售自动化工具开发人员”的广告而获得这份工作的。WW-SFAT 经理联系了你，你通过了小部件世界的技术考试（部分得益于你对 _Professional PHP 6_ 的专注学习），并满怀热情地开始了新的软件开发职业生涯。

此刻正值周一早上 8:00，你再也不会这么天真了。

### 这真的是关于技术吗？

WW-SFAT 的需求大致包括以下内容：

- [ ] 销售联系人报告
- [ ] 销售线索报告
- [ ] 通过电子邮件、BlackBerry、传真和 Web 报告分发的销售联系人管理列表
- [ ] 基于销售业绩的小部件生产信息流
- [ ] 小部件市场报告及全彩、亮面、可直接打印的图表
- [ ] 小部件会计报告
- [ ] 培训

这实际上是一种常见场景的体现：一个典型项目，采用一流的开发技术来让客户满意。然而，尽管“客户”看起来可能与 WW-SFAT 经理毫无二致，但客户并非孤立存在。这里的所有参与者都对项目各自部分的结果有切身利益。

### 开发方法

你将开始使用极限编程（XP）所代表的一些开发实践。不要被名字迷惑。XP 是一套敏捷开发方法论，以下实践列表最好由肯特·贝克和辛西娅·安德斯在 _Extreme Programming Explained: Embrace Change, Second Edition_（Addison-Wesley，2004 年）中描述：

- [ ] 规划——通过结合业务优先级和技术估算来确定项目范围，并持续更新。
- [ ] 小版本发布——让最终用户尽早开始使用系统，并在非常短的周期内发布新版本。





- 简单设计 — 始终尽可能保持设计简单。复杂性将持续被移除。

- 测试 — 开发人员不断编写单元测试，以确保系统随时都能无瑕运行。客户编写测试以证明功能按要求工作。

- 重构 — 在不修改行为的情况下重构代码，以保持易读性、消除重复或简化代码。

- 驻场客户 — WW-SFAT经理是你团队的一半成员，随时可用，以回答与业务相关的问题。

这些实践使您能够管理项目和正在开发的软件的复杂性和范围。典型系统的流程类似于图 15-2 所示曲线。通过从多个不同角度管理复杂性，您可以使曲线发生巨大变化，如图 15-3 所示。

![](img/a1b732997d9cb194dceec0570dc79710_394_0.png)

图 15-2: 典型系统流程

![](img/a1b732997d9cb194dceec0570dc79710_395_0.png)

图 15-3: 通过管理复杂性改变曲线

按需创建功能是管理系统复杂性的绝佳方式。以后添加功能的成本并不会比现在高出多少（无论流程中的“现在”指何时），这意味着你不必猜测你认为将来需要什么，并可以避免构建一段时间内都不会使用的功能。

可以这样想：使用传统的复杂性方法，如果现在添加一个功能的成本（按时间计算）是5.00美元，而以后同一功能的成本是100.00美元，那么现在添加它更安全；但如果你能设置成本，使得现在添加同一功能的成本是5.00美元，而以后添加的成本是6.00美元，那么现在添加它收益甚微。暂时省略它；你的系统保持更简单，你最终只会拥有从一开始就被使用的功能。

## 这对你意味着什么

请首先考虑由Winston W. Royce博士首次记录的传统瀑布方法（参见“管理大型软件系统的开发：概念与技术”，IEEE WESCON论文集，1970年8月）。图 15-4 表示这一概念，它要求如下：

- 两周收集需求
- 两周分析和辩论需求
- 两周设计系统
- 八周编码
- 四周质量保证（QA）和其他测试

![](img/a1b732997d9cb194dceec0570dc79710_396_0.png)

图 15-4: 瀑布方法

尽管它非常严格，但瀑布模型往往被实施为散弹枪式方法，并且有几个弱点：

- 它缺乏灵活性，并假设设计第一次就会做正确。阶段之间相隔数周，几乎没有时间用于反馈循环——而且，事后诸葛亮当然很容易。
- 很难预测所需功能，因为需求很可能会改变。

这当然听起来几乎像是注定失败，这就是为什么你将遵循Kent Beck的原则（前面列出过），以便在编写代码时创建一个小型、灵活且经过彻底测试的系统。你将与你的WW-SFAT经理密切合作，并得到所有需要的问题的解答。你的WW-SFAT经理拥有广泛的Widget World业务经验，并将每天使用该系统。

这也意味着你将修复看到的问题并移除不再需要的功能。你将坚持“一次且仅一次”规则，这意味着你将合并重复的逻辑，并且会毫不留情地这样做。毫不留情地重构将使你的整个系统保持精简且强大。

最后，你将拥有你的单元测试。通过测试你创建的每一个功能模块，你将始终拥有一个经过完全测试的系统。一个经过完全测试的系统非常强大，因为它让你对由次要或三级错误引起的断裂和症状有敏锐的认识。当出问题时，一个经过完全测试的系统会立即让你知晓。

拥有一个编写良好的测试套件作为安全网，使你能够大胆地修改功能。测试套件并不会不必要地束缚你，而是允许你成为一名更大胆的开发人员，让你在业务需求变化时（以及在需要时）朝不同方向推进你的系统。

这其实只是对XP（极限编程）的一个10分钟介绍，XP是一种更敏捷的开发方法论。如果你对刚才读到的内容并不完全认同也没关系，因为你将在接下来的几个章节中探索这种方法论如何真正见效。很快，你就会发现，通过使用这里描述的实践，你不仅能交付小型、快速且灵活的软件，还能采用一种使客户能够积极参与开发过程的流程。

## 技术

尽管你被警告过不要过早构建太多内容，但以下是你将要接触的一些技术特性：

- 统一建模语言（UML） — 在适当的地方，设计快照（类图和序列图）将以UML展示。有快速备忘单可用。
- 设计模式 — 这包括如何有效地使用它们并在你的代码中识别它们。
- 集合和迭代器 — 它们在哪里合理以及在哪里不合理
- 调度器 — 只是为了体验一下事件驱动编程
- 简单对象访问协议（SOAP） — 这将用于其中一个数据源。

## 总结

现在你了解了Widget World及其业务需求的背景，你很快就可以开始运用这里简要概述的开发技术。

不遵循严格的瀑布开发方法，你可以采用一种更灵活的方法，强调快速发布、简单设计、经过良好测试的代码库、对持续代码改进的承诺，以及一种能够与客户保持持续反馈的手段。

利用这种方法，你可以开发出一个在首次发布时就能交付业务价值的应用程序，其价值可用天和周来衡量，而不是月和年。

那么，接下来呢？你可以着手制定项目计划——所有这些艰苦工作将确保你的项目按时、按预算、高质量交付——但在你全身心投入之前，先了解是什么使项目真正成功，这要好得多。

在第16章中，你将开始学习这些 —— 一系列通常称为*项目管理*方法论的技术。你将只有一章理论内容，然后再回到规划工具本身。只有那时，你才能打开你最喜欢的编辑器，实际构建该工具。

## 项目管理

许多传统的Web项目负责人来自项目管理背景。他们离开大学或学院后以“初级制作人”身份进入行业，并逐步晋升，最终获得自由度和权限来运行自己的项目。但是，尽管许多优秀的项目管理专业人士确实走过这样一条道路，近年来却出现了一种趋势：软件开发专业人员“转行”——即放下开发工具，转而有机会带领一支由前同事组成的团队，并在项目的成败（或失败）中发挥关键作用。

确实，如果实话实说，这样的发展是非常受欢迎的。如果你作为软件开发人员曾对自己的项目负责人感到沮丧，很可能是因为他们“根本不懂”。在实践中，无论项目经理多么有才华，如果他们没有编写代码的经验，他们往往很难理解你的观点。

即使你永远不需要管理自己的项目，了解项目经理（即掌控全局的人）每天必须面对的事情也会非常有用。理解并同情运行一个成功的开发项目从开始到结束所需的技能，将使你作为软件架构师和个人变得更强大。

此外，如果有一天你发现自己负责一支充满朝气的年轻开发人员团队，你会发现本章和下一章所获得的技能将对你大有裨益。

本章讨论如何将业务需求汇总为一份连贯的简报，以及如何用一份坚如磐石的规格说明书和项目计划做出恰当回应。你将学习如何识别和选择将向你汇报的关键人员，以及如何在整个项目生命周期中指导和管理他们。你还将探讨几种编程范式，了解如何评估其对你自己项目的有用性，并探讨应对车间开发工作的两种关键方法。最后，你将发现如何有效地管理与客户的工作关系。





诚然，本章与 PHP 6 的具体细节关系不大。尽管如此，此处涵盖的内容与你可能参与的任何 PHP 项目都非常相关，尽管所示技术同样适用于 ASP.NET、Java——任何语言。它们之所以仍被收录于此书，是因为它们很可能会彻底改变你处理大型项目的方式。

## 做好家庭作业

通常，一个项目最常见、最显眼的第一步是项目经理告诉开发团队中的高级成员，他有新的事情要团队去做，这往往不过是在茶水间旁或吸烟休息期间的一次非正式闲聊。当然，在实际中，项目的创意起源要早得多。追溯任何给定项目的根源是至关重要的。只有从项目一开始就应用项目管理方法论，才能取得成功。

在采取步骤接收项目的正式简报之前，有几个关键问题需要问——你可以称之为你的“家庭作业”。这些问题合在一起将构成你在接收正式简报时所调整的策略基础。需要问的第一个问题是：“为什么？”

## 项目为何启动？

这个简单问题对你从现在开始所做的每一件事都有巨大影响，因为你处理和构建项目（从开始到结束）的方式应由其预期功能决定。

新 Web 站点或应用程序需求背后的典型场景可能包括以下内容：

- 为启动一个新业务，而该业务的核心就是应用程序
- 替换一个正在失效或已不再足够的现有应用程序
- 接手一个现有供应商未能按时、按预算或按要求交付的项目（在某些情况下，甚至三者皆未）

当然，还有其他原因可能需要启动新项目，且并非所有原因都像此处列出的三个那样关键。例如，你可能只是发现自己不得不实施某位副总裁或高管的宠儿项目。无论是什么，确定项目的 *存在的理由* 都是头等大事。

## 项目是为谁而做？

这个问题的答案有时不像你想象的那么容易。在最简单的层面上，该项目是为你自己公司或组织的另一个部门、新客户或现有客户而做。请记住，你必须从实际谁委托了工作的角度来识别项目的接收方。如果一个男人去商店给妻子买指甲油，他不是真正的客户——他只是在执行真正客户的请求。

同样，你的客户可能仅为了满足其负责的第三方的某些要求而委托这项工作。产品的这些最终终端用户被称为 *领域专家*，忽视他们将自食其果。

你的产品的最终用户通常将是客户组织中最实际动手的人，因此，他们对项目的需求往往与作为潜在供应商接近你的申请人有着巨大的不同。

### 识别角色与议程

举例来说，假设你是中型组织的首席技术官（CTO），并且已由人力资源（HR）总监委托为你的整个公司构建一个新的内联网。你可以使用全职员工和合同员工。你认为每个角色（你、客户和领域专家）的各种议程是什么？

稍微带点愤世嫉俗的角度来看，这种情形很可能是这样的：

- 作为开发者的你，希望尽快且以最少投入交付高质量、有效、高效且令人满意的解决方案，以便在客户、同事和老板面前表现出色。
- HR 总监希望你交付一个高质量、有效、高效且令人满意的解决方案，让他或她体面。
- 内联网的日常用户（领域专家）希望你交付一个高质量、有效、高效且令人满意的解决方案，它能按照他们的意愿运作。

请注意，这里唯一真正无私的议程是由领域专家持有的。秘诀在于确保满足所有三个议程。前两个非常容易满足；最后一个最困难。但通过专注于第三个，前两个通常会迎刃而解。

因此，这就是你的关键所在：*关注领域专家*。你设计或构建的一切，以及在过程中做出的每个决定，都应牢记领域专家。当然，*你* 可能使用 Pico 编辑文本文件，或使用 Google Chrome 浏览 Web，但你的用户呢？可能不会。与其站在道德制高点（“好吧，他们*应该*使用 Pico”），不如交付他们实际想要和需要的东西。

认识到“说得对”与“做得对”之间的区别，正是区分卧室程序员与软件开发专业人士的关键。

### 利用角色为己所用

请考虑：你的客户只是项目中连接领域专家的渠道，无论他或她还会告诉你什么。虽然客户在交付时表示对你构建的东西非常满意并离开要容易得多，但如果领域专家不喜欢，斧头将落在客户头上——而随后，几天、几周或几个月后，斧头也会落在你头上。从一开始就代表领域专家的需求，对客户来说极其有利。

一个好的客户将能够同情其领域专家的真实需求和要求，并将它们汇集成一个单一、和谐的声音供你倾听。然而，在实际中，你需要推动、探询和劝说客户，以便恰当地代表其领域专家的现实和合理需求。

如果你觉得你的客户没有充分代表其领域专家，那么建议他或她重新实施咨询过程至关重要。这可以通过以下方式实现：

- 头脑风暴会议
- 匿名建议箱方式
- 任命一个工作组来代表领域专家的需求，并让他们参与项目过程

如果角色从一开始就没有明确划分，帮助划分它们至关重要。这样，当你收到项目的正式简报时，你就能放心地回应它，因为你知道你回应的实际上正是真正需要的东西。

## 项目的历史是什么？

同样重要的是，要确定这个项目是否带有任何包袱。新项目总是令人兴奋，但它内部可能不像外表看起来那样新。很好地掌握项目历史，能使你相应地调整方法的某些方面。

一般来说，只有先前曾尝试过启动该项目——即一次错误起步——时，该项目才会带有严重的包袱。如果你知道情况属实，那么无论之前的尝试是在多久以前，都应立即意识到以下潜在包袱：

- **已离职员工**——如果该项目之前由已离职、被解雇或被调往组织内其他岗位的员工处理，请小心。几乎不可避免地，客户会认为前任员工未能完成其指定的任务。这里的诀窍是，充分了解客户提出与你合作的新代表的优缺点。本章稍后将更多地讨论这一点。
- **已离职供应商**——如果你是作为另一供应商（无论是商业供应商还是内部供应商）的替代者来承接该项目，那么值得评估客户当初为何放弃该供应商；或者，确实，为何该供应商放弃了客户——这种情况时有发生。如有必要，与该供应商的其他前客户打听情况，了解他们的经历，并根据你获得的任何有用信息来塑造你的方法。客户希望从一开始就信任你，所以给他或她一个充分的理由。
- **与内部员工合作困难**——如果某公司将项目外包给你，你可能会在与该客户公司的 IT 部门合作时遇到困难。有时即使公司内部从未尝试启动该项目，但人们认为本应启动，也会出现这种情况。最好的建议是从一开始就让该 IT 部门参与进来。在撰写技术规格说明书时给该部门打个电话——这样会让他们完全措手不及，甚至可能因此成为巨大的帮助。





## 项目预期前提条件是什么？

你应尽早在项目生命周期中了解这些，因为它们甚至可能影响你是否愿意继续。一些典型的前提条件可能包括以下内容：

- 平台 — 客户是否要求项目使用 ASP.NET、J2EE 或其他你作为 PHP 专业人士不太熟悉的开发语言来构建？这可能有合理的商业原因，这也是判定 PHP 不适合某项工作的最常见原因
- 部署 — 客户是否需要将此应用程序部署到现有服务器上？如果是，客户是否愿意在必要时让你重新配置这些服务器？
- 时间表 — 客户从一开始是否对交付有任何特定期望，可能是为了满足某些内部目标或截止日期？
- 预算 — 客户是否有特定的预算？它是否现实？

在着手接收简报流程之前，建立这些前提条件非常重要。毕竟，如果你无法满足前提条件，进入下一步就几乎没有意义了。

## 接收正式简报

做好功课后，你应该接收正式简报。任何简报最重要的部分是将其文字化。到这一阶段，你可能已经收到了大量关于项目的信息，但将简报文字化，可以确保你和你的团队以最有效的方式做出回应。

如果你的客户只愿意当面简报，而不提供任何书面文档，请务必做详细笔记，然后将其整理出来。

然而，初始简报很少会以令人满意的形式呈现——无论是口头还是书面。因此，通常需要你将客户的意愿转化为大家都能使用的连贯简报。与其将其作为单独的文档，不如最好将其作为你的演示的一部分，这将在后面探讨。

让客户阐述其需求是项目经理最艰难的工作之一。更糟糕的是，客户很少区分你基于信息缺失做出的错误假设和那些纯属错误的假设。解决这个问题的办法是确保你在演示中做出的所有假设和猜测都基于你可获得的最佳和最详尽的信息。因此，你必须在这个早期阶段彻底提取客户业务需求的细节。

尽可能在编写简报和回应之前，争取与客户进行电话交谈，或者理想情况下进行会面。

如果你有幸通过与客户的电话交谈或会面来构建正式简报，那么提出正确的问题非常重要。你必须关注这里涵盖的若干关键领域。在涵盖这些之后，你就可以编写简报了。

## 业务需求

在这个阶段，确定你正在构建的系统或应用程序的具体广泛需求。专注于询问关于领域专家目标的问题，而不是客户心中预期的解决方案。

即使你推荐的解决方案与客户预期完全不同也没关系，只要你能以“因果”基础精确地将你的决策映射到领域专家的目标上。这些映射构成了你整体解决方案依据的基础，是演示的关键组成部分。

提出引导性问题。尽量多听少说。客户不加提示的随想在优化你的提案以最好地满足其需求方面可能非常有用，甚至在潜意识层面也是如此。尽量进行商业和后勤探询的强烈混合。例如，以下通用问题可能有用：

- [ ] 你考虑过哪些其他解决方案？
- [ ] 你为什么拒绝了它们？
- [ ] 这个系统的最终用户是谁？
- [ ] 目前没有系统的情况下，您如何处理这个流程？
- [ ] 你认为该系统可能带来哪些好处？
- [ ] 你期望何种投资回报率？
- [ ] 你将如何衡量该回报？
- [ ] 对于想要向你提供此解决方案的供应商，你最重要的三个要求是什么？
- [ ] 你考虑过多少其他供应商？
- [ ] 对迄今为止收到的提案，您满意吗？
- [ ] 你选择供应商的时间表是什么，是什么在推动这个时间表？
- [ ] 哪些人可能参与决策过程，他们的角色是什么？
- [ ] 你对该项目推进最大的担忧是什么？
- [ ] 其他供应商是否已令你满意地解决了这些问题？

再次，不要害怕让客户说大部分话。尽量避免在记笔记时让个别要点被遗漏。相反，提出探询性问题，从客户那里榨取“额外的百分之十”。

以下是供应商和客户之间的示例对话：

供应商：你选择供应商的时间表是什么？
客户：当然。我们将在三十号之前做出决定。
供应商：这个月三十号？真的吗？看来你们很想启动这个项目，是吗？
客户：肯定。我们下个月有一个大型广告活动开始。
供应商：哦，对了。这个系统可能成为该广告活动的重要组成部分吗？
客户：是的。如果到那时开发已经开始，这肯定会成为一个强有力的卖点。

对比没有额外探询的同一段对话：

供应商：你选择供应商的时间表是什么？
客户：当然。我们将在三十号之前做出决定。
供应商：很好，谢谢。

注意从探询中获得的额外信息：

客户下个月将开展一个广告活动。

客户希望能够在向潜在客户进行销售演示时展示未完成的系统。

这信息并非秘密，客户也不是故意隐瞒——只是他想起来时没有提到。但是，不要犯错——这些额外信息对你确实非常有用。

故事的寓意是，不要害怕对客户说的话表示兴趣，并提出可能让你获得额外关键信息的问题。这可能会让你在竞争中占据优势。

## 范围

在建立系统的更广泛业务需求，并明确客户试图解决或满足的具体问题或需求后，有必要进一步询问客户关于需求范围的问题。让我们明确一下这里术语 _范围_ 的含义。通过建立范围，你是在考虑为了解决那个问题或满足那个需求，你要走多远。

人们常谈论 _范围蔓延_ 或 _功能蔓延_，但在实践中这是一个被误用的短语。它实际上指的是项目中期所需内容的规模在不考虑商业影响的情况下增长。它 _不_ 指需求本身发生变化。没有一个短语来形容那种情况；那只是糟糕的规划。

通过现在建立范围，你可以尽可能防止范围蔓延。你制作的规格说明使你能够通过将选定范围映射到构建过程中将包含的特定功能组件来强制执行该范围。

范围几乎总是由时间和金钱人为限制，但在早期阶段通过划分阶段边界来帮助管理预期是一项有用的练习。十有八九，向客户建议两阶段方法可以对你大有帮助，因为客户会立即向你说明哪些功能可能进入第二阶段开发，哪些功能现在需要。只承诺后者，你就能明确定义初始范围。

如果客户不愿考虑将项目分阶段，那么需要采取更直接的方法。向客户解释，满足其要求的唯一限制是时间和金钱，现在了解项目的绝对必要组件可以让他/她更轻松，因为他/她将能够在更公平的基础上解释交付时间和成本的提案。如果没有其他供应商竞标该工作，请向客户解释，现在建立范围将节省大量后续时间，并使项目能够更快速地推进，减少规格修订次数。

在时间和预算的背景下讨论范围很重要。不要对客户说不，你可以告诉他们，他们的要求可能会延长时间表或超出预算。让我们现在来看看这些。

## 时间表

建立时间表不仅仅是弄清楚客户需要何时交付系统。即使在早期阶段，设置里程碑并与客户达成一致也至关重要。你应该尝试为以下内容制定里程碑：

- [ ] 提案所需日期
- [ ] 对所选供应商做出决定的日期（如果适用）
- [ ] 供应商需要提交任何书面规格说明的日期
- [ ] 客户签署任何书面规格说明的日期，或者如果需要修订，则提交修订意见的日期
- [ ] 规格说明过程（包括所有修订）必须完成的日期
- [ ] 供应商制作的任何设计必须提交初步批准的日期
- [ ] 任何设计（包括所有修订）必须完成的日期
- [ ] 构建必须开始的日期
- [ ] 构建必须完成至测试版标准的日期
- [ ] 构建必须完成至最终标准的日期
- [ ] 测试必须进行的日期
- [ ] 成品移交必须进行的日期

当然，向客户询问所有这些日期可能会让他们不知所措甚至感到烦恼。为避免这种情况，选择你认为关键的里程碑，并自行填补空白。你甚至可以在这个早期阶段通过宣布日期将如何配合，对客户对你流程的看法产生积极影响。请考虑以下对话片段：



供应商：您何时需要交付完成的系统？
客户：我们需要在六月一日前让员工上手运行。
供应商：那样的话，我们应该争取在五月二十二日前将系统交付给您，以便留出几天时间处理可能需要的任何最后时刻的微调和更改。

在简报过程中，不要忘记仔细记录所有里程碑，并在必要时引导客户远离不切实际的预期，如下例所示：

供应商：您何时需要交付完成的系统？
客户：我们需要在五月一日前让员工上手运行。
供应商：我认为，鉴于我们已商定的工作范围，这个日期会比较难以达成。我建议五月二十二日的交付日期可能更贴近实际，这应该能让您在随后不久就开始运行。我认为我们有两个选择。我们可以在这一阶段缩减系统范围，或者考虑稍晚一点的交付日期。
客户：好吧，老实说，我们可以接受五月二十二日。我们宁愿第一次就把它做对。

注意，这里是如何使用被动语气向客户说明其日期不切实际的。你不是在“告诉”客户，因为对方可能会认为你在耍“我们最懂”的把戏，这可能会冒犯对方。相反，你是在“建议”，在很多情况下（如前述示例），你通常会发现比最初陈述的有更多的余地。

务必指出不切实际的日期；绝不能让它们不经检查就溜过去。客户会期望现在就指出任何不可实现的事情。如果直到书面提案出来才提及，你就有疏远客户的风险，尤其是如果他们已经把预期日期告诉了项目中其他相关人员。本质上，任何未被反驳的东西都会被视为默契同意，所以要当心。

希望你了解自己的估算能力。如果在实际中经常超出最初估算，计算超出多少，然后将此作为应急余量。如果你遵循本书中的技巧，你交付速度本身就会比竞争对手快，所以增加20%的应急余量来保护自己也没有坏处，尤其是如果你的合同对延迟交付有各种可怕的罚款条款时。

## 预算

预算可能是一个棘手的问题。即使你是在内部交付解决方案，你仍然需要考虑直接成本。许多大型公司会为内部活动互相向成本中心开账单，因此内部工作的预算和谈判可能与外部委托一样激烈。

不要过早询问预算问题。这会非常扫兴。客户预期会被问到这个问题，但他们可能会根据你提问的顺序，快速判断他们认为你作为供应商的优先事项。合适的时间可能是在提出工作范围问题附近，因为你已经确定了范围很可能受时间和金钱的限制。请记住，在整体项目预算被提及之前，你的客户可能会询问你的费率卡（即你的人员收费的费率）。你不应该回避回答这个问题。希望你对自己的收费率感到自豪；你知道它物有所值，并且它反映了你的资历。

# 第三部分：真实世界案例研究

一种不错的整体预算问题表述方式如下：“当我过去为像Acme这样的公司实施类似解决方案时，他们通常预期投资在35,000到65,000美元之间。这听起来是否符合您对该项目的预期范围？”

首先，请注意，你并没有询问预算是多少。相反，你暗示了以下几点：

- 你过去从事过类似的项目 —— *积极*
- 你过去与像Acme这样的公司合作过 —— *积极*
- 这些公司投资的金额在35,000到65,000美元之间不等 —— *中性*

在你的提问中强调积极面，这意味着与确定预算相关的任何负面想法都不会像直接提问时那样自动触发。

其次，请注意，你提供了一个大致范围。这个范围实际上相当宽泛。始终这样做；在这个阶段过于具体暗示了你对客户需求的理解带有傲慢，而你目前并不了解这些需求。通过建议一个宽泛的价格范围，你在潜意识中向客户暗示你仍未锁定具体要求。请确保你建议的最低金额是你愿意承接工作的绝对最低限度，而最高金额约为该数字的40%到50%。这样，如果客户同意，你可以肯定自己手头有一笔有利可图的工作。具体能赚多少还有待观察，没错；但你已经排除了亏本生意的可能性。

最后，请注意“他们通常预期投资”这一短语。之所以使用它而非“我们通常向他们报价”，是有充分理由的——也就是说，你在暗示这些公司实际上在与你交谈*之前*就预期会花费这笔钱，*而不是*这是你向他们报出的金额。

当然，这并未回答“贵司的预算是多少？”这个永恒问题。总的来说，它所做的是在客户心中植入一个关于项目实际市场价值的坚定概念。

一旦意识到这一情况，如果客户意识到根本没有预算来推进，他或她通常会告诉你。这本身显然不是一件好事，但它确实使你能够非常快速地判断，你花在接收简报上的时间是否物有所值。

考虑以下两种方法。在两种对话中，供应商仅为该应用程序保本就需要收取约15,000美元。客户的预算只有5,000美元。以下是第一种场景：

> **供应商：** 您心中有预算吗？
>
> **客户：** 我不想告诉您预算。过去我们这样对待供应商时，他们只是回来报出我告诉他们的那个预算金额。我宁愿您直接给出一个报价，然后我告诉您是否可行。
>
> **供应商：** 好的，没问题。

相比之下，请看以下示例：

> 供应商：约翰，我想和你谈谈预算问题。当我过去实施过类似的这类解决方案时，客户通常预期投资在15,000到22,000美元之间。这听起来是否符合您对该项目的预期范围？
>
> 客户：哦……不，真的不是。恐怕我们能承担的最大金额是5,000美元，勉强的话也许7,000美元。
>
> 供应商：好的，约翰。那样的话，恐怕我认为我们这次无法开展业务，除非你愿意大幅缩减工作范围。你可能会发现，一家较小的本地供应商会是更好的选择。

在两种情况下，供应商都拿不到生意；但在第二种情况下，供应商立即就知道没有成交的希望，而在第一种情况下，几天时间会浪费在制作全面的提案上，最后却会被拒绝。

还请注意，你为客户提供了一个替代方案——他或她可能会想要找一家较小的本地供应商。将生意让给别人可能会有点令人不快——但这是一种清新的做法。你的潜在客户会感激你的诚实，并且你可能会得到一两个意想不到的好处：另一家供应商可能会请你喝一杯啤酒，而失去的客户甚至可能在未来向别人推荐你——“嘿，我几个月前找过的这些人对我们来说太贵了，但他们可能适合你。”

不要因为询问金钱而尴尬；它是任何企业的命脉。诚实地面对这个问题，并仔细选择你的语言和时机。

## 商业条款

即使在这个早期阶段，谈论商业条款也并非坏主意。如果你已确认客户乐意支付约50,000美元来完成项目开发，这当然是个好开端——但某些常被忽略的技术细节可能会迅速浇灭这个领先优势。

付款条款确实很重要，尤其是如果你是一家小供应商。如果你的项目不涉及任何直接成本（如硬件、软件、媒体费用等），那么这只是一个现金流问题——你需要完成一项工作，然后等待付款。如果你将要购买外部商品或服务，则应确保你付出的现金不会早于你从客户那里收到付款的时间。否则，你基本上就是在给客户垫钱。

与预算问题一样，尽早解决商业条款问题要好得多。这样，如果它们证明是障碍，你现在就可以了解，并在必要时退出。以下问题可能更适用于小型企业，而非大型科技机构，但如果你有任何与付款相关的顾虑，仍然值得询问：

- “我们通常喜欢向客户收取前期百分比的费用，以便在构建过程中覆盖任何零星费用。这会成为问题吗？”
- “因为我们是一家小公司，我们必须对付款条款非常坚定。我们所有的发票严格为30天。您认为贵公司的应付账款人员能接受吗？”





再说，措辞在这里非常重要。例如，使用友好的反询句“这样会是问题吗？”强烈建议使用。你更有可能得到同情的“哦，不，我不这么想”的回应，而不是更具攻击性或敷衍的回应。

另一句常用话是“你认为这会不会阻止我们一起做生意呢？” 听起来非常情感化，但其语气暗示“不”是合适的答案，因此更有可能引出这种回答。积极的回应有用，不仅因为这是你想听到的，还因为这是客户想说的。

> > 研究表明，参与方使用积极词语和肢体语言的会议，比充斥着“不”和摇头的会议留下的印象要好得多。

通过让客户对会议留下正面印象，你也让他们对你本人留下了正面印象。

另外，与客户坦诚说明加价也很有必要。如果你在采购外部商品或服务，完全可以以较小的加价转嫁给客户，以覆盖行政成本——通常是一个固定比例（15% 很常见）。确保客户知道你在这样做。再说一次，诚实会营造信任与尊重的氛围。

## 未来计划

在尽可能合理的范围内，你应努力询问客户关于系统的未来计划。你可能已经确定了什么在“在范围内”，但了解什么既在“在范围外”又可能在未来成为需求，同样重要。

作为软件架构师，你可能非常熟悉“把自己逼进死角”的概念。最好的项目经理也了解这些概念，这也是为什么许多优秀的项目经理倾向于有架构背景的又一个原因（这一观点在本章开头就已提出）。

牢记这一点，应尽早确定哪些内容可能在未来成为需求，即使另一家供应商可能会承担这项工作也是如此。对目前显然不会付费或执行的内容表现出兴趣，表明你致力于避免“一次性”编程，并表明你是那种客户可以建立长期关系的供应商。

## 外观和感觉

如今，即使是再简单或再注重功能的 Web 应用程序，也应该看起来美观。没有理由让它看起来不好。设计必须是你流程中不可或缺的一部分，而不仅仅是事后补救，并且应尽可能向客户强调这一点。

在此阶段，确定客户对所交付内容的外观和感觉是否存在任何要求或特定请求。例如，是否期望遵循特定的企业品牌？系统是否需要与现有系统高度相似？品牌更改的可能性有多大，更改频率是怎样的？

## 技术

与客户公司打交道的人很可能不是技术人员。对于大多数项目来说，这是可以理解的，因为所需系统（即你接手的这个项目）的商业或功能目标不太可能是技术性的。即便如此，在此阶段就技术问题提出深入探询的问题，仍是一个极好的主意。

基本上，你必须判断自己在做这些决策时拥有多大的自由度。至少，在书面提案中，你需要概述所做的平台和基础设施选择，并在必要时能够加以论证。应尽量询问那种能够确定以下问题的问题：客户是否接受你使用 PHP 编码，可能存在哪些部署问题，以及需要解决哪些安全问题。

如果你发现的任何限制看起来过于苛刻，那这可能是另一个危险信号——表明你需要止损退出。作为 PHP 专业人士，如果客户坚持使用 ASP.NET 和 SQL Server，你最好考虑拒绝这项工作，或者反过来，尝试理解客户为何做出该决定。也许你可以说服客户 PHP 是正确的选择——但前提是没有根本的商业原因将他们绑定到那个替代平台。

无论哪种情况，你都必须尽早进行这次谈话，以防止任何徒劳的推销。知道何时该放弃，这也是真正专业人士的又一标志。如果你的客户在 Microsoft 硬件和软件方面已经全副武装，并且有一套现成的 .NET 应用程序，那你为什么还要尝试推销基于 PHP 的解决方案呢？

## 支持

如果有一个问题你应当始终尝试与客户提及，那就是售后支持的问题。客户可能连想都没想过，但明确客户的期望及其与你自己的期望是否一致，是非常有用的。

确定谁将创建面向用户的文档（如需要）、系统部署后由谁提供支持，以及客户在移交期间期望什么样的服务，都是需要解决的重要问题。如果客户显得不知所措，尝试为你自己的问题提出合适的答案，并获得客户的默许，以便将其纳入你的推销中。

奇怪的是，许多不习惯聘请 Web 开发专业人士的客户似乎存在一种错觉，即他们可以期望免费获得终身售后支持和维护。值得确保你的项目不是这种情况，如果是，则要让客户明白过来。

## 接下来怎么办？

既然你已拿到正式需求说明书，并与客户就时间、预算、设计、技术和支持进行了深入交流，现在是时候着手赢得业务了。如果你有幸为本组织的其他部门开发项目，可能可以跳过下一节，因为那很可能根本不是推销场景。

不过，如果你需要真正说服客户你作为供应商的价值，并在过程中提供一份详细定价的提案，请继续阅读。

## 构建推销方案

推销本身可以有多种形式。可以是演示、模型、示例系统，甚至是你过去参与过的类似解决方案的演示。无论哪种情况，书面材料通常是每次推销的一部分，而本节就是讲这个的。

首先要问的问题是，你是否真的需要做推销——或者仅提供报价是否足够了。

## 推销方案与报价

不用说，你至少必须为已获取的工作提供报价。然而，何时将该报价扩展为完整的推销，则是一个棘手的决定。

想想你作为消费者上一次被主动“推销”是什么时候。那大概是你上次购买汽车、高端电视或家庭娱乐系统、或新厨房的时候。当你看价值 $400 的电视时，你期望受到推销，那么为什么在节假日去商店为家人购买价值 $400 的杂货时，超市里却没有人向你推销呢？

区别非常清楚。电视是一项长期开支；杂货几周内就会消失。用同样的思路考虑你所报价的工作。不要过分纠结于现金价值。相反，要考虑你提议的工作对客户意味着什么。如果它会产生长期影响，那么你就需要推销它，因此需要制作推销方案。如果它仅仅是短期需求——一种耗材——那么，很可能你只需要一份报价。

可能只需要报价的工作示例包括对现有应用程序进行特定更改（前提是这些更改相对简单），或在服务器机架上安装和配置 PHP、Linux、MySQL 和 Apache。在这两种情况下，都没什么可说的——所以别说。

如果你仅提供报价，准备几页关于你业务的标准库材料（可以称之为“宣传材料”）可能会很有用——也许概述一些关键技能、经验、过去的客户等等。这可以与你的报价一起交给客户公司，以防公司里的任何人需要查看一些传统的销售材料。

在本节的其余部分，让我们假设你已经不遗余力地选择了推销方案，而不是报价。

## 推销方案与规格说明书

如果你认真想要赢得这笔业务，就计划在推销方案上投入大量精力。这本身并非坏事，但你确实需要非常小心，不要掉入一个非常严重的陷阱——即，实际上制作一份规格说明书，而不是推销方案。





你将在后面接触到规格说明。本质上，它们是你将要构建的系统的详细蓝图。然而，在投标阶段，你要小心不要陷入那种细节层次。不仅会让你做超出必要范围的工作，如果你最终没有赢得投标，还可能白白提供免费建议。

仔细思考你希望通过投标实现什么目标。你试图让客户公司相信以下几点：

- [ ] 你已充分理解客户的需求说明。
- [ ] 你已针对客户的需求说明设计出高效、有效且创新的响应方案。
- [ ] 你能够在客户要求的时间内交付你推荐的解决方案。
- [ ] 你能够以 X 的价格交付解决方案，且该价格是通过有条不紊的方式得出的。
- [ ] 你是客户应当合作的那种供应商。

深入探讨系统功能或背后技术的细节并无助于实现这些目标，因此应予以省略。

有时，为了解释投标文件中缺乏完整功能，需要对客户进行一定程度的“向上管理”。要完全坦诚。向客户说明，你已采用严谨的规格说明流程，以确保系统完全按照客户要求交付。在这个阶段，你是一家高质量的解决方案提供商，已全面理解系统的需求（而非具体细节）。如果客户接受这些论断，那么按照推论，他或她也必须接受你能够完全提供所需系统。

如果客户仍然坚持要求更多细节，请谨慎行事。不要因为轻易提供免费建议而贬低自己的价值。

## 投标时应当邀请谁参与

到现在为止，你可能已经清楚，如果赢得这笔业务，你想在项目中邀请谁参与。本章后面你会了解更多相关内容；但目前，值得考虑的是你应该让谁参与投标文件的编写。由于投标是你的责任，最终关于其内容的任何编辑决定都由你做出。

话虽如此，请注意投标过程中包含创意要素！你必须清楚地展示出相对于竞争同一业务的其他供应商的优势，以及在客户预算限制内交付所需解决方案的能力。牢记这一点，确实值得在早期阶段让那些可能对创意过程有所贡献的人参与进来。

然而，因为你并不陷入具体细节，所以不必让一位以上的资深技术专家和一位资深创意人员参与（假设你有这样的人可用）。三人如何确定投标内容完全由你们决定。在项目经理主导、头脑风暴环境中制作整份文件，已被证明比仅仅将投标拆分为可分配的部分后再拼凑起来要有效得多。

### 何时付出额外努力

有些客户会让你为赢得业务而付出艰苦努力。在许多情况下，这非常值得。但在其他时候，风险可能太大。知道何时以及何时不应付出额外努力是一项必备技能。不要把这看作是懒惰；你的时间可能更适合用于追逐其他潜在的商业线索，而不是将精力投入到一个不太可能成功的候选者身上。

客户有时要求的额外步骤可能包括现场演示、演示你过去开发过的类似系统，甚至提供之前客户的推荐和证言。有些人还会要求提供财务状况证明（如账目、银行对账单和纳税申报表副本）。此时你应该问自己的问题是：

- [ ] 你赢得这笔业务的可能性有多大？
- [ ] 采取这些额外步骤涉及哪些成本？
- [ ] 其他供应商在做什么？

如果你从客户那里得到强烈信号，表明交易即将达成，你当然应该考虑继续。然而，如果客户反应不佳，决定可能已经偏向其他人，在这种情况下，你应该拒绝提供更多信息的邀请。

始终要评估采取这些额外步骤的现金成本（差旅、耗材）和有效成本（以潜在损失收入计算的时间）。作为一条规则，如果成本看起来接近项目价值的 5% 以上，肯定应该考虑退一步。

如果可能，试着打探一下其他供应商在做什么。在客户处有一位友好的内部人士会非常有用。例如，接待员显然不是决策者，但很可能对消息相当灵通。尽量获取你能了解到的任何信息；如果你的竞争对手付出了额外努力，那你也应该如此。

### 何时说不

奇怪的是，很少有专业人士会考虑什么时候适合拒绝投标某项业务，然而知道何时放弃与知道何时全力以赴抓住机会同样重要。

除了显而易见的情况（如缺乏必要的技能或人员，或客户缺乏必要的预算）之外，你应始终警惕以下情况：

- “只是好奇”类需求——客户没有真正的权力委托你执行项目，只是在行业期刊上读到过，想知道大概需要多少钱。典型的警示信号包括被初级职员负责说明，该人员经常提到需要和老板谈谈。
- “压低报价”类需求——客户已经选定了供应商，但想通过获取其他供应商的报价作为筹码，来压低该供应商的报价。
- 宠物项目——通常，需求由公司中一位相对资深的人员提出，但其他人似乎都未参与或毫无兴趣。虽然这类项目确实可能有资金支持，但如果那位资深人员离开，你的项目很可能也会随之夭折。

始终心中要有数。如果项目看起来麻烦大于价值，就不要害怕退一步。客户甚至可能因此尊重你。

## 投标结构

你的投标书面部分可以采用几乎任何你希望的结构，只要在不同投标之间保持一致即可。如果你可能为单个客户制作多份提案，这一点尤为重要；文件之间的保持一致性至关重要。

值得遵循的几个关键点：

- 提供介绍——始终在投标上注明日期，以客户名称（而非你的名字）作为标题，并添加“prepared for X”一行，其中 X 是你在该公司的主要联系人姓名——这是立即得分的好方法。
- 始终将需求说明的关键点作为第一部分予以复现——如果客户提供了书面需求说明，不要逐字复制，而是用大约半页的篇幅进行总结。许多客户会仅根据你提案的首页和报价做出决定，所以要明智使用空间。
- 提出你的解决方案——如有必要，可包含简单的 Visio 图表或插图，并在不超过两到三页的篇幅内完整描述你的解决方案。同样，不要陷入细节。这是对系统的鸟瞰式、自上而下的概述——对你刚才描述的需求说明的自有创意解读。提供你构思的“巧妙功能”和想法的要点列表，而不仅仅是列出组件。
- 始终提供清晰的“投资摘要”——称之为“投资摘要”而非“报价”。“投资”一词具有更积极的内涵，暗示对客户的长期益处。当然，不要试图向客户隐瞒价格。清楚地展示你是如何得出价格的，并包含你提出的任何商业条款的详细信息。
- 如果你之前为该客户报过价，请确保你的报价与之前的报价一致。例如，如果你在之前的报价中采用的是每天 800 美元的固定费率，就不要在此时采用每天超过 800 美元的费率，除非你已充分准备好在客户提出质疑时进行辩护。
- 适当深入细节——谈谈你的流程（如果有）、你的公司及其历史和背景。如果可能，提及之前满意的客户，尤其是知名客户。
- 对日期要坦诚——向客户说明完成工作需要多长时间，你预计何时交付，以及客户何时可以开始使用系统。强调你在遵守截止日期方面一丝不苟。如有必要，提供一个简单的甘特图，显示任何依赖关系——特别是需要客户参与的那些依赖关系。
- 设定目标和期望——包含一条“什么该做下一步”的说明，告知客户如何就问题联系你，以及如果客户希望立即开始该如何进行。





如果在收到简报时进行过面对面会议或电话会议，请尝试引用你提出的一些引导性问题以及提供的答案。提醒客户这些答案，并展示你如何利用这些答案来驱动到目前为止所做出的决策。例如，“您在与我们会面时告诉我们，您需要系统能够作为 XML Web 服务访问。因此，我们在提议的解决方案中包含了……的功能。”

如果以电子方式发送文档，请尽量使用 PDF，而不是 MS Word 文档或任何其他专有格式。此外，务必随后致电核实客户是否已收到文档，但此时要克制催促客户的诱惑。在进行任何后续电话联系之前，至少要让一周过去。

最重要的是，如果你向客户承诺在某个特定时间日期前提交提案文件，请不要错过截止日期。第一印象很重要，你只有一次机会。

> 请记住，无论你多么出色，都不可能全部赢得。

不过，除非你的中标率证明是灾难性的，否则不要纠结于任何错过的提案。继续前进，并尝试从客户那里获取一些友好的反馈，了解下次可以如何改进你的方法。

假设获得客户的批准，你需要很快组建一个项目团队。现在让我们来看看这个。

## 选择团队成员

在着手推动项目之前，你必须组建一个负责交付的团队。如果可能，请为此过程预留一整天——并向客户清楚地说明你在做什么。这个团队最终的规模显然取决于你可用的资源和项目的要求。本节将介绍项目中的不同角色以及它们如何协同工作。

## 项目经理

如果你正在阅读本章，那么你很可能将担任这个角色。项目经理（有时也称为制作人，视当地情况而定）负责项目的日常运营，从投标一直到交付和移交。一般来说，项目经理直接与构建团队的高级成员合作，如果没有客户经理处理与客户的关系，则直接与客户合作。

项目经理设定与项目交付更广泛目标相兼容的内部截止日期和目标，管理进度，并识别和解决构建团队在整个过程中遇到的任何冲突或困难。

这本身并非技术角色，但要成为一名有效的项目经理，深入了解软件架构师、软件工程师及其他人员所从事的工作几乎是必不可少的。因此，理想的项目经理应该是一位平易近人、具备技术意识、高度有条理且高效的人，并且有按时按预算交付项目的良好记录。

除非存在相反的特定要求，否则任何给定的项目只需要一名项目经理。

## 客户经理

如果可用，客户经理是你项目团队中一个有价值的成员。客户经理是你（供应商）与客户之间唯一的联系点。所有双向沟通都通过客户经理进行。

如果客户对构建团队有特殊请求，客户会将其提交给客户经理，客户经理再将请求转交给项目经理。项目经理随后会在内部处理该请求，并根据情况与构建团队合作。

客户经理不参与项目本身的日常运营，而是专注于管理客户与供应商之间的关系。然而，客户经理和项目经理需要定期沟通非常重要，以便客户经理能让项目经理了解客户的期望和反馈，项目经理能让客户经理了解关键项目里程碑的进展和完成（或未完成）情况。

客户经理并非必不可少，但往往能与客户建立更紧密、更富有成效的关系，因为这个角色不像项目经理那样承担以团队为中心的责任。然而，同样因此，有时会导致客户经理过于迅速地同意客户的要求，因为实际实施此类要求的负担并不落在客户经理肩上。

理想的客户经理是一个外向热情的人——那种能轻易与遇到的每个人建立并保持良好关系的人。此外，客户经理必须对项目团队其余成员能否完成什么、不能完成什么的限制有所理解，并在必要时能够向客户传达这些限制。

与项目经理一样，任何给定的项目只应指派一名客户经理。

## 主架构师

项目的主架构师是整个项目生命周期的技术决策者。他/她的职责是将项目的即时需求（在日常基础上）转化为关于如何通过技术实现这些需求的决策。

任何给定项目的主架构师始终是软件架构师，而非工程师，因此经验要丰富得多。然而，主架构师还必须具备一定的项目管理经验，以确保其决策以客户为导向。主架构师还应具备出色的团队管理能力，因为初级技术人员将直接向他/她汇报。

除了具备软件架构师的全面能力外，主架构师还必须深入了解系统和网络，以便能够合理构思项目可能需要的任何部署基础架构。

主架构师通常承担的软件架构职责包括：创建或批准（或两者兼而有之）项目的数据库架构和对象模型、维护编码标准以及定期进行代码评审。

鉴于该职位职责的范围，任何给定的项目只应指派一名主架构师。

## 软件架构师和工程师

任何给定的项目都需要若干软件架构师和工程师来处理应用程序背后的后端技术（就本书而言，即 PHP）。这两个角色之间的区别在于资历。

*软件架构师*在主架构师设定的界限和标准范围内，有一定的自主权来决定架构、布局、结构、基础架构和编码标准。相比之下，*软件工程师*必须遵循软件架构师制定的法令和标准。

如果资源不允许使用客户端开发人员（见下一节），软件工程师也可能承担开发网站模板和 HTML 的任务。

当然，分配给项目的架构师和工程师数量可以不受限制。

## 客户端开发人员

客户端开发人员的职责仅限于生成为正在开发的应用程序提供用户界面的 HTML、CSS 和 JavaScript。通常，他们将在模板驱动的环境中工作——例如，使用 Smarty 模板。通常不要求他们了解 PHP 或任何其他服务器端脚本语言。

他们将与任何给定项目中的高级设计师和工作室美术人员合作，接收设计并将其转换为 HTML，但会直接向主架构师汇报。

任何给定项目中可部署的客户端开发人员数量不受限制。

## 信息架构师

对于除了最简单的应用程序之外的所有应用程序，你都需要一些专门的资源来负责构建中至关重要的 *信息架构*——即在 Visio 或类似软件中设计和制作线框图。这些线框图可以作为功能规范过程的一部分，也可以作为设计师为项目制作创意方案的起点。

信息架构师在某种程度上是一种专业人才。他们是一种奇特的技术、商业和创意的混合体。这并非一种可以教授或学习的技术，而是一种技能，其最佳从业者对其有着天然的亲和力。





## 高级设计师

设计流程由高级设计师主导，他们负责所生产应用程序的整体概念设计。这些团队成员将制作初步设计以供客户批准，并就字体、颜色和图像做出更广泛的决策。他们与首席架构师合作做出此类决策，以确保所创建的概念在项目的技术限制范围内。

通常，一个项目最多有两名高级设计师，其中一人通常担任领导角色。

## 工作室美工

高级设计师手下还有一位更初级的资源——工作室美工。工作室美工并非专门负责创意概念，但仍精通Photoshop、Illustrator和其他设计软件，通常会有条不紊地响应特定组件的请求。例如，制作带有特定标题集的导航栏通常属于工作室美工的职责范围。

工作室美工通常只使用高级设计师在项目中指定的现有模板、样式和颜色工作。

给定项目可以部署任意数量的工作室美工。

## 角色兼任

资源配置常常是一个挑战，即使是规模最大的机构也不例外。出于此考虑，如果您被迫兼任角色，以下建议可能有所帮助：

- 项目经理通常能够胜任客户经理的角色，前提是他们天生具有面向客户的特质。在紧急情况下，他们还可以承担基本的信息架构工作。
- 首席架构师显然可以承担通常由软件架构师和软件工程师执行的所有角色。
- 软件工程师通常可以完成分配给客户端开发人员的开发工作。
- 高级设计师当然可以承担通常分配给更初级工作室美工的所有职责。

## 工作惯例

在可能的范围内，让项目团队在一个房间里一起工作是个非常好的主意。这样一来，常被谈论但大多属于理论的协同效应概念就近了一步——也就是说，获得来自一支整体实力大于其个体之和的员工队伍所带来的额外竞争优势。也许更重要的是，让整个团队在同一个屋檐下工作，会让您作为项目经理的工作轻松得多。

## 您客户的角色

让您的客户为项目定义明确的角色并分配人员到这些角色中，与您正确构建自己的团队同样重要。这显然是一件您无法像控制自己项目团队角色分配那样加以控制的事情。

但是，如果可能的话，您应确保客户指派一名关系经理，作为您与客户的第一个联系点——负责处理、提出和解答有关项目的任何查询，以及任何商业查询。如果客户需要就项目提供任何定期投入（通常是提供内容），客户还应指派一名内部项目经理。该人员负责管理或执行客户端所需的任何工作，以向您提供此内容。

## 总结

在本章中，您详细学习了成功管理软件应用程序项目的基础知识。您了解了收到简报的重要性，包括您应该提出的关键问题，以便在其他供应商中获得竞争优势，以及如何回应该简报，包括如何和何时构建合适的提案。

在第17章中，您将了解不同的软件开发流程和方法论，它们如何应用于您的团队，以及如何确定哪种最适合您。

## 项目规划

说实话，您很少会独自开发大型网站。随着开发生涯的进步，您会发现自己在越来越大的项目中担任更高级的角色。然而，与一群技术和商务专业人士共同开发复杂的动态PHP-based网站和应用程序并非易事。您将面临许多挑战，其中有些挑战的性质并非完全技术性的。

您选择的商业规划框架无疑将影响您的软件项目发展的方向。选择提供严格（但舒适）结构的流程将限制您的项目变化的动态程度，但反过来会给您带来一份纸质追踪和一份详细的路线图供您遵循。不过，采取更动态的规划方法可能会降低与技术或商业未知数相关的风险。

关于哪种系统规划方法最适合您的项目的决定并非易事，无论您的个人或职业偏好如何，在做出该决定之前，您都应熟悉所有规划选项。

### 选择流程

既然您已经将项目团队组建好了，毫无疑问您渴望开始交付客户急切期盼的解决方案。但是，在开始之前，您必须确定为构建最终产品而采用哪种流程。

国际知名的项目管理学会（PMI）在项目管理领域倡导许多标准和实践。这包括培训和认证，以及许多正式的项目规划和执行方法的定义和文档记录。有关PMI的更多信息，请参见www.pmi.org。

有几个可供选择，但两个最基本的流程被称为_瀑布流程_和_螺旋流程_。这两个流程具有相同的基本阶段（或阶段）和元素。区别在于处理它们的顺序和方式。这两个流程共享以下四个连续阶段：

- 1. 规格说明
- 2. 设计
- 3. 构建
- 4. 测试

### 瀑布流程

在瀑布流程中，整个项目被视为一次性交付的完整解决方案——实际上只有完成才算完成。图17-1显示了所遵循的大致流程。

![](img/a1b732997d9cb194dceec0570dc79710_422_0.png)

图17-1：瀑布流程

瀑布流程最重要的原则是，在前一阶段完全完成之前，任何项目阶段都不得开始。例如，在设计和架构阶段开始之前，必须完成并批准整个项目的书面规格说明。只有然后，才能完成并批准项目的构建过程。最后，才能进行项目的测试阶段。

这种传统流程原则上是可以的，但在实践中存在一些潜在问题。例如，如果在某个阶段中发生错误，直到以后才被发现，那么该阶段及之后的所有阶段可能都需要重复，这非常耗时且昂贵。如果客户在交付时才发现规格说明阶段的错误，则需要重新进行规格说明、重新设计、重新构建和重新测试。

另一个潜在问题是，因为解决方案是一次性构建的，所以很难在开发过程早期向客户提供任何部分完成的东西供其试用。如果客户希望提供早期演示，或者只是需要对进度的保证，直到项目生命周期的很晚之前，这些都很难完成。

### 螺旋流程

螺旋流程与瀑布流程具有相同的核心组件：规格说明、设计和架构、构建以及测试。但是，它不将整个解决方案视为应用这四个步骤的单一实体，而是将系统划分为单个组件，然后将流程应用于每个组件。

组件可以是离散的功能片段，也可以是功能片段的部分演进（或层）。对于每个组件，都应用这四个阶段：该组件的规格说明，接着是该组件的设计和架构，接着是该组件的构建，接着是该组件的测试——全部独立进行。

该流程之所以被称为螺旋，是因为您遵循着螺旋的路径——沿着路径前进，但一次又一次地经过相同的四个罗盘点（每个四个阶段中的每一个），如图17-2所示。





![](img/a1b732997d9cb194dceec0570dc79710_424_0.png)

图 17-2：螺旋过程

该流程的一大优势在于，如果在四个阶段的任何阶段发现错误，则需要退回重做的步骤要小得多，因为您只需处理一个离散组件，而不是整个应用程序。此外，客户能够更早地体验您应用程序的第一个组件，这可能带来巨大的政治利益。

请注意，瀑布流程中的测试阶段与螺旋流程略有不同之处在于，针对每个新组件应用的测试理想情况下还应包含之前组件的所有测试。这是为了确保没有新的功能模块会导致之前已测试并签字确认的功能模块失败——这一过程称为回归测试。

## 做出决策

本章并不主张其中一种流程优于另一种。在本书后面，您将在计划中的 Widget World 销售自动化应用程序的背景下再次看到其中一种流程，但目前，让我们敞开大门。您选择哪种方法很大程度上取决于手头的项目。

尽管螺旋流程从变更请求和异常处理的角度来看确实具有巨大优势，但额外的文书工作和行政参与也有其成本，也必须同等权衡。

您自己的经验会让您对两种流程有所了解。在许多情况下，决策在很大程度上取决于个人偏好，与其他因素无异。如果您是项目负责人，无疑会获得选择方法的自由裁量权。无论您选择哪种方式，都有共同步骤，且每个步骤都有最佳实践，所以让我们接下来看看这些内容。

## 常见流程实践

如前所述，瀑布流程和螺旋流程在坚持所有开发都必须有规格说明阶段，然后是设计阶段，然后是构建阶段，然后是测试阶段方面是一致的。

区别在于每次迭代中完成了多少规格说明、设计、构建和测试，以及以什么大小的块来完成。此外，规格说明、设计、构建和测试这些词本身也很大程度上存在解释上的歧义。现在让我们更仔细地看看，无论您为项目选择了瀑布流程还是螺旋流程，如何实现每个阶段。

为了本示例的目的并保持语言的清晰，让我们假设您为项目采用了瀑布流程。因此，本次考察将阶段描述为应用于整个项目，而不是单个组件。但是，如果采用了螺旋流程，您可以将完全相同的方法论应用于螺旋中的每个组件。

## 规格说明阶段

在很多方面，规格说明阶段是任何项目中最困难的部分，通常比构建过程本身更棘手。如果您被分配去构建一个略显平凡的系统（例如，一个简单数据库的前端），则尤其如此。开发任务本身并不特别具有挑战性；难的是第一次就为客户把事情做对。

此阶段旨在确保您知道要构建什么，更重要的是，确保客户知道您要构建什么——并且它尽可能紧密地符合客户的原始业务需求。在此采用的最简单方法是为项目制作纸质规格说明——包括功能规格说明和技术规格说明。

## 功能规格说明

项目的功能规格说明详细描述了系统在预设计级别的功能。它应使用通俗易懂的英语编写，不应过分强调（或提供）技术主导决策的依据。作为经验法则，大致遵循您的提案文档（如果您写过的话），并在此详细复述简介。这为寻求客户确认项目参照条款是否保持不变提供了极好的起点。

不过，与您的提案的相似之处到此为止。您之前被告知不要在提案文档中包含的所有细节，都应在此处包含。删除您宁愿不重复的区域中的任何歧义，以免出错。掌握好细节程度是一项微妙的平衡艺术。过多，文档将变得不可读；过少，则会留下太多解释空间或日后对功能产生分歧。

考虑到这一点，请在您认为可能存在歧义的任何区域力求清晰。例如，如果您使用短语“用户将能够上传照片以关联到其个人资料”，客户不太可能注意到您遗漏了照片数量或格式。在这种情况下，当出现用户想要上传 800 个 .pcx 文件但您的应用程序不支持的场景时，您可能会遇到麻烦。相反，请尝试使用诸如“用户将能够上传最多八张 JPEG 格式的照片以关联到其个人资料”之类的短语。

同样，然而，应避免令人乏味的细节，因为海量信息可能会压倒、沮丧或惹恼即使是最耐心的客户。如果您发现自己使用诸如“页面将有一个主页按钮，单击后将用户带到主页”这样的句子，您就有罪了。此外，正如过于技术性的信息可能令人生畏一样，过于简单的信息可能显得傲慢。

判断规格说明是否准确的试金石是，您是否可以将其交给五支不同的称职的开发和设计团队，并且在这五种情况下，都能构建出大致相同的东西。同时，您也应将那些最好留到后续阶段或交由项目其他人员决定的问题留给解释。例如，应避免“页面将有一个位于屏幕左侧 124 像素处的主页按钮”这样的句子，因为此决定应留给高级设计师在设计阶段做出。

在功能规格说明中，请尽可能清晰、一致地布局文档。以下是从头到尾建议的布局：

- 复制客户的原始简介（或您制作的工作范围文档，如果有）。尝试将其限制在不超过半页，并确保使用您自己的措辞。
- 关于本文档提供的内容、对客户的期望，以及您将作为规格说明过程的一部分交付的其他文档的说明。在此阶段，请明确这一点，即您希望客户在继续之前亲自对本文档签字确认。
- 用不超过半页的篇幅，说明您所提议解决方案的顶层摘要，并列出其可能包含的组件。
- 对于每个组件，提供其功能的详细解释，包括针对“虚拟”用户的典型使用演练。
- 如果您真诚地认为图表能提高清晰度，请提供图表；否则，避免使用。无论您多么强调它们只是图表，客户一贯会将其视为完成的设计，并导致可预见的后果。同样的陷阱也同样适用于“线框图”（有时称为信息架构），您将在本章后面遇到它们。
- [ ] 在文档末尾补充说明，如果客户想要提出问题或更改，或者想要对文档签字确认，他或她必须做什么。说明文档签字确认后的下一阶段，并温和地提醒，此前商定的交付里程碑全部取决于及时同意本文档。

在实践中，您可能需要对规格说明进行至少两到三次迭代，客户才会满意。事实上，您应警惕任何立即批准初始规格说明的客户。十有八九，这意味着客户没有阅读它。

## 技术规格说明

与描述您计划做什么的功能规格说明不同，技术规格说明描述您计划如何做。您在此处需要包含的细节程度因客户而异，差异很大。通常，如果客户有一个对项目表现出浓厚兴趣的 IT 部门，那么您将需要提供详尽的细节，一直到您的编码实践。否则，您通常只需提供以下内容即可：

- [ ] 构建的建议语言（附理由和解释），以及对其他竞争语言的比较和拒绝

- [ ] 建议的数据库平台（附理由和解释），以及对其他数据库平台的比较和拒绝

- [ ] 建议的 Web 和数据库服务器操作系统——同样，附其他平台的比较及其被拒绝的理由

- [ ] 关于项目的托管和部署计划的说明（如有），包括带宽要求等细节，在适用的地方。

- [ ] 关于本文档提供的内容、对客户的期望，以及您将作为规格说明过程的一部分交付的其他文档的说明。请明确，本技术规格说明直接关系到客户已在功能规格说明中签字确认的功能。

如果您选择为项目采用螺旋流程，则不必为螺旋的每次遍历提供技术规格说明。相反，在项目开始时提供一份技术规格说明，并向客户解释，该规格说明涉及后续所有单独组件的实现。

对于许多客户（尤其是那些没有自己技术部门的客户），此文档可能显得相当陌生。如果是这样，您有两个选择：

- [ ] 与客户详细解释文档，不遗余力地确保客户对您所做的决定感到满意。

- [ ] 让客户盲目签字（客户可能更愿意这样做）。

有时，后一种决定是最容易的。毕竟，大多数客户认为他们付钱给您是为了让您告诉他们在技术上什么是合理的，而不是为了征求他们的许可。





## 设计阶段

这里，*设计*一词可能会产生误导。它既涉及平面设计，也涉及软件设计；但这两者当然是非常不同的学科，你应该意识到其中的区别。尽管如此，客户几乎不可避免地希望尽快看到项目关键组件的一些单独平面设计。

项目中的资深设计师完全可以负责并制作这些设计，只要与首席架构师密切协商，确保所提议内容的技术可行性即可。经验丰富的资深设计师会了解技术限制，因此在为 Web 进行设计时需要较少指导。

同样，在设计完全正确之前，预期要制作几个设计迭代版本。这可能非常棘手。客户对想要的东西有自己独特的愿景，他们可能难以向你作为供应商表达清楚。有时客户只知道你制作的不是他们想要的，他们不会犹豫向你明确指出这一点。

向客户展示设计时，有时让资深设计师亲自演示会很有用，甚至可以使用加载了图形和 RAD 软件的笔记本电脑，以便在客户面前进行建议的修改。像“那就是了，我就要这样的”这样的反应会非常令人欣慰，在商业上也很有用。

## 创意规范

关键设计获得签字确认后，制作所谓的*创意规范*或*风格指南*是非常有用的练习。这份文件通常不会提交给客户审阅，尽管，如果客户非常注重品牌保护或有内部图形人员，那么这么做也未尝不是好主意。

这份文件的传统目的是将资深设计师的艺术愿景传达给更初级的工作室艺术家，并确保项目上任何未来的设计工作也与该愿景保持一致。

风格指南包括字体、颜色、布局、徽标、背景等细节——构成更广泛艺术愿景的所有组件。该指南确保如果提出“生成一个写有“加入购物车”的按钮”之类的请求，其结果完全符合资深设计师的预期。

## 信息架构

设计阶段中可能最具争议的组件是信息架构，有时称为*页面地图*。本质上，它是用户 Web 浏览器中给定页面的线框图，即黑白模型，试图在不传达任何设计方面的情况下阐明用户界面 (UI)。它使得通用 UI 能够独立于平面设计获得批准，在商业或政治压力使这可能有用时，或者当此页面没有制作特定的平面设计时，这非常有用。

此外，它可以连同创意规范一起交给开发团队，以便他们可以直接委托工作室艺术家和客户端开发人员制作交付特定组件所需的设计和 HTML 代码。但是，在实践中，线框图有两个主要陷阱。

首先，客户往往难以区分 UI 和设计的概念。这意味着向客户展示完整的信息架构可能是一项乏味且令人压力山大的任务，因为客户会将你的线框图视为最终的外观和感觉，并对此望而却步。结果，反馈通常与用户界面完全无关——例如，你的客户可能会要求你“把那个按钮做大一点”。显然，你必须从一开始就清楚地说明你正在展示什么，但即便如此，试图指导不熟悉该流程的客户以获取关于 UI 的重要反馈，仍然可能是一个极其令人沮丧的过程。

其次，实际制作信息架构的人员职责难以界定。平面设计师很少是制作“界面”本身的专家，而且通常不愿意使用 Visio 及其他制作这些交付物所需的软件包。项目经理通常太忙了。因此，这项任务往往落在首席架构师的肩上。鉴于向软件架构师和工程师传达特定组件制作愿景本身就是首席架构师职责的核心，因此记录该愿景的论点也就减弱了。

## 软件架构：十点计划

同样，你可能想要（或不想要）提交给客户审批的另一份文档是软件架构计划。这通常被称为十点计划，因为它通常是一系列简短、有力的要点列表，概述当前实际项目或组件的最佳方法，而不是一份散文繁多的文档。

制作这份文件非常属于首席架构师的职责范围，他通常在技术规范获批并签字确认后很久才制作它。因此，它不涉及技术选型、硬件、托管等问题。相反，它专注于数据库架构、对象模型以及 MVC 等设计模式的实现等问题。

首席架构师将文件传达给他的软件架构师，软件架构师再按各自理解进行诠释。理论上，“架构愿景”也应该向下层级的软件工程师传递。

你是否选择向客户展示这份文件，取决于客户提供的技术人员的能力和水平。如果客户没有足够技术的人员（例如，他们只有通用 IT 从业人员，而没有开发职能），那么不太可能得到反馈。如果他们有时会自行进行开发工作，那么还应该争取这些开发人员在高级别上的认可也未尝不可。（你的客户应该能够做出必要的介绍。）

但是请记住，无论你的软件架构多么健壮，都存在“非我莫属”综合征的风险。你可能会发现客户的开发人员出于原则对你的方法挑刺。最好是迁就这样的人（在一定程度上），但如果他们开始影响交付日期，不要害怕让客户知道。你会惊讶于他们多么迅速地被激励而退让。

## 构建阶段

一旦所有设计参数达成一致，构建过程本身即可开始。此阶段没有伴随的书面文档，但有几点值得牢记：

- 始终维护开发服务器和暂存服务器，以及生产服务器。这些不一定非得是独立的物理服务器，但至关重要的是，你可以向客户发布部分完成的开发阶段，以记录你取得的进展。你还可以决定暴露一个“边缘”服务器，客户可以随时在上面检查进度——前提是客户看到的是正在进行中的工作，并且不一定能完美运行。

- 尝试采用一种编程方法论，如果它适合你的项目。这些内容将在本章后面的“编程方法和实践”部分中详细讨论。

- 首席架构师负责管理构建过程，并确保他的团队按时、按要求的标准交付所有组件，以便整个系统可以作为完成的包交付给项目经理，而不是零零碎碎地交付。

- 始终保持严格的版本控制。本书的其他地方，你将了解 Subversion，这是解决这个常见问题的免费方案。

## 测试阶段

构建解决方案后，对你进行适当的测试至关重要——既为了确保你所生成内容的质量，也为了让客户放心，他或她不必进行详尽的测试。

你进行的测试应始终附带详细说明你发现的书面报告。出于明显的原因，在你对测试已经完全成功 100% 满意之前，不要发布这些报告。

### 功能测试

*功能测试*确保产品按预期完全工作，既满足规格说明，又没有错误或故障。要有系统性。使用多组不同的数据集和/或输入参数，不懈地测试每个功能领域。系统地记录你的发现，以便实际上可以在每个独特功能旁边的方框中显示“已检查”状态。

当然，始终要向开发团队强调，尽可能“边做边测试”至关重要，绝不要提交已知存在严重错误的代码。你可以考虑使用 Mantis (www.mantisbt.org) 之类的缺陷跟踪系统，在发现每个缺陷时维护一个集中式缺陷库，将缺陷分配给开发人员，并适当注释。

### 负载测试

如果你正在构建的应用程序现在或未来某个时候可能是高流量应用，那么了解它在崩溃前能承受多少是有意义的。





只有当您能够将应用程序部署到真实环境（通常是生产服务器）时，才能进行负载测试。如果您知道将被迫部署到运行 Solaris 的 Sun 机器上，那么在您的 Xeon 驱动的 Linux 开发服务器上测试应用程序也没有意义。有许多软件包可供使用，其中最流行的可能是 LoadRunner（访问 https://h10078.www1.hp.com/cda/hpms/display/main/hpms_content.jsp?zn=bto&cp=1-11-126-17%5E8_4000_100&jumpid=reg_R1002_USEN 了解更多信息）。不过，使用一组自定义构建的测试脚本也可以取得类似结果。

负载测试的关键是永远不要害怕将音量调高，直到扬声器爆炸。仅仅知道可以处理客户的流量预期是好的，但确切知道它们还能处理多少更多流量则更好。如果您能提供确切数字，例如“该网站可以处理 1,000 个并发用户且没有任何问题”，客户会感到非常满意。

## 交付

在编制出一份文档齐全、设计良好、经过充分测试的软件后，与客户安排一次适当的交付会议至关重要。这是客户的最终签署确认——无论是针对整个项目还是针对该组件，具体取决于您决定采用哪种流程（在本章前面部分有所描述）。

在交付过程中，您应该确保客户完全熟悉成品的内部工作原理。因此可能需要进行一定程度的培训。此外，请记住您在此的目的——移交项目。向客户提供一份包含源代码副本的 DVD 可能具有难以衡量的象征意义。

在交付过程中，出现小变更请求几乎是不可避免的。本章后面您将学习如何处理它们。

## 编程方法和实践

让我们简要看一下构建过程本身。无论您选择了哪种总体项目流程，在构建过程中都可能希望采用一些最佳实践方法。

### 测试驱动开发

在第 13 章中，您简要了解了 PHPUnit，并学习了如何使用它来构建单元测试框架。当然，只有当您以单元驱动的方式构建应用程序时，才能应用这些知识。

测试驱动开发要求您先编写测试，再编写代码。为您打算编写代码的类编写测试这一行为，迫使您思考您计划如何使用特定的类、它需要做什么以及其接口应该是什么样子。PHPUnit（通过 PEAR 在 http://pear.php.net 获取）是一个良好的测试框架。

在尝试编写类本身之前，您希望先确认单元测试是否有效。这可能需要使用一个与真实类具有相同接口的虚拟类，以使测试运行并自然失败。

构建完成后，该类的单元测试将探测您的 PHP 类的接口并详细分析返回的数据。作为开发人员，您的责任是编写代码以满足您的单元测试。

尽量使您的单元测试尽可能通用。如果您有许多接口相似的类，可以将单元测试合并为一个 PHPUnit 实例。

使用单元测试有许多优点，这些优点将在本书后面部分详细探讨，那时您将开始构建 `discovernewbands.com` 门户。是否适合您的项目，再次是一个判断问题。它是一种测试方法论，可以说更适合具有更多独立组件的大型项目，而不是简单的传统“数据库应用程序”。

### 极限编程

*极限编程（XP）*的概念也许是编程范式中最真实的一个例子。它之所以是一个范例，是因为它可能比在每个开发场景中都实用，更具有雄心，并且并非没有批评者。然而，作为一个工作模型，它有许多方面可供根据需要挑选和选择。

它只是有时被称为 *敏捷开发方法论* 的一种例子——一套声称更适合二十一世纪应用程序开发的、多种不太正统的方法。

### 理解 XP

XP 的有效性通过许多不同的工作实践来实现。它们太多，无法全部列出，但让我们详细看看其中几个。

XP 的主要目标是交付由客户需求驱动的高质量软件。它通过管理复杂性来实现这一目标。随着系统日益复杂，添加和修改功能的成本会增加。反之，如果系统不变得不必要地复杂，那么以后添加功能的成本大约与现在添加功能的成本相同。

这是一种非常有力的武器，因为传统方法论往往遵循这样的曲线：随着开发各个阶段投入的时间增加，软件修改成本呈指数级上升。

例如，在需求阶段添加功能比在实现阶段更具成本效益，而实现阶段的成本要高得多；但假设您的项目开发遵循一条曲线，使变更成本增长得更慢，且更快趋于平稳。如果您可以随时添加、删除和修改功能，那么在项目初期试图预先确定整个功能集就没有压力或理由了。

正如 Kent Beck 和 Cynthia Andres 在 *Extreme Programming Explained, Embrace Change, Second Edition*（Addison-Wesley，2004 年）中明确概述的那样，XP 的实践就是遵循一组实践：

- 规划 — 通过结合业务优先级和技术估算，不断更新来确定项目范围。
- 小版本发布 — 将系统交付给将使用它的人，并按照非常短的计划发布新版本。
- **简单设计** — 始终尽可能保持设计简单。复杂性将持续被移除。
- **测试** — 开发人员持续编写单元测试，以确保系统始终完美运行。客户编写测试以证明功能按要求工作。
- **重构** — 在不修改行为的情况下重构代码，以保持代码易读、消除重复或简化代码。
- **现场客户** — 客户应在开发过程始终可用，随时回答问题。

贯穿构建过程始终可用的客户，实际上成为开发过程的一部分，*而不仅仅是通过其需求推动它向前发展。如果可能，最好在开发过程的关键阶段让客户（最好是某个领域专家且技术水平合理的代表）现场参与。

不要担心客户会不必要地骚扰您的团队。只要他们得到适当参与，您的团队就会向上管理客户。XP 的这一信条对于实现高客户满意度尤其重要。如果客户从第一天起就参与其中，就不会出现“这不是我想要的”这样的抱怨。

通过在创建类本身之前为类创建单元测试，如果代码第一次不起作用，可以节省时间。在包含许多不同类的大型项目中，这种时间节省可以轻松达到几天。

使用单元测试还带来其他好处。首先，在心理上，它促使软件架构师和工程师更充分、更彻底地考虑给定组件的需求，这意味着成品通常比非单元驱动方法所允许的更贴近真实需求。此外，它对编码风格有积极的直接影响，对参与开发过程的所有人都非常有益。

其次，它确保编码标准在项目早期就确定，并且整个开发团队都遵守这些标准。没有“代码所有权”，因此只要单元测试继续工作，任何开发人员都可以修改任何代码片段。

也许 XP 最著名的方面是它允许两名软件工程师（或者软件架构师和一名工程师）同时在同一工作站上编写代码。通常，最佳配置是两人并排坐着，但一人驱动（即控制键盘和鼠标），另一人指导代码编写过程。当两人积极参与每段代码的开发时，业务和技术专长不会被卡在某个开发人员的脑子里，这允许信息更均匀地分布，并避免项目依赖于任何特定的开发人员。此外，老话说得没错：两个头脑几乎总是比一个更好；结对编程不仅影响代码质量，还能减少错误数量。

XP 最具争议的信条是反对加班（即让程序员工作到精疲力竭），甚至“禁止”加班。其论点是，当项目得到适当的规格说明、预算和管理时，起初就不应该需要加班；并且当加班通常被需要时，项目无论如何也注定会延期完成。





## 何时使用 XP

极限编程（XP）最适合用于风险较高的项目。也许项目有紧迫的截止日期需要满足。也许某些未知因素或动态需求意味着所提议的解决方案不能绝对保证满足客户的最终需求。可想而知，所提议的解决方案可能非常前沿，以至于存在根本无法工作的风险。

实际开发团队规模应较小——不少于两人，且不超过 10 或 11 人——项目团队的所有成员（不仅仅是开发团队）都有权对构建过程负责。

XP 的预期成果如下：

- 开发团队的生产效率大幅提高。
- 客户满意度更容易实现。
- 高质量标准得以达成并保持。
- 客户需求得到更精确的满足。
- 截止日期得到更准确和一致的满足。

编程社区中关于 XP 的相对成功性和可行性存在大量争论。通常，巨大的商业压力使得遵循这一范式根本不可能。然而，与任何范式一样，它只是一个模型——一个值得追求的目标。您可以在 http://www.extremeprogramming.org/ 上找到关于 XP 实践和建议的更多详细信息。

## 变更管理

在几乎每个规模的项目中，客户都会提出变更请求。管理这些变更至关重要。不仅要评估所做任何变更的商业影响，还必须理解对根深蒂固的软件或系统架构进行重大变更可能造成的巨大破坏。

本节将探讨客户最常提出的几种变更类型，以及处理每种变更的最佳方式。

## 规范修订

规范修订不仅不可避免，而且应积极鼓励。您的客户会希望对您制定的规范进行更改，因为几乎可以肯定，您第一次就无法完全准确地把握需求。

将所有变更请求汇总到 48 小时周期内。如有必要，使用 Microsoft Project 或 BaseCamp（http://www.basecamphq.com）等变更管理工具。每 48 小时，将前两天的变更纳入规范的新版本，并提供给客户。

务必在变更请求提出后尽快让客户知晓任何（出于各种原因）不可行的请求。这就是为什么与客户的工作进度会议必须由具有应用开发实践知识的人员参加至关重要；仅派“商务人士”去是适得其反的。

## 签字后产生的规范变更

如果客户在签字确认规范后请求变更，您可能会遇到麻烦。首先，不要慌张。您占据道德高地。客户在您的规范上签字，表明他或她对所交付成果100%满意。严格来说，如果您需要为变更向客户收费，您有权这样做。

不过，在做出决定之前，请先咨询团队的其他成员。尝试确定您的团队在设计和/或构建阶段进展到什么程度。尝试以工时为单位，量化将流程退回到规范阶段以便实施请求变更所涉及的干扰程度。

如果您能为这项工作定价，请自行判断是否应将此成本转嫁给客户。通常情况下，在这些情况中表现出一些宽容和灵活性有利于良好的客户关系，除非此类情况频繁发生。

如果您决定继续推进变更，请务必向客户明确说明其时间影响，并就变更可能要求的任何修订里程碑达成协议。确保您的项目团队同意，并且新的时间表中包含缓冲余量。

## 因理解差异产生的争议

有时，客户可能会质疑对规范的理解，并因此请求变更。这类查询始终难以管理。毕竟，您不能直接指责客户完全错了。处理此类情况的最佳方法是尽量在规范中力求严谨和具体，尽可能避免歧义，从而在一开始就尽量完全避免此类问题。

不过，当歧义确实出现时，请做好与客户协商的准备。仔细倾听客户的关切，并努力理解其观点。与您的团队讨论实施所涉变更所需的时间，然后进行一个简单的商业测试：从真金白银的角度来看，争论这一点是否值得？

## 客户报告的缺陷

请务必仔细确定客户关心的是缺陷还是系统变更。在此阶段，客户提出的任何交付后变更几乎肯定超出规范范围，因此应视为额外的、可收费的工作。

始终将客户报告的缺陷作为优先事项进行响应，即使它们看起来并非缺陷（例如，客户自身操作失误）。使用 Mantis 等缺陷跟踪系统跟踪所有报告的缺陷，并向客户提供访问权限，以便他们可以自行报告。鼓励客户使用该系统，而不是立即给您打电话。

客户通常对缺陷表示理解；如今大多数人都足够开明，能够接受“这种事情会发生”。快速、高效、有条理地响应（即使在系统上线后）也可能意味着是获得同情还是接到愤怒电话之间的区别。

## 摘要

您现在知道，在赢得业务并一直持续到项目完成之前，保持严格的方法论的价值。您已经了解可能参与项目的各类人员，并考察了运行项目本身的两种不同方法论。您还研究了几种理论范式，可能会在构建过程中应用这些范式。

最后，本章简要概述了变更管理以及如何最好地处理由此产生的情况。

在第 18 章，您将了解如何为项目规划合适的硬件和系统基础架构。

## 系统架构

现在您已经阅读了几百页的软件架构细节，可能很想立即着手构建您的最新项目。您已规划好系统、挑选好人员、选择了合适的方法论，并了解了详细说明业务需求和功能集的规范。然而，最后需要考虑的——系统架构——不应轻率对待。

本章将使您了解系统架构的基础——它是什么、为什么重要，以及如何基于您对应用程序架构所做的决定，有效地开展最适合您项目的系统设计。

### 什么是系统架构？

最简单来说，系统架构是指支撑您计划构建的应用程序的基础架构。一般而言，这包括以下内容：

- 您的应用程序将部署在其上的硬件性质
- 服务器（或服务器群）的配置、连接和保护的具体方式
- 使用防火墙、负载均衡器、交换机和路由器等专用设备
- 这些设备的物理位置，以及电力和互联网连接的提供

如您所料，这是一个庞大的主题。接下来几页的讨论仅涉及表面，但希望它能提供足够细节，让您开始思考系统要求，并鼓励您探索更多资源以了解更多。





## 为什么这很重要？

为您的应用程序选择合适的基础设施至关重要。作为应用程序开发人员，您在工作室里可能只有一台开发服务器。这台机器可能同时充当 Web 服务器和数据库服务器，或许还同时运行 MySQL 和 PostgreSQL。如果您不仅使用 PHP 进行开发，可能还有其他应用服务器和编程语言环境（例如 J2EE、Python、Ruby 等等）。这台机器可能放在办公室的服务器机柜里，与公司其他基础设施放在一起。在某些情况下，这个环境可能非常适合较小应用将要部署到的简单共享托管环境。然而，企业级应用程序通常需要比单台服务器所能提供的更多的容错能力、性能能力和安全性。

这本书的一位作者最近为一家主要包装商品制造商部署了一个应用程序，该应用通过一个流行且大量做广告的 Web 应用程序每月传输超过 2 TB 的数据。典型的小型自研应用每月 20 美元的共享托管环境会在这种负载下迅速崩溃。然而，通过仔细的规划、对媒体购买（网站计划投放的广告数量和性质）的深入了解、对应用程序性能参数的仔细分析以及对系统架构原理的掌握，设计了一种托管方案，能够快速扩展到该吞吐量级别且没有中断。

在这本书的后面，您将了解更多关于 *质量保证 (QA)* 原理的内容，这些原理对于避免计划外中断也至关重要。您现在可以通过设计一个有效的系统架构来补充和支持您已开发的软件架构，从而为自己节省大量时间和麻烦。

## 需要做什么？

您的系统架构实际上是生产环境的作战计划。您很可能希望单独编写一份支持文档，或将计划纳入现有的技术规范中。无论哪种情况，获得关键利益相关者的认可都是必不可少的，因为成本可能非常高昂。营销活动与技术预期之间缺乏协调是问题和非计划停机的常见原因。

对预期负载和计划流量高峰做出经过仔细研究的假设，构成了系统架构的核心。随着您与客户共同制定这份方案，这些知识可以转化为有效的系统决策。

以下是需要做出的关键决策：

- [ ] **托管** — 应用程序将物理部署在哪里？这是否是合适的环境（即，配有空调和不间断电源）？如果它是现有企业数据中心的一部分，是否已对带宽的额外需求做出合理安排，并考虑了安全因素？

- [ ] **互联网连接** — 需要哪种互联网链路？谁将提供？可能需要多少费用？在 ISP 出现中断的情况下，内置了哪种冗余？

- [ ] **服务器** — 支持该应用程序需要多少台服务器，它们的规格是什么？

- 网络 — 哪种拓扑最能支持这些服务器？

- 冗余与韧性 — 需要哪种保证的可用性？可以有单点故障吗？

- 维护 — 谁将负责维护每台服务器及其软件？

- 安全 — 如何从外部世界保护基础设施？

这些决策将在本章后面进行更详细的探讨；但首先，我们要直面现实，刚才提出的反问句通常不是可以直接问客户的问题。

虽然您偶尔可能会遇到客户对系统架构拥有完全所有权并只希望您构建应用程序的项目（在这种情况下，您可以跳到下一章），但更可能的情况是，您被期望根据客户告诉您的内容，或根据您提出的问题所得出的答案来做出重大决策。

因此，更可能的情况是，您将是那个必须提出问题的人。这些问题应旨在收集大量信息，然后您可以利用这些信息来设计环境。在下一节中，您将了解应该提出哪些问题。

## 确定业务需求

作为初始发现阶段的一部分，尽早确定客户的托管要求至关重要。以下是几个关键考虑因素：

- 谁负责托管该应用程序？ — 有些客户拥有熟悉设置 Web 应用程序环境的现有 IT 部门。许多客户没有，在这种情况下，责任可能会落到您和您的团队身上。

- 是否存在应该或可以利用的现有基础设施？ — 如果已经存在一个非常好的环境，则没有必要创建不必要的基础设施。如果它不存在或不够好，那么这项投资是合理的。

- 该应用程序是否需要与其他系统通信？ — 例如，如果身份验证和授权必须针对客户的 Windows Active Directory (AD) 系统进行，那么托管必须以允许 PHP 跨越任何安全障碍并与 AD 系统通信的方式进行安排。例如，如果应用程序必须提供来自大型机的账单数据，该信息将如何提供给 PHP？

- 计划流量水平是多少？ — 这通常是一个很难回答的问题，但除了盲目猜测或得出过于乐观的“期望”数字之外，还有几种方法可以得出合理的数字。例如，您可以查看媒体购买情况。如果三个月内将有 1 亿次标准横幅广告展示，您可以假设平均点击率为 0.1%。这将导致每月预计流量为 33,000 访客（平均），即每天约 1000 名访客。这是确定面向营销的网站流量水平的有效方法。对于更偏向事务的模型（例如，旨在处理保险索赔信息的应用程序），您可以通过查看每天处理的典型索赔数量的历史数据来确定预期流量水平。

- 预算是多少？ — 复杂的托管平台每月可能花费数千美元，并要求签订 12 个月（或更长）的合同承诺。如果应用程序需要这种方案来处理预期流量，那么是否有现金可用来支付？

- 是否有任何特别复杂的安全考虑或法规要求？ — 用于收集电子邮件地址以供营销目的的网站需要合理的安全性。但是，收集社会安全号码和信用卡详细信息的应用程序需要完全不同的配置和进一步考虑。如果应用程序用于受严格监管的行业（例如银行业），可能还有其他法规要求。

- 存储需求是什么？ — 如果这是一个主要为只读的应用程序，您可以检查 PHP、数据库、图像和其他资产以立即确定存储需求。但是，对于任何涉及用户输入的应用程序，您必须仔细规划存储考虑因素。同样，请记住可能需要保存比您原本计划的多得多信息的任何法规要求（尤其是在应用程序日志、电子邮件和备份方面）。应用程序用户数量的增长应映射到每个用户的平均存储需求。

- 最后，备份要求是什么？ — 如果应用程序主要是只读的，并且数据、源代码和其他资产已在其他地方备份（例如，在 subversion 仓库中），那么所需的备份策略比高度事务性网站（例如电子商务应用程序）或写密集型应用程序（例如 wiki 或热门博客）要简单得多。

这些业务需求直接转化为系统架构考虑因素，您现在可以开始检查这些因素。

## 确定硬件需求

需要考虑几种硬件，每种都有重要作用。在较小的安装中，一台硬件可能执行多种功能，而在更大的架构中，这些功能可能由专用设备处理。

## Web 服务器

作为用户活动的第一线，这是 PHP 代码执行的地方，同时也提供 HTML、图像和其他资产。这些机器将运行 Apache 或其他 HTTP 守护进程，它们是首先考虑一些冗余（以多台负载均衡机器的形式）的地方。还应考虑 RAID 1（镜像）硬盘，以防止灾难性硬件故障（硬盘故障的频率比您想象的更高）。

## 数据库服务器

对于访问量相当大的网站，强烈建议使用专用机器或机器阵列来处理数据库事务。通过将繁重的数据处理卸载到单独的硬件上，您可以使慢速查询在不中断更常规前端应用程序功能性能的情况下进行。此处也强烈推荐使用 RAID 5 硬盘，同时还应具备一些冗余


以多台集群数据库机器的形式。PostgreSQL 和 MySQL 如今都拥有相当稳健的集群支持，以及关于如何最佳实现的大量文档。

## 负载均衡

在多台机器处理相同功能的任何地方，都必须确定请求被导向哪台物理机器。实现负载均衡有三种方式：

- 基于 DNS 的负载均衡
- 基于软件的负载均衡
- 专用负载均衡

### 基于 DNS 的负载均衡

基于 DNS 的负载均衡涉及为单个主机名创建指向多个 IP 地址的 DNS 记录。例如，通常，你可能会有一个如下所示的 DNS 条目：

```
$ORIGIN example.com.
www	IN	A	192.168.111.222
```

你也可以为该同一记录指定一个地址池，如下所示：

```
$ORIGIN example.com.
www	IN	A	192.168.111.222
www	IN	A	192.168.111.223
www	IN	A	192.168.111.224
```

当客户端尝试解析你 Web 服务器的地址时，他们的计算机将从你指定的地址池中随机获得一个地址。因此，不同的客户端将使用不同的 Web 服务器。此方法非常容易实现。

这种方法的缺点有两个。首先，许多操作系统（尤其是 Windows）在执行名称查找后会缓存 IP 地址。这意味着对同一主机名的后续请求将继续将流量发送到该机器，无论该机器上已有多少额外负载。其次，如果该机器宕机，那么网站对用户而言将看起来无法使用，因为用户的操作系统不会尝试另一次名称解析。

### 基于软件的负载均衡

第二种方法是在 Web 服务器本身上使用基于软件的负载均衡。在拥有两台 Web 服务器的系统中，一个公共 IP 地址在它们之间的虚拟网络接口上共享。（这是 www 主机名将解析到的 IP 地址。）该软件允许服务器之间协商哪台机器将处理下一个传入请求。对于两台机器来说，设置起来相当简单，但当服务器超过两台时，情况就会开始变得有点棘手。

### 专用负载均衡

第三种方法是使用专用负载均衡器。这可以是运行 Linux 和开源负载均衡应用程序的商品硬件，也可以是专用商业设备。该机器被分配公共 IP 地址，而 Web 服务器被分配在 Web 服务器和负载均衡器共享的内部网络上的私有不可路由 IP 地址。负载均衡器处理传入请求并将其转发到最能处理它的机器。

可能的负载均衡方法包括以下内容：

- 轮询 — 将每个请求导向可用机器列表中的下一台机器
- 基于会话 — 将特定会话中的所有请求导向同一台机器。（给定用户的所有活动将由单台物理机器处理。）
- 方法 — 这些可以检查每台机器的连接数，将请求导向负载最小的机器。

如果机器变得不可用（例如发生崩溃），负载均衡器会自动将其从池中移除。在使用专用负载均衡器时，应始终考虑使用冗余对。你可以有 20 台 Web 服务器，但即使只有一台负载均衡器发生故障，也没有人能访问这些 Web 服务器，应用程序将宕机。

## 防火墙

入侵预防和检测是无数书籍的主题，此处不作深入探讨。虽然每台机器都能运行自己的防火墙软件，但专用设备具有单点管理的优势，并将数据包分析的 CPU 负担卸载到不参与应用程序处理的机器上。与负载均衡器一样，应用程序架构师应考虑使用冗余防火墙对，以防其中一台发生故障。

## 了解物理环境和连接性

服务器的物理位置是性能、安全性和可靠性的重要考虑因素。毫无疑问，这里的最佳方法是专用数据中心。此类设施的唯一目的是为服务器和其他设备提供安全、空调、受控的环境，并提供带宽和 IP 地址。

由于这些设施存放的是专为远程访问设计的服务器，它们对于人类来说往往是相当不友好的环境。致癌阻燃剂的使用在大多数国家和地区已被禁止，但强烈的空调可能会让即使是最健康的软件架构师在退出时也喘不过气来。然而，这种环境对服务器来说是完美的。

数据中心有两种类型：运营商特定型和运营商中立型。运营商特定型数据中心通常由提供带宽和连接的 ISP 拥有。因此，只有该特定 ISP 可用于连接。运营商中立型中心只关注设备托管，并使你能够与任何数量的在当地提供连接的 ISP 连接。

两者都有各自的优缺点。运营商特定型中心往往拥有更一体化的支持和计费方式，这当然可以减少麻烦。然而，使用运营商中立型中心时，如果某个 ISP 被证明不可靠或不合适（或者你只是想换一下），你可以移动设备而无需物理移动它。无论哪种方式，你通常会得到一个产品，其中包括一定量的机架空间、一组 IP 地址（或者在某些情况下，是一组地址和它们网络上的单个 IP，需要你自备路由器），以及一个交接点——一个进入你 ISP 网络的物理以太网链路。你的 ISP 当然会为你启动和运行提供相当多的支持和帮助，但从一开始就订购正确的产品非常重要。

你的 ISP 会向你出售以承诺信息速率（CIR）为单位（以兆比特计）的带宽数量，或者以每月传输量（以千兆字节计）的数量。

### 计算 CIR

CIR 几乎总是更昂贵的选择，但对于大型网站来说是必不可少的。它使你能够在给定带宽内尽可能多地推送流量。要计算 CIR，请考虑你的应用程序可能需要支持的同时会话数量。

例如，假设你的 Webmail Web 应用程序必须支持总共 1,000 个同时会话。这代表 1,000 人在任何给定时间点都在使用该应用程序。它不代表 1,000 个同时连接。这一区别很重要。在使用任何给定应用程序时，每个会话包括一阵 HTTP 请求（页面加图像），然后是阅读内容的暂停，接着是另一阵 HTTP 请求，以此类推。考虑到这一点，连接仅在给定百分比的时间内建立。

同样重要的是要了解每个页面上可能的*停留时间*。只有用户测试才能准确确定这一点，但你可以将其估计为消费者网站上典型网页的约 30 秒，或 Web 应用程序（例如 Webmail 应用程序）的 60 秒。

如果你假设每个页面大约需要 10 秒加载，那么在 Web 应用程序上，每个会话将呈现*每个会话的模式*：10 秒流量，接着是 60 秒无流量，接着是 10 秒流量，以此类推。

通过一个快速且稍微粗略的计算（即 10 秒除以 60 秒），你可以看出在任何给定时刻，任何给定会话传输数据的可能性约为 15%。因此，对于 Web 应用程序，同时连接数可能等于同时会话数的 15%，而对于 Web 站点则为 2%。

在前面 1,000 个同时会话的示例中，你可以看出这代表 150 个同时连接；但有些用户使用 6 Mbps 的有线调制解调器连接，而另一些人使用 56 KB 的拨号上网，你如何知道这代表什么样的带宽需求呢？

这时来自客户的挖掘数据就派上用场了。客户很可能掌握有关其预计人群统计的一些数据。例如，办公室里的人都可能拥有 T1 或 T3 线路，但这些线路很可能在每个办公室的其他人之间共享。对于家庭用户，你可以利用全国范围的宽带普及率数据来推算宽带和拨号上网可能占据的百分比。更好的是，如果你能访问类似过去项目的服务器日志，就把它们找出来自己做计算吧。



## 计算每月传输量

另一个可选方案是每月传输限额，即在该限额内可随意使用ISP带宽的“自助餐式”服务。根据涉及的站点类型，这可能更便宜。例如，如果你在下午6:00有大量用户涌入，但其他时间段大量空闲，此选项可能适合你。

计算每月传输需求很简单：将你预计每月收到的用户会话数乘以每个会话传输的数据量即可。

例如，若典型会话包含10个请求，且每个请求的平均页面大小为50 KB，则每个用户会话将消耗约0.5 MB的传输量。如果5,000名常规用户每天各使用系统一次，则相当于每天5,000个会话，即2.5 GB的传输量。按一个月计算，总计75 GB。

## 机架空间考量

所需机架空间显然取决于你将使用的服务器数量。不过请记住，任何网络设备（如交换机和路由器）也会占用空间。

在规划未来扩展时，你可能希望在当前需求之外预留一定的空闲机架空间。例如，如果你在共享机架中只购买五个单位，那么你两侧的空间几乎必定会被ISP很快出售，因此未来设备可能不得不部署在其他位置。

## 网络考量

将所有设备连接起来可能看起来是简单的部分，但在这个环节稍作规划，就能为你日后省去许多麻烦和烦恼。

考虑每个接口上的流量，并围绕此进行规划。例如，数据库密集型Web应用程序将与数据库服务器产生巨大的来回流量，这些流量与客户端Web浏览器发出的Web请求完全无关。考虑到这一点，你应该考虑在每个Web服务器上配置一个单独的接口来连接数据库服务器。

这种配置很常见。你有一个核心交换机，所有Web服务器都连接到它，你的防火墙内部接口也连接到它。你的数据库交换机连接到每个Web服务器的辅助网卡，以及你使用的每个数据库服务器的网卡。

结果，Web服务器与数据库服务器之间的流量不会干扰真正的Web流量——从而提升性能。如果你使用的是高端交换机，甚至可以使用虚拟局域网（VLAN）将，比如说，24个端口分隔为两个各12个端口的虚拟交换机——一个用于Web服务器和防火墙，另一个用于数据库服务器和Web服务器的辅助网卡。

这种配置的副作用是为你的数据库提供了额外的保护层。由于没有暴露给Internet的接口，它们离被攻破又远了一步。

## 存储考量

对于需要存储大量数据的大型应用程序，机架式服务器内置的硬盘可能不够用。存储区域网络（SAN）通常由管理较好的托管服务商提供，并且通常允许近乎无限（且可扩展）的硬盘空间，这非常适合需要快速扩展的存储密集型应用程序。

其他存储方案包括磁盘外壳，其更高级的形式允许多个服务器连接到同一磁盘阵列。还有一些基于Web服务的方案（如Amazon的S3），它们使用第三方存储数据，并提供用于上传和检索的API。

## 维护管理

托管服务商将在你的服务器上执行基本维护（包括内核补丁、软件安装和更新），并提供一般系统管理支持。无论你选择此方案还是决定自行处理这些任务，都取决于你以及你与客户的关系。

如果你确实决定承担这份工作，那么你应该为服务器维护制定每周行动计划。这应是一份每周需要执行的任务清单，以确保你的服务器保持清洁、高效且为最新状态。你的行动计划中的任务应包括以下内容：

- [ ] 内核版本 — 每台服务器是否运行最新版本？
- [ ] Apache和PHP版本 — 每台服务器是否运行最新版本？
- [ ] PHP依赖项 — libxml2、libxslt和expat是否都为最新版本？
- [ ] 磁盘空间 — 每台服务器的每个分区是否有足够空间？是否有日志文件失控增长并需要修剪？特别是Apache，不允许任何给定日志文件超过2 GB，如果超过，会非常严重地崩溃。

## 总结

在本章中，你了解了稳健系统架构对你应用程序的重要性。在掌握系统架构定义后，你接着了解了应向客户提出的正确问题，以用大白话确定确切的系统需求。

接下来，你学习了如何将这些信息转化为合理的技术决策。这样一来，当你的项目上线时，就不会遇到不愉快的意外。

你如何呈现这些信息主要取决于你。一份三页或四页的客户参考指南可能就足够了，或者你可能希望将其纳入技术规范中。重要的是立即进行规划，远在应用程序开发之前。稍后的负载测试将确保你的理论正确。现在略有错误的预测，也好过完全没有预测。

遵循你迄今所学的项目管理方法和设计模式，第19章将探讨你如何使用工具包组件和新获得的知识来构建一个销售自动化项目。

## 构建应用程序

既然你了解了技术的工作原理，这就是你将其整合为一个统一整体的机会。本章讲述的是从零开始开发软件，由于这是一个小型项目，你将大量使用极限编程（XP）的许多技术。

在开始一个重要新项目的所有喧嚣和戏剧性中，很容易在脑中跳得太远，开始思考_如何_做事，而你应该尽力思考_应该做什么_。

因此，收起你的电脑。忘记你的登录名、密码、数据库，并且，暂时你也不需要PHP。相反，你将使用一种人类在过去几千年中不断完善的技术——纸。

是的，纸就是技术。它无处不在、价格低廉、即使弄湿也能阅读，并且不需要电池（除非你处于黑暗中）。同一种媒介类型支持只写、可重写以及彩色和黑白墨水。当纸张被裁剪成小型索引卡尺寸时，它可以很好地用于表示你的PHP类。这些卡片不仅可移动，还可以贴在墙上、交换、订书、夹住、分类和存储。

简而言之，你的设计和开发过程在很大程度上依赖于社交互动、智慧和千年技术，就像依赖计算机硬件和软件一样。

### 项目启动：星期一

你精神饱满、兴高采烈地到达工作地点。虽然Widget World IT部门正忙着为你的第一天工作设置电脑，但幸运的是，你的办公用品储物柜里有今天工作所需的一切：

- [ ] 钢笔
- [ ] 3 × 5索引卡
- [ ] 4 × 6索引卡

Bridget（Widget World销售自动化工具经理）坐在你附近，准备在你的第一天与你一起工作。Bridget提到，因为Edwina（Widget World东部区域销售经理）今天在办公室，她已安排了一次会议。Harold是一名销售人员，由于冲突碰巧在办公室工作，未来两周他都有空。Wade（Widget World会计师）也在，并且每天上午9:30到午餐时间他都100%有空（如有需要）。

去开会吧，别忘了带上你的卡片。

### 倾听心声

在会议开始时，每个人自我介绍完毕后，你解释说，你来这里是为了收集他们对新系统的期望以及他们希望如何使用新系统的故事。

使用你那千年老技术的笔和纸，记录这些故事。把每个故事写在单独的卡片上，并坚持让Wendy、Wade和Edwina都参与进来。当然，他们可能会对什么在技术上可行、什么不可行，谁必须对什么签字，以及工作流程如何提出问题。

请记住，每个故事（或功能）都应被分解，使其大小大致相同。在这个练习中，大小意味着你实现该故事所需的精力量。这可能是最困难的部分，因为作为开发者的你需要始终保持整体视角。

确定每个故事作为时间单位的正确大小并非易事。尝试将时间单位控制在最小半天，最多一周或两周左右。同样，每个故事的大小应大致相同。故事大小和时间估计将在以后用于帮助你确定工作量，并更好地估计未来任务。

例如，如果一个功能是“建造一艘火箭飞船”，则将其分解为更小、更易管理的部分，例如“逃生舱应在逃生舱门关闭后10秒内发射”。

你近乎全天的会议产生了以下故事。记录谁建议了（或坚持了）它不是强制性的，但这里展示了一种方法，让你了解这个过程通常是如何进行的。从实体表单开始（参见图19-1）通常是一个不错的起点，因为它符合当前的工作流程和结构：

- [ ] 故事1 — Edwina：“我们使用这种可传真的表格来跟踪销售人员的联系人，这也是我们根据反馈决定下一步将他们派往何处的方式。能够以某种电子格式访问这些信息将非常棒。”
- [ ] 故事2 — Wade：“收集销售人员的所有日常差旅费用和收据既费时又容易出错。我们希望每周收集一次，按日期和类别进行小计。”
- [ ] 故事3 — Harold：“有时我需要解释某笔费用。例如，我为一次特殊的FedEx快递在‘邮费’下记录了30美元。我希望有办法在费用报告底部添加评论。”
- [ ] 故事4 — Wade和Harold：“费用报告应以类似电子表格的方式对项目进行小计。”
- [ ] 故事5 — Wade：“当提交费用报告时，我希望收到带有摘要的通知。”
- [ ] 故事6 — Edwina：“当提交联系人报告时，我希望收到带有摘要的通知。”
- [ ] 故事7 — Harold：“我希望每个销售人员都收到相同的通知，以便他们有机会再次核对。”




- Story 8 — Edwina: “The mailroom needs to be notified when a contact report contains a literature request.”
- Story 9 — Edwina and Harold: “Each salesperson needs to have his or her own private login.”
- Story 10 — Wade: “I don’t authorize the cash advances but I still need to track them. Add “Less Cash Advance” to the expense report.”
- Story 11 — Harold: “The cash advances come from multiple sources, so allow the salespeople to control the amount. Don’t automatically debit it from a special account; just allow it to be entered in the expense report.”
- Story 12 — Wade: “Store the amount of the cash advance so that I can track the total amount per salesperson.”
- Story 13 — Wade: “I’d like to be able to get the data from the expense reports in order to feed it into my special spreadsheets.”

![](img/a1b732997d9cb194dceec0570dc79710_448_0.png)

Figure 19-1: Faxable form

At this point, you have a plan for implementing the first revision of the software that Widget World needs in order for its sales force to be more productive.

This should round out your first day at work. The client stories that you collected today are the seeds of a plan that is based on the needs of your clients. Of course, you’re not going to start writing the software yet, because your plan is not yet complete.

### Story Weight Estimation

Now that your story sizes are roughly in the same ballpark in relation to each other, you can sit down and try to estimate how much effort it will take to implement each one. This is done by assigning a numerical value to each story. A simple project might have only three values:

- [ ] 1（轻量）
- [ ] 2（中等）
- [ ] 3（沉重）

Another option is to take a stab at guessing the relative weight of each story implementation by the number of perfect-engineering time units that it would take to implement it. A *perfect-engineering time unit* is the number of hours, days, or weeks that you envision a task taking if absolutely nothing goes wrong, and your performance is stellar.

For example, consider Story 9: “Each salesperson needs to have his or her own private login.” Think about that for a moment: “Private login” means that you shouldn’t be dependent on something like Apache’s built-in security, but it could run the gamut from PHP sessions to URL rewriting, including something in between the two.

However, let’s face it: Sessions are not that difficult to do correctly if done early. Therefore, if you were using the simple point scale, it would be rated as a “1（轻量）.” If your points are based on “完美工程半天,” it would probably still be rated as a “1.” However, if your points are based on “完美工程周,” and the particular story would be complete in a matter of hours, it’s an indication that this particular story needs to be more uniform in size with your other stories, which are presumably based on “完美工程周” rather than days or half-days.

Let’s walk through a few more stories. Consider Story 13: “I’d like to be able to get the data from the expense reports in order to feed it into my special spreadsheets.” Wade needs access to the expense-report data in a format that is importable by spreadsheet software.

Although the point system is based on “完美工程半天,” the word “完美” here is deliberately given some often all-too-necessary wiggle room in its exact meaning. For example, this story was submitted by Wade, the Widget World accountant, and it may very well apply only to his role as an accountant. This means that, in addition to using a login screen, you’ll need to classify the users of the system into Wade and not-Wade — that is, accountant and user. Write that information directly on the card.

Spreadsheets can readily import data from files using comma-separated values (CSV文件), which technically isn’t challenging because it’s simply a different view of the data set. Therefore, adding a user classification system and outputting a data set as CSV would probably collectively rate as about one perfect engineering day, or in your system of perfect engineering half-days, 2 points.

Take a look at Story 5. Wade needs to be “notified, with a summary, when an expense report is submitted.” This is directly dependent upon the expense report described in Story 2, which includes “collecting all the travel expenses and receipts.” Write that dependency on the card, and estimate the story as being “slightly easier than Story 2.” Estimate the value after estimating Story 2.

Now, consider Story 6. Edwina needs to be “notified, with a summary, when a contact report is submitted.” Note that the functionality is similar to that of Story 5, so write it on each card.

Next, work through each story, estimating how long it will take, writing required features on each, and noting dependencies between them. Feel free to break stories up if they are too big; conversely, consolidate them if they are too small.

Here is the list you now have:

- Story 1: “Track the salesperson’s contacts using this faxable form.”
  - Basic employee information: 1 point
  - Each distributor/customer can be unique
  - One-to-many relationship between salesperson and customer: 1 point

Putting it all together (making sure that the Web form works and so on) would be another point, for a total of 3 points, or two perfect-engineering days.

- Story 2: “Collect the daily travel expenses and receipts of each salesperson on a weekly basis, subtotaled by day and category.”
  - This is the Travel Expense Report
  - One-to-many relationship between salesperson and customer
  - It should look sort of like a spreadsheet. This is a nontrivial request: 4 points
  - Broken down by category: 1 point
  - Getting everything right: 2 points
  - 7 points total

- Story 3: “Comments at the bottom of the expense report.”
  - Should probably be rolled into Story 2
  - That makes the relationship more interesting — rather than just being an employee-to-daily expense, you’re now charged with an employee-to-daily expense and employee-to-weekly comments of daily expenses, as shown in Figure 19-2: 2 points total
  - Keep as a separate story, but note that it’s dependent upon Story 2
  - 2 points total

## Part III: A Real-World Case Study

| sales person | | | | | | | Week starting: 5 Jan 2004 |
|---|---|---|---|---|---|---|---|---|
| | sun | mon | tue | wed | thu | fri | sat | |
| breakfast | 1 | | | | | | | |
| lunch | 2 | | | | | | | |
| dinner | 3 | | | | | | | |
| sub total | 0 | | | | | | | |
| Sales person comments: Blah blah... | | | | | | | | |

Figure 19-2: Comments at bottom of expense report

- Story 4: “The expense report should subtotal the items in a manner similar to a spreadsheet.”
  - Although just front-end work, it’ll be time-consuming: 4 points
  - 4 points total

- Story 5: “Notify accountant, with a summary, when an expense report is submitted.”
  - Via e-mail
  - E-mail configuration, management, and so on: 1 point
  - Dependent upon Story 2: 1 point
  - 2 points total

- Story 6: “Notify sales manager, with a summary, when a contact report is submitted.”
  - Each sales manager has multiple salespeople.
  - One-to-many relationship: 2 points
  - Dependent upon Story 5 but easy: 1 point
  - 3 points total

- Story 7: “Notify salespeople with expense-report details.”
  - If dependent upon Story 2: 2 points
  - If dependent upon Story 5: 1 point
  - 1 or 2 total points

- Story 8: “The mailroom needs to be notified when a contact report contains a literature request.”
  - Conditional notification: 1 point
  - If dependent upon Story 2 or Story 5: 1 or 2 points
  - 2 or 3 total points

- Story 9: “Each salesperson needs to have his or her own private login.”
  - Authentication: 2 points
  - Authorization: 2 points
  - 4 points total





- Story 10: “在报销单中添加‘减少预支现金’”
  - 与 Story 3 存在相同问题（报销单上的评论）。
  - 依赖于 Story 2。
  - 未借记，因此无需账户跟踪
  - 持久化，非计算：2 点
  - 总计 2 点

- Story 11: “允许销售人员控制预支现金的金额。不要自动从专用账户中借记它；只需允许在报销单中输入即可。”
  - 依赖于 Story 10。
  - 这个故事其实不算一个用户故事。它是对当前系统的批评。删除此故事，并在 Story 10 上添加注释：“未借记”。
  - 0 点

- Story 12: “存储预支现金的金额，以便我可以跟踪每位销售人员的总金额。”
  - 依赖于 Story 10。
  - 这个故事很简单。添加注释：持久化。
  - 0 点

- Story 13: “为电子表格导出报销单数据。”
  - 仅会计：1 点
  - 工作：2 点
  - 总计 3 点

你现在已经将用户故事分解，并完成了第一轮估算。此步骤可能需要多次迭代，并需要返回向客户询问诸如以下的问题：

- 通知能否利用电子邮件发送？
- 是否有三种类型的用户：经理、销售人员和会计？
- 会计能否接受 CSV 格式的报销单导出？
- 会计希望如何指定导出？（可以按员工、按员工和日期，或者按销售经理等不同方式进行。）

然而，在所有问题都得到回答后，你仍未脱离困境。毕竟，你并不确定系统是否支持发出的电子邮件；即使支持，你知道如何在 PHP 中实现吗？

## 优化你的估算

与你的客户交谈，并获取他们对新问题的回答。重要的是他们必须可用，因为你不希望这些问题耽误你的工作。此外，你的每个客户（Wendy，项目经理；Wade，会计；Edwina，销售经理；Harold，销售人员）在某种程度上都将使用该系统，所以这真的是他们的项目，而你是推动它运行的人。

与此同时，你的客户问题已得到回答：

- [ ] Q: 通知能否利用电子邮件发送？
- [ ] A: 是的，与电子邮件相关的任何摘要都应作为附件包含。
- [ ] Q: 是否确实有三种类型的用户：经理、销售人员和会计？
- [ ] A: 是的。
- [ ] Q: 会计能否接受 CSV 格式的报销单导出？
- [ ] A: 是的，他一直都是这样做的。
- [ ] Q: 会计希望如何指定导出：按员工、按员工和日期，或者按不同方式，例如销售经理？
- [ ] A: 只需按员工和日期。

这就只剩下技术问题了：

- [ ] 如何使用 PHP 发送电子邮件？
- [ ] 电子邮件附件又如何处理？

### 刺探

当然，最后两个问题是修辞性的技术问题。你的客户不知道你的技术问题的答案——那是你的专长。此时，你没有足够的信息来做出完整的估算。

是时候去做一些功课了，这称为 *刺探*。虽然这项工作可能看起来与主线无关，但它是必需的，用于确定你的思路是否会有回报，或者在本例中，回答一个技术问题。

留出一些时间来确定那些必然会出现的 *是否* 或 *如何* 问题。这些事情可能需要一些时间，可能需要一两天，但在此例中，答案很快就出来了。浏览 PHP API 后发现如下内容：

```
mail( "wade@widgetworld.com", "Email Spike Test", "One\nTwo\nThree" );
```

是的，PHP 可以轻松发送电子邮件，所以现在你必须对其进行测试，或与管理员交谈以使其正常工作。

至于电子邮件附件——那不太容易。PHP 不支持以易于使用的函数形式附加电子邮件，但这是因为 MIME 电子邮件定义已在诸如 RFC 822（消息头）、2045（MIME）和 2046（MIME 类型）等 RFC 中有详细记录。因此，大量阅读和少量编码得出了这个代码片段：

```
$mime_boundary = "<<<=+==X[". md5( time() ) . "]";
$headers .= "MIME-Version: 1.0\r\n";
$headers .= "Content-Type: multipart/mixed; \r\n";
$headers .= " boundary=\"".$mime_boundary."\"\r\n";
$message = "This is a multi-part message in MIME format.\r\n\r\n";
$message .= "\r\n\r\n";
$message .= "--".$mime_boundary."\r\n";
$message .= "Content-Type: text/plain; charset=\"iso-8859-1\"\r\n\r\n";
$message .= "Content-Transfer-Encoding: 7bit\r\n\r\n";
$message .= "\r\n\r\n";
```

上述代码遵循上述 RFC，这些 RFC 定义了 MIME 邮件头（$headers 中定义的行）以及在消息最终组装并交给你的消息传输代理 (MTA) 之前的消息内容。阅读 RFC 可能是一项艰苦的工作，所以请务必在真实的邮件系统上进行测试，使用与你的客户相同的邮件客户端，并使其无错误地运行。

这很容易就消耗掉至少 1 点。

## 估算技巧

既然你所有剩余的技术问题都已解决，你可以放心地继续填写你的用户故事估算：

- [ ] Story 1: 客户联系报告，3 点
- [ ] Story 2: 差旅费用报告，7 点
- [ ] Story 3: 费用报告评论，2 点
- [ ] Story 4: 作为电子表格的费用报告，4 点
- [ ] Story 5: 会计通知，3 点
- [ ] Story 6: 销售经理通知，3 点
- [ ] Story 7: 销售人员通知，1 点
- [ ] Story 8: 邮件室通知，2 点
- [ ] Story 9: 身份验证和授权，4 点
- [ ] Story 10: 持久化费用报告预支现金，2 点
- [ ] Story 11: 0 点
- [ ] Story 12: 0 点
- [ ] Story 13: 费用报告导出，3 点
- [ ] 总计：34 点

不要陷入认为 34 点仅等于 17 个完美工程日的陷阱，因为这里的关键词是“完美”。你将有会议要参加，会有快节奏和慢节奏的日子，更不用说要处理计划的变更，以及许多其他不完美的人为因素。

此外，这实际上只是你的第一次估算。在每个故事完成后，你会记录下实际耗时，一两周后，你的估算将变得更加精确，点数与时间的换算关系也将更加准确。

目前，你很满意。

## 发布计划

与 Wendy、Wade、Edwina 和 Harold 进一步交谈后，你意识到该项目的第一个“发布”分为三个不同的部分。（你可以将它们视为“桶”。）各方一致同意，这些部分需要大致按以下顺序发布：

- [ ] 客户联系报告
  - [ ] Story 9: 身份验证和授权，4 点
  - [ ] Story 1: 客户联系报告，3 点
  - [ ] Story 6: 销售经理通知，3 点
  - [ ] Story 8: 邮件室通知，2 点
- [ ] 差旅费用报告
  - [ ] Story 2: 差旅费用报告，7 点
  - [ ] Story 3: 费用报告评论，2 点
  - [ ] Story 10: 持久化费用报告预支现金，2 点
  - [ ] Story 4: 作为电子表格的费用报告，4 点
- [ ] 差旅费用服务
  - [ ] Story 5: 会计通知，3 点
  - [ ] Story 7: 销售人员通知，1 点
  - [ ] Story 13: 费用报告导出，3 点

他们提出的决定是，客户联系报告比差旅费用报告更需要及时交付。客户联系报告也是一个比差旅费用报告更“简单”的输入表单，交互更少，然而，客户联系报告也将代表对整个系统的近乎端到端的测试。

用户故事所属的每个“桶”都称为一个 *迭代*，在此例中，每个迭代的完成时间不应超过三周。目前，这是整体计划，每个迭代结束时都应该交付客户可以使用的东西。





因此，你的第一个目标是创建客户联系报告，并为销售人员配备完整的登录和通知功能。完成联系报告并完成第一次迭代后，你将从以下几个方面看到估计的效果如何：

- 相互之间
- 与你的原始估计相比
- 与时间或你每周的点数相比

每次迭代结束时，你需要后退一步，衡量进度，获取客户的反馈，并根据客户不断变化的需求和目标调整计划。不要太担心；此过程旨在灵活且能响应你和你的客户的需求。

到目前为止，你已经学会了如何将问题空间划分为用户定义的故事，以及如何创建故事并将其拆分为更多故事，或合并为大小大致相同的更少数量的故事。故事估算是一个持续的过程，反馈（例如相关的尖峰）将有助于解决技术问题。

与客户合作确定对他们最重要的事情非常重要，并且要就每个请求功能的难度向他们提供诚实的反馈。这样可以让你做出更好、更及时的估计。这也能让客户看到系统的实际运行情况，并就系统的当前状态做出明智的决策。

## 开始工作

现在，你和你的客户确切地知道第一次迭代（即客户联系报告）中将实现什么：

- 故事 9：身份验证和授权，4 点
- 故事 1：客户联系报告，3 点
- 故事 6：销售经理通知，3 点
- 故事 8：邮件室通知，2 点

## 概述故事 9 的详细信息

> “每个销售人员都需要有自己的私有登录。”

首先，这假设“销售人员”作为一个逻辑实体存在（不一定是 PHP 类，至少目前不是），因此让我们概述它的需求。

存在对基本可读用户信息的需求：

```
First Name
Last Name
```

是的，你既是名字也是数字：
员工 ID

由于用户必须登录系统，让我们允许他或她选择登录名和密码：

登录名
登录密码

你还需要知道该人员访问系统时的角色。虽然一个人的角色可能与职位相关，但职位往往是短暂的。此外，你必须确定三种角色之一：销售人员、会计师或销售经理。

公司角色

这引发了一些好问题。某人是否可以同时身兼多职？某人既可以是会计师又可以是销售经理吗？那销售人员和销售经理呢？温迪回答说：“可能不行；韦德和埃德温娜的职责不重叠。”探头看向韦德整洁的隔间证实了你的假设，给埃德温娜打电话也是如此。因此，角色是互斥的。

由于你负责身份验证，让我们决定如何使用系统。

## 编写测试

问自己几个问题：

- [ ] 你希望如何启用登录？
- [ ] 登录应该用于什么目的？应该是简单的身份验证吗？
- [ ] 谁应该使用登录功能？

你知道用户包含什么：

员工 ID
名
姓
公司角色

你还知道身份验证需要什么：

登录名
登录密码

回忆第 12 章中的 HTTPSession 类。现在不用去查找它；你现在不需要它——但这与两个尚未定义的类 WidgetSession 和 WidgetUser 一起使用是一个合理的选择：

```
<?php
$session = new WidgetSession(); // inherited from HTTPSession
$session->impress();
// authentication
$session->login("ed","12345");
if ($session->isLoggedIn() == false) exit;
$user = $session->getUser(); // returns WidgetUser
print $user->first_name;
print $user->last_name;
print $user->email;
// authorization
print $user->role;
print $user->isSalesPerson();
print $user->isSalesManager();
print $user->isAccountant();
?>
```

请记住，前面的代码片段只是“一种合理的场景”。它尚未成为正式的测试或可运行的代码。这仅仅是你脑海中关于使用新类的设想。当你对这种“假设”场景感到满意时，你会在测试中正式化其使用。让我们继续编写一些测试！

## PHPUnit

这里的想法是编写测试，以模拟你计划使用与当前故事相关的软件的方式。这被称为测试驱动开发，除了开发优势之外，你最终还会获得一套出色的测试。你在第 13 章查看应用程序架构时第一次接触到它。希望你仍然安装了 PHPUnit。

> 以你将要使用应用程序的相同方式进行测试，迫使你查看函数或对象并确定参数和其他元素。
> 这可以避免创建未使用的功能，或在错误的位置使用功能。

与“束缚你的手脚”恰恰相反，拥有一套测试为你提供了很大的自由度，因为你可以立即知道通过添加新功能或修改现有代码是否意外破坏了系统的遥远部分。

以下是一些旨在反映常见使用场景的新测试。将以下内容保存为 test.widgetsession.php：

```
<?php
require_once ("widgetsession.php3");
require_once ("lib/phpunit/phpunit.php");
class TestWidgetSession extends TestCase {
private $_session;
function setUp() {
$dsn = array ('phptype' => "pgsql", 'hostspec' => "localhost",
		'database' => "widgetworld",
		'username' => "wuser",
		'password' => "foobar");
	$this->_session = new WidgetSession($dsn, true);
}

function testValidLogin() {
	$this->_session->login("ed", "12345");
	$this->assertEquals(true, $this->_session->isLoggedIn());
}

function testInvalidLogin() {
	$this->_session->login("ed", "54321"); // fail
	$this->assertEquals(false, $this->_session->isLoggedIn());
}

function testUser() {
	$user = $this->_session->getUser();
	$this->assertEquals("Lecky-Thompson", $user->last_name);
	$this->assertEquals("Ed", $user->first_name);
	$this->assertEquals("ed@lecky-thompson.com", $user->email);
}

function testAuthorization () {
	$user = $this->_session->getUser();
	$this->assertEquals("Sales Person", $user->role);
	$this->assertEquals(true, $user->isSalesPerson());
	$this->assertEquals(false, $user->isSalesManager());
	$this->assertEquals(false, $user->isAccountant());
}
}

$suite = new TestSuite;
$suite->addTest(new TestWidgetSession("testValidLogin"));
$suite->addTest(new TestWidgetSession("testInvalidLogin"));
$suite->addTest(new TestWidgetSession("testUser"));
$suite->addTest(new TestWidgetSession("testAuthorization"));
$testRunner = new TestRunner();
$testRunner->run( $suite );
?>
```

但是，运行前面的代码时，你会得到以下错误：

找不到类 'WidgetSession'，位于 test.widgetsession.php 第 16 行

目前，让我们模拟适当的虚拟 WidgetSession 和 WidgetUser 类，以便测试至少可以运行。将以下代码插入 test.widgetsession.php 前一个列表的顶部：

```
class WidgetSession {
    public function __construct($one, $two) {}
    public function login() {}
    public function isLoggedIn() { return null; }
    public function getUser() {
        return new WidgetUser();
    }
}

class WidgetUser {
    public $first_name = "";
    public $last_name = "";
    public $email = "";

    public function isSalesPerson() { return null; }
    public function isSalesManager() { return null; }
    public function isAccountant() { return null; }
}
```

现在在 test.widgetsession.php 中再次运行测试。以下是 PHPUnit 的相应输出：

```
TestWidgetSession - testValidLogin FAIL
TestWidgetSession - testInvalidLogin FAIL
TestWidgetSession - testUser FAIL
TestWidgetSession - testAuthorization FAIL
4 tests run.
9 failures.
0 errors.
Failures
1. testValidLogin
   true type:boolean
   null type:NULL
2. testInvalidLogin
   false type:boolean
   null type:NULL
3. testUser
   Lecky-Thompson type:string
   type:string
4. testUser
   Ed type:string
   type:string
5. testUser
   ed@lecky-thompson.com type:string
   type:string
6. testAuthorization
   Sales Person type:string
   type:string
7. testAuthorization
   true type:boolean
   null type:NULL
```



- 8. testAuthorization
  - false 类型:boolean
  - null 类型:NULL
- 9. testAuthorization
  - false 类型:boolean
  - null 类型:NULL

在开发过程的这一点上，你的每个测试都应该能够在没有语法错误的情况下运行，但会失败。这是因为你尚未实现测试所针对的任何功能！所以，没错，第一次运行测试时，你应该为它们全部失败而感到高兴。请记住，测试是基于常见使用场景的，并且你应该测试场景所要求的所有功能。

现在，实现通过测试所需的实际代码是你的责任了。登录和会话过程可以相当轻松地修复，因为该行为存在于 HTTPSession 中。

针对 WidgetSession 处理容易解决的问题。由于 WidgetSession 正在为 HTTPSession 添加功能，因此扩展 HTTPSession 是合理的。因此，先从你的模拟 WidgetSession 类开始，并在 test.widgetsession.php 中扩展 HTTPSession，使其现在包含可工作的代码：

```
require("httpsession.php");
class WidgetSession extends HTTPSession {
    public function getUser() {
        return new WidgetUser();
    }
}
```

现在重新运行 test.widgetsession.php 测试：

- TestWidgetSession - testValidLogin 通过
- TestWidgetSession - testInvalidLogin 通过
- TestWidgetSession - testUser 失败
- TestWidgetSession - testAuthorization 失败
- 4 个测试已运行。
- 7 个失败。
- 0 个错误。

通过利用 HTTPSession 中固有的功能，你已经通过了一半的测试。

仍在编辑 test.widgetsession.php，首先通过重写 HTTPSession 的 getUserObject() 函数来返回 WidgetUser 类，从而开始处理 WidgetUser 对象。如所示修改 WidgetSession 的声明：

```
class WidgetSession extends HTTPSession {
    public function getUserObject() {
        $suid = $this->GetUserID(); // calling up from HTTPSession
        if ($suid == false) return null;
        // pull ourselves out of the database
        $stmt = "select * FROM \"user\" WHERE id = ".$suid;
        $result = $this->getDatabaseHandle()->query($stmt);
        return new WidgetUser($result->fetchRow());
    }
}
```

你的 WidgetUser 类必须保持其状态。但是，WidgetUser 类是从数据库中获取的，数据库可以以关联数组的形式返回数据。因此，只需将 WidgetUser 的状态存储在关联数组中。

当然，__set 和 __get 都需要重新定义。仍在编辑 test.widgetsession.php：

```
class WidgetUser {
    protected $contentBase = array();

    function __construct($initdict) {
        $this->contentBase = $initdict; // copy
    }

    function __get ($key) {
        if (array_key_exists ($key, $this->contentBase)) {
            return $this->contentBase[$key];
        }
        return null;
    }

    function __set ($key, $value) {
        if (array_key_exists ($key, $this->contentBase)) {
            $this->contentBase[$key]=$value;
        }
    }

    public function isSalesPerson() { return null; }
    public function isSalesManager() { return null; }
    public function isAccountant() { return null; }
}
```

再次重新运行 test.widgetsession.php 时，大多数用户测试都通过了，但有一个显著的例外：

- 1. testUser
- ed@lecky-thompson.com   类型:string
- null    类型:NULL

嗯，让我们更仔细地看看在第 12 章中定义的 PostgreSQL 版本的 user 表：

```
CREATE TABLE "user" ( id serial PRIMARY KEY,
    username varchar(32) default NULL,
    md5_pw varchar(32) default NULL,
    first_name varchar(64) default NULL,
    last_name varchar(64) default NULL
);
```

## 第三部分：真实世界案例研究

你可以看到 user 表缺少电子邮件字段，因此必须添加它，使表如下所示：

```
CREATE TABLE "user" (
 id serial PRIMARY KEY,
 username varchar(32) default NULL,
 md5_pw varchar(32) default NULL,
 first_name varchar(64) default NULL,
 last_name varchar(64) default NULL,
 email varchar(255) default NULL
);
```

你可以使用 ALTER TABLE "user" ADD "email" varchar(255) 语法来实现此目的。

运行 test.widgetsession.php 测试：

```
TestWidgetSession - testValidLogin ok
TestWidgetSession - testInvalidLogin ok
TestWidgetSession - testUser ok
TestWidgetSession - testAuthorization FAIL
4 tests run.
4 failures.
```

零个错误。

既然 testUser 已通过，请注意 testAuthorization。由于“role”尚未包含在数据库中，请也添加它。（'s' 的默认值是“销售人员”的缩写。）

```
ALTER TABLE "user" ADD "role" char(1) default 's';
```

表现在将如下所示：

```
CREATE TABLE "user" (
 id serial PRIMARY KEY,
 username varchar(32) default NULL,
 md5_pw varchar(32) default NULL,
 first_name varchar(64) default NULL,
 last_name varchar(64) default NULL,
 email varchar(255) default NULL,
 role char(1) NOT NULL default 's'
);
```

将一些状态检索访问器方法放入 WidgetUser 类可以解决大部分剩余问题。你仍在编辑 WidgetUser 类，该类目前暂时位于 test.widgetsession.php 中：

```
public function isSalesPerson() {
 if ($this->role == "s") return true;
 return false;
}

public function isSalesManager() {
 if ($this->role == "m") return true;
 return false;
}
```

```php
public function isAccountant() {
    if ($this->role == "a") return true;
    return false;
}
```

但是，测试在“role”上仍然失败，因为它期望一个人类可读的字符串，但实际上仅限于 s、m 和 a 这几个单个字符：

- 1. testAuthorization
- Sales Person 类型:string
- s 类型:string

回顾先前正在测试的内容：

```php
function testAuthorization () {
    $user = $this->session->getUser();
    $this->assertEquals("Sales Person", $user->role);

    $this->assertEquals(true, $user->isSalesPerson());
    $this->assertEquals(false, $user->isSalesManager());
    $this->assertEquals(false, $user->isAccountant());
}
```

请注意，由于下一个问题的性质，当调用 $user->role 时，期望得到“Sales Person”。请记住，该角色直接来自数据库，因此要么更改数据库，要么更改你的软件。

这个主意怎么样：因为你希望在 __get 函数中继续直接访问 $user->role，所以可以确定正在查询哪个角色，并将其分派到 getRole() 函数。

代码如下：

```
class WidgetUser {
    protected $contentBase = array();
    protected $dispatchFunctions = array("role" => "getRole");

    function __construct($initdict) {
        $this->contentBase = $initdict; // copy
    }

    function __get ($key) {
        // dispatch by function first
        if (array_key_exists($key, $this->dispatchFunctions)) {
            $funcname = $this->dispatchFunctions[$key];
            return $this->$funcname();
        }

        // otherwise return based on state
        if (array_key_exists ($key, $this->contentBase)) {
            return $this->contentBase[$key];
        }
        return null;
    }
    function __set ($key, $value) {
        if (array_key_exists ($key, $this->contentBase)) {
            $this->contentBase[$key]=$value;
        }
    }
    public function getRole() {
        switch ($this->contentBase["role"]) {
        case "s": return ("Sales Person");
        case "m": return ("Sales Manager");
        case "a": return ("Accountant");
        default: return ("");
        }
    }
    public function isSalesPerson() {
        if ($this->contentBase["role"] == "s") return true;
        return false;
    }
    public function isSalesManager() {
        if ($this->contentBase["role"] == "m") return true;
        return false;
    }
    public function isAccountant() {
        if ($this->contentBase["role"] == "a") return true;
        return false;
    }
}
```

请注意，`isSalesPerson()`、`isSalesManager()` 和 `isAccountant()` 都访问 `contentBase`，而不是调用 `$this->role`。否则，它将通过 `getRole()` 函数进行分派，而该函数返回诸如“Sales Manager”之类的人类可读结果。根据人类可读的结果尝试返回布尔值不是个好主意，因为它们可能会随意更改。

## 创建登录屏幕

既然你的 `WidgetUser` 和 `WidgetSession` 对象已正常工作，是时候将它们用于真实登录了。

虽然登录屏幕并不十分复杂，但你将继续使用 Smarty 作为模板系统，仅因为它很方便。




这是你的初始 index.php 文件：

```php
<?php
require_once ("Smarty.class.php"); require_once ("widgetsession.php");
$session = new WidgetSession(array(
'phptype' => "pgsql",
'hostspec' => "localhost",
'database' => "widgetworld",
'username' => "wuser",
'password' => "foobar"));
$session->Impress();
$smarty = new Smarty;
if ($_REQUEST["action"] == "login") {
$session->login($_REQUEST["login_name"],$_REQUEST["login_pass"]);
if ($session->isLoggedIn()) {
$smarty->assign_by_ref("user", $session->getUserObject());
$smarty->display ("main.tpl");
exit;
} else {
$smarty->assign('error', "Invalid login, try again.");
$smarty->display ("login.tpl");
exit;
}
} else {
if ($session->isLoggedIn() == true) {
$smarty->assign_by_ref("user", $session->getUserObject());
$smarty->display ("main.tpl");
exit;
}
}
$smarty->display ("login.tpl");
?>
```

屏幕的逻辑如下。如果表单的 action 变量为 login，则表示正在尝试登录，因此通过调用 $session->login() 尝试登录。正面结果通过渲染主菜单来处理。负面结果会导致设置一个错误变量，并且登录界面会再次显示给用户。

当然，如果你不是在尝试登录，则会检查 $session->isLoggedIn() 以确认会话中的登录状态。如果用户已登录，则显示主菜单屏幕。否则，会再次显示登录屏幕。

登录屏幕和主屏幕这两个界面，连同页眉和页脚，都很简单。

以下是 login.tpl 的代码：

```
{include file="header.tpl" title="Widget World Login"}
<h3>Please Login:</h3> <p>
{section name=one loop=$error}{sectionelse}
<font color="#FF0000">($error)</font><p>
{/section}
<form action="index.php" method="post">
<table border="0">
<tr>
<td width="20"></td>
<td>User:</td>
<td><input name="login_name" type="text" size="20" maxlength="50"></td>
</tr>
<tr>
<td width="20"></td>
<td>Password:</td>
<td><input name="login_pass" type="password" size="20" maxlength="50"></td>
</tr>
<tr>
<td width="20"></td>
<td></td>
<td><input type="submit" value=" Login "></td>
</tr>
</table>
<input type="hidden" name="action" value="login">
</form>
{include file="footer.tpl"}
```

## 第三部分：实际案例研究

以下是 header.tpl 的代码：

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
<meta HTTP-EQUIV="content-type" CONTENT="text/html; charset=ISO-8859-1">
<title>{$title|default:"no title"}</title>
</head>
<h1>Widget World</h1>
<hr><p>
```

以下是 footer.tpl 的代码：

```
<br/><br/>
<hr/>
For Widget World use only - testing environment.
</body>
</html>
```

以下是 main.tpl 的代码：

```
{include file="header.tpl" title="Widget World Menu"}
Welcome {$user->first_name} the {$user->role}!
<table border="0" cellspacing="8" cellpadding="8">
{strip}
{section name=security show=$user->isAccountant()}
<tr><td><h3>Accountant functionality goes here.</h3></td></tr>
{/section}
<tr>
<td valign="top">
<h3><a href="travel-expenses.php">New Travel Expenses</a></h3>
</td>
</tr>
<tr>
<td valign="top">
<h3><a href="customer-contacts.php">New Customer Contacts</a></h3>
</td>
</tr>
{/strip}
</table>
{include file="footer.tpl" }
```

图 19-3 展示了其外观。登录后，你将看到如图 19-4 所示的菜单。如果将 ed 的角色更改为会计（accountant），则 ed 会看到稍有不同的视图，如图 19-5 所示。

![](img/a1b732997d9cb194dceec0570dc79710_468_0.png)

图 19-3：登录屏幕

![](img/a1b732997d9cb194dceec0570dc79710_468_1.png)

图 19-4：主菜单

![](img/a1b732997d9cb194dceec0570dc79710_469_0.png)

图 19-5：Ed 的视图

恭喜！你的第一个用户故事现已完成。你利用 PHP 会话、数据库查询、PEAR::DB 和 PHPUnit 完成了大量工作，以实现确定谁在登录以及该用户应该能够做什么所需的功能，这绝非易事。

好好休息一下，享受吃饼干的时光；还有大量工作即将到来。

### 下一个用户故事

你之前的用户故事（用户故事 9：“身份验证与授权”）值 4 个点数。请记录完成这个 4 点数任务花了多少天或半天。

请回顾，本次迭代的客户联系报告包含以下内容：

- [ ] 用户故事 9：身份验证与授权，4 点数（已完成）
- [ ] 用户故事 1：客户联系报告，3 点数
- [ ] 用户故事 6：销售经理通知，3 点数
- [ ] 用户故事 8：邮件室通知，2 点数

是时候重新投入工作了。

### 客户联系需求

请回顾本章前面部分（参见图 19-1）中每周联系报告的要求。其数据要求大致如下：

```
CREATE TABLE contact_visits (
  emp_id integer NOT NULL,
  week_start date NOT NULL,
  seq integer NOT NULL,
  company_name varchar(40) default NULL,
  contact_name varchar(40) default NULL,
  city varchar(40) default NULL,
  state varchar(40) default NULL,
  accomplishments text,
  followup text,
  literature_request text
);
CREATE UNIQUE INDEX cv_pk on contact_visits (emp_id,week_start,seq);
CREATE INDEX cv_emp_id ON contact_visits (emp_id);
CREATE INDEX cv_week_start ON contact_visits (week_start);
CREATE INDEX cv_seq ON contact_visits (seq);
```

数据按周存储，与员工关联，且在包含序列列时具有唯一性。数据量可能很大。

请注意，state 字段长度为 40 个字符，以容纳非美国州份，以及加拿大和墨西哥的省份。还要注意，客户联系报告包含员工的部门，而当前用户表中尚不存在该字段。请继续添加它：

```
CREATE TABLE "user" (
id serial PRIMARY KEY,
username varchar(32) default NULL,
md5_pw varchar(32) default NULL,
first_name varchar(64) default NULL,
last_name varchar(64) default NULL,
email varchar(255) default NULL,
role char(1) NOT NULL default 's',
department varchar(40) NOT NULL default 's'
);
```

### 客户联系测试

考虑你打算如何使用客户联系数据。从这个输入屏幕来看，几乎所有表单数据都通过 Web 服务器提供，这意味着在准备将其持久化时，你需要从 WidgetSession 中获取员工 ID。

此外，在将数据写入表格之前，请考虑你需要的最低信息：id、week_start 和 sequence，使用如下的 PHPUnit 测试：

```
function testValidContactVisit() {
$cv = new ContactVisit (
array ('emp_id'
=> "1",
'seq'
=> "1",
'week_start'
=> "1980-01-01",
'company_name'
=> "test one",
'contact_name'
=> "Big One",
'city'
=> "Columbus",
'state'
=> "OH",
'accomplishments'
=> "phone call",
'followup'
=> "",
'literature_request' => ""));
$this->assertEquals(true, $cv->isValid(), "valid log");
}
```

此测试是 ContactVisit 所需的最低信息。因此，如果 emp_id、seq 和 week_start 包含任何值，则 isValid() 将返回 true。反之亦然，也应该进行相反的测试：

```
function testInvalidContactVisit() {
    $cv = new ContactVisit (
        array ('emp_id'
        => "1",
        'week_start' => "", // date required
        'company_name' => "test one",
        'contact_name' => "Big One",
        'city' => "Columbus",
        'state' => "OH",
        'accomplishments' => "phone call",
        'followup' => "",
        'literature_request' => ""));
    $this->assertEquals(false, $cv->isValid(), "invalid visit");
}
```

由于每次拜访都需要唯一的序列值，因此它们不妨自行确定顺序：

```
function testSequence() {
    $cv1 = new ContactVisit(array());
    $this->assertEquals(1, $cv1->seq);
    $cv2 = new ContactVisit(array());
    $this->assertEquals(2, $cv2->seq);
}
```

请注意，通过创建 ContactVisit，每个新 ContactVisit 的序列（seq）会自动递增，从而无需要求容器为每个实例分配唯一的序列号。

持久化仍在变动之中，但这肯定可行：

```
function testPersistence() {
    $this->session->getDatabaseHandle()->query("delete FROM
        contact_visits WHERE emp_id = 1 and week_start = '1980-01-01'");
    // remove multiples
    $cv = new ContactVisit (
        array ('emp_id' => "1",
        'week_start' => "1980-01-01",
        'seq' => 1,
        'company_name' => "test one",
        'contact_name' => "Big One",
        'city' => "Columbus",
        'state' => "OH",
        'accomplishments' => "phone call",
        'followup' => "",
        'literature_request' => ""));
    $result = $this->session->getDatabaseHandle()->query("select * FROM
        contact_visits WHERE emp_id = 1 and week_start = '1980-01-01'");
    $this->assertEquals(0, $result->numRows());
}
```




```php
$cv->persist();
$result = $this->session->getDatabaseHandle()->query("select * FROM
contact_visits WHERE emp_id = 1 and week_start = '1980-01-01'");
$this->assertEquals(1, $result->numRows());
}
```

请注意，week_start 的值选为 1980 年元旦是有原因的：

- 它不是正常周的开始，对美国人来说，正常周通常从星期日开始。
- 它在你心中格外突出，因此如果出了严重问题并且它进入了生产数据库，可以轻易地被识别为非真实联系人。

在运行测试之前，别忘了为 ContactVisit 打桩，以确保测试在正确满足测试之前能够成功 FAIL（但在语法上能执行）。以下是 contact.php 的内容：

```
class ContactVisit {
function __construct ($results) {
public function isValid() { return null; }
public function persist() { }
public function getSequence() { return null; }
}
```

## 满足测试

由于访问将按顺序进行，请使用静态变量，以便序列计数在类的所有实例之间共享。在构造函数中递增它还可确保无需更多管道代码即可覆盖所有情况。在 contact.php 中实现 ContactVisit 的构造函数：

```
class ContactVisit {
function __construct ($results, $dbh = null) {
static $sequence = 0;
$this->dbh = $dbh;
$this->contentBase = $results; // copy
$sequence = $sequence + 1; // increment across class
$this->contentBase["seq"] = $sequence;
}
```

```
public function isValid() { return null; }
public function persist() { }
public function getSequence() { return null; }
}
```

此外，请注意 ContactVisit 必须存储对数据库的引用。这是正常数据（公司名称、城市、州等）之外的内容，因此在 ContactVisit 的 `__get()` 函数的最后一个 return 中返回 ContactVisit 的状态。以下是 contact.php 中的内容：

```
function __get ($key) {
  if (array_key_exists ($key, $this->contentBase)) {
    return $this->contentBase[$key];
  }
  return $this->$key;
}
```

将所有内容整合在一起，添加一些生成所需 SQL 的函数，就大功告成了。contact.php 文件如下：

```
class ContactVisit {
  protected $contentBase = array();
  protected $dbh = null; // database handle

  function __get ($key) {
    if (array_key_exists ($key, $this->contentBase)) {
      return $this->contentBase[$key];
    }
    return $this->$key;
  }

  function __construct ($results, $dbh = null) {
    static $sequence = 0;
    $this->dbh = $dbh;
    $this->contentBase = $results; // copy
    $sequence = $sequence + 1; // increment across class
    $this->contentBase["seq"] = $sequence;
  }

  private function isEmpty($key) {
    if (array_key_exists($key, $this->contentBase) == false) return true;
    if ($this->contentBase[$key] == null) return true;
    if ($this->contentBase[$key] == "") return true;
    return false;
  }

  public function isValid() {
    if ($this->isEmpty("emp_id") == true) return false;
    if ($this->isEmpty("week_start") == true) return false;
    if ($this->isEmpty("company_name") == true) return false;
    return true;
  }

  private function implodeQuoted(&$values, $delimiter) {
    $sql = "";
    $flagIsFirst = true;
    foreach ($values as $value) {
      if ($flagIsFirst) {
        $flagIsFirst = false;
      } else {
        $sql .= $delimiter;
      }
      if (gettype($value) == "string") {
        $sql .= "'".$value."'";
      } else {
        $sql .= $value;
      }
    }
    return $sql;
  }

  private function generateSqlInsert($tableName, &$metas, &$values) {
    return "insert into " . $tableName .
    " (" . implode($metas, ", ") . ") " .
    " values ( " . $this->implodeQuoted($values, ", ") . ")";
  }

  public function persist() {
    if ($this->isValid() == false) return false;
    $sql = $this->generateSqlInsert("contact_visits",
    array("emp_id",
    "week_start",
    "seq",
    "company_name",
    "contact_name",
    "city",
    "state",
    "accomplishments",
    "followup",
    "literature_request"),
    array($this->emp_id,
    $this->week_start,
    $this->seq,
    $this->company_name,
    $this->contact_name,
    $this->city,
    $this->state,
    $this->accomplishments,
    $this->followup,
    $this->literature_request));
    if (DB::isError($this->dbh->query($sql))) return false;
    return true;
  }
}
```

简言之，已实现的方法如下：

- isValid() 满足你的两个有效性测试。isValid() 依赖于 isEmpty()，这只是一个方便函数。
- persist() 满足你的持久性测试。persist() 调用 generateSqlInsert()，后者根据表名、表元信息以及你想要插入的值生成 SQL INSERT 语句。generateSqlInsert() 又调用 implodeQuoted()，为字符串值添加 SQL 引号。

implodeQuoted() 和 generateSqlInsert() 均坚持数组按引用传递，而非按值传递。当然，PHP 6 的默认行为是按引用传递对象，但数组在默认情况下按值传递。

## 创建屏幕

请考虑以下名为 customer-contacts.tpl 的表单：

```
{include file="header.tpl" title="Widget World - Customer Contact"}
<h3>Customer Contact Report</h3>
<form action="customer-contacts.php" method="post">
<table border="0" width="100%">
<tr>
<td><b>Employee Name:</b></td><td>{$user->first_name} {$user->last_name}</td>
<td><b>Department:</b></td><td>{$user->department}</td>
</tr>
<tr>
<td><b>Number:</b></td><td>{$user->id}</td><td><b>Start Week:</b></td>
<td><SELECT NAME="week_start">
{html_options values=$start_weeks output=$start_weeks selected=$current_start_week}
</SELECT>
</td>
</tr>
</table>
<br><br>
<hr>
<p><font size="+1">
<b>Significant Distributors and Customers Visited:</b>
</font>
<br>
(also distributors/OEM/prospects)<p>
<table border="0">
{section name=idx loop=$max_weekly_contacts} {strip}
<tr>
<td width="20"></td>
<td><b>Company:</b></td>
<td><b>Contact:</b></td>
<td><b>City:</b></td>
<td><b>State:</b></td>
<td><b>FollowUp:</b></td>
<td><b>Literature Request:</b></td>
</tr>
<tr>
<td width="20"></td>
<td><input name="company_name_{$smarty.section.idx.index}"
size="20" maxlength="50"></td>
<td><input name="contact_name_{$smarty.section.idx.index}"
size="20" maxlength="50"></td>
<td><input name="city_{$smarty.section.idx.index}"
size="20" maxlength="50"></td>
<td><input name="state_{$smarty.section.idx.index}"
size="10" maxlength="50"></td>
<td><input name="followup_{$smarty.section.idx.index}"
size="20" maxlength="2000"></td>
<td><input name="literature_request_{$smarty.section.idx.index}"
size="20" maxlength="2000"></td>
</tr>
<tr>
<td width="20"></td>
<td colspan="7"><b>Accomplishments:</b></td>
</tr>
<tr>
<td width="20"></td>
<td colspan="7">
<TEXTAREA NAME="accomplishments_{$smarty.section.idx.index}"
ROWS=4 COLS=95></TEXTAREA><br><br>
</td>
</tr>
</table>
{/strip}{/section}
<table>
<br><hr>
<input type="hidden" name="action" value="persist_contact">
<br><br>
<center>
<input type="submit" name="submit" value=" Save " 
onclick="return checkInputs(this.form);">
</center>
</form>
{include file="footer.tpl"}
```

请注意，主循环 {section name=idx loop=$max_weekly_contacts} 会迭代并创建唯一的输入名称：company_name_{$smarty.section.idx.index}，然后对这些名称进行操作。

Smarty 提供了一个便捷的功能，可根据当前周的日期数组填充下拉框：

```
<SELECT NAME="week_start">
{html_options values=$start_weeks
output=$start_weeks selected=$current_start_week}
</SELECT>
```

你可能已经注意到，输入屏幕外观相当简陋，因为它使用的是常规 HTML，而不是像 XHTML 和 CSS 这样更严格、跨平台浏览器兼容性更好的东西。这是因为，在这个过程中，你更关心让系统运行起来而不是外观，因为定义在不久的将来可能会略有更改。在过程的后期，可以对显示进行美化。

## 喂养野兽

尽管 ContactVisits 知道如何持久化自身，但收集几周的下拉框信息，然后将所有联系人保存到数据库中，需要出人意料的大量工作。所需功能简单地放置在 customer-contacts.php 的函数中：

```
<?php
require_once ("Smarty.class.php") ;
require_once ("widgetsession.php") ;
$session = new WidgetSession(array ('phptype' => "pgsql",
'hostspec' => "localhost",
```





```php
'database' => "widgetworld",
'username' => "uwuser",
'password' => "foobar")));
$session->Impress();
$smarty = new Smarty;
$GLOBALS["max-weekly-contacts"] = 5;
function getStartDateOffset ($i) {
if ($i < 0) $i = 5;
$dates = array("Sunday" => 0, "Monday" => -1, "Tuesday" => -2,
"Wednesday" => -3, "Thursday" => -4, "Friday" => -5,
"Saturday" => -6);
return date("Y-m-d", mktime (0,0,0,date("m"),
date("d")+$dates[date("l")]-(($i-5)*7),date("Y"));
}
function getCurrentStartWeek () {
if (strlen($_REQUEST["week_start"]) >= 8) return $_REQUEST["week_start"];
return getStartDateOffset(-1); // this sunday
}
function getStartWeeks () {
$todayArray = array();
for ($i=20; $i > 0; $i--) {
array_push($todayArray, getStartDateOffset($i));
}
return ($todayArray);
}
function persistContactVisits (&$dbh, $emp_id) {
$dbh->query("delete from contact_visits where emp_id
= ".$emp_id." and week_start = '".getCurrentStartWeek()."'");
$seq = 0;
for ($i = 0; $i < $GLOBALS["max-weekly-contacts"]; $i++) {
$cv = new ContactVisit (
array ("emp_id" => $emp_id,
"week_start" => getCurrentStartWeek(),
"company_name" => $_REQUEST["company_name.".$i],
"contact_name" => $_REQUEST["contact_name.".$i],
"city" => $_REQUEST["city_".$i],
"state" => $_REQUEST["state_".$i],
"accomplishments" => $_REQUEST["accomplishments_".$i],
"followup" => $_REQUEST["followup_".$i],
"literature_request" => $_REQUEST["literature_request_".$i]),
$dbh);
$cv->persist();
}
}
$user = $session->getUserObject();
// display
if ($_REQUEST["action"] != "persist_contact") {
    $smarty->assign_by_ref ("user", $user);
    $smarty->assign('start_weeks', getStartWeeks());
    $smarty->assign('current_start_week', getCurrentStartWeek());
    $smarty->assign("max_weekly_contacts", $GLOBALS["max-weekly-contacts"]);
    $smarty->display('customer-contacts.tpl');
    exit();
}
// persist contact visits
require_once ("contact.php");
persistContactVisits ($session->getDatabaseHandle(), $user->id);
$smarty->display('thankyou.tpl');
?>
```

此功能的有趣之处始于 getStartDateOffset()，它根据传入的整数偏移量返回开始周的日期，从而填充日期下拉列表：

```php
function getStartDateOffset ($i) {
    if ($i < 0) $i = 5;
    $dates = array("Sunday" => 0, "Monday" => -1, "Tuesday" => -2,
    "Wednesday" => -3, "Thursday" => -4, "Friday" => -5,
    "Saturday" => -6);
    return date("Y-m-d", mktime (0, 0, 0, date("m"),
    date("d")+$dates[date("l")]-(($i-5)*7), date("Y"));
}
```

它的工作原理是将星期几（例如星期二）与使用 date("l") 检索并访问 $dates 数组相关联，该数组返回一个整数，表示距离目标日期星期日的天数。当你知道最近的星期日的日期时，通过将最近的星期日日期乘以 7，然后将这些天数加到当前星期日来计算星期日 + 周偏移量。因此，无论当前是星期几，都会返回星期日 +/- $i 周。

但是，因为 getStartWeeks() 通过从 20 计数到 0 返回一个包含 20 个星期日的数组，getStartDateOffset() 还会自动向默认值添加 5 周。因此，Week 的下拉列表框中有 15 个过去的周、当前的星期日和未来的 4 周。

主要工作由 persistContactVisits() 完成，它删除旧联系人，创建新的 ContactVisit，并对每个联系人调用 persist() 以将结果保存到数据库中。

图 19-6 展示了功能的实际运行情况。

![](img/a1b732997d9cb194dceec0570dc79710_479_0.png)

图 19-6: 客户联系报表中的下拉列表

现在，已经完成了两个故事，你可以在去使用应用程序接 Wendy、Wade、Edwina 和 Harold 之前，享受一个甜蜜的 10 分钟休息。你需要休息。

## 重新估算

好消息是 Wendy、Wade、Harold 和 Edwina 喜欢这个应用程序；但他们也只是凡人，并提出了一些非常合理的要求：

- 包含一个注销按钮。
- 先登录后才允许访问 `customer-contacts.php`。
- 更改周应调出之前保存的周。
- 在客户联系屏幕中，还要按 *每周* 基础跟踪以下内容：商店来电数量、工程师来电数量、经销商来电数量、里程大概、工作区域和区域评论。
- 联系人数量可能会偶尔变化。可以配置吗？

粗略估计一下，你认为新任务如下：

- 包含一个注销按钮：1/2 点
- 先登录后才允许访问 `customer-contacts.php`：（bug）1/2 点
- [ ] 更改周应调出之前保存的周：1 点
- [ ] 在客户联系屏幕中，还要按每周基础跟踪商店来电数量、工程师来电数量、经销商来电数量、里程大概、工作区域和区域评论：1 点
- [ ] 配置联系人数量（可能会偶尔变化）：1/2 点

原计划如下：

- [ ] 故事 9：身份验证和授权，4 点（已完成）
- [ ] 故事 1：客户联系报表，3 点（大部分已完成）
- [ ] 故事 6：销售经理通知，3 点
- [ ] 故事 8：邮件室通知，2 点

考虑到半点不太算数，但新任务算数，你与客户讨论后确定他们希望按以下顺序排列：

- [ ] 故事 9：身份验证和授权，4 点（已完成）
- [ ] 故事 1：客户联系报表，3 点（大部分已完成）
- [ ] 故事 14：更改周会调出之前的周：（新）
- [ ] 故事 15：客户联系报表中的每周项目：（新）

他们还希望在下一个迭代中先获得电子表格，再要求通知，因此目前可以放弃以下内容：

- [ ] 故事 6：销售经理通知，3 点
- [ ] 故事 8：邮件室通知，2 点

回到工作中。

## 清理

在开始新故事之前，先考虑一下当前代码库的状态。是的，有些部分有点丑陋，但功能完全正常。有些部分显然是从其他地方复制粘贴来的，但它能工作。不过，它确实包含一个很棒的测试套件。

不要因为一个经过充分测试、可正常工作的产品上有几个瑕疵而自责。这很常见，被称为代码债务。就像现实生活中一样，当你赶时间或情况所需时，你可以通过负债来超出财力消费。

既然你有时间清理一下，是时候还清债务了。这很容易，尽管最好在编码时遵循良好的开发准则，以便在不负债的前提下尽可能高效。

这指的是什么？看看你当前的工作文件：

```
index.php
customer-contacts.php
contact.php
test.contact.php
widgetsession.php
test.widgetsession.php
templates/customer-contacts.tpl
templates/footer.tpl
templates/header.tpl
templates/login.tpl
templates/main.tpl
templates/thankyou.tpl
```

现在问自己：所有这些文件都需要放在根目录吗？如果只保留客户端“入口点”呢？

按照这个思路，删除那些 PHP 模块（.php）文件和测试文件。这些肯定是普通 Web 浏览器不应该意外访问到的内容。将它们移动到以下层次结构中：

```
index.php
customer-contacts.php
lib/contact.php
lib/test.contact.php
lib/widgetsession.php
lib/test.widgetsession.php
templates/customer-contacts.tpl
templates/footer.tpl
templates/header.tpl
templates/login.tpl
templates/main.tpl
templates/thankyou.tpl
```

现在好多了，因为你的根目录中只有两个文件，而且这两个文件都会被 Web 浏览器访问。你也可以考虑将测试文件（test.*）移到另一个单独的目录中。但是，如果目录中只包含一两个文件，创建目录就不划算了；等你有至少四个测试文件要放进去时再做。

移动文件后，检查它们并确保更新你的 includes 和 requires，并确保测试继续运行。大扫除稍微少点乐趣，但之后你会有同样美好的感觉。

## 重构代码

开发代码时请记住一些基本任务：

- 保持简单。
- 不要创建你不会使用的东西。
- 删除重复（另一种说法是“一次且只有一次”）。
- 删除未使用的功能，包括类和函数。





最后一条尤其难以做到，因为编写代码很困难，那为什么要扔掉“好工作”呢？理由和你修剪植物一样：去除枯枝败叶能带来更健康的整体系统。

况且，你的代码在源代码仓库中，对吧？使用 CVS、Subversion、SourceSafe，或随手可得的任何工具，但把所有文件都放入你的源代码仓库。

在快速完成简单的半点任务（例如 Logout 按钮）时，请始终牢记编码规范，因为 footer.tpl 到处都在使用：

```html
<br><br>
<a href="index.php?action=logout">Logout</a><br>
<hr>
For Widget World use only - testing environment.
</body>
</html>
```

现在，在修改 index 之前，请查看 customer-contacts.php 和 index.php 顶部的复制粘贴内容。这两个文件都以如下内容开头：

```php
require_once ("Smarty.class.php"); require_once ("widgetsession.php");
$session = new WidgetSession(array ('phptype' => "pgsql",
'hostspec' => "localhost",
'database' => "widgetworld",
'username' => "wuser",
'password' => "foobar")));

$session->Impress();

$smarty = new Smarty;
```

它违反了“一次且仅一次”规则，所以将其删除——直接剪切并放入另一个文件。暂时放在 lib/common.php 中。

此外，你不应该在 Web 空间中存放登录名和密码，因此应将内容提取出来，放入另一个 PHP 可访问但位于 Web 根目录之外的文件中，这样 Apache 就不会将其提供给好奇或恶意的人。

请记住，由于我们处理的是设置（按请求），需要添加一个最大每周联系人数设置。所有这些都应放入一个名为 ../../../../settings.php 的新文件中，该文件不便地位于 Web 根目录之外，以防有人利用你自己的 Web 服务器读取配置文件，进而获取数据库访问权限：

```php
<?php
/**
* database setup
*/
$GLOBALS["db-type"] = "pgsql";
$GLOBALS["db-hostname"] = "localhost";
$GLOBALS["db-username"] = "wuser";
$GLOBALS["db-password"] = "foobar";
$GLOBALS["db-name"] = "widgetworld";
/*
 * 3rd party environment
 */
$GLOBALS["smarty-path"] = "/usr/lib/php/smarty/";
/*
 * system settings
 */
$GLOBALS["max-weekly-contacts"] = 5;
?>
```

## 第三部分：真实世界案例研究

你的 lib/common.php 文件应包含以下内容：

```php
<?php
require_once ("../../../../settings.php");
require_once ("./lib/widgetsession.php");
require_once ($GLOBALS["smarty-path"] . 'Smarty.class.php'); $smarty = new Smarty;
$session = new WidgetSession(array ('phptype' => $GLOBALS['db-type'],
                                     'hostspec' => $GLOBALS['db-hostname'],
                                     'database' => $GLOBALS['db-name'],
                                     'username' => $GLOBALS['db-username'],
                                     'password' => $GLOBALS['db-password']));
$session->Impress();
?>
```

趁此机会，你或许还应该要求除 index.php 以外的每个页面都登录，因为 index.php 目前是唯一使用登录功能的页面。将此内容追加到你的 common.php 中：

```php
/*
 * require login
*/
$scriptname = end(explode("/", $_SERVER["REQUEST_URI"]));
if ($scriptname <> "index.php") {
    if ($session->isLoggedIn() == false) {
        Header ("Location: index.php");
    }
}
```

现在将注意力转向 index.php，在添加处理登出的逻辑后，它看起来如下（是的，它处理所有情况）：

```php
<?php
require_once ("lib/common.php");
if (array_key_exists("action", $_REQUEST)) {
    switch ($_REQUEST["action"]) {
        case "login":
            $session->login($_REQUEST["login_name"], $_REQUEST["login_pass"]);
            if ($session->isLoggedIn()) {
                $smarty->assign_by_ref("user", $session->getUserObject());
                $smarty->display ("main.tpl");
                exit;
            } else {
                $smarty->assign('error', "Invalid login, try again.");
            }
            break;
        case "logout":
            $session->logout();
            $smarty->display ("login.tpl");
            exit;
            break;
        default:
            $smarty->display ("login.tpl");
            exit;
    }
} else {
    if ($session->isLoggedIn() == true) {
        $smarty->assign_by_ref("user", $session->getUserObject());
        $smarty->display ("main.tpl");
        exit;
    }
}
$smarty->display ("login.tpl");
?>
```

尝试登录时，你要么成功并转到 `main.tpl`，要么失败并返回 `login.tpl`。登出时，你希望登出并转到 `login.tpl`。如果没有分配任何操作，则使用 `$session->isLoggedIn()` 检查登录状态。最后，最后一行显示 `login.tpl`，尽管从逻辑上讲（目前）你的代码不可能执行到这一步。不过，未来可能会出现这种情况，因此将其作为“兜底”用法是明智的，以防你出现疏忽。

尽管前面的代码从技术上讲可以运行，但总觉得有点不对劲。代码需要确定显示哪个屏幕，但它既依赖登录状态，也依赖表示状态的请求变量。代码显得过于冗长，因此你应该花几分钟时间看看如何使其更易读——换句话说，是时候进行重构了。

重构是一个持续的过程，起初可能看起来是主观的，但你客观上仍会因此得到一个更整洁的代码库。有一种通过创建相似性来重构相似性的技术。起初这似乎有点奇怪，但如果你的代码看起来像是消除重复（也称为“_一次且仅一次_”重构）的候选者，那么这项技术可能值得研究。

检查代码，考虑如何与现有内容在逻辑上创建相似性。例如，以下代码仍然是完全合法的 PHP —— 它通过测试并在浏览器端继续正常工作：

```php
<?php
require_once ("lib/common.php");
if (array_key_exists("action", $_REQUEST)) {
    switch ($_REQUEST["action"]) {
        case "login":

        $session->login($_REQUEST["login_name"],$_REQUEST["login_pass"]);
        if ($session->isLoggedIn()) {
            $smarty->assign_by_ref("user", $session->getUserObject());
            $smarty->display ("main.tpl");
            exit;
        } else {
            if (array_key_exists("login_name", $_REQUEST)) {
                $smarty->assign('error', "Invalid login, try again.");
            }
            $smarty->display ("login.tpl");
            exit;
        }

        break;
        case "logout":
        $session->logout();
        if ($session->isLoggedIn()) {
            $smarty->assign_by_ref("user", $session->getUserObject());
            $smarty->display ("main.tpl");
            exit;
        } else {
            if (array_key_exists("login_name", $_REQUEST)) {
                $smarty->assign('error', "Invalid login, try again.");
            }
            $smarty->display ("login.tpl");
            exit;
        }
        break;
        default:
        if ($session->isLoggedIn()) {
            $smarty->assign_by_ref("user", $session->getUserObject());
            $smarty->display ("main.tpl");
            exit;
        } else {
            if (array_key_exists("login_name", $_REQUEST)) {
                $smarty->assign('error', "Invalid login, try again.");
            }
            $smarty->display ("login.tpl");
            exit;
        }
    }
} else {
    if ($session->isLoggedIn()) {
        $smarty->assign_by_ref("user", $session->getUserObject());
        $smarty->display ("main.tpl");
        exit;
    } else {
        if (array_key_exists("login_name", $_REQUEST)) {
            $smarty->assign('error', "Invalid login, try again.");
        }
    }
}

$smarty->display("login.tpl");
exit;
}
$smarty->display("login.tpl");
?>
```

你刚才所做的就是在当前逻辑结构中添加高亮的条件语句，从而有意创建相似性。这是复制粘贴编程最糟糕的做法，但出于充分的理由。

接下来，逐字复制相似内容并创建一个函数，传入所需的任何局部状态。这种特定的重构被称为“提取方法，”Martin Fowler 在 _重构_ (Addison-Wesley, 1999) 中有所描述：

```php
function displaySmartyPage (&$smarty, &$session, $PageToDisplay) {
    if ($session->isLoggedIn()) {
        $smarty->assign_by_ref("user", $session->getUserObject());
        $smarty->display ($PageToDisplay);
        exit;
    } else {
        if (array_key_exists("login_name", $_REQUEST)) {
            $smarty->assign('error', "Invalid login, try again.");
        }
        $smarty->display ("login.tpl");
        exit;
    }
}
```

有了新函数 displaySmartyPage() 可供使用，index.php 剩下的内容如下：

```php
if (array_key_exists("action", $_REQUEST)) {
    switch ($_REQUEST["action"]) {
    case "login":
        $session->login($_REQUEST["login_name"],$_REQUEST["login_pass"]);

        displaySmartyPage ($smarty, $session, "main.tpl");
        break;

    case "logout":
        $session->logout();

        displaySmartyPage ($smarty, $session, "main.tpl");
        break;

    default:
        displaySmartyPage ($smarty, $session, "main.tpl");
    }
} else {
    displaySmartyPage ($smarty, $session, "main.tpl");
}

displaySmartyPage ($smarty, $session, "main.tpl");
```




现在代码更清晰了，很明显你的逻辑可以重构如下：

```
if (array_key_exists("action", $_REQUEST)) {
    switch ($_REQUEST["action"]) {
        case "login":
            $session->login($_REQUEST["login_name"], $_REQUEST["login_pass"]);
            break;
        case "logout":
            $session->logout();
            break;
    }
}
displaySmartyPage($smarty, $session, "main.tpl");
```

因为displaySmartyPage()函数只被调用一次，你现在可能能明白为什么之前把代码重构到displaySmartyPage()函数中了。

既然displaySmartyPage()函数代码已不再必要，你要撤销之前的“提取方法”重构，改用“内联方法”技术（也见于Martin Fowler的《重构》）将其重构回去。这完全相反：

```
<?php
require_once ("lib/common.php");
if (array_key_exists("action", $_REQUEST)) {
    switch ($_REQUEST["action"]) {
        case "login":
            $session->login($_REQUEST["login_name"], $_REQUEST["login_pass"]);
            break;
        case "logout":
            $session->logout();
            break;
    }
}
if ($_session->isLoggedIn()) {
    $smarty->assign_by_ref("user", $_session->getUserObject());
}
$smarty->display ("main.tpl");
} else {
    if (array_key_exists("login_name", $_REQUEST)) {
        $smarty->assign('error', "Invalid login, try again.");
    }
    $smarty->display ("login.tpl");
}
?>
```

只需付出一点努力，你就显著降低了复杂度，移除了多余的Smarty调用，并将总行数减少了三分之一以上。

正如你所见，降低复杂度可以带来一些惊人的节省，代码也更易于阅读和理解。当然，你应当通过践行“一次且仅一次”规则来避免陷入代码债。如果有选择，保持解决方案简单，不要害怕移除不需要的功能。

## 完成迭代

牢记你新学到的重构技巧，处理剩下的用户故事时，着眼于消除重复并使代码更简单。

## 用户故事14：切换周时调用前一周

调用状态并不困难，因为ContactVisit状态几乎就是恳求这样做。你通过将以下函数添加到customer-contacts.php中，很快就完成了一半：

```
function gatherContactVisits ($dbh, $emp_id) {
	$result = $dbh->query ("select * from contact_visits where
		emp_id = ".$emp_id." and week_start = 
		'".getCurrentStartWeek()."' order by seq");
	if (DB::isError($result)) {
		return array();
	}
	$visits = array();
	while ($row =& $result->fetchRow()) {
		array_push ($visits, new ContactVisit($row));
	}
	return $visits;
}
```

在调用gatherContactVisits()函数时应该采取“懒加载”策略，因为从数据库调用ContactVisits()的操作并非每次都需要（例如，在保存ContactVisits()时）。

现在，按引用将联系访问数据分配给ContactVisits，并在customer-contacts.tpl中像这样为显示调用它：

```
<input name="company_name_${smarty.section.idx.index}" size="20"
	maxlength="50" value="${contactVisits[idx]->company_name}">
```

你已经准备好一切，除了当下拉菜单中的周发生变化时重新加载。这里有一个小技巧：下拉菜单通常不会触发表单提交，但在这种情况下你需要强制提交。

为了强制提交，你创建一个带有week_start值的隐藏表单。当日期发生变化时，调用JavaScript函数reload，它会将week_start填充为所选内容。然后，用一个新的action“提交”它：

```
{literal}
<SCRIPT TYPE="text/javascript">
<!--
function reload () {
	window.document.forms[0].week_start.value =
		window.document.forms[1].week_start.value // hidden form
	window.document.forms[0].submit(); // hidden form
}
// -->
</SCRIPT>
</literal>
```

### 客户联系报告

```
<form action="customer-contacts.php" method="post">
<input type="hidden" name="action" value="reload_contact">
<input type="hidden" name="week_start" value="">
</form>
```

```
<form action="customer-contacts.php" method="post">
<table border="0" width="100%">
<tr>
<td><b>Employee Name:</b></td><td>{$user->first_name} {$user->last_name}</td>
<td><b>Department:</b></td><td>{$user->department}</td>
</tr>
<tr>
<td><b>Number:</b></td><td>{$user->id}</td>
<td><b>Start Week:</b></td>
<td>
<SELECT NAME="week_start" onchange="reload()">
{html_options values=$start_weeks output=$start_weeks
selected=$current_start_week)
</SELECT>
</td>
</tr>
</table><br><hr>
```

## 用户故事15：客户联系报告中的每周项目

需要关注的要素包括店铺来电数、工程师来电数、分销商来电数、约束里程、工作区域和区域评论。所有这些都按周发生。

要意识到，你正在查看联系访问与新结构Contact之间的多对一关系：

```
CREATE TABLE contact (
  emp_id integer NOT NULL default '0',
  week_start date NOT NULL,
  shop_calls integer default NULL,
  distributor_calls integer default NULL,
  engineer_calls integer default NULL,
  mileage decimal(9,2) default NULL,
  territory_worked varchar(60) default NULL,
  territory_comments text
);
CREATE UNIQUE INDEX co_pk on contact (emp_id, week_start);
CREATE INDEX co_emp_id ON contact (emp_id);
CREATE INDEX co_week_start ON contact (week_start);
```

这不是问题，因为Contact的用法与ContactVisits大致相同。为联系持久性创建测试：

```
function testContactPersistence() {
    $this->session->getDatabaseHandle()->query("delete FROM contact WHERE
      emp_id = 1 and week_start = '1980-01-01'"); // remove multiples
    $c = new Contact (
    array ("emp_id" => "1",
    "week_start" => "1980-01-01",
    "shop_calls" => 2,
    "distributor_calls" => 3,
    "engineer_calls" => 4,
    "mileage" => 50,
    "territory_worked" => "Central Ohio",
    "territory_comments" => "Buckeyes are great. " ),
    $this->session->getDatabaseHandle());
    $result = $this->session->getDatabaseHandle()->query("select * FROM
      contact WHERE emp_id = 1 and week_start = '1980-01-01'");
    $this->assertEquals(0, $result->numRows());
    $c->persist();
    $result = $this->session->getDatabaseHandle()->query("select * FROM
      contact WHERE emp_id = 1 and week_start = '1980-01-01'");
    $this->assertEquals(1, $result->numRows()); }
```

Contact还与ContactVisits共享相同的作用域。这是一个重要提示，因为这两个类做的事情几乎一样并且共享相同的作用域。它们通常是轻松的重构目标。

更深入地查看这些类，你会发现你的直觉是正确的，即新的Contact类以及现有的ContactVisit和WidgetUser类包含共同功能。

正如你之前可能记得的，ContactVisit和WidgetUser的结构如下：

```
class ContactVisit {
    protected $contentBase = array();
    protected $dbh = null; // database handle
    function __get ($key) {}
    function __construct($results, $dbh = null) {}
    private function isEmpty($key) {}
    public function isValid() {}
    private function implodeQuoted() {}
    private function generateSQLInsert($tableName, &$metas, &$values) {}
    public function persist() {}
}

class WidgetUser {
    protected $contentBase = array();
    protected $dispatchFunctions = array ("role" => "getrole");
    function __construct($initdict) {}

    function __get ($key) {}

    function __set ($key, $value) {
    public function getRole() {}
    public function isSalesPerson() {}
    public function isSalesManager() {}
    public function isAccountant() {}
}
```

这是使用“提取类”（参见《重构》）重构来整合代码的绝佳用例。整合将大量持久性功能上移到一个名为PersistableObject的新类中：

```
class PersistableObject {
protected $contentBase = array();
protected $dbh = null; // database handle
protected $dispatchFunctions = array ("role" => "getrole");

function __get ($key) {
// dispatch by function first
if (array_key_exists ($key, $this->dispatchFunctions)) {
$funcname = $this->dispatchFunctions[$key];
return $this->$funcname();
}

// then state
if (array_key_exists ($key, $this->contentBase)) {
return $this->contentBase[$key];
}

// then self
return $this->$key;
}

function __construct ($results, $dbh = null) {
$this->dbh = $dbh;
if ($results <> null) {
$this->contentBase = $results; // copy
}
}

public function implodeQuoted (&$values, $delimiter) {
$sql = "";
$flagIsFirst = true;
foreach ($values as $value) {
if ($flagIsFirst) {
$flagIsFirst = false;
} else {
$sql .= $delimiter;
}
if (gettype ($value) == "string") {
$sql .= "'".$value."'";
} else {
$sql .= $value;
}
}
}
```




}
return $sql;
}

public function generateSqlInsert ($tableName, &$metas, &$values) {
    return " insert into ".$tableName.
    " ( ".implode ($metas, ", ")." ) ".
    " values ( ".$this->implodeQuoted ($values, ", ")." ) ";
}

public function generateSqlUpdate ($tableName, &$metas, &$values) {
    $sql = " update ".$tableName." set ";
    for ($i=0; $i<count($metas); $i++) {
        $sql .= $metas[$i]." = ".$values[$i].", ";
    }
    return $sql;
}

public function generateSqlDelete ($tableName) {
    return " delete from ".$tableName." where ".$this->getSqlWhere();
}
```

```
```
// note: should be implemented by concrete classes
public function getSqlWhere() {
    return "";
}
```

```
public function isValid() {
    return true;
}

public function persistWork ($tablename, $meta) {
    if ($this->isValid() == false) return false;
    $values = array();
    foreach ($meta as $mvalue) {
        array_push ($values, $this->$mvalue);
    }
```

```
if (strlen($this->getSqlWhere()) > 0) {
    $sql = $this->generateSqlDelete ($tablename);
    $this->dbh->query($sql);
}
```

```
$sql = $this->generateSqlInsert ($tablename, $meta, $values);
if (DB::isError ($this->dbh->query($sql))) return false;
return true;
} }
```

你可能已经注意到，添加 generateSqlUpdate 和 generateSqlDelete 使得 PersistableObject 能够分别在数据库中更新和删除自身。当然，这两个函数都需要 SQL WHERE 子句，以确保不会更新或删除表中的每条记录。这就是为什么子类（如 ContactVisit）有责任定义它们的独特之处；它们通过实现 getSqlWhere 函数来做到这一点。

## 第三部分：真实世界案例研究

将持久化函数（implodeQuoted、generateSqlInsert、isValid、persistWork）和持久化状态（contentBase、dispatchFunctions）移至 PersistableObject，使得 Contact、ContactVisit 和 WidgetUser 能够以更简洁的形式实现：

```
class Contact extends PersistableObject {
    function __construct ($results, $dbh = null) {
        parent::__construct ($results, $dbh);
    }

    public function persist() {
        return $this->persistWork ("contact",
            array ( "emp_id",
                "week_start",
                "shop_calls",
                "distributor_calls",
                "engineer_calls",
                "mileage",
                "territory_worked",
                "territory_comments")) ;
    }

    public function getSqlWhere() {
        return " emp_id = ".$this->emp_id." and
            week_start = ".$this->week_start."";
    }
}
```

```
class ContactVisit extends PersistableObject {

    function __construct ($results, $dbh = null) {
        parent::__construct ($results, $dbh);
        static $sequence = 0;
        $sequence = $sequence + 1; // increment across class
        $this->contentBase["seq"] = $sequence;
    }

    private function isEmpty($key) {
        if (array_key_exists($key, $this->contentBase) == false) return true;
        if ($this->contentBase[$key] == null) return true;
        if ($this->contentBase[$key] == "") return true;
        return false;
    }

    public function isValid() {
        if ($this->isEmpty("emp_id") == true) return false;
        if ($this->isEmpty("week_start") == true) return false;
        if ($this->isEmpty("company_name") == true) return false;
        return true;
    }

    public function persist() {
        return $this->persistWork ("contact_visits",
            array ( "emp_id",
                "week_start",
                "seq",
                "company_name",
                "contact_name",
                "city",
                "state",
                "accomplishments",
                "followup",
                "literature_request" ));
    }
}
```

```
class WidgetUser extends PersistableObject {
function __construct($initdict) {
parent::__construct($initdict);
$this->dispatchFunctions = array ("role" => "getrole");
$this->contentBase = $initdict; // copy
}
public function getRole() {
switch ($this->contentBase["role"]) {
case "s": return ("Sales Person");
case "m": return ("Sales Manager");
case "a": return ("Accountant");
default: return ("");
}
}
public function isSalesPerson() {
if ($this->contentBase["role"] == "s") return true;
return false;
}
public function isSalesManager() {
if ($this->contentBase["role"] == "m") return true;
return false;
}
public function isAccountant() {
if ($this->contentBase["role"] == "a") return true;
return false;
}
}
```

哎呀，拥有所有那些单元测试来指示出错时，真是太好了。你将面临的一个障碍是决定目标类如何使用以及它们之间有何不同。例如，Contact 和 ContactVisit 存在微妙的差别：你只持久化有效的 ContactVisit，但总是存在一个可能为空（但仍已实例化）的 Contact。

此外，请注意 Contact 实现了 getSqlWhere 函数，以便它可以被删除和更新。但是，请记住 ContactVisit 在插入操作之前被删除，而 WidgetUser 仅被持久化到数据库，因此不需要实现 getSqlWhere 函数。

然而，Contact 和 ContactVisits 之间的差异与类本身关系不大，更多与它们所处的业务规则和环境有关。因此，尽管你的类开始整合和共享代码，但各自的单元测试仍应继续测试各个类的多样性。

现在 customer-contacts.tpl 需要一个新部分来显示新的 Contact 信息：

```
<table border="0">
<tr>
<td>Number of Shop Calls:</td>
<td><input name="shop_calls" size="7" maxlength="17"
value="<?=$contact->shop_calls?>"></td>
<td width="20"></td>
<td>Number of Engineer Calls:</td>
<td><input name="engineer_calls" size="7" maxlength="17"
value="<?=$contact->engineer_calls?>">
</td>
</tr>
<tr>
<td>Number of Distributor Calls:</td>
<td><input name="distributor_calls" size="7" maxlength="17"
value="<?=$contact->distributor_calls?>"></td>
<td width="20"></td>
<td>Approximate Mileage:</td>
<td><input name="mileage" size="7" maxlength="17"
value="<?=$contact->mileage?>"></td>
</tr>
<tr>
<td>Territory Worked:</td>
<td colspan="2"><input name="territory_worked"
value="<?=$contact->territory_worked?>"></td>
</tr>
<tr>
<td colspan="7">
Territory Comments:<br>
<TEXTAREA NAME="territory_comments" ROWS=4 COLS=95>
<?=$contact->territory_comments?>
</TEXTAREA>
</td>
</tr>
</table>
```

将这些新的支持函数添加到 customer-contacts.php 中，以读取和保存 Contact 信息：

```
function persistContact (&$dbh, $emp_id) {
    $c = new Contact (
    array ("emp_id" => $emp_id,
    "week_start" => getCurrentStartWeek(),
    "shop_calls" => $_REQUEST["shop_calls"],
    "distributor_calls" => $_REQUEST["distributor_calls"],
    "engineer_calls" => $_REQUEST["engineer_calls"],
    "mileage" => $_REQUEST["mileage"],
    "territory_worked" => $_REQUEST["territory_worked"],
    "territory_comments" => $_REQUEST["territory_comments"]),
    $dbh);
    $c->persist();
}
function gatherContact (&$dbh, $emp_id) {
    $result = $dbh->query ("select * from contact where
       emp_id = ".$emp_id." and week_start =
       ".getCurrentStartWeek()."");
    if (DB::isError($result)) return array();
    return new Contact ($result->fetchRow());
}
$user = $session->getUserObject();
// display
if ($_REQUEST["action"] != "persist_contact") {
   $smarty->assign_by_ref ("user", $user);
   $smarty->assign_by_ref ("contact", gatherContact (
      $session->getDatabaseHandle(), $user->id));
   $smarty->assign_by_ref ("contactVisits", gatherContactVisits (
      $session->getDatabaseHandle(), $user->id));
   $smarty->assign('start_weeks', getStartWeeks());
   $smarty->assign('current_start_week', getCurrentStartWeek());
   $smarty->assign('max_weekly_contacts', GLOBALS['max-weekly-contacts']);
   $smarty->display('customer-contacts.tpl');
   exit;
}
// persist contact visits
require_once ("lib/contact.php");
persistContact ($session->getDatabaseHandle(), $user->id);
persistContactVisits ($session->getDatabaseHandle(), $user->id);
```

图 19-7 显示了你辛勤工作的成果。

![](img/a1b732997d9cb194dceec0570dc79710_496_0.png)

图 19-7：向客户联系报告添加每周项目 t



上一个故事完成的速度表明，如果你通过不制造代码债来保持代码库的整洁，你的前进势头不一定会付诸东流。

努力进行重构，这在一定意义上永远不会完成。有些部分仍然可以以批判性的眼光审视，尤其是那些与 `Contact` 和 `ContactVisits` 的支持函数非常相似的部分。支持函数的存在本身（而非让对象自己处理一切）表明，通过使用共享作用域，往往可以实现更大程度的整合。

尽管如此，这仍然可能朝着不同的方向发展，你必须记住，要使某次特定的重构成功，结果代码应该更易于阅读和理解。如果你发现自己花更多时间编写过多的支持代码或框架，那就把它当作一个信号，也许应该暂停一下。虽然有时需要大规模重构，但它们绝对应该是例外。

## 差旅费用报告

你当前的杰出路线图如下：

- [ ] 差旅费用报告
  - [ ] Story 2: 差旅费用报告, 7 点
  - [ ] Story 3: 费用报告评论, 2 点
  - [ ] Story 10: 持久化费用报告预付款, 2 点
  - [ ] Story 4: 费用报告电子表格, 4 点
- [ ] 差旅费用服务
  - [ ] Story 5: 会计通知, 3 点
  - [ ] Story 7: 销售人员通知, 1 点
  - [ ] Story 13: 费用报告导出, 3 点
- [ ] 未完成的故事
  - [ ] Story 6: 销售经理通知, 3 点
  - [ ] Story 8: 邮件室通知, 2 点

仅凭其点数之多，差旅费用报告就不会是一场速胜。

如前面图 19-2 所示，差旅费用报告在细节方面相当精简。是时候开始着手工作了。通过与 Wendy 和 Edwina 的交谈，你了解到，他们真正想要的是更像图 19-8 这样的东西。

| 员工姓名: | XXXXXXXXXXXXXXXXX | | 部门: | XXXXXXXX | | | | |
|---|---|---|---|---|---|---|---|---|
| 编号: | X | | 开始周: | YYYY-MM-DD (下拉) | | | | |
| 工作区域: | XXXXXXXXXXXXXXXXX | | | | | | | |
| | 周日 | 周一 | 周二 | 周三 | 周四 | 周五 | 周六 | 合计 |
| 住宿 | | | | | | | | |
| 住宿和酒店 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 其他 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 小费 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 住宿总计 | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 21 |
| 餐饮 | | | | | | | | |
| 早餐 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 午餐和零食 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 晚餐 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 小费 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 娱乐 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 餐饮总计 | 6 | 6 | 6 | 6 | 6 | 6 | 6 | 42 |
| 交通 | | | | | | | | |
| 机票 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 汽车租赁 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 自驾里程（固定） | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 过路费/停车费 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 交通小计 | 4 | 4 | 4 | 4 | 4 | 4 | 4 | 20 |
| 非里程行驶 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 里程（每英里 XXX） | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 交通总计 | 6 | 6 | 6 | 6 | 6 | 6 | 6 | 42 |
| 杂项 | | | | | | | | |
| 礼品 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 电话和传真 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 维修 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 邮资 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 其他 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 7 |
| 杂项总计 | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 35 |
| | | | | | | | | |
| 评论: | XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | | 小计 | | 147 | | | |
| XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | | | 减预付现金 | | 47 | | | |
| XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | | | 应付员工 | | 100 | | | |
| XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | | | 应付公司 | | | | | |

### 图 19-8: 所需的差旅费用报告

尽管对类别（住宿、餐饮等）进行排序和修改花费了大半天时间，但你现在拥有的已非常接近原始 Widget World 传真表单的外观。当然，既然你的客户意识到事物可能会发生变化，他们很可能会——因为尽管一定程度的灵活性和未知因素困扰着几乎每个项目，但你将随遇而安，不会为每个冒出来的“以防万一”功能过度设计。

还有一点：“里程（每英里 XXX）”标题中的 XXX 是基于联邦税法的美元金额。幸运的是，它是一个常量，因此你不需要为每个州/省追踪它，而且只需处理一个国家。然而，该费率通常每年都会变化，因此你需要在提交时记录该金额。

至关重要的预付现金也需要包含在计算中；如果预付款足够，它可能会溢出为欠公司的款项，由“应付员工”及其布尔对应项“应付公司”表示。

暂且不考虑复杂性，先从简单的部分入手。该表格的核心是与日期和描述符关联的美元金额。

随手一写得出以下数据项：

```
CREATE TABLE travel_expense_item (
 emp_id integer NOT NULL,
 expense_date date NOT NULL,
 description varchar(40) NOT NULL,
 amount decimal(9,2) NOT NULL
);
```

## 第三部分：真实世界案例研究

添加需要捕获的每周信息：

```
CREATE TABLE travel_expense_week (
    emp_id        integer NOT NULL,
    week_start    date    NOT NULL,
    comments      text,
    territory_worked  varchar(60),
    cash_advance      decimal(9,2),
    mileage_rate   decimal(3,2) NOT NULL
);
```

从技术角度来看，你仍然需要为数据库添加默认值、索引等；在业务方面，请注意你正在跟踪 cash_advance 和 mileage_rate。由于每周提交每笔差旅费用，表单的每周小计部分可以轻松计算，因此无需存储小计。

## 差旅费用项目

让我们着手编写测试。简单情况只是验证最少所需信息，如下所示：

```
function testValidTravelExpenseItem() {
    $tvi = new TravelExpenseItem (
        array ('emp_id' => "1",
            'expense_date' => "1980-01-01",
            'description' => "one",
            'amount' => "1.0" ));
    $this->assertEquals(true, $tvi->isValid(), "valid expense");
}
function testInvalidTravelExpenseItem() {
    $tvi = new TravelExpenseItem (
        array ('emp_id' => "1",
        'expense_date' => "", // date required
            'description' => "one",
            'amount' => "1.0" ));
    $this->assertEquals(false, $tvi->isValid(), "valid expense");
}
```

它还需要做什么？如果给定一个数组，它可以自行填充，因此差旅费用项目需要相应地持久化自身。为差旅费用项目添加另一个测试：

```
function testTravelExpenseItemPersistence() {
    $this->session->getDatabaseHandle()->query("delete FROM
        travel_expense_item WHERE emp_id = 1 and expense_date
        = '1980-01-01'"); // remove multiples
    $tvi = new TravelExpenseItem (
        array ('emp_id' => "1",
            'expense_date' => "1980-01-01",
            'description' => "one",
            'amount' => "1.0" ));
    $result = $this->session->getDatabaseHandle()->query("select * FROM
        travel_expense_item WHERE emp_id = 1 and
        expense_date = '1980-01-01'");
    $this->assertEquals(0, $result->numRows());
    $tvi->persist();
    $result = $this->session->getDatabaseHandle()->query("select * FROM
    travel_expense_item WHERE emp_id = 1 and
    expense_date = '1980-01-01'");
    $this->assertEquals(1, $result->numRows());
}
```

运行这些测试时，请记住连接到测试数据库。你最不希望的就是用一条错误的 DELETE 语句意外地清除生产数据。

在新文件 lib/expense.php 中为差旅费用项目打桩：

```
class TravelExpenseItem {
public function isValid() { }
public function persist() { }
}
```

确保测试运行（并失败），然后着手使其通过。

以 ContactVisit 为模板，这出乎意料地简单：

```
class TravelExpenseItem extends PersistableObject {
function __construct($results, $dbh = null) {
parent::__construct($results, $dbh);
}
}
```

```
private function isEmpty($key) {
if (array_key_exists($key, $this->contentBase) == false) return true;
if ($this->contentBase[$key] == null) return true;
if ($this->contentBase[$key] == "") return true;
return false;
}
```

```
public function isValid() {
if ($this->isEmpty("emp_id") == true) return false;
if ($this->isEmpty("expense_date") == true) return false;
if ($this->isEmpty("description") == true) return false;
if ($this->isEmpty("amount") == true) return false;
return true;
}
public function persist() {
return $this->persistWork (
"travel_expense_item",
array ( "emp_id",
"expense_date",
"description",
"amount" ));
}
public function getSqlWhere() {
return " emp_id = ".$this->emp_id." and expense_date = '".$this->expense_date."' and description = '".$this->description."'";
}
}
```





回顾 ContactVisit 的定义：

```php
class ContactVisit extends PersistableObject {
    function __construct ($results, $dbh = null) {}
    private function isEmpty($key) {}
    public function isValid() {}
    public function persist() {}
}
```

当然，isEmpty() 函数现在在两个共享共同父类的类之间是冗余的。这对你意味着什么？它在尖叫着“把 IsEmpty() 移动到 PersistableObject 中！”不要忘记将 isEmpty() 设为 protected；否则，子类将无法调用它。

完成此操作后，确保 ContactVisit 测试继续通过。相关类现在应如下所示：

```php
class PersistableObject {
    protected $contentBase = array();
    protected $dbh = null; // database handle
    protected $dispatchFunctions = array("role" => "getrole");
    function __get ($key) {}
    function __construct ($results, $dbh = null) {}
    public function implodeQuoted (&$values, $delimiter) {}
    public function generateSqlInsert ($tableName, &$metas, &$values) {}
    public function generateSqlUpdate ($tableName, &$metas, &$values) {}
    public function generateSqlDelete ($tableName) {}
    public function getSqlWhere() {}
    public function isValid() {}
    protected function isEmpty($key) {}
    public function persistWork ($tablename, $meta) {} }
class ContactVisit extends PersistableObject {
    function __construct ($results, $dbh = null) {}
    public function isValid() {}
    public function persist() {}
}
class TravelExpenseItem extends PersistableObject {
    function __construct ($results, $dbh = null) {}
    public function isValid() {}
    public function persist() {}
    public function getSqlWhere() {}
}
```

在接手差旅费周类之前，先去吃块饼干吧。

## 差旅费周

到现在，你可以轻松搞定差旅费周的简单测试用例。将这些附加方法保存到 test.widgetsession.php：

```php
function testValidTravelExpenseWeek() {
    $tvi = new TravelExpenseWeek (
        array ('emp_id' => "1",
        'week_start' => "1980-01-01",
        'comments' => "comment",
        'mileage_rate' => "0.31",
        'territory_worked' => "Midwest" ));
    $this->assertEquals(true, $tvi->isValid(), "valid expense");
}
function testInvalidTravelExpenseWeek() {
    $tvi = new TravelExpenseWeek (
    array ('emp_id' => "1",
        'week_start' => "", // date required
        'comments' => "comment",
        'mileage_rate' => "0.31",
        'territory_worked' => "Midwest" ));
    $this->assertEquals(false, $tvi->isValid(), "valid expense");
}
function testTravelExpenseWeekPersistence() {
    $this->session->getDatabaseHandle()->query("delete FROM
    travel_expense_week WHERE emp_id = 1 and week_start
    = '1980-01-01'"); // remove multiples
    $tvi = new TravelExpenseWeek (
    array ('emp_id' => "1",
        'week_start' => "1980-01-01",
        'comments' => "comment",
        'territory_worked' => "Midwest",
        'mileage_rate' => "0.31",
        'cash_advance' => "0",
    $this->session->getDatabaseHandle();
    $result = $this->session->getDatabaseHandle()->query("select *
    FROM travel_expense_week WHERE emp_id = 1 and
    week_start = '1980-01-01'");
    $this->assertEquals(0, $result->numRows(), "pre check");
    $tvi->persist();
    $result = $this->session->getDatabaseHandle()->query("select *
    FROM travel_expense_week WHERE emp_id = 1 and
    week_start = '1980-01-01'");
    $this->assertEquals(1, $result->numRows(), "persist");
}
```

另外，请考虑这样一个事实：必须有东西负责所有 TravelExpenseItems 的生命周期。TravelExpenseWeek？TravelExpenseItem？这两个选项中，哪一个听起来像是一个不错的容器？

TravelExpenseWeek 作为容器的一个（极其明确的）测试如下所示：

```php
function testTravelExpenseWeekContainerRead() {
    // clear out the test database
    $this->session->getDatabaseHandle()->query("delete FROM
    travel_expense_item WHERE emp_id = 1 and
    expense_date >= '1980-01-06' and expense_date
    <= '2001-09-15'");
    $dbh = $this->session->getDatabaseHandle();
    // monday
    $item1 = new TravelExpenseItem (
    array ('emp_id' => "1", 'expense_date' => "1980-01-06",
        'description' => "lodging_and_hotel", 'amount' => "1.1"),
    $dbh);

    $item2 = new TravelExpenseItem (
    array ('emp_id' => "1", 'expense_date' => "1980-01-06",
        'description' => "meals_breakfast", 'amount' => "2.2 "),
    $dbh);

    $item3 = new TravelExpenseItem (
    array ('emp_id' => "1", 'expense_date' => "1980-01-06",
        'description' => "misc_supplies", 'amount' => "3.3 "),
    $dbh);

    // tuesday
    $item4 = new TravelExpenseItem (
    array ('emp_id' => "1", 'expense_date' => "2001-09-10",
        'description' => "lodging_and_hotel", 'amount' => "4.4 " ),
    $dbh);

    $item5 = new TravelExpenseItem (
    array ('emp_id' => "1", 'expense_date' => "2001-09-10",
        'description' => "meals_breakfast", 'amount' => "5.5 " ),
    $dbh);

    $item6 = new TravelExpenseItem (
    array ('emp_id' => "1", 'expense_date' => "2001-09-10",
        'description' => "misc_supplies", 'amount' => "6.6 " ),
    $dbh);

    // wednesday
    $item7 = new TravelExpenseItem (
    array ('emp_id' => "1", 'expense_date' => "1980-01-01",
        'description' => "lodging_and_hotel", 'amount' => "7.7 " ),
    $dbh);

    $item8 = new TravelExpenseItem (
    array ('emp_id' => "1", 'expense_date' => "1980-01-01",
        'description' => "meals_breakfast", 'amount' => "8.8 " ),
    $dbh);

    $item9 = new TravelExpenseItem (
    array ('emp_id' => "1", 'expense_date' => "1980-01-01",
        'description' => "misc_supplies", 'amount' => "9.9 " ),
    $dbh);
}
```

TravelExpenseItems 填充了周的前三天，每个代表不同类型的项目：meals_breakfast、misc_supplies 和 lodging_and_hotel：

## 第三部分：真实世界案例研究

```php
$item1->persist();
$item2->persist();
$item3->persist();
$item4->persist();
$item5->persist();
$item6->persist();
$item7->persist();
$item8->persist();
$item9->persist();
$week = new TravelExpenseWeek (
    array ('emp_id' => "1",
    'week_start' => "1980-01-06"),
    $this->session->getDatabaseHandle());
$week->readWeek();
// monday
$this->assertEquals(1.1, (float) $week->getExpenseAmount(0, 'lodging_and_hotel'));
$this->assertEquals(2.2, (float) $week->getExpenseAmount(0, 'meals_breakfast'));
$this->assertEquals(3.3, (float) $week->getExpenseAmount(0, 'misc_supplies'));
// tuesday
$this->assertEquals(4.4, (float) $week->getExpenseAmount(1, 'lodging_and_hotel'));
$this->assertEquals(5.5, (float) $week->getExpenseAmount(1, 'meals_breakfast'));
$this->assertEquals(6.6, (float) $week->getExpenseAmount(1, 'misc_supplies'));
// wednesday
$this->assertEquals(7.7, (float) $week->getExpenseAmount(2, 'lodging_and_hotel'));
$this->assertEquals(8.8, (float) $week->getExpenseAmount(2, 'meals_breakfast'));
$this->assertEquals(9.9, (float) $week->getExpenseAmount(2, 'misc_supplies'));
```

TravelExpenseItems 持久化后，此测试表明新的 TravelExpenseWeek 类将能够在给定员工 ID 和起始周的情况下检索一周的 TravelExpenseItems。

从其他方面来看，这也是一个重要的测试，因为在这里你正在定义 Web 页面的接口。回想一下，TravelExpenseItem 是基于天的，而 Web 页面是基于周的，因此需要 TravelExpenseWeek。因此，以每周方式遍历 TravelExpenseItems 的能力应当是至关重要的。

请注意，由于 TravelExpenseWeek 知道哪一天是周的第一天（对美国人来说是周日），你不需要明确指定目标日期。相反，你可以使用偏移量。周日用 0，周一用 1，依此类推。

## 探测性开发

在继续之前，考虑一下你将如何在屏幕上显示需要展示的内容。回去再看看图 19-8。请注意，必须有东西负责小计，更不用说顺序了。必须有东西将人类名称与数据库中存在的内容关联起来。

另外，请记住，“某物”最终都要由你来负责，任何能让你生活更轻松的事情都不会是坏事。显然，硬编码 HTML 将是一场维护噩梦。

为避免硬编码 HTML 导致的维护噩梦，请考虑使用如下的数据结构，它可用于生成需要显示的内容，并将其映射到你的数据字段：

```php
array(
    array('name' => 'Lodging', 'code' => 'lodging', 'data' =>
        array('Lodging &amp; Hotel', 'Other', 'Tips'),
    'persist' => array('lodging_and_hotel', 'lodging_other',
        array('lodging_tips')),
    array('name' => 'Meals', 'code' => 'meals', 'data' =>
        array('Breakfast', 'Lunch &amp; Snacks',
        'Dinner', 'Tips', 'Entertainment'),
```





```php
'persist' => array('meals_breakfast', 'meals_lunch',
    'meals_dinner', 'meals_tips',
    'meals_entertainment')),
array('name' => 'Transportation', 'code' => 'trans', 'data' =>
    array('Airfare', 'Auto Rental', 'Auto Maint./Gas',
    'Local Transportation', 'Tolls/Parking'),
    'persist' => array ('trans_airfare',
    'trans_auto_rental', 'trans_auto_maint', 'trans_local',
    'trans_tolls', 'trans_miles_traveled')),
array('name' => 'Miscellaneous', 'code' => 'misc', 'data' =>
    array('Gifts', 'Telephone &amp; Fax', 'Supplies',
    'Postage', 'Other'),
    'persist' => array('misc_gifts', 'misc_phone',
    'misc_supplies', 'misc_postage', 'misc_other'))));
```

第一层是一个节数组，这意味着每个节都会有一个小计，并且每个节包含行项目。

每个节都有一个 data 数组（即人类可读的描述），以及其计算机对应项 `persist`（这可能是数据库中每个项目的名称）。关联数组中的 code 项存在的目的是为了自动创建每个节都必须计算的半语义 JavaScript 变量（例如，用于餐饮、住宿和交通的变量）。这个数据结构将是将 HTML、JavaScript 数学、数据库和 PHP 对象粘合在一起的部分胶水；它是你的路线图。

## 更多交通费周测试

从 PHP 的交通费表单响应到数据库是一个重要步骤。这就是你定义期望从页面接收的内容的地方。请记住，你需要一种方法来获取整个响应，并从中轻松创建 TravelExpenseItem。这似乎是 TravelExpenseWeek 容器的合适工作。

回想一下，确定每个单元格唯一值的命名约定是 lodging_sun_0，它代表“节”+“天”+“行项目”。由于描述相同列/行、垂直/水平、电子表格单元格关系的方法几乎无穷无尽，这个命名约定相当合适。

此外，你可以根据其节偏移量（lodging_sun_0 中的“0”）轻松确定你正在处理的水平行。天和行项目是不同类型，这是有原因的：为了你的理智。在不同维度中操作数据已经很困难了；跟踪哪个对哪个更困难，而记住它们基于什么是在找麻烦。在其他条件相同的情况下，lodging_sun_0 包含的语义信息比 lodging_0_0 更多。

这是解析请求的测试：

```php
function testTravelExpenseWeekContainerParseRequest() {
    $response = array ( 'lodging_sun_0' => "1.1",
        'meals_sun_0' => "2.2",
        'misc_sun_2' => "3.3",
        'lodging_mon_0' => "4.4",
        'meals_mon_0' => "5.5",
        'misc_mon_2' => "6.6",
        'lodging_tue_0' => "7.7",
        'meals_tue_0' => "8.8",
        'misc_tue_2' => "9.9" );
    $week = new TravelExpenseWeek (
        array ( 'emp_id' => "1",
            'week_start' => "1980-01-06" ));
    $week->parse($response);
    $this->assertEquals(1.1, $week->getExpenseAmount(0, 'lodging_and_hotel'));
    $this->assertEquals(2.2, $week->getExpenseAmount(0, 'meals_breakfast'));
    $this->assertEquals(3.3, $week->getExpenseAmount(0, 'misc_supplies'));
    $this->assertEquals(4.4, $week->getExpenseAmount(1, 'lodging_and_hotel'));
    $this->assertEquals(5.5, $week->getExpenseAmount(1, 'meals_breakfast'));
    $this->assertEquals(6.6, $week->getExpenseAmount(1, 'misc_supplies'));
    $this->assertEquals(7.7, $week->getExpenseAmount(2, 'lodging_and_hotel'));
    $this->assertEquals(8.8, $week->getExpenseAmount(2, 'meals_breakfast'));
    $this->assertEquals(9.9, $week->getExpenseAmount(2, 'misc_supplies')); }
```

$response 数组模拟了你将从表单输入接收到的内容，请记住，$response 的值和 persist 元值反映在你的路线图数据结构中。

为持久化容器再创建一个测试。它与交通费项目测试非常相似：

```php
function testTravelExpenseWeekContainerWrite () {
    $this->session->getDatabaseHandle()->query("delete FROM
        travel_expense_item WHERE emp_id = 1 and
        expense_date >= '1980-01-06' and expense_date
        <= '2001-09-15'");
    $response = array (
        'lodging_sun_0'=>"1.1",'meals_sun_0'=>"2.2",'misc_sun_2'=>"3.3",
        'lodging_mon_0'=>"4.4",'meals_mon_0'=>"5.5",'misc_mon_2'=>"6.6",
        'lodging_tue_0'=>"7.7",'meals_tue_0'=>"8.8",'misc_tue_2'=>"9.9" );
    $week = new TravelExpenseWeek (
        array ('emp_id' => "1",
            'week_start' => "1980-01-06",
            'territory_worked' => "Midwest",
            'comments' => "comment",
            'cash_advance' => "0",
            'mileage_rate' => "0.31"));
    $this->session->getDatabaseHandle();
    $week->readWeek();
    $this->assertEquals(1.1, (float)
        $week->getExpenseAmount(0, 'lodging_and_hotel'));
    $this->assertEquals(2.2, (float)
        $week->getExpenseAmount(0, 'meals_breakfast'));
    $this->assertEquals(3.3, (float)
        $week->getExpenseAmount(0, 'misc_supplies'));
    $this->assertEquals(4.4, (float)
        $week->getExpenseAmount(1, 'lodging_and_hotel'));
    $this->assertEquals(5.5, (float)
        $week->getExpenseAmount(1, 'meals_breakfast'));
    $this->assertEquals(6.6, (float)
        $week->getExpenseAmount(1, 'misc_supplies'));
    $this->assertEquals(7.7, (float)
        $week->getExpenseAmount(2, 'lodging_and_hotel'));
    $this->assertEquals(8.8, (float)
        $week->getExpenseAmount(2, 'meals_breakfast'));
    $this->assertEquals(9.9, (float)
        $week->getExpenseAmount(2, 'misc_supplies')); }
```

在这个测试中（作为额外方法添加到 test.widgetsession.php），TravelExpenseWeek 解析 $response，在 $week->persist() 中持久化 TravelExpenseItem，从数据库中重新读取 $week->readWeek()，并最终验证读取的内容。

请注意，这些测试大量使用了复制粘贴编程。保持整洁是一条通用规则，因此如果大多数测试需要相同的设置，请将它们放入设置中，但不要过早重构你的测试。你的测试通常是更改的第一个位置，因此它们应该易于阅读和修改。

## 满足交通费周测试

到现在，满足 TravelExpenseWeek 的有效性和持久性测试应该可以预见地很容易：

```php
class TravelExpenseWeek extends PersistableObject {
    public $items = array();

    function __construct($results, $dbh = null) {
        parent::__construct($results, $dbh);
    }

    public function isValid() {
        if ($this->isEmpty("emp_id") == true) return false;
        if ($this->isEmpty("week_start") == true) return false;
        if ($this->isEmpty("territory_worked") == true) return false;
        if ($this->isEmpty("mileage_rate") == true) return false;
        return true;
    }

    public function persist() {
        return $this->persistWork("travel_expense_week",
            array ( "emp_id",
                "week_start",
                "comments",
                "territory_worked",
                "cash_advance",
                "mileage_rate"));
    }

    public function getSqlWhere() {
        return " emp_id = ".$this->emp_id." and week_start = ".$this->week_start."";
    }

    public function parse(&$request) { }
    public function readWeek() { }
    public function getExpenseAmount($offset, $description) { }
}
```

parse、readWeek 和 getExpenseAmount 函数由 TravelExpenseWeekContainerParseRequest 和 TravelExpenseWeekContainerWrite 测试要求；因此，它们只是语法存根。

## 满足解析请求测试

TravelExpenseWeekContainerParseRequest 测试可能有点棘手，因为它涉及数据操作。你的首要任务是处理依赖项，这是你之前考虑过的元数组路线图的一部分。将此函数添加到 lib/expense.php 中的 TravelExpenseWeek 类将完成这项工作：

```php
public function getExpensesMetaArray () {
    return array(
        array('name' => 'Lodging', 'code' => 'lodging', 'data' =>
            array('Lodging &amp; Hotel','Other','Tips'), 'persist' =>
            array('lodging_amp_hotel', 'lodging_laundry',
            'lodging_tips')),
        array('name' => 'Meals', 'code' => 'meals', 'data' =>
            array('Breakfast', 'Lunch &amp; Snacks',
            'Dinner', 'Tips', 'Entertainment'), 'persist' =>
            array('meals_breakfast', 'meals_lunch',
            'meals_dinner', 'meals_tips',
            'meals_entertainment')),
        array('name' => 'Transportation', 'code' => 'trans', 'data' =>
            array('Airfare', 'Auto Rental', 'Auto Maint./Gas',
            'Local Transportation',
            'Tolls/Parking'), 'persist' =>
            array ('trans_airfare', 'trans_auto_rental',
            'trans_auto_maint', 'trans_local',
            'trans_tolls', 'trans_miles_traveled')),
        array('name' => 'Miscellaneous', 'code' => 'misc', 'data' =>
            array('Gifts', 'Telephone &amp; Fax', 'Supplies',
            'Postage', 'Other'), 'persist' =>
            array('misc_gifts', 'misc_phone',
            'misc_supplies', 'misc_postage',
            'misc_other')));
    }
}
```




## 第三部分：一个真实案例研究

除了元数组之外，你还需要一种检索每个 `TravelExpenseItem` 的方式。回顾你的 `TravelExpenseWeekContainerParseRequest` 测试，你的测试需要 `TravelExpenseWeek-getExpenseAmount()` 函数：

```php
$this->assertEquals(8.8, $week->getExpenseAmount(2, 'meals_breakfast'));
```

目前，该函数只是通过遍历 `TravelExpenseWeek->items` 来简单实现。在 `lib/expense.phpm` 的 `TravelExpenseWeek` 中添加以下内容，给自己留个关于这种丑陋实现的备注：

```php
/**
 * todo: put into an associative array
 */
public function getExpenseAmount($offset, $description) {
    $targetDate = $this->addDays($this->week_start, $offset);
    foreach ($this->items as $item) {
        if ($item->expense_date == $targetDate &&
            $item->description == $description) {
            return $item->amount;
        }
    }
    return "";
}
```

请注意，你正在调用一个带有偏移量的 `addDays()` 函数，以获取日期的当前字符串表示。

最好创建一个 `addDays()` 方法，然后快速做一个三分钟的黑客攻击来添加一天的秒数（86400 等于 60*60*24）。`TravelExpenseWeek` 现在包含以下内容：

```php
/**
 * todo: will this fail on daylight savings time?
 */
public function addDays($start, $days) {
    return date("Y-m-d", strtotime($start) + $days * 86400);
}
```

然而，这可能会带来一个隐患。在美国夏令时切换期间，特定的那一天会有一小时的秒数差异。PHP 返回的是哪种时间？是本地时间还是 GMT？你最好弄清楚这一点，否则六个月后你就会在当地快餐店翻汉堡包了。目前，先记下这种丑陋的实现，并继续满足你的 `TravelExpenseWeekContainerParseRequest` 测试。

`TravelExpenseWeek` 对象的核心功能是解析 PHP 的差旅费用表单响应，以创建单独的 `TravelExpenseItem`，或数据的关联数组。

回顾你正在映射以下数据结构：

```php
array('name' => 'Lodging', 'code' => 'lodging', 'data' =>
    array('Lodging &amp; Hotel', 'Other', 'Tips'), 'persist' =>
    array('lodging_and_hotel', 'lodging_laundry',
        'lodging_tips'))
```

此外，PHP 响应对象中包含以下命名约定：

```
lodging_sun_0
```

一旦你弄明白了这一点，剩下的就是创建 `TravelExpenseItems` 并将它们存储在 `TravelExpenseWeek->items` 数组中。在 `lib/expense.phpm` 的 `TravelExpenseWeek` 中添加解析函数：

```php
/**
 * This function bridges the gap between the day-based DB and the
 * week-based view
 */
public function getWeekArray() {
    return array ('sun', 'mon', 'tue', 'wed', 'thu', 'fri', 'sat');
}
public function parse (&$request) {
    // section loop
    foreach ($this->getExpensesMetaArray() as $sectionlist) {
    // row loop
    for ($i=0; $i < count ($sectionlist['persist']); $i++) {
        $daynum = 0;
        // day loop
        foreach ($this->getWeekArray() as $day) {
            $index = $sectionlist['code']."_".$day."_".$i;
            if (array_key_exists($index, $request) and
            $request[$index] <> null and
            $request[$index] <> "") {
            // create new item and store in $this->items
            array_push (
            $this->items,
            new TravelExpenseItem (
            array ('emp_id' => $this->emp_id,
            'expense_date' =>
            $this->addDays ($this->week_start,
            $daynum),
            'description' =>
            $sectionlist['persist'][$i],
            'amount' => (float) $request[$index]),
            $this->dbh));
            }
            $daynum++;
        }
    }
}
}
```

这五个函数共同构成了 `TravelExpenseWeek` 中实现的大部分功能。该类承担了一项并非轻而易举的任务：使用以数据库为中心的结构修改基于 Web 的数据结构。

### 满足差旅费周容器读写测试

在给出最少量的数据、员工 ID 和起始周后，你的测试应该使用 TravelExpenseItems 填充 TravelExpenseWeek 以与数据库交互。回顾该测试大致执行以下操作：

```php
$week = new TravelExpenseWeek (
    array ( 'emp_id' => "1",
        'week_start' => "1980-01-06",
        'territory_worked' => "Midwest",
        'comments' => "comment",
        'cash_advance' => "0",
        'mileage_rate' => "0.31"),
    );
$this->__session->getDatabaseHandle());
$week->readWeek();
```

这应该能完美完成任务。将 readWeek() 函数添加到 lib/expense.phpm 的 TravelExpenseWeek 中：

```php
public function readWeek() {
    $sql = "select * from travel_expense_week where";
    $sql .= " emp_id = ".$this->emp_id." and ";
    $sql .= " week_start = '".$this->week_start."'";
    $result = $this->dbh->query($sql);
    if (DB::isError($result) <> true && $result->numRows() > 0) {
        $row = $result->fetchRow();
        $this->contentBase['comments'] = $row['comments'];
        $this->contentBase['territory_worked'] = $row['territory_worked'];
        $this->contentBase['cash_advance'] = $row['cash_advance'];
        $this->contentBase['mileage_rate'] = $row['mileage_rate'];
    }
    $sql = "select * from travel_expense_item where";
    $sql .= " emp_id = ".$this->emp_id." and ";
    $sql .= " expense_date >= '".$this->week_start."' and ";
    $sql .= " expense_date <= '".$this->addDays($this->week_start, 6)."'";
    $this->items = array();
    $result = $this->dbh->query($sql);
    if (DB::isError($result) or $result->numRows() == 0) return;
    while ($row = $result->fetchRow()) {
        array_push ($this->items, new TravelExpenseItem ($row));
    }
}
```

请注意，这实际上有两个部分。第一个数据库查询返回 TravelExpenseWeek 的状态；第二部分返回关联的 TravelExpenseItems，并将它们添加到 TravelExpenseWeek->items 数组中。

不过，你注意到一个微妙的问题了吗？注意你是如何懒惰地将整个 $row 传递给 TravelExpenseItem 构造函数的？回顾 PersistableObject（TravelExpenseItem 的父类）的构造函数如下：

```php
function __construct ($results, $dbh = null) {
    $this->dbh = $dbh;
    if ($results <> null) {
        $this->contentBase = $results; // copy
    }
}
```

因此，TravelExpenseItem 是否盲目地存储你给它的任何东西，而不考虑数据是什么？
嗯，这绝对是浪费，而且尽管数据库中没有 TravelExpenseItem 中没有的数据，但该对象的行为来自 PersistableObject，而 TravelExpenseWeek、Contact 和 ContactVisit 都是它的子类。将这些对象中的任何一个传递给 PHP 的 $_REQUEST 将导致可怕的资源浪费。

要将 PersistableObject 的默认行为从“存储一切”更改为“存储你期望找到的内容”，请退后一步，创建一个新测试，用于测试不希望的行为。因为 TravelExpenseItem 很简单，所以它是理想的候选者：

```php
function testIgnoreExtra() {
    $response = array ('emp_id'
        => "1",
        'expense_date' => "1980-01-01",
        'description' => "one",
        'amount' => "1.0",
        'extra' => "extra bits");
    $tvi = new TravelExpenseItem($response);
    $this->assertEquals(null, $tvi->extra);
}
```

果不其然，这个测试失败了。这也意味着，如果你在构造过程中做些蠢事，比如传入响应，TravelExpenseWeek（预期会解析 PHP 的 $_RESPONSE 对象）将会变得非常臃肿。

解决这个问题的一种方法是事先知道对象需要什么，从而忽略其他任何内容。因此，不要让 TravelExpenseItem->persist() 函数看起来像

```php
public function persist() {
    return $this->persistWork (
        "travel_expense_item",
        array ( "emp_id",
            "expense_date",
            "description",
            "amount"));
}
```

通过传入一些内部状态，持久化函数可以变得更加简洁：

```php
public function persist() {     return $this->persistWork (
    $this->contentMetaTable,
    $this->contentMetaOnly);
}
```



把所有内容组合在一起，你最终会得到重写后的类。它没什么不同。只是稍微移动了一下位置：

```
class TravelExpenseItem extends PersistableObject {
    protected $contentMetaTable = null;
    protected $contentMetaOnly = null;
    function __construct ($results, $dbh = null) {
        $this->contentMetaTable = "travel_expense_item";
        $this->contentMetaOnly = array ( "emp_id",
            "expense_date",
            "description",
            "amount");
        $content = array();
        foreach ($this->contentMetaOnly as $key) {
            if (array_key_exists($key, $results))
                $content[$key] = $results[$key];
        }
        parent::__construct ($content, $dbh);
    }
    public function isValid() {
        if ($this->isEmpty("emp_id") == true) return false;
        if ($this->isEmpty("expense_date") == true) return false;
        if ($this->isEmpty("description") == true) return false;
        if ($this->isEmpty("amount") == true) return false;
        return true;
    }
    public function getSqlWhere() {
        return " emp_id = " .$this->emp_id. " and expense_date
        = " .$this->expense_date." ' and description = " .$this->description."'";
    }
    public function persist() {
        return $this->persistWork (
            $this->contentMetaTable,
            $this->contentMetaOnly);
    }
}
```

在这种情况下，你需要检查通过构造函数传入的内容是否就是你要找的。修复最后剩下的TravelExpenseWeek测试，然后进行重构。

编写TravelExpenseWeek所需的工作量要小得多，因为每个TravelExpenseItem已经知道如何持久化自身。你只需要调用每个的`persist()`函数即可。

只需在lib/expense.php中TravelExpenseWeek的持久化函数末尾添加这个小循环：

```
public function persist() {
    $this->persistWork ("travel_expense_week",
        array("emp_id",
            "week_start",
            "comments",
            "territory_worked",
            "cash_advance",
            "mileage_rate"));
// persist each item to the database
foreach ($this->items as $item) {
    $item->persist();
}

return true;
}
```

恭喜！你的所有单元测试现在都通过了。现在是时候添加一些剩余功能，包括快速重构。

## 快速重构

满足所有单元测试至关重要，因为在下一次重构期间，它们会告诉你是否不小心破坏了看似无关的代码部分。

既然TravelExpenseItem和TravelExpenseWeek现在结构更加相似，但错误检查程度不一，请将该功能上移到PersistableObject中。

基本上，你想在PersistableObject中添加这个：

```
protected $contentMetaTable = null;
protected $contentMetaOnly = null;
public function persist() {
    return $this->persistWork (
        $this->contentMetaTable,
        $this->contentMetaOnly);
}
```

两个构造函数中还有相同的循环，也可以上移：

```
foreach ($this->contentMetaOnly as $key) {
    if (array_key_exists($key, $results))
        $this->contentBase[$key] = $results[$key];
}
```

以下是生成的对象快照：

```
class PersistableObject {
    protected $contentBase = array();
    protected $contentMetaTable = null;
    protected $contentMetaOnly = null;
    protected $dbh = null; // database handle
    protected $dispatchFunctions = array("role" => "getrole");
    function __get ($key) {
        // content removed for brevity
    }

    function __construct ($results, $dbh = null) {
        $this->dbh = $dbh;
        if ($this->contentMetaOnly <> null) {
            foreach ($this->contentMetaOnly as $key) {
                if (array_key_exists($key, $results)) {
                    $this->contentBase[$key] = $results[$key];
                }
            }
        } elseif ($results <> null) {
            $this->contentBase = $results; // copy
        }
    }

    public function implodeQuoted (&$values, $delimiter) {
        // content removed for brevity
    }

    public function generateSqlInsert ($tableName, $metas, $values) {
        // content removed for brevity
    }

    public function generateSqlInsert ($tableName, $metas, $values) {
        // content removed for brevity
    }

    public function generateSqlUpdate ($tableName, $metas, $values) {
        // content removed for brevity
    }

    public function generateSqlDelete ($tableName) {
        // content removed for brevity
    }

    public function getSqlWhere() {
        // content removed for brevity
    }

    protected function isEmpty($key) {
        // content removed for brevity
    }

    public function isValid() {
        // content removed for brevity
    }

    public function persistWork ($tablename, $meta) {
        // content removed for brevity
    }
}

public function persist() {
    return $this->persistWork (
        $this->contentMetaTable,
        $this->contentMetaOnly);
}
```

构造函数负责确定数据是否“可保留”。还要注意的是，该行为具有向后兼容性，因为如果contentMetaOnly数组为null，PersistableObject会简单地将$results复制到其contentBase中。

现在你的TravelExpenseItem可以进一步精简：

```
class TravelExpenseItem extends PersistableObject {
    function __construct ($results, $dbh = null) {
        $this->contentMetaTable = "travel_expense_item";
        $this->contentMetaOnly = array (
            "emp_id",
            "expense_date",
            "description",
            "amount");
        parent::__construct ($results, $dbh);
    }
    public function isValid() {
        if ($this->isEmpty("emp_id") == true) return false;
        if ($this->isEmpty("expense_date") == true) return false;
        if ($this->isEmpty("description") == true) return false;
        if ($this->isEmpty("amount") == true) return false;
        return true;
    }
    public function getSqlWhere() {
        return " emp_id = ".$this->emp_id." and expense_date = '
```

你看到了吗？TravelExpenseItem的构造函数设置其PersistableObject状态，然后将参数传递给父类PersistableObject？

因此，尽管你被要求显式调用构造函数，但这让你有机会在父对象PersistableObject中预先设置状态。

现在对TravelExpenseWeek做同样的修改：

```
class TravelExpenseWeek extends PersistableObject {
    public $items = array();
    function __construct ($results, $dbh = null) {
        $this->contentMetaTable = "travel_expense_week";
        $this->contentMetaOnly = array (
            "emp_id",
            "week_start",
            "comments",
            "territory_worked",
            "cash_advance",
            "mileage_rate");
        parent::__construct ($results, $dbh);
    }
    public function isValid() {
        // content removed for brevity
    }
}

public function persist() {
    if (parent::persist() == false) return false;
    // persist each item to the database
    foreach ($this->items as $item) {
        if ($item->persist() == false) return false;
    }
    return true;
}
public function getSqlWhere() {
    return "emp_id = ".$this->emp_id." and week_start = "."'".$this->week_start."'";
}
public function getExpensesMetaArray () {
    // content removed for brevity
}
public function getWeekArray() {
    // content removed for brevity
}
public function addDays($start, $days) {
    // content removed for brevity
}
public function parse (&$request) {
    // content removed for brevity
}
public function readWeek() {
    // content removed for brevity
}
public function getExpenseAmount($offset, $description) {
    // content removed for brevity
}
}
```

请注意，TravelExpenseWeek重写了PersistableObject->persist()函数。不过，它首先调用PersistableObject->persist()，然后持久化其持有的每个TravelExpenseItem。请记住，由于插入/更新/删除的逻辑位于PersistableObject->persistWork()中，它仍然可以正常工作，你只需要记住在具体类（如TravelExpenseWeek）中实现getSqlWhere函数。测试仍然通过吗？做得好，但别太快，因为现金预付不是必需的（如有效性测试所示）：

```
function testValidTravelExpenseWeek() {
    $tvi = new TravelExpenseWeek (
        array ('emp_id' => "1",
        'week_start' => "1980-01-01",
        'comments' => "comment",
        'mileage_rate' => "0.31",
        'territory_worked' => "Midwest" ));
    $this->assertEquals(true, $tvi->isValid(), "valid expense");
}
```




然而，其他每个测试都将 cash_advance 设置为零。如果从测试中移除 cash_advance 会发生什么？它会崩溃！这是因为 PersistableObject 会根据数据库记录的每个字段盲目创建 SQL。

修改持久性测试，以反映 cash_advance 和 comments 都不是必需的：

```
function testTravelExpenseWeekPersistence() {
	$this->session->getDatabaseHandle()->query("delete FROM
travel_expense_week WHERE emp_id = 1 and
week_start = '1980-01-01'"); // remove multiples

	$tvi = new TravelExpenseWeek (
	array ('emp_id' => "1",
		'week_start' => "1980-01-01",
		'territory_worked' => "Midwest",
		'mileage_rate' => "0.31"));
	$this->session->getDatabaseHandle();

	$result = $this->session->getDatabaseHandle()->query("select *
FROM travel_expense_week WHERE emp_id = 1 and week_start
= '1980-01-01'");

	$this->assertEquals(0, $result->numRows (), "pre check");
	$this->assertEquals (true, $tvi->persist (), "save");
	$result = $this->session->getDatabaseHandle()->query("select *
FROM travel_expense_week WHERE emp_id = 1 and week_start
= '1980-01-01'");
	$this->assertEquals(1, $result->numRows (), "persisted ok");
	$row = $result->fetchRow();
	$this->assertEquals (0.0, (float) $row['cash_advance'],
	"cash advance default");
}
```

cash_advance 的默认值也是个容易修复的问题。只需修改 TravelExpenseWeek 的构造函数，将默认值设置为零和空字符串：

```
class TravelExpenseWeek extends PersistableObject {
function __construct ($results, $dbh = null) {
$this->contentMetaTable = "travel_expense_week";
$this->contentMetaOnly = array ("emp_id",
"week_start",
"comments",
"territory_worked",
"cash_advance",
"mileage_rate");

$this->contentBase['comments'] = "";
$this->contentBase['cash_advance'] = "0.0";
	parent::__construct ($results, $dbh);
}
```

## 第三部分：真实世界案例研究

测试又一次通过了，这意味着你完成了，对吧？进行一次快速的“grep 待办”搜索，会发现这个令人烦恼的问题：

```
/**
* todo: will this fail on daylight savings time?
*/
public function addDays($start, $days) {
 return date("Y-m-d", strtotime($start)+$days*86400);
}
```

再仔细看一下，你决定可能确实存在问题。在美国大多数地方，夏令时在十月的最后一个星期日结束，这意味着时钟会拨慢，且这一天的秒数超过 86,400 秒。编写一个测试来确认它会失败：

```
function testDaylightSavingTime() {
 $tw = new TravelExpenseWeek (array());
 $this->assertEquals("2004-10-30", $tw->addDays("2004-10-29", 1));
 $this->assertEquals("2004-10-31", $tw->addDays("2004-10-29", 2));
 $this->assertEquals("2004-11-01", $tw->addDays("2004-10-29", 3, "no DST"));
}
```

果然，有问题。从十月二十九日添加三天应该进入十一月，而不是两次落在十月三十一日。查阅你的函数，strtotime() 可以接受日期偏移量来为你执行日期计算。在不假设每天秒数的情况下，重写 PersistableObject 的 addDays() 函数：

```
public function addDays($start, $days) {
 return date("Y-m-d", strtotime($start." + ".$days." days"));
}
```

因为你剩下的“待办”工作是修改 getExpenseAmount 函数，这其实是优化，可以留到以后再做。没有必要过早优化，保持进度非常重要。

虽然这确实是一项大量工作，但你现在拥有编写得相当合理、完全向后兼容的持久性对象。你的系统正在分阶段增长，下次你处理它们时会更新 Contact 和 ContactVisit。现在是时候完成当前的任务：差旅费用报表。

### 已完成的差旅费用报表

经过几个小时的工作，你得到了图 19-9 中所示的内容。

### Widget World

### 差旅费用报表

员工姓名：Ed Locky-Thompson  
编号：1  
工作地区：worked  
部门：sales  
起始周：2004-07-04  

| | 周日 | 周一 | 周二 | 周三 | 周四 | 周五 | 周六 | 合计 |
|---|---|---|---|---|---|---|---|---|
| 住宿 | | | | | | | | |
| 住宿与酒店 | 1.00 | 2.00 | 3.00 | | | | | |
| 其他 | 2.00 | | | | | | | |
| 小费 | 3.00 | | | | | | | |
| 住宿总计 | | | | | | | | |
| 餐饮 | | | | | | | | |
| 早餐 | 4.00 | | | | | | | |
| 午餐与小吃 | 5.00 | | | | | | | |
| 晚餐 | 6.00 | | | | | | | |
| 小费 | 7.00 | | | | | | | |
| 娱乐 | 8.00 | | | | | | | |
| 餐饮总计 | | | | | | | | |
| 交通 | | | | | | | | |
| 机票 | 9.00 | | | | | | | |
| 汽车租赁 | 10.00 | | | | | | | |
| 汽车保养/汽油 | 11.00 | | | | | | | |
| 本地交通 | 12.00 | | | | | | | |
| 过路费/停车费 | 13.00 | | | | | | | |
| 交通小计 | | | | | | | | |
| 行驶里程数 | 19.00 | | | | | | | |
| 每英里 0.36 的里程费 | | | | | | | | |
| 交通总计 | | | | | | | | |
| 杂项 | | | | | | | | |
| 礼品 | 14.00 | | | | | | | |
| 电话与传真 | 15.00 | | | | | | | |
| 耗材 | 16.00 | | | | | | | |
| 邮资 | 17.00 | | | | | | | |
| 其他 | 18.00 | | | | | | | |
| 杂项总计 | | | | | | | | |

小计  
减去预付现金 20.00  
应付员工  
应付公司  

评论：  
评论内容  

提交报表  

退出  

仅供 Widget World 内部使用 - 测试环境。  

图 19-9：已完成的差旅费用表单  

这是初稿，因此先从如何在文件 travel-expenses.php 中为 Smarty 模板提供数据开始，如果用户是从主菜单进入，该文件即为其登录入口：

```
<?php
require_once ("lib/common.php");
require_once ("lib/expense.php");
// is the user logged in?
if (!($session->isLoggedIn()) {
    redirect ("index.php");
}

$user = $session->getUserObject();
$week = new TravelExpenseWeek (
    array ('emp_id' => $user->id,
        'week_start' => getCurrentStartWeek(),
        'territory_worked' => $_REQUEST["territory_worked"],
        'comments' => $_REQUEST["comments"],
        'cash_advance' => $_REQUEST["cash_advance"],
        'mileage_rate' => $GLOBALS["expense-mileage-travelrate"]),
    $session->getDatabaseHandle());
```

```
// display
if ($_REQUEST["action"] != "persist_expense") {
    $week->readWeek();
    $smarty->assign_by_ref ("user",
        $user);
    $smarty->assign_by_ref ("week",
        $week);
    $smarty->assign('start_weeks',
        getStartWeeks());
    $smarty->assign('current_start_week',
        getCurrentStartWeek());
    $smarty->assign_by_ref ('expenses',
        $week->getExpensesMetaArray());
    $smarty->assign('travelrate',
        $GLOBALS["expense-mileage-travelrate"]);
    $smarty->display('travel-expenses.tpl');
    exit();
}
```

```
// gather and persist week
$week->parse($_REQUEST);
$week->persist();
print "saved, thanks";
?>
```

作为用户可访问的登录点，此脚本有两种操作模式：一种是从数据库读取差旅费用（readWeek）进行显示，另一种是根据 action 是否设置为 persist_expense 来保存表单数据（persist）。

和往常一样，你非常有趣的 getExpensesMetaArray() 是屏幕的基石，并作为 Smarty 变量 expenses 传入。请注意，所有重量级对象均按引用传递给 Smarty，因此不会自动创建副本。

现在，来看看位于 templates/travel-expenses.tpl 中的用于显示差旅费用页面的基本 Smarty 模板：

```
{include file="header.tpl" title="Widget World - Travel Expenses"}
{literal}
<SCRIPT TYPE="text/javascript">
<!--
function reloadCalc () {
    window.document.forms[0].week_start.value =
    window.document.forms[1].week_start.value // hidden form
    // window.document.forms[0].submit(); // hidden form )
-->
</SCRIPT>
{/literal}
<h3>Travel Expense Report</h3>
<form method="post">
<input type="hidden" name="action" value="reload_expense">
<input type="hidden" name="week_start" value="">
</form>
<form id="calc" name="calc" action="travel-expenses.php" method="post">
<table border="0" width="100%">
<tr>
<td><b>Employee Name:</b></td>
<td>({$user->first_name}) {$user->last_name}</td> <td><b>Department:</b></td>
<td>{$user->department}</td>
</tr>
<tr>
<td><b>Number:</b></td>
<td>{$user->id}</td> <td><b>Start Week:</b></td>
<td><SELECT NAME="week_start" onchange="reloadCalc()">{html_options
values=$start_weeks output=$start_weeks selected=$current_start_week}
</SELECT></td>
</tr>
<tr>
<td><b>Territory Worked:</b></td>
<td colspan=3><input name="territory_worked" size=20 maxsize=60 value =
"{$week->territory_worked}"></td>
</tr>
</table>
<br><br>
```

页面上的第一个表单与客户联系报表中的类似，你使用了一个特殊的“隐藏”表单，该表单由 JavaScript 填充起始周的值。选择新周时，表单会自动提交。

第二个表单的开头仅包含一些你正在收集的基本信息，包括 territory_worked。





## 第三部分：真实世界案例研究

下一节开始显示电子表格部分。代码在周日和周六之间简单复制。请记住，这是您的第一个屏幕，您可能需要更改某些项目；因此，忽略最终的“周”循环可以理解。目前，它只是一个基本的输入表单，没有错误检查或电子表格类似的活动：

```
<table border="0">
<tr><td></td><td></td><td>Sun/<td><td>Mon/<td><td>Tues/<td><td>Wed/<td><td>Thur/<td>
<td>Fri/<td><td>Sat/<td><td>Total</td></tr>
{section name=idx loop=$expenses}{strip}
<tr><td><b>{$expenses[idx].name}</b></td><td></td><td></td><td></td><td></td><td></td><td></td><td>
<td></td><td></td><td></td><td></td></tr>
```

```
{section name=idx2 loop=$expenses[idx].data}{strip}
{assign var="p" value=$expenses[idx].persist[idx2]}
```

```
<tr bgcolor="{cycle values="#eeeee, #dddddd"}">
<td>{$expenses[idx].data[idx2]}</td>
```

```
<td><input name="{$expenses[idx].code}_sun_{$smarty.section.idx2.index}"
type="text" size="7" maxsize="17" value="{$week->getExpenseAmount(0, $p)}"/></td>
```

请记住，您正在构建看起来像这样的 HTML 输出：

```
<input name="lodging_sun_0" type="text" size="7" maxsize="17" value="1.00">
```

这里的两个主要循环遍历您的费用数组：

```
return array(
    array('name' => 'Lodging', 'code' => 'lodging', 'data' =>
    array('Lodging &amp; Hotel','Other','Tips'), 'persist' =>
    array('lodging_and_hotel', 'lodging_laundry',
    'lodging_tips'))
```

Smarty 变量 $p 是动态创建的，作为一种便利，以确保 Smarty 代码不会变得过于笨拙：getExpenseAmount(0, $p) 比 getExpenseAmount(0, $expenses[idx].persist[idx2]) 更易读。最后，代表周日的最后两行被复制了六次，以表示一周的每一天。它们（幸运的是）没有显示：

```
<td><input readonly
name="{$expenses[idx].code}_week_sub_{$smarty.section.idx2.index}"
type="text" size="7" maxsize="17">
</td>
</tr>
{/strip}{/section}
```

这工作良好，但总是有例外。您的客户要求在接受“行驶英里数”之前先提供交通小计，然后对该部分进行汇总。

Smarty 可以处理自己的条件，所以接下来加上这个；但行驶英里数不在您的费用元数组中，因此必须加以处理：

```
{if $expenses[idx].code == 'trans'}
<tr><td>{$expenses[idx].name} Subtotal</td>
<td><input readonly name="{$expenses[idx].code}_sun_sub"
type="text" size="7" maxsize="17"></td>
```

同样，代码在小计之前又被复制了六次（未显示）：

```
<td><input readonly name="{$expenses[idx].code}_week_sub" type="text" size="7" maxsize="17"/></td></tr>
<tr><td>Nbr of miles traveled</td>
<td><input name="mitr_sun" type="text" size="7" maxsize="17"
value="{$week->getExpenseAmount(0, 'trans_miles_traveled')}"/></td>
```

为简洁起见，一周的其余部分未显示：

```
<td><input readonly name="mitr_tot" type="text" size="7"
maxsize="17"/></td></tr>
<tr><td>Miles at {$travelrate} / mile </td><td><input readonly
name="mitot_sun" type="text" size="7" maxsize="17"/></td>
```

同样是重复的里程数（mitrs）：

```
<td><input readonly name="mitot_tot" type="text" size="7"
maxsize="17"/></td></tr>
<tr><td>{$expenses[idx].name} Total</td><td><input readonly
name="{$expenses[idx].code}_sun_sub2" type="text" size="7"
maxsize="17"/></td>
{else}
<tr><td>{$expenses[idx].name} Total</td><td><input readonly
name="{$expenses[idx].code}_sun_sub" type="text" size="7"
maxsize="17"/></td>
```

这完成了交通例外，并继续进行标准处理。本质上，它使您能够避免在交通底部添加额外的里程行。

```
<td><input readonly name="{$expenses[idx].code}_week_sub" type="text"
size="7" maxsize="17"/></td></tr>
{/if}
{/strip}{/section}
```

屏幕的其余部分表示小计、应付金额和每周评论：

```
<tr><td></td><td></td><td></td><td></td><td></td></td></td>
<td colspan="3">Subtotal</td>
<td>
<input readonly name="subtotal" type="text" size="7" maxsize="17">
</input>
</td>
</tr>
<tr><td></td><td></td><td></td><td></td><td></td></td></td>
<td colspan="3">Less Cash Advance</td>
<td><input name="cash_advance" type="text" size="7"
maxsize="17" value="{$week->cash_advance}"/></td>
</tr>
<tr><td></td><td></td><td></td><td></td><td></td></td></td>
<td colspan="3">Due Employee</td>
<td><input readonly name="totaldueemployee" type="text" size="7"
maxsize="17"/></td></tr>
```

```
<tr><td></td><td></td></td></td></td></td></td></td>
<td colspan="3">Due Company</td>
<td><input readonly name="totalduecompany" type="text" size="7"
maxsize="17"></td></tr>
</table>
<br><br>
Comments:<br>
<TEXTAREA NAME="comments" COLS=80 ROWS=6>{$week->comments}</TEXTAREA>
<br><br><center>
<input type="submit" name="submit" value=" Submit Report " >
</center>
<input type="hidden" name="action" value="persist_expense">
</form>
{include file="footer.tpl"}
```

尽管屏幕甚至缺乏基本的错误检查或任何电子表格类似的功能，但您仍处于项目非常关键的节点。该屏幕当前状态从技术上讲可以用于生产。

不建议，是的，但这是您交付业务价值的地方！将其交到客户手中，开始获取他们的反馈。

这次大跨度刚刚处理了故事 2、3 和 10。

### 旅行费用报表作为电子表格

您的客户喜欢旅行费用报表。他们正在使用它，并就如何、什么和原因向您提供有价值的反馈。

幸运的是，他们想要的唯一额外功能是让它像电子表格一样运行，那需要什么呢？

JavaScript 提供了一个您感兴趣的事件：onkeyup。它可以应用于您的输入框，以便在输入新信息时即时重新计算。

然而，模拟电子表格并不像听起来那么容易。这是新的模板/travel-expenses.tpl：

```
{include file="header.tpl" title="Widget World - Travel Expenses"}
{literal}
<SCRIPT TYPE="text/javascript">
<!-- function subtotal(thisForm, totalcell, cellArray) {
var subtot = 0;
for (var i=0; i < cellArray.length; i++) {
if (isNaN(thisForm[cellArray[i]].value))
thisForm[totalcell].value = 0;
else
subtot = Math.round(subtot*100 +
thisForm[cellArray[i]].value*100)/100;
}
thisForm[totalcell].value = subtot;
return subtot;
}
```

从顶部开始，JavaScript 函数 subtotal() 接受一个表单，用于存放答案，以及一组要求相加的数字。

尽管 JavaScript 支持小数，但它不支持任意精度。因此，因为您希望精确到分（如 $9.99），必须将所有内容乘以 100。进行计算，四舍五入结果，然后除以 100。

因此，将 0.01 加到 9.98 上，将所有内容乘以 100：1.0 和 998.0。执行加法：999.0。四舍五入结果：999，然后除以 100：9.99。是的，这看起来会很麻烦。

接下来的几个函数用于对每个部分（住宿、餐饮、交通等）中的列进行总计，垂直总计每天的每个金额。最后，daycalc() 由每个“单元格”调用：

```
function subday (thisForm, totalcell, prefix, maxindex) {
    var cellArray = new Array (maxindex);
    for (var i=0; i < maxindex; i++) {
        cellArray[i] = thisForm[prefix+i].name;
    }
    return subtotal(thisForm, totalcell, cellArray);
}
```

```
function subweek (thisForm, totalcell, prefix, postfix) {
    return subtotal (thisForm, totalcell,
        new Array (prefix+'sun'+postfix, prefix+'mon'+postfix,
            prefix+'tue'+postfix, prefix+'wed'+postfix,
            prefix+'thr'+postfix, prefix+'fri'+postfix,
            prefix+'sat'+postfix));
}
```

```
function daycalc (thisForm, day, code, thisindex, maxindex) {
    subday (thisForm, code+"_"+day+"_sub", code+"_"+day+"_", maxindex);
    subweek (thisForm, code+"_week_sub"+thisindex, code+"_", '_'+thisindex);
    subday (thisForm, code+"_week_sub", code+"_week_sub", maxindex);
    totalcalc (thisForm);
    return true;
}
```

daycalc() 函数是从 HTML 表单中接受用户输入的每个单元格以这种方式调用的：

```
onkeyup="return daycalc(this.form, 'sun', 'lodging', '0', 3)"
```

请记住，屏幕是根据您的费用元数组生成的：

```
array('meals_breakfast', 'meals_lunch', 'meals_dinner', 'meals_tips',
    'meals_entertainment')
```

但是，JavaScript 不知道 PHP、Smarty 或您在后端使用的其他东西，因此您必须明确告诉 JavaScript 您正在使用哪个单元格，以及需要对多少个单元格进行小计。这些分别是 daycalc() 函数调用中的最后两个参数：'0' 是当前行，'3' 表示在 subday 函数中需要垂直小计的最大行数。





## Part III: 真实案例研究

英里的数量（一个例外）必须分别计算。用于里程输入的单元格名为 mitr_sun、mitr_mon 等等。它们的小计（即里程数乘以里程费率）由 mitot_sun、mitot_mon 等等表示。在使用 subweek 计算横向每周总计后，根据当前垂直日期更新总里程数。最后，更新交通部分的总计：

```javascript
function micalc (thisForm, day, travelrate) {
var totalcell = 'mitot_'+day;
var sourcecell = 'mitr_'+day;
// mileage input and mileage total
thisForm[totalcell].value = Math.round(
thisForm[sourcecell].value * 100 * travelrate)/100;
subweek (thisForm, 'mitot_tot', 'mitr_', "");
subweek (thisForm, 'mitot_tot', 'mitot_', "");
// trans total by day
thisForm["trans_"+day+"_sub2"].value = Math.round(
(thisForm[totalcell].value * 100) +
(thisForm["trans_"+day+"_sub"].value * 100))/100;
// grand total of week
subweek (thisForm, "trans_week_sub2", "trans_", "_sub2");
totalcalc (thisForm);
}
```

接下来是一些基本的错误检查：

```javascript
function checkTransInput (thisForm, day) {
if (thisForm["trans_"+day+"_sub"].value > 0 &&
thisForm["mitr_"+day].value == "" ) {
alert ( "Please enter your mileage for "+day);
return false;
}
return true;
}
function checkInputs(thisForm) {
if ( checkTransInput(thisForm, "sun") == false) { return false; }
if ( checkTransInput(thisForm, "mon") == false) { return false; }
if ( checkTransInput(thisForm, "tue") == false) { return false; }
if ( checkTransInput(thisForm, "wed") == false) { return false; }
if ( checkTransInput(thisForm, "thr") == false) { return false; }
if ( checkTransInput(thisForm, "fri") == false) { return false; }
if ( checkTransInput(thisForm, "sat") == false) { return false; }
if ( thisForm["subtotal"].value == 0 ) { alert ("Please enter data.");
return false; } if (thisForm["territory_worked"].value == "") {
alert ("Please enter your territory worked.");
return false; }
return true;
}
```

现在是庞大的 totalcalc() 函数，它确保整个表单被重新计算：

```javascript
//
// No easy way to pass a php array to JS unless we generate it by hand.
//
function totalcalc (thisForm) {
var sectionArray = new Array ( 'lodging', 'meals', 'trans', 'misc' );
var subtotal = 0;
for (var i=0; i < sectionArray.length; i++) {
subtotal = subtotal +
Math.round(thisForm[sectionArray[i]+"_week_sub"].value*100)/100;
}
subtotal = subtotal + Math.round(thisForm["mitot_tot"].value*100)/100;
thisForm["subtotal"].value = subtotal;
var total = subtotal - Math.round(thisForm["cash_advance"].value*100)/100;
total = Math.round(total*100)/100;
if (total >= 0) {
thisForm["totaldueemployee"].value = total;
thisForm["totalduecompany"].value = "";
} else {
thisForm["totaldueemployee"].value = "";
thisForm["totalduecompany"].value = Math.round(total * 100)/100 * (-1);
}
}
```

如果发生错误，recalculate() 函数将附加到“重新计算”按钮。此函数会“触摸”每一行和每一列，以便使屏幕最初被计算。请记住，列由天数表示，行是费用元数组的第一层。虽然 recalculate 函数并非良好编程的典范，但通过蛮力排列而不是依赖另一层循环，它更易于阅读：

```javascript
// don't knock it; looping is less readable
function recalculate (thisForm, mileage) {
daycalc(thisForm, 'sun', 'lodging', '0', 3);
```

周一至周五因简洁已被删除：

```
daycalc(thisForm, 'sat', 'lodging', '0', 3);
daycalc(thisForm, 'sat', 'lodging', '1', 3);
daycalc(thisForm, 'sat', 'lodging', '2', 3);
daycalc(thisForm, 'sun', 'meals', '0', 5);
```

周一至周五因简洁已被删除：

```
daycalc(thisForm, 'sat', 'meals', '0', 5);
daycalc(thisForm, 'sat', 'meals', '1', 5);
daycalc(thisForm, 'sat', 'meals', '2', 5);
daycalc(thisForm, 'sat', 'meals', '3', 5);
daycalc(thisForm, 'sat', 'meals', '4', 5);
daycalc(thisForm, 'sun', 'trans', '0', 5);
```

周一至周五因简洁已被删除：

```
daycalc(thisForm, 'sat', 'trans', '0', 5);
daycalc(thisForm, 'sat', 'trans', '1', 5);
daycalc(thisForm, 'sat', 'trans', '2', 5);
daycalc(thisForm, 'sat', 'trans', '3', 5);
daycalc(thisForm, 'sat', 'trans', '4', 5);
daycalc(thisForm, 'sun', 'misc', '0', 5);
```

周一至周五因简洁已被删除：

```
daycalc(thisForm, 'sat', 'misc', '0', 5);
daycalc(thisForm, 'sat', 'misc', '1', 5);
daycalc(thisForm, 'sat', 'misc', '2', 5);
daycalc(thisForm, 'sat', 'misc', '3', 5);
daycalc(thisForm, 'sat', 'misc', '4', 5);
micalc(thisForm, 'sun', mileage);
```

周一至周五因简洁已被删除：

```
micalc(thisForm, 'sat', mileage);
return (totalcalc(thisForm));
}
function reloadCalc() {
    window.document.forms[0].week_start.value =
    window.document.forms[1].week_start.value // hidden form
    window.document.forms[0].submit(); // hidden form }
    // ->
</SCRIPT>
{/literal}
```

现在已有用于计算行和列总计的代码，每个单元格必须响应 onkeyup 事件并调用 daycalc()。修改 templates/travel-expenses.tpl 中的七个每日输入：

```
<input name="${expenses[idx].code}_sun(${smarty.section.idx2.index)"
       onkeyup="return daycalc(this.form, 'sun', '${expenses[idx].code}",
           '${smarty.section.idx2.index}', '${smarty.section.idx2.total})"
       type="text" size="7" maxsize="17" value="${week->getExpenseAmount(0, $p)}">
```

里程输入函数也需要添加 onkeyup 函数：

```
<input name="mitr_sun" onkeyup="return micalc(this.form, 'sun',
    ${travel_rate})" ...
```

应添加一个“重新计算”按钮。如果一切不尽如人意，它将有助于调试 JavaScript：

```
<br><br>
<center>
<input type="button" value=" Recalculate " onclick="return recalculate
    (this.form, '${travelrate})">
</center>
```

<br><br>
评论：<br><TEXTAREA NAME="comments" COLS=80 ROWS=6>{$week->comments}
</TEXTAREA>
<br><br><center>

主要的“提交”按钮现在通过 onclick 事件运行 checkInputs() 来检查基本输入错误：

```
<input type="submit" name="submit" value=" Submit Report " onclick="
"return checkInputs(this.form);">
```

你差不多完成了。

还有几个未解决的问题。例如，如果更改下拉式开始周，表单将重新加载并自行重新计算，但不幸的是，当表单初始加载时不会触发该事件。

你必须确保在表单加载时运行 JavaScript recalculate() 函数。这是通过 <body> 标签的 onload 事件实现的，但 <body> 标签定义在 header.tpl 中，因此请执行以下操作。在 travel-expenses.php 文件中，修改显示部分：

```
// display
if ($_REQUEST["action"] != "persist_expense") {
 $week->readWeek();
 $smarty->assign_by_ref ("user",
 $user);
 $smarty->assign_by_ref ("week",
 $week);
 $smarty->assign('start_weeks',
 getStartWeeks());
 $smarty->assign('current_start_week',
 getCurrentStartWeek());
 $smarty->assign_by_ref ('expenses',
 $week->getExpensesMetaArray());
 $smarty->assign('travelrate',
 $GLOBALS["expense-mileage-travelrate"]);
 $smarty->assign('formfunc',
 "recalculate(window.document.forms[1]."
 $GLOBALS["expense-mileage-travelrate"].")");
 $smarty->display('travel-expenses.tpl');
 exit();
}
```

你正在将函数分配给变量 formfunc。现在更改 header.tpl 使其相应读取：

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
<html>
<head>
<meta HTTP-EQUIV="content-type" CONTENT="text/html; charset=ISO-8859-1">
<title>{title|default:"no title"}</title>
</head>
<body onload="{$formfunc|default:""}">
<h1>Widget World</h1>
<hr><p>
```

$formfunc Smarty 变量保存了在 HTML 表单加载时执行的 JavaScript 函数名称，$formfunc。onload 表单属性设置为 $formfunc，或者如果 $formfunc 未定义，则设置为空字符串。这样，你可以在加载过程中选择性地重新计算整个电子表格。这样做，daycalc() 只需关注其列、行和总计，而无需在每次按键时重新计算每个单元格。

### 任何其他事项

客户反馈表明，“英里数”似乎未能从屏幕正确持久化。作为元数组的例外，它未在 parse() 函数中得到处理。

到现在你应该知道该怎么做。编写一个测试：

```
function testParsingNbrMiles() {
    $this->session->getDatabaseHandle()->query("delete FROM
    travel_expense_item WHERE emp_id = 1 and
    expense_date >= '1980-01-06' and expense_date
    <= '2001-05-15'");
    $response = array ('mtr_sun' => "1.1",
    'mtr_mon' => "2.2");
    $week = new TravelExpenseWeek (
    array ('emp_id' => "1",
    'week_start' => "1980-01-06",
    'territory_worked' => "Midwest",
    'comments'
    => "comment",
    'cash_advance'
    => "0",
    'mileage_rate'
    => "0.31"),
    $this->session->getDatabaseHandle());
    $week->parse($response);
    $this->assertEquals(true, $week->persist());
    $week = new TravelExpenseWeek (
    array ('emp_id' => "1",
    'week_start' => "1980-01-06",
    'territory_worked' => "Midwest",
    'comments'
    => "comment",
    'cash_advance'
    => "0",
    'mileage_rate'
    => "0.31"),
    $this->session->getDatabaseHandle());
    $week->readByWeek();
    $this->assertEquals(1.1, (float) $week->getExpenseAmount (0,
    'trans_miles_traveled'));
    $this->assertEquals(2.2, (float) $week->getExpenseAmount (1,
    'trans_miles_traveled'));
}
```

通过对 TravelExpenseWeek lib/expense.php 进行相应更改来使其成功：

```
private function createByRequest ($description, $daynum,
    $index, &$request) {
    if (array_key_exists($index, $request) and
    $request[$index] <> null and
```






```php
if ($request[$index] != "") {
array_push (
$this->items,
new TravelExpenseItem (
array ('emp_id' => $this->emp_id,
'expense_date' =>
$this->addDays($this->week_start, $daynum),
'description' => $description,
'amount' => (float) $request[$index]),
$this->dbh));
})
}
```

```php
/**
* This function bridges the gap between the day-based DB and the
* week-based view
*/
public function parse(&$request) {
foreach ($this->getExpensesMetaArray() as $sectionlist) {
for ($i=0; $i < count ($sectionlist['persist']); $i++) {
$daynum = 0;
foreach ($this->getWeekArray() as $day) {
$index = $sectionlist['code'].".".$day.".".$i;
$this->createByRequest (
$sectionlist['persist'][$i], $daynum,
$index, $request);
$daynum++;
}
}
}
// arg, mitr is an exception
$daynum = 0;
foreach ($this->getWeekArray() as $day) {
$this->createByRequest ("trans_miles_traveled", $daynum,
"mitr_".$day, $request);
$daynum++;
}
}
```

一个新的函数 TravelExpenseWeek->createByRequest() 让你免于代码重复，因为它在正常处理和里程计算中都会被调用。

所有测试都通过了，你的客户很满意，屏幕也能正常工作。现在你已完成用户故事 4：“差旅费报告作为电子表格”，如图 19-10 所示。

## Widget 世界

## 差旅费报告

员工姓名：Ed Lecky-Thompson	部门：sales
编号：1	起始周：2004 07 04
工作区域：worked

| | 周日 | 周一 | 周二 | 周三 | 周四 | 周五 | 周六 | 总计 |
|---|---|---|---|---|---|---|---|---|
| 住宿 | | | | | | | | |
| 住宿与酒店 | 1.00 | 2.00 | 3.00 | | | | | 6 |
| 其他 | 2.00 | | | | | | | 2 |
| 小费 | 3.00 | | | | | | | 3 |
| 住宿合计 | 6 | 2 | 3 | 0 | 0 | 0 | 0 | 11 |
| 餐饮 | | | | | | | | |
| 早餐 | 4.00 | | | | | | | 4 |
| 午餐与小吃 | 5.00 | | | | | | | 5 |
| 晚餐 | 6.00 | | | | | | | 6 |
| 小费 | 7.00 | | | | | | | 7 |
| 娱乐 | 8.00 | | | | | | | 8 |
| 餐饮合计 | 30 | 0 | 0 | 0 | 0 | 0 | 0 | 30 |
| 交通 | | | | | | | | |
| 机票 | 9.00 | | | | | | | 9 |
| 汽车租赁 | 10.00 | | | | | | | 10 |
| 车辆维护/汽油 | 11.00 | | | | | | | 11 |
| 当地交通 | 12.00 | | | | | | | 12 |
| 过路费/停车费 | 13.00 | | | | | | | 13 |
| 交通小计 | 55 | 0 | 0 | 0 | 0 | 0 | 0 | 55 |
| 行驶里程数 | 19.00 | | | | | | | 19 |
| 每英里 0.36 的里程费 | 6.84 | 0 | 0 | 0 | 0 | 0 | 0 | 6.84 |
| 交通总计 | 61.84 | 0 | 0 | 0 | 0 | 0 | 0 | 61.84 |
| 杂项 | | | | | | | | |
| 礼品 | 14.00 | | | | | | | 14 |
| 电话与传真 | 15.00 | | | | | | | 15 |
| 办公用品 | 16.00 | | | | | | | 16 |
| 邮费 | 17.00 | | | | | | | 17 |
| 其他 | 18.00 | | | | | | | 18 |
| 杂项合计 | 80 | 0 | 0 | 0 | 0 | 0 | 0 | 80 |

小计 182.84
减去预付现金 20.00
应付员工 162.04
应付公司

重新计算

评论：评论

保存报告

## 图 19-10: 作为电子表格的差旅费报告

现在，不再是“仅仅工作”，你拥有一个经过良好测试的系统和一个能够演化的框架的开端。

你已经了解 PHP、JavaScript 和浏览器如何（以及如何不）交互，每个如何负责其层，以及如何在它们之间移动信息。创建类似电子表格的复杂行为，虽然不容易，但可以用相对较少的代码完成。

接下来你要去哪里？只是机械地完成剩余的用户故事？继续读下去，因为还有另一个重要教训需要学习。

## 模拟对象

有时在测试期间，你必须与一个确定性对象交互，但出于各种原因，你在测试环境中无法访问它。例如，考虑以下情况：

- 实际对象是非确定性的，例如实时股票或天气数据馈送。
- 实际对象对于你的测试套件来说太慢，例如负载过高的事务生产数据库。
- 你需要测试异常情况，例如入侵警报或系统宕机。
- 实际对象不存在。这可以从无法访问所需对象到必要的对象内部功能的任何事情。

基本上，模拟对象是一个伪装出足够功能或所需功能的对象，以便你能够完全测试你的系统。

例如，如果你想测试会话超时、错误或恶意破解，你可能会导入 mock-widgetsession.php，它包含以下内容：

```
class MockWidgetSession extends WidgetSession {
    public function getUserObject() {
        return new WidgetUser(
            array (
                'id' => 1,
                'username' => 'ed',
                'md5_pw' => '827ccb0eea8a706c4c34a16891f84e7b',
                'first_name' => "Ed",
                'last_name' => "Lecky-Thompson",
                'email' => "ed@lecky-thompson.com",
                'role' => "s",
                'department' => "sales"));
    }
}
```

不论编码细节，这个 MockWidgetSession 示例将使你的测试环境能够出于任何你需要的原因模拟登录。

Smarty 也可以用于模拟 HTML 屏幕。除了将 HTML 显示到屏幕上，你还可以将 HTML 保存在变量中，并随意处理。

例如，用户故事 6 需要销售经理通知，因此你只需在保存联系人时向经理发送电子邮件。听起来很简单，但你面临着希望在多大程度上进行测试的问题，特别是他们希望电子邮件内容包含输入屏幕的 HTML。

获取屏幕 HTML 不是问题。基本上，你必须测试浏览器输出，这很好，因为直到现在你还没有测试过浏览器看到的内容。为了端到端的完整性，以下测试将使用正则表达式引用 HTML 输出：

```
function testContactEmail () {
    $u = new WidgetUser(
        array ('id' => 1,
            'username' => "ed",
            'first_name' => "Ed",
            'last_name' => "Lecky-Thompson",
            'email' => "ed@lecky-thompson.com",
            'role' => "s",
            'department' => "sales"));
    $cv = new ContactVisit (
        array ('emp_id' => "1",
            'week_start' => "1980-01-01",
            'company_name' => "test one",
            'contact_name' => "Big One",
            'city' => "Columbus",
            'state' => "OH",
            'accomplishments' => "phone call",
            'followup' => "",
            'literature_request' => ""));
    $c = new Contact (
        array ("emp_id" => "1",
            "week_start" => "1980-01-01",
            "shop_calls" => 2,
            "distributor_calls" => 3,
            "engineer_calls" => 4,
            "mileage" => 50,
            "territory_worked" => "Central Ohio",
            "territory_comments" => "Buckeyes are great. "),
        $this->_session->getDatabaseHandle()));
}
```

```
list ($email, $from, $subject, $message, $headers) =
    generateContactEmail($u, $c, array ($cv), false);
```

```
// test screen capture, requires 7bit ascii encoding (read: none)
```

```
$this->assertEquals(1, preg_match ("/Employee Name.........Ed Lecky-Thompson/", $message), "employee name");
$this->assertEquals(1, preg_match("/company_name_0........................test one/", $message), "company name");
$this->assertEquals(1, preg_match ("/shop_calls........................./", $message), "shop calls");
$this->assertEquals(1, preg_match ("/To: ed@lecky-thompson.com/", $headers), "email");
```

```
// test base64 encoding
list ($email_from, $subject, $message, $headers) =
           generateContactEmail($u, $c, array ($cv));
```

```
$this->assertEquals(0, preg_match ("/Employee Name................Ed Lecky-Thompson/", $message), "employee name");
$this->assertEquals(1, preg_match ("/To: ed@lecky-thompson.com/", $headers), "email");
```

如果你要手动输入上述代码，请确保不要在正则表达式中间换行；它们应该在一行中输入。

generateContactEmail() 函数旨在返回 PHP mail() 函数所需的内容：mail($email_address, $subject, $message, $headers);。

在这个示例中，你正在测试浏览器看到的内容。你不是测试 100% 的 HTML 输出，而是确保表单包含你期望的信息。因此，简单的正则表达式

```
"/Employee Name............Ed Lecky-Thompson/"
```

将完美匹配以下生成的 HTML：

```
<tr><td><b>Employee Name:</b></td><td>Ed Lecky-Thompson</td>
<td><b>Department:</b></td><td>sales</td></tr>
```

由于 base64 编码人类无法读取，base64 编码的测试仅检查电子邮件标题中是否存在电子邮件地址，而不是员工姓名，因为员工姓名（在消息中且经过 base64 编码）通常无法读取。

以下是可能放置在你的 lib/common-functions.php 中的函数：

```
function mimeifyContent ($content, $mime_boundary,
           $filename, $flagBase64=true) {
$message = "";
$message .= " \r\n";
$message .= "--".$mime_boundary."\r\n";
$message .= "Content-Type: text/html;\r\n";
$message .= "name=\"".$filename.".html\"\r\n\r\n";
// default is 7bit ascii

if ($flagBase64) {
    $message .= "Content-Transfer-Encoding: base64\r\n";
}

$message .= "Content-Disposition: attachment;\r\n";
$message .= " filename=\"".$filename.".html\"\r\n";
$message .= "\r\n";
if ($flagBase64) {     $message .= base64_encode($content);
} else {
    $message .= $content;
}
```




```
$message .= "\r\n";
return ($message);
}
function generateContactEmail(&$user, &$contact,
$contactVisits, $flagBase64=true) {
    global $GLOBALS;
    require_once ($GLOBALS["smarty-path"].'Smarty.class.php');
    $smarty = new Smarty;
    $smarty->assign_by_ref ("user", $user);
    $smarty->assign_by_ref ("contact", $contact);
    $smarty->assign_by_ref ("contactVisits", $contactVisits);
    $smarty->assign('start_weeks', getStartWeeks());
    $smarty->assign('current_start_week', $contact->week_start);
    $smarty->assign("max_weekly_contacts", $GLOBALS["max-weekly-contacts"]);
    $email_body = @$smarty->fetch('customer-contacts.tpl');
    $headers = "";
    $headers .= "From: ".$GLOBALS["email-from"]."\n";
    $headers .= "To: ".$user->email."\n";
    if (strlen ($GLOBALS["email-contact-cc"]) > 0)
    $headers .= "Cc: ";
    $headers .= $GLOBALS["email-contact-cc"];
    $headers .= "\n";
    if (strlen ($GLOBALS["email-contact-bcc"]) > 0)
    $headers .= "Bcc: ".$GLOBALS["email-contact-bcc"]."\n";
    $mime_boundary = "<<<===".md5(time())."";
    $headers .= "MIME-Version: 1.0\r\n";
    $headers .= "Content-Type: multipart/mixed;\r\n";
    $headers .= " boundary=\"".$mime_boundary."\"";
    $message = "";
    $message .= "This is a multi-part message in MIME format.\r\n";
    $message .= "\r\n";
    $message .= "--".$mime_boundary."\n";
    $message .= "Content-Type: text/plain; charset=\"iso-8859-1\"\r\n";
    $message .= "Content-Transfer-Encoding: 7bit\r\n";
    $message .= "\n";
    $message .= $GLOBALS["email-contact-message"]."\n";
    $nextEnding = "\r\n";
    $message.=mimeifyContent($email_body,$mime_boundary,
        "customer-contact", $flagBase64);
    $message.="--".$mime_boundary."".$nextEnding;
    $subject = $user->emp_id. " ".$user->last_name. " : ".$user->email_subject;
    return array ($user->email, $subject, $message, $headers);
}
```

Note two things here. One, you’re calling $smarty->fetch() instead of $smarty->display(). The fetch function places the HTML output into a variable, rather than to the screen, as does the display function.

Two, for technical reasons, it’s safer to base64-encode HTML output if there is any chance of it using non-7-bit ASCII (e.g., if you’re using Unicode or non-English characters). However, base64-encoding the HTML in the e-mail makes it practically untestable, which is why the $flagBase64 argument exists.

If this function contained the function to physically mail the e-mail instead of simply creating the content, then you would most certainly create and utilize a mock object that simulated the e-mailing API and didn’t base64-encode the content.

## Summary

With this chapter, the Widget World software development effort is concluding. You would be correct in pointing out that not all the stories and features have been completed, but we have no desire to be historical revisionists of this real-world example or to force you through another 100 redundant pages of the same procedure. By now, you have the tools and know-how to complete it yourself.

Testing is one aspect of software development that has historically been considered little more than “busywork,” but you’ve experienced how test-driven development can help you not only develop your code, but also find bugs and continue to test even when you’re working on distant parts of the system.

Refactoring is not just a technical term for “code cleanup.” Ideally, it shouldn’t even be considered a distinct task from software development. Refactoring is simply a coding priority, much in the same way that developing system objects is a coding priority too. Plus, you’ve seen how constant refactoring can help to develop a complex framework without the need for excessive analysis and unused features.

These are just a few of the principles of extreme programming (XP), which is designed to reduce complexity in order to sustain development by keeping your code base nimble and flexible. Although not every project is a candidate for the complete methodology of XP, that does not mean that your methodology, whether it’s spiral, waterfall, or RUP, cannot benefit from some of the practices such as testing and constant refactoring. Additionally, because of a lack of peer programmers (for you, the reader), as well as space and focus on code, many aspects of XP haven’t formally been examined, such as planning for a release and measuring the project metrics. XP is quite a disciplined approach, and you should learn more about it, because its strengths and rewards are solidly concerned with the subtleties of software development as a team.

Of course, no matter how methodical and diligent your approach during the build process, you can’t skip the most important part of any project — quality assurance. That’s something you’ll meet in Chapter 20, as you discover what steps you can take post-build to ensure that your project features the quality levels your clients have a right to expect.

## Quality Assurance and Testing

The Widget World sales force automation toolkit site is looking pretty good. You’re on schedule and on budget, and the client is, thus far, happy with the beta version running on your development environment and staging server. Furthermore, by employing rigorous unit testing throughout the build process in Chapter 19, you can be sure that the individual components that comprise the application all function more or less correctly independently; hence, there shouldn’t be any deep-rooted problems in the code itself.

At this point, you might well be tempted to let your guard down. In fact, you have now reached one of the most critical stages in the entire project. The application is more or less complete, and the client is urging you to let them use it. You must resist, however.

Quality assurance (QA) is a term you might be familiar with. Indeed, it is borrowed from traditional manufacturing and engineering processes, and is the kind of procedure you expect to be carried out on your new DVD player or luxury family sedan. Why would you not, therefore, want to apply it to something as complex and crucial as your application?

This chapter introduces you to the QA process in large-scale PHP projects. You’ll learn why quality assurance is of great importance, and what it means in terms of your expectations and those of your client. You’ll also learn about the kinds of testing you must do in order to be able to confidently give your application a seal of approval, and how to get your team on board to help you when things go wrong.

## Introduction to QA

Somewhat understandably, expectations regarding the reliability of the Web and the Internet at large are still pretty low among its everyday users. Chances are good that you’ve had a client or two call you recently to say that their e-mail was down, and so they might not have received anything you’ve sent. Maybe you’ve tried to order something online recently, only to be kicked off while your credit card was being processed. Or maybe your friend’s ISP has been down for a couple of days, and no one in tech support seems to be able to tell him when he’ll be back online again.

## Part III: A Real-World Case Study

Scenarios like this are all too common. What is truly shocking is that the parties involved typically shrug their shoulders and accept it. Your clients didn’t sound surprised when they told you that e-mail was down. You probably didn’t even curse under your breath when your online order went wrong. And your friend likely shrugged his shoulders and got out his 3G data card.

This is a phenomenon still more or less unique to the Internet. If you bought a new car and it stalled on the highway just weeks later, you’d be pretty mad at your dealer. If you ordered a mocha latte before work and your barista gave you a cappuccino， you’d be mad and insist on a new cup. And if your DVD player died soon after purchase, you’d take it back.

There are two reasons why people don’t get upset when the Internet doesn’t work right. First, most people reason that there’s something innately complicated about the Internet, and that it must go wrong as a result. This is a non sequitur, of course. Yes, the Internet is complicated, but so is your DVD player. In practice, too, the underlying infrastructure (that is, the servers, routers, and so forth) of the Internet is pretty much rock solid. It’s bad programmers who cause things to break with the bad code they write, and the poor decisions they make when developing.

The second and more crucial reason applies to those who have had previous experience with Internet application developers. Frequently, their past experiences with these agencies and individuals have been such that their expectations with present vendors have hit rock bottom. In fact, and unfortunately, there are few other industries in which such an explosion of dangerously under-skilled labor has occurred in the past few years. This has manifested itself in both appalling freelance Web “professionals” (who can barely produce valid XHTML, let alone high-quality back-end code), and some truly awful digital agencies (that revel in producing self-indulgent “award-winning” creative work without so much as a nod to how well it works under the hood). Excellence is the exception rather than the rule. In effect, there are literally thousands of vendors who talk the talk, but don’t walk the walk.

The more cynical inference from this observation is that because your client’s expectations will be low, you should aim low, too, because they’re not likely to get mad at you if things go wrong. This approach, however, is not only cynical, it is also not commercially sensible.

## Why You Should Aim High

Aiming to have a high-quality product before handing over to the client is not just about keeping the client happy. It’s about maintaining your own sanity, too.

It is inevitable that your assembled system will (initially, at least) be functionally defective in some way. This does not necessarily mean that it will malfunction in the traditional sense. It could be slow when real-world data is applied, or have some unforeseen business logic error. A systematic approach to QA prior to handover ensures the following:

- Developer time, and hence cost spent on resolving defects, is minimized through a thorough, structured approach.
- The team’s timely transition onto other projects can be closely adhered to.
- Problems encountered during deployment can be isolated as being unrelated to the application itself.





# Chapter 20: Quality Assurance and Testing

不过，尽管如此，请对比以下两种态度：

- [ ] “客户的期望较低，因此我可以交付不足而无需担心报复。”
- [ ] “客户的期望较低，因此当我交付超预期时，我会被视为卓越。”

毫无疑问，被视为卓越会迅速让你脱颖而出。客户与其他供应商的过往经验可能平淡无奇，客户的期望因此可能较低，但请记住，客户没有再次使用那些其他供应商。

追求卓越意味着努力获得高质量。努力与实现之间的区别始于首先了解什么是质量。

### 质量是什么？

关于软件应用中什么构成质量，存在一些混淆。让我们回到家庭轿车的类比。当汽车记者评论高质量汽车时，他们并不总是明确指可靠性或性能本身，而是指一些不那么具体和可量化的因素，例如以下几点：

- [ ] 内饰的耐用性
- [ ] 使用昂贵、坚固的材料（例如拉丝铬）
- [ ] 纯粹的美学细节（例如蓝色背光显示屏）
- [ ] 驾驶员关上车门时发出的坚实响亮的声音

在这里，质量与其说是单一的决定性因素，甚至是任何积极的东西，不如说是所有可能出错但未出错领域的总和。

这种观点在车展上首次评审或检验汽车时常采用的方法中得到了体现。反复激活杯架机制、按动开关、抚摸内饰——这些是用于评估质量的快速粗糙的试金石测试。然而，这些测试中的任何一项都无法告诉你有关汽车操控、油耗、可靠性或年度折旧的任何信息。那么，它们为什么重要呢？

事实是，虽然你不能以貌取人，但你通常可以通过内饰来评判一辆车。拥有顺滑弹出的杯架、手感良好的铬制开关以及无缝机制的汽车，几乎可以肯定未来也会享有卓越的可靠性。那些以这些外观特征自豪的最高品质品牌（例如 BMW、Audi 或 Mercedes）同样始终被评为道路上最可靠的车辆之一。

这一原则同样适用于你的 Web 应用程序。质量不仅仅在于网站是否正常运行并按照功能规格说明执行功能。更重要的是细节；而且，不可避免地，当表面的小细节都正确时，底层的大事情也都是正确的。

车辆就谈到这里！是什么让 Web 应用程序高质量，以及如何衡量它？

### 可衡量和可量化的质量

在对你的应用程序进行 QA 时，必须评估几个核心质量领域。不可避免地，你分配给每个领域的重要性很大程度上取决于你的产品及其目标受众的性质。

### 功能合规性

在最简单和最基本的层面上，你的应用程序应提供与项目原始功能规格说明中详细说明的功能完全一致的功能。

当然，这不仅仅是确保没有 PHP 警告或错误出现。你的应用程序的行为必须在一套详尽的测试条件下正确。这包括以下内容：

- 当按下更新按钮时，数据库会实际更新。
- 当向新用户发送欢迎电子邮件时，发送的电子邮件是正确的。
- 当用户进行搜索时，返回的数据是数据库和指定搜索条件的准确反映。

这种合规性可能显而易见，但通常 QA 计划中最明显的点也会被忽略。

### 现实世界容忍度

现实世界容忍度（RWT）意味着你的应用程序应能处理比开发期间可能运行的环境和条件更接近其实际生产运行环境的环境和条件。

这不仅仅是指系统上的用户数量或数据量。它还指当用户（例如）没有按预期格式输入数据时，系统能够妥善处理的要求。在这种情况下，正确的行为当然是向用户提供错误消息。模拟此类条件非常重要，因为用户不仅不时会做错事，他们提供的数据也不时会是错误的，这一点几乎不可避免。

### 故障时的优雅处理

开发时，很容易不考虑每一种可能的场景。例如，某些场景可能看起来不太可能。然而，应抵制这种诱惑。例如，比用户信用卡处理失败更糟糕的事情，就是未能通知用户其信用卡处理失败。

在可能发生故障的任何阶段，无论其可能性多么小，你的应用程序都必须优雅地处理。例如，考虑一个无法访问的数据库服务器。显然，这是一种不希望出现的情况，在这种情况下，应用程序将无法正常运行。幸运的是，这是系统管理员可以正确解决的问题。但是，如果没有考虑到这一点，你的应用程序可能只是在搜索时返回零个搜索结果，或者告诉人们他们的登录不正确。这两种结果都源于你的应用程序没有考虑到数据库完全不可访问的情况，用户将因此被严重误导。提供一个简单的“对不起，网站目前不可用”页面提供了一个明显且即时的解决方案。

### 负载容忍度

在功能测试期间，你的应用程序将面临的总受众可能并不比你的开发团队大多少——可能不到十人同时使用系统。当然，在实际中，你的受众肯定会比这大得多，要求支持 100、1000，甚至可能 10000 个同时用户。

你将从技术规格说明中了解实际数字或估计值，并起草了相应的架构。然而，在纸上可行的方法不一定能在现实中奏效。当然，这至关重要。

如果应用程序在高负载下的响应是不可接受的响应时间，或者更糟的是彻底失败，那么显然客户不会接受该产品是令人满意的。

### 可用性

当今界面架构中最新的流行术语是可用性。由雅各布·尼尔森（Jakob Nielsen）等领先专家倡导（请参阅他的优秀网站 www.useit.com），它是指用户界面固有的直观性和逻辑性。它不仅适用于 Web，还适用于传统的客户端软件应用程序，甚至洗衣机的控制面板。

它通常是通过新用户执行某些任务的难易程度和速度来衡量的。这些任务表述为目标，并且不提供有关如何完成的具体指导。例如，Web 邮件应用程序的用户可能被要求向 foo@example.com 撰写一封新消息。但是，他们不会被引导去点击屏幕左上角的撰写按钮，或在收件人框中输入 foo@example.com，等等。

观察用户执行这些任务的有效性是可用性测试的基石，将在稍后讨论。

### 表面修饰（外观）

可用性之后的一步是产品的表面修饰（或外观）。还记得前面关于轿车中铬制开关和杯架的类比吗？你的应用程序的表面修饰是直接的等价物，由于这是用户对你的应用程序的第一次真实体验，它能深刻洞察应用程序的底层质量。

什么是表面修饰？考虑本书中快速粗糙的示例，不包括较大的 Widget World 项目范围。每个示例都是为了演示一个概念而构建的，别无其他目的。因此，它们看起来和感觉上从来都不算好——也许有点粗糙。然而，这从来都不重要，因为它们只是在演示技术概念。当然，成品永远不应该采用这种方法。

驾驶舱中的铬制开关就是你分页中渲染得当的“上一页”和“下一页”按钮。杯架的顺滑弹出机制就是你在应用程序中选择每个部分时导航刷新更新的方式。这就是你的应用程序的表面修饰（或外观），尽管实现不佳也不是致命问题，但它可以对你的应用程序的整体质量有很多说明。

许多软件架构师和工程师在设计用户界面美学方面可能不如你想象的那么擅长。作为你自己的项目管理方法论的一部分，确保



让一位拥有界面架构技能的资深高级设计师随时待命，以确保您成品的精致度始终保持完好无损。

在项目后期提出小变更时，很容易产生偷工减料、让软件工程师负责新功能的想法。只有在您已建立坚如磐石的样式指南（如第 16 章所述）的情况下，才可以这样做。否则，您可能会发现，在原本美观的界面上出现了一个灰色的矩形提交按钮，从而破坏了您精心打造的应用程序。

## 测试

不言而喻，确保先前提到的核心品质贯穿您的项目，最有效的方法就是测试、测试、再测试。

不过，测试可以采取多种形式。前面提到的每种品质都与一种或多种测试方法论相关联。让我们逐一查看。

## 单元测试

好消息是，您以前至少做过一次——也就是说，如果您详细遵循了第 13 章，那么您确实做过，在那里您会作为 Widget World 应用程序构建的一部分接触到单元测试。

单元编程和测试框架的概念在本书前面部分已经涉及，包括了为什么在大型项目中采用这些做法是良好实践的理论。在第 13 章中，您在构建应用程序时将该理论付诸实践。

不过，让我们简要回顾一下。单元驱动编程涉及构建您的应用程序，将其整合为整齐打包的、独立的组件，这些组件具有接口，可根据给定的一组数据产生人类可预测的结果。然后为每个组件构建一个测试框架，该框架根据一系列理论输入断言一系列人类确定的理论结果，并通过将这些理论结果与该组件方法执行得出的实际结果进行比较来测试这些断言的有效性。

这些框架将成为黑盒，使您能够在组件演进过程中持续测试其功能。因此，您可以在项目早期构建此类框架，并随着组件的演进和变得更加复杂，对其进行回归测试，以确保它们仍然产生预期的结果。简而言之，您可以测试以确保您的更改没有破坏以前能够正常工作的东西！

单元测试会捕获编码错误。此类错误通常是程序员的疏忽。单元测试不会捕获任何其他形式的问题；因此，它只是确保功能合规性高质量所需测试的一部分。

例如，考虑一个 Web 邮件应用程序。您可能构建了一个用户类、一个邮箱类和一个消息类。这三个类可能都能通过您的单元测试。但是，考虑正在查看的消息上的回复按钮。它将实例化一个新消息对象，并将原始消息对象的发送者属性复制到消息对象的收件人对象。此操作可能不会由任何类中的任何特定方法执行，因此可能不是任何单元测试的对象。如果在单击回复时电子邮件的收件人未正确设置，那么这显然是一个必须解决的功能错误。然而，这并非正在执行的单元测试框架会在任何三个测试中捕获的问题。因此，您可以看出，单元测试不是功能合规性的终极测试。实际上，它只测试模型-视图-控制器（MVC）设计模式中的“模型”。

## 功能测试

功能测试是确保您项目功能合规性质量的另一半。它通常会在给予项目原始功能规范应有尊重的前提下进行。

正式化功能测试有多种可能的方法。最重要的遵循规则是，它实际上首先被正式化。在大型项目中，仅仅让开发人员对关键功能进行快速走查是不够的。

值得考虑的一种方法是组建一个测试人员团队，理想情况下由比较聪明且典型的目标受众人员组成，并向他们发放正式的待完成文档。考虑为每个测试团队成员分配网站的特定区域进行测试。

## 功能测试文档

考虑 Web 邮件示例，您可以制定一个看起来如表 20-1 所示的表格。作为项目经理，您应完成“动作”和“预期结果”列。您的测试团队将完成“实际结果”列，然后您可以使用该列将每个测试评为 FAIL 或 PASS。

表 20-1: Web 邮件示例的功能测试表单

| 动作 | 预期结果 | 实际结果 | 得分 |
|---|---|---|---|
| 通过单击导航上的登录链接打开登录页面。 | 显示登录页面，其中包含用户名和密码文本框以及提交按钮。 | 预期结果 | PASS |
| 输入登录名 joet1301f 和密码 ixrsh0z1 并单击登录。 | 表单提交并重新加载页面，指出您的登录成功。五秒后，您将自动转至主页。 | 预期结果 | PASS |
| 单击导航上的收件箱链接。 | 您将进入收件箱。您将看到列出的若干条消息。对于每条消息，应列出主题、接收日期和发件人。将显示此邮箱包含的总页数。如果存在多页，将显示上一页和下一页按钮 | 预期结果，但尽管显示第 1 页 / 共 18 页，却未显示下一页按钮 | FAIL |

当然，跟进任何 FAIL 标记至关重要。作为项目经理，您应首先亲自再次检查任何失败。如果发现任何失败是真实的，可以将其录入故障管理系统，此类系统将在本章后面讨论。

当然，您在每份功能测试文档中列出的动作，将以一种或另一种方式直接源自功能规范。本质上，您正在制定用户旅程。您的测试团队需要按顺序执行这些动作。例如，显然，任何登录都必须在依赖用户已登录的任何活动之前进行。请建议您的测试用户，如果他们发现因阻塞性失败而无法执行后续动作，应相应地在文档上标记并继续。

## 功能测试注意事项

您必须确保测试覆盖用户旅程的每个分支，至少要达到可以合理确信系统在功能上正确的程度。每次做出决策时都会出现一个分支。例如，如果登录您系统的用户有三种类型（例如，普通用户、超级用户和管理员），则需要有三个初始分支。如果对于每种登录，用户可以选择查看三个邮箱中的一个，那么每个初始分支将创建额外的三个分支。

使用某种树形图绘制所有可能的用户旅程可能会有所帮助，然后您可以将其转化为前面的测试文档。

这种功能测试方法并非万无一失，但远比仅仅要求开发团队“彻底测试”要有效得多。生成的文档还构成一种正式证明文件，可作为文档证明提交给客户，证明系统在交付前已经过彻底测试。

## 负载测试

负载测试的一般原则是确定您的应用程序在崩溃前能够承受哪种极端环境条件。

传统观点认为，只需确定应用程序能否支持技术规范中规定的并发用户数，以及在该使用水平下的响应时间是否在合理范围内，就足够了。

更进取的方法是不断加大负载直到系统崩溃。客户更希望听到“您的网站在当前基础设施下可支持 530 名并发用户”，而不是简单的“是的，您的网站支持您需要的 500 名并发用户。”得知系统只能再支持 30 名额外用户可能不是客户想听到的消息，但客户越早知道，比越晚知道要好。

负载测试的原则在附录 C“调优 PHP 性能”中有详细说明。





## 可用性测试

请回顾一下表 20-1 中所示的功能测试工作表示例。你给测试人员分配了诸如“点击导航栏上的登录链接以打开登录页面”之类的任务。

在可用性测试中，类似的任务会简单地表述为“登录系统”。当然，目的截然不同，因此表述方式也截然不同。可用性测试不关心事情是否能正常工作。这一点是在功能测试期间确定的。相反，它询问用户完成相关任务的效率或难易程度。

在软件测试中，这或许是独一无二的，可用性测试很少直接向测试对象提问。相反，观察才是关键。

例如，当被指示“登录系统”时，用户将被观察（无论是当面还是远程）。引起关注的是用户在完成（或未完成）所需任务过程中的动作或行为（这部分行为只能部分用数字量化）。

例如，你可能想尝试回答以下问题：

- 用户在哪里物理性地寻找登录链接？它在你放置的位置，还是其他位置？（请注意，用户屏幕上光标的位置往往是用户正在查看位置的线索。）

- 登录屏幕加载到用户开始输入用户名之间有什么样的延迟？

- 用户在找到登录页面之前，是否错误地访问了任何其他页面？

这些问题的答案将让你很好地了解应用程序的可用性。当然，将此类研究量化为数字可能很困难。

可用性测试及其可提供的有用指标本身就是一个巨大的主题，超出了本章的范围。关于可用方法的更多信息，可以在 Jakob Nielsen 运营的出色网站 www.useit.com 上找到。

## 故障跟踪

使用先前描述的技术进行的测试不可避免地会导致观察结果，例如：

- 功能测试表明，回复现有消息时，收件人地址未被正确复制到新消息中。
- 负载测试表明，系统对 530 个并发会话发出的请求的响应不够及时。
- 可用性测试表明，人们期望邮箱视图中的“上一页”和“下一页”按钮位于页面顶部，而不是底部。

没有相应行动点汇总，这些观察结果基本上无用。对于先前概述的问题，你可以提出以下行动点：

- 确保回复消息时，收件人自动设置为被回复消息的发件人。
- 当有 530 个会话处于活动状态时，将额外用户重定向到“服务不可用”页面，说明服务器暂时无法处理他们的请求。
- 将邮箱视图中的“上一页”和“下一页”按钮移动到页面顶部。

这些行动对小型项目来说都足够简单，但在大型项目中，你可能有数百个甚至数千个行动点（例如需要修复的错误和用于微调的调整）。你如何跟踪它们？

当然，可以使用任何毫无防备地被抛入项目管理世界的办公室职员的著名默认解决方案——Microsoft Excel。它确实为跟踪项目故障报告及其状态提供了一种快速且简便的机制，形式是一个由所有参与项目的人定期更新的彩色编码表。

然而，其局限性很快就会变得明显。没有 Web 访问意味着用户必须身处该电子表格驻留的本地文件服务器所在的办公室。没有多用户访问意味着一次只能有一个用户更新电子表格。要求使用者频繁且定期地检查和更新（当需要他们关注的问题出现时，没有通知的前景）意味着问题往往得不到检查，即使是紧急问题。

这时，专门构建的解决方案可以提供一个有效的替代方案。

## 使用 Mantis 进行有效的故障管理

本节将介绍一种名为 Mantis 的故障管理系统，该系统目前可从 www.mantisbt.org 免费获取。

Mantis 的目的是使你能够有效地跟踪项目中的所有故障和缺陷，将它们分配给开发人员解决，并在适当的时候使开发人员能够对它们发表评论。

Mantis 是一个用 PHP（还能用什么？）编写的 Web 应用程序，通常作为外联网运行。是否将其开放给客户访问，完全由你决定。在处理较小的客户时，这通常很有好处，因为它让他们能够感觉自己是 QA 流程的一部分。Mantis 支持多用户，每个用户都有自己的访问级别和权限，因此你可以为自己和开发人员提供不同的访问权限。

当然，存在许多其他故障管理系统。本次讨论专门考察 Mantis，因为它免费可用、易于使用，并且用 PHP 编写。这意味着，如果需要，你理论上可以修改和扩展它以更好地满足你的需求。

### 安装 Mantis

从其 Web 站点下载 Mantis 安装存档，以通常的方式解压缩：

```
tar -xzvf mantis-1.1.2.tar.gz
```

此操作将创建一个名为 mantis-1.1.2 的目录，其中包含 Mantis 的所有源文件和配置文件。你应该在 Apache 的 httpd.conf 配置文件中配置一个虚拟主机，将其指向此位置，如下所示：

```
<VirtualHost 192.168.168.2>
    ServerAdmin you@example.com
    ServerName mantis.example.com
    CustomLog /home/production/logfile_mantis common
    ErrorLog /home/production/errlog_mantis
    DocumentRoot /home/production/public_html/mantis-1.1.2
</VirtualHost>
```

如果你使用的 Web 服务器不是 Apache，则应按照你惯用的方式设置一个虚拟服务器以支持 Mantis。

### 首次配置 Mantis

Mantis 的早期版本仅支持 MySQL。正如你在这本书中读到的，作者通常青睐 PostgreSQL，因为它提供了一个真正免费、开源且功能更丰富的替代方案，更接近 Oracle 等商业企业级对应物，代价是性能有一定损失，当然，与商业软件相比，其支持范围也相对有限。

幸运的是，在 Mantis 的较新版本中，PostgreSQL 得到了同等良好的支持。事实上，正是使用了数据库抽象层（正如在第 6 节中所倡导的那种），才使得 Mantis 开发人员顺应大众需求，原生支持 PostgreSQL。

打开 Web 浏览器，指向你在上一节中设置的虚拟主机。你应该会看到类似图 20-1 所示的屏幕——一个“一次性运行”的安装屏幕。请注意，出于安全考虑，浏览器窗口中的 URL 已部分模糊。

## 第三部分：现实世界案例研究

![](img/a1b732997d9cb194dceec0570dc79710_550_0.png)

图 20-1：Mantis 安装

从图 20-1 可以看出，Mantis 想要知道你的数据库详细信息。在继续之前，你必须在 PostgreSQL 中创建一个空数据库，以及一个 Mantis 可以使用的用户（带密码）。

从你的 shell 中，使用以下语法来完成此操作：

```
root@gdmsrv02:~# /usr/local/pgsql/bin/createuser -P mantis
Enter password for new role:
Enter it again:
Shall the new role be a superuser? (y/n) n
Shall the new role be allowed to create databases? (y/n) n
Shall the new role be allowed to create more new roles? (y/n) n
```

不要忘记记下你选择的密码。接下来，按以下方式创建空数据库：

```
root@dmsrv02:~# /usr/local/pgsql/bin/createdb mantis
```

现在，你可以将 Mantis 安装屏幕（希望仍在你的 Web 浏览器中打开）指向你刚刚创建的数据库，然后单击“安装/升级数据库”。

安装屏幕应该会告诉你一切成功，并提供一个链接让你“继续”首次登录 Mantis。

### 以管理员身份登录

启动 Web 浏览器，将其指向你先前创建的虚拟主机。你应该会看到类似图 20-2 所示的登录屏幕。同样，出于安全考虑，完整 URL 已被隐去。

![](img/a1b732997d9cb194dceec0570dc79710_551_0.png)

图 20-2：登录消息





## 第三部分：真实案例研究

现在，以`administrator`身份登录。默认情况下，密码已在PostgreSQL数据库生成脚本中设置为`administrator`。

登录后，你首先应该锁定你的Mantis安装。最好的方法是创建另一个不名为`administrator`的账户，使用更安全的密码来进行日常管理。如果你可以通过公共互联网访问你的Mantis安装，这一点尤其重要。

你可能还会注意到，Mantis安装在登录时提示你从安装中删除`admin`目录。你应该这样做。你不再需要该文件夹，因此要么删除它，要么将其从Web服务器的文档根目录中完全移除。一旦移除，该烦人的提示消息将相应消失。

### 创建和编辑用户

每个需要访问Mantis的人（即你自己、你的开发团队，以及可能的客户代表）都需要一个用户账户。

要创建账户，以管理员身份登录后点击Manage链接。“Manage Users”默认被选中，相应地，你将看到系统上的用户账户列表。创建新账户只需点击Create New Account即可。不要忘记将访问级别设置为适当的级别。任何唯一任务是报告缺陷或错误的人可以设置为reporter，而你希望你自己的账户是administrator。

创建完所有必要的用户账户（包括至少一个具有管理员权限的账户）后，你可以完全删除administrator账户。

创建用户后，你可以通过点击其用户名来修改该用户账户的更多属性。图20-3展示了Mantis中典型的用户编辑会话。

![](img/a1b732997d9cb194dceec0570dc79710_553_0.png)

图20-3：Mantis中典型的用户编辑会话

### 将用户添加到项目

关键的是，编辑用户屏幕不仅可用于编辑用户详细信息，还可用于将该用户添加到项目。默认情况下，用户无法访问任何项目，这意味着即使他或她具有reporter身份，该用户也无法报告任何错误。

要将你正在编辑的用户添加到项目，请选择相关项目（如果你是第一次使用Mantis，你目前还没有项目）并点击Add。如果项目被标记为public，你可以跳过此步骤，因为所有用户都将有权访问。这很少是可取的，特别是当你有客户使用系统时。

请注意，创建账户时，你的新用户会自动收到一封包含其用户名和密码以及访问此Mantis安装URL的电子邮件。如果此行为不可取，你可以在几分钟前编辑的Mantis配置文件中禁用它。

### 创建新项目

Mantis支持的项目数量没有限制。

要创建新项目，请选择屏幕顶部附近的Manage Projects链接。将显示与Manage Users中所示类似的视图，显示所有当前项目。要创建新项目，请点击Create New Project。

最初，系统会要求你指定项目名称、status（仅供你自己参考的任意标志）、view status（出于之前讨论的原因应设置为private）、描述以及上传文件路径。上传文件路径是系统中附加到已提交错误的任何二进制文件（例如正在复制的错误的屏幕截图）的存储位置。这必须可由Web服务器写入，你可能需要通过手动更改服务器上该特定文件夹的权限来实现这一点。

### 设置项目错误类别

创建新项目后，你可以通过点击其名称来编辑其更细致的详细信息。你想要设置的最重要的细节是项目的类别。系统中输入的每个缺陷都可以放入一个类别，你会想要定义尽可能多的类别。图20-4展示了以这种方式管理的典型项目，通过添加错误类别使项目准备就绪。

![](img/a1b732997d9cb194dceec0570dc79710_555_0.png)

图20-4：管理典型项目

你可能希望拥有类似下面的类别：

- 文本/副本更改
- 设计和外观
- 易用性
- 功能：业务逻辑
- [ ] 功能：可取的（超出范围且需收费）
- [ ] 功能：不正确
- [ ] 功能：故障
- [ ] 功能：缺失（但在规范中有详细说明）
- [ ] 功能：用户界面
- [ ] 项目管理和行政
- [ ] 数据库架构
- [ ] 系统和基础设施

创建一组类别后，你可以通过明智地使用Copy Categories From和Copy Categories To按钮，在未来的项目中轻松重用这些类别。这些按钮可以通过编辑项目上的类别（选择Manage ⇔ Manage Projects），然后滚动到你正在维护的现有类别列表的最底部来找到。你可能会发现，类似前面所述的通用类别列表将对你在未来可能承担的任何项目都有好处。

项目设置好后，以后每次登录Mantis时可能需要选择它，尤其是当系统上有多个项目时。屏幕右上角的小下拉列表框使你可以按名称在项目之间切换。

### 报告错误

现在你已经设置好项目，你和你的团队可以开始录入发现的错误。请务必将任何故障转化为更具体的任务，而不仅仅是宣布问题。例如，“将分页栏从页面底部移动到顶部，”比“分页栏位置不正确”更有效率。

要报告错误，只需从主导航中选择Report Bug。

你必须为错误选择一个类别。此列表将从你先前输入的类别中动态生成。

你需要输入的其他信息包括以下内容：

- [ ] 可重现性（Reproducibility）— 如果这是一个故障，而不是简单的请求，请说明问题可以重现的频率。如果这是对新功能的请求，请选择N/A，因为没有可重复的内容。
- [ ] 严重性（Severity）— 此列表硬编码到Mantis中，与故障对项目的影响相关。其中大多数不言自明。Feature是指功能级别的故障，暗示关键功能要么缺失，要么因故障而完全无法使用。Block是指由于此故障，其他测试正在被搁置。
- [ ] 优先级（Priority）— 这表示开发团队需要处理的故障的相对严重性级别。
- [ ] 摘要（Summary）— 这是对故障的简短、一行摘要，或者如果空间不足，则是故障正在发展的区域（例如，“回复电子邮件时文本字段的自动完成”）。
- **描述（Description）**— 这提供了关于故障的更多详细信息。
- **其他信息（Additional Information）**— 这提供了可能有助于开发人员解决问题的任何其他要点。
- **上传文件（Upload file）**— 如果你希望将二进制文件与此故障关联（例如，显示故障运行情况的屏幕截图），可以在此处上传。它将存储在你设置项目时指定的服务器位置。
- **报告后停留（Report Stay）**— 如果你选中此框，在错误成功输入后，你将被返回到“报告新错误”屏幕。这使你能够更轻松地批量输入错误。

输入错误后，你可以从主导航菜单的View Issues下查看它。值得注意的是，该错误尚未分配给任何人。这是下一步。

### 分配错误

将错误输入系统后，你无疑会希望使用你自己的Mantis登录将其解决分配给你的开发团队中的一名成员。

从View Issues下显示的列表中按编号选择错误，你将看到名为Assign To的按钮旁边有一个用户下拉列表。选择你希望将错误分配给的用户（可以是你自己），然后单击该按钮。有幸被指派解决此错误的用户将收到一封带有错误直接链接的电子邮件。

你也可以从View Issues屏幕批量分配错误。如果你正在处理小型项目，并希望将所有未解决的错误分配给某个用户，这将很有用。在你要分配的错误旁边打勾，在列表底部的下拉列表框中选择Assign，然后单击Go。你将被邀请选择一个用户，选中的错误将以同样的方式分配给该用户。

### 标注错误

你的开发人员可能会对你提出的错误有异议，或者想要添加他们自己的问题或评论。他们可以通过查看错误，在相关文本框中输入文本，然后单击Add Bugnote来实现。评论将针对错误记录，副本会发送给最初提出错误的人。提出错误的人随后可能想要添加他或她自己的评论（如有必要，进行回复），这将反过来发送给开发人员，以此类推。

开发人员还可能希望使用错误的解决状态来指示他或她对手头任务的进度，或对错误的整体反应。这包括诸如“不是错误（not a bug）”、“不会修复（won’t fix）”、“已修复（fixed）”等标志。任何状态更改也会向提出错误的人生成通知电子邮件。

### 解决错误

开发人员修复错误后，他或她只需单击Resolved按钮将其标记为已解决。此操作会将错误的解决状态和总体状态均更改为“已解决（resolved）”，在此过程中向提出错误的人发送电子邮件。

如果项目管理员同意该错误已解决，他或她可以将其总体状态设置为“已关闭（closed）”。如果他或她不同意已解决，则可以重新分配，并将解决状态设置为“已重新打开（reopened）”。开发人员将收到通知，错误已被重新打开。





两个状态标志在查看问题视图中特别有用，在该视图中可以应用筛选器仅查看特定状态的错误。使用颜色编码可以一目了然地指示错误的状态。

## 充分利用 Mantis

Mantis 入门虽然相当简单，但它是一个功能极其强大的软件包，需要且值得深入关注。对其所有功能和特性的完整讨论超出了本章的范围，但 Mantis 网站 www.mantisbt.org 提供了详细说明，包括一个有用的常见问题解答（FAQ）。

## 摘要

本章向你介绍了质量保证（QA）的基础知识。你首先了解了应用程序开发中质量的真正含义，以及构成质量的六个核心概念。

接着，你学习了如何在现实世界中测试其中许多概念，以确定和衡量任何给定项目的质量，以及如何最好地记录这些测试的结果。

最后，你了解了 Mantis，这是一个功能强大的错误跟踪和故障管理工具。你学习了如何安装和配置它，以及如何在自己的项目中日常使用它。

到这时，你应该已经拥有一个无缺陷的高质量产品。在第 21 章中，你将学习如何制定有效的部署策略，将该产品从开发和暂存服务器部署到实时环境。

## 部署

销售自动化工具包现在不仅完全符合商定的规格和蓝图，而且完全无错误，这在很大程度上归功于第 20 章中彻底的质量保证（QA）和测试。

当你最初开始 Web 开发时，将应用程序上传到生产服务器的过程可能看起来很简单，但对于真正的专业人士来说，总有一个（一如既往的）最佳实践需要遵循。这种最佳实践不仅仅是做样子。它对于确保有效的版本控制和 QA——本书其他部分涉及的两个主题——至关重要。

在本简短章节中，你将学习如何为开发团队构建服务器环境，并在“上线”过程中管理服务器之间的源代码迁移。你还将探讨如何以及何时应用每次迁移，以符合你和客户团队的即时商业目标。

### 制定开发环境

在开发大型 PHP 应用程序时，通常不可避免地需要多个服务器或开发环境来在开发过程中各司其职。

当然，最终，你完成的应用程序（无论是公共网站还是封闭式内网应用程序）都将驻留在某个服务器上。该服务器可能位于专用数据中心，也可能仅位于客户公司的服务器机柜中。

该服务器通常被称为生产服务器，或者（如果涉及多个服务器，这在高流量/高可用性网站中经常出现，如第 23 章所述）生产环境。当你开始项目时，该服务器可能甚至尚未购买。因此，需要一系列过渡环境为你的应用程序部署提供按时间顺序的垫脚石。

### 工作室开发环境

作为项目负责人，你必须为开发团队配备一个本地开发环境以供开发。此示例假设你的项目名为 Widgets。你的本地开发服务器可能仅位于你的内部网络上，使用私有 IP 地址 192.168.1.1（或类似地址）；并且不应暴露给外部世界，因为外部世界永远不需要访问它。你还可能制定了一个内部域名——也许是 mydevelopmentco.local——该域名仅使用你自己的内部 DNS 服务器进行解析。

你随后可以在 Apache 或你选择的 Web 服务器中建立一个虚拟服务器：

```
http://dev.widgets.mydevelopmentco.local
```

在 UNIX/Linux 上 Apache 的 httpd.conf 中对应的条目如下：

```
<VirtualHost 192.168.1.1:80>
ServerName dev.widgets.mydevelopmentco.local
ServerAdmin ed@example.com
CustomLog /home/widgets/logfile_wid common
ErrorLog /home/widgets/errlog_wid
DocumentRoot /home/widgets/public_html/dev/php
</VirtualHost>
```

显然，你需要修改 IP 地址、服务器名称、电子邮件地址和路径以匹配；并且，其他 Web 服务器的配置语法当然也会有细微差别。

你还必须将用户 widgets 的主目录暴露给整个开发团队，以便他们可以使用自己选择的开发环境轻松修改代码。在典型设置中，他们可能使用 Windows 工作站来修改代码。在这种情况下，强烈建议使用 Samba（www.samba.org）来创建一个网络驱动器字母，从中他们可以访问源代码库，并直接在开发服务器上对其进行修改。

你的团队随后对源代码库所做的修改将仅在开发 URL（http://dev.widgets.mydevelopmentco.local）上可见，而不会在实时站点上可见。

如果你使用附录 A 中描述的任何形式的版本控制方法，还必须为每个开发人员提供虚拟服务器实例——例如 http://johndoe.dev.widgets.mydevelopmentco.local。有关此设置及其在版本控制中所起作用的更多详细信息在附录 A 中提供。在这样的设置中，之前提到的主开发服务器仍然存在，但它是作为提交到版本控制仓库的源代码库的镜像，而不是任何正在进行的实时开发。

> 在较大的开发工作室环境中，为每个新项目（以及使用版本控制时的每个新开发人员）创建 DNS 条目可能很耗时。如果你为所有项目只使用一台物理服务器，则可以通过使用通配符 DNS 设置来简化此过程。这意味着 *.mydevelopmentco.local 将自动解析到 192.168.1.1。你可以在网上查找如何操作的信息。只需搜索“通配符 DNS”。

### 工作室暂存环境

作为一家开发公司，你会希望拥有自己的生产服务器——一个你和你的团队在将代码发送给客户之前托管自己批准的最终代码的地方。

如果你使用版本控制，这将是你的仓库的镜像，但不一定在所有情况下都是最新版本。相反，它将是每个文件中已获准提交给关键项目干系人审批的最新版本。在实践中，这将代表每个文件中已被“标记”为发布的版本。

有关标记的更多信息可以在附录 A 中找到，附录 A 更详细地探讨了版本控制。

工作室暂存环境通常仅供内部使用。它对希望评估项目真实进度的项目经理最有用，也适用于 QA 和测试，因为在这些阶段不能冒风险修改实时数据库。

在前面的示例中，工作室暂存环境可能命名如下：

```
http://studiostaging.widgets.mydevelopmentco.local
```

对应的 Apache 条目可能如下：

```
<VirtualHost 192.168.1.1:80>
ServerName dev.widgets.mydevelopmentco.local
ServerAdmin ed@example.com
CustomLog /home/widgets/logfile_wid-staging common
ErrorLog /home/widgets/errlog_wid-staging
DocumentRoot /home/widgets/public_html/staging/php
</VirtualHost>
```

### 实时暂存环境

实时暂存环境为你提供了一个测试平台，以便在实时生产环境中发布之前向项目干系人演示新功能。

暂存环境通常托管在与生产环境相同的服务器（或服务器）上，但使用略有不同的 URL。例如，如果你的实时站点称为 http://www.widgets.com，你可以使用 http://staging.widgets.com 作为你的实时暂存环境。

典型的 Apache 配置可能如下：

```
<VirtualHost 192.168.2.1:80>
ServerName staging.widgets.com
ServerAdmin ed@example.com
CustomLog /home/widgets/logfile_wid-staging common
ErrorLog /home/widgets/errlog_wid-staging
DocumentRoot /home/widgets/public_html/staging/php
</VirtualHost>
```

请注意与开发服务器相比的不同 IP 地址——实际上，是不同的子网。为你负责的每个服务器集群使用不同的私有地址范围是值得的。因为你的实时暂存环境很可能位于数据中心，而不是位于你的


本地网络中，已引入第二个子网：192.168.2.x 代替 192.168.1.x。保持子网不同，可以让你在需要时更轻松地配置对远程数据中心的虚拟专用网（VPN）访问。这样也不会那么容易混淆。

如果你的实时生产环境在负载均衡配置中使用多台服务器，那么明智的做法是让你的暂存环境仅运行在一台服务器上。毕竟，你的暂存环境不太可能吸引需要使用多台服务器的负载。

为你的实时暂存环境设置用户名和密码保护可能是明智的，因为它从严格意义上说是公开可访问的。如果普通大众看到了例如受新闻封禁限制的内容，那将是灾难性的。想象一下，如果人们只需访问 `http://staging.apple.com` 就能查看苹果公司即将在其最新全球开发者大会（WWDC）上发布的内容，会造成怎样的后果！

但是，避免使用 `.htaccess` 文件来实现此功能，因为该文件在部署过程中可能被意外复制到生产环境，从而将你的生产环境暴露在相同的密码保护之下。

相反，你可以直接将此安全层添加到 Apache 配置文件中：

```
<VirtualHost 192.168.2.1:80>
    ServerName staging.widgets.com
    ServerAdmin ed@example.com
    CustomLog /home/widgets/logfile_wid-staging common
    ErrorLog /home/widgets/errlog_wid-staging
    DocumentRoot /home/widgets/public_html/staging/php
    <Directory /home/widgets/public_html/staging/php>
        AuthType Basic
        AuthName Staging
        AuthUserFile /home/widgets/.htpasswd
        Satisfy All
        Require valid-user
    </Directory>
</VirtualHost>
```

.htpasswd 文件以正常方式创建（即使用 `/usr/local/apache/bin/htpasswd`）。

保持 .htpasswd 文件位置在 Web 站点目录结构之外非常重要。在此示例中，它位于 `/home/widgets` 上三级文件夹中。这样可以确保恶意入侵者无法通过简单的 HTTP 请求检索密码文件。

顺便提一下，值得记住的是，这种基本身份验证（正如它所知的）并非工业级强度。如果你在实时暂存环境中存放真正敏感的材料，你还应考虑使用 Apache 指令 `Allow` 和 `Deny` 按 IP 地址限制访问。

## 实时生产环境

你的实时生产环境提供公众所见的环境——即实时网站本身。如果这是一个封闭系统，这可能不是面向普通大众的，但它仍然是完全经过测试、完全获准、已批准代码的场所。

典型的 Apache 配置可能如下所示：

```
<VirtualHost 192.168.2.1:80>
	ServerName www.widgets.com
	ServerAdmin ed@example.com
	CustomLog /home/widgets/logfile_wid-live common
	ErrorLog /home/widgets/errorlog_wid-live
	DocumentRoot /home/widgets/public_html/live/php
</VirtualHost>
```

## 开发数据库

假设你的应用程序是数据库驱动的，你必须有意决定为每个环境使用哪个数据库实例（即哪台物理服务器以及该服务器上的哪个数据库）。

考虑到某些代码演进可能需要修改数据库架构，如果在仍由旧版代码驱动的生产数据库上进行此类修改，肯定会导致错误。这一点尤为重要。

牢记这一点，请考虑以下策略：

- 单个开发环境（如果使用）应使用针对该个人的本地托管数据库。例如，John Doe 应使用名为 `widgets-johndoe` 的数据库。
- 主开发环境应使用本地托管数据库（也许仅命名为 `widgets-dev`），不特定于任何单个开发人员，但应反映支持版本控制平台中最新版本所需的最新数据库架构。
- 工作室暂存环境应使用本地托管数据库（也许仅命名为 `widgets-stg`），不特定于任何单个开发人员，但应反映支持版本控制平台中最新发行版标记版本所需的最新数据库架构。
- 实时生产环境自然应使用实时数据库服务器和实时数据库。
- 实时暂存环境也应使用实时数据库，这样当客户使用它进行测试和批准时，它可以准确反映更改部署后实时环境的表现。

当然，随时存在至少四个数据库，跟踪数据库架构本身的必要更改可能很棘手。

版本控制软件在这里用处不大。是的，可以在仓库中维护数据库结构的转储，但仅下载此转储不会在物理上更新数据库架构。直接删除并重新创建数据库是一个选项，但这会丢失其中存储的任何测试数据。在处理较大的项目时，也很难使用这种 SQL "转储" 文件来确定数据库架构的差异。

因此，最好的方法是良好的沟通。版本控制在这里可以发挥重要作用。在仓库中创建一个名为 `db-changes` 的文件夹。指示开发人员在对数据库架构进行更改时，添加包含一系列 `ALTER` 语句的文本文件，这样任何执行“获取最新版本”的开发人员也会收到一系列需要对其自身数据库进行的更改。

此类文件也可以标记为 `release`，以便负责维护主开发环境和工作室暂存环境的人员可以确保两个数据库都保持适当程度的最新状态。

> 告诉你的应用程序使用哪个数据库可能会导致尴尬的 `switch` 语句，或者更糟的是，需要手动更改的硬编码值。不过，还有另一种方法。你无疑有一个名为 `constants.php`（或类似）的文件，用于指定数据库 IP 地址、数据库名称、用户名、密码等。通过调整此文件以查询 `$_SERVER[ "HTTP_HOST" ]` 属性，可以根据所使用的虚拟服务器，有条件且动态地确定数据库 IP、名称、用户名和密码，并自动选择正确的数据库。这样一来，每个人都可以共享同一个常量文件。

## 部署工作流

仅拥有这些开发环境并不能自动促进最佳实践部署策略。源代码的工作流也很重要。

你可能会发现图 21-1 中的图表对于说明从部署到实时的源代码流程很有用。

开始
开发人员在其自身开发环境中处理代码，并在需要时更新其数据库架构
代码提交到版本控制仓库
代码自动部署到主开发环境（MDE）
是否需要 MDE 数据库更新？
应用来自版本控制仓库的更新
项目经理评估 MDE 上的代码以确定就绪情况
所有代码是否就绪？
为“发布”标记相关代码版本
带“发布”标记的代码部署到工作室暂存环境（SSE）
是否需要 SSE 数据库更新？
应用来自版本控制仓库的更新
项目经理评估 SSE 上的代码以确定就绪情况
所有代码是否就绪？
代码部署到暂存实时环境（SLE）
是否需要实时数据库更新？
应用来自版本控制仓库的更新
客户评估 SLE 上的代码
所有代码是否就绪？
将 SLE 部署到实时生产环境（LPE）

图 21-1：源代码流




以下是该过程的核心：

- 1. 各开发者针对其自身的开发环境进行开发，并使用其自身的数据库。
- 2. 此代码部署到主开发环境。这可能通过计划任务自动发生，或由项目经理在半定期基础上发起。此时，主开发环境的数据库架构中需要进行的任何更改也会一并进行。
- 3. 主开发环境上的代码由项目经理或（最好是）项目首席架构师进行测试、检查和批准。某些文件可能会被标记为可用于工作室暂存环境，因此也可用于发布。
- 4. 此代码随后全部或部分进入工作室暂存环境，在提交给客户之前经过最终审核。工作室暂存环境的数据库也会在需要时进行修改。
- 5. 代码随后部署到实时暂存环境，实时数据库也会修改以支持任何架构更改。客户在此处批准或拒绝您所做的更改。
- 6. 最后，代码从实时暂存环境进入实时生产环境。在此过渡期间无需更改数据库，因为相同的“实时”数据库既用于实时暂存环境，也用于实时生产环境。

现在让我们来看看这些过渡背后的技术。

## 自动化版本控制仓库提取

许多较大的项目使用一种称为 _版本控制_ 的技术，这是一种确保项目中不同开发者的工作在任何阶段都不会发生冲突的技术。它还会跟踪代码更改的时间和内容，以防在开发过程中出现问题。附录 A 提供了关于版本控制的更多信息。

在项目中使用版本控制时，您可能会不时需要自动从仓库中检索最新版本。在之前的流程中，这是汇集开发团队的工作以组装快照主开发环境所必需的。

### 使用 CVS

使用开源并发版本控制系统 (CVS) 程序，可以使用类似于以下语法来完成此操作。此语法适用于 CVS 的 UNIX 实现。使用 Windows CVS 客户端时，该过程变成了简单的点击操作。

```
cvs -d :pserver:username@cvsserver:/path checkout -r tag module
```

在此处，_module_ 是项目名称，_username_ 是有权访问该项目的 CVS 用户名，_cvsserver_ 是 CVS 服务器的主机名。可选地，您可以指定标签。如果您希望将内容提取到工作室暂存环境，这可能会很有用。

项目经理或首席架构师可以使用标签来指定项目中每个文件的不同版本，作为独立发布的一部分。例如，您的应用程序的最新稳定版本可能由某个文件的版本 1.3、另一个文件的版本 1.5、第三个文件的版本 1.4 等等组成。通过为每个相关版本添加诸如 lateststable 之类的标签，那些希望检索您应用程序特定版本的人可以轻松做到。

此类命令很可能会被提交到您服务器的 crontab 中，以便按计划运行。例如，您可能会有以下两个条目：

- 每天午夜，仓库的内容（无论标签如何）都将被提取以形成主开发环境。

- 每天凌晨 3:00，带有 release 标签的仓库内容将被提取以形成工作室暂存环境。

### 使用 Subversion

附录 A 考察了 Subversion（简称 SVN）作为一种比 CVS 更易用、更实用的替代方案。特别是，附录 A 演示了如何通过 SSH 协议对 SVN 进行隧道传输，可以轻松部署新的 SVN 仓库，无需担心在防火墙上打洞等等。

此方法允许使用类似于以下语法轻松检出给定的代码仓库：

```
$ svn checkout svn+ssh://ed@ssh.example.com/home/production/svn/widgets
```

在此示例中，名为 widgets 的项目从仓库中被检出，该仓库的根目录位于 ssh.example.com 服务器上的 /home/production/svn。检出操作以用户 ed 身份执行。理所当然，此用户必须对相关仓库拥有文件系统读取权限。

幸运的是，从版本控制仓库检索所有带有给定标签的文件的过程相对简单。

在 Subversion 中，标签和分支只是仓库树中的复制路径。按惯例，标签位于 /tags 下，分支位于 /branches 下。

```
$ svn copy svn+ssh://ed@hspux01.unix.example.com/home/production/svn/widgets/
 trunk svn+ssh://ed@hspux01.unix.example.com/home/production/svn/hss/
 widgets/release
```

上述语法将基于当前主干版本创建项目的带标签副本。然后您可以像检出任何其他仓库目录一样检出它：

```
$ svn checkout svn+ssh://ed@ssh.example.com/home/production/svn/widgets/
 tags/release
```

您可以在 http://svnbook.red-bean.com/en/1.0/ch04s06.html 上找到关于 Subversion 分支和标记的更多信息。

## 使用 rsync

不难看出，最常见的部署要求是将服务器 B 上文件夹 A 的内容上传到服务器 D 上的文件夹 C。

这本身是一个简单的操作，但考虑到现代项目源代码库的大小，仅为了部署一个小更改就在互联网上传输数百兆字节的任务，确实看起来低效。

这时 `rsync` 就派上用场了。`rsync` 实用程序仅适用于 Linux/Mac OS X/UNIX，尽管最近一些作者已尝试制作 Windows 移植版。它提供了一种方法，将本地服务器上给定文件夹的内容复制到远程服务器上的另一个给定文件夹，同时仅复制已更改的文件（或文件的部分）。换句话说，它同步这两个文件夹。

然而，这通常是单向同步：从 A 到 B。自上次部署到 B 以来在 A 上更改的文件会被复制，但在此期间在 B 上更改的任何内容都不会复制回 A。然而，如果严格遵循本章讨论的部署模式，这不是问题。

您可能会在以下两种最可能的情况下使用 `rsync`：

- 将工作室暂存环境的内容部署到实时暂存环境

- 将实时暂存环境（获批准后）的内容部署到实时生产环境

`rsync` 甚至适用于同一服务器上的两个文件夹。因此，即使您的实时生产环境与您的实时暂存环境是同一台物理服务器，您仍然可以使用它进行部署。在服务器之间复制时，`rsync` 使用 SSH（或在紧急情况下使用 RSH）协议。因此，允许复制进行所需的唯一防火墙规则是为 TCP 流量打开端口 22。还有一个 `rsync` 特定的协议，但除非出于某种原因您无法使用 SSH，否则不需要使用它。

### 基本 rsync 用法

您通常会将 `rsync` 用作 shell 脚本的一部分。例如，您可能会创建名为 `deploy-studio-staging-to-live-staging` 的脚本和另一个名为 `deploy-live-staging-to-live-production` 的脚本。然而，它们的工作方式大致相同，并使用以下语法调用 `rsync`：

```
rsync -avrz -e ssh /local/directory/* username@remotehost:/remote/directory
```

相关指令如下：

- `-a` 标志实现 `archive mode`，它提供了一组预先打包的有用设置，适用于之前描述的用途，包括在传输启动时保持目录权限和符号链接完好。

- `-v` 标志会生成详细输出。您将看到实际被选择要复制的文件的详细列表。





- -r 标志会导致复制操作递归执行。
- -z 标志会导致传输中的数据在传输前被压缩。在同一服务器上的复制操作中，应省略此选项。
- -e ssh 指令告诉 rsync 使用 SSH 传输文件，而非 RSH。
- 源目录指定为 /local/directory/*（* 仅表示应复制该目录下的所有文件）。
- 远程目录指定为 username@remotehost:/remote/directory，但如果要在同一服务器上的另一个文件夹中复制，则应省略 username@remotehost 指令。

执行 rsync 命令时，系统可能会提示输入密码。这是指定远程服务器上与用户名关联的登录密码，就像你以正常方式 SSH 登录到该服务器一样。

让我们看看这种语法的实际示例。

## rsync 语法示例

首先，让我们看看如何将 studio 暂存环境的内容部署到客户数据中心的实时暂存环境中。你将使用以下语法：

```
rsync -avrz -e ssh /home/widgets/staging/
 * widgets@staging.widgets.com:/home/widgets/staging
```

如果客户随后批准了暂存服务器上的更改，你可以将其发布到生产环境。在本示例中，假设你将其发布到同一服务器上的另一个文件夹。你将使用以下语法：

```
rsync -avr /home/widgets/staging/* /home/widgets/live
```

请注意，此处省略了协议指令，因为这是仅限本地的同步。此外，未启用压缩，因为你假设速度提升将微乎其微。

如果客户的实时生产服务器是一台物理上不同的服务器，你可能会使用以下语法：

```
rsync -avrz -e ssh /home/widgets/staging/* widgets@live:/home/widgets/live
```

或者，如果客户在三台服务器之间使用负载均衡，你需要执行三次部署，每台目标服务器一次：

```
rsync -avrz -e ssh /home/widgets/staging/* widgets@web01:/home/widgets/live
rsync -avrz -e ssh /home/widgets/staging/* widgets@web02:/home/widgets/live
rsync -avrz -e ssh /home/widgets/staging/* widgets@web03:/home/widgets/live
```

## 使用 rsync 保持服务器同步

如果你的实时生产环境确实涉及多台 Web 服务器，那么 `rsync` 还有另一个非常有用的作用。

许多网站涉及使用服务器可写的 `/data` 文件夹。这些文件夹是大型二进制文件和其他数据的容器，这些数据可能不适合存储在 PostgreSQL 或 MySQL 等数据库中，或者可能实际上是从关系数据库生成的“静态资产”。（这是第 23 章中倡导的一种技术，该章探讨了如何最好地支持高流量和高可用性 Web 网站。）一个好示例是各种用户上传的文档。例如，用户可能为“我的个人资料”页面上传了一张照片。

在部署多台实时 Web 服务器的环境中，会出现一个两难困境。如何使新上传的数据对集群中的所有 Web 服务器都可访问？一种方法是使用集中式文件服务器，就像使用集中式数据库服务器一样，也许可以通过网络文件系统 (NFS) 导出其内容。然而，这可能非常缓慢，并且是必须考虑的额外开销。

另一种方法是在集群中的服务器之间以非常频繁的计划基础使用 `rsync`，以便在上传新二进制文件后，它会在几分钟内（甚至几秒钟内）同步到集群中的其他服务器上。

使用 `rsync` 可以相当有效地实现此方法，但如果你尝试计划任何此类命令，先前讨论过的键盘密码提示可能会成为障碍——毕竟，`cron` 调度程序无法为你输入密码。

幸运的是，有一种变通方法。它涉及使用所谓的 _passwordless SSH_，并在连接前在客户端和服务器上放置密钥文件。因为在设置了无密码 SSH 的环境中，`rsync` 依赖于 SSH，所以 `rsync` 也是无密码的，因此安排此类任务变得容易得多。

设置基于密钥的 SSH 略有挑战性，超出了本章的范围，但可以在网上找到详细信息。请查看以下出色的“操作指南”文档，了解所需的所有配置步骤：

`http://www.cs.toronto.edu/~murray/commnotes/passwordless_ssh.html`

但是，请注意一个注意事项。如果你确实采用这种方法，请确保你的应用程序知道二进制数据在上传后的几分钟内不一定可用。例如，如果你知道你的 `cron` 作业设置为每五分钟运行一次，那么在上传完成后的五分钟内，应禁用任何用户个人资料照片的显示，而是显示“照片即将发布”消息。五分钟过去后，你可以确定照片已存在于集群中的所有 Web 服务器上，因此可以安全地尝试正常显示照片。为此，只需在用户的数据库记录中添加一个 `time_photo_uploaded` 属性并测量经过的时间即可。

如果出于某种原因，你必须允许立即访问此类上传的照片，请考虑实施这样一个系统：当在没有该照片的 Web 服务器（例如 `web01`）上首次请求该照片时，该 Web 服务器会立即与其他 Web 服务器分别启动对该文件的 `rsync`，直到找到一台拥有该照片的服务器（例如 `web04`），然后向用户显示新复制的照片。这听起来可能有些啰嗦，但在实际操作中，用户在文件复制期间只会体验到非常短暂的延迟；随后从该 Web 服务器请求该照片的访问者将以正常方式获取它。

如果你确实采用这种方法，请考虑确保上传数据的文件名唯一，以便在它们被新版本替换时，不会出现一些服务器提供旧版本而另一些服务器提供新版本的情况。例如，如果你的用户个人资料照片是使用数据库表 user 中的用户 ID 命名的（例如 /data/userpics/193913.JPG），那么请考虑使用带序列号的后缀，因此文件名变为 193913_1.JPG，下一个版本为 193913_2.JPG，以此类推。你会将当前序列号存储在数据库中的用户记录上，因此仅显示最新版本。

## 关于 FTP 的一些话

在结束之前，值得快速了解一下文件传输协议 (FTP) 的作用。你几乎肯定已经对它非常熟悉了。它已经存在多年（比 Web 本身还要久），大多数每月 10 美元的 ISP 都将其作为将文件上传到 Web 服务器的主要方式。

然而，对于企业级或专业级开发来说，它根本行不通。除了因 FTP 服务器软件中发现的安全漏洞而臭名昭著外，还因为启用必要防火墙支持的过程繁琐（FTP 与众不同之处在于，在“主动”模式下，服务器实际上会连接回你的计算机），它还有一个主要缺陷：未加密。

这在实践中意味着，通过 FTP 从服务器传输到服务器的任何文件都可能面临暴露给外部世界的风险——无论是窃取你 Wi-Fi 流量的人，还是你 ISP 中的不法员工，亦或任何人。那段代码是你的知识产权。它是机密的。此外，让其他人看到你的代码会增加未来遭受入侵或攻击的风险，因为人们会了解你的应用程序在内部是如何工作的。

简而言之——不要这样做。坚持使用 rsync，它使用安全复制协议 (SCP) 或安全文件传输协议 (SFTP)。这两种协议都使用 SSH 作为底层传输机制，固然安全且加密。它并非万无一失（SSH 也不时会发现问题），但它比 FTP 好得多。

## 摘要

在本简短章节中，你了解了企业级 PHP 应用程序部署的原则，包括为团队有效构建开发环境，以及使用仓库提取和 rsync 管理每台服务器之间的源代码过渡。

在第 22 章中，你将了解 PHP 平台上可用的一些最常见的内容管理系统 (CMS) 和内容管理框架 (CMF)，无论是免费的还是商业的。你将了解每种系统的优缺点，以及在为自己的应用程序推荐或指定 CMS/CMF 时如何做出明智而审慎的决策。





# 第四部分

## 将 PHP 推向极限

- 第 22 章：PHP 世界中的内容管理
- 第 23 章：处理高流量和高可用性
- 第 24 章：PHP 推广
- 第 25 章：你作为 PHP 专业人士的职业生涯

## PHP 世界中的内容管理

迟早，你会遇到一位询问内容管理的客户。在千禧年之交，内容管理并未被广泛理解，许多市场部门和业主都不了解安装此类系统的好处。

今天，情况截然不同。随着博客、维基和其他发布工具的出现，内容管理已走入主流，每个人似乎都清楚它们为何如此有益。首先，商业利益相关者能立即理解消除瓶颈的好处，以及允许市场和内容团队在业务需要信息“公之于众”时发布信息的好处。

在本章中，你将了解内容管理的概览——它是什么，公司和组织拥有它能带来什么好处，以及这些系统为何重要。接下来，你将了解内容管理的简史，并快速浏览几款开源 PHP 系统。最后，本章将以一份内容管理的开发人员需求清单作结，以防你想要编写自己的系统。

### 什么是内容管理？

内容管理的教科书定义（你会在例如 wikipedia.org 这样的地方找到的定义）是“一套支持数字信息演进生命周期的流程和技术”。这是一个相当死板的定义，但它切中了要害。

当你从一个更高的视角（俗称的“30,000英尺视角”）审视内容管理时，很容易看出构成该术语所暗示的地理现实的山峰、山谷、斜坡、沼泽和城镇。

内容管理涉及以下方面，不分先后：

- 创建在 Web 上发布的信息（即内容）的人员可能都挤在一个房间里，也可能分布在全球各地。他们可能向单一指挥链（例如市场部门）汇报，也可能作为网站的志愿者贡献者松散地组成一个团队。他们可能使用英语或几十种语言创建内容。

- 内容本身可以是文本、图像、电影、富互联网应用或音频。此外，内容可能采用各种形式，例如 PDF 文件、博客文章、论坛讨论、白皮书、文章等。

- 在内容管理的世界中，内容可以以多种方式进行切分和分类。例如，内容项可能被归入不同的类别。（这些是主题类别，例如关于爱好、工作、宗教、政治等等的内容。）它们可能按文件类型或存储介质（例如数据库、平面文件或 XML）来区分。内容还可以按区域（例如，美国内容可能与英国内容不同）和语言进行分类。它甚至可以按受众画像分组（例如基础/初级、中级、高级专家等等）。

- 可能会根据多种因素向内容应用某些工作流规则。例如，世界某些地区的内容可能需要以特定方式进行审核。编辑者和发布者可能本能地信任某些贡献者（例如已在职员工），而不信任其他人（例如从未合作过的自由职业者）。一些团队可能选择始终将内容经过多个级别的审核（例如，由编辑执行语法/拼写/标点检查，由事实核查人员进行事实核查，由区域编辑进行最终审核，由网站管理员进行最终发布，等等）。其他团队可能选择信任初始贡献者撰写可接受的内容。

- 内容发布后，还会对每个内容应用一定的规则。例如，可能需要每 90 天自动审核某些类型的内容（例如文章或白皮书），以确保其仍然相关且准确。没有什么比一份严重落后于行业惯例的“最佳实践”白皮书更糟糕的了。

超越内容管理系统（CMS）的严格功能需求，你会遇到一大堆运营和战略因素。例如，内容的编辑者、作者和发布者很少脱离实际运作。他们必须为特定受众发布材料。

拥有受众并关注他们想要什么，需要进行受众分析。一些组织会经历极其严格的受众分析任务，以确切了解受众想要什么。这包括不仅审视他们关心的话题，还审视哪些格式是可接受的，他们觉得哪些频率舒适，甚至这些文章的语调和倾向。其他团队采取更多启发式方法，发布他们通常知道受众会喜欢的内容，因为他们本身就是该受众的成员。

在受众分析之外，还有组织的需求。人们容易忘记，组织本身（无论是营利性还是非营利性）及其业务合作伙伴、供应商和投资者也是发布项目的利益相关者。如果公司（或其合作伙伴、投资者等）正在努力实现某个目标，那么该组织发布的内容应该支持该目标。没有什么比内容战略与业务战略相悖更尴尬的了。

无论战略方向如何，大多数发布项目都必须遵守上层组织的政策。例如，不应允许网站发布泄露内部公司机密的材料。想象一下，如果网站发布诽谤性、诋毁性以及其他冒犯性（即性别歧视、种族歧视或诽谤性）的内容，将给组织带来多少痛苦和苦难。即使是一个由某个立场或观点的热心拥护者运营的一人主导项目，如果他或她所做的只是发布煽动性、指责性、诋毁特定个人的文章，最终也会遇到问题。

从运营角度来看，通过 CMS 在网站上部署的内容必须备份并防止非法删除。用于运行 CMS 的服务器和数据库必须维护、打补丁，并在其自身参数范围内运行。任何软件和操作系统（例如 Apache 和 PHP）也必须维护、打补丁并确保安全。这些功能大多由组织内部的 IT 部门处理，或由外部 SaaS（软件即服务）或 ASP 厂商处理。

总之，内容管理的问题远远超出了构建或安装 CMS。事实上，内容管理的技术方面与非技术方面相比相形见绌。当放在更广泛的战略 IT 范畴（例如计算或数据备份的一般政策）中考虑时，它可能只占组织计算需求的一小部分。

然而，你必须记住一件非常重要的事情：CMS 本身是对组织需求的技术响应。这个需求非常简单：组织如何快速、轻松、有效地发布信息？发布后，如何维护这些信息？

简而言之，内容管理提供了一项总体的主要好处：它帮助组织在信息发布方面跟上市场步伐。一旦你理解了这一点，其余一切都会迎刃而解。

### 内容管理简史

尽管你可以论证内容管理可以追溯到大型机时代，但本章主要关注 Web 内容管理，因此，内容管理的故事始于 1995 年的 InterLeaf 和 CNET。

InterLeaf 已经是一家创造桌面出版系统的创新公司，它看到了在万维网上发布信息的需求，并创建了 Cyberleaf。Cyberleaf 与其他编辑产品（例如 HoTMetaL Pro 和 Vermeer FrontPage）的不同之处在于，它使用户能够将文字处理应用程序中创建的文档转换为 HTML。它还使用户能够管理文档之间的链接。换句话说，它不仅仅是一个编辑器，而是一个单源发布系统，Web 只是发布信息的众多目标之一（还有印刷和其他交互渠道）。





## Part IV：将 PHP 推向极限

大约在同一段时间，CNET 创建了一个运行在内部 Web 发布系统上的网站，该系统后来被申请专利并命名为 PRISM。基本上，PRISM 是一个工具，即使是最恐惧技术的用户也能轻松创建网页。CNET 想要商业化 PRISM，但不想分散其核心业务（即发布内容）的精力。

1996 年某个时候，Ross Garber 和 Neil Webber 出现了，他们在德克萨斯州奥斯汀创立了 Vignette，其明确目标是让 Web 发布更加简单和个性化。他们一直在开发一款名为 StoryBuilder 的大规模内容管理工作流产品，当时他们与 CNET 联手。他们获得了 PRISM 的授权，向 CNET 提供了项目股权，并将其转变为 StoryServer，后者于 1997 年发布。

结果（使用工具命令语言，即 TCL 构建）是一种远胜于现有 CGI/Perl 动态网站构建方法的产品。公司可以购买 Vignette StoryServer 产品（许可费在六位数范围内），并使用提供的工具构建完整的应用程序。

在发展过程中，内容管理领域迅速变得拥挤。BroadVision、InterWoven、Documentum、DynaBase、Future Tense、FileNet、Stellent 以及数百家其他公司都在积极开发创新产品，所有这些产品都围绕内容发布的不同方面展开：工作流引擎、缓存技术、内容分发、个性化等。除了主要的企业参与者外，还有许多其他公司，最著名的是菲尔·格林斯朋（Phil Greenspun），他是 MIT 教授，也是 Ars Digita 的创始人，创建了 AOLServer。

接着，dot-com 泡沫破裂，内容管理市场分裂为两大阵营，看似处于光谱的两端，市场呈现出惊人的兼并/收购狂潮。

在光谱的一端是那些在企业领域运营的巨头（例如 Vignette、IBM 等）。他们的系统通常涉及“大型机”（后端使用 Oracle，部署在大型服务器上，有大量冗余备份和网络运维基础设施），需要大量顾问长时间工作，并且预算巨大。

在光谱的另一端，是新千年早期开始演进的开源应用程序。这些系统大多是基于浏览器的系统，利用了 LAMP（Linux、Apache、MySQL、PHP）技术栈。其中一些系统是商业的（例如 Mambo，顺便说一句，它也有一个开源分支），另一些是开源的（例如 Joomla!，Mambo 的分支；而另一些则是 20 世纪 90 年代早期系统的分支，例如 TYPO3）。不过，它们共同的一点是，都与前一个时代的企业系统形成了鲜明对比。

首先，新的 CMS 极其便宜或免费。客户可以将资金用于定制前端、工作流和数据后端，而非购买基础软件包。

此外，许多较小的系统都专注于让某一类用户满意。Drupal 最初被创建为论坛软件，后来演变为一个开源 CMS，在一个日历年内（2007 年 5 月至 2008 年 4 月）从 drupal.org 站点获得了 140 万次下载。WordPress（最初是一个博客平台）吸纳了许多更简单的内容管理功能。Joomla! 诞生于一整群 Mambo 开发者跳槽去构建他们觉得更贴近开源运动精神的系统的时候。

## PHP CMS 示例

由于本书是关于 PHP 的，因此将本章的大部分精力放在基于 PHP 的 CMS 上是合适的。你将在本节了解四个系统的相关知识。前两个你可能听说过，后两个可能不了解。选择这些系统并非因为它们是该领域的典范，或因为其受欢迎程度，而是因为它们各自以不同的方式处理内容管理。

希望通过这次快速概览，你在系统选择（届时）或甚至构建自己的系统（如果这是你的目标）时能做出良好的决策。

## Drupal

Drupal 是一个 Web 内容管理框架。如图 22-1 所示，它本质上是模块化的，允许几乎无限的定制。所有内容都存储在数据库中，通常是 MySQL。中间件和模块均使用 PHP 编写。

![](img/a1b732997d9cb194dceec0570dc79710_577_0.png)

Figure 22-1：Drupal 示例布局

在 Drupal 中，内容存储在单独的节点中。你可能有一个故事节点（例如文章），或者一个博客节点。多年来，开发人员创建了许多不同的节点类型，每种都有自己的一套规则、元数据等。

请注意，在 Drupal 中，节点被称为节点并非因为它是网络的一部分。相反，请将节点视为拼图的一块。节点可以是博客、在线帮助系统或论坛的一部分。使用内容构建套件（Content Construction Kit），用户可以创建自己的节点。从最基本的层面来看，所有节点都关联了一些通用元数据，包括以下内容（请参见图 22-2）：

- [ ] 节点 ID
- [ ] 内容类型
- [ ] 标题
- [ ] 正文
- [ ] 创建日期
- [ ] 正文
- [ ] 作者

![](img/a1b732997d9cb194dceec0570dc79710_578_0.png)

Figure 22-2：使用 Drupal 创建内容

每个节点可以与其他节点拥有任意数量的关系。如果你加载某个节点（例如，节点 198393），Drupal 会将其呈现给用户，并获取与其关联的所有其他节点。那个特定的节点、那个特定的 ID，可能是一篇带有标题、正文等内容的博客文章，但它还将包含指向其他节点的指针——例如，与该博客文章相关的所有评论，以及侧边栏中列出的所有相关博客文章。

在 Drupal 中，布局由主题处理。默认主题是一个三列布局，中间列充当“内容列”，侧边栏列提供导航和上下文链接。每列可以包含信息块，例如当前查看的故事、最近发布的故事、最受欢迎的故事等等。

内容块可能会显示给观众，也可能不会，这取决于观众的角色。例如，如果你已经登录，就不需要显示登录块。不同的菜单项可能会根据你的角色显示，从而提供一定程度的个性化。

节点可以组织成分类，在 Drupal 中这被称为分类法（taxonomy）。例如，你可能有一个组织为五个主要主题领域（产品、服务、关于我们、联系我们和客户服务）的网站，每个领域下都有子分类（例如，产品 ⇒ 产品 1；服务 ⇒ 服务 1；等等）。

图 22-3 显示了管理内容时可用选项的示例。

![](img/a1b732997d9cb194dceec0570dc79710_579_0.png)

Figure 22-3：使用 Drupal 管理内容

## Joomla!

当一群开发者因对如何处理 Mambo 的开源版本存在分歧而从 Mambo 叛逃时，Joomla! 应运而生。Joomla! 是斯瓦希利语单词的英文拼写，意思是“全部在一起”或“作为一个整体”。

如图 22-4 所示，使用 Joomla! 时，你使用文章。文章可以是任何类型的内容，从网页副本到博客文章，或者你需要的任何内容。文章还可以分配给类别和区段。区段和类别之间的主要区别很简单：区段可以包含多个类别，类别可以包含多篇文章。

![](img/a1b732997d9cb194dceec0570dc79710_580_0.png)

Figure 22-4：基于 Joomla! 的网站

例如，你可能有一个名为“产品”的区段，以及名为“服务”、“关于我们”和“联系”的其他区段。在每个区段中，你可以为每个产品或服务设置类别。

最后，每篇文章可以分配给一个类别。如图 22-5 所示，每篇文章都有标题、状态、内容区域以及其他高级功能，例如“阅读更多”（仅在普通视图中显示文章的一部分）和“首页”（在网站主页上展示该文章）。

![](img/a1b732997d9cb194dceec0570dc79710_581_0.png)

Figure 22-5：使用 Joomla! 创建内容

与大多数其他系统一样，Joomla! 允许你创建用户，每个用户都有自己的登录名、密码和关联权限。一些用户可能能够创建和编辑文章，而另一些用户可能仅限于投稿，但不能发布。

Joomla! 还能方便地创建指向你网站的 Web 链接（或书签）和新闻源。这些内容类型中的每一种都可以分配给特定的类别，从而非常轻松地为给定类别下的所有文章显示统一的链接和源集。





每个类别还可以分配其自己的布局，Joomla! 让您可以控制各种参数（例如菜单中的类别顺序、页面标题等），以及外观和感觉。

最后但同样重要的是，Joomla! 支持添加各种模块，每个模块通常专注于特定任务。例如，有些模块显示面包屑链接，有些显示存档内容或自定义菜单，还有些分发内容并显示投票。

图 22-6 显示 Joomla! 控制面板。

![](img/a1b732997d9cb194dceec0570dc79710_582_0.png)

图 22-6：Joomla! 控制面板

## ExpressionEngine

ExpressionEngine 是由 Ellis Lab 的人员创建和推广的 CMS，该团队也将 CodeIgniter（一个 PHP MVC 框架）推向了市场。在所有主要的 CMS 中，ExpressionEngine 最具 Web 2.0 特色，提供许多前沿功能，并且以物超所值的价格提供大量功能（个人许可证约 99 美元，商业许可证约 250 美元，但核心系统对开发者免费）。图 22-7 显示了一个使用 ExpressionEngine 的网站。

![](img/a1b732997d9cb194dceec0570dc79710_583_0.png)

图 22-7：ExpressionEngine 允许创建精美的网站

在 ExpressionEngine 控制面板中（参见图 22-8），您可以管理 CMS 用户、内容和模板。创建模板（参见图 22-9）可以对外观和感觉进行相当细致的控制。每个模板可以包含由 ExpressionEngine 解析的 XHTML 标记和表达式（因此得名）。

## 第四部分：将 PHP 推向极限

![](img/a1b732997d9cb194dceec0570dc79710_584_0.png)

图 22-8：在 ExpressionEngine 中添加内容

![](img/a1b732997d9cb194dceec0570dc79710_584_1.png)

图 22-9：ExpressionEngine 模板

这些表达式可以简单到添加自定义文本片段，或在侧边栏中循环博客文章。例如，如果您要在网站上发布书籍列表，可以创建作者、ISBN、标题、出版年份和语言等自定义字段，所有这些字段都可以在网站的其他部分由 ExpressionEngine 使用。例如，您可以列出某位作者的所有书籍，或某年出版的书籍。您还可以将某个自定义字段指定为下拉列表或日期字段。

此外，模板与网站其他部分协作的方式巧妙地简单。您可以将模板分组，以创建自解释的 URL 路径。例如，您可以创建名为“服务”的模板组，并将与服务相关的页面放置在该模板中。

## Frog CMS

Frog CMS 源于 phpRadiant，即流行的基于 Rails 的 Radiant CMS 的 PHP 版本。其标语是“简化内容管理”（参见图 22-10），任何使用过它的人都会同意。它提供了非常优雅的用户界面、灵活的模板引擎，以及用户和资产（文件）管理所需的精简工具（参见图 22-11）。

![](img/a1b732997d9cb194dceec0570dc79710_585_0.png)

图 22-10：Frog CMS 网站的主页

![](img/a1b732997d9cb194dceec0570dc79710_586_0.png)

图 22-11：在 Frog CMS 中管理页面

用户可以为其布局创建代码片段（参见图 22-12），每个代码片段都是一段可重用的代码，例如页眉或页脚。代码片段也可以是纯内容，例如链接列表或图形。Frog CMS 还允许用户使用简化的 HTML 编辑器创建内容。

![](img/a1b732997d9cb194dceec0570dc79710_587_0.png)

图 22-12：在 Frog CMS 中管理代码片段

最后但同样重要的是，您可以向 Frog CMS 添加模块（通常是插件或主题），从而扩展它。核心插件包括存档功能、评论、文件管理、404 自定义页面控件和 SQLite。已经，用户社区创建了一个完整的插件库，包括投票、下载管理、时事通讯、联系表单等。

## 构建您自己的系统

内容管理领域的一件有趣的事情是，许多组织拥有所谓的“独特本地需求”——换句话说，他们在内容创建、发布、管理和分发方面有如此特殊的需求，以至于没有任何现成程序（无论是免费还是商业）是合适的。修改任何现成系统也行不通。

相反，大量内容管理项目涉及适量的 DIY 编程。如果您正在参与此类项目，以下是任何项目都会列入候选清单的要求汇总。此汇总中包含一些技术细节，可帮助您理清思路。它并不全面，但这是一个良好的开端。

### 与内容相关的问题

对某些开发人员来说，这似乎总是一个令人震惊的发现，但内容管理系统的整个要点就是 *管理内容*。提出这一点只是因为大多数项目似乎会沦陷到涉及工作流引擎和数据库缓存的奇怪泥潭中。

内容为王。其他一切都从属于这一论断。内容的核心是 *内容类型*——这只是描述内容结构和使用方式的基础简称。大多数人直觉上明白新闻稿与博客文章有所不同。它们不仅有不同的组成部分，还有不同的用途和受众。

为此，您可以推出一组固定内容类型的 CMS：

- [ ] 网页
- [ ] 文章
- [ ] 博客文章
- [ ] 新闻稿
- [ ] 新闻源

这些类型中的每一个都可能有自己特定的一组数据字段（例如标题、作者、摘要、出版日期等）。或者，您可以推出一个允许用户定义自己内容类型的系统。

如果您选择前者，这看起来始终是更容易的选择（毕竟，创建动态内容构建系统需要大量工作），那么您必须准备好应对不断创建新内容类型的需求，并修改那些在开发期间看似不错但现在在发布后的严酷现实面前开始褪色的类型。

如果您选择后者，并允许管理员定义自己的内容类型，那么您必须问自己如何定义内容类型。在思考一段时间之前，这个问题的答案并不完全明显，也没有一个答案是 100% 正确的。然而，一条建议始终能带来良好结果：将内容类型定义为两组标准的交汇点：

- [ ] 与该内容类型关联的元数据是什么？（这将是名词和形容词。）
- [ ] 与该内容类型关联的行为是什么？（这将是动词和副词。）

一旦建立起这个思维框架，名词/动词比喻就成为表达任何内容类型的便捷方式。

让我们以新闻稿为起点。如果你思考新闻稿的形态（这是指“其组成部分”的花哨说法），你可以轻松地将这些部分转换为元数据。每个新闻稿都有以下组件（作为粗略的开始）：

- [ ] 标题
- [ ] 副标题
- [ ] 日期标识符
- [ ] 摘要
- [ ] 正文
- [ ] 联系信息
- [ ] 关键词/标签/分类

给足够的时间，你可能会发现另一组可能也可能不需要由你组织的公关团队使用的元数据。总而言之，你已经有足够的内容可以开始了。

但是，如果在名词处停止探索，你对新闻稿的认识将不完整。大多数组织还需要新闻稿以某种方式运作——换句话说，新闻稿也有与之关联的行为。例如，每个新闻稿都有一个发布窗口，通常表示为日期和时间（通常在市场收盘后）。它还包含使监管人员满意（如果存在）或不满意（如果不存在）的法律语言片段。

新闻稿的这些“动词性”部分也体现为元数据；但主要区别在于系统必须意识到它们，并根据存储在那里的内容做出响应。例如，法律片段最好存在，否则新闻稿无法发布。智能的 CMS 不应该允许新闻稿在未提醒某人法律片段缺失或不正确的情况下上线。发布窗口也是如此——如果新闻稿以某种方式分类（例如，其内容被标记为财经或市场新闻），那么 CMS 不应该允许在市场收盘前发布。

一旦你规划好新闻稿所需的内容，就对客户当前（以及未来可能）需要的所有其他可能内容类型做同样的处理。你不可避免地会发现所有内容类型在名词和动词方面有很多相似之处。事实上，你会注意到几乎每个内容都有标题、日期、作者、关键词、正文等。有些内容类型会有特殊需求（例如活动，可能还有报名 URL 和提醒小部件）。因此，你应该考虑可以添加到各个类型的非全局元数据。

一旦你完成了内容的技术设计，就必须决定采取哪条路径。如果你向客户提供硬编码的内容类型，那么你可能会为每个内容类型创建不同的数据库表。如果是这样，请确保未来添加新内容类型非常容易。这时良好的 MVC 设计就派上用场了，它让你可以轻松地为日历事件等添加数据库表，以及相应的模型、管理控制器和任何用于 CRUD（创建、审查、更新、删除）的视图。

如果你选择另一条路径，那么你可能会得到一个集中式表格，存放所有可互换的内容块（标题块、作者块、日期块、正文块等），然后赋予用户重用、重命名和连接这些块的能力——以他们选择的任何方式——将它们组合成称为 *内容类型* 的更大块。

不过，请记住，无论哪种方式，你都必须想出某种方法来告诉 CMS 你的元数据中什么很重要。换句话说，如果你硬编码内容类型，你就必须有办法告诉 CMS 没有标题的文章不能发布，或者新闻稿必须遵循某些工作流规则。如果你给管理员自由定义他们自己的内容类型，情况也是如此。





## Administrators and Privileges

Speaking of administrators, you will have to account for them. There’s no way around it. Make the site’s administrators happy, and you’ll have a happy team. The more they adopt your system, the more they love working with it, the easier you make things for them, the better off you’ll be.

If you have a small installation, with a small group of people (e.g., just one or two administrators), then you probably won’t have to expend a lot of energy on managing users and setting up different privileges for them. However, once you get past a certain number (e.g., five administrators) or if the administrators are split into different time zones or geographies (and, certainly, continents or language groups), then you most certainly have to deal with the complexities of privileges.

There are two ways to handle privileges. One is to give the administrators interchangeable building blocks, each of which represents a type of activity: creating content, updating content, reviewing (or reading) only, deleting, publishing, archiving, and so on. There could even be a "super administrator" activity that allows a user to administer other users, add new plug-ins, and so on.

The super administrator could then create a new user in the system (and, of course, each user would have a username, password, real name, e-mail address, phone number, and so on), and then assign building blocks to create a privilege profile. To give the super administrators more granular control, you could also give them building blocks that match up with different content types or sections of the site, as well as activities.

In effect, you could have a new user who has full access when it comes to working with press releases (they are the head of PR, after all!), but only read-only access to articles or blog posts. Other users (such as the CEO) could have read-only access to every single content type, but only create (not publish) authority over a little corner of the blog.

This kind of system is somewhat ingenious, but it requires a whole lot of work, and you’d better get your building blocks right, or you’ll be coming back again and again to revise the setup.

Another approach involves levels of access. The levels typically go something like this:

- Subscriber — This is a person who can log in to see items in read-only view only, or who gets regular reports about what is going on. Think of a C-level executive or senior VP who wants to know what is going on but shouldn’t be allowed within ten feet of a blog post.
- Contributor — This is a base-level content person who can create any content he or she wants, edit anything he or she has written (as long as it is still in draft stage), but must then send it to a higher power in order to see it published.
- Author — This is a trusted contributor who can write original material and publish it in certain areas of the site.
- Editor — This is a staff person (typically) who can only edit and revise pieces written by authors and contributors.
- Manager — This is a supervisory editor who can review anything, write new material, and launch pieces throughout the site. The manager can also set rules for pulling items off the live site, and for archiving material.
- Administrator — This is usually someone who deals with installing new plug-ins, sets up backups, sets up caching, and figures out the workflow rules and all the other background minutiae. This person also has the right to create new content (and update that content), but usually doesn’t just because he or she is too busy.

This second approach is much easier to deal with from the development side, but it leads to some oversimplistic effects on the operations side. For example, a manager might want to bring on a trusted freelancer but have no choice but to give that person a contributor role because the author privileges are just too far-reaching.

## Workflow

At its simplest, a *workflow* defines the steps that a piece of content goes through between initial draft and final deletion. In between are stages such as drafting, submitting for approval, legal review, publication, archiving, and, eventually, oblivion.

The heart of a good workflow system is good metadata. Most content types include a mandatory status field, usually a drop-down with a limited set of options. Most administrator roles or privilege sets include the capability to choose different subsets of the status markers — for example, if you are a low-level contributor, you may only be able to have two status markers: draft and pending. You won’t be able to make anything live, nor are you able to work on anything that is already live.

Generally speaking, workflows can either be hard-coded into a CMS (easy on the developers, but difficult on the operations staff) or made more flexible, such that content operations staff can define paths for either different content types or different sections of the site (or some combination of the two). For example, for an article, you may have three workflow steps (draft, approve, publish), but an article for the products section of the site may have more approval steps. It may need to be checked by a product manager, a subject matter expert (SME), and the editorial board.

Furthermore, most workflow systems should have some kind of messaging capability. If an editor rejects a draft from a contributor and sends it back to draft status, the editor should be able to send an e-mail to the contributor, explaining why that decision was made.

Alternatively, if you have a complex workflow setup, then you must take into account tracking both parallel and sequential approvals. Most workflows are sequential (drafting, submittal, reviews, and then on to publication); but in the previous example with the SME, product manager, and editorial review board, you would probably want the SME and product manager to review simultaneously, and then pass the material along to the editorial review board.

One other note and then we’ll move on. Because workflows are often hard to visualize, the best workflow systems are visual in nature. Either they allow the administrator to graphically add symbols to the screen and pipe them together (much like a UML or process flow) or they use some kind of vertical metaphor (in which the content drops through the pipeline following the rules in each step). Along the way, each step is associated not only with the content item being worked on, but also any other affected groups, such as a certain editor (or maybe the whole editorial group) or even other pieces of content that need to be released at the same time (such as the press release about a product, the five product pages, and the freebie download for that product).

Either way, you must make it easy for an administrator to create and then maintain a workflow. It has to be intuitive enough that you understand it at a glance, but powerful enough to do everything the team needs vis-à-vis their workflows.

## Templates

In the early days of content management, it seemed that every Web site run by a CMS was easily identified because of its boxy look and feel. Nowadays, though, the CSS and XHTML wizards on the front end have joined forces with the back-end developers to offer users impressive experiences.

There are at least three ways to handle templates in your CMS.

The quick-and-easy way is to hard-code your look and feel, adding whatever hooks you need in your PHP front-end templates to pull in what you need from the database. For example, if you are working on a template for a press release, you can pull in the headline, body, author byline, contact information, legal bits, and the rest of it.

The problem with this approach is pretty obvious. It’s easy on the developers (at first), but a misery for the operations staff. If someone creates a new content type, you must create a new set of templates. No matter how pretty and usable your templates are, this kind of thing can get pretty old.

A second approach is to offer dynamic templates that the administrators control. Again, you can give them the capability to create reusable blocks or snippets to create what they need in terms of sidebars, headers, footers, and content blocks. Then, if you give your templates some smarts and insight into the content types they’re supporting, you can enable the administrators to punch out any kind of content they want, using metadata fields as they need them.

For example, let’s say that you have a page layout system consisting of four major snippets:

- A header snippet, which includes not only the logo, but also the global navigation
- A footer snippet, which contains legal/copyright, and so on
- A sidebar snippet, for use on either the left or the right, which itself might contain other snippets
- A main content snippet, which holds a blog post, article, or whatever

You could make it such that each of these snippets knew about the different content types and the different fields associated with each type, and then use them interchangeably as needed. For example, let’s say that you organized content types such that no matter what type is being used, it has a set of universal metadata fields (such as byline, headline, body, date, and so on). You could easily come up with a way to use parsed text in your templates and take advantage of that, as shown here:

```
<h1>[[:content_type:headline]]</h1>
<p>by [[:content_type:byline]]</p>
[[:content_type:body]]
```

The :content_type: expression would be a generic rule that tells the template engine to apply this rule to any content type — for example, because every single one would have a headline. The template engine would be smart enough to deduce that anything between the [[ and ]] tags requires extra processing before final delivery of HTML to the browser.





或者，如果您想为新闻稿创建一个专用模板，例如，可以采取更具体的方法：

```
<h1>[ :content_type:headline type='pr' ]</h1>
<p>by [ :content_type:byline type='pr' ]</p>
[ :content_type:body type='pr' ]
```

第三种方法是使用开源或商业模板系统，可供选择的有很多。最著名的大概是 Smarty，这是一个相当强大的模板引擎，可让您将 XHTML 与 PHP 分离。您的 Smarty 模板最终将包含与 PHP 中设置的变量相关联的标记。请参考以下示例：

```
//this is your PHP
include('smarty.php');
$smarty = new Smarty;
$smarty->assign('nickname', 'myerman');
$smarty->assign('realname', 'Thomas Myer');
$smarty->assign('city', 'Austin, TX');
$smarty->display('user.tpl');

//and here is user.tpl

<html>
<head><title>User info for {$nickname|capitalize}</title></head>
<body>
<h1>User info for {$nickname|capitalize}</h1>
<p>Real name: {$realname}</p>
<p>City: {$city}</p>
</body>
</html>
```

请注意本示例中的两点。首先，也是最重要的是，PHP 端的任何赋值在 Smarty 端都可以轻松以 `{$varname}` 格式访问，从而有效简化了前端开发人员或设计师的工作，他们通常对后端代码望而却步。第二点需要注意的是，可以为不同变量添加运算符 — `$nickname` 末尾的 `|capitalize` 可让您根据需要将数据转换为显示格式。

就像开发者生活中的大多数事情一样，关于模板引擎的讨论常常演变成宗教之争。你绝不局限于 Smarty（有些开发者讨厌它，有些开发者喜欢它），因此请选择最适合您作为开发者的需求、网站设计师的需求以及网站访问者需求的系统。

## 摘要

在本章中，您了解了一些关于内容管理系统（CMS）的知识。您了解了什么是内容管理系统，学习了一点历史知识，回顾了四个基于 PHP 的系统示例，甚至了解了需求概览，以防您想自己构建系统。

第 23 章提供了一些关于处理高流量和高可用性的技巧。

## 处理高流量和高可用性

第 22 章向您介绍了一些基于 PHP 的内容管理系统（CMS），这些平台您很可能会尝试纳入大型或企业级 Web 应用程序中。所有此类 CMS 都特别适合规模更大或流量更高的网站，在这些网站中，手动更新的负担在商业上是不切实际的。

然而，构建大型网站既有技术影响，也有商业影响。大型网站在开发小型项目时不会遇到两个关键负担：确保高可用性（即在给定时期内可用时间的高百分比）以及处理异常高水平的流量而不受不利影响。涉及的保险技术对小型网站来说往往很陌生，但出乎意料地容易实现，尤其是考虑到它们不一定是 PHP 特有的。

在本章中，您将了解这些专业技术以及如何将它们纳入您自己应用程序的架构中。通过这样做，您将最终证明 PHP 非常适合此类大型网站。此外，您还将偷偷了解一些网络上最高流量商业网站的架构，包括 Flickr 和 Facebook —— 两者都自豪地使用 PHP 构建。

### 理解术语

术语*高流量*和*高可用性*对不同的人有不同的含义。在深入探讨之前，值得巩固您对企业架构师通常认为它们含义的理解。

#### 高可用性

“可用性”一词是指应用程序在可接受参数范围内的正常功能和运行。如果应用程序基本可用（即使运行速度比平时稍慢），则被认为是可用的。可用性通常按应用程序可用的时间占给定时期的百分比来衡量。

在 http://royal.pingdom.com/?p=116 上有一个关于 2007 年前 20 个网站停机时间的有趣列表。全年实现 100.0% 的唯一网站是 Yahoo!；Google 实现了令人印象深刻的 99.995%，甚至使用 ColdFusion 构建的 MySpace 也实现了 99.98%。前 20 个网站的平均值为全年 99.987% 的正常运行时间——每月仅六分钟的停机时间。

在本章中，您还会看到冗余一词。在此语境下，冗余的含义非常具体 — 即在架构中引入通过提供到相同备份设备的故障转移来应对意外故障的能力。前 20 个网站在高流量下实现看似非常高的可用性水平，很大程度上依赖于冗余的使用。

就本章而言，高可用性是指全年正常运行时间为 99.75% — 可能低于前 20 个网站的预期，但远超典型的 PHP 网站。

#### 高流量

用于定义“高流量”的指标可能略有不同。Google、Flickr 和 MySpace 等网站每月实际收到数以十亿计的页面展示量。这当然属于“高流量”，但大型公司的网站呢？虽然 unilever.com 和 deloitte.com 等网站不是 B2C 应用程序，但它们每月仍有数百万页面展示量。与大型社交网络网站相比，这微不足道，但仍在许多 Web 开发者会认为属于“高流量”的范围内。

不过，实际上，这主要关乎认知和定位。请考虑一辆快速、主流、紧凑的汽车，例如 MazdaSpeed3。许多人会认为它是一辆快车；名称、外观、品牌——所有这些都指向对性能的强调。确实，它并非省油灯：0–60 英里/小时只需 5.9 秒。但将其与布加迪 Veyron 相比，后者在远不到一半的时间内即可达到相同速度，或者与一级方程式赛车相比，后者在马自达达到 60 英里/小时的同一时间内，轻松可达 140 英里/小时。

关键在于，这三种汽车都会被外行认为是快车。数字支持这一观点。当今市场上所有汽车的平均 0–60 英里/小时加速时间约为 13 秒。非黑即白地看，你可以认为 13 秒以下算“快”，13 秒以上算“慢”。

将同样的规则应用于 Web，可行网站（排除关闭的网站、链接农场、诈骗网站等）平均每月收到的页面展示量约为 100,000 次 — 每天仅 3,000 次。该数字之所以低，是因为 Web 无处不在。每有一个享受数百万点击量的商业 Web 运营，就有一千个运营只有几百个点击量，甚至更少。这与数学家所说的正态分布并不完全相同。

另一种看法是，任何其流量水平可能需要对硬件、软件或网络架构给予特别关注的网站，都可以被认为是“高流量”的。每月收到 150,000 个页面展示量的网站可以轻松在单台标准规格服务器上运行，可能使用相当普通的 Internet 连接。相反，在每月约 100 万页面展示量时，就必须对网站运行的硬件、其到 Internet 的连接以及底层代码的构建方式做出特别考虑。

那么，让我们在本章中以此作为衡量标准。任何每月页面展示量超过 100 万的网站都将被视为*高流量*网站。

#### 平台

您现在应该理解本章将把兼具高流量和高可用性需求的网站作为研究对象。确实，两者通常密不可分。高流量网站通常（尽管并非总是）是其资助者的商业成功，而这一成功取决于该网站持续的高可用性。Google 2008 年第一季度的网站收入为 34 亿美元 — 即每分钟 26,000 美元。您可以看到停机时间对 Google 盈利可能造成的影响。

更糟糕的是，高可用性在高流量情况下通常更难实现。大量 HTTP 请求对设备的不断冲击会迅速放大任何潜在的断裂点。

在考虑高流量下影响可用性的具体因素之前，值得简要识别和探讨构成应用程序*平台*的拼图碎片。您会发现，这远不止是开发语言的选择。这些组件中的许多都可能在阻碍您实现高可用性的目标方面发挥作用。

#### 外部网络

按定义，任何可通过 Internet 访问的 Web 网站或应用程序都必须拥有某种形式的外部连接。实际上，只有公司内联网往往不属于这一显而易见的要求。外部网络是指最终用户与内部网络之间的连接链路 — 通常是从用户的计算机一直到托管 Web 网站的设备上的终止路由器。

一般来说，企业级应用程序通常托管在*自主托管*或*代管*服务器上。在自主托管服务器场景中，网站背后的个人、公司或组织提供并管理服务器，而互联网服务提供商（ISP）提供放置服务器的空间。在代管服务器环境中，ISP 提供并管理服务器，网站背后的实体只需上传其应用程序。

但是，无论哪种情况，ISP 都有责任为该服务器提供合适的连接。它应该是*高带宽* — 换言之，总带宽（以兆比特每秒 Mbps 计）应足以容纳进站流量。值得记住的是，10 Mbps 的连接听起来很多，但仅足以支持五个并发的 2 Mbps 最终用户连接。幸运的是，HTTP 的间歇性意味着五个并发连接并不等同于五个并发用户，而更接近一百个。您将在本章后面了解这些假设背后的数学原理。





请记住，有些 ISP 会按流量计费，通常不提供具体带宽上限（即*承诺信息速率*，或 CIR），而是采用这种方式。从商业角度看，ISP 这样出售带宽通常更合理。出售 CIR 意味着 ISP 需始终保留相当数量的带宽，不进行超售。相反，许多 ISP 会将所有可用带宽汇总，按照先到先得的方式出售，并设置每月数据传输上限。这有时对网站有利，有时则不利。这基本取决于运气，取决于 ISP 总体是否繁忙。

如今，带宽相当便宜，但高质量带宽则相对较贵。质量的一个指标通常是*延迟*（通俗地说，*ping 时间*）。在实际中，这往往比带宽更重要。一个架构良好的网站理应更侧重内容，而非花哨的图形或视频。看看 Facebook。它在很大程度上只是纯文本，却因其易用性成为互联网上最受欢迎、最受推崇的网站之一。然而，这种易用性可能会因延迟不佳而受到不利影响，在 HTTP 语境下，这将表现为网站对用户活动的响应能力。如果与远程主机建立套接字连接需要半秒钟，那么该连接向连接的 Web 浏览器发回数据的速度就无关紧要了。最终用户体验将很差，因为服务器的响应能力会被认为较差。

当然，这一切都归结于 ISP，但请记住，在主机托管（与托管服务器相对）环境中，有些 ISP 倾向于将责任推给客户设备（即，争论连接链条中故障所在的位置，可能会声称是有故障的客户防火墙或交换机必须负责）。当然，这可以按需要轻松证明或反驳，但问题出现时，这确实是又一个需要跨越的障碍。

因此，尽可能保持内部网络良好运行非常重要，以便在解决连接速度和响应性问题时将其排除在调查范围之外。

## 内部网络

ISP 将连接移交给您设备的节点通常称为*交接点*。这种呈现方式取决于您从 ISP 购买的服务性质，但通常有两种提供方式。

在最简单的场景中，它以单个以太网端口、公共互联网上的一个地址范围以及同一网络子网内的固定网关地址形式提供。通常，您会将防火墙的外部接口直接连接到相关以太网端口，并将流量路由到给出的网关地址。防火墙的内部接口随后会连接到交换机，再由交换机为您的服务器提供连接。

在更复杂的环境中，连接可能以单个网关地址和*不同*子网上的地址范围形式提供。在这种情况下，您需要自备路由器，并将分配给您的网关地址绑定到该路由器上。接着，您需要自备防火墙，其外部接口连接到该路由器的辅助接口，路由器会监听所有提供给您的地址。然后，您的防火墙将其内部接口连接到交换机，您的服务器以常规方式连接到该交换机。

因此，您的内部网络设备必须能够处理适量的流量。负载取决于它在链条中的位置。边缘路由器处理网站*所有*的入站和出站流量。然而，它可以配置为拦截其认为不可路由的某些流量。因此，防火墙的负载通常略低于边缘路由器。

防火墙（在大多数情况下）也会过滤掉大量不需要的流量，这意味着内部网络交换机需要处理的流量略少于防火墙。在更大型的架构中，无疑会使用两台或多台服务器来交付内容，因此网卡的单个流量负载会更低——尽管服务器之间（非通过互联网）的内部通信很容易再次增加负载。

中端路由器通常可以毫无问题地处理约 10 Mbps 的流量。因此，明智的做法是寻找能够处理相近流量量的防火墙。您的交换机几乎肯定是 100 Mbps 的，但您应考虑服务器之间是否可能发生内部通信。如果数据库服务器和应用服务器是分开的，那么就会发生这种情况，提供每秒 1 千兆比特（Gbps）交换和 1 Gbps 网络接口卡（NIC）将实现最佳性能。

# 硬件

当然，您的应用程序必须运行在某些设备上，高可用性/高流量网站的典型配置至少包括一台独立的 Web/应用服务器和一台数据库服务器——即两台物理机器。

在 Web 早期，来自 Silicon Graphics, Inc. (SGI) 和 Sun Microsystems 等公司的高端硬件遍布全球的企业架构。这曾不是 Intel 感兴趣的领域，其 CPU 主要面向桌面环境。然而，如今基于 x86 架构的服务器级芯片很容易获得，而且价格低廉。事实上，与其他架构的竞争对手相比，它们便宜到在 99% 的应用中，采用 Intel 路线更具成本效益，即使这涉及使用两倍数量的物理机器。

不过，有两种趋势值得考虑。摩尔定律表明，处理能力大约每两年翻一番。因此，越来越多的企业架构师正在考虑虚拟化的优点。在这种配置中，集群中的一台或多台物理服务器通过软件模拟提供一台或多台虚拟（或可寻址）服务器。

好处众多。根据流量和负载调整应用程序的硬件基础规模的能力是最明显的好处，无需通常的成本和交付时间关联。通过在多台物理服务器上分配负载，还提供了一定程度的冗余；单点故障被消除。

第二种趋势（主要由 Google 推动）是使用普通硬件（现成的、非专业设备）来提供托管。这可能看不寻常，但请算算账。如果每台 500 美元的 20 台机器能提供与每台 1,500 美元的 15 台机器相同级别的冗余和性能，就不难理解为什么第一种选择更具吸引力。专用服务器硬件的主要优点——韧性、可靠性和寿命——被大规模数量和规模经济所抵消。

理论上，使用虚拟化将普通服务器合并为一个可寻址环境可以兼得两者之长——尽管值得记住的是，这是一项相对年轻的技术，即使在 2009 年，仍有待解决的问题。

# 操作系统

假设现代应用架构在很大程度上依赖基于 Intel 的硬件，操作系统的选择大致限于运行在 Intel 架构上且可用大量合适应用软件（Web 服务器、数据库服务器、应用服务器等）的系统。

除专业和小众操作系统外，大部分可用系统主要分为 Windows 和一系列 UNIX 变体。

在 Windows 方面，只有 Windows Server 系列操作系统适合用作 Web 服务器。基于 Microsoft 的 NT 架构，Windows Server 2003 和 2008 使用与 Microsoft 桌面操作系统等效版本（XP 和 Vista）相同的核心内核，但专门针对服务器角色进行了优化。在 Windows Server 2008 中，一项名为 Server Core 的新功能移除了面向桌面的 Windows Explorer 界面，提供了精简的、更类似 UNIX 的方法。

至于 UNIX 和类 UNIX 操作系统，选择则更加多样。当然，Linux 在 Intel 硬件上仍然是最普及、最流行的 UNIX 操作系统，这也有充分理由。它在很大程度上是免费的（取决于发行版），且支持极好，是一款出色的“全能选手”——几乎没有什么是它不擅长的。话虽如此，Apple 2005 年决定转向 Intel 架构，使 Mac OS X 能够作为基于 PHP 的架构的可行服务器操作系统进行竞争。（当然，购买者仅限于购买正版 Apple 硬件，这通常意味着 XServe 服务器设备。与 Dell 和 HP 等公司规格相似的通用服务器设备相比，这些设备价格更高。）

还有几个“非主流”的 UNIX 选项。Sun 最近发布了 OpenSolaris（可作为开源免费获得），它基本上是 Solaris，但移除或替换了专有和闭源组件。FreeBSD 仍受良好支持，并且在负载下偶尔可能比 Linux 更稳定。OpenBSD 在安全性和韧性方面享有极佳声誉。

在 UNIX 和 Windows 之间的选择往往取决于个人偏好；事实上，这在各地博客中是众多“圣战”的主题。然而，事实难以反驳。如您在本章后面将看到的，绝大多数高流量网站（微软自身拥有和运营的网站除外）仍然使用某种 UNIX 变体作为基础——Google、Yahoo!、Wikipedia、YouTube、Facebook，名单还在继续。

# Web 服务器

选择合适的 Web 服务器的重要性不容低估。对您网站的每一个请求都包含针对页面和相关资源的大量 HTTP 请求。这些 HTTP 请求中的每一个都会经过 Web 服务器之手。选择错误的一个，整个网站都面临风险。

标准仍然是 Apache。它在 UNIX 和 Windows 上都能运行，不过，坦率地说，在 Windows 上运行时相当糟糕。近 51% 的市场份额意味着它远超其最接近的竞争对手——截至撰写本文时，Microsoft 的 Internet Information Server (IIS) 约为 35%。它达到这一地位更多是默认的结果——因为它免费、支持良好，并且在任何一件事情上都不算特别糟糕。它在任何一件事情上也不算特别出色；因此，它成为“不需要思考”的选择。





近年来，IIS已经取得了长足进步。早期版本饱受安全问题之苦。同样严重的是，近年来其在负载下的性能和韧性也备受质疑。虽然这些缺陷现在已得到很大程度的解决，但一个事实依然存在：在Windows上运行IIS支持给定流量水平所需的硬件基础设施，比（也许）在UNIX上运行Apache所需的要更强大。

另一方面，某些专业Web服务器可以发挥重要作用：

- Squid (*www.squid-cache.org*/) 提供前端流量管理、缓存和负载分发。
- lighttpd 和 thttpd 是“轻量级”Web服务器，专为仅提供图片、CSS样式表和可下载二进制文件等静态资产而设计。
- 内核级Web服务器（如TUX和KHTTPD）为同一问题提供了更轻量级的解决方案，直接将Web服务功能构建到操作系统本身中。

如您在本章后面将看到的，Web服务器的选择通常取决于整体网络基础设施的选择。在较大的部署中，多台服务器通常可以运行不同的Web服务器甚至不同的操作系统，这一切都是出于最大化性能这一可敬的目标。

## 应用程序服务器

*应用程序服务器*的概念对PHP开发人员来说通常并不熟悉。因为大多数开发人员将PHP作为Web服务器的一部分运行（无论是作为模块、编译进去，还是（很少见）作为CGI模块），Web服务器和应用程序服务器被认为是同一件事。

当然，情况并非如此。应用程序服务器运行应用程序；Web服务器提供Web页面。这一比喻在Java 2 Enterprise Edition (J2EE)中得到了恰当的体现。Tomcat、JBoss或BEA/Weblogic等应用程序服务器确实可以通过HTTP接受请求，但它通常与前端Web服务器相耦合，由后者将请求转发给它。应用程序服务器通常支持Web服务器不具备的高级功能（如资源池、诊断以及对高级部署技术的支持）。因此，它们被恰当地认为对于提供简单网页和其他资产来说“大材小用”。

在PHP的语境中，“应用程序服务器”一词指的是直接将请求传递给PHP引擎的服务器。为了获得最佳性能，这通常是Apache，其中PHP被静态“编译进去”（而不是作为模块加载），以便单个可执行文件提供应用程序。如本章后面所示，添加静态资产服务器和前端缓存服务器可以实现流量的更智能分发，每台服务器各尽其职。

## 数据库

正如您所料，底层数据库的选择对任何高流量PHP应用程序都有重大的性能影响。预计针对应用程序页面的大部分HTTP请求都会调用某种SQL查询。因此，完成每个HTTP请求的速度完全取决于执行这些SQL查询的速度，以及（如适用）返回数据的速度。

本书大篇幅论述了这样一个事实：架构良好的PHP应用程序是与数据库无关的，因为诸如PDO之类的抽象层和像ORM之类的SQL生成技术提供了高度的可移植性。确实，在低流量级别，各数据库之间差别不大。

然而，在高流量级别，一切都发生了变化。人们常大谈MySQL运行`SELECT`查询的性能，但通过适当使用缓存和页面生成，其带来的好处会被抵消。远更重要的是，数据库处理那些本质上无法缓存或预先生成的事务的性能——例如，用户注册、搜索和Web 2.0功能（如即时通信和帖子评论）等操作。

此外，应用程序的可扩展性通常取决于“增加特定组件”的能力。数据库也不例外。就您选择的RDBMS而言，从单台数据库服务器扩展到两台、三台、四台或更多有多简单？

这种简单性由两个功能决定：集群和复制。**集群**使多个物理数据库服务器能够向连接设备呈现为单个虚拟数据库服务器，从而在此过程中分布负载。**复制**使所有这些数据库服务器始终持有相同的数据集，从而确保无论为给定请求选择哪个物理服务器，返回的数据都是相同的。

有些RDBMS比其他RDBMS更适合集群和复制。虽然本书是**PostgreSQL**的大力拥护者，但可以公平地说，其对集群和复制的支持完全依赖于诸如**Slony-I**和**Continuent uni/cluster**之类的针对PostgreSQL的第三方包。**MySQL**稍好一些，但即使其备受吹嘘的**MySQL Cluster**平台对于企业部署也充满了诸多限制。

相比之下，Microsoft SQL Server和**Oracle 11g**开箱即用支持大规模集群和复制。出于这个原因，令人遗憾的是，对于真正的高流量应用程序，仍然需要掏腰包。

## 软件架构

最后，值得考虑一个人为因素——如果不给予足够关注，这个因素很容易抵消在先前讨论的所有问题上遵循最佳实践所取得的所有成果。

无论在出色的服务器硬件、一流ISP、运营商级网络设备等方面花费多少资金，如果应用程序编写糟糕，都无济于事。糟糕的应用程序在压力下极易崩溃。

在第13章中，您了解了设计架构良好的PHP应用程序的基础知识——这些构建将可靠、安全、可扩展、模块化且易于维护。但是，架构良好的应用程序（通常情况下）在压力下表现会更好，仅仅是因为它防止开发人员犯下可能导致性能泄漏的人为错误。

或许同样重要的是，架构良好的应用程序的模块化特性意味着，在发现性能瓶颈时，*它们*更容易追踪、识别和解决。

## 影响因素

在考虑了任何Web应用程序的核心组件后，您需要了解每个组件在高流量水平下产生不良性能或低可用性方面所起的作用。

请记住，不可用不仅仅意味着应用程序将完全无法访问。它还可能意味着某些核心功能暂时被禁用。本章开头定义的指标是99.75%的可用性，但这意味着99.75%的时间所有功能都存在且正确——而不仅仅是其中一部分。

同样，如果性能达不到标准，可用性就毫无意义。许多因素会表现为性能不佳：

- Socket response time — 在扣除本地网络状况后，发起到Web服务器的套接字连接至连接建立所花费的时间。约50毫秒（ms）的时间是可以接受的。在本地网络延迟为20 ms的情况下，这意味着连接应在请求发出后70 ms内打开。
- HTTP latency — 在隔离网络延迟后，客户端发出HTTP请求（无论是GET、POST还是其他）到服务器开始向客户端返回数据所花费的时间。超过100 ms即为不佳。也就是说，在发出诸如GET /index.php之类的命令后，服务器应在100 ms内开始向客户端返回数据（无论是HTML还是其他内容）。
- Transfer rate — 数据传输的速率（以每秒位、字节或千字节为单位）。截至编写本文时，家庭连接轻松可达8 Mbps，因此您的基础设施支持体面的传输速率变得越来越重要，尤其是对于较大的文件，例如经常构成Flash电影和视频的二进制资产（最低约2 Mbps）。

因此，经验法则是，如果在高流量下您的应用程序无法在50 ms内响应套接字连接、在100 ms内响应HTTP请求，或以至少2 Mbps的速率传输数据，那么它就不达标。

考虑到这一点，哪些因素会影响负载下的可用性？

## 服务器负载

支持您的应用程序的每台服务器都处于负载之下。一般而言，流量越大，负载越重。随着流量水平（以页面浏览量计）增加，Web服务器、应用程序服务器和数据库服务器都将对其系统资源（内存、CPU和磁盘）承受越来越大的压力。

计算机能够同时执行多个操作的能力（从技术上讲即多任务和多线程）在某种程度上是个神话。每个CPU一次只能执行一条指令。每个硬盘一次只能读取或写入磁盘的一个部分。但是，硬件控制器和操作系统本身提供的表面功夫，使多任务处理成为可能。

这种幻觉实际上是一个简单的轮询。如果两个任务正在竞争CPU时间，CPU会在两者之间交替，每个时钟周期一次，尽管不一定是50/50的比例。磁盘和内存通常以相同方式工作。当前未被服务的请求实际上被保存在队列中。随着负载增加，该队列会变长，排队等待的时间也会随之增加。





因此，在负载过重的情况下，任务完成时间会更长，因为每个服务器都要处理更多数量的任务。因此，投入到每个任务中的资源比例更小。根据哪个服务器是罪魁祸首，负载可能以不同方式表现出来。过载的Web服务器可能会提供糟糕的套接字响应时间，而过载的数据库或应用程序服务器可能会影响HTTP延迟。不过，只有负载极其严重的服务器才会运行得足够慢以影响传输速率。毕竟，网络传输速率比内部总线传输速率低许多个数量级。

在这里，数据库服务器通常是最大的罪魁祸首。在典型的PHP应用程序中，单次访问对Web服务器来说可能微不足道，因为它只需响应单个HTTP请求。对应用程序服务器来说，这可能稍微大些，因为它必须运行必要的PHP代码。但对数据库服务器来说，这却是一件大事，因为它可能需要执行几十或几百个查询。

因此，数据库服务器通常是第一个宕机的。在本章后面，您将了解一些合适的缓解技术。

## 组件故障

当然，应用程序基础设施中无数物理组件都可能发生故障——路由器、交换机、网卡、网线、主板、电源、硬盘、内存芯片、CPU等。

如果您的应用程序架构曾出现单点故障，那么任何一个组件的故障都可能导致立即停机。幸运的是，在几乎每一个可能的故障点上，都有缓解策略。

只有一种物理组件具有机械运动部件：硬盘。因此，只有硬盘才有固定寿命，其寿命与流量水平成反比。话虽如此，现代硬盘（即使在高负载下）也能使用多年。

## 网络负载

您内部网络基础设施中的大部分都能实现远超外部互联网连接的吞吐速度。即使是廉价的以太网交换机也能达到100 Mbps。您从ISP那里可能得不到接近这个速度的带宽。

然而，延迟是另一回事。随着以太网设备（交换机、路由器和网卡）负载的增加，打开和关闭连接的速度会下降。因此，高流量可能导致过高的延迟，从而降低用户体验。

## 网络故障

无论您的ISP多么昂贵，偶尔的中断都难以避免。如果您ISP的核心路由器损坏，那么没有流量能到达您的网站，也没有流量能发出。换句话说，您的网站就宕机了——就这么简单。

在使用传统ISP时，很难缓解这种情况，事实上，知名网站遭受的大部分停机时间都是由ISP故障引起的，而不是由更险恶或更复杂的原因造成的。

## 缓解技术

乍一看，前面的所有讨论都相当令人生畏——一长串在您的网站承受负载时可能出错的事情，所有这些都可能导致不可用性或性能不佳。

幸运的是，可以部署大量策略来几乎保证正常运行时间。Yahoo!一年内达到的100%可能是个偶然，但本章前面提到的99.75%肯定是可以实现的，您将会看到。

### 负载均衡

对于可能每天只服务几千个页面展示量的小型网站，单服务器配置很常见。在这种情况下，网站的主机名（也许是www.example.com）将在DNS中解析为互联网上的单个公共IP地址。然后该IP会绑定到服务器上，或者更常见的是，绑定到防火墙上，防火墙在过滤流量后将其转发到服务器。该服务器将运行合适的操作系统、Web服务软件、数据库平台和应用程序语言。最常见的配置是Linux、Apache、MySQL和PHP，通常简称为LAMP。

在负载均衡环境中，会设置两台或多台服务器来共享网站流量产生的HTTP请求负担。这样，网站就能处理超出单台服务器成功处理能力的流量。

然而，这并非完全是线性关系。平衡Web服务器非常容易，但如您稍后将看到，数据库服务器、交换机等更难以实现冗余。

负载均衡传统上有两种实现方式：通过DNS或使用硬件负载均衡器。

### DNS负载均衡

使用DNS，可以通过将单个主机名（例如www.example.com）指向一个或多个IP地址（而非单一IP地址）来将流量分布到两台服务器上。在DNS区域文件中，合适的条目如下所示：

```
$ORIGIN example.com.

www	IN	A	10.0.0.1
www	IN	A	10.0.0.2
www	IN	A	10.0.0.3
```

每次访问您的网站都会导致针对主机名的DNS查询。名称服务器返回的与该主机名关联的IP地址是随机的。因此，最终接收与访问网站请求关联的HTTP流量的服务器也是随机的。理论上，如果DNS条目关联了两台服务器IP地址，那么每台服务器应接收50%的流量。这确实能达到分发流量的预期效果，而且成本低廉，但至少存在一些缺点。首先，最主要的是，为单个主机名分配多个公共IP地址是浪费的。颁发IP地址的机构（尤其是在当前极度超额认购的IPv4地址空间中）正在打击无理请求，大多数新订单都需要以非常详细的方式证明需求。仅有两台服务器时这可能不是问题，但如果您的网站扩展到八台或更多，您可能会遇到麻烦。

还存在另一个更微妙的问题。DNS查询几乎总是被缓存——至少在浏览器访问网站的整个生命周期内都会缓存。这意味着与单个会话相关的所有流量（考虑到底层HTML、CSS、JavaScript、图像和其他外部资源，可能高达30个左右的请求）通常会访问同一台Web服务器。因此，一次漫长的10分钟网站会话可能导致500个HTTP请求，全部打在一台服务器上。然而，另一个访问者快速的30秒访问可能仅包含50个请求。在这种情况下，您可以计算两次网站访问，但绝对不能说两台服务器之间有50/50的流量分布。在数百次访问过程中，这种差异可能会更加明显。

您还必须警惕使用自有DNS缓存的ISP。在这种情况下，提供给最终用户的DNS服务器实际上是DNS缓存设备。它们可能仅在四五天的周期内执行一次查询，然后缓存结果。严格来说，这违反了DNS区域文件中定义的所谓生存时间（TTL）规定，后者通常禁止缓存超过几分钟。但是，考虑到ISP每天必须处理的海量DNS请求，您可以理解它们为何违反规定。

违反规定对ISP来说带来了好处。为了满足基本的用户DNS请求，需要走“外网”的流量少得多；但结果可能导致DNS负载均衡失效。某个主机会被解析到特定的IP地址，并且该单一IP地址会被ISP缓存。因此，直到缓存条目“过期”之前，这就是提供给ISP最终用户的唯一IP地址。任何使用此ISP的用户都根本无法进行负载均衡。

还有后勤问题。服务器时不时会发生故障。DNS负载均衡没有考虑到这一点，因为DNS区域文件“不知道”哪台服务器宕机，哪台服务器正常。更进一步，服务器会“生病”。有些服务器的负载会高于其他服务器，因此理应分担较少的网站流量。

### 硬件负载均衡

使用硬件负载均衡可以解决所有这些问题——这是一种更具企业级水准的方法，价格也相应不菲。在这种情况下，一种称为负载均衡器的专用设备充当所有访问您网站流量的哨兵。它会根据具体情况将单个HTTP请求重定向到两台或多台Web服务器。这通常基于简单的“轮询”方式，但有时也会考虑服务器可用性、服务器负载和请求类型等因素——例如，可能会将请求定向到资源服务器（稍后讨论），但将PHP脚本请求定向到专用应用程序服务器。

企业级负载均衡器本身也可以实现冗余或集群，通过专有协议、连接器和电缆（有时称为心跳链路）共享负载。这样可以在负载均衡器发生故障时提供冗余，并允许流量极大的网站在多个均衡设备之间共享负载。





这样的企业级套件可不便宜——专用设备要 30,000 美元或更多。这笔成本通常不是硬件——负载均衡器通常只是普通服务器 PC——而是运行在该设备上的软件和操作系统的许可成本。这些高昂成本意味着一些架构师会仔细考虑自行开发。Squid (http://wiki.squid-cache.org/SquidFaq/ReverseProxy) 提供了负载均衡功能的基本子集，在实践中，可能对大多数读者来说已经足够。那些寻求商业解决方案的人最好去 www.f5.com 查看 F5。

## 地理负载均衡

毫无疑问，在服务器之间分配负载是充分利用现有硬件的好方法，也便于以后通过添加更多服务器来轻松扩展。

然而，随着网站性质日益全球化，连接主机的分布也随之全球化。一个全球网站可能会收到来自世界各地的流量。正如你所料，流量传输距离越远，用户体验就越慢。例如，澳大利亚的用户连接到英国的服务器，流量需要往返 20,000 英里——这可算不上飞快。

显而易见的解决方案是在全球四角部署服务器，使用户永远不会离托管所需内容的服务器太远。一个真正的全球网站可能会在洛杉矶、纽约、伦敦、东京、悉尼、孟买和上海设有服务器。这样的设置可以将 99% 流量的总“跳数”降到绝对最低。

假设所有用户都使用相同地址（例如 www.example.com）访问网站，流量如何到达离他们最近的服务器？将远程用户的 IP 地址映射回大约地理位置是一项相当容易的任务。众多数据库（其中一些是免费的）为开发者提供了实现此类解析的简单资源。MaxMind GeoIP (www.maxmind.com) 就是一个很好的例子；但有了这样的数据库，有几种可能的方法可以将初始流量引导到正确的服务器。

最简单的方法是以标准方式接受 www 上的流量，但随即将用户重定向到专门针对他们的（且地理位置附近）主机。例如，来自伦敦的用户可能通过 http://www.example.com 访问你的网站，但随后会立即被重定向到 http://london.example.com。

虽然这种方法足够好用，但有几点需要注意：

- 首先，也是最重要的是，对 www 的初始请求仍需传输相当长的距离，因此性能仍可能受到影响。
- 其次，你会让搜索引擎更难索引你的网站。将核心内容放在 www 以外的主机下不是个好主意。
- 第三，人们互相发送链接存在风险。如果伦敦的用户向东京的用户发送链接，收件人不太可能考虑相应调整 URL。

有一个解决方案：地理负载均衡，即使用 DNS 根据用户位置分配负载。当对初始记录 (www.example.com) 进行查找时，通常是针对用户 ISP 的 DNS 服务器进行的。幸运的是，该用户的 ISP 通常与用户位于同一国家。因此，当该 DNS 服务器将请求转发到网站域（即 example.com）使用的名称服务器时，该名称服务器可以根据远程 IP 地址发出动态响应。这样一来，www.example.com 解析到的 IP 地址会根据远程用户的位置而变化。因此，来自首个请求的流量就会命中正确的服务器。

不过，两种方法都面临一个挑战——保持内容同步。假设世界各地的用户都应该获得相同的内容，则这些服务器必须不断相互复制。在代码和静态内容方面，可以使用计划任务和诸如 rsync 之类的同步软件轻松实现。当然，数据库更加复杂。这一点将在本章后面提及。

## NIC 联合

在消除单点故障的值得称赞的探索中，网络设备故障的潜在风险常常被忽略。如果服务器必须在单个 IP 地址上侦听和响应，那么拥有两个网卡、两个交换机和两个防火墙又有什么用呢？

通过使用 NIC 联合（有时也称为链路聚合），两个物理网卡可以共享一个 IP 地址。这样一来，两个网卡可以共享负载。如果其中一个出现故障，就提供了一定程度的冗余。此外，别忘了网线也可能失效。这种策略也应能缓解这一问题。

通常，每个网卡连接到自己的交换机，以防交换机成为单点故障。由于交换机只知道硬件地址（而不知道逻辑地址），交换机级别不需要特殊配置。两者只需保持分离，不相互连接。然而，在服务器上，操作系统必须配置为支持 NIC 联合。有时还需要更改 BIOS。有关进一步阅读，请参阅 http://en.wikipedia.org/wiki/Link_aggregation。

平衡路由器和防火墙更棘手。一般来说，需要一个心跳连接，让一个设备作为热备“待命”，而另一个处于活动状态。如果活动设备故障，备用设备可以自动接管。实现方式因设备和制造商而异。在大多数情况下，您的 ISP 应该能提供帮助。

## 磁盘容错

如今的硬盘比过去可靠得多。在典型使用和典型流量水平下，大多数小型计算机系统接口（SCSI）、串行连接 SCSI（SAS）和串行高级技术附件（SATA）磁盘可使用五年或更久——远长于服务器本身的典型寿命。

不过，磁盘也会不时发生故障；如果你的 Web 应用程序依赖于单个磁盘，那就是自找麻烦。故障不仅会导致停机，而且从备份手动恢复丢失的数据（假设你有备份）也会非常麻烦。请记住本章前面提到，Google 每分钟停机会损失 26,000 美元的收入。这有助于保持正确的视角。

解决方案是独立磁盘冗余阵列 (RAID)。在这种情况下，多个物理硬盘组合成一个单一的虚拟容器。操作系统只看到一个磁盘，RAID 控制器负责在需要时将数据读写到正确的磁盘。

取决于配置，这可以带来许多优势。在最常见的配置之一 RAID 5 中，条带和镜像方法意味着多个硬盘提供更大的高容量机会，并且任何一个磁盘可以完全故障而不会中断服务，也不会丢失数据。你可以配置控制器在发生此类情况时通过电子邮件甚至可能短信服务 (SMS) 通知你。你只需获取一块新磁盘，移除旧磁盘，然后插入新磁盘。RAID 控制器会处理其余事项，逐渐使新磁盘“赶上进度”，并在同步后重新上线。

RAID 还带来性能优势。数据通常分布在磁盘物理盘片的各处。如果虚拟磁盘需要快速连续从两个不同位置读取数据，那么与其让磁头在这两个位置之间“跳跃”，不如让两个物理磁盘各自负责传送每个数据块。这样一来，执行磁头跳跃所需的时间就被消除了。这可能看起来不多，但在高负载下却能带来巨大差异。

要真正发挥 RAID 的优势，需要比简单宣布“全面采用 RAID 5”更聪明一些。RAID 5 虽然读取速度极佳，但写入性能较差，因此可能不适合用于频繁写入的磁盘。

通过在不同磁盘上混合使用不同的 RAID 级别，可以实现最佳性能。例如，你可能决定将操作系统引导分区放在两个磁盘的单个 RAID 1 镜像上，提供冗余和出色速度，但没有增量容量。随后，你可能决定将交换卷放在没有任何 RAID 的单个磁盘上，因为该磁盘故障不太可能影响任何关键内容。应用程序数据可能放在另外三个磁盘上，这些磁盘可能构成一个 RAID 5 卷。

有关选择适合你的 RAID 级别，请参阅 http://en.wikipedia.org/wiki/Standard_RAID_levels。请记住，不同服务器执行不同角色。Web/应用程序服务器绝不应存储可变数据；因此，重点应放在性能而非冗余上。数据库服务器既需要快速又需要冗余，因此 RAID 5 或 RAID 6 是更好的选择。

监控和通知至关重要。在磁盘发生故障（或即将故障）时，及时更换很重要。部署可以在磁盘暂时离线时通过电子邮件通知你的软件，可以提供早期预警系统，表明磁盘即将故障。然后你可以立即重新订购和更换。毕竟，降级的 RAID 阵列可以说不比没有 RAID 好。

## 电源冗余

大多数服务器配备两个电源和两个电源连接器，通常为 IEC60320/C14 类型（请参阅 http://en.wikipedia.org/wiki/IEC_connector）。只要可能，应始终连接两者，但请记住，这可能（取决于制造商）使服务器的功耗翻倍。采用此设置后，如果一个电源故障，服务器将继续运行。





## 第四部分：将 PHP 推向极限

同样，你应确保操作系统层面可用的所有监控电源的实用程序都已安装，并配置为在电源故障或电压开始超出可接受容差范围时（这可能预示着即将发生故障）通知你。

同时，确保你的 ISP 数据中心为你的设备提供充足的电源供应。这意味着电源应由受控不间断电源（UPS）支持，以应对短期的电压浪涌和欠压。不过，背后还应配备柴油发电机，以便在更长时间的停电中提供一天或更长时间的电力。

不过要小心，因为随着全球能源价格上涨，ISP 对电力的要求变得越来越严格。大多数情况下，很难在一个 42U 机架中填满服务器，而这些服务器的电力需求恰好能在 ISP 每个机架设定的限制范围内得到满足。此处需格外小心。如果对机架的用电负载过大，你可能会发现仅仅跳闸了一个保险丝——整个机架就全部报废了。

## 多段拓扑

在典型的高流量环境中，多台服务器将分别用作 Web 服务器、数据库服务器、应用服务器和资源服务器。如图 23-1 所示，在基本的多服务器配置中，这些服务器通常都位于同一个以太网段上。这意味着所有服务器之间都有物理链接，并且可以相互自由通信。

![](img/a1b732997d9cb194dceec0570dc79710_609_0.png)

图 23-1：传统以太网分段

从严格意义上讲，这种配置没有问题，但请考虑防火墙后面服务器的性质。它们真的都需要相互访问吗？同样，来自互联网的流量是否真的需要到达它们？如果其中任何一个问题的答案是否定的，那么你可能需要考虑将服务器放置在独立的以太网段上，如图 23-2 所示。

![](img/a1b732997d9cb194dceec0570dc79710_610_0.png)

在双以太网配置中，两台服务器配备双网卡。一块网卡将它们连接到“外部网段”（该网段可访问防火墙，按定义也可访问互联网），另一块网卡（在不同子网上拥有独立 IP 地址）将它们连接到“内部网段”（该网段不可访问互联网）。

这种配置的好处在于，它从物理上阻止了不需要通信的服务器之间的交互。通常，数据库服务器会设置在“内部网段”上，这意味着无论防火墙规则如何，外部世界都无法物理上访问数据库服务器。安全性因此得到加强。无需担心防火墙规则配置错误，因为根本不存在需要配置的规则。不过，通过那个辅助网卡，Web 服务器仍然可以与数据库服务器通信，反之亦然。

另一大优势是速度。Web 服务器和数据库服务器之间有专用链路，这意味着通信不必与普通 Web 流量争夺带宽。

如果需要，还可以将分段推进到另一个层级。如果将 Web 服务器、应用服务器和数据库服务器分开，每台都可以位于自己的以太网段上。只有 Web 服务器对外部世界公开可访问，并位于外部网段，它们将 HTTP 请求传递给中间网段上的应用服务器。这些应用服务器反过来访问位于内部网段上的数据库，如图 23-3 所示。

![](img/a1b732997d9cb194dceec0570dc79710_611_0.png)

## 图 23-3：三层以太网分段

这进一步提升了隔离级别。唯一能访问互联网的设备是外部网段上的 Web 服务器。

不过这里有一个“陷阱”。你的应用服务器很可能需要访问互联网，以便发送电子邮件和调用外部 Web 服务。在上述架构中，它们没有互联网访问权限，只能与数据库和 Web 服务器通信。可以通过在外部网段提供 HTTP 代理和邮件服务器来缓解此问题。你的应用服务器随后可以在需要时使用这些服务。

## 数据库集群与复制

本章前面你已经了解到，使用硬件负载均衡器，甚至多个 DNS 记录，在 Web 服务器之间实现负载均衡相对容易。

这样做可以将流量分散到多台服务器上，从而消除单点故障。如果一台 Web 服务器宕机，另一台可以分担压力，尽管最终用户的性能会有所下降。

不过，对数据库服务器做同样的事情则更棘手。以 `SELECT` 开头的查询很简单——你可以使用与在 Web 服务器之间分发 HTTP 流量完全相同的方法来分发它们。但任何_修改_数据的查询（主要是 `UPDATE`、`DELETE`、`INSERT` 等等）都必须发送到_所有_服务器；否则，服务器将不同步。

此外，如果数据库服务器离线几个小时，当它重新上线时，必须先更新到最新状态才能重新加入池中；否则，其数据可能与其他服务器不同步。

所有这些及更多功能都通过一种称为_集群与复制_的技术实现。_集群_一词指的是将多台数据库服务器汇集为单一单元的能力，这样连接的应用程序只需感知集群，而无需感知组成集群的数据库服务器。通过集群，实现了容错（即任何一台服务器故障都不会影响数据库的可用性和完整性），以及负载均衡（即负载通常在服务器之间均匀共享）。

相比之下，_复制_简单地指两台不同的数据库服务器使其部分或全部数据库相互保持同步的行为。正如你所料，你可以在没有集群的情况下实现复制——但没有复制就不可能实现集群。

如何实现其中一项或两项，在很大程度上取决于所选 RDBMS。这是 MySQL 目前还不够出色的一个领域。虽然新发布的 MySQL Cluster 确实按传统意义上提供了集群功能，但它存在显著限制——其中最重要的是其内存需求，以及节点在故障后自动恢复的能力。MySQL 复制功能已经存在多年，但它本身并不提供负载均衡。你的代码需要补足这一不足。它也是异步的，这意味着数据库更改传播到对等节点之间存在固有延迟。

多年来支持一直很差，但在 PostgreSQL 方面最近取得了巨大进展。例如 pgpool-II 支持连接池、负载均衡、复制，甚至并行查询处理，这意味着复杂查询的负担可以分摊到参与的数据库之间。在商业级别，uni/cluster for PostgreSQL 提供了几乎即插即用的操作。

正如你所料，两大商业巨头——Oracle 和 MS SQL Server——开箱即用支持集群和复制。

最后再谈这一点。数据库集群与复制并非万能药——大多数情况下，它是可以避免的。使用缓存、代码生成和资源服务，可以将发往数据库服务器的流量降至最低，并尽量减少数据库离线的实际影响。

## 流量微积分

“流量微积分”一词近年来应运而生。它指的是一门致力于理解 Web 站点流量形状的数学分支。

例如，考虑为某电视频道推出新网站。该网络的首席执行官可能会告诉你，每月预计有 1000 万次页面展示量。合理地假设，这种流量可能会在整个日历月内相当均匀地分布（也就是说，没有迹象表明第一周的流量应该高于第二周，或者反过来）。先进行基本计算，你因此可以确定，每周你的网站预计可获得约 230 万次页面展示量。





## 第四部分：将 PHP 推向极限

你可能会假设（基于合理的猜测或其他地方可用的数据），网站 40% 的流量可能发生在周末，60% 发生在工作日。这表明流量偏向周末。因此，你可以推断，从流量角度来看，你最繁忙的一天很可能是周六或周日。如果两天流量相当，你可以假设在周六或周日，你的网站将收到大约 461,000 次页面展示。

不过，在一天之中，这种流量不太可能保持不变。你可以采用一个工作理论：每天 60% 的流量可能发生在下午 3 点到下午 6 点之间，因为该网站支持一个每天下午 3 点开始、下午 4 点结束的电视节目。这意味着在那三个小时的时间段内，网站可能会收到每天 60% 的页面展示量，即 276,000 次展示。

你还可以进一步假设，在那三个小时的时间段内，下午 3 点到 4 点可能占那段峰值流量块的 20%，下午 4 点到 5 点（紧随其后的一个小时）占 50%，下午 5 点到 6 点占剩下的 30%。因此，你的高峰小时是下午 4 点到 5 点，届时你可以预期大约 138,000 次页面展示。

使用微积分，你可以假设在那一个小时内，页面展示量大致会按照正态分布进行分布，峰值出现在整点后五分钟。通过绘制一个均值为五分钟的正态分布图，你可以尝试不同的标准差和 Y 标量值，直到找到一个“符合”你预测流量的形状。这一点在图 23-4 中得到了很好的说明。

![](img/a1b732997d9cb194dceec0570dc79710_613_0.png)

图 23-4: 高峰小时的流量

作为一种正态分布，曲线在均值点的梯度（dy/dx）将等于零，该点已被规定为整点后五分钟。因此，通过计算 x 等于 5 时曲线的 y 值，可以计算出每分钟的峰值页面展示量：大约每分钟 2,800 次页面展示。这一点可以通过快速目视检查图表来验证。

如果一个页面展示包括一次针对页面的 HTTP 请求，接着是大约 20 次用于图像、CSS、JavaScript 和其他资源的请求，总“重量”为 100 KB，因此你可以假设在那一分钟内达到峰值传输量 280,000 KB。这相当于 37 Mbps。就 HTTP 请求而言，如果每个页面展示包含 21 个 HTTP 请求，你需要能够处理每秒 980 个 HTTP 请求的吞吐量。

# 第 23 章：处理高流量和高可用性

因此，在这个练习中，你已经能够计算出你假设的网站在带宽和每秒请求数方面的“最坏情况”。

你如何使用这些数据取决于你。例如，你可以在与 ISP 的合同谈判中使用你的峰值 Mbps 数值——也许要求 10 Mbps 的连接，并在需要时能够“突发”到 100 Mbps 而无需支付额外费用。

你也可以寻求确保你的整个基础设施能够处理每秒 1,000 个 HTTP 请求的峰值，也许可以使用诸如 LoadRunner 之类的负载测试软件来实现这一点，甚至可以编写自己的测试脚本来模拟负载。

无论如何，你都使用了一个简单的数学练习，将一个商业目标——每月页面展示量——映射到真实的技术需求。当然，你是通过假设才得出结论的，但企业一直在使用假设。至少你所指定的基础设施背后有一些逻辑。

### 缓存

PHP 快速且轻量，架构良好的 PHP 应用程序运行迅速，只需要相当普通的硬件支持。尽管如此，在任何可以节省资源的地方，你都应该这样做，页面缓存使你能够做到这一点，即仅在真正需要时执行代码。

通过使用某种缓存方式，对 Web 应用程序的每个请求都会仔细检查，如果可能，会在不执行底层代码的情况下（甚至根本不执行代码）将其交付给客户端。结果，你的应用服务器——也许还有数据库服务器——的负担减轻了。这是通过在首次请求时缓存输出（即存储一份副本）来实现的。

一般来说，请求的 URL、HTTP GET 和 POST 参数以及 Cookie 都会被检查。这四者的组合提供了一种“唯一键”。如果最近过去生成了基于这四个参数的相同请求，内容将从缓存中检索并发送给最终用户；否则，代码将正常执行，但输出会被捕获并存储在缓存中。“最近”一词几乎总是使用缓存过期常量来定义；大约两小时左右是常见的。

缓存可以在许多点进行。PHP 本身可以执行缓存。你可以轻松地对代码进行设置，通过使用 `md5()` 函数将 `$_POST`、`$_GET`、`$_COOKIE` 和 `$_SERVER["REQUEST_URI"]` 序列化为一个唯一键来检查输入参数。你也可以同样轻松地使用 `ob_get_contents()` 捕获输出缓冲区内容。通过这样做，你可以使用简单的条件语句来确定是否继续执行脚本，或者是否从缓存中提供内容。

你还可以在数据库访问点进行缓存。你可以轻松地在 PDO 之外创建一个包装器，例如检查正在进行的 `SELECT` 查询，如果在过去几个小时内进行过相同的查询，则拦截对数据库的调用，并改为从内存或磁盘中检索缓存响应并返回。

在请求点使用专用缓存代码也并不罕见，特别是当与负载平衡结合使用时。在这种情况下，负载平衡设备确定何时将用户请求转发到（其中一台）Web 服务器。它可能仅从缓存中提供内容，特别是在 HTTP `GET` 请求的情况下。

无论你使用什么缓存技术，都存在潜在的陷阱。在部署新内容时，如果内容在缓存过期前几个小时内不可见，你的内容创作者可能会感到沮丧。因此，你可能需要提供一种手动机制来“刷新”或以其他方式重置缓存，以提前新内容的可见性。此外，如果你在多服务器的负载平衡环境中使用缓存，你必须确保它们的缓存始终同步；否则，用户可能无法从一个请求到另一个请求获得一致的内容反映。

这些陷阱除外，缓存提供了一种最大化基础设施能力的绝佳方法。一个好经验法则是：如果你不需要运行 PHP 代码，或者不需要访问数据库，那就不要去做。

### 内容生成

与缓存类似，“内容生成”的概念考虑到了这样一个事实：普通的 Web 服务器非常擅长提供静态内容——即完全无需任何处理，直接从硬盘读取的文件。

在这种情况下，你的 Web 应用程序中的页面（尽可能）会预先生成静态 .html 文件及相关图像。考虑另一种方案：一个复杂的 PHP 脚本，在每个请求中使用数据库动态构建页面。如果该页面每小时变化不大，那么“离线”生成它并将结果保存到磁盘是有意义的。这样，用户不需要等待页面重新生成。当然，仍然可以使用数据库。区别在于，只有重建页面的脚本才会访问数据库。用户请求不会接触数据库——它们会获得静态 HTML。

这项技术在 BBC 新闻网站 http://news.bbc.co.uk/ 上被很好地应用，该网站每天收到数亿次访问。你看到的几乎所有内容都是使用 PERL 脚本静态生成的——简单的 PERL CGI 脚本仅在需要时提供动态功能 _仅在需要时_。这不算高科技，但它确实能应对流量，即使在 9/11 等重大世界新闻事件期间也是如此。

在开发周期中，你可能会遇到 Web 应用程序中“接近静态”的页面——也就是说，除了一小块动态区域外，它们从一个请求到另一个请求都是一致的。也许页面右下角有一个新闻滚动条，或者有一个小登录标签，显示“你未登录”或“当前以 Ed 身份登录”，或类似内容。如果不是因为那个小小的动态区域，整个页面本可以静态生成。

在这里，如果你想坚持自己的想法并采用代码生成路线，你有几个选择。第一个是使用 IFRAME 或 JavaScript。在这种情况下，发送给客户端的 HTML 是相同的，但客户端被指示请求一个始终动态生成的 JavaScript 片段或单独的 IFRAME。生成这些内容片段仍然有服务器负担，但远低于生成整个页面所需的负担。然而，这确实对搜索引擎可见性和可访问性有影响，因为搜索引擎和屏幕阅读器通常无法读取 JavaScript，并且通常会忽略 IFRAME，认为它们是广告。

第二个选择是使用服务器端包含（SSI），这是生成的 HTML 中的一个简单“标签”，告诉服务器何时引入外部资源。与普遍的看法相反，使用 SSI 引入一段 PHP 来生成那个动态片段是完全可能的。例如，考虑如何使用 SSI 包含一段 HTML，如下所示：

```
<!--#include virtual="header.html" -->
```





你可以改为包含如下所示的一段 PHP 代码：

```
<!--#include virtual="loginstatus.php" -->
```

请记住，这段代码将在服务器端执行，而不会由客户端浏览器调用，因此无法获取原始 HTTP 请求中传递的任何 Cookie。

## Asset Servers

提高 Web 站点基础架构性能的一个简单方法是使用专用的 _资产服务器_ 来提供本质上静态的内容片段（也就是说，这些内容永远不需要通过 PHP 或任何其他动态内容生成引擎）。在编写 HTML 时，您只需将 `` tags` 等指向您的资产服务器，而不是 `www`。

本质上静态的内容示例包括图片、CSS 样式表、JavaScript 文件、Adobe Flash 电影和简单的 `.html` 文件。由于这些内容都不会包含 PHP，为什么要通过配备 PHP 的服务器来交付它们呢？

诚然，Apache 等 Web 服务器足够智能，只有在必要时才会调用 PHP，但 Apache 远非用于提供此类内容的最佳 Web 服务器。它是一大段代码，远非精简——它会执行许多你不需要的操作。出于这个原因，你可能希望在资产服务器上运行其他东西——也许是 Boa、lighttpd 或 thttpd（自行 Google 其中任何一个）。如果你真的专注于榨干基础架构的每一滴性能，那么像 TUX Web 服务器这样的东西怎么样呢？它直接内置于 `linux` 内核中，使你能够构建一个 _什么也不做_ 而仅提供静态 Web 页面的服务器——而且速度非常快。

## Content Delivery Networks

_内容分发网络 (CDN)_ 是性能调优工具箱中较为昂贵的工具之一，但也是最有效的工具之一。在实践中，CDN 由第三方公司提供，这些公司同意代表你托管大量经常请求的静态内容（通常是图片、音频、视频和二进制下载），并直接将其交付给最终用户。这使你能够专注于托管核心基础架构。

在实践中，CDN 只不过是采用本章前面探讨过的许多技术的专门 ISP，包括地理负载平衡、硬件负载平衡和静态资产服务器；但通过大规模构建基础架构，它们实际上正在进行集中采购，因此通常能够以比那些尝试在较小规模上自行操作的单位低得多的成本提供大规模交付。它们实际上也具有“无限”容量。随着你的网站变大，你只需支付更多费用即可。

对于大规模部署，CDN 是有意义的，但请先算算账。

## Real-World Examples

最后，值得看看世界上流量最大的几个网站是如何应对的。这些网站的流量可能远超大多数读者自己项目（或其雇主项目）的最疯狂梦想，但它们在展示最佳实践方面值得关注——而且还在使用 PHP。

### Flickr

Flickr (www.flickr.com) 由 Yahoo! 运营，是世界上最成功的照片共享网站。它在数百个国家/地区为数千万用户提供服务，并提供超过 20 亿张图片。除了本身是一个受欢迎的目的地外，它还经常被博客作者和其他 Web 2.0 体验的贡献者用作托管其自身照片的引擎，从而节省了可能昂贵的带宽账单。至今，Flickr 仍然（基本上）免费使用，这无疑是其吸引力和受欢迎程度的一部分。

### Database Configuration

Flickr 使用 MySQL 复制（而非集群）解决方案。在此环境中，有一个“权威”的单一主数据库。有疑问时，主数据库永远是正确的。它使用 MySQL 复制异步复制到许多从数据库，这些从数据库始终持有该主数据库的相同副本。

一个定制设计的硬件负载均衡器在各个数据库服务器之间分配流量。所有 SELECT 流量都发送到多个从数据库之一；UPDATE、INSERT 和 DELETE 流量仅发送到主数据库。这样一来，PHP 代码无需进行任何特殊调整来相应路由数据库流量。

不过，会有轻微的“从库延迟”——即主数据库更新到该主数据库复制到所有从数据库之间的时间。由于从数据库专用于所有 SELECT 查询，所选的从数据库可能无法完全“同步”的可能性很小。这会对 Flickr 用户产生奇怪的影响，例如向相册上传新照片时，照片会短暂消失。

### Web/Application Servers

正如你所料，Flickr 的前端由成百上千台服务器提供支持。DNS 中不执行任何负载均衡——无论是地理上的还是其他方式。无论在世界哪里解析 www.flickr.com，你都会得到一个单一的唯一 IP 地址。

实际上，Flickr 使用 Squid 进行前端缓存。在可能的情况下，它会缓存静态内容，这意味着内容直接交付给最终用户，而无需查询应用程序（PHP）服务器或数据库（MySQL）服务器。

数据不言而喻。Flickr 每秒提供近 3,000 张图片，其中 80% 来自缓存。这使得绝大多数流量完全远离 Web 和 MySQL 服务器。

### Further Reading

你可以在 www.ludicorp.com/flickr/zend-talk.ppt 上找到关于 Flickr 如何处理其不断增长的流量水平的更多细节。

## Wikipedia

Wikipedia 仍然独立所有，是一个免费的、多语言的、基于 Web 的百科全书，其内容完全由普通公众成员贡献和维护。尽管衍生出了无数副本（或“分支”），Wikipedia 仍然是原版——也是最受欢迎的。它每年吸引 6.38 亿访客，这些访客阅读超过 250 种语言中的 1000 多万篇文章，其流量仍在每日增长。就本文撰写时，它每秒收到 20,000 到 45,000 个请求。

### Wiki Software

Wikipedia 基于 MediaWiki，这是一个免费开源的 Wiki 平台，提供一种轻量级内容管理平台来交付 Wiki 内容。MediaWiki 平台用 PHP 编写，可以使用任意数量的相应数据库平台。但是，Wikipedia 选择了 MySQL。

### Geographic Load Balancing

如前文所述，作为全球性网站，Wikipedia 使用地理负载均衡。这样做时，其每个主机（en.wikipedia.org、fr.wikipedia.org 等）的 DNS 解析取决于执行 DNS 解析的客户端计算机的地理位置。例如，在伦敦，en.wikipedia.org（英文版）解析为 91.198.174.2。在德克萨斯州休斯顿，它解析为 208.80.152.2。

两个 IP 地址上的服务器提供完全相同的内容，但它们位于地理位置相距很远的地方。这样一来，到 Web 服务器的“追踪”被降至最低——也就是说，流量从用户的 Internet 连接到服务器必须经过的路由器和网关的数量被降至最低。

### Static File Server

Wikipedia 出色地使用了 lighttpd，这是一个轻量级、无多余功能的数据库服务器，非常适合提供图片和 CSS 样式表等静态资产。特别是，缩略图（而非其全尺寸变体）以这种方式交付。

实际上，Wikipedia 使用的 lighttpd 安装比大多数安装更复杂一些。它被配置为：如果找不到缩略图，则请求可以传递到应用程序服务器集群进行实时生成。这使其更像是一个内容缓存，而不是简单的无脑资产服务器，能够根据需要智能地路由请求。

### Linux Virtual Server (LVS)

Wikipedia 环境中的负载均衡由 Linux 虚拟服务器 (LVS) 提供。这使得许多物理服务器的资源可以被池化、平衡，并向外部世界暴露为一个单一的虚拟服务器。

与传统的负载均衡相比，这有很多优势。它与协议无关，不需要任何软件级支持，是内核级的以实现速度，并且还可以提供无单点故障的冗余。

有关更多信息，请参见 www.linuxvirtualserver.org/。特别是，http://kb.linuxvirtualserver.org/wiki/Load_balancing 有关其在提供负载均衡中的作用的详细信息。

### memcached

最后，本章前面未提及的是 memcached。它在 PHP 中得到原生支持（有关更多信息，请参见 http://uk.php.net/manual/en/intro.memcache.php），它提供分布式内存缓存，使“昂贵”的应用程序操作的结果能够缓存在内存中。





由于内存几乎总是比，例如，从磁盘读取、调用Web服务或与数据库服务器通信更快，因此可以享受巨大的速度优势，并由此推断，支持更高的负载。

以维基百科为例，专用服务器池实际上充当带有大量RAM的专用缓存。因此，建立与缓存服务器的连接以存储或检索缓存值会带来轻微负担，因此在决定是否使用缓存时，会遵循某些启发式规则。

在维基百科的情况下，有一个大约30台服务器的池，每台配备2GB RAM——这相当于超过60GB的文本值缓存。

## 进一步阅读

如需进一步（相当晦涩）阅读维基百科基础设施的内容，请访问 http://damm.it.lt/uc/workbook2007.pdf。

## 摘要

在本章中，你终于直面了企业级PHP的残酷现实——即在高流量下对高应用可用性的需求。

最初，你探索了这些神话般（但常用）短语的实际含义，并了解了两者的一些冷冰冰的硬性指标。怀着此念头，你审视了影响负载下可用性的架构因素及其各自的相对重要性。随后，你详细探索了一本可减轻这些断裂点所造成风险的方法百科全书。

最后，你深入了解了两个流行网站——Flickr和维基百科——并学习了它们如何采用其中一些缓解策略取得良好效果，从而轻松应对海量流量。

在第24章中，你将被迫问自己一些尖锐的问题，即PHP是否实际上是你应用程序的正确选择。在此过程中，你将学习一些出色的宣传技巧——以及何时适合寻找其他替代方案。

## PHP宣传

显然，除非你相信某种编程语言是Web应用程序开发的最佳方法，否则你不会着手撰写一整本关于该语言的书。然而，PHP存在一些声誉问题，尤其是在某些应用程序开发人员群体中，他们认为简单的语法、弱类型变量以及缺乏庞大复杂的应用服务器环境，将PHP的实用性局限于非常简单的应用程序，以及缺乏其他环境知识的初学者程序员。

诚然，对于任何想要构建Web应用程序的人来说，极低的入门门槛意味着许多基于PHP的网站构建糟糕，存在巨大的安全漏洞、业务逻辑与HTML标记难以分辨的混杂体，以及严重的性能问题。然而，PHP平台的简单性和易访问性也是主要优势，低入门门槛是值得庆祝而非贬低的事情。

像本书这样的（以及其他优秀的印刷和在线PHP资源）应该鼓励初级开发人员增加对软件开发及其产品工艺的了解。对于习惯于在其他环境中工作的有经验的开发人员来说，这些资源应该鼓励他们重新审视PHP，并将其视为下一个项目的选择。

本章提供了一些理由，说明为什么PHP是即使是企业级应用程序开发的最佳编程语言选择。它还为那些坚持认为其他平台拥有更大合法性的人提供了一些反驳论点。

## 低开销

运行基于Java的Web应用程序最令人恼火的事情之一，是为了让即使是最简单的应用程序运行起来，也需要进行大量的设置、安装、配置和性能调优。

安装Java、Web服务器、J2EE应用服务器、用于使Web服务器与应用服务器通信的连接器、Ant（或其他构建管理器）、创建XML文件以配置构建管理器、编译应用程序、将其打包为部署文件（WAR或EAR包）、部署到应用服务器、调整应用程序配置文件、调整应用服务器配置文件，然后重启应用服务器之后，你才能发现代码是否正常工作。

真烦！

PHP环境的简单性（即只需一个Web服务器和PHP模块）使得让PHP应用程序运行起来非常容易。除非你的应用程序需要一些自定义模块或其他深奥的东西（这不常见），否则通常只有一个小的应用程序配置文件，通常包含数据库连接字符串和其他简单细节，应用程序即可运行。大多数UNIX平台（包括Mac OS X）现在都预装了Apache和PHP。

在许多应用程序中，你可能需要定期运行cron作业，为此通常使用命令行应用程序或脚本。然而，运行Java命令行应用程序（以及在较小程度上，Python或Ruby应用程序）的基本命令行语法可能十分复杂且并不明显，而PHP命令行应用程序通常只用一个参数调用：即要运行的脚本名称。

采用简洁的MVC范式架构的应用程序，从命令行与应用程序交互通常只涉及一个新控制器和一些新视图。

虽然这对任何编写良好的应用程序都适用，但PHP中调用的简单性使得这比其他环境中更令人乐于接受。

无论你是从命令行还是从Web服务器运行，调用任何PHP应用程序的简单性都因系统库的通用安装位置而大大增强。

用C编写的编译模块有指定的安装位置，而由PEAR安装的基于PHP的扩展进入一个通用目录。

与Perl采用的系统不同（该系统涉及许多此类通用文件夹，都带有版本特定的名称），PHP结构非常易于理解和发现，通常通过查看phpinfo()的输出即可。

Java（偶尔还有Python）晦涩难懂的类路径并不涉及PHP应用程序的配置。

当必须安装新扩展时，在Web服务器上安装它们有两种非常简单的方法：PEAR和PECL。

PEAR是用PHP编写的实用程序库系统，而PECL包括作为PHP扩展用C编写的那些扩展。

这两个仓库的文档都很出色，可从各自的网站获取（http://pear.php.net 和 http://pecl.php.net）。

虽然这些借鉴了Perl的CPAN仓库，但它们访问起来简单得多，文档也易读得多。

对于.NET或Java，不存在以有意义的方式存在的此类仓库。

推荐的做法是从源代码编译新扩展，这也是本书作者的偏好。

许多其他开发人员非常满足于使用其操作系统的包管理器为PHP添加新功能。

例如，在Red Hat/Fedora环境中，如果你需要PHP的PostgreSQL模块，可以简单地以root身份从命令行键入以下内容：

```
#yum install php-pgsql
```

PHP的近乎普遍意味着各种GNU/Linux发行版的维护者确保PHP模块经过充分测试且易于安装。

## 语言简单性

PHP的语法受多种流行编程语言的影响，例如Perl、C甚至ASP。因此，它受益于这些语言更悠久的传统，并能够吸收其语法中最有用的部分，舍弃那些令人困惑且不必要的功能。

### 弱类型语言

强类型编程语言（如Java和C#）的主要优势在于，某些编程错误会在应用程序部署之前由编译器捕获，从而捕获一些否则可能难以追踪的错误。

然而，这是以程序员花费时间确保变量从一开始就被分配正确类型，然后在转换数据结构时将值从一种形式转换为另一种形式为代价的。

像Perl、Python和Ruby一样，PHP使开发人员能够确定数据在运行时将如何使用。

这允许自动类型转换，在执行的不同点重用变量以保存不同类型的信息，并且通常代码更简单。

当然，此功能可能被滥用；但强类型和弱类型编程语言之间存在一个主要的哲学差异：后者*信任*开发人员知道自己在做什么。

以下代码也许有些随意，但在PHP中完全有效：

```
$words = array('Hello', 'World');
$words = join('', $words);
```

创建另一个变量来保存连接数组的字符串表示可能是更好的做法，但在Java或C#等强类型语言中，你必须花时间声明和实例化对象来保存两个不同的值。

同样，以下代码也是完全有效且无歧义的PHP代码：

```
$a = 6;
$b = "42";
$c = $a + $b; // 48
$d = $a . $b; // "642"
```

请注意，与其他弱类型语言相比，这里存在优势，在这些语言中，加法运算符和连接运算符是相同的（Perl、JavaScript等）。

在设置`$c`的值时，PHP会自动将字符串"42"强制转换为其数字等价值42。

在连接两个变量以获得`$d`时，6会被强制转换为"6"。

在为不同数据类型重载运算符的语言中，`$c`的值将是模棱两可的。

### 减少标点符号

Perl等语言使用不同的符号（sigil）来标识变量类型（例如，`$foo`是标量，`@bar`是数组，`%baz`是散列表，而令人困惑的是，`$baz`是`%baz`的引用）。

使用此类语言时的常见抱怨是，在各种形式之间转换值并跟踪使用哪个符号（以及何时使用）极其耗时，并且是错误的常见来源。

Ruby使用相同的符号来指示变量作用域，这进一步增加了混淆。

PHP通过为其变量使用一种语法来简化所有这些内容：`$myvar`。





一般来说，PHP 开发人员倾向于向语言中引入更少的标点符号，避免使用 Perl 的快捷变量（例如 $_ $?）以及 Perl 和其他语言中发现的那些奇怪的字符串运算符（如 qq）。

在 PHP 中创建数组，只需使用 array()。这很直观，无需记忆数组运算符是 [ ]、( )、{ } 还是其他东西——这在多种编程语言中很常见。这意味着一切都必须更显式一些，或许会占用更多代码行，但由于专业程序员关心其软件对他人的可读性，这是一项优势，尤其因为它不需要额外的程序员时间来实现。

## 普遍理解的语法

尽管有诸多缺点，带有分号和花括号的 C 风格语法被广泛理解，并在大量编程语言中很常见。虽然 Python 和 Visual Basic 等语言中的替代语法对新程序员更友好，但我们中的大多数人在空白字符无关紧要、语句以分号结束的世界里感觉相当自在。舒适虽然不一定令人兴奋，但能提高生产力。

任何有先前编程经验的人都可以非常快速地掌握 PHP 的基本语法，并立即理解如何处理基本操作。所有运算符都是简单的单一标点符号（例如，赋值是 =，连接是 .），函数使用关键字 function 构建，无需像在 C 中那样单独声明。虽然许多人欣赏 Python 这类视觉上整洁的语言的简洁性，但这与我们许多人习惯的语法方法不同。像 Ruby 这样在 PHP 的命令式编程风格之外支持多种编程范式（例如函数式编程）的编程语言，不仅会导致语法上的混淆，还会导致对一段代码意图的混淆。

## 跨平台支持

像本节讨论的许多其他语言一样，PHP 几乎在所有常用操作系统上都受到支持。Java 带有“一次编写，到处运行”的理念，在语言层面支持这一概念；但一旦将各种应用服务器环境纳入考虑，这一承诺就会迅速打折扣。非常多时候，为在 JBoss 上运行而创建的应用程序无法正常工作，或者其部署方式与为（例如）WebLogic 编写的应用程序不同。这两种环境的复杂性在于，一次编写可能对应用程序逻辑有效（有时），但每次部署都必须创建大量容器特定的配置信息。这还假设应用程序是针对 Sun 版本的 Java 编写并针对其编译的。

> 值得一提的是，Java 的实现存在一些碎片化，来自 Microsoft（大多被忽略）、Apple 的竞争性 JVM 以及 GNU 项目人员开发的更兼容开源许可证的版本。所有这些实现都略有不同。

PHP 只有一种实现，采用完全自由开源软件许可证，拥有非常活跃的开发者社区，并且短期内不太可能出现分支。“一次编写，到处运行”的承诺在 PHP 项目中得以实现，值得一提的是，Python、Ruby、Perl 及其他几种语言也是如此。

由于 PHP 只需将简单的插件集成到 Web 服务器即可工作，无需额外的服务器进程或守护进程来支持它，因此它很容易适应任何 Web 服务器环境，并且几乎存在适用于你可能想要使用的任何可想象的 Web 服务器软件的 SAPI 模块。

部署 PHP 应用程序通常只是将一些文件上传到 Web 服务器，然后执行任何应用程序特定的配置（例如编辑数据库连接字符串）这一简单的事情。没有需要重启服务器来部署 WAR 文件的复杂操作，也没有数十行长的复杂 XML 文件来设置执行环境。对于许多安装来说，源代码分发中包含的默认 php.ini 文件对于其部署所在的平台几乎（且常常完全）是正确的。此外，除非必须向 PHP 添加新扩展，否则初始安装后，此配置通常永远不需要再次修改。

要将 PHP 应用程序部署到生产 Web 服务器，可以使用 FTP 客户端复制文件。但更好的方法是使用 Subversion 客户端（或 CVS）从源代码仓库的特定分支进行部署。（附录 A 讨论了源代码管理系统和 Subversion。）由于 PHP 是一种解释型语言，不存在需要部署的编译型机器特定二进制文件。此外，与 J2EE 应用程序不同，代码以纯文本形式分发，而不是 ZIP 文件（WAR 和 EAR 文件实际上就是 ZIP 文件），这有助于对自上次部署以来更改的文件进行简单快速的增量更新。

与 IIS 等复杂的 GUI 应用程序服务器相比，一个巨大的优势是能够通过 SSH 会话使用 vi 或 emacs 远程编辑纯文本配置文件。由于从一台机器向另一台机器隧道 SSH 连接很容易，因此出于管理目的配置到 Web 服务器的安全连接也是一件简单的事。要安全地连接到 Windows 远程桌面连接来管理安全性、应用程序设置、用户帐户和其他详细信息，通常涉及连接到 VPN、远程登录到 DMZ 中的机器，然后从那里连接到实际的 Web 服务器机器的混乱过程，而在那里一切都是通过占用带宽和内存的 GUI 完成的。

.NET 应用程序（其本身通常也不易于部署）是一种“一次编写，在一个系统上运行”的操作系统应用程序环境。尽管有 Microsoft 通用语言运行时的承诺，以及开源 Mono 项目取得的进展，.NET 开发仍然高度依赖于 Microsoft 应用程序服务器环境。虽然本书不一定主张在运行 IIS 的 Web 服务器上部署 PHP 应用程序，但至少有几个应用程序（特别是那些对本书作者的几个客户都有用的应用程序）已成功部署在 UNIX 和 Windows 机器上（分别使用 MySQL 和 MSSQL 数据库），对应用程序源代码几乎没有修改，除了对 SQL 查询进行一些小的更改外。

对于 .NET 开发，基本上只有一种可用的编程环境，那就是 Microsoft 的确相当出色的 Visual Studio。然而，软件开发被绑定到一种环境是令人窒息的，MSVS 的巨大开销意味着你只能在相当强大的硬件上进行 .NET 开发，而你可能并不总能接触到这样的硬件。只需一个 SSH 客户端和一份 emacs 副本，你就可以从最基本的计算机远程开发 PHP 应用程序。对于本地开发，你基本上可以运行任何喜欢的操作系统，并使用任何喜欢的文本编辑器或集成开发环境（IDE）。（有关一些可用的更好的 PHP IDE 的讨论，请参见附录 B。）

## 普遍性

PHP 的普遍性和长寿是它在创建新应用程序时出现在任何可能语言列表顶部的其他原因。因为你知道几乎每个 ISP 都会支持它，并且它可以在你可能需要部署到的任何环境中工作（包括 Windows 上的 IIS），所以你知道你不需要担心系统支持，而 Java、Python 和 Ruby 通常不受广泛支持，尽管对后两者的支持正在增长。

尽管 Python 和 Ruby 得到一些非常有影响力的用户的支持，但它们将享有多长的寿命仍有待观察——尤其是 Ruby，它目前带有一种“本周流行”的光环，尽管它是一种非常强大且健壮的语言。虽然 Ruby on Rails 启发了许多程序员创建了一些创新应用程序，但 Ruby 语言本身仍然相对冷门，Rails 项目的企业支持也很有限。

相对而言，Python 已经存在一段时间了，并且在 Google（以及 Web 世界中的其他重量级企业）中被广泛使用。然而，Python 在主要 ISP 和企业数据中心的支持仍然有限。虽然这种情况在未来几年可能会开始改变，但它仍然是一种专业的应用程序开发环境。

文档的质量及其访问的便捷性（只需访问 http://php.net/{function_name} 即可获取任何函数的文档）使学习 PHP 变得轻而易举。虽然有大量的 Python 文档，但访问不那么便捷，Ruby 文档还有很长的路要走。PHP 被广泛使用的时间也意味着，对几乎任何可以想象的编程任务，都有大量优秀的教程和操作示例。由于 Python 和 Ruby 相对新晋，可用于这些语言的资源并不那么丰富。Java 的文档丰富且结构良好，但该平台上应用程序开发的复杂性抵消了其实用性。Microsoft 的官方 .NET 文档质量中等，尽管该开发社区拥有一个非常活跃的教程编写者群体。

## 强大

关于 PHP 曾有过这样的说法：虽然它可能适合你表兄的博客，但尚未准备好进行企业级软件开发；但只需询问任何公司，看看它们是否运行比 Wikipedia、Facebook、Yahoo!，是的，WordPress 更多处理器密集型、存储密集型、注重安全或关键任务的应用程序，以及无数其他每小时流量远超大多数企业应用程序一个月流量的 Web 站点。

话虽如此，使用 PHP 编写非常糟糕的应用程序是非常非常容易的。为完整的 J2EE 环境编写任何应用程序都是非常非常困难的。当你拥有优秀的软件开发人员，仔细思考软件架构（并根据既定业务逻辑规划执行）时，PHP 提供了形式化的语言和执行环境来创建最强大的应用程序。当你拥有使用业余技术和糟糕项目管理的缺乏经验的软件开发人员时，无论使用何种编程语言，每个应用程序都会很糟糕。

PHP 的早期版本因缺乏面向对象支持（在 PHP 5 中修复）、缺乏命名空间（在 PHP 5.3 中修复）以及糟糕的应用程序设计决策（例如 php.ini 中存在 register_globals）而受到相当程度的指责。PHP 5 已发布近五年，并已证明自身作为



既是一种功能强大的语言，也是一个稳健的执行环境。PHP 6 默认包含高级 PHP 缓存（APC，Advanced PHP Cache），这是一个在附录 C 中简要介绍的 opcode 缓存扩展，你可以在此基础上实现大幅性能提升，叠加在本版本发布的 PHP 运行时优化之上。

本讨论未提及某些替代语言，例如 ColdFusion，它在某些圈子中仍然很流行。此处排除它，原因是它迅速失去人气，在专业软件开发人员中支持甚少，并且是一个平台受限、相当昂贵且性能不佳的环境。此外，还排除了一些高级应用程序库，例如用于在 Java 中实现 MVC 的 Struts 和 Tiles，或者用于 Perl 的 Catalyst。与基于 PHP 的解决方案（如 Smarty）或 PHP 本身首选的模板系统相比，这些系统的巨大复杂性简直可笑。

## 摘要

本章应当已经说明了 PHP 为何拥有持久的受欢迎程度，以及本书作者为何是它的热心拥护者。希望那些可能曾经认为（由于如今早已过时的反对意见）PHP“尚未准备好迎接黄金时段”的读者，能够重新审视该语言及其运行时环境，并查看许多目前每天为数百万访问者提供服务的优秀开源 PHP 应用程序的软件架构（维基百科和 WordPress 是不错的起点）。此外，考虑一下你的时间是更有利于为应用程序服务器编写 XML 配置文件，还是使用 PHP 为实际应用程序编写业务逻辑。

既然你已经掌握了关于 PHP 为何是如此出色的应用程序开发平台的所有信息，第 25 章将提供一些关于如何利用它建立成功职业生涯的思路。

## 作为 PHP 专业人员的职业生涯

如果你不知怎地在未接触过计算机的情况下坚持到此，请至少参考之前几章中的几章。我们人类倾向于通过实际操作所学内容来获得最佳学习效果。回去挑选一章（或两章）引起你兴趣的内容，并随意尝试代码。“投入多少，收获多少”这句格言在此同样适用。

即使你已一丝不苟地阅读每个段落并运行每个应用程序，这也应该很真实。毕竟，你一定曾经产生过“如果……会怎样？”这样的想法。不知道答案？在文档中找不到？那就去尝试。通过探索边界而弄坏代码并不可耻，到这时你的 PHP 技能应该已达到一个关键点。你可以摆脱任何你自己陷入的困境。

这是一个重要的区别。利用技术技能、使用单元测试并深思“如何”和“为什么”来摆脱困境，意味着你的学习可以继续，并希望超越技术领域。确定问题的可能原因，然后制定一份可能的最佳解决方案短名单（医学医生称之为“鉴别诊断”的技能），是你作为专业技术人员成长中至关重要的一部分。这种能力仅来自经验以及一路上犯下的几个错误。

## 动机

无论你购买本书的原因是什么，走到这一步所付出的努力肯定非同小可，你当得起一句“辛苦了”。走到这一步可能涉及牺牲至少一些你本可以花在玩电子游戏、参加社交聚会、与家人互动，或者只是好好睡觉上的时间。

你现在应该能够欣赏 PHP 的一些特性及其普遍性。走出去应用你所学的知识，如果需要的话可以循序渐进，但务必应用所学的教训。安装 PHPUnit。浏览 PEAR 归档库，不要仅仅安装和运行第三方 PHP 应用程序，而是要查看它们、阅读源代码、弄明白它们在做什么，并在必要时修复它们。（请记住，这些是开源库；回馈项目，尤其是解决问题的贡献，通常受到赞赏和追捧。）

尽管你的技能组合可能既深又广，但你永远不会停止学习。与认为 Wrox 试图折磨你的看法相反，每一章的存在都有原因，没有哪一章纯属学术性质。这本书由 PHP 专业人士（从业者）创作，所有呈现给你的内容都在专业环境中使用。

这也意味着一切都有来历。本书和 PHP 6 并非凭空产生，因此这些功能和实践值得进一步探索。整本书（甚至整个公司和某些子行业）都支持所呈现给你的概念。继续阅读，因为一些优秀资源即将呈现。

### 作为开发人员的职业生涯

假设你认真对待成为专业软件开发人员（而不仅仅是领取工资写代码的人），你就应当有意识地努力提升技能。技术技能的保质期越来越短，你为跟上趋势和发展所付出的任何努力都不会被视为浪费。

你如何分配宝贵的时间？你不可能样样通，全面发展的技术人员被认为非常有价值。

### 不仅仅是 Web 开发技能

PHP 不仅仅涉及会话管理、文件下载和配置变量的细节。PHP 是一种随着时间发展和变化的语言，旨在满足像你这样的开发人员的需求，他们需要尽早完成任务。

尽管 PHP 的设计和实现面向 Web 站点开发，但 PHP 不仅可以用于与浏览器交互。考虑一下你可以使用一个能够在 Windows 和 Linux 之间无缝运行，并能与文件系统及几乎所有流行数据库通信的工具做些什么。你还能用它做什么？不妨参考以下内容：

- [ ] 翻译数据库
- [ ] 处理 XML
- [ ] 收集 RSS/Atom 提要
- [ ] 测试替代 Web 开发技术的表单/网站
- [ ] 使用类似 Perl 的文本处理
- [ ] 运行通用实用程序

即使你不是每天都创建网站，仍然可以找到机会发挥你辛苦获得的宝贵 PHP 技能。

## 软技能

是的，这些也被称为令人生畏的“人际交往技能”。即使是 PHP 极客，也必须不时与真实活生生的人类互动，即使他们是其他 PHP 极客。

奇怪的是，这些能力通常不被视为标准技术技能，尽管大多数专业软件开发人员花费大量时间与客户和同事互动、收集功能需求、确定业务逻辑、协调开发工作并对已完成的工作进行复盘评估。坦率地说，大多数程序员天生并不具备最有效的社交技能。

投入时间提升你的非技术技能，将大有裨益。主动向同事和客户征询关于你的沟通能力、性格特征和表达能力的反馈。总的来说，软件开发人员往往智力很高，但也往往惊人地缺乏社交意识，并且还带有傲慢。

你的客户和同事并非因为不懂技术而智力低下。（出于其他原因他们可能是白痴，但缺乏技术知识并不等同于缺乏智力。）要敏感地意识到技术会让大多数非技术人员感到畏惧。这可能部分是因为其复杂性，但也可能归因于多年来与傲慢的技术人员打交道的经历，这些人特意贬低那些没有计算机科学知识的人，并用深奥的术语让他们不知所措，试图“解释”一个问题。不要做那个傲慢的人。知道如何向非技术人员有效传达复杂话题是本书作者花时间培养的技能，也是我们每天用来赢得和留住客户的技能。

不要将被提问视为被“打扰”或“分心”，而应将其视为一个教学机会。这确实是一个机会。你的客户和同事越了解应用程序创建所包含的内容，他们就越能欣赏各种任务为何需要一定时间，以及哪些活动是非同小可的。

这种教育的目的不是让客户经理或平面设计师掌握数据库架构的知识，而是帮助他们了解启动某些类型应用程序所需的各项活动的性质。

例如，本书作者定期为客户和同事举办正式计划的研讨会，但更经常地在工作日抽出一点时间充分解释对某些问题的回答。正式教育和非正式教育都极大地改善了客户和同事之间的关系，并有助于确保开发人员在项目需要其意见的阶段被征询意见，而在浪费时间的会议中被排除在外。妥善地教育所有人，会让每个人的生活更轻松。





## 学术技能

我们所做的既是艺术也是科学，不断演进。专业软件开发人员明白，持续的计算机科学教育对于职业发展、个人成长以及生产力和应用程序稳定性的提高至关重要。大多数人每天都会抽出一些时间（哪怕只有1小时）来浏览文献、监控重要的邮件列表，并了解行业新闻和趋势（不，在Slashdot上花一小时发表尖刻评论不算是对本职工作的深入了解）。除了丰富的在线资源和定期出版的文献外，还有几部经典之作应该阅读、重读，并完全内化。

充分理解设计模式是什么、如何在PHP和其他编程语言中实现一些最常见的模式，以及学习如何运用设计模式方法思考软件架构，几乎必然会带来更好的整体应用设计和对象的更好可重用性。《可复用面向对象软件的基础：设计模式》（Design Patterns: Elements of Reusable Object-Oriented Software），作者是Erich Gamma、Richard Helm、Ralph Johnson和John M. Vlissides（常被统称为“四人帮”或“GoF”（Addison-Wesley，1994）），是一部经典；本书分章节清晰，排版精美，呈现出精心装订的美丽大部头（甚至配有一条花哨的书签丝带用于标记页码）。每周学习一章，半年就会转瞬即逝。

更深入理解PHP运作方式的一种方法是花些时间分析和理解PHP本身的源代码（它是用C语言编写的）。如果你打算进行任何低层次的性能调优，这尤其有用。有了Ronald Mak编写的《编译器与解释器》（Writing Compilers and Interpreters）（Wiley，1996），了解PHP等语言如何“施展魔法”，在遇到困难时将大有裨益。

《重构：改善既有代码的设计》（Refactoring: Improving the Design of Existing Code），作者Martin Fowler、Kent Beck、John Brant、William Opdyke和Don Roberts（Addison-Wesley，1999），探讨了编写简洁优雅代码的技术。《敏捷建模：eXtreme Programming和统一流程的有效实践》（Agile Modeling: Effective Practices for eXtreme Programming and the Unified Process），作者Scott Ambler和Ron Jeffries（Wiley，2002），详细阐述了敏捷开发实践与标准建模技术的集成。

## 社区技能

PHP之所以存在，是因为它是作为社区协作成果开发的。大量开发人员参与了这一过程，哪怕只是以测试人员的身份。对语言本身开发项目而言，另一项非常重要的贡献是进行测试和编写文档。PHP之所以取得如此成功，部分原因在于现有文档的质量和数量；但如果你想为PHP源代码、PEAR或PECL库之一，或任何其他开源项目的开发做出贡献，了解构成开发核心的人员的文化至关重要。

总有一天，你会发现某个PHP工具或应用程序需要修复，或者你可能会发现有人为你写的东西提供了补丁。无论哪种情况，在政治过程中，一点谦逊都大有裨益，这一点也不例外。

积极参与PEAR等社区项目可以提升你的个人PHP技能，而类似开发人员使用你的工具所节省的时间会使这项工作的价值成倍增加。即使你的技术水平未必达到项目最初的要求，创建“How-To”指南或面向开发人员的教程这一行为，往往对学习新技术大有裨益。遗憾的是，即使是最好的项目也往往缺乏优秀的文档。

## 总结

本书介绍的技术概念被视为最佳实践，你应该做好准备，了解它们是什么。作为软件开发人员，你几乎肯定会遇到MVC、重构、UML、设计模式和集合方面的好坏参半的示例。

因此，运用你的新技能与最初学习它们同样重要。尝试在其他领域发挥你所学知识，并始终留意有趣的工具、开发技术、设计和项目。

毕竟，你和我们（作者）同住在地球上，我们欢迎任何帮助，共同创造一个劣质软件不那么容易找到的地方。

> 记住，年轻的绝地武士：“未来总是在变动”（尤达）。

# 第五部分

# 附录

- 附录 A：版本控制
- 附录 B：PHP 集成开发环境
- 附录 C：PHP 性能调优
- 附录 D：PHP 最佳实践安装

## 版本控制

许多程序员都畏惧大型项目，原因多种多样。然而，大型项目的一个特定方面有时比任何其他方面都更让人望而却步：代码组织。六七名软件开发人员、两名软件架构师、一名首席架构师以及客户端开发人员共同参与同一项目，往往是灾难的配方。

幸运的是，近年来，随着易于获取、易于使用且跨平台的版本控制软件的出现，大型项目的代码组织变得容易多了。

本附录探讨了版本控制的基本原则，并讨论了如何为你的项目组织版本控制策略。你还将学习这些原则在两种最流行的版本控制软件应用程序中的应用方式，以及如何选择（如果其中任何一种适合的话）最适合你项目的那一种。

### 版本控制的原则

版本控制的目的有两个。首先是避免多个程序员处理同一组项目文件时可能出现的版本冲突。第二是自动记录项目关键文件的更改，从而创建代码更改的历史记录，并使回退到先前版本成为可能。

通过要求程序员在想要处理某个文件时从中央仓库*检出文件*，版本控制平台可以记录谁在何时处理哪些文件。根据所采用的方法，此方式要么完全禁止其他开发人员同时处理该文件，要么允许其他开发人员也处理该文件，并在文件签回时合并他们的更改。

项目中对文件的*文件日志记录*涉及保留每个文件的先前版本。只要将文件签入仓库，版本控制平台就会将其标记为当前版本，因此任何从仓库检索该文件的人默认都会获取最新版本。但是，会保留该文件先前状态的副本。这不仅允许项目管理员或首席架构师在新版本出现问题时回滚文件，还使版本之间的更改易于列出，从项目管理角度来看，这大大有益。

所有版本控制系统都使用某种仓库来存储项目文件和目录结构的副本（通常是原封不动地存储在磁盘上，但有时作为更复杂且通常为专有的数据库格式的一部分）。访问此仓库的方式因系统而异。典型拓扑将在本附录后面进行探讨。

### 并发与独占版本控制

版本控制平台在所讨论原则的实现方式上差异巨大，尤其是在文件如何被检出方面。

在任何版本控制平台中，当程序员检出一个文件时，最新版本的该文件会从中央仓库检索，用户的本地版本会被该最新版本替换。

但是，在采用*独占版本控制*的平台上，会立即对该文件加锁。在文件被检出期间，其他开发人员仍可检索该文件的最新版本，但他们自己无法将其检出以进行处理。这种独占版本控制通常通过将开发人员的本地文件副本标记为只读来强制执行。当然，这只是名义上的强制执行，实际操作中还需要开发人员的配合才能奏效。处理该文件的开发人员签回该文件后，锁会被移除。随后，仓库会更新以反映最新版本。

*并发版本控制*采用完全不同的方法。检索文件最新版本和检出文件进行处理这两个动作被合并，本质上成为同一个动作。换句话说，要处理某个文件，开发人员只需确保自己拥有该文件的最新版本，然后开始处理即可。每个开发人员完成对文件的更改后，会将其签回。神奇之处就在于此。如果第二个开发人员在另一个开发人员检出文件后检出同一文件，并在第一个开发人员签回更改版本后尝试签回，那么两个新提交的版本将被合并。

#### 并发版本控制示例

为了更清晰地说明，请考虑以下示例。这是一个名为*helloworld.php*的虚构文件，用于在Web浏览器中打印“Hello World”。请注意，行号已包含在内。当然，这些行号不会包含在保存的代码中。

```
1: <?php
2: $strToPrint = "Hello World";
3: ?>
4: <html>
5: <body>
6: <?php echo $strToPrint; ?>
7: <br /><br />
8: </body>
9: </html>
```

你可以将这段代码称为文件的1.0版本。

假设Jane Doe和John Doe都在参与该项目。John在纽约工作，Jane在洛杉矶工作。




已与客户召开了一次会议。客户希望修改此特定文件的代码，使其不再打印“Hello World”，而是打印“Goodbye World”。John Doe 的经理已将修改代码以反映此要求的任务交给了 John。

在此次会议中，客户还要求在打印的文本下方绘制一条水平线。Jane Doe 的经理已将修改代码以包含该额外行的任务交给她了。

在独占版本控制设置中，John 和 Jane 将无法同时进行更改。John 必须先签出文件，进行修改，然后再签入。随后 Jane 可以签出文件，进行她的修改，并再次签入。

在并发版本控制设置中，不存在此类要求。假设在东部时间 12:00 P.M.，John 进行签出以获取文件的最新版本，当前为版本 1.0。他开始进行更改。在东部时间 12:01 P.M.，Jane 也进行了签出，同样是为了获取文件的最新版本。这仍然是版本 1.0；John 尚未签入任何内容。Jane 开始进行她的更改。

在东部时间 12:05 P.M.，John 完成了工作。代码运行正常，因此他决定签入自己的工作。他这么做了，仓库将他新提交的版本保存为最新版本——版本 1.1。版本 1.1 现在如下所示：

```
1: <?
2: $strToPrint = "Goodbye World";
3: ?>
4: <html>
5:   <body>
6:     <?php echo $strToPrint; ?>
7:     <br /><br />
8:   </body>
9: </html>
```

在东部时间 12:09 P.M.，Jane 也完成了工作。代码对她来说运行正常，因此她现在想签入自己的工作。她的代码现在如下所示：

```
1: <?
2: $strToPrint = "Hello World";
3: ?>
4: <html>
5:   <body>
6:   <?=$strToPrint?>
7:   <br /><br />
8:   <hr />
9:   </body>
10: </html>
```

当她签入时，仓库注意到她正在签入版本 1.0 的修改版本——而不是当前最新的版本 1.1。她提交文件的尝试将导致一条错误消息，指示她必须先从仓库获取最新版本，并将其与自己的更改合并，然后才能提交。

仓库现在必须合并 John 在版本 1.0 和 1.1 之间所做的更改，与 Jane 在 1.0 和她新提议的版本之间所做的更改。

仓库确定 John 所做的更改是将第 2 行从

```
2: $strToPrint = "Hello World";
```

改为：

```
2: $strToPrint = "Goodbye World";
```

仓库还确定 Jane 所做的更改是在在第 7 行之后插入以下内容：

```
8: <hr />
```

仓库随后仅取最后一个版本（1.0），并系统地应用 John 和 Jane 的双方更改。合并后的代码现在如下所示：

```
1: <?
2: $strToPrint = "Goodbye World";
3: ?>
4: <html>
5: <body>
6: <?=$strToPrint?>
7: <br />
8: <hr />
9: </body>
10: </html>
```

如您所见，两位开发者的更改均已成功合并。仓库现在将此版本标记为 1.2，任何后续对最新版本的请求都将返回此版本。虽然已向两位开发者通报合并情况，但软件完全确信合并可以在不影响 Jane 更改的情况下完成，她无需手动干预合并过程。

## 并发版本控制冲突

在某些场景中，两个或多个开发者在同一文件的同一版本上进行更改，这些更改彼此不兼容——换句话说，就会发生冲突。

假设又进行了一次客户会议，提出了两项额外要求：在向世界告别时包含当前时间，以及包含日期。项目经理将实现时间要求的任务分配给 John，将实现日期要求的任务分配给 Jane。

John 签出版本 1.2 并将其修改为如下内容：

```
1: <?
2: $strTime = time("H:i:s");
3: $strToPrint = "Goodbye World, it's $strTime";
4: ?>
5: <html>
6: <body>
7: <?php echo $strToPrint; ?>
8: <br />
9: <hr />
10: </body>
11: </html>
```

Jane 也签出版本 1.2 并将其修改为如下内容：

```
1: <?
2:   $strTime = time("Y-m-d");
3:   $strToPrint = "Goodbye World, it's $strDate";
4: ?>
5: <html>
6:   <body>
7:     <?php echo $strToPrint; ?>
8:     <br /><br />
9:     <hr />
10:   </body>
11: </html>
```

谁先签入（谁先到）就会创建版本 1.3。你能预见当两位开发者中较慢的那位签入代码时会发生什么吗？在两种情况下都插入了一行新行，并修改了一行现有行。尽管版本控制平台可能能够合并两行新行（只需将两者都合并），但它不知道如何合并对单行（两种情况均为第 3 行）所做的更改。作为 PHP 开发者，您可以看到所需的解决方案——这只是常识：

```
3: $strToPrint = "Goodbye World, it's $strTime on $strDate";
```

然而，版本控制平台并不像相关人类那样聪明，因此它会引发一个错误，向用户通报冲突。随后，由导致冲突的最近一次签入尝试的开发者负责解决它。在实践中，版本控制系统将创建一个临时新版本 1.4，其中包含冲突详细信息。在冲突解决并使该版本生效之前，此临时版本不会被发布。签入文件的最后一位开发者将由版本控制平台通知冲突，并被邀请编辑临时版本以解决冲突。在签入文件的两位开发者中，后一位开发者负责解决冲突，因为版本控制平台认为是该开发者导致了冲突。

仓库创建的临时版本 1.4 可能如下所示：

```
1: <?
2:   $strTime = time("Y-m-d");
<<<<<<< helloworld.php
3:   $strToPrint = "Goodbye World, it's $strTime";
=======
3:   $strToPrint = "Goodbye World, it's $strDate";
>>>>>>> 1.3
4: ?>
5: <html>
6:   <body>
7:     <?php echo $strToPrint; ?>
8:     <br /><br />
9:     <hr />
10:   </body>
11: </html>
```

您可以看到版本控制平台引入的标记，以显示第 3 行的两种不同替代方案。

之前的示例是一个非常简单的可解决冲突。冲突标记将被移除，相关行将被修改以合并两位开发者的更改，然后在仓库中激活完成的版本。

显然，在更现实的示例中，冲突解决偶尔可能既乏味又耗时。然而，允许多个开发者同时编辑文件所带来的生产力提升通常远超过解决冲突所浪费的任何时间。这是并发版本控制的双刃剑。两个开发者同时处理同一文件很有用，但当冲突发生时，他们必须准备好承担解决冲突的责任。

## 做出选择

在实践中，并发版本控制通常是更好的解决方案。正如本书中一再强烈建议的那样，您应该将项目划分为多个组件，并将每个组件表示为单个文件以符合最佳实践（这有助于消除多个开发者在同一文件上进行的工作量）。然而，通常有几个文件（例如，MVC 应用程序中的主控制器类）需要开发者频繁修改。使用具有高效合并能力的系统可以实现最大生产力。

之前的示例显然非常简单，但存在大量场景，其中不止一个用户可能对同一文件做出像那样的小更改。例如，负责编写模型类的一个开发者可能会注意到另一个开发者编写的异常处理显示一条指示语法问题的错误消息。可以就该问题交换一系列电子邮件，在缺陷跟踪应用程序中打开一个故障单，并派遣 QA 团队确认问题已解决；或者负责模型类的开发者可以直接进入视图并修复错误。

话虽如此，值得指出的是，并发版本控制的原则似乎暗示，开发者可以无需通过实际人类语言进行沟通就共同参与开发项目。有效的沟通和项目管理对于确保任何项目的成功至关重要，尤其是当有多个开发者参与时。源代码控制系统并非用于促进沟通的工具。并发版本控制应用程序（例如 Concurrent Versioning System (CVS) 和 Subversion (SVN)）在开源开发中被频繁使用并不令人惊讶，开源开发涉及数千名开发者，其中许多人从未见过面，但所有人都在同一项目上工作；但重要的是要意识到，邮件列表、电子邮件线程、实际的语音沟通以及偶尔的面对面会议才是真正使这些项目成功的因素。

另一种选择是独占版本控制，它禁止两个开发者同时处理同一文件。在文件被签出后，它会被物理锁定，阻止其他开发者访问，直到第一位开发者将其签回为止。因此，如前所述，不可能发生签入冲突。

当然，独占版本控制也有其缺点，即使您的项目旨在防止任何可能导致两人需要同时处理同一文件的情况。一个经常出现的特定问题是“度假”问题。也就是说，一位开发者去度假并意外留下了一个已签出的文件，而另一位开发者现在需要处理它。当然，您可以进入该开发者的工作站并将其签入，但如果它是尚未准备好进行中的工作怎么办？或者如果您在伦敦工作，而那位开发者在洛杉矶工作怎么办？如果您撤销签出，您可能会丢失更改，而这些更改可能（就您所知）已完成 90%！这自然在很大程度上是一个流程问题，为您的开发团队建立适当的政策可以避免这种情况。




选择很大程度上取决于你。内容合并只能用于纯文本源，例如 PHP 和 HTML 代码。像大型 Flash 项目配合小型 PHP 后端这样非常依赖二进制的应用程序，可能更适合采用独占式版本控制，而像 PHP 和 HTML 应用程序这样更复杂、后端更复杂的项目，则始终适合采用并发式版本控制系统。在大多数情况下，你应该选择并发式版本控制。

## 版本控制拓扑

马上就要向你介绍几个提供版本控制平台的软件包。在此之前，值得更好地了解一下版本控制拓扑在实际部署中的工作原理。

无论你决定使用什么软件，无论你为项目选择并发式还是独占式版本控制，类似这样的拓扑通常都适用。请参考图 A-1，其中 John、Jane 和 David 都是在同一个项目（项目 foo）上工作的开发人员。每个开发人员都有自己专用的工作站。

![](img/a1b732997d9cb194dceec0570dc79710_639_0.png)

图 A-1：版本控制拓扑

显然，他们不会在每个工作站上运行 PHP，因此他们共享一台强大的中央开发服务器。每个开发人员都有自己的虚拟服务器实例，代表该开发人员的项目 foo 副本，基于存储在开发服务器上他或她自己的主目录中的源代码。

例如，John 使用 `http://john.projectfoo.example.com`，该网址指向开发服务器上他自己的主目录中保存的源代码（位于 `/home/john/public_html/projectfoo`）。为项目上的每个开发人员都存在类似的设置。

还有一台暂存服务器，由首席架构师用作测试和检查项目最新版本的基础，可能还用于内部演示。一个外部暂存服务器可能在场外维护，用于外部客户演示。

当 John、Jane 和 David 想要处理项目代码时，他们处理自己主目录中的代码副本，其他人无法访问这些目录。这些主目录位于服务器上，因此他们使用 Samba（有关更多信息，请参见 `www.samba.org`）将工作站上的网络驱动器映射到服务器上的主目录。然后他们直接编辑自己项目副本中的文件。这是他们的工作区。项目文件从不存储在他们自己的工作站上，但因为文件通过网络驱动器暴露出来，开发人员在工作站上编辑它们就像它们是本地文件一样。

但是，John、Jane 和 David 必须在此项目上使用版本控制软件。这意味着每当他们想要处理文件时，都必须使用在工作站上运行的版本控制软件执行签出操作（为了本示例的目的，假设它是 Microsoft Visual SourceSafe，稍后将进行描述）。签出过程将相关文件的最新版本从存储库服务器下载到开发服务器上的主目录中。该文件副本设置为可写，以便开发人员可以自由地对其进行工作。如果 John、Jane 或 David 在他们选择的 IDE 中打开文件之前忘记签出，他们会发现文件设置为只读，并且无法保存更改。在文件签出期间，其他人不得签出该文件来进行工作。

当他们处理完文件后，只需签入文件，即可在存储库中记录最新版本。将来签出该文件的其他人随后将看到包含刚刚所做更改的最新版本。如果其中一人希望将新文件添加到存储库，过程类似——快速按一下“添加文件”按钮，文件即被永久纳入。

因为 John、Jane 和 David 同时在项目上工作，他们需要定期执行“获取最新版本”操作。这意味着存储库中所有文件的最新版本将被复制到他们开发服务器主目录上的本地副本中，即使他们无意签出这些文件。这是一种重要的做法，原因有二。可能需要某人最近添加到项目中的一些额外功能，以使你想要处理的某个其他组件能够正常工作。此外，这种做法使开发人员能够快速了解同事们在做什么，并在必要时指出任何错误或提供建设性批评。

偶尔，首席架构师 Paul 可能会选择将“获取最新版本”操作执行到服务器上标记为暂存的某个目录（不是他自己的目录）。这为他提供了存储库中项目当前状态的快照，以便他也能对团队的工作提出建设性批评。

使用另一个版本控制包时，此拓扑和过程中可能存在细微差异。例如，使用 CVS 时，开发人员不太可能在工作站上使用任何客户端软件。相反，他们只需创建某种终端连接（例如 SSH 连接）到开发服务器，然后直接在服务器上运行 CVS 客户端。

值得指出的是，存储库服务器的确切角色也各不相同。CVS 支持一种名为 pserver 的真实客户端/服务器协议来交换数据。但是，Visual SourceSafe 只是使用网络驱动器上的共享数据卷。因此，可能不需要单独的物理存储库服务器，开发服务器也很容易兼任存储库角色。

## 版本控制软件

你可以找到许多用于处理版本控制的软件应用程序。在本简短部分中，你将探讨其中三种，研究其优缺点，并了解它们如何实现版本控制的常见功能和原则。

本附录中没有足够的空间详细介绍每个软件的设置、安装和维护。网上有大量文档详细介绍了每个软件的方方面面，但本部分至少应能让你做出明智的选择，决定哪个版本控制平台最适合你的项目。

### Microsoft Visual SourceSafe

SourceSafe 已经存在很长时间了，现在与 Visual Studio .NET 捆绑提供。在 PHP 环境中使用它可能看起来不寻常，但对于更习惯于 Microsoft 开发环境的人来说，它绝对值得一试。

虽然它不是免费的，但其基于 Windows 的客户端易于使用。PHP 开发人员从不回避挑战，但花精力去弄清楚如何使用版本控制客户端几乎没有意义，你本可以用它来想出处理算法或对象模型的巧妙方法。SourceSafe 使用起来非常简单，你就可以做到这一点。

相反，SourceSafe 为其存储库使用共享磁盘空间，而不是适当的客户端/服务器协议。这有通常与共享 Access 数据库相关的问题，因此，在较大的文件和许多修订版本上使用它可能会非常缓慢。它还存在创建和恢复备份方面的困难；并且有一些令人恼火的方面，这些方面在很大程度上归结为 Windows 和 UNIX 之间的差异（例如文件名大小写敏感性）。

SourceSafe 仅使用独占式版本控制——也就是说，当文件被签出时，其他人不得签出它。与许多使用独占式版本控制的软件包一样，这是通过使用文件本地副本的只读属性来强制执行的。因为这是基于 Windows 的客户端，开发人员几乎肯定会签出到网络驱动器。严格来说，这略显低效。工作站充当下载数据的通道，这有些不必要。

SourceSafe 以完全任意的格式存储其数据库，因此你不能将其存储库存储区用作自动暂存服务器。但是，有一个相当全面的命令行语法，你可以使用它来构建自动化脚本，用于为暂存服务器下载最新版本。当然，此类脚本需要在 Windows 环境中运行，因为没有任何描述的 UNIX 客户端。




这个替代方案值得一看，但请记住，许可证成本对于小型项目来说可能过高。不过，你只需要支付 SourceSafe 的副本费用。因为它依赖共享磁盘空间，因此不存在所谓的服务器，你甚至可以使用由运行在 Linux 上的 Samba 提供的网络驱动器。

## CVS

并发版本控制系统（CVS），顾名思义，是实现开发者检出并发版本控制的更知名的版本控制平台示例之一。CVS 的巨大优势在于其采用 GNU 通用公共许可证发布，这意味着它基本上可以免费下载和使用。

它将仓库存储在一个大体上镜像相关项目真实目录结构的文件夹中，并使用文件中的小型标记行、目录中的隐藏文件以及文件名的轻微拼接，在存储文件本身最新版本之外存储辅助数据。这与 SourceSafe 存储文件的方式形成鲜明对比。

CVS 客户端可以通过两种方式连接到 CVS：直接查看仓库（如果它位于本地机器上），或使用 pserver 协议进行连接。理论上，可以共享网络驱动器（类似 SourceSafe）来允许前一种连接方式，但使用 pserver 协议是实现客户端/服务器环境中 CVS 的最佳方式。

CVS 通常在 UNIX 下运行，且通常与文件的本地副本位于同一台机器上。在前面的拓扑示例中，CVS 是由每个用户通过到开发服务器的 shell 连接运行的。对于更精通 UNIX 的用户来说，这可能是首选路线。对于不那么精通 UNIX 的用户，则存在一个名为 WinCVS 的类似 SourceSafe 的 Windows 客户端，它复制了 UNIX 客户端的大部分功能。

在 CVS 中解决冲突通常相对简单。CVS 会尽可能进行合并，然后向用户展示一个带有注释以演示冲突的新版本。用户随后修改此新版本以解决冲突，保存它，然后重新提交。CVS 然后将其存储为最新版本。当然，当冲突更严重时，也会出现困难。

CVS 可能是一个不错的选择，但其并发版本控制可能并不适合所有人（原因如前所述）。请仔细考虑这是否适合该项目，以及其存在是否可能鼓励开发人员养成不良的工作习惯。

## Subversion

CVS 的继任者是越来越受欢迎的应用程序，本书作者偏好的 Subversion（SVN）。Subversion 试图保留 CVS 中所有出色的特性，并取代那些不那么出色的特性。它在需要时提供对仓库的直接文件系统访问，但也拥有一个出色的 Apache 模块，可通过 HTTP 上的 WebDAV 实现远程用户访问。此方法不需要在防火墙中打开任何额外端口，也不需要在服务器上运行额外的守护进程，并且提供了比 CVS 中 pserver 强大得多的权限系统。备份和恢复是一项简单操作，整个仓库可以导出为纯文本文件，并相对轻松地迁移到新服务器。

像 CVS 一样，SVN 是一个并发版本控制系统，可通过命令行界面和图形界面访问。对于在 Windows 上开发的用户，Windows 资源管理器的 TortoiseSVN 扩展非常易于使用，并将所有 SVN 功能集成到 Windows 资源管理器上下文菜单中。Mac OS X Finder 也有类似的插件（尽管在撰写本文时不够强大）。

## Other Minor Contenders

大量其他商业源代码控制系统常见于大型软件开发公司，包括 Perforce、BitKeeper、Git（用于管理 Linux 内核）、Bazaar 和 Microsoft 的 Team Foundation Server。其中一些采用的架构似乎仅对大型开源应用有效；另一些则有许可证限制和高昂成本。你应该进一步探索这些选项，并尝试其中的一些其他应用程序。

## Advanced Version Control Techniques

版本控制的内容远比本附录所能涵盖的多。就像 PHP 中的许多内容一样，这个话题本身就足以写成一本书。不过，有一些有趣的技巧，你可能希望在所选的版本控制环境中使用。

## Branching

*分支*涉及将单个项目分叉为两个并行项目。这是一种非常有用的代码重用技术。假设你为两个不同的客户端开发两个内容管理系统，这两个系统在功能上几乎完全相同——唯一的区别是次要的或美观的。显然，你希望从一个系统中重用代码到另一个系统，但这样做存在一个陷阱。如果你在第一个项目中进行重大更改，你希望该更改传播到第二个项目。反之，你在第二个项目中所做的任何更改，你可能不希望向上传播到第一个项目，因为这些更改代表定制。

分支就是解决方案。通过将第一个项目分支形成第二个项目，你的版本控制软件会自动将对第一个项目所做的任何更改在发生时（以及发生时）传播到第二个项目，同时保留在第二个项目中所做的更改，作为该项目独有的定制。

分支也可用于维护项目的两个不同方向。例如，你可能希望一组开发人员负责你产品的维护版本，而另一组负责下一个重大版本。分支使你可以拍摄产品在某个时间点的快照，然后分叉为两条不同的开发路径，放心的是，分支前产品的任何重大更改都将传播到这两条路径中。

## Tagging

不要与 CVS 为其自身使用在单个文件中放置的标签混淆，*打标签*涉及为每个文件的给定版本应用任意属性，以创建发布版本。

例如，你可能希望为你的项目创建一个 beta 版本。这涉及将项目中的几乎每个文件打包在一起，但你可能希望使用每个文件的不同版本——此文件的 1.3 版本，那个文件的 1.5 版本，等等。通过为每个文件打上正确版本的标签，你可以轻松地告诉你的版本控制软件按需交付特定版本。单个开发人员可以在他们觉得有把握时（以及随时）移动标签；这样，无论何时你请求特定版本（无论是 beta 版、候选发布版 1 还是其他），你都可以确定获得的是最新稳定版本。

## Comments

所有版本控制系统中一个经常被忽视的功能是签入时应用注释。签入文件时，开发人员会被要求提供一个注释。最好确保你的开发人员利用此功能并提供简短描述，即使只是像“修复了 bug 21301”这样简单的内容。在查看特定文件的历史记录时，这些信息可能非常有用。

## Binary Files

将二进制文件（例如图像）添加到仓库时，应始终小心。虽然将整个项目保存在一个地方通常是个好主意，但许多版本控制包在处理二进制文件时效率极低，面对几十个 JPEG 文件时可能会变得极其缓慢。

考虑是否有第三种方法。例如，考虑那些包含页面标题的 .GIF 文件。是否可以用单个 PHP 脚本替换它们，该脚本在需要时使用 imagetext 渲染标题？这种“跳出框框”的方法可能至关重要，因为二进制文件只是版本控制可能不合适或笨拙的一个例子（更不用说让 PHP 制作所有这些标题图形，而不是由制作图形设计师，或者更糟的是你自己，所带来的生产力提升了）。

## Summary

在本附录中，你接触到了版本控制的原理和方法论及其在大型项目中的用途。你了解了并发版本控制与独占版本控制之间的区别。你简要了解了典型版本控制基础设施的拓扑结构，并考察了该基础设施在多个流行版本控制包中的实现。最后，你学习了版本控制中一些更高级的技术，以及它们如何对你自己的项目有用。




## PHP IDEs

使用他们最喜欢的编辑器，许多开发人员仍然倾向于使用 PHP 进行编程，并开发自己调试代码的首选方法；但有数百万开发人员在使用 PHP，为什么集成开发环境 (IDE) 并不像 Visual Studio .NET 用于 ASP .NET 那样被广泛使用，这仍然有点令人费解。这可能是因为许多人仍然不将 PHP 6 视为独立的成熟编程语言。（当然，作者希望根据你在本书中看到的内容，你持不同看法。）

无论如何，PHP 6 是一门成熟的编程语言，且适用于它的 IDE 确实存在。如果你尚未使用支持 PHP 6 的 IDE 进行开发，那么本附录就是为你编写的。IDE 中包含的大量有用功能可能会让这项投资对你来说物有所值。当然，最大的用途之一是大多数 IDE 提供的高级调试设施。

虽然本附录并未对市面上每个 IDE 提供全面详尽的概述，但它将让你了解从某些主要 IDE 中可以期望什么，以及还有哪些其他选择。大体上，你应该能够从它们的文档中更深入地了解每个 IDE 的功能。本附录首先详细介绍 Zend Studio，因为这是市场上最大的以 PHP 为中心的 IDE。随后，将简要探讨 Komodo 等替代方案。

## 选择 IDE

IDE 的目的是为你（开发人员）提供开发强健应用程序所需的所有支持和帮助，以高效、准确地进行开发。实现这一点的方式因产品而异，但在所有 IDE 中都有一件你应该寻找的东西。与你使用的任何软件一样，在长期在某一环境中开发之前，首先要决定的事情之一就是该环境是否对你有益。换句话说，IDE 是否让你更轻松地开发应用程序？如果是，那么理所当然，你应该将该产品作为你首选的开发环境。就这么简单。

然而，将问题简单化为你认为所选 IDE 是否在履行其职责，忽略了一个你应该牢记的重要事实。与任何其他软件一样，可能需要一些时间才能充分利用这些 IDE 内在的强大功能，因此花时间熟悉它们是值得的。为此，以下几个部分应该能让你了解预期情况。

## Zend Studio

在寻找 IDE 时，Zend 的产品理应是你的首选之地——前提是你愿意支付大约 399 美元的费用。当然，在购买之前，你应该仔细查看它，可以从 www.zend.com/en/products/studio 下载免费试用版。

撰写本文时，Zend Studio 的当前发行版本为 6.1，尚未包含对 PHP 6 的完整支持，但预计在 PHP 6 正式发布后将提供支持。它适用于 Windows、Linux 和 Mac OS X 平台，并基于 Eclipse。其他基于 Eclipse 的 IDE 包括 Adobe Flex，两者紧密集成，为使用 Flex 和 PHP 创建富 Internet 应用程序提供了一个引人注目的平台。

如果你不熟悉 IDE，它们起初可能会让人感到有些望而生畏。请记住，它们的目的在于提供帮助，而不是增加混乱。在此情况下，Zend Studio (ZS) 不仅仅是一个 IDE；它还提供开发环境之外的功能，包括代码分析、与 JavaScript 库的集成、SCM 集成等等。就本附录的目的而言，我们将主要集中于使你能够管理和开发代码的工具。考虑到这一点，ZS 中呈现给你的第一个屏幕与图 B-1 所示的非常相似（显示一个示例项目）。

![](img/a1b732997d9cb194dceec0570dc79710_646_0.png)

图 B-1：Zend Studio 中的示例项目

大量文档涵盖了 ZS 的所有功能，因此此处没有必要详尽地介绍所有内容。相反，让我们聚焦于最重要的功能，以让你大致了解 ZS 的用途。在使用 ZS 一段时间后，你可以决定是否要采用它。

### 管理项目

在图 B-1 的左上角，你会注意到 PHP Explorer 窗口。这显示了工作区中所有项目的列表。你可以将工作区视为你各个项目的主要存储库；在大多数场景中，你的计算机上只需要一个工作区。工作区中包含一个或多个项目。每个 ZS 项目对应你的一个实际项目。请注意，项目不必在物理上存储为包含工作区的文件夹的子文件夹。

MyProject 窗口使你能够浏览正在处理的任何给定项目，并执行各种操作，例如从特定项目中添加和删除文件。或许值得提及的是，Zend 开发环境 (ZDE) 主菜单上的“Project”菜单项使你能够创建、打开、保存和关闭项目，并编辑项目属性，例如部署目标。

你使用项目为文件定义一个共同的工作环境。例如，在为客户处理新网站时，你可能希望拥有一个特定的调试配置。将网站的文件放入项目中，使你能够以高效的方式完成此操作。

![](img/a1b732997d9cb194dceec0570dc79710_647_0.png)

图 B-2：代码补全弹出窗口

### 编辑代码

显然，你会期望这样一个全功能 IDE 包含某些编辑功能，ZS 当然也有一些不错的功能。编辑窗口是图 B-1 中显示的大型中央窗口，它包含一系列旨在让编码更轻松的工具。主要功能之一是代码补全，适用于 PHP 和 HTML。这使你能够显示函数参数、已声明函数、关键字和常量的弹出窗口。图 B-2 显示了在开始键入 PHP 6 数组函数时出现的弹出窗口示例。

与该 IDE 的大多数方面一样，代码补全是可配置的，你可以通过选择 Tools ➜ Preferences ➜ PHP ➜ Code Assist 来查看选项。

Preferences 窗口为你提供许多其他可配置设置，例如编辑和调试选项。

ZS 还为你提供代码缩进选项。你可以选择在输入时手动缩进代码，或者一次性全部缩进——这是一个能让生活更轻松的不错功能。如果你查看 Preferences 对话框中的 PHP ➜ Editor 部分，将看到所有可用编辑功能的列表。其中更有用的功能之一是匹配括号功能，如图 B-3 所示。

![](img/a1b732997d9cb194dceec0570dc79710_648_0.png)

图 B-3：括号匹配

在开始元素之前或结束元素之后立即放置光标，会导致编辑器高亮显示匹配的元素。这里的一个有用技巧是按 Ctrl+Shift+P 在匹配元素之间跳转，以避免繁琐的滚动。有关更多导航快捷方式，请参见 Navigate → Go To 菜单。

模板也可用于加速原本重复的任务。提供了几个模板，但你也可以添加自己的模板或修改包含的模板。要查看可用模板，请选择 Preferences 窗口的 Template 选项卡。每个模板都有一个指定的键，用于表示其特定模板。例如，图 B-4 显示了在 Editor 窗口中键入 my 的结果。

![](img/a1b732997d9cb194dceec0570dc79710_648_1.png)

图 B-4：代码补全模板

前四个选项均为随 IDE 提供的模板。如果你单击其中一个，分配给该键的模板代码将自动添加到 Editor 窗口。图 B-5 显示了单击第二个选项的结果。

![](img/a1b732997d9cb194dceec0570dc79710_648_2.png)

图 B-5：选择选项模板的结果

还有许多其他有用的编辑功能，范围从 HTML 标签快捷方式到语法错误高亮显示。真正学习这些功能的唯一方法就是与它们交互。帮助文件很好地概述了 IDE 的所有功能，因此请使用它们来熟悉环境。让我们继续，看看 ZS 的另一个有用功能。

### 检查代码

回到图 B-1，左下角的窗格称为 Outline。它带有三个选项：Outline、PHP Project Outline 和 PHP Functions。第一个选项为编辑器窗口中具有焦点的文件的所有元素提供一个可折叠列表。如果需要，你可以使用它进行导航。双击 Outline 窗口中列出的任何元素，都会将光标直接移动到源文件中的那段代码。





你可以通过单击“项目”标签从上一级查看代码。这可以让你概览当前项目中的所有内容。它的工作方式与“文件”窗口非常相似：你可以在“项目”窗口中单击任意文件或文件中显示的元素，然后该文件将在主窗口中打开以供编辑。

最后一个选项“PHP 函数”将列出所有 PHP 函数及其语法。如果你想了解的内容不仅限于某个函数的用法，可以在“大纲”窗口中突出显示该函数并按 F1，以查看在浏览器窗口中弹出的更详细的信息文件。顺便说一下，这也适用于编辑器窗口中的 PHP 函数——只需突出显示你想了解的函数并按 F1 即可。

## 使用 ZDE 进行调试

为了简化起见，假设所有内容都在一台机器上运行，以便你可以在本地调试应用程序。可以通过在中心非本地服务器上安装 Zend Platform 产品来设置多用户调试环境，有关详细信息，请查阅文档。

使用 IDE 能带来的最大优势之一就是可以利用其提供的创新调试功能。翻阅错误日志文件是一种方法，但与可用的更复杂的方法相比，这显得相当笨拙。内置调试器拥有一系列功能，旨在帮助你监控代码中确切发生的情况。具体来说，其主要功能是为你提供以下内容：

- 程序流监控
- 调试窗口
- 调试消息窗口
- 输出呈现

让我们详细了解一下这些内容。

你需要首先熟悉的事情之一就是如何调试代码。ZS 提供了多种在不同位置之间移动的方法。有些方法涉及设置断点，而其他方法只是逐步跟踪程序流程。单击“运行”->“调试”。当提示切换到 PHP 调试透视时，单击“是”。Eclipse 和 ZS 中的透视是另一组针对特定任务（在此例中为调试）定制的 UI 元素。

如图 B-6 所示，一组箭头可用于单步跳过和在断点之间移动，或者只是运行你的代码。

![](img/a1b732997d9cb194dceec0570dc79710_649_0.png)

图 B-6：调试窗口中的箭头

在你熟练掌握如何单步跳过代码或跟踪脚本执行后，可以使用这些功能来了解代码状态的重要信息。默认位于 ZS PHP 调试透视左上角的“调试”窗格为你提供五个选项来监控和管理项目的调试。从这里，你可以查看变量的值、监视点的位置、堆栈跟踪、断点的位置以及缓冲区。所有这些都可能派上用场，具体取决于你想确定代码的哪些方面。

例如，假设你已单步跳过一个非常简单的 PHP 脚本的执行，以演示“变量”标签如何向你显示与代码关联的所有变量（包括全局变量）的信息。如图 B-7 所示。

![](img/a1b732997d9cb194dceec0570dc79710_650_0.png)

图 B-7：“变量”标签

调用调试器后，如果你查看编辑器窗口，将看到应用程序执行的第一行被高亮显示。这是因为，目前调试器已在脚本执行的此点停止。你在“变量”窗格中看到的值是程序执行到此特定点时的值。如果你已经知道想要检查的代码片段，可以跳过逐行单步跳过所有代码，而是将光标放在你希望调试器前往的那一行上。单击“运行”->“运行至行”（或按 Ctrl+R）以运行应用程序，直到它到达该行代码。

跟踪执行堆栈也是确定代码中当前位置的有用方法。“调试”窗格让你可以查看程序堆栈中的当前位置。这很有帮助，因为如果代码的一部分调用一个函数，程序的执行会离开当前位置去运行被调用的函数。如果该函数本身又使用其他函数，那么程序的执行将再次前去执行那些函数。能够确切确定自己在其中所处的位置，正是调试器堆栈跟踪功能的作用所在。

图 B-8 显示了一个示例，其中“调试”窗格被用来跟踪一个简单的脚本，该脚本正在从 index.php 文件调用的类中执行一个方法。

![](img/a1b732997d9cb194dceec0570dc79710_651_0.png)

图 B-8：在“调试”标签中查看堆栈

与其在代码的不同区域中逐步进入、跳过和绕过，有时我们只希望应用程序运行直到到达源代码中的某个特定点。为了让调试器在你想要的位置停止，必须设置断点。断点只是告诉调试器冻结当前执行状态的分隔符，以便你可以查看所需的任何内容。

如图 B-9 所示，通过在编辑器窗口中单击行号左侧的区域，已在第 33 行上设置了一个断点。这会导致选定行在边距中显示一个点，表明现在已设置了断点。在 PHP 调试器透视中单击“断点”标签即可为你验证这一点。

![](img/a1b732997d9cb194dceec0570dc79710_651_1.png)

图 B-9：设置断点

做完这些之后，还剩下两件事需要提及。第一个是“控制台”窗格，它默认位于窗口的左下角。它会显示在脚本调试过程中出现的通知、警告和错误。双击“控制台”窗格中的消息，即可通过将光标发送到编辑器窗口中的相应位置，轻松定位其来源。

最后，ZS 还会在“调试输出”窗格中呈现你的脚本输出。一旦脚本生成任何输出，这就会在 ZS 窗口的右侧弹出。使用它来监控脚本是否生成了正确的标头和 HTML 输出。呈现的 HTML 可以在“浏览器输出”标签中查看。

Zend 还提供了其他调试功能。例如，使用远程调试，你可以在应用程序在网站上运行时实际对其进行调试。这样做有几个优势，因为你可以跟踪应用程序像往常一样处理输入。否则，这通常相当困难。此外，“调试”窗格的输出会显示在浏览器中。这一切都需要 Web 服务器上运行 Zend Server。（此类安装的详细信息超出了本书的范围。）

考虑到所提供的所有调试和编辑功能，我们鼓励你下载一个演示版并试用一下。你永远不知道——你可能会发现这就是你编程梦想的答案。在结束对 Zend 开发产品的快速概览之前，还应提及几种其他重要工具。

## 更多 Zend 工具

Zend 还提供一个性能分析器（单击“运行性能分析”以进入 PHP 性能分析透视），用于帮助分析应用程序的性能。可以使用此性能分析器通过识别问题区域来确定如何改进应用程序的性能。几个标签为你提供不同类型的信息，范围从饼图（显示脚本消耗的时间量）到表格和图表（显示各种函数的统计信息，以及调用跟踪以监控从一次调用到下一次调用的线性时间消耗）。

此外，Zend 可以与 CVS 和 SVN 版本控制集成，因此你应查阅文档以了解如何设置和运行此功能。（附录 A 提供了有关 CVS 和 SVN 的更多详细信息。）

最后，还有 Zend Guard，它使你能够使用混淆代码分发 PHP 应用程序，这可以防止他人轻松理解应用程序逻辑——从而使无需担心盗版问题即可分发闭源应用程序成为可能。对于大多数应用程序而言，如果分发者是唯一处理源代码的个人，或者任何根据开源许可证向公众发布的内容，Zend Guard 都是不必要的；但是，如果你计划将应用程序出售以安装在客户的 Web 服务器上，并且担心保护你的知识产权，那么像这样的产品可能会让你感兴趣。Zend Guard 还包括许多许可方案的实现。

## Komodo

你可以从其网站 (www.activestate.com/Products/Komodo/) 下载 ActiveState 的 Komodo 试用版。专业版（用于商业用途）需要 295 美元，因此在购买之前先试用演示版当然是个好主意。从历史上看，它曾同时适用于 Linux 和 Windows，但随着最新版本（4.4）的发布，它现在也适用于 Mac OS X。

Komodo 是一款备受推崇的 IDE，支持多种开源编程语言（尽管它本身是闭源商业软件），而非仅限于 PHP。它支持（包括但不限于）Perl、Python、Ruby、Tcl、HTML、CSS、JavaScript 和 XML。不过，撰写本文时，PHP 6 调试器扩展尚未发布，因此 Komodo 中的调试支持仅限于早期版本。你应查阅 Komodo 网站以获取有关此方面的任何更新。

## 管理项目

Komodo 为你提供了一个项目管理器，可用于执行大量操作。默认情况下，它位于 IDE 窗口的左侧，项目相关功能可以通过“项目”主菜单项访问。除其他功能外，你可以执行以下操作：



- 创建和打开项目
- 添加文件和文件夹
- 添加命令、模板、URL、Web 服务和对话框
- 组织、保存和关闭项目

此外，您可以通过右键单击项目成员来访问弹出式上下文菜单。您将获得哪个上下文菜单取决于所选元素的类型。

## 编辑代码

Komodo 的代码编辑器具有一些有趣的功能，以及着色和缩进等更标准的功能。例如，提供了代码折叠功能来折叠代码段，使您可以查看代码的抽象（或骨架）版本，以了解正在发生的情况。图 B-10 显示了带有折叠代码的编辑器窗口。

![](img/a1b732997d9cb194dceec0570dc79710_653_0.png)

图 B-10：带有折叠代码的编辑器

编辑器还为 PHP 提供自动完成功能——具体来说，是针对类、函数和变量。键入单词 new 时，将显示当前文件和包含文件中的类；使用 -> 运算符时，将显示类方法。同样，在键入四个匹配字符后，将显示所有用户定义的函数和 PHP 函数。

编辑器的另一个实用功能是提示，告诉您可以在函数中使用哪些参数。在为给定函数（无论是用户定义的还是 PHP 函数）键入开始花括号后，这些提示会显示出来。图 B-11 显示了用户定义函数的调用提示。

![](img/a1b732997d9cb194dceec0570dc79710_653_1.png)

图 B-11：用户定义函数的调用提示

编辑器中还有许多其他功能，但其中大多数使用起来相当直观，此处无需详细介绍。它们包括以下内容：

- 最近使用列表
- 检测更改的文件
- 在浏览器中预览
- 后台语法检查
- 代码注释

## 使用 Komodo 进行调试

此处未详细介绍 Komodo 的调试器，因为 PHP 6 扩展尚未发布。要使 Komodo 的 PHP 调试器正常工作，需要满足一些配置要求，您应查阅文档以获取说明。除此之外，Komodo 为您提供了一个功能齐全的调试器，其中包括以下内容：

- 断点控制
- 单步执行
- 监视变量
- 查看调用堆栈
- 发送输入
- 添加命令行参数

当然，Komodo 附带了许多其他工具来补充其编辑器和调试器。让我们快速看一下。

## 更多 Komodo 工具

由于 Komodo 允许将大量项目添加到项目中（例如快捷方式、文件夹、文件、命令和模板），因此它还提供了一个工具箱来存储所有这些项目以便轻松访问。您可以通过右侧窗格中的选项卡或“工具箱”主菜单项来使用工具箱。图 B-12 显示了工具箱中可用的示例项目。在此示例中，代码片段是通过双击将其添加到代码窗口中的。

![](img/a1b732997d9cb194dceec0570dc79710_654_0.png)

Komodo 还可以与 CVS、SVN 和 Perforce 集成。要启动并运行此功能，请从主菜单单击“编辑 > 首选项 > 源代码控制”，然后配置您选择的源代码控制工具。

同样，您应该下载演示版本来试用 Komodo。就成本而言，一个需要注意的地方是，您可能会发现自己为不太有用的功能支付了额外费用。例如，Komodo 中包含的一些工具专门针对 Perl（例如 Perl 开发工具包）。这增加了 Komodo 的开发成本，但对 PHP 项目管理帮助不大；不过，如果您经常用其他语言进行开发，这可能对您有用。

## 其他 IDE 和编辑器

为专业 PHP 开发者提供了许多其他开发环境。有些比其他更有用，具体取决于您如何使用它们。例如，PHPEdit（适用于 Windows）提供了一大堆有用的编辑工具，以及一个调试器。它可在 www.phpedit.com 免费下载。以下是其主要功能的简要介绍：

- 语法高亮
- 代码提示，代码洞察
- 集成 PHP 调试器
- 帮助生成器
- 可自定义的快捷方式
- 超过 100 个可脚本化的命令
- 键盘模板
- 待办事项报告生成器
- 快速标记
- 插件

您可能还想查看一些其他 IDE 和编辑器：

- PHPEclipse (www.phpclipse.de)
- EditPlus (www.editplus.com)
- NuSpherePHPEd (www.nusphere.com)
- PHPCode (www.phpide.de)

当然，仅仅因为本讨论未涵盖所有可用选项，并不意味着它们不值得查看。例如，NuSphere 的 PHPEd 提供了大量高级功能，如代码补全、调试、性能分析和部署设施等。作为一个 IDE，它获得了一些赞誉，并且值得深入调查。

## 摘要

本关于集成开发环境（IDE）的附录让您了解市面上有哪些产品，以及您可能从支持 PHP 的 IDE 中期望什么。您已了解 Zend Studio 作为 PHP 特定平台的环境，以及 Komodo 作为支持 PHP 6 的开源环境。

发现使用 IDE 带来的优势是一项有益的过程，因为使用 IDE 应该能提高您的工作效率。由于购买上述 IDE 等开发工具代表一项投资，因此在做出选择之前，您应该花些时间仔细查看每个工具的功能。

## PHP 性能调优

配置得当，精心打造的 PHP 应用程序的性能可以与任何其他应用程序环境（例如 Java、ASP.NET、Ruby on Rails 等）相抗衡。

需要考虑两种性能：程序员的性能和应用程序执行的性能。本书其余部分提供了提升前者的框架。本附录涉及提升后者。无论您是有兴趣榨取自己精心设计的应用程序的最佳性能，还是试图在不购买新硬件的情况下挽救另一方编写的糟糕应用程序，本章中的许多技巧都将派上用场。

在本附录中，您将学习识别不同类型的性能瓶颈以及如何查找其原因。之后，您将了解如何为最佳效率和速度设计和编写代码，以及如何追溯修复您不幸继承的糟糕代码。

### 性能问题简介

通常，您第一次听到应用程序运行缓慢是从用户那里得知的。不幸的是，用户在这方面很少特别有用。办公室里“这东西太慢了”的喊声几乎毫无信息量。因此，进行一些调查很重要。

### 性能瓶颈类型

让我们回到基础，来看看 HTTP GET 或 POST 请求的结构。当用户的 Web 浏览器发出请求时，它会与 Web 服务器建立套接字连接，通常是端口 80；对于 SSL 连接，则是端口 443。这是 Web 浏览器中的阻塞活动，之所以如此称呼，是因为浏览器在连接成功建立之前无法执行任何其他操作。不过，在实际中，大多数现代 Web 浏览器允许用户在连接尝试进行过程中取消，并且在更快的连接上，连接会在不到一秒的时间内建立；但是，如果服务器负载过重，建立连接可能需要一段时间。如果是这种情况，则说明该服务器上的其他应用程序或进程正在拖慢速度（不一定是问题所在的应用程序）。

建立连接后，Web 浏览器不会等待任何响应，因为 HTTP 协议并未规定应有响应。它会立即发送一个非常小的请求数据包，通常不超过几个字节。此请求包含（除其他数据外）Web 浏览器需要的文档，以及用户作为请求一部分提供的任何 `GET` 或 `POST` 参数。

此请求本身很小。从套接字连接建立到将请求发送到 Web 服务器之间的时间可能非常短。

从 Web 服务器接收请求到开始返回数据之间的时间称为脚本的 _处理时间_。在大多数情况下，PHP 会在整个脚本执行完毕之前不尝试向 Web 浏览器发送任何输出，除非您的输出量超过 `php.ini` 中 `output_buffering` 的值。这意味着处理时间大约等于 PHP 开始执行脚本到执行完毕之间的时间。这是延迟最可能发生的地方。

从数据开始返回到 Web 浏览器到数据传输完成之间的时间称为 _传输时间_，它不太可能以任何方式与 PHP 相关。此数据传输所需的时间更可能与网络性能相关，无论是服务器端（例如连接过载）还是客户端（例如调制解调器极其缓慢）。除非您的页面重量超过 55 KB（通常被视为合理网页的限制），否则这不太可能是延迟的原因。

识别性能瓶颈所在位置的最简单方法是使用手动工具（而非真正的 Web 浏览器）发出 HTTP 请求，然后自行分析结果。

## 区分不同类型的瓶颈

假设您想要分析在服务器 www.example.com 上针对页面 /example.php（GET 参数 foo 等于 bar）的请求中，性能问题可能出现在哪里。这当然等同于 `http://www.example.com/example.php?foo=bar`。启动控制台会话，并按如下方式使用 telnet：

```
ed@host: $ telnet www.example.com 80
Trying 192.168.1.2...
Connected to www.example.com
Escape character is '^]'.
GET /example.php?foo=bar HTTP/1.1
Host: www.example.com
```

服务器的典型响应可能如下所示：

```
<HTML>
<BODY>
Hello, World!
</BODY>
</HTML>
```





在 Windows 中，同样的方法也适用——启动命令提示符，并以完全相同的方式使用 telnet。

当然，要获得实际输出，您需要将主机名和 URL 替换为真实示例。在看到空行时按 Enter，并完全按所示输入空格。您可能会发现先在记事本中全部写好，再粘贴到 telnet 中会更轻松。

执行此操作时，请准备好秒表。观察延迟发生的位置，并按以下推断：

- 按下 Enter 与观察到 Trying 192.168.1.2 之间的延迟，表明针对服务器 IP 地址对名称服务器进行解析时出现延迟。这很不寻常。这可能表明名称服务器无响应，无论是您自己使用的名称服务器（通常是您自己的 ISP 提供的），还是为问题服务器所在域名服务的名称服务器（通常是托管该服务器的 ISP）。这种无响应存在的原因超出了本书的范围，但您至少可以让自己放心，PHP 不应受到指责。对于真实世界用户来说，这种延迟仅在首次访问网站时会体验一次，因为大多数 Web 浏览器（实际上，操作系统也是如此）会缓存名称服务器查找的结果。

- Trying, ... 行与 Connected 行之间的延迟，表明服务器本身花费了一段时间才成功响应您的连接请求。此处出现延迟影响极大，因为包含多个图片的页面可能轻易包含 20 或 30 个 HTTP 请求。如果每个请求都有延迟，那么即使脚本执行时间非常快，页面也可能会显得极其迟缓。不幸的是，延迟可能存在于两个位置之一：要么是服务器往返的网络，要么是服务器及时响应连接的能力。后者可能由服务器负载引起，而服务器负载又可能是由未优化的 PHP（不一定是该脚本）或其他进程使服务器不堪重负引起的。快速检查服务器上的内存和 CPU 利用率可以在这里揭示真相。如果是前者，则对其进行故障排除超出了本书的范围。如果是后者，那么您应该尝试追踪是哪个脚本引起了问题；如果是 PHP，则应将此处所示相同的方法应用到该脚本上。

- 在输入 HTTP 请求后按两次 Enter 与看到响应 HTML 之间的延迟，几乎可以肯定表明处理时间性能不佳。这可以通过在代码中添加监视来验证和确认。

假设延迟可以追溯到脚本处理时间，您现在可以确定脚本中是什么导致了延迟（或延迟）。

## 了解 PHP 请求的结构

暂且不论良好 PHP 架构的广泛准则，请记住 PHP 是一种脚本语言。其脚本有开头、中间和结尾，就像任何脚本语言一样。确实，在最基本、最简化的层面上，任何 PHP 脚本的执行模式大致如下：

- 1. 对于 index.php 的请求，打开 index.php 并对其内容（以及 index.php 包含或要求的任何文件的内容）进行词法分析。这意味着将 $x = $y + 2 解释为类似下面的内容：

```
VARIABLE "x" EQUALS VARIABLE "y" PLUS 2
```

- 2. 接下来，解析字符串的词法表示形式以创建实际可执行指令。这包括确保变量 $x 和 $y 是有效的，加法运算符可以对 $y 和常量整数执行，然后构建实际执行指令，以字节码的形式。

- 3. 将字节码传递给 PHP 虚拟机，并执行其中包含的指令。这涉及以下内容：

  - a. 读取输入参数，无论是 GET、POST 还是 COOKIE。

  - b. 使用这些输入参数做出决策，在此过程中查询外部数据源。

  - c. 生成输出并发送到 Apache/IIS 以传输到请求客户端。

## Opcode 缓存

大型 PHP 应用程序中最大的性能滞后之一（除了由糟糕的应用程序设计引起的情况）发生在词法分析/解析步骤期间，该步骤会对请求中包含的每个文件执行，并且针对对这些文件的每个请求重复执行，即使源代码没有更改。您可以通过使用一种称为操作码缓存（或简称 opcode 缓存）的东西，来避免为每个请求重复这两个步骤。

Opcode 缓存应用程序保留解析步骤的输出，即发送到 PHP VM 的实际指令，并将其保存，通常在内存中，以便在对同一源代码文件的后续请求中使用。在包含数千行 PHP 代码的大型应用程序中，这可以显著提升性能。此外，在 PHP 6 中，最好的 opcode 缓存之一已包含在发行版中，并且默认处于启用（但未打开）状态。替代 PHP 缓存（APC）长期以来通过 PECL 作为可选（但强烈推荐）PHP 模块提供。然而，它的实用性、性能、配置灵活性和简单性使其在 PHP 源代码库中被提升为一等公民，现在已包含在 PHP 6 源代码中。

要启用 APC，请在 php.ini 文件中将 apc.enabled 设置为 1。您还需要配置其他一些参数，例如应分配多少内存给缓存、应使用哪种缓存类型，以及排除文件被缓存的任何过滤器。现有的 APC 文档相当不错。Google 搜索应该能找到大量有关如何正确配置 APC 的有用材料。有关基本文档，请参见 www.php.net/manual/en/book.apc.php。

## 其他性能问题来源

剩余的性能问题来源（一旦尽可能消除词法分析/解析步骤）归结为应用程序设计和系统工程。

这些延迟将归结为以下三者之一：

- 算法不佳——低效代码导致执行时间较长

- 硬件不佳——代码并不不合理，但其运行的硬件已老化或负荷过重。

- 外部瓶颈——数据库导致延迟

硬件很少是问题所在。除极端情况（例如大量使用 GD 进行图形渲染、大量数值计算或大型报告应用程序）之外，PHP 本身所带来的开销不需要大量系统资源。

### 追踪瓶颈

解决每种不同的可识别瓶颈都有简单的步骤，如本附录其余部分所述。然而，您的首要任务是确定瓶颈所在的位置以及它属于先前描述的三个类别中的哪一个。

### 数据库查询

最容易追踪的罪魁祸首是慢速数据库查询。几乎所有企业级 PHP 应用程序都依赖于某种数据库。本书大力推荐 PostgreSQL，但许多应用程序（特别是您会遇到的由第三方编写的应用程序）将使用更流行的 MySQL。

在尝试优化代码之前，必须先消除数据库瓶颈。因为大多数代码在某种程度上都依赖于数据库（即使只是为了数据的供应），在数据源得到优化之前查看代码并不是时间的合理利用。

确定脚本中是否存在数据库瓶颈的最简单方法是暂时调整数据库交互代码以添加计时器方法。

考虑 PostgreSQL 抽象层的查询方法。通过在每个查询前后添加错误日志时间戳，您可以显示每个查询花费的时间，并为您的页面轻松生成可分析的日志。以下摘录显示了一个示例，演示如何通过将 `execute query` 语句夹在中间来测量数据库抽象层中执行查询所需的时间：

```php
$intTimeNow = microtime();
$q_handle = pg_exec($this->link_ident, $sql);
$intTimeTaken = microtime() - $intTimeNow;
error_log("DEBUG: QUERY: $sql\n");
error_log("DEBUG: TIME TAKEN: $intTimeTaken\n");
```

这将产生类似于以下内容的错误日志输出：

```
[Sun May 16 22:10:19 2004] [error] DEBUG: QUERY: SELECT id, logged_in, user_id FROM "user_sessions" WHERE session_id='98ce552be0a2ea6b6f69fbebcd14997c' AND user_agent='Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)' AND ip_address='192.168.4.3'
[Sun May 16 22:10:19 2004] [error] DEBUG: TIME TAKEN: 0.003752
```

使用前示例所示处理过的数据库抽象层执行典型 PHP 脚本时，将生成一系列 `DEBUG: QUERY xx` 和 `DEBUG: TIME TAKEN` 语句，如所示。

如果您能确保没有其他警告、错误消息或代码发起的调试语句写入错误日志，并且您对查询耗时的分析目前具有独占性，那么查询模式将更容易分析。





你应该很容易就能发现运行缓慢的部分。在典型设置中，任何持续超过半秒的操作都应引起警觉。还要注意页面查询的总持续时间。总时间超过三秒被认为是非常糟糕的做法，会让用户抓狂。

## 算法

在解决了数据库瓶颈后，你可以安全地查看代码本身。PHP 非常快，因此算法卡顿不太可能成为影响因素，远不如数据库性能差。

不过，通过在脚本中添加类似于排查数据库问题时所用的时间戳输出，你可以确定瓶颈可能所在的位置。

出于显而易见的原因，你无法一步完成此操作。责任在于你，需要在怀疑可能有问题的代码块两侧放置“开始计时”和“停止计时”语句。如果确实找到了某个问题，你可以随时深入并在此代码块内添加更多开始/停止语句，以找到确切的罪魁祸首。不要害怕在 error_log 语句中输出变量值——例如，在 for 循环中提供进度提示。

此方法可以通过使用 APD（Advanced PHP Debugger，高级 PHP 调试器，http://pecl.php.net/package/apd）之类的包在一定程度上实现自动化，但对于较小的应用程序以及采用“最佳实践”模块化方式构建的应用程序，其庞大的功能很可能属于大材小用。

只要不涉及外部数据源，PHP 中步骤之间的进度应该几乎是瞬间完成的。逻辑块之间延迟超过几十分之一秒则指向代码中的严重问题。

## 性能补丁优化

既然你知道了问题所在及其位置，你可以专注于打补丁以提升性能。幸运的是，有一件事你可以肯定：你绝不是唯一遇到此类瓶颈的 PHP 开发者。因此，有一些经过验证的技术可供遵循，以尝试修补这些问题。

### 修复数据库卡顿

前面，你已经了解了如何识别哪些查询拖慢了脚本的执行。查询运行不佳的原因可能有多种因素。优化 SQL 语句是一个庞大的主题，此处没有空间详细介绍。你可以找到大量关于 PostgreSQL、MySQL 及其他数据库的优秀著作，内容涉及查询优化。然而，以下几点值得铭记：

- 数字形式的主键作为主索引始终比字母数字形式的主键更快，即使存在原本看起来显然是主键的候选唯一字母数字值也是如此。通常，所需的是“id”列。
- 确保在 `SELECT` 语句中用于过滤或排序的列（也许更重要的是，列的组合）已定义相应的索引。
- 定期运行脚本清理频繁更新内容的表格（例如在 PostgreSQL 中使用 VACUUM 语句），很可能是明智的投资。
- 永远不要使用 SELECT *。如果你知道想要的列名，请指定它们。这将提升性能。
- 子查询比 INNER 或 OUTER 连接更容易组合，但效率远不如它们。如果可能，请避免使用（这还会作为副作用提高 RDBMS 可移植性）。如果你怀疑子查询正在拖慢应用程序，请尝试根据需要用 INNER 或 OUTER 连接替换它们。有关更多信息，请查阅偏好数据库的文档。

前面的大多数建议只能提高几十分之一秒的速度，但这确实是聚沙成塔的情况，尤其是在处理查询数量众多的页面时。

别忘了，你几乎肯定需要在 PHP 脚本本身之外查找问题 SQL 查询，尤其是在遵循本书中描述的最佳实践原则时。如果你设计了一个高度依赖数据库后端的对象模型，你可能会发现该模型中使用的查询的性能调整会在其他地方带来意想不到的性能提升。同样，在对这种高级类进行更改时，应彻底测试所有依赖它们的组件，以确保功能和行为与预期保持一致。

### 修复代码卡顿

最终，优化数据库查询所遵循的相同原则也适用于此。仅仅知道哪个代码块导致卡顿是不够的；你需要弄清楚哪个 PHP 语句运行缓慢以及在什么情况下。

### 逻辑错误

不过，有时应用程序逻辑中的简单错误才是罪魁祸首。在这种情况下，应用程序的功能正常，因此常规 QA 技术未能发现错误，但代码中的人为错误却对性能产生了不利影响。这些是最容易修复的。

请考虑以下示例：

```
switch ($i) {
case 0:
    array_pop($arMediumArray);
    break;
case 1:
    array_reverse($arAnotherHugeArray);
case 2:
    $arHugeArray = array_unique($arHugeArray);
    break;
};
```

你可能已经注意到，当 $i 等于 1 的 case 下，这段代码缺少 break 语句。这意味着当 $i 等于 1 时，$i 等于 2 的 case 也会被执行。在这种情况下，只需要反转 $arAnotherHugeArray。但是，作为副作用，$arHugeArray 也被去重了。很有可能，如果 $i 等于 1，此 switch 语句之后 $arHugeArray 将不再被使用，因此错误调用此方法未必会直接导致故障。但它很可能做的事情是使该块的执行时间翻倍。添加 `break` 语句可以停止冗余的方法调用，从而加快执行速度。

前面提到的方法仍应能帮助你追踪此类问题。通过打印整个代码块的执行时间以及你认为应当被执行的语句的执行时间，你通常会看到两者之间存在差异。虽然这种差异可能由多种问题引起，但完全有可能是逻辑错误所致。因此，在深入查询优化和其他更强烈的性能调整之前，检查此类问题是值得的，尤其是在使用容易出错的结构（如 `switch` 语句）时。

### 瓶颈规避

在其他所有时间，谨慎运用前面提到的技术应该能让你将瓶颈缩小到单个罪魁祸首身上，或者至少缩小到一组罪魁祸首上。

PHP 内置的（出于各种原因可能非常慢）最常见的方法包括以下几项：

- [ ] 任何依赖外部数据源的方法。本附录已将数据库作为瓶颈单独讨论，但请考虑，例如，访问繁忙磁盘或网络驱动器、HTTP 和 FTP 请求、IP 地址解析，以及通过 SOAP 和 XML-RPC 等 Web 服务协议与其他对象通信。
- [ ] 内存密集型方法在单独调用时可能没有问题，但当与脚本的其他实例争夺物理内存，并因此被迫使用虚拟内存（即磁盘）时，这些方法可能会陷入停顿。通常，任何与内置图形库 `gd` 相关的内容都可能是罪魁祸首，尤其是在处理大图像时。考虑实现缓存技术，或使用定时任务进行离线生成，是否可行。
- [ ] 涉及套接字的任何内容都高度依赖网络性能。同样，在请求时离线进行套接字对话，并告知用户其状态，而不是在请求发生时直接发起套接字对话，是一种更好的方法。因此，考虑维护一个每五分钟处理一次的电子邮件队列数据库表，并在脚本中向该队列插入数据，而不是直接在脚本中发送邮件。
- [ ] 使用共享网络驱动器（尤其是通过 NFS）作为大型二进制文件的来源时，要格外小心。例如，社区网站可能允许用户上传自己的 JPEG 照片用于个人资料。在多服务器环境中，此 JPEG 需要所有 Web 服务器都能访问。使用基于磁盘的文件存储而非数据库（数据库在存储二进制数据方面仍然很糟糕）是有意义的，但共享网络磁盘协议以速度慢著称。相反，考虑使用 rsync 或类似工具在每个服务器上复制二进制数据。同步脚本可能作为后台进程每五分钟运行一次，在服务器之间重新分发数据，因此在初始上传后五分钟内始终可以使用本地副本。

还有许多其他可能导致瓶颈的方法示例。PHP 在线文档在特定方法和类的条目中经常提及潜在的性能问题。




当你依赖于 PEAR 类时，也值得检查你的服务器是否安装了最新受支持的版本。与所有分布式组件一样，错误确实会出现，因此请确保你拥有最新版本，以排除那些错误可能引起的任何性能问题。

## 测试

之前讨论的发现所导致的任何代码或 SQL 查询更改都需要进行彻底测试。确保在测试你更改过的脚本和组件时，应用第 20 章中讨论的相同基本 QA 首要原则，就像测试整个应用程序一样。

这不仅包括测试你在更改过程中使用的输入参数和使用场景，还包括所有可能受你更改影响的可想象的参数和场景。宁可过度测试，也不要测试不足。

如果你是在开发环境而非实时环境中进行了更改，请尝试获取实时数据库或数据存储的副本并在本地进行测试。如果这不可能，请尝试在 Apache（或你首选的 Web 服务器）中设置一个虚拟服务器作为临时暂存环境，使用新代码库连接实时数据库，但与实时环境分离运行。

无论哪种情况，在上线时，请务必确信你的更改不仅能产生提升性能的预期效果，而且不会以任何方式对功能产生不利影响。

## 预防性避免

目前为止讨论的所有内容都涉及修复现有应用程序。这固然不错，但这些临时解决方案依赖于最终用户指出他们遇到的性能不佳问题，这可能会带来相当严重的商业后果。

更有生产力（也更专业）的方法是从一开始就将性能考虑在内进行设计。当然，这本身就是一整本书的内容。一般来说，本书阐述的原则都将性能作为优先事项，因此希望如果恰当使用并在合理的数据量下，它们都不会对你的应用程序产生不利影响。你需要小心的在于你自己的架构。

## 高性能架构技巧

在构建应用程序时，你可以采用以下一些有用的技巧，它们应该有助于从一开始就确保快速、高效的设计：

- 选对硬件 — 即使是世界上最快的 PHP，在不合适的硬件上也会运行得像糖浆一样慢。提供 Web 页面相对简单，因此让性能较弱的硬件充当 Apache 工作马。将强大的硬件留给运行数据库。此外，尽可能让所有服务器都配备高性能 SCSI 磁盘并采用 RAID 配置。

- 在最低级别使用缓存 — 如果你的一些高负载脚本反复产生相同的输出，你真的需要每次都访问数据库吗？诚然，数据库在某些层面上会缓存查询响应，但如果 HTML 每次都相同，为什么不直接缓存 HTML 本身呢？PECL 中有质量参差不齐的各种第三方缓存包，但你可以轻松使用传递给脚本的 `GET`、`POST` 和 `COOKIE` 参数的序列化来编写自己的缓存。通过将该序列化与之前请求的序列化进行比较，你可以确定每个请求的“唯一性”。与之前请求相同的请求可以使用缓存数据来满足，而无需再次访问数据库。

- - [ ] **离线执行不可预测的进程** — 如果你的某个脚本中的进程依赖于某个不可预测的第三方，请强烈考虑将其移至离线执行。最明显的例子是通过支付服务提供商处理信用卡。如果你必须进行实时授权（例如，客户可以购买访问在线内容的权限），那么请使用一个简单的、自动刷新的页面，在数据库更新以指示授权后跳转到成功页面。将一个外部脚本（作为计划任务运行，即使每 60 秒一次）分配批量处理授权卡片的请求，并更新数据库以反映这些请求的成功授权或其他情况。

- - [ ] **谨慎使用数据库** — 并非所有数据都必须使用数据库存储。例如，将内容以 XML 形式存储的内容管理系统，将数据存储在磁盘上可能比存储在数据库中更好。数据库不适合存储大量文本。

- - [ ] **优化数据库查询** — 了解在你特定的数据库类型中哪些查询快、哪些慢，并倾向于使用更快的技术。例如，PostgreSQL 在处理子查询时明显较慢，而 `INNER` 连接可能是更高效的选择。此外，确保所有必要的索引都已建立，同样重要的是，删除任何不必要的索引，因为这些索引实际上会减慢数据库速度。

- - [ ] **负载测试** — 使用现实的流量水平和数据集对各个组件进行负载测试，以确保实际性能与开发时的性能相匹配。这将在稍后更详细地讨论。

### 负载测试

功能测试是 QA 的重要组成部分，但负载测试同样重要，以确保最终项目的整体质量。

简而言之，负载测试涉及模拟若干同时连接到 Web 服务器，并在每种情况下执行典型的用户流程场景。同时，你应该随着负载增加测量脚本的性能，以及对服务器整体的总体影响。

然后可以生成一张数据表，经过适当分析，可以建议在给定的同时用户数下，响应时间将是 *n*。当然，随着同时用户数增加，*n* 显然会趋向于无穷大，但它在什么时候达到不可接受的值，因此，在所讨论的设置中最多可以支持多少同时用户？

像 ApacheBench (`http://codeflux.com/ab/`) 这样的优秀包可以模拟最简单的场景，但更复杂的商业软件（如 LoadRunner）可以通过随机偏离每个用户请求之间的间隔，并请求随机变化的页面序列，来重现更真实的场景，以更真实地匹配真实人类用户的行为。

进行负载测试时，请努力使用另一台服务器（或理想情况下是多台服务器）作为连接到实时 Web 服务器的客户端。这可确保负载测试软件本身不会对 Web 服务器构成负担。此外，请始终尝试使用运行在暂存模式下的实时服务器，或者如果不可行，则在另一台服务器上准确重建实时环境和配置，以确保结果具有代表性。

以非技术性的方式向客户展示测试结果（假设结果为正面）通常很有帮助。这将帮助客户根据自身的商业或运营目标规划未来扩展。

## 摘要

在本附录中，你学习了如何识别代码中可能出现的不同类型的瓶颈，如何逐一定位它们，以及如何快速修复它们。

你还学习了如何通过避免软件和系统架构中的一些常见陷阱，并利用操作码缓存软件来避免不必要的词法分析/解析，从而从一开始就避免性能瓶颈。

最后，你了解了负载测试以及在自己的项目中进行负载测试时必须考虑的一些因素。

## 最佳实践 PHP 安装

如今，似乎任何人都能处理简单的安装。就连你的爸爸妈妈可能也能处理在电脑上安装最新版本的 Windows。

这条规则的例外似乎是 PHP 之类的服务器应用程序。虽然 PHP 网站和提供的文档确实涉及如何让它运行起来，但它们从未真正详细说明这一点。拥有一个可用的安装完全是另一回事，需要一些内部知识。

本附录探讨了如何将 PHP 正确设置为最适合本书详细介绍的那种企业开发的配置。你将了解 Windows 上的 PHP 和 UNIX 上的 PHP 之间的区别，并发现哪种更适合企业开发。

## PHP 安装简介

PHP 是一种应用程序语言。它本身并不是服务器，也不是传统意义上的软件。它也不是 Pascal 或 C++ 这样的编译器。它必须被安装——如果你愿意的话，可以理解为“包装”——在 Web 服务器中。考虑到这一点，每次 PHP 安装都需要某种 Web 服务器，例如 Apache。

因此，“安装 PHP”这一短语可能并不十分准确。“安装 PHP 和 Apache”会更好，但这忽略了 PHP 对第三方库和应用程序的高度依赖，才能实现其任何更复杂的功能。

更糟糕的是，本书向你介绍的大多数应用程序，以及你自己编写的任何有用代码，都需要某种后端数据库。本书主张使用 PostgreSQL 而非 MySQL，但在实践中两者大致相同。




事实上，PHP 安装的实际步骤大致如下：

- 1. 安装和配置各种外部库。
- 2. 安装和配置你的数据库平台。
- 3. 安装和配置你的 Web 服务器。
- 4. 安装和配置 PHP。

正如你所见，这远非易事。更糟糕的是，前面步骤的具体实现方式因你选择的操作系统（UNIX 或 Windows）、Web 服务器（Apache、IIS、Zeus 等）以及数据库平台（MySQL、PostgreSQL、MS SQL Server、Oracle、IBM DB2、Informix）而异。

如果在本附录中详尽介绍每一种可能的组合，不仅会影响制作本书所需的树木数量，更是疯狂之举，因为有一个非常有说服力的论点支持某一种特定组合优于其他所有组合。

## 获胜平台

要明确一点，本书并非关于操作系统之争。那些对伟大的 Windows 与 UNIX 辩论感兴趣的人，可以在 Slashdot（www.slashdot.org）那些永远理性且口才出众的居民中，找到成千上万页经过深思熟虑、见多识广的对话。

不过，我们确实提出如下大胆声明：“Windows 不擅长作为 Internet 应用服务器，正如 UNIX 不擅长作为工作站操作系统。”

这某种程度上是一种笼统的概括，规则当然有例外，但仅在美国就有数以万计的 ISP 和大型企业不会错。虽然 Windows 在企业环境中常作为 Exchange 服务器或域控制器出现，但正是 UNIX 托管着网站和 DNS，并在整个 Internet 上以 SMTP 层路由邮件。同样，虽然有些人选择在笔记本电脑上使用配有 Enlightenment、Gnome 和 KDE 等 X 窗口管理器的 Linux，但他们只是少数。大多数人都认识到，Windows 在桌面端表现出色，而 UNIX 在服务器环境中表现出色。

我们深知 UNIX 是一个注册商标名称，特指某个特定的操作系统，而非我们大多数人日常使用的 GNU/Linux 发行版。我们使用公所周知的称谓 UNIX，是指符合 POSIX 标准的操作系统，例如各种 GNU/Linux 发行版、FreeBSD、OpenBSD、Solaris 等等，有时统称为 *nix 系统。然而，*nix 不易发音，而 GNU/Linux、FreeBSD、OpenBSD、Solaris 等等又需要输入很多字符。因此，我们选择使用 UNIX。

做出这一区分的原因其实非常简单。Windows 界面针对桌面进行了优化，因为它经年累月地以 GUI 桌面应用程序为主要焦点进行开发。成千上万小时投入到研究和演进 Windows 用户界面，以使其直观且高效。它并不完美，但比其 UNIX 同类产品提供的更好。

截至撰写本文时，Microsoft 的 Internet Information Services (IIS) 是在 Windows 平台上托管网站的默认且最流行的选择。尽管它比过去好得多，但 IIS 仍然相当频繁地被发现存在重大且广为人知的安全漏洞，并且常被系统管理员视为不稳定且不可靠。此外，Windows 环境的巨大开销意味着，专用的 Windows 服务器在 Internet 上仍然背负着大量不必要的负担。一台配备 2GB 内存的服务器，轻易就有 512MB 被操作系统及其各种服务占用，而其中只有 64MB 实际用于为其运行的 Web 服务器提供动力。

相比之下，大多数生产 UNIX 服务器根本不运行 GUI，这使它们能够将更多系统资源用于应用程序，而被操作系统占用的更少。诚然，配置起来不太容易，但它快得无可比拟，更加稳定可靠，并且更加“尊重”资源。

你可能已经看出这在说什么了。当然，有人会主张为基于 ASP 的网站使用 IIS/Windows  Web 服务器，因为在 UNIX 上运行 ASP.NET（确实存在）极难成功配置；但这是一本 PHP 书，可以公平地说，在 Windows 上运行 PHP 和在 UNIX 上运行 ASP.NET 一样是个糟糕的主意。

可能存在合理的例外——例如，你正在为一个完全基于 Windows 的客户开发内联网平台，而他或她坚持要求部署到现有的 Windows 环境中。考虑到这一点，你可以在本附录末尾找到说明，帮助你处理差异。然而，这将是例外，而非常态。绝大多数网站都托管在由托管公司运营的机器（或机器集群）上，该公司的操作系统、Web 服务器和编程语言选择仅限于某些预定义配置；对于 PHP，这几乎总是 GNU/Linux 和 Apache。

考虑到这一点，本书假设你的 PHP 安装在 UNIX 上，而非 Windows。这一假设贯穿始终，并在所有演示示例中无一例外地体现出来。在 UNIX 上运行 PHP 是专业人士的选择，而这是一本专业人士的书。

别担心。这并不意味着你自己需要使用 UNIX。确实，附录 B（考察了包括 Zend Studio 在内的各种开发环境）表明，Windows 是桌面上最佳平台，事实也确实如此。你将使用的开发服务器可能就放在你的 PC 旁几英寸处，需要运行 UNIX——但你的工作站不需要。当今还有许多优秀的虚拟化选项，可让性能不错的工作站在 Windows 或 Mac OS 主机操作系统下，轻松愉快地将 UNIX 作为虚拟服务器运行。这是本书作者相当成功地使用过的一种选项。

## 获胜 Web 服务器

在此阶段选择操作系统后，你在 UNIX 上有多种 Web 服务器软件可供选择：Apache、lighttpd、Zeus 和其他。

PHP 可以以两种主要方式编译和安装：作为 CGI 可执行文件，或作为 Web 服务器的组成部分（称为 SAPI 模块）。后一种方式快得多，并能处理更多并发连接。CGI 二进制文件需要为每个 HTTP 请求加载一个 PHP 解释器实例，效率非常低。前面提到的所有选项都支持将 PHP 作为 SAPI 模块。作者不建议任何生产或开发环境将 PHP 作为 CGI 模块运行。

尽管前面所述的所有选项都完全有效，但 Apache 服务器如此普遍，几乎无法避免。它运行着现存一半的网站。请回顾本附录前面提到的，你将要部署到的 ISP 几乎可以肯定会优先运行 Apache，而不是其他任何替代方案。如果你坚持使用 Apache，你的生活将会轻松得多。

它本身也是一个不错的选择。Apache 已被证明稳定、安全且支持非常好；它还在持续开发中。作为开源应用程序，它免费，且不受商业许可证负担。

考虑到所有这些，本节的说明涉及如何在 UNIX 上的 Apache 中让 PHP 运行起来。幸运的是，与操作系统不同，所使用的 Web 服务器实际上根本不影响 PHP 语法，因此本书中的示例，虽然可能特定于 UNIX，但并不特定于任何特定的 Web 服务器。

## 获胜数据库

尽管你已将 PHP/Web 服务器限制在 UNIX 平台上，但这并不妨碍你的数据库服务器是一台完全不同的物理机器。事实上，你构建的许多高流量网站和应用程序几乎肯定需要一个独立的数据库服务器——在某些情况下，甚至需要两三台。

因此，考虑到这一点，大门已为你敞开。你需要在 PostgreSQL、MySQL、SQLite、Oracle、Informix、DB2、Microsoft SQL Server、SAP DB 和更多数据库之间做出选择。

确实，上述所有选项都是绝佳选择。它们都非常成熟且经常更新。由于数据库服务器不暴露在 Internet 上，发现的任何安全漏洞都不太重要。只要配置了合适的防火墙，它们都同样安全。

它们在名义上的可靠性方面存在微小差异，但老实说，对于每一个 SQL Server 的拥护者，也同样有 MySQL、Oracle、DB2 等等的拥护者。

它们也都很快。任何真正的性能差异通常与你如何构建数据库有关，而与数据库服务器本身无关。

考虑到这一点，你可能会难以抉择。我们也是如此，但本书出于多种原因鼓励使用 PostgreSQL：

- 你可能希望尽可能使用免费软件，因为 Apache 和 PHP 都可以免费下载和使用。PostgreSQL 也是如此，因此它通过了第一个测试。
- PostgreSQL 在不成为 Oracle 的前提下，已经尽可能接近 Oracle 等行业标准重量级产品。其语法在很大程度上符合 ANSI 标准，这意味着将应用程序从 PostgreSQL 迁移到另一个数据库是一项相对简单的工作。





- 编写存储过程和函数的丰富环境远远超越了 MySQL 5 提供的有限环境，并支持 Perl 和甚至 PHP 本身等标准编程语言来编写存储过程，而不像 SQL Server 和 Oracle 使用的专有语言；而且，针对地理信息服务等更复杂功能的大量库使其远远优于许多其他企业级数据库服务的替代方案。

- 它方方面面都很出色。除了免费且符合标准之外，它还非常快速、非常稳定，并且设置和安装相当容易。它还得到了 PHP 的很好支持，考虑到本书的主题，这是一个巨大的加分项。

## 安装本身

既然您了解了背景，现在是时候开始安装了。以下假设您有一台可以正常工作的 UNIX 机器，已安装并准备就绪。

如果您还没有 UNIX 机器，并想找个好的起点，GNU/Linux 是面向 PC 硬件的理想基于 UNIX 的操作系统。只需确保在安装过程中选择安装所有开发实用程序，因为您需要它们来让 PHP 运行起来。

此安装假设您的 UNIX 机器已联网，分配了专用 IP 地址，并且可以从您的工作站 ping 通（您的工作站也可以从中 ping 通）。还假设您熟悉基本的 UNIX 命令和实用程序。

如果这一切看起来都没问题，那么您可以开始了。以 root 身份登录到您的 UNIX 机器（或使用 su 从普通用户帐户切换到 root），然后即可开始。

## 下载和安装 PostgreSQL

由于您的开发环境仅供自己使用，您不必担心将 PostgreSQL 放在单独的机器上。您可以使用同一台机器运行 Apache、PHP 和您的数据库，而不会产生真正的性能影响。

Mac OS X 用户很幸运，无需遵循本节。相反，请从 http://www.postgresql.org/download/macosx 下载向导驱动的安装程序，它几乎无需干预即可为您安装、配置并启动 PostgreSQL。

请确保从 www.postgresql.org 获取 PostgreSQL 的完整归档文件，并且下载的是源代码——而不是任何二进制文件。您将亲自编译它以获得最大速度和稳健性。下载的文件名看起来会像 postgresql-8.3.3.tar.gz 这样。要查找 URL，请访问 www.postgresql.org，单击 Downloads，并找到源代码的链接。

如果非要的话，可以使用 Lynx 或 FTP 下载文件，但作者更推荐使用 wget：

```
# wget ftp://ftp.postgresql.org/pub/latest/postgresql-8.3.3.tar.gz
```

下载完成后，以常规方式解压 PostgreSQL：

```
# tar -xzvf postgresql-8.3.3.tar.gz
```

这将创建一个名为 postgresql-8.3.3 的目录，其中包含 PostgreSQL 的源文件。进入该目录：

```
# cd postgresql-8.3.3
```

运行 configure 脚本以生成适合您特定 UNIX 环境的 Makefile：

```
# ./configure
```

运气好的话，您不会看到任何错误，并会看到一系列检查通过，最后一行读取如下或类似：

```
config.status: linking ./src/makefiles/Makefile.linux to src/Makefile.port
```

如果一切看起来都没问题，您可以通过键入以下内容来开始编译过程：

```
# make
```

PostgreSQL 编译可能需要相当长的时间，这时可以去喝杯咖啡。当您回来时，希望 PostgreSQL 已顺利编译完成，您可以按以下方式安装它：

```
# make install
```

严格来说，PostgreSQL 现在已安装，但仍需要进行一定量的配置。您必须创建守护进程将以其身份运行的用户帐户，为数据目录设置权限以便该用户拥有它，然后初始化数据目录。按照以下步骤设置数据库工作目录（所有数据都将存储在此）：

```
# adduser postgres
# mkdir /usr/local/pgsql/data
# chown postgres /usr/local/pgsql/data
# su - postgres
# /usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data
```

您现在几乎可以启动 PostgreSQL 守护进程（服务器）了。最后一步：您必须告诉 PostgreSQL 允许从哪里接受连接。通常，这将只是来自同一服务器，或者在不得已的情况下，来自同一网络上的其他机器。

假设您的服务器 IP 地址在此示例中为 192.168.1.1，并且您只希望允许来自该 IP 地址的访问。使用您喜欢的编辑器编辑文件 /usr/local/pgsql/data/pg_hba.conf，将此行添加到文件的最底部：

```
Host all all 192.168.1.1 255.255.255.255 trust
```

保存文件并退出编辑器。您现在可以使用以下语法启动 PostgreSQL：

```
# su - postgres
# /usr/local/pgsql/bin/postmaster -i -D /usr/local/pgsql/data &
```

第一行非常重要。postmaster 进程必须以新的 postgres 用户身份运行，而不是以 root 或您可能登录过的其他任何用户身份运行。启动时的 -i 指令也很重要，因为它告诉 PostgreSQL 允许 TCP/IP 连接——这是默认不允许的。

就这样。您可以再次以 postgres 用户身份按以下方式创建数据库：

```
# /usr/local/pgsql/bin/createdb databasename
```

现在您可以按以下方式使用 PostgreSQL 控制台操作它：

```
# /usr/local/pgsql/bin/psql databasename
```

最后，您可以按以下方式创建新用户：

```
# /usr/local/pgsql/bin/createuser username
```

这就结束了 PostgreSQL 安装的速成课程。根据您的操作系统和功能要求，此过程有许多变体。更高级的设置和所需库的更多细节在 PostgreSQL 文档中有所介绍。

## 安装各种支持库

在理想世界中，您现在可以继续安装 PHP 和 Apache。不幸的是，现实并非如此，您需要为 PHP 安装一些支持库。

PHP 6 大大减少了启动核心功能所需的外部库数量。主要的 GNU/Linux 发行版也在处理这些库的二进制分发方面变得好得多，而且，作者首次建议现在从二进制分发中安装所需的少数库。使用您喜欢的包管理器（例如 yum、apt-get 等）安装以下库：

- libicu
- libicu-devel

这两个库包含国际化组件的代码，这些组件提供了一些支持 PHP 6 新 Unicode 支持所需的软件基础设施。您需要的任何其他库（如果有的话）取决于您需要的确切功能。

安装 libicu 后，您就可以着手处理 PHP 和 Apache 本身了。

## 安装 PHP 和 Apache

PHP 和 Apache 必须同步安装，因此它们将在同一节中介绍。很快就会明白确切原因。

Mac OS X 用户再次可以在此步骤跳过，从 http://www.mamp.info/en/index.php 下载并安装 MAMP。它将使用简单的“向导”过程为您创建一个可用的 PHP 6 安装。完成后，您会发现可以在 http://localhost:8080 处找到 PHP 安装。

首先，从各自的网站下载 Apache 和 PHP 的最新版本——httpd.apache.org 和 www.php.net。

您将下载的两个文件名可能类似于 `httpd-2.2.9.tar.gz` 和 `php-6.0.0.tar.gz`。以常规方式解压缩它们。

```
# tar -xzvf httpd-2.2.9.tar.gz
# tar -xzvf php-6.0.0.tar.gz
```

第一步是对 Apache 进行初始配置。切换到 Apache 目录（可能是 `httpd-2.2.9`），使用默认参数运行 configure 脚本，然后编译并安装：

```
# ./configure
# make && make install
```

完成后，继续配置 PHP。切出 Apache 目录并进入 PHP 目录：

```
# cd ..
# cd php-6.0.0
```

与 PHP 早期版本的要求相比，您现在使用一个异常简单的 `configure` 语句来配置 PHP：

```
./configure --with-apxs2=/usr/local/apache/bin/apxs --with-pgsql --with-pdo-pgsql
```

请注意，如果您将 Apache 安装到不同的前缀，或使用了 `-enable-layout` 选项之一，则需要修改 `--with-apxs2` 指令以指向 `apxs` 可执行文件的安装位置。

配置可能需要几分钟，但假设您迄今为止都正确遵循了本附录，您不应该收到任何错误消息，一切都应该配置成功。

然后您可以构建 PHP：

```
# make
# make install
```

请注意，`make` 可能需要几分钟，具体取决于服务器的硬件和负载。`make install` 可能不会花太长时间。如果失败，您可能需要重新检查步骤。特别是，请确认上一节中提到的所有支持包都已正确配置。

PHP 编译和安装过程会在您的 Apache `modules` 目录中创建一个模块；现在您可以配置并安装 Apache 以使用该模块。您必须告诉 Apache 配置文件如何处理 `.php` 扩展名。修改文件 `/usr/local/apache/conf/httpd.conf`（同样，根据您的 configure 参数，此路径可能会有所不同，但这是默认值）并添加以下行：

```
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
```





这些行几乎可以添加到任何位置，但应将其放置在文件中所有其他 AddType 和 AddHandler 指令附近，以保持整洁。请注意，PHP 应该已经编辑了此文件以添加以下行：

```
LoadModule php6_module lib/apache/libphp6.so
```

确认上述行已存在于您的 httpd.conf 文件中。如果没有，请添加它。

## 测试您的安装

还剩下的就是测试您的安装。使用以下语法启动 Apache：

```
# /usr/local/apache/bin/apachectl start
```

现在在 /usr/local/apache/htdocs 中创建一个名为 test.php 的文件，包含以下代码：

```php
<?php
phpinfo();
?>
```

保存它，然后在工作站的 Web 浏览器中，将其指向您 UNIX 机器的 IP 地址，后跟 /phpinfo.php。例如，如果您的服务器是 192.168.1.1，请将其指向 http://192.168.1.1/phpinfo.php。您应该会看到显示 PHP 安装完整详细信息的屏幕。

如果是，恭喜。您的 PHP 安装已成功！不过，您可能希望为正在处理的每个项目创建虚拟服务器条目。有关此内容的更多信息可以在第 21 章中找到。

## 何时需要 Windows

确实会出现必须使用 Windows 的场景。最典型的例子是将封闭系统安装到已基于 Windows 的大型公司 IT 基础架构中，而管理层坚决拒绝安装 UNIX 服务器。

经过一些调整，本书中的示例仍然可以正常工作。以下指南可能会帮助您将 PHP 从 UNIX 迁移到 Windows。

## 更改路径

请记住，Windows 上的路径与 UNIX 上的路径看起来非常不同。磁盘上的诸如 /data/res/1230.jpg 之类的路径引用需要更改为 Windows 等效路径，例如 C:\data\res\1230.jpg。

PHP 很友好，允许您保留正斜杠（/）。如果通过使用相对路径避免驱动器号，您可能能够使应用程序更具可移植性。

## 外部库

因为 Windows 不像 UNIX 一样自带内置且广泛的 C/C++ 编译器，所以 PHP 在 Windows 下运行不需要大量外部库。相反，PHP 随其 Windows 安装包提供了大量针对本附录讨论的各种扩展的预编译 DLL。请注意，这些 DLL 仅随 Windows 二进制文件的 ZIP 分发版提供。您不应使用 .msi 安装程序在 Windows 上安装 PHP。

要启用此类扩展，请确保 PHP 扩展目录在系统 PATH 中（例如 C:\php\ext），确保 php.ini 中的 extension_dir 指令设置正确（默认情况下未设置为 Windows 安装的有用值），并重新启动 Web 服务器。您会发现相关功能立即可供 PHP 使用。

## 使用 PEAR

在 Windows 上使用 PEAR 仓库安装库包的方式与在 UNIX 上略有不同。在使用 PEAR 之前，必须使用以下随附脚本对其进行设置：

```
C:\php\PEAR>..\php go-pear.php
Welcome to go-pear!
Go-pear will install the 'pear' command and all the files needed by
it. This command is your tool for PEAR installation and maintenance.
```

该脚本会询问您有关代理服务器等的各种问题，但会创建一个作为批处理文件的单一 pear 命令，您可以以与其 UNIX 版本完全相同的方式使用它。

## 总结

在本附录中，您了解了本书在示例中选择 UNIX、Apache 和 PostgreSQL 的关键原因，以及您可能希望在自己的 PHP 企业开发中考虑采用同样做法的原因。

接着，您了解了在 UNIX 平台上从头到尾设置可运行的 Apache、PHP 和 PostgreSQL 实际安装所涉及的基本步骤。

最后，您了解了 Windows 上的 PHP 与 UNIX 上的 PHP 之间的一些关键差异，以及如何在自己的开发中有效地绕过这些差异。

### A

- _a 标志，rsync，564
- 抽象类图，观察者模式，84-86
- 抽象类
  - 设计小部件以从中继承，88
  - 指示从中继承，38
  - 与接口相比，77
  - 在 PHP 6 中，29
  - 在类图中何时使用，77
- 抽象方法
  - DataBoundObject 类，181
  - 在父类中定义以在子类中实现，174, 181
  - 实现所有接口，26
  - 在子类中实现，26
- AbstractInstrument 类，77-81
- PHP 专业人员的学术技能，630
- 访问器方法
  - DataBoundObject 类，183
  - 概述，10-11
  - 业务对象原型设计，160
- 客户经理，选择，411
- 激活，UML 序列图，45
- 活动图，UML，42-44, 190
- 参与者，用例图，33-35
- AddConstraint() 方法，329
- _addFunction 方法，SoapServer，229
- addItem() 方法，Collection 类，105-107, 109
- addObserver() 方法，Observable 接口，86, 87-88
- addRecord() 方法，Observable 接口，88
- 管理员
  - CMS 构建，588-589
  - 以管理员身份登录 Mantis，547-548
- 高级 PHP 调试器 (APD)，664
- 議程，识别项目，395
- 聚合，UML 类图，39
- 敏捷开发方法论，426
- 敏捷建模：极限编程和统一流程的有效实践 (Ambler 和 Jeffries)，630
- 算法
  - 性能瓶颈，664
  - 性能问题，662
- 替代 PHP 缓存 (APC)，662
- 和符号 (&)，81
- 在 Mantis 中标注缺陷，553
- Apache Web 服务器
  - 用于 PHP 安装的选择，674
  - 在实时暂存环境中的配置，557-558
  - 在工作室暂存环境中的配置，557
  - 处理 PHP 高流量/高可用性，598-599
  - 安装 PHP 和，677-679
  - 测试安装，679
  - Ulysses 仅与其兼容，362
- APC (替代 PHP 缓存)，662
- APD (高级 PHP 调试器)，664
- 应用程序日志，209
- 应用程序架构
  - MVC. 参见 MVC (模型-视图-控制器) 设计模式
  - 概述，305-306
  - 真正的模板化，333-342
  - 单元测试。参见单元测试
- 应用程序框架
  - 应用程序结构，356
  - 数据库抽象，359
  - 部署注意事项，379-380
  - 开发环境。参见开发环境
  - 示例应用程序。参见 Ulysses
  - 表单持久化，358
  - 对象关系映射，358-359
  - 概述，355-356
  - Prado，377-378
  - 代码与显示逻辑分离，356-357
  - 总结，380
  - URL 重写，357
  - 用例场景，359-361
  - 实用程序类，359
  - 验证，357
  - Zend Framework，378-379
- 应用程序服务器，599, 616
- 应用程序结构
  - 框架提供，356
  - Ulysses 框架，376
- 架构，高性能，667
- 归档模式，rsync，564
- $arRelationMap 成员变量，170
- 箭头，Zend Studio 调试窗口，651
- 基于 ASP 的网站，Web 服务器用于，673
- 资产服务器
  - 硬件负载平衡和，604
  - 改善基础架构性能，615
- 关联，类图，37-38
- 关联数组 (哈希)，Smarty，337
- 属性类型，类图，36
- 身份验证
  - HTTP，277
  - 会话和。参见会话和身份验证
  - 作为 SMS 代码发送，250
- 作者，CMS 构建，588
- 自动化版本控制，存储库提取。另参见版本控制
  - 概述，562
  - 使用 CVS，562-563
  - 使用 Subversion，563
- 可用性，在 PHP 中。参见高流量/高可用性

### B

- 备份要求，434
- 带宽
  - 计算 CIR，437
  - 计算月传输量，438
  - 高，595
- Base64 编码，531-533
- BaseCamp，428
- 基本身份验证，实时暂存，558
- beginTransaction() 方法，PDO，142-143
- 双向可导航性，37
- 二进制文件，版本控制和，646
- bindColumn() 方法，PDOStatement，147
- 绑定元素，WSDL，236
- bindParam() 方法，PDO，140-141
- bindValue() 方法，PDO，141
- 位逻辑，MVC 小型工具包常量，312-314
- 黑盒
  - 为您的类创建测试套件，345
  - 使用进行单元测试，540
- 空 servlet，366
- 流血服务器，424
- 密件收件人，260, 262
- 书签，280
- 布尔标志，170
- 瓶颈，性能
  - 导致的方法，666-667
  - 追踪，663-664
  - 类型，659-661
- 分支，版本控制技术，645
- 断点，Zend 调试，653
- 简报，正式项目
  - 预算，401-403
  - 业务需求，398-399
  - 商业条款，403-404
  - 未来计划，404
  - 外观和感觉，404-405
  - 概述，397-398
  - 范围，399-400
  - 总结，405-406
  - 支持，405
  - 技术，405
  - 时间表，400-401
  - 何时拒绝，408-409
- 广播电子邮件提供商，274
- 预算
  - 业务需求，434
  - 接收正式简报，401-403
- 缺陷，在 Mantis 中，550-554
- 构建过程，424
- 生成器模式
  - 注意事项，100
  - Director，99-100
  - 实现，97-99
  - 概述，96-97
- 构建应用程序
  - 清理，475-482
  - 已最终确定的差旅费用报告，514-529
  - 完成迭代，483-492
  - 模拟对象，529-533





### 启动项目
- 参见 启动项目，构建应用程序

### 开始工作
- 参见 开始工作，构建应用程序

### 总结
- 533

### 差旅费报告
- 492–514

### 批量电子邮件
- 274

### 业务分析，对象建模
- 344

### 业务对象
- 添加数据绑定，160–162
- 构建可工作版本，166–168
- 设计，157
- 延迟实例化，173
- 局限性，172
- 满足需求，166–169
- 概述，156–157
- 属性监视，173
- 原型设计，158–160
- 关系映射，162
- 可重用性，173
- 在 Ulysses 中，363–365
- 理解，169–171
- 与实用工具类相比，343

### 业务需求
- OOP 的优点，4
- 确定，433–434
- 正式简报，398–399

## C

### 缓存
- 高性能，667–668
- 为最大化基础设施能力，613–614

### _call 方法，SoapClient
- 228

### call_user_func()，回调
- 111–115

### 回调
- 实现，113–115
- 概述，110–111
- 使用 call_user_func，111–113

### 捕获输出，Smarty
- 342

### 抄送 (Cc:) 收件人，电子邮件
- 260–262, 267

### 职业生涯
- 作为 PHP 专业人员。参见 PHP 专业人员职业生涯中
- 作为专业软件开发人员，628–631

### 中立运营商数据中心
- 436–437

### 特定运营商数据中心
- 436–437

### 用例图
- 76

### 大小写敏感
- PHP 变量和成员名称，162
- 模板，367

### 案例研究
- 构建应用程序。参见 构建应用程序部署。参见 部署
- 项目管理。参见 项目管理
- 项目概述。参见 项目概述
- 项目规划。参见 项目规划
- 系统架构。参见 系统架构

### 类别
- 内容管理，572
- 章节 vs.，578–579

### 类别，项目错误
- 550–554

### Cc: (抄送) 收件人，电子邮件
- 260–262, 267

### CDNs (内容分发网络)
- 615

### 蜂窝电话
- 参见 SMS (短消息服务) 文本消息

### CGI 二进制文件，以 PHP 安装
- 673–674

### 变更管理
- 428–429

### CIR (承诺信息率)
- 带宽和，596
- 计算，437

### 类图，UML
- 生成器模式，97
- 组合模式，76, 82
- 装饰器模式，90
- 设计事件驱动解决方案，191
- 实现，39–42
- 领域建模，35–37
- 观察者模式，83
- 关系，37–39
- 使用 Collection 类，119–120

### 类层次结构，通信
- Communication 类，255–259
- EmailRecipient 类，253–255
- 概述，251
- Recipient 类，252–253

### class 关键字
- 7

### 类型提示
- 86

### class.Dispatcher.php
- 192–193

### 类
- 向...添加方法，6
- 向...添加属性，8–10
- OOP 的优点，4
- 使用...构建对象，6–7
- 联系人管理器应用程序，50–51
- 创建，7–8
- (续)
- 定义，5
- MVC 设计模式模型，306–307
- Web 应用程序中的 MVC，308
- MVC 迷你工具包，为...定义常量，312–314
- 概述，6
- PHP 缺少预定义的，132–133
- 类型，155–157
- 单元测试，344–346
- class.Event_Handler.php，194
- class.Handler_Edit.php，195
- class.Handler_View.php，194–195

### 清理应用程序
- 代码债务，475–476
- 重构代码，476–482

### 客户
- 客户报告的错误，429–430
- 因理解差异产生的争议，429
- 从...收集需求，32
- ...在项目团队中的角色，414
- 签字后的规格变更，429

### 选择客户端开发人员
- 412

### close() 函数
- 291

### 集群
- 600, 610–611

### CMS (内容管理系统)
- 定义，571–573
- Drupal，575–577
- ExpressionEngine，580–583
- Frog CMS，583–585
- 历史，573–575
- Joomla!，578–580
- 概述，575

### CMS (内容管理系统)，自行构建
- 管理员和权限，588–589
- 内容相关问题，586–587
- 概述，585
- 模板，590–591
- 工作流，589–590

### CNET，历史
- 574

### 代码
- 折叠，655
- 债务，475
- 极限编程，427
- 修复...中的瓶颈，665–666
- 分离显示逻辑和...的框架，356–357
- 重用，4, 16, 173
- Ulysses 框架，376
- 单元测试发现...中的错误，540

### 代码完成，Zend
- 649

### 代码重复，ORM 局限性
- 172

### 代码编辑器
- CMS，588
- Komodo，655–656
- Zend IDE，649–650

### 代码折叠，Komodo
- 655

### 折叠的代码
- 655

### Collection 类
- 参见 集合

### 集合
- Collection 类基础，106–109
- Collection 类设计，105
- Collection 类改进，125–126
- Collection 类用途，103–104
- 实现延迟实例化。参见 延迟实例化
- 使用...存储收件人，256–257
- 摘要，126
- 使用 Collection 类，108–109, 119–125

### 共置服务器，托管 PHP 应用程序
- 595

### 注释，版本控制
- 646

### 商业条款，接收...的简报
- 403–404

### commit() 方法，PDO
- 142–143

### 提交，PDO
- 142–143

### 承诺信息率 (CIR)
- 带宽和，596
- 计算，437

### 通用硬件，托管
- 597

### Communication 类
- EmailCommunication 类，259
- 传递电子邮件消息，267
- 概述，255–256, 257–259
- SMS 文本消息，270
- 使用集合存储收件人，256–257
- TemplatedEmailCommunication 类，268–270

### 社区技能，PHP 专业人员
- 630–631

### 组件类，组合模式
- 77

### 组件图，UML
- 47–48

### 组件故障
- 602

### 组件，螺旋模型
- 417–418

### 组合对象，组合模式
- 77

### 组合模式
- 注意事项，82–83
- 实现，78–82
- 概述，76–77

### 组合，UML 类图
- 38–39, 53–55

### 具体构造函数，LoggerBackend 类
- 213

### 并发版本控制
- 选择，640–641
- 冲突，638–640
- 示例，636–638
- 独占 vs.，636

### 并发版本控制系统 (CVS)
- 版本控制软件，644
- Zend 与...的集成，654

### 条件语句，Smarty
- 337–338

### 连接字符串
- 解析，210
- 重新设计 Logger 类以使用，210–213

### 连接性
- PHP 数据库，128–129
- 物理环境和，436–439
- 系统架构，432
- 测试 PDO，136
- 使用持久连接，147–148

### 控制台窗格，Zend
- 653

### 常量
- MVC 迷你工具包，312–314
- PDO，143

### Constraint 类
- 323–324

### ConstraintFailure 类
- 323–324

### _construct() 函数
- 11–12, 29

### 构造函数
- 创建联系人管理器，57
- DataBoundObject 类，181–182
- 向用户发送电子邮件，261–262
- HTTPSession 类，301
- 实现业务对象，170–171
- 使用...继承，19–20
- 使用...实例化对象，11–12

### 联系人管理器，创建
- 联系人类型类，58–62
- DataManager 类，62–63
- 描述，49–50
- Entity、Individual 和 Organization 类，64–71
- PropertyObject 类，56–58
- UML 图，50–56

### 内容
- 在内容管理中，572
- 利用内容最大化基础设施能力，614–615
- 类型，586–587

### 内容分发网络 (CDN)
- 615

### 内容管理
- 参见 CMS (内容管理系统)

### 贡献者，CMS 构建
- 588

### 控制器，MVC 设计模式
- 文件命名约定，310
- 引入，306
- 概述，307–308
- search.php，MVC 迷你工具包，324–326
- searchresults.php，MVC 迷你工具包，327–329
- Web 应用程序，308

### 控件
- 在 Ulysses 页面中添加，367–371
- Prado 框架，378

### Cookie
- 定义，280
- 发现有效会话，283–284
- 使用...持续会话，280–281
- 使用补充键，283

### CREATE DATABASE 消息
- 128–129

### 创建新项目，Mantis
- 550

### 创意规格设计计划
- 422

### 跨平台支持，PHP
- 622–623

### CRUD 缩写，业务对象
- 161–162, 166–168

### 客户联系报告应用程序
- 清理应用程序，475–483
- 完成迭代，483–492
- 发布规划，450–451
- 启动项目。参见 启动项目，构建应用程序
- 开始工作。参见 开始工作，构建应用程序

### CVS (并发版本控制系统)
- 版本控制软件，644
- 使用...进行版本控制，562–563
- Zend 与...的集成，654

## D

### 数据绑定，业务对象
- 160–162

### 数据中心
- 436

### 数据源，PDO 的局限性
- 151

### 数据库
- 为 PHP 安装选择类型，674–675
- 集群和复制，610–611
- 将 PHP 会话管理连接到，290–292
- 连接性，128–132
- 为数据绑定创建，160–161
- 数据库支持，128
- 开发，559–560
- 修复...中的瓶颈，664–665




### 数据库（续）
- Flickr 配置，616
- 特定于数据库的函数，147
- 高性能架构提示，668
- ORM 的局限性，172
- 记录到表中，215–219
- 维护用于保存电子邮件的作业队列，271–272
- PDO 特定函数，147
- 查询中的性能瓶颈，663–664
- 用于 PHP 应用程序平台，599–600
- PostgreSQL，128–129
- 与 PHP 相关的问题，132–133
- 服务器，434
- 会话性能，303
- 使用包装器类，133–134

### 数据库抽象
- 数据库抽象的框架，359
- 概述，134–136
- 在 Ulysses 框架中，377
- 使用 ORM 进行此操作。另见 ORM（对象关系映射）

### 数据源名称 (DSN)，137, 148

### DataBoundObject 类
- 优点，184–185
- 代码，175–178
- 设计，174
- 示例实现，178–180
- DataBoundObject 类的框架，358
- 概述，173
- 了解其工作原理，180–184

### DataManager 类
- 创建联系人管理器，62–63
- 在类图中指示，UML，52–55
- 更新 UML 图，64

### DataSource 对象
- 装饰器模式，92
- 观察者模式，87–89

### date_default_timezone_set() 函数，Logger 类，207

### daycalc() 函数，524–526

### db_changes 文件夹，560

### db_connect() 函数，194

### DEBUG 函数，220–221

### Debug Output 窗格，Zend，653

### Debug 窗口，Zend，651

### Debugger 类，219–222

### 调试
- 另见 日志记录；测试
- 为调试创建机制，219–222
- 使用 Komodo，656
- MVC 设计模式与调试，306
- 测试阶段计划，424–425
- 使用 ZDE，651–654

### debugPrint() 函数，220–222

### 决策点，UML 活动图，44

### Decorator 类，90, 93–95

### 装饰器模式
- 注意事项，94–95
- 实现，92
- 概述，89–91
- 使用，93–94

### 专用数据中心，436

### 专用负载平衡，435–436

### definitions 元素，WSDL，233–234

### 交付时间，660

### 依赖关系，UML 组件/部署图，48

### 部署
- 应用程序框架，379–380
- 设计开发环境，555–560
- 概述，555
- 源代码工作流。另见 源代码工作流，部署
- 总结，567

### 部署图，UML，47–48

### 设计
- 案例研究开发方法，388
- 极限编程，426
- 实现业务对象，157

### 设计模式
- 生成器模式，96–100
- 组合模式，76–83
- 装饰器模式，89–95
- 外观模式，95–96
- MVC。另见 MVC（模型-视图-控制器）设计模式
- 观察者模式，83–89
- 概述，75
- 反应器模式，199
- 总结，100–101

### 《设计模式：可复用面向对象软件的基础》（Gamma, Helm, Johnson 和 Vlissides），630

### 设计过程，422–423

### destroy() 函数，291

### 销毁对象，12–15

### _destruct() 函数，12, 14, 29

### 析构函数，业务对象，171–172

### 开发者，职业生涯。另见 专业软件开发人员

### 开发数据库，559–560

### 开发环境
- 开发数据库，559–560
- 实时生产环境，559
- 实时暂存环境，557–558
- 概述，555
- PHP 中的简单性，619–620
- 工作室开发环境，556
- 工作室暂存环境，557

### 开发服务器，版本控制，642

### 字典攻击，282

### 数字签名，273

### Director 类，97–98

### 磁盘容错，使用缓解措施，606–607

### Dispatcher 类
- class.Dispatcher.php，193
- 设计事件驱动解决方案，189–191
- 事件驱动编程注意事项，198–199

### 显示逻辑
- 分离代码和显示逻辑的框架，356–357
- Ulysses 框架，376

### $displayHash，325, 326, 329

### displaySmartyPage() 函数，481–482

### DKIM（域密钥识别邮件），273–274

### DLLs，680

### DNS 负载平衡，435, 603–604

### 领域专家，项目管理，395–396

### 域密钥识别邮件 (DKIM)，273–274

### 域，157
- 定义，32
- 在类图中建模，35–37

### draw() 方法，装饰器模式，89–90, 91–92

### 下拉列表，强制使用提交，483

### Drupal
- 使用 Drupal 创建内容，576
- 使用 Drupal 管理内容，577
- 示例布局，575

### DSN（数据源名称），137, 148

### 双以太网分段，609

### 停留时间，计算 CIR，437

## E

### -e ssh 指令，rsync，565

### eCircle，274

### 编辑代码
- Komodo，655–656
- Zend IDE，649–650

### 省略号 (...)，37

### 电子邮件
- 广播提供商，274
- 通过电子邮件通知，248–249
- 收件人，251
- 蠕虫，284

### EmailCommunication 类
- 构建测试版本，259–263
- 传递消息，263–268
- 概述，259
- 使用 MIME，270
- 使用模板，268–270

### 向用户发送电子邮件
- 阻止活动，271–272
- 构建测试版本，259–263
- 可送达性，272–274
- 传递消息，263–268
- 概述，259
- 使用模板，268–270
- 使用 MIME，270

### EmailRecipient 类，253–255

### EmailRecipientCommunication 类，259

### 封装
- PHP6 中的更改，29
- 定义，6
- 概述，27–28

### Entity 类
- 创建联系人管理器，52–55, 59
- 开发，65–71

### 环境，开发。另见 开发环境

### errorCode() 方法，PDO，143–145

### 错误，处理 PDO，143–145

### 错误日志，209

### 转义，141

### 以太网段，608–610

### 事件驱动编程
- 设计，189–191
- 实现，192–195
- 概述，187
- 暂停思考，198–199
- 安全性，196–198
- 总结，199
- 了解事件，187–188

### 事件，187–188

### 异常处理，SOAP 客户端，239–240

### 特殊通知，248

### 独占版本控制，636, 640–641

### exists() 方法，108

### 期望，在推销期间设定，409

### 过期时间，会话，285

### 指数序列，312

### ExpressionEngine
- 在 ExpressionEngine 中添加内容，581–582
- 模板函数，582–583
- 网站功能，580–581

### extends 关键字，继承，16, 17

### 扩展，PHP 作为，128

### 扩展目录，680

### 外部网络，PHP，595–596

### 外部数据源，性能调优，666

### 极限编程。另见 XP（极限编程）

### 《极限编程：拥抱变化，第2版》（Addison-Wesley, 2004），387, 426

## F

### 外观模式，95–96

### Facebook，延迟和，596

### 虚假开端，项目历史，396

### 故障跟踪，QA，543–544

### faultcode 属性，SoapFault 客户端，239–240

### faultstring 属性，SoapFault 客户端，239–240

### 传真
- 电子邮件到传真网关，271
- 收件人，251

### fclose() 方法，Logger 类，202

### 功能蔓延，399

### 功能集，与 PDO，150–151

### fetch() 方法，PDOStatement 类，139

### fetchall() 方法，PDOStatement 类，139

### 文件日志记录
- 示例文件系统布局，202–203
- 简单，201–202
- 使用 Logger 类，203–208

### 文件传输协议 (FTP)，警告，567

### 文件，在 MVC 中拆分，309

### 完成迭代，构建应用程序，483–492

### 防火墙，硬件要求，436

### Flickr，616

### fopen() 方法，Logger 类，202

### 分支，UML 活动图，44

### 表单持久性，框架，358, 376

### 框架可用性，单元测试，351

### 框架。另见 应用程序框架

### Frog CMS
- 内容管理简化，583
- 管理页面，584
- 代码片段，584–585

### 前端控制器，Zend 框架，379

### FTP（文件传输协议），警告，567

### 功能合规性质量，538, 541–542

### 功能规格说明，420–421

### 功能测试表，541

### 功能测试
- 注意事项，542
- 功能测试表，541–542
- 概述，541
- 计划，424
- 单元测试减轻其负担，352
- 与可用性测试相比，543

### 未来计划，正式简报，404

### fwrite() 方法，Logger 类，202

## G

### 甘特图，409

### gc() 函数，292

### Gd（图形库），666

### 泛化，UML 类图，38, 52–54

### generateSqlDelete() 函数，487

### generateSqlUpdate() 函数，487

### 地理负载平衡，605–606, 617

### GET 请求，HTTP
- 工作原理，276–278
- 性能瓶颈，659–661
- 作为无状态，275
- Ulysses 框架，366

### GetAccessor() 方法，160, 183

### getConnection() 函数，62–63

### getDescription() 方法，81–82

### _getFunctions() 方法，SoapClient，228, 229, 230

### getInstance() 方法，Logger 类，205–206, 210–213

### getItem() 方法，Collection 类，105–109

### _getLastRequest() 方法，SoapClient，228

### _getLastResponse() 方法，SoapClient，228

### getSessionIdentifier() 方法，HTTPSession 类，302

### getSqlWhere() 方法，487–489

### getStartDateOffset() 方法，473

### getStringRepresentation() 方法，252, 254–255

### _getTypes() 方法，SoapClient，228




getUserID() 函数，HTTPSession 类，302
getUserObject() 函数，HTTPSession 类，302
GNU/Linux，672，675
良好会话实践，199
故障期间的优雅处理，QA，538
优雅降级，143
图形库 (Gd)，666

## H

- 黑客，281–285
- __handle 方法，SoapServer，229
- handle_the_event() 函数，193–194
- handled_event() 方法
  - class.Dispatcher.php，193
  - class.Event_Handler.php，194
  - class.Handler_Edit.php，195
  - class.Handler_View.php，194–195
  - interface.Handlered.php，193
- 处理程序
  - class.Dispatcher.php，193
  - class.Event_Handler.php，194
  - class.Handler_Edit.php，195
  - class.Handler_View.php，194–195
  - 设计事件驱动解决方案，189–191
  - 事件驱动编程注意事项，198–199
  - interface.Handlered.php，193
- 交接，定义，596–597
- 交接过程，425

- 硬件
  - 确定需求，434–436
  - 高性能提示，667
  - 作为缓解技术的负载均衡，604–605
  - 性能问题，662–663
  - 用于 PHP 应用平台，597
- 哈希，Smarty，337
- 心跳链接，604
- 高带宽，595
- 高流量/高可用性
  - Flickr，616
  - 高可用性，594
  - 高流量，594–595
  - 影响因素。参见 影响因素
  - 缓解技术。参见 缓解技术
  - 概述，593，615
  - 平台。参见 平台
  - 现实世界示例，615–618
  - 总结，618
  - 理解术语，593–595
  - Wikipedia，616–618
- 高质量产品，QA，536
- 项目历史，396–397
- 托管
  - 业务需求，433
  - 系统架构，432
- HOSTS 文件，283–284
- HTML，search.phtml，326–327
- HTTP 延迟，601

- HTTP 请求
  - 阻塞活动，271
  - 工作原理，276–278
  - 概述，275
  - 会话与，277–278
- HTTPSession 类
  - 数据库架构，292–293
  - 工作原理，300–302
  - HTTPSession.php 代码，293–297
  - 概述，292
  - 性能注意事项，302–303
  - 总结，304
  - 测试，297–300
  - HTTPSession.php 代码，297–300

## I

- $ID 成员变量，170
- IDE（集成开发环境）
  - 选择，647–648
  - Komodo，654–657
  - 其他类型的编辑器及，657
  - 总结，658
  - Zend Studio，648–654
- IIS（互联网信息服务），在 Windows 上使用它进行托管，673
- 影响因素，601–602
- impress() 函数，HTTPSession 类，301–302
- 包含，用例图，34–35
- index.php，478
- Individual 类，51–53，68–71
- 信息架构师，选择，412
- 信息架构设计计划，422–423
- 基础设施，业务需求，433

- 继承
  - 类图，38，52–55
  - 定义，5
  - 重写方法，20–23
  - 概述，15–20
  - 保留父类功能，23–24
  - 理解，24–25
- 对象的初始化，11–12
- 内联方法，重构，482
- 内连接，数据库阻塞，665
- 输入、处理和输出 (IPO) 模型，308
- INSERT 语句，数据库连接，131
- 安装，Mantis，545–547
- 安装，PHP
  - 选择数据库，674–675
  - 选择 Web 服务器，673–674
  - 下载和安装 PostgreSQL，675–677
  - 安装 PHP 和 Apache，677–679
  - 安装支持库，677
  - 步骤，671–672
  - 总结，680
  - 测试安装，679
  - 在 UNIX 服务器上，672–673
  - 当需要 Windows 时，679–680
- 安装，PHPUnit，347
- 安装，Smarty，334–335
- 实例化
  - 延迟。参见 延迟实例化
  - 对象，6–7
  - 单例，149
- Instrument 接口
  - 实现，39–41
  - 表示关联，37–38
  - 表示组合，38–39
  - 使用组合模式。参见 组合模式
- 集成开发环境。参见 IDE
- （集成开发环境）
- interface.Handled.php，193
- 接口
  - 类图表示的，38，77
  - 组件/部署图表示的，48
  - 创建 Recipient 接口，252–253
  - 定义，6
  - 设计事件驱动解决方案，191
  - 为类设计，344–345
  - 实现事件驱动解决方案，193
  - 概述，25–27
- 内部网络，应用平台，596–597
- InterLeaf，573
- 内部成员变量
  - 定义，10
  - 封装与，28
  - 概述，25–27
- 互联网信息服务 (IIS)，在 Windows 上使用它进行托管，673
- 客户访谈，需求收集，32
- 简介，演示文稿，409
- 投资摘要，演示文稿，409
- IP 地址，良好会话实践，286
- IPO（输入、处理和输出）模型，308
- is_callable() 函数，115
- isEmpty() 函数，496
- isLoggedIn() 函数，302
- isset() 方法，172
- isValid() 方法，252，255
- 迭代
  - 构建。参见 构建应用程序
  - 发布计划，450–451

## J

- Java，支持，624
- 连接
  - 外连接，和数据库阻塞，665
  - UML 活动图，44
- Joomla!
  - 控制面板，580
  - 使用...创建内容，579
  - 基于 Joomla! 的网站，578
- 文件日志记录，635–636
- 垃圾邮件
  - 广播电子邮件提供商和，274
  - 域密钥标识邮件和，273–274
  - 限制...的可送达性，271–272
  - 发件人 ID 和，273
  - SPF 记录和，273

## K

- KeyInUseException 类，107–109
- keys() 函数，108
- Komodo
  - 编辑代码，655–656
  - 管理项目，654–655
  - 概述，654

## L

- 语言，PHP 中的弱类型，621
- 大对象，PDO，146–147
- lastInsertID() 方法，业务对象，171
- 延迟（ping 时间），带宽和，596
- 延迟实例化
  - 回调，110–115
  - 定义，104
  - 实现，109–110
  - 实现业务对象，173
  - Collection 类的 setLoadCallback 方法，115–119
- 首席架构师
  - 选择，411–412
  - 管理构建过程，424
  - 制定十点计划，423
- libicu，支持库，677
- libicu-devel，支持库，677
- 库
  - 外部，PHP 在 Windows 中不需要，680
  - 在 PHP 6 中实现 SOAP，227
  - 安装支持，677
- 生命线，UML 序列图，45
- lighttpd Web 服务器，599
- 线性数组，Smarty，336
- 语言简洁性，PHP，621–622
- 链路聚合（NIC 团队），606
- Linux 虚拟服务器 (LVS)，617
- 监听器接口，观察者模式，83–86，88–89
- 实时生产环境，559
- 实时预发布环境，557–558
- Load() 方法，DataBoundObject 类，181–182
- 负载均衡器，604
- 负载均衡
  - 专用，435–436
  - 基于 DNS，435，603–604
  - 硬件，604–605
  - 概述，603
  - 基于软件，435
- 负载测试
  - 使用...的高性能架构，668–669
  - 用于质量保证，542
  - 测试阶段计划，424–425
- 负载容忍度，QA，539
- LoadRunner，425
- LOB（大对象），146–147
- logging_sun_0，500–501
- 注销，478–479
- Logger 类
  - 扩展，208–209
  - LoggerBackend 类，213
  - 记录到数据库表，215–219
  - 概述，203–208
  - 解析连接字符串，210
  - 重新设计以使用连接字符串，210–213
  - 子类化 LoggerBackend 类，213–215
- LoggerBackend 类
  - 记录到数据库表，215–219
  - 概述，213
  - 重新设计以使用连接字符串，212–213
  - 子类化，213–215
- 日志记录。另请参阅 调试
  - 记录到数据库表，215–219
  - 示例文件系统布局，202–203
  - Logger 类，203–208
  - LoggerBackend 类，213
  - 概述，208–209
  - 解析连接字符串，210
  - 重新设计 Logger 类以使用连接字符串，210–213
  - 简单文件，201–202
  - 子类化 LoggerBackend 类，213–215
- 登录
  - 清理应用程序，477–479
  - 配置 Mantis，547–548
  - 创建屏幕，460–464
  - PHP 中的数据库连接，130
  - 良好会话实践，286
  - 在可用性测试中，543
- logMessage() 方法
  - Logger 类，202–203，206–208
  - LoggerBackend 类，213
- 外观和感觉，正式简介，404–405
- LVS（Linux 虚拟服务器），617

## M

- mail() 函数，250
- 维护管理，433，439
- manageBackends() 函数，Logger 类，213
- 托管服务器，托管 PHP 应用程序，595
- 项目管理。参见 项目管理
- Mantis，544–554
  - 标注缺陷，553
  - 分配缺陷，553
  - 创建和编辑用户，548–549
  - 创建新项目，550
  - 充分利用，553–554
  - 以管理员身份登录，547–548
  - 概述，544–547
  - 报告缺陷，552–553





### Mantis（续）
- 解决错误，553–554
- 设置项目错误类别，550–552
- MarkForDeletion() 方法，业务对象，171
- MDOB，PEAR 仓库，133–134
- MediaWiki，617
### 成员变量
- 实现业务对象，170
- 内部，10
- 保护访问权限，10–11
- Request 类，312–314
### memcached 服务器，303, 617–618
### 内存
- 性能调优与，666
- 会话性能与，303
### 消息元素，WSDL，235–236
### 消息，电子邮件，250, 263–268
### 方法
- 访问器。另见 访问器方法
- 添加，8
- 添加到类，6
- Collection 类，106–108
- 重写，20–23
- 请求对象，320–322
### Microsoft Project，428
### Microsoft Visual SourceSafe，643–644
### Microsoft Windows
- 操作系统，598
- 将 PHP 从 UNIX 迁移到，679–680
- 使用 UNIX Web 服务器与之对比，672–673
### 里程碑，建立，400–401
### MIME，用于 HTML 电子邮件，270
### 缓解技术
- 资产服务器，615
- 缓存，613–614
- 内容分发网络，615
- 内容生成，614–615
- 数据库集群与复制，610–611
- 磁盘容错，606–607
- 地理负载平衡，605–606
- 负载平衡，603–605
- 多段拓扑，608–610
- NIC 聚合，606
- 概述，603
- 电源冗余，607–608
- 流量计算，611–613
### 模拟对象，构建应用程序，529–533
### mod_rewrite 支持，Apache，362
### 模型，MVC 设计模式，306–308, 310
### 建模领域，软件设计，35–37
### 模型-视图-控制器。另见 MVC（模型-视图-控制器）设计模式
### 模块化，OOP，4–5
### 每月传输量，计算，438
### MS SQL Server，128
### 多维数组，Smarty，340–341
### 多段拓扑，以太网，608–610
### 多任务，幻觉，601–602
### MVC（模型-视图-控制器）设计模式
- 控制器，307–308
- 模型，306–307
- 概述，306
- 在 PHP 中，309–311
- 视图，307
- 在 Web 应用程序中，308
- Zend Framework 作为传统模式，378–379
### MVC（模型-视图-控制器）设计模式，迷你工具包
- 常量，312–314
- Constraint 类，322–324
- 概述，311–312
- PRG，331–332
- Request 类，314–322
- search.php，324–326
- search.phtml，326–327
- searchresults.php，327–329
- searchresults.phtml，330
- 尝试，330–331
### MyProject 窗口，Zend，649
### MySQL
- 调用存储过程，148
- 数据库集群与复制，611
- Flickr 的使用，616
- php.net 参考站点，128

## N
### 命名约定
- Cookie，281
- 数据库字段，57
- 确定单元格的唯一值，500–501
- MVC 设计模式的文件，309–310
- PHP 变量和成员名称，162
### 原生模板
- 概述，310
- 陷阱，333–334
- 回顾，333
- 真正的模板与，334
- 何时使用 Smarty 与，342
### 可导航性，关联线和，37–38
### Net_SMTP 包，263–268
### 网络
- 高流量/高可用性与，602
- 物理环境和连接性，437
- 规划系统架构，433
### NIC 聚合（链路聚合），606
### Unix 系统，672
### 节点
- 在 Drupal 中，576–577
- UML 组件/部署图，47–48
### 通知，248–249
### notifyObservers() 方法，Observable 接口，88
### NuSOAP，227

## O
### 对象组合，75
### 对象图，81
### 对象重载，160
### 对象关系映射。另见 ORM（对象关系映射）
### 目标，在推销过程中设定，409
### 面向对象编程。另见 OOP（面向对象编程）
### 对象
- 向对象添加方法，8
- 向对象添加属性，8–10
- 创建类，7–8
- 创建联系人管理器。另见 创建联系人管理器
- 定义，5
- 销毁，12–15
- 初始化，11–12
- 概述，6–7
- 保护对成员变量的访问，10–11
- 系统，71–73
### $objPDO 成员变量，170
### Observable 接口，观察者模式，83, 87–89
### Observer 接口，观察者模式，83–86, 88–89
### 观察者模式
- 连接 Observer 和 Observable，88–89
- 注意事项，89
- DataSource，87–88
- 概述，83
- 小部件，84–86
### 一次且仅一次重构，479–481
### 在线参考
- BaseCamp，428
- 群发电子邮件提供商，274
- 域密钥标识邮件，274
- eFax，271
- 启用 PHP 支持，136
- 极限编程，428
- 在 PHP 6 中实现 SOAP 的库，227
- LoadRunner，425
- Mantis，424, 544
- memcached 服务器，303
- MIME，270
- PDO 文档，151
- PHP 支持的驱动程序，137
- php.net 参考站点，128
- PMI（项目管理学院），416
- PostgreSQL 源代码，675
- Prado，377–378
- 发件人 ID，273
- Smarty，334, 342
- SoapClient 和 SoapServer 函数，227
- SPF 记录，273
- SQL 注入攻击，141
- Ulysses，361
- WSDL，233
- Zend Framework，379, 648
### 现场客户
- 案例研究开发方法，388
- XP，426
### 现场利用，284
### OOP（面向对象编程）
- 类，6
- 封装，27–28
- 继承。另见 继承
- 接口，25–27
- 对象。另见 对象
- 概述，5–6
- PHP 6 中的变更，29–30
- 总结，30
- 理解，3–5
### 操作码缓存，662
### open() 函数，291
### 操作系统，为 PHP 安装选择，672–673
### 操作系统，PHP 应用程序平台，598
### 操作，类图，36
### Oracle，128
### Organization 类，52–53, 68–71
### ORM（对象关系映射）
- 业务对象和。另见 业务对象
- DataBoundObject 类。另见 DataBoundObject 类
- 作为框架，358–359
- 概述，155
- 总结，185
- 类类型，155–157
- 在 Ulysses 框架中，377
### 外部连接，与数据库停顿，665
### 大纲窗口，Zend，651
### 输出，捕获 Smarty，341
### 开销，与 PHP，619–620
### 重写方法，父类中，20–23
### 加班，XP 和，427

## P
### 页面映射设计计划，422–423
### 页面，Prado 框架，378
### 父类
- 重写其方法，20–23
- 保留其功能，23–24
- parent::[function name]，23
### parse() 方法，电子邮件输出，269
### 解析请求文本，满足，503–505
### parse_url() 函数，210, 212
### 解析，连接字符串，210
### 无密码 SSH，566–567
### 密码
- 清理应用程序，477
- 良好的会话实践，286
- HTTP 工作原理，277–278
- Mantis 以管理员身份登录，547–548
- 验证，249
### 补丁，性能
- 修复代码停顿，665–667
- 修复数据库停顿，664–665
- 测试，667
### 路径，将 PHP 从 UNIX 迁移到 Windows，679–680
### 面向模式的软件架构，第 2 卷，并发和网络对象模式（Wiley，2000），199
### PDF，将推销文档创建为，410
### PDO（PHP 数据对象）
- 常量，143
- 数据库抽象，134–136
- 数据库特定函数，147
- 定义，135
- 启用 PHP 支持，135–136
- 执行查询，138
- 作为数据库抽象框架，359
- 错误处理，143–145
- 大对象，146–147
- 局限性，150–151
- 概述，127
- PDO 类，137
- PDOStatement 类，139
- 持久连接，147–148
- PHP 和数据库，128–134
- 预处理语句，139–141
- 会话性能与，302–303
- 单例实例化，149
- 存储过程，148–149
- 总结，152
- 只写语句，141–142
### PDO 类
- 常量，143
- 数据库特定函数，147
- 执行查询，138
- 错误处理，143–144
- 概述，137
- PDOStatement 类，139
- 预处理语句，139–141
- 事务和提交，142–143
- 只写语句，141–142
### PDOFactory，Ulysses 框架，375
### PDOStatement 类
- 数据库特定函数，147
- 错误处理，143–144
- 概述，139
- 查询数据库，138
### PEAR，使用 MIME，270
### PEAR 仓库，680
### PEAR::SOAP，227
### 完美工程时间单位，444
### 性能
- HTTPSession 类和，302–303
- 基本 PHP 会话的局限性，290
- 预处理语句和，141
### PHP 性能调优
- PHP 请求剖析，661–663
- 补丁，664–667
- 预先避免与，667–669
- 跟踪瓶颈，663–664
- 性能瓶颈类型，659–661
### 权限，Smarty 安装，335
### 持久性，Ulysses 框架，372–373
### 持久连接，PDO，147–148
### PHP
- 内容管理。另见 CMS（内容管理系统）
- 跨平台支持，622–623
- 语言简单性，620–622
- 低开销，619–620
- PHP 中的 MVC，309–311
- 概述，619
- 功能，624–625
- 总结，625
- 普遍性，624
- Zend 函数，651
### .php（控制器）
- MVC 规则，310
- search.php，324–325
- searchresults.php，327–329
### PHP，从事专业职业
- 动机，627–628
- 概述，627
- 软件开发人员，628–630
### PHP 数据对象。另见 PDO（PHP 数据对象）
### .phpm（类），MVC 规则，310
### PHPUnit
- 客户联系测试，465–467
- 安装，347
- 简介，346–347
- 使用的测试驱动开发，425
- 单元测试，346–350
- 编写测试，构建应用程序，453–460
### .phtml（模板）
- MVC 规则，310–311
- search.phtml，325–327
- searchresults.phtml，330
### 物理环境，与连接性，436–439
### 物理入侵，与会话安全，283–284
### 推销
- 使用功能规格说明，420
- 与报价单对比，406
- 与规格说明对比，406–407
- 结构，409–410
- 何时付出额外努力，408
- 何时拒绝，408–409
- 邀请谁参与，407
### 平台
- 应用服务器，599
- 数据库，599–600
- 外部网络，595–596
- 硬件，597
- 内部网络，596–597
- 操作系统，598
- 概述，595
- 软件架构，600
- Web 服务器，598–599
### PMI（项目管理学院），415
### 多态性，5
### portType 元素，WSDL，236
### POST 请求，HTTP
- 工作原理，276–278
- 作为无状态，275
- 性能瓶颈类型，659–661
- Ulysses 框架，366
### PostgreSQL 数据库
- 调用存储过程，148
- 首次配置 Mantis，545–546
- 通过 PDO 连接和断开连接，136
- 将 PHP 会话管理连接到，290–292
- PHP 中的连接性，128–132
- 数据库集群与复制，611
- 销毁对象，13–15
- 下载和安装，675–677
- HTTPSession 类，292
- 概述，12–13
- PHP 和，128–129
- php.net 参考站点，128
- 选择理由，674–675
- 架构，292–293
### 重定向获取（PRG）设计模式，331–332
### PHP 的功能，624–625
### 电源冗余，607–608
### Prado 框架，377–378
### 首选项窗口，Zend，649
### prepare() 方法，PDO，140
### prepare() 方法，PDOStatement 类，139
### 预处理语句，PDO，139–141
### 前提条件，项目管理，397
### PRG（重定向获取）设计模式，331–332
### 主键，修复数据库停顿，664
### 主要收件人，电子邮件，260–262, 267
### printArray() 方法，调试，221–222
### 隐私问题，Cookie，281
### 私有成员变量封装与，28
### HTTPSession 类，300
### 概述，11
### 权限，构建 CMS，588–589





### process
- 构建阶段, 424
- 项目规划中选择, 415–416
- 设计阶段, 422–423
- 移交, 425
- 对...做出决策, 419
- 概览, 419
- 规范阶段, 419–421
- 螺旋模型, 417–418
- 测试阶段, 424–425
- 瀑布模型, 416–417

### 脚本的处理时间, 660

### 生产环境, 555

### 生产服务器, 555

### professional software developer
- 学术技能, 630
- 社区技能, 630–631
- 超过 Web 开发技能, 628–629
- 概览, 628
- 软技能, 629
- 总结, 631

### 性能分析器, Zend, 654

### 编程方法论, 424–426

### project management
- 预期项目先决条件, 397
- 选择团队, 410–414
- CMS 构建中, 588
- 构建推介, 406–410
- 项目历史, 396
- Komodo, 654–655
- 概览, 393–394
- 项目面向对象, 394–396
- 项目启动原因, 394

### 项目管理学会 (PMI), 415

### project management, receiving formal brief
- 预算, 401–403
- 业务需求, 398–399
- 商业条款, 403–404
- 未来计划, 404
- 外观和感觉, 404–405
- 概览, 397–398
- 范围, 399–400
- 总结, 405–406
- 支持, 405
- 技术, 405
- 时间表, 400–401

### 项目经理, 410–411

### project overview
- 开发方法, 387–391
- 概览, 383–384
- 总结, 392
- 小部件世界, 背景, 384–386
- 小部件世界环境, 386–387

### project planning
- 构建阶段, 424
- 构建流程方法论, 425–428
- 变更管理, 428–430
- 选择流程, 415–416
- 设计阶段, 422–423
- 移交, 425
- 做出决策, 419
- 概览, 419
- 规范阶段, 419–421
- 螺旋流程, 417–418
- 总结, 428–430
- 测试阶段, 424–425
- 瀑布流程, 416–417

### 项目选项卡, Zend, 651

### properties
- 添加到类, 8–10
- 类的, 6
- 监控, 173
- 使用访问器方法, 11

### PropertyObject 类
- 联系人类型类, 58–62
- 创建联系人管理器, 56–58
- 更新 UML 图, 64

### 受保护成员变量
- 创建联系人管理器, 57

### DataBoundObject 类, 181
- 封装和, 28
- 概览, 11

### 原型设计, 业务对象, 158–160

### pserver, 643

### public members
- 封装和, 28
- 成员变量或方法, 11

### 标点符号, 在 PHP 中减少, 621–622

### Python, 对...的支持, 624

## Q

### QA (quality assurance)
- 介绍, 535–536
- 可衡量和可量化的质量, 538–540
- 质量定义, 537
- 测试。参见测试
- 与单元测试框架, 351–352
- 为什么你应该追求卓越, 536–537

## R

### -r 标志, rsync, 565

### 机架空间, 438

### RAID (独立磁盘冗余阵列), 607

### 反应器, 189

### 反应器模式, 199

### read() 函数, 291

### 实现, 类图, 38

### 现实世界容差 (RWT), QA, 538

### recalculate() 函数, 523, 525

### 收件人类, 252–253

### 收件人接口, 252–255

### 收件人。另见电子邮件用户
- 比较, 251
- 定义, 250
- EmailRecipient 类, 253–255
- Recipient 类, 252–253
- 使用集合存储, 256–257

### redraw() 函数, 观察者模式, 89

### 冗余, 433

### 独立磁盘冗余阵列 (RAID), 607

### 重新估算, 开始工作, 474–475, 594

### 重构 (Fowler), 481–482

### refactoring code
- 案例研究开发方法, 388
- 在极限编程中, 426
- 完成迭代, 483–492
- 概览, 476–482
- 差旅费报告应用程序, 509–514

### 重构：改善既有代码的设计 (Fowler, Beck, Brant, Opdyke and Roberts), 630

### 参考文献，图书。另见在线参考
- 设计模式, 199
- 极限编程, 387, 426
- 重构代码, 481–482
- 理解 XML, 226

### register() 方法, Logger 类, 210–213

### 回归测试, 351, 418

### 关系映射, 162

### 关系, UML 类图, 37–39, 52–55

### 发布, 387, 450–451

### 远程调试, Zend, 654

### removeItem() 方法, 集合类, 105–109

### replication
- 数据库和, 600
- 定义, 611

### 报告错误, Mantis, 552–553

### 表述性状态转移。参见 REST (表述性状态转移)

### 请求类, MVC, 314–322

### 请求元素, WSDL, 234–235

### requests, PHP
- 请求结构, 661–663
- SOAP 扩展, 237–239

### requirements
- 实现业务对象, 166–169
- UML 收集阶段, 31–33

### 韧性, 系统架构, 433

### 响应, PHP 6 SOAP 扩展, 237–239

## S

### REST (Representational State Transfer)
- 实现客户端, 244–245
- 构建服务器, 245–246
- 概览, 243
- PHP 6 和, 244

### 可重用性, 4, 16, 173

### roles, project
- 客户端, 414
- 识别, 395
- 利用以获益, 395–396
- 团队双角色, 413

### rollback() 方法, PDO, 142–143

### 轮询负载平衡方法, 436

### rsync
- 基本用法, 564–565
- 用于保持服务器同步, 566–567
- 语法示例, 565
- 使用 rsync 进行版本控制, 564

### Ruby, 对...的支持, 624

### 运行时配置, Smarty, 340

### Save() 方法
- 业务对象, 171
- DataBoundObject 类, 182

### 计划邮件表, 272

### scope
- cookie 的范围, 283–284
- 接收正式简报的范围, 399–400

### 屏幕, 创建, 399, 470–471

### search.php, 324–326, 339–340

### search.phtml, 326–327, 339–340

### searchresults.php, 327–329

### searchresults.phtml, 330

### 部分, 类别 vs., 578–579

### secure_handler() 方法, 196–197

### security
- 业务需求, 434
- 事件驱动编程, 196–198
- 规划系统架构, 433
- 会话, 281–285, 290

### SELECT 查询, ORM, 172, 173

### SELECT 语句, 171, 664

### 避免 SELECT *, 665

### send() 方法, 电子邮件, 261, 263

### 发件人 ID, 273

### 发件人策略框架 (SPF) 记录, 273

### 高级设计师, 选择, 413

### 序列图, UML, 44–46

### 顺序序列, 312

### 服务器负载, 601–602

### $_SERVER["HTTP_HOST"] 属性, 560

### servers
- 确定硬件需求, 434
- 物理位置, 436–439
- 规划系统架构, 432
- 机架空间考虑, 438

### 服务器端包含 (SSIs), 614–615

### Servlet
- 会话 ID, 378
- Ulysses 框架, 366–372

### session IDs
- 概览, 278
- 会话安全和, 281–285
- 在 cookie 中存储, 280–281
- 使用 URL 重写, 279–280

### session timeouts
- 创建表以计算, 292
- 良好会话实践, 285
- 概览, 278

### session_read_method(), 301

### session_set_save_handler() 方法, 291, 292, 301

### session_start() 方法, 288–289, 291

### 基于会话的负载平衡方法, 436

### sessions
- 基础, 288–290
- 计算 CIR, 437
- 计算月度传输, 438
- 定义, 275, 278
- 良好实践, 285–287
- HTTP 工作原理, 276–278
- 概览, 275
- 使用 cookie 持久化, 280–281
- 使用 URL 重写持久化, 279–280
- 安全, 281–285

### sessions and authentication
- 将 PHP 会话管理连接到数据库, 290–292
- 创建 Authentication 类, 290
- 数据库架构, 292–293
- 良好会话实践, 287
- HTTPSession 类工作原理, 300–302
- HTTPSession.php 代码, 293–297
- 性能考虑, 302–303
- 全部整合, 304
- 总结, 304
- 测试 HTTPSession 类, 297–300
- 使用 HTTPSession 类, 292

### _set() 重载方法, 302

### SetAccessor() 方法, 160, 183

### _setClass() 方法, SoapServer, 229

### setLoadCallback 方法, 集合类, 115–119

### _setPersistence() 方法, SoapServer, 229

### 共享网络驱动器, 666

### 短消息服务。参见 SMS (短消息服务) 文本消息

### 静默模式, PDO, 143

### 简单对象访问协议。参见 SOAP (简单对象访问协议)

### PHP 的简洁性, 619–622

### 单例模式, 149, 205

### sizeof() 函数, 108

### 小型发布, XP, 426

### Smarty
- 关联数组中, 337
- 捕获输出, 342
- 条件语句中, 337–338
- 最终定稿的差旅费报告, 516–520
- 函数, 341–342
- 进一步阅读, 342
- 安装, 334–335
- 线性数组中, 336
- 使用 Smarty 制作 HTML 屏幕原型, 529–532





- 多维数组，340–341
- 其他模板，342
- 生成模板驱动的电子邮件输出，268–270
- 使用它重写 search.php，338–339
- 运行时配置，340
- smartytest.php，335
- smartytest.tpl，336
- 传统模板化 vs.，342
- 使用它的真正模板化，334
- 变量修饰符，341
- smarty test.php，335
- smarty test.tpl，336
- SMS（短消息服务）文本消息
- 概述，270
- 收件人，251
- 用作身份验证，250
- SMTP 服务器，271
- 代码片段
- CMS 模板和，590
- Frog CMS 管理，584–585
- SOAP（简单对象访问协议）
- 创建服务器，240–243
- 概述，226
- PHP 6 与，226–227
- PHP 6 扩展，227–230
- 通过其的 SMS 文本消息接口，270
- SOAP（简单对象访问协议），创建客户端
- 中的异常处理，239–240
- 概述，232
- 请求和响应信封，237–239
- WSDL 文档，232–237
- soap_functions.php，230
- SoapClient 函数，227，228
- SoapFault 对象，229，239–240
- SoapHeader 对象，229
- SoapParam 对象，230
- SoapServer 函数，227，228–229
- SoapVar 对象，229
- 套接字
- 性能调优，666
- 响应时间，601
- PHP 专业人员的软技能，629
- 软件。另请参见专业软件开发人员
- 架构设计计划，423
- 选择架构师和工程师，412
- 架构的重要性，600
- 基于其的负载均衡，435
- 版本控制，643–645
- Wikipedia（MediaWiki），617
- 软件开发人员。参见专业软件开发人员
- 源代码存储库，477
- 源代码工作流，部署
- 自动化版本控制，562–565
- 图表，561
- 概述，560–562
- SourceSafe，643–644
- 垃圾邮件
- 广播电子邮件提供商和，274
- 域密钥识别邮件和，273–274
- 限制其投递率，271–272
- 发件人 ID 和，273
- SPF 记录和，273
- 规格说明阶段，流程，419–421
- 规格说明
- 客户报告的错误，429
- 签署后的更改，429
- 由解释差异引起的争议，429
- 提案 vs.，406–407
- 修订，428–429
- 速度，和基本 PHP 会话，290
- SPF（发件人策略框架）记录，273
- 尖峰
- 启动项目，448–449
- 差旅费报告，499–500
- 螺旋模型
- 选择，417–418
- 关于其的决策，419
- 技术规格说明，421
- 电子表格，520–526
- SQL 注入攻击，141
- Squid Web 服务器，599，605
- SSIs (服务器端包含)，614–615
- 暂存服务器，642
- 起点，UML 活动图，42
- 启动项目，构建应用程序
- 收集关于新系统的用户故事，442–444
- 估算提示，449–450
- 概述，441–442
- 细化估算，448
- 发布计划，450–451
- 尖峰，448–449
- 用户故事权重估算，444–447
- 开始工作，构建应用程序
- 创建登录屏幕，460–464
- 创建屏幕，470–471

- 开始工作，构建应用程序（续）
- 客户联系需求，464–465
- 客户联系测试，465–467
- 喂养野兽，471–474
- 下一个用户故事，464
- 概述用户故事细节，451–452
- PHPUnit，453–460
- 重新估算，474–475
- 满足测试，467–469
- 编写测试，452–453
- 状态，6
- 状态图，UML，46–47
- 无状态协议，HTTP 为，248，275
- 静态文件服务器，Wikipedia，617
- 静态方法，63，113
- 存储要求，434，437
- 存储过程，PDO，148–149
- 用户故事
- 估算实现所需工作量，444–447
- 估算提示，449–450
- 概述其细节，451–452
- 发布计划，450–451
- 尖峰，448–449
- 通过文档化启动项目，442–444
- strftime() 函数，Logger 类，206–207
- 字符串，Logger 类，207
- strip 函数，Smarty，341
- 工作室美工，413
- 工作室开发环境，556
- 工作室暂存环境，557
- StudlyCaps，162
- 风格指南设计计划，422
- 子类，LoggerBackend 类，213–215
- 提交，强制，483
- 订阅者，CMS，588
- 子查询，修复数据库阻塞，665
- Subversion。另请参见 SVN (Subversion)
- 补充密钥，会话安全，283
- 支持
- 生产后，405
- 跨平台，622–623
- SVN (Subversion)
- 版本控制软件，644–645
- 使用其进行版本控制，563
- Zend 与其的集成，654
- 泳道，UML 活动图，44
- 语法，通常理解的，622
- 系统架构
- 业务需求，433–434
- 定义，431
- 硬件要求，434–436
- 重要性，432
- 维护管理，439
- 物理环境和连接性，436–439
- 总结，439

### T

- 表，数据库
- 记录到其中，215–219
- 维护作业队列以保存电子邮件，271–272
- 会话身份验证和，292–293
- 标记
- 在工作室暂存环境中，557
- 版本控制技术，645–646
- 分类法，组织节点，577
- 团队，项目
- 客户经理，411
- 客户端开发人员，412
- 角色兼任，413
- 信息架构师，412
- 首席架构师，411–412
- 项目经理，410–411
- 资深设计师，413
- 软件架构师和工程师，412
- 工作室美工，413
- 工作实践，413
- 技术规格说明，421–422
- 技术
- 案例研究项目概述，391
- 接收其正式简报，405
- TemplatedEmailCommunication 类，268–270
- 模板。另请参见真正模板化
- CMS 构建，590–591
- ExpressionEngine，582–583
- MVC 设计模式视图，307
- 原生 PHP，310
- 使用其生成电子邮件输出，268–270
- search.phtml，MVC 迷你工具包，326–327
- searchresults.phtml，MVC 迷你工具包，330
- Zend Framework，379
- Zend IDE，650
- 十点计划，423
- 测试用例类，345
- 测试用例，PHPUnit，347–350
- 测试套件
- PHPUnit 测试，350
- 单元测试，345

- TestConstraints() 方法，329
- 测试驱动开发，425–426
- 测试
- 案例研究开发方法，388
- 客户联系，465–467
- 极限编程，426
- 故障跟踪，543–544
- 功能测试，541–542
- HTTPSession 类，297–300
- 负载测试，542
- 性能调优，667
- PHP 安装，679
- 满足，467–469
- 差旅费报告应用程序。参见差旅费报告
- 单元测试。参见单元测试
- 可用性测试，543
- 使用 Mantis。参见 Mantis
- 瀑布流程 vs. 螺旋，418
- 编写，构建应用程序，452–453
- 测试阶段，424–425
- 文本消息
- 通知，249
- 收件人，251
- 验证，250
- 主题，Drupal，577
- 瘦客户端，实现，274
- 多线程，601–602
- 三层以太网分段，609–610
- thttpd Web 服务器，599
- 时间表，接收其正式简报，400–401
- 时间戳，206–208，282
- 生存时间 (TTL) 指令，604
- 时区，PHP，207
- 工具箱，Komodo，656
- 拓扑，版本控制，641–643
- 流量
- 确定业务需求，433
- PHP 和。另请参见高流量/高可用性
- 网站，611–613
- 事务，PDO，142–143
- 传输速率，601
- 转换，UML 活动图，42
- 差旅费报告
- 更多差旅周测试，500–502
- 概述，492–494
- 发布计划，450
- 满足差旅周测试，502–514
- 尖峰，499–500
- 差旅费用条目，494–496
- 差旅周，496–499
- 差旅费报告，最终版
- 其他任何内容，526–529
- 概述，514–520
- 作为电子表格，520–526
- 触发的电子邮件，提供商，274
- 真正模板化
- 高级 Smarty，340–342
- 定义，327
- 安装 Smarty，334–335
- 原生 PHP 模板化，333
- 使用 Smarty 模板，334
- 使用 Smarty，335–340
- 何时使用传统模板 vs. Smarty，342
- try...catch 块
- SOAP 客户端中的异常处理，240
- PDO 中的错误处理，144–145
- 在集合中封装方法调用，124–126
- TTL (生存时间) 指令，604

### U

- PHP 的普遍性，624
- Ulysses
- 业务对象，364–365
- 将其与 Prado 框架进行比较，377–378
- 作为首选框架，377
- 回家，374
- 安装，361–363
- 简介，361
- 持久性，372–373
- 处理用户输入，371–372
- 快速检查，374
- 快速摘要，375–377
- 保存输入，374–375
- Servlet，366–371
- 设置，363–364
- 验证，373–374
- 需要完成的工作，432–433
- 使用，363
- UML (统一建模语言)
- 活动图，42–44
- 类图。另请参见类图，UML 组件和部署图，47–48
- 创建联系人管理器应用程序，50–56
- 设计 Collection 类，105–106
- 使用其进行继承，16–17
- 其需求收集阶段，31–32
- 序列图，44–46
- 状态图，46–47




- 统一建模语言 (Unified Modeling Language) (续)
- 概述, 48
- 更新, 64
- 用例图, 33-35
- 单向可导性, 37-38
- 统一建模语言。另见 UML (统一建模语言)
- 统一资源定位符 (URL)，和 REST, 243-246
- 单元测试
- 案例研究开发方法, 391
- 为类创建测试套件, 345
- 设计类的接口, 344-345
- 在极限编程中, 426
- 概述, 343-344
- 用于质量保证, 540-541
- 使用的理由, 351-352
- 使用的测试驱动开发, 426
- 差旅费报告应用程序。另见差旅费报告
- 使用 PHPUnit, 346-350
- 编写你的类的实现, 346
- UNIX 服务器
- 选择, 673-674
- 定义, 672
- 作为服务器环境的优点, 672-673
- 在 UNIX 服务器上安装 PHP, 673
- UNIX 服务器的操作系统, 598
- 从 UNIX 服务器将 PHP 迁移到 Windows, 679-680
- 更新
- 设计小部件, 84-86
- 实现业务对象, 162, 167-168
- 观察者模式, 83
- URL 重写
- 作为 URL 重写机制的框架, 357
- 使用 URL 重写的会话持久化, 279-280
- 在 Ulysses 框架中, 376
- 统一资源定位符 (URL)，和 REST, 243-246
- 产品可用性, QA, 539
- 可用性测试, 543
- 用例图, 33-35
- 用例
- 应用程序框架场景, 359-361
- 与用例关联的序列图, 44
- 用户代理一致性, 286
- 用户通信
- 阻塞活动, 271
- 广播电子邮件提供商, 274
- 作为类层次结构, 251-258

- 可投递性, 272-273
- 域密钥和 DKIM, 273-274
- 给你的用户发电子邮件。另见给用户发电子邮件
- 电子邮件到传真网关, 271
- 维护作业队列, 271-272
- 用户通信的理由, 247-250
- 发件人 ID, 273
- SMS 短信, 270
- SPF 记录, 273
- 用户通信的类型, 250-251
- 用户名, 277-278, 286
- 用户, Mantis, 548-550
- 实用类
- 业务对象 vs., 343
- 提供实用类的框架, 359
- 概述, 156
- 在 Ulysses 框架中, 377

## V

- -v 标志, rsync, 564
- 验证
- 提供验证的框架, 357, 358
- Ulysses 框架和验证, 373-374, 376
- 通过验证的用户通信, 249-250
- 变量修饰符, Smarty, 341
- 变量, 287
- 产品外观, QA, 539-540
- 版本控制
- 高级技术, 645-646
- 自动化。另见自动化版本控制, 仓库提取
- PHP 框架的部署, 379-380
- FTP 和版本控制, 567
- 保持服务器同步, 566-567
- 在构建阶段维护, 424
- 概述, 635
- 版本控制的原则, 635-641
- 软件, 643-645
- 拓扑, 641-643
- 使用 rsync, 564-567
- 与版本控制的 Zend 集成, 654
- 视图, MVC 设计模式
- 文件命名约定, 310
- 介绍, 306
- 概述, 307-308
- 在 Web 应用程序中, 308
- 查看问题屏幕, Mantis, 553
- 虚拟化, 597
- 可见性, 成员变量, 11, 28

## W

- 瀑布模型
- 选择, 416-417
- 极限编程 vs., 391
- 概述, 389-391

- Web 应用程序中的 MVC, 308

- Web 开发技能, PHP 专业人员, 628-629

- Web 服务器
- 用于应用程序平台, 598-599
- 确定, 434
- Flickr, 616
- 保持同步, 566-567
- 负载, 601-602
- 负载平衡, 603-605
- PHP 安装, 673-674

- Web 服务描述语言。另见 WSDL (Web 服务描述语言)

- Web 服务
- 概述, 225-226
- REST, 243-246
- SOAP 另见 SOAP (简单对象访问协议)

- 小部件对象
- 连接到 Observable 数据源, 88-89
- 在观察者模式中设计, 84-86
- 实装装饰器模式, 89-91

- Widget World 软件开发案例研究
- Widget World 的背景, 384-386
- 构建应用程序。另见构建应用程序
- 部署。另见部署
- 财务层, 386
- 政治层, 386
- 项目管理。另见项目管理
- 项目概览。另见项目概览
- 项目规划。另见项目规划
- 系统架构。另见系统架构
- 技术层, 386
- WW-SFAT 需求, 387
- 你在 Widget World 中的角色, 387

- Wikipedia, 616-618

- 通配符 DNS 设置, 556

- Windows。另见 Microsoft Windows
- 线框图, 信息架构设计, 422-423

- 工作流, 在内容管理中, 572, 589-590

- 工作实践, 项目团队, 413

- 蠕虫, 284

- 包装类, 133-134

- write() 函数, 291

- 仅写语句, PDO, 111-142

- 编写编译器和解释器 (Mak), 630

- WSDL (Web 服务描述语言)
- 增强 SOAP 应用程序, 227
- 创建 SOAP 客户端, 230-231
- 创建 SOAP 服务器, 240-243
- WSDL 在 SOAP 中的使用, 226
- SoapClient 函数, 228
- 理解在 SOAP 中的用法, 232-237

- WW-SFAT 经理, 384-385, 387

## X

- XML
- REST 的使用, 244
- SOAP 的使用, 226

- XP (极限编程)
- XP 中的案例研究开发, 387-391
- 定义, 426
- 理解, 426-427
- 何时使用, 428

## Z

- -z 标志, rsync, 565

- Zend (Zend Studio)
- 使用 ZDE 调试, 651-654
- 编辑代码, 649-650
- 检查代码, 650-651
- 管理项目, 649
- 更多工具, 654
- 概述, 648-649
- Zend Framework, 378-379
- Zend Guard, 654
