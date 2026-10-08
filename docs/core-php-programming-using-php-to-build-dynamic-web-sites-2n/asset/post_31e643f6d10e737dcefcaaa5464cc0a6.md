
# Core PHP Programming

## Chapter 6. CLASSES AND OBJECTS

Defining a Class

Creating an Object

Accessing Properties and Methods

Object-oriented programming was devised as a solution to problems associated with large software projects where many programmers work on a single system. When source code grows to be tens of thousands of lines of code or more, each change can cause unexpected effects. This happens when modules form secret alliances like nations in pre-WWI Europe. Imagine a module for handling logins that allows a credit card processing module to save its database connection. Surely that was done with best intentions, to save the overhead of acquiring another connection. Some time later, the login module severs the agreement by changing the variable name. The credit card processing module breaks; the module that invoices breaks. Soon unrelated modules are dragged into the fray.

So, I'm being a bit dramatic. Most programmers pick up appreciation for coupling and encapsulation. Less coupling is better. We'd like to take modules from existing projects and reuse them in new projects. We'd like to make wholesale changes to the internals of modules without worrying about how they affect other modules. The solution is to follow the principle of encapsulation. Modules are treated as independent states, and exchanges between modules are done through narrow, structured interfaces. Modules do not spy on each other by reaching into other's variables. They ask politely through functions.

Encapsulation is a principle you can apply in any programming language, if you have discipline. In PHP, and many procedural languages, it's easy to be tempted to be lazy. Nothing prevents you from building a web of conceit with your modules. Object-oriented programming is a way of making it nearly impossible to violate encapsulation.

In object-oriented programming, modules are organized into objects. These objects have methods and properties. From an abstract perspective, methods are what an object does, and properties are the characteristics of the object. From a programming perspective, methods are functions and properties are variables. In an ideal object-oriented system, each part is an object. The running of the system consists of objects exchanging with other objects using methods.

Each language takes a different approach to objects. PHP borrows from C++ and offers a data type that may contain functions and variables under a single identifier. When PHP was first conceived, even when version 3 was created, PHP wasn't intended as capable of powering projects of 100,000 lines or more of code. Due to recent advances built into PHP and Zend, this is a reality. But no matter the size of your project, building your scripts with classes will certainly aid you in writing code that can be reused. This is a good idea, especially if you wish to share your code.

The idea of objects is one of those mind-blowing concepts in computer science. It's hard to grasp at first, but I can attest once you get it, it becomes quite natural to think in its terms. Nevertheless, you can ignore objects if you wish and return to this chapter later. Built-in functions return objects. You can find alternatives that don't, or you can cast the objects as arrays, as described at the end of this chapter.

# Defining a Class

When you declare a class, you are really making a template for the creation of objects. You list all the variables the object should have and all the functions it will need. Sometimes these are called properties and methods, Figure 6-1 displays the form of a class declaration. Note that the curly braces you only declare variables with the var statement or declare functions. Listing 6.1 shows the definition of a class with three properties and two methods.

Figure 6-1. Defining a class.

```
class name extends another class
{
    var Variable Declaration
    Function Declaration
}
```

When you declare a property, you don't specify a data type. It is a variable like any other, and it may contain an integer, a string, or even another object. Depending on the situation, it might be a good idea to add a comment near the declaration of the property that states its use and data type. When you declare a class, you do just so as you would a function outside a class definition. Methods and properties exist within their own scope, or name space. This means you can safely create methods that have the same name as functions declared outside class definitions without conflicts. Any exception to this are built-in functions. For example, you can have a print method.

Aside from variables passed as arguments, methods contain a special variable called this. It stands for the particular instance of the class. You must use this to refer to properties and other methods of the object. Some object-oriented languages assume an unqualified variable that refers to a local property, but in PHP any variables referred within a method are simply variables local to that. Note the use of the this variable in the constructor for the user in Listing 6.1.

If you choose to declare a function within a class that has the same name as the class itself, the function will be considered a constructor and will be executed immediately upon creating an object from that class. Typically the constructor is used to initialize the object's properties. Like any other function, the constructor may have parameters and even default values. You can set up classes that allow you to create an object and set all its properties in one statement. Unlike other languages, PHP does not allow for destructors—functions that execute when the instance is deleted. However, if you choose to use unset on an object, the memory associated with that object will be freed. In situations where you must execute some code when you finish using an object, create your own shutdown function and remember to call it.

One powerful aspect of classes is inheritance, the idea that a class can extend the functionality of another class. The new class will contain all the methods and properties of the class it extends, plus any others it limits within its body. You may also override methods and properties from the extended class. As shown in Figure 6-1, you extend a class using the extends keyword.

Listing 6.1 Using Classes

![](img/58e6a0f5d6a8a41d4645d8c07b3bf1e3_104_0.png)

```php
<?
/**
** define class for tracking users
 */
class user
{
    /*
    ** properties
    */
    var $name;
    var $password;
    var $last_login;

    /*
    ** methods
    */
    function user($inputName, $inputPassword)
    {
        $this->name = $inputName;
        $this->password = $inputPassword;
        $this->last_login = time();
    }

    // get the date of the last login
    function getLast()
    {
        return(Date("M d Y", $this->last_login));
    }
}

// create an instance
$currentUser = new user("Leon", "sdf123");

// get last date
print($currentUser->getLast());
print("<br>\n");

// print the user's name
print($currentUser->name);
print("<br>\n");
?>
```

One issue you might wonder about is whether and how constructors are inherited. While they are inherited along with other methods, if you require this functionality, you must write it explicitly by calling the parent class's.

# Creating an Object

Once you have defined a class, you use the new statement to create an instance of the class. If the definition of the class is the blueprint, the instance is the widget rolling off the assembly line. The new statement expects the name of a class and returns a new instance of that class. If a constructor has been declared, you may also follow the class name with parentheses. Look for the line in Listing 6.1 that uses new statement.

When you create an object, memory is set aside for all the properties. Each instance has its own set of properties, the methods are handled by all instances of that class.

As recall, PHP allows you to create variables without explicitly defining the type. Objects are no different. You can create an object simply by using it in the proper context. That is, using the -> operator on a variable will make it an object. You can create as many properties as you wish on this new object by referring to them. Unfortunately, you will not be able to attach methods to this object.

Another way to create an object is to change the type of an array. When an array becomes an object, the elements indexed by strings become properties. Elements indexed by numbers will remain but be inaccessible. If the variable later returns to an array, this is similar to what happens when an object is cast as an array. All properties will be available as array elements, but methods are not. When an object is created through casting or inference, it is of type stdClass.

# Accessing Properties and Methods

The properties of an instance are variables, just like any other PHP variable. To refer to them, you must use the -> operator. You do not use a dollar sign in front of the property name. For example, refer to the line in Listing 6.1 that prints the name property of the currentUser object.

Use of -> can be chained. If an object's property contains an object itself, you can use two -> operators to get a property on the inner object. The parser in PHP 3 was unable to deal with complex expressions like this. In PHP 4 you are not limited with this.
