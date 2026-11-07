
A very simple solution to this is to move the code that loads the template into its own function. Amend `index.php` to the code below.

**示例：[OOP-入口点模板](https://github.com/spbooks/phpmysql7/tree/OOP-EntryPoint-Template)**

```
<?php
function loadTemplate($templateFileName, $variables) {
    extract($variables);

    ob_start();
    include  __DIR__ . '/../templates/' . $templateFileName;

    return ob_get_clean();
}

try {
    include __DIR__ . '/../includes/DatabaseConnection.php';
    include __DIR__ . '/../classes/DatabaseTable.php';
    include __DIR__ . '/../controllers/JokeController.php';

    $jokesTable = new DatabaseTable($pdo, 'joke', 'id');
    $authorsTable = new DatabaseTable($pdo, 'author', 'id');

    $jokeController = new JokeController($jokesTable, $authorsTable);

    $action = $_GET['action'] ?? 'home';

    $page = $jokeController->$action();

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

我创建了 `loadTemplate` 函数来加载模板文件并创建 `$variables` 参数中提供的变量。

当调用该函数时，它会接收由控制器操作在 `$page` 中指定的模板名称，以及 `$page['variables']` 中指定的变量：

```
$variables = $page['variables'] ?? [];
$output = loadTemplate($page['template'], $variables);
```

由于 `'variables'` 键可能不存在，我使用了现在熟悉的 `??` 运算符将 `$variables` 变量设置为控制器操作返回值中指定的变量或一个空数组。

通过将加载模板的代码移至其自己的函数中，如果 `variables` 数组包含名为 `page` 或 `title` 的键，现有的变量不会被覆盖，因为它们在函数的作用域内不存在。

在本章中，我向你展示了如何使用面向对象编程进一步拆分代码并减少重复。我们还开始为控制器代码添加更清晰的结构。

有了这种新结构，向网站添加新页面现在是一项非常简单的任务：

1. 在 `jokeController` 中创建一个函数，该函数返回一个包含模板文件名、页面标题和模板使用的变量的数组。
2. 通过在 URL 中指定函数名称来访问页面：`index.php?action=functionName`。

你可能已经意识到这并不具有很强的可扩展性。一个有 100 个页面的网站将需要一个包含 100 个函数的控制器。这将非常难以管理。

在下一章，我将向你展示如何使 `index.php` 可用于其他控制器，并开始思考可以在不同网站上使用的代码。

## 摘要

在本章中，你学习了面向对象编程的基础知识以及如何将代码拆分为类。在这些更改到位后，向网站添加新页面变得更加简单，并且需要复制和粘贴的代码大大减少（记住 DRY 原则！）。

每个页面现在都是通过 `index.php` 访问的函数调用，而不是每个页面一个文件。因此，每个页面上用于连接数据库和加载类文件的所有设置代码都可以在一个地方完成。

# 第9章：创建可扩展框架

现在你能够编写具有方法的控制器，并从 `index.php` 调用这些方法，下一步是添加用于管理网站的其余页面。目前，我们可以通过指定 `action` URL 参数通过 `index.php` 将笑话添加到数据库中。然而，真正的网站需要做的事情远不止处理单个表的基本数据库操作。

网站的下一个扩展将是允许用户注册为作者并发布自己的笑话。然而，在这样做之前，我将向你展示如何编写一个现代、灵活的框架以便在此基础上构建。到本章结束时，你将拥有构建任何网站的基础，并且对专业 PHP 开发者使用的技术和概念有良好的理解。

我们在本章中不会添加任何新功能。相反，我将向你展示如何组织代码，以便可以在你构建的每个网站上重复使用。

在上一章中，我们以 `index.php` 中的这段代码结束：

```
<?php
function loadTemplate($templateFileName, $variables) {
    extract($variables);

    ob_start();
    include  __DIR__ . '/../templates/' . $templateFileName;

    return ob_get_clean();
}

try {
    include __DIR__ . '/../includes/DatabaseConnection.php';
    include __DIR__ . '/../classes/DatabaseTable.php';
    include __DIR__ . '/../controllers/JokeController.php';

    $jokesTable = new DatabaseTable($pdo, 'joke', 'id');
    $authorsTable = new DatabaseTable($pdo, 'author', 'id');

    $jokeController = new JokeController($jokesTable, $authorsTable);

    $action = $_GET['action'] ?? 'home';

    $page = $jokeController->$action();

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

这使我们可以通过指定 `action` URL 参数来调用 `JokeController` 类中的任何函数——例如，通过链接到或访问 `index.php?action=list`。

## 搜索引擎优化

在对代码进行任何结构性更改之前，我们需要做一些整理工作。在 PHP 中，函数不区分大小写。`list` 的处理方式与 `LIST` 完全相同。由于不区分大小写，访问 `index.php?action=list` 会显示页面，但 `index.php?action=LIST` 或 `index.php?action=List` 也会显示页面。这看起来似乎是一件好事，因为人们可以输入错误的 URL 仍然看到正确的页面。然而，这一特性也可能给搜索引擎带来问题。

一些搜索引擎会将这两个 URL 视为两个完全不同的页面，即使它们显示完全相同的内容。`index.php?action=LIST` 和 `index.php?action=list` 都将出现在搜索结果中。你可能会想“太好了，我的更多页面会出现在搜索结果中！”但搜索引擎通常不喜欢“重复内容”，要么降低其排名，要么完全忽略它。你更愿意在第一页看到一个结果，还是在搜索页面的更后面看到两个结果？

有几种方法可以修复这个问题。你可以告诉搜索引擎忽略某些页面。或者你可以告诉他们哪个是“规范”（主要）版本。但在大型网站上管理起来可能很困难，通常更简单的方法是强制使用严格的 URL。一种常见的方法是强制所有 URL 为小写。

强制 URL 为小写是可能的，使用一段简单的 PHP 代码，该代码检测用户是否输入了小写 URL：

```
$action = $_GET['action'];

if ($action == strtolower($action)) {
    $jokeController->$action();
} else {
    echo 'Sorry that page does not exist.';
}
```

这段代码将 `$action` 与 `$action` 的小写版本进行比较。`strtolower` 函数将任何字符串转换为小写：`LISTJOKES`、`listJokes` 或 `listjokes` 都变成 `listjokes`。通过将原始 `$action` 与小写版本进行比较，可以判断某人是否使用 `$action` 的小写值来访问页面。如果没有，则显示错误。访客和搜索引擎只能看到 URL 小写版本上的内容。

### 配置：PHP 与服务器
