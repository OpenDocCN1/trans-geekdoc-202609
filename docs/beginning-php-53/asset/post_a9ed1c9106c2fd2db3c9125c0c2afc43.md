
The wonderful thing about inheritance is that, if you want to create a lot of similar classes, you have to write the code that they have in common only once, in the parent class. This saves you from duplicating code. Furthermore, any outside code that can work with the parent class automatically has the ability to work with its child classes, provided the code works only with the properties and methods contained in the parent class.

Imagine that you’re creating a program to deal with various regular shapes, such as circles, squares, equilateral triangles, and so on. You want to create a Shape class that can store information such as number of sides, side length, radius, and color, and that can calculate values such as the shape’s area and perimeter. However, not all shapes are the same. Circles don’t really have a clearly defined number of sides, and you calculate an equilateral triangle’s area using a different formula than for a square. So if you wanted to handle all types of regular shapes in a single Shape class, your class’s code would get quite complicated.

By using inheritance, however, you can break the problem down into simpler steps. First, you create a parent Shape class that contains just those properties and methods that are common to all shapes. Then, you can create child classes such as Circle, Square, and Triangle that inherit from the Shape class.

To create a child class that’s based on a parent class, you use the `extends` keyword, as follows:

```
class Shape {
  // (General Shape properties and methods here)
}

class Circle extends Shape {
  // (Circle-specific properties and methods here)
}
```

## Try It Out Create a Parent Class and Child Classes

The following script shows inheritance in action. It creates a parent Shape class, holding properties and methods common to all shapes, then creates two child classes based on Shape — Circle and Square — that contain properties and methods related to circles and squares, respectively.

Save the script as inheritance.php in your document root folder, then run the script in your Web browser. You should see the page shown in Figure 8-5.

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Creating Shape Classes using Inheritance</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Creating Shape Classes using Inheritance</h1>

<?php
class Shape {
private $_color = "black";
private $_filled = false;

public function getColor() {
return $this->_color;
}

public function setColor( $_color ) {
$this->_color = $_color;
}

public function isFilled() {
return $this->_filled;
}

public function fill() {
$this->_filled = true;
}

public function makeHollow() {
$this->_filled = false;
}
}

class Circle extends Shape {
private $_radius = 0;

public function getRadius() {
return $this->_radius;
}

public function setRadius( $_radius ) {
$this->_radius = $_radius;
}

public function getArea() {
return M_PI * pow( $this->_radius, 2 );
}
}

class Square extends Shape {
private $_sideLength = 0;

public function getSideLength() {
return $this->_sideLength;
}

public function setSideLength( $length ) {
$this->_sideLength = $length;
}

public function getArea() {
    return pow( $this->_sideLength, 2 );
}
}

$myCircle = new Circle;
$myCircle->setColor( "red" );
$myCircle->fill();
$myCircle->setRadius( 4 );
echo "<h2>My Circle</h2>";
echo "<p>My circle has a radius of " . $myCircle->getRadius() . ".</p>";
echo "<p>It is " . $myCircle->getColor() . " and it is " . ( $myCircle->isFilled() ? "filled" : "hollow" ) . ".</p>";
echo "<p>The area of my circle is: " . $myCircle->getArea() . ".</p>";

$mySquare = new Square;
$mySquare->setColor( "green" );
$mySquare->makeHollow();
$mySquare->setSideLength( 3 );
echo "<h2>My Square</h2>";
echo "<p>My square has a side length of " . $mySquare->getSideLength() . ".</p>";
echo "<p>It is " . $mySquare->getColor() . " and it is " . ( $mySquare->isFilled() ? "filled" : "hollow" ) . ".</p>";
echo "<p>The area of my square is: " . $mySquare->getArea() . ".</p>";

?>

</body>
</html>
```

![](img/1ddec54918a4802eb9b4febec3d4e7f6_232_0.png)

## Figure 8-5

## How It Works

The script first creates the parent `Shape` class. This class contains just the properties and methods common to all shapes. It contains private properties to store the shape’s color and record whether the shape is filled or hollow, then provides public accessor methods to get and set the color, as well as fill the shape or make it hollow and retrieve the shape’s fill status.

Next, the script creates a `Circle` class that inherits from the `Shape` class. Remember that a child class inherits all the properties and methods of its parent. The `Circle` class also adds a private property to store the circle’s radius, and provides public methods to get and set the radius, as well as calculate the area from the radius using the formula πr².

The script then creates `Square`, another class that inherits from `Shape`. This time, the class adds a private property to track the length of one side of the square, and provides methods to get and set the side length and calculate the square’s area using the formula (side length)².

Finally, the script demonstrates the use of the `Circle` and `Square` classes. First it creates a new `Circle` object, sets its color, fills it, and sets its radius to 4. It then displays all the properties of the circle, calculates its area using the `getArea()` method of the `Circle` class. Notice how the script calls some methods that are in the parent `Shape` class, such as `setColor()` and `isFilled()`, and some methods that are in the child `Circle` class, such as `setRadius()` and `getArea()`.

The script then repeats the process with the `Square` class, creating a hollow green square with a side length of 3, then displaying the square’s properties and calculating its area using the `Square` class’s `getArea()` method.

## Overriding Methods in the Parent Class

What if you want to create a child class whose methods are different from the corresponding methods in the parent class? For example, you might create a class called `Fruit` that contains methods such as `peel()`, `slice()`, and `eat()`. This works for most fruit; however, grapes, for example, don’t need to be peeled or sliced. So you might want your `Grape` object to behave somewhat differently to the generic `Fruit` object if you try to peel or slice it.

PHP, like most object-oriented languages, lets you solve such problems by _overriding_ a parent class’s method in the child class. To do this, simply create a method with the same name in the child class. Then, when that method name is called for an object of the child class, the child class’s method is run instead of the parent class’s method:

```
class ParentClass {
   public function someMethod() {
      // (do stuff here)
   }
}
```

```
class ChildClass extends ParentClass {
   public function someMethod() {
      // This method is called instead for ChildClass objects
   }
}
```

```
$parentObj = new ParentClass();
$parentObj->someMethod(); // Calls ParentClass::someMethod()
$childObj = new ChildClass();
$childObj->someMethod(); // Calls ChildClass::someMethod()
```

Notice that the parent class's method is called when accessed from an object of the parent class, and the child class's method is called when using an object of the child class.

The following example code shows how you can use inheritance to distinguish grapes from other fruit:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Overriding Methods in the Parent Class</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Overriding Methods in the Parent Class</h1>

<?php
class Fruit {
public function peel() {
echo "<p>I'm peeling the fruit...</p>";
}

public function slice() {
echo "<p>I'm slicing the fruit...</p>";
}

public function eat() {
echo "<p>I'm eating the fruit. Yummy!</p>";
}

public function consume() {
$this->peel();
$this->slice();
$this->eat();
}
}

class Grape extends Fruit {
public function peel() {
echo "<p>No need to peel a grape!</p>";
}

public function slice() {
echo "<p>No need to slice a grape!</p>";
}
}
```
