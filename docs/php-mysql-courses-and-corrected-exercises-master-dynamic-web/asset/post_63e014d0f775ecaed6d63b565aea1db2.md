
$numbers[1] = 100; // The element to be modified has index 1

If you want to delete the "Sarah" element from the $lastname array, simply use the predefined unset() function in PHP :

```
unset($lastnames[3]); // Deletes the fourth element (Sarah)
```

## Browse an indexed table

To browse an indexed array in PHP, you can use various flow control structures, such as the **for** loop, which we studied in a previous chapter, or the **foreach** loop, which we'll look at next.

## Loop for

The for loop is used when you know in advance the number of elements in the array. You can iterate over each element of the array using an index. To find out the number of elements in an array, PHP provides a function called **count()**, which returns the number of elements in an array passed as an argument.

## Example

```
<?php
$numbers = [10, 20, 30, 40, 50];
$length = count($numbers);
for ($i = 0; $i < $length; $i++) {
   echo $numbers[$i] . "<br>";
}
?>
```

In this example, we have an indexed array called $numbers containing five elements: 10, 20, 30, 40 and 50. The count() function is used to obtain the total number of elements in the array, which is stored in the $length variable.

Next, a for loop is used to iterate through each element of the array using an index. The variable $i is initialized to 0, and the loop continues as long as the value of $i is less than $length. At each iteration, the value of the array element at index $i is displayed with echo, followed by a <br> tag to create a line break in the HTML rendering. Execution of this code displays the following result:

![](img/caba2aa22f5409ba73dea47176330677_204_0.png)

The for loop works perfectly for browsing this type of array, and its use is entirely appropriate. However, we’ll now turn to another loop specifically designed for arrays: the foreach loop.

## Foreach loop

The foreach loop is used when you want to iterate over each element of the array without worrying about knowing the size of the array in advance. The **foreach** loop admits two different syntaxes, the first syntax we use to traverse an indexed array is :

```
foreach ($stable as $value) {
// Block of code to execute
}
```

In this syntax, the $value variable directly contains the value of each element of the $stable array during iteration. The element key is not accessible in this form of the foreach loop. This foreach loop syntax allows you to iterate through the elements of an array on values only, without needing to retrieve the keys associated with each value. Each time the loop is iterated, the $value variable contains the value of the currently traversed element in the array. This simplifies the process of traversing arrays when only the value of elements is required, without worrying about the associated keys.

## Example

```
<?php
$numbers = [10, 20, 30, 40, 50];
foreach ($numbers as $number) {
echo $number . "<br>";
}
?>
```

This example uses the **foreach** loop to traverse the $numbers array. In this loop, $number (singular) represents each element of the $numbers array at each iteration. In fact, at each iteration, the $number variable takes on the value of the **current** element in the array. So, on each loop turn, the value of $number is displayed, followed by a <br> tag for a line feed. This loop is handy for browsing through all the elements of an array without needing to explicitly manage an index as with the for loop. The output result of this code is exactly the same as that obtained with the for loop.

## Associative arrays

Associative arrays, as their name suggests, associate keys with values. Unlike indexed arrays, where values are accessible by their numerical position, in an associative array, values are accessible by their associated key. Here's how to declare and initialize an associative array in PHP :

## Declaration of an empty associative array

The method for declaring an empty associative array is the same as for declaring an indexed array:

```
<?php

$empty_associative_array = [];

?>
```

In this example, we declare and initialize an empty associative array using PHP's array syntax. The variable $empty_associative_array is assigned to an empty associative array using empty double square brackets, i.e. an array that contains no key-value pairs.

This declaration creates an empty associative array that can be used to store data by associating keys with values later in the code.

## Declaring and initializing an associative array with values

Associative arrays work on the same principle as indexed arrays, except that each key is associated with a distinct name rather than a number. Let's take the example of the array illustrated in the following figure.

How can we declare and initialize this array in PHP?

| Keys | Values |
| :--- | :--- |
| lastname | Dupont |
| firstname | Amine |
| age | 29 |
| gender | M |
| country | Canada |

The syntax used to declare and initialize the $person associative array is as follows:

```
<?php
$person = [
    "last_name" => "Dupont",
    "first_name" => "Amine",
    "age" => 29,
    "gender" => "M",
    "country" => "France"
];
?>
```

In this example, we initialize an associative array $person using PHP's associative array syntax.
This syntax uses square brackets [ ] to delimit the beginning and end of the associative array. Inside the
square brackets, each element of the array is a key-value pair, where the key is followed by the => sign and
the value associated with that key. Key-value pairs are separated by commas. This syntax allows you to
create an associative array where each key is associated with a specific value.

The keys "last_name", "first_name", "age", "gender" and "country" are associated with their respective
values: "Dupont", "Amine", 29, "M" and "France" using the => sign. This table stores information about a
person, such as surname, first name, age, gender and country. Keys are used to access the corresponding
values in the table.

## Declaring an associative array with the array() function

The third way to declare an associative array is to use PHP's predefined array() function:

```
<?php

$grades = array(
"Maths" => 15,
"Physics" => 18,
"English_language" => 12
);
?>
```

In this example, we initialize an associative array $grades using the **array()** function. This syntax begins with the array() keyword, followed by a list of key-value pairs. Each pair is defined by specifying the key followed by the => sign and the value associated with that key. Key-value pairs are separated by commas. This syntax allows you to create an associative array where each key is associated with a specific value.

The $grades array therefore contains three elements: "Maths" associated with note 15, "Physics" associated with note 18, and "English_language" associated with note 12. Keys are used to access the corresponding values in the table.

## Accessing elements in an associative array

To access a specific element in an associative array, we use the corresponding key in square brackets.

For example, to access the "first_name" element in the $person associative array, we use $person["first_name"].

If you add the following line of code to your script, you'll retrieve and display the first name: "Amine".

```
echo $person["first_name"]; //retrieves and displays the first name: Amine
```

To access the Maths score in the $grades array, we use $grades["Maths"].

```
echo $grades["Maths"]; //retrieve and display the Maths grade: 15
```

## Adding elements to an associative array

We can add new elements to an associative array by assigning a value to a new key.
For example, to add the element "email" with the value "amine.dupont@example.com" to the
associative array $person, we use :

```
$person["email"] = "amine.dupont@example.com";
```

To display all the elements of an array, we can use the **print_r()** function, predefined in PHP:

```
<?php
$person = [
"last_name" => "Dupont",
"first_name" => "Amine",
"age" => 29,
"gender" => "M",
"country" => "France"
];

$person["email"] = "amine.dupont@example.com";
echo "<pre>";
```
