
> **Note**
> In this case, where there are no associative indices, a for loop would solve the problem. However, PHP offers many other sorting functions.

With PHP's associative arrays, you may want to get not only the value, but also the index to the value. Here too, foreach provides excellent services, as Figure 8.9 shows.

```php
<?php
$stockprices = array("IBW" => 232, "Miemens" => 34, "Rheinwerk" => 340);
foreach ($stockprices as $index => $stockprice) {
print "The company " . $index . " ";
print "has the stock price: " . $stockprice . "<br />";
}
?>
```

### Listing 8.7 Read the Index with foreach ("array_foreach_index.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_245_0.png)

### Figure 8.9 The Index Also Can Be Output

> **Note**
> Since PHP 7.1, you can also use arrays in foreach loops in the JSON-based shorthand notation. The following example shows the JSON array in a variant without objects.

```php
<?php
$stockprices = [
["IBW", 232],
["Miemens", 34],
["Rheinwerk", 340]
];
foreach ($stockprices as [$index, $stockprice]) {
print "The company " . $index . " ";
print "has the stock price: " . $stockprice . "<br />";
}
?>
```

### Listing 8.8 "foreach" with the JSON Notation ("array_foreach_abbreviation.php")

## 8.2.3 Functions for Iteration

In addition to loops, PHP also offers a number of functions that you can use to traverse arrays. The concept behind this is a kind of pointer to the current element of the array.<sup>1</sup>

With the current(Array) function, for example, you get the current element. With next(Array), on the other hand, the pointer is moved one element further and you get this element. If there is no element left, you will receive the value false.

The following simple example goes through all the elements of an array (see Figure 8.10).

```php
<?php
$stockprices = array("IBW" => 232, "Miemens" => 34, "Rheinwerk" => 340);
print current($stockprices) . "<br />";
while (next($stockprices)) {
    print current($stockprices) . "<br />";
}
?>
```

Listing 8.9 "current()" and "next()" ("current_next.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_246_0.png)

**Figure 8.10 All Stock Prices**

> **Note**
> Attention: the approach just shown fails if one of the values of the array is false or 0! In this case, the while loop would be aborted even though the array is not yet complete. However, at least the value 0 could be sorted out if you check for absolute inequality:
> while (next($rates) != false) { ... }

1 PHP does not have a real pointer concept like other programming languages (e.g., C). However, the functions mentioned come a little closer to this.

In addition to these two, there are several other functions for iteration:

- pos(Array) is a synonym for current().
- prev(Array) returns the array element before the current one. If there are no more, then false is returned.
- reset(Array) sets the pointer back to the first element. If the array is empty, the function returns false.
- end(Array) sets the pointer to the last element. If the array is empty, the function returns false.
- each(Array) works like next(), except that the key and value are returned in an array. However, the function is no longer recommended since PHP 7.2 and has been removed from PHP 8.
- key(Array) returns the index of the element at the current pointer position in the array.
- array_walk(Array, Function, Parameter) automatically walks through an array and calls a function for each element. The function receives the value and the index of the respective element as parameters. Optionally, you can also pass a third parameter. When using array_walk(), you should not change the array. The output is in the input order of the elements. This is the case for all iteration functions. array_walk_recursive() works in the same way as array_walk(), except that it also penetrates multidimensional arrays. The following listing offers a simple example of array_walk(); you can see the output in Figure 8.11.

```php
<?php
$stockprices = array("IBW" => 232, "Miemens" => 34, "Rheinwerk" => 340);

function output($stockprices, $index, $text) {
if ($index != "Miemens") {
print $text . $index . ": ";
print $rate . "<br />";
}
}

array_walk($stockprices, "output", "The stock price from: ");
?>
```

### Listing 8.10 "array_walk()" ("array_walk.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_247_0.png)

### Figure 8.11 The Function Returns Two Prices and Singles One Out

- array_map(function, array ...) calls the function for each array element and returns an array with the elements from the array or arrays passed as parameters after they have passed through the function.

## 8.3 Examine

Let's assume that you don't know very much about the return of a function, but you suspect that it is usually an array and need some information from it. PHP offers some interesting functions for this.

You already know about count(Array). This function counts the number of elements in an array. If you specify COUNT_RECURSIVE or 1 as the second parameter, then all elements are counted recursively. This means that count(Array, Mode) also counts the elements in nested arrays. Assume the following array:

```php
$ibw_stockprices = array("1.1.2015" => 232, "1.1.2020" => 254);
$stockprices = array("IBW" => $ibw_stockprices);
```

If you now count all elements without the mode, like this:

```php
print count($stockprices);
```

then you get 1. If, on the other hand, you work recursively, with

```php
print count($stockprices, 1);
```

then count() also counts the elements of the subordinate array and returns 3.

Now to the other interesting examination functions in PHP:

- sizeof() is a synonym of count().
- isset(Array) determines whether an array is defined at all. isset() also returns true for an empty array.
- empty(Array) checks whether an array is empty (true) or has elements (false). If an array does not exist, then empty() returns true.
- is_array(Array) checks whether something is an array. If the array does not exist, is_array() returns a warning. You must therefore combine this function with isset().
- in_array(Search element, Array, Strict) checks whether a value is present in the array. The Search element can be any data type, including another array (since PHP 4.2.0). If the optional parameter Strict is set to true, then the data type of the Search element and the find must match. Caution: in_array() is one of two array functions that do not start with the array, but with the search element!<sup>2</sup>

2 People discussed whether to change these two functions, in_array() and array_search(), in a future PHP version. However, as there are only the two and the damage to old scripts would probably be great, this was not done.

> **Note**
> The same rules apply to this function as those for comparison operators. With string comparisons, the ASCII position of the character is decisive; that is, a distinction is made between upper- and lowercase. With Strict, it is a check for absolute equality or inequality.

## 8.4 Transform

In the extensive universe of array helper functions, we first show you the most important ones for transforming, splitting, and joining arrays. You will also learn how to convert variables into arrays and vice versa.

> **Note**
> Most array auxiliary functions can also be more or less easily replicated with the normal array functions. However, there is hardly anyone who wants to do this work.

### 8.4.1 Adding and Removing

You can imagine an array like a stack. The first element created is the first element in the stack; the last element added is the last.

Let's take a look at the four functions that PHP offers for this:

- array_pop(Array) removes the last element of the array and returns it. If there is no element, then the function returns zero.
- array_push(Array, Value, Value ...) adds the value or values to the end of the array. You automatically receive the highest indices. The size of the array is increased by the specified number of elements. The total number of elements is returned.
- array_shift(Array) removes the first element of the array and changes the numerical index of all other elements (associative indices remain unaffected). In the following example, Saturday disappears and Sunday has the index 0:

```php
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
array_shift($days);
```

The function returns the removed element, or zero in the case of an empty array.
- array_unshift(Array, Value, Value ...) adds new values to the beginning of the array and returns the number of elements the array has afterward.
