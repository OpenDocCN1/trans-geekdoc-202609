
# 添加登录检查

有几种方法可以添加登录检查。我们可以添加一个方法来返回需要登录才能查看的页面列表。这需要在 `Website` 类中而不是 `EntryPoint` 类中，因为 URL 列表在每个网站上都相同。

## 使用 `getSecurePages` 的初始方法

这里有一个可行但不理想的方法。我们可以让 `Website` 类提供一个页面列表，其中包含仅对已登录用户可用的 URL 列表：

```
class JokeWebsite implements \Ninja\Website {
    public function getSecurePages(): array {
        return ['joke/edit', 'joke/delete'];
    }
}
```

然后我们可以让 `EntryPoint` 类调用此方法，并在当前页面在列表中时应用一些逻辑：

```
class EntryPoint {
 public function run(string $uri, string $method) {
        try {
            $this->checkUri($uri, $method);

            if ($uri == '') {
                $uri = $this->website->getDefaultRoute();
            }

            $requiresLogin = $this->website->getSecurePages();

            $authorsTable = new \Ninja\Database($pdo, 'authors', 'id');
            $authentication = new Authentication($authorsTable, 'email', 'password');

            if (in_array($uri, $this->website->getSecurePages()) && !$authentication->isLoggedIn()) {
                header('location: /login');
                exit();
            }
        }
    }
}
```

上面的代码创建了之前提到的 `Authentication` 类的实例，然后从 `Website` 类获取需要用户登录才能查看的页面列表，然后使用 `in_array()` 检查当前的 `$uri` 是否在登录受限页面列表中。如果 URL 在需要登录的页面列表中且用户未登录（`$authentication->isLoggedIn()` 返回 false），则用户将被重定向到登录页面。

我们添加的登录检查如下所示：

```
$authorsTable = new \Ninja\DatabaseTable($pdo, 'authors', 'id');
$authentication = new Authentication($authorsTable, 'email', 'password');
if (in_array($uri, $this->website->getSecurePages()) && !$authentication->isLoggedIn()) {
    header('location: /login');
    exit();
}
```

## 硬编码值和限制

这段代码包含大量特定于笑话网站的硬编码值。我们可以在 `Website` 类中添加相关方法来处理这个问题：

```
$authentication = $this->website->getAuthentication(); //get the Authentication instance for this particular website from the `website` instance
if (in_array($uri, $this->website->getSecurePages()) && !$authentication->isLoggedIn()) {
    header('location: ' . $this->website->getLoginUrl()); //get the URL of the login page for this particular website from the `website` instance
    exit();
}
```

我没有给出 `Website` 类中对应的方法，因为我们不会使用这种方法。然而，在此示例中，`Authentication` 类由 `Website` 类配置并提供。`Joke` 网站可以提供其 `Authentication` 类的配置（链接到具有 `email` 和 `password` 列名的 `author` 表），而另一个网站可以提供具有不同配置的 `Authentication` 实例。

虽然这样可行，而且具有通用性，但实际上非常受限。虽然到目前为止我们一直将可能在不同网站上重复的代码放在 `EntryPoint` 类中，但在这种情况下，这种方法实际上会适得其反。这种确切的登录检查可能在每个网站上都会使用，而且这种方法仍存在一些问题：

* 它假设每个网站都有只能在登录后查看的页面。
* 它将 `EntryPoint` 类绑定到我们之前创建的 `Authentication` 类。
* 它假设如果有人在未登录的情况下尝试访问受限页面，我们应该只重定向到登录页面。

它没有能力执行以下任何替代方案：

* 使用他人编写的不同登录代码，而不是我们的 `Authentication` 类。
* 当有人尝试查看受限页面时，显示错误消息而不是重定向。
* 记录未登录时查看受限页面的尝试。
* 为不同用户设置不同的权限，以便某些用户可以查看某些页面，而其他已登录用户则不能。

## 重构为 `Website::checkLogin`

而不是尝试将其放在 `EntryPoint` 类中，我们将在 `Website` 类中创建一个名为 `checkLogin` 的方法，该方法接收 URI 然后确定接下来应该发生什么。`EntryPoint` 只需调用该方法并提供正在查看的页面的 URI：

```
class EntryPoint {
 public function run(string $uri, string $method) {
        try {
            $this->checkUri($uri, $method);

            if ($uri == '') {
                $uri = $this->website->getDefaultRoute();
            }

            $route = explode('/' $uri);

            $controllerName = array_shift($route);
            $action = array_shift($route);

            $this->website->checkLogin($controllerName . '/' . $action);
        }
    }
}
```

`Website` 类将提供 `checkLogin` 方法，该方法接收 `$uri` 并确定查看它的人是否应该能够查看该页面。由于 `$uri` 变量可能包含像 `joke/edit/1` 这样的参数，我使用 `$controllerName` 和 `$action` 重构了它，使其仅变为 `controller/action`，不带任何额外参数。

## 将表实例提升为类属性

在添加该方法之前，我们有一个潜在问题。`$authorsTable` 实例需要在 `getController` 方法（其中当前正在创建它）和即将添加的 `checkLogin` 方法中可用。为了解决这个问题，我们将变量提升为类变量，并在构造函数中创建对象（以及它们所需的数据库连接）：

```
namespace Ijdb;
class JokeWebsite implements \Ninja\Website {
    private \Ninja\DatabaseTable $jokesTable;
    private \Ninja\DatabaseTable $authorsTable;

    public function __construct() {
        $pdo = new \PDO('mysql:host=mysql;dbname=ijdb;charset=utf8mb4', 'ijdbuser', 'mypassword');

        $this->jokesTable = new \Ninja\DatabaseTable($pdo, 'joke', 'id');
        $this->authorsTable = new \Ninja\DatabaseTable($pdo, 'author', 'id');
    }

    public function getDefaultRoute(): string {
        return 'joke/home';
    }

    public function getController(string $controllerName): ?object {
        if ($controllerName === 'joke') {
            $controller = new \Ijdb\Controllers\Joke($this->jokesTable, $this->authorsTable);
        }
        else if ($controllerName === 'author') {
            $controller = new \Ijdb\Controllers\Author($this->authorsTable);
        }
        else {
            $controller = null;
        }

        return $controller;
    }
}
```

通过将 `$authorsTable` 和 `$jokesTable` 提升为类变量，它们将对该类的任何方法都可用。由于我们没有使用构造函数参数提升来创建变量，两者都需要使用 `private` 关键字定义为类变量。根据惯例，类变量定义在类的顶部。创建这些类变量后，它们需要在 `getController` 方法中通过 `$this->` 前缀访问。

现在我们可以在类的任何方法中访问 `$this->authorsTable` 对象，让我们添加新的 `checkLogin` 方法，该方法将接收当前页面的 URI 并确定接下来会发生什么：
