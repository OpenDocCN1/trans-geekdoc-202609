

## 上下文单例

你之前已经在前端控制器中看到了对 sfContext::createInstance() 的调用。在动作中，getContext() 方法返回同一个单例。这是一个非常有用的对象，它存储了与给定请求相关的所有 symfony 核心对象的引用，并为每个对象提供访问器：

- sfController：控制器对象（->getController()）
- sfRequest：请求对象（->getRequest()）
- sfResponse：响应对象（->getResponse()）
- sfUser：用户会话对象（->getUser()）
- sfRouting：路由对象（->getRouting()）
- sfMailer：邮件对象（->getMailer()）
- sfI18N：国际化对象（->getI18N()）
- sfLogger：日志对象（->getLogger()）
- sfDatabaseConnection：数据库连接（->getDatabaseConnection()）

所有这些核心对象都可以通过任何代码中的 sfContext::getInstance() 单例来使用。然而，这是一种非常糟糕的做法，因为这会创建一些硬依赖，使你的代码非常难以测试、重用和维护。你将在本书中学习如何避免使用 sfContext::getInstance()。

## 动作终止

动作执行结束时可能出现各种行为。动作方法返回的值决定了视图将如何渲染。sfView 类的常量用于指定使用哪个模板来显示动作的结果。

如果有一个默认视图可调用（这是最常见的情况），动作应如下结束：

```
return sfView::SUCCESS;
```

Symfony 将查找名为 actionNameSuccess.php 的模板。这被定义为默认动作行为，因此如果你在动作方法中省略 return 语句，symfony 也会查找 actionNameSuccess.php 模板。空动作也会触发该行为。有关成功动作终止的示例，请参见清单 6-8。

### 清单 6-8 - 将调用 indexSuccess.php 和 listSuccess.php 模板的动作

```
public function executeIndex()
{
    return sfView::SUCCESS;
}

public function executeList()
{
}
```

如果有一个错误视图可调用，动作应如下结束：

```
return sfView::ERROR;
```

Symfony 将查找名为 actionNameError.php 的模板。

要调用自定义视图，请使用以下结尾：

### 清单 6-16

```
return 'MyResult';
```

Symfony 将查找名为 actionNameMyResult.php 的模板。

如果没有视图可调用——例如，在批处理中执行的动作的情况——动作应如下结束：

### 清单 6-17

```
return sfView::NONE;
```

在这种情况下，不会执行任何模板。这意味着你可以完全绕过视图层，直接从动作中设置响应 HTML 代码。如清单 6-9 所示，symfony 为此情况提供了特定的 renderText() 方法。当你需要动作具有极高的响应速度时，这可能很有用，例如 Ajax 交互，这将在第 11 章中讨论。

### 清单 6-9 - 通过回显响应并返回 sfView::NONE 来绕过视图

```
public function executeIndex()
{
    $this->getResponse()->setContent("<html><body>Hello,
    World!</body></html>");
    return sfView::NONE;
}
```

```
// Is equivalent to
public function executeIndex()
{
    return $this->renderText("<html><body>Hello, World!</body></html>");
}
```

在某些情况下，你需要发送一个空响应，但其中包含一些定义的头部（尤其是 X-JSON 头部）。通过下一章讨论的 sfResponse 对象定义头部，并返回 sfView::HEADER_ONLY 常量，如清单 6-10 所示。

### 清单 6-10 - 绕过视图渲染并仅发送头部

```
public function executeRefresh()
{
    $output = '<"title","My basic letter"],["name","Mr Brown">';
    $this->getResponse()->setHttpHeader("X-JSON", '('. $output .')');
    return sfView::HEADER_ONLY;
}
```

如果动作必须由特定模板渲染，请忽略 return 语句，改用 setTemplate() 方法。

### 清单 6-20

```
public function executeIndex()
{
    $this->setTemplate('myCustomTemplate');
}
```

使用此代码，symfony 将查找 myCustomTemplateSuccess.php 文件，而不是 indexSuccess.php。

## 跳转到另一个动作

在某些情况下，动作执行结束于请求新的动作执行。例如，处理 POST 请求中表单提交的动作通常在更新数据库后重定向到另一个动作。

动作类提供两种方法来执行另一个动作：

- 如果动作将调用转发给另一个动作：

```
$this->forward('otherModule', 'index');
```

- 如果动作导致 Web 重定向：

```
$this->redirect('otherModule/index');
$this->redirect('http://www.google.com/');
```

动作中 forward 或 redirect 之后的代码永远不会执行。你可以认为这些调用等同于 return 语句。它们抛出 sfStopException 以停止动作的执行；此异常随后被 symfony 捕获并简单地忽略。

在重定向和转发之间做选择有时很棘手。要选择最佳解决方案，请记住，转发是应用程序内部的，对用户透明。就用户而言，显示的 URL 与请求的 URL 相同。相比之下，重定向是发送给用户浏览器的消息，涉及来自浏览器的新请求，并更改最终生成的 URL。

如果动作是由 method="post" 的提交表单调用，你应该 **始终** 进行重定向。主要优势是，如果用户刷新生成的页面，表单不会被重新提交；此外，后退按钮会按预期工作，显示表单而不是询问用户是否要重新提交 POST 请求的警告。

有一种特殊的转发非常常用。forward404() 方法转发到“页面未找到”动作。当动作执行所需的参数在请求中不存在时（从而检测到错误输入的 URL），通常会调用此方法。清单 6-11 显示了一个期望 id 参数的 show 动作示例。

### 清单 6-11 - forward404() 方法的使用

```
public function executeShow(sfWebRequest $request)
{
// Doctrine
//article =
Doctrine::getTable('Article')->find($request->getParameter('id'));

// Propel
$article = ArticlePeer::retrieveByPK($request->getParameter('id'));

if (!$article)
{
$this->forward404();
}
}
```

如果你要查找错误 404 动作和模板，可以在 $sf_symfony_lib_dir/controller/default/ 目录中找到它们。你可以通过向应用程序添加新的默认模块来自定义此页面，覆盖框架中位于该位置的模块，并在其中定义 error404 动作和 error404Success 模板。或者，你可以在 settings.yml 文件中设置 error_404_module 和 error_404_action 常量以使用现有动作。

经验表明，大多数情况下，动作在测试某些内容后会进行重定向或转发，如清单 6-12 所示。这就是为什么 sfActions 类有一些更多方法，名为 forwardIf()、forwardUnless()、forward404If()、forward404Unless()、redirectIf() 和 redirectUnless()。这些方法只需一个额外参数，表示一个条件，如果测试结果为 true（对于 xxxIf() 方法）或 false（对于 xxxUnless() 方法），则触发执行，如清单 6-12 所示。

### 清单 6-12 - forward404If() 方法的使用

```
// This action is equivalent to the one shown in Listing 6-11
public function executeShow(sfWebRequest $request)
{
  $article =
  Doctrine::getTable('Article')->find($request->getParameter('id'));
  $this->forward404If(!$article);
}
```

```
// So is this one
public function executeShow(sfWebRequest $request)
{
  $article =
  Doctrine::getTable('Article')->find($request->getParameter('id'));
  $this->forward404Unless($article);
}
```

使用这些方法不仅能保持代码简短，还能使其更具可读性。

> 当动作调用 forward404() 或其同类方法时，symfony 会抛出 sfError404Exception 来管理 404 响应。这意味着，如果你需要在不想访问控制器的位置显示 404 消息，可以直接抛出类似异常。

## 模块中多个动作的重复代码

命名动作 executeActionName()（在 sfActions 类的情况下）或 execute()（在 sfAction 类的情况下）的约定保证了 symfony 会找到动作方法。它让你能够添加自己的其他方法，只要它们不以 execute 开头，这些方法就不会被视为动作。

当你需要在每个动作的实际执行之前重复多条语句时，还有另一个有用的约定。你可以将它们提取到动作类的 preExecute() 方法中。你可能已经猜到如何在每个动作执行之后重复语句：将它们封装在 postExecute() 方法中。这些方法的语法在清单 6-13 中显示。

### 清单 6-13 - 在动作类中使用 preExecute()、postExecute() 和自定义方法

```
class mymoduleActions extends sfActions
{
  public function preExecute()
  {
```

