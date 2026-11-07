
# 控制器依赖注入与路由

## 依赖注入问题

`JokesController` 类依赖于两个 `DatabaseTable` 对象——一个用于作者，一个用于笑话。`AuthorController` 类仅依赖于一个，即 `$authorsTable`。如果我们尝试自动化控制器的创建，就会产生一个问题：如果构造函数不同，如何自动创建对象？

解决此问题的一种方法是确保所有控制器具有相同的构造函数。它们都需要访问所有可能的 `DatabaseTable` 对象。这种方法可行，但很混乱。它会导致控制器依赖于任何控制器可能需要的全部内容。这种方法的一个主要缺点是，当添加新的数据库表时，所有控制器的构造函数都必须更改。我们可以通过传递所有可能依赖项的数组并挑选出我们需要的依赖项来克服这个问题。这本质上被称为“服务定位器”，这是一种常见的方法，尽管在过去几年中它已被广泛认为是不良实践。（请参阅上文的“不要这样做”提示框，了解有关服务定位器的更多信息。）

我们所做的事情的技术术语是 **依赖注入**。听起来很复杂，但它只是将依赖项传递给构造函数的花哨说法。你一直在不知不觉中这样做！

解决不同构造函数需要不同参数问题的最简单方法是一系列 if 语句。这样，每个控制器都可以用正确的依赖项创建：

```
$action = $_GET['action'] ?? 'home';
$controllerName = $_GET['controller'] ?? 'joke';

if ($controllerName === 'joke') {
    $controller = new JokeController($jokesTable, $authorsTable);
}
else if ($controllerName === 'author') {
    $controller = new AuthorController($authorsTable);
}

$page = $controller->$action();
```

现在控制器由 `$_GET['controller']` 中提供的变量选择，并且在控制器对象上调用 `$_GET['action']` 中定义的方法。如果未设置 `$_GET['controller']`，则默认为 `home`，如果未设置 `$_GET['action']`，则默认为 `home`。

这种方法非常灵活。它允许我们通过在 `controller` URL 变量中指定类名，在 `action` URL 变量中指定方法名，来调用任何控制器的任何方法。

### 3. 在正确的控制器上调用操作

第三个更改非常容易实现。我们需要在正确的控制器上调用正确的方法。完成之前的更改后，只有一个控制器被实例化并存储在 `$controller` 中。它是哪一个控制器并不重要。你只需使用以下代码：

```
$controller->$action();
```

如果 `$controller` 存储的是 `JokeController` 实例，它将调用 `JokeController` 类中的方法。如果它存储的是 `AuthorController` 实例，则会调用 `AuthorController` 类中的方法。

### 完成

完整的 `index.php` 如下所示。

**示例：[CMS-控制器](https://github.com/spbooks/phpmysql7/tree/CMS-Controller)**

```
<?php
function loadTemplate($templateFileName, $variables = []) {
    extract($variables);

    ob_start();
    include  __DIR__ . '/../templates/' . $templateFileName;

    return ob_get_clean();
}

try {
    include __DIR__ . '/../includes/DatabaseConnection.php';
    include __DIR__ . '/../classes/DatabaseTable.php';
    include __DIR__ . '/../controllers/JokeController.php';
    include __DIR__ . '/../controllers/AuthorController.php';

    $jokesTable = new DatabaseTable($pdo, 'joke', 'id');
    $authorsTable = new DatabaseTable($pdo, 'author', 'id');

    $action = $_GET['action'] ?? 'home';
    $controllerName = $_GET['controller'] ?? 'joke';

    if ($controllerName === 'joke') {
        $controller = new JokeController($jokesTable, $authorsTable);
    }
    else if ($controllerName === 'author') {
        $controller = new AuthorController($authorsTable);
    }

    if ($action == strtolower($action) && $controllerName == strtolower($controllerName)) {
        $page = $controller->$action();
    } else {
        http_response_code(301);
        header('location: index.php?controller=' . strtolower($controllerName) .'&action=' . strtolower($action));
    }

    $title = $page['title'];

    $variables = $page['variables'] ?? [];
    $output = loadTemplate($page['template'], $variables);

} catch (PDOException $e) {
    $title = 'An error has occurred';

    $output = 'Database error: ' . $e->getMessage() . ' in ' .
    $e->getFile() . ':' . $e->getLine();
}

include  __DIR__ . '/../templates/layout.html.php';
```

请注意，我还更新了检查 URL 是否为正确大小写的 `if` 语句。它现在还会检查控制器名称是否为小写，并在其不是小写时将用户重定向到小写的控制器和操作。

理想情况下，我们希望能够在不编辑 `index.php` 的情况下使用 *任何* 控制器。但为了简单起见，我们将坚持这种方法。

现在它们已经更改，我们还需要修改 `layout.html.php` 以在菜单中使用新的路由：

```
<li><a href="index.php?controller=joke&amp;action=list">Jokes List</a></li>
<li><a href="index.php?controller=joke&amp;action=edit">Add a new Joke</a></li>
```

在我们继续更改网站上所有链接之前，这些 URL 变得越来越长且笨重，为了避免这种情况，我想介绍一种称为“URL 重写”的方法。

## URL 重写

许多网站都是用 PHP 编写的，包括 Facebook 和 Wikipedia。如果你访问这些网站，你会发现 URL 看起来不像我们在笑话网站上使用的那样。

SitePoint 的 Wikipedia 页面 URL 是 `https://en.wikipedia.org/wiki/SitePoint`，其 Facebook 页面 URL 是 `https://www.facebook.com/sitepoint/`。

使用我们迄今为止查看的结构，你可能会期望看到类似 `https://www.facebook.com/index.php?controller=page&id=sitepoint` 或 `https://en.wikipedia.org/index.php?controller=wiki&action=sitepoint` 的内容。

大多数 PHP 网站实际上不会在 URL 中显示 PHP 文件名。许多年前，搜索引擎会惩罚大量使用 URL 变量的网站，当时的趋势是使用更友好的 URL 以在搜索引擎中排名更高。如今，[搜索引擎不在乎 URL 结构](https://www.sitepoint.com/friendly-urls/)，友好 URL 更多是出于美观原因而使用。例如，当你在社交媒体上粘贴链接时，最好能提供一个简洁明了的地址。

由于大多数网站使用更友好的 URL，了解如何实现这一点很有用。

Web 服务器的默认行为是将 URL 直接映射到文件名。如果你访问 `website.com/logo.png`，它会在其 `public` 目录中查找 `logo.png`。访问 `about-the-company.php` 将根据 URL 查找 PHP 脚本。

URL 到服务器上文件的这种映射是一种合理的约定，但它只是默认行为，可以被覆盖。如果你愿意，可以指示 Web 服务器在有人访问 `homepage.php` 时从其 `public` 目录加载 `home.php`。

URL 和文件仅通过这种默认行为关联，但实际上它们完全相互独立。

**URL 重写** 是更改此约定的工具。你可以配置 Web 服务器，以便当有人访问 `/jokes/list` 时，实际上运行 `index.php?controlelr=joke&action=list`，或者当有人访问 `contact.php` 时，反而运行 `index.php?action=contact`。

重要的是，地址栏中的 URL 可能与服务器上实际运行的 PHP 脚本完全不同，而查看页面的人只能看到更友好的 URL。

URL 重写是一个漫长而复杂的话题。你可以设置各种精彩而令人印象深刻的规则。然而，几乎所有现代 PHP 网站都使用相同的易于实现的规则：如果请求的文件不存在，则加载 `index.php`。
