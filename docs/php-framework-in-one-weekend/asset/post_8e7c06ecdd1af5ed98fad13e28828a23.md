
## Multiple Controllers

Now we can add another controller with some new functionality. Let’s create a simple contact form. Listing 7.3 shows the code for an empty ContactController class. This is just the outline that shows how the code for the class will be structured.

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

Listing 7.3: src/Controller/ContactController.php

I’m going to add an instance variable to store the Twig environment and the same initialisation code that I used in the BasicPageController. You may notice that we’re repeating ourselves, which is usually a sign that we can improve the design of our code. We will revisit this later and look at how we can avoid having the same initialisation code in both controllers.

My ContactController constructor now looks like this:

```php
protected $twig;
public function __construct() {
$loader = new Twig_Loader_Filesystem(__DIR__.'/../../templates'); $this->twig = new Twig_Environment($loader);
}
```

I have two callbacks in this controller, one called get() and another called post(). This is because there will be two different types of call to this controller. The router will dispatch HTTP GET and POST requests to this controller. We will look at how that is configured later, but for now let's just create and return a contact form from the get() callback. This is what my first attempt looks like:

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

Now update the router defined in App to send requests for the /contact path to the new ContactController. In the switch statement in the run() method add the following case:

```php
case '/contact':
$controller = new ContactController();
return $controller->get();
```

You will get an error if you now try and access /contact. The error is coming from Twig because we have asked it to render a template that does not exist. To get it working create the templates/forms folder with a contact.html template form as per Listing 7.4.

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

**Listing 7.4:** templates/forms/contact.html

You will also need to update your index.html template because it will automatically escape the $content variable and display the HTML tags. This is the security measure described earlier. We add the raw filter to disable the automatic escaping in the template, as we know it won’t be user input. But, we will revisit later and see how this can be improved. For now, update your index.html template file so the content is output raw:

```php
<p>{{ content | raw }}</p>
```

You should now see a contact form when you visit /contact. But, because the router doesn’t know the difference between the GET and POST requests you also see the form when you click submit. The submit button causes the form data to be sent via a POST request. Let’s add a route to our router to dispatch this to the post() callback on the ContactController.

The HTTP method is available from the $request object:
$method = $request->getMethod();

We use this $method variable in the router to decide which callback method is called on the controller. Notice that I also pass the $request variable so that the post() callback can get the submitted data:

```php
case '/contact':
$controller = new ContactController();
if ($method == 'POST')
{
return $controller->post($request);
}
return $controller->get();
```

All that remains is to implement the post() request, handle the form data, then respond with a thank you message:

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

I’ve deliberately left the validation of input and the sending of email as a future task to be implemented later. The important thing here is to see how different controllers can be mapped to different requests, and how different HTTP methods can be mapped to different callback methods on the controllers. We urgently need to deal with dependencies before our controllers get too complicated.

## Chapter 8

### Dependency Injection

We now have two controllers. If you look in the constructors for both BasicPageController and ContactController you will see some duplicate code. Both controllers have a dependency on the Twig system that they use to render the output. Both controllers currently instantiate their own version of the Twig environment and store it in an instance variable. Duplicating code like this is never a good idea if you care about the maintainability of your software. If the Twig code needs to change you’ve got to find every place it’s used and update it. That might not be as much of an issue here, with just two controllers, but as the system grows so does the complexity. Keeping things separate is important.

The Twig dependency is hard-coded into both our controllers. The BasicPageController also has a hard-coded dependency on our $filesystem object, and our menu.json configuration.

Testing objects with hard-coded dependencies is difficult. As you saw earlier in our brief look at testing, we ideally want to test each bit of functionality separately.

If we can remove the hard-coded dependencies we can make our controllers a bit easier to understand, easier to maintain, and isolate functionality. We do this by using dependency injection, which simply means we pass in the dependencies rather than create them in the class. So, in the case of the ContactController we pass in the Twig environment to the constructor:

```php
public function __construct(Twig_Environment $twig) {
$this->twig = $twig;
}
```

In the case of the BasicPageController we pass in the Twig environment and the menu config into the constructor. We no longer need the $filesystem as this was just used to load the config:

```php
public function __construct(Twig_Environment $twig, $menu) {
$this->twig = $twig;
$this->menu = $menu;
}
```

Our controllers are now much simpler, but this makes our App a bit more complicated. We need to instantiate the dependencies so that we can pass them into the controllers. Because both controllers use Twig, I’ve added it as a global service by creating an instance variable in our App constructor. I’ve also added the $filesystem in the same way:

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

I then added a private method that loads the menu configuration:

```php
private function getMenuConfig()
{
return json_decode($this->filesystem->read('menu.json'), true);
}
```

And now update the router to create and pass the dependencies into the controllers:

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

## Testing

Now that our controllers are independent, they should be easier to test. Let’s try this out by revisiting our simple test.php script. Listing 8.1 shows how the functionality of the controller can be tested separately. We’re not testing the dependencies, so we create fake (simplified) versions of the dependencies and pass them in to the controller. We do this for all the scenarios we want to test our controller against.

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

**Listing 8.1:** test.php

This is a simple example, and in reality you would probably use a testing framework. PHPUnit is a popular testing framework and provides a mechanism to create fake objects (or Mocks, as they’re called in testing) to use as dependencies. Many PHP packages come with adapters and plugins to use as dependencies in tests. For example, the Flysystem package we are using as a filesystem abstraction provides a Memory and a Null adapter that you can use to create fake filesystems in your tests.
