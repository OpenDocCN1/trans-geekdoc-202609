```
class Laptop extends Computer {
 protected $CPU = "3 GHz Mobile";
}
```

The answer: Yes, it would. protected releases a property or method for the entire class hierarchy—that is, for the parent and all inheriting classes.

> Note
> protected for methods is similar to its use for properties. You simply write the keyword before the method:
> protected function innerCalculation() {
>  Instructions;
> }

# "final"

A method marked with final cannot be overwritten in a subclass. The following code example therefore leads to an error, as shown in Figure 11.18.

```
<?php
class Computer {
 final function start() {
 return "Computer is started";
 }
 }
 class Laptop extends Computer {
 public function start() {
 return "Laptop is started";
 }
 }
 $MyLaptop = new Laptop();
 echo $MyLaptop->start();
?>
```

# Listing 11.20 “final” (“final.php”)

![](bbox=[0.13, 0.755, 0.74, 0.88])

# Figure 11.18 The Final “start()” Method Must Not Be Overwritten