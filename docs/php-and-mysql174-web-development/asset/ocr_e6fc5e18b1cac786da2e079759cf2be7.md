This function can be useful for splitting email addresses, domain names, or dates. For example,

```
$address = 'username@example.com';
$arr = preg_split('/\.|@|', $address);
while (list($key, $value) = each($arr)) {
    echo '<br />' . $value;
}
```

This example splits the =email address into its three components and prints each on a separate line:

```
username
example
com
```

> Note
In general, the regular expression runs less efficiently than the string functions with similar functionality. If your task is simple enough to use a string expression, do so. This may not be true for tasks that can be performed with a single regular expression but multiple string functions.

# Further Reading

PHP has many string functions. We covered the more useful ones in this chapter, but if you have a particular need (such as translating characters into Cyrillic), check the PHP manual online to see whether PHP has the function for you.

The amount of material available on regular expressions is enormous. You can start with the man page for regexp if you are using Unix.

Regular expressions take a while to sink in; the more examples you look at and run, the more confident you will be using them.

# Next

In the next chapter, we discuss several ways you can use PHP to save programming time and effort and prevent redundancy by reusing pre-existing code.