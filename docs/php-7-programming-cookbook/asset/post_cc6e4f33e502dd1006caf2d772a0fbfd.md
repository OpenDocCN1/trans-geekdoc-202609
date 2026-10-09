
# Working with PHP Object-Oriented Programming

## How it works...

For illustration purposes, define a directory structure that matches the `Application\*` namespace. Create a base folder *Application*, and a sub-folder *Entity*. You can also include any sub-folders as desired, such as *Database* and *Generic*, used in other chapters:

![](img/39390f6d56c5a83b28db083a8bd5185c_124_0.png)

Next, create three entity classes, each in their own file, under the *Application/Entity* folder: *Name.php*, *Address.php*, and *Profile.php*. We only show `Application\Entity\Name` here. `Application\Entity\Address` and `Application\Entity\Profile` will be the same, except that Address has an $address property, and Profile has a $profile property, each with an appropriate get and set method:

```php
<?php
declare(strict_types=1);
namespace Application\Entity;

/**
 * Name
 *
 */
class Name
{
    protected $name = '';

    /**
     * This method returns the current value of $name
     *
     * @return string $name
     */
    public function getName() : string
    {
        return $this->name;
    }

    /**
     * This method sets the value of $name
     *
     * @param string $name
     * @return name $this
     */
    public function setName(string $name)
    {
        $this->name = $name;
        return $this;
    }
}
```

You can then either use the autoloader defined in *Chapter 1, Building a Foundation*, or use the simple autoloader mentioned previously. Place the commands to set up autoloading in a file, `chap_04_oop_namespace_example_1.php`. In this file, you can then specify a use statement which only references the namespace, not the class names. Create instances of the three entity classes `Name`, `Address` and `Profile`, by prefixing the class name with the last part of the namespace, `Entity`:

```php
use Application\Entity;
$name = new Entity\Name();
$addr = new Entity\Address();
$prof = new Entity\Profile();

var_dump($name);
var_dump($addr);
var_dump($prof);
```

Here is the output:

![](img/39390f6d56c5a83b28db083a8bd5185c_125_0.png)

Next, use **Save as** to copy the file to a new one named `chap_04_oop_namespace_example_2.php`. Change the `use` statement to the following:

```php
use Application\Entity\Name;
use Application\Entity\Address;
use Application\Entity\Profile;
```

You can now create class instances using only the class name:

```php
$name = new Name();
$addr = new Address();
$prof = new Profile();
```

When you run this script, here is the output:

![](img/39390f6d56c5a83b28db083a8bd5185c_126_0.png)

Finally, again run **Save as** and create a new file, `chap_04_oop_namespace_example_3.php`. You can now test the **group use** feature introduced in PHP 7:

```php
use Application\Entity\{
    Name,
    Address,
    Profile
};

$name = new Name();
$addr = new Address();
$prof = new Profile();
```

Again, when you run this block of code, the output will be the same as the preceding output:

```text
Terminal
Argument Passed to Autoloader = Application\Entity\Name
Argument Passed to Autoloader = Application\Entity\Address
Argument Passed to Autoloader = Application\Entity\Profile
class Application\Entity\Name#1 () {
    protected $name =>
        string(0) ""
}
class Application\Entity\Address#2 () {
    protected $address =>
        string(0) ""
}
class Application\Entity\Profile#3 () {
    protected $profile =>
        string(0) ""
}
--------------------------
(program exited with code: 0)
Press return to continue
```

## Defining visibility

Deceptively, the word *visibility* has nothing to do with application security! Instead it is simply a mechanism to control the use of your code. It can be used to steer an inexperienced developer away from the *public* use of methods that should only be called inside the class definition.

### How to do it…

- Indicate the visibility level by prepending the `public`, `protected`, or `private` keyword in front of any property or method definition. You can label properties as `protected` or `private` to enforce access only through public getters and setters.

- In this example, a `Base` class is defined with a `protected` property `$id`. In order to access this property, the `getId()` and `setId()` public methods are defined. The `protected` method `generateRandId()` can be used internally, and is inherited in the `Customer` child class. This method cannot be called directly outside of class definitions. Note the use of the new PHP 7 `random_bytes()` function to create a random ID.

```php
class Base
{
    protected $id;
    private $key = 12345;

    public function getId()
    {
        return $this->id;
    }

    public function setId()
    {
        $this->id = $this->generateRandId();
    }

    protected function generateRandId()
    {
        return unpack('H*', random_bytes(8))[1];
    }
}

class Customer extends Base
{
    protected $name;
    public function getName()
    {
        return $this->name;
    }
    public function setName($name)
    {
        $this->name = $name;
    }
}
```

> **Best practice**
> Mark properties as *protected*, and define the public `getNameOfProperty()` and `setNameOfProperty()` methods to control access to the property. Such methods are referred to as *getters* and *setters*.

- Mark a property or method as *private* to prevent it from being inherited or visible from outside the class definition. This is a good way to create a class as a **singleton**.

- The next code example shows a class *Registry*, of which there can only be one instance. Because the constructor is marked as *private*, the only way an instance can be created is through the static method `getInstance()`:

```php
class Registry
{
    protected static $instance = NULL;
    protected $registry = array();
    private function __construct()
    {
    }

    public static function getInstance()
    {
        if (!self::$instance) {
            self::$instance = new self();
        }
        return self::$instance;
    }

    public function __get($key)
    {
        return $this->registry[$key] ?? NULL;
    }

    public function __set($key, $value)
    {
        $this->registry[$key] = $value;
    }
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_129_0.png)

> You can mark a method as **final** to prevent it from being overridden. Mark a class as **final** to prevent it from being extended.

- Normally, class constants are considered to have a visibility level of public. As of PHP 7.1, you can declare class constants to be *protected* or *private*. In the following example, the TEST_WHOLE_WORLD class constant behaves exactly as in PHP 5. The next two constants, TEST_INHERITED and TEST_LOCAL, follow the same rules as any protected or private property or method:

```php
class Test
{
    public const TEST_WHOLE_WORLD   = 'visible.everywhere';

    // NOTE: only works in PHP 7.1 and above
    protected const TEST_INHERITED = 'visible.in.child.classes';

    // NOTE: only works in PHP 7.1 and above
    private const TEST_LOCAL= 'local.to.class.Test.only';

    public static function getTestInherited()
    {
        return static::TEST_INHERITED;
    }

    public static function getTestLocal()
    {
        return static::TEST_LOCAL;
    }
}
```

### How it works...

Create a file `chap_04_basic_visibility.php` and define two classes: Base and Customer. Next, write code to create instances of each:

```php
$base        = new Base();
$customer = new Customer();
```

Notice that the following code works OK, and is in fact considered the best practice:

```php
$customer->setId();
$customer->setName('Test');
echo 'Welcome ' . $customer->getName() . PHP_EOL;
echo 'Your new ID number is: ' . $customer->getId() . PHP_EOL;
```

Even though $id is protected, the corresponding methods, getId() and setId(), are both public, and therefore accessible from outside the class definition. Here is the output:

![](img/39390f6d56c5a83b28db083a8bd5185c_130_0.png)

The following lines of code will not work, however, as private and protected properties are not accessible from outside the class definition:

```php
echo 'Key (does not work): ' . $base->key;
echo 'Key (does not work): ' . $customer->key;
echo 'Name (does not work): ' . $customer->name;
echo 'Random ID (does not work): ' . $customer->generateRandId();
```

The following output shows the expected errors:

![](img/39390f6d56c5a83b28db083a8bd5185c_131_0.png)

## See also

For more information on getters and setters, see the recipe in this chapter entitled Using getters and setters. For more information on PHP 7.1 class constant visibility settings, please see https://wiki.php.net/rfc/class_const_visibility.

# Using interfaces

Interfaces are useful tools for systems architects and are often used to prototype an Application Programming Interface (API). Interfaces don't contain actual code, but can contain names of methods as well as method signatures.

> All methods identified in the Interface have a visibility level of public.
