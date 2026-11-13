
powerful feature that gives you the ability to easily write the contents of a PHP array to a database or file.

Lessons 17, "Filesystem Access," and 19, "Using a MySQL Database," deal with the specifics of filesystem and database storage. For now let's just take a look at how serialization of an array works.

Calling `serialize` with an array argument returns a string that represents the keys and values in that array, in a structured format. You can then decode that string by using the `unserialize` function to return the original array.

The serialized string that represents the associative array `$temps` is as follows:

```
a:12:{s:3:"jan";i:38;s:3:"feb";i:40;s:3:"mar";i:49;
s:3:"apr";i:60;s:3:"may";i:70;s:3:"jun";
i:79;s:3:"jul";i:84;s:3:"aug";i:83;s:3:"sep";
i:76;s:3:"oct";i:65;s:3:"nov";i:54;s:3:"dec";i:42;}
```

You can probably figure out how this string is structured, and the only argument you would ever pass to `unserialize` is the result of a serialize operation. There is no point in trying to construct it yourself.

## Multidimensional Arrays

It is possible and often very useful to use arrays to store two-dimensional or even multidimensional data.

### Accessing Two-Dimensional Data

In fact, a *two-dimensional array* is an array of arrays. Suppose you were to use an array to store the average monthly temperature, by year, using two key dimensions the month and the year. You might display the average temperature from February 1995 as follows:

```
echo $temps[1995]["feb"];
```

Because `$temps` is an array of arrays, `$temps[1995]` is an array of temperatures, indexed by month, and you can reference its elements by adding the key name in square brackets.

### Defining a Multidimensional Array

Defining a multidimensional array is fairly straightforward, as long as you remember that what you are working with is actually an array that contains more arrays.

You can initialize values by using references to the individual elements, as follows:

```
$temps[1995]["feb"] = 41;
```

You can also define multidimensional arrays by nesting the array function in the appropriate places. The following example defines arrays by nesting the array function in the appropriate places. The following example defines the first few months for three years (the full array would clearly be much larger than this):

```
$temps = array (
    1995 => array ("jan" => 36, "feb" => 42, "mar" => 51),
    1996 => array ("jan" => 37, "feb" => 42, "mar" => 49),
    1997 => array ("jan" => 34, "feb" => 40, "mar" => 50) );
```

The `print_r` function can follow as many dimensions as an array contains, and the formatted output will be indented to make each level of the hierarchy readable. The following is the output from the three-dimensional `$temps` array just defined:

```
Array
(
    [1995] => Array
    (
        [jan] => 36
        [feb] => 42
        [mar] => 51
    )

    [1996] => Array
    (
        [jan] => 37
        [feb] => 42
        [mar] => 49
    )

    [1997] => Array
    (
        [jan] => 34
        [feb] => 40
        [mar] => 50
    )

)
```

## Summary

In this lesson you have learned how to create arrays of data and manipulate them. The next lesson examines how regular expressions are used to perform pattern matching on strings.

## Lesson 8. Regular Expressions

In this lesson you will learn about advanced string manipulation using regular expressions. You will see how to use regular expressions to validate a string and to perform a search-and-replace operation.

### Introducing Regular Expressions

Using regular expressions sometimes known as _regex_ is a powerful and concise way of writing a rule that identifies a particular string format. Because they can express quite complex rules in only a few characters, if you have not come across them before, regular expressions can look very confusing indeed.

At its very simplest, a regular expression can be just a character string, where the expression matches any string that contains those characters in sequence. At a more advanced level, a regular expression can identify detailed patterns of characters within a string and break a string into components based on those patterns.

### Types of Regular Expression

PHP supports two different types of regular expressions: the POSIX-extended syntax which is examined in this lesson and the Perl-Compatible Regular Expression (PCRE). Both types perform the same function, using a different syntax, and there is really no need to know how to use both types. If you are already familiar with Perl, you may find it easier to use the PCRE functions than to learn the POSIX syntax.

Documentation for PCRE can be found online at www.php.net/manual/en/ref.pcre.php.

### Using ereg

The ereg function in PHP is used to test a string against a regular expression. Using a very simple regex, the following example checks whether $phrase contains the substring PHP:

```php
$phrase = "I love PHP";
if (ereg("PHP", $phrase)) {
    echo "The expression matches";
}
```

If you run this script through your web browser, you will see that the expression does indeed match $phrase.

Regular expressions are case-sensitive, so if the expression were in lowercase, this example would not find a match. To perform a non-case-sensitive regex comparison, you can use eregi:

```php
if (eregi("php", $phrase)) {
    echo "The expression matches";
}
```

**Performance** The regular expressions you have seen so far perform basic string matching that can also be performed by the functions you learned about in Lesson 6, "Working with Strings," such as strstr. In general, a script will perform better if you use string functions in place of ereg for simple string comparisons.

### Testing Sets of Characters

As well as checking that a sequence of characters appears in a string, you can test for a set of characters by enclosing them in square brackets. You simply list all the characters you want to test, and the expression matches if any one of them occurs.

The following example is actually equivalent to the use of eregi shown earlier in this lesson:

```php
if (ereg("[Pp][Hh][Pp]", $phrase)) {
    echo "The expression matches";
}
```

This expression checks for either an uppercase or lowercase P, followed by an uppercase or lowercase H, followed by an uppercase or lowercase P.

You can also specify a range of characters by using a hyphen between two letters or numbers. For example, [A-Z] would match any uppercase letter, and [0-4] would match any number between zero and four.

The following condition is true only if $phrase contains at least one uppercase letter:

```
if (ereg("[A-Z]", $phrase)) ...
```

The ^ symbol can be used to negate a set so that the regular expression specifies that the string must not contain a set of characters. The following condition is true only if $phrase contains at least one non-numeric character:

```
if (ereg("[^0-9]", $phrase)) ...
```

### Common Character Classes

You can use a number of sets of characters when using regex. To test for all alphanumeric characters, you would need a regular expression that looks like this:

```
[A-Za-z0-9]
```

The character class that represents the same set of characters can be represented in a much clearer fashion:

```
[[:alnum:]]
```

The [: and :] characters indicate that the expression contains the name of a character class. The available classes are shown in Table 8.1.

### Table 8.1. Character Classes for Use in Regular Expressions

| Class Name | Description |
|---|---|
| alnum | All alphanumeric characters, A-Z, a-z, and 0-9 |
| alpha | All letters, A-Z and a-z |
| digit | All digits, 0-9 |
| lower | All lowercase characters, a-z |
| print | All printable characters, including space |
| punct | All punctuation characters (any printable character that is not a space or alnum) |
| space | All whitespace characters, including tabs and newlines |
| upper | All uppercase letters, A-Z |

### Testing for Position

All the expressions you have seen so far find a match if that expression appears anywhere within the compared string. You can also test for position within a string in a regular expression.

The ^ character, when not part of a character class, indicates the start of the string, and $ indicates the end of the string. You could use the following conditions to check whether $phrase begins or ends with an alphabetic character, respectively:

```
if (ereg("^[a-z]", $phrase)) ...
```

```
if (ereg("[a-z]$", $phrase)) ...
```

If you want to check that a string contains only a particular pattern, you can sandwich that pattern between ^ and $. For example, the following condition checks that $number contains only a single numeric digit:

```
if (ereg("^[[:digit:]]$", $number)) ...
```

![](img/2edc6e6954e3485ad7d94117645931d8_95_0.png)

**The Dollar Sign** If you want to look for a literal $ character in a regular expression, you must delimit the character as \$ so that it is not treated as the end-of-line indicator.

When your expression is in double quotes, you must use \\$ to double-delimit the character; otherwise, the $ sign may be interpreted as the start of a variable identifier.

### Wildcard Matching
