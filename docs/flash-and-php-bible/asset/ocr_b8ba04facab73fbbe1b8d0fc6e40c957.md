# # Multiple classes

PHP allows a class script to hold multiple classes. This is both a good and bad idea, because too many classes in one file result in bloated code that is hard to manage. On the other hand, having the classes all in one file makes it easier to distribute. I am sure you are asking yourself how exactly are multiple classes defined in one file; here is an example of a pseudo-class package.

```
<?php

class Animals
{
    function Animal ()
    {
    }
    public function speak($word)
    {
        print $word;
    }
}

class Dog extends Animals
{
    function Dog($word)
    {
        $this->speak($word);
    }
}

// Create a new Dog
$dog = new Dog("Hello... Woof!" );

?>
```

In fact, PHP really doesn't follow all of the standard OOP practices, which I think will change as newer versions are developed. For now, you can create your own version of a package and get the same basic functionality. It is important to note that a pseudo-package does not offer the same level of separation and security that a real package does, but with some creative programming and proper creation of your classes, you can keep the code secure.

> See Chapter 6 for more in-depth information on code security.

That is all there is to using and understanding classes in PHP, up to the point needed for this book. You can, of course, extend this newfound knowledge and start exploring the more advanced aspects of classes in PHP.

> PHP offers a lot of “magic” methods and properties that make classes more fun and less painful to work with.