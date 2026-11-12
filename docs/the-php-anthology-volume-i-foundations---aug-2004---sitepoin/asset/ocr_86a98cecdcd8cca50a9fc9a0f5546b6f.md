In simple cases of copying one variable to another PHP's internal **reference counting** feature prevents unnecessary memory usage. For example,

```
```php
$a = 'the quick brown fox';
$b = $a;
```
```

In the above example, the value of `$b` would not take up any extra memory, as PHP's internal reference counting will implicitly reference `$b` and `$a` to the same location in memory, until their values become different. This is an internal feature of PHP and affects performance without affecting behavior. We don't need to worry about it much.

In some cases, however, using a reference _is_ faster, especially with large arrays and objects, where PHP's internal reference counting can't be used. and the contents must therefore be copied.

So, for best performance, you should do the following:

+   - With simple values such as integers and strings, avoid references whenever possible.

+   - With complex values such as arrays and objects, use references whenever possible.

# ## References and PHP 5

With PHP 5, references will cease to be an issue because the default behavior of PHP, when passing objects, will be to pass by reference. If you ever need a copy of an object, you can use the special __clone method to create copies.

Essentially, the change brings PHP in line with the majority of object oriented programming languages like Java, and will certainly do a lot to reduce the confusion surrounding the subject. For now, though, and until PHP 5 has been widely adopted, knowing how references work is important.

# ## How do I take advantage of inheritance?

**Inheritance** is one of the fundamental pieces of the object oriented paradigm and is an important part of its power. Inheritance is a relationship between different classes in which one class is defined as being a child or subclass of another. The child inherits the methods and member variables defined in the parent class, allowing it to “add value” to the parent.