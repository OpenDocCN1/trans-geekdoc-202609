If you're familiar with other languages such as C++, you'll be happy to know that in PHP you can add new elements to the end of an array on the fly, even after you've created the array, thereby making the array longer. In C++, you can't do that.

After you create an array, you can change the value in one of its elements by simply assigning something new to the element. Suppose you have an array called $nums, and you initialized element 2 to have the value 4. You now want this element to have the value 10. Here's how you can change the value:

```
$nums[2] = 10;
```

This statement replaces whatever value element 2 previously had with the value 10.

In PHP, a variable doesn't have a fixed type. Therefore, you can write code such as this:

```
$nums[2] = 10;
```

Then later, you can change it to this:

```
$nums[2] = 'hello';
```

You can also add new values to an array, simply by assigning them with an index. Here's an example:

```
<?php
$needmore = array(
    "icecream" => "chocolate",
    "pizza" => "pepperoni",
    "sandwich" => "turkey" );
$needmore["snacks"] = "potato chips";
print $needmore["pizza"]."<br>\n";
print $needmore["snacks"];
?>
```

Here, I created the $needmore array and put three items in it. Then I added another item to the array, the value potato chips for the index snacks.

# Removing a value from an array

To remove an item from an array, use the unset keyword. (Yes, the name is a little strange, but this is the world of computers.) Here's an example: