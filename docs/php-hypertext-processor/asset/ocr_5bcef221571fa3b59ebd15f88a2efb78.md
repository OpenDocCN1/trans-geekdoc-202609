```
array preg_grep ( string $pattern, array $input [, int $flags ] );
```

# Definition and Usage

Returns the array consisting of the elements of the input array that match the given pattern.

If flag is set to PREG_GREP_INVERT, this function returns the elements of the input array that do not match the given pattern.

# Return Value

+   Returns an array indexed using the keys from the input array.

# Example

Following is the piece of code, copy and paste this code into a file and verify the result.

```
<?php
$foods = array("pasta", "steak", "fish", "potatoes");

// find elements beginning with "p", followed by one or more letters.
$p_foods = preg_grep("/p(\w+)/", $foods);

print "Found food is " . $p_foods[0];
print "Found food is " . $p_foods[1];
?>
```

This will produce the following result –

Found food is pastaFound food is

# PHP — Function preg_quote()

# Syntax