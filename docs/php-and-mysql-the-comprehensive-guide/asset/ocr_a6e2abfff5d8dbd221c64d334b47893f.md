The preceding script therefore outputs the following:

Laptop is started

However, unlike interfaces, abstract classes cannot implement methods marked as abstract, which are then used by the inheriting instantiable class.

Even with abstract classes, the abstract method must have the same parameters as the implemented method.9 However, including additional optional parameters is possible.

```
abstract class Computer {
abstract function start($sek);
}
class Laptop extends Computer {
public function start($sek) {
return "Laptop will start in $sek";
}
}
```

# Listing 11.30 Abstract Class with One Parameter (Excerpt from "abstract_parameter.php")

Abstract classes are subject to the following restrictions:

+   - You cannot instantiate an object from abstract classes.
+   - A class cannot inherit from several abstract classes at the same time. This restriction applies above all to interfaces, which are more flexible in this respect.
+   - Methods cannot be declared as `private` as they must be inherited, and they cannot be declared as `final` as they are overwritten.
+   - There is another at least partial restriction: although you can define properties in an abstract class, you cannot create abstract properties that would be mandatory for the inheriting class.
+   - In PHP 7.2, another restriction was lifted. Since this version, methods in abstract classes that inherit from each other can overwrite each other.

# 11.3.8 Anonymous Classes

Anonymous classes are a new feature in PHP 7 and are used when a class is required as a structure but should not be used multiple times. One common area of application for such classes, for example, is cases in which a function or method expects a class as a parameter.