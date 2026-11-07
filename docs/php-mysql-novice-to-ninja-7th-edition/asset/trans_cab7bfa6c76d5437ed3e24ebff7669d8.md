
这个方法非常简单：如果 `REQUEST_METHOD` 是 `POST`，它会将单词 `submit` 追加到 `$action` 变量。也就是说，如果你正在访问 `/joke/edit` 且请求类型为 `POST`，`$action` 变量将被设置为 `editSubmit`，并且控制器中以 `Submit` 结尾的方法将被调用。

让我们将 `edit` 方法拆分为两个不同的方法——`edit` 用于显示表单，`editSubmit` 用于处理表单提交：

```
public function editSubmit() {
    $joke = $_POST['joke'];
    $joke['jokedate'] = new \DateTime();
    $joke['authorId'] = 1;

    $this->jokesTable->save($joke);

    header('location: /joke/list');
}

public function edit($id = null) {
    if (isset($id)) {
        $joke = $this->jokesTable->find('id', $id)[0] ?? null;
    }

    $title = 'Edit joke';

    return ['template' => 'editjoke.html.php',
        'title' => $title,
        'variables' => [
            'joke' => $joke ?? null
        ]
    ];
}
```

我们实际上并没有改变网站的功能，因为用户在显示表单时和提交表单时都已经导航到了 `/joke/edit`。这种让同一个 URL 根据请求方法执行不同操作的做法松散地被称为 **表述性状态转移** (REST)。虽然 REST 最初有稍微严格一点的含义，但最近它已经变成了一个模糊的流行词。你会在招聘信息上看到它，但大多数人现在所说的 REST 只是同一个 URL 根据请求方法做出不同响应。

请记住，我们的 `delete` 方法使用了 `$_POST`，所以你也需要将其重命名为 `deleteSubmit`。

## REST 方法

虽然 REST 通常支持 `PUT` 和 `DELETE` 方法，以及 `GET` 和 `POST`，但由于 Web 浏览器仅支持 `GET` 和 `POST`，PHP 开发者倾向于使用 `POST` 代替 `PUT` 和 `DELETE` 请求。因此，在本书中不值得探讨它们之间的差异。

一些 PHP 开发者找到了模仿 `PUT` 和 `DELETE` 的表面方法，但大多数开发者只是坚持使用 `POST` 来写入数据，使用 `GET` 来读取。

有关 REST 的更多信息，请参阅 SitePoint 文章“[从零构建 REST API：入门介绍](https://www.sitepoint.com/build-rest-api-scratch-introduction/)”。

从现在开始创建表单时，我们将有两个方法：一个用于显示表单，另一个是处理表单提交的该方法的 `submit` 版本。

## 非 Web 应用

我们的 `EntryPoint` 类现在看起来像这样：

```
class EntryPoint {
    public function __construct(private $website) {
    }

    public function run($uri) {
        try {
            $this->checkUri($uri);

            if ($uri == '') {
                $uri = $this->website->getDefaultRoute();
            }

            $route = explode('/', $uri);

            $controllerName = array_shift($route);
            $action = array_shift($route);

            if ($_SERVER['REQUEST_METHOD'] === 'POST') {
                $action .= 'Submit';
            }

            $controller = $this->website->getController($controllerName); 

            $page = $controller->$action(...$route);

            $title = $page['title'];

            $variables = $page['variables'] ?? [];
            $output = $this->loadTemplate($page['template'], $variables);

        } catch (\PDOException $e) {
            $title = 'An error has occurred';

            $output = 'Database error: ' . $e->getMessage() . ' in ' .
            $e->getFile() . ':' . $e->getLine();
        }

        include  __DIR__ . '/../templates/layout.html.php';
    }

    private function loadTemplate($templateFileName, $variables) {
        extract($variables);

        ob_start();
        include  __DIR__ . '/../templates/' . $templateFileName;

        return ob_get_clean();
    }

    private function checkUri($uri) {
        if ($uri != strtolower($uri)) {
            http_response_code(301);
            header('location: ' . strtolower($uri));
        }
    }
}
```

这个方法的问题在于它不够灵活。如果我们以后想在非 Web 应用中使用 `EntryPoint` 类，它将无法工作，因为 `$_SERVER` 变量不会被设置。就像我们对 `uri` 变量所做的那样，最好将其作为参数传入：

```
 public function run($uri, $method) {
        try {
            $this->checkUri($uri);

            if ($uri == '') {
                $uri = $this->website->getDefaultRoute();
            }

            $route = explode('/', $uri);

            $controllerName = array_shift($route);
            $action = array_shift($route);

            if ($method === 'POST') {
                $action .= 'Submit';
            }
```

我们然后在 `index.php` 中提供它：

```
include __DIR__ . '/../includes/autoload.php';

$uri = strtok(ltrim($_SERVER['REQUEST_URI'], '/'), '?');

$jokeWebsite = new \Ijdb\JokeWebsite();
$entryPoint = new \Ninja\EntryPoint($jokeWebsite);
$entryPoint->run($uri, $_SERVER['REQUEST_METHOD']);
```

如果我们愿意，我们可以通过从不同位置提供 `REQUEST_URI` 和 `REQUEST_METHOD` 来在命令行应用中使用 `EntryPoint`。

避免这种硬编码是一种非常好的习惯。PHP（以及软件开发总体上）的趋势是朝着 **测试驱动开发** (TDD) 发展，而像 `$_SERVER['REQUEST_METHOD']` 这样的硬编码值会使测试变得困难。虽然 TDD 超出了本书的范围，但我确实想教你一些实践，让你最终转向 TDD 时尽可能轻松。

## 使用接口强制依赖结构

在第 8 章，当我们创建 `DatabaseTable` 类时，我们编写了构造函数使其检查其参数的类型：

```
public function __construct(\PDO $pdo, string $table, string $primaryKey) {
```

使用这种方法，不提供 `PDO` 的实例作为第一个参数，就不可能构造 `DatabaseTable` 类的实例。

`EntryPoint` 类依赖于作为 `$website` 类变量提供的 `JokeWebsite`。`EntryPoint` 的 `run` 方法调用 `getDefaultRoute()` 和 `getController()` 方法：

```
if ($uri == '') {
    $uri = $this->website->getDefaultRoute();
}
//...
$controller = $this->website->getController($controllerName);
```

然而，如果 `$this->website` 变量不是 `JokeWebsite` 的实例，或者它是一个没有 `getController` 方法的对象，会发生什么？

`run` 方法接受 `$uri` 和 `$method` 变量。如果它们没有被设置为字符串会怎样？

就像我们对 `DatabaseTable` 所做的那样，我们可以在定义参数时使用类型提示来强制类型：

```
namespace Ninja;
class EntryPoint {
    public function __construct(private \Ijdb\JokeWebsite $website) {
    }

    public function run(string $uri, string $method) {
```

在设置了类型提示后，不提供 `\Ijdb\JokeWebsite` 的实例作为构造函数参数 `$website`，就无法构造 `EntryPoint` 类。但这破坏了我们的灵活性！当我们构建在线商店并想使用名为 `\Shop\Routes` 的类时会怎样？理想情况下，我们希望有灵活性让每个网站为 `$website` 变量提供一个类，但我们也希望获得类型检查带来的健壮性。

这可以通过称为“接口”的东西来实现。一个 **接口** 可用于描述类应包含哪些方法，但它不包含任何实际逻辑。然后类可以 *实现* 接口。

路由的接口看起来像这样：

```
<?php
namespace Ninja;
interface Website {
    public function getDefaultRoute();
    public function getController(string $controllerName);
}
```
