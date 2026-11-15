```
public $RAM = "1024";
public function ramcheck() {
    $gb = $this->mb2gb($this->RAM);
    return "Computer has " . $gb . ' GB RAM';
}
}
class Laptop extends Computer {
    public $RAM = "4096";
}
$MyLaptop = new Laptop();
echo $MyLaptop->ramcheck();
?>
```

# Listing 11.42 Use of a Trait ("traits.php")

![](bbox=[0.15, 0.36, 0.74, 0.455])

# Figure 11.32 The Method of the Trait Provides the Appropriate Conversion

> **Note**
> If you define several methods with the same name within a class structure, the overwriting sequence is as follows: priority is always given to the method that is defined directly in the respective class. This is followed by the trait that is used in the class. At the end of this ranking is a method from an inheriting class.

The methods in traits can be used quite flexibly, and both their names and their visibility can be changed. The former is particularly necessary if there could be name conflicts with several traits or methods in the class.

To change the name and visibility, there are two keywords that are placed in curly brackets after the use statement; if there are two traits with the same methods, then `instead of` decides which trait should be used. `as` allows you to specify an alias, a different name, for a method and to change the visibility—or to do only one of the two.

The following example shows two traits with identical `mb2gb()` methods. In the `Computer` class, it is then specified that the method from the `converter` trait is used for the identical methods. In addition, the visibility is increased to `protected` so that the method can be used in the inheriting class, `Laptop`. We make the method of the same name from the `Helpers` trait publicly accessible and assign the `convertRam()` alias. Figure 11.33 shows the output.