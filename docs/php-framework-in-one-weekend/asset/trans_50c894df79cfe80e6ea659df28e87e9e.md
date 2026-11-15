

## DI 容器

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

## 使用 DI 容器

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

