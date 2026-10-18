
最后，实例化该类，然后调用 `aStaticMethod()` 来演示这同样有效：

```php
$objExample = new noInstancesRequiredClass;
$objExample->aStaticMethod();
```

> **注意：** 静态属性不能通过对象使用箭头运算符 `->` 来访问。

上述脚本的输出为：

```
Simon Stobart
Simon Stobart
Simon Stobart
```

## 17.7 类常量

PHP 类支持包含常量值。常量一旦定义，就保持不变且不可更改。常量与普通数据成员的区别在于，你不需要使用 `$` 符号来声明或使用它们。请看以下脚本：

```php
<?php
// File: example17-7.php

class constantClass {
    const strName = "Simon Stobart";
    function showConstant() {
        echo "<p>" . self::strName . "</p>";
    }
}

echo "<p>" . constantClass::strName . "</p>";
$objExample = new constantClass;
$objExample->showConstant();
?>
```

在上述脚本中，定义了 `constantClass`，并创建了一个 `const` 成员：

```php
class constantClass {
    const strName = "Simon Stobart";
```

> **注意：** 常量成员在定义时不使用 `$` 符号。

定义了一个方法 `showConstant()`，用于输出常量的值。请注意，这里使用 `self::` 作用域运算符来访问常量成员，因为 `->` 运算符无法实现此操作：

```php
function showConstant() {
    echo "<p>" . self::strName . "</p>";
}
```

在类外部，使用作用域运算符即可访问常量成员的值，无需实例化该类：

```php
echo "<p>" . constantClass::strName . "</p>";
```

最后，实例化该类，然后调用 `showConstant()` 方法，以说明这同样有效：

```php
$objExample = new constantClass;
$objExample->showConstant();
```

上述脚本的输出为：

```
Simon Stobart
Simon Stobart
```

## 17.8 类型提示

PHP 5 引入了类型提示的概念。函数可以强制参数为对象（通过在函数原型中指定类名）或数组。请看以下脚本：

```php
<?php
// File: example17-8.php

class typeHintingClass {

    private $arrNames = array();

    function __construct(array $arrNames) {
        $this->arrNames = $arrNames;
    }

    function showContents() {
        foreach ($this->arrNames as $arrItem)
            echo "<p>$arrItem</p>";
    }

    function showOtherClass(typeHintingClass $objOther) {
        $objOther->showContents();
    }
}

$arrNames = array("Simon","Alan","Fred");
$arrColours = array("Red","Green","Blue","Yellow");

$objNames = new typeHintingClass($arrNames);
$objNames->showContents();

$objColours = new typeHintingClass($arrColours);
$objNames->showOtherClass($objColours);
?>
```

> **注意：** 类型提示只能是对象类型和数组类型（自 PHP 5.1 起）。如果你的电脑没有运行 PHP 5.1 或更高版本，上述脚本将无法运行。

该脚本首先创建了一个名为 `typeHintingClass` 的类，其中包含一个数据成员数组：

```php
class typeHintingClass {
    private $arrNames = array();
}
```

构造函数为数组成员赋值：

```php
function __construct(array $arrNames) {
    $this->arrNames = $arrNames;
}
```

`showContents()` 方法显示数组的内容：

```php
function showContents() {
    foreach ($this->arrNames as $arrItem)
        echo "<p>$arrItem</p>";
}
```

`showOtherClass()` 方法接收一个对象，然后调用 `showContents()` 方法来显示其成员的内容。在方法参数中使用了类型提示，以指定该方法期望接收一个 `typeHintingClass` 对象：

```php
function showOtherClass(typeHintingClass $objOther) {
    $objOther->showContents();
}
```

创建了两个数组：

```php
$arrNames = array("Simon","Alan","Fred");
$arrColours = array("Red","Green","Blue","Yellow");
```

创建一个对象并显示其内容：

```php
$objNames = new typeHintingClass($arrNames);
$objNames->showContents();
```

创建另一个对象，然后将新对象传递给之前的对象进行显示：

```php
$objColours = new typeHintingClass($arrColours);
$objNames->showOtherClass($objColours);
```

### 图 17.14 类型提示

![](img/b2471264f405d17994ef173e4b9cec92_535_0.png)

你可以尝试插入下面这行脚本，以演示这段代码中类型提示的作用：

```php
$objNames->showOtherClass("Not an object!");
```

这会导致错误，因为传入的是字符串，而不是对象。

上述脚本的输出如图 17.14 所示。

## 17.9 比较对象

在 PHP 5 中，对象比较比该语言之前的版本更复杂。对象可以通过两种不同的方式进行比较。首先，使用比较运算符（`==`）时，如果两个对象实例具有相同的属性和值，并且是同一个类的实例，则它们相等。其次，使用全等运算符（`===`）时，当且仅当对象变量引用同一个类的同一个实例时，它们才完全相同。请看以下示例：

```php
<?php
// File: example17-9.php

class Person {
    public $strName;
    function __construct ($strName) {
        $this->strName = $strName;
    }
}

class AnotherPerson {
    public $strName;
    function __construct ($strName) {
        $this->strName = $strName;
    }
}

$objSimon = new Person("Simon");
$objSimon2 = new Person("Simon");
$objSimon3 = new AnotherPerson("Simon");
$objSimon4 = $objSimon;

if ($objSimon == $objSimon2)
    echo '<p>$objSimon == $objSimon2</p>';

if ($objSimon == $objSimon3)
    echo '<p>$objSimon == $objSimon3</p>';

if ($objSimon == $objSimon4)
    echo '<p>$objSimon == $objSimon4</p>';

if ($objSimon === $objSimon2)
    echo '<p>$objSimon === $objSimon2</p>';

if ($objSimon === $objSimon3)
    echo '<p>$objSimon === $objSimon3</p>';

if ($objSimon === $objSimon4)
    echo '<p>$objSimon === $objSimon4</p>';
?>
```

此脚本首先创建了一个 `Person` 类，其中包含一个数据成员 `$strName` 和一个构造函数：

```php
class Person {
    public $strName;
    function __construct ($strName) {
        $this->strName = $strName;
    }
}
```

还创建了另一个名为 `AnotherPerson` 的类，它包含与 `Person` 类完全相同的数据成员：

```php
class AnotherPerson {
    public $strName;
    function __construct ($strName) {
        $this->strName = $strName;
    }
}
```

创建了四个对象。第一个和第二个是 `Person` 类的对象：

```php
$objSimon = new Person("Simon");
$objSimon2 = new Person("Simon");
```

第三个是 `AnotherPerson` 类的对象：

```php
$objSimon3 = new AnotherPerson("Simon");
```

第四个是 `Person` 类型的对象，因为它是根据一个已经创建的实例创建的：

```php
$objSimon4 = $objSimon;
```

使用比较运算符（`==`）比较 `$objSimon` 和 `$objSimon2`，结果为 true：

```php
if ($objSimon == $objSimon2)
    echo '<p>$objSimon == $objSimon2</p>';
```

使用比较运算符（`==`）比较 `$objSimon` 和 `$objSimon3`，由于类不同，结果为 false：

```php
if ($objSimon == $objSimon3)
    echo '<p>$objSimon == $objSimon3</p>';
```

使用比较运算符（`==`）比较 `$objSimon` 和 `$objSimon4`，结果为 true：

```php
if ($objSimon == $objSimon4)
    echo '<p>$objSimon == $objSimon4</p>';
```

使用全等运算符（`===`）比较 `$objSimon` 和 `$objSimon2`，由于它们不是同一个对象实例，结果为 false：

```php
if ($objSimon === $objSimon2)
    echo '<p>$objSimon === $objSimon2</p>';
```

使用全等运算符（`===`）比较 `$objSimon` 和 `$objSimon3`，由于它们不是同一个对象实例，结果为 false：

```php
if ($objSimon === $objSimon3)
    echo '<p>$objSimon === $objSimon3</p>';
```

使用全等运算符（`===`）比较 `$objSimon` 和 `$objSimon4`，结果为 true：

```php
if ($objSimon === $objSimon4)
    echo '<p>$objSimon === $objSimon4</p>';
?>
```
