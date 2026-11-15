

## 多控制器

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

## 测试

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

