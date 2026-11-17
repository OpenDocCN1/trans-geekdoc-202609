

将所有 symfony 文件放在 web 根目录下，在本地计算机上测试 symfony 没问题，但对于生产服务器来说是个非常糟糕的主意，因为这可能会让最终用户看到应用程序的所有内部细节。

你现在可以通过阅读 Web 服务器配置部分来完成安装。

沙箱本质上只是一个为你执行了一些任务并更改了一些配置的普通 symfony 项目，因此将其用作新项目的起点非常容易。不过请记住，你可能需要调整配置；例如更改与安全相关的设置（参见本章中 XSS 和 CSRF 的配置）。

## 摘要

在本地服务器上测试和尝试 symfony，安装的最佳选择无疑是沙箱，它包含一个预配置的 symfony 环境。

对于真正的开发或生产服务器，请选择存档安装或 SVN 检出。这将安装 symfony 库，你仍然需要初始化一个项目和一个应用程序。应用程序设置的最后一步是服务器配置，这可以通过多种方式完成。Symfony 与虚拟主机配合使用非常完美，也是推荐的解决方案。

如果在安装过程中遇到任何问题，可以在 symfony 网站上找到许多教程和常见问题解答。如果需要，可以将问题提交给 symfony 社区，你将得到快速且有效的回答。

项目初始化后，启动版本控制流程是一个好习惯。

既然你已经准备好使用 symfony，是时候学习如何构建基本的 Web 应用程序了。

## 第 4 章 页面创建基础

出人意料的是，程序员学习新语言或新框架时跟随的第一个教程，通常是那个在屏幕上显示“Hello, world！”的教程。把电脑当作能够向全世界问候的东西，这听起来很奇怪，因为人工智能领域的每一次尝试到目前为止都导致了糟糕的对话能力。但 symfony 不比其他任何程序更笨，证明就是，你可以用它创建一个显示“Hello, <你的名字>”的页面。

### 创建模块骨架

如第 2 章所述，symfony 将页面分组为模块。在创建页面之前，你需要创建一个模块，它最初是一个带有 symfony 能识别的文件结构的空壳。

symfony 命令行自动化了模块的创建。你只需要以应用程序名称和模块名称作为参数调用 generate:module 任务。在上一章中，你创建了一个 frontend 应用程序。要向此应用程序添加一个 content 模块，请键入以下命令：

```
Listing 4-1
$ cd ~/myproject
$ php symfony generate:module frontend content

>> dir+  ~/myproject/apps/frontend/modules/content/actions
>> file+  ~/myproject/apps/frontend/modules/content/actions/
actions.class.php
>> dir+  ~/myproject/apps/frontend/modules/content/templates
>> file+  ~/myproject/apps/frontend/modules/content/templates/
indexSuccess.php
>> file+  ~/myproject/test/functional/frontend/contentActionsTest.php
>> tokens  ~/myproject/test/functional/frontend/contentActionsTest.php
>> tokens  ~/myproject/apps/frontend/modules/content/actions/
actions.class.php
>> tokens  ~/myproject/apps/frontend/modules/content/templates/
indexSuccess.php
```

除了 actions/ 和 templates/ 目录外，此命令仅创建了三个文件。test/ 文件夹中的文件涉及功能测试，直到第 15 章之前你都不需要关心它。actions.class.php（如清单 4-1 所示）会转发到默认模块的 congratulation 页面。templates/indexSuccess.php 文件为空。

### 清单 4-1 - 默认生成的动作，位于 actions/actions.class.php

```php
<?php
class contentActions extends sfActions
{
    public function executeIndex()
    {
        $this->forward('default', 'module');
    }
}
```

如果你查看实际的 actions.class.php 文件，会发现不止这几行，还包含大量注释。这是因为 symfony 建议使用 PHP 注释来记录你的项目，并使每个类文件与 phpDocumentor 工具兼容。

对于每个新模块，symfony 都会创建一个默认的 index 动作。它由名为 executeIndex 的动作方法和名为 indexSuccess.php 的模板文件组成。execute 前缀和 Success 后缀的含义将分别在第 6 章和第 7 章中解释。在此之前，你可以将此命名视为一种约定。你可以通过访问以下 URL 查看相应的页面（如图 4-1 所示）：

http://localhost/frontend_dev.php/content/index

本章不会使用默认的 index 动作，因此你可以从 actions.class.php 文件中删除 executeIndex() 方法，并从 templates/ 目录中删除 indexSuccess.php 文件。

Symfony 提供了除命令行之外的其他方式来初始化模块。其中一种方法是自己创建目录和文件。在许多情况下，模块的动作和模板旨在操作给定表的数据。由于创建、检索、更新和删除表中记录所需的代码通常相同，symfony 提供了一种机制为你生成此代码。

### 图 4-1 - 默认生成的索引页面

![](img/0f886a7f4cbcc3939be96e985ca35ff4_49_0.png)

### 添加页面

在 symfony 中，页面背后的逻辑存储在动作中，表现层在模板中。没有逻辑的页面（仍然）需要一个空动作。

### 添加动作

“Hello, world！”页面将通过 show 动作访问。要创建它，只需向 contentActions 类添加一个 executeShow 方法，如清单 4-2 所示。

*清单 4-2 - 添加动作就像向动作类添加一个 Execute 方法*

```php
<?php
class contentActions extends sfActions
{
  public function executeShow()
  {
  }
}
```

动作方法的名称始终是 executeXxx()，其中名称的第二部分是首字母大写的动作名称。

现在，如果你请求以下 URL：

```
http://localhost/frontend_dev.php/content/show
```

symfony 会抱怨缺少 showSuccess.php 模板。这很正常；在 symfony 中，页面始终由动作和模板组成。

>> URL（不包括域名）区分大小写，symfony 也是如此（尽管 PHP 中的方法名不区分大小写）。这意味着如果你在浏览器中调用 sHow，symfony 会返回 404 错误。

### URL 是响应的一部分

Symfony 包含一个路由系统，允许你在实际动作名称和调用它所需的 URL 形式之间实现完全分离。这允许对 URL 进行自定义格式化，就好像它是响应的一部分。你不再受限于文件结构或请求参数；动作的 URL 可以看起来像你想要的短语。例如，调用名为 article 的模块的 index 动作通常如下所示：

```
http://localhost/frontend_dev.php/article/index?id=123
```

此 URL 从数据库中检索给定文章。在此示例中，它检索 Europe 部分中专门讨论法国金融的一篇文章（id=123）。但 URL 可以通过对 routing.yml 配置文件进行简单更改，以完全不同的方式编写：

```
http://localhost/articles/europe/france/finance.html
```

生成的 URL 不仅对搜索引擎友好，对用户也很有意义，用户可以将地址栏作为伪命令行来执行自定义查询，如下所示：

```
http://localhost/articles/tagged/finance+france+euro
```

Symfony 知道如何为用户解析和生成智能 URL。路由系统会自动从智能 URL 中剥离请求参数并使其可用于动作。它还格式化响应中包含的超链接，使其看起来“智能”。你将在第 9 章中了解更多有关此功能的信息。

总的来说，这意味着动作的命名不应受调用其 URL 形式的影响，而应受动作在应用程序中功能的影响。动作名称解释了动作实际做什么，通常是动词原形（如 show、list、edit 等）。动作名称可以对最终用户完全不可见，因此请不要犹豫，使用明确的动作名称（如 listByName 或 showWithComments）。你将节省解释动作功能的代码注释，而且代码也会更易于阅读。

### 添加模板

动作期望一个模板来呈现自身。模板是模块 templates/ 目录中的一个文件，由动作和动作终止符命名。默认动作终止符是“success”，因此 show 动作要创建的模板文件应命名为 showSuccess.php。

模板应该只包含表现层代码，因此在其中尽可能少地使用 PHP 代码。事实上，显示“Hello, world！”的页面可以有一个像清单 4-3 中那样简单的模板。

### 清单 4-3 - content/templates/showSuccess.php 模板

```php
<p>Hello, world!</p>
```

如果你需要在模板中执行一些 PHP 代码，应该避免使用通常的 PHP 语法，如清单 4-4 所示。相反，应使用 PHP 替代语法编写模板，如清单 4-5 所示，以便非 PHP 程序员也能理解代码。最终代码不仅会正确缩进，还能帮助你将复杂的 PHP 代码保留在动作中，因为只有控制语句（if、foreach、while 等）才有替代语法。

