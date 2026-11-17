

## Listing 15-32 - 示例功能测试命名实践

```
$browser->
get('/foobar/index')->
with('request')->begin()->
isParameter('module', 'foobar')->
isParameter('action', 'index')->
end()->
with('response')->begin()->
isStatusCode(200)->
checkElement('body', '/foobar/')->
end()
;
```

```
# get /comment/index
ok 1 - status code is 200
ok 2 - request parameter module is foobar
ok 3 - request parameter action is index
ok 4 - response selector body matches regex /foobar/
```

如果你遵循这一约定，你的测试输出将足够清晰，可用作项目的开发者文档——在某些情况下甚至足以让实际文档变得多余。

## 特殊测试需求

symfony 提供的单元测试和功能测试工具在大多数情况下应已足够。下面列出了一些额外技术，用于解决自动化测试中的常见问题：在隔离环境中启动测试、在测试中访问数据库、测试缓存，以及测试客户端交互。

## 在测试框架中执行测试

test:unit 和 test:functional 任务可以启动单个测试或一组测试。但如果在不带任何参数的情况下调用这些任务，它们将运行 test/ 目录中编写的所有单元测试和功能测试。会涉及一种特殊机制，将每个测试文件隔离在独立的沙箱中，以避免测试之间的污染风险。此外，在这种情况下保持与单个测试文件相同的输出是没有意义的（输出将长达数千行），因此测试结果会被压缩成一个综合视图。这就是为什么执行大量测试文件使用测试框架，即具有特殊功能的自动化测试框架。测试框架依赖于 lime 框架的一个组件，称为 lime_harness。它按文件显示测试状态，并在最后显示通过测试数与总数的概览，如 Listing 15-33 所示。

## Listing 15-33 - 在测试框架中启动所有测试

```
$ php symfony test:all
unit/myFunctionTest.php............ok
unit/mySecondFunctionTest.php......ok
unit/foo/barTest.php.............not ok

Failed Test                                                Stat Total   Fail  List of Failed
------------------------------------------------------------------
unit/foo/barTest.php                                          0     2     2  62 63
Failed 1/3 test scripts, 66.66% okay. 2/53 subtests failed, 96.22% okay.
```

测试执行方式与逐个调用时相同，只是输出被缩短以真正有用。特别是，最终图表关注失败的测试，帮助你定位它们。

你可以使用 test:all 任务一次性启动所有测试，该任务也使用测试框架，如 Listing 15-34 所示。在每次部署到生产环境之前都应该这样做，以确保自最新版本以来未出现回归。

## Listing 15-34 - 启动项目的所有测试

```
$ php symfony test:all
```

## 访问数据库

单元测试通常需要访问数据库。当你首次调用 sfBrowser::get() 时，数据库连接会自动初始化。但是，如果你想在使用 sfBrowser 之前访问数据库，则必须手动初始化 sfDatabaseManager 对象，如 Listing 15-35 所示。

## Listing 15-35 - 在测试中初始化数据库

```
$databaseManager = new sfDatabaseManager($configuration);
$databaseManager->loadConfiguration();

// Optionally, you can retrieve the current database connection
$con = Propel::getConnection();
```

在开始测试前，应该使用固定数据填充数据库。这可以通过 sfPropelData 对象完成。该对象可以从文件加载数据，就像 propel:data-load 任务一样，也可以从数组加载，如 Listing 15-36 所示。

## Listing 15-36 - 从测试文件填充数据库

```
$data = new sfPropelData();

// Loading data from file
$data->loadData(sfConfig::get('sf_data_dir').'/fixtures/test_data.yml');

// Loading data from array
$fixtures = array(
    'Article' => array(
        'article_1' => array(
            'title'   => 'foo title',
            'body'    => 'bar body',
            'created_at' => time(),
        ),
        'article_2'  => array(
            'title'   => 'foo foo title',
            'body'    => 'bar bar body',
            'created_at' => time(),
        ),
    ),
);

$data->loadDataFromArray($fixtures);
```

然后，根据你的测试需求，像在正常应用程序中一样使用 Propel 对象。请记得在单元测试中包含它们的文件（你可以使用 sfSimpleAutoload 类来自动化此过程，如前面本章“桩、固定数据和自动加载”部分的提示中所述）。功能测试中会自动加载 Propel 对象。

## 测试缓存

为应用程序启用缓存时，功能测试应验证缓存的操作是否按预期工作。

首先要做的是为测试环境启用缓存（在 settings.yml 文件中）。然后，如果你想测试页面是来自缓存还是动态生成的，应该使用 view_cache 测试组提供的 isCached() 测试方法。Listing 15-37 演示了此方法。

## Listing 15-37 - 使用 isCached() 方法测试缓存

```
<?php
include dirname(__FILE__).'/../../bootstrap/functional.php';
// Create a new test browser
$b = new sfTestFunctional(new sfBrowser());
$b->get('/mymodule');
$b->with('view_cache')->isCached(true); // Checks that the response comes from the cache
$b->with('view_cache')->isCached(true, true); // Checks that the cached response comes with layout
$b->with('view_cache')->isCached(false); // Checks that the response doesn't come from the cache
```

> 在功能测试开始时不需要清除缓存；引导脚本会为你完成此操作。

## 测试客户端交互

之前描述的技术的主要缺点是它们无法模拟 JavaScript。对于非常复杂的交互，例如 Ajax 交互，你需要能够精确复现用户会进行的鼠标和键盘输入，并在客户端执行脚本。通常，这些测试是手动重现的，但非常耗时且容易出错。

解决方案称为 Selenium52，它是一个完全用 JavaScript 编写的测试框架。它就像普通用户一样，使用当前浏览器窗口在页面上执行一组操作。相对于 sfBrowser 对象，Selenium 的优势在于它能够在页面中执行 JavaScript，因此你可以使用它来测试甚至 Ajax 交互。

Selenium 默认未随 symfony 捆绑。要安装它，需要在 web/ 目录中创建一个新的 selenium/ 目录，并在其中解压 Selenium 存档53 的内容。这是因为 Selenium 依赖 JavaScript，而大多数浏览器中的标准安全设置不会允许它运行，除非它与你的应用程序位于相同的主机和端口上。

> 注意不要将 selenium/ 目录传输到生产服务器，因为任何通过浏览器访问 Web 文档根目录的人都可以访问它。

Selenium 测试用 HTML 编写，并存储在 web/selenium/tests/ 目录中。例如，Listing 15-38 显示了一个功能测试，其中加载主页、单击“click me”链接，并在响应中查找文本“Hello, World”。请记住，为了在测试环境中访问应用程序，你必须指定 frontend_test.php 前置控制器。

## Listing 15-38 - 示例 Selenium 测试，位于 web/selenium/test/testIndex.html

```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
<meta content="text/html; charset=UTF-8" http-equiv="content-type">
<title>Index tests</title>
</head>
<body>
<table cellspacing="0">
<tbody>
<tr><td colspan="3">First step</td></tr>
<tr><td>open</td> <td>/frontend_test.php</td>
<td>&nbsp;</td></tr>
<tr><td>clickAndWait</td> <td>link=click me</td>
<td>&nbsp;</td></tr>
<tr><td>assertTextPresent</td> <td>Hello, World!</td>
<td>&nbsp;</td></tr>
</tbody>
</table>
</body>
</html>
```

测试用例由包含三列（命令、目标和值）的表格的 HTML 文档表示。不过，并非所有命令都需要值。在这种情况下，可以留空该列或使用 &nbsp; 使表格看起来更好。有关命令的完整列表，请参阅 Selenium 网站。

你还需要通过在同一目录下的 TestSuite.html 文件的表格中插入新行，将此测试添加到全局测试套件中。Listing 15-39 演示了如何操作。

## Listing 15-39 - 将测试文件添加到测试套件中，位于 web/selenium/test/TestSuite.html

```
...
<tr><td><a href='./testIndex.html'>My First Test</a></td></tr>
...
```

要运行测试，只需浏览至

http://myapp.example.com/selenium/index.html

选择“主测试套件”，单击运行所有测试按钮，然后观察浏览器复现你指示它执行的步骤。

> 由于 Selenium 测试在真实浏览器中运行，它们还允许你测试浏览器不一致性。使用一个浏览器构建测试，然后用单个请求在所有网站预期可用的其他浏览器上进行测试。

由于 Selenium 测试用 HTML 编写，编写 Selenium 测试可能会很麻烦。但得益于 Firefox Selenium 扩展^54，创建测试只需在录制会话中运行一次测试。在录制会话中导航时，你可以

