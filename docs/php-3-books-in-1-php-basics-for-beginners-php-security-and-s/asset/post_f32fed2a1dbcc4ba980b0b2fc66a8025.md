
The previous example shows a simple demonstration of inheritance in PHP. Notice that each child's class inherits variables and methods from the parent "Person." In the code above, it's simple to see that the child class is a sub-class of its superclass. In this example, if a method or variable of the parent is changed, it will affect all classes derived from it.

## Importance of inheritance class
- 1. The program becomes more readable and easier to understand.
- 2. Code re-usability – inheritance enables the reuse of code.
- 3. It simplifies the system because there will be fewer classes that you need to implement and maintain.
- 4. The application becomes more flexible because it's easier to extend the functionality of existing classes.
- 5. It allows calling of parent class function from a child class function within a program.
- 6. Inheritance makes it easy for you to add comments to your code; just add the include <?php ... ?> and the above code will be added as a comment at the top of the "Child" class.
- 7. The implementation inheritance makes it easy to improve classes and re-use them.
- 8. Improves the code quality because each class contains only the specific information necessary to do its job.

## PHP Final Keyword
The word 'final' often signifies the last in a series of steps. In programming, 'final' means that no more changes can be made to that function's code after it has been called. It is also used when asking a question of the user and expecting an answer from only one particular argument, not from many different arguments. This tutorial will help you understand what the final keyword is and how it interacts with other PHP keywords like if statements, for loops, etc.

The final keyword works as a modifier in PHP, and it tells the interpreter that whatever follows the word 'final' cannot be overridden or extended in any way. Many programmers use the final keyword to describe a condition that is required for the following code to work correctly or execute on a particular condition. For example, the final keyword can be used if you need to find whether a string contains only lowercase letters or not. You could use a regular expression but doing so would end up in error because regular expressions are case insensitive. So, if you are using a final keyword, you will either have to make sure that no other code may modify the string or else make sure that the string is not modified in any way while using regular expressions.

To provide an interface for creating a concrete subclass of that abstract class. This allows you to create multiple concrete subclasses from the same abstract parent class but with different sets of variables and methods in each subclass.

For example, here we have an abstract class called Shape that has a constructor that takes a pair of integer coordinates:

```
1.2.3.4.5.6
```

The shape class contains two abstract methods named area() and perimeter(). The area method returns the area of the shape, while the perimeter method returns the perimeter of the shape.

We can use this abstract class to create concrete subclasses of it. For example, a square concrete subclass can be created by writing the following code:

```
1.2.3.4.5.6
```

The shape_square class has the same shape constructor method as the Shape parent class, but it overrides the area and abstract perimeter methods to provide a different implementation than Shape provides:

The following code creates a circle concrete subclass:

```
1.2.3.4.5.6
```

The shape_circle class has the same constructor method as Shape, but it overrides the area, and perimeter methods to provide a different implementation than Shape provides:

## Key Points about Abstract Classes:
A child class can only have one parent class. With abstract classes, you can define multiple parent classes. This is done by putting an arrow in between each parent class that you want to include.

An abstract class can have one or more abstract methods. The purpose behind an abstract method is to provide a base implementation of an operation that occurs at least once in a class hierarchy. An abstract method allows you to create multiple concrete subclasses from the same parent class but with different sets of variables and methods in each subclass.

An abstract method must always be overridden by a concrete method. The following code example shows how to override the area() and perimeter() methods:

```
M1: submethod of Shape 1.2.3.4.5.6
M2: submethod of Shape 1.2.3.4.5.6
```

Abstract classes can be used to define interfaces or abstract data types.

Abstract classes are also useful for implementing multiple inheritances by putting an arrow between two classes and setting the relationship type to DbC.

## PHP Class Interfaces
An interface is a contract, an agreement of sorts. It defines the minimum required methods and properties that a class needs to have in order to implement it. When you declare an interface, you're telling other developers that this is the knowledge you need in order to write code for your application - nothing else will suffice.

Interfaces are a very popular method of writing interfaces in PHP. A PHP class is declared to implement one or more interfaces.

Say for example you want to define an interface for customers. You could write something like this:

```
```php
<?php interface Customer { /** * Returns the name of a customer * @return string */ public function getName(); }
?>
```
```

We declare the interface with the keyword "interface." We then define the name and the methods that belong to this interface. The "public" keyword is meant to tell the client (i.e., other developers) that they can get at these methods, even if they don't have access to the interface itself (i.e., they don't have access to the class that implements it).

If we want to use this interface in our HTML page, we might write something like this:

```
```html
<html> <head> <script type ="text/javascript"> $(document).ready(function() { var c = new Customer(); c.getName(); }); </script> </head> <body> <h2>The Customer Interface</h2> <p><b>Name:</b> <?php echo $c->getName(); ?></p> </body> </html> <...
```
```

This is the way interfaces were usually used in older versions of PHP. However, with the advent of namespaces in PHP 5.3, the implementation of interfaces has changed. Now, when you define an interface, you can also declare the namespace for this interface. This allows for better encapsulation and flexibility of your class implementation.

```
```php
<?php namespace CustomerInterface ; interface Customer { /** * Returns the name of a customer * @return string */ public function getName(); } ?>
<?php namespace Userinterface ; class Customer implements CustomerInterface { public function getName() { return "My name is " . $this -> firstName . " " . $this -> lastName ; } }?>
```
```

You can now tell that the GetName() method belongs to the Customer interface. The name of your web page will also change, in this example from <script

```
```javascript
type="text/javascript">...</script>... to <script type="application/javascript">...</script>...
```
```

This gives you more control over your application, as you don't have to be confined to having every method of an interface implemented in every class that implements it.

If you want to use the above example in an HTML page, this is how it would look now:

```
<html> <head> <script type = "text/javascript" src = "/js/customerinterface.js" > </script> <script type = "text/javascript"> $(document).ready(function() { var customer = new Customer(); customer.getName(); }); </script> </head> <body> <h2>The Customer Interface</h2> <p><b>Name:</b> <?php echo $customer->getName(); ?> </p> </body> </html><...
```

## Benefits of PHP Class Interfaces
- 1. Interfaces can be declared in namespaces where they belong, instead of being mixed with classes
- 2. Interfaces are easier to organize and use
- 3. Interfaces can have properties and methods added as more features are required, instead of having to modify the original interface definition every time
- 4. Client code does not need to change when new features are added; it simply uses the interface methods even if they're implemented by a new class
- 5. Interfaces can be changed without affecting client code
- 6. Interfaces can be extended to add new methods and properties without modifying the original interface definition
- 7. Interfaces encourage re-use of code, as any class that implements the interface must support all of the methods and properties defined by it.
