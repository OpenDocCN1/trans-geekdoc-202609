
## Basic Computer Coding: PHP

The array_slice() function returns a new array consisting of a consecutive series of values from the original array. The offset parameter identifies the initial element to copy (0 represents the first element in the array), and the length parameter identifies the number of values to copy. The new array has consecutive numeric keys starting at 0. For example:

```
$people = array("Tom", "Dick", "Harriet", "Brenda", "Jo");
$middle = array_slice($people, 2, 2); // $subset is array("Harriet", "Brenda")
```

It is generally only meaningful to use array_slice() on indexed arrays (i.e., those with consecutive integer indices starting at 0):

```php
// this use of array_slice() makes no sense
$person = array("name" => "Fred", "age" => 35, "wife" => "Betty");
$subset = array_slice($person, 1, 2); // $subset is array(0 => 35, 1 => "Betty")
```

Combine array_slice() with list() to extract only values to variables:

```php
$order = array("Tom", "Dick", "Harriet", "Brenda", "Jo");
list($second, $third) = array_slice($order, 1, 2);
// $second is "Dick", $third is "Harriet"
```

## Splitting an Array into Chunks

To divide an array into smaller, evenly sized arrays, use the array_chunk() function:

Boolean value is one with two choices: true or false, yes or no, 1 or 0:

```php
$chunks = array_chunk(array, size [, preserve_keys]);
```

The function returns an array of the smaller arrays. The third argument, preserve_keys, is a Boolean value that determines whether the elements of the new arrays have the same keys as in the original (useful for associative arrays) or new numeric keys starting from 0 (useful for indexed arrays). The default is to assign new keys, as shown here:

```php
$nums = range(1, 7);
$rows = array_chunk($nums, 3);
print_r($rows);

Array (
    [0] => Array (
        [0] => 1
        [1] => 2
        [2] => 3
    )
    [1] => Array (
        [0] => 4
        [1] => 5
        [2] => 6
    )
    [2] => Array (
        [0] => 7
    )
)
```

## Keys and array_keys() function

The array_keys() function returns an array consisting of only the keys in the array in internal order:

```php
$arrayOfKeys = array_keys(array);
```

Here's an example:

```php
$person = array('name' => 'Fred', 'age' => 35, 'wife' => 'Wilma');
$keys = array_keys($person); // $keys is array("name", "age", "wife")
```

PHP also provides a (generally less useful) function to retrieve an array of just the values in an array, array_values():

```php
$arrayOfValues = array_values(array);
```

With array_keys(), the values are returned in the array's internal order:

```php
$values = array_values($person); // $values is array("Fred", 35, "Wilma")
```

## Checking Whether an Element Exists

To see if an element exists in the array, use the array_key_exists() function:

```php
if (array_key_exists(key, array)) { ... }
```

The function returns a Boolean value that indicates whether the first argument is a valid key in the array given as the second argument.
It is not sufficient to simply say:

```php
if ($person['name']) { ... }
// this can be misleading
```

Even if there is an element in the array with the key name, its corresponding value might be false (i.e., 0, NULL, or the empty string). Instead, use array_key_exists(), as follows:

Value is the representation of some entity that can be manipulated by a program.

```php
$person['age'] = 0; // unborn

if ($person['age']) {
    echo "true!\n";
}

if (array_key_exists('age', $person)) {
    echo "exists!\n";
}
```

Many people use the isset() function instead, which returns true if the element exists and is not NULL:

```php
$sa = array(0, NULL, '');
function tf($v) {
    return $v ? 'T' : 'F';
}

for ($i=0; $i < 3; $i++) {
    printf("%d: %s %s\n", $i, isset($sa[$i]), tf(array_key_exists($i, $sa)));
}

Output:
0: T T
1: F T
2: T T
```

## Removing and Inserting Elements in an Array

The array_slice() function can remove or insert elements in an array and optionally create another array from the removed elements:

```php
$removed = array_slice($array, start [, length [, replacement ]));
```

We will look at array_slice() using this array:

```php
$subjects = array("physics", "chem", "math", "bio", "cs", "drama", "classics");
```

We can remove the "math", "bio", and "cs" elements by telling array_slice() to start at position 2 and remove 3 elements:

```php
$removed = array_slice($subjects, 2, 3);
// removed = array("math", "bio", "cs")
// subjects = array("physics", "chem", "drama", "classics");
```

If you omit the length, array_slice() removes to the end of the array:

```php
$removed = array_slice($subjects, 2);
// removed = array("math", "bio", "cs", "drama", "classics");
// subjects = array("physics", "chem");
```

If you simply want to delete elements from the source array and you do not care about retaining their values, you do not need to store the results of array_slice():

```php
array_slice($subjects, 2);
// subjects = array("physics", "chem");
```

To insert elements where others were removed, use the fourth argument:

```php
$new = array("law", "business", "IS");
array_slice($subjects, 4, 3, $new);
// subjects = array("physics", "chem", "drama", "classics", "law", "business", "IS");
```

Wait, the OCR text has some fragmented parts at the end. Let's reconstruct the logic based on standard PHP behavior and the provided snippets:

## Basic Computer Coding: PHP (Continued)

```php
$capitals = array(
    'USA' => "Washington",
    'Great Britain' => 'London',
    'New Zealand' => 'Wellington',
    'Australia' => 'Canberra',
    'Italy' => "Rome",
    'Canada' => "Ottawa"
);

$removed = array_slice($capitals, 2, 2);
// $removed is array(0 => "Wellington", 1 => "Canberra")
// $capitals is array('USA' => "Washington", 'Great Britain' => 'London', 'Italy' => "Rome", 'Canada' => "Ottawa")
```

## SUMMARY

- Array functions allow you to interact and manipulate arrays. Arrays are essential for storing, managing, and operating on sets of variables.
- An array is a structure that stores one or more similar type of values.
- Numeric arrays can store numbers, strings and any object but their index will be represented by numbers. By default array index starts from zero. own- PHP arrays have an internal order to their elements that is independent of the keys and values, and there are functions you can use to traverse the arrays based on this order. own- Associative arrays are very similar to arrays but they are different in terms of their index. Associative array will have string so that you can establish a strong association between key and values.
- Storing a value in an array will create the array if it did not exist, but trying to retrieve a value from an array that has not been defined would not create the array.
- A multidimensional array each element in the main array can also be an array. And each element in the sub-array can be an array, and so on. Values in the multidimensional array are accessed using multiple index.

---

- Which of the following type of variables are named and indexed collections of other values?
  - Strings
  - Arrays
  - Objects
  - Resources
- Which of the following array represents an array containing one or more arrays?
  - Numeric Array
  - Associative Array
  - Multidimensional Array
  - None of the above.
- Which of the following type of variables are sequences of characters, like 'PHP supports string operations.'
  - Strings
  - Arrays
  - Objects
  - Resources
- Which of the following function returns the sum of the values in an array?
  - array_sum()
  - array_splice()
  - array_udiff()
  - array_udiff_assoc()
- Which of the following is correct about determine the “truth” of any value not already of the Boolean type?
  - If the value is an array, it is false if it contains no other values, and it is true otherwise. For an object, containing a value means having a member variable that has been assigned a value.
