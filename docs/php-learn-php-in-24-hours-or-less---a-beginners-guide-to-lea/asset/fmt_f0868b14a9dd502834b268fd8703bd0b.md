
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

## 迭代器

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

## 设计模式

在设计程序时，您会遇到某些问题。专家程序员已经解决了其中一些问题，这些解决方案被称为“设计模式”。基本上，设计模式为程序员提供了一种通用的程序设计方法。您可能听过应用程序开发人员说：“这个项目需要单例模式。”在本书的这一部分，您将了解最重要的设计模式。请仔细阅读这些材料——它们将帮助您在 24 小时内学会 PHP。

### 策略模式

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

### 单例模式

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

### 工厂模式
