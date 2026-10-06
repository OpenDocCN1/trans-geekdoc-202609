# Part II: Learning the Language

+   - Private properties of a class can be accessed only by code inside the class. If you create a property that's declared private, only methods inside the same class can access its contents. (If you attempt to access the property outside the class, PHP generates a fatal error.)

+   - Protected class properties are like private properties in that they can't accessed by code outside the class, but there is one subtle difference: any class that inherits from the class can access the properties. (You learn about inheritance later in the chapter.)

Generally speaking, it's a good idea to avoid creating public properties where possible. Instead, it's safer to create private properties, then to create methods that allow code outside the class to access those properties. This means you can control exactly how your class's properties are accessed. You learn more about this concept later in the chapter. In the next few sections, though, you work most with public properties, because these are easiest to understand.

# Declaring Properties

To add a property to a class, first write the keyword public, private, or protected — depending on the visibility you want to give to the property — followed by the property's name (preceded by a $ symbol):

```
class MyClass {
    public $property1; // This is a public property
    private $property2; // This is a private property
    protected $property3; // This is a protected property
}
```

By the way, you can also initialize properties at the time that you declare them, much like you can with variables:

```
class MyClass {
    public $widgetsSold = 123;
}
```

In this case, whenever a new object is created from MyClass, the object's $widgetsSold defaults to the value 123.

# Accessing Properties

Once you've created a class property, you can access the corresponding object's property value from within your calling code by using the following syntax:

```
$object->property;
```

That is