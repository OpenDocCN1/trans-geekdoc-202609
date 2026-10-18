
The object-oriented paradigm also supports the concept of polymorphism. Polymorphism is a concept where a number of related classes all have a method, which shares the same name. For example, we could have created a number of classes, which draw different shapes on the screen. All of the shapes have a method called draw () which allows them to display themselves. The programmer can invoke the draw () method in any of the classes knowing that it will result in the shape being displayed. However, the resulting image produced will be different depending on the shape class from which the message is sent.

Creating classes is not the end of the story. Classes are in effect templates, which define what information can be held and what things they can do. Classes are essentially sophisticated ‘variable types’. In the same way that variables are designed to hold data of a specific type and you can do certain things with a particular variable, we can build classes which can contain certain data (held in the data members) and have associated with them certain methods which allow that data to be manipulated in different ways. However, before you can use a variable you need to create an instance of one and the same is true with classes. The class is the template and to use it you must create an instance of the class with some specific data. An instance of a class is known as an object.

Most object-oriented programming languages will implement the features described previously. However, depending on the programming language you are using, the terminology used differs. For example, class methods, functions and procedures are all used to describe the same thing. Likewise, data members, fields and variables are terms used to mean the same thing.

## 16.2 PHP and object orientation

PHP keeps things simple and consistent with the other aspects of the PHP language. In defining a class, the programmer specifies the data members and methods (variables and functions), which are encompassed within the class. Instances of classes will be referred to as objects.

### Creating a class

The keyword used to define a class is ‘class’. This is followed by a class name, which can be any name that isn’t a reserved word in PHP. The name is followed by a pair of curly braces, which contain the definition of the class’s data members and methods:

```
class name {
}
```

If we were to create a class called person then we would begin with:

```
class person {
}
```

This class doesn’t do anything just yet because we haven’t assigned any methods or data members to the class. Before we can do that we need to know about data member and method visibility.

### Visibility

The visibility of a method or data member can be defined by prefixing the declaration with the keywords:

```
public
protected
private
```

‘Public’ items can be accessed everywhere, both within and outside of the class. ‘Protected’ limits access to classes which inherit from the class and also the original class in which the item was defined. ‘Private’ limits the visibility of the method or data member only to the class that defines the item.

If we include some data members in our class it is usual for them to be private as we want to make use of the encapsulation feature of the object-oriented paradigm.

### Class data members and methods

The following script illustrates our class with some data members defined. All class members must be placed inside the class definition, i.e. between the start and end braces:

```
class person {
    private $strFirstname = "Simon";
    private $strSurname = "Stobart";
}
```

Classes can also have methods associated with them. Each class method is defined in exactly the same way as a function defined outside of the class. Class methods must be defined as public, private, or protected.

Consider our class with two member functions included:

```
class person {
    private $strFirstname = "Simon";
    private $strSurname = "Stobart";

    function getFirstname() {
    }
    function getSurname() {
    }
}
```

NOTE
Class members without any visibility specified in their declaration are defined as public. That is why the two methods in the example above appear not to have any visibility but they are, in fact, public.

These functions don’t do anything at the moment as they contain no code. What we would like them to do is return the values of data members $strFirstname and $strSurname

respectively. You would think that we could simply include a return statement like this in method getFirstname():

```
function getFirstname() {
    return $strFirstname;
}
```

Unfortunately this will not work. The above code fragment would be fine if we had defined variable $strFirstname as part of the getFirstname() method. However it is not, it is a data member (defined within the class but outside any class method). To solve this problem we need to introduce a new pseudo-variable called $this.

### $this

Pseudo-variable $this is a reference to the calling object (usually the object to which the method or data member belongs). To access a data member of the class, we use $this, followed by the operator -> followed by the variable name, for example:

```
$this->strFirstname;
```

| NOTE | Note that the $ symbol is in front of ‘this’ and not immediately in front of the name of the data member. |
|------|------------------------------------------------------------|

We can now amend our class methods to make correct use of the $this pseudo-variable, like this:

```
class person {
    private $strFirstname = "Simon";
    private $strSurname = "Stobart";

    function getFirstname() {
        return $this->strFirstname;
    }
    function getSurname() {
        return $this->strSurname;
    }
}
```

We now have a class which contains two data members and has two methods. These methods have been designed to return the values of the respective data members. However, if you were to view the output from the above script in a browser you would be very disappointed as nothing would appear. This is because while we have correctly created a class we have not used it. What we need to do now is to create an instance of this class, known as an object.

### Using a class

To make use of our person class we need to create an object of that class. To do this we need to use the keyword new. A new object must be created and assigned to a variable:

```
variable = new class
```

So for our example class we could write:

```
$objSimon = new person();
```

The above is essentially saying we wish to create a variable called $objSimon which is of the type “person”. This is the same as creating a new variable:

```
$strName;
```

Now, if you remember our class has two methods: getFirstname() and getSurname(). To invoke these methods, we use the syntax:

```
objectName->methodName()
```

Therefore, with our example class, we write either of the following:

```
$objSimon->getFirstname();
$objSimon->getSurname();
```

In order to access the values returned by the methods we need to echo the result or copy the returned values into variables. The following script contains our completed class, created object and object method calls:

```
<?php
// File: example16-1.php

class person {
    private $strFirstname = "Simon";
    private $strSurname = "Stobart";

    function getFirstname() {
        return $this->strFirstname;
    }
    function getSurname() {
        return $this->strSurname;
    }
}
$objSimon = new person;
echo "<p>Firstname: " . $objSimon->getFirstname() . "</p>";
echo "<p>Surname: " . $objSimon->getSurname() . "</p>";
?>
```

The output from the above script is illustrated in Figure 16.2.

So that works. If we want to alter the values of data members, $strFirstname and $strSurname, we can try to write something like:

```
$objSimon->strFirstname = "Tim";
```

Unfortunately this will result in an error message being generated because the data member strFirstname is defined as private and is therefore not available for access outside of the class. What we need to do in order to allow us to alter an object's data member values is to write some methods to allow us to do this.
