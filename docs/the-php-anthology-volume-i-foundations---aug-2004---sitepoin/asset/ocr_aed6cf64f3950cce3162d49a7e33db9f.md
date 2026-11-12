All of these means of passing a variable create a copy of that variable’s value; this is called **passing by value**.

# # Using a Reference

To pass using a reference, you need to use the reference operator & (ampersand). For example:

```
<?php
$color = 'blue';
$settings['color'] = &$color;
?>
```

$settings['color'] now contains a *reference* to the original $color variable.

Compare the following examples, the first using PHP’s default copying behavior:

```
<?php
$color = 'blue';
$settings['color'] = $color; // Makes a copy
$color = 'red'; // $color changes
echo $settings['color']; // Displays "blue"
?>
```

The second involves **passing by reference**:

```
<?php
$color = 'blue';
$settings['color'] = &$color; // Makes a reference
$color = 'red'; // $color changes
echo $settings['color']; // Displays "red"
?>
```

Passing by reference allows us to keep the new variable “linked” to the original source variable. Changes to either the new variable or the old variable will be reflected in the value of both.

So far, so good. You’re probably wondering, “What’s the big deal here? What difference does it make whether PHP copies or makes a reference to a variable, as long as we get what we expected?” For variables passed around a procedural program, you hardly ever need to worry about references. However, when it comes to objects interacting with one another, if you don’t pass an object by reference, you may well get results you weren’t expecting.