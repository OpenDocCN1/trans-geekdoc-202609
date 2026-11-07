
此约定被称为 **PSR-4**（PSR 代表 PHP Standards Recommendations），并且被几乎所有现代 PHP 项目使用。每个类都应包含在直接映射到其命名空间和类名的文件中。完整的类名（包括命名空间）应与目录和文件名完全匹配，包括大小写敏感。PSR-4 标准还提供了一些其他规则，这里就不展开了。要了解更多关于 PSR-4 的信息，请查看 [PHP-FIG 网站](http://www.php-fig.org/psr/psr-4/)。

## 使用 PSR-4 进行自动加载

使用 PSR-4，将命名空间中的类名转换为文件路径变得很简单。让我们用这个 PSR-4 版本替换 `autoload.php`：

```
<?php
function autoloader($className) {
    $fileName = str_replace('\\', '/', $className) . '.php';

    $file = __DIR__ . '/../' . $fileName;

    include $file;
}

spl_autoload_register('autoloader');
```

当自动加载器在命名空间内触发类时，会传递完整的类名，包括命名空间。例如，当加载 `EntryPoint` 时，自动加载器会得到类名 `Ninja\EntryPoint`。

行 `str_replace('\\', '/', $className) . '.php';` 将反斜杠替换为正斜杠以在文件系统中表示文件。`Ninja\EntryPoint` 变为 `Ninja/EntryPoint.php`，引用该文件。

有了自动加载器，我们现在可以从 `IjdbRoutes.php` 中删除 `include` 行，这些行加载 `JokeController` 和 `AuthorController`：

```
include __DIR__ . '/../controllers/JokeController.php';
include __DIR__ . '/../controllers/AuthorController.php';
```

在编辑这些 include 行时，数据库连接也在此处被包含。由于它仅在此类中使用，我们只需将 `DatabaseConnection.php` 中的代码移入此类即可。找到这一行：

```
include __DIR__ . '/../includes/DatabaseConnection.php';
```

用 `DatabaseConnection.php` 的内容替换它：

```
$pdo = new PDO('mysql:host=mysql;dbname=ijdb;charset=utf8mb4', 'ijdbuser', 'mypassword');
```

`Joke` 类中不应再有任何 `include` 行。

然后我们应更改对控制器的引用以使用完整的类名：

```
$controller = new \Ijdb\Controllers\Joke($jokesTable, $authorsTable);
```

快完成了！我们正接近使用新的文件和命名空间结构再次让网站运行起来。然而，如果我们尝试加载其中一个页面，会看到此错误：

```
Uncaught TypeError: Argument 1 passed to Ninja\DatabaseTable::__construct() must be an instance of Ninja\PDO, instance of PDO given
```

要修复它，我们可以打开 `DatabaseTable.php` 并将构造函数中的类型提示从 `PDO` 改为 `\PDO`。我们看到此错误是因为命名空间是 *相对* 的。如果你在类型提示中或 `new` 关键字后提供对类名的引用，PHP 将在当前命名空间中查找具有该名称的类。我们还需要在 `Joke.php` 和 `DatabaseTable.php.` 中将 `DateTime` 替换为 `\DateTime`，并在此 `DatabaseTable.php` 中将 `PDOException` 替换为 `\PDOException`。

由于 `DatabaseTable` 类位于 `Ninja` 前缀内，PHP（没有反斜杠前缀）将希望加载类 `\Ninja\PDO` 而不是内置的 PHP 类 `PDO`。

`PDO` 类位于所谓的 **global namespace** 中——意味着它是一个存在于最顶层的类，实际上不在命名空间内。要引用全局命名空间中的类，我们必须为其添加反斜杠前缀。

保存 `DatabaseTable.php` 并刷新页面。还有一个错误需要修复：

```
Fatal error: Uncaught TypeError: Argument 1 passed to Ijdb\Controllers\Joke::__construct() must be an instance of Ijdb\Controllers\DatabaseTable, instance of Ninja\DatabaseTable given
```

这与上面相同的问题。因为没有指定命名空间，PHP 会在 *当前* 命名空间中查找名为 `DatabaseTable` 的类。由于控制器位于 `Ijdb` 命名空间中，PHP 将尝试加载类 `Ijdb\DatabaseTable`。

我们可以用与上面相同的方式修复——通过提供带命名空间的类名（PHP 将其称为 **fully qualified class name**）：`\Ninja\DatabaseTable`。但更优雅的解决方案是将类 `DatabaseTable` *import* 到当前命名空间。

我们可以在命名空间声明之后使用 `use` 关键字来完成此操作。

**Example: [CMS-EntryPoint-Namespaces](https://github.com/spbooks/phpmysql7/tree/CMS-EntryPoint-Namespaces)**

```
<?php
namespace Ijdb\Controllers;
use \Ninja\DatabaseTable;

class Joke {
    // …
```

如果我们已正确完成所有操作，应该能够刷新网站并再次看到一切正常运行。

我们在这里做了很多更改，但仅限于代码的结构。大多数代码与之前相同；我们只是移动了它们的位置。回顾一下，我们做了以下操作：

*   将我们的代码拆分为类，区分特定于笑话网站的代码和可在任何未来网站上使用的代码
*   将所有类组织在 `Ijdb` 目录（用于项目特定文件）或 `Ninja` 目录（用于框架文件）中
*   为所有类添加了命名空间
*   通过实现 PSR-4–compatible 自动加载器移除了所有类的 include 语句

### Composer

大多数现代 PHP 应用程序使用名为 Composer 的工具来处理所有自动加载。它还用于快速轻松地下载和安装第三方库。这超出了本书的范围，但如果你遵循 PSR-4 约定，当你想开始使用它时，你的类就可以直接使用了，并且你可以使用 Composer 的自动加载器作为我们刚刚编写的 `autoload.php` 的即插即用替代品。

当你开始使用 Composer 时，只需将以下代码添加到你的 `composer.json` 文件中：

```
{
  "autoload": {
    "psr-4": {
        "Ninja\": "Ninja",
        "Ijdb\": "Ijdb"
    }
  }
}
```

有关 Composer 的概述，请查看 SitePoint 文章 “[重新介绍 Composer，现代 PHP 应用的基石](https://www.sitepoint.com/re-introducing-composer/)”。

## 以及 REST

我们路由器的当前迭代使用非常简单的方法。每个路由都是来自 URL 的字符串，映射到控制器并调用特定操作。

如果我们继续使用这种方法，我们很快就会发现自己在控制器中重复逻辑。

我们的编辑笑话表单包含以下逻辑：*if the form is submitted, process the submission, otherwise display the form*。

此逻辑将适用于网站上的任何表单。同样，我们可以设想未来其他功能需要在控制器中实现类似的逻辑。例如：*display the page if the user is logged in, otherwise display the login form*。

当编辑笑话表单被提交时，它使用 `POST` 方法。对网站页面的任何其他请求都将使用 `GET` 方法。

PHP 可以检测页面是使用 `GET` 还是 `POST` 请求的。变量 `$_SERVER['REQUEST_METHOD']` 由 PHP 创建，并将包含字符串 `GET` 或字符串 `POST`，具体取决于浏览器如何请求页面。你已经看到 `GET` 和 `POST` 可以定义为表单的 `action`，但仅在浏览器中导航到页面也是一种 `GET` 请求。

我们可以在 `EntryPoint` 类中使用它来确定表单是否已提交，并在表单提交时调用不同的控制器操作：

```
//...

$controllerName = array_shift($route);
$action = array_shift($route);

if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $action .= 'Submit';
}

$controller = $this->website->getController($controllerName); 

$page = $controller->$action(...$route);

//...
