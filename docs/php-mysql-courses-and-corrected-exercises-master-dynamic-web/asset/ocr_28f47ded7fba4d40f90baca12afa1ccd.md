from an object. It receives two arguments: the name of the attempted method and any associated arguments, which are then converted into an array.

As for the magic __callStatic() method, it is triggered when we try to use a method that doesn't exist or is inaccessible in a static context. This method accepts the same arguments as __call().

# **Example of the __call() method:**

```
<?php
class Example {
    public function __call($lastNameMethod, $arguments) {
        echo "The method '$lastNameMethod' does not exist or is inaccessible.";
        echo "The arguments passed are: " . implode(', ', $arguments);
    }
}

$object1 = new Example();
$object1->methodNotExist("argument1", "argument2");
```

In this example, we have an “Example” class with a magic __call() method. When we try to call a method methodNotExist() on the object $object1, this method doesn’t exist in the class. Consequently, the __call() method is invoked automatically. It displays a message indicating that the method does not exist, as well as the arguments passed to this method.

Execution of this code will produce the following display: