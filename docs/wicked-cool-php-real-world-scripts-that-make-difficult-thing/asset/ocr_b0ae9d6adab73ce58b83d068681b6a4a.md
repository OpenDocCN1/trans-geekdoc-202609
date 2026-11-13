+   3. A second query extracts at most $items_per_page rows from the table,
+      starting at $start_number.
+   4. The row data is formatted.
+   5. The create_navbar() function creates the navigation bar; the formatted
+      bar goes in the $navbar variable.
+   6. The script prints the formatted navigation bar and data.

# #4: Printing the Contents of an Array

Let's say that you have been adding and subtracting items from an array,
but you're running into some problems. What you really need is to view the
contents of an array as they were at a specific line in your script. There's a
really easy way to do this that doesn't get *nearly* the attention that it should
from PHP tutorials around the world—the print_r() function! Here's an
example:

```
<?php
$alacarte = array("chocolate ice cream",
    "vanilla pudding",
    "snozberry whip");
$menu = array ("appetizer" => "fruit",
    "entree" => roast beef,
    "dessert" => $alacarte);
print_r($menu);
?>
```

The print_r() function prints arrays onscreen in a format that humans
can read. This is especially handy when you're dealing with *multidimensional
arrays* (which, if you're not familiar with the term, are arrays that contain
other arrays). Feed an array to print_r(), and you get a simple plaintext
display. Because it uses whitespace but no HTML markup, you may need to
view the page source to see it as it is meant to be seen. The previous sample
results in this output:

```
Array
(
    [appetizer] => fruit
    [entree] => roast beef
    [dessert] => Array
    (
        [0] => chocolate ice cream
        [1] => vanilla pudding
        [2] => snozberry whip
    )
)
```