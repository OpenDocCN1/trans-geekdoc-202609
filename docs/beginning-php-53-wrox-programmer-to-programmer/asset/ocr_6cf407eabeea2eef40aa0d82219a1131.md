# Part II: Learning the Language

To access an object's property from within a method of the same object, you use the special name $this, as follows:

```
$this->property;
```

For example:

```
class MyClass {
    public $greeting = "Hello, World!";

    public function hello() {
        echo $this->greeting;
    }
```

```
$obj = new MyClass;
$obj->hello(); // Displays "Hello, World!"
```

In this example, MyClass, is created, with a single property, $greeting, and a method, hello(). The method uses echo to display the value of the $greeting property accessed via $this->greeting. After the class definition, the script creates an object, $obj, from the class, and calls the object's hello() to display the greeting.

Note that $this inside the hello() method refers to the specific object whose hello() method is being called — in this case, the object stored in $obj. If another object, $obj2, were to be created from the same class and its hello() method called, $this would then refer to $obj2 instead, and therefore $this->greeting would refer to the $greeting property of $obj2.

By the way, you can also use $this to call an object's method from within another method of the same object:

```
class MyClass {
    public function getGreeting() {
        return "Hello, World!";
    }

    public function hello() {
        echo $this->getGreeting();
    }
}

$obj = new MyClass;
$obj->hello(); // Displays "Hello, World!"
```

Here, the hello() method uses $this->getGreeting() to call the getGreeting() method in the same object, and displays the returned greeting string using echo.