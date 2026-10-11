
# Chapter 12: ArrayAccess and Iterator Interfaces

## Section 12.6: ArrayAccess and Iterator Interfaces

In PHP 5.5 and later you can use `array_column()` in conjunction with `array_search`.

This is particularly useful for [checking if a value exists in an associative array](http://stackoverflow.com/questions/6990855/php-check-if-value-and-key-exist-in-multidimensional-array/37935356#37935356):

![Image00324.jpg](Image00324.jpg)

Another useful feature is accessing your custom object collections as arrays in PHP. There are two interfaces available in PHP (>=5.0.0) core to support this: `ArrayAccess` and `Iterator`. The former allows you to access your custom objects as arrays.

### ArrayAccess

Assume we have a user class and a database table storing all the users. We would like to create a `UserCollection` class that will:

1. Allow us to address certain user by their username unique identifier
2. Perform basic (not all CRUD, but at least Create, Retrieve and Delete) operations on our users collection

Consider the following source (hereinafter we're using short array creation syntax `[]` available since version 5.4):

![Image00325.jpg](Image00325.jpg)
![Image00326.jpg](Image00326.jpg)

Then we can:

```php
$users = new UserCollection();

var_dump(empty($users['testuser']), isset($users['testuser']));
$users['testuser'] = [
    'username' => 'testuser',
    'password' => 'testpassword',
    'email'    => 'test@test.com'
];
var_dump(empty($users['testuser']), isset($users['testuser']), $users['testuser']);
unset($users['testuser']);
var_dump(empty($users['testuser']), isset($users['testuser']));
```

Which will output the following, assuming there was no `testuser` before we launched the code:

![Image00328.jpg](Image00328.jpg)

**IMPORTANT:** `offsetExists` is not called when you check existence of a key with `array_key_exists` function. So the following code will output `false` twice:

```php
var_dump(array_key_exists('testuser', $users));
$users['testuser'] = [
    'username' => 'testuser',
    'password' => 'testpassword',
    'email'    => 'test@test.com'
];
var_dump(array_key_exists('testuser', $users));
```

![Image00329.jpg](Image00329.jpg)

### Iterator

Let's extend our class from above with a few functions from `Iterator` interface to allow iterating over it with `foreach` and `while`.

First, we need to add a property holding our current index of iterator, let's add it to the class properties as `$_position`:

![Image00330.jpg](Image00330.jpg)

Second, let's add `Iterator` interface to the list of interfaces being implemented by our class:

![Image00331.jpg](Image00331.jpg)

Then add the required by the interface functions themselves:

![Image00332.jpg](Image00332.jpg)
![Image00333.jpg](Image00333.jpg)

So all in all here is complete source of the class implementing both interfaces. Note that this example is not perfect, because the IDs in the database may not be sequential, but this was written just to give you the main idea: you can address your objects collections in any possible way by implementing `ArrayAccess` and `Iterator` interfaces:

![Image00334.jpg](Image00334.jpg)

And a `foreach` looping through all user objects:

![Image00335.jpg](Image00335.jpg)

Which will output something like:

![Image00336.jpg](Image00336.jpg)

# Chapter 13: Array iteration

## Section 13.1: Iterating multiple arrays together

Sometimes two arrays of the same length need to be iterated together, for example:

![Image00337.jpg](Image00337.jpg)

`array_map` is the simplest way to accomplish this:

![Image00338.jpg](Image00338.jpg)

Which will output:

![Image00339.jpg](Image00339.jpg)

This can be done through a common index:

![Image00340.jpg](Image00340.jpg)

`array_values($array)[$i]` can be used to replace `$array[$i]`.

If the two arrays don't have the incremental keys, `array_values` or `array_keys` can be used instead.

If both arrays have the same order of keys, you can also use a `foreach`-with-key loop on one of the arrays:

![Image00341.jpg](Image00341.jpg)

Separate arrays can only be looped through if they are the same length and also have the same key name. This means if you don't supply a key and they are numbered, you will be fine, or if you name the keys and put them in the same order in each array.

You can also use `array_combine`.

```php
$combinedArray = array_combine($people, $foods);
// $combinedArray = ['Tim' => 'chicken', 'Tony' => 'beef', 'Turanga' => 'slurm'];
```

Then you can loop through this by doing the same as before:

![Image00343.jpg](Image00343.jpg)

## Section 13.2: Using an incremental index

This method works by incrementing an integer from 0 to the greatest index in the array.

![Image00344.jpg](Image00344.jpg)

This also allows iterating an array in reverse order without using `array_reverse`, which may result in overhead if the array is large.

![Image00345.jpg](Image00345.jpg)

You can skip or rewind the index easily using this method.

![Image00346.jpg](Image00346.jpg)

Output:

![Image00347.jpg](Image00347.jpg)

For arrays that do not have incremental indices (including arrays with indices in reverse order, e.g. `[1 => "bar"]`, `["foo" => "f", "bar" => "b"]`), this cannot be done directly. `array_values` or `array_keys` can be used instead:

![Image00348.jpg](Image00348.jpg)

## Section 13.3: Using internal array pointers

Each array instance contains an internal pointer. By manipulating this pointer, different elements of an array can be retrieved from the same call at different times.

### Using `each`

Each call to `each()` returns the key and value of the current array element, and increments the internal array pointer.

![Image00349.jpg](Image00349.jpg)

### Using `next`

![Image00350.jpg](Image00350.jpg)

Note that this example assumes no elements in the array are identical to boolean `false`. To prevent such assumption, use `key()` to check if the internal pointer has reached the end of the array:

![Image00351.jpg](Image00351.jpg)

This also facilitates iterating an array without a direct loop:

![Image00352.jpg](Image00352.jpg)

## Section 13.4: Using foreach

### Direct loop

![Image00353.jpg](Image00353.jpg)

### Loop with keys

![Image00354.jpg](Image00354.jpg)

### Loop by reference

In the `foreach` loops in the above examples, modifying the value (`$color` or `$food`) directly doesn't change its value in the array. The `&` operator is required so that the value is a reference pointer to the element in the array.

![Image00355.jpg](Image00355.jpg)
![Image00356.jpg](Image00356.jpg)

This is similar to:

![Image00357.jpg](Image00357.jpg)

### Concurrency

PHP arrays can be modified in any ways during iteration without concurrency problems (unlike e.g. Java `List`s). If the array is iterated by reference, later iterations will be affected by changes to the array. Otherwise, the changes to the array will not affect later iterations (as if you are iterating a copy of the array instead). Compare looping by value:

![Image00358.jpg](Image00358.jpg)

Output:

![Image00359.jpg](Image00359.jpg)

But if the array is iterated with reference:

![Image00360.jpg](Image00360.jpg)

Output:

![Image00361.jpg](Image00361.jpg)

The key-value set of `4 => 5` is no longer iterated, and `6 => 7` is changed to `6 => 17`.

## Section 13.5: Using ArrayObject Iterator

PHP `ArrayIterator` allows you to modify and unset the values while iterating over arrays and objects.

Example:

![Image00362.jpg](Image00362.jpg)

Output:

![Image00363.jpg](Image00363.jpg)

# Chapter 14: Executing Upon an Array

## Section 14.1: Applying a function to each element of an array

To apply a function to every item in an array, use `array_map()`. This will return a new array.

![Image00364.jpg](Image00364.jpg)

Instead of using an anonymous function, you could use a named function. The above could be written like:

![Image00365.jpg](Image00365.jpg)
