
现在，`animal_functions.php` 只包含一次（在 `mouse.php` 中），因此 `animalSpeak()` 函数只会被定义一次。`display_animal_sounds.php` 脚本现在将正确运行，显示以下输出：

```
squeak
meow
```

## 使用包含路径

处理大型应用程序时的另一个问题是跟踪文件的位置。假设你将所有公共代码（包括 `animal_functions.php`）都组织在位于中央的 `/home/joe/lib` 目录中。这是一个包含路径列表的字符串。每个路径由冒号（Linux 服务器）或分号（Windows 服务器）分隔。`PATH_SEPARATOR` 常量包含当前系统的分隔符。路径按照它们出现的顺序进行搜索。你可以显示当前的 `include_path` 值——它通常从 `php.ini` 配置提取——调用 `get_include_path()` 函数：

```php
echo get_include_path(); // 显示如 :/usr/php
```

在这个示例中，包含路径包含两个路径：当前目录 `.` 和 `/usr/php`。要设置新的 `include_path` 值，你猜对了——`set_include_path()`：

```php
set_include_path("/home/joe/lib");
```

> 建议将路径包含当前目录 `.`，如所示。这意味着 PHP 始终在当前目录查找要的文件（这通常是你想要的）。

你通常会在应用程序启动时设置包含路径。一旦设置了包含路径，你就可以通过指定文件名来包含路径中的任何文件：

```php
include_once("animal_functions.");
```

在这个示例中，PHP 引擎会在当前目录查找 `animal_functions.php`。由于那里没有，它会在 `/home/joe/lib` 中查找并在那里找到。

你可以通过在包含路径中创建子文件夹来组织你的代码库。假设你将 `animal_functions.php` 文件放在名为 `animals` 的子文件夹中。该文件的绝对路径将是：

```
/home/joe/lib/animals/animal_functions.php
```

要在脚本中包含此文件，你可以写，例如：

```php
require("animals/animal_functions.php");
```

注意，你的脚本现在更具移植性。要将应用程序移动到具有不同路径的新服务器，你只需要在 `set_include_path()` 调用中指定新路径。顺便提一下，通常的做法是将你的新包含路径或路径添加到现有的包含路径中，而不是替换现有路径。这意味着任何其他库文件（如 PEAR 包）仍然可以被找到。要这样做，你可以使用以下代码：

```php
set_include_path( get_include_path() . PATH_SEPARATOR . "/home/joe/lib" );
```

如果你需要将包含路径还原为默认设置，只需调用 `restore_include_path()` 即可。

## 动态包含

由于 `include()` 及其相似函数 [are] 是 PHP 函数，你可以在 PHP 脚本的任何地方调用它们 —— 包括代码块或循环内部。例如，根据代码来包含不同的文件是非常有用的：

```php
if ($queryType == "animal" ) {
    include("animal_functions.php");
} else {
    include("plant_functions.php");
}
```

然后你可以使用变量的值来决定要包含哪个文件。这是动态仅包含所需的库文件的一种简单方法：

```php
include ($queryType . "_functions.php");
```

> 如果你这样做，出于安全考虑，请务必先对变量的值进行验证和清洗过滤。请参阅本章节后面的“检查输入和编码输出”以获取更多关于该主题的信息。

## 使用命名空间避免冲突

有时，你会发现自己在同一个应用程序中为不同的目的使用了相同的函数名、类名或常量名。当你处理一个非常大的应用程序，或者你的应用程序使用了许多库时，就会发生这种情况。通常，这会导致问题，因为你不能使用同一个名称来引用多个一个函数、类或常量。

例如，假设你正在开发一个在线商店应用程序。你可能有一个购物车脚本，其中包含一个 `display()` 函数用于显示购物车的标记：

```php
<?php
function display($cart) {
    // (显示购物车)
}
...
display ($_SESSION['cart']);
?>
```

# 第三部分：在实践中使用 PHP

到目前为止，一切顺利。现在假设你之前为另一个应用程序编写了一些结算库代码，这些代码存储在 `checkout.php` 中。除了其他之外，该文件包含一个也叫 `display()` 的函数，用于显示结算页面：

```php
<?php
function display($cartContents) {
    // (显示结算)
}
...
?>
```

你想在 `cart.php` 中包含这个库文件 `checkout.php`，以便你能够为用户显示结算页面。你可以如下修改 `cart.php`：

```php
<?php
require 'checkout.php';
function display($cart) {
    // (显示购物车)
}
if ($_GET['action'] == 'checkout') {
    display($_SESSION['cart']);
} else {
    display($_SESSION['cart']);
}
?>
```

不幸的是，这里有一个问题：`cart.php` 和 `checkout.php` 都包含一个名为 `display()` 的函数。当你尝试在 `cart.php` 顶部使用 `require` 语句包含 `checkout.php` 时，PHP 引擎会生成以下错误：

```
PHP Fatal error: Cannot redeclare display() (previously declared in cart.php:4) in checkout.php on line 4
```

这是因为在一个中不能有两个同名的函数（即使这些函数最初在不同的文件中）。此外，`cart.php` 结尾的决策代码显然是无意义的：PHP 如何知道在每情况下调用哪个 `display()` 呢？

从 PHP 5 开始，你可以通过使用命名空间来避免此类问题。命名空间是一个容器，你可以在其中为你创建的每个应用程序或库放置函数、类和常量名。这允许你在不同的脚本或库中使用相同的名称，而没有任何冲突的风险。

你可以将命名空间想象成文件系统中的文件夹：你不能在同一个文件夹中拥有两个名为 `myfile.txt` 文件，但你可以在一个文件夹中有一个 `myfile.txt`，在另一个文件夹中有另一个 `myfile.txt`。

在 PHP 中创建命名空间，你使用 `namespace` 关键字后跟命名空间名：

```php
<?php
namespace MyLibrary;
function myFunction() {
    // 脚本其余部分
}
?>
```

命名空间声明必须是脚本中开启 `<?php` 标签之后的第一行。此外，`<?php` 标签之前不能出现任何字符（例如，你不能在 PHP 代码之前放置任何 HTML 标记）。

一旦你在脚本顶部声明了命名空间，该脚本中的所有代码都属于该命名空间。

> 虽然在理论上你可以在单个脚本文件中声明多个命名空间，但这不是良好的编码习惯。

如果你想使用在相同命名空间定义的类、函数或常量，只需正常编写其名称即可：

```php
$result = myFunction();
```

如要从命名空间外部使用命名空间的类、函数或常量，编写命名空间名，后跟一个反斜杠 `\`，然后是类、函数或常量名：

```php
$result = MyLibrary\myFunction();
```

你现在知道你需要将你的购物车和结算功能分开了。这里是修改后的 `checkout.php`：

```php
<?php
namespace Checkout
function display($cartContents) {
    // (显示结算)
}
?>
```

你可以看到结算库现在被赋予了它命名空间 `Checkout`。这里是新的 `cart.php` 脚本：

```php
<?php
require "checkout.php";
function display($cart) {
    // 显示 (购物车)
}
if ($_GET["action"] == "checkout") {
    Checkout\display($_SESSION["cart"]);
} else {
    display($_SESSION["cart"]);
}
?>
```

现在，`cart.php` 通过以下方式调用 `checkout.php` 中定义的 `display()` 函数：

```php
Checkout\display($_SESSION["cart"]);
```

同时，它通过简单使用以下方式调用 `cart.php` 自身定义的 `display()` 函数：

```php
display($_SESSION["cart"]);
```

多亏使用了命名空间，两个 `display()` 函数的名称不再冲突了。

你还可以创建子命名空间，就像文件系统中的子文件夹。这允许你创建一个命名空间层次结构。你用反斜杠字符分隔每个命名空间层。例如，以下代码在 `MyStore` 命名空间内声明了 `Checkout` 命名空间：

```php
<?php
namespace MyStore\Checkout;
?>
```

你可以使用相对表示法指定命名空间，就像处理相对路径一样。例如，要从 `MyStore` 命名空间内的代码中调用 `MyStore\Checkout\display()`，你可能会写：

```php
<?php
namespace MyStore;
require "checkout.php";
Checkout\display($_SESSION["cart"]);
?>
```

如要从不相关的命名空间内部使用命名空间类、函数或常量，你需要在命名空间名称开头添加反斜杠，这样 PHP 就知道你指的是绝对路径：

```php
<?php
namespace AnotherNamespace;
\MyStore\Checkout\display();
?>
```

## 第 20 章：编写高质量代码

- 在函数调用中何时使用空格：本书倾向于在函数参数周围使用空格，但在函数名和左括号之间不留空格：

```
include("animal_functions.php");
```

- 如何格式化流程结构：本书在条件判断括号周围和内部都使用空格：

```
if ($queryType == "animal") {
```

- 如何命名标识符：一种常用的命名技术是使用下划线分隔标识符内的单词（`variable_name` 或 `CONSTANT_NAME`）；由于 C 语言编程中使用了这种惯例，这有时被称为“C 风格”。另一种常用技术是将标识符中的每个单词的首字母大写（可选包括第一个字母）（`VariableName` 和 `variableName`）；这些约定通常被称为大驼峰命名（upper camel case）和小驼峰命名（lower camel case）；请遵循本书的规定：

- 类名使用大写（`MyClass`）
- 函数、方法和变量名使用小写（`myMethod()` 和 `$variable`）
- 常量名使用大写字母加下划线（`MY_CONSTANT`）
- 预定义字面值使用小写（`true`, `false`, `null`）

你可以发明自己的编码标准（如果有帮助，可以正式写出来）或采用现有的标准。常见的标准包括：

- PEAR 编码标准：http://pear.php.net/manual/en/standards.php
- Java 代码规范：http://java.sun.com/docs/codeconv/
- GNU 编码标准：http://www.gnu.org/prep/standards/

使用现成标准还是创建自己的标准并不重要。重要的是，一旦你采纳了某种标准，就应该将其一致地应用于你所有的 PHP 代码中。

## 为代码编写文档

为代码编写良好的文档需要自律，但它是构建应用程序的一个重要方面。虽然没有文档的代码在编写时完全可以理解，但代码在六个月后你再次回看时，往往会变得难以理解。更此外，如果其他开发者需要处理你没有文档的代码，他们将很难弄清楚这些代码的意图。

## 第三部分：在中使用 PHP

记录 PHP 代码的主要方法是在代码中添加注释。到此时你可能已经知道 PHP 中可以创建两种注释：

- 单行注释：以两个斜杠 `//` 或井号 `#` 开头。
- 多行注释：以 `/*` 开头，以 `*/` 结束。

## 编写良好的注释

编写注释非常简单，但如何编写良好的注释呢？首先，注释需要解释一段代码的作用（或意图）。然而，不要陈述显而易见的事。以下是一个糟糕注释的示例：

```
for ($i=0; $i < count($users); $i++) { // 从 0 循环到 count($users) -
$users[$i]->insert(); //为用户调用 insert() 方法
}
```

这些注释所只是重复了阅读代码本身就能看出显而易见的内容；它们没有为代码增加额外的含义。下面的注释会有用得多：

```
// 将所有用户插入到数据库
for ($i=0; $i < count($users); $i++) {
    $users[$i]->insert();
}
```

这让读者能够从更高层面的视角理解代码正尝试做什么。

改进注释的另一种方法是提高可读性的格式化。在注释开始之前（可能可能在注释之后）添加一个空行；在使用行内注释时，在 `//` 后添加一个空格；并将跨行的行内注释对齐。考虑以下格式化糟糕的注释：

```
//Retrieve all users
$users = User::getAll();
/*
Add the users to the database.
Each user's modification time is updated
before the user is added.
*/
for ($i=0; $i < count($users); $i++) {
    $users[$i]->updateModDate(); //Set the modification time
    $users[$i]->insert(); //Insert the user
}
```

你可以看出，很难判断脚本哪些部分是注释，哪些部分是代码。这是一个改进后的版本：

```
// 获取所有用户
$users = User::getAll();
/*
 将所有用户添加到数据库。
 在添加用户之前更新每个用户的修改时间。
*/
for ( $i=0; $i < count($ users ); $i++ ) {
    $users[$i]->updateModification(); // 修改时间
    $users[$i]->insert();
}
```

通过在注释之间添加水平和垂直空间并对齐两个行内注释，代码变得更具读性。

另一种良好的注释策略是在编写代码的同时编写注释，而不是事后补写。事实上，在代码还停留在脑海中的这个阶段编写注释更容易。此外，因为注释描述了代码的意图，注释会鼓励你思考如何以及为什么要编写那段代码。事实上，为了增加一倍自律性，尝试在编写代码之前先写注释！

通过添加大量有帮助的注释使代码更易于读，你可以通过使用有意义的变量、函数和方法名来改进代码。以下代码足够清晰，不需要任何注释：

```
$jim = new User();
$jim->setFirstName("Jim");
$jim->setLastName("Smith");
$jim->addToDatabase();
```

## 使用 phpDocumentor 生成外部文档

虽然代码注释很有用，但如果文档与代码文件分离，开发者可能更容易获得应用程序的更高层面的概览。

`phpDocumentor` 是一个 PEAR 包，用于更新外部文档文件的生成。它读取你的 PHP 脚本文件，并使用代码中的注释生成文档。通过以特殊方式格式化注释，你可以为 phpDocumentor 提供关于代码的额外信息，例如每个变量的作用范围和数据类型，以及变量、函数和类之间的关系。

你可以像安装其他 PEAR 包一样安装 phpDocument（安装 PEAR 包的更多信息请参见第 15 own 章）：

```
$ php install --aldeps phpDocument
downloading phpDocument-1.4.2.tgz
Starting to download PhpDocument-1.4.2.tgz (2,421,028 bytes)
-------------------------------------------------------
... done: 2,421,028 bytes
downloading XML_Beautifier-1.2.0.tgz
Starting to download XML_Beautifier-1.2.0.tgz (12,948 bytes)
-------------------------------------------------------
... done: 12,948 bytes
downloading XML_Parser-1.3.2.tgz
```
