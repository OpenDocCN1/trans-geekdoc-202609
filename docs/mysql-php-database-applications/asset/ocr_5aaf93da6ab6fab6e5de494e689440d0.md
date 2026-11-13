few functions that retrieve information about the defined objects, classes, and methods. Here they are.

# is_a()

Use this function to determine whether a given object is an instance of a given class or an instance of a class descended from the given class. Specify the object in the first argument and the class name in the second; the function will return TRUE if the one is an instance of the other.

```
bool is_a (object object, string class_name)
```

# is_object()

This function, much like the other is_ functions, returns TRUE if the argument is an object, and FALSE otherwise.

```
bool is_object (mixed var)
```

# get_class()

Given an object, this function returns the name of the class of which the object is an instance.

```
string get_class (object obj)
```

# get_object_vars()

Given an object, this function returns an associative array containing the object's current properties.

```
array get_object_vars (object obj)
```

# method_exists()

Given an object and a method name, this function returns TRUE if the method (function) is defined for the object.

```
bool method_exists (object object, string method_name)
```

# Print functions

Several functions enable you to print information to the screen. Only two pop up in this book, but you should be aware of all the functions listed in this section.

# PRINT FUNCTIONS USED IN THIS BOOK

In this case the word “functions” may be something of a misnomer. For instance, print() is probably better described as a language construct. (The useful difference