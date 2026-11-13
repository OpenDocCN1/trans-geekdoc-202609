To write the same code without the concept of an interface, you'd have to do something like this:

```
$methods = get_class_methods($object);
if (in_array('width', $methods) and in_array('height', $methods))
{
    $width = $object->width();
    $height = $object->height();
}
```

Even then, you don't know if that object's width() method is going to require an argument that you can't supply. Plus, clearly, this is going to be a lot slower to run. The Rectangle interface tells you very simply that this is a proper Rectangle that knows how to respond to a decent width() call, regardless of what other kinds of foolishness it might get up to somewhere else.

Another benefit of using interfaces can come when you have multiple people working on different parts of the same project. By laying out a set of interfaces as the first step, each person can write code that will call on the other classes being built by other people, whether or not those other classes have actually been written yet, and without worrying about how they're going to work when they are written.

We can take that approach one step further, to specific properties and methods, by moving on to inheritance and abstract classes.

# ABSTRACT CLASSES

An abstract class is sort of a blueprint's blueprint. It looks just like a regular class, because that's what it is, except for one difference: You can't make an object out of it. To add another $5 word to our pile, we can say that an abstract class cannot be instantiated — meaning that you can't create an instance of one, at least not directly.

Instead, abstract classes are there solely to be inherited. One way you can use them is as a place to put utility code — code that all of your classes will use, but that doesn't really have a purpose outside of the specific context of one of those classes. Maybe your abstract class has a method that does some complex mathematical calculations or one that picks one string at random from an array of strings.

PHP considers a class to be abstract if you explicitly declare the class that way — abstract class MyClass { ... } — or if one of the class's methods is declared to be abstract—abstract function some_function();. Another, indirect way of making a class abstract is by declaring that it implements an interface without supplying one or more of the methods that the interface defines. The effect is to shift the burden of supplying those required methods onto the class's children.

Here's another step in our example that shows what we mean: an abstract class that implements one of the interfaces we declared previously — except not really:

```
abstract class TextBox implements Drawable
{
```