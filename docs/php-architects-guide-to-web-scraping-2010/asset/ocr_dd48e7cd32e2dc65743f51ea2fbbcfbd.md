```
// Matches 'a' 1 or more times, however many that may be
$matches = (preg_match('/a+/', $string) == 1);

// Matches 'a' 0 times or 1 time if present, same as ?
$matches = (preg_match('/a{0,1}/', $string) == 1);

// Matches 'a' 0 or more times, same as *
$matches = (preg_match('/a{0,}/', $string) == 1);

// Matches 'a' 1 or more times, same as +
$matches = (preg_match('/a{1,}/', $string) == 1);

// Matches 'a' exactly 2 times
$matches = (preg_match('/a{2}/', $string) == 1);
?>
```

Note that any use of curly brackets that is not of the form {X}, {X,}, or {X,Y} will be treated as a literal string within the pattern.

# ## Subpatterns

You’ll notice in the examples from the previous section that only a single character was used. This is because the concept of **subpatterns** hadn’t been introduced yet. To understand these, it’s best to look an example that doesn’t use them in order to understand the effect they have on how the pattern matches.

```
<?php
// Matches 'a' follow by one or more instances of 'b'
$matches = (preg_match('/ab+/', $string) == 1);
?>
```

Without subpatterns there would be no way to match, for example, one or more instances of the string 'ab'. Subpatterns solve this pattern by allowing individuals parts of a pattern to be grouped using parentheses.

```
<?php
// Matches 'ab' one or more times
$matches = (preg_match('/(ab)+/', $string) == 1);
```