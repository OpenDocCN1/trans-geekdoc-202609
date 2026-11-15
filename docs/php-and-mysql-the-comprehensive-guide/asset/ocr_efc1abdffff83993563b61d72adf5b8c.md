you want to rule out the possibility of the user only entering spaces, or if you want to save data cleanly—without whitespaces at the beginning or end—in the database.

PHP offers several functions to clean strings:

+   - trim(String) removes whitespaces at the beginning and end of the string.
+   - ltrim(String) only removes them on the left-hand side—that is, at the beginning of the string.
+   - rtrim(String) deletes whitespaces on the right—that is, at the end.
+   - chop(String) is an alias of rtrim(), so it also removes the whitespaces at the end of a string.

Consider the following small example.

```
<?php
$a = " Space ";
echo "Many " . trim($a) . "!";
?>
```

# Listing 7.17 “trim()” (“trim.php”)

# 7.5 Search and Replace

Search and replace is one of the categories that does a text editor credit. Searching and replacing in strings does not usually have to be quite so sophisticated. Nevertheless, PHP offers a multitude of possibilities.

> **Note**
> You have even more options with regular expressions. More on this follows in chapter 10.

# 7.5.1 Search

The search functions differ in what they return. Is it the position of the string part found, or perhaps the remaining string from this position? The search functions are then subdivided in this section.9

# Position

The strpos(String, search_string, start) function is primarily responsible for searching for a position. It searches a string for the search_string10 and returns the first (!)