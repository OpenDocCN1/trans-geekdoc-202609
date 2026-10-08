# Core PHP Programming

scripts with classes will certainly aid you in writing code that can be reused. This is a good idea, especially if you wish to share your code.

The idea of objects is one of those mind-blowing concepts in computer science. It's hard to grasp at first, but I can attest once you get it, it becomes quite natural to think in its terms. Never the less, you can ignore objects if you wish and return to this chapter later. Built-in functions return objects. You can find alternatives that don't, or you can cast the objects as arrays, as described at the end of this chapter.

# Defining a Class

When you declare a class, you are really making a template for the creation of objects. You list all the variables the object should have and all the functions it will need. Sometimes these are called properties and methods, Figure 6-1 displays the form of a class declaration. Note that the curly braces you only declare variables with the var statement or declare functions. Listing 6.1 shows the definition of a class with three properties and two methods

Figure 6-1. Defining a class.

```
class name extends another class
{
    var Variable Declaration
    Function Declaration
}
```

When you declare a property, you don't specify a data type. It is a variable like any other, and it may contain an integer, a string, or even another object. Depending on the situation, it might a good idea to add a comment near the declaration of the property that states its use and data type. When you declare a class, you do just so as you would a function outside a class definition. Methods and properties exist within their own scope, or name space. This means you can safely create methods that have the same name as functions declared outside class definitions without conflicts. Any exception to this are built-in functions. For example, you can have a print method.

Aside from variables passed as arguments, methods contain a special variable called this. It stands for the particular instance of the class. You must use this to refer to properties and other methods of the object. Some object-oriented languages assume an unqualified variable that refers to a local property, but in PHP any variables referred within a method are simply variables local to that. Note the use of the this variable in the constructor for the user in Listing 6.1.

If you choose to declare a function within a class that has the same name as the class itself, the function will be considered a constructor and will be executed immediately upon creating an object from that class. Typically the constructor is used to initialize the object's properties. Like any other function, the constructor may have parameters and