The value of the `callback` function parameter takes one of three forms:

+   - `string $functionName` — A string corresponding to the name of the procedural function to be called
+   - `array(object $object, string $functionName)` — An array consisting of an instantiated object and a string corresponding to the name of the method to be called on that object
+   - `array(string $className, string $functionName)` — An array consisting of the name of a class and a string corresponding to the name of a `static` method of that class

Here are a few examples of using this function:

```
<?php

class Bar {

private $_foo;

public function __construct($fooVal) {
$this->_foo = $fooVal;
}

public function printFoo() {
print $this->_foo;
}

public static function sayHello($name) {
print "Hello there, $name!";
}

}

//procedural function - not part of the Bar class
function printCount($start, $end) {
for($x = $start; $x <= $end; $x++) {
print "$x ";
}
}

/* ex. 1 */
/*prints 1 2 3 4 5 6 7 8 9 10 */
call_user_func('printCount', 1, 10);

/* ex. 2 */
/*calls $objBar->printFoo() */
$objBar = new Bar('elephant');
call_user_func(array($objBar, 'printFoo'));

/* ex. 3 */
/*calls Bar::sayHello('Steve')
```