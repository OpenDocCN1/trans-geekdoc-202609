# 6.2 CREATING AN OBJECT

It is much easier to create objects and use them than it is to define object classes, so before we discuss how to define classes, let's look at creating objects. To create an object of a given class, use the new keyword:

```
$object = new Class;
```

Assuming a Person class has been defined, here's how to create a Person object:

$srasmus = new Person;

Do not quote the class name, or you'll get a compilation error:

```
$srasmus = new ‘Person’; // does
not work
```

Some classes permit you to pass arguments to the new call. The class’s documentation should say whether it accepts arguments. If it does, you’ll create objects like this:

```
$object = new Person('Fred’, 35);
```

The class name does not have to be hardcoded into your program. You can supply the class name through a variable:

```
$class = ‘Person’;
```

```
$object = new $class;
```

// is equivalent to

```
$object = new Person;
```

Specifying a class that doesn’t exist causes a runtime error.

Variables containing object references are just normal variables—they can be used in the same ways as other **variables**. Of particular note is that variable variables work with objects, as shown here:

# Remember

You enclose a class using curly braces { } } ... just you do with functions.