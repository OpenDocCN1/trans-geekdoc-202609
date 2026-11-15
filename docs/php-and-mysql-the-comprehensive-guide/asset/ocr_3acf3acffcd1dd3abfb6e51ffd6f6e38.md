+   - If there is a `k` at the beginning, the data is sorted by index. The index/value assignments are also retained here. All other sorting functions sort by value.
+   - The index/value assignments change for all others.
+   - A `u` means that the function expects a sort function as a parameter.
+   - A `nat` means that a natural sorting is attempted, as a human would do. For example, the numbers 1, 2, and 3 are sorted before 10, 20, and and 30. An algorithm from Martin Pool is used for this is used for this (see http://s-prs.co/v602269).

Consider the following simple example. The `sort()` function sorts by value (as `k` is not specified for `key`), and it changes the index/value assignments. The sort function—like all others—changes the original array. Figure 8.20 shows the result.

```
<?php
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
sort($days);
print_r($days);
?>
```

# Listing 8.19 "sort()" ("sort.php")

![](bbox=[0.14, 0.455, 0.74, 0.545])

# Figure 8.20 Alphabetical Sorting

# 8.6 Superglobal Arrays

_Superglobal arrays_ are actually very easy to describe. They are (associative) arrays that contain important information. For example, `$_SERVER` contains HTTP headers, paths, and so on; `$_POST` and `$_GET` contain data from sent forms; and `$_SESSION` contains information about user sessions. As they are so important, we will briefly introduce them here and refer to the chapters in which they are explained in more detail for the frequently used ones.

But before we get to that, a few general words about superglobal arrays. When PHP 4 was released, it was very easy to access form values in PHP. You could simply use the name of the HTML field as a variable. Before PHP 5.4, it was possible to set the `register_globals` directive in `php.ini` to `On`. As of PHP 5.4, this option has been removed for good. This is a good thing as it is a potential security vulnerability.³

3 More on this in Chapter 13 and in Chapter 32.