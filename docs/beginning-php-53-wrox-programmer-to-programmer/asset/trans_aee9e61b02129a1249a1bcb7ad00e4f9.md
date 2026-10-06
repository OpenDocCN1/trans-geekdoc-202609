

# 第8 章：对象

## 尝试一下

以下示例展示了如何使用 `__get()` 和 `__set()` 在私有数组中存储“不存在”的属性。这实际上创建了一个可能具有无限数量“虚拟”属性的类，这些属性被安全地存储，与类的任何真实属性隔离开。这种技术对于创建不持有任意数据的类非常有用。

将以下内容保存为 `set_get.php` 并于你的文档根目录中，然后在浏览器中运行它。你应该能看到图 8-3 所示的结果。

```php
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
http://www.w3.org/TR/xhtml/DTD/xhtml-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:en lang="en">
<head>
  <title>Using __get() and __set()</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
  <h1>Using __get() and __set()</h1>
</body>
</html>

<?php
class Car {
  public $manufacturer;
  public $model;
  public $color;
  private $_extraData = array();

  public function __get($propertyName) {
    if (array_exists($propertyName, $this->_extraData)) {
      return $this->_extraData[$propertyName];
    } else {
      return null;
    }
  }

  public function __set($propertyName, $propertyValue) {
    $this->_extraData[$propertyName] = $propertyValue;
  }
}

$car = new Car();
$car->manufacturer = "Volkswagen";
$car->model = "Beetle";
$car->color = "red";
$car->engineSize = 1.8;
$car->otherColors = array("green", "blue", "purple");

echo "<p>My car's manufacturer is " . $car->manufacturer . "</p>";
echo "<p>My car's engine size is " . $car->engineSize . "</p>";
echo "<p>My car's fuel type is " . $car->fuelType . "</p>";
echo "<h2>The $car Object:</h2><pre>";
print_r($car);
echo "</pre>";
?>
```

![](img/ede05b7b77968b82cbd9a513122fb183_223_0.png)

## __get() 和 __set()

某些属性：

- 我的汽车制造商是大众。
- 我的汽车引擎尺寸是 1.8。
- 我的汽车燃料类型是。

The $car 对象：

```text
(
    [manufacturer] => Volkswagen
    [model] => Beetle
    [color] => red
    [_extraData:private] => Array (
        [engineSize] => 1.8
        [otherColors] => Array (
            [0] => green
            [1] => blue
            [2] => purple
        )
    )
)
```

### 它可以工作

该脚本创建了一个熟悉的 Car 类，其中包含了一些固定属性——$manufacturer,$model，并添加了一个私有数组 $_extraData。Car 类还包含一个 `__get()` 方法，该方法会在 $_extraData 数组的键中查找请求的属性名，如果找到，则返回对应的值。

为了测试这些方法，脚本随后创建了一个新的 $car 对象并设置属性。前三个是实际属性——$manufacturer,$model 和 $color——因此这些属性被赋值为“Volkswagen”、“Beetle”和“red”。第四个属性 $engineSize 在类中不存在，因此调用了 `__set()` 方法；这在 $_extraData 中创建了一个值为 1.8 的数组。

同样地，第五个属性 $otherColors 在类中也不存在，因此调用了 `__set()`，在 $_extraData 中创建了一个键为 "otherColors" 的数组，该数组包含了字符串“green”、“blue”和“purple”。

接下来，脚本显示了 $car 对象的某些属性。注意，对于调用代码来说，$engineSize 属性是不存在的。脚本还尝试获取名为 $fuelType 的属性值，但由于该属性在类中或 $_extraData 数组中均不存在，`__get()` 方法向向调用代码返回了 `null`。这就是为什么页面上没有显示任何值的原因。

最后，脚本使用 `print_r()` 输出了 $car 对象的内容。请注意，这些额外的“属性”——$engineSize 和 $otherColors 位于 $_extraData 数组中。（你可以看到 print_r() 显示了对象内部的属性，这对调试很有用。）

尽管这些不存在的属性被存储在私有数组中，但它们也可以被存储在文件或数据库中，或者通过 API（应用程序接口）传递给 `__get()` 和 `__set()`。这让你对这两个方法的威力有了初步了解。

## 使用 __call() 重载方法调用

就像你可以使用 `__get()` 和 `__set()` 来处理属性的读写一样，你也可以使用 `__call()` 来处理类中不存在的方法。在类中创建一个名为 `__call()` 的方法，接收字符串类型的方法名以及以数组形式传递的任何参数。该方法应该向调用代码返回一个值（如果有的话）：

```php
public function __call($methodName, $arguments) {
    // (实现逻辑)
}
```

`__call()` 是非常有用的，当你想要为不存在的方法方法创建一个包装类时。就像你可以使用 `__get()` 和 `__set()` 来处理属性的读写一样，你也可以使用 `__call()` 来处理类中不存在的方法。在类中创建一个名为 `__call()` 的方法，接收字符串类型的方法名以及以数组形式传递的任何参数。该方法应该向调用代码返回一个值（如果有的话）：

`__call()` 是非常有用的，当你想要为不存在的方法方法创建一个包装类时。

# 第二部分：学习语言

## 尝试一下 包装类

以下示例展示了如何使用 `__call()` 来创建一个包装类。在这种情况下，该类提供了对内置字符串函数的接口。将脚本保存为 `clever_string.php` 并在你的文档根目录中运行它：

```php
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
http://www.w3.org/TR/xhtml/DTD/xhtml-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:en lang="en">
<head>
  <title>Creating a Class with __call()</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
  <h1>Creating a Class with __call()</h1>
</body>
</html>

<?php
class CleverString {
  private $theString = "";
  private static $_allowedFunctions = array("strlen", "strtoupper", "strpos");

  public function setString($stringVal) {
    $this->theString = $stringVal;
  }

  public function getString() {
    return $this->theString;
  }

  public function __call($methodName, $arguments) {
    if (in_array($methodName, self::$_allowedFunctions)) {
      array_unshift($arguments, $this->theString);
      return call_user_func_array($methodName, $arguments);
    } else {
      die("<p>CleverString::$methodName doesn't exist</p>");
    }
  }
}

$myString = new CleverString();
$myString->setString("Hello!");
echo "<p>The string is: " . $myString->getString() . "</p>";
echo "<p>The length of the string is: " . $myString->strlen() . "</p>";
?>
```

运行后，脚本产生了图 8-4 所示的输出。

![](img/ede05b7b77968b82cbd9a513122fb183_226_0.png)

## 它可以工作

CleverString 类有两个作用：它存储了一个一个要操作的字符串，并提供了对三个内置字符串函数的方法化访问：

- `strlen()` 用于计算字符串长度
- `strtoupper()` 用于将字符串转换为大写
- `strpos()` 用于查找字符在字符串中的出现位置

正如前面提到的，出于安全考虑，对这类方法与允许列表进行检查是很好的做法。如果 $methodName 不在这些列表中，脚本将终止。

