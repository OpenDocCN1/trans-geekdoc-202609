PHP 8 has been tidied up. The string is now only converted into a number if it also results in a meaningful number. If not, the comparison is made on a string basis; that is, "0" is compared with "test" and results in false.

# Sorting Strings Alphabetically

To sort strings alphabetically, there is a simple trick: store the strings in variables specifically for the comparison and convert them to lower- or uppercase letters before you compare them (see Figure 5.3).

```
<?php
$a = "a";
$b = "B";

$a_low = strtolower($a);
$b_low = strtolower($b);

if ($a_low < $b_low) {
    echo "$a is before $b in the alphabet.";
} else {
    echo "$b is before $a in the alphabet.";
}
?>
```

Listing 5.3 Sort Strings Alphabetically ("strings_sort.php")

![](bbox=[0.149, 0.543, 0.805, 0.693])

Figure 5.3 Now Strings Are Compared Regardless of Upper- and Lowercase Characters

In practice, this simple trick is often used in conjunction with arrays. PHP offers its own function called sort() for sorting an array:

```
$collection = array("Monet", "Chagal", "Dali", "Manet");
sort($collection);
```

If you output the first and last element of the sorted array, then Chagal and Monet are output correctly:

```
echo "$collection[0] and $collection[3]";
```