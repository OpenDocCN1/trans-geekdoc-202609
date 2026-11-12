# # Good and Bad Practices

When working with classes and objects, it’s a good idea to use references whenever an object is involved. Occasionally, you may have to do the same with an array, such as when you want to sort the array in a different section of code. But, for the most part, normal variables will not need this treatment, simply because, when your code reaches the level of complexity where you’d need to do so, you will (I hope!) be storing variables inside objects and passing the complete object by reference.

Let’s look at some other situations in which you might need to use references...

```
```php
// Make sure $myObject is a reference to
// the variable created by the new keyword
$myObject = &new MyClass();
```
```

This looks odd at first, but remember, a variable created by the new keyword is being passed here—even if you can’t see it. The reference operator saves PHP from having to create a copy of the newly-created object to store in $myObject.

```
```php
class Bar {
}

class Foo {
    // Return by reference
    function &getBar()
    {
        return new Bar();
    }
}

// Instantiate Foo
$foo = &new Foo();

// Get an instance of Bar from Foo
$bar = &$foo->getBar();
```
```

In the above example, you’ll notice the getBar method in the Foo class. By preceding the function name with the reference operator, the value the function returns is passed by reference. Note that we also had to use a reference operator when assigning the return value of getBar to $bar. This technique is commonly used when a class method will return objects.

What’s bad practice is the following: