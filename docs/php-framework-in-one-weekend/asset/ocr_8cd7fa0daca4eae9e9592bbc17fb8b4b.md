# Multiple Controllers

Now we can add another controller with some new functionality. Let’s create a simple contact form. Listing 7.3 shows the code for an empty ContactControllerclass. This is just the outline that shows how the code for the class will be structured.

```
1 <?php
2 namespace Weekend\Controller;
3
4 class ContactController
5 {
6 public function __construct()
7 {
8 }
9
10 public function get() 11 {
12 }
13
14 public function post()
15 {
16 }
17 }
```

Listing 7.3: src/Controller/ContractController.php

I’m going to add an instance variable to store the Twig environment and the same initialisation code that I used in the BasicPageController. You may notice that we’re repeating ourselves, which is usually a sign that we can improve the design of our code. We will revisit this later and look at how we can avoid having the same initialisation code in both controllers.

My ContactControllerconstructor now looks like this:

```
protected $twig;
public function __construct() {
$loader = new Twig_Loader_Filesystem(__DIR__.'/../../templates'); $this->twig = new Twig_Environment($loader);
}
```

I have two callbacks in this controller, one called get()and another called post(). This is because there will be two different types of call to this controller. The router will dispatch HTTP GET and POST requests to this controller. We will look at how that is configured later, but for now let's just create and return a contact form from the get()callback. This is what my first attempt looks like:

```
public function get() {
'title' => 'Contact', 'content' => $form,
$form = $this->twig->render('forms/contact.html'); $content = $this->twig->render('index.html', [
]);
return new Response($content); }
```

Now update the router defined in App to send requests for the /contact path to the new ContactController.In the switch statement in the run()method add the following case: