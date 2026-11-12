```
class Dog extends Mammal {
public function bark() {
    echo "The dog barks. ";
}
}
```

# index.php :

```
<?php
require_once 'Animal.php';
require_once 'Mammal.php';
require_once 'Dog.php';

// Using the classes
$dog = new Dog();
$dog->eat(); // Will display: The animal is eating.
$dog->breastfeed(); // Will display: The mammal is breastfeeding.
$dog->bark(); // Will display: The dog is barking.

require_once 'Animal.php';
require_once 'Mammal.php';
require_once 'Dog.php';
```