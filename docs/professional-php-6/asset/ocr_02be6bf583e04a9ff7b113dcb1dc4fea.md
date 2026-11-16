# # Changes to OO in PHP 6

Support for objects in PHP goes all the way back to PHP 3. There was never any intention of supporting the idea of classes or objects, but some limited support was added, almost as an afterthought, to provide “syntactic sugar” (to use Zeev Suraski’s phrase) for associative arrays. Object support in PHP was originally designed as a convenient way of grouping data and functions, but only a small subset of the features traditionally associated with a full-blown object-oriented programming language was included. As PHP grew in popularity, the use of an OO approach became increasingly common in large applications. However, the poor internal implementation became limiting.

Most notably, there was no support for real encapsulation. You could not specify member variables or methods to be private or protected. Everything was public — which, as you’ve seen, can be problematic.

Additionally, there was no support for abstract interfaces or methods. Methods and member variables could not be declared static. There were no destructors. All these concepts are familiar to anyone with a background in another OOP language, and the lack of these features in PHP’s object model could make the transition from a language such as Java (which does support all these ideas) to PHP difficult. For those who have previous experience with PHP 4, Table 1-1 lists some of the new features in the PHP

# Table 1-1: Object Model Evolution from PHP 4 to PHP 5 and 6

| New Feature | Benefit |
| :--- | :--- |
| Private, protected member variables and methods | Real encapsulation and data protection are now possible in PHP. |
| Improved dereferencing support | Statements such as `$obj->getSomething()->doSomething()` are now possible. |
| Static member variables and methods | Methods that can be called statically are now clearly identifiable. Class-level constants help control pollution of the global namespace. |
| Unified constructors | All class constructors are now called `__construct()`. This helps with encapsulation of overridden subclass constructors, and makes it easier to alter inheritance when multiple classes are involved in a tree of inheritance. |
| Destructor support | Through the `__destruct()` method, classes in PHP can now have destructors. This feature allows actions to be carried out when the object is destroyed. |
| Support for abstract classes and interfaces | You can define required methods in a parent class while deferring implementation to a subclass. Abstract classes can’t be instantiated; only their non-abstract subclasses can. |
| Parameter type hints | You can specify the class for function parameters that are expecting an object. `function foo(Bar $objBar) { ...` allows you to be sure that the data type of the parameter is what you expect. |