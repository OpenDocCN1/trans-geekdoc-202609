
# Autoloading and OOP Concepts in PHP

## Autoloading Basics

Technically, autoloading works by executing a callback when a PHP class is required but not found. Such callbacks usually attempt to load these classes.

Generally, autoloading can be understood as the attempt to load PHP files (especially PHP class files, where a PHP source file is dedicated for a specific class) from appropriate paths according to the class's fully-qualified name (FQN) when a class is needed.

Suppose we have these classes:

- Class file for `application\controllers\Base`
- Class file for `application\controllers\Control`
- Class file for `application\models\Page`

Under the source folder, these classes should be placed at the paths as their FQNs respectively.

This approach makes it possible to programmatically resolve the class file path according to the FQN, using this function:

```php
function getClassPath(string $sourceFolder, string $className, string $extension = ".php") {
    return $sourceFolder . "/" . str_replace("\\", "/", $className) . $extension;
    // note that "/" works as a directory separator even on Windows
}
```

The `spl_autoload_register()` function allows us to load a class when needed using a user-defined function.

This function can be further extended to use fallback methods of loading.

Note that PHP doesn't attempt to load the classes whenever a file that uses this class is loaded. It may be loaded in the middle of a script, or even in shutdown functions. This is one of the reasons why developers, especially those who use autoloading, should avoid replacing executing source files in the runtime, especially in phar files.

## Section 26.5: Method and Property Visibility

There are three visibility types that you can apply to methods (class/object functions) and properties (class/object variables) within a class, which provide access control for the method or property to which they are applied.

You can read extensively about these in the [PHP Documentation for OOP Visibility](http://php.net/manual/en/language.oop5.visibility.php).

### Public

Declaring a method or a property as `public` allows the method or property to be accessed by:

- The class that declared it.
- The classes that extend the declared class.
- Any external objects, classes, or code outside the class hierarchy.

### Protected

Declaring a method or a property as `protected` allows the method or property to be accessed by:

- The class that declared it.
- The classes that extend the declared class.

This does not allow external objects, classes, or code outside the class hierarchy to access these methods or properties. If something using this method/property does not have access to it, it will not be available, and an error will be thrown. Only instances of the declared self (or subclasses thereof) have access to it.

The example above notes that you can only access the protected elements within its own scope. Essentially: "What's in the house can only be accessed from inside the house."

### Private

Declaring a method or a property as `private` allows the method or property to be accessed by:

- The class that declared it Only (not subclasses).

A private method or property is only visible and accessible within the class that created it.

Note that objects of the same type will have access to each other's private and protected members even though they are not the same instances.

As noted, you can only access the private method/property from within its defined class.

## Section 26.6: Interfaces

### Introduction

Interfaces are definitions of the public APIs classes must implement to satisfy the interface. They work as "contracts", specifying what a set of subclasses does, but not how they do it.

Interface definition is much alike class definition, changing the keyword `class` to `interface`.

Interfaces can contain methods and/or constants, but no attributes. Interface constants have the same restrictions as class constants. Interface methods are implicitly abstract.

Note: interfaces must not declare constructors or destructors, since these are implementation details on the class level.

### Realization

Any class that needs to implement an interface must do so using the `implements` keyword. To do so, the class needs to provide an implementation for every method declared in the interface, respecting the same signature.

A single class can implement more than one interface at a time.

When abstract classes implement interfaces, they do not need to implement all methods. Any method not implemented in the base class must then be implemented by the concrete class that extends it.

Notice that interface realization is an inherited characteristic. When extending a class that implements an interface, you do not need to redeclare it in the concrete class, because it is implicit.

Note: Prior to PHP 5.3.9, a class could not implement two interfaces that specified a method with the same name, since it would cause ambiguity. More recent versions of PHP allow this as long as the duplicate methods have the same signature [[1]](http://php.net/manual/en/language.oop5.interfaces.php).

### Inheritance

Like classes, it is possible to establish an inheritance relationship between interfaces, using the same keyword `extends`. The main difference is that multiple inheritance is allowed for interfaces.

### Examples

In the example below we have a simple example interface for a vehicle. Vehicles can go forwards and backwards.

Then we create two classes that implement the interface: `Bike` and `Car`. `Bike` and `Car` internally are very different, but both are vehicles, and must implement the same public methods that `VehicleInterface` provides.

Typehinting allows methods and functions to request Interfaces. Let's assume that we have a parking garage class, which contains vehicles of all kinds.

Because `addVehicle()` requires a `$vehicle` of type `VehicleInterface` — not a concrete implementation — we can input both `Bike` and `Car` objects, which the `ParkingGarage` can manipulate and use.

## Section 26.7: Final Keyword

**Definition:** The `final` keyword prevents child classes from overriding a method by prefixing the definition with `final`. If the class itself is being defined as `final`, then it cannot be extended.

### Final Method

### Final Class

### Final Constants

Unlike Java, the `final` keyword is not used for class constants in PHP. Use the keyword `const` instead.

### Why do I have to use final?

1. Preventing massive inheritance chain of doom
2. Encouraging composition
3. Force the developer to think about user public API
4. Force the developer to shrink an object's public API
5. A final class can always be made extensible
6. `extends` breaks encapsulation
7. You don't need that flexibility
8. You are free to change the code

### When to avoid final

Final classes only work effectively under following assumptions:

1. There is an abstraction (interface) that the final class implements
2. All of the public API of the final class is part of that interface

## Section 26.8: Autoloading

Nobody wants to `require` or `include` every time a class or inheritance is used. Because it can be painful and is easy to forget, PHP is offering so called autoloading. If you are already using Composer, read about autoloading using Composer.

### What exactly is autoloading?
