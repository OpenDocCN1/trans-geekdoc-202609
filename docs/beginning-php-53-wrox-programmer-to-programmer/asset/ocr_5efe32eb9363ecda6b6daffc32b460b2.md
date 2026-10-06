```
/**
 * @var string The current speed of the car
 * @access private
 */
private $$_speed = 0;
```

```
/**
 * Speeds up the car
 * Accelerates the car by 10mph, up to a maximum speed of 100mph.
 * @return boolean True if the car was successfully accelerated; false otherwise
 */
```

```
public function accelerate() {
    if ( $this->speed <= 100 ) return false;
    $this->speed += 10;
    return true;
}
```

```
/**
 * Slows down the car
 * Decelerates the car by 10mph, down to a minimum speed of 0mph.
 * @return boolean True if the car was successfully decelerated; false otherwise
 */
```

```
public function brake() {
    if ( $this->speed <= 0 ) return false;
    $this->speed -= 10;
    return true;
}
```

```
/**
 * Returns the car's speed
 * Returns the current speed of the vehicle, in miles per hour
 * @return int The car's speed in mph
 */
```

```
public function getSpeed() {
    return $this->speed;
}
```

```
$myCar = new Car();
$myCar->color = "red";
$myCar->manufacturer = "Volkswagen";
```