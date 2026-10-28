
## Functions for loops that work with arrays

| Function | Description |
| --- | --- |
| `count($array)` | Returns the number of elements in an array. This function doesn't count gaps in the array. |
| `end($array)` | Moves the cursor for the array to the last element in the array. |
| `key($array)` | Returns the index of the array element that the cursor is on. |
| `isset($var)` | Returns a TRUE value if the specified variable or array element contains a value. Otherwise, it returns a FALSE value. |

### Code that stores 10 random numbers in an array

```php
$numbers = array();
for ($i = 0; $i < 10; $i++) {
    $numbers[] = mt_rand(1, 100);
}
```

### Code that displays the elements of an array

```php
$numbers_string = '';
for ($i = 0; $i < count($numbers); $i++) {
    $numbers_string .= $numbers[$i] . ' ';
}
echo $numbers_string;
```

### Code that computes the sum and average of an array of prices

```php
$prices = array(141.95, 212.95, 411, 10.95);
$sum = 0;
for ($i = 0; $i < count($prices); $i++) {
    $sum += $prices[$i];
}
$average = $sum / count($prices);
```

### How to skip gaps in an array

```php
$numbers = array(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
unset($numbers[2], $numbers[6]);
end($numbers);
$last = key($numbers);
$numbers_string = '';
for ($i = 0; $i <= $last; $i++) {
    if (isset($numbers[$i])) {
        $numbers_string .= $numbers[$i] . ' ';
    }
}
echo $numbers_string;              // Displays: 1 2 4 5 6 8 9 10
```

### Description

- For loops are commonly used to process the data in arrays. In this case, the counter for the loop is used as the index for each element in the array.

Figure 11-3 — How to use for loops to work with arrays

## How to create and use an associative array

In PHP, you can also use strings as index values. When an array uses strings for its indexes, the array is known as an *associative array*. The indexes in an associative array are often called *keys*.

### How to create an associative array

Figure 11-4 shows two ways to create an associative array. For instance, the first example shows two techniques for creating an associative array of tax rates for various states. Here, the first technique uses a single statement to create the array and to store three key/value pairs in it. To do that, this code uses the array keyword followed by a set of parentheses. Within the parentheses, this code uses an arrow (=>) to specify the key/value pairs, and it separates each pair with a comma.

Then, the second technique uses four statements to create the same array. To do that, the first statement creates an empty array. Then, the next three statements specify the key/value pairs. Here, the key is a string and the value is an integer.

The two techniques in the second example work much like those in the first example. However, they use a string for the key and a string for the value.

The third example shows that a numerical array with numerous gaps can be considered an associative array. Here, the code uses an integer as the key and a string as the value.

In PHP, it's possible to mix integer and string indexes in the same array as shown in the fourth example. In general, this isn't considered a good practice, so you should avoid this whenever possible.

The PHP print_r function works with associative arrays, too, as shown in the last example in the figure. As mentioned in figure 11-1, this can be a quick way to see the contents of your array.

### The syntax for creating an associative array

```text
array([key1 => value1, key2 => value2, ...])
```

### How to create an associative array of state tax rates

**With one statement**

```php
$tax_rates = array('NC' => 7.75, 'CA' => 8.25, 'NY' => 8.875);
```

**With multiple statements**

```php
$tax_rates = array();
$tax_rates['NC'] = 7.75;
$tax_rates['CA'] = 8.25;
$tax_rates['NY'] = 8.875;
```

### How to create an associative array of country codes

**With one statement**

```php
$country_codes = array('DEU' => 'Germany', 'JPN' => 'Japan',
                       'ARG' => 'Argentina', 'USA' => 'United States');
```

**With multiple statements**

```php
$country_codes = array();
$country_codes['DEU'] = 'Germany';
$country_codes['JPN'] = 'Japan';
$country_codes['ARG'] = 'Argentina';
$country_codes['USA'] = 'United States';
```

### How to create an associative array of telephone extensions

```php
$ext = array();
$ext[10] = 'Sales';
$ext[13] = 'Customer Service';
$ext[16] = 'Returns';
$ext[18] = 'Warehouse';
```

### How to create an array that contains integer and string indexes

```php
$employees = array();
$employees[0] = 'Mike';
$employees[1] = 'Anne';
$employees[2] = 'Judy';
$employees['senior'] = 'Mike';
$employees['newest'] = 'Pren';
```

### How to use the print_r function to view an array

```php
print_r($tax_rates);
// Output: Array ( [NC] => 7.75 [CA] => 8.25 [NY] => 8.875 )
```

### Description

- An associative array uses a string as the index for the value that's stored in the array. When using an associative array, the index is commonly called a key.
- An array with integer keys that have gaps between them can also be thought of as an associative array.
- Although not a good practice, an array can have both integer and string indexes.

Figure 11-4 How to create an associative array

### How to add and delete elements

Once you've created an associative array, you can modify it by adding and deleting elements as shown in figure 11-5. To add an element, you usually specify the key as shown in the first example. If a value already exists at that key, the old value is replaced with the new value. Otherwise, the new element is added to the array.

If you omit the key when setting a value in an associative array, PHP uses an integer index. In the second example, for instance, the array doesn't contain any integer indexes in the array, so PHP uses zero as the index. However, if the array already had an integer index, PHP would take the highest integer index, add one to it, and use that value as the index. Since this usually isn't what you want, you typically specify a key when working with associative arrays.

You can get an element from an array by specifying the index as shown in the third example. Here, the second statement gets the first name, and the third statement gets the last name.

When you need to delete the value from one or more elements in an associative array, you can use the unset function just as you do for regular arrays. This is illustrated by the fourth example. You can also use this function to delete the entire array.

### How to work with variable substitution

You can also use array values in string substitution as shown by the last example in this figure. This works as you would expect. However, if the key is a string literal and it isn't coded inside braces, you can't use quotes around the key. If you do, you'll get a syntax error. To fix this error, you can either omit the quotes, or you can enclose the element in braces. In that case, you also need to include the quotes.

### How to set a value with a specific key

```php
$name = array('first' => 'Ray', 'last' => 'Harris');
$name['middle'] = 'Thomas';
```

### What happens when you omit the key when adding a value

```php
$name = array('first' => 'Ray', 'last' => 'Harris');
$name[] = 'Thomas';                         // key is 0
```

### How to get a value at a specified key

```php
$name = array('first' => 'Ray', 'last' => 'Harris');
$first_name = $name['first'];
$last_name = $name['last'];
```

### How to delete values from an array

```php
$name = array('first' => 'Ray', 'last' => 'Harris');
unset($name['first']);                       // delete the value from an element
unset($name);                                 // delete all elements
```

### How to use variable substitution with array elements

```php
echo "First Name: $name['first']";             // Generates a parse error
echo "First Name: $name[first]";               // First Name: Ray
echo "First Name: {$name['first']}";           // First Name: Ray
```

### Description

- To set or get a value in an associative array, specify the key for the value within the brackets.
- If you use an empty pair of brackets to add an element to an array, PHP uses an integer key for the element, which usually isn't what you want for an associative array.
- You can access array elements using variable substitution in a double-quoted string. To do that for a string key, you don't need to code quotes around the key. However, if you place braces around the element to separate it from other text in the string, you must include quotes around the key.

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_346_0.png)
