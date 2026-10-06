```
public function setColor($color ) {
    $this->_color = $color;
}
```

```
public function isFilled() {
    return $this->_filled;
}
```

```
public function fill() {
    $this->_filled = true;
}
```

```
public function makeHollow() {
    $this->_filled = false;
}
```

```
abstract public function getArea();
```

You now use the ShapeInfo class with any class that is derived from the Shape class, safe in the knowledge that the child class implements getArea().

So when the programmer attempts to add his Rectangle class without the getArea() method, it generates an error:

Class Rectangle contains 1 abstract method and must therefore be declared abstract or implement the remaining methods (Shape::getArea)

This should be enough to remind the programmer to add the required getArea() method to the class:

```
class Rectangle extends Shape {
    private $_width = 0;
    private $_height = 0;
```

```
public function getWidth() {
    return $this->_width;
}
```

```
public function getHeight() {
    return $this->_height;
}
```

```
public function setWidth($width ) {
    $this->_width = $width;
}
```

```
public function setHeight($height ) {
    $this->_height = $height;
}
```