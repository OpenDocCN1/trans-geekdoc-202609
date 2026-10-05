# 6.1.1 PHP Objects vs. Classes

In the real world, an object has its own characteristics and behaviors. We can group similar objects with the same characteristics and behaviors in into one class. So we can say that a class is a blueprint of the objects. See the image below:

![](bbox=[0.173, 0.279, 0.545, 0.467])

From the same Car class, we created three individual objects with the name of: Mercedes, Bmw, and Audi.

Although all of the objects were created from the same class and thus have the class's methods and properties, they are still different. This is not only, because they have different names, but also because they may have different values assigned to their properties. For example, in the image above, they differ by the color property - the Mercedes is green while the Bmw is blue and the Audi is orange.

>  

Notice that the getter and setter names, match the associated property name.

# 6.1.2 Defining Classes and Objects

Before creating any new object, you need a class or blueprint of the object. It is pretty easy to define a new class in PHP. To define a new class in PHP you use the class keyword as the following example: