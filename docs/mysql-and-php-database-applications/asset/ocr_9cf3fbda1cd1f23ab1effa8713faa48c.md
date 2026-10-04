# Chapter 6: PHP's Built-In Functions 143

Note that if the flag is PREG_SPLIT_NO_EMPTY, empty items will not be placed in the array.
Again, if explode() can do it, make sure to use it.

# In addition to the functions in the previous section, you can make use of split(),
which uses a case-insensitive pattern match.

# Array functions

I am a big fan of the array functions available in PHP 4. Just about anything you'd
like to do to an array you can do with a built-in function. The developers of PHP have\done a good job of making sure you have to loop arrays infrequently.
in the PHP 4.0.2 manual there are exactly 47 listed array functions. It's likely
that by the time you read this chapter, there will be several more. So make sure you
scan the manual to see the full range of available array functions.

![](bbox=[0.181, 0.413, 0.829, 0.487])

# ARRAY FUNCTIONS USED IN THIS BOOK

When you're dealing with database applications, much of your logic should come
within your SQL statements. Then, in the applications presented in this book fairly
few array functions were necessary. Here's a rundown of the ones used.

ARRAY_FLIP() This function, which is useful with associative arrays, exchanges the
keys and values. That is, the keys become the values and the values become the keys.

array array_flip (array trans)
This comes up once in the course of the book, in the following code:

```
$trans = array_flip(get_html_translation_table(HTML_ENTITIES));
$title = strtr($title, $trans);
```

Before the array_flip() function, the array will return many elements. Here
are a couple of examples:

```
[(c)] => &copy
[(r)] => &reg
```