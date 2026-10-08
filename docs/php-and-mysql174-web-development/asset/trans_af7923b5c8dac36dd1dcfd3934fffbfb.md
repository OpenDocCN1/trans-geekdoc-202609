

# 列表 7.1 basic_exception.php—抛出与捕捉异常

```php
<?php
try {
    new Exception("A terrible error has occurred", 42);
}
catch (Exception $e) {
    echo "Exception: " . $e->getCode() . ": " . $e->getMessage() . "<br />";
    echo "in " . $e->getFile() . " on line " . $e->getLine() . "<br />";
}
?>
```

在列表 7.1 中，你可以看到我们使用了 Exception 类的中的几个方法，我们稍后会讨论这些方法。运行此代码的结果如图 7.1 所示。

![](img/654520c37415debd4290b9b4aa2c03f2_232_0.png)

在示例代码中，你可以看到我们抛出了 `Exception` 类的异常。这个内置类包含了一些可以在 `catch` 块中使用的方法，用于报告有用的错误信息。

# Exception 类

PHP 有一个内置类 `Exception`。构造函数接受三个可选参数，正如我们之前讨论过的样：错误消息、错误代码以及上一个异常。

除了构造函数外，该类还带有以下内置方法：

- getCode()—返回传递给构造函数的代码
- getMessage()—返回传递给构造函数的错误消息
- getFile()—返回抛出异常的代码文件的完整路径
- getLine()—返回抛出异常的代码文件中的行号
- getTrace()—返回一个包含异常抛出处回溯轨迹的数组
- getTraceAsString()—返回与 `getTrace` 相同的信息，但格式化为字符串
- getPrevious()—返回上一个异常（来自构造函数的第三个参数）
- __toString()—允许你 `echo` 一个 Exception 对象，从而提供上述所有信息

你可能已经在列表 7.1 中使用了这些方法中的前四个。你可以通过执行 `echo $e;` 来获取相同的信息（加上回溯轨迹）。

回溯轨迹显示了在异常抛出时正在执行哪些函数。

# 用户自定义异常

与其实例化并传递基类 `Exception` 的实例不同，你可以传递任何你自定义的其他对象。在大多数情况下，你会扩展 `Exception` 类来创建你自己的异常类。

你可以在 `throw` 子句中传递任何其他对象。如果你在处理某个特定对象时遇到问题，并想为了调试目的将其传递出去，偶尔可能需要这样做。

在大多数时候，你需要扩展基类。PHP 手册提供了显示 `Exception` 类骨架的代码。这段代码取自 http://php.net/manual/en/exceptions.php，并复制于列表 7.2 中。请注意，这不是全部代码，但它代表了你可以继承的内容。

# 列表 7.2 Exception 类—这是你可以继承的内容

```php
<?php
class Exception
{
    protected $message = 'Unknown exception'; // 异常消息
    private $string; //
    protected $code = 0; // 用户定义的代码
    protected $file; // 源文件名
    protected $line; // 源行号
    private $trace; // 回溯轨迹
    private $previous; // 嵌套时的上一个异常

    public function __construct($message = null, $code = 0, Exception $previous = null);

    final function __clone(); // 禁止异常克隆。
    final function getMessage(); // 异常消息
    final function getCode(); // 异常代码
    final function getFile(); // 源文件名
    final function getLine(); // 源行号
    final function getTrace(); // 回溯轨迹数组
    final function getPrevious(); // 上一个异常
    final function getTraceAsString(); // 格式化后的轨迹字符串

    /* 重写 */
    public function __toString(); // 用于显示的格式化字符串
}
?>
```

我们查看此类的主要原因是为了注意大多数公共方法都是 `final`（最后的）：这意味着你不能重写它们。你可以创建自己的子类，但不能更改基础方法的行为。注意，你可以重写 `__toString()`，因此你可以更改异常的显示方式。你也可以添加自己的方法。

列表 7.3  own了一个用户自定义类的示例。

# 列表 7.3 user_defined_exception.php—用户自定义类的示例

```php
<?php

class myException extends Exception
{
    function __toString()
    {
        return "Exception " . $this->getCode() .
        ": " . $this->getMessage() . "<br />"
        ."in " . $this->getFile() . " on line " . $this->getLine() . "<br />";
    }
}

try {
    throw new myException("A terrible error has occurred", 42);
}
catch(myException $m) {
    echo $m;
}
?>
```

在这段代码中，你声明了一个新的异常类 `myException`，它扩展了基础 `Exception` 类。这个类与 `Exception` 类的区别在于重写了 `__toString()` 方法以提供异常的“美化”打印。执行此代码的输出如图 7.2 所示。如你所见，它与之前的示例相似。

![](img/654520c37415debd4290b9b4aa2c03f2_235_0.png)

图 7.2 Exception 类提供了带美化打印的异常

这个示例非常简单。在下一节中，我们将查看如何创建不同的异常来处理不同类别的错误。

# Bob 的汽车零件中的异常

第 2 章“存储和检索数据”描述了你如何将 Bob 的订单数据存储在平面文件中。你知道 I/O（实际上是任何类型的 I/O）是程序中经常发生错误的领域之一。这是一个应用异常处理的好地方。

回溯原始代码，你可以看到写入文件时可能出现三个问题：文件无法打开、无法获取锁或无法写入文件。我们为每种可能性都创建了一个异常类。每种可能的代码如列表 7.4 所示。

# 列表 7.4 file_exceptions.php—与 I/O 相关的异常

```php
<?php
class fileOpenException extends Exception
{
    function __toString() {
        return "fileOpenException " . $this->getCode() .
        ": " . $this->getMessage() . "<br />"
        "in " . $this->getFile() . " on line " . $this->getLine() . "<br />";
    }
}
class fileWriteException extends Exception
{
    function __toString() {
        return "fileWriteException " . $this->getCode() .
        ": " . $this->getMessage() . "<br />"
        "in " . $this->getFile() . " on line " . $this->getLine() . "<br />";
    }
}
class fileLockException extends Exception
{
    function __toString() {
        return "fileLockException " . $this->getCode() .
        ": " . $this->getMessage() . "<br />"
        "in " . $this->getFile() . " on line " . $this->getLine() . "<br />";
    }
}
?>
```

这些异常子类并没有做什么特别有趣的事情。事实上，对于此应用程序，你可以让它们为空子类，或者使用提供的 Exception 类。我们为每个子类都提供了 `__toString()` 方法来解释发生了什么类型的异常。

我们重写了第 2 章的 `processor.php` 文件以包含异常的使用。新版本如列表 7.5 所示。

# 列表 7.5 processor.php—包含异常的 Bob 订单脚本

```php
<?php

require_once("file_exceptions.php");

// 创建短变量
$tireqty = (int) $_POST['tireqty'];
$oilqty = (int) $_POST['oilqty'];
$sparkqty = (int) $_POST['sparkqty'];
$address = preg_replace('/tR]/', '', $_POST['address']);
$document_root = $_SERVER['DOCUMENT_ROOT'];
$date = date('H:i, JS F Y');

<!DOCTYPE html>
<html>
<head>
<title>Bob's Auto Parts - Order Results</title>
</head>
<body>
<h1>Bob's Auto Parts</h1>
<h2>Order Results</h2>
<?php
echo "<p>Order processed at " . date('H:i, JS F Y') . "</p>";
echo "<p>Your order is as follows: </p>";

$totalqty = 0;
$totalamount = 0.00;

define('TIREPRICE', 100);
define('OILPRICE', 10);
define('SPARKPRICe', 4);

$totalqty = $tireqty + $oilqty + $sparkqty;
echo "<p>Items ordered: " . $totalqty . "<br> />";

if ($totalqty == 0) {
    echo "You在上一个页面没有订单任何东西!<br /> ";
} else {
    if ($tireqty > 0) {
        echo htmlspecialchars($tireqty).' tires<br> />";
    }
    if ($oilqty > 0) {
        echo htmlspecialchars($oilqty).'bottles of oil<br> />";
    }
    if ($sparkqty > 0) {
        echo htmlspecialchars($sparkqty).'spark plugs<br> />";
    }
}
?>
</body>
</html>
```
