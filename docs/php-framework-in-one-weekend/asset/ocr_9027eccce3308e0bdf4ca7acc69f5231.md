override framework configuration on a site-by-site basis.

The second load()call in the Appconstructor (line 19, listing 10.2) looks like it has potential
to cause us bugs in the future. You might want to consider alternative ways to provide the
location of this extra configuration so that it’s not hard-coded in the framework. For
example, you might want to provide a root directory option that can be set when
instantiating the App.

The previous router in the run() method of App had the routes hard coded in it. This wont
work because the framework no longer knows about what routes are available. To make
the router more general we allow the user to configure their own routes. A simple example
is provided in listing 10.2 which uses an addRoute()method to build an array of available
routes in the App. This is used by the router in run(), lines 33-38, listing 10.2.

We also have to make a small change to the get()callback on the BasicPageController. To allow
for the generalised router code, all route callbacks on controllers take the same parameters.
In the previous examples, the get()callback on the basic page controller was taking the
$spathas parameter, now it gets the Requestobject, like all controller callbacks.

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
12 protected $container; 13 protected $routes; 14
15 public function __construct()
16 {
17 $this->container = new ContainerBuilder();
18 $loader = new YamlFileLoader($this->container, new FileLocator(__DIR__)) ;
19 $loader->load('services.yml');
20 $loader->load('.././src/services.yml');
21 }
22
23 public function addRoute($path, $method, $controller) 24 {
25 $this->routes[$path][$method] = $controller; 26 }
27
28 public function run(Request $request)
29 {
30 $path = $request->getPathInfo();
31 $method = strtolower($request->getMethod());
32
33 if (isset($this->routes[$path][$method]))
34 {
35 $controllerName = $this->routes[$path][$method];
36 $controller = $this->container->get($controllerName);
37 return call_user_func([$controller, $method], $request);
```