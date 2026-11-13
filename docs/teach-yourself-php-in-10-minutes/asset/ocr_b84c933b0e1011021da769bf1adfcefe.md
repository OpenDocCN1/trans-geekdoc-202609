# Using ereg

The ereg function in PHP is used to test a string against a regular expression. Using a very simple regex, the following example checks whether $phrase contains the substring PHP :

```
```php
$phrase = "I love PHP";
if (ereg("PHP", $phrase)) {
    echo "The expression matches";
}
```
```

If you run this script through your web browser, you will see that the expression does indeed match $phrase .

Regular expressions are case-sensitive, so if the expression were in lowercase, this example would not find a match. To perform a non-case-sensitive regex comparison, you can use eregi :

```
```php
if (eregi("php", $phrase)) {
    echo "The expression matches";
}
```
```

**Performance** The regular expressions you have seen so far perform basic string matching that can also be performed by the functions you learned about in Lesson 6 , "Working with Strings," such as strstr . In general, a script will perform better if you use string functions in place of ereg for simple string comparisons.

# Testing Sets of Characters

As well as checking that a sequence of characters appears in a string, you can test for a set of characters by enclosing them in square brackets. You simply list all the characters you want to test, and the expression matches if any one of them occurs.

The following example is actually equivalent to the use of eregi shown earlier in this lesson:

```
```php
if (ereg("[Pp][Hh][Pp]", $phrase)) {
    echo "The expression matches";
}
```
```