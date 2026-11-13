```
$myObject->myMethod();
$myObject->myValue = "Custard";
$myObject->myMethod();
```

This example makes two separate calls to myMethod . The first time it displays the default value of myValue ; an assignment within the class specifies a default value for a property. The second call comes after that property has had a new value assigned. The class uses $this to reference its own property and does not care, or even know, that in the script its name is $myObject .

If the class includes a special method known as a constructor , arguments can be supplied in parentheses when an object is created, and those values are later passed to the constructor function. This is usually done to initialize a set of properties for each object instance, and it looks similar to the following:

```
$myObject = new myClass($var1, $var2);
```

# Using a Third-Party Class

The best way to learn how to work with classes is to use one. Let's take a look at a popular third-party class written by Manuel Lemos, which provides a comprehensive way to validate email addresses. You can download this class from www.phpclasses.org/browse/file/28.html and save the file locally as email_validation.php .

Manuel's class validates an email address not only by checking that its format is correct but also by performing a domain name lookup to ensure that it can be delivered. It even connects to the remote mail server to make sure the given mailbox actually exists.

+   **DomainLookups** If you are following this example on a Windows-based web server, you need to download an additional file, getmxrr.php , to add a suitable domain name lookup function to PHP. You can download this file from www.phpclasses.org/browse/file/2080.html .

The email_validation.php script defines a class called email_validation_class , so you first need to create a new instance of a validator object called $validator , as follows:

```
$validator = new email_validation_class;
```

You can set a number of properties for your new class. Some are required in order for the class to work properly, and others allow you to change the default behavior.

Each object instance requires you to set the properties that contain the mailbox and domain parts