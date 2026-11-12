

在此语法中，$param1 是必填参数，而 $param2 是带有默认值的可选参数。

调用函数时，如果未为 $param2 传递参数，则将使用其默认值。否则，调用时传递的值将替换默认值。

以下是使用带默认参数的函数的示例：

```php
<?php
function greet($name = "My friend") {
   echo "Hello, $name!";
}

// Function calls with and without parameter specification
greet(); // Display "Hello, My friend!"
echo "<br>"; // Line break
greet("Alice"); // Display "Hello, Alice!"
?>
```

在此示例中，greet() 函数接受一个带有默认值 "My friend" 的 $name 参数。当不带参数调用函数时，它使用此默认值。当传递参数时，它替换默认值，因此执行此代码得到以下结果：

![](img/caba2aa22f5409ba73dea47176330677_162_0.png)

带默认参数的函数在定义函数时提供了额外的灵活性，允许开发者指定默认行为，同时保留根据需要对其进行自定义的可能性。

### 示例 2：

```php
<?php
// Function definition
function display_name($firstname, $lastname = "Mercier") {
// Checks if the name is not "Mercier".
if ($lastname != "Mercier") {
echo "Your last name is $lastname and your first name is $firstname";
} else {
echo "Your first name is: $firstname";
}
}
// call the display_name function with a single argument ("Amandine")
display_name("Amandine");
echo "<br>";
// call the display_name function with two arguments ("Sarah" and "Smith")
display_name("Sarah", "Smith");
?>
```

此代码定义了一个 **display_name()** 函数，该函数接受必填参数 $firstname 和带有默认值 "Mercier" 的可选参数 $lastname。调用函数时，它检查姓氏是否不同于 "Mercier"。如果是，则同时显示名和姓，否则仅显示名。

如果运行此代码，将得到以下结果：

![](img/caba2aa22f5409ba73dea47176330677_164_0.png)

- 当我们用单个参数调用函数（display_name("Amandine")）时，它使用名 "Amandine" 和默认姓 "Mercier"，因此显示 "Your first name is: Amandine"。
- 当我们用两个参数调用函数（display_name("Sarah", "Smith")）时，它使用名 "Sarah" 和指定的姓 "Dupont"，因此显示 "Your last name is Smith and your first name is Sarah"。

### 带引用参数的函数

要介绍本节，让我们考虑一个用于翻倍作为参数传递的数字的简单函数的代码：

```php
<?php
function double($number) {
	$number *= 2;
}

$x = 10;
double($x); // call the double() function
echo $x;
?>
```

此代码定义了一个名为 "double" 的函数，该函数接受一个参数 $number。在函数中，使用复合赋值运算符 "*=" 将 "$number" 的值乘以 2。这意味着 "$number" 变量将被翻倍。

接下来，将变量 $x 初始化为 10。然后用 $x 作为参数调用 "double" 函数。

如果运行此代码，您将得到变量 $x 的值。在此示例中，您将始终得到 10，因为 "double" 函数使用 $x 值的副本，而不是对变量本身的引用。

但是，有时您可能需要函数直接修改作为参数传递的变量的值，并且该更改在程序的其余部分保持有效。为此，您可以使用引用参数的概念。

引用参数允许函数直接修改作为参数传递的变量的值。
要声明引用参数，请在函数签名中使用 & 符号在参数名称之前。

如果我们采用与上面相同的示例，并在函数参数前添加 & 符号，这将允许 "double" 函数直接修改 $x 变量的值，因此在调用函数后显示 $x 时，您将得到 20。

```php
<?php

function double(&$number) {
    $number *= 2;
}

$x = 10;
double($x); // call the double() function
echo $x;

?>
```

### 引用函数与值函数

带引用参数的函数允许您直接修改作为参数传递给函数的变量的值，并且此更改在退出函数后仍然有效。与按值传递参数的函数不同，后者使用作为参数传递的变量值的副本，按引用传递参数的函数直接作用于原始变量。

### 了解带引用参数的函数的工作原理：

- 当您调用函数并按 **引用** 传递参数时，PHP 将原始变量的内存地址存储在内部引用中。
- 在函数内部，当您使用此参数时，PHP 使用此内部引用直接访问原始变量并进行必要的修改。
- 通过此参数对变量所做的任何修改都会直接影响原始变量，因为 PHP 使用的是变量本身的内存地址，而不是其值的副本。

这允许函数直接修改原始变量，并且这些修改在退出函数后仍然保留。这就是为什么在需要修改变量的值并希望该修改在函数外部可见时使用引用参数的原因。

### 了解按值传递参数的函数的工作原理：

- 当您调用函数并按 **值** 传递参数时，PHP 创建原始变量值的 **副本** 并将其分配给函数内部使用的 **新内存位置**。
- 在函数内部，对按值传递的参数所做的任何修改仅影响此值的 **副本**，不会修改函数外部的原始变量。
- 当函数结束时，按值传递的参数值的副本会被 **销毁**，原始变量保持不变。

这意味着在函数内部对按值传递的参数所做的修改仅局限于该函数，在函数外部不可见。通常在希望在函数内部使用变量的值而不修改函数外部的原始变量时使用按值传递的参数。

## 带命名参数的函数

在 PHP 中，函数还可以接受所谓的命名参数，在调用带有多个参数的函数时提供了更大的灵活性。请考虑以下代码：

```php
<?php
function infos_display($lastname, $firstname, $age, $isactive){
   return "Last Name: $lastname, First Name: $firstname, Age: $age, Active: $isactive";
}

$person_info = infos_display("Dupont", "Jean_marc", 32, True);
echo $person_info;
?>
```

在此示例中，我们有一个名为 "infos_display" 的函数，它接受四个参数：$lastname、$firstname、$age 和 $isactive。然后函数返回由这些参数组成的句子。
然后我们调用此函数，将返回值存储在 $person_info 变量中，然后显示它。

如果运行此代码，您将得到类似以下的结果：

Last Name: Dupont, First Name: Jean_marc, Age: 32, Active: 1

但是，如果在调用函数时，我们不遵守参数的顺序会怎样呢？

```php
$person_info = infos_display(32, True, "Jean-Marc", "Dupont");
echo $person_info;
```

在此示例中，我们尝试以不同于定义顺序的顺序调用带有参数的函数。我们没有遵守函数参数的顺序（姓、名、年龄、是否活跃），而是颠倒了此顺序，以不同的方式传递了值：姓为 32，名为 True，年龄为 "Jean-Marc"，是否活跃为 "Dupont"。

在此情况下，执行代码将得到以下结果：
