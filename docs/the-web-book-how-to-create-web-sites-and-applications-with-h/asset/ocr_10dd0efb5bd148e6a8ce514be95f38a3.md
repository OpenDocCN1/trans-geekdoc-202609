introduces the possibility of an error in the program if we forget to do this. As you might expect, there’s a way round it. Just change the “for” loop to:

```
$total_drinks = count($drink);  
for($i = 0; $i <= $total_drinks; $i++)
```

The count() function returns the number of elements in the specified array. But remember that arrays start at zero, so treat the returned count accordingly. In this case, the function returns 9, but that doesn’t mean the highest-numbered drink is element 9. The list starts at 0, so the highest-numbered element will be one less than the value which count() returns.

When you’re adding data to an array, you don’t even have to specify the numeric bit if you don’t want to. The following will work just fine, and PHP will allocate the numbers automatically, starting from zero. This is handy if you’re reading a list of items from a database and you want to add them to an array in order to manipulate them.

```
$drink[] = "Whiskey";  
$drink[] = "Brandy";  
$drink[] = "Pint of lager";  
$drink[] = "Shandy";  
$drink[] = "White wine (large)";  
$drink[] = "White wine (small)";  
$drink[] = "Red wine (large)";  
$drink[] = "Red wine (small)";
```

PHP has lots of useful functions for manipulating data in arrays. For example, `array_sort` does what you might expect, allowing you to add just one line of code to the above program to present the list of drinks in alphabetical order. Although, if you were reading the list of drinks from a database table, it’s far more efficient to use the `ORDER BY` clause as part of the MySQL query, in order to retrieve a ready-sorted list, rather than read the data in a random order from the database and then sort it within the array.

Before we finish our very brief introduction to arrays, there’s something important that you need to know about them. In some languages, such as Basic, array subscripts (ie, the bit in square brackets) have to be sequential and numeric. In PHP, this is not the case. We could, if we wish, create our array of drinks thus:

```
$drink["a"] = "Whiskey";  
$drink["fred"] = "Brandy";  
$drink[2] = "Pint of lager";  
$drink["hello"] = "Shandy";  
$drink[412] = "White wine (large)";
```