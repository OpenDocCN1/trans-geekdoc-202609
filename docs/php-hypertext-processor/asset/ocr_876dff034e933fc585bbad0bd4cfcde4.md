+   - **Constructor:** refers to a special type of function which will be called automatically whenever there is an object formation from a class.

+   - **Destructors:** refers to a special type of function which will be called automatically whenever an object is deleted or goes out of scope.

# Defining PHP Classes

The general form for defining a new class in PHP is as follows:

```
<?php
class phpClass{
var $var1;
var $var2 = "constant string";
function myfunc ($arg1, $arg2) {
[...]
}
[...]
}
?>
```

Here is the description of each line:

+   - The special form **class**, followed by the name of the class that you want to define.

+   - A set of braces enclosing any number of variable declarations and function definitions.

+   - Variable declarations start with the special form **var**, which is followed by a conventional $ variable name; they may also have an initial assignment to a constant value.

+   - Function definitions look much like standalone PHP functions but are local to the class and will be used to set and access object data.

# Example

Here is an example which defines a class of Books type:

```
<?php
class Books{
/* Member variables */
var $price;
var $title;
/* Member functions */
function setPrice($par){
$this->price = $par;
}
```