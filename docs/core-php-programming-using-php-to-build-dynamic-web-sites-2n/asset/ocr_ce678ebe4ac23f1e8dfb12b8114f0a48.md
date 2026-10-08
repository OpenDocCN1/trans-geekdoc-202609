# string ucfirst(string text)

Use the ucfirst function to capitalize the first character of a string. Compare this function to strtoupper and ucwords. As with these other functions, your locale determines which characters are considered letters.

```
<?php
print(ucfirst("i forgot to capitalize something."));
?>
```

# string ucwords(string text)

Use the ucwords function to capitalize every word in a string. Compare it to strtoupper and ufirst. As with these other functions, your locale determines which characters are considered letters.

```
<?php
print(ucwords("core PHP programming"));
?>
```

# array unpack(string format, string data)

The unpack function transforms data created by the pack function into an associative array. The format argument follows the same rules as pack except that each element is separated by a slash to them to be named. These names are used as the keys in the returned associative array. See the pack example.

# value unserialize(string data)

Use unserialize to transform serialized data back into a PHP value. The description of serialize has an example of the entire process.

# string urldecode(string url_text)

The urldecode function returns the url_text string translated from URL format into plain text. It is not safe for binary data.

```
?>
```