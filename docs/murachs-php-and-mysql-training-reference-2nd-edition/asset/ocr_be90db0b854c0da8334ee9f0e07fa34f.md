# How to code a method

# The syntax

```
```php
[public | private | protected] function functionName ([parameterList]) {
    // Statements to execute
}
```
```

# A public method

```
```php
public function getSummary() {
    $maxLength = 25;
    $summary = $this->description;
    if (strlen($summary) > $maxLength) {
        $summary = substr($summary, 0, $maxLength - 3) . '...';
    }
    return $summary;
}
```
```

# A private method

```
```php
private function internationalizePrice($country = 'US') {
    switch ($country) {
        case 'US':
            return '$' . number_format($this->price, 2);
        case 'DE':
            return number_format($this->price, 2, ',', '.') . ' DM';
        default:
            return number_format($this->price, 2);
    }
}
```
```

# A method that accesses a property of the current object

```
```php
public function showDescription() {
    echo $this->description;
}
```
```

# A method that calls a method of the current object

```
```php
public function showPrice($country = 'US') {
    echo $this->internationalizePrice($country);
}
```
```

# Description

+   - To code a method in a class, you code one of the access modifier keywords followed by the function keyword, the name of the method, an optional parameter list in a set of parentheses, and a block of code to execute.
+   - By default, methods are public. As a result, if you omit the access modifier, the method is public. However, to make your code more consistent and readable, it’s generally considered a good practice to code an access modifier for all methods.