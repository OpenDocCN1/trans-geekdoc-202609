# Encapsulation: protecting data and methods

In PHP object-oriented programming, encapsulation refers to the grouping of data (properties, etc.) and the actions used to manipulate them within a class.

Encapsulation is very important for limiting access to properties from outside the class. To determine who can access the various properties, methods and constants of our classes, we use access limiters, also known as visibility levels, represented by the keywords public, private and protected.

# Principles of encapsulation :

Encapsulation concerns the visibility and accessibility of class properties and methods.
When creating a new class, it's crucial to determine which properties and methods must be accessible from outside the class.

As we saw in the previous chapter, properties, methods or constants defined with the **public** keyword are accessible everywhere, both inside and outside the class. Properties, methods or constants defined with the **private** keyword can only be accessed inside the class that defined them.

In the upcoming chapter on inheritance, we'll discover that properties, methods or constants defined with the **protected** keyword are accessible inside the class that defined them, as well as in child classes that inherit from this class or in the parent class itself.

By convention, attributes are declared as private, as it is risky to access a class attribute directly. To access these attributes, we use public methods.

In most cases, we define our methods with the keyword public and our properties with the keywords