

```php
$sum = $val_1 + $val_2;
}
assign_to_global(5,6);
echo $sum;
```

This script prints 11. For something a bit more complicated, we borrow the following function from the applications section of the book:

```php
function set_result_variables ($result)
{
    if (!$result) { return; }
    $row = mysql_fetch_array($result,MYSQL_ASSOC);
    while (list($key,$value) = each($row))
    {
        global $$key;
        $$key = $value;
    }
}
```

This function expects a result identifier gathered by mysql_query() in an earlier function. Assume that the query run prior to this function call returns a single row. That row is then assigned to an associative array named $row. Then each column taken from the query (which is now the key in the associative array) and its value are available as a global. This availability can be useful if the values retrieved from the query are needed in many other functions. However, beware of having columns with the same names as PHP variables – particularly global variables. You should try to not let that happen, lest conflicts occur.

Global variables are used sparingly within functions throughout the applications in this book. This is because it is easier to keep track of your variables if you are passing them through arguments and retrieving them through return values. If you start using globals extensively you might find that your variables are returning unexpected values in different places – and finding the functions that are causing the error can be a major pain.

Here's another reason to avoid globals when possible: You will be using the same variable names over and over and over again. We don't know how many times in these applications the variable names $query, $result, $row, or $i are used, but trust us when we say that they are used frequently. All kinds of hassle are introduced if you have to keep track of each time you use a variable name.

At times you have little choice but to use global variables, but before you do, make sure that you can't accomplish what you're trying to do using variables of local scope.

## Object-Oriented Programming

A few years back there was a large move toward object-oriented programming. Some people thought that the procedural approach – that is, coding strictly with functions – just wasn't enough. Therefore, the folks working on languages like C++ and Java popularized an approach that enables a developer to think about code in a different way.

The idea behind object-oriented programming is to think of portions of your application as objects. What is an object? Well, it's an amorphous thing, a kind of black box – a superstructure of variables and functions. But if you are new to the concept, this description may not be so clear.

To make things clearer conceptually, we provide a few examples. In our examples, our objects are things that can be displayed as part of a Web page. For each of the different kinds of elements of a page, you might want to know different things. If you're displaying an image, for example, you might want to know how wide it is. For an HTML table, you might want to know if it has a color. By treating the elements as objects, you can effectively ask them how wide they are or what color they are without having to dig inside them to find out yourself. You can also tell the elements to do things, like draw themselves on the page.

Now all you need is the correct nomenclature. Descriptions of the object (such as width and color) are called *properties*, and descriptions of the actions an object can take (such as draw) are known as *methods*. Some methods are a bit of both, and you can think of them as descriptions of the questions you can ask the object–a `width()` method might tell you how wide the object is and whether it has one property named `width` or a dozen different properties that it has to add together first. And as it happens, in the actual code of a class, you use the word `function` just as you would in a regular user-defined function, so you might hear both terms used interchangeably. Here's an example of what a PHP class looks like:

```php
class TextBox
{
    var $_text;

    function TextBox($text)
    {
        $this->_text = $text;
    }
    function style()
    {
        return "font-family:'Helvetica Neue',Helvetica,sans-serif;";
    }
    function text()
    {
        return <<<EOT
<font style="${this->style()}">${this->_text}</font>
EOT;
    }
}
```

Before you get to using objects, however, we want to explain a couple of the advantages of this object-oriented approach. Suppose some programmer has created an object and tells you about its methods and properties. You don't really need to know how any of it works; you just need to know that it does. You can make use of the methods and properties of the object in your scripts with little effort.

Of course, the same could be said of a well-designed procedural approach. A well-documented collection of functions can work equally well. Time was when objects in PHP weren't much more than collections of function libraries and arrays that used little arrows instead of square brackets. That has changed dramatically with PHP 5, and the language is now much closer to other object-oriented languages like Java. However you look at it, you should be able to write good procedural code before you move on to objects.

By using objects, not only can you make use of methods and properties in the heart of your scripts, but also you can extend the functionality of a class in a number of different ways, with one of the most basic being the use of a concept called inheritance. Going back to the previous example, for example, an image and a table both might have a height and a width. We can create a class called a Rectangle that knows about heights and widths and then have our Image class and Table class inherit Rectangle, automatically being able to make use of all its properties and methods. (In object terminology, we call Rectangle the parent class, and Image and Table are both children.)

There's a lot more to object-oriented programming (or OOP for short – not to be confused with OOPS, which is the kind of programming we're trying to avoid) than just inheritance, though. We can't do full justice to the topic here, but we'll try to cover some of the basics.

## Classes, Continued

In object-oriented programming, you work with classes and objects. A class is a definition describing properties and methods, while an object is a variable that has those properties and can use those methods. You could think of the blueprints for the chair you're sitting in now as a kind of Chair class. That would make your actual chair an object, or instance, of the Chair class. If your chair came from a factory, there might be thousands of Chair instances out there in the world, but still only one Chair class.

You can use a few different kinds of classes. Let's start out our small example with one of the most minimal kinds of classes, an interface.

## INTERFACES

```php
interface Color
{
    public function color();
}
interface Drawable
{
    public function draw($return=false);
}
interface Rectangle
{
    public function height();
    public function width();
}
```

Not much code here. But then that's the point— an interface isn't about how you will do something, so much as what you will be able to do. An interface is like a promise: Any class that builds on the Color interface, for example, swears that it will have a method named color() with no arguments that you will be able to call. In this case, we're not promising anything about what that method will do (or what it will return to you, for that matter). But if you're dealing with an object that has Color in its background, you know that you'll be able to call $object->color() and get some kind of response.

So what does that get you besides a new buzzword? Well, without claiming to describe all of the benefits, here are a couple of basic ones.

In PHP, normal classes are inherited, while interfaces are implemented, like so:

```php
class AlertBox extends TextBox implements Color, Rectangle
```

Here, extends means that the AlertBox class is inheriting the properties and methods of the TextBox class. You can inherit only from a single class in PHP, but you can implement as many interfaces as you like. The benefit comes from the fact that you can tell if a particular object implements the interface in which you're interested, using the instanceof operator. Say that you've got a section of code that doesn't care about anything but rectangles. Circles, triangles, lines of text—let somebody else deal with those; we just want rectangles. You can make that work like this:

```php
if ($object instanceof Rectangle)
{
    $width = $object->width();
    $height = $object->height();
}
```

