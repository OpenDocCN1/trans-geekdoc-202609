```
```php
$a = "PHP is great";
$i = 1;
$start = strtok($a, " ");
while ($start) {
    $name = "part" . $i;
    $$name = $start;
    $start = strtok(" ");
    $i++;
    echo $$name . " ";
}
```
```

Listing 7.7 "strtok()" with Loop ("strtok_loop.php")

# 7.2.5 Strings and Arrays

Splitting and joining strings also includes converting strings into an array and vice versa. There are different powerful functions for both.

# String to Array

Let's start simple. The explode(delimiter, string, limit) function splits a string into an array at certain delimiters. If the optional Limit parameter is specified, only as many array elements are created as the limit specifies. The last array element contains the rest of the string regardless of its length.

Consider the following simple example. First, the script splits the string at each space and then outputs the individual elements of the array.

```
```php
<?php
$a = "PHP is great";
$strings = explode(" ", $a);
foreach ($strings as $element) {
    echo $element . "<hr />;
}
?>
```
```

Listing 7.8 "explode()" ("explode.php")

But what if, for example, you want to take several separators into account? In this case, there are a few other approaches, which are explained in more detail in the following sections.

# Custom Functions

It is often best to quickly write your own function, especially for separating. You can find some of these in the PHP documentation, especially in the useful user comments.