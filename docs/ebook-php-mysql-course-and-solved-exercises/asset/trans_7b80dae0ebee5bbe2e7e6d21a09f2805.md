
`__toString()` 方法会在对象被用于期望字符串的上下文中时自动调用，例如当它被传递给 `echo` 函数时。它定义了对象的字符串表示形式。

```php
class Example {
    private $name;

    public function __construct($name) {
        $this->name = $name;
    }

    public function __toString() {
        return "This object is called " . $this->name;
    }
}

$object1 = new Example("NameObject1");
echo $object1; // 显示 : This object is called Example
```

在本例中，`Example` 类定义了一个魔术 `__toString()` 方法。当我们尝试使用 `echo` 或字符串连接来显示对象 `$object1` 时，`__toString()` 方法会被自动调用。该方法返回一个以有意义的方式表示对象的字符串。

![Image](images/image-205.png)

### `__destruct()`

`__destruct()` 方法会在对象销毁之前自动调用。它用于执行清理操作或释放与对象关联的资源。

```php
class Example {
    public function __destruct() {
        echo "The object has been destroyed.";
    }
}

$object1 = new Example();
unset($object1); // 显式销毁对象。显示: The object has been destroyed.
```

在本例中，`Example` 类定义了一个魔术 `__destruct()` 方法。当对象被销毁时，无论是使用 `unset()` 函数显式销毁，还是在脚本结束时隐式销毁，该方法都会被自动调用。在本例中，当我们使用 `unset($object1)` 销毁对象 `$object1` 时，`__destruct()` 方法被调用并显示一条指示对象已被销毁的消息。

![Image](images/image-206.png)

## 结论

PHP 的魔术方法为自定义对象和类的行为提供了强大的灵活性。它们能在与对象的各种交互过程中实现自动干预，使代码管理和扩展更加容易。

在本章中，我们探讨了一些最常用的魔术方法，例如 `__get()`、`__set()`、`__call()`、`__callStatic()`、`__toString()` 和 `__destruct()`。这些方法为管理属性访问、动态调用方法、将对象显示为字符串以及在对象销毁时执行操作提供了有用的功能。

值得注意的是，PHP 中还有其他魔术方法，例如 `__isset()`、`__unset()`、`__invoke()`、`__clone()` 等，它们提供了额外的功能以满足特定的开发需求。

通过审慎地利用这些魔术方法，PHP 开发人员可以使他们的代码更加灵活、更加健壮且更易于维护，同时受益于应用程序设计中更强的表达能力。

# 练习答案

### 练习 1

编写一个 PHP 脚本，定义一个包含您姓名的 `name` 变量和一个包含您年龄的 `age` 变量。接下来，脚本应显示一条消息："Hello [your name], you're [your age] years old!"。

#### 答案

```php
$name = "John"; // 替换为您的姓名
$age = 30; // 替换为您的年龄
echo "Hello $name, you are $age years old!";
```

### 练习 2

编写一个 PHP 脚本，将一个人的姓氏、名字和年龄存储在变量中，并使用连接运算符以句子的形式显示这些信息。

#### 答案

```php
$lastname = "Strock";
$firstname = "John";
$age = 30;
echo "Hello, my name is " . $firstname . " " . $lastname . " and I'm " . $age . " years old.";
```

### 练习 3

编写一个 PHP 程序，将产品的价格存储在 `$price` 变量中，将数量存储在 `$quantity` 变量中，并通过将价格乘以数量来计算和显示订单的总金额。

#### 答案

```php
$price = 39; // 单价
$quantity = 7; // 订购数量
$total = $price * $quantity; // 计算总金额
echo "The total amount of the order is : $total euros";
```

### 练习 4

编写一个脚本，检查存储在变量中的数字是正数、负数还是零。

#### 答案

```php
$number = 34;
if ($number > 0) {
    echo "The number is positive.";
} elseif ($number < 0) {
    echo "The number is negative.";
} else {
    echo "The number is zero";
}
```

### 练习 5

编写一个程序，使用条件指令检查按 100 分制评估的学生技能发展情况。

- 如果胜任度水平达到 80% 或以上，学生将被分在第一组。
- 如果胜任度在 50% 到 80% 之间，学生将被分在第二组。
- 如果胜任度在 30% 到 50% 之间，学生将被分在第三组。
- 如果胜任度水平低于 30%，学生将不及格。

#### 答案

```php
$degreeSkills = 60;
if ($degreeSkills >= 80) {
    $group = "Group 1";
} elseif ($degreeSkills >= 50) {
    $group = "Group 2";
} elseif ($degreeSkills >= 30) {
    $group = "Group 3";
} else {
    $group = "Failure";
}
echo "Student assignment group: $group";
```

### 练习 6

编写一个条件脚本，测试一个数字是否同时是 3 和 5 的倍数。

#### 答案

```php
$x = 1325775;
if ($x % 3 == 0 && $x % 5 == 0) {
    echo $x . " is a multiple of 3 and 5 <br />";
} else {
    echo $x . " is not a multiple of 3 or 5 <br>";
}
```

### 练习 7

编写一个程序，根据数字使用 switch 语句显示星期几（例如 Monday）。

- 第 1 天视为 Monday
- 如果数字不在 1 到 7 之间，默认显示 "invalid number"。

#### 答案

```php
$day = "3";
switch ($day) {
    case "1":
        echo "It's Monday!";
        break;
    case "2":
        echo "It's Tuesday!";
        break;
    case "3":
        echo "It's Wednesday!";
        break;
    case "4":
        echo "It's Thursday!";
        break;
    case "5":
        echo "It's Friday!";
        break;
    case "6":
        echo "It's Saturday!";
        break;
    case "7":
        echo "It's Sunday! ";
        break;
    default:
        echo "Invalid number!";
}
```

### 练习 8

编写一个程序，使用 while 循环显示从 10 到 50 的整数。

#### 答案

```php
$nb = 10;
while ($nb <= 50) {
    echo $nb;
    echo "<br>" ;
    $nb++;
}
```

### 练习 9

使用 for 循环，编写一个程序计算从 1 到 20 所有整数的乘积 (1x2x3x4x5x.....x19x20)。然后显示结果。

#### 答案

```php
$product = 1;
for ($x = 1; $x <= 20; $x++) {
    $product = $product * $x;
}
echo "The product of all numbers from 1 to 20 is $product";
```

### 练习 10

编写 7 的乘法表（针对从 1 到 100 的所有数字），使用 for 循环。该表应以无序列表的形式呈现。

#### 答案

```php
echo '<ul>';
for ($i = 1; $i <= 10; $i++)
    echo '<li>' . $i . ' x 7 = ' . ($i * 7) . '</li>';
echo '</ul>';
```

### 练习 11

编写一个程序计算以下求和：

1 + 3 + 3² + 3³ + 3⁴ + 3⁵ + ... ... + 3^(20)

#### 答案

```php
$x = 3;
$n = 20;
$sum = 0;
for ($i = 0; $i <= $n; $i++) {
    $term = $x ** $i;
    $sum = $sum + $term;
}
echo $sum;
```

### 练习 12

编写一个函数，测试一个数字是否为 3 的倍数，并根据测试结果显示一条消息。

#### 答案

```php
function multiples_of_three($x) {
    if ($x % 3 == 0) {
        echo "The number $x is a multiple of 3";
    } else {
        echo "The number $x is not a multiple of 3";
    }
}

multiples_of_three(3672);
echo "<br>";
multiples_of_three(10);
```

### 练习 13

编写一个 PHP 函数，接收三个数字作为输入，并返回这三个数字中最大的一个。

