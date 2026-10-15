# Example

```
```php
class A
{
    public static function test()
    {
        echo "This is static function";
    }
    public function hello()
    {
        self::test();   // Calling a static function using self and ::
    }
}
```
```

**Static Properties or Variables:** Just like static functions or
methods, You can also access static properties or variables in the
same way using :: operator. Example

```
```php
<?php
class A
{
    public static $rating = 7;  // Static propertys / Member variable
    public function __construct()
    {
        echo "Rating is" . self::$rating;  // Accessing static variable
    }
}
```
```