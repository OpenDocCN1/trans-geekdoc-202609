# HTTP Requests

PHP makes the data from the incoming request available as global variables. They look like this:

```
$name = $_GET['name'];
```

We don’t want to work with these global variables directly. And, now we have a library of code to make working with HTTP messages easier, we don’t have to. The HTTP Foundation component can create a request object for you from the data provided by PHP in the global variables.

When we used the Composer requirecommand to download the package it added it to the autoloader so that the classes are automatically available to us. The code for them will be automatically included when we first use the class in our code. We can create an object to represent the request like this:

```
$request = \Symfony\Component\HttpFoundation\Request::createFromGlobals();
```

When we are including code from multiple packages we need to ensure that the names of things defined by the packages don’t clash. PHP provides a feature called namespaces that protects against naming collisions. You can see in the previous example that the Request object provided by the HttpFoundation component has the _fully qualified_ name:

```
\Symfony\Component\HttpFoundation\Request
```

Because we don’t have anything called Request in this file there will not be a clash of names. We can therefore tidy up our code by _importing_ the name to our local scope with PHP’s usekeyword. You can see this demonstrated in listing 3.2 (lines 2 and 5).

Now we have an object we can use to get information from the request:

```
$name = $request->get('name');
```

You will notice that I have also added a print_rstatement to our example page (line 16, listing 3.2) so you can see the structure of the $requestobject. Listing 3.2 shows our new public/index.phpfile.

```
1 <?php
2 use Symfony\Component\HttpFoundation\Request;
3 require __DIR__.'../vendor/autoload.php';
4
10 <head>
11 <meta charset="UTF-8">
12 <title>Document</title>
13 </head>
14 <body>
15 <h1>Hello <?php print $name; ?>!</h1> 16 <pre><?php print_r($request); ?></pre> 17 </body>
18 </html>
```

```
5 $request = Request::createFromGlobals();
6 $name = $request->get('name');
7 ?>
8 <!DOCTYPE html>
9 <html lang="en">
```