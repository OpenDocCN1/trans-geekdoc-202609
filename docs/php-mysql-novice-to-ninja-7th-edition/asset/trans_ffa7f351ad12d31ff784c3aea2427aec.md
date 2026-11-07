
# 接口概述

你会注意到它看起来有点像一个类。它有一个命名空间、一个名称和一个方法。然而，接口与类之间的区别在于，接口只包含方法头（第一行）。它不包含任何逻辑，并且方法后面没有大括号（`{` 和 `}`）。

让我们将接口保存在 `Ninja` 目录中，命名为 `Website.php`。与类文件一样，接口文件也可以由自动加载器加载。

我们现在可以在 `EntryPoint` 中对接口进行类型提示：

```
public function __construct(private \Ninja\Website $website) {
}
```

目前，这将阻止我们将 `Ijdb\JokeWebsite` 的实例传递给 `EntryPoint` 的 `__construct`。然而，我们可以让 `Idjb\JokeWebsite` 实现该接口。

**示例：[CMS-入口点-接口](https://github.com/spbooks/phpmysql7/tree/CMS-EntryPoint-Interface)**

```
<?php
namespace Ijdb;
class JokeWebsite implements \Ninja\Website {
        //...
```

这有两个影响：

* 类 `Ijdb\JokeWebsite` 必须包含接口中描述的方法。如果没有，将显示错误。
* `Ijdb\JokeWebsite` 类现在可以使用接口进行类型提示。

现在，当我们构建在线商店或其他任何网站时，我们可以通过实现接口来创建路由类的新版本：

```
namespace Shop;
class JokeWebsite implements \Ninja\Website {
  public function getController(string $controllerName) {
        //...
    }

    public function getDefaultRoute() {
        //...
    }
}
```

接口对于我们构建的这种通用框架非常有用。通过提供一组接口，每个网站都可以提供实现这些接口的类，从而保证框架代码和项目特定代码能够很好地契合。

你可以将电视连接到蓝光播放器、卫星电视接收器、游戏主机，甚至是电脑，因为它们都使用 HDMI。电视制造商不知道会连接什么，但只要遵循 HDMI 标准的东西就能与电视配合使用。同样，任何使用 `Ninja\Website` 接口的东西都将与我们创建的 `Ninja` 框架配合工作。

接口在正确使用时，是连接框架代码和项目特定代码的非常强大的工具。

## 返回类型提示

我们上面的代码中还有一个小小的空白。任何实现 `Ninja\Website` 接口的类都必须具有 `getController` 和 `getDefaultRoute` 函数，但如果这些函数什么都不做怎么办？

请看这段代码：

```
$controller = $this->website->getController($controllerName); 

$page = $controller->$action(...$route);
```

由于我们使用了类型提示，当执行到这段代码时，可以保证 `` `$this->website` `` 变量包含一个实现了 `Ninja\Website` 的类。要执行到这一行，`` `$this->website` `` 必须是一个对象，并且该对象必须包含一个名为 `getController()` 的方法。

但是如果 `getController` 方法返回一个字符串会怎样？如果它根本不返回任何东西呢？

有可能在执行 `` `$controller->$action(...$route);` `` 时，`` `$controller` `` 变量实际上是一个字符串。

在声明方法时——无论是在接口还是类中——你可以添加返回类型提示，指定函数必须返回的值类型。

让我们看一个非常简单的例子：

```
function add(int $num1, int $num2): int {
    $result = $num1 + $num2;
    return $result;
}
```

在参数列表之后，有一个返回类型提示——`: int`。你可以在这里指定任何类型，它告诉 PHP 返回值必须是该类型。如果 `` `$result` `` 变量是字符串、对象或除 `int` 之外的任何东西，脚本将停止并显示错误。

与方法和参数一样，此返回类型也可以在接口中强制执行：

```
namespace Ninja;

interface Website {
    public function getDefaultRoute(): string;
    public function getController(string $controllerName): object;
}
```

通过在接口中指定返回类型，实现该接口的任何类也必须指定返回类型。

考虑这段代码运行时：

```
$controller = $this->website->getController($controllerName); 

$page = $controller->$action(...$route);
```

`` `$controller` `` 变量不能是 `object` 之外的任何东西，因为如果 `getController()` 返回除 `object` 之外的任何内容，脚本将停止。

由于类中的方法必须遵循接口，`Ijdb\JokeWebsite` 类也必须更新以提供返回类型提示。完整的 `Ijdb\JokeWebsite` 类现在如下所示的代码。

```
namespace Ijdb;
class JokeWebsite implements \Ninja\Website {
    public function getDefaultRoute(): string {
        return 'joke/home';
    }

    public function getController(string $controllerName): object {
        $pdo = new \PDO('mysql:host=mysql;dbname=ijdb;charset=utf8mb4', 'ijdbuser', 'mypassword');

        $jokesTable = new \Ninja\DatabaseTable($pdo, 'joke', 'id');
        $authorsTable = new \Ninja\DatabaseTable($pdo, 'author', 'id');

        if ($controllerName === 'joke') {
            $controller = new \Ijdb\Controllers\Joke($jokesTable, $authorsTable);
        }
        else if ($controllerName === 'author') {
            $controller = new \Ijdb\Controllers\Author($authorsTable);
        }

        return $controller;
    }
}
```

## 错误处理

在结束本章之前，还有一个最后的收尾工作需要完成。当有人访问没有对应控制器的 URL（例如 `/doesnt/exist`）时会发生什么？或者当有人尝试在存在但控制器中没有对应方法的控制器上运行操作时会发生什么（例如 `/joke/search`）？

如果有人指定一个不存在的控制器，它实际上会在 `Website` 类的 `getController` 方法中导致错误。目前，方法头说它总是返回一个对象：

```
public function getController(string $controllerName): object {
```

但如果你仔细查看代码，返回变量 `` `$controller` `` 可能永远不会被设置。请看当前的方法：

```
if ($controllerName === 'joke') {
    $controller = new \Ijdb\Controllers\Joke($jokesTable, $authorsTable);
}
else if ($controllerName === 'author') {
    $controller = new \Ijdb\Controllers\Author($authorsTable);
}

return $controller;
```

如果有人访问 `/doesnt/exist`，`` `$controllerName` `` 变量将被设置为 `doesnt`，而 `` `$controller` `` 变量将永远不会被设置。我们可以添加一个 else 块，像这样：

```
if ($controllerName === 'joke') {
    $controller = new \Ijdb\Controllers\Joke($jokesTable, $authorsTable);
}
else if ($controllerName === 'author') {
    $controller = new \Ijdb\Controllers\Author($authorsTable);
}
else {
    $controller = new \Ijdb\Controllers\Error();
}
```

但这需要为此错误消息页面创建一个完整的控制器。相反，让我们在没有指定 `` `$controllerName` `` 的控制器时将 `` `$controller` `` 变量设置为 `null`：

```
if ($controllerName === 'joke') {
    $controller = new \Ijdb\Controllers\Joke($jokesTable, $authorsTable);
}
else if ($controllerName === 'author') {
    $controller = new \Ijdb\Controllers\Author($authorsTable);
}
else {
    $controller = null;
}
```

如果你测试这个，它会引发错误，因为方法头包含 `: object`，指定此方法必须返回一个对象。如果 `` `$controller` `` 被设置为 `null`，语句 `` `return $controller` `` 将返回 `null`，而 `null` 不是对象。

这实际上是编程中非常常见的问题。想象一个搜索某物的函数：你搜索的东西可能不存在。

PHP 允许我们通过在返回类型前加上问号来轻松处理这种情况，如下所示：
