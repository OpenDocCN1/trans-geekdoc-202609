

```php
class Users {
private $name = "John";
}
$user = new Users();
echo $user->name; // Error: property is private
?>
```

In this code, a User class is defined with a private property $name. When we try to access this property after instantiating the class, an error is generated because the property is declared as private and therefore inaccessible from outside the class. If we redefine the __get magic method in the User class, the error disappears.

```php
<?php
class Users {
private $name = "John";
public function __get($propertyName) {
if ($propertyName == 'name') {
return $this->name;
}
}
}

$user = new Users();

// Using the magic method __get() to access the private property
echo $user->name; // Displays "John"
?>
```

In this code, the __get() method is a PHP magic method that is called automatically when an attempt is made to access an inaccessible object property.

In this example, the __get() method is defined for the User class. When trying to access an inaccessible property of the class, this method is invoked with the property name as argument.

In the body of the method, we check whether the property name passed as an argument corresponds to 'name'. If so, the value of the object's private property $name is returned to the caller.

This magic method provides controlled access to a private property, returning it only when the requested property name matches that of the object's private property. Execution of this code will produce the following display:

![](img/caba2aa22f5409ba73dea47176330677_586_0.png)

### c. __set()

Now suppose we want to modify the value of the "name" property from outside the "User" class. Again, this property is private, so we get an error if we try to do so directly. We can use the magic __set() method to allow this property to be modified in a controlled way. Here's an example:

```php
<?php
class Users {
private $name;

public function __set($propertyName, $value) {
if ($propertyName == 'name') {
$this->name = $value;
}
}
}

$user = new Users();

// Use the __set() magic method to modify the private property
$user->name = "Lina"; // The "name" property is now set to "Lina".
?>
```

In this example, the User class defines a private property $name. The __set() magic method is used to intercept attempts to assign values to inaccessible object properties.

When we try to assign a value to the "name" property of the $user object, the __set() method is automatically invoked. It receives two arguments: the name of the property to be modified and the value to be assigned to it.

In the body of the __set() method, we check whether the name of the property passed corresponds to "name". If so, the value supplied is assigned to the object's $name property.

This magic method allows you to modify a private property of the User class in a controlled way, by intercepting and processing attempts to assign values to this property.

### d. __call() and __callStatic()

The magic __call() method is invoked when we attempt to call a method that doesn't exist or is inaccessible from an object. It receives two arguments: the name of the attempted method and any associated arguments, which are then converted into an array.

As for the magic __callStatic() method, it is triggered when we try to use a method that doesn't exist or is inaccessible in a static context. This method accepts the same arguments as __call().

### Example of the __call() method:

```php
<?php
class Example {
    public function __call($lastNameMethod, $arguments) {
        echo "The method '$lastNameMethod' does not exist or is inaccessible.";
        echo "The arguments passed are: " . implode(', ', $arguments);
    }
}

$object1 = new Example();
$object1->methodNotExist("argument1", "argument2");
?>
```

In this example, we have an "Example" class with a magic __call() method. When we try to call a method methodNotExist() on the object $object1, this method doesn't exist in the class. Consequently, the __call() method is invoked automatically. It displays a message indicating that the method does not exist, as well as the arguments passed to this method.

Execution of this code will produce the following display:

![](img/caba2aa22f5409ba73dea47176330677_589_0.png)

This result clearly shows that the magic __call method has been executed instead of the non-existent method, since the latter doesn't exist.

### Example of the __callStatic() method:

```php
<?php
class Example {
public static function __callStatic($lastNameMethod, $arguments) {
    echo "The static method '$lastNameMethod' does not exist or is inaccessible.";
    echo "The arguments passed are: " . implode(',', $arguments);
}
}
Example::staticMethodNotExist("argument1", "argument2");
?>
```

In this example, we have an Example class with a __callStatic() magic method. When we try to call a static method staticMethodNotExist() on the "Example" class, this method doesn't exist in the class.

Consequently, the __callStatic() method is invoked automatically. It displays a message indicating that the static method does not exist, as well as the arguments passed to this method.

![](img/caba2aa22f5409ba73dea47176330677_590_0.png)

### e. __toString()

The __toString() method is called automatically when an object is used in a context where a character string is expected, for example when it is passed to the echo function. It defines the string representation of the object.

```php
<?php
class Example {
private $name;

public function __construct($name) {
$this->name = $name;
}

public function __toString() {
    return "This object is called " . $this->name;
}

}

$object1 = new Example("NameObject1");
echo $object1; // Display : This object is called Example
?>
```

In this example, the Example class defines a magic __toString() method. When we attempt to display the object $object1 using echo or string concatenation, the __toString() method is automatically invoked. This method returns a string that represents the object in a meaningful way.

![](img/caba2aa22f5409ba73dea47176330677_591_0.png)

### f. __destruct()

The __destruct() method is invoked automatically just before the object is destroyed. It is used to perform cleanup operations or release resources associated with the object.

```php
<?php
class Example {
    public function __destruct() {
        echo "The object has been destroyed.";
    }
}

$object1 = new Example();
unset($object1); // Explicit object destruction. Displays: The object has been destroyed.
?>
```

In this example, the Example class defines a magic __destruct() method. This method is automatically called when the object is destroyed, either explicitly using the unset() function, or implicitly when the script ends. In this case, when we use unset($object1) to destroy the object $object1, the __destruct() method is invoked and displays a message indicating that the object has been destroyed.

The object has been destroyed.

## Conclusion

PHP's magic methods offer powerful flexibility for customizing the behavior of objects and classes. They enable automatic intervention during various interactions with objects, making code management and extension easier.

In this chapter, we've explored some of the most commonly used magic methods, such as __get(), __set(), __call(), __callStatic(), __toString() and __destruct(). These methods provide useful functionality for managing access to properties, calling methods dynamically, displaying objects as strings and performing actions when objects are destroyed.

It's worth noting that there are other magic methods in PHP, such as __isset(), __unset(), __invoke(), __clone(), and others, which offer additional functionality to meet specific development needs.

By judiciously exploiting these magic methods, PHP developers can make their code more flexible, more robust and easier to maintain, while benefiting from greater expressiveness in the design of their applications.

