
called `__autoload()` and put your autoloading code there. At some point in the future, `__autoload()` might be removed from PHP, so it is more forward compatible to use `spl_autoload_register()` instead.

**NOTE:** PHP also provides functionality for accessing class methods and class properties that do not exist:

- If a class method is called but does not exist, the class’s `__call()` method is executed, if it exists.
- If a class property is accessed but does not exist, the class’s `__get()` and `__set()` methods are executed (for read and write access), if they exist.

## Cloning Objects

```php
$b = clone $a;
```

Suppose you have a class instance in `$a`. The assignment `$b = $a` would not create a copy of `$a`, but `$b` would now contain a reference to `$a`; you would still have only one class instance.

As an alternative, PHP provides the clone keyword, which allows creating a copy of the class:

```php
$b = clone $a;
```

However, sometimes you do not want exact copies. For instance, imagine that each class instance has a property that contains a globally unique identifier (GUID). Even though you create a clone of a class instance, you want the GUID still to be as unique as possible.

PHP provides a way to inject code after an object has been cloned. If the class contains a method called __clone(), it is executed for the cloned class instance after the cloning process has finished:

```php
<?php
class MyCloneableClass {
    private $guid = null;

    public function __construct() {
        $this->guid = uniqid();
    }

    public function __clone() {
        $this->guid = uniqid();
    }

    public function getGuid() {
        return $this->guid;
    }
}

$c1 = new MyCloneableClass();
$c2 = clone $c1;
echo '1: ', $c1->getGuid(), ', 2:', $c2->getGuid();
?>
```

Cloning Objects (and Changing Them Nevertheless) (clone.php)

Running the preceding code leads to a result comparable to Figure 4.2: The two instances have different GUIDs.

![](img/2862989e5dc7f1b1d0bc64321737f084_124_0.png)

Figure 4.2 The two instances have different GUIDs.

## Serializing and Deserializing Objects

```php
public function __sleep() {
    $this->db->close();
    return array('guid');
}
public function __wakeup() {
    $this->connectDb();
}
```

When you are storing objects for later use, they need to be transformed into something that can easily be put in, say, a database. PHP provides several ways to transform an object instance into a string (and putting it back into its original form); the most common approach is to use the serialize() and unserialize() functions, which are also used in other chapters of this book.

Interesting from an OOP point of view is that it is possible to intercept the process of serialization and deserialization. Suppose, for instance, that your class

contains a property that should (or can) not be serialized (perhaps a database handle). Ideally, this property should be removed before serialization and re-created upon deserialization.

PHP aids us with this task and provides the following two "magic" method names. If your class contains these methods, they will be executed accordingly:

- __sleep()—Needs to return an array with all properties to be serialized, may also clean up
- __wakeup()—Is called after deserialization, can be used to re-setup properties

The following code listing shows a typical implementation closing and resetting a database connection. After serialization and deserialization, the GUID is the same, but the database connection has been reestablished:

```php
<?php
class MySerializableClass {
    public $guid = null;
    public $db = null;

    public function __construct() {
        $this->guid = uniqid();
        $this->connectDb();
    }

    private function connectDb() {
        $this->db = new MySQLi('server', 'user',
        'password', 'db');
    }

    public function __sleep() {
        $this->db->close();
        return array('guid');
    }

    public function __wakeup() {
        $this->connectDb();
    }
}

$c1 = new MySerializableClass();
echo 'Before: ', $c1->guid;
$s = serialize($c1);
$c2 = unserialize($s);
echo '; after: ', $c2->guid;
?>
```

Serializing and Deserializing Objects (serialize.php)

**NOTE:** When deserializing an object, you need to make sure that the class exists; otherwise, PHP uses the dreaded "special" PHP Incomplete Class Name class in the result.

**TIP:** PHP supports a variety of magic methods and functions. The online manual features a list at http://php.net/oop5.magic.

## Implementing Singletons

```php
if (self::$instance == null) {
    self::$instance = new self;
}
return self::$instance;
```

A common —but also criticized—design pattern is the singleton pattern. It is not entirely easy to implement, so we have dedicated a phrase to its creation.

The main goal of using the singleton pattern is that no matter how often you instantiate a certain class, you only get one object. This can, for instance, prove useful when creating database connections: often, you only need one connection that can be reused within your code.

A common PHP implementation of the singleton pattern uses a few OOP features of the language to prevent multiple different instances of one class. First of all, the class constructor is not available because we make it private:

```php
private function __construct() {
}
```

Another approach to create two instances of the class is to use one instance and then clone it. This can be avoided by making the __clone() magic method private, as well:

```php
private function __clone() {
}
```

So, right now we cannot create multiple instances of the class, we cannot even create one instance. Therefore, we introduce a method that will give us a class instance. Within the class, we can call the class constructor—the private visibility allows that. The class instance will then be stored in a static and private class member. So, the dummy instantiation method first checks whether we already have a class instance stored in that static property. If so, the instance is returned; otherwise, the code creates a new (and only) instance:

```php
static private $instance = null;

static public function getInstance() {
    if (self::$instance == null) {
        self::$instance = new self;
    }
    return self::$instance;
}
```

The following code listing contains the complete syntax for the singleton class:

```php
<?php
class PHPSingleton{
    static private $instance = null;

    static public function getInstance() {
        if (self::$instance == null) {
            self::$instance = new self;
        }
        return self::$instance;
    }

    private function __construct() {
    }
    private function __clone() {
    }
}
?>
```

*Implementing a Singleton (singleton.php)*

**NOTE:** As mentioned, singleton patterns have some shortcomings. Code generally gets harder to test because the singleton class needs to be global and adds state to the application. As always, your mileage may vary.

## Using Namespaces

One major new feature of PHP 5.3 is the inclusion of namespaces. Namespaces are a tool to group related functionality and to avoid name clashes. Imagine you write a function with the generic name such as showInfo(). Another developer in the same project writes a different function but uses the same name. Usually, you would prefix the function name so that it is unique, which leads to the dreaded, really long identifiers, like Project_Module Submodule showInfo(). Namespaces can help here: You provide the context in form of a namespace; within that namespace, showInfo() is unique; the other developers use other namespaces. In the end, this facilitates encapsulation of functionality.

The main keyword for namespaces is –surprise! – namespace. The namespace keyword must be the first command within a PHP page (after optional comments) and must even not be preceded by HTML markup. If you would like to structure namespaces, you may create a hierarchy, by using the (a bit unusual) backslash character as a separator:

```php
namespace Project\Module\Submodule;
```

This namespace is now valid for the whole file. If you create the showInfo() method within that file, and include the file in another PHP script, the following code can be used to execute the method:

```php
Project\Module\Submodule\showInfo();
```

To define several namespaces in one file, you could use multiple namespace statements; the preferred way however is to use curly braces:
