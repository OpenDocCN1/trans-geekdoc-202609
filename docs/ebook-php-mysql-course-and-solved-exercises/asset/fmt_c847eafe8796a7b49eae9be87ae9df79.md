
# PHP 字符串处理与常量

## 字符串显示与变量解析

```php
echo "Hello, $firstname!"; // Displays "Hello, Alice!"

echo "<br>";

echo 'Hello, $firstname!'; // Display "Hello, $firstname!"
```

**Result:**

![Image](images/image-19.png)

在该示例中，第一条 `echo` 语句使用双引号显示变量 `$firstname` 的值，而第二条 `echo` 语句使用单引号，显示字面文本 `$firstname` 而不解析变量。

## 连接运算符（点号 `.`）的使用

在 PHP 中，连接运算符由点号（`.`）表示，用于连接字符串。

### 示例 1

```php
<?php
$firstname = "Alice";
$name = "Smith";
$message = "Hello, " . $firstname . " " . $name . " !";
echo $message;
?>
```

在该示例中，变量 `$firstname` 和 `$lastname` 分别包含值 "Alice" 和 "Dupont"。连接运算符（`.`）用于将这些变量与文本字符串结合，形成完整消息 "Hello, Alice Smith!"。

双引号（`" "`），由一个空格分隔并插在两个变量 `$firstname` 和 `$lastname` 之间，在这两个变量的值之间创建了一个空格（在 Alice 和 Dupont 之间）。

**Result:**

![Image](images/image-20.png)

### 示例 2

```php
<?php
$age = 30;
$message = "She's turning " .$age. " next week, but she doesn't look a day over 25 ";
echo $message;
?>
```

在该示例中，变量 `$age` 包含数值 30。连接运算符（`.`）用于将该变量与文本字符串结合，形成完整消息 "I'm 30 years old"。

**Result:**

![Image](images/image-21.png)

## 包含撇号的收缩字符串

让我们修改前一个示例，使用撇号代替双引号：

```php
<?php
$age = 30;
$message = 'She's turning " .$age. " next week, but she doesn't look a day over 25 ';
echo $message;
?>
```

运行此代码时，会在定义变量 `$message` 的那一行报错。

![Image](images/image-22.png)

错误发生的原因是字符串“**She’s**”和“**doesn’t**”中使用了撇号。在 PHP 中，当字符串用单引号（`''`）括起时，字符串内的撇号必须用反斜杠（`\`）转义，以避免与字符串结束符混淆。

要解决此错误，可以用反斜杠（`\`）转义撇号：

```php
<?php
$age = 30;
$message = 'She\'s turning " .$age. " next week, but she doesn\'t look a day over 25 ';
echo $message;
?>
```

## 使用 `.=` 运算符

在 PHP 中，可以使用 `.=` 运算符将字符串连接到现有变量。

```php
<?php
$message = "Hello ";
$message .= "everyone!";
echo $message;
?>
```

在该示例中，字符串 "Everybody!" 与已包含字符串 "Hello" 的变量 `$message` 连接，形成完整消息 "Hello everybody!"。

换句话说，代码行 `$message .= "everyone!";` 使用连接运算符（`.=`）将字符串 "everyone!" 追加到变量 `$message` 的末尾。这意味着字符串 'everybody!' 被追加到 `$message` 变量中现有字符串的末尾。

注意字符串 "Bonjour" 末尾包含一个空格，允许在两个文本字符串 "Bonjour" 和 "Bonjour tout le monde!" 之间插入空格。

![Image](images/image-23.png)

在 PHP 中，连接是结合字符串和变量以创建动态消息和复杂表达式的有效方法。

通过使用这些不同的显示和连接方法，您可以在 PHP 脚本中高效地操作文本和变量。

# 在 PHP 中使用常量

PHP 常量是标识符（名称），代表脚本执行过程中不可变的值。一旦定义，常量在脚本执行期间不能被修改或重新赋值。

## 在 PHP 中定义常量

在 PHP 中，有两种定义常量的方法：使用 `define()` 函数或 `const` 指令。定义常量的语法如下：

![Image](images/image-24.png)

### 示例

```php
<?php
define('VAT', 0.20);
const AVERAGE_GRADE = 10;
?>
```

第一个常量使用 `define()` 函数定义，名为 `VAT`。其值设为 0.20，代表 20% 的 `VAT` 税率。该常量在全局声明，定义后可在整个脚本中使用。

第二个常量使用 `const` 指令定义，名为 `AVERAGE_GRADE`。其值设为 10，代表平均分。该常量也在全局声明，定义后可在整个脚本中使用。

## 使用常量的优势

与变量相比，常量具有以下优势：

*   **不可变**：常量在脚本执行期间保持其值，保证值恒定且可预测。
*   **易读性**：常量通常具有描述性名称，使代码更易理解。
*   **可复用性**：常量可在代码的多处使用，无需重复值。
*   **安全性**：常量在脚本执行期间不能被意外修改，确保代码一致性和可靠性。

## 命名和使用常量的最佳实践

定义和使用常量时，建议遵循以下最佳实践：

*   对常量使用描述性的大写名称（如 `VAT`、`MAX_SIZE`）。
*   避免在常量名称中使用特殊字符或空格。
*   在脚本开头定义常量，以提高可读性。

## PHP 中的预定义常量示例

PHP 中有许多预定义常量可在脚本中使用：

*   `PHP_VERSION`：此预定义常量包含服务器上安装的当前 PHP 版本。
*   `PHP_OS`：此预定义常量包含运行 PHP 服务器的操作系统名称。
*   `PHP_INT_MAX`：此预定义常量包含当前 PHP 平台上整数的最大值。
*   `__FILE__`：此预定义魔术常量包含使用它的文件的绝对路径。
*   `__LINE__`：此预定义魔术常量包含文件中使用它的当前行号。

```php
<?php
echo PHP_VERSION ."<br>"; // Display current PHP version
echo PHP_OS ."<br>"; // Display operating system name
echo PHP_INT_MAX ."<br>"; // Display the maximum value of an integer on a given platform
echo __FILE__ ."<br>"; // Display the absolute path of the file
echo __LINE__ ."<br>"; // Display current line number
?>
```

执行此代码将得到类似以下输出（特定于我们机器的数据）：

![Image](images/image-25.png)

*   `8.1.17`：是我们计算机上安装的 PHP 版本
*   `Darwin`：是我们机器的 Mac 操作系统
*   `92233372036854775807`：是 64 位平台上的最大数字
*   `/Application/XAMPP/xamppfiles/htdocs/ebookphp/index.php`：是当前正在运行的文件的绝对路径
*   `21`：是对应 `echo __LINE__` 指令的行号

## 比较变量和常量

变量和常量是 PHP 编程的基本元素，但它们在行为和用途上有所不同：

变量可以在脚本执行期间被修改和重新赋值，而常量保持其不可变的值。

变量使用 `$` 符号声明，而常量使用 `define()` 或 `const` 声明。

常量通常用于脚本中保持不变的值，如税率或数学常量，而变量用于脚本执行期间可能更改的值。

# PHP 中的数据类型
