
```
User name: Dupont
User first name : Alice
User's age: 30
User email: dupont.alice@example.com
```

## Conclusion

In this chapter on encapsulation and data modeling in object-oriented programming, we have explored the fundamental concepts involved in structuring and protecting data within an application. We began with encapsulation, which consists of grouping data and associated methods within classes, while defining visibility levels to control access to these elements.

We then looked in detail at the getters and setters methods, which provide a secure and controlled means of accessing and modifying a class's private properties. Using these methods, we saw how to guarantee data integrity and reinforce encapsulation by preventing direct access to private properties.

We have also examined the advantages of using getters and setters, particularly in terms of flexibility, maintainability and code security. By using specific methods to access data, we can easily implement data validation and processing logic, while preserving encapsulation and minimizing the risk of data corruption.

Finally, we looked at the essential role of the constructor in creating objects and initializing their properties. By defining an appropriate constructor, we can ensure that objects are correctly configured as soon as they are created, contributing to a safer and more consistent use of our classes.

In conclusion, encapsulation and data modeling are key concepts in object-oriented programming, enabling the design of robust, modular and easily maintainable applications. By understanding and applying these principles, developers can create more efficient and reliable software systems, guaranteeing data protection and integrity throughout their lifecycle.

## EXERCISES

### Exercise 26

Create a class Person that contains the following properties:

- $name: the person's name
- $age: the person's age

The Person class must have the following methods:

- __construct($name, $age): a constructor that initializes the name and age properties
- getName(): a method that returns the person's name
- getAge(): a method that returns the person's age
- setAge($age): a method that modifies the person's age

Create an instance of the Person class and display its name and age. Then, modify the person's age and display the new value.

### Exercise 27

Create a class Vehicle with the following attributes: brand, model, year, price. The attributes should be defined in the constructor.

The class must have getters and setters for each attribute, as well as a display() method that displays the vehicle's information as a string.

Then, create an object (vehicle1) of type Vehicle with initial information and use the display() methods and setters to modify the information of the created vehicle.

## Chapter 16

### Inheritance in PHP

Inheritance is one of the fundamental concepts of object-oriented programming. It allows a class to inherit properties and methods from another class, called a parent or base class. In PHP, inheritance offers a powerful mechanism for reusing code and structuring applications.

This chapter will focus on exploring inheritance in PHP, examining in detail its syntax, benefits and best practices. We'll discover how to create class hierarchies, access inherited members, and redefine methods to customize them to the specific needs of a child class. In addition, we'll discuss important considerations when using inheritance in software development.

Understanding inheritance is essential to mastering object-oriented programming in PHP and to designing more modular, scalable and maintainable applications. So let's delve into the world of inheritance in PHP and discover how it can enrich our development practices.

### Defining inheritance in object-oriented programming

Inheritance is a key concept in object-oriented programming (OOP), which enables a class to inherit the characteristics (properties and methods) of another class called its parent or base class. With inheritance, a child class can reuse and extend the behavior of its parent class, thus promoting code reuse and the logical structuring of applications.

In PHP, inheritance is implemented using the extends keyword, which allows a child class to extend a parent class by inheriting its public and protected members. In this way, the child class can access the properties and methods of its parent class as if they were defined locally in its own class definition.

![](img/caba2aa22f5409ba73dea47176330677_499_0.png)

Let's illustrate the concept of inheritance with a simple example:

Let's create a new file named "Person.php", in which we define a class with the same name, i.e. "Person" :

```php
<?php
// Parent class
class Person {
    protected $name;
    protected $age;

    // Constructor
    public function __construct($name, $age) {
        $this->name = $name;
        $this->age = $age;
    }

    // Method to display person's details
    public function displayDetails() {
        echo "Name: ". $this->name . ", Age: ". $this->age . " years";
    }
}
```

This code defines a class called Person. This class has two properties defined by the **protected** keyword: $name and $age, which represent the person's name and age respectively. The protected keyword is a visibility level in object-oriented programming used to define access to a class's properties and methods. When a member (property or method) is declared as protected, it is accessible within the class in which it is defined, as well as in derived classes (child classes) that inherit from this class, but not outside these classes.

In concrete terms, this means that protected members are not directly accessible outside the class where they are declared, but can be used in child classes that inherit from this parent class. This provides an additional level of encapsulation and security, as protected members are not exposed outside the class hierarchy, but can be used by subclasses to extend or specialize the behavior of the parent class.

The constructor of the Person class is defined to initialize these properties when a new object of type Person is created. It takes two parameters, $name and $age, and uses them to initialize the corresponding object properties.

The Person class also has a public displayDetails() method, which displays the person's details, such as name and age, using the concatenation operator (.) to form a string containing these details.

Now let's create a new file called Employee.php in which we define a class with the same name that inherits from the Person class:

```php
<?php
require_once 'Person.php';

class Employee extends Person {
    private $salary;

    public function __construct($name, $age, $salary) {
        parent::__construct($name, $age);
        $this->salary = $salary;
    }

    public function displayEmployeeDetails() {
        parent::displayDetails();
        echo ", Salary: $ " . $this->salary;
    }
}
```

This code defines a class called "Employee" that extends the parent class "Person". Here's a detailed explanation of each part of the code:

require_once 'Person.php';: This line includes the file "Person.php", which contains the parent class "Person". This allows the "Employee" class to extend the "Person" class.

class Employee extends Person {...}: This class declaration, using the extends keyword, creates the "Employee" class as a child of the "Person" class. This means that the "Employee" class will inherit the properties and methods of the "Person" class.

private $salary;: This is a declaration of a new private property specific to the "Employee" class. It stores the employee's salary.

public function __construct($name, $age, $salary) {...}: This is the constructor of the "Employee" class. It takes three parameters: the name, age, and salary of the employee. The parent::__construct() function calls the constructor of the parent class "Person" with the name and age. Note the use of the double colon operator (::) to call the parent constructor. Then, the employee's salary is initialized with the value passed as an argument.

public function displayEmployeeDetails () {...}: This is a method added to display the details of the employee by using the displayDetails() method of the parent class "Person", and then adds the display of the salary. The parent::displayDetails() method calls the displayDetails() method of the parent class "Person" to display the employee's name and age, and then adds the employee's salary to the display.

In summary, this code creates an "Employee" class that inherits functionalities from the "Person" class and adds an additional property to store the employee's salary. The constructor initializes all necessary properties, while the "displayEmployeeDetails()" method displays the details of the employee, including their salary.

To evaluate the functionality of inheritance, insert the following code into the index.php file.

```php
<?php
require_once 'Person.php';
require_once 'Employee.php';

// Instantiate the Employee class
$employee1 = new Employee("John Dupont", 35, 50000);
```
