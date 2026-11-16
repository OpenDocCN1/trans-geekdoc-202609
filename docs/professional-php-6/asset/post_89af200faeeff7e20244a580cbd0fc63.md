
- Interfaces — A way of specifying that an object is capable of doing something without actually defining how it is to be done (e.g., a dog and a human are “things that walk,” but they do it very differently)
- Encapsulation — The ability of an object to protect access to its internal data

If any of these terms seem difficult to understand, don’t worry. The material that follows will clarify everything. Your newfound knowledge may even completely change the way you approach your software development projects.

## Classes

In the real world, objects have characteristics and behaviors. A car has a color, a weight, a manufacturer, and a gas tank of a certain volume. Those are its characteristics. A car can accelerate, stop, signal for a turn, and sound the horn. Those are its behaviors. Those characteristics and behaviors are common to all cars. Although two particular cars in the same parking lot may have different colors, all cars have a color. Using a construct known as a class, OOP enables you to establish the idea of a car as being something with all those characteristics. A class is a unit of code (composed of variables and functions) that describes the characteristics and behaviors of all the members of a set. A class called Car would describe the properties and methods common to all cars.

In OO terminology, the characteristics of a class are known as its properties. Properties have a name and a value. Some allow their value to be changed; others do not. For example, in the Car class, you would probably have such properties as color and weight. Although the color of the car can be changed by giving it a new paint job, the tare weight of the car (without cargo or passengers) is a fixed value.

Some properties represent the state of the object. State refers to those characteristics that change because of certain events but are not necessarily directly modifiable on their own. In an application that simulates vehicle performance, the Car class might have a property called velocity. The velocity of the car is not a value that can be changed on its own, but rather is a by-product of the amount of fuel being sent to the engine, the performance characteristics of that engine, and the terrain over which the car is traveling.

The behaviors of a class are known as its methods. Methods of classes are syntactically equivalent to functions found in traditional procedural code. Just like functions, methods can accept any number of parameters, each of any valid data type. Some methods act on external data passed to them as parameters, but they can also act on the properties of their object, either using those properties to inform actions made by the method (such as when a method called accelerate examines the remaining amount of fuel to determine whether the car is capable of accelerating) or to change the state of the object by modifying values such as the velocity of the car.

## Objects

To begin with, you can think of a class as a blueprint for constructing an object. In much the same way that many houses can be built from the same blueprint, you can build multiple instances of an object from its class; but the blueprint doesn’t specify details such as the color of the walls or the type of flooring. It merely specifies that those things will exist. Classes work much the same way. The class specifies the behaviors and characteristics the object will have, but not necessarily the values of those characteristics. An object is a concrete entity constructed using the blueprint provided by a class. The idea of a house is analogous to a class. Your house (a specific instance of the idea of a house) is analogous to an object.

With a blueprint in hand and some building materials, you can construct a house. In OOP, when you use the class to build an object, this process is known as instantiation. Instantiating an object requires two things:

- A memory location into which to load the object. This is automatically handled for you by PHP.
- The data that will populate the values of the properties. This data can come from a database, a flat text file, another object, or some other source.

A class can never have property values or state. Only objects can. You must use the blueprint to build the house before you can give it wallpaper or vinyl siding. Similarly, you must instantiate an object from the class before you can interact with its properties or invoke its methods. Classes are manipulated at design time when you make changes to the methods or properties. Objects are manipulated at run-time when values are assigned to their properties, and their methods are invoked. The problem of when to use the word class and when to use the word object is something that often confuses those new to OOP.

After an object is instantiated, it can be put to work implementing the business requirements of the application. Let’s look at exactly how to do that in PHP.

## Creating a Class

Starting with a simple example, save the following in a file called class.Demo.php:

```php
<?php
class Demo {
}
?>
```

There you have it — the Demo class. Although not terribly exciting just yet, this is the basic syntax for declaring a new class in PHP. Use the keyword class to let PHP know you’re about to define a new class. Follow that with the name of the class and braces to indicate the start and end of the code for that class.

It’s important to have a clearly defined convention for organizing your source code files. A good rule to follow is to put each class into its own file and to name that file class.[ClassName].php.

You can instantiate an object of type Demo like this:

```php
<?php
require_once( 'class.Demo.php' );

$objDemo = new Demo();
?>
```

To instantiate an object, first ensure that PHP knows where to find the class declaration by including the file containing your class (class.Demo.php in this example); then invoke the new operator and supply the name of the class, followed by opening and closing parentheses. The return value of this statement is assigned to a new variable, $objDemo in this example. Now you can invoke the $objDemo object's methods and examine or set the value of its properties — if it actually has any.

Even though the class you've created doesn't do much of anything just yet, it's still a valid class definition.

## Adding a Method

The Demo class isn't particularly useful if it isn't able to do anything, so let's look at how you can create a method. Remember, a method of a class is basically just a function. By coding a function inside the braces of your class, you're adding a method to that class. Here's an example:

```php
<?php

class Demo {
    function sayHello($name) {
        print "Hello $name!";
    }
}

?>
```

An object derived from your class is now capable of printing a greeting to anyone who invokes the sayHello method. To invoke the method on your $objDemo object, you need to use the operator -> to access the newly created function:

```php
<?php

require_once('class.Demo.php');

$objDemo = new Demo();

$objDemo->sayHello('Steve');

?>
```

The object is now capable of printing a friendly greeting. The -> operator is used to access all methods and properties of your objects.

> For readers who have had exposure to OOP in other programming languages, note that the -> operator is always used to access the methods and properties of an object. PHP does not use the dot operator (.) in its OO syntax at all.

## Adding a Property

Adding a property to your class is just as easy as adding a method. You simply declare a variable inside the class to hold the value of the property. In procedural code, when you want to store some value, you assign that value to a variable. In OOP, when you want to store the value of a property, you also use a variable. This variable is declared at the top of the class declaration, inside the braces that bracket the class's code. The name of the variable is the name of the property. If the variable is called $color, you will have a property called color.

Open the class.Demo.php file and add the following highlighted code:

```php
<?php
class Demo {
  public $name;
  function sayHello() {
    print "Hello $this->name!";
  }
}
?>
```

This new variable, called $name, is all you have to do to create a property of the Demo class called name. To access this property, you use the same -> operator as that of the previous example, along with the name of the property. The rewritten sayHello method shows how to access the value of this property.

Create a new file called testdemo.php and add the following:

```php
<?php
require_once('class.Demo.php');
$objDemo = new Demo();
$objDemo->name = 'Steve';
$objAnotherDemo = new Demo();
$objAnotherDemo->name = 'Ed';
$objDemo->sayHello();
$objAnotherDemo->sayHello();
?>
```

Save the file and then open it in your Web browser. The strings “Hello Steve!” and “Hello Ed!” print to the screen.

The keyword public is used to let the class know that you want to have access to the following variable from outside the class. Some member variables of the class exist only for use by the class itself and should not be accessible to external code; these variables are declared as private or protected (more on that later). In this example, you want to be able to set and retrieve the value of the property name. Note that the way the sayHello method works has changed. Instead of taking a parameter, it now fetches the name value from the property.

You use the variable $this so that the object can get information about itself. You might have multiple objects of a class, for example, and because you don't know in advance what the name of an object variable will be, the $this variable enables you to refer to the current instance.
