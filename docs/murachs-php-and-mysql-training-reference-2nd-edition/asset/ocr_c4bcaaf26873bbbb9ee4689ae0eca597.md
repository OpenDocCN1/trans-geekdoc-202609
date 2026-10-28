# How to pass one function to another

# A variable function

```
```php
$function = (mt_rand(0,1) == 1) ? 'array_sum' : 'array_product';
$values = array(4, 9, 16);
$result = $function($values);    // 29 for array_sum, 576 for array_product
```
```

# A function that uses a callback

```
```php
function validate($data, $functions) {
    $valid = true;
    foreach ($functions as $function) {
        $valid = $valid && $function($data);
    }
    return $valid;
}

function is_at_least_18($number) {
    return $number >= 18;
}

function is_less_than_62($number) {
    return $number < 62;
}

$age = 25;
$functions = array('is_numeric', 'is_at_least_18', 'is_less_than_62');
$is_valid_age = validate($age, $functions);    // true
```
```

# Language constructs that can’t be used in variable functions

+   - die
+   - echo
+   - empty
+   - exit
+   - eval
+   - include
+   - include_once
+   - isset
+   - list
+   - require
+   - require_once
+   - return
+   - print
+   - unset

# Description

+   - A *variable function* is a function name stored in a variable as a string. When PHP encounters a variable function, it evaluates the variable and attempts to call the function.
+   - To call a variable function, code the variable name followed by a set of parentheses. Within the parentheses, code the argument list for the function.
+   - You can use a variable function when the function isn’t known until runtime.
+   - You can use a variable function in a function that uses a callback. A *callback* is a function that’s passed as an argument to another function.
+   - You can’t use the language constructs listed above with variable functions directly. However, you can use a wrapper function that calls one of these constructs in a variable function.

Figure 13-9 How to work with variable functions