
## Define a PHP Class and Object:

A class contains a set of functions and member variables (also called properties). A PHP class can hold many functions and variables as follows:

```php
class Teacher
{
    public $course = "Java";

    function students()
    {
        // set of statements or lines here
    }
}
```

The above class Teacher contains one member variable (class variable or property), i.e. course, and one function, i.e. students(). Here public is an access specifier which means the variable $course can be accessed or used by another class. Please note before declaring a class variable or property, we should add the visibility keyword (public / private / protected) to define where the variable is available.

## Naming a Class:

The name you use for a class ("Teacher" in the above example):

- Should not be a PHP reserved word (Keyword).
- Should start with a letter or underscore.
- Can have letters, numbers or underscores after the first letter.

To access member variables or functions of any class, you need to create an object of that class first. Example below:

```php
$obj = new Teacher;
```

Once the object of the class is created, you can access member variables or functions something like this:

```php
$obj->students();
echo $obj->course;
```

Remember, to execute or view output from a function, you have to call it first. A function will not produce any output until you call it.

## What is Constructor?

As explained, every function should be called to get output from it. But a constructor is a function that doesn’t require any calling, as it is automatically called once the object of the class is created. In PHP, a constructor is defined using the __construct() method. Example below:

**Example: PHP Constructor**

```php
class Teacher
{
    public $course = "Java";

    function __construct()
    {
        echo "This function is constructor- default function";
    }

    function __destruct()
    {
        echo "This function is destructor will call after end of program";
    }
}

$obj = new Teacher;
```

In the above program, we have created 2 functions, __construct() and __destruct(), which will be automatically called once the object is created. A constructor is used to initialize memory, while a destructor is used to release or de-initialize memory of the class, usually when the script ends.

*Please note: if you have a constructor with arguments, you should send the values for those arguments when you create it.*

## The $this Keyword

`$this` is a pseudo-variable which is only available inside methods. `$this` is used to access properties / member variables of the present class. In other words, we use the `$this` variable to access the current object. Example below:

```php
<?php

class Users {
    public $email;
    function sendData($x)
    {
        $this -> email = $x;
    }
}
```

## Access specifiers or visibility mode in PHP

There are 3 visibilities or access specifiers available in PHP: public, private, and protected. These visibilities are used with properties or member variables to enable access from outside the class. These specifiers also play an important role in validating and restricting information in the program. For example, my credit card and its PIN details are private, and I don’t want to share them with someone else.

- The **Public** properties or methods can be accessed anywhere or outside the class.
- The **Private** properties or methods can only be accessed within the class.
- The **Protected** properties can be accessed by the classes that inherit its parent class.

```php
<?php
class myDetails
{
    private $pin = "1234";

    function view_details()
    {
        echo $this->pin;    // Inside class this is valid
    }
}

$ob = new myDetails;

echo $ob->pin;   // Error: cannot access outside the class
```

So from the above example, any method inside the class has access to private property (pin). But, you cannot access it from outside the class.

## PHP OOPs Inheritance

Inheritance is the process of creating a new class from the existing one. However, we can also add some additional functionality or resources to the newly created class apart from the existing base class.

It could be useful if you have certain classes that represent some common methods or properties. For example, an e-Commerce portal has several classes, and in each class you require some user information like email and auth key. So, instead of creating separate properties for each class, you can create a master class and allow other classes to use these properties using inheritance.

When we say an inherited class, it is a child class or sub class, and the class from which we inherit is called the parent class or base class.

There are several types of Inheritance in PHP OOPs programming, which are listed below:

- **Single Inheritance**: When a class is inherited by only one class, it is called Single Inheritance.
- **Multilevel Inheritance**: When a parent class is inherited by a child class, and then that child class is further inherited by another child class.
- **Hierarchical Inheritance**: When a single parent class has more than one child class, it is called hierarchical inheritance.

*Please note that PHP doesn’t support multiple inheritances; however, **Traits** are there in PHP to solve the same.*

Hirdesh Bhardwaj

```php
class B extends A   // First child class of A
{
    function fn1()
    {
        $this->price = 200;
        echo $this->price;
    }
}

class C extends A   // Second child class of A
{
    function fn2()
    {
        $this->price = 300;
        echo $this->price;
    }
}

$ob1 = new B;
$ob1->fn1();
echo "<br>";

$ob2 = new C;
$ob2->fn2();
```

**Traits in PHP:** Since we already know that PHP doesn’t support multiple inheritances, Traits in PHP can be used to declare methods that can be used in multiple classes. By doing so, you can reduce code duplication, as there's no need to redefine the same method again and again.

### Example: Using Traits in PHP

```php
<?php
Trait A
{
    public function hello()
    {
        echo "Hello This is Trait A";
    }
}

Trait B
{
    public function test()
    {
        echo "Hello This is Trait B";
    }
}

class MyClass
{
    use A, B; // Calling Traits A and B in the class
}

$obj = new MyClass();
$obj->hello();
$obj->test(); // Calling function test
?>
```

## Static Methods and properties in PHP

Static methods are widely used to create Helper and Utility functions (e.g., autoloading), which gives you more ability to organize and recall your functions. Static functions in PHP can be called directly (using the Resolution Operator `::`) without creating an object of the class. The `static` keyword is used to define a static function in PHP.

### Example

```php
class A
{
    static function fn()
    {
        echo "This is a Static Function";
    }
}

echo A::fn(); // Calling function without creating object
```

Please note that if no visibility mode or access specifier (public, private, or protected) is declared, the visibility mode will be *public* by default.

Static methods can also be accessed from other methods in the same class using the **self** keyword and `::` (Resolution Operator).

**Static Properties or Variables:** Just like static functions or methods, you can also access static properties or variables in the same way using the `::` operator. Example:

```php
<?php
class A
{
    public static $rating = 7;  // Static properties / Member variable

    public function __construct()
    {
        echo "Rating is" . self::$rating;  // Accessing static variable
    }
}
```

```php
echo A::$rating;    // Accessing static variable directly
A::$rating = 10;
new A();  // Object to call constructor
```

## Getter and Setter in PHP

Getter and Setter methods provide encapsulation of data so that in order to set or get data, it has to pass through a method.

A “getter” allows you to retrieve or “get” a given property. A “setter” allows you to “set” the value of a given property.

### Example

```php
<?php

class MyClass
{
    public $greeting = "Good Morning";

    public function setProperty($x)
    {
        $this->greeting = $x;
    }

    public function getProperty()
    {
```
