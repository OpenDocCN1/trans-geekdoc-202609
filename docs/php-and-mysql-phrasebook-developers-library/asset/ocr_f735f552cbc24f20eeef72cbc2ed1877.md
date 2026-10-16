If the array turns out to be a nested one, however, the tactic has to be changed a little. Then you can use a recursive function. If an array element is a string, it is HTML encoded. If it's an array, the recursive function calls itself on that array. The following code implements this, and Figure 2.6 shows the result:

```
```php
<?php

function sanitize_recursive($s) {
    if (is_array($s)) {
        return(array_map('sanitize_recursive', $s));
    } else {
        return htmlspecialchars($s);
    }
}

$a = array(
    'harmless' =>
        array('no', 'problem'),
    'harmful' =>
        array('<bad>', '-> <worse> <--')
);

$a = sanitize_recursive($a);
echo '<pre>' . print_r($a, true) . '</pre>';
?>
```
```

*Recursively Applying htmlspecialchars() to All Elements of a Nested Array (array_map_recursive.php)*