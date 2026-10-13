
# Multidimensional Arrays

## PHP Script Example

```php
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>Multidimensional Arrays</title>
</head>
<body>
<p>Some North American States, Provinces, and Territories:</p>
<?php # Script 2.7 - multi.php

// Create one array:
$mexico = array(
    'YU' => 'Yucatan',
    'BC' => 'Baja California',
    'OA' => 'Oaxaca'
);

// Create another array:
$us = array(
    'MD' => 'Maryland',
    'IL' => 'Illinois',
    'PA' => 'Pennsylvania',
    'IA' => 'Iowa'
);

// Create a third array:
$canada = array(
    'QC' => 'Quebec',
    'AB' => 'Alberta',
    'NT' => 'Northwest Territories',
    'YT' => 'Yukon',
    'PE' => 'Prince Edward Island'
);

// Combine the arrays:
$n_america = array(
    'Mexico' => $mexico,
    'United States' => $us,
    'Canada' => $canada
);

// Loop through the countries:
foreach ($n_america as $country => $list) {

    // Print a heading:
    echo "<h2>$country</h2><ul>";

    // Print each state, province, or territory:
    foreach ($list as $k => $v) {
        echo "<li>$k - $v</li>\n";
    }

    // Close the list:
    echo '</ul>';
} // End of main FOREACH.

?>
</body>
</html>
```

## Step-by-Step Explanation

### 3. Create the second and third arrays

```php
$us = array(
    'MD' => 'Maryland',
    'IL' => 'Illinois',
    'PA' => 'Pennsylvania',
    'IA' => 'Iowa'
);

$canada = array(
    'QC' => 'Quebec',
    'AB' => 'Alberta',
    'NT' => 'Northwest Territories',
    'YT' => 'Yukon',
    'PE' => 'Prince Edward Island'
);
```

### 4. Combine all of the arrays into one

```php
$n_america = array(
    'Mexico' => $mexico,
    'United States' => $us,
    'Canada' => $canada
);
```

You don’t have to create three arrays and then assign them to a fourth in order to make the desired multidimensional array, but I think it’s easier to read and understand this way (defining a multidimensional array in one step makes for some ugly code).

The `$n_america` array now contains three elements. The key for each element is a string, which is the country’s name. The value for each element is the array of states, provinces, and territories found within that country.

### 5. Begin the primary `foreach` loop

```php
foreach ($n_america as $country => $list) {
    echo "<h2>$country</h2><ul>";
}
```

Following the syntax outlined earlier, this loop will access every element of `$n_america`. This means that this loop will run three times. Within each iteration of the loop, the `$country` variable will store the `$n_america` array’s key (*Mexico*, *Canada*, or *United States*). Also within each iteration of the loop, the `$list` variable will store the element’s value (the equivalent of `$mexico`, `$us`, and `$canada`).

To print out the results, the loop begins by printing the country’s name within `H2` tags. Because the states and so forth should be displayed as an HTML list, the initial unordered list tag (`<ul>`) is printed as well.

### 6. Create a second `foreach` loop

```php
foreach ($list as $k => $v) {
    echo "<li>$k - $v</li>\n";
}
```

This loop will run through each sub-array (first `$mexico`, then `$us`, and then `$canada`). With each iteration of this loop, `$k` will store the abbreviation and `$v` the full name. Both are printed out within HTML list tags. The newline character is also used, to better format the HTML source code.

### 7. Complete the outer `foreach` loop

```php
echo '</ul>';
} // End of main FOREACH.
```

After the inner `foreach` loop is done, the outer `foreach` loop has to close the unordered list begun in Step 5.

### 8. Complete the PHP and HTML

```php
?>
</body>
</html>
```

### 9. Save and test

Save the file as `multi.php`, place it in your Web directory, and test it in your Web browser.

### 10. Check HTML source

If you want, check out the HTML source code to see what PHP created.

---

## Tip: Multidimensional Arrays from HTML Forms

Multidimensional arrays can also come from an HTML form. For example, if a form has a series of checkboxes with the name `interests[]`:

```html
<input type="checkbox" name="interests[]" value="Music" /> Music
<input type="checkbox" name="interests[]" value="Movies" /> Movies
<input type="checkbox" name="interests[]" value="Books" /> Books
```

The `$_POST` variable in the receiving PHP page will be multidimensional. `$_POST['interests']` will be an array, with `$_POST['interests'][0]` storing the value of the first checked box (e.g., Movies), `$_POST['interests'][1]` storing the second (Books), etc. Note that only the checked boxes will get passed to the PHP page.

---

## Tip: Multidimensional Arrays from Select Menus

You can also end up with a multidimensional array if an HTML form’s select menu allows for multiple selections:

```html
<select name="interests[]" multiple="multiple">
    <option value="Music">Music</option>
    <option value="Movies">Movies</option>
    <option value="Books">Books</option>
    <option value="Napping">Napping</option>
</select>
```

Again, only the selected values will be passed to the PHP page.

---

# Arrays and Strings

Because arrays and strings are so commonly used together, PHP has two functions for converting between them:

```php
$array = explode(separator, $string);
$string = implode(glue, $array);
```

The key to using and understanding these two functions is the *separator* and *glue* relationships. When turning an array into a string, you establish the glue—the characters or code that will be inserted between the array values in the generated string. Conversely, when turning a string into an array, you specify the separator, which is the token that marks what should become separate array elements.

For example, start with a string:

```php
$s1 = 'Mon-Tue-Wed-Thu-Fri';
$days_array = explode('-', $s1);
```

The `$days_array` variable is now a five-element array, with *Mon* indexed at `0`, *Tue* indexed at `1`, etc.

```php
$s2 = implode(', ', $days_array);
```

The `$s2` variable is now a comma-separated list of days: *Mon, Tue, Wed, Thu, Fri*.

---

## Sorting Arrays

One of the many advantages arrays have over the other variable types is the ability to sort them. PHP includes several functions you can use for sorting arrays, all simple in syntax:

```php
$names = array('Moe', 'Larry', 'Curly');
sort($names);
```

The sorting functions perform three kinds of sorts:

1. **Sort by value, discarding original keys** using `sort()`. It’s important to understand that the array’s keys will be reset after the sorting process, so *if the key-value relationship is important, you should not use* `sort()`.
2. **Sort by value while maintaining keys** using `asort()`.
3. **Sort by key** using `ksort()`.

Each of these can sort in reverse order if you change them to `rsort()`, `arsort()`, and `krsort()` respectively.

To demonstrate the effect sorting arrays will have, this next script will create an array of movie titles and ratings (how much I liked them on a scale of 1 to 10) and then display this list in different ways.

### To sort arrays

#### 1. Begin a new PHP document

Create a new PHP document in your text editor or IDE, to be named `sorting.php`, starting with the initial HTML (**Script 2.8**):

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```
