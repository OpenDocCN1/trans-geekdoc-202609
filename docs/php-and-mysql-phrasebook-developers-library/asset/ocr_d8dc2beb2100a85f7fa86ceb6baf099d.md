```
$a = array_walk($a, 'printElement', $i);
?>
```

Printing Array Elements Using array_walk() and a Counter Passed by Reference (array_walk.php)

Running the preceding code shows the following:

0: one
1: two
2: three
3: four

# Filtering Arrays

```
array_filter($values, 'checkMail')

<?php
function checkMail($s) {
    // ...
}

$values = array(
    'valid@email.tld',
    'invalid@email',
    'also@i.nvalid',
    'also@val.id'
);
echo implode(', ', array_filter($values, 'checkMail'));
?>
```

Filtering Valid Email Addresses (array_filter.php)