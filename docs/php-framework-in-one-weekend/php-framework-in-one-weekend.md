# PHP 框架周末速成





## 前言

> “周末，编程自我提升的基本单位”
> Peter Shirley

我最近很享受阅读 Peter Shirley 的《周末光线追踪》[21]。在几个章节中，Peter 指导你完成构建基本光线追踪应用程序的过程。它不是一个全面的工具，但在一个周末内，你将学习足够的材料来掌握基本概念。Peter 说他包含了“这些作业中最基础的一组，这样在一个周末内就非常可行，这是编程自我提升的基本单位。”

## 关于本项目

我在此遵循了 Peter 的方法，并将引导你完成一个短小的项目，这个项目在一个周末内应该可以轻松完成。该项目基于我曾与小型 PHP 开发者小组一起开展的为期 2 天的培训课程。我将内容精简为一组简单的示例，每个示例都在前一个基础上构建。

它并非旨在成为你可以立即用于真实网站的工具，而是作为学习现代 PHP Web 应用中使用的基本概念的起点。它也不旨在成为 Web 技术的入门课程。假设你对 HTML、CSS、JavaScript 和 PHP 有一定的了解。

这门课程的另一个目标是教授现代 PHP。有大量过时的书籍、教程和指南教授 PHP，但它们今天都无法通过代码审查。在这个项目中，我们将努力使用现代 PHP 最佳实践。但是，一个周末不足以涵盖整个现代 PHP。我们鼓励你阅读《PHP 正确做法》[16]，以了解使用 PHP 的现代方法的更详细概述。

这个周末项目是关于探索现代 PHP 以及 PHP 包和库的生态系统。在整个周末中，你将学习构建现代 PHP 应用所依赖的一些基本概念。Drupal、phpBB、Laravel、eZ Publish、Joomla!、Magento、Piwik 等许多项目都在使用 Symfony Components[25] 作为构建基础。我们将使用这些以及更多内容来构建我们自己的 PHP 框架。

## 关于作者

我于 2001 年在谢菲尔德大学编写并讲授了我的第一门 PHP 课程。在唱片公司短暂工作后，我联合创立了一家数字音乐初创公司，并担任 CTO 直到 2007 年，之后我创立了 Ideation Networks。作为一名 Drupal 专家，我为 Drupal 机构、大规模 Drupal 部署和旗舰 Drupal 网站提供软件开发和培训。最近，这包括帮助开发者从 Drupal 7 切换到 Drupal 8，并教授现代 PHP。

## 约定

等宽字体中的文本要么是代码片段，要么是在命令行中输入的命令。我在 OSX 上使用 iTerm2，但任何 PHP 运行的环境都应该可以。我使用 $ 字符来指示命令提示符。如果你看到一行以该字符开头，后跟一个空格，那么它是应该在终端中输入的命令。

```
$ pwd
/Users/darren/dev/book
```

shell 块中不以 $ 字符开头的任何行都是命令返回的输出。你应该预期在运行前面的命令后，在终端中看到这些输出。

等宽字体的其他用途包括代码示例、PHP 关键字、文件名、类、函数和命令。你会看到部分代码示例，内联包含，例如：

```
$name = $_GET['name'];
```

你还会看到完整源文件的完整代码清单。这些将包括 PHP、CSS、JavaScript、Twig 模板和 JSON 配置文件，例如清单 1。代码清单旁边的标题用于指示其关联的文件。源代码左侧的行号指示引用了源文件中的哪些行。如本示例所示，已提供第 2-6 行。清单可能列出整个文件，也可能仅列出突出正在讨论的问题的选定行数。

```
2 require __DIR__.'../vendor/autoload.php';
3 $name = "World";
4 ?>
5 <!DOCTYPE html>
6 <html lang="en">
```

**清单 1：** public/index.php 注意 源文件仅作为示例提供。它们旨在说明正在讨论的概念。你应当自己编写代码。请不要复制粘贴。阅读代码，理解它，然后编写自己的版本。如果你自己编写代码、即兴发挥并根据喜好进行调整，你将学到更多。你可以随意使用提供的代码，但它仅旨在作为参考。

如果你卡住了，请查看 GitHub 仓库[23] 或联系作者[2]。

## 第 0 章

### 开始

你应该使用最新的稳定版 PHP。我正在使用 PHP 7，但这个项目在 PHP 5.6 上也应该可以正常工作。你可以使用 php -v 命令检查已安装的 PHP 版本。

```
$ php -v
PHP 7.0.6 (cli) (built: May 12 2016 15:13:35) ( NTS ) Copyright (c) 1997-2016 The PHP Group
Zend Engine v3.0.0, Copyright (c) 1998-2016 Zend Technologies
```

如果你在 OSX 上，可以使用 Homebrew[10] 更新和安装 PHP：

```
$ brew update
$ brew install homebrew/php/php70
```

我们将使用一个名为 Composer 的应用程序来下载 PHP 包，并使其可供我们的 PHP 代码使用。

如果你还没有安装 Composer，可以在 Composer 网站[5] 上找到安装说明。你可以将 Composer 本地安装到这个单个项目，但我更喜欢全局安装它。我会假设你已经做了同样的操作，并将 composer 可执行文件添加到你的 PATH 中。如果你以不同方式安装了它，可能需要更新示例命令。

```
$ composer
```

如果你运行上面的命令，你应该能看到关于 Composer、其选项以及可用命令列表的一些基本帮助。





## 第 1 章：管理复杂度

这个周末我们要做的很多事情看起来可能有些大材小用。之所以这样，是因为示例比较简单，旨在展示在更复杂系统中所使用的概念。随着项目规模变大，复杂度增加，你需要有方法来管理复杂性。在 Web 开发中，我们通过分层来应对复杂性。

编写代码时，你是在编写指令语句。这些语句被组织成函数（或方法），函数又被组织成类，类则组合成系统。当这一切变得太大，无法装进脑海时，你就无法对其进行推理了。我们需要尽可能保持系统设计的简单。

为简化设计，我们将事物拆分为独立的块。这些块有许多名称，例如模块、包、组件和库。目标是使它们尽可能自包含。当组件的依赖被最小化时，我们称其为松耦合（与紧耦合相对）。我们将所有相关组件（即共享依赖的组件）分组在一起，以便能够独立于系统的其余部分来思考它们。这通常看起来像是将系统设计分成了若干层。我们称这个过程为分层。

在现代 PHP 中，我们经常谈论包。这些是可复用代码的独立块，具有最小的依赖和清晰、明确定义的 API。当我们创建自己的应用时，更倾向于复用包提供的功能，而不是自己造轮子。包的大小各不相同，从几个函数到整个子系统不等。

框架是一组协同工作的组件的集合。传统上，框架中的组件是为满足特定类型问题而设计和打包在一起的。越来越多地，得益于 PHP 包广泛的开源生态系统，我们能够从不同来源汇总组件，并使它们轻松协同工作。

我们的项目所依赖的包在名为 composer.json 的配置文件中定义，该文件位于代码库的根文件夹中。

使用 Composer init 命令交互式地创建 composer.json 文件。系统会提示你输入一些关于项目的详细信息，并询问你是否要交互式定义依赖。暂时请回答 no 以跳过添加依赖（require）和开发依赖（require-dev）。

```
$ mkdir php-framework
$ cd php-framework
$ composer init
```

你现在应该有一个名为 php-framework 的项目文件夹，其中包含一个简单的 Composer 配置文件（composer.json），大致如下所示：

```
1 {
2 "name": "darrenmothersole/php-framework",
3 "authors": [
4 {
5 "name": "Darren",
6 "email": "darren@darrenmothersel.com"
7 }
8 ],
9 "require": {}
10 }
```

清单 1.1: composer.json

require 部分是我们列出项目所依赖的所有包及其所需版本的地方。Composer 会将它们全部下载到 vendor 文件夹中，并创建一个自动加载器，以便在 PHP 代码中使用它们。

### 自动加载

PHP 不需要在每个请求时都加载整个应用及其依赖。每个请求只会使用代码的一小部分。在现代 PHP 中，我们将代码拆分为多个文件，通常每个文件一个类，然后只包含处理当前任务所需的文件。为了方便开发者，PHP 提供了自动加载机制。这意味着你不需要为每个请求指定要包含的文件。PHP 会使用自动加载器在需要时确定要包含哪些文件。Composer 会根据 composer.json 文件中的配置为我们创建一个自动加载器。

使用 composer install 命令下载依赖并创建自动加载器。

```
$ composer install
```

我们尚未指定任何必需的包，因此没有任何内容被下载到项目中。Composer 只是在 vendor/composer 文件夹中创建了自动加载器。我们通过在应用中包含 vendor/autoload.php 文件来加载它。

### 你好世界

现在让我们搭建一个简单的页面并运行起来。在现代 PHP 中，我们将源代码与 Web 可访问资源分开。创建一个 public 文件夹，用于存放所有公开可访问的文件。在这个文件夹中，按照清单 1.2 创建一个 index.php 文件。

```
1 <?php
2 require __DIR__.'../vendor/autoload.php';
3 $name = "World";
4 ?>
5 <!DOCTYPE html>
6 <html lang="en">
7 <head>
8 <meta charset="UTF-8">
9 <title>Document</title>
10 </head>
11 <body>
12 <h1>Hello <?php print $name; ?>!</h1>
13 </body>
14 </html>
```

清单 1.2: public/index.php

然后使用 PHP 的内置 Web 服务器来查看内容：

$ php -S localhost:4000 -t public/

现在如果你在浏览器中访问 http://localhost:4000/，应该会看到 “Hello World！”。

## 第 2 章

### 测试

测试是现代 PHP 开发中的一个重要概念，试图在这个周末内全面涵盖它是不太现实的。出于我们的目的，我们将定义一个简单的测试脚本，但在实际项目中，你更可能会使用像 PHPUnit[17] 这样的测试框架。

目前，我们的应用程序只是输出 “Hello World!”。如果要为其编写测试，我们会请求该页面，然后检查它是否包含文本 “Hello World!”。按照清单 2.1 创建一个名为 test.php 的文件。

```
1 <?php
2 ob_start();
3 include 'public/index.php';
4 $output = ob_get_clean();
5 echo strpos($output, "Hello World!"), PHP_EOL;
```

清单 2.1: test.php

这个简单的测试启动一个输出缓冲区，包含 index.php 文件，然后将缓冲区的内容获取到字符串变量 $output 中。脚本的最后一行测试字符串 “Hello World!” 是否出现在输出中。

你现在可以使用 PHP 从命令行运行此测试：

```
$ php test.php
109
```

你应该会看到一个打印出的数字（例如 109）。这是 “Hello World!” 字符串在输出中的位置。如果你看到空行，则表示测试未能在输出中找到所需的 “Hello World!” 字符串。

你大概可以想象，随着项目规模变大，以这种方式进行测试会变得复杂且耗时。到某个时候，你会想要使用一个测试框架。

我们还将努力通过将功能分离到组件中来使代码易于测试，以便它们可以独立测试。

在上面的示例中，我们测试的不仅仅是 $name 变量的正确输出。我们还在测试 index.php 文件中的任何其他功能。随着项目规模变大，这一点会变得更加清晰。理想情况下，我们希望有一种方法来独立测试每个功能点。例如，如果我们非常基础的应用中的输出是由回调函数生成的，我们可以独立测试这个单一函数：

```
1 <?php
2 require 'vendor/autoload.php';
3 $controller = new HelloController();
4 $output = $controller->run("World");
5 if ($output == "Hello World!") echo "Test Passed!";
```

清单 2.2: test.php

这只是伪代码。现在不需要理解它，只需注意我们只测试控制器的 run() 方法。而且，我们只在特定情况下进行测试（即当输入等于 “World” 时）。将此与清单 2.1 中的前一个示例进行比较，看看测试现在是如何更有针对性的。当测试针对一个特定的代码单元时，我们称其为单元测试。因此，PHP 最流行的测试框架 PHPUnit 得名于此。

## 第 3 章：HTTP

我们的 Web 框架将处理 HTTP 消息。我们将接收 HTTP 请求，并返回 HTTP 响应。

我们需要解析并从 HTTP 请求中提取信息。请求的是哪个资源？要执行什么操作？客户端接受哪些内容类型？我们的应用程序可能会接受用户输入，在这种情况下，我们需要在 HTTP 请求中查找表单字段输入、URL 参数和上传的文件。

我们还需要构建一个有效的 HTTP 响应，以便客户端能够理解我们作为对其请求的回复所发送的内容。这包括内容，以及关于格式和编码方式的信息。

与其研究 HTTP 消息和 URI 的规范，不如使用一个隐藏所有细节并提供更开发者友好的方式来接收和创建 HTTP 消息的 PHP 包。PHP FIG（框架互操作性组）定义了一组标准的 HTTP 消息接口[20]，框架和 PHP 包可以采用这些接口来改进互操作性。你可以在 Packagist[14] 上搜索与 HTTP 相关的流行 PHP 包。我们将使用最流行的 HTTP 消息抽象，即 Symfony HttpFoundation 组件[27]。它也是 Drupal 和 Laravel 等许多流行 PHP 系统中使用的同一组件。

让我们回到 composer.json，将 HTTP Foundation 组件添加到我们的依赖项中，以便 Composer 可以在我们的项目中安装它。你可以手动编辑 composer.json 文件，或使用 Composer require 命令：

```
$ composer require symfony/http-foundation
```

这将下载最新的稳定版本。撰写本文时，这是 v3.0.6。你会注意到它还下载了 mbstring 兼容包，因为它是 HTTP Foundation 组件的必需依赖项。你的 composer.json 配置文件的 require 部分现在看起来类似于清单 3.1。

```
9 "require": {
10 "symfony/http-foundation": "^3.0"
11 }
```

清单 3.1: composer.json





### HTTP 请求

PHP 将传入请求的数据作为全局变量提供。它们如下所示：

```php
$name = $_GET['name'];
```

我们不希望直接操作这些全局变量。而且，既然我们有了一组代码库来简化对 HTTP 消息的处理，就不必这样做了。HTTP Foundation 组件可以根据 PHP 在全局变量中提供的数据为您创建请求对象。

当我们使用 Composer require 命令下载包时，它会将包添加到自动加载器中，以便类自动可用。当我们第一次在代码中使用类时，其代码会自动加载。我们可以创建一个表示请求的对象，如下所示：

```php
$request = \Symfony\Component\HttpFoundation\Request::createFromGlobals();
```

当我们引入多个包中的代码时，需要确保包中定义的名称不会冲突。PHP 提供了一种称为命名空间（namespaces）的功能，可防止命名冲突。你可以在之前的示例中看到，HttpFoundation 组件提供的 Request 对象具有 _完全限定_ 名称：

```php
\Symfony\Component\HttpFoundation\Request
```

由于此文件中没有名为 Request 的内容，因此不会发生名称冲突。因此，我们可以使用 PHP 的 use 关键字将名称 _导入_ 到本地作用域，以整理代码。你可以在清单 3.2（第 2 行和第 5 行）中看到这方面的演示。

现在我们有了一个对象，可以用来从请求中获取信息：

```php
$name = $request->get('name');
```

你会注意到我也在示例页面中添加了一个 print_r 语句（第 16 行，清单 3.2），以便你可以查看 $request 对象的结构。清单 3.2 展示了我们的新 public/index.php 文件。

```php
1 <?php
2 use Symfony\Component\HttpFoundation\Request;
3 require __DIR__.'../vendor/autoload.php';
4
5 $request = Request::createFromGlobals();
6 $name = $request->get('name');
7 ?>
8 <!DOCTYPE html>
9 <html lang="en">
10 <head>
11 <meta charset="UTF-8">
12 <title>Document</title>
13 </head>
14 <body>
15 <h1>Hello <?php print $name; ?>!</h1>
16 <pre><?php print_r($request); ?></pre>
17 </body>
18 </html>
```

### 清单 3.2：public/index.php

启动 PHP 内置 Web 服务器（如果之前仍在运行，则无需重复），并在浏览器中加载页面以检查是否正常工作。

```bash
$ php -S localhost:4000 -t public/
```

请务必在 URL 中为 $name 参数提供值，如下所示：

```
http://localhost:4000/?name=World
```

备注：直接输出用户输入绝不是好主意。这是将安全问题引入代码的最简便方法。在此示例中，我们直接从用户输入获取了 $name 变量并将其输出。在实际情况中，你会过滤此值以删除任何危险字符，以防止跨站脚本（XSS）攻击。我们在此不这样做，因为我们将使用一个模板系统来为我们处理此问题。你可以通过加载以下 URL 来确认此操作不安全：

```
http://localhost:4000/?name=Danger<script>alert('hi!')</script>
```

你将看到一个 JavaScript 警告。GET 参数中的代码直接嵌入到页面中。你不必是安全专家也能意识到，允许用户将 JavaScript 代码注入页面是个坏主意。

## 第 4 章
### 模板

目前我们所有代码都放在一个源文件（index.php）中。在我们的 PHP Web 框架中，我们希望将逻辑与显示分开。随着项目规模扩大，这样做更具可扩展性且更易于维护。这也意味着设计师可以单独处理模板，而无需了解任何 PHP 代码。我们还可以受益于自动转义（过滤危险内容）等安全功能。

有许多可作为 PHP 包使用的模板引擎^1。你（或你的 Web 设计师）可能有偏爱。你可能想要使用某个特定模板，因为它得到工作流中其他工具的支持。Mustache[13] 很流行，因为它在几乎所有语言中都有实现，但有些人发现其无逻辑模板有局限性。我们将使用 Twig[29]，因为它“灵活、快速且安全”。

让我们使用 Composer 安装 Twig：

```bash
$ composer require twig/twig
```

你的 composer.json 配置文件的 require 部分现在应如清单 4.1 所示。

```json
9 "require": {
10 "symfony/http-foundation": "^3.0",
11 "twig/twig": "^1.24"
12 }
```

### 清单 4.1：composer.json

在项目中创建一个模板文件夹，并按清单 4.2 创建名为 templates/index.html 的新文件。

^1 你可以使用 Packagist 网站搜索 PHP 包。以下是按下载量排序的“template”搜索[15]。

```html
1 <!doctype html>
2 <html lang="en">
3 <head>
4 <meta charset="UTF-8">
5 <title>Document</title>
6 </head>
7 <body>
8 <h1>Hello {{ name }}!</h1>
9 </body>
10 </html>
```

### 清单 4.2：templates/index.html

Twig 网站提供了模板语法的完整参考[28]。注意它如何使用 {{ 和 }} 来界定表达式。界定符之外的内容将作为 HTML 输出。界定符内的表达式会被求值，并将其输出插入到 HTML 中。在此示例中，简单表达式 {{ name }} 将求值为提供的 name 变量的值。你将在下文看到如何传入模板所期望的所有变量。

现在让我们将系统的其余部分转换为使用模板。这意味着修改 public/index.php，使其不再将 HTML 标记硬编码在其中。目前，我们将用加载和执行 Twig 的代码来替换它。

Twig 是一个非常灵活的系统，由各种组件组成。要开始使用，你只需要一个 *模板加载器*（Template Loader），以便 Twig 知道如何加载模板文件，以及一个 *Twig 环境*（Twig Environment），所有模板处理都在此发生。

清单 4.3 显示了新的 public/index.php 文件，其中在第 9 行创建了模板加载器，在第 10 行加载了 Twig 环境。

```php
1 <?php
2 use Symfony\Component\HttpFoundation\Request;
3 require __DIR__.'.././vendor/autoload.php';
4
5 $request = Request::createFromGlobals();
6
7 $name = $request->get('name');
8
9 $loader = new Twig_Loader_Filesystem(__DIR__.'.././templates');
10 $twig = new Twig_Environment($loader);
11
12 echo $twig->render('index.html',['name' => $name]);
```

### 清单 4.3：public/index.php

HTML 标记已被删除，现在是在第 12 行调用 $twig 对象的 render() 方法时生成的。对 $twig->render() 的调用需要两个参数。第一个是模板名称，第二个是要传递给模板的 *模板变量* 数组。在我们的模板文件（templates/index.html）中，有一个引用名为 name 的变量的表达式 {{ name }}。在调用 render 时，我们传递从请求对象检索到的 $name 变量。

如果之前未运行，请再次启动 PHP 内置 Web 服务器。如果你加载以下 URL，应看到“Hello World！”。
http://localhost:4000/?name=World

请注意，如果你直接访问 http://localhost:4000 而不提供 name 参数，则只会看到“Hello !”。我们在第 2 章（清单 2.1）中创建的基本测试脚本将失败。让我们通过为 name 提供默认值来修复这个问题。

清单 4.4 展示了 Twig default() 过滤器的用法。管道符号 (|) 用于将 *name* 变量的输出 *管道* 到 *default* 过滤器。Twig 提供了许多可用的过滤器[12]。如果输入为空，此过滤器只是提供一个默认值。

```html
1 <!doctype html>
2 <html lang="en">
3 <head>
4 <meta charset="UTF-8">
5 <title>Document</title>
6 </head>
7 <body>
8 <h1>Hello {{ name | default('World') }}</h1>
9 </body>
10 </html>
```

### 清单 4.4：templates/index.html

备注：顺便提一下，你可以测试一下这如何解决上一章末尾讨论的安全问题。你可以尝试访问同一个不安全的 URL，但这次请注意输出中你会看到 Hello Danger<script>alert(...)</script>！Twig 在输出时会自动过滤变量。HTML 标签被转义，因此它们会显示在页面上，而不是被解释为有效的脚本标签。





## 第 5 章 内容

既然我们已经建立了模板系统，就需要一些内容来填充模板。未来我们可能需要数据库来进行更高级的内容管理。目前，我们将把内容存储在简单的文本数据文件中。

在项目中创建一个名为 data 的文件夹，它将是我们的扁平文件数据存储的根目录。开发期间我们将使用本地文件系统上的一个文件夹，但得益于 Flysystem[9] 包，这些数据文件可以放在任何地方。我们不使用 PHP 内置的文件访问，而是使用 Flysystem，因为它提供了文件系统抽象。这提供了一个用于处理文件的优雅 API，包括加载、保存、重命名、复制、删除和列出文件。因为它是一个抽象，我们可以以相同的方式处理多个文件系统。插件为不同类型的文件系统提供实现细节。Flysystem 将这些插件称为适配器。有适用于本地文件、Azure、Amazon S3、Dropbox、FTP、SFTP、WebDAV 等的适配器，还有更多。

使用 Composer 安装 Flysystem：

```
$ composer require league/flysystem
```

Composer 将下载最新版本，将其添加到配置的 require 部分，并通过自动加载器使其可供 PHP 代码使用。清单 5.1 显示了 composer.json 文件中 require 部分在新增内容后的样子。

```
9 "require": {
10 "symfony/http-foundation": "^3.0",
11 "twig/twig": "^1.24",
12 "league/flysystem": "^1.0"
13 }
```

### 清单 5.1：composer.json

我们将使用 \League\Flysystem\Filesystem 对象与文件系统交互。为了实例化文件系统，我们需要先创建适配器。我们使用的是 Local 适配器，它要求将要用作文件系统根目录的文件夹作为参数传递给构造函数。我们从 Flysystem 导入命名空间，然后按如下方式创建对象：

```
<?php
use League\Flysystem\Adapter\Local;
use League\Flysystem\Filesystem;
$adapter = new Local(__DIR__.'../data');
$filesystem = new Filesystem($adapter);
```

让我们以 JSON 格式创建一个简单的数据结构。我们可以使用 PHP 内置的 json_decode() 函数将文件中的 JSON 数据转换为 PHP 数组。在 data 文件夹中创建一个名为 data/menu.json 的文件，如清单 5.2 所示。

```
1 {
2 "index": {
3 "title": "Hello World!",
4 "content": "Welcome to my PHP framework."
5 },
6 "about": {
7 "title": "About",
8 "content": "This is an example site."
9 }
10 }
```

### 清单 5.2：data/menu.json

我们可以从 $filesystem 中 read() 文件并将其解析为 JSON 数据。我将 true 作为第二个参数传递给 json_decode() 函数，因为我希望结果是一个值数组，而不是 PHP 对象：

```
$variables = json_decode($filesystem->read('menu.json'), true);
```

然后我从 $variables 数组中提取所需数据，并将其作为第二个参数传递给 $twig->render() 的 Twig 模板。清单 5.3 显示了带有这些更改的新 index.php 文件。

```
1 <?php
2 use League\Flysystem\Adapter\Local;
3 use League\Flysystem\Filesystem;
4 use Symfony\Component\HttpFoundation\Request;
5
6 require __DIR__.'./../vendor/autoload.php';
7
8 $request = Request::createFromGlobals();
9 $adapter = new Local(__DIR__.'./../data');
10 $filesystem = new Filesystem($adapter);
11
12 $variables = json_decode($filesystem->read('menu.json'), true);
13
14 $loader = new Twig_Loader_Filesystem(__DIR__.'./../templates');
15 $twig = new Twig_Environment($loader);
16 echo $twig->render('index.html', $variables['index']);
17
```

### 清单 5.3：public/index.php

可以看到我目前没有从 $request 中使用任何内容，但暂时保留了它。清单 5.4 显示了更新后的 Twig 模板，用于使用从 menu.json 传入的变量。

```
1 <!doctype html>
2 <html lang="en">
3 <head>
4 <meta charset="UTF-8">
5 <title>{{ title }}</title>
6 </head>
7 <body>
8 <h1>{{ title }}</h1>
9 <p>{{ content }}</p>
10 </body>
11 </html>
```

### 清单 5.4：templates/index.html

## 第 6 章 路由

我们已经有了模板系统和基本的扁平文件数据存储。现在我们需要根据请求提供不同响应的能力。Web 框架倾向于使用一种称为前端控制器的设计模式，其中单个脚本负责处理所有请求。这通常需要对 Web 服务器进行一些配置。如果不为 Web 服务器包含配置，则需要在站点的每个 URL 中包含控制器脚本的名称，您的 URL 将如下所示：

http://example.com/index.php?page=about

而您真正想要的是：

http://example.com/about

您可能希望通过 URL 传递更多信息。例如，如果要显示 ID=1 的文章，您的 URL 可能是：

http://example.com/index.php?type=article&id=1

而您真正想要的是：

http://example.com/article/1

或者甚至可能是：

http://example.com/articles/my-article-title

如果没有配置，Web 服务器不知道应将所有传入请求映射到前端控制器脚本。当它看到：

http://example.com/about

它可能会尝试加载名为 about 或 about/index.html 的文件并返回 404 错误。

### 服务器配置

配置前端控制器的过程取决于您使用的服务器。下面我将介绍如何在 Apache 和 Nginx 上配置此功能。本周末我们只使用 PHP 内置 Web 服务器。这个开发服务器不需要任何配置。当我们使用以下命令启动内置服务器时，我们会自动免费获得对 index.php 文件的路由：

```
$ php -S localhost:4000 -t public/
```

如果您使用 Apache，则可以创建 .htaccess 文件来添加 Web 服务器配置。类似这样的内容对 Apache 有效：

```
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . index.php
[L]
```

这需要启用 Apache 的 rewrite 模块。配置首先检查请求不是针对现有文件（图片、css、js 等），然后将其他所有内容路由到 index.php。

Nginx 是另一种常用于 PHP 的 Web 服务器。在这种情况下，您将类似这样的内容添加到 nginx.conf：

```
try_files $uri $uri/ /index.php;
```

### 创建响应

我们添加了 HTTP Foundation 组件，以便为使用 HTTP 消息提供一个良好的面向对象接口。我们已经看到如何从 HTTP 请求创建对象。现在让我们使用 HTTP Foundation 来创建 HTTP 响应对象。到目前为止，我们一直直接打印输出，并依赖 PHP 将其作为响应发送。得益于 HttpFoundation，将其转换为 `Response` 对象很容易。该组件提供了不同的响应类型，以便轻松发送 JSON 结果或二进制文件，但目前我们将只使用标准 HTML 响应。

该包提供了几种创建响应的不同方式。您可以创建一个新的 `Response` 对象：
`use Symfony\Component\HttpFoundation\Response; $response = new Response($content);`

您还可以通过构造函数设置 HTTP 状态码和 HTTP 标头。默认情况下，HTTP 状态码将为 200。如果要提供“404 页面未找到”页面，可以按如下方式创建响应：
`$response = new Response(“not found”, 404);`

生成响应后，必须将其发送给用户。这是通过在 `$response` 对象上调用 `send()` 完成的，如下所示：
`$response->send();`

还提供了一个方便的工厂方法，您可以（可选）向其提供内容、状态和标头：
`$response = Response::create($content, $status, $headers);`

默认内容为空字符串，因此您需要为此提供自己的值。您可以省略状态和标头并使用默认值（假设没有出错）。默认状态为 200。工厂方法在生成响应时支持链式调用，因此您可以直接调用 `send()` 方法，如下所示：
`Response::create($content)->send();`

清单 6.1 显示了我们 `index.php` 文件的新版本，它将 Twig 结果封装为 HTTP 请求对象并发送它（第 20 行）。

```
1 <?php
2 use League\Flysystem\Adapter\Local;
3 use League\Flysystem\Filesystem;
4 use Symfony\Component\HttpFoundation\Request;
5 use Symfony\Component\HttpFoundation\Response;
6
7 require __DIR__.'../vendor/autoload.php';
8
9 $request = Request::createFromGlobals();
10
11 $adapter = new Local(__DIR__.'../data');
12 $filesystem = new Filesystem($adapter);
13
14 $variables = json_decode($filesystem->read('menu.json'), true);
15
16 $loader = new Twig_Loader_Filesystem(__DIR__.'../templates');
17 $twig = new Twig_Environment($loader);
18
19 $content = $twig->render('index.html', $variables['index']);
20 Response::create($content)->send();
```

### 清单 6.1：public/index.php





### App 类

现在我们准备开始为应用程序添加其他路由。让我们先通过为代码创建一个独立的 App 类来稍微整理一下。然后我们将把代码从 index.php 移出来，以便能更有条理地组织。

我们需要自己的命名空间，这样在定义 App 类时就不必担心未来与其他名为 App 的东西发生冲突。我们还使用这个命名空间来配置 Composer，指定源代码的位置。让我们使用 Weekend 作为我们的命名空间。

在项目根目录下创建一个 src 文件夹。源代码将放在这里。从现在起，我们将只使用 public 文件夹来存放公开可访问的资源，与源代码分开。public 文件夹将包含我们的静态资源，如图片、CSS 和 JavaScript。我们还需要保留 public/index.php 文件，因为所有 Web 请求都会路由到这里。我们将修改 public/index.php 文件，使其只加载并运行我们的 App。

我们在 src/App.php 中创建应用程序的源文件。我们遵循 PSR-4 规范[19]来命名文件和类。我们告诉 Composer 源文件所在的位置，然后它会将它们添加到自动加载器中。这意味着我们不需要包含所有源文件，因为它们会在需要时自动加载。

列表 6.2 显示了我们放在 src/App.php 中的新 App 类的代码，使用了之前 index.php 文件中的代码。列表 6.3 显示了加载并运行我们的 App 的新 index.php 文件。

### Listing 6.2: src/App.php

```php
<?php
namespace Weekend;

use League\Flysystem\Adapter\Local;
use League\Flysystem\Filesystem;
use Symfony\Component\HttpFoundation\Request;
use Symfony\Component\HttpFoundation\Response;
use Twig_Environment;
use Twig_Loader_Filesystem;

class App
{
    public function run(Request $request)
    {
        $adapter = new Local(__DIR__ . '/../data');
        $filesystem = new Filesystem($adapter);
        $variables = json_decode($filesystem->read('menu.json'), true);
        $loader = new Twig_Loader_Filesystem(__DIR__ . '/../templates');
        $twig = new Twig_Environment($loader);
        $content = $twig->render('index.html', $variables['index']);
        return Response::create($content);
    }
}
```

### Listing 6.3: public/index.php

```php
<?php
use Symfony\Component\HttpFoundation\Request;

require __DIR__ . '/../vendor/autoload.php';
$request = Request::createFromGlobals();

$app = new \Weekend\App();
$response = $app->run($request);
$response->send();
```

如果你现在尝试运行，会得到一个错误。消息将出现在你的浏览器或 PHP 错误日志中，具体取决于你的配置。它会显示 Class Weekend\App not found。这是因为我们尚未将类包含在自动加载系统中。要做到这一点，我们需要将其添加到 composer.json 配置中。在 autoload 下创建一个 psr-4 条目，并将 Weekend 命名空间映射到我们的 src 文件夹。Composer 对此处的格式很在意。文件必须是有效的 JSON。注意不要添加多余的逗号，或遗漏命名空间末尾的双反斜杠。列表 6.4 显示了更新后的 composer.json 文件。

### Listing 6.4: composer.json

```json
{
    "name": "darrenmothersel/php-framework",
    "authors": [
        {
            "name": "Darren",
            "email": "darren@darrenmothersele.com"
        }
    ],
    "require": {
        "symfony/http-foundation": "^3.0",
        "twig/twig": "^1.24",
        "league/flysystem": "^1.0"
    },
    "autoload": {
        "psr-4": {
            "Weekend\\": "src/"
        }
    }
}
```

现在使用 dump-autoload Composer 命令重新生成自动加载器：

```bash
$ composer dump-autoload
```

只有在手动编辑 composer.json 文件中的自动加载器设置时才需要运行此命令。当你使用 Composer 更新或安装新包时，自动加载器会自动重新生成。

### 路由

现在我们准备实现一个基本路由器。在上一步中，我们将所有功能都移到了 App 类的 run() 方法中。run() 方法以 Request 对象作为输入，并返回一个 Response 对象。这是所有 Web 应用程序的基础，所有 Web 框架都有这个基本功能。

我们简单应用（在当前状态下）的限制是功能被硬编码到了 run() 方法中。我们需要一种根据请求将调用路由到不同功能的方法。

首先，让我们尝试一个简单的路由器，它使用请求中的信息和我们之前创建的 data/menu.json 文件中的配置。我们使用 getPathInfo() 方法从请求中获取请求的路径：

```php
$path = $request->getPathInfo();
```

现在我们可以通过检查 $path 变量来更改响应的 $content。例如，使用这样的 switch 语句：

```php
$content = "";
switch ($path) {
case '/':
case '/index':
    $content = $twig->render('index.html', $variables['index']);
    break;
case '/about':
    $content = $twig->render('index.html', $variables['about']);
    break;
}
```

这个 switch 语句定义了两个不同的路由及其对应的代码。我们稍后会回到此处，但你可能已经看到改进的方法。在我们的 run() 方法中，我们只需要将 $content 包装在 Response 中并返回它。我们还进行错误检查，当路径未匹配时返回 404：

```php
if (empty($content)) {
    return Response::create("Not found", 404);
}
return Response::create($content);
```

你可以尝试每个 URL 来确认这行得通：

- http://localhost:4000/
- http://localhost:4000/index
- http://localhost:4000/about

另外，尝试加载一个未定义路由的 URL 并检查是否会得到 404 错误：

```
http://localhost:4000/contact
```

## 第 7 章

### 控制器

自我们的第一个“Hello World！”示例以来，我们已经走得很远了，当时我们在一个 PHP 脚本中完成了所有事情。我们现在已经有了一些结构，但所有内容仍然在 App 类的单个 run() 方法中。

在 Web 框架中，你通常会发现不同的请求类型由不同的对象负责。前端控制器将请求分发给适当的控制器以生成响应。我们迄今为止定义的两个路由都可以由同一个控制器处理。如果你看看我们创建的基本路由器，生成内容的代码几乎是一样的。让我们创建一个 BasicPageController 类来封装这个功能。

按照 PSR-4 的自动加载命名规则，我们为控制器创建一个名为 src/Controller 的文件夹。我们的 Weekend 命名空间映射到 src 文件夹，因此我们的控制器的命名空间将是 Weekend\Controller。如果我们需要完整引用我们的新控制器类，它将被称为 Weekend\Controller\BasicPageController。列表 7.1 显示了我们新 BasicPageController 类的代码。

### Listing 7.1: src/Controller/BasicPageController.php

```php
<?php
namespace Weekend\Controller;

use League\Flysystem\Adapter\Local;
use League\Flysystem\Filesystem;
use Symfony\Component\HttpFoundation\Response;
use Twig_Environment;
use Twig_Loader_Filesystem;

class BasicPageController
{
    protected $filesystem;
    protected $menu;
    protected $twig;

    public function __construct()
    {
        $adapter = new Local(__DIR__ . '/../../data');
        $this->filesystem = new Filesystem($adapter);
        $this->menu = json_decode($this->filesystem->read('menu.json'), true);
        $loader = new Twig_Loader_Filesystem(__DIR__ . '/../../templates');
        $this->twig = new Twig_Environment($loader);
    }

    public function get($path)
    {
        $page = ($path == '/') ? 'index' : substr($path, 1);
        if (isset($this->menu[$page])) {
            $content = $this->twig->render('index.html', $this->menu[$page]);
            return new Response($content);
        }
        return Response::create("not found", 404);
    }
}
```

构造函数（第 16-25 行）现在负责创建文件系统和 Twig 环境。我们还将 menu.json 的内容加载到 $menu 变量中，以便在我们的 *控制器回调* 中稍后使用。get() 方法（第 27-36 行）是我们的回调，路由器将为此控制器定义的请求 *分发* 到该回调。之前硬编码到路由器中的处理响应的代码已从 App 的 run() 方法移动到此控制器的 get() 方法中。

get() 回调中的第 29 行检查默认路径，并从路径中去掉开头的 /。$page 的值用于获取 $this->menu 数组的相应部分，该数组在构造函数中通过读取 menu.json 文件创建。

我们 App 类中的路由器现在简单多了。我们将所有三个定义的路由都路由到同一个控制器。列表 7.2 显示了我们 run() 方法中的新路由代码。

### Listing 7.2: src/App.php

```php
public function run(Request $request)
{
    $path = $request->getPathInfo();
    switch ($path)
    {
    case '/':
    case '/index':
    case '/about':
        $controller = new BasicPageController();
        return $controller->get($path);
    }
    return Response::create("Not found", 404);
}
```





### 多控制器

现在我们可以添加另一个具有新功能的控制器。让我们创建一个简单的联系表单。清单 7.3 展示了空 ContactController 类的代码。这只是一个轮廓，展示了类代码的结构。

```php
<?php
namespace Weekend\Controller;

class ContactController
{
public function __construct()
{
}

public function get()
{
}

public function post()
{
}
}
```

清单 7.3: src/Controller/ContactController.php

我将添加一个实例变量来存储 Twig 环境，以及我在 BasicPageController 中使用的相同初始化代码。你可能注意到我们在重复自己，这通常表明我们可以改进代码设计。我们稍后会再次讨论这个问题，并看看如何避免在两个控制器中拥有相同的初始化代码。

我的 ContactController 构造函数现在如下所示：

```php
protected $twig;
public function __construct() {
$loader = new Twig_Loader_Filesystem(__DIR__.'/../../templates'); $this->twig = new Twig_Environment($loader);
}
```

在这个控制器中，我有两个回调，一个叫 get()，另一个叫 post()。这是因为会有两种不同类型的对该控制器的调用。路由器会将 HTTP GET 和 POST 请求分发到这个控制器。我们稍后会看看如何配置这一点，但现在，让我们就从 get() 回调中创建并返回一个联系表单。我的第一次尝试如下：

```php
public function get() {
$form = $this->twig->render('forms/contact.html');
$content = $this->twig->render('index.html', [
'title' => 'Contact',
'content' => $form,
]);
return new Response($content);
}
```

现在更新 App 中定义的路由器，将 /contact 路径的请求发送到新的 ContactController。在 run() 方法的 switch 语句中添加以下 case：

```php
case '/contact':
$controller = new ContactController();
return $controller->get();
```

如果你现在尝试访问 /contact，将会收到错误。错误来自 Twig，因为我们要求它渲染一个不存在的模板。为了使其工作，请创建 templates/forms 文件夹，并添加一个 contact.html 模板表单，如清单 7.4 所示。

```html
<form action="/contact" method="post">
<label for="name">Name</label>
<input type="text" name="name"><br>
<label for="email">Email</label>
<input type="text" name="email"><br>
<label for="message">Message</label>
<textarea name="message" cols="30" rows="10"></textarea><br>
<input type="submit" value="Send">
</form>
```

**清单 7.4:** templates/forms/contact.html

你还需要更新 index.html 模板，因为它会自动转义 $content 变量并显示 HTML 标签。这是前面描述的安全措施。我们添加 raw 过滤器以禁用模板中的自动转义，因为我们知道它不会是用户输入。但是，我们稍后会再次讨论并看看如何改进这一点。现在，请更新 index.html 模板文件，以原样输出内容：

```php
<p>{{ content | raw }}</p>
```

现在当你访问 /contact 时，应该会看到联系表单。但是，由于路由器不知道 GET 和 POST 请求之间的区别，当你点击提交时也会看到表单。提交按钮会通过 POST 请求发送表单数据。让我们向路由器添加一个路由，将此分发到 ContactController 上的 post() 回调。

HTTP 方法可从 $request 对象获取：
$method = $request->getMethod();

我们在路由器中使用这个 $method 变量来决定控制器上调用哪个回调方法。请注意，我还传递了 $request 变量，以便 post() 回调可以获取提交的数据：

```php
case '/contact':
$controller = new ContactController();
if ($method == 'POST')
{
return $controller->post($request);
}
return $controller->get();
```

剩下的就是实现 post() 请求，处理表单数据，然后用感谢信息进行响应：

```php
public function post(Request $Request) {
// TODO: validate input and send email
$content = $this->twig->render('index.html', [
'title' => 'Contact',
'content' => "Thank you for your message.",
]);
return new Response($content);
}
```

我故意将输入验证和发送电子邮件留作未来任务，稍后再实现。这里重要的是要看到不同的控制器如何映射到不同的请求，以及不同的 HTTP 方法如何映射到控制器上的不同回调方法。在控制器变得过于复杂之前，我们迫切需要处理依赖项。

## 第 8 章

### 依赖注入

我们现在有两个控制器。如果你查看 BasicPageController 和 ContactController 的构造函数，你会看到一些重复代码。两个控制器都依赖于用于渲染输出的 Twig 系统。两个控制器目前都会实例化他们自己的 Twig 环境版本，并将其存储在实例变量中。如果你关心软件的可维护性，像这样重复代码绝不是个好主意。如果 Twig 代码需要更改，你必须找到每个使用它的位置并进行更新。这里只有两个控制器，这可能不是什么大问题，但随着系统增长，复杂性也会增加。保持事物分离很重要。

Twig 依赖项被硬编码到两个控制器中。BasicPageController 还对我们的 $filesystem 对象和 menu.json 配置有硬编码依赖。

测试具有硬编码依赖的对象是困难的。如前面我们简要介绍测试时所见，我们理想情况下希望分别测试每个功能。

如果我们可以移除硬编码依赖，我们可以使控制器更容易理解，更易于维护，并隔离功能。我们通过使用依赖注入来实现这一点，这仅仅意味着我们传入依赖项，而不是在类中创建它们。因此，对于 ContactController，我们将 Twig 环境传递给构造函数：

```php
public function __construct(Twig_Environment $twig) {
$this->twig = $twig;
}
```

对于 BasicPageController，我们将 Twig 环境和菜单配置传递给构造函数。我们不再需要 $filesystem，因为它只是用于加载配置：

```php
public function __construct(Twig_Environment $twig, $menu) {
$this->twig = $twig;
$this->menu = $menu;
}
```

我们的控制器现在简单得多，但这使我们的 App 有点更复杂。我们需要实例化依赖项，以便将它们传递给控制器。由于两个控制器都使用 Twig，我已将其作为全局服务添加，在 App 构造函数中创建一个实例变量。我还以同样的方式添加了 $filesystem：

```php
protected $twig;
protected $filesystem;
public function __construct() {
$loader = new Twig_Loader_Filesystem(__DIR__ . '/../templates');
$this->twig = new Twig_Environment($loader);
$adapter = new Local(__DIR__ . '/../data');
$this->filesystem = new Filesystem($adapter);
}
```

然后我添加了一个私有方法来加载菜单配置：

```php
private function getMenuConfig()
{
return json_decode($this->filesystem->read('menu.json'), true);
}
```

现在更新路由器，以创建并将依赖项传递给控制器：

```php
switch ($path) {
case '/':
case '/index':
case '/about':
$menu = $this->getMenuConfig();
$controller = new BasicPageController($this->twig, $menu);
return $controller->get($path);
case '/contact':
$controller = new ContactController($this->twig);
if ($method == 'POST')
{
return $controller->post($request);
}
return $controller->get();
}
```

### 测试

既然我们的控制器是独立的，它们应该更容易测试。让我们通过重新查看我们的简单 test.php 脚本来尝试这一点。清单 8.1 展示了如何单独测试控制器的功能。我们不测试依赖项，因此创建依赖项的假（简化）版本并将它们传递给控制器。我们这样做是为了我们想要针对控制器测试的所有场景。

```php
<?php
use Weekend\Controller\BasicPageController;
require_once 'vendor/autoload.php';
$templates = [
'index.html' => '{{ title }}',
];
$twig = new Twig_Environment(
new Twig_Loader_Array($templates));
$menu = ['test' => [
'title' => 'Hello World!',
'content' => 'Test content'
]];
$controller = new BasicPageController($twig, $menu);
$output = $controller->get('/test');
if (strpos($output, "Hello World!"))
{
echo "Test passed!", PHP_EOL;
}
```

**清单 8.1:** test.php

这是一个简单的示例，在现实中，你可能会使用测试框架。PHPUnit 是一个流行的测试框架，提供了一种创建假对象（在测试中称为 Mocks）的机制，可用作依赖项。许多 PHP 包都带有适配器和插件，可用作测试中的依赖项。例如，我们用作文件系统抽象的 Flysystem 包提供了 Memory 和 Null 适配器，你可以在测试中用它们来创建假文件系统。





### DI 容器

我们已经看到使用依赖注入简化了我们的控制器类。一般来说，依赖注入使代码更易于维护、更易于复用，并且更易于测试。但它增加了调用控制器的代码工作量，因为调用代码在使用控制器之前必须创建并传入依赖项。我们还实例化了 $filesystem 依赖项，尽管它并不是在每个请求中都被使用。我们可以通过使用依赖注入容器来解决这两个问题。

让我们抽象一下，以便更详细地了解依赖注入的工作原理。我们有一个类 A，它需要 B，但我们不想在 A 内部硬编码 B 的创建。因此我们将 B 传递给 A 的构造函数。

```
class A
{
public function doSomething() { $b = new B();
return $b->run($this->data);
}
}
$a = new A();
$a->doSomething();
```

我们使用依赖注入，并这样做：

```
class A {
protected $b;
public function __construct(B $b) {
$this->b = $b;
}
public function doSomething() {
return $this->b->run($this->data);
}
}
$b = new B();
$a = new A($b);
$a->doSomething();
```

但如果 b 也有依赖项呢？而这些依赖项又有依赖项？创建对象的过程可能会变得非常复杂。你最终会得到：

```
$d = new D();
$c = new C();
$b = new B($c, $d);
$a = new A($b);
$a->doSomething();
```

而你真正想做的只是：

```
$a = new A();
$a->doSomething();
```

大多数 PHP Web 框架提供的解决方案是某种用于管理依赖和依赖注入的机制。本质上，这只是一种创建对象并配置其所需依赖项的推荐方式。这通常被称为容器。我们使用容器的伪代码示例可能如下所示：

```
$container->get('A')->doSomething();
```

PHP 中有许多可用选项，包括：

- Symfony 提供了一个 DI 组件[26]，允许你使用 XML、JSON 或 PHP 配置依赖。
- Pimple[24] 是一个不错的独立选项，被 Silex 微框架使用。
- Container[11] 是由创建我们正在使用的文件系统抽象的同一开发团队提供的解决方案。
- Auryn[1] 提供依赖项的自动装配。

### 注意

重要的是要注意，DI 容器只应用于创建运行应用所需的对象。你绝不应该将 DI 容器作为依赖项传递给类。这种情况实际上发生得相当多，并被视为一种 *反模式*（即与最佳实践相反）。在这种情况下，你所做的是将 DI 容器转换为 *服务定位器*，这与依赖注入应该做的恰恰相反。它将依赖项深藏于类内部，而你实际上正在尝试在顶层暴露并提供所有依赖项。

### 使用 DI 容器

我们将配置一个依赖注入容器，在请求时创建对象及其依赖项。这样做意味着我们的对象只在需要时才会被实例化，并且使调用代码更容易编写，因为我们可以直接创建对象，而无需担心先实例化依赖。

我们将使用 Symfony 依赖注入容器和一个 YAML 配置文件。使用 Composer require 命令将这些 PHP 包安装为依赖：

```
$ composer require symfony/dependency-injection
$ composer require symfony/config
$ composer require symfony/yaml
```

我们现在可以移除在 App 中创建的 _全局服务_，并用容器替换它们：

```
protected $container;
public function __construct() {
$this->container = new ContainerBuilder();
$loader = new YamlFileLoader($this->container, new FileLocator(__DIR__));
$loader->load('services.yml');
}
```

此代码使用 YamlFileLoader 加载存储我们 _服务_ 定义的配置文件。清单 8.2 显示了我们示例的 services.yml 配置文件。此文件的格式由 Symfony DI 容器定义。它允许你指定一个 parameters 节和一个 services 列表。服务是容器知道如何构建的对象。每个服务的配置指定使用哪个类，以及其构造函数需要哪些参数。这些可以引用其他服务（依赖项）或 parameters 节中的配置。

```
parameters:
  template_dir: '../templates'

  data_dir: '../data'

services:
  loader:
    class: Twig_Loader_Filesystem
    arguments: ["%template_dir%"]
  twig:
    class: Twig_Environment
    arguments: ["@loader"]
  adapter:
    class: League\Flysystem\Adapter\Local
    arguments: ["%data_dir%"]
  filesystem:
    class: League\Flysystem\Filesystem
    arguments: ["@adapter"]
```

**清单 8.2:** src/services.yml

我们需要时从容器中获取对象。只有实际使用的依赖项才会被实例化，容器会为我们连接所有依赖。我们只需请求想要的项目，如下所示：

```
$fs = $this->container->get('filesystem');
```

例如，我们的 /contact 路由变成这样：

```
case '/contact':
$twig = $this->container->get('twig');
$controller = new ContactController($twig);
if ($method == 'POST') {
return $controller->post($request);
}
return $controller->get();
```

如你所见，在此示例中，我们从容器中 get() 依赖项，并像之前一样将其传递给控制器。我们或许也应该将此依赖添加到配置中。让我们将控制器添加到 services.yml 文件中，然后使用容器来创建它们。

我们的 ContactController 配置非常简单，因为它仅依赖于 Twig。我们将此添加到 services.yml 文件的 services: 节中：

```
contact_controller:
  class: Weekend\Controller\ContactController
  arguments: ['@twig']
```

我们现在可以直接从 DI 容器中获取控制器。它将在创建联系控制器时自动创建所需的 Twig 依赖。**BasicPageController 稍微复杂一些，因为我们在将菜单配置传递给构造函数之前要对其进行一些处理**。为了帮助做到这一点，我们将创建一个服务类来加载和管理我们的配置。创建 src/Service 文件夹，并使用清单 8.3 作为创建 ConfigService 类的指南。

```
<?php
namespace Weekend\Service;

use League\Flysystem\FilesystemInterface;

class ConfigService
{
  protected $config;
  public function __construct(FilesystemInterface $fs)
  {
    $this->config = json_decode($fs->read('menu.json'), true);
  }

  public function getConfig()
  {
    return $this->config;
  }
}
```

**清单 8.3:** src/Service/ConfigService.php

注：在 ConfigService 类构造函数中，我实际上已将参数类型定义为 FilesystemInterface。接口有点像合同。它不指定实现的任何细节，只说明存在什么功能。它是一种规范。类可以声明它们实现接口规范，这意味着它们为接口规范描述的所有功能提供实现。这样我们就可以轻松地稍后替换其他实现。我们只使用接口中定义的功能，因此可以确保提供的任何其他实现都能工作。

我们现在可以将此 ConfigService 添加到 services.yml 文件中：

```
config_service:
  class: Weekend\Service\ConfigService
  arguments: ['@filesystem']
```

还要添加依赖于 Twig 和这个新配置服务的 BasicPageController：

```
basic_page_controller:
  class: Weekend\Controller\BasicPageController
  arguments: ['@twig', '@config_service']
```

更新 BasicPageController 中的构造函数，以将 ConfigService 作为依赖项，而不是之前传递的原始菜单数据：

```
public function __construct(Twig_Environment $twig, ConfigService $config) {
$this->twig = $twig;
$this->config = $config;
}
```

更新控制器中的 get() 回调，以便从 ConfigService 获取 $menuConfiguration：

```
public function get($path) {
$Page = ($path == '/') ? 'index' : substr($path, 1);
$menu = $this->config->getConfig();
if (isset($menu[$Page])) {
$content = $this->twig->render('index.html', $menu[$page]);
return new Response($content);
}
return Response::create("not found", 404);
}
```

然后最后，整理路由器，使其现在从容器中获取控制器：

```
switch ($path) {
case '/':
case '/index':
case '/about':
$controller = $this->container->get('basic_page_controller');
return $controller->get($path);
case '/contact':
$controller = $this->container->get('contact_controller');
if ($method == 'POST') {
return $controller->post($request);
}
return $controller->get();
}
```

也许你可以开始思考改进的方法。run() 方法现在不必处理实例化依赖和控制器。在 run() 中，我们只是处理将请求路由到正确的控制器回调。你将如何从路由器逻辑中提取路由配置？这是我们稍后会再回来讨论的事情，但目前请考虑以下示例。你看到如何改进它吗？

```
public function run(Request $request) {
$path = $request->getPathInfo();
$method = strtolower($request->getMethod());
$routes = [
'/' => 'basic_page_controller',
'/index' => 'basic_page_controller',
'/about' => 'basic_page_controller',
'/contact' => 'contact_controller',
];
if (isset($routes[$path])) {
$controller = $this->container->get($routes[$path]);
if (is_callable([$controller, $method])) {
return call_user_func_array([$controller, $method], [$request]);
}
}
}
```





return Response::create("Not found", 404);
}

## 第 9 章
设计与布局

让我们暂时把注意力转到前端，让输出看起来更专业一些。public 文件夹是我们项目中唯一可通过 Web 访问的文件夹。我们使用 PHP 内置 Web 服务器作为开发环境，但最终生产环境的 Web 服务器也将指向此处。

到目前为止，我们的 public 文件夹仅包含用于启动 App 的 index.php 文件。它从 PHP 的全局请求变量中创建 $request 对象，实例化 App，将 $request 传递给 app，然后发送生成的 $response。

我们现在将把一些其他文件放入这个 public 文件夹，以便网站用户能够通过 Web 下载它们。我们目前还没有 CSS 或 JavaScript。让我们使用 Twitter Bootstrap，因为这是快速入门的一种方式。我们暂时使用预编译并压缩过的版本。从入门页面 [4] 下载资源包，解压缩并将 css、fonts 和 js 文件夹复制到你的 public 文件夹中。

清单 9.1 展示了使用 Bootstrap 基础模板代码的更新后的基础模板 templates/index.html 文件。清单 9.2 展示了更新为使用 Bootstrap 表单标记的联系表单。

```
2 <html lang="en">
3 <head>
4 <meta charset="utf-8">
5 <meta http-equiv="X-UA-Compatible" content="IE=edge">
6 <meta name="viewport" content="width=device-width, initial-scale=1">
7 <title>{{ title }}</title>
8 <link href="/css/bootstrap.min.css" rel="stylesheet">
9 <!--[if lt IE 9]>
10 <script src="https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
11 <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
12 <![endif]-->
13 </head>
14 <body>
15 <div class="container">
16 <h1>{{ title }}</h1>
17 <p>{{ content | raw }}</p>
18 </div>
19
20 <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
21 <script src="/js/bootstrap.min.js"></script>
22 </body>
23 </html>
```

### 清单 9.1: templates/index.html

```
1 <form action="/contact" method="post">
2 <div class="form-group">
3 <label for="name">Name</label>
4 <input type="text" name="name" id="name" class="form-control">
5 </div>
6 <div class="form-group">
7 <label for="email">Email</label>
8 <input type="email" name="email" id="email" class="form-control">
9 </div>
10 <div class="form-group">
11 <label for="message">Message</label>
12 <textarea name="message" cols="30" rows="10" id="message" class="form-control"></textarea>
13 </div>
14 <input type="submit" value="Send" class="btn btn-primary">
15 </form>
```

### 清单 9.2: templates/forms/contact.html

### 模板继承

还记得我们添加联系表单时，不得不将 {{ content }} 的输出改为 {{ content | raw }} 吗？我们这样做是因为我们渲染了表单模板，然后将其作为 content 变量传递给了页面模板。Twig 拥有 raw 过滤器来绕过其自动过滤和转义。这是一项重要的安全措施，因此理想情况下我们不想禁用它。

我们可以创建单独的 HTML 页面模板，一个用于基础页面控制器，一个用于联系页面，但这会引入不必要的重复。我们要善待我们的未来自己，考虑维护问题。当我们将来回来更新设计时，我们希望有一个单一的位置来进行这些更改。这可以通过将所有公共代码放入单个模板，然后在需要做不同事情时扩展此模板来创建自定义版本来实现。

为了展示其工作原理，我们首先将主 index.html 改为其他模板可以继承的父模板。为此，我们定义可自定义的 Twig 块。清单 9.3 的第 20-23 行定义了一个 content 块。然后我们创建一个名为 basic.html 的新模板文件，它扩展了 index.html。如清单 9.4 所示。这个模板中内容很少，因为我们不需要重新创建整个页面。此模板复用了 index 模板的 HTML，除了将 {% block content %} 定义的区域替换为其自身的 content 块。不要混淆 basic.html 模板中 content 这两个不同的用法。我们有一个名为 content 的块，还有一个名为 content 的输出变量。块指的是我们正在替换的父模板中的 content 块。变量指的是传递给模板的 content 变量。

清单 9.5 显示了为联系页面创建的新模板。这也扩展了主 index 模板。我们再次重新定义 content 块，但这次是包含表单而不是打印 content 变量。

清单 9.6、9.7 和 9.8 显示了控制器中为使用新模板进行输出所需的更新。

```
2 <html lang="en">
3 <head>
4 <meta charset="utf-8">
5 <meta http-equiv="X-UA-Compatible" content="IE=edge">
6 <meta name="viewport" content="width=device-width, initial-scale=1">
7 <title>{{ title }}</title>
8 <link href="/css/bootstrap.min.css" rel="stylesheet">
9 <!--[if lt IE 9]>
10 <script src="https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
11 <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
12 <![endif]-->
13 </head>
14 <body>
15 <div class="container">
16 <h1>{{ title }}</h1>
17
18 {% block content %}
19 <p>Template will replace this content.</p>
20 {% endblock %}
21
22 </div>
23 <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
24 <script src="/js/bootstrap.min.js"></script>
25 </body>
26 </html>
```

### 清单 9.3: templates/index.html

```
1 {% extends 'index.html' %}
2
3 {% block content %}
4 <p>{{ content }}</p>
5 {% endblock %}
```

### 清单 9.4: templates/basic.html

```
1 {% extends 'index.html' %}
2
3 {% block content %}
4 {% include 'forms/contact.html' %}
5 {% endblock %}
```

### 清单 9.5: templates/contact.html

### 清单 9.6: src/Controller/BasicPageController.php

```
25 $content = $this->twig->render('basic.html', $menu[$page]);
```

### 清单 9.7: src/Controller/ContactController.php

```
20 $content = $this->twig->render('contact.html', [
21     'title' => 'Contact'
22 ]);
```

### 清单 9.8: src/Controller/ContactController.php

```
29 $content = $this->twig->render('basic.html', [
30     'title' => 'Contact',
31     'content' => "Thank you for your message.",
32 ]);
```

### 模板逻辑

你可能注意到，我们在最新的 Twig 模板中使用了不同的语法。我们创建的第一批模板仅使用了表达式分隔符，例如 {{ title }}。我们现在引入另一种类型的分隔符，{% ... %}。

双花括号（{{ ... }}）始终包含表达式。内容会被求值并打印出来。它可能包含单个变量，在这种情况下会输出该变量的值。它可以包含更复杂的表达式，并使用过滤器。Twig 求值表达式，将结果传递给任何指定的过滤器，并将结果输出到模板中。

我们可以使用另一种分隔符（{% ... %}）向模板添加逻辑。最后一个示例显示它们用于定义模板之间的继承，以及将一个模板包含在另一个模板中。我们也可以使用它们添加条件语句来打开或关闭模板的部分内容。它们还可以用于添加循环，重复模板的部分内容。

让我们通过使用先前创建的 menu.json 配置文件向模板添加导航来演示这一点。为了做到这一点，我们需要使菜单结构可供我们的 Twig 模板使用。我们鼓励你考虑实现此目的的不同方式。作为示例，我们将创建自己的模板服务。目前我们使用 Twig 提供的 Twig_Environment 类的实例作为我们的模板服务。相反，我们可以定义自己的模板服务，将工作委托给 Twig。这意味着我们将有一个单一的位置向 Twig 环境添加内容。这种方法还有隔离我们对 Twig 依赖性的好处。如果所有模板调用都通过单个服务类进行，那么如果将来我们决定使用不同的模板引擎，将更容易调整我们的框架。

创建一个新模板来存放我们的导航。我在 templates 文件夹中创建了一个名为 include 的子文件夹，我计划将其用于可以包含到其他模板中的模板片段。基于 Bootstrap navbar 组件的示例导航模板如清单 9.9 所示。有趣的部分是第 16-18 行，其中 for 命令用于重复模板的一部分。预期 nav 变量是一个列表，该部分将为列表中的每个项目重复。清单 9.10 显示添加到主 index.html 模板的行，该行将导航包含到模板中。由于基本页面和联系模板都扩展了此模板，因此它们会自动包含此导航。

```
1 <nav class="navbar navbar-default">
2 <div class="container">
3 <div class="navbar-header">
4 <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#main-nav" aria-expanded="false">
5 <span class="sr-only">Toggle navigation</span>
6 <span class="icon-bar"></span>
7 <span class="icon-bar"></span>
8 <span class="icon-bar"></span>
9 </button>
10 <a class="navbar-brand" href="/">PHP Weekend</a>
11 </div>




```
12
13 <div class="collapse navbar-collapse" id="main-nav"> 14 <ul class="nav navbar-nav">
15
16 {% for item in nav %}
17 <li><a href="{{ item.url }}">{{ item.title }}</a></li> 18 {% endfor %}
19
20 </ul>
21 </div> <!-- /.navbar-collapse --> 22 </div> <!-- /.container -->
23 </nav>
```

### 清单 9.9: templates/includes/nav.html

```
17 {% include 'includes/nav.html' %}
```

### 清单 9.10: templates/index.html

nav 变量的值由我们的新 TemplateService 类设置。清单 9.11 显示了这可能是什么样子。我们随后更新控制器以使用我们的模板服务，而不是直接访问 Twig。清单 9.12 和 9.13 显示了控制器类的更新。我们然后需要用新模板服务的详细信息更新我们的依赖注入配置。这以 twig 和 config_service 服务作为依赖进行配置。我们也更改控制器的配置，以提供新的模板服务而不是 twig。清单 9.14 显示了新的 services.yml 配置文件。

```
2
3 namespace Weekend\Service;
4
5
6 use Twig_Environment;
7
8 class TemplateService
9 {
10     protected $twig;
11     protected $menu;
12
13     public function __construct(Twig_Environment $twig, ConfigService $config) 14 {
15         $this->twig = $twig;
16
17         $this->menu = $config->getConfig();
18     }

19     public function render($templateName, $variables) 20 {
21         foreach ($this->menu as $path => $menuItem) 22 {
23             $variables['nav'][] = [
24                 'title' => $menuItem['title'],
25                 'url' => '/' . $path,
26             ];
27         }

28         return $this->twig->render($templateName, $variables); 29 }
30

31 }
```

### 清单 9.11: src/Service/TemplateService.php

```
3 use Symfony\Component\HttpFoundation\Response;

4 use Weekend\Service\ConfigService;

5 use Weekend\Service\TemplateService;

6

7 class BasicPageController
8 {
9     protected $menu;
10     protected $theme;

12     public function __construct(TemplateService $theme, ConfigService $config) 13 {
14         $this->theme = $theme;
15         $this->config = $config;
16     }
17
18     public function get($path)
19     {
20         $page = ($path == '/') ? 'index' : substr($path, 1); 21         $menu = $this->config->getConfig();
22         if (isset($menu[$page]))
23         {
24             $content = $this->theme->render('basic.html', $menu[$page]); 25             return new Response($content);
26         }
27         return Response::create("not found", 404);
28     }
29 }
```

### 清单 9.12: src/Controller/BasicPageController.php

```
3 use Symfony\Component\HttpFoundation\Request;
4 use Symfony\Component\HttpFoundation\Response;
5 use Weekend\Service\TemplateService;
6
7 class ContactController
8 {
9     protected $theme;

11     public function __construct(TemplateService $theme) 12 {
13         $this->theme = $theme;
14     }
15
16     public function get()
17     {
18         $content = $this->theme->render('contact.html', [
19             'title' => ' Contact'
20         ]);
21         return new Response($content);
22     }
23
24     public function post(Request $request)
25     {
26         // TODO: validate input and send email
27         $content = $this->theme->render('basic.html', [
28             'title' => ' Contact',
29             'content' => "Thank you for your message.",
30         ]);
31         return new Response($content);
32     }
```

### 清单 9.13: src/Controller/ContactController.php

```
1 parameters:
2 template_dir: './templates'
3 data_dir: './data'
4
5 services:
6 loader:
7 class: Twig_Loader_Filesystem
8 arguments: ['%template_dir%']
9 twig:
10 class: Twig_Environment
11 arguments: ['@loader']
12 adapter:
13 class: League\\Flysystem\\Adapter\\Local 14 arguments: ['%data_dir%']
15 filesystem:
16 class: League\\Flysystem\\Filesystem 17 arguments: ['@adapter']
18
19 contact_controller:
20 class: Weekend\\Controller\\ContactController 21 arguments: ['@template_service']
22 basic_page_controller:
23 class: Weekend\\Controller\\BasicPageController 24 arguments: ['@template_service', '@config_service'] 25
26 config_service:
27 class: Weekend\\Service\\ConfigService 28 arguments: ['@filesystem']
29
30 template_service:
31 class: Weekend\\Service\\TemplateService 32 arguments: ['@twig', '@config_service']
```

### 清单 9.14: src/services.yml

## 第 10 章

### 复用

目前，我们的框架不是很有用，因为它与我们一直在构建的示例应用程序紧密耦合。构建框架的目的是拥有一组可复用的代码。当我们想要做类似的事情时，应该能够将其包含在项目中，以节省重复进行所有基础工作。为了能够做到这一点，我们需要使代码尽可能可复用。

迄今为止，我们已将所有 PHP 代码放入 src 文件夹。我们还在 vendor 文件夹中有由 Composer 管理的 PHP 代码。最终，我们可以将框架作为一个独立项目，并通过 Composer 包含它，但目前我们将把它存储在项目的单独文件夹中。这将允许我们识别并分离出框架的可复用部分。

创建一个名为 lib/weekend 的文件夹，并将当前 src 文件夹中的所有代码移动到这个新位置。如果您现在尝试访问应用程序，将会收到类似“Uncaught Error: Class Weekend\App not found”的错误。我们需要告诉 Composer 我们已移动命名空间 Weekend 的代码，并更新其自动加载器。按清单 10.1 编辑 composer.json 的 autoload 部分。请注意，我们还将 src 文件夹添加到自动加载器配置中，以便它可以找到站点的代码。在此示例中，我没有为站点特定代码使用命名空间。

```
19 "autoload":{
20 "psr-4":{
21 "Weekend\\": "lib/weekend",
22 "": "src/"
23 }
24 }
```

### 清单 10.1: composer.json

使用 Composer 的 update 或 dump-autoload 命令重新生成自动加载器。您现在应该发现站点又可以正常工作了（假设您仍在运行 PHP 的内置 Web 服务器）。

现在我们可以将站点特定代码放入 src 文件夹。首先，将两个控制器移回 src，因为它们特定于此站点。这会产生一个新错误，因为依赖注入容器不再能找到它们。为了绕过这个问题，我们向 src 文件夹添加一个 services.yml 文件用于站点特定配置。请参阅 10.2 以了解我们如何更新 App 中的构造函数，以便它可以找到我们的额外配置。清单 10.3 显示了带有额外配置的新文件。

请注意，我们首先将局部于 App 的 services.yml 文件加载到依赖注入容器中。这允许我们指定对框架核心至关重要的依赖项。然后我们从 src 文件夹加载第二个 services.yml 配置。这允许我们的应用向依赖注入容器提供额外配置，例如站点特定控制器。这是一种有用的机制，因为它还允许我们按站点覆盖框架配置。

App 构造函数中的第二个 load() 调用（第 19 行，清单 10.2）看起来未来有可能给我们带来 bug。您可能需要考虑提供此额外配置位置的替代方法，以便它不在框架中被硬编码。例如，您可能希望提供一个可在实例化 App 时设置的根目录选项。

App 中 run() 方法的先前路由器在其中将路由硬编码了。这将不起作用，因为框架不再知道有哪些路由可用。为了使路由器更通用，我们允许用户配置自己的路由。清单 10.2 提供了一个简单示例，它使用 addRoute() 方法在 App 中构建可用路由数组。这由 run() 中的路由器使用（第 33-38 行，清单 10.2）。

我们还需要对 BasicPageController 中的 get() 回调进行小幅更改。为了适应通用路由器代码，控制器上的所有路由回调都采用相同的参数。在之前的示例中，基本页面控制器上的 get() 回调将 $path 作为参数，现在它获取 Request 对象，如所有控制器回调一样。

```
2 namespace Weekend;
3
4 use Symfony\Component\Config\FileLocator;
5 use Symfony\Component\DependencyInjection\ContainerBuilder;
6 use Symfony\Component\DependencyInjection\Loader\YamlFileLoader;
7 use Symfony\Component\HttpFoundation\Request;
8 use Symfony\Component\HttpFoundation\Response;
9
10 class App
11 {
12     protected $container;
13     protected $routes;
14
15     public function __construct()
16     {
17         $this->container = new ContainerBuilder();
18         $loader = new YamlFileLoader($this->container, new FileLocator(__DIR__)) ;
19         $loader->load('services.yml');
20         $loader->load('.././src/services.yml');
21     }
22
23     public function addRoute($path, $method, $controller) 24 {
25         $this->routes[$path][$method] = $controller; 26     }
27
28     public function run(Request $request)
29     {
30         $path = $request->getPathInfo();
31         $method = strtolower($request->getMethod());
32
33         if (isset($this->routes[$path][$method]))
34         {
35             $controllerName = $this->routes[$path][$method];
36             $controller = $this->container->get($controllerName);
37             return call_user_func([$controller, $method], $request);
```

### 清单 10.2





```
38 }
39 return Response::create("Not found", 404);
40 }
41 }
```

### 清单 10.2: lib/weekend/App.php

```
services:
contact_controller:
  class: ContactController
  arguments: ['@template_service']
basic_page_controller:
  class: BasicPageController
  arguments: ['@template_service', '@config_service']
```

### 清单 10.3: src/services.yml

```php
<?php

use Symfony\Component\HttpFoundation\Request;
use Symfony\Component\HttpFoundation\Response;
use Weekend\Service\ConfigService;
use Weekend\Service\TemplateService;

class BasicPageController
{
protected $menu;
protected $theme;

public function __construct(TemplateService $theme, ConfigService $config) {
$this->theme = $theme;
$this->config = $config;
}

public function get(Request $request)
{
$path = $request->getPathInfo();
$page = ($path == '/')? 'index' : substr($path, 1);
$menu = $this->config->getConfig();
if (isset($menu[$page]))
{
$content = $this->theme->render('basic.html', $menu[$page]);
return new Response($content);
}
return Response::create("not found", 404);
}
}
```

### 清单 10.4: src/BasicPageController.php

```php
use Symfony\Component\HttpFoundation\Request;
use Symfony\Component\HttpFoundation\Response;
use Weekend\Service\TemplateService;
```

```php
class ContactController
{
    protected $theme;

    public function __construct(TemplateService $theme) {
        $this->theme = $theme;
    }

    public function get()
    {
        $content = $this->theme->render('contact.html', [
            'title' => 'Contact',
        ]);
        return new Response($content);
    }

    public function post(Request $request)
    {
    // TODO: validate input and send email
    $content = $this->theme->render('basic.html', [
        'title' => 'Contact',
        'content' => "Thank you for your message.",
    ]);
    return new Response($content);
    }
}
```

### 清单 10.5: src/ContactController.php

## 接下来？

你现在已经有了自己 PHP Web 框架的雏形。以下是一些关于下一步发展方向的想法：

- 将其用于创建项目的起点。收集你自己偏好的 PHP 包集合，包含配置和样板代码，以便在开始新项目时节省时间。
- 尝试替代的依赖注入容器。试着使用 Pimple[24] 作为应用的基础。你更喜欢这种工作方式吗？还是你喜欢 YAML 配置文件？
- 添加缓存支持以提升性能。
- 完成并改进联系控制器中的表单处理。
- 学习 PHP 安全，包括 CSRF[18]。你可以在这里如何扩展框架以使其更安全？你可以在框架中提供哪些设施，以便在未来的项目中更容易实现安全性？
- 使用你自己的改进版本替换我们的基础路由器。阅读这篇关于使用正则表达式的博客[7]并尝试 FastRoute[8]。或者，如果你更喜欢更友好的 API，试试 Route[22]。
- 查看 Awesome PHP[3] 列表，找出你认为对项目有用的包，并将它们集成到你的框架中。
- 使用 Symfony 的 Session 组件作为存储用户会话的基础，添加用户登录系统。
- 安装 PHPUnit 并编写一些真正的单元测试。
- 添加 DocBlock 格式的文档，以改进 PHPStorm 等 IDE 的支持。
- 选择合适的许可证。大多数 PHP 项目使用开源 MIT 许可证。
- 为用户提供更多自定义应用程序工作方式的方式。考虑实现事件[6] 作为挂钩核心功能的方法。

## 链接

- [1] Auryn 依赖注入容器。https://github.com/rdlowrey/Auryn.
- [2] 作者的个人网站。http://www.darrenmothersele.com. [3] Awesome PHP。https://github.com/ziadoz/awesome-php.
- [4] Bootstrap：入门指南。http://getbootstrap.com/getting-started/. [5] Composer - 全局安装说明。https://getcomposer.org/doc/00-intro.md#globally.
- [6] 事件分发器组件。http://symfony.com/doc/current/components/event_dispatcher/introduction.html.
- [7] 使用正则表达式的快速请求路由。http://nikic.github.io/2014/02/18/Fast-request-routing-using-regular-expressions.html.
- [8] FastRoute - PHP 的快速请求路由器。https://github.com/nikic/FastRoute.
- [9] 由非凡包联盟提供的 Flysystem 文件系统抽象层。http://flysystem.thephpleague.com/.
- [10] Homebrew - macOS 的包管理器。http://brew.sh/.
- [11] League 依赖注入容器。http://container.thephpleague.com/.
- [12] 用于模板的 Twig 过滤器列表。http://twig.sensiolabs.org/doc/filters/index.html.
- [13] Mustache 模板语言。http://mustache.github.io/.
- [14] Packagist 中搜索“HTTP”，按下载量排序。https://packagist.org/search/?q=http&orderBy[0][sort]=downloads&orderBy[0][order]=desc.
- [15] Packagist 中搜索“template”，按下载量排序。https://packagist.org/search/?q=template&orderBy[0][sort]=downloads&orderBy[0][order]=desc.
- [16] PHP 正确做法 - 现代 PHP 在线指南。http://www.phptherightway.com/.
- [17] PHPUnit - PHP 测试框架。https://phpunit.de/.
- [18] 防止 CSRF 攻击。http://blog.ircmaxell.com/2013/02/preventing-csrf-attacks.html.
- [19] PSR-4: 自动加载器。http://www.php-fig.org/psr/psr-4/.
- [20] PSR-7: HTTP 消息接口。http://www.php-fig.org/psr/psr-7/.
- [21] 一周内学会光线追踪。http://in1weekend.blogspot.co.uk/2016/01/ray-tracing-in-one-weekend.html.
- [22] 基于 FastRoute 构建的路由器和分发器。http://route.thephpleague.com/.
- [23] “PHP Framework in One Weekend” 源代码仓库，托管于 GitHub。https://github.com/ideationnet/php-framework.
- [24] 一个简单的 PHP 依赖注入容器。http://pimple.sensiolabs.org/.
- [25] Symfony 组件。http://symfony.com/components.
- [26] Symfony 依赖注入组件。http://symfony.com/doc/current/components/dependency_injection/introduction.html.
- [27] Symfony HTTP 组件。http://symfony.com/doc/current/components/http_foundation/introduction.html.
- [28] Twig 模板语法。http://twig.sensiolabs.org/doc/templates.html. [29] Twig 模板系统。http://twig.sensiolabs.org/.

