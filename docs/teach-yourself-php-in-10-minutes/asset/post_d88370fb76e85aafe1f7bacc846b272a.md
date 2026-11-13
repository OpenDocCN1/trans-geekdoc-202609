
### Random Algorithms

PHP includes another random number generator, known as Mersenne Twister, that is considered to produce better random results than `rand`. To use this algorithm, you use the functions `mt_rand` and `mt_srand`.

## Mathematical Functions

PHP includes many mathematical functions, including trigonometry, logarithms, and number base conversions. As you will rarely need to use these in a web environment, those functions are not covered in this book.

To find out about a function that performs a specific mathematical purpose, refer to the online manual at www.php.net/manual/en/ref.math.php.

## Summary

In this lesson you have learned how to work with numbers. In the next lesson you will learn all about string handling in PHP.

## Lesson 6. Working with Strings

In this lesson you will learn about some of the powerful string functions that are included in the PHP language.

## Anatomy of a String

A *string* is a collection of characters that is treated as a single entity. In PHP, strings are enclosed in quotation marks, and you can declare a string type variable by assigning it a string that is contained in either single or double quotes.

The following examples are identical; both create a variable called `$phrase` that contains the phrase shown:

```
$phrase = "The sky is falling";
$phrase = 'The sky is falling';
```

> **Quote Characters** Quotation marks in PHP do not point in a direction. The same symbol is used to start a string as to indicate the end. You must use two apostrophe characters (` ` ) around a single-quoted string; do not use backtick characters (` ` ).

### Escaping Characters with Backslash

Double quotes can be used within single-quoted strings and vice versa. For instance, these string assignments are both valid:

```
$phrase = "It's time to party!";
$phrase = 'So I said, "OK"';
```

However, if you want to use the same character within a quoted string, you must escape that quote by using a backslash. The following examples demonstrate this:

```
$phrase = 'It\'s time to party!';
$phrase = "So I said, \"OK\"";
```

In the previous examples, if the backslash were not used, PHP would mismatch the quotes, and an error would result.

Which style of quoting you use largely depends on personal preference and, hopefully, a desire to create tidy code. Remember, though, as you saw in Lesson 2, "Variables," that a variable prefixed with a dollar sign inside a double-quoted string is replaced with its values, whereas in a single-quoted string, the dollar sign and variable name appear verbatim.

If you want a dollar sign to form part of a double-quoted string, you can also escape this by using a backslash. For example, the following two statements are equivalent:

```
$offer = 'Save $10 on first purchase';
$offer = "Save \$10 on first purchase";
```

Without the backslash, the second example would attempt to find the value of a variable called `$10`, which is, in fact, an illegal variable name.

The backslash character can also be used in a double-quoted string to indicate some special values inside strings. When followed by a three-digit number, it indicates the ASCII character with that octal value.

You can send the common nonprintable ASCII characters by using standard escape characters. A newline is `\n`, tab is `\t`, and so on. Refer to man ascii on your system or www.ascii.cl for a comprehensive list.

### Concatenation

You have already seen how strings can be joined using the period symbol as a concatenation operator. A compound version of this operator, `.=`, can be used to append a string to an existing variable.

The following example builds up a string in stages and then displays the result:

```
$phrase = "I want ";
$phrase .= "to teach ";
$phrase .= "the world ";
$phrase .= "to sing";
echo $phrase;
```

The phrase appears as expected. Note the use of spaces after teach and world to ensure that the final string is correctly spaced.

### Comparing Strings

You can compare string values simply by using the standard comparison operators. To check whether two strings are equal, you use the double equals (`==`) sign:

```
if ($password == "letmein")
    echo "You have a guessable password";
```

The equality operator, when applied to strings, performs a case-sensitive comparison. In the previous example, any other capitalization of `$password`, such as `LetMeIn`, would not pass this test.

The inequality operators `<`, `<=`, `>`, and `>=` perform a comparison based on the ASCII values of the individual characters in the strings. The following condition could be used to divide people into two groups, based on their last names—those with names beginning A-M and those beginning N-Z:

```
if ($last_name < "N")
    echo "You are in group 1";
else
    echo "You are in group 2";
```

![](img/2edc6e6954e3485ad7d94117645931d8_70_0.png)

**ASCII Values** Because string comparisons are done on their underlying ASCII values, all lowercase letters have higher values than their equivalent uppercase letters. Letters `a-z` have values `97-122`, whereas `A-Z` occupy values `65-90`.

## Formatting Strings

PHP provides a powerful way of creating formatted strings, using the `printf` and `sprintf` functions. If you have used this function in C, these will be quite familiar to you, although the syntax in PHP is a little different.

### Using printf

You use `printf` to display a formatted string. At its very simplest, `printf` takes a single string argument and behaves the same as `echo`:

```
printf("Hello, world");
```

The power of `printf`, however, lies in its ability to substitute values into placeholders in a string. Placeholders are identified by the percent character (`%`), followed by a format specification character.

The following example uses the simple format specifier `%f` to represent a float number.

```
$price = 5.99;
printf("The price is %f", $price);
```

The second argument to `printf` is substituted in place of `%f`, so the following output is produced:

```
The price is 5.99
```

There is actually no limit to the number of substitution arguments in a `printf` statement, as long as there are an equivalent number of placeholders in the string to be displayed. The following example demonstrates this by adding in a string item:

```
$item = "The Origin of Species";
$price = 5.99;
printf("The price of %s is %f", $item, $price);
```

### Table 6.1. `printf` Format Characters

| Character | Meaning |
|---|---|
| b | A binary (base 2) number |
| c | The ASCII character with the numeric value of the argument |
| d | A signed decimal (base 10) integer |
| e | A number displayed in scientific notation (for example, 2.6e+3) |
| u | An unsigned decimal integer |
| f | A floating-point number |
| o | An octal (base 8) number |
| s | A string |
| x | A hexadecimal (base 16) number with lowercase letters |
| X | A hexadecimal (base 16) number with uppercase letters |

Suppose you use the `%d` format specifier instead of `%f` to display the value of `$price`:

```
$price = 5.99;
printf("As a decimal, the price is %d", $price);
```

In this case, PHP will treat the argument passed as an integer, so only the whole part of the value will be displayed. The output produced is as follows.

As a decimal, the price is 5

**Decimals** The `%d` format string represents a decimal integer, with *decimal* referring to base 10 numbers and not decimal points. There are different format specifiers to display numbers in base 16 (*hex*, `%x`), base 8 (*octal*, `%o`), and base 2 (*binary*, `%b`).

### Format Codes

A format specifier can also include optional elements to specify the padding, alignment, width, and precision of the value to be displayed. This allows you to carry out some very powerful formatting.

The width specifier indicates how many characters the formatted value should occupy in the displayed string and appears between the percent sign and the type specifier. For instance, the following example ensures that the name displayed takes up exactly 10 characters:

```
$name1 = "Tom";
$name2 = "Dick";
$name3 = "Harry";
echo "<PRE>";
printf("%10s \n", $name1);
printf("%10s \n", $name2);
printf("%10s \n", $name3);
echo "</PRE>";
```

**Padding** These examples use `<PRE>` tags to make sure that multiple spaces used for padding are displayed onscreen. Usually a web browser will treat multiple adjacent whitespace characters as a single space.

String padding is not used very often in creating dynamic web pages. However, it is useful when you're producing plain-text output, such as generated email text, in PHP.

If you run this example through a web browser, you will see that each name displayed is indented from the left of the screen by the correct number of characters to make each name right-aligned with the others.

The default behavior is to right-align to the given width. However, you can reverse this by using the minus symbol as an alignment specifier. To left-align the strings in the previous example, you would use the format specifier `%-10s`. Although visibly this would not appear any different from simply using `%s`, the strings would be padded on the right with spaces to a length of 10 characters.

You can change the padding character from a space to any other character by placing that character before the width value, prefixed with a single quotation mark. The following example ensures that a five-digit order number is always displayed padded with zeros if necessary:

```
$order = 201;
printf("Order number: %'05d", $order);
```

The output produced is as follows:

```
Order number: 00201
```
