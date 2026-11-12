Let’s look at the argument string haystack. This says the first argument should be a string value, while haystack simply names the argument so that it can be referred to in the detailed description. Note that the third argument is placed inside square brackets, which means it’s optional (i.e. you don’t have to supply this argument).

Here’s how you could use strpos:

```
<?php
$haystack = 'Hello World!';
$needle = 'orld';
// Use the strpos() function
$position = strpos($haystack, $needle);
echo 'The substring "' . $needle . '" in "' . $haystack . '" begins at character ' . $position;
?>
```

Notice that I’ve used strpos similarly to the way it appears in the manual. I used the variable names $haystack and $needle to make clear the way each relates to the explanation in the manual, but you can use whatever variable names you like.

The function signature convention is used consistently throughout the manual, so once you’re used to it, you’ll be able to grasp quickly how to use functions you haven’t tried before.

# Get Help When Problems Arise

> If you make a mistake using an in-built function in PHP 4.3.0, the default error reporting mechanism of PHP will display an error message with a link that takes you directly to the manual.

If you’re ever in doubt, be sure to read through the comments submitted by other PHP developers, which appear at the bottom of every page in the manual. Usually, you will at least see an example of how the function is used, which may solve the particular dilemma you’ve run into. In many cases you’ll also find alternative explanations and uses for a function, which help broaden your understanding.