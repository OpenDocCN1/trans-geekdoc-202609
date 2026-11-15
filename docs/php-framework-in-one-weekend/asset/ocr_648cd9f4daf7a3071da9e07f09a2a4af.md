# Chapter 8
Dependency Injection

We now have two controllers. If you look in the constructors for both BasicPageController and ContactController you will see some duplicate code. Both controllers have a dependency on the Twig system that they use to render the output. Both controllers currently instantiate their own version of the Twig environment and store it in an instance variable. Duplicating code like this is never a good idea if you care about the maintainability of your software. If the Twig code needs to change you’ve got to find every place it’s used and update it. That might not be as much of an issue here, with just two controllers, but as the system grows so does the complexity. Keeping things separate is important.

The Twig dependency is hard-coded into our both our controllers. The BasicPageController also has a hard-coded dependency on our $filesystem object, and our menu.jsonConfiguration.

Testing objects with hard-coded dependencies is difficult. As you saw earlier in our brief look at testing, we ideally want to test each bit of functionality separately.

If we can remove the hard-coded dependencies we can make our controllers a bit easier to understand, easier to maintain, and isolate functionality. We do this by using dependency injection, which simply means we pass in the dependencies rather than create them in the class. So, in the case of the ContactController we pass in the Twig environment to the constructor:

```
```php
public function __construct(Twig_Environment $twig) {
$this->twig = $twig; }
```
```

In the case of the BasicPageController we pass in the Twig environment and the menu config into the constructor. We no longer need the $filesystem as this was just used to load the config:

```
```php
public function __construct(Twig_Environment $twig, $menu) {
$this->twig = $twig; $this->menu = $menu; }
```
```

Our controllers are now much simpler, but this makes our Appa bit more complicated. We need to instantiate the dependencies so that we can pass them into the controllers. Because both controllers use Twig, I’ve added it as a global service by creating an instance variable in our App constructor. I’ve also added the $filesystem in the same way:

```
```php
protected $twig;
protected $filesystem;
public function __construct() {
$loader = new Twig_Loader_Filesystem( __DIR__.'/../templates');
$this->twig = new Twig_Environment($loader);
$adapter = new Local(__DIR__.'./../data');
$this->filesystem = new Filesystem($adapter); }
```
```

I then added a private method that loads the menu configuration:

```
```php
private function getMenuConfig()
{
return json_decode($this->filesystem->read('menu.json'), true);
```
```