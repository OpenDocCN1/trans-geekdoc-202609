
# Typed PHP 入门指南

## 引言

### 为什么写这本书

我决定写这本书是因为我花了大量时间致力于开发简化字符串、数组等处理方法的库。它们被称为标量类型（Scalar Types），因为 PHP 处理它们的方式与对象不同。它们没有属性，也没有方法。

PHP 拥有丰富的历史并在 Web 占据主导地位。尽管存在语言不一致性和困难（特别是在处理这些标量类型时），它取得了巨大的成就。Bjarne Stroustrup 曾说过：“语言只有两种：人们抱怨的语言和没有人使用的语言。”。PHP 是那种*每个人*都在使用的语言之一，但这通常被视为忽视糟糕部分并直接完成任务的理由。

最后，你应该拥有一个良好的网络连接。本书中的示例在`Vagrant`虚拟机内部运行效果最好。如果你对这个术语熟悉，不用担心。我们稍后会讨论它，它基本上是一种用于安装开发环境的软件。这种安装经常发生，并且受益于快速的连接。

## 过程式 / 面向对象

过程式和面向对象是不同的编程风格，它们以不同的方式处理程序执行。了解它们的工作原理，以及它们如何定义标量类型的状态是有益的。

### 过程式编程

过程式编程描述了一种**自上而下**程序执行方法。也就是说；过程式程序由一系列解释器要执行的步骤组成（从上到下）。

在伪代码中，一个过程式的图像缩放程序可能如下：

1. 开始执行
2. 然后存储由`open_file()`函数返回的文件引用
3. 然后存储由`resize_image()`函数返回的修改后的图像
4. 然后关闭打开的文件
5. 然后存储由`open_file()`函数返回的文件引用
6. 然后将修改后的图像数据写入第二个打开的文件
7. 然后关闭该文件
8. 然后清空修改后的图像变量
9. 结束执行

过程式程序可以调用函数（如示例所示）并可以定义函数。当前执行的行位置可以通过循环结构和类似 goto 的结构进行修改，但在大多数情况下，程序是框定在一组指令中的。

### 面向对象编程

面向对象编程将程序执行描述为实体（或对象）的交互和描述。这些对象可以具有任意属性（所有变量的别名）和方法（所有函数的别名）的组合。

这些所有函数内部的代码仍然是从上到下执行的，但核心思想是程序依赖对象之间的通信来保持其连贯性。

在伪代码中，一个面向对象的图像缩放程序可能如下：

1. 开始执行
2. 然后创建一个文件对象
3. 然后创建一个图像缩放对象
4. 然后将文件对象传递给图像缩放对象
5. 然后创建另一个文件对象
6. 然后将图像缩放对象的`resize()`方法的结果写入第二个文件对象
7. 然后关闭第二个文件对象
8. 然后销毁第二个文件对象
9. 然后销毁图像缩放对象
10. 然后销毁第一个文件对象
11. 结束执行

### 哪种最好？

……这是一个错误的问题。两者都有其优缺点。面向对象编程产生的代码通常比过程式编程多。面向对象编程有利于更好的关注点分离。换句话说——思考对象及其行为比思考整个程序的流程要更容易。

最终，过程式代码可以像面向对象代码一样整洁。

“有时，优雅的实现就是一个函数。不是方法。不是类。不是框架。仅仅是一个函数。” - John Carmack

### PHP 是哪种？

PHP 是非常过程式的。这就是 Rasmus（在那个远古的时代）构建它的方式，它也一直基本保持这样。这一点在处理和操作标量变量时是显而易见的。PHP 类型不是对象。

对于大多数中小型项目来说，添加一个修订后的类型系统是没有必要的。然而，如果你已经学会了如何构建（甚至只是使用）一个良好的类型系统，那么在大型项目中使用它难道不是很有意义吗？或者在任何你足够在乎的项目中使用呢？

PHP 的这一领域经常将开发者推向更漂亮的语言。不要成为那些开发者之一！学习如何通过使用整洁的抽象来编写更整洁的代码。

## 结构

### 封装 (Boxing)

“封装”（Boxing）是指将数据封装（封闭）在类中的做法，以便为被封装的数据添加行为。让我们来看一个例子：

```php
 1 <?php
 2 
 3 class StringBox
 4 {
 5   /**
 6    * @var string
 7    */
 8   protected $data;
 9 
10   /**
11    * @param string $data
12    */
13   public function __construct($data)
14   {
15     $this->data = $data;
16   }
17 
18   /**
19    * @return string
20    */
21   public function toString()
22   {
23     return (string) $this->data;
24   }
25 
26   /**
27    * @return string
28    */
29   public function toUpperCase()
30   {
31     return strtoupper($this->data);
32   }
33 
34   /**
35    * @return string
36    */
37   public function toLowerCase()
38   {
39     return strtolower($this->data);
40   }
41 
42   /**
43    * @param string $needle
44    * @param mixed  $offset
45    *
46    * @return int
47    */
48   public function getIndexOf($needle, $offset = null)
49   {
50     $index = strpos($this->data, $needle, $offset);
51 
52     if ($index === false) {
53       return -1;
54     }
55 
56     return $index;
57   }
58 }
59 
60 $box = new StringBox("Hello World");
61 
62 print $box->toString();          // "hello world"
63 print $box->toUpperCase();       // "HELLO WORLD"
64 print $box->toLowerCase();       // "hello world"
65 print $box->getIndexOf("foo");   // -1
66 print $box->getIndexOf("World"); // 6
```

这种方法被 PHP 完全支持，不需要任何额外的扩展或依赖。如果你仔细想，这是一个简单的概念。你正在使用受保护属性，并暴露一个公有 API 来设置、获取和操作它们。

它的困难之处在于，这会导致比直接使用原生函数产生多得多的代码。你需要定义包装器（wrappers）。你需要定义 setter（set 器）和 getter（get 器）。每当你想要放入`native`类型并取出`native`类型时，都必须使用它们。我最后那句话的意思是？

```php
1 $helloBox = new StringBox("Hello");
2 $worldBox = new StringBox("World");
3 
4 $worldBox = new StringBox(
5   $helloBox->toString() . " " . $worldBox->toString()
6 );
```

这很快就会变得难以处理。它也更消耗内存，并且比直接使用原生函数更慢。PHP 允许使用一个名为`__toString`的方法。当一个类定义了这个方法（返回一个字符串），并且该类的实例用在一个期望字符串的操作中时；`__toString`方法会被自动调用。这还不足以让我们模拟一个可扩展的类型系统，否则它就太短了。

### 解析类型 (Resolving Types)

PHP 是弱类型的。这意味着，变量可以在不指定类型的情况下声明。它们的类型可以在任何时候被更改。它们可以根据需要强制转换为不同的类型。如果我们想实现更强的类型处理，我们需要能够识别变量的类型。`gettype`函数返回变量的数据类型。它可以识别以下类型：

- `boolean`
- `integer`
- `double`
- `string`
- `array`
- `object`
- `resource`

如果这些类型中没有一个能正确描述变量，`gettype`将返回`unknown type`。我们再次看到了一些不一致之处。首先，浮点数被识别为`double`，而空值返回为`NULL`（与其他所有类型标识符相反）。我们可以使用类似于下面的内容对此函数进行抽象：

```php
1 <?php
2 
3 function type($variable) {
4   $type = gettype($variable);
5 
6   switch ($type) {
7 
8     case "integer":
9     case "double":
10       return "number";
11 
12     case "NULL":
13       return "null";
14 
15   }
16 
17   return $type;
18 }
19 
20 print type(0);    // "number"
21 print type(0.0);   // "number"
22 print type(null); // "null"
```

`type(0)` // "number"

`type(0.0)` // "number"

`type(null)` // "null"

### 可调用性 (Callable)

`is_callable`函数用于检查变量是否是可调用的。在 PHP 中，很多东西都是可调用的：

- 匿名函数
- 闭包
- 静态方法
- 实例方法
- 带有`__invoke`方法的对象

例如：

```php
<?php
function hello() {
    echo "hello";
}
var_dump(is_callable('hello')); // true

$anonymous = function() {
    echo "anonymous";
};
var_dump(is_callable($anonymous)); // true

class MyClass {
    public static function method() {
        echo "static method";
    }
    public function method() {
        echo "method";
    }
}

var_dump(is_callable(['MyClass', 'method'])); // true
$obj = new MyClass();
var_dump(is_callable([$obj, 'method'])); // true

class Invoker {
    public function __invoke() {
        echo "invoked";
    }
}
$invoker = new Invoker();
var_dump(is_callable($invoker)); // true
```

但是，`is_callable`并不总是检查它是否是函数。它只是检查它是否可以被调用。这意味着，如果一个类定义了`__invoke`方法，那么它的实例就是可调用的。

```php
<?php
class Invoker {
    public function __invoke() {
        echo "invoked";
    }
}
$invoker = new Invoker();
var_dump(is_callable($invoker)); // true
```

此外，`is_callable`还可以检查字符串是否代表一个定义的函数名。

```php
<?php
function hello() {
    echo "hello";
}
var_dump(is_callable('hello')); // true
var_dump(is_callable('non_existent_function')); // false
```

总之，`is_callable`是一个非常实用的工具，只要你理解它的工作原理。

PHP 文档（请访问[`www.php.net/manual/en/intro.pcre.php`](http://www.php.net/manual/en/intro.pcre.php)）将表达式描述为用定界符包围的[字符串]。这些定界符可以是任何非字母数字字符，但不能是反斜杠或空字节。

我们可以使用以下代码涵盖大部分情况：

```php
 1 <?php
 2 
 3 function is_regex($variable) {
 4   return @preg_match($regex, "") !== false
 5     && preg_last_error() == PREG_NO_ERROR;
 6 }
 7 
 8 print is_regex("/^.*$/"); // true
 9 print is_regex("/hello world/"); // true
10 print is_regex("/hello world/i"); // true
11 print is_regex("hello world"); // false
12 print is_regex("\\hello world\\"); // false
13 print is_regex("\\x00foo\\x00"); // false
14 print is_regex("1foo1"); // false
15 print is_regex("afooa"); // false
```

`preg_match`函数在匹配时返回`1`，不匹配时返回`0`，发生错误时返回`false`。假设`preg_match`返回`false`，错误可能是由于任何原因引起的（例如`PREG_INTERNAL_ERROR`或`PREG_BAD_UTF8_ERROR`）。因此，我们使用`preg_last_error`函数来排除所有其他错误。

使用错误抑制（`@`）通常是一个坏主意。只有极少数情况下使用它被认为是可以的。而这里就是其中之一！

## 命名空间函数 (Namespace Functions)

我之前提到过所有这些全局函数都是不好的，而且有一个非常简单的替代方案：命名空间函数。你可能已经在已经在类中使用过命名空间，但同样的结构也能很好地隔离函数：

```php
 1 <?php
 2 
 3 namespace Type\String {
 4   function length($string) {
 5     return strlen($string);
 6   }
 7 }
 8 
 9 namespace {
10   print Type\String\length("Hello World");
11 }
```

### Composer 自动加载 (Composer Autoload)

这种函数定义并不遵循标准的自动加载模式。为了让 Composer 自动加载此类文件，必须显式定义应该加载哪些文件：

```json
1 {
2   "autoload" : {
3     "files" : [
4       "namespace-functions.php"
5     ]
6   }
7 }
```

之后，我们必须使用以下命令导出旧的自动加载器：

```bash
1 $ composer dump-autoload
2 
3 Generating autoload files
```

现在，这些（包含命名空间函数的文件将在任何使用 Composer 自动加载器的地方被自动加载。

### 未来的特性 (Future Goodies)

PHP 5.6 支持`use function`结构，用于从其他命名空间导入函数。它目前处于测试阶段（编写本文时），但这个功能非常符合我们的胃口。

同时，可以部分导入函数：

```php
1 use Type\String;
2 
3 print String\length("Hello World");
```

这对于深度嵌套的设计尤为有用。尽管如此，能够省略全命名空间仍然很棒。结果更加整洁（er）。

## 结论 (Conclusion)

即使在今天，也可以创建更整洁的类型/抽象。我们不需要特殊的扩展或编译。只需要一点努力就能让代码变得干净。尽管如此，扩展可以使我们的生活更轻松，同时允许我们希望实现的定制化程度。我们将在下一章中查看其中几个……

## 扩展 (Extensions)

即使在今天，也可以创建更整洁的类型/抽象。我们不需要特殊的扩展或编译。只需要一点努力就能让代码变得干净。尽管如此，扩展可以使我们的生活更轻松，同时允许我们希望实现的定制化程度。我们将在下一章中查看其中几个……

（注：此处原文重复，我将继续翻译翻译）

`preg_match`函数在匹配时返回`1`，不匹配时返回`0`，发生错误时返回`false`。假设`preg_match`返回`false`，错误可能是由于任何原因引起的（例如`PREG_INTERNAL_ERROR`或`PREG_BAD_UTF8_ERROR`）。因此，我们使用`preg_last_error`函数来排除所有其他错误。

使用错误抑制（`@`）通常是一个坏主意。只有极少数情况下使用它被认为是可以的。而这里就是其中之一！

## 命名空间函数 (Namespace Functions)



我之前提到过，所有这些全局函数都是不好的，而且有一个非常简单的替代方案：命名空间函数。你可能已经在类中使用过命名空间，但同样的结构也能很好地隔离函数：

```php
1 <?php
2 
3 namespace Type\String {
4   function length($string) {
5     return strlen($string);
6   }
7 }
8 
9 namespace {
10   print Type\String\length("Hello World");
11 }
```

### Composer 自动加载（Composer Autoload）

这种函数定义并不遵循标准的自动加载模式。为了让 Composer 自动加载此类文件，必须显式定义应该加载哪些文件：

```json
1 {
2   "autoload" : {
3     "files" : [
4       "namespace-functions.php"
5     ]
6   }
7 }
```

之后，我们必须使用以下命令导出旧的自动加载器：

```bash
1 $ composer dump-autoload
2 
3 Generating autoload files
```

现在，这些包含命名空间函数的文件将在任何使用 Composer 自动加载器的地方被自动加载。

### 未来的特性（Future Goodies）

PHP 5.6 支持 `use function` 结构，用于从其他命名空间导入函数。它目前处于测试阶段（编写本文时），但这个功能非常符合我们的胃口。

同时，可以部分导入函数：

```php
1 use Type\String;
2 
3 print String\length("Hello World");
```

这对于深度嵌套的设计尤为有用。尽管如此，能够省略全命名空间仍然很棒。结果更加整洁。

## 结论（Conclusion）

即使在今天，也可以创建更整洁的类型/抽象。我们不需要特殊的扩展或编译。只需要一点努力就能让代码变得干净。尽管如此，扩展可以使我们的生活更轻松，同时允许我们实现所希望的定制化程度。我们将在下一章中查看其中几个……

## 扩展（Extensions）

此命令将带你进入虚拟机内部，就像连接到远程服务器一样。在虚拟机内部，你可以运行客户主机操作系统通常支持的任何命令，包括针对虚拟机上安装的包执行 PHP 脚本。

[`phansible.com`](http://phansible.com) 是 [Erika Heidi](https://twitter.com/erikaheidi) 的心血。她也是 [Vagrant Cookbook](https://leanpub.com/vagrantcookbook) 的作者。如果你有任何问题，或者只是想了解更多关于 Vagrant 的信息，我强烈推荐阅读这本书！

## SPL 类型

SPL（或标准 PHP 库）是一个包含额外类型的库，用于增强 PHP 原生类型。它有一些流行的类，如 `LogicException` 和 `ArrayObject`。某些标准 PHP 安装版本附带了部分 SPL。但我们很快要查看的部分并不包含它们……

你可以在 `http://www.php.net/manual/en/book.spl-types.php` 找到这些神秘库。

本节假设你正在使用之前介绍的 Vagrant box。如果不是，请先进行设置。这些命令是 Linux 特有的，并且取决于之前解释过的预装模块。

### 安装 SPL 类型

要安装它们，请运行以下命令：

```bash
1 $ sudo apt-get install libpcre3-dev php5-dev
2 
3 Reading package lists... Done
4 Building dependency tree
5 Reading state information... Done
6 The following extra packages will be installed:
7   autoconf automake autotools-dev build-essential...
```

```bash
1 $ sudo pecl install SPL_Types
2 
3 downloading SPL_Types-0.4.0.tgz ...
4 Starting to download SPL_Types-0.4.0.tgz (8,388 bytes)
5 .....done: 8,388 bytes
6 6 source files, building
7 running: phpize...
```

这两个命令安装了编译 PECL 扩展所需的先决条件。PECL 是一个类似于 PEAR 的库。如果你这两个都还没听过，请不要担心。你只需要知道 SPL 类型托管在此处，因此为了安装它们，我们需要能够编译 PECL 扩展。

```bash
1 $ sudo bash -c "echo extension=spl_types.so >> /etc/php5/cli/php.ini"
```

此命令将 `extension=spl_types.so` 添加到 `php.ini` 文件中（按照安装说明）。

```bash
1 $ sudo service php5-fpm restart
2 
3 php5-fpm stop/waiting
4 php5-fpm start/running, process...
```

此命令重启 PHP-FPM——解释 PHP 命令行指令和 Nginx Web 请求的进程。这些命令应该已经安装了 SPL 类型，但为了起见，请运行以下命令：

```bash
1 $ php -i | grep SPL_Types
2 SPL_Types
```

如果你看到了 `SPL_Types` 这一行，那么就可以正常使用了！

### 使用 SPL 类型

让我们来看一些这些类的用法示例：

```php
1 <?php
2 
3 class NumberType extends SplFloat
4 {
5   /**
6    * @return float
7    */
8   public function toInteger()
9   {
10     return round($this);
11   }
12 
13   /**
14    * @return string
15    */
16   public function toString()
17   {
18     return (string) $this;
19   }
20 }
21 
22 $number = new NumberType(13.86);
23 
24 print $number->toInteger(); // 14
25 print $number->toString();  // "13.86"
26 
27 print (float) $number + 1.00; // 14.86
28 print $number * 12;           // 156
```

`toInteger` 和 `toString` 方法对包装类做了类似的事情。神奇发生在对 `$number` 对象进行基础算术运算时。SPL 类型在算术表达式、类型转换或拼接时会自动解箱。任何通常情况下适用于标量类型的运算符，也适用于相应的 SPL 类型。

这里是另一个例子：

```php
1 <?php
2 
3 class StringType extends SplString
4 {
5   /**
6    * @param int   $start
7    * @param mixed $length
8    *
9    * @return StringType
10   */
11   public function slice($start = 0, $length = null)
12   {
13     if ($length === null) {
14       return new static(substr($this, $start));
15     }
16 
17     return new static(substr($this, $start, $length));
18   }
19 }
20 
21 $string = new StringType("Hello World");
22 
23 print $string->slice(6); // "World"
```

我们可以设计这些类型使其返回新实例。这为我们提供了一个简单的链式调用接口。

在假设原生 PHP 函数的返回类型时要小心。务必确认。

Zephir 是一个用于编写可编译和可安装 PHP 扩展的框架，它使用一种与 C 代码具有相似之处的 PHP 超集语言。Zephir 并不是严格的 PHP 扩展，Zephir 库也用 PHP 编写。

它与 Phalcon 框架属于同一个集体，而 Phalcon 本身就是一个 PHP 扩展。这将会变得非常有趣！

## 安装 Zephir

Zephir 需要一些库才能正确编译。我们可以通过以下命令安装它们：

```bash
1 $ sudo apt-get install git gcc make re2c php5 php5-json php5-dev libpcre3-dev
```

接下来，我们需要安装 `JSON-C` 库（Zephir 用它来编译扩展）：

```bash
1 $ git clone https://github.com/json-c/json-c.git && cd json-c && sh autogen.sh\
2 && ./configure && make && sudo make install
```

这些命令将克隆 `JSON-C` 仓库并对其进行配置和编译。最后，我们需要安装 Zephir：

```bash
1 $ git clone https://github.com/phalcon/zephir && cd zephir && ./install -c
```

这应该已经安装了一个可用的 Zephir 版本。你可以进入克隆文件夹并运行以下命令来检查它是否正常工作：

```bash
1 $ zephir version
```

## 使用 Zephir

使用 Zephir 相对简单（考虑到实际执行的工作）。让我们从初始化一个全新的扩展骨架项目开始：

```bash
1 $ zephir init type
```

这将在当前工作目录下创建一个骨架项目文件夹。进入新创建的 `type` 目录并运行：

```bash
1 $ ls -la
2 
3 ext/ type/ config.json
```

扩展类位于 `type` 文件夹中（这特定于扩展的名称，即我们通过 `init` 命令指定的名称）。在其中找到一个名为 `StringType.zep` 的文件，用你的编辑器打开它。

Zephir 的语法与 PHP 非常相似，但带有一丝 C 风格。你可以在 [`www.zephir-lang.com/index.html`](http://www.zephir-lang.com/index.html) 找到相关文档。

创建以下类：

```zephir
1 namespace Type;
2 
3 class StringType
4 {
5   protected data;
6 
7   public function __construct(var data)
8   {
9     let this->data = data;
10   }
11 
12   public function length()
13   {
14     return strlen(this->data);
15   }
16 }
```

除了缺少 `$` 符号以及增加了 `var`/`let` 关键字外，这非常容易理解。保存文件并（从扩展根目录）运行：



执行`zephir build`命令：

```
$ zephir build

Compiling...
/bin/bash /vagrant/zephir/type/ext/libtool --mode=compile gcc  -I. -I/vagrant/zephir/type/ext -DPHP_ATOM_INC -I/vagrant/zephir/type/ext/include -I/vagrant/zephir/type/ext/main -I/vagrant/zephir/type/ext -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib  -DHAVE_CONFIG_H  -O2 -fvisibility=hidden -Wparentheses -flto -c /vagrant/zephir/type/ext/stringtype.zep -o type/stringtype.lo...
```

扩展类文件编译为纯 C 代码，并添加类加载代码。构建的最后可能类似于：

```
Installing...
Extension installed!
Add extension=type.so to your php.ini
Don't forget to restart your web server
```

我们需要将其添加到`php.ini`文件中：

```
$ sudo bash -c "echo extension=type.so >> /etc/php5/cli/php.ini"
```

这将安装我们刚刚创建的`Type`扩展。我们可以通过运行以下命令检查它是否已安装：

```
$ php -i | grep "type => enabled"

type => enabled
```

如果你看到了这一行，说明扩展已安装并准备就绪。

使用这个新扩展非常简单：

```php
<?php

$string = new Type\StringType("Hello World");

print $string->length();
```

命名空间和类完全位于编译扩展文件中。Zephir 扩展可以使用现有的核心和扩展命名空间/类。它可以被纯 PHP 代码使用（只要在在使用时已注册）。

## 结论

扩展极大地简化了我们的工作，因为它处理了如装箱和解箱等问题。

## 设计

### 使用何种方法

我们已经决定使用命名空间函数作为基础，因此需要决定如何在类内部使用这些函数。

#### 解析类型

在类型方法中，我们经常需要解析类型。任何参数都可能是错误的类型。将类型解析/转换函数放在自己的命名空间中是合理的：

* `Type\isString`
* `Type\isStringObject`
* `Type\isExpression`
* …
* `Type\toStringObject`
* `Type\toExpression`
* …

我们应该代理到创建方法：

```php
class StringObject extends SPLString
{
  public function trim($mask = "\t\n\r\0\x0B")
  {
    $isString       = Type\isString($mask);
    $isStringObject = Type\isStringObject($mask);

    if ($isString or $isStringObject) {
      if (Type\isExpression($mask)) {
        $raw = Type\String\trimWithExpression(
          $this,
          $mask
        );
      } else {
        $raw = Type\String\trimWithString(
          $this,
          $mask
        );
      }

      return Type\toStringObject($raw);
    }

    throw new LogicException("mask is not a string");
  }
}
```

## 链式调用

我们所采用的面向对象方法的好处之一是我们可以对类型进行链式调用。你可能已经注意到它是如何实现的（参考上一个示例），但万一你没：

```php
return Type\toStringObject($raw);
```

操作方法应该返回原始的 PHP 类型 - 因为我们希望人们能够交替使用这些类型。因此，轮由类（代理）将原始 PHP 类型封装在`SPL Types`中。

## 合并数字类型

我已经提到过我对单一数字类型的愿望，而这正是我想要在这里实现的。出于这个原因，我们将完全忽略`SPLNumber`类，转而使用`SPLFloat`。

原因很简单 - 数字应该能够处理小数点，而不需要额外的一组方法或额外的心理负担。这将导致数值操作中产生额外的类型转换，但并不是世界末日。

## 如何测试

测试是取代原生类型处理系统的至组成部分。好消息是，这很容易！

### PHPUnit

PHPUnit 是一个单元测试库，它让测试小型代码单元的过程变得超级简单：

```php
class StringObjectTest extends PHPUnit_Framework_TestCase
{
  /** @test */
  public function trimWorksWithStrings()
  {
    $subject = Type\toStringObject("Hello World...");

    $this->assertEquals(
      "Hello World",
      $object->trim(".")
    );
  }
}
```

这种测试可以使用许多测试框架完成。归根结底，只要你在编写测试，使用哪种测试框架由你决定。

### 应该测试什么？

简短的答案是：一切。

我们的目标是构建一些稳固的东西，而且它是非常底层的。这意味着我们需要确保事情继续按照预期工作。考虑到我们将制作的方法是多么简单，这甚至并不难。

我们应该力求对命名空间下的函数有有良好的覆盖率，并编写几个测试以确保它们从（代理）类中被正确调用。

### 什么时候应该编写测试？

这真的取决于你。也许你想先写测试，并遵循“红-绿-重构”循环。也许你想先写完所有的库代码，然后确保一切都按照你预期的方式运行（通过为库代码编写测试）。

重要的一是编写测试。

### 建议

我强烈推荐以下书籍：

* [Robert C. Martin 写的《Clean Code》](http://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)
* [Chris Hartjes 写的《The Grumpy Programmer’s PHPUnit Cookbook](https://leanpub.com/grumpy-phpunit)

## 如何打包

如果你希望你的代码被（他人）使用，那么明智的做法是将其打包，让别人也想使用它。

### 创建一个`Readme`文件

这听起来很简单，但你会对实际上有多少开发者在做这件事感到惊讶！当其他开发者偶然发现你的仓库（在 Github/BitBucket 等地方）时，如果他们看到的只有一个空空目录结构而空无一物，他们不会印象深刻。

创建一个`Readme`文件，并包含以下内容……

### 几个示例

展示你的库能做什么。没有什么比更令人沮丧的，被某些营销吸引（去了解更多某个库），结果却不得不从测试和/或源代码中去搞清楚。

那些地方是学习的绝佳场所，但它们必须主动寻找，而几个示例（在你的`Readme`文件中）是很容易找到。包含涵盖你库主要方面的示例。

在我们的情况下，这意味着提供一个或两个关于支持库的底层过程代码示例。这意味着提供一个或两个关于面向对象封装的示例，它们为传统的过程化操作提供了流式接口。这意味着提供一个或两个关于如何子类这些类型以进一步自定义的示例。

制作这些并不难 - 甚至可以从你的单元测试中提取……

### 测试说明

开发者想知道你的代码有多稳固。诚然你使用了 [SemVer](http://semver.org)，但你的测试覆盖率是多少？你的测试通过了吗？我可以信任你吗？

回答这些问题最简单的方法是编写单元测试，然后提供如何运行它们的说明。你不需要任何复杂的配置：

```bash
composer install && phpunit
```

### 安装说明

好了 - 你已经说服了某人使用经过良好测试的库。示例提供了它的价值。那么他们如何安装你的库呢？

这就是你创建一个`composer.json`文件并包含 Composer 安装说明的地方。这需要去 [Packagist](https://packagist.org) 转一圈，但这样做会让你受益匪浅。

然后只需要一组简单的指令即可：

```bash
composer require "vendor/library:1.0.0"
```

### 许可证

包含一个开源许可。像 [MIT](http://opensource.org/licenses/MIT) 这样友好的许可就可以。在你的`Readme`文件中指定，并包含一个命名清晰的文件（如`LICENSE`或`license.md`），其中包含完整的许可内容。

### 贡献指南

这是可选的，但它大大增加了其他开发者发送兼容拉取请求的概率。如果你对代码风格很挑剔（你应该是这样的），请务必告诉人们你希望他们的提交看起来像什么样。

### 总结

构建一个新的类型系统部分是关于代码。制作良好的库包含了大量的设计考虑。花时间决定一个合理的结构 - 一个能让使用者获得最大灵活性的结构。

良好测试。良好打包。清晰。

## 为未来设计

本章节尚未完整。

## 附录

### PHP 实现

此部分尚未完整。

### Zephir 实现

此部分尚未完整。

### JavaScript 实现

此部分尚未完整。
