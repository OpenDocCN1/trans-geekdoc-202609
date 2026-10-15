# Converting Strings to Arrays

```
<?php
  $csvdata = 'Sams Publishing,800 East 96th Street,Indianapolis,Indiana,46240';
  $a = explode(',', $csvdata);
  $info = print_r($a, true);
  echo "<pre>$info</pre>";
?>
```

*Turning a String into an Array (explode.php)*

The PHP function explode() creates an array out of these values; you just have to provide the character(s) at which the string needs to be split. The browser then shows this output:

```
Array
(
    [0] => Sams Publishing
    [1] => 800 East 96th Street
    [2] => Indianapolis
    [3] => Indiana
    [4] => 46240
)
```

# Converting Arrays to Strings

```
$address = implode('<br />', $data);
```

The way back (that is, making a string representation out of the elements in an array) can be done using implode(). Again, two parameters are required: the separation elements, then the array. The order is quite unusual, yet important.

So, PHP joins the elements of the array, using the <br /> HTML element. Therefore, in the browser, each array’s elements stay at its own line.