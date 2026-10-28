# How to create a class constant

# A class with three class constants

```
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
```

# Use the constant outside the class

```
```php
$person = new Person();
$person->setEyeColor(Person::GREEN_EYES);
```
```

# Description

+   - A *class constant* is a constant value that belongs to the class, not to objects created from the class.
+   - To access a constant that belongs to a class, you can code the name of the class followed by a double colon. This double colon is known as the *scope resolution operator*. It is also known as the *Paamayim Nekudotayim*, which means double colon in Hebrew.
+   - Inside a class, you can access a class constant by coding the self keyword followed by a double colon and the class constant name.
+   - Outside the class, you can access a class constant by coding the class name followed by a double colon and the class constant name.
+   - Class constants are always public. You can’t use the public, private, or protected keywords with them.
+   - Class constants are typically used for defining a set of options that are passed to methods in the class.

Figure 14-7 — How to code class constants