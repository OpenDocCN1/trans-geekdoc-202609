# Sorting Nested Arrays

![](bbox=[0.175, 0.095, 0.9, 0.39])

Figure 2.3 Sorting associative arrays.

> NOTE
> Trying to use sort() or rsort() with associative arrays works—but the keys are then all lost.

# Sorting Nested Arrays

```
```php
function sortNestedArray(&$a) {
    sort($a);
    for ($i = 0; $i < count($a); $i++) {
        if (is_array($a[$i])) {
            sortNestedArray($a[$i]);
        }
    }
}
```
```

The standard sorting functions of PHP have to give up when they work on nested arrays. However, if you use a recursive function, you can code this in just a few lines.

The goal is to sort an array that is nested, but consists only of numeric subarrays, so only numeric (and, therefore, useless) keys are used.