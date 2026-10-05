# Basic Computer Coding: PHP

The function returns a Boolean value that indicates whether the first argument is a valid key in the array given as the second argument.
It is not sufficient to simply say:

```
if ($person['name']) { ... }
// this can be misleading
```

Even if there is an element in the array with the key name, its corresponding value might be false (i.e., 0, NULL, or the empty string). Instead, use array_key_exists(), as follows:

Value is the representation of some entity that can be manipulated by a program.

```
$person['age'] = 0; // unborn

if ($person['age']) {
    echo "true!\n";
}

if (array_key_exists('age', $person)) {
    echo "exists!\n";
}
```

exists!

Many people use the isset() function instead, which returns true if the element exists and is not NULL:

```
$sa = array(0, NULL, '');
function tf($v) {
    return $v ? 'T' : 'F';
}

for ($i=0; $i < 3; $i++) {
    printf("%d: %s %s\n", $i, isset($sa[$i]), tf(array_key_exists($i, $sa)));
}

0: T T
1: F T
2: T T
3: FF
```

# Removing and Inserting Elements in an Array

The array_slice() function can remove or insert elements in an array and optionally create another array from the removed elements:

```
$removed = array_slice($array, start [, length [, replacement ]));
```

We will look at array_slice() using this array: