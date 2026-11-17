
如果需要声明多个助手组，请向 use_helper() 调用添加更多参数。例如，要在模板中加载 Text 和 Javascript 助手组，请调用 `<?php use_helper('Text', 'Javascript') ?>`。

每个模板中默认提供少量助手，无需声明。这些是以下助手组的助手：

- Helper：用于助手包含（实际上，use_helper() 函数本身就是一个助手）
- Tag：基本标签助手，几乎所有助手都使用它
- Url：链接和 URL 管理助手
- Asset：填充 HTML <head> 部分的助手，并提供指向外部资源（图片、JavaScript 和样式表文件）的便捷链接
- Partial：允许包含模板片段的助手
- Cache：缓存代码片段的操作助手

每个模板默认加载的标准助手列表可在 settings.yml 文件中配置。因此，如果你知道不会使用 Cache 组的助手，或者将始终使用 Text 组的助手，请相应地修改 standard_helpers 设置。这将稍微加快你的应用程序速度。你不能删除前面列表中的前四个助手组（Helper、Tag、Url 和 Asset），因为模板引擎正常工作需要它们。因此，它们甚至不出现在标准助手列表中。

如果需要在模板之外使用助手，你仍然可以通过调用 sfProjectConfiguration::getActive()->loadHelpers($helpers) 从任何位置加载助手组，其中 $helpers 是助手组名称或助手组名称数组。例如，如果你想在动作中使用 auto_link_text()，则需要先调用 sfProjectConfiguration::getActive()->loadHelpers('Text')。

## 常用助手

你将在后续章节中详细了解一些助手，与它们所辅助的功能相关。清单 7-4 简要列出了使用频率最高的默认助手，以及它们返回的 HTML 代码。

## 清单 7-4 - 常用默认助手

```
// Helper group
<?php use_helper('HelperName') ?>
<?php use_helper('HelperName1', 'HelperName2', 'HelperName3') ?>

// Url group
<?php echo link_to('click me', 'mymodule/myaction') ?>
=> <a href="/route/to/myaction">click me</a> // Depends on the routing settings

// Asset group
<?php echo image_tag('myimage', 'alt=foo size=200x100') ?>
=> <img src="http://www.symfony-project.org/images/myimage.png" alt="foo" width="200" height="100" />
<?php echo javascript_include_tag('myscript') ?>
=> <script language="JavaScript" type="text/javascript" src="http://www.symfony-project.org/js/myscript.js"></script>
<?php echo stylesheet_tag('style') ?>
=> <link href="/stylesheets/style.css" media="screen" rel="stylesheet" type="text/css" />
```

symfony 中还有许多其他助手，要详细描述所有助手需要一整本书。助手的最佳参考是在线 [API 文档](http://www.symfony-project.org/api/1_4/)，其中所有助手都有详细文档，包括语法、选项和示例。

## 添加你自己的助手

Symfony 自带了许多用于各种目的的助手，但如果你在 API 文档中找不到所需内容，可能会想要创建一个新助手。这非常容易实现。

助手函数（返回 HTML 代码的常规 PHP 函数）应保存为名为 FooBarHelper.php 的文件，其中 FooBar 是助手组的名称。将文件存储在 apps/frontend/lib/helper/ 目录中（或存储在项目中任意 lib/ 文件夹下的 helper/ 目录中），以便 use_helper('FooBar') 助手可以自动找到它并包含。

> 此系统甚至允许你覆盖现有的 symfony 助手。例如，要重新定义 Text 助手组的所有助手，只需在 apps/frontend/lib/helper/ 目录中创建一个 TextHelper.php 文件。每当你调用 use_helper('Text') 时，symfony 将使用你的助手组而非其自身的助手组。但请注意：由于原始文件甚至不会被加载，你必须重新定义助手组的所有函数才能覆盖它；否则，某些原始助手将完全不可用。

## 页面布局

清单 7-1 所示的模板不是有效的 XHTML 文档。缺少 DOCTYPE 定义以及 <html> 和 <body> 标签。这是因为它们存储在应用程序的其他位置，即名为 layout.php 的文件中，该文件包含页面布局。该文件也称为全局模板，存储了应用程序所有页面共有的 HTML 代码，以避免在每个模板中重复编写。模板的内容集成到布局中，或者，如果你改变视角，布局“装饰”模板。这是装饰器设计模式的应用，如图 7-1 所示。

> 有关装饰器和其他设计模式的更多信息，请参阅 Martin Fowler 编著的《企业应用架构模式》（Addison-Wesley 出版，ISBN: 0-32112-742-0）。

## 图 7-1 - 使用布局装饰模板

![](img/0f886a7f4cbcc3939be96e985ca35ff4_100_0.png)

清单 7-5 显示了默认页面布局，位于应用程序 templates/ 目录中。

## 清单 7-5 - 默认布局，位于 myproject/apps/frontend/templates/layout.php

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <?php include_javascripts() ?>
  <?php include_stylesheets() ?>
  <?php include_http_metas() ?>
  <?php include_metas() ?>
  <?php include_title() ?>
  <link rel="shortcut icon" href="/favicon.ico" />
</head>
<body>
  <?php echo $sf_content ?>
</body>
</html>
```

在 <head> 部分中调用的助手会从响应对象和视图配置中获取信息。<body> 标签输出模板的结果。使用此布局、默认配置以及清单 7-1 中的示例模板，处理后的视图如清单 7-6 所示。

## 清单 7-6 - 布局、视图配置和模板的组合

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <meta http-equiv="content-type" content="text/html; charset=utf-8" />
  <meta name="title" content="symfony project" />
  <meta name="robots" content="index, follow" />
  <meta name="description" content="symfony project" />
  <meta name="keywords" content="symfony, project" />
  <title>symfony project</title>
  <link rel="stylesheet" type="text/css" href="/css/main.css" />
  <link rel="shortcut icon" href="/favicon.ico">
</head>
<body>
  <h1>Welcome</h1>
  <p>Welcome back, <?php echo $name ?>!</p>
  <h2>What would you like to do?</h2>
  <ul>
    <li><?php echo link_to('Read the last articles', 'article/read') ?>
    </li>
    <li><?php echo link_to('Start writing a new one', 'article/write') ?>
    </li>
  </ul>
</body>
</html>
```

全局模板可以针对每个应用程序完全自定义。添加所需的任何 HTML 代码。此布局通常用于保存站点导航、徽标等。你甚至可以拥有多个布局，并决定每个动作应使用哪个布局。暂时不要担心 JavaScript 和样式表包含；本章稍后的“视图配置”部分将介绍如何处理。

## 模板快捷方式

在模板中，始终可用一些 symfony 变量。这些快捷方式通过核心 symfony 对象，提供对模板中最常用信息的访问：

- $sf_context：整个上下文对象（sfContext 的实例）
- $sf_request：请求对象（sfRequest 的实例）
- $sf_params：请求对象的参数
- $sf_user：当前用户会话对象（sfUser 的实例）

上一章详细介绍了 sfRequest 和 sfUser 对象的有用方法。你可以实际上在模板中通过 $sf_request 和 $sf_user 变量调用这些方法。例如，如果请求包含 total 参数，其值可在模板中通过以下方式获取：

```
// Long version
<?php echo $sf_request->getParameter('total') ?>

// Shorter version
<?php echo $sf_params->get('total') ?>

// Equivalent to the following action code
echo $request->getParameter('total')
```

## 代码片段

你可能经常需要在多个页面中包含一些 HTML 或 PHP 代码。为了避免重复代码，大多数时候 PHP include() 语句就足够了。

例如，如果应用程序的许多模板需要使用相同的代码片段，请将其保存为名为 myFragment.php 的文件，放在全局模板目录（myproject/apps/frontend/templates/）中，并在模板中按如下方式包含：

```
<?php include(sfConfig::get('sf_app_template_dir').'/myFragment.php') ?>
```

但这不是打包片段的非常干净的方法，主要原因是片段与包含它的各种模板之间可能有不同的变量名。此外，symfony 缓存系统（第 12 章中描述）无法检测 include，因此片段无法独立于模板进行缓存。Symfony 提供了三种替代的智能代码片段类型来替换 include：

- 如果逻辑较轻量，你只需包含一个可访问你传递给它的某些数据的模板文件。为此，你将使用 partial。
- 如果逻辑较重（例如，如果你需要访问数据模型和/或根据会话修改内容），你将更倾向于将展示与逻辑分开。为此，你将使用 component。
- 如果片段旨在替换布局的特定部分，而该部分可能已有默认内容，你将使用 slot。

这些片段的包含由 Partial 组的助手实现。这些助手可从任何 symfony 模板使用，无需初始声明。

## Partials

Partial 是可重复使用的模板代码块。例如，在出版应用程序中，显示文章的模板代码用于文章详细信息页面，也用于文章列表中。
