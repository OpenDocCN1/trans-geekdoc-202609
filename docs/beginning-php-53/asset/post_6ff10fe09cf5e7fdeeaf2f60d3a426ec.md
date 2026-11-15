
echo "</p><p>Top speed! Slowing down...<br />";
while ( $myCar->brake() ) {
    echo "Current speed: " . $myCar->getSpeed() . " mph<br />";
}
echo "</p><p>Stopped!</p>";
?>
</body>
</html>

![](img/1ddec54918a4802eb9b4febec3d4e7f6_215_0.png)

Figure 8-2

## How It Works

This script adds some useful behaviors to the `car` class in the form of three methods:

- `accelerate()` speeds up the car by 10 mph, returning `true` if successful. If the car is already at top speed — 100 mph — the car isn't accelerated any further, and `accelerate()` returns `false`
- `brake()` does the opposite of `accelerate()` — it decreases speed by 10 mph, returning `true` if successful, or `false` if the car is stationary
- `getSpeed()` simply returns the car’s current speed, in mph

The script then creates an instance of the Car class — the $myCar object — and sets its public properties to reflect a specific car (a red Volkswagen Beetle). Finally, the script displays these properties, then runs through a couple of loops, accelerating the car to top speed then decelerating back down to zero mph, and displaying the current speed as it goes by using the getSpeed() method.

Notice that the Car class contains a private property, $speed. This is good OOP practice, because you should keep an object’s data and behaviors private unless they absolutely need to be publicly available. In this case, you don’t want outside code to be able to directly read or modify the car’s speed; instead the calling code should use the three methods you created. For this reason, it makes sense for $speed to be private.

Incidentally, the underscore at the start of the $speed variable name is a common coding practice used to indicate private properties and methods. You don’t have to use this convention, but it can make it easier to identify private class members at a glance.

## Static Methods

PHP lets you create static methods in much the same way as static properties. To make a method static, add the static keyword before the function keyword in the method definition:

```
class MyClass {
    public static function staticMethod() {
        // (do stuff here)
    }
}
```

To call a static method, write the class name, followed by two colons, followed by the method name and the arguments (if any) in parentheses:

```
MyClass::staticMethod();
```

As with static properties, static methods are useful when you want to add some functionality that’s related to a class, but that doesn’t need to work with an actual object created from the class. Here’s a simple example:

```
class Car {

    public static function calcMpg( $miles, $gallons ) {
        return ( $miles / $gallons );
    }

}

echo Car::calcMpg( 168, 6 ); // Displays "28"
```

The calcMpg() method takes two arguments — miles traveled and gallons of fuel used — and returns the calculated miles per gallon. The method is then tested by calling it with some sample figures and displaying the result.

Unlike the accelerate(), brake(), and getSpeed() methods you created in the car_simulator.php example earlier, the calcMpg() method doesn't depend on an actual object to do its job, so it makes sense for it to be static. Notice that the calling code doesn't need to create a Car object to use calcMpg().

If you need to access a static method or property, or a class constant, from within a method of the same class, you can use the same syntax as you would outside the class:

```
class MyClass {
    const MYCONST = 123;
    public static $staticVar = 456;

    public function myMethod() {
        echo "MYCONST = " . MyClass::MYCONST . ", ";
        echo "\$staticVar = " . MyClass::$staticVar . "<br />";
    }
}

$obj = new MyClass;
$obj->myMethod(); // Displays "MYCONST = 123, $staticVar = 456"
```

You can also use the self keyword (much as you use $this with objects):

```
class Car {
    public static function calcMpg( $miles, $gallons ) {
        return ( $miles / $gallons );
    }

    public static function displayMpg( $miles, $gallons ) {
        echo "This car's MPG is: " . self::calcMpg( $miles, $gallons );
    }
}

echo Car::displayMpg( 168, 6 ); // Displays "This car's MPG is: 28"
```

## Using Hints to Check Method Arguments

Generally speaking, PHP doesn't care much about the types of data that you pass around. This makes PHP quite flexible, but it can cause problems that are quite hard to track down. Consider the following code:

```
class Car {
    public $color;
}

class Garage {
    public function paint( $car, $color ) {
        $car->color = $color;
    }
}

$car = new Car;
$garage = new Garage;
$car->color = "blue";
$garage->paint( $car, "green" );
echo $car->color; // Displays "green"
```

This code creates two classes: Car, with a single $color property, and Garage, with a paint() method. This method takes a Car object and a color string, and changes the car's $color property to the string provided. You can see this in action in the code after the Garage class, which creates new Car and Garage objects, sets the Car object's color to blue, then calls the Garage object's paint() method to change the car's color to green. So far so good.

However, suppose that another, somewhat naive programmer wants to use your Garage class to paint a cat, rather than a car: They create a string variable holding the name of the cat, then try to use the paint() method on it:

```
$cat = "Lucky";
$garage = new Garage;
$garage->paint( $cat, "red" ); // Error!
```

Unsurprisingly, PHP takes exception to this, generating the following warning-level error:

```
PHP Warning: Attempt to assign property of non-object
```

This is because the Garage::paint() method has attempted to change the $color property of a string, "Lucky", which is of course impossible. The error is really in the calling code — it shouldn't have passed a string as the first argument to Garage::paint() — but the script actually falls over inside the paint() method. If the paint() method was quite long, or if it in turn called other methods, it could get quite hard to track down the source of the problem.

This is where type hinting comes into play. You can use a hint to tell PHP that Garage::paint() should expect a Car object as its first argument, and reject any other type of argument. To do this, you simply place the class name before the argument name, as follows:

```
public function paint( Car $car, $color ) {
```

Now, if the same programmer tries to call the paint() method with a string instead of a Car object as the first argument, PHP gives an error similar to the following:

```
PHP Catchable fatal error: Argument 1 passed to Garage::paint() must be an instance of Car, string given, called in script.php on line 23 and defined in script.php on line 9
```

This is much more helpful, because it lets you track down the problem to the calling code, rather than wasting time looking inside the method for a bug.

By the way, you can also use type hinting with regular functions, not just methods, and you can also check that an argument is an array using hinting:

```
function showAll( array $items ) {
```

Sadly, PHP supports type hinting only for objects and arrays. Other data types, such as strings or integers, can't be checked using this technique. If you want to check for these types you'll need to use is_string(), is_int(), and so on as described in Chapter 3.

## Making Your Classes Self-Contained with Encapsulation

So far, most of the classes you've created in this chapter have contained public properties, and outside code has been able to reach into a class's innards and manipulate its public properties at will. Usually, this is a bad idea. One of the strengths of OOP is the concept of encapsulation. This means that a class's internal data should be protected from being directly manipulated from outside, and that the details of the class's implementation — such as how it stores values or manipulates data — should be hidden from the outside world. By doing this, you gain two advantages:

- You can change your class's implementation details at any time without affecting code that uses the class
- You can trust the state of an object to be valid and to make sense

Generally speaking, all internal properties of a class should be declared private. If outside code needs to access those variables, it should be done through a public method. This gives your class the opportunity to validate the changes requested by the outside code and accept or reject them.

For example, if you're building a banking application that handles details of customer accounts, you might have an Account object with a property called $totalBalance and methods called makeDeposit() and makeWithdrawal(). The only way to affect the balance should be to make a withdrawal or a deposit. If the $totalBalance property is implemented as a public property, you could write outside code that would increase the value of that variable without having to actually make a deposit. Obviously, this would be bad for the bank.

Instead, you implement this property as a private property and provide a public method called getTotalBalance(), which returns the value of that private property:

```
class Account {
private $totalBalance = 0;

public function makeDeposit( $amount ) {
$this->totalBalance += $amount;
}

public function makeWithdrawal( $amount ) {
if ( $amount < $this->totalBalance ) {
$this->totalBalance -= $amount;
}
else {
die ( "Insufficient funds<br />" );
}
}
}
```
