

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

