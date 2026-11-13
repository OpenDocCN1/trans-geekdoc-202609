+   - __hash__ (self): returns an integer hash value for the object, and is used in hashable collections such as sets and dictionaries; if you override __eq__, you should also override __hash__, ensuring that objects that are considered equal have the same hash value – see Section B4.1.6 for an explanation of what this means
+   - __lt__ (self, other), __le__ (self, other), __gt__ (self, other), __ge__ (self, other): used for comparison operators <, <=, > and >= respectively; they are used by the sorted() function and other areas where there is a concept of an ordering of objects
+   - __getitem__ (self, key), __setitem__ (self, key, value), __delitem__ (self, key): called to retrieve, set or delete an item using the indexing syntax obj[key]
+   - __iter__ (self) and __next__ (self): used to make an object iterable (usable in a FOR loop, for example); __iter__ should return an iterator object, which is typically the object itself, and __next__ should return the next item or raise StopIteration to end the iteration.

Refer to the Java and Python documentation for examples of implementing each of the methods above, as relevant.

# B3.2.3 Abstraction and abstract classes

One common way of making use of inheritance and polymorphism is through the use of abstract classes. Abstract classes can be thought of as generic templates without any executable code of their own. They are classes that cannot be instantiated. They are designed to be extended by other classes.

You use abstract classes when you know that all your subclasses should have certain methods or fields, but the implementation of these methods is inherently specific to each subclass, such that it doesn’t make logical sense to provide a default implementation.

While it doesn’t provide any functionality, the abstract class provides standardization and consistency in the implementation of subclasses; the benefit being that anyone using your class hierarchy will know that certain methods are always available, and any new derived classes need to adhere to the defined contract.

As an example, consider an application that needs objects to manage the properties of various 2D geometric shapes, such as a possible computer game. It makes sense to require that all classes that implement a 2D shape have a function that returns its surface area, and another that returns its perimeter. An abstract class of Shape can be defined that stipulates these requirements, as the following example demonstrates.

Notice that, because Python and Java can rely upon the contract associated with Shape, there is no problem creating code that executes getPerimeter() and getArea() on an array containing a mix of Rectangle and Circle objects.