
Note
In PHP 8, this was cleaned up a bit: If the inheriting class had a `private` method with the same name as the method of the inheriting class marked as `final`, then a fatal error was still thrown. In the background, PHP performed its inheritance checks unnecessarily, even though the method in the inheriting class was `private`. In PHP 8, this behavior has been removed for performance and cleanliness reasons.

You can also use `final` to identify entire classes. In such a case, you can no longer inherit from these classes (see Figure 11.19).

```
final class Computer {
public function start() {
return "Computer is started";
}
}

class Laptop extends Computer {
public function start() {
return "Laptop is started";
}
}
```

Listing 11.21 Final Classes (Excerpt from "final_class.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_327_0.png)

Figure 11.19 The Error when Trying to Access a Final Class

Note
There are no final properties. The following construct therefore results in the error message shown in Figure 11.20, which states that `final` can only be defined for methods:
`class Computer {
final $CPU = "The CPU";
}`

![](img/ae7820c36e8f24c1623d26668b28e80e_328_0.png)

Figure 11.20 "final" for Properties Fails

## "readonly"

Since PHP 8.1, there is a new `readonly` attribute. This allows properties to be defined as read-only and not writable:

```
private readonly string $sek;
```

In this case, there is only one way to give the property a value, which is in the constructor, because without a value the property would be meaningless:

```
public function __construct(string $sek) {
    $this->sek = $sek;
}
```

It is not possible to give it a default value or to change it subsequently in other methods. In these cases, PHP would throw an error.

The following listing shows the complete example.

```
<?php
class Computer {
private readonly string $sek;

public function __construct(string $sek) {
    $this->sek = $sek;
}

public function start() {
    return "Computer starts in " . $this->sek;
}
}

$MyComputer = new Computer("15 seconds");
echo $MyComputer->start();
?>
```

Listing 11.22 A "readonly" Property ("readonly.php")

> Note
> Since PHP 8.2, the readonly attribute has also been available for classes. This means that all properties of a class are read-only and can only be set via the constructor.

### 11.3.5 Interfaces

An _interface_ represents a template for a class. It declares methods without implementation:

```
interface Bootmanager {
    function start();
}
```

These methods can now be implemented in classes. The implements keyword is used for this purpose. The method is then filled with life or functionality within the class.

```
class Computer implements Bootmanager {
    function start() {
        return "Computer is started";
    }
}
```

Listing 11.23 Interfaces (Excerpt from "interfaces.php")

> Note
> You cannot define properties in interfaces!

However, the interface defines not only the method name, but also any parameters that the method receives. If there are differences between the class and the interface, you will receive an error.

```
interface Bootmanager {
    function start($sek);
}
```

```
class Computer implements Bootmanager {
    function start($sek) {
        return "Computer starts in $sek";
    }
}
```

Listing 11.24 Parameters in Interfaces (Excerpt from "interfaces_parameter.php")

Note
Because PHP is only loosely typed—that is, the data types do not have to be defined—the methods defined in the interface do not need to have the same data type for the return value in the classes. In strictly typed languages, however, this is usually required.

One of the advantages of interfaces is that several interfaces can be implemented for one class. The following example uses a Bootmanager interface for the Computer class and the Auto class (with all the electronics!). The Formatter interface, on the other hand, defines a method that is only implemented in the Computer class. Figure 11.21 shows the output.

```
<?php
interface Bootmanager {
function start();
}
interface Formatter {
function format($drive);
}
class Computer implements Bootmanager, Formatter {
public function start() {
return "Computer is started";
}
public function format($drive): string {
return "Drive $drive is formatted";
}
}
class Car implements Bootmanager {
public function start() {
return "Car is started";
}
}
$MyComputer = new Computer();
echo $MyComputer->start() ."<br />";
echo $MyComputer->format("C")."<br />";
$MyCar = new Car();
echo $MyCar->start();
?>
```

Listing 11.25 Handling Multiple Interfaces ("interfaces_multiple.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_331_0.png)

Figure 11.21 The Various Methods Are Used

### 11.3.6 Late Static Binding

If you define static methods with static, you can also work with them in the inheritance context of classes. The following example shows two classes, Computer and Laptop. Laptop inherits from Computer. The start() method is only defined in Computer and is called statically.

The class() static method is called in the start() method. With __CLASS__ the class name from the current context is returned. This method also exists in the Laptop class. self::; however, accesses the class in which the call is made directly. Incidentally, a call to the higher-level class would be made via parent.

```
<?php
class Computer {
public static function class() {
return __CLASS__;
}
public static function start() {
return self::class() . " is started.";
}
}
class Laptop extends Computer {
public static function class() {
return __CLASS__;
}
}
echo Laptop::start();
?>
```

Listing 11.26 Static Inheritance with "self" ("self.php")

The output here is therefore this:

Computer is started.

Late static binding defines a new keyword: static. Now, the keyword itself is not actually new; it is only used here to clarify the static binding. In the inheritance situation, it does not refer to the current class but contains the runtime information about which class is being called—in this case, the Laptop class. The runtime information is also why the process is called late static binding.

Consider the following slightly adapted example.

```
<?php
class Computer {
public static function class() {
return __CLASS__;
}
public static function start() {
return static::class() . " is started.";
}
}
class Laptop extends Computer {
public static function class() {
return __CLASS__;
}
}
echo Laptop::start();
?>
```

Listing 11.27 Static Inheritance with "static" ("staticbinding.php")

The output here is:

Laptop is started.

## "static" as Return Value

In PHP 8, a method (or function) can also contain a static class as a return value. This means that static is also a type declaration.

It is simply specified as a type declaration in the method:

```
public static function class() : static {
return new static();
}
```

To ensure that the static method actually returns a static class, the static() function is used here.

> Note
> static can also be combined as a union type (see Chapter 6) with other types or null — for example, ?static or static|array.

The following listing shows the complete script.

```php
<?php
class Computer {
    public static function class() : static {
        return new static();
    }

    public static function start() : string {
        return get_class(static::class()) . " is started.";
    }
}

class Laptop extends Computer {
    public static function class() : static {
        return new static();
    }
}

echo Laptop::start();

?>
```

Listing 11.28 Return Typing with "static" ("static_return.php")

The output returns the name of the called class with the appended string:

Laptop is started.

### 11.3.7 Abstract Classes

Abstract classes and methods are very similar to interfaces. Here too, an abstract method is not implemented in the abstract class, but only specified. The abstract class itself cannot be instantiated. The methods are only implemented in the class that uses the abstract class.

```php
<?php
abstract class Computer {
    abstract function start();
}

class Laptop extends Computer {
    public function start() {
        return "Laptop is started";
    }
}

$MyLaptop = new Laptop();

echo $MyLaptop->start();

?>
```

Listing 11.29 Abstract Classes ("abstract.php")
