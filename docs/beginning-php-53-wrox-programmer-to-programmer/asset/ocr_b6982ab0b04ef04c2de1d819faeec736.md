# Part II: Learning the Language

The calcMgpg() method takes two arguments — miles traveled and gallons of fuel used — and returns the calculated miles per gallon. The method is tested by calling it with some simple examples and displaying the result.

Unlike the accelerate(), brake(), and getSpeed() methods you created in the car_simulator.php example earlier, the calcMgpg() method does not depend on an object to do its job, so it makes sense for it to be static. Notice that the calling method doesn't need to create a Car object to use calcMgpg().

If you need to access a static method or property, or a class constant, from within a method of the class, you can use the same syntax as outside the class:

```
class MyClass {
    const MYCONST = 123;
    public static $staticVar = 456;
```

```
public function myMethod() {
    echo "MYCONST = " . MyClass::MYCONST . ", " ";
    echo "$staticVar = " . MyClass::$staticVar . "<br />";
}
```

```
$obj = new MyClass;
$obj->myMethod(); // Displays MYCONST = 123, $staticVar = 456
```

You can also use the self keyword (much as you use $this with objects):

```
class Car {
    public static function calcMgpg($miles, $gallons) {
        return $miles / $gallons;
    }
```

```
public static function displayMgpg($miles, $gallons) {
    echo "This car's MPG is: " . self::calcMgpg($miles, $gallons);
}
```

```
Car::displayMgpg(168, 6); // Displays "This car's MPG is: 28"
```

# Using Hints to Check Method Arguments

Generally speaking, PHP doesn't care much about the types of data that you pass around. This makes PHP quite flexible, but it can cause problems that are quite hard to track down. Consider the following code:

```
class Car {
    public $color;
}
```

```
class Garage {
    public function paint($car, $color) {
```