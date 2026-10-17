
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

?>
```

// 使用两个参数 ("Sarah" 和 "Smith") 调用 `display_name` 函数

`display_name("Sarah", "Smith");`

?>

这段代码定义了一个 `display_name()` 函数，它接受一个必需参数 `$firstname` 和一个默认值为 "Mercier" 的可选参数 `$lastname`。调用函数时，它会检查 lastname 是否不同于 "Mercier"。如果是，则同时显示名和姓，否则仅显示名。

如果运行这段代码，将得到以下结果：

![Image](img/image-64.png)

*   当我们使用单个参数调用函数时 (`display_name("Amandine")`)，它使用名字 "Amandine" 和默认姓氏 "Mercier"，因此显示 "Your first name is: Amandine"。
*   当我们使用两个参数调用函数时 (`display_name("Sarah", "Smith")`)，它使用指定的名字 "Sarah" 和姓氏 "Smith"，因此显示 "Your last name is Smith and your first name is Sarah"。

### 按引用传参的函数

为了引入本节，让我们来看一段将作为参数传递的数字加倍的简单函数代码：

```php
function double($number) {
    $number *= 2;
}

$x = 10;
double($x); // 调用 double() 函数
echo $x;
```

这段代码定义了一个名为 "double" 的函数，它接受一个参数 `$number`。在函数内部，使用复合赋值运算符 `*=` 将 `$number` 的值乘以 2。这意味着 `$number` 变量将被加倍。

接下来，变量 `$x` 被初始化为 10。然后使用 `$x` 作为参数调用 `double` 函数。

如果运行这段代码，你将得到变量 `$x` 的值。在本例中，你将始终得到 10，因为 `double` 函数使用的是 `$x` 值的**副本**，而不是对变量本身的引用。

然而，有时你可能需要函数直接修改作为参数传递的变量的值，并使该更改在程序的其余部分保持有效。为此，你可以使用按引用传参的概念。

按引用传参允许函数直接修改作为参数传递的变量的值。要声明按引用传参，请在函数签名中的参数名称前使用 `&` 符号。

如果我们采用上面相同的示例，并在函数参数前添加 `&` 符号，这将允许 `double` 函数直接修改 `$x` 变量的值，因此在调用函数后显示 `$x` 时将得到 20。

```php
function double(&$number) {
    $number *= 2;
}

$x = 10;
double($x); // 调用 double() 函数
echo $x;
```

### 按引用传参函数 vs. 按值传参函数

按引用传参的函数允许你直接修改作为参数传递给函数的变量的值，且该更改在退出函数后仍然有效。与按值传参的函数（它们使用作为参数传递的变量值的副本）不同，按引用传参的函数直接作用于原始变量。

理解按引用传参函数的工作原理：

*   当你调用函数并按**引用**传递参数时，PHP 会将原始变量的内存地址存储在内部引用中。
*   在函数内部，当你使用此参数时，PHP 会使用此内部引用直接访问原始变量并进行必要的修改。
*   通过此参数对变量所做的任何修改都会直接影响原始变量，因为 PHP 处理的是变量本身的内存地址，而不是其值的副本。

这使得函数能够直接修改原始变量，并且这些修改在退出函数后仍然保留。这就是为什么当你需要修改变量的值并希望该修改在函数外部可见时，会使用按引用传参。

理解按值传参函数的工作原理：

*   当你调用函数并按**值**传递参数时，PHP 会创建原始变量值的**副本**，并将其分配给一个**新的内存位置**以供函数内部使用。
*   在函数内部，对该按值传递参数所做的任何修改仅影响该**值的副本**，而不会修改函数外部的原始变量。
*   当函数结束时，按值传递的参数值副本被**销毁**，原始变量保持不变。

这意味着在函数内部对按值传递参数所做的修改仅局限于该函数，在外部不可见。当你希望在函数内部使用变量的值而不修改函数外部的原始变量时，通常使用按值传参。

### 具有命名参数的函数

在 PHP 中，函数还可以接受所谓的命名参数，这在调用具有多个参数的函数时提供了更大的灵活性。请看以下代码：

```php
function infos_display($lastname, $firstname, $age, $isactive){
    return "Last Name: $lastname, First Name: $firstname, Age: $age, Active: $isactive";
}

$person_info = infos_display("Dupont", "Jean_marc", 32, True);
echo $person_infos;
```

在本例中，我们有一个名为 `infos_display` 的函数，它接受四个参数：`$lastname`、`$firstname`、`$age` 和 `$isactive`。然后函数返回由这些参数组成的句子。

然后我们调用此函数，并将返回的值存储在 `$person_info` 变量中，然后显示它。

如果运行这段代码，你将得到类似以下的结果：

![Image](img/image-65.png)

但是，如果在调用函数时不遵守参数的顺序会怎样？

```php
$person_info = infos_display(32, True, "Jean-Marc", "Dupont");
echo $person_info;
```

在本例中，我们尝试使用与定义不同的顺序传递参数来调用函数。我们没有遵守函数参数的顺序（姓、名、年龄、是否激活），而是反转了此顺序，并以不同的方式传递值：32 代表姓，True 代表名，"Jean-Marc" 代表年龄，"Dupont" 代表是否激活。

在这种情况下，执行代码将得到以下结果：

![Image](img/image-66.png)

我们显示个人信息时获得的结果是不正确的。我们没有得到预期的详细信息，而是得到了意外的输出。为了解决这个问题，PHP 8 引入了命名参数的概念。实际上，命名参数允许以反转参数顺序的方式调用函数。

使用命名参数，我们可以在调用函数时显式指定每个参数的名称，后跟冒号 (`:`)，再后跟其值。这确保了每个实参都与正确的形参相关联，无论它们在函数调用中传递的顺序如何。因此，即使我们在函数调用中反转了实参的顺序，使用命名参数也能保证函数根据其关联的参数正确处理每个值。以下是如何使用命名参数并解决反转函数参数顺序时可能出现的问题。

```php
function infos_display($lastname, $firstname, $age, $isactive) {
    return "Last Name: $lastname, First Name: $firstname, Age: $age, Active: $isactive";
}

$person_info = infos_display(age:32, isactive:True, firstname: "Jean-Marc", lastname: "Dupont");
echo $person_info;
```

当我们执行这段代码时，结果与调用 `infos_display()` 函数并遵守参数顺序时获得的结果相同。

![Image](img/image-67.png)

## PHP 中的类型声明与变量作用域

### PHP 中的类型声明

在 PHP 中，可以指定参数和函数返回值的类型，以提高代码清晰度并保证更好的数据完整性。PHP 中可使用两种类型声明：严格类型和弱类型。

#### 弱类型（默认）

默认情况下，PHP 使用弱类型，这意味着函数参数和返回值的数据类型未显式声明。这提供了极大的灵活性，但有时会导致难以检测的错误。

**无类型声明的函数示例：**

```php
<?php

function addition($a, $b) {
    return $a + $b;
}

$result1 = addition(5, 10);
echo $result1 . "<br>";

$result2 = addition(5, "10");
echo $result2 . "<br>";

?>
```

这段 PHP 代码定义了一个名为 `addition()` 的函数，它接受两个参数 `$a` 和 `$b`，并返回这两个参数的和。随后使用不同的参数调用了该函数两次。

在本例中，`addition()` 函数未指定其 `$a` 和 `$b` 参数的类型。它们可以是任意数据类型，函数的结果将取决于传入值的类型。

在第一次调用 `addition(5, 10)` 中，两个参数均为整数（`$a = 5` 且 `$b = 10`）。函数返回这两个数字的和（即 15），该值被赋给变量 `$result1`。最后输出 `$result1` 的值，屏幕显示 15。

在第二次调用 `addition(5, "10")` 中，第一个参数是整数（`$a = 5`），但第二个参数是字符串（`$b = "10"`）。PHP 在加法运算时执行**自动类型转换**，将字符串 "10" 转换为整数。因此，函数同样返回 15（5 和 10 之和），该值被赋给变量 `$result2`。最后输出 `$result2` 的值，屏幕同样显示 15。

总之，对 `addition()` 函数的两次调用结果相同（均为 15），尽管第二次调用对第二个参数使用了字符串。这是由于 PHP 在加法运算期间执行了自动类型转换。

#### 严格类型

严格类型随 PHP 7 引入，允许显式指定参数和函数返回值的数据类型。这使得类型不一致可在开发阶段尽早被检测到，有助于减少错误。

要启用严格类型，必须在 PHP 脚本开头声明指令 `declare(strict_types=1);`：

![Image](img/image-68.png)

要声明参数类型，只需在每个参数前指定所需类型；要指定函数返回值的类型，在参数列表后添加冒号（`:`），后跟预期的返回类型。

让我们修改前一个示例，指定参数类型和返回类型：

```php
<?php

declare(strict_types=1);

function addition(int $a, int $b): int {
    return $a + $b;
}

$result1 = addition(5, 10);
echo $result1 . "<br>";

$result2 = addition(5, "10");
echo $result2 . "<br>";

?>
```

运行此代码将得到类似如下的结果：

![Image](img/image-69.png)

结果首先显示数字 15，对应变量 `$result1` 的值。当我们调用 `addition(5, 10);` 时，传入了两个整数，这与声明的类型一致。因此，函数将这两个整数相加并返回一个整数结果，存储在变量 `$result1` 中，随后被显示。

然而，在随后的调用 `addition(5, "10");` 中，我们传入了一个整数和一个字符串，这与声明的类型 `int` 不符。由于启用了**严格**类型，这会产生一个致命错误，因为提供的数据类型与函数预期的类型不匹配。因此，脚本停止并显示错误，而不会像未启用严格类型时那样自动将字符串转换为整数。

最后请注意，从 PHP 8 起，可以使用联合类型运算符 `|`（竖线）为同一参数指定多种类型。这允许定义参数可接受多种不同的数据类型。例如，若参数可以是整数或字符串，可按如下方式声明：

```php
<?php

function example(int|string $parameter1, float|int $parameter2) {
    // 函数体
}

?>
```

在本例中，`$parameter1` 可以是整数或字符串。而 `$parameter2` 可以是浮点数或整数。这为函数参数类型定义提供了更大的灵活性。

### 变量的作用域

变量作用域是编程中的一个基本概念，它决定了变量在 PHP 脚本中的可用范围。理解变量作用域对于编写结构良好的代码、避免逻辑错误以及确保程序平稳运行至关重要。

在 PHP 中，变量根据其在脚本中的位置不同，可以拥有不同的作用域。有些变量可在脚本的任何位置访问，而另一些则被限制在代码的特定部分。

在本节中，我们将探讨 PHP 中不同类型的变量作用域，它们的定义和使用方式，以及有效处理它们的最佳实践。我们还将了解与变量作用域相关的常见陷阱及其规避方法。

让我们首先了解 PHP 中变量作用域背后的主要概念，以及它们如何影响我们的代码编写方式。

#### 全局作用域

在 PHP 中，在任何函数外部声明的变量具有全局作用域。这意味着它们可以在 PHP 脚本的任何位置访问，无论是在函数内部还是外部。

当变量在任何函数外部声明时，它自动成为全局变量。例如：

```php
<?php

$global_variable = "I am a global variable";

function display_global_variable() {
    global $global_variable;
    echo $global_variable;
}

display_global_variable(); // 调用函数

?>
```

在本例中，`$global_variable` 是一个全局变量，因为它在任何函数外部声明。它可以在 `display_global_variable()` 函数内部使用，但前提是必须使用 `global` 关键字。

重要的是要注意，使用全局变量会降低代码的可读性并增加维护难度，因为它们可能在脚本的不同位置被不可预测地修改。因此建议限制全局变量的使用。

执行此代码显示结果：

![Image](img/image-70.png)

**警告**：如果尝试在函数内部使用全局变量而不使用 `global` 关键字声明它：

```php
<?php

$global_variable = "I am a global variable";

function display_global_variable() {
    echo $global_variable;
}

display_global_variable(); // 调用函数

?>
```

在这种情况下，你将得到类似如下的错误消息：

![Image](img/image-71.png)

#### 局部作用域

在局部作用域中，变量在函数内部声明，只能在该函数内部访问。这些变量仅在函数运行期间存在，函数一结束即被销毁。这意味着它们不能在声明它们的函数外部使用。这种作用域限制有助于避免代码不同部分之间的变量名冲突。

以下示例演示了变量的局部作用域：

```php
<?php

function displayMessage() {
    $message = "Hello, world!";
    echo $message;
}

displayMessage(); // 显示 "Hello, world!"

echo $message; // 尝试访问变量 $message

?>
```

在本例中，`$message` 变量是在 `displayMessage()` 函数内部声明的，这使其成为该函数的局部变量。此 `$message` 变量无法在其定义所在的函数外部访问。当我们尝试在函数外部显示该变量的值时，会生成一个错误，提示在代码的这一点上无法识别 `$message` 变量。

![Image](img/image-72.png)

此演示突出了 PHP 中变量的局部作用域。局部变量仅限于声明它们的函数内部，且不能在该函数外部使用。这有助于避免命名冲突，并使代码更加模块化和有条理。

#### 静态作用域

在函数内部创建的局部变量，会在函数执行结束时自动销毁。然而，在某些情况下，我们可能需要在函数的连续调用之间保留该变量的值，以便稍后使用，因此引入了静态作用域的概念。

PHP 中的静态变量作用域允许变量在连续的函数调用之间保留其值。与每次函数调用时都会创建和销毁的局部变量不同，静态变量即使在函数退出后仍保留其值。

请看以下示例：

```php
<?php

function counter() {

    $counter = 0;

    $counter++;

    echo "Number of function calls : $counter <br>";

}

counter();

counter();

counter();

?>
```
