# PHP — Function spliti()

# Syntax

```
array spliti (string pattern, string string [, int limit])
```

# Definition and Usage

The spliti() function operates exactly in the same manner as its sibling split(), except that it is not case sensitive. Case-sensitive characters are an issue only when the pattern is alphabetical. For all other characters, spliti() operates exactly as split() does.

# Return Value

+   * Returns an array of strings after splitting up a string.

# Example

Following is the piece of code, copy and paste this code into a file and verify the result.

```
<?php
$ip = "123.456.789.000"; // some IP address
$iparr = spliti ("\.", $ip, 3);

print "$iparr[0] <br />";
print "$iparr[1] <br />" ;
print "$iparr[2] <br />" ;
print "$iparr[3] <br />" ;
?>

```

This will produce only three strings as we have limited number of strings to be produced.

```
123
456
789.000
```