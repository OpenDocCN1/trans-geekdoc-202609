We can now add this ConfigService to our services.ymlfile:

```
config_service:
class: Weekend\\Service\\ConfigService arguments: ['@filesystem']
```

And also add the BasicPageController which depends on Twig and this new config service:

```
basic_page_controller:
class: Weekend\\Controller\\BasicPageController arguments: ['@twig', '@config_service']
```

Update the constructor in BasicPageControllerto take the ConfigServiceas a dependency, rather than the raw menu data that was being passed before:

```
public function \_\_construct(Twig_Environment $twig, ConfigService $config) {
This->twig = $twig; $this->config = $config; }
```

Update the get()callback in the controller so that it fetches the $menuConfiguration from the ConfigService:

```
public function get($path) {
$Page = ($path == '/') ? 'index' : substr($path, 1); $menu = $this->config->getConfig();
if (isset($menu[$Page]))
{
$content = $this->twig->render('index.html', $menu[$page]); return new Response($content);
}
return Response::create("not found", 404);
}
```

And then finally, tidy up the router so that it now fetches the controllers from the container:

```
switch ($Path) {
case '/':
case '/index':
case '/about':
$controller = $this->container->get('basic_page_controller'); return $controller->get($path);
case '/contact':
$controller = $this->container->get('contact_controller'); if ($method == 'POST')
{
return $controller->post($Request); }
return $controller->get();
}
```

Maybe you can start to think about ways to improve this. The run()method now doesn't
have to deal with instantiating dependencies and controllers. In run()we are just dealing
with routing requests to the correct controller callback. How would you extract the route
configuration from the router logic? This is something we’ll come back to, but for now
consider the following example. Can you see how to improve it?

```
public function run(Request $request) {
$path = $request->getPathInfo();
$method = strtolower($request->getMethod()); ];
$routes = [
'/' => 'basic_page_controller', '/index' => 'basic_page_controller', '/about' => 'basic_page_controller', '/contact' => 'contact_controller',
]
if (isset($routes[$path])) {
$controller = $this->container->get($routes[$path]);
if (is_callable([$controller, $method])) {
return call_user_func_array([$controller, $method], [$request]); }
}
```