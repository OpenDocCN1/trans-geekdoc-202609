# How to assign a default value to a parameter

# A function with one default parameter

```
```php
function get_rand_bool_text($type = 'coin') {
    $rand = mt_rand(0, 1);
    switch ($type) {
        case 'coin':
            $result = ($rand == 1) ? 'heads' : 'tails';
            break;
        case 'switch':
            $result = ($rand == 1) ? 'on' : 'off';
            break;
    }
    return $result;
}
```
```

# A function with an optional parameter

```
```php
function is_leap_year($date = NULL) {
    if (!isset($date)) {
        $date = new DateTime();
    }
    if ($date->format('L') == '1') return true;
    else return false;
}
```
```

# A function with one required and two default parameters

```
```php
function display_error($error, $tag = 'p', $class = 'error') {
    $opentag = '<' . $tag . ' class="' . $class . '">';
    $closetag = '</' . $tag . '>';
    echo $opentag, $error, $closetag;
}
```
```

# Calling a function with a default parameter value

# Omitting optional parameters

```
```php
echo get_rand_bool_text();             // Displays 'heads' or 'tails'
echo display_error('Out of range');     // 'p' tag with error class
$is_leap_year = is_leap_year();         // true or false based on current date
```
```

# Providing optional parameters

```
```php
echo get_rand_bool_text('switch');                         // Displays 'on' or 'off'
echo display_error('Out of range', 'li');                  
$is_leap_year = is_leap_year(new DateTime('March 15, 2015')); // false
```
```

# Description

+   - To supply a default value for a parameter, code the parameter name followed by the equals sign and the default value. The default value must be a scalar value, an array of scalar values, or NULL. A *scalar value* is a literal number, string, or Boolean value. A scalar value cannot contain operators, variables, or function calls.
+   - To code a function that sets a default value for a parameter, assign NULL to the parameter. Then, within the function, you can check whether the parameter contains NULL. If so, you can write the code that sets the default value for the parameter.

Figure 13-4  How to provide default values for parameters