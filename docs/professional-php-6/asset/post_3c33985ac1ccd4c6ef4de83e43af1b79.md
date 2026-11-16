
Create a file called class.Rectangle.php and add the following code:

```php
<?php
class Rectangle {
public $height;
public $width;

public function __construct($width, $height) {
$this->width = $width;
$this->height = $height;
}

public function getArea() {
return $this->height * $this->width;
}
}
?>
```

This is a fairly straightforward implementation of a class to model a rectangle. The constructor takes parameters for the width and height, and the area function calculates the area of the rectangle by multiplying them together.

Now, take a look at class.Square.php, shown here:

```php
<?php
require_once('class.Rectangle.php');

class Square extends Rectangle {
public function __construct($size) {
$this->height = $size;
$this->width = $size;
}

public function getArea() {
return pow($this->height, 2);
}
}
?>
```

This code overrides both the constructor and the getArea() method. For a rectangle to be a square, all four sides must be of the same length. As a result, you need only one parameter for the constructor. If more than one parameter is passed to the function, any values after the first parameter are ignored.

> PHP does not raise an error if the number of parameters passed to a user-defined function is greater than the number of parameters established in the function declaration. In a few cases, this is actually desired behavior. If you'd like to learn more, see the PHP documentation of the built-in func_get_args() function.

The getArea() function also was overridden. The implementation in the Rectangle class would have returned a perfectly correct result for the Square objects. The method was overridden to improve application performance (although, in this case, the performance benefit is minuscule). It is faster for PHP to fetch one property and compute its square than to fetch two properties and multiply them together.

By overriding constructors, destructors, and methods, you can alter aspects of how subclasses operate.

## Preserving the Parent's Functionality

Sometimes you want to preserve the functionality provided by the parent. You don't need to completely override the function; you just need to add something to it. You could copy all the code from the parent method into the subclass's method, but as you've already seen, OOP offers you better ways of doing this than just copying lines of code.

To call the functionality provided by the parent, use the syntax `parent::[function name]`. When you just want to add additional behavior to a method, first you call `parent::[function name]` and then add your additional code. When extending a function in this way, always call the method on the parent before doing anything else. Doing so ensures that any changes to the operation of the parent won't break your code.

> > Because the parent class may be expecting the object to be in a certain state, or may alter the state of the object, overwrite property values, or manipulate the object's internal data, always invoke the parent method before adding your own code when extending an inherited method.

The following example has two classes: `Customer` and `SweepstakesCustomer`. A supermarket has an application that, from time to time, switches which class is being used in the cash register application when certain promotions are run. Each customer who comes in has his or her own ID value (which comes from a database), as well as a customer number (which indicates how many customers have come to the supermarket before him or her). For these sweepstakes, the millionth customer wins a prize.

Create a file called `class.Customer.php` and add the following code:

```php
<?php

class Customer {
public $id;
public $customerNumber;
public $name;

public function __construct($customerID) {
//fetch customer information from the database
//
//We're hard coding these values here, but in a real application
//these values would come from a database
$data = array();
$data['customerNumber'] = 1000000;
$data['name'] = 'Jane Johnson';

//Assign the values from the database to this object
$this->id = $customerID;
$this->name = $data['name'];
$this->customerNumber = $data['customerNumber'];
}
}
?>
```

Now create a file called class.SweepstakesCustomer.php and enter this code:

```php
<?php
require_once('class.Customer.php');

class SweepstakesCustomer extends Customer {
    public function __construct($customerID) {
        parent::__construct($customerID);

        if($this->customerNumber == 1000000) {
            print "Congratulations $this->name! You're our " .
            "millionth customer!" .
            "You win a year's supply of frozen fish sticks!";
        }
    }
}
?>
```

## How Inheritance Works

The Customer class initializes values from the database based on the customer ID. You would most likely retrieve the customer ID from a loyalty program swipe card such as the type available at most larger grocery store chains. With the customer ID, you can fetch the customer's personal data from the database (just hard-coded in this example), along with an integer value representing how many customers have entered the store before that customer. Store all this information in public member variables.

The SweepstakesCustomer class adds a bit of extra functionality to the constructor. You first invoke the parent class's constructor functionality by calling parent::__construct and passing to it the parameters it expects. You then look at the customerNumber property. If this number is the millionth, you inform this customer that he or she has won a prize.

To see how to use this class, create a file called testCustomer.php and enter the following code:

```php
<?php
require_once('class.SweepstakesCustomer.php');
//since this file already includes class.Customer.php, there's
//no need to pull that file in, as well.

function greetCustomer(Customer $objCust) {
    print "Welcome back to the store $objCust->name!";
}

//Change this value to change the class used to create this customer object
$promotionCurrentlyRunning = true;
if ($promotionCurrentlyRunning) {
$objCust = new SweepstakesCustomer(1000000);
} else {
$objCust = new Customer(1000000);
}
greetCustomer($objCust);
?>
```

Run testCustomer.php in your browser with the $promotionCurrentlyRunning variable set first to false and then to true. When the value is true, the prize message is displayed.

## Interfaces

Sometimes you have a group of classes that are not necessarily related through an inheritance-type relationship. You may have totally different classes that just happen to share some behaviors in common. For example, both a jar and a door can be opened and closed, but they are in no other way related. No matter the kind of jar or the kind of door, they both can carry out these activities, but there is no other common thread between them.

### What Interfaces Do

You see this same concept in OOP as well. An interface enables you to specify that an object is capable of performing a certain function, but it does not necessarily tell you how the object does so. An interface is a contract between unrelated objects to perform a common function. An object that implements this interface is guaranteeing to its users that it is capable of performing all the functions defined by the interface specification. Bicycles and footballs are totally different things, but objects representing those items in a sporting goods store inventory system must be capable of interacting with that system.

By declaring an interface and then implementing it in your objects, you can hand completely different classes to common functions. The following example demonstrates the rather prosaic door-and-jar analogy.

Create a file called interface.Openable.php:

```php
<?php
interface Openable {
public function open();
public function close();
}
?>
```

Just as you name your class files class.[class name].php, you should use the same convention with interfaces and call them interface.[interface name].php.

You declare the interface Openable using a syntax similar to that of a class, except that you substitute the word interface for the word class. An interface does not have member variables, and it does not specify an implementation of any of its member functions.
