# Overwrite

With inheritance, you can overwrite the properties and methods of the parent class in
the subordinate (inheriting) class. To do this, simply create a property or method with
the same name as its counterpart in the parent class. In the following example, both the
CPU property and the start() method are overwritten; Figure 11.9 shows the result.

```
<?php
class Computer {
public $CPU = "The CPU";
public function start() {
return "Computer is started.";
}
}
class Laptop extends Computer {
public $CPU = "2,5 GHz Mobile";
public function start() {
return "Laptop is started.";
}
}
$MyLaptop = new Laptop();
echo "CPU: $MyLaptop->CPU<br />";
echo $MyLaptop->start();
?>
```

Listing 11.10 Overwrite Properties and Methods ("inheritance_overwrite.php")

![](bbox=[0.142, 0.562, 0.792, 0.705])

Figure 11.9 Property and Method Are Overwritten

# Indirect Access to Methods

If you want to access a method of the superordinate class from a method, you need a
reference to this class. You could instantiate an object or access the class directly using
the colon syntax, but then you would always need to know the name of the class. The
cleverer alternative is to use the parent keyword. This allows you to access the parent
class regardless of its name.