# Working with PHP Object-Oriented Programming

```
$orphan = new Orphan();
$orphan->testid(103);
echo test($orphan) . PHP_EOL;
} catch (TypeError $e) {
echo 'Does not work!' . PHP_EOL;
echo $e->getMessage();
}
```

We can observe this in the following image:

![](bbox=[0.23, 0.29, 0.77, 0.54])

# Using static properties and methods

PHP lets you access properties or methods without having to create an instance of the class. The keyword used for this purpose is **static**.

# How to do it...

+   1. At its simplest, simply add the *static* keyword after stating the visibility level when declaring an ordinary property or method. Use the *self* keyword to reference the property internally:

```
class Test
{
public static $test = 'TEST';
public static function getTest()
{
```