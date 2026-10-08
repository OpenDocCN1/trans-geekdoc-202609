# Core PHP Programming

even default values. You can set up classes that allow you to create an object and set all its properties in one statement. Unlike other languages, PHP does not allow for destructors—functions that execute when the instance is deleted. However, if you choose to use unset on an object, the memory associated with that object will be freed. In situations where you must execute some code when you finish using an object, create your own shutdown function and remember to call it.

One powerful aspect of classes is inheritance, the idea that a class can extend the functionality of another class. The new class will contain all the methods and properties of the class it extends, plus any others it limits within its body. You may also override methods and properties from the extended class. As shown in Figure 6-1, you extend a class using the extends keyword.

Listing 6.1 Using Classes