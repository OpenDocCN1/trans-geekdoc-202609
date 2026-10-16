called `__autoload()` and put your autoloading code there. At some point in the future, `__autoload()` might be removed from PHP, so it is more forward compatible to use `spl_autoload_register()` instead.

**NOTE:** PHP also provides functionality for accessing class methods and class properties that do not exist:

+   - If a class method is called but does not exist, the class’s `__call()` method is executed, if it exists.
+   - If a class property is accessed but does not exist, the class’s `__get()` and `__set()` methods are executed (for read and write access), if they exist.

# Cloning Objects

```
```php
$b = clone $a;
```
```

Suppose you have a class instance in `$a`. The assignment `$b = $a` would not create a copy of `$a`, but `$b` would now contain a reference to `$a`; you would still have only one class instance.

As an alternative, PHP provides the clone keyword, which allows creating a copy of the class:

```
```php
$b = clone $a;
```
```

However, sometimes you do not want exact copies. For instance, imagine that each class instance has a property that contains a globally unique identifier (GUID). Even though you create a clone of a class instance, you want the GUID still to be as unique as possible.