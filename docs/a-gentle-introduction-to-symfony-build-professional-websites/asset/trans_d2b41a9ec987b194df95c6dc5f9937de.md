
要启动功能测试，请使用 symfony 命令行中的 test:functional 任务，如清单 15-12 所示。此任务需要应用程序名称和测试名称（省略 Test.php 后缀）。

## 清单 15-12 - 从命令行启动单个功能测试

```
Listing 15-13
$ php symfony test:functional frontend foobarActions

# get /comment/index
ok 1 - status code is 200
ok 2 - request parameter module is foobar
ok 3 - request parameter action is index
not ok 4 - response selector body does not match regex /This is a temporary page/
# Looks like you failed 1 tests of 4.
1..4
```

新模块生成的功能测试默认不会通过。这是因为在新建模块中，index 动作会转发到恭喜页面（包含在 symfony 默认模块中），该页面包含句子“This is a temporary page”。只要你不修改 index 动作，该模块的测试就会失败，这保证了你无法使用未完成的模块通过所有测试。

> 在功能测试中，自动加载已激活，因此你无需手动包含文件。

## 使用 sfBrowser 对象进行浏览

浏览器能够发出 GET 和 POST 请求。在这两种情况下，都使用真实 URI 作为参数。清单 15-13 演示了如何编写对 sfBrowser 对象的调用以模拟请求。

## 清单 15-13 - 使用 sfBrowser 对象模拟请求

```
Listing 15-14
include dirname(__FILE__).'/../../bootstrap/functional.php';

// Create a new browser
$b = new sfBrowser();

$b->get('/foobar/show/id/1');       // GET request
$b->post('/foobar/show', array('id' => 1));  // POST request

// The get() and post() methods are shortcuts to the call() method
$b->call('/foobar/show/id/1', 'get');
$b->call('/foobar/show', 'post', array('id' => 1));

// The call() method can simulate requests with any method
$b->call('/foobar/show/id/1', 'head');
$b->call('/foobar/add/id/1', 'put');
$b->call('/foobar/delete/id/1', 'delete');
```

典型的浏览会话不仅包含对特定动作的请求，还包含点击链接和浏览器按钮。如清单 15-14 所示，sfBrowser 对象也能模拟这些操作。

## 清单 15-14 - 使用 sfBrowser 对象模拟导航

```
$b->get('/'); // Request to the home page
$b->get('/foobar/show/id/1');
$b->back(); // Back to one page in history
$b->forward(); // Forward one page in history
$b->reload(); // Reload current page
$b->click('go'); // Look for a 'go' link or button and click
```

浏览器维护一个调用栈，因此 back() 和 forward() 方法的工作方式与真实浏览器相同。

> 浏览器拥有管理会话（sfTestStorage）和 Cookie 的自身机制。

在最需要测试的交互中，与表单相关的交互可能排在第一位。要模拟表单输入和提交，你有三种选择。你可以发送希望发送的参数的 POST 请求，以数组形式作为参数调用 click()，或者逐个填写字段并点击提交按钮。无论如何，它们都会生成相同的 POST 请求。清单 15-15 展示了一个示例。

## 清单 15-15 - 使用 sfBrowser 对象模拟表单输入

```
// Example template in modules/foobar/templates/editSuccess.php
<?php echo form_tag('foobar/update') ?>
<input type="hidden" name="id" value="<?php echo $sf_params->get('id')
?>" />
<input type="text" name="name" value="foo" />
<input type="submit" value="go" />
<textarea name="text1">foo</textarea>
<textarea name="text2">bar</textarea>
</form>
```

```
// Example functional test for this form
$b = new sfBrowser();
$b->get('/foobar/edit/id/1');

// Option 1: POST request
$b->post('/foobar/update', array('id' => 1, 'name' => 'dummy', 'commit' => 'go'));

// Option 2: Click the submit button with parameters
$b->click('go', array('name' => 'dummy'));

// Option 3: Enter the form values field by field name then click the
submit button
$b->setField('name', 'dummy')->
click('go');
```

> 使用第二种和第三种选项时，默认表单值会自动包含在表单提交中，且无需指定表单目标。

当动作通过 redirect() 结束时，浏览器不会自动跟随重定向；你必须使用 followRedirect() 手动跟随，如清单 15-16 所示。

## 清单 15-16 - 浏览器不会自动跟随重定向

```php
// Example action in modules/foobar/actions/actions.class.php
public function executeUpdate($request)
{
  // ...

  $this->redirect('foobar/show?id='. $request->getParameter('id'));
}
```

```php
// Example functional test for this action
$b = new sfBrowser();
$b->get('/foobar/edit?id=1')->
  click('go', array('name' => 'dummy'))->
  followRedirect();   // Manually follow the redirection
```

还有最后一个你应该了解的用于浏览的方法：restart() 重新初始化浏览历史、会话和 Cookie——就像你重新启动了浏览器一样。

在发出第一个请求后，sfBrowser 对象可以访问请求、上下文和响应对象。这意味着你可以检查很多内容，从文本内容到响应头、请求参数和配置：

```php
$request = $b->getRequest();
$context = $b->getContext();
$response = $b->getResponse();
```

## 使用断言

由于 sfBrowser 对象可以访问响应和请求的其他组件，你可以对这些组件进行测试。你可以为此创建一个新的 lime_test 对象，但幸运的是 sfTestFunctional 提供了一个 test() 方法，它返回一个 lime_test 对象，你可以在其中调用之前描述的单元断言方法。查看清单 15-17 了解如何通过 sfTestFunctional 进行断言。

*清单 15-17 - 测试浏览器通过 test() 方法提供测试功能*

```php
$b = new sfTestFunctional(new sfBrowser());
$b->get('/foobar/edit/id/1');
$request = $b->getRequest();
$context = $b->getContext();
$response = $b->getResponse();
```

```php
// Get access to the lime_test methods via the test() method
$b->test()->is($request->getParameter('id'), 1);
$b->test()->is($response->getStatusCode(), 200);
$b->test()->is($response->getHttpHeader('content-type'), 'text/html; charset=utf-8');
$b->test()->like($response->getContent(), '/edit/');
```

> > getResponse()、getContext()、getRequest() 和 test() 方法不返回 sfBrowser 对象，因此你不能在它们之后链式调用其他 sfBrowser 方法。

你可以通过请求和响应对象轻松检查传入和传出的 Cookie，如清单 15-16 所示。

*清单 15-16 - 使用 sfBrowser 测试 Cookie*

```
$b->test()->is($request->getCookie('foo'), 'bar'); // Incoming cookie
$cookies = $response->getCookies();
$b->test()->is($cookies['foo'], 'foo=bar'); // Outgoing cookie
```

使用 test() 方法测试请求元素会导致代码行很长。幸运的是，sfTestFunctional 包含一组代理方法，帮助你保持功能测试的可读性和简洁性——此外，它们本身也会返回一个 sfTestFunctional 对象。

例如，你可以以更快速的方式重写清单 15-15，如清单 15-18 所示。

## 清单 15-18 - 直接使用 sfTestFunctional 进行测试

```
$b = new sfTestFunctional(new sfBrowser());
$b->get('/foobar/edit/id/1')->
with('request')->isParameter('id', 1)->
with('response')->begin()->
isStatusCode()->
isHeader('content-type', 'text/html; charset=utf-8')->
matches('/edit/')->
end();
```

每个代理方法都属于一个测试组。使用测试组需要用 with() 和 end() 方法包裹方法调用。with() 方法接受测试组名称（如 request 和 response）。

状态 200 是 isStatusCode() 期望的参数的默认值，因此你可以不带任何参数调用它来测试成功响应。

代理方法的另一个优势是，你不需要像使用 lime_test 方法那样指定输出文本。消息由代理方法自动生成，测试输出清晰易读。

```
# get /foobar/edit/id/1
ok 1 - request parameter "id" is "1"
ok 2 - status code is "200"
ok 3 - response header "content-type" is "text/html"
ok 4 - response matches "/edit/"
1..4
```

在实践中，清单 15-17 中的代理方法涵盖了大多数常规测试，因此你很少会在 sfTestFunctional 对象上使用 test() 方法。

清单 15-15 显示 sfBrowser 不会自动跟随重定向。这有一个优势：你可以测试重定向。例如，清单 15-19 展示了如何测试清单 15-14 的响应。

## 清单 15-19 - 使用 sfTestFunctional 测试重定向

```
$b = new sfTestFunctional(new sfBrowser());
$b->
get('/foobar/edit/id/1')->
click('go', array('name' => 'dummy'))->
with('request')->begin()->
isParameter('module', 'foobar')->
isParameter('action', 'update')->
end()->
with('response')->begin()->
isStatusCode(200)->
isRedirected() // Check that the response is a redirect
end()->
```
