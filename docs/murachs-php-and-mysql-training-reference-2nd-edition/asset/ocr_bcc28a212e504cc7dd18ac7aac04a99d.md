# How to code a property

# The syntax

```
```php
[ public | protected | private ] $propertyName [ = initialValue ];
```
```

# A private property

```
```php
private $firstName;
```
```

# A public property with a default value

```
```php
public $comment = '';
```
```

# A protected property

```
```php
protected $counter;
```
```

# Five properties on the same line

```
```php
private $category, $id, $name, $description, $price;
```
```

# Description

+   - A *public property* can be directly accessed by code outside of the class.
+   - *Private* and *protected* properties can’t be directly accessed by code outside the class.
+   - By default, properties are public. As a result, if you omit the access modifier, the property is public.
+   - To code an initial value for a property, you must supply a scalar value, an array of scalar values, or NULL. A *scalar value* is a literal number, string, or Boolean value.
+   - To code multiple properties on the same line, you can separate the property names with commas.

Figure 14-3　How to code properties