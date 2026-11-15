```
```php
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
}
```
```