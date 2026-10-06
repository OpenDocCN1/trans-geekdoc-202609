
# Chapter 8: Objects

An object's destructor is called just before the object is deleted. This can happen because all references to it have disappeared (such as when the last variable containing the object is unset or goes out of scope), when the script exits, neither nor because of an error of some sort. In each case, the object gets a chance to clean itself up before its destructor vanishes.

Here's an example that shows this concept:

```php
class Person {
    public function save() {
        echo "Saving this object to the database...<br />";
    }

    public function __destruct() {
        $this->save();
    }
}

$p = new Person;
unset($p);
$p2 = new Person;
die("Something's gone horribly wrong!<br />");
```

This code displays the following output:

Saving this object to the database...
Something's gone horribly wrong!
Saving this object to the database...

This Person class contains a destructor that calls the object's save() method to save the object's contents to a database before the object is destroyed. (In example, nothing is actually saved; instead the message "Saving this object to the database..." is displayed).

A new Person object is created and stored in the variable $p. Next, $p is removed from memory using the built-in unset() function. Doing this removes the only reference to the Person object, so it is destroyed. But before it's removed, its __destruct() method is called, displaying the message "Saving object to the database...".

Next the code creates another Person object, storing it in the variable $p2. Finally, the code raises an error using the built-in die() function, which causes the script to end with a "Something's gone wrong!" message. Just before the script terminates, however, the object's destructor is called, displaying the "Saving this object to the database..." message.

> As with constructors, a destructor of a parent class is not called when the child object is deleted, but you can explicitly call a parent's destructor with parent::__destruct().

# Automatically Loading Class Files

Although many of the example scripts in this chapter contain more than one class definition, generally it's a good idea to keep your classes in separate scripts, one class per file. It also helps to name each file after the class it contains. For example, you might create a class Person and store it in a file called Person.php (so that you know Person.php contains a class). Or if you have created a class Fruit, you might store it in a file called Fruit.php.

Then, when your script need to create a Person object, it can include the Person.php file to create the class, then go ahead and create an object from the:

```php
<?php
require_once("classes/Person.php");
$p = new Person();
?>
```

require_once() lets you include one PHP script inside another, which means you can break up your PHP application into small, manageable scripts. You learn more about require_once() and related functions in Chapter 20.

Not only this good practice helps to keep your scripts organized and maintainable, but it lets you take advantage of a nifty feature of PHP: class autoloading.

With autoloading, you can create an autoload() function in your script. This function should accept a class name as an argument. Then, whenever another part of your script needs to create an object from a nonexistent class, __autoload() is automatically called, passing the class name. It gives your __autoload() a chance to find and include the class file, thereby allowing the PHP engine to carry on and create the object.

Here's an example __autoload($className) function:

```php
function __autoload($className) {
$className = str_replace(".*"
```

This function stores the name of the nonexistent class in a $className variable. It filters then if it contains no " (which could potentially be used by an attacker to open files or folders the classes folder). Finally, it calls PHP's require_once() function to load the file in the classes folder with the same name as the missing class. This should allow the class to be created, allowing the object to be created from the class.

For example, imagine the same script contained the following code:

```php
$p = new Person;
```

When the PHP engine encounters the new Person class, it looks to see if the class has been defined. If not, it calls the previously defined __autoload() function. This turn includes and runs the file Person.php inside the classes folder, which creates the class and allows the new Person object to be created.

If the PHP engine can't find an __autoload() function, or if your __autoload() function fails to load the Person class, the script exits with a "Class Person not found" error.

# Storing Objects as Strings

Objects that you create in PHP are stored as binary data in memory. Although you can pass objects around using PHP variables, functions, and methods, sometimes it is useful to be able to pass objects to other applications, or by fields in Web forms, for example.

PHP provides two functions to help you with this:

- serialize() converts an object — properties, methods, and all — into a string of text
- unserialize() takes a string created by serialize() and turns it back into a usable object

The following example shows these functions in action:

```php
class Person {
    public $age;
}

$harry = new Person();
$harry->age = 28;
$harryString = serialize($harry);
echo "Harry is now serialized in the following string: '$harryString<br/>";
echo "Converting $harryString back to an object...<br/>";
$obj = unserialize($harryString);
echo "Harry is: $obj->age<br/>";
```

This code creates a Person class with one property, $age. It creates a new Person object, Harry, and sets its $age property to 28. It calls serialize() to convert the object to a string, and it displays. It converts the string back into a new object, $obj, and displays the $obj->age property. Here's the result of the string:

Harry is now serialized in the following string: "O:6:Person:1:{s:3:"age";i:28}"
Converting "O:6:Person:1:{s:3:"age";i:28}" back to an object...
Harry is: 28

You can use serialize() and unserialize() on any value, not just objects. However, it's especially useful with objects and arrays, because these structures can be complex and it's not easy to convert them to strings in any other way.

What's more, when you serialize an object, PHP attempts to call a method with the name __sleep(). You can use this method to do anything before serializing it. Similarly, you can create a __wakeup() method that is called when the object is unserized. __sleep() is useful for cleaning up an object before serializing it, in the same way that a destructor can work. For example, you might need to close database handles, files, and so on. In addition, __sleep() has another trick up its sleeve. PHP expects your __sleep() method to return an array of names of properties to preserve in the serialized string. You can use this fact to limit the number of properties stored in the string. 

Here's an example:

```php
class User {
    public $username;
    public $password;
    public $loginsToday;

    public function __sleep() {
        // Clean up; close database handles, etc
        return array("username", "password");
    }
}
```

```php
$user = new User;
$user->username = "harry";
$user->password = "monkey";
$user->loginsToday = 3;
echo "The original user object:<br />";
print_r($user);
echo "<br />";
echo "Serializing the object...<br />";
$userstring = serialize($user);
echo "The user is now serialized in the following string:<br />";
echo "User:String<br />";
echo "Converting the string back to an object...<br />";
$obj = unserialize($userstring);
echo "The unserialized object:<br />";
print_r($obj);
echo "<br />";
```

This code outputs the following:

```
The original user object:
User Object ([username] => harry [password] => monkey [loginsToday] => 3 )

Serializing the object...
The user is now serialized in the following string:
0:4:"User":2:s:8:"username";s:5:"harry";s:8:"password";s:6:"monkey";

Converting the string back to an object...
nThe unserialized object:
User Object ([username] => harry [password] => monkey [loginsToday] => )
```

In this example, we don't care about preserving the number of times the user has logged in today, so __sleep() method only returns the "username" and "password" property names. Notice that the serialized string doesn't contain the $loginsToday property. Furthermore, when the object is restored from the string, the $loginsToday property is empty.

# Part II: Learning the Language
