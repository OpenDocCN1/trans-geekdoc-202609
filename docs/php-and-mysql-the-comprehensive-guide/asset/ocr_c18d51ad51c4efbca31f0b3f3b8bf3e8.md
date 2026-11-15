```
}
$MyCar = new Car();
change($MyCar);
?>
```

# Listing 11.50 Typing Objects ("class_types.php")

![](bbox=[0.145, 0.22, 0.755, 0.485])

# Figure 11.40 The Class Is an Instance of "Car", Not of "Computer"

> **Note**
> 
> The class name technique is important in object-oriented languages that use strict typing. PHP, on the other hand, is loosely typed; that is, you do not have to specify any data types. Specifying the class type is therefore an exception. In accordance with the architecture of PHP, the check only takes place when the script is executed (runtime).

The error message when specifying the class type is not always desirable. For this reason, there is another keyword to determine whether an object is an instance of a class: instanceof. The syntax looks like this:

```
Object instanceof class
```

The return value of this construct is a truth value. With the instanceof operator, you can quickly rewrite the script with class types and simply check whether the object passed to the change() function comes from the Computer class, as in the following listing. Of course, this gives you more reaction options, but you also have to type a little more code. Figure 11.41 shows the output.