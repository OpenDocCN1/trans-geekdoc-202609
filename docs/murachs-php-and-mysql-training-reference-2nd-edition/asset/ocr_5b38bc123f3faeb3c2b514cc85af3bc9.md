# How to inspect an object

Figure 14-12 shows how to inspect an object. This is known as *introspection* or *reflection*. To start, this figure summarizes some of the methods that are used to inspect an object. These methods are often used in functions and methods to check if an object parameter is of the expected type. In addition, they can be used to make sure a property or method exists before it’s called.

The first example shows how to use the is_a function. To start, an if statement checks whether the $trumpet object is an instance of the Product class. If so, this example executes code that works with a Product object.

The second example shows how to use the property_exists function. To start, an if statement checks whether the $trumpet object has a price property. If so, this example executes code that uses the price property.

The third example shows how to use the method_exists function. To start, an if statement checks whether the $trumpet object has a getPrice method. If so, this example executes code that uses the getPrice method.

When you use the property_exists and method_exists methods, you should be aware that they both return TRUE for properties and methods whether they are public, protected, or private. However, you may not be able to call properties and methods if they are protected or private, even though they exist.

The functions presented in this figure provide only a brief introduction to the reflection capabilities of PHP. Beyond this, PHP 5 provides comprehensive reflection capabilities that allow you to get any information you want about an object. However, this information is primarily used in debugging very large applications. To learn more about reflection, you can visit the URL shown at the top of this figure.