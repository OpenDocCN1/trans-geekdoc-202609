
如果你加载了 `reusable.php`，当浏览器中出现“Here is a very simple PHP statement.”时你可能不会感到意外。如果你加载了 `main.php`，就会发生一些有趣的事情。该脚本的输出如图 5.1 所示。

![](img/654520c37415debd4290b9b4aa2c03f2_164_0.png)

图 5.1 `main.php` 的输出显示了 `require()` 语句的结果

# 第5章 重用代码与编写函数

使用 `require()` 语句需要一个文件。在前面的示例中，你使用了名为 `reusable.php` 的文件。当你运行脚本时，`require()` 语句 `require('reusable.php');` 会被请求文件的内容替换，然后执行脚本。这意味着如果你使用 `main.php`，它的运行如下：

```php
<?php
echo 'This is the main file.<br />';
echo 'Here is a very simple PHP statement.<br />';
echo 'The script will end now.<br />';
?>
```

在使用 `require()` 时，你需要注意不同的文件扩展以及 PHP 标签的处理。PHP 不会检查被包含文件的扩展名。这意味着只要你不计划直接调用它，你可以为它命名任何名称。当你使用 `require()` 加载文件时，它就变成了 PHP 文件的一部分并以此执行。

通常情况下，如果 PHP 语句位于名为 `page.html` 的文件中，它们不会被处理。PHP 通常只解析具有定义扩展的文件，如 `.php`。如果你通过 `require()` 语句加载 `page.html`，PHP 将会被处理。因此，你可以使用任何喜欢的扩展，但出于以下原因，坚持使用 `.php` 是个好主意：如果以 `.inc` 或或其他标准扩展结尾的文件存储在文档树中且用户直接在浏览器中加载它们，他们将看到纯文本代码，包括密码。将包含的文件存储在文档树之外或使用标准扩展是重要的。

在示例中，重用文件 `reusable.php` 编写如下：

```php
<?php
echo 'Here is a very simple PHP statement.<br />';
?>
```

## 使用 require() 创建网站模板

如果你公司的网页具有一致的视觉风格，你可以使用 PHP 通过 `require()` 将模板和标准元素添加到页面中。

例如

使用 require () 和 include () 135

现有页面，从文件中间剪掉现有文本，输入新文本，并以新名称保存文件。

![](img/654520c37415debd4290b9b4aa2c03f2_166_0.png)

图 5.2 TLA Consulting 的所有网页都有统一的视觉外观和感受

考虑以下场景：该网站已经运行了一段时间，公司现在有几十个、数百个甚至数千个页面都遵循相同的样式。现在决定更改标准外观的一部分；这种更改可能是微小的，例如在每个页面的页脚处添加电子邮箱地址，或者在导航菜单中添加一个新条目。你想在几十个、数百个甚至数千个页面上都进行那个微小的更改吗？

直接运行所有页面通用的 HTML 部分比在几十个、数百个甚至数千个页面上剪粘贴要好得多。图 5.2 所示的首页 `home.html` 源代码见于列表 5.1。

### 列表 5.1 home.html——生成 TLA Consulting 首页的 HTML

```html
<!DOCTYPE html>
<html
<head>
<title>TLA Consulting Pty Ltd</title>
<link href="styles.css" type="text/css" rel="stylesheet">
</head>
<body>
```

```html
<!-- page header -->
<header>
  <img src="logo.gif" alt="TLA logo" height="70" width="70" />
  <h1>TLA Consulting</h1>
</header>
<!-- menu -->
<nav>
  <div class="menuitem">
    <a href="home.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">Home</span>
    </a>
  </div>
  <div class="menuitem">
    <a href="contact.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">Contact</span>
    </a>
  </div>
  <div class="menuitem">
    <a href="services.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">Services</span>
    </a>
  </div>
  <div class="menuitem">
    <a href="about.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">About</span>
    </a>
  </div>
</nav>
<!-- page content -->
<section>
  <h2>Welcome to the home of TLA Consulting.</h2>
  <p>Please take some time to know us.</p>
  <p>We specialize in serving your needs and hope to hear from you soon.</p>
</section>
```

使用 require() 和 include () 137

```html
<!-- page footer -->
<footer>
<p>&copy; TLA Consulting Pty Ltd.<br />
Please see our
  <a href="legal.php">legal information page</a></p>
</footer>
</body>
</html>
```

你可以在列表 5.1 中看到该文件中包含许多不同的代码部分。`<head>` 元素链接到页面使用的样式表 `CSS` 定义。标记为 "page header" 的部分显示公司名称和标志，“menu”部分创建页面导航栏，而 "page content" 是该页面的唯一文本。在下方，你可以将此文件拆分并命名为 `header.php`、`home.php` 和 `footer.php`。`header.php` 和 `footer.php` 包含了其他页面将重用的代码。`home.php` 是 `home.html` 的替换，包含了唯一的页面内容以及列表 5.2 所示的 `require()` 语句。

### 列表 5.2 home.php——生成 TLA 首页的页面

```php
<?php
require('header.php');
?>
<!-- page content -->
<section>
  <h2>Welcome to the home of TLA Consulting.</h2>
  <p>Please take some time to know us.</p>
  <p>We specialize in serving your needs and hope to hear from you soon.</p>
</section>
<?php
require('footer.php');
?>
```

`home.php` 中的 `require()` 语句加载了 `header.php` 和 `footer.php`。如前所述，给这些文件的命名不会影响你用 `require()` 调用它们时的处理方式。一种常见的约定是将部分文件称为 `inc`。这种策略不被推荐，因为除非 Web 服务器专门进行了配置，否则 `.inc` 文件不会被解析。这种设置是一种很好的策略，因为它防止了文件被单独加载。这会导致 a) 如果文件扩展名为 `.php` 但只包含部分页面时产生错误，或者 b) 使用另一个扩展名允许人们读取你的源代码。`header.php` 文件包含了页面使用的 CSS 定义、显示公司名称的导航菜单，如列表 5.3 所示。

### 列表 5.3 header.php——所有TLA网页的可复用头部

```html
<!DOCTYPE html>
<html>
<head>
<title>TLA Consulting Pty Ltd</title>
<link href="styles.css" type="text/css" rel="stylesheet">
</head>
<body>
<!-- page header -->
<header>
  <img src="logo.gif" alt="TLA logo" height="70" width="70" />
  <h1>TLA Consulting</h1>
</header>
<!-- menu -->
<nav>
  <div class="menuitem">
    <a href="home.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">Home</span>
    </a>
  </div>
  <div class="menuitem">
    <a href="contact.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">Contact</span>
    </a>
  </div>
  <div class="menuitem">
    <a href="services.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">Services</span>
    </a>
  </div>
  <div class="menuitem">
    <a href="about.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">About</span>
    </a>
  </div>
</nav>
```

`footer.php` 文件包含了在每个页面底部显示页脚的内容。该文件见列表 5.4。

### 列表 5.4 footer.php——所有TLA网页的可复用页脚

```html
<!-- footer -->
<footer>
<p>&copy; TLA Consulting Pty Ltd.<br />
Please see our
  <a href="legal.php">legal information page</a></p>
</footer>
</body>
</html>
```

这种方法可以让你轻松地创建一个外观一致的网站，你可以通过输入如下内容创建一个相同样式的新页面：

```php
<?php require('header.php'); ?>
Here is the content for this page
<?php require('footer.php'); ?>
```

最重要的是，在使用这些头部和页脚创建许多页面后，你可以轻松地更改头部和页脚文件。无论你是进行微小的文本更改还是完全重新设计网站的外观，你只需要更改一次。你不需要处理网站中的每一个页面，因为每个页面都在头部和页脚文件中加载的。

这里显示的示例在主体、头部和页脚中仅使用 HTML。情况并非如此。在这些文件中，你可以使用 PHP 语句来动态生成页面的部分。

如果你想确保一个文件被视为纯文本或 HTML，而不包含任何 PHP，你可能想使用 `readfile()` 代替。该函数会输出文件内容而不进行解析。如果你使用用户提供的文本，这是一项重要的安全措施。

## 调用函数

以下行是最简单的可能的函数调用方式：

```
function_name();
```

此行调用了一个名为 `function_name` 的函数，该函数不需要参数。此行代码忽略了该函数可能返回的任何值。

许多函数正是通过这样调用的。`phpinfo()` 函数在测试中非常有用，因为它显示了已安装的 PHP 版本、PHP 信息、服务器设置以及各种 PHP 和服务器变量。`phpinfo()` 函数接受一个参数并返回一个值，但这两者很少被同时使用，通常对 `phpinfo()` 的调用如下：

```
phpinfo();
```

大多数函数需要一个或多个参数。你通过在函数名后的括号内放置数据或键值来传递参数。你可以如下调用一个接受单个参数的函数：

```
function_name('parameter');
```

在这种情况下，参数是一个只包含该单词的字符串，但随后的调用也可能取决于函数的预期：

```
function_name(2);
function_name($variable);
```

在最后一行中，`$variable` 可能是任何类型的 PHP 变量，包括数组或对象——特定的函数需要特定的数据类型。你可以从函数的原型中看到一个函数接受多少参数、每个参数代表什么，以及每个参数需要什么类型的数据。在本书描述一个函数时，我们会展示其原型。这是 `fopen()` 的原型：

```
resource fopen(string filename, string mode [, bool include_path=false, resource context])
```

原型告诉了你许多信息，知道如何正确解释规范非常重要。在这种情况下，函数名之前的单词告诉此函数将返回一个资源，即文件句柄。参数在括号内。在 `fopen()` 的情况下，原型中显示了四个参数：`filename` 和 `mode` 是字符串，`include_path` 是布尔值，`context` 是资源。`include_path` 和 `context` 周围的中括号表示这些参数是可选的。你可以为可选参数提供值，也可以选择忽略它们并使用默认值。但请注意，具有多个可选参数的函数只能省略右侧的参数。例如，在使用 `fopen()` 时，你可以省略 `include_path` 或 `context`；但是，你不能在提供 `context` 的情况下省略 `filename`。在阅读了该函数的原型后，你就知道以下代码片段是 `fopen()` 的有效调用：

```
$name = 'myfile.txt';
$mode = 'r';
$fp = fopen($name, $mode);
```
