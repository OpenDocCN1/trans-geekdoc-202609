

- 创建应用程序配置和 symfony 上下文。
- 加载并启动核心框架类。
- 加载配置。
- 解码请求 URL 以确定要执行的操作和请求参数。
- 如果操作不存在，则重定向到 404 错误操作。
- 激活过滤器（例如，如果请求需要身份验证）。
- 执行过滤器，第一遍。
- 执行操作并渲染视图。
- 执行过滤器，第二遍。
- 输出响应。

## 默认前置控制器

默认前置控制器名为 index.php，位于项目 web/ 目录下，是一个简单的 PHP 文件，如清单 6-1 所示。

## 清单 6-1 - 默认生产环境前置控制器

```
<?php
require_once(dirname(__FILE__).'/../config/ProjectConfiguration.class.php');

$configuration =
ProjectConfiguration::getApplicationConfiguration('frontend', 'prod',
false);
sfContext::createInstance($configuration)->dispatch();
```

前置控制器创建应用程序配置实例，负责处理步骤 2 至 4。调用 sfController 对象（即 symfony MVC 架构的核心控制器对象）的 dispatch() 方法会分发请求，负责处理步骤 5 至 7。最后的步骤由过滤器链处理，如本章后面所述。

## 调用另一前置控制器以切换环境

每个环境都有一个前置控制器。事实上，正是前置控制器的存在定义了环境。环境由你传递给 ProjectConfiguration::getApplicationConfiguration() 方法调用的第二个参数定义。

要更改浏览应用程序所在的环境，只需选择另一个前置控制器。使用 generate:app 任务创建新应用程序时可用的默认前置控制器有：生产环境的 index.php 和开发环境的 frontend_dev.php（前提是你的应用名为 frontend）。默认的 mod_rewrite 配置会在 URL 不包含前置控制器脚本名称时使用 index.php。因此，以下两个 URL 在生产环境下显示相同页面（mymodule/index）：

```
http://localhost/index.php/mymodule/index
http://localhost/mymodule/index
```

而此 URL 在开发环境下显示相同页面：

```
http://localhost/frontend_dev.php/mymodule/index
```

创建新环境与创建新前置控制器一样简单。例如，你可能需要一个预发布环境，以便客户在上线前测试应用程序。要创建此预发布环境，只需将 web/frontend_dev.php 复制到 web/frontend_staging.php，并将 ProjectConfiguration::getApplicationConfiguration() 调用的第二个参数值更改为 staging。现在，在所有配置文件中，你可以添加一个新的 staging: 部分来为此环境设置特定值，如清单 6-2 所示。

## 清单 6-2 - 适用于预发布环境的示例 app.yml，包含特定设置

```
staging:
  mail:
    webmaster: dummy@mysite.com
    contact: dummy@mysite.com
  all:
    mail:
      webmaster: webmaster@mysite.com
      contact: contact@mysite.com
```

如果你想查看应用程序在此新环境下的表现，请调用相关前置控制器：

```
http://localhost/frontend_staging.php/mymodule/index
```

## 操作

操作是应用程序的核心，因为它们包含应用程序的所有逻辑。它们调用模型并为视图定义变量。当你在 symfony 应用程序中发出 Web 请求时，URL 定义了操作和请求参数。

## 操作类

操作是名为 moduleNameActions、继承自 sfActions 类且按模块分组的类中的 executeActionName 方法。模块的操作类存储在模块 actions/ 目录中的 actions.class.php 文件中。

## 清单 6-3 - 示例操作类，位于 apps/frontend/modules/mymodule/actions/actions.class.php

```
class mymoduleActions extends sfActions
{
  public function executeIndex($request)
  {
    // ...
  }
}
```

> 尽管 PHP 中的方法名不区分大小写，但在 symfony 中区分大小写。因此请记住，操作方法必须以小写 execute 开头，后跟首字母大写的精确操作名称。

要请求一个操作，需要以模块名和操作名为参数调用前置控制器脚本。默认情况下，通过将 module_name/action_name 对追加到脚本来实现。这意味着清单 6-4 中定义的操作可通过以下 URL 调用：

http://localhost/index.php/mymodule/index

添加更多操作只需向 sfActions 对象添加更多 execute 方法，如清单 6-4 所示。

## 清单 6-4 - 包含两个操作的操作类，位于 frontend/modules/mymodule/actions/actions.class.php

```
class mymoduleActions extends sfActions
{
    public function executeIndex($request)
    {
        // ...
    }

    public function executeList($request)
    {
        // ...
    }
}
```

如果操作类规模过大，你可能需要进行一些重构，并将部分代码移至模型层。操作通常应保持简短（不超过几行），所有业务逻辑通常应位于模型中。

不过，模块中的操作数量可能足够多，以至于你需要将其拆分为两个模块。

## Symfony 编码规范

在本书给出的代码示例中，你可能已经注意到，左花括号和右花括号（{ 和 }）各自占用一行。这一规范使代码更易于阅读。

在框架的其他编码规范中，缩进始终使用两个空格；不使用制表符。这是因为制表符根据所使用的文本编辑器具有不同的空格值，而且混合使用制表符和空格缩进的代码无法阅读。

核心和生成的 symfony PHP 文件不以通常的 ?> 结束标签结尾。这是因为它并非真正需要，而且如果此标签后有空格，可能会在输出中造成问题。

如果你真的留意，会发现 symfony 中的行永远不会以空格结尾。这次的原因更为平凡：以空格结尾的行在 Fabien 的文本编辑器中看起来很难看。

## 替代操作类语法

提供了一种替代操作语法，用于将操作分发到单独的文件中，每个操作一个文件。在这种情况下，每个操作类扩展 sfAction（而不是 sfActions）并命名为 actionNameAction。实际的操作方法简单地命名为 execute。文件名与类名相同。这意味着清单 6-4 的等效代码可以使用清单 6-5 和 6-6 中显示的两个文件来编写。

## 清单 6-5 - 单个操作文件，位于 frontend/modules/mymodule/actions/indexAction.class.php

```
class indexAction extends sfAction
{
  public function execute($request)
  {
    // ...
  }
}
```

## 清单 6-6 - 单个操作文件，位于 frontend/modules/mymodule/actions/listAction.class.php

```
class listAction extends sfAction
{
  public function execute($request)
  {
    // ...
  }
}
```

## 在操作中检索信息

操作类提供了一种访问控制器相关信息和核心 symfony 对象的方式。清单 6-7 演示了如何使用它们。

## 清单 6-7 - sfActions 常用方法

```
class mymoduleActions extends sfActions
{
  public function executeIndex(sfWebRequest $request)
  {
    // Retrieving request parameters
    $password = $request->getParameter('password');

    // Retrieving controller information
    $moduleName = $this->getModuleName();
    $actionName = $this->getActionName();

    // Retrieving framework core objects
    $userSession = $this->getUser();
    $response = $this->getResponse();
    $controller = $this->getController();
    $context = $this->getContext();

    // Setting action variables to pass information to the template
    $this->setVar('foo', 'bar');
    $this->foo = 'bar';         // Shorter version
  }
}
