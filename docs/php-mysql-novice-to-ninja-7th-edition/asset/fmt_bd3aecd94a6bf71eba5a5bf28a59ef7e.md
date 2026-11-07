
I’ve used the shorthand property promotion again here to create the `$this->website` class variable, but notice what’s happening: when the `EntryPoint` class is constructed, it will need to be given an instance of `JokeWebsite`:

```
$website = new JokeWebsite();
$entryPoint = new EntryPoint($website);
```

Then, when it comes to setting the `$uri` variable for the home page, it reads it from the `$this->website` instance, which will call the `getDefaultRoute()` method in the `JokeWebsite` class:

```
if ($uri == '') {
    $uri = $this->website->getDefaultRoute();
}
```

We’ve added a new class with new method, a constructor and class variable in the existing `EntryPoint` class, just to provide a simple string: `joke/home`. This seems like a lot of work for something so trivial.

However, consider what’s happening here. If we developed a new website—such as an online shop—we could provide a version of the `JokeWebsite` class for that particular website:

```
class OnlineShopWebsite {
    public function getDefaultRoute() {
        return 'product/onsale';
    }
}

// and in index.php
$website = new OnlineShopWebsite();
$entryPoint = new EntryPoint($website);
```

By passing the `OnlineShopWebsite` instance into the `EntryPoint` class, when the `getDefaultRoute` method is run, it will return `product/onsale` and load the sale page as the home page!

This method is relatively simple, but it illustrates the technique of moving site-specific code out of one class and into another. By doing so, we can create another class, with the same set of methods, that exists for a completely different website.

We’ll build on this idea and move all of the code that’s specific to the joke website into the `JokeWebsite` class, leaving just the code that’s useful on any website in the `EntryPoint` class.

The `EntryPoint` class currently contains a lot of code for creating objects needed for the joke website. Firstly, there are the various `DatabaseTable` instances, and slightly further down there’s the code that creates the controllers:

```
include __DIR__ . '/../includes/DatabaseConnection.php';
include __DIR__ . '/../classes/DatabaseTable.php';
include __DIR__ . '/../controllers/JokeController.php';
include __DIR__ . '/../controllers/AuthorController.php';

$jokesTable = new DatabaseTable($pdo, 'joke', 'id');
$authorsTable = new DatabaseTable($pdo, 'author', 'id');

//...
if ($controllerName === 'joke') {
    $controller = new JokeController($jokesTable, $authorsTable);
}
else if ($controllerName === 'author') {
    $controller = new AuthorController($authorsTable);
}
```

The first half of this code is creating `DatabaseTable` instances so they can later be used when creating the controller classes. Look through the code: neither the `$jokesTable` nor `$authorsTable` variables are used anywhere other than when the controllers are created.

Let’s take all this code and move it into a function in the `JokeWebsite` class:

```
class JokeWebsite {
    public function getDefaultRoute() {
        return 'joke/home';
    }

    public function getController(string $controllerName) {
        include __DIR__ . '/../includes/DatabaseConnection.php';
        include __DIR__ . '/../classes/DatabaseTable.php';
        include __DIR__ . '/../controllers/JokeController.php';
        include __DIR__ . '/../controllers/AuthorController.php';

        $jokesTable = new DatabaseTable($pdo, 'joke', 'id');
        $authorsTable = new DatabaseTable($pdo, 'author', 'id');

        if ($controllerName === 'joke') {
            $controller = new JokeController($jokesTable, $authorsTable);
        }
        else if ($controllerName === 'author') {
            $controller = new AuthorController($authorsTable);
        }

        return $controller;
    }
}
```

I’ve added one line of code here at the bottom—`return $controller`—because we need to use this variable in the `EntryPoint` class. This method also needs some information that comes from the `EntryPoint` class, so I’ve added `$controllerName` as an argument, with a type hint that specifies that it must be a string.

Notice that I haven’t actually changed any of the code here. I’ve just moved it into its own method and provided it with the variable it uses as an argument.

Conceptually, this method is actually fairly simple. It’s passed the name of the controller as an argument (for example, `joke`) and then returns the corresponding fully constructed object (for example, an instance of `JokeController`).

Using it on its own, it would look like this:

```
$website = new JokeWebsite();
$jokeController = $website->getController('joke');
$authorController = $website->getController('author');
```

Now that the code is in the `JokeWebsite` class, the `EntryPoint` class can be used to call the new method rather than including all this code. Here’s the complete `EntryPoint` class with the `getController` call to the `JokeWebsite` class:

```
class EntryPoint {
    public function __construct(private $website) {
    }

    public function run($uri) {
        try {
            $this->checkUri($uri);

            if ($uri == '') {
                $uri = $this->website->getDefaultRoute();
            }

            $route = explode('/', $uri);

            $controllerName = array_shift($route);
            $action = array_shift($route);

            $controller = $this->website->getController($controllerName); 

            $page = $controller->$action(...$route);

            $title = $page['title'];

            $variables = $page['variables'] ?? [];
            $output = $this->loadTemplate($page['template'], $variables);

        } catch (PDOException $e) {
            $title = 'An error has occurred';

            $output = 'Database error: ' . $e->getMessage() . ' in ' .
            $e->getFile() . ':' . $e->getLine();
        }

        include  __DIR__ . '/../templates/layout.html.php';
    }

    private function loadTemplate($templateFileName, $variables) {
        extract($variables);

        ob_start();
        include  __DIR__ . '/../templates/' . $templateFileName;

        return ob_get_clean();
    }

    private function checkUri($uri) {
        if ($uri != strtolower($uri)) {
            http_response_code(301);
            header('location: ' . strtolower($uri));
        }
    }
```

For completeness, the whole of `index.php` that makes use of this class is shown below.

**Example: [CMS-EntryPoint-Framework](https://github.com/spbooks/phpmysql7/tree/CMS-EntryPoint-Framework)**

```
include_once '../classes/EntryPoint.php';
include_once '../classes/JokeWebsite.php';

$uri = strtok(ltrim($_SERVER['REQUEST_URI'], '/'), '?');

$jokeWebsite = new JokeWebsite();
$entryPoint = new EntryPoint($jokeWebsite);
$entryPoint->run($uri);
```

There’s now *nothing* in the `EntryPoint` class that’s specific to the joke website! We have a generic `EntryPoint.php`. There are no longer any references to *jokes*, *authors*, or anything specific to one particular website.

If we wanted to use this code on another website, we’d just need to create a class that had the `getController` and `getDefaultRoute` methods and then adjust `index.php` to create the alternate object. For example, for an online shop you could create this class:
