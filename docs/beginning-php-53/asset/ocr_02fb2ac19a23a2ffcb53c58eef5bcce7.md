Within the `Car` class, a static property, `$numberSold`, is declared and also initialized to `123`. Then, outside the class definition, the static property is incremented and its new value, `124`, is displayed.

Static properties are useful when you want to record a persistent value that’s relevant to a particular class, but that isn’t related to specific objects. You can think of them as global variables for classes. The nice thing about static properties is that code outside the class doesn’t have to create an instance of the class — that is, an object — in order to access the property.

# Class Constants

You learned in Chapter 3 that you can create constants — special identifiers that hold fixed values throughout the running of your script. PHP also lets you create constants within classes. To define a class constant, use the keyword `const`, as follows:

```
class MyClass {
    const MYCONST = 123;
}
```

As with normal constants, it’s good practice to use all-uppercase letters for class constant names.

Like static properties, you access class constants via the class name and the `::` operator:

```
echo MyClass::MYCONST;
```

Class constants are useful whenever you need to define a fixed value, or set a configuration option, that’s specific to the class in question. For example, for the `Car` class you could define class constants to represent various types of cars, then use these constants when creating `Car` objects:

```
class Car {
    const HATCHBACK = 1;
    const STATION_WAGON = 2;
    const SUV = 3;

    public $model;
    public $color;
    public $manufacturer;
    public $type;
}

$myCar = new Car;
$myCar->model = "Dodge Caliber";
$myCar->color = "blue";
$myCar->manufacturer = "Chrysler";
$myCar->type = Car::HATCHBACK;

echo "This $myCar->model is a ";
switch ( $myCar->type ) {
    case Car::HATCHBACK:
        echo "hatchback";
        break;
```