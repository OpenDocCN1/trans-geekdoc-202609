
"{$this->price}.<br>\n";
} );

class FrozenPizza extends FrozenFood {
    var $toppings;
    function DescribeToppings() {
        print "This pizza has ({$this->toppings})";
        print " on it.<br>\n";
    }
}

$pizza = new FrozenPizza();
$pizza->price = 4.53;
$pizza->toppings =
    "pepperoni sausage anchovies";
$pizza->Describe();
$pizza->DescribeToppings();
?>

这个示例创建了一个名为 FrozenFood 的类，其中包含两个成员：一个名为 $price 的变量和一个名为 Describe 的函数。接下来，这段代码创建了一个名为 FrozenPizza 的新类，使用 extends 关键字从 FrozenFood 派生。因为 FrozenPizza 是从 FrozenFood 派生的，所以 FrozenPizza 拥有与 FrozenFood 相同的成员（$price 和 Describe），以及 FrozenFood 为自己定义的任何成员（$toppings 和 DescribeToppings）。在随后的代码中，你可以看到类 FrozenPizza 的对象 $pizza 确实拥有所有四个成员：$price、$toppings、Describe 和 DescribeToppings。

当派生一个新类时，你可以自由重写基类的任何成员函数。例如，我可以向 FrozenPizza 类添加一个新的 Describe 函数，如下所示：

```
class FrozenPizza extends FrozenFood {
    var $toppings;
    function DescribeToppings() {
        print "This pizza has ({$this->toppings})";
        print " on it.<br>\n";
    }

    function Describe() {
        print "This is a pizza!<br>\n";
        FrozenFood::Describe();
        $this->DescribeToppings();
    }
}
```

此类现在有其自己的 Describe 函数，而基类 FrozenFood 也提供了一个 Describe 函数。假设你有如下代码：

```
$pizza = new FrozenPizza();
$pizza->price = 4.53;
$pizza->toppings =
    "pepperoni sausage anchovies";
$pizza->Describe();
```

PHP 处理器将运行哪个版本的 Describe？它将运行 FrozenPizza 类中的那个，因为该对象的类型是 FrozenPizza。

你可以在 FrozenPizza 类的 Describe 代码中看到，我使用了一个有趣的结构：

```
FrozenFood::Describe();
```

这一行调用 FrozenFood 类中 Describe 的基类版本。

## 获取类的信息

PHP 库包含一组实用函数，可帮助你获取有关对象和类的信息。以下列表介绍了一些更有用的函数：

- **get_object_vars**：此函数返回对象中变量的关联数组。键是变量的名称，数组值是变量的值。要使用此函数，请传递对象的变量名。

- **get_class**：这将返回一个包含类名的字符串。要使用此函数，请传递对象的变量名。

- **get_parent_class**：这将返回一个包含基类名的字符串。要使用此函数，请传递对象或类名。（要传递类名，_不要_ 将名字放在引号中。）

- **get_class_methods**：这将返回一个类的成员函数数组。有些人喜欢将成员函数称为 _methods_，因此这个函数的名字如此。

- **get_declared_classes**：此函数返回 PHP 处理器所知道的所有类的名称数组。该数组包含你声明的任何类，加上任何内置类。

你可以通过访问 www.php.net/classobj 探索其他类和对象函数。

以下是一个示例程序，演示如何使用这些函数：

```
<?php
class Base {
    var $basevar;
    function BaseFunc() {
        print "Hello!<br>\n";
    }
}
class Derived extends Base {
    var $derivedvar;
    function DerivedFun() {
        print "Greetings!<br>\n";
    }
}
$obj = new Derived();
$obj->basevar = 10;
$obj->derivedvar = 20;
$objs = get_object_vars($obj);
print "The object belongs to class <b>";
print get_class($obj)."</b><br>\n";
print "The base class is <b>";
print get_parent_class($obj)."</b><br>\n";
print "Object's Variables<br>\n";
foreach ($objs as $name=>$var) {
    print " * $name = $var<br>\n";
}
print "Base class has these functions<br>\n";
$basemethods = get_class_methods(Base);
foreach ($basemethods as $method) {
    print " * $method<br>\n";
}
print "Here are all the classes defined:<br>\n";
$allclasses = get_declared_classes();
foreach ($allclasses as $classname) {
    print " * $classname<br>\n";
}
?>
```

以下是该程序的输出：

该对象属于类 <b>derived</b><br>
基类是 <b>base</b><br>
对象的变量<br>
* basevar = 10<br>
* derivedvar = 20<br>
基类具有这些函数<br>
* basefunc<br>
以下是所有定义的类：<br>
* stdClass<br>
* __PHP_Incomplete_Class<br>
* Directory<br>
* COM<br>
* VARIANT<br>
* base<br>
* derived<br>

如你所见，除了你创建的类之外，PHP 在其内部机制中还定义了一些类。

## 第 10 章：增强你网站的十种方法

### 本章内容

- 将 index.html 重定向到 index.php
- 动态生成样式表
- 允许文件上传
- 在适当的时候使用 POST
- 随机生成每日图片
- 从文件写入文本
- 确定正在运行的浏览器
- 从 IP 地址确定主机名

在本章中，我将为你提供十种使用 PHP 增强网站的绝妙方法。请继续阅读！

### 将 index.html 重定向到 index.php

文件名 index.html 通常是 Web 服务器中的默认文件。如果访问者只使用网站名称（例如 www.dummies.com）访问你的网站，服务器默认会提供 index.html。但是，如果你的索引文件中包含 PHP 代码怎么办？你可能想改用 index.php。

将 index.html 重定向到 index.php 的最简单方法是配置 Apache，使其默认发送 index.php 文件。如果你有权访问根 httpd.conf 文件，可以为整个服务器设置配置。如果你使用的是第三方托管服务，你的域名映射到文件系统上的一个目录（很可能是你自己的 public_html 目录）。在这种情况下，你需要使用 .htaccess 文件。

无论你使用 .htaccess 还是根 httpd.conf 文件，都可以将以下指令输入到 .htaccess 或 httpd.conf 文件本身中：

```
DirectoryIndex index.php
```

请记住，有些访问者可能会继续手动输入 index.html（如果他们使用互联网很长时间）。如果那些人输入 index.html 这样显而易见的内容却看到 404：未找到文件 错误消息，他们会感到沮丧。前面的重定向无济于事，因为访问者不仅输入了域名，还输入了 index.html。因此，我还建议你包含一个带有重定向的 index.html 文件。唯一的棘手之处是，你无法在 PHP 中执行此重定向，因为 index.html 具有 .html 扩展名，因此不会经过 PHP 处理器。（因此又回到了你最初想使用 index.php 的想法。哎呀。）你需要的完整 index.html 文件如下：

```
<html><head><title>Redirect!</title>
<meta http-equiv="Refresh" content="0; URL=index.php">
</head></html>
```

HTML Refresh 元标签会导致浏览器立即加载 index.php 文件。

![](img/3f967ab8a8fddc723173059f56621648_505_0.png)

如果你是 Unix 爱好者，可能听说过可以使用符号链接来实现重定向。我尝试使用以下代码：

```
ln -s index.php index.html
```

我的担忧得到了证实：虽然重定向有效，但该文件不会经过 PHP 处理器。Apache 服务器不知道它实际读取的文件是 index.php。Apache 只需打开 index.html，操作系统会悄悄地将 index.php 的数据提供给 Apache；Apache 不知道这是一个符号链接。Apache 将文件作为 .html 文件发送到浏览器，因为那是 index.html 的扩展名。那么发送到浏览器的是什么？你的所有 PHP 代码。所以不要使用符号链接，因为它不能按你想要的方式工作。

### 显示当前时间

有些人喜欢在网页上显示当前时间。但是，如果你有一个静态 HTML 页面，你输入的任何时间都会很快过时。为避免此问题，你可以使用 PHP。

以下是一个简短的 .php 文件，用于显示当前时间：

```
<html><head><title>Welcome</title></head>
<body>
Welcome to my Web page!
It is
