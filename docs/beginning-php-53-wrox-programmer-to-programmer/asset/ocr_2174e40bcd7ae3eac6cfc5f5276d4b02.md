# Automatically Loading Class Files

Although many of the example scripts in this chapter contain more than one class definition, generally it's a good idea to keep your classes in separate scripts, one class per file. It also helps to name each file after the class it contains. For example, you might create a class Person and store it in a file called Person.php (so that you know Person.php contains a class). Or if you have created a class Fruit, you might store it in a file called Fruit.php.

Then, when your script need to create a Person object, it can include the Person.php file to create the class, then go ahead and create an object from the:

```
<?php
require_once("classes/Person.php");
$p = new Person();
?>
```

require_once() lets you include one PHP script inside another, which means you can break up your PHP application into small, manageable scripts. You learn more about require_once() and related functions in Chapter 20.

Not only this good practice helps to keep your scripts organized and maintainable, but it lets you take advantage of a nifty feature of PHP: class autoloading.

With autoloading, you can create an autoload() function in your script. This function should accept a class name as an argument. Then, whenever another part of your script needs to create an object from a nonexistent class, __autoload() is automatically called, passing the class name. It gives your __autoload() a chance to find and include the class file, thereby allowing the PHP engine to carry on and create the object.

Here's an example __autoload($className) function:

```
function __autoload($className) {
$className = str_replace(".*"
```

This function stores the name of the nonexistent class in a $className variable. It filters then if it contains no " (which could potentially be used by an attacker to open files or folders the classes folder). Finally, it calls PHP's require_once() function to load the file in the classes folder with the same name as the missing class. This should allow the class to be created, allowing the object to be created from the class.

For example, imagine the same script contained the following code:

```
$p = new Person;
```

When the PHP engine encounters the new Person class, it looks to see if the class has been defined. If not, it calls the previously defined __autoload() function. This turn includes and runs the file Person.php inside the classes folder, which creates the class and allows the new Person object to be created.