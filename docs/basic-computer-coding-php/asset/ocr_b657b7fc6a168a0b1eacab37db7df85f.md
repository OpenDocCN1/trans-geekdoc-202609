# Basic Computer Coding: PHP

```
return $this->name; }

function set_name ($new_name) {
    $this->name = $new_name;
}
```

![](bbox=[0.109, 0.266, 0.313, 0.323])

PHP provides a set of special predefined constants and magic methods to your programs. Unlike the constants you would set using define(), the value of the constants depend on where they are used in your code and used to access read-only information about your code and PHP.

```
var $name = ' Doe'; // works
var $age = ; // works
var $day = 60*60*24; // doesn't work
```

# 6.3.3 Inheritance

To inherit the properties and methods from another class, use the extends keyword in the class definition, followed by the name of the class base:

```
class Person {
var $name, $address, $age;
}
```

```
class Employee extends Person {
var $position, $salary;
}
```

The Employee class contains the $salary properties, as well as the $name, $address, and $age properties inherited from the Personclass.

If a derived class has a property or method with the same name as one in its parent class, the property or method in the derived class takes precedence over, or overrides, the property or method in the parent class. Referencing the