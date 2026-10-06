# Part III: Using PHP Practice

The second DocBlock describes the Car class itself:

```
/**
 * Represents a real-world automobile
 *
 * This class represents an automobile. The automobile can have
 * a specified color, manufacturer, and method.
 * to accelerate and slow down the car, as well as retrieve the
 * car's current speed.
 *
 * @package CarSimulator
 */
```

As with the previous DocBlock, this DocBlock contains a short description, a long description, and a @package tag to specify the package that it belongs to.

Within the class, a separate DocBlock describes each property and method. For example, the private $speed_property is documented as follows:

```
/**
 * var string The current speed of the car
 * @access private
 */
private $speed = 0;
```

The @var tag lets you specify the data type of the variable. Because PHP is loosely typed, this is a useful way to remind yourself (and other developers) of each variable's intended type.

Also note that the $speed_property's DocBlock has an @access private tag. This tells phpDocumentor that the property is private, and shouldn't be included in the standard documentation.

> You can use the --paraseprivate option to make phpDocumentor document code too. This is useful if you need to produce documentation for developers who are modifying your classes, rather than just working with them.

Here is the getSpeed() method's DocBlock:

```
/**
 * Returns the car's speed
 * Returns the current speed of the vehicle, in miles per hour
 * @return int The car's speed in mph
 */
public function getSpeed() {
    return $this->speed;
}
```

This DocBlock contains a short description, a long description, and a @return tag. This tag describes the return value from the method, and specifies its data type.

Try browsing the documentation pages you generated earlier to see how each of these DocBlocks affects phpDocumentor's output.