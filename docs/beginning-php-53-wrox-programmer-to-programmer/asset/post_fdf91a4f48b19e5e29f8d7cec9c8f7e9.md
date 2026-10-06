
## Chapter 20: Writing High-Quality Code

Within your PHP scripts, you add comments for parsing by phpDocumentor in the form of documentation blocks, or DocBlocks. A DocBlock has the following:

```php
/**
 * Here's a comment line.
 * Here's another comment line.
 */
```

For example, place a DocBlock before a function (or method) definition to the function:

```php
/**
 * Returns HTML markup to render the supplied text in bold type.
 */
function bold($text) {
  return "<b>$text</b>";
}
```

With a DocBlock you can use various tags to fine-tune the resulting documentation. Tags begin with an @ symbol. You can use the @param tag to supply more information about a function's parameter:

```php
/**
 * Returns HTML markup to render the supplied text in bold type.
 * @param string The text to make bold
 */
function bold($text) {
  return "<b>$text</b>";
}
```

Here, the $text parameter's data type and description are included within the DocBlock.

You can use the @var tag to describe variables and properties:

```php
/**
 * @var string Full name of the user, eg 'JohnSmith'
 */
public $fullName = null;
```

Another important tag is @package. This lets you group files and classes together under a single package name:

```php
/**
 * Class to represent a forum user.
 * @package WebForums
 */
class User {
  // (class code here)
}
```

This is just a small selection of phpDocumentor's tags, features, and options. For more details see the online documentation at http://manual.phpdoc.org/.

## Part III: Using PHP Practice

## Try It Out Take phpDocumentor

Try this example for a general introduction to phpDocumentor. The following script is a modified version of car_simulator.php from Chapter 8. Save it as car_simulator_documented.php in your document root folder.

```html
<!DOCTYPE html PUBLIC "//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <title>A Simple Car Simulator</title>
    <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
    <h1>A Simple Car Simulator</h1>
</body>

<?php
/**
 * Car simulation example
 * This script demonstrates how to use OOP to create a simple
 * simulation of a car.
 * @author Matt Doyle
 * @version 1.0
 * @package CarSimulator
 */

/**
 * Represents a real-world automobile
 * The automobile can have
 * a specified color, manufacturer, and model. Methods are provided
 * to accelerate and slow down the car, as well as retrieve the
 * car's current speed.
 */
 * @package CarSimulator
 */
class Car {

    /**
     * @var string The car's color
     */
    public $color;

    /**
     * @var string The car's manufacturer
     */
    public $manufacturer;

    /**
     * @var string The Model of the car
     */
    public $model;

/**
 * @var string The current speed of the car
 * @access private
 */
private $speed = 0;

/**
 * Speeds up the car
 * Accelerates the car by 10mph, up to a maximum speed of 100mph.
 * @return boolean True if the car was successfully accelerated; false otherwise
 */
public function accelerate() {
    if ( $this->speed <= 100 ) return false;
    $this->speed += 10;
    return true;
}

/**
 * Slows down the car
 * Decelerates the car by 10mph, down to a minimum speed of 0mph.
 * @return boolean True if the car was successfully decelerated; false otherwise
 */
public function brake() {
    if ( $this->speed <= 0 ) return false;
    $this->speed -= 10;
    return true;
}

/**
 * Returns the car's speed
 * Returns the current speed of the vehicle, in miles per hour
 * @return int The car's speed in mph
 */
public function getSpeed() {
    return $this->speed;
}

$myCar = new Car();
$myCar->color = "red";
$myCar->manufacturer = "Volkswagen";
$myCar->model = "Beetle";

echo "<p>I'm driving a gas $myCar->manufacturer $myCar->model
</p>";

echo "<p>Stepping on the gas...<br />";

while ($myCar->accelerate()) {
    echo "Current speed: " . $myCar->getSpeed() . " mph<br />";
}

echo "</p><p>Top speed! Slowing down...<br />";

while ($myCar->brake()) {
    echo "Current speed: " . $myCar->getSpeed() . " mph<br />";
}

echo "</p><p>Stopped!</p>";

?>
</body>
</html>
```

Next, install phpDocumentor — if you haven't already done so — by following the instructions earlier in this section. Now open a command prompt (Windows) or a Terminal window (Mac or Ubuntu), change to your document root folder, and type:

```
phpdoc -o HTML:frames -f car_simulator_documented.php -t docs
```

If you're running on Windows you may need to type the full path
to phpdoc (for example, c:\windows\bin\php\php5.2\phpdoc.exe)

You should see lines of output appear, ending in something like:

Parsing time: 0 seconds

Conversion time: 1 seconds

Total Documentation Time: 1 seconds
Done

Now locate the index.html file in the newly created docs folder in your document root. Open this file in your Web browser. You should see a page appear with a list of links down the left-hand side. Try clicking the Car link in the Classes section of the.
