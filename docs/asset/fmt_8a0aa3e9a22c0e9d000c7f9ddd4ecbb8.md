
```php
class HiClass {

  function show($sampleCount)

  {

    for ($a = 0; $a < $sampleCount; $a++) {

      print “Hi, how are you?\n”;

    }

    return $sampleCount;

  }

}

class HiDelegator {

  function __construct()

  {

    $this->object = new HiClass();

  }

  function __call ($sampleMethod, $sampleArguments)      

  {

    return call_user_func_array(array ($this->object , $sampleMethod) ,

    $sampleArguments;

  }

  private $sampleObject;

}

$sampleObject = new HiDelegator();

print $sampleObject->show(5);
```

如果你运行此脚本，你的屏幕将显示：

```
Hi, how are you?

Hi, how are you?

Hi, how are you?

Hi, how are you?

Hi, how are you?

5
```

名为 `call_user_func_array()` 的函数允许 `__call()` 原型将调用和参数传递给 `HiClass::show()`。除了将调用中继给另一个对象外，你还可以从 `__call()` 方法原型返回值。

#### 如何重载数组访问语法

程序员通常在程序框架中拥有值或键的映射（也称为“查找字典”）。这就是 PHP 提供关联数组的原因。基本上，关联数组将字符串和整数值映射到其他 PHP 支持的值。您已在前一章中了解过它。为了帮助您记住这个概念，这里有一个使用数组搜索用户 SSN 的代码片段：

```php
print "Mike's SSN is " . $sampleMap["Mike"];
```

如果用户拥有所有所需信息，关联数组将变得极其有用。但是，如果您处理数百万数据库条目，将整个数据库加载到 `$sampleMap` 关联数组中以搜索单个用户是不切实际的。此时，您应该创建一个新方法，通过数据库调用来搜索该人的 SSN。您可以使用这种方法重写上面给出的代码片段。新代码将如下所示：

```php
print "Mike's SSN is " . $database->LocateSSN("Mike");
```

这种方法工作完美。然而，许多程序员在访问值/键字典时选择使用关联数组语法。因此，PHP 允许您重载对象，使其表现得像典型数组一样。您可以使用关联数组的语法，但实际上 PHP 将调用您编写的方法，该方法将运行适当的数据库调用并检索所需数据。

您想用于访问值/键字典的方法取决于您自己。在某些情况下，利用 PHP 的重载能力比通过冗长的代码调用方法更好。最终，您应该使用的方法取决于您的需求和偏好。

#### 迭代器

您可以使用 `foreach()` 循环来迭代对象的属性。这是一个示例：

```php
class YourClass {
    public $personName = "Mike";
    public $personSex = "male";
}

$object = new YourClass();

foreach ($object as $sampleKey => $sampleValue) {
    print "object [$sampleKey] = $sampleValue\n";
}
```

此脚本输出以下信息：

```text
object [sampleName] = Mike
object [sampleSex] = male
```

然而，在编写面向对象脚本时，您的类可能不表示像上面那样的基本数组。您的代码可能包含复杂信息，例如配置文件或数据库查询。

PHP 语言允许您在代码内部重载 `foreach()` 迭代的行为。这意味着您可以根据程序的需要使用 `foreach()` 语句。

#### 设计模式

在设计程序时，您会遇到某些问题。专家程序员已经解决了其中一些问题，这些解决方案被称为“设计模式”。基本上，设计模式为程序员提供了一种通用的程序设计方法。您可能听过应用程序开发人员说：“这个项目需要单例模式。”在本书的这一部分，您将了解最重要的设计模式。请仔细阅读这些材料——它们将帮助您在 24 小时内学会 PHP。

##### 策略模式

当程序员需要一种可以与不同变体互换的算法时，会使用此模式。例如，如果您的代码生成图像，您可能现在想生成 GIF 文件，稍后想生成 JPEG 文件。

通常，程序员通过使用基于算法的方法声明一个基类来实现此模式。程序将通过继承一个或多个具体类来实现此方法。在代码的某处，程序员将决定必须使用哪个具体策略。PHP 将实例化该策略，并在适当的地方使用它。

下面给出的示例展示了下载服务器如何根据访问它们的 Web 浏览器选择文件选择方案。在生成包含下载按钮的 HTML 时，它将根据 Web 浏览器的操作系统（即 OS）标识生成指向 `.zip` 或 `.tar.gz` 文件的链接。为保持简单，假设当 `$_SERVER["HTTPS_USER_AGENT"]` 中存在“Win32”时，您正在使用 Windows 计算机，需要生成 `.zip` 下载链接；否则，您正在使用需要 `.tar.gz` 链接的计算机系统。

此示例涉及两种不同的策略：`.zip` 和 `.tar.gz`。分析以下代码：它将向您展示如何编写有效的策略模式：

```php
abstract class FileSelectionStrategy {
    abstract function generateLink($nameOfFile);
}

class ZipStrategy extends FileSelectionStrategy {
    function generateLink($nameOfFile) {
        return "https://downloads.samplesite.com/$nameOfFile.zip";
    }
}

class TarGzStrategy extends FileSelectionStrategy {
    function generateLink($nameOfFile) {
        return "https://downloads.samplesite.com/$nameOfFile.tar.gz";
    }
}

if (strstr($_SERVER["HTTPS_USER_AGENT"], "Win32")) {
    $selectionObject = new ZipStrategy();
} else {
    $selectionObject = new TarGzStrategy();
}

$mark_filename = $selectionObject->generateLink("Marketing101");
$sales_filename = $selectionObject->generateLink("Sales101");

print <<<EOF
<h1>These free eBooks will help you become a better entrepreneur</h1>
<br>
<a href="$mark_filename">An eBook that focuses on marketing</a><br>
<a href="$sales_filename">An excellent resource for sales-related concerns</a><br>
<br>
EOF;
```

如果您使用 Windows 机器访问此脚本，将获得以下输出：

```html
<h1>These free eBooks will help you become a better entrepreneur</h1>
<br>
<a href="https://downloads.samplesite.com/Marketing101.zip">An eBook that focuses on marketing</a><br>
<a href="https://downloads.samplesite.com/Sales101.zip">An excellent resource for sales-related concerns</a><br>
<br>
```

##### 单例模式

这是软件设计中最流行的模式之一。程序员经常遇到这样的情况：他们拥有处理程序中某些集中操作的对象（例如记录器对象）。在这些情况下，程序员倾向于通过创建一个程序范围内的实例来保持简单，该实例可以被源代码的任何部分访问。特别是在处理记录器对象时，您需要应用程序的每个部分都能访问该实例，并允许记录机制根据日志级别配置管理日志消息。单例设计模式是应对这种情况的最佳选择。

您可以通过实现 `getInstance()` 将类转换为单例类。基本上，`getInstance()` 是一个静态方法，返回类的唯一实例。如果您第一次调用此方法，它将生成一个实例，将其保存在静态变量中，并将该实例返回给您。后续对 `getInstance()` 方法的调用将返回之前创建的实例的句柄。分析以下示例：

```php
class SampleLogger {
    static function getInstance() {
        if (self::$sampleInstance == NULL) {
            self::$sampleInstance = new SampleLogger();
        }
        return self::$sampleInstance;
    }

    private function __construct() {
    }

    private function __clone() {
    }

    function Log($sampleString) {
        // This code takes care of log-related processes.
    }

    static private $sampleInstance = NULL;
}

SampleLogger::getInstance()->Log("Check");
```

这段代码的重要部分是 `SampleLogger::getInstance()`。这部分允许您从代码的任何部分访问“记录器”。

对于此应用程序，“clone”和“constructor”被标记为私有方法。这种方法确保程序员不会错误地创建 `SampleLogger` 类的另一个实例。简单来说，`getInstance()` 是您访问该类实例的唯一途径。

##### 工厂模式

在面向对象编程中，多态性和基类利用发挥着重要作用。

基类包含子类，有时需要创建具体的实例。在 PHP 中，程序员使用一种称为“工厂”的设计模式来创建所需的子类。工厂类具有一个接受输入的方法。根据提供的输入，这些类将决定生成哪种类型的实例（通常是子类）。

假设您的网站允许不同类型的用户登录。其中一些人是访客，一些是客户，还有一些是管理员。在这种情况下，大多数程序员将创建一个基类和三个子类。您可以将基类命名为 `Users`。然后，您可以将子类命名为 `Visitors`、`Customers` 和 `Admins`。基类及其所有子类将包含收集用户相关数据的方法（例如用户的个人偏好以及他/她可以访问的在线资源）。

您可以在任何可能的情况下使用 `Users` 基类来创建一个健壮的网站。这样，您可以泛化您的源代码，并简化新用户类型的添加。

##### 观察者模式

使用 PHP 创建的程序会操作信息。在大多数情况下，对某条信息的修改会影响程序源代码的不同部分。例如，如果一位来自亚洲的客户访问 eBay 的美国站点，汇率将影响他/她屏幕上看到的价格。

假设每个编程对象代表一个 eBay 产品。代码中使用的对象直接来自 eBay 的数据库。另一方面，汇率可能来自外部数据源，且不保存在数据库中。每个对象都包含 `display()` 方法，该方法返回与产品相关的 HTML 内容。

“观察者”设计模式允许对象注册以接收特定信息和/或事件。当信息发生变化或事件发生时，PHP 将通知已注册的对象。通过这种方法，您可以将产品项标记为汇率的观察者。此外，您可以在打印项目列表之前，更新已注册编程对象关于汇率的信息。这意味着每个对象都可以更新自身，并在其 `display()` 方法中包含新信息。

通常，PHP 用户通过一个称为“观察者”的接口来实现观察者模式。需要充当观察者的类应实现此接口。

一个“可观察”对象通常有一个名为 `register` 的方法，它允许“观察者”（即接口）自动注册。

### 第 7 章：使用 PHP 创建应用程序

人们使用 PHP 构建网站。这种计算机语言允许程序员制作动态 Web 应用程序。动态应用程序通过 HTML 表单从用户处收集数据。从用户处获得并保存在网站中的数据是机密的，这使得安全性成为一个严重的关注点。PHP 语言具有允许您安全获取和存储数据的功能。PHP 拥有您所需的一切：您只需利用该语言提供的功能来开发应用程序。在本章中，您将学习如何使用 PHP 构建动态 Web 应用程序。

#### PHP 和 HTML

您不必将 PHP 代码嵌入 HTML 文件中。您始终可以生成不包含任何 HTML 元素的 PHP 文件。然而，在创建 Web 应用程序时，您很可能会在单个文件中结合使用这两种语言。计算机专家说 PHP 是为网站而创建的，用作 HTML 文档的模板。一旦您向文件中添加 PHP，该文件将获得 “.php” 或 “.php5” 作为其扩展名。

下面的代码展示了如何结合 PHP 和 HTML：

```html
<html>
<head><title>First Sample</title></head>
<body>
<?php
  // This code has a data-based “if” statement.
  if (date('md' == '1225')) {
    echo 'Merry Christmas '
      'and Happy New Year';
  } else {
    echo 'Hi, how are you?';
  }
?>
</body>
</html>
```

在本例中，`<?php` 部分标志着嵌入式 PHP 代码的开始。另一方面，`?>` 部分表示 PHP 代码的结束。您可能注意到，此示例通过 `echo` 发送输出。如果您处理的是如上所示的简单代码，这种方法是可以接受的。但是，如果您在包含单引号/双引号的字符串上使用 `echo`，您的代码将变得极其复杂。

如果回显的文本是链接（例如 `<a href='https…'>`），此示例将导致错误。这是因为回显文本中的引号将与包围字符串的引号发生冲突。在这种情况下，您可以在处理文本输出前结束 PHP 部分。然后，在终止“if”语句的代码之前重新开始。这是一个例子：

```html
<html>
<head><title>Second Sample</title></head>
<body>
<?php
  // This code contains a date-based “if” statement.
  if (date('md' == '1225')) {
    echo 'Merry Christmas and ' . 
      'Happy New Year!';
  } else {
    echo 'Hi, how are you?';
  }
?>
</body>
</html>
```

这种编写代码的风格令人困惑。它违反了一个重要的编程原则：“不要混合内容和逻辑。” 下面给出的嵌入风格使用变量来存储字符串并回显该变量：

```php
<?php
  // This code contains a date-based “if” statement.
  if (date ('md' == '1225') ) {
    $message = 'Merry Christmas and Happy New Year!”;
  } else {
    $message =   'Hi, how are you?';
  }
?>

<html>
<head><title>Third Sample</title></head>
<body>
<?php echo $message; ?>
</body>
</html>
```

#### 用户输入

在学习如何在 HTML 文件中包含 PHP 之后，您应该知道如何设置用户指定的操作。例如，一个在线书店需要注册和登录系统。显然，用户需要执行一个操作（例如输入登录凭据）才能“进入”在线商店。这种类型的系统需要基于 HTML 的表单和一个存储来保存收集到的数据。

对于此示例，您在注册过程中需要从每个用户那里获取几项信息。这些是：姓名、密码和电子邮件地址。分析以下 HTML 代码：
