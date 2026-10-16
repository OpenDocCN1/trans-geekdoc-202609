Listing 26.14 shows how we can use these classes. You can see the output in Figure 26.2.

# Listing 26.14.

```
```php
<?php
require_once('Pet.php');
require_once('Dog.php');
require_once('Cat.php');

// Create a pet, dog, and cat
$my_pet = new Pet();
$my_dog = new Dog();
$my_cat = new Cat();

// Set Pet's name and exercise
$my_pet->setName("Gerald");
$my_pet->exercise();

echo '**********<br />';

// Set Dog's name, exercise, and bark
$my_dog->setName('Sparky');
$my_dog->exercise();
$my_dog->bark();

echo '**********<br />';

// Set Cat's name, exercise, and meow
$my_cat->setName('Boo');
$my_cat->exercise();
$my_cat->meow();
```
```

Exercising my pet Gerald.
**********
Exercising my pet Sparky.
Sparky is barking.
**********
Exercising my pet Boo.
My cat Boo is meowing.

Figure 26.2.

> You’ll notice that I include a reference to the Pet class even though Dog and Cat also include the Pet class. It is a best practice, as long as I am instantiating an object of a base class to include the base class, even though an instantiated sub-class inherits the base class as well. The reason is, I would minimize any breaking changes if the inheritance structure were to be redesigned. Remember to use require_once so you don’t get a fatal error when including a class that already exists.