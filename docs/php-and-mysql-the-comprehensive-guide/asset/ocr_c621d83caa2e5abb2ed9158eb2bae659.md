```
<?php
class Computer {
    private $cpu = "The CPU";
    public function setCPU($cpu) {
        echo 'The computer has ' . $cpu;
    }
}

$refClass = new ReflectionClass('Computer');
$computer = new Computer();
$method = $refClass->getMethod('setCPU');
echo $method;
echo '<br />';
$method->invoke($computer, '4 CPUs');
?>
```

Listing 11.59 "ReflectionClass" Is Used ("reflection_object.php")

Here, a method is executed and inspected via a reflection class. The `invoke()` method is used for execution. There is also `invokeArgs(Object, Array)`, which can be used to pass several parameters as an array (see Figure 11.48).

![](bbox=[0.14, 0.45, 0.79, 0.59])

Figure 11.48 The Method Is First Inspected, Then Executed

> **Note**
> You can learn more at http://s-prs.co/v602274.

# 11.4.11 SPL

The Standard PHP Library is based on the Standard Template Library (STL) from C++. What is this library? It's a set of firmly defined classes and interfaces for iterators and other important standard tasks.10 An `iterator` is a programming construct that iterates through other elements. The simplest type of iterator is a loop, as you’ve seen in Section 11.4.8. Here we start with a similar example, which is then extended to include SPL functionality.

10. The basis of SPL is the design pattern idea, and the father of SPL in PHP is Marcus Börger.