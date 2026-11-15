```
```php
foreach($words as $word) {
    for ($i = 1; $i < strlen($word); $i++) {
        $ascii = ord(substr($word, $i, 1));
        if ($ascii >= 65 && $ascii <= 90) {
            $big++;
        } elseif ($ascii >= 97 && $ascii <= 122) {
            $small++;
        }
    }
}
if ($big > $small) {
    return ucwords(strtolower($string));
} else {
    return $string;
}
```
```

# Listing 7.16 A Simple Scream Protection ("big_small.php")

If the user now enters PHP CMS SHOP, for example, the function converts this entry into
Php Cms Shop

php cms shop, on the other hand, is left as it is. You could extend and improve this func-
tion as you wish. For example, umlauts could be checked, or you could protect some
terms such as PHP from being converted.

# ## 7.4 Pruning

One function for cutting out parts of a string is substr(). It finds its actual home in this
section. There are also some other auxiliary functions, such as to remove spaces.

# ### 7.4.1 Cut Out Characters

substr(string, start position, length) has three parameters:

+   - string specifies the string that is to be cut.
+   - start position determines where the cutoff begins.
+   - length specifies how many characters are truncated. This parameter is optional. If it
+     is omitted, substr() returns all characters from the start position to the end of the
+     string.

What characterizes substr() is its relatively high flexibility. Take a look at a few exam-
ples. The starting point is the following string: