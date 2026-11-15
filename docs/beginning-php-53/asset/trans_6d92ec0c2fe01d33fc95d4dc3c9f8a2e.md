

在当前脚本执行期间只包含一次。如果您再次调用 `include_once()` 或 `require_once()` 来包含同一文件，则不会发生任何事情。

因此，可以通过对 `mouse.php` 和 `cat.php` 文件进行一些小调整来解决之前的问题：

```
mouse.php:

<?php
include_once( "animal_functions.php" );
echo animalSpeak( "mouse" ) . "<br />"; // Displays "squeak";
?>
```

```
cat.php:

<?php
include_once( "animal_functions.php" );
echo animalSpeak( "cat" ) . "<br />"; // Displays "meow";
?>
```

现在，`animal_functions.php` 将只被包含一次（在 `mouse.php` 中），因此 `animalSpeak()` 函数将只被声明一次。`display_animal_sounds.php` 脚本现在将正确运行，显示以下输出：

- squeak
- meow

## 使用包含路径

在处理大型应用程序时，另一个问题是跟踪要包含的文件的位置。假设您已将所有通用库代码（包括 `animal_functions.php`）组织到位于 `/home/joe/lib` 的中心文件夹中。您在 `/home/joe/htdocs` 中有一个网站，其文档根目录包含之前所示的 `mouse.php` 文件。`mouse.php` 如何引用 `animal_functions.php`？它可以使用绝对路径：

```
include_once( "/home/joe/lib/animal_functions.php" );
```

或者，它可以使用相对路径：

```
include_once( "../lib/animal_functions.php" );
```

这两种方法都可行，但生成的代码可移植性不高。例如，假设网站需要部署到不同的 Web 服务器上，其中库代码存储在 `/usr/lib/joe` 文件夹中。每一行包含 `animal_functions.php`（或任何其他库文件）的代码都需要使用新路径进行更新：

```
include_once( "/usr/lib/joe/animal_functions.php" );
```

为了解决这个问题，您可以使用 PHP 的 `include_path` 指令。这是一个字符串，包含要搜索以查找可包含文件的路径列表。每个路径之间用冒号（Linux 服务器上）或分号（Windows 服务器上）分隔。PATH_SEPARATOR 常量包含当前系统使用的分隔符。

路径按照它们在字符串中出现的顺序进行搜索。您可以通过调用 `get_include_path()` 函数来显示当前的 `include_path` 值（该值通常从 `php.ini` 配置文件中获取）：

```
echo get_include_path(); // Displays e.g. ".:/usr/local/lib/php"
```

在此示例中，`include_path` 指令包含两个路径：当前目录 (`.`) 和 `/usr/local/lib/php`。

要设置新的 `include_path` 值，请用——您猜对了——`set_include_path()`：

```
set_include_path( ".:/home/joe/lib" );
```

> 如刚才所示，将当前目录 (`.`) 放在包含路径的最前面是个好主意。这意味着 PHP 始终会先在当前目录中搜索所需文件，这通常就是您想要的结果。

您通常只需在应用程序开始时设置一次包含路径。设置包含路径后，您只需指定文件名即可包含路径中的任何文件：

```
include_once( "animal_functions.php" );
```

在此示例中，PHP 引擎会在当前目录中查找 `animal_functions.php`。因为那里没有，所以它会接着在 `/home/joe/lib` 中查找，并在那里找到它。

您可以通过在包含路径中创建子文件夹来组织代码库。假设您将 `animal_functions.php` 文件放入名为 `animals` 的子文件夹中。那么该文件的绝对路径将是：

`/home/joe/lib/animals/animal_functions.php`

要在脚本中包含此文件，您可以这样写，例如：

```
require( "animals/animal_functions.php" );
```

请注意，您的脚本现在更具可移植性。要将应用程序移动到路径不同的新服务器，您只需在 `set_include_path()` 调用中指定新路径即可。

顺便说一句，将新的包含路径添加到现有包含路径中，而不是替换现有路径，通常是个好主意。这意味着任何其他库文件（例如 PEAR 包）仍然可以被找到。要做到这一点，您可以使用以下代码：

```
set_include_path( get_include_path() . PATH_SEPARATOR . "/home/joe/lib" );
```

如果您需要将包含路径重置回默认设置，只需调用 restore_include_path() 即可。

## 动态包含

由于 include() 及其相关函数是 PHP 函数，您可以在 PHP 脚本的任何位置调用它们——包括在条件代码块或循环内部。例如，有时根据条件包含不同的文件很有用：

```
if ( $queryType == "animal" ) {
include( "animal_functions.php" );
} else {
include( "plant_functions.php" );
}
```

您甚至可以使用变量的值来确定要包含哪个文件。这是动态仅包含所需库文件的简便方法：

```
include( $queryType . "_functions.php" );
```

如果您这样做，请先出于安全考虑验证并清理变量的值。有关此主题的更多信息，请参见本章稍后的“检查输入和编码输出”。

## 使用命名空间避免冲突

有时您会发现，希望在同一应用程序中为不同目的使用相同的函数名、类名或常量名。如果您正在处理非常大的应用程序，或者应用程序使用了许多库，就可能发生这种情况。通常，这会导致问题，因为您不能使用相同的名称来引用多个函数、类或常量。

例如，假设您正在开发一个在线商店应用程序。您可能有一个名为 cart.php 的购物车脚本，其中带有一个 display() 函数用于显示购物车标记：

```
<?php
function display( $cart ) {
// (display the cart)
}

...

display( $_SESSION["cart"] );
?>
```

到目前为止，一切正好。现在假设您之前为另一个应用程序编写了一些结账库代码，该代码存储在 `checkout.php` 中。除了其他内容外，该文件还包含一个名为 `display()` 的函数，用于显示结账页面：

```
<?php
function display( $cartContents ) {
    // (display the checkout)
}

...

?>
```

您希望将此库文件 `checkout.php` 包含在 `cart.php` 中，以便为用户显示结账页面。您可以按照以下方式修改 `cart.php`：

```
<?php
require "checkout.php";

function display( $cart ) {
    // (display the cart)
}

if ( $_GET["action"] == "checkout" ) {
    display( $_SESSION["cart"] );
} else {
    display( $_SESSION["cart"] );
}

?>
```

不幸的是，这里存在一个问题：`cart.php` 和 `checkout.php` 都包含一个名为 `display()` 的函数。当您尝试在 `cart.php` 顶部使用 `require` 语句包含 `checkout.php` 时，PHP 引擎会生成以下错误：

> PHP 致命错误：无法重新声明 display()（之前在 cart.php:4 中声明）在 checkout.php 第 4 行

这是因为在一个脚本中不能有两个同名函数（即使这些函数最初位于不同的文件中）。此外，`cart.php` 末尾的决策代码显然毫无意义：PHP 如何知道在每种情况下应调用哪个 `display()` 函数？

从 PHP 5.3 开始，您可以使用命名空间来避免此类问题。`namespace` 是一个容器，您可以在其中放置为每个应用程序或库创建的函数名、类名和常量名。这样，您可以在不同的脚本或库中使用相同的名称，而不会有任何冲突风险。

您可以将命名空间视为类似于文件系统中的文件夹：在同一文件夹中不能有两个名为 myfile.txt 的文件，但可以在一个文件夹中有一个 myfile.txt，在另一个文件夹中有一个不同的 myfile.txt。

在 PHP 中创建命名空间时，请使用 namespace 关键字，后跟命名空间名称：

```
<?php
namespace MyLibrary;

myFunction() {
    ...
}

// rest of script here
?>
```

命名空间声明必须是脚本中紧随开头 <?php 标签之后的第一行。此外，<?php 标签之前不能出现任何字符（因此例如无法在 PHP 代码之前放置 HTML 标记）。

在脚本顶部声明命名空间后，该脚本中的所有代码都属于该命名空间。

> 尽管您理论上可以在单个脚本文件中声明多个命名空间，但这不是良好的编码实践。

如果要使用在同一命名空间中定义的类、函数或常量，只需正常编写其名称：

```
$result = myFunction();
```

要从命名空间外部使用命名空间中的类、函数或常量，请编写命名空间名称，后跟反斜杠 (\)，再跟类名、函数名或常量名：

```
$result = MyLibrary\myFunction();
```

您现在了解了使购物车和结账正常工作所需的所有知识。以下是修订后的 checkout.php：

```
<?php
namespace Checkout;

function display( $cartContents ) {
    // (display the checkout)
}
?>

