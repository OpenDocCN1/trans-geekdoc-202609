# How to create a closure

# An array of arrays

```
```php
$employees = array (
    array('name' => 'Ray',  'id' => 5685),
    array('name' => 'Mike', 'id' => 4302),
    array('name' => 'Anne', 'id' => 3674),
    array('name' => 'Pren', 'id' => 1527),
    array('name' => 'Joel', 'id' => 6256)
);
```
```

# A function to sort the array by any column

```
```php
function array_compare_factory($sort_key) {
    return function ($left, $right) use ($sort_key) {
        if ($left[$sort_key] < $right[$sort_key]) {
            return -1;
        } else if ($left[$sort_key] > $right[$sort_key]) {
            return 1;
        } else {
            return 0;
        }
    };
}
```
```

# Code that sorts the array by the name column

```
```php
$sort_by_name = array_compare_factory('name');
usort($employees, $sort_by_name);
```
```

# Code that sorts the array by the id column

```
```php
$sort_by_id = array_compare_factory('id');
usort($employees, $sort_by_id);
```
```

# Description

+   - *A closure* is an inner function that has access to the outer function’s variables. To create a closure, code a use clause in the inner function.
+   - To allow the inner function to change the outer function’s variable, use the reference operator (&) in the use clause.
+   - The outer function’s variables are available after it has finished executing as long as there is a reference to the inner function.
+   - The inner function is an anonymous function that is returned by the outer function or stored in a parameter that was passed by reference. You can store it in a variable and call it as a variable function like you would an anonymous function.