To instantiate an object, first ensure that PHP knows where to find the class declaration by including the file containing your class (class.Demo.php in this example); then invoke the new operator and supply the name of the class, followed by opening and closing parentheses. The return value of this statement is assigned to a new variable, objDemo in this example. Now you can invoke the $objDemo object's methods and examine or set the value of its properties — if it actually has any.

Even though the class you've created doesn't do much of anything just yet, it's still a valid class definition.

# Adding a Method

The Demo class isn't particularly useful if it isn't able to do anything, so let's look at how you can create a method. Remember, a method of a class is basically just a function. By coding a function inside the braces of your class, you're adding a method to that class. Here's an example:

```
```php
<?php

class Demo {
    function sayHello($name) {
        print "Hello $name!";
    }
}

?>
```
```

An object derived from your class is now capable of printing a greeting to anyone who invokes the sayHello method. To invoke the method on your $objDemo object, you need to use the operator -> to access the newly created function:

```
```php
<?php

require_once('class.Demo.php');

$objDemo = new Demo();

$objDemo->sayHello('Steve');

?>
```
```

The object is now capable of printing a friendly greeting. The -> operator is used to access all methods and properties of your objects.

> For readers who have had exposure to OOP in other programming languages, note that the -> operator is always used to access the methods and properties of an object. PHP does not use the dot operator (.) in its OO syntax at all.

# Adding a Property

Adding a property to your class is just as easy as adding a method. You simply declare a variable inside the class to hold the value of the property. In procedural code, when you want to store some value, you assign that value to a variable. In OOP, when you want to store the value of a property, you also use a variable. This variable is declared at the top of the class declaration, inside the braces that bracket the