
For example, the `Car` class might indicate merely that cars should have a color, whereas a specific `myCar` object might be colored red.

The distinction between classes and objects is often confusing to those new to OOP. It helps to think of classes as something you create as you design your application, whereas objects are created and used when the application is actually run.

## Properties

In OOP terminology, the characteristics of a class or object are known as its *properties*. Properties are much like regular variables, in that they have a name and a value (which can be of any type). Some properties allow their value to be changed and others do not. For example, the `Car` class might have properties such as `color` and `weight`. Although the color of the car can be changed by giving it a new paint job, the weight of the car (without cargo or passengers) is a fixed value.

## Methods

The behaviors of a class — that is, the actions associated with the class — are known as its *methods*. Methods are very similar to functions; in fact, you define methods in PHP using the `function` statement.

Like functions, some methods act on external data passed to them as arguments, but an object’s method can also access the properties of the object. For example, an `accelerate` method of the `Car` class might check the `fuel` property to make sure it has enough fuel to move the car. The method might then update the object’s `velocity` property to reflect the fact that the car has accelerated.

The methods of a class, along with its properties, are collectively known as *members of the class*.

## Creating Classes and Objects in PHP

Although the theory behind classes and objects can get quite involved, classes and objects are actually really easy to create in PHP. As you’d imagine, you need to create a class before you create an object belonging to that class. To create a class, you use PHP’s `class` keyword. Here’s a really simple class:

```
class Car {
// Nothing to see here; move along
}
```

This code simply defines a class called `Car` that does nothing whatsoever — it merely includes a comment. (You add some functionality to the class shortly.) Notice that a class definition consists of the `class` keyword, followed by the name of the class, followed by the code that makes up the class, surrounded by curly brackets ({ }).

*A common coding standard is to begin a class name with a capital letter, though you don’t have to do this. The main thing is to be consistent. You can find out more about coding standards in Chapter 20.*

Now that you’ve defined a class, you can create objects based on the class. To create an object, you use the `new` keyword, followed by the name of the class that you want to base the object on. You can then assign this object to a variable, much like any other value.

Here’s an example that shows how to create objects:

```
class Car {
// Nothing to see here; move along
}

$beetle = new Car();
$mustang = new Car();

print_r( $beetle ); // Displays "Car Object ( )"
print_r( $mustang ); // Displays "Car Object ( )"
```

This code first defines the empty `Car` class as before, then creates two new instances of the `Car` class — that is, two `Car` objects. It assigns one object to a variable called `$beetle`, and another to a variable called `$mustang`. Note that, although both objects are based on the same class, they are independent of each other, and each is stored in its own variable.

Once the objects have been created, their contents are displayed using `print_r()`. You’ll remember from Chapter 6 that `print_r()` can be used to output the contents of arrays. It can also be used to output objects, which is very handy for debugging object-oriented code. In this case, the `Car` class is empty, so `print_r()` merely displays the fact that the objects are based on the `Car` class.

> In Chapter 7, you learned how PHP passes variables to and from functions by value, and assigns them to other variables by value, unless you explicitly tell it to pass them or assign them by reference. The exception to this rule is objects, which are always passed by reference.

## Creating and Using Properties

Now that you know how to create a class, you can start adding properties to it. Class properties are very similar to variables; for example, an object’s property can store a single value, an array of values, or even another object.

## Understanding Property Visibility

Before diving into creating properties in PHP, it’s worth taking a look at an important concept of classes known as _visibility_. Each property of a class in PHP can have one of three visibility levels, known as public, private, and protected:

- Public properties can be accessed by any code, whether that code is inside or outside the class. If a property is declared public, its value can be read or changed from anywhere in your script.
- Private properties of a class can be accessed only by code inside the class. So if you create a property that’s declared private, only methods inside the same class can access its contents. (If you attempt to access the property outside the class, PHP generates a fatal error.)
- Protected class properties are a bit like private properties in that they can’t be accessed by code outside the class, but there’s one subtle difference: any class that inherits from the class can also access the properties. (You learn about inheritance later in the chapter.)

Generally speaking, it’s a good idea to avoid creating public properties wherever possible. Instead, it’s safer to create private properties, then to create methods that allow code outside the class to access those properties. This means that you can control exactly how your class’s properties are accessed. You learn more about this concept later in the chapter. In the next few sections, though, you work mostly with public properties, because these are easiest to understand.

## Declaring Properties

To add a property to a class, first write the keyword public, private, or protected — depending on the visibility level you want to give to the property — followed by the property’s name (preceded by a $ symbol):

```
class MyClass {
    public $property1;     // This is a public property
    private $property2;    // This is a private property
    protected $property3;  // This is a protected property
}
```

By the way, you can also initialize properties at the time that you declare them, much like you can with variables:

```
class MyClass {
    public $widgetsSold = 123;
}
```

In this case, whenever a new object is created from MyClass, the object’s $widgetsSold property defaults to the value 123.

## Accessing Properties

Once you’ve created a class property, you can access the corresponding object’s property value from within your calling code by using the following syntax:

```
$object->property;
```

That is, you write the name of the variable storing the object, followed by an arrow symbol composed of a hyphen (-) and a greater-than symbol (>), followed by the property name. (Note that the property name doesn’t have a $ symbol before it.)

Here's an example that shows how to define properties then set and read their values:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Defining and Using Object Properties</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Defining and Using Object Properties</h1>

<?php
class Car {
public $color;
public $manufacturer;
}

$beetle = new Car();
$beetle->color = "red";
$beetle->manufacturer = "Volkswagen";

$mustang = new Car();
$mustang->color = "green";
$mustang->manufacturer = "Ford";

echo "<h2>Some properties:</h2>";
echo "<p>The Beetle's color is " . $beetle->color . ".</p>";
echo "<p>The Mustang's manufacturer is " . $mustang->manufacturer . ".</p>";
echo "<h2>The $beetle Object:</h2><pre>";
print_r( $beetle );
echo "</pre>";
echo "<h2>The $mustang Object:</h2><pre>";
print_r( $mustang );
echo "</pre>";
?>
</body>
</html>
```

You can see the output from this script in Figure 8-1. The script defines a class, Car, with two public properties, $color and $manufacturer. Then it creates a new Car object and assigns it to a variable called $beetle, and sets $beetle’s $color and $manufacturer properties to "red" and "Volkswagen", respectively. Next the script creates another Car object, assigns it to $mustang, and sets its $color property to "green" and its $manufacturer property to "Ford".

Now that the two objects have been created and their properties set, the script displays the values of a couple of properties: the $color property of the $beetle object ($beetle->color) and the $manufacturer property of the $mustang object ($mustang->manufacturer). Finally, the script uses print_r() to display the two objects; notice how print_r() displays an object’s properties in much the same way as it displays array keys and values.
