# Listing 26.16.

```
<?php
require_once('Pet.php');
class Cat extends Pet
{
    public function meow()
    {
        echo 'My cat ' . $this->name . ' is meowing.<br />';
    }

    // Do some cat exercise!
    public function exercise()
    {
        echo 'My cat ' . $this->name . ' is chasing mice!<br />';
    }
}
```

A powerful feature of OOP is we don’t have to make any changes to code that uses the Pet, Dog, and Cat class since we call the methods the same way. Just rerun it and notice the change in the output in Figure 26.3.

![](bbox=[0.68, 0.36, 0.88, 0.55])

# Constructors

Constructors are used in object-oriented languages to initialize an object from a class as part of instantiation. So far, when we’ve instantiated an object, we have done so using an empty set of parenthesis following the name of the class using the new keyword:

```
$myDog = new Dog();
```

This method of initialization is using the default constructor. If you do not define a constructor, PHP will try to initialize your object’s properties.

A constructor is a function that runs during the initialization of your object. You want to define a constructor if you have some specific initialization you want to perform in your class.

We define a constructor using the PHP Magic Method __construct(). PHP has a number of “Magic Methods”[7] which are functions starting with a double-underscore (__). I will only talk about __construct() and __destruct() in this chapter.

[7] “Magic Methods”: https://php.net/language.oop5.magic