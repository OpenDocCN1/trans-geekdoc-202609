```
<?php
require_once "Shape.php";

// Definition of a concrete class that extends the abstract class
class Rectangle extends Shape {
    private $length;
    private $width;

    public function __construct($length, $width) {
        $this->length = $length;
        $this->width = $width;
    }

    // Implementation of the abstract method calculSurface
    public function calculateArea() {
        return $this->length * $this->width;
    }
}
```

In this code, we define a Rectangle class that extends the abstract Shape class. This means that the Rectangle class inherits all the abstract methods of the Shape class and must implement them.

The Rectangle class has two private properties, $length and $width, which represent the dimensions of the