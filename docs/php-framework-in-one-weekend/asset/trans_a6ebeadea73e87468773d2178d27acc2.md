

```
12
13 <div class="collapse navbar-collapse" id="main-nav"> 14 <ul class="nav navbar-nav">
15
16 {% for item in nav %}
17 <li><a href="{{ item.url }}">{{ item.title }}</a></li> 18 {% endfor %}
19
20 </ul>
21 </div> <!-- /.navbar-collapse --> 22 </div> <!-- /.container -->
23 </nav>
```

### **清单 9.9: templates/includes/nav.html**

```
17 {% include 'includes/nav.html' %}
```

### **清单 9.10: templates/index.html**

nav 变量的值由我们的新 TemplateService 类设置。清单 9.11 显示了这可能是什么样子。我们随后更新控制器以使用我们的模板服务，而不是直接访问 Twig。清单 9.12 和 9.13 显示了控制器类的更新。我们然后需要用新模板服务的详细信息更新我们的依赖注入配置。这以 twig 和 config_service 服务作为依赖进行配置。我们也更改控制器的配置，以提供新的模板服务而不是 twig。清单 9.14 显示了新的 services.yml 配置文件。

```
2
3 namespace Weekend\Service;
4
5
6 use Twig_Environment;
7
8 class TemplateService
9 {
10     protected $twig;
11     protected $menu;
12
13     public function __construct(Twig_Environment $twig, ConfigService $config) 14 {
15         $this->twig = $twig;
16
17         $this->menu = $config->getConfig();
18     }

19     public function render($templateName, $variables) 20 {
21         foreach ($this->menu as $path => $menuItem) 22 {
23             $variables['nav'][] = [
24                 'title' => $menuItem['title'],
25                 'url' => '/' . $path,
26             ];
27         }

28         return $this->twig->render($templateName, $variables); 29 }
30

31 }
```

### **清单 9.11: src/Service/TemplateService.php**

```
3 use Symfony\Component\HttpFoundation\Response;

4 use Weekend\Service\ConfigService;

5 use Weekend\Service\TemplateService;

6

7 class BasicPageController
8 {
9     protected $menu;
10     protected $theme;

12     public function __construct(TemplateService $theme, ConfigService $config) 13 {
14         $this->theme = $theme;
15         $this->config = $config;
16     }
17
18     public function get($path)
19     {
20         $page = ($path == '/') ? 'index' : substr($path, 1); 21         $menu = $this->config->getConfig();
22         if (isset($menu[$page]))
23         {
24             $content = $this->theme->render('basic.html', $menu[$page]); 25             return new Response($content);
26         }
27         return Response::create("not found", 404);
28     }
29 }
```

### **清单 9.12: src/Controller/BasicPageController.php**

```
3 use Symfony\Component\HttpFoundation\Request;
4 use Symfony\Component\HttpFoundation\Response;
5 use Weekend\Service\TemplateService;
6
7 class ContactController
8 {
9     protected $theme;

11     public function __construct(TemplateService $theme) 12 {
13         $this->theme = $theme;
14     }
15
16     public function get()
17     {
18         $content = $this->theme->render('contact.html', [
19             'title' => ' Contact'
20         ]);
21         return new Response($content);
22     }
23
24     public function post(Request $request)
25     {
26         // TODO: validate input and send email
27         $content = $this->theme->render('basic.html', [
28             'title' => ' Contact',
29             'content' => "Thank you for your message.",
30         ]);
31         return new Response($content);
32     }
```

### **清单 9.13: src/Controller/ContactController.php**

```
1 parameters:
2 template_dir: './templates'
3 data_dir: './data'
4
5 services:
6 loader:
7 class: Twig_Loader_Filesystem
8 arguments: ['%template_dir%']
9 twig:
10 class: Twig_Environment
11 arguments: ['@loader']
12 adapter:
13 class: League\\Flysystem\\Adapter\\Local 14 arguments: ['%data_dir%']
15 filesystem:
16 class: League\\Flysystem\\Filesystem 17 arguments: ['@adapter']
18
19 contact_controller:
20 class: Weekend\\Controller\\ContactController 21 arguments: ['@template_service']
22 basic_page_controller:
23 class: Weekend\\Controller\\BasicPageController 24 arguments: ['@template_service', '@config_service'] 25
26 config_service:
27 class: Weekend\\Service\\ConfigService 28 arguments: ['@filesystem']
29
30 template_service:
31 class: Weekend\\Service\\TemplateService 32 arguments: ['@twig', '@config_service']
```

### **清单 9.14: src/services.yml**

## 第 10 章

### 复用

目前，我们的框架不是很有用，因为它与我们一直在构建的示例应用程序紧密耦合。构建框架的目的是拥有一组可复用的代码。当我们想要做类似的事情时，应该能够将其包含在项目中，以节省重复进行所有基础工作。为了能够做到这一点，我们需要使代码尽可能可复用。

迄今为止，我们已将所有 PHP 代码放入 src 文件夹。我们还在 vendor 文件夹中有由 Composer 管理的 PHP 代码。最终，我们可以将框架作为一个独立项目，并通过 Composer 包含它，但目前我们将把它存储在项目的单独文件夹中。这将允许我们识别并分离出框架的可复用部分。

创建一个名为 lib/weekend 的文件夹，并将当前 src 文件夹中的所有代码移动到这个新位置。如果您现在尝试访问应用程序，将会收到类似“Uncaught Error: Class Weekend\App not found”的错误。我们需要告诉 Composer 我们已移动命名空间 Weekend 的代码，并更新其自动加载器。按清单 10.1 编辑 composer.json 的 autoload 部分。请注意，我们还将 src 文件夹添加到自动加载器配置中，以便它可以找到站点的代码。在此示例中，我没有为站点特定代码使用命名空间。

```
19 "autoload":{
20 "psr-4":{
21 "Weekend\\": "lib/weekend",
22 "": "src/"
23 }
24 }
```

### **清单 10.1: composer.json**

使用 Composer 的 update 或 dump-autoload 命令重新生成自动加载器。您现在应该发现站点又可以正常工作了（假设您仍在运行 PHP 的内置 Web 服务器）。

现在我们可以将站点特定代码放入 src 文件夹。首先，将两个控制器移回 src，因为它们特定于此站点。这会产生一个新错误，因为依赖注入容器不再能找到它们。为了绕过这个问题，我们向 src 文件夹添加一个 services.yml 文件用于站点特定配置。请参阅 10.2 以了解我们如何更新 App 中的构造函数，以便它可以找到我们的额外配置。清单 10.3 显示了带有额外配置的新文件。

请注意，我们首先将局部于 App 的 services.yml 文件加载到依赖注入容器中。这允许我们指定对框架核心至关重要的依赖项。然后我们从 src 文件夹加载第二个 services.yml 配置。这允许我们的应用向依赖注入容器提供额外配置，例如站点特定控制器。这是一种有用的机制，因为它还允许我们按站点覆盖框架配置。

App 构造函数中的第二个 load() 调用（第 19 行，清单 10.2）看起来未来有可能给我们带来 bug。您可能需要考虑提供此额外配置位置的替代方法，以便它不在框架中被硬编码。例如，您可能希望提供一个可在实例化 App 时设置的根目录选项。

App 中 run() 方法的先前路由器在其中将路由硬编码了。这将不起作用，因为框架不再知道有哪些路由可用。为了使路由器更通用，我们允许用户配置自己的路由。清单 10.2 提供了一个简单示例，它使用 addRoute() 方法在 App 中构建可用路由数组。这由 run() 中的路由器使用（第 33-38 行，清单 10.2）。

我们还需要对 BasicPageController 中的 get() 回调进行小幅更改。为了适应通用路由器代码，控制器上的所有路由回调都采用相同的参数。在之前的示例中，基本页面控制器上的 get() 回调将 $path 作为参数，现在它获取 Request 对象，如所有控制器回调一样。

```
2 namespace Weekend;
3
4 use Symfony\Component\Config\FileLocator;
5 use Symfony\Component\DependencyInjection\ContainerBuilder;
6 use Symfony\Component\DependencyInjection\Loader\YamlFileLoader;
7 use Symfony\Component\HttpFoundation\Request;
8 use Symfony\Component\HttpFoundation\Response;
9
10 class App
11 {
12     protected $container;
13     protected $routes;
14
15     public function __construct()
16     {
17         $this->container = new ContainerBuilder();
18         $loader = new YamlFileLoader($this->container, new FileLocator(__DIR__)) ;
19         $loader->load('services.yml');
20         $loader->load('.././src/services.yml');
21     }
22
23     public function addRoute($path, $method, $controller) 24 {
25         $this->routes[$path][$method] = $controller; 26     }
27
28     public function run(Request $request)
29     {
30         $path = $request->getPathInfo();
31         $method = strtolower($request->getMethod());
32
33         if (isset($this->routes[$path][$method]))
34         {
35             $controllerName = $this->routes[$path][$method];
36             $controller = $this->container->get($controllerName);
37             return call_user_func([$controller, $method], $request);
```

### **清单 10.2**

