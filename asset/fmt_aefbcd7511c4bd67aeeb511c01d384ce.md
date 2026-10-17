
但如果你希望`$new_variable`和`$old_variable`继续指向同一个值，并且`$new_variable`的更改影响`$old_variable`的值，反之亦然，PHP 4 有一种新机制来支持这种安排：别名（aliases）。

别名是 PHP 4 中引入的新特性。

别名是一个指向另一个变量引用的变量。它没有自己的值，但指向另一个变量的值。在所有其他用途上它就像一个变量；你可以给它赋值，如果它是一个对象，则可以调用它的方法。

```
$alias = &$variable;
```

以下是使用别名和使用变量区别的示例：

```
$variable = "Test String One"
$new_variable = "Test String One"
$alias = &$variable;
echo "Starting values:"
echo $variable;
echo $new_variable;
echo $alias;

$variable = "Changed via Variable"
echo "After changing $variable:"
echo $variable;
echo $new_variable;
echo $alias;

$alias = "Changed via Alias"
echo "After changing $alias:"
echo $variable;
echo $new_variable;
echo $alias;
```

## 552 第三部分 高级技术

你可能想使用别名的三个原因：

1. 为对象存储多个属性。
2. 缩短名称。
3. 防止 PHP 创建额外的副本。

## 显示和打印对象

PHP 4 有两个显示对象的函数：`var_dump` 和 `print_r`。它们的输出略有不同，如果你想将其封装在`<pre>`标签中：

```
echo "<pre>";
var_dump($object);
echo "</pre>";
print_r($object);
echo "</pre>";
```

## 内省

对象是一个数据包。PHP 4 提供了查看所有数据的名称、类型和值的方法。对象可以像数组进行遍历以查找变量。

## 第 30 章 PHP 5-49 中的面向对象编程

### 类型和类内省

表 30-1 到 30-3 列出了 PHP 中最重要的类型、类和变量函数。

关于类型检查的更多详细信息请参阅第 6 章

**表 30-1 布尔类型检查**

| 函数 | 行为 |
|---|---|
| `is_array($var)` | 如果`$var`是数组则返回 true。 |
| `is_int($var)` | 如果`$var`是整数则返回 true。注意：PHP 4 不区分整数和长整数。 |
| `is_integer($var)` | 如果`$var`是整数则返回 true。注意：PHP 4 不区分整数和长整数。 |
| `is_long($var)` | 如果`$var`是整数则返回 true。注意：PHP 4 不区分整数和长整数。 |
| `is_float($var)` | 如果`$var`是双精度浮点数则返回 true。注意：PHP 4 不区分浮点数、双和实数。 |
| `is_real($var)` | 如果`$var`是双精度浮点数则返回 true。注意：PHP 4 不区分浮点数、双和实数。 |
| `is_double($var)` | 如果`$var`是双精度浮点数则返回 true。注意：PHP 4 不区分浮点数、双和实数。 |
| `is_numeric($var)` | 如果`$var`是整数或双精度浮点数或包含二者的字符串则返回 true。 |
| `is_string($var)` | 如果`$var`是字符串则返回 true。 |
| `is_object($var)` | 如果`$var`是对象则返回 true。 |
| `class_exists(string)` | 如果 string 是预定义类或用户定义类名则返回 true。 |

## 554 第三部分 高级技巧

**表 30-1 (续)**

| 函数 | 行为 |
| --- | --- |
| `empty($var)` | 如果`$var`是一个未设置且未使用的变量名，或者其值为零（如 0 或 "0"），则返回 true。 |
| `isset($var)` | 如果`$var`是一个未设置且未使用的变量名，则返回 true。 |

**表 30-2 类型与类函数总结**

| 函数 | 行为 |
| --- | --- |
| `gettype($var)` | 返回表示`$var`类型的字符串，即 "string""object" 或 "double"。 |
| `setype($var)` | 尝试将`$var`的类型强制转换为 "array""double""integer""object" 或 "string"。此函数可能会产生违反直觉的结果，因此在使用前请进行测试。 |
| `doubleval($var)` | 返回一个由`$var`的值决定的双浮点数；例如 "0.045" 变为 0.045，6 变成 6.0。此函数不适用于数组或对象。 |
| `intval($var)` | 返回一个由`$var`的值决定的整数；例如 "45" 变为 4，4.0 变成 4。请小心，`intval`返回的是 int！此函数不适用于数组或对象。 |
| `unset($var)` | 移除指定的变量。该变量将不再可用，调用`isset($var)`将返回 false。 |

**表 30-3 类型与类 I/O 函数总结**

| 函数 | 行为 |
| --- | --- |
| `print_r($var)` | 打印变量或对象的字符串表示 |
| `var_dump($var)` | 打印变量或对象的字符串表示。此函数的输出与`print_r()`的输出略有不同。 |
| `strval($var)` | 返回变量的字符串表示。不列出数组或对象的详细信息。不打印。 |

## 第 30 章 ♦ 使用 PHP 5 面对象编程 555

| 函数 | 行为 |
| --- | --- |
| `serialize($var)` | 返回包括对象在内的变量字节流表示。此输出适用于存储在数据库中或页面间传输。对于某些任务，此流可能需要使用`base64_encode()`进一步编码。 |
| `unserialize($var)` | 返回从`serialize()`函数输出构造的变量。 |

我们将在下文中查看这三个函数：

- `is_object()`
- `gettype()`
- `get_class()`

我们可以将动态查找类变量的能力与类型内省相结合，编写自己的对象显示函数。列表 30-1 显示了两个函数：`display_object()`，它承担了大部分工作；以及`spaceout()`，它是一个辅助格式化内部对象的辅助函数。

`display_object()`函数遍历它接收到的对象，显示每个变量的名称、类型和值。如果变量是一个对象，该函数将带有新对象递归调用自身。这让我们能够看到大多数对象及其内部任何内容的完整深度，但如果对象包含对自身的自身的引用，就会可能出现无限递归的情况！

### 列表 30-1：显示对象

```php
function spaceout($depth) {
    for ($i = 0; $i < $depth*4; $i++)
        echo "&nbsp";
}
function display_object($obj, $depth = 0) {
    if (!is_object($obj)) {
        return;
    }
    if ($depth == 0)
        echo "<b>Printing Object Details:</b><br><br>";
    reset($obj);
```

## 556 第三部分 + 高级技巧

### 列表 30-1 (续)

```php
while list($slot) = each($obj) {
    echo spaceout($depth) . "<b>$slot:</b><br>";
    echo spaceout($depth) . "name: $slot<br>";
    echo spaceout($depth) . "type: " . gettype($slot) . "<br>";
    if (is_object($slot)) {
        echo spaceout($depth) . "class: " . get_class($slot) . "<br>";
    }
    echo spaceout($depth) . "value: ";
    if (gettype($slot) == "string") {
        echo $slot;
    } else if (gettype($slot) == "integer") {
        echo $slot;
    } else if (gettype($slot) == "double") {
        echo $slot;
    } else if (gettype($slot) == "array") {
        print_r($slot);
    } else if (gettype($slot) == "object") {
        echo spaceout($depth) . "<i>Object of class:</i><br>";
        display_object($slot, $depth+1);
        continue;
    }
    echo "<br>";
}
```

包含各种类型变量和内部对象的类：

```php
class walkme {
    var $stringOne = "String One Value";
    var $stringTwo = "String Two Value";
    var $objectOne;
    var $doubleOne;
    var $arrayOne;

    function init() {
        $this->stringOne = "String One Value";
        $this->objectOne = new intro();
        $this->integerOne = 6;
        $this->doubleOne = 6.5;
        $this->arrayOne = array("a","b","c");
    }
}
```

由于我们不能用对象初始化非静态变量，因此必须在实例化对象后设置`$objectOne`的值。在这里，我们通过一个函数这样做以防万一。接下来，我们创建一个对象并通过调度器发送它：

```php
$obj = new walkme();
echo "Created Object\n";
$obj->init();
display_object($obj);
```

这将产生列表 30-2 所示的输出。

### 列表 30-2：显示对象的输出

```
Created Object

Printing Object Details:

stringOne Details:

name: stringOne

type: string

value: String One Value

stringTwo Details:

name: stringTwo

type: string

value: String Two Value

objectOne Details:

name: objectOne

type: object

class: intro

value: Object of class intro

stringOne Details:

name: stringOne

type: string

value: String One Value

stringTwo Details:

name: stringTwo

type: string

value: String Two Value

objectOne Details:

name: objectOne

type: object

class: intro

value: Object of class intro:
```

### 列表 30-3 (续)

```
stringOne Details:
name: stringOne
type: string
value: String One Value
stringTwo Details:
name: stringTwo
type: string
value: String Two Value
integerOne Details:
name: integerOne
type: integer
value: 6
doubleOne Details:
name: doubleOne
type: double
value: 6.5
arrayOne Details:
name: arrayOne
type: array
value: Array ([0] => a [1] => b [2] => c)
```

## 对象序列化

出于几个原因，将对象编码为线性字节序列，然后将该序列解码回对象是有用的。通过这种能力，你可以将对象写入磁盘然后再次读取，或者通过网络传递给另一个程序并在另一端进行重构。这种对象的编码和解码被称为序列化。

PHP 4 提供了两个方便完成此任务的任务：`serialize()`和`unserialize()`。这些函数自动将 PHP 对象处理为可保存的字符串，并将将保存的字符串转换为 PHP 对象。

> 你不能序列化外部对象，例如由 COM 和 Java 扩展接口返回的 COM 或 Java 对象。某些句柄和类型（例如数据库连接句柄）可能无法通过序列化生存。

你可以将序列化的对象保存到文件或数据库中，甚至通过链接从一个页面传递到另一个页面。

```php
if ( isset($in_object) ) {
    $in_object = new walkme();
    echo "下方链接包含一个编码的对象。<br>";
    echo "<a href='session.php4?in_object=base64_encode(serialize($object))'>点击这里</a>";
} else {
    echo "解码并恢复跨 URL 序列化的对象。<br>";
    $out_object = unserialize(base64_decode($in_object));
    echo "<pre>";
    var_dump($out_object);
    echo "</pre><br><br>";
}
```

注意的是，要确保在反序列化时序列化对象的类已经定义。如果未定义，序列化对象的变量将是可，但你将无法调用对象的任何函数。

> 虽然理论上可以通过 GET 和 POST 传递序列化对象，但请注意长度限制可能会截断你的对象。对于 GET 方法尤其如此，因为它只需要容纳 255 个字符。

## 扩展接口：COM、DCOM、Java 和 CORBA

理论上，PHP 4 扩展模块目前提供了连接和操作 COM、DCOM 和 Java 对象的支持。CORBA 在 4.0.0 版本中不受支持，但至少有一个模块在 Orbit ORB 下得到了证明。

PHP 4 支持将外部对象封装为 PHP 4 对象。这些外部对象由模块创建并可以像标准的 PHP 4 对象一样调用。

> COM 和 DCOM 接口仅在 Windows 平台上可用。Java 接口应该在大多数平台上可用。

> 虽然 Java 支持是 PHP 4 发布的一部分，但我们在 PHP 4 Beta 版本中测试 Java 支持时并未成功。请访问我们的网站 http: www.troutworks.com 获取 PHP 4 Java 支持的最新动态。

### COM 和 DCOM

COM 模块支持具有 IDispatch 接口的 COM 和 DCOM 对象。COM 模块是 PHP 4 Win32 二进制发行的一部分。表 30-4 总结了可用的 COM 接口函数。

如果你在 phpini 文件中指定了类型库，PHP 4 就可以识别自动化常量。有关如何操作的最新说明，请参见模块的 README 文件。

支持 DCOM 但默认禁用。要启用 DCOM，请在`php.ini`文件中添加一行：`allow_dcom=1;`。模块会自动在 COM 和 PHP 4 之间转换类型，但它不会转换 PHP 4 对象或数组。

以下是一个使用 COM 与数据库通信的示例。

```php
$db = new COM("ADODB.Connection");
$database_name = "librarians";
$table_name = "librarians";

echo "COM object type: ";
echo gettype($db);
echo <br>necho COM object class: ";
echo get_class($db);
echo <br>necho <br>";
```

```php
$db->Open($database_name,"");

$result = $db->Execute("SELECT 'First Name','Last Name','State' FROM " . $table_name . " order by state ");


echo "New COM object type: ";
echo gettype($result);
echo <br>necho New COM object class: ";
echo get_class($result);
echo <br>necho <br>";
```
