# Controlling Access with private and public

PHP uses access modifiers. To control the visibility of attributes and methods, and are placed in front of attribute and method declarations. PHP supports the following three different access modifiers:

+   - The default option is public, meaning that if you do not specify an access modifier for an attribute or method, it will be public. Items that are public can be accessed from inside or outside the class.
- The private access modifier means that the marked item can be directly accessed only from inside the class. In most cases, you will want to make all class attributes private. You may also choose to make some methods private, for example, if they utility functions for use inside the class only. The items that are private will not be inherited (on this issue in this chapter).
- The protected access modifier means that the marked item can be accessed only from inside the class. It also exists in any subclasses; we will return this when we discuss inheritance in this class. For now, you can think of protected as being halfway between private and public.

The following code shows the use of the public and private access modifiers: class manners

```
private $greeting = 'Hello';
public function greet($name) {
    echo $this->greeting, $name;
}
```

Here, each class is faced with an access modifier to show whether it is private or public. You could leave out the public keyword because it is the default, but the code is easier to understand with it in if you are using the other modifiers.

# Writing Accessor Functions

It is not generally a good idea to access attributes from outside a class. One of the advantages of an object-oriented approach is that it encourages encapsulation. You can enforce this with the use of _get and _set functions. If, instead, of accessing the attributes of a class directly, you make your attributes private or protected and write accessor functions, you can make all your accesses through a single section of code. When you initially write your accessor functions, they might look as follows:

```
class class {
    private $attribute;
```