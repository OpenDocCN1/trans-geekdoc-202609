

# 测试页面内容

我们可以像在 WelcomeCept 中一样的方式编写测试。使用 `$I->amOnPage()` 方法设置 URI，并使用 `$I->see()` 方法检查结果。

tests/acceptance/NewsCept.php

```
$I->amGoingTo('access the archive page');
$I->amOnPage('/news');
$I->see('News archive');
$I->see('News test');
$I->see('News text', '.main');
$I->seeInTitle('CodeIgniter Tutorial');
```

# 注释

$I->amGoingTo()` 方法允许你描述将要执行的操作。这是一种为你的测试添加注释的方法。你也可以使用 `$I->expect()` 和 `$I->expectTo()` 方法来添加描述预期结果的注释。

$I->amGoingTo('access the archive page');

# 断言

$I->see()` 方法是一个断言方法。它允许我们检查参数字符串是否在页面上。

```
$I->see('News archive');
$I->see('News test');
```

我们可以使用第二个参数来应用我们期望应用到字符串的 CSS 类。

```
$I->see('News text', '.main');
```

我们还可以检查页面标题。

```
$I->seeInTitle('CodeIgniter Tutorial');
```

要了解更多关于断言方法的信息，请参阅文档的 assertions 部分。

# 测试表单

Codeception 还允许我们填写和提交表单。我们使用 `$I->fillField()` 方法填充表单字段，然后使用 `$I->click()` 方法点击提交按钮。

> *http://codeception.com/docs/03-AcceptanceTests#Assertions

# 使用 Codeception 进行浏览器测试

tests/acceptance/NewsCept.php

```
$I->amGoingTo('post a valid item');
$I->fillField('title', 'CodeIgniter is easy to write tests');
$I->fillField('text', 'You can write tests for controllers very easily!');
$I->click('Create news item');
$I->see('Successfully created');
```

如果你想了解更多关于表单操作的信息，请查看文档的 Forms 部分。

# NewsCept

以下是 Newscept.php 的完整代码列表。

```
tests/acceptance/Newscept.php
<?php
system('CI_ENV=testing php index.php dbfixture all');

$I = new AcceptanceTester($scenario);
$I->wantTo('ensure that News works');

$I->amGoingTo('access the archive page');
$I->amOnPage('/news/');
$I->see('News archive');
$I->see('News test');
$I->see('News test', '.main');
$I->seeTitle('CodeIgniter Tutorial');

$I->amGoingTo('access an item which does not exist');
$I->amOnPage('/news/not-existing-slug/');
$I->see('404 Page Not Found');
$I->dontSeeInTitle('CodeIgniter Tutorial');

$I->amGoingTo('access an existing item');
$I->amOnPage('/news/news-test');
$I->see('News test');
$I->seeTitle('CodeIgniter Tutorial');

$I->amGoingTo('access the create page');
26 $I->amOnPage('/news/create');
27 $I->see('Create a news item');
28
29 $I->amGoingTo('post a valid item');
30 $I->fillField('title', 'CodeIgn is easy to write tests');
31 $I->fillField('text', 'You can write tests for controllers very easily!');
32 $I->click('Create news item');
33 $I->see('Successfully created');
34
35 $I->amGoingTo('access the archive page');
36 $I->amOnPage('/news');
37 $I->see('News test');
38 $I->see('CodeIgniter is easy to write tests');
39
40 $I->amGoingTo('post an invalid item');
41 $I->amOnPage('/news/create');
42 $I->click('Create news item');
43 $I->see('The Test field is required.');
44 $I->see('The Test field is required.');
```

运行它并确认测试通过。在运行测试之前，忘记运行 Selenium 服务器和 Web 服务器。

```
$ php codecept.phar run acceptance tests/acceptance/NewsCept.php
```

你应该看到类似所示的绿色 OK：

> Codeception PHP Testing Framework v2.1.4
Powered by PHPUnit 4.8.10 by Sebastian Bergmann and contributors.

Acceptance Tests (1)
Ensure that news works (NewsCept)
Ok

Time: 5.86 seconds, Memory: 5.25Mb

OK (1 test, 14 assertions) 

如果你想了解更多关于 Codeception 验收测试的功能，请查看 [验收测试文档]().

http://codeception.com/docs/03-AcceptanceTests

# 10.7 使用 Google Chrome 进行测试

要使用 Google Chrome 运行测试，我们需要安装 Google Chrome 和用于 Selenium 的 ChromeDriver。

# 安装 ChromeDriver

你可以在 http://www.seleniumhq.org/download/ 或 https://github.com/SeleniumHQ/selenium/wiki/ChromeDriver 驱动。

你可能需要点击几个链接来获取最新驱动。在本书中，我们使用 v.20。下载适用于你平台的驱动并解压。将驱动移动到 PHP 项目的根目录。

```
CodeIgniter/
└── chromedriver
```

-   对于 Windows 用户
Windows 驱动文件名为 chromedriver.exe。

# 配置验收测试

若要在测试中使用 Chrome 驱动，请在 acceptance.suite.yml 的 env 根目录下定义不同的环境。为环境命名（firefox, chrome 等），然后重新定义之前设置的任何配置参数。

```
--- a/CodeIgniter/tests/acceptance.suite.yml
+++ b/CodeIgniter/tests/acceptance.suite.yml
@@ -11,3 +11,12 @@
  url: http://127.0.0.1:800
  url: http://127.0.0.1:800
  firefox:
  chrome:
    modules:
      enabled:
        - WebDriver:
          browser: chrome
          window_size: 1280x1020
```
