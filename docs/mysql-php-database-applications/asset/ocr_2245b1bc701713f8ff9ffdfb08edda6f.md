```
return <<<EOT
<font style="${this->style()}">${this->_text}</font>
EOT;
]
]
```

Before you get to using objects, however, we want to explain a couple of the advantages of this object-oriented approach. Suppose some programmer has created an object and tells you about its methods and properties. You don’t really need to know how any of it works; you just need to know that it does. You can make use of the methods and properties of the object in your scripts with little effort.

Of course, the same could be said of a well-designed procedural approach. A well-documented collection of functions can work equally well. Time was when objects in PHP weren’t much more than collections of function libraries and arrays that used little arrows instead of square brackets. That has changed dramatically with PHP 5, and the language is now much closer to other object-oriented languages like Java. However you look at it, you should be able to write good procedural code before you move on to objects.

By using objects, not only can you make use of methods and properties in the heart of your scripts, but also you can extend the functionality of a class in a number of different ways, with one of the most basic being the use of a concept called inheritance. Going back to the previous example, for example, an image and a table both might have a height and a width. We can create a class called a Rectangle that knows about heights and widths and then have our Image class and Table class inherit Rectangle, automatically being able to make use of all its properties and methods. (In object terminology, we call Rectangle the parent class, and Image and Table are both children.)

There’s a lot more to object-oriented programming (or OOP for short – not to be confused with OOPS, which is the kind of programming we’re trying to avoid) than just inheritance, though. We can’t do full justice to the topic here, but we’ll try to cover some of the basics.

# Classes, Continued

In object-oriented programming, you work with classes and objects. A class is a definition describing properties and methods, while an object is a variable that has those properties and can use those methods. You could think of the blueprints for the chair you’re sitting in now as a kind of Chair class. That would make your actual chair an object, or instance, of the Chair class. If your chair came from a factory, there might be thousands of Chair instances out there in the world, but still only one Chair class.

You can use a few different kinds of classes. Let’s start out our small example with one of the most minimal kinds of classes, an interface.