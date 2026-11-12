
print_r($person);
echo "</pre>";
?>

In this code, we have an associative array named $person with five key-value pairs representing different information about a person: last name, first name, age, gender, and country. Next, a new "email" key with the value "amine.dupont@example.com" is added to the array using the syntax $person["email"] = "amine.dupont@example.com";.

The **print_r()** function is used to display the contents of the $person array. By wrapping this function with the HTML tags <pre> and </pre>, the result is displayed in a formatted, more readable way in the browser.

As shown in the figure below, the result of running this code will display the full contents of the $person array, including the newly added "email" key, with all key-value pairs in a readable format.

```
Array
(
    [last_name] => Dupont
    [first_name] => Amine
    [age] => 29
    [gender] => M
    [country] => France
    [email] => amine.dupont@example.com
)
```

## Modifying elements in an associative array

To change the value of an element in an associative array, we simply reassign a new value to the corresponding key.

For example, to change the age of the person in the $person associative array, we use :

```
$person["age"] = 40;
```

After executing this line of code, the value of the "age" element in the $person array becomes 40.

## Deleting elements from an associative array

To delete a specific element from an associative array, we use the **unset()** function, predefined in PHP, with the key of the element we want to delete.

For example, to delete the "age" element from the $person associative array, we use :

```
unset($person["age"]);
```

## Browse an associative table

Associative arrays are data structures where each element is associated with a key rather than a numerical index. This allows values to be accessed using explicit keys rather than numerical indexes.

Here are some methods for browsing an associative array:

### Using the foreach loop :

The foreach loop is a particularly effective tool for browsing associative arrays. It allows you to navigate easily through each key-value pair in the array. We've already seen its use with indexed arrays. Now let's explore how to use this loop with associative arrays. Here's the second syntax of the foreach loop:

![](img/caba2aa22f5409ba73dea47176330677_215_0.png)

In this syntax we have:

- $table : represents the table to be browsed.
- $key: represents the key of the current element in the array.
- $value: represents the value of the current element in the array.

The foreach loop iterates through each element of the array, assigning the key and value of each element to the variables $key and $value, respectively. The instructions inside the loop are executed for each element of the array.

### Here's an example:

```
<?php

$person = [
    "last_name" => "Dupont",
    "first_name" => "Amine",
    "age" => 29,
    "gender" => "M",
    "country" => "France"
];

foreach ($person as $key => $value) {
    echo "Key: $key, Value: $value <br>";
}

?>
```

In this example, we have an associative array called $person that we created earlier.

The **foreach** loop is used to traverse the $person array. With each iteration of the loop, the **key** and **value** of each element in the array are stored in the **$key** and $value variables respectively.

Within the foreach loop, we display the key and value of each element in the array using the echo function.

The key is displayed using the `$key` variable and the value is displayed using the `$value` variable.

So, for each element of the `$person` array, this loop displays the corresponding key followed by its value, separated by a comma, then followed by a line break for better readability in the browser.

### Result:

![](img/caba2aa22f5409ba73dea47176330677_217_0.png)

## Multidimensional tables

Whereas simple arrays store simple data (numbers, strings etc.) in a linear fashion, multidimensional arrays are a complex data structure where each element can be an array itself. These arrays are useful for representing tabular data, matrices or other more complex data structures requiring multiple levels of organization. Take, for example, the multi-dimensional array shown in the following figure. This table shows the capital and population of France, Canada, Morocco and Spain.

| | 0 | 1 | 2 |
|---|---|---|---|
| 0 | France | Paris | 67 |
| 1 | Canada | Ottawa | 38 |
| 2 | Morocco | Rabat | 40 |
| 3 | Spain | Madrid | 47 |

By analyzing the structure of this multidimensional table, we can deduce that it is structured as a list of countries, where each country is represented by a sub-table containing three elements: the name of the country, its capital and the number of inhabitants.

Here's how each element is organized in the table:

- The first element of each sub-table is the country name.
- The second element is the country's capital.
- The third element is the number of inhabitants in the country.

In this way, each sub-table represents a country with its associated characteristics, and all these sub-tables are grouped together in a main table to form the complete multi-dimensional array. There are several methods for declaring and initializing this array in PHP.

### Method 1: Use the array() function to create an array.

```
<?php
$info_country = array(
    array("France", "Paris", 67),
    array("Canada", "Ottawa", 38),
    array("Morocco", "Rabat", 40),
    array("Spain", "Madrid", 47)
);
?>
```

### Method 2: Using bracket notation [ ].

```
<?php
$info_country = [
    ["France" , "Paris", 67],
    ["Canada", "Ottawa", 38],
    ["Morocco", "Rabat", 40],
    ["Spain", "Madrid", 47]
];
?>
```

These two methods are equivalent and produce the same result. They both define a multi-dimensional array containing four sub-arrays, each representing a country with its associated information (name, capital, number of inhabitants). The only difference lies in the syntax used: the first method uses the array() function, while the second uses PHP's shortened array syntax, introduced with the square bracket notation [ ].

Each element of the **main** table is an indexed table containing information for a specific country and represents one row of the table illustrated above. The first element of each table represents the country name, the second element represents the capital and the third element represents the number of inhabitants.

To visualize the structured contents of this table and better understand its layout, we can use the **print_r()** function by surrounding it with the HTML <pre> tag:

```
<?php

$info_country = array(
  array("France", "Paris", 67),
  array("Canada", "Ottawa", 38),
  array("Morocco", "Rabat", 40),
  array("Spain", "Madrid", 47)
);
echo "<pre>";
print_r($info_country);
echo "</pre>";
?>
```

When this code is executed, the result displayed will be similar to the following. This result clearly illustrates the structure of the multi-dimensional array. The main array is represented by the first "Array ( )", containing four sub-arrays indexed from 0 to 3. Each of these sub-arrays contains three elements indexed from 0 to 2.

![](img/caba2aa22f5409ba73dea47176330677_221_0.png)

## Accessing the elements of a multidimensional array

If we take the example of the multidimensional array $info_country, to access its elements, you can use numerical indexes, then their individual elements. For example, to access the capital of France, you can use the following syntax:

```php
// Access to the capital of France
$capital_france = $info_country[0][1];
echo $capital_france; // Display "Paris".
```

For example, to access the number of inhabitants of Morocco, you can use the following syntax:

```php
// Access to the number of inhabitants in Morocco
$capital_france = $info_country[2][2];
echo $capital_france; // Display 40
```
