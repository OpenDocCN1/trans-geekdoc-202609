# Part II: Learning the Language

![](bbox=[0.125, 0.091, 0.773, 0.355])

# Defining and Using Object Properties

Some properties:

The Beetle's color is red.

The Mustang's manufacturer is Ford.

# The $beetle Object:

```
Car Object

[color] => red
manufacturer => Volkswagen
```

# The $mustang Object:

```
Car Object

[color] => green
manufacturer => Ford
```

Done

Figure 8-1

# Static Properties

You encountered static function variables in the previous chapter. You can also create static properties in a similar way, by adding the static keyword just before the property name:

```
class MyClass {
    public static $myProperty;
}
```

Static members of a class are independent of any particular object derived from that class. To access a static property, you write the class name, followed by two colons (:), followed by the property name (preceded by a $ symbol):

```
MyClass::$myProperty = 123;
```

Here's an example using the Car class:

```
class Car {
    public $color;
    public $manufacturer;
    static public $numberSold = 123;
}
```

```
Car::$numberSold++;
echo Car::$numberSold; // Displays "124"
```