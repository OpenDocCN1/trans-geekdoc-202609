```
33 return new Response($content);
34 }
35 return Response::create("not found", 404);
36 }
37 }
```

# **Listing 7.1: src/Controller/BasicPageController.php**

The constructor (lines 16-25) now deals with creating the filesystem and the Twig environments. We also load the content of menu.json into a $menu variable so that it can be used later in our _controller callback_. The get() method (lines 27-36) is our callback to which the router will _dispatch_ requests defined for this controller. The code which dealt with handling the response, that was previously hard-coded into the router has been moved from App’s run() method to this controller’s get() method.

Line 29 in the get()callback checks for a default path, and drops the leading /from paths. The value of $page is used to fetch the appropriate section of the $this->menu()array that was created in the constructor by reading from menu.json file.

The router in our App class is now much simpler. We route all three of the defined paths to the same controller. Listing 7.2 shows the new routing code in our run() method.

```
13 public function run(Request $request)
14 {
15 $path = $request->getPathInfo();
16 switch ($path)
17 {
18 case '/':
19 case '/index':
20 case '/about':
21 $controller = new BasicPageController();
22 return $controller->get($path);
23 }
24 return Response::create("Not found", 404);
25 }
```

# **Listing 7.2: src/App.php**