
## 视图元素

视图层也可以从代码分离中获益。一个网页在整个应用程序中通常包含一致的元素：页面标题、图形布局、页脚和全局导航。只有页面的内部部分会发生变化。这就是为什么视图被分为布局和模板。布局通常对整个应用程序或一组页面是全局的。模板只是将控制器提供的变量成形。需要一些逻辑来使这些组件协同工作，这个视图逻辑层将保留“视图”名称。根据这些原则，清单 2-3 中的视图部分可以分为三部分，如清单 2-8、2-9 和 2-10 所示。

```
Listing 2-8 - The Template Part of the View, in mytemplate.php

<h1>List of Posts</h1>
<table>
<tr><th>Date</th><th>Title</th></tr>
<?php foreach ($posts as $post): ?>
    <tr>
    <td><?php echo $post['date'] ?></td>
    <td><?php echo $post['title'] ?></td>
    </tr>
<?php endforeach; ?>
</table>
```

```
Listing 2-9 - The View Logic Part of the View

<?php
$title = 'List of Posts';
$posts = getAllPosts();
```

```
Listing 2-10 - The Layout Part of the View

<html>
<head>
<title><?php echo $title ?></title>
</head>
<body>
<?php include('mytemplate.php'); ?>
</body>
</html>
```

## 动作和前端控制器

在之前的示例中，控制器不做太多工作，但在真实的 Web 应用程序中，控制器有大量工作要做。这项工作的重要部分对应用程序中的所有控制器都是共通的。共通任务包括请求处理、安全处理、加载应用程序配置以及类似的例行工作。这就是为什么控制器通常被分为一个对整个应用程序唯一的前端控制器，以及仅包含特定于单个页面的控制器代码的动作。

前端控制器的一大优势是，它为整个应用程序提供了唯一的入口点。如果你决定关闭对应用程序的访问，只需编辑前端控制器脚本即可。在没有前端控制器的应用程序中，每个单独的控制器都需要被禁用。

## 面向对象

之前的所有示例都使用过程式编程。现代语言的面向对象能力使编程变得更加容易，因为对象可以封装逻辑、相互继承，并提供整洁的命名约定。

在非面向对象语言中实现 MVC 架构会引起命名空间和代码重复问题，且整体代码难以阅读。

面向对象让开发者能够处理视图对象、控制器对象和模型类等内容，并将之前示例中的所有函数转换为方法。对于 MVC 架构而言，这是必不可少的。

> 如果你想深入了解在面向对象环境中 Web 应用程序的设计模式，请阅读马丁·福勒（Martin Fowler）的《企业应用架构模式》（Patterns of Enterprise Application Architecture，Addison-Wesley，ISBN: 0-32112-742-0）。福勒书中的代码示例使用 Java 或 C# 编写，但 PHP 开发者仍然可以轻松阅读。

## Symfony 的 MVC 实现

稍等一下。对于单个页面列出博客文章，需要多少个组件？如图 2-2 所示，我们有以下部分：

- 模型层
  - 数据库抽象
  - 数据访问
- 视图层
  - 视图
  - 模板
  - 布局
- 控制器层
  - 前端控制器
  - 动作

七个脚本——每次创建新页面都要打开和修改如此多的文件！不过，symfony 让事情变得简单。在吸收 MVC 架构精华的同时，symfony 以一种使应用程序开发快速且无痛苦的方式实现了它。

首先，前端控制器和布局对应用程序中的所有动作都是共通的。你可以有多个控制器和布局，但每种只需要一个。前端控制器是纯粹的 MVC 逻辑组件，你永远不需要编写任何前端控制器，因为 symfony 会为你生成它。

另一个好消息是，模型层的类也会根据你的数据结构自动生成。这是 ORM 库的工作，它提供类骨架和代码生成。如果 ORM 发现外键约束或日期字段，它将提供特殊的访问器和修改器方法，使数据操作变得轻而易举。而且，数据库抽象对你来说完全不可见，因为它由 PHP Data Objects 原生处理。因此，如果你决定随时更换数据库引擎，你无需重构任何代码。你只需要更改一个配置参数。

最后，视图逻辑可以轻松地转换为一个简单的配置文件，无需编程。

图 2-2 - Symfony 工作流

![](img/0f886a7f4cbcc3939be96e985ca35ff4_26_0.png)

这意味着，我们示例中描述的文章列表在 symfony 中只需要三个文件即可工作，如清单 2-11、2-12 和 2-13 所示。

```
Listing 2-11 - list Action, in myproject/apps/myapp/modules/weblog/actions/actions.class.php

```php
<?php

class weblogActions extends sfActions
{
    public function executeList()
    {
        $this->posts = PostPeer::doSelect(new Criteria());
    }
}
```
```

```
Listing 2-12 - list Template, in myproject/apps/myapp/modules/weblog/templates/listSuccess.php

```php
<?php slot('title', 'List of Posts') ?>

<h1>List of Posts</h1>
<table>
<tr><th>Date</th><th>Title</th></tr>
<?php foreach ($posts as $post): ?>
<tr>
<td><?php echo $post->getDate() ?></td>
<td><?php echo $post->getTitle() ?></td>
</tr>
<?php endforeach; ?>
</table>
```
```

此外，你仍然需要定义一个布局，如清单 2-13 所示，但它将被多次重用。

清单 2-13 - 布局，位于 myproject/apps/myapp/templates/layout.php

```
<html>
<head>
<title><?php include_slot('title') ?></title>
</head>
<body>
<?php echo $sf_content ?>
</body>
</html>
```

这真的是你所需要的全部。这是显示与之前清单 2-1 中所示平面脚本完全相同页面所需的精确代码。其余部分（使所有组件协同工作）由 symfony 处理。如果你数一下行数，你会发现，使用 symfony 在 MVC 架构中创建文章列表所需的时间和编码量，与编写平面文件并无不同。尽管如此，它为你带来巨大的优势，尤其是代码组织清晰、可重用性、灵活性，以及更多乐趣。作为额外福利，你还拥有 XHTML 合规性、调试能力、易配置、数据库抽象、智能 URL 路由、多环境以及更多开发工具。

## Symfony 核心类

symfony 的 MVC 实现使用了几个你在这本书中会经常遇到的类：

- sfController 是控制器类。它解码请求并将其交给动作。
- sfRequest 存储所有请求元素（参数、cookie、标头等）。
- sfResponse 包含响应标头和内容。这是最终将被转换为 HTML 响应并发送给用户的对象。
- 上下文（通过 sfContext::getInstance() 获取）存储对所有核心对象和当前配置的引用；它可从任何位置访问。

你将在第 6 章了解更多关于这些对象的内容。

正如你所见，所有 symfony 类都使用 sf 前缀，模板中的 symfony 核心变量也是如此。这应当避免与你自己的类和变量发生名称冲突，并使核心框架类易于识别。

> 在 symfony 使用的编码规范中，UpperCamelCase 是类和变量命名的标准。存在两个例外：核心 symfony 类以 sf 开头，该前缀为小写；模板中的变量使用下划线分隔语法。
