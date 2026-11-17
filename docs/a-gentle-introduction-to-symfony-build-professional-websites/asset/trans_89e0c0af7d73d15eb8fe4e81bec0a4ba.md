

> 在测试期间（在开发环境中），如果您想检查浏览器中给定请求匹配了哪条规则，请展开 Web 调试工具栏的“日志”部分，并查找指定“matched route XXX”的一行。有关 Web 调试模式的更多信息，请参见第 16 章。

## 在不使用 routing.yml 的情况下创建规则

与大多数配置文件一样，routing.yml 是定义路由规则的一种解决方案，但不是唯一的解决方案。您可以在 PHP 中定义规则，但在调用 dispatch() 之前，因为该方法根据当前路由规则确定要执行的操作。在 PHP 中定义规则授权您创建动态规则，具体取决于配置或其他参数。

处理路由规则的对象是 sfPatternRouting 工厂。它可以通过 sfContext::getInstance()->getRouting() 在代码的每个部分中使用。其 prependRoute() 方法在 routing.yml 中定义的现有规则之上添加一条新规则。它期望两个参数：路由名称和一个 sfRoute 对象。例如，清单 9-18 中显示的 routing.yml 规则定义与清单 9-22 中显示的 PHP 代码等效。

### 清单 9-22 - 在 PHP 中定义规则

```php
sfContext::getInstance()->getRouting()->prependRoute(
 'article_by_id',          // Route name
 new sfRoute('/article/:id', array('module' => 'article', 'action' =>
 'read'), array('id' => '\d+')),   // Route object
);
```

sfRoute 类构造函数接受三个参数：一个模式、一个关联数组形式的默认值，以及另一个用于要求的关联数组。

sfPatternRouting 类还有其他用于手动处理路由的有用方法：clearRoutes()、hasRoutes() 等等。有关更多信息，请参阅 API 文档 39。

> 一旦您开始完全理解本书中介绍的概念，您就可以通过浏览在线 API 文档或，更好的，symfony 源代码来加深对框架的理解。本书无法描述 symfony 的所有调整和参数。然而，在线文档是无限的。

> 路由类可以在 factories.yml 配置文件中进行配置（要更改默认路由类，请参见第 17 章）。本章介绍的是 sfPatternRouting 类，它是默认配置的路由类。

## 在操作中处理路由

如果您需要检索有关当前路由的信息——例如，为将来的“back to page xxx”链接做准备——应该使用 sfPatternRouting 对象的方法。getCurrentInternalUri() 方法返回的 URI 可以用于 link_to() 辅助函数的调用，如清单 9-23 所示。

### 清单 9-23 - 使用 sfRouting 获取有关当前路由的信息

```php
// If you require a URL like
http://myapp.example.com/article/21

$routing = $this->getContext()->getRouting();

// Use the following in article/read action
$uri = $routing->getCurrentInternalUri();
=> article/read?id=21

$uri = $routing->getCurrentInternalUri(true);
=> @article_by_id?id=21

$rule = $routing->getCurrentRouteName();
=> article_by_id

// If you just need the current module/action names,
// remember that they are actual request parameters
$module = $request->getParameter('module');
$action = $request->getParameter('action');
```

如果您需要在操作中将内部 URI 转换为外部 URL——就像模板中的 url_for() 所做的那样——请使用 sfController 对象的 genUrl() 方法，如清单 9-24 所示。

### 清单 9-24 - 使用 sfController 转换内部 URI

```php
$uri = 'article/read?id=21';

$url = $this->getController()->genUrl($uri);
=> /article/21

$url = $this->getController()->genUrl($uri, true);
=> http://myapp.example.com/article/21
```

## 总结

路由是一种双向机制，旨在允许格式化外部 URL，使其更加用户友好。URL 重写是必需的，以便在每个项目的一个应用程序的 URL 中省略前置控制器名称。如果您希望路由系统双向工作，则每次需要在模板中输出 URL 时都必须使用链接辅助函数。routing.yml 文件配置路由系统的规则，并使用优先级顺序和规则要求。settings.yml 文件包含有关外部 URL 中前置控制器名称存在情况以及可能后缀的其他设置。

## 第 10 章 表单

处理表单输入的显示、表单提交的验证以及表单的所有特殊情况是 Web 开发中最复杂的任务之一。幸运的是，symfony 为一个非常强大的表单子框架提供了简单的接口，并帮助您在几行代码内设计和处理任何复杂程度的表单。

## 显示表单

一个包含姓名、电子邮件、主题和消息字段的简单联系表单通常呈现如下：

| 姓名 | |
|---|---|
| 电子邮件 | |
| 主题 | 主题 A ▼ |
| | 主题 A |
| | 主题 B |
| | 主题 C |
| 消息 | |
| | 提交查询 |

在 symfony 中，表单是在操作中定义并传递给模板的一个对象。要显示表单，必须首先定义它包含的字段 - symfony 使用术语“widget”。最简单的方法是在操作方法中创建一个新的 sfForm 对象。

```php
// in modules/foo/actions/actions.class.php
public function executeContact($request)
{
$this->form = new sfForm();
$this->form->setWidgets(array(
'name' => new sfWidgetFormInputText(),
'email' => new sfWidgetFormInputText(array('default' =>
'me@example.com')),
'subject' => new sfWidgetFormChoice(array('choices' => array('Subject
A', 'Subject B', 'Subject C'))),
'message' => new sfWidgetFormTextarea(),
)));
}
```

sfForm::setWidgets() 期望一个 widget 名称/对象的关联数组。sfWidgetFormInputText、sfWidgetFormChoice 和 sfWidgetFormTextarea 是 symfony 提供的众多 widget 类中的一些；您将在本章后面找到完整列表。

上一个示例显示了您可以使用的两个 widget 选项：default 设置 widget 值，适用于所有 widget。choices 是 choice widget 特有的选项（它呈现为下拉列表）：它定义用户可选择的可用选项。

因此，foo/contact 操作定义了一个表单对象，然后通过 $form 变量将其传递给 contactSuccess 模板。模板可以使用此对象在 HTML 中呈现表单的各个部分。最简单的方法是调用 echo $form，这将呈现带有标签的所有字段作为表单控件。您也可以使用表单对象生成表单标签：

### 清单 10-2

```php
// in modules/foo/templates/contactSuccess.php
<?php echo $form->renderFormTag('foo/contact') ?>
<table>
<?php echo $form ?>
<tr>
<td colspan="2">
<input type="submit" />
</td>
</tr>
</table>
</form>
```

使用传递给 setWidgets() 的参数，symfony 拥有足够的信息来正确显示表单。生成的 HTML 与上面的屏幕截图完全相同，其底层代码如下：

### 清单 10-3

```html
<form action="/frontend_dev.php/foo/contact" method="POST">
<table>
<tr>
<th><label for="name">Name</label></th>
<td><input type="text" name="name" id="name" /></td>
</tr>
<tr>
<th><label for="email">Email</label></th>
<td><input type="text" name="email" id="email"
value="me@example.com" /></td>
</tr>
<tr>
<th><label for="subject">Subject</label></th>
<td>
<select name="subject" id="subject">
<option value="0">Subject A</option>
<option value="1">Subject B</option>
<option value="2">Subject C</option>
</select>
</td>
</tr>
<tr>
<th><label for="message">Message</label></th>
<td><textarea rows="4" cols="30" name="message"
id="message"></textarea></td>
</tr>
<tr>
<td colspan="2">
<input type="submit" />
</td>
</tr>
</table>
</form>
```

每个 widget 都会生成一个包含 `<label>` 标签和表单输入标签的表格行。Symfony 通过将 widget 名称大写来推断标签名称（`subject` widget 名称生成“Subject”标签）。至于输入标签，它取决于 widget 类型。Symfony 根据每个 widget 的名称添加一个 `id` 属性。最后，表单的呈现始终符合 XHTML 标准。

## 自定义表单显示

使用 echo $form 对于原型开发非常好，但您可能希望完全控制生成的 HTML 代码。表单对象包含一个字段数组，调用 echo $form 实际上会遍历字段并逐个呈现它们。要获得更多控制权，您可以手动遍历字段，并在每个字段上调用 renderRow()。下一个清单生成与之前完全相同的 HTML 代码，但模板会逐个输出每个字段：

```php
// in modules/foo/templates/contactSuccess.php
<?php echo $form->renderFormTag('foo/contact') ?>
<table>
<?php echo $form['name']->renderRow() ?>
<?php echo $form['email']->renderRow() ?>
<?php echo $form['subject']->renderRow() ?>
<?php echo $form['message']->renderRow() ?>
<tr>
<td colspan="2">
<input type="submit" />
</td>
</tr>
</table>
</form>
```

逐个呈现字段允许您更改显示顺序，还可以自定义其外观。`renderRow()` 将 HTML 属性列表作为第一个参数，因此您可以定义自定义类、`id` 或 JavaScript 事件处理程序。`renderRow()` 的第二个参数是一个可选标签，用于覆盖从 widget 名称推断的标签。以下是联系表单的自定义示例：

```php
// in modules/foo/templates/contactSuccess.php
<?php echo $form->renderFormTag('foo/contact') ?>
<table>
<?php echo $form['name']->renderRow(array('size' => 25, 'class' =>
'foo'), 'Your Name') ?>
<?php echo $form['email']->renderRow(array('onclick' => 'this.value =
```

