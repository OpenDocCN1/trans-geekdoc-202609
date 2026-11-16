```
$item->display();
echo("<br><br>");
}
```

This code will display every media item sequentially, regardless of it being a CD, a movie, a book, or a software application. Even though there are differences in all the media subtypes, we can treat them similarly because they all have a `display()` method. Here the PHP script engine will figure out what needs to be done and display accordingly.

This code gives a clean, elegant looking solution when printing all the media items in our store. It’s much nicer than our bulky functional version we saw earlier. Let’s say we had to create a new subclass, called ConsoleGame. We would add a new subtype from the Media class and add some new instances of the ConsoleGame class to the `$mediaItems` array, and our solution to display all the media items above doesn’t have to change at all:

```
$mediaItems[] = new ConsoleGame(...);
foreach ($mediaItems as $item) {
    $item->display();
    echo("<br><br>");
}
?>
```

This will print out the existing list and also the newly added ConsoleGame object. Notice how the foreach statement did not have to change. Polymorphism enables us to write such maintainable code. Inheritance is really no good on its own. We use inheritance to take advantage of polymorphism to give us clean, maintainable code. Inheritance is not only a method for reusing code as stated above, but is also used to achieve polymorphism in application code. When we get into design patterns, we’ll see that a lot of problems can be simplified using inheritance and polymorphism.

# # Abstract Methods

When we use inheritance, often times the parent class will contain methods that have no code because it is impossible to specify common behavior. Therefore, we use a concept called an **abstract method** to indicate that a method contains no code and the implementer of any possible subtypes must implement the behavior for that method. If the method is not overridden (as discussed in the Inheritance section), it will continue to provide no behavior.

If you fail to define an abstract method and your subtypes do not override it, you will receive a PHP runtime error specifying that the method does not exist in the object. Therefore, it is important that you define all empty methods that you intend to have no behavior.

> In object-oriented terminology, abstract methods usually force the implementer to override the method. However, in PHP this is not the case due to limitations in its object-oriented features. Implementers of subtypes should look at the documentation for the class they want to create subtypes for to see what abstract methods are needed to be overridden to have a properly implemented subtype.