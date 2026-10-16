# 26. INTRODUCTION TO OBJECT-ORIENTED PROGRAMMING IN PHP

# About Constructors

When working with constructors and destructors[8] in PHP, something to keep in mind is that they may function differently in other OOP languages. Take a look at this quote from the PHP manual regarding constructors to make sure you know how to design your classes to take advantage of construction in the way you intend:

> Parent constructors are not called implicitly if the child class defines a constructor. To run a parent constructor, you must call parent::__construct() within the child constructor. If the child does not define a constructor, then it may be inherited from the parent class and called just like a standard class method (if it was not declared as private).

# Constructor Property Promotion in PHP 8

Although this book assumes PHP 7.x, as of the time of publishing for this book, PHP version 8 is out and offers several new features and enhancements. I'd like to introduce just one of them to you called constructor property promotion.

Constructor property promotion allows you to combine class properties, constructor definition, and variable assignments all in the __construct() parameter list. In a standard definition of class instance properties, construction, and assignment, you would use code like Listing 26.20.

# Listing 26.20.

```
```php
<?php

class Student
{
    private $id;
    private $name;
    private $email;

    // Constructor
    public function __construct(
        $id,
        $name,
        $email
    ) {
        $this->id = $id;
        $this->name = $name;
        $this->email = $email;
    }
}
```
```

[8] constructors and destructors: https://php.net/manual/en/language.oop5.decon