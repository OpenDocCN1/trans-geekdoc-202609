
## How to create an object

### The syntax

```
$objectName = new ClassName(argumentList);
```

### Create a Category object

```php
$brass = new Category(4, 'Brass');
```

### Create a Product object

```php
$trumpet = new Product($brass, 'Getzen', 'Getzen 700SP Trumpet', 999.95);
```

## How to access an object’s properties

### The syntax for setting a public property value

```
$objectName->propertyName = value;
```

### The syntax for getting a public property value

```
$objectName->propertyName;
```

### Set a property

```php
$trumpet->comment = 'Discontinued';
```

### Get a property

```php
echo $trumpet->comment;
```

## How to call an object’s methods

### The syntax

```
$objectName->methodName(argumentList);
```

### Call the getFormattedPrice method

```php
$price = $trumpet->getFormattedPrice();
```

### Object chaining

```php
echo $trumpet->getCategory()->getName();
```

### Description

- An object is an *instance* of a class. In other words, you can create more than one object from a single class. The process of creating an object from a class is sometimes called *instantiation*.
- To create an object, you code the `new` keyword followed by the name of the class and a set of parentheses. Inside the parentheses, you code the arguments for the constructor separated by commas.
- To access an object’s property, you code a reference to the object followed by the object access operator (`->`) and the name of the property.
- To call an object’s method, you code a reference to the object followed by the object access operator (`->`), the name of the method, and a set of parentheses. Inside the parentheses, you code the arguments for the method separated by commas.
- If a function or method returns an object, you can use the function or method call as a reference to the object and continue accessing the returned object’s properties and methods. This is called *object chaining*.

## How to code class constants, properties, and methods

So far, this chapter has shown how to define the properties and methods of an object that is created from a class. As a result, you must create an object from the class before you can access these properties and methods. Now, you’ll learn how to define constants, properties, and methods that you can access directly from the class.

### How to code class constants

Figure 14-7 shows how to create and use *class constants*. A class constant is a constant that is defined in a class. All class constants are public. As a result, they are available to code outside the class. In addition, class constants belong to the class, not the object. As a result, you can access class constants directly from the class without creating an object from the class first.

Class constants are often used to provide a set of fixed values for an option. In this figure, for example, the Person class defines three constants for eye color: GREEN_EYES, BLUE_EYES, and BROWN_EYES. Using constants to define a set of fixed values helps eliminate errors by forcing the programmer to specify one of the fixed values. In this figure, for example, the setEyeColor method only accepts one of these three constants.

To create a class constant, you code the const keyword followed by the constant name, an equals sign, and a scalar value. Then, to refer to the constant inside the class declaration, you code the self keyword followed by the double colon and the name of the constant. This keyword is a reference to the current class. To refer to the constant outside the class declaration, you code the name of the class followed by a double colon and the name of the constant.

The double colon is also known as the *scope resolution operator*. However, some error messages may refer to the double colon as *Paamayim Nekudotayim*, which means double colon in Hebrew. This term crept into the PHP error messages because the internal PHP code was developed in Israel.

Within the Person class, the setEyeColor method checks whether the value of its parameter is one of the three accepted values. If so, the property is set. Otherwise, the method exits with an error message.

Outside the Person class, the second example begins by creating a Person object. Then, it calls the setEyeColor method and passes one of the class constants as an argument to the method. Here, an integer value of 1 could also have been used, but if the value of the constant were changed later, the call to the setEyeColor method would no longer work.

### How to create a class constant

**A class with three class constants**

```php
class Person {
    const GREEN_EYES = 1;
    const BLUE_EYES = 2;
    const BROWN_EYES = 3;

    private $eye_color;

    public function getEyeColor() {
        return $this->eye_color;
    }

    public function setEyeColor($value) {
        if ($value == self::GREEN_EYES || $value == self::BLUE_EYES ||
            $value == self::BROWN_EYES) {
            $this->eye_color = $value;
        } else {
            exit('Eye Color Not Set');
        }
    }
}
```

**Use the constant outside the class**

```php
$person = new Person();
$person->setEyeColor(Person::GREEN_EYES);
```

### Description

- A *class constant* is a constant value that belongs to the class, not to objects created from the class.
- To access a constant that belongs to a class, you can code the name of the class followed by a double colon. This double colon is known as the *scope resolution operator*. It is also known as the *Paamayim Nekudotayim*, which means double colon in Hebrew.
- Inside a class, you can access a class constant by coding the self keyword followed by a double colon and the class constant name.
- Outside the class, you can access a class constant by coding the class name followed by a double colon and the class constant name.
- Class constants are always public. You can’t use the public, private, or protected keywords with them.
- Class constants are typically used for defining a set of options that are passed to methods in the class.

*Figure 14-7 — How to code class constants*

### How to code static properties and methods

Figure 14-8 shows how to use static properties and static methods. Since static properties and methods belong to the class, not to an object, they are also known as class properties and class methods. In this sense, static properties and methods are similar to class constants.

There are two main differences between class constants and static properties and methods. First, when you declare a static property or method, you can use an access modifier such as public or private. Second, since a static method doesn’t belong to an object, you can’t use the $this variable inside a static method to get the current object. However, you can use the self keyword to access the current class. As a result, a static method can only work with other static methods, properties, and class constants.

The Category class in this figure begins by declaring a static property named $objectCount to count the number of objects created from this class. Here, the code uses the static keyword to specify that this property is static. In addition, the code initializes this property to a value of zero. This shows that you can specify an initial value for a static property. However, the initial value must follow the same rules as an initial value for an object property. In other words, it must be a scalar value, an array of scalar values, or NULL.

Within the constructor, the static $objectCount property is incremented by one. As a result, this property indicates how many objects have been created from the Category class.

The static method named getObjectCount returns a count of the objects created. This provides a public way to get the value stored in the private $objectCount property.

Inside a class, you can access a static property or method by coding the self keyword followed by a double colon and the name of the static property or method. Note, however, that static property names are preceded by a dollar sign and static methods are not.

Outside a class, you can access the public static properties and methods by coding the class name followed by a double colon and the name of the static property or method. Again, static property names are preceded by a dollar sign and static methods are not.

When you call a static method from within a class, you can access all properties and methods even if they are private or protected. However, when you call a static method from outside a class, you can only access the public properties and methods.

The second example shows how to use a static method. Here, the first two statements create two objects from the Category class. Then, the third statement calls the static getObjectCount method to display the count. Finally, the last two statements create a third object and display the count again.

The third example shows how to code a public static property. For this code to work, however, the $objectCount property would need to be coded as public instead of private.
