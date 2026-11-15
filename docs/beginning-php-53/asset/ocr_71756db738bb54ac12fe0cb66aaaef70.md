Similarly, here's how you make a final method:

```
class ParentClass {
    public $someProperty = 123;
    public final function handsOffThisMethod() {
        echo "A method";
    }
}

// Generates an error:
// "Cannot override final method ParentClass::handsOffThisMethod() "
```

```
class ChildClass extends ParentClass {
    public function handsOffThisMethod() {
        echo "Trying to override the method";
    }
}
```

You probably won't need to create final classes or methods that often; usually it's better to allow your classes to be extended, because it makes your code more flexible.

# Using Abstract Classes and Methods

Being able to create new child classes from parent classes is all very well, but things can get out of hand if a child class has radically different functionality to its parent. Sometimes it's good to be able to lay down some ground rules about how a child class should behave. Abstract classes and methods let you do just that.

To illustrate class abstraction, cast your mind back to the `Shape` class example you created earlier. Remember that you created a generic `Shape` parent class that contained some basic functionality, then extended the `Shape` class with the `Circle` and `Square` child classes.

Now, both `Circle` and `Square` contain a `getArea()` method that calculates the shape's area, regardless of the type of shape. You can use this fact to your advantage to create a generic `ShapeInfo` class that contains a method, `showInfo()`, that displays the color and area of a given shape:

```
class ShapeInfo {
    private $_shape;

    public function setShape( $shape ) {
        $this->_shape = $shape;
    }

    public function showInfo() {
        echo "<p>The shape's color is " . $this->_shape->getColor() ;
        echo ", and its area is " . $this->_shape->getArea() . "</p>";
    }
}
```