# Part II: Learning the Language

This is where abstract classes and methods come to play. By making a parent class abstract, you lay down the rules as to what its child classes must contain. When you declare an abstract method in the parent class, you don't actually insert any code in the method; instead, you leave up to the child classes. You're specifying what the child class must do, not how to do it.

To declare an abstract method, use the abstract keyword, as follows:

```
abstract public function myFunction($param1, $param2);
```

As you can see, you can optionally specify any parameters that the method must contain. However, you don't include any code that implements the method, nor do you specify what type of value the method must return.

If you declare one or more methods of a class to be abstract, you must also declare the whole class to be abstract:

```
abstract class MyClass {
    abstract public function myFunction($param1, $param2);
}
```

You can't instantiate an abstract class — that is, creating an object from it — directly:

```
// Generates an error: "Cannot instantiate abstract class MyClass"
$myObj = new MyClass();
```

So when you create an abstract class, you are essentially creating a template, rather than a fullyfledged class. You are saying that any child class must implement any abstract methods in the abstract class (unless those child classes are themselves declared to abstract).

By the way, you can mix abstract and non-abstract methods within an abstract class. So your abstract class might define behavior that is common to all possible child classes, leaving the remainder of the methods for the child classes to implement.

> The opposite of an abstract class — that is, a class that implements all the methods of its parent class is called a concrete class.

Now return to the Shape class. By creating the Shape class as an abstract class, you can add a declaration for the abstract getArea() method, ensuring that all child classes of Shape have to implement getArea();

```
abstract class Shape {
    private $_color = "black";
    private $_filled = false;

    public function getColor() {
        return $this->color;
    }
```