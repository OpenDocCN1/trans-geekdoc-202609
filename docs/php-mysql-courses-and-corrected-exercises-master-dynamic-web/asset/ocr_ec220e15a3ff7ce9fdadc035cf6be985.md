by child classes, as well as a concrete method that can be used as is or redefined as needed in derived classes.

# # Implementing abstract classes

Abstract classes cannot be instantiated directly. To use them, you need to create one or more classes that extend them. Here's how to do it:

Define a concrete class that extends the abstract class: Create a new class using the **extends** keyword to inherit from the abstract class. This class must provide implementations for all abstract methods defined in the parent abstract class.

Implement abstract methods : For each abstract method defined in the parent abstract class, provide an implementation in the child class. Implemented methods must match the signature (name and parameters) of the parent class's abstract methods.

Using the concrete class: Once the concrete class has been implemented, you can instantiate it and use its methods in the same way as any other class. You can also further extend the concrete class by creating subclasses that will in turn inherit its functionality.

Here's a practical example of how to use an abstract class in PHP :

Create an abstract class Shape (Shape.php):

```
<?php

// Abstract class definition
```