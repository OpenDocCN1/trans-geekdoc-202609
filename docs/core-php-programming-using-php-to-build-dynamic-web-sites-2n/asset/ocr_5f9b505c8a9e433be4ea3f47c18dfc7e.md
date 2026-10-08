# Core PHP Programming

```
print("World is at position " . 
strpos($text, "World") . "<BR>\n";
>
```

# strchr

This is an alias for strrpos.

# integer strrpos(string text, string character)

The strrpos function operates similarly to strpos. It returns the last occurrence of the second argument in the first. However, only the first character of the second argument is used. This function offers a very neat way of chopping off the last part of a path, as in the example below.

```
<<?n//set test string
$path = "/usr/local/apache";

// find last slash
$pos = strrpos($path, "/");

//print everything after the last slash
print(substr($path, $pos+1));
>
```

# integer strspn(string text, string set)

The strspn function returns the position in the first character in the text argument that is not part of the set of characters in the set argument. Compare this function to strcspn.

```
<<?$text = "cabbage";
$set = "abc";
$position = strspn($text, $set);

// prints 'cabba'
print(substr($text, 0, $position));
>
```