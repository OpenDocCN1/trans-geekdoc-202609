
Another useful related function is `str_word_count()`, which returns the number of words in a string. For example:

```php
echo str_word_count( "Hello, world!" ); // Displays 2
```

## Accessing Characters within a String

You might be wondering how you can access the individual characters of a string. PHP makes this easy for you. To access a character at a particular position, or _index_, within a string, use:

```php
$character = $string[index];
```

In other words, you place the index between square brackets after the string variable name. String indices start from 0, so the first character in the string has an index of 0, the second has an index of 1, and so on. You can both read and change characters this way. Here are some examples:

```php
$myString = "Hello, world!";
echo $myString[0] . "<br />"; // Displays 'H'
echo $myString[7] . "<br />"; // Displays 'w'
$myString[12] = '?';
echo $myString . "<br />"; // Displays 'Hello, world?'
```

If you need to extract a sequence of characters from a string, you can use PHP's `substr()` function. This function takes the following parameters:

- The string to extract the characters from
- The position to start extracting the characters. If you use a negative number, `substr()` counts backward from the end of the string
- The number of characters to extract. If you use a negative number, `substr()` misses that many characters from the end of the string instead. This parameter is optional; if left out, `substr()` extracts from the start position to the end of the string

Here are a few examples that show how to use `substr()` :

```php
$myString = "Hello, world!";
echo substr( $myString, 0, 5 ) . "<br />"; // Displays 'Hello'
echo substr( $myString, 7 ) . "<br />"; // Displays 'world!'
echo substr( $myString, -1 ) . "<br />"; // Displays '!'
echo substr( $myString, -5, -1 ) . "<br />"; // Displays 'orld'
```

You can't modify characters within strings using `substr()` . If you need to change characters within a string, use `substr_replace()` instead. This function is described later in the chapter.

## Searching Strings

Often it's useful to know whether one string of text is contained within another. PHP gives you several string functions that let you search for one string inside another:

- strstr() tells you whether the search text is within the string
- strpos() and strrpos() return the index position of the first and last occurrence of the search text, respectively
- substr_count() tells you how many times the search text occurs within the string
- strpbrk() searches a string for any of a list of characters

### Searching Strings with strstr()

If you just want to find out whether some text occurs within a string, use strstr() . This takes two parameters: the string to search through, and the search text. If the text is found, strstr() returns the portion of the string from the start of the found text to the end of the string. If the text isn't found, it returns false. For example:

```php
$myString = "Hello, world!";
echo strstr( $myString, "wor" ) . "<br />"; // Displays 'world!'
echo ( strstr( $myString, "xyz" ) ? "Yes" : "No" ) . "<br />"; // Displays 'No'
```

As of PHP 5.3, you can also pass an optional third Boolean argument. The default value is false. If you pass in a value of true, strstr() instead returns the portion from the start of the string to the character before the found text:

```php
$myString = "Hello, world!";
echo strstr( $myString, "wor", true ); // Displays 'Hello, '
```

### Locating Text with strpos() and strrpos()

To find out exactly where a string of text occurs within another string, use strpos() . This function takes the same two parameters as strstr() : the string to search, and the search text to look for. If the text is found, strpos() returns the index of the first character of the text within the string. If it’s not found, strpos() returns false :

```php
$myString = "Hello, world!";
echo strpos( $myString, "wor" ); // Displays '7'
echo strpos( $myString, "xyz" ); // Displays '' (false)
```

There’s a gotcha when the searched text occurs at the start of the string. In this case, strpos() returns 0 (the index of the first character of the found text), but it’s easy to mistake this for a return value of false if you’re not careful. For example, the following code will incorrectly display "Not found" :

```php
$myString = "Hello, world!";
if ( !strpos( $myString, "Hel" ) ) echo "Not found";
```

So you need to test explicitly for a false return value, if that’s what you’re checking for. The following code works correctly:

```php
$myString = "Hello, world!";
if ( strpos( $myString, "Hel" ) === false ) echo "Not found";
```

strpos() can take an optional third argument: an index position within the string to start the search. Here's an example:

```php
$myString = "Hello, world!";
echo strpos( $myString, "o" ) . "<br />"; // Displays '4'
echo strpos( $myString, "o", 5 ) . "<br />"; // Displays '8'
```

You can use this third argument, combined with the fact that strpos() returns the position of the matched text, to repeatedly find all occurrences of the search text within the string — for example:

```php
$myString = "Hello, world!";
$pos = 0;
while ( ( $pos = strpos( $myString, "l", $pos ) ) !== false ) {
    echo "The letter 'l' was found at position: $pos<br />" ;
    $pos++;
}
```

This code produces the output shown in Figure 5-1.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_117_0.png)

Figure 5-1

strpos() has a sister function, strrpos(), that does basically the same thing; the only difference is that strrpos() finds the last match in the string, rather than the first:

```php
$myString = "Hello, world!";
echo strpos( $myString, "o" ) . "<br />" ; // Displays '4'
echo strrpos( $myString, "o" ) . "<br />" ; // Displays '8'
```

As with strpos(), you can pass an optional third argument indicating the index position from which to start the search. If this index position is negative, strrpos() starts that many characters from the end of the string, rather than from the beginning.

### Finding the Number of Occurrences with substr_count()

Occasionally you might need to know how many times some text occurs within a string. For example, if you were writing a simple search engine, you could search a string of text for a keyword to see how relevant the text is for that keyword; the more occurrences of the keyword, the greater the chance that the text is relevant.

You could find the number of occurrences easily enough using `strpos()` and a loop, but PHP, as in most other things, gives you a function to do the job for you: `substr_count()` . To use it, simply pass the string to search and the text to search for, and the function returns the number of times the text was found in the string. For example:

```php
$myString = "I say, nay, nay, and thrice nay!";
echo substr_count( $myString, "nay" ); // Displays '3'
```

You can also pass an optional third argument to specify the index position to start searching, and an optional fourth argument to indicate how many characters the function should search before giving up. Here are some examples that use these third and fourth arguments:

```php
$myString = "I say, nay, nay, and thrice nay!";
echo substr_count( $myString, "nay", 9 ) . "<br />"; // Displays '2'
echo substr_count( $myString, "nay", 9, 6 ) . "<br />"; // Displays '1'
```

### Searching for a Set of Characters with strpbrk()

What if you need to find out if a string contains any one of a set of characters? For example, you might want to make sure a submitted form field doesn't contain certain characters for security reasons. PHP gives you a function, `strpbrk()`, that lets you easily carry out such a search. It takes two arguments: the string to search, and a string containing the list of characters to search for. The function returns the portion of the string from the first matched character to the end of the string. If none of the characters in the set are found in the string, `strpbrk()` returns false .

Here are some examples:

```php
$myString = "Hello, world!";
echo strpbrk( $myString, "abcdef" ); // Displays 'ello, world!'
echo strpbrk( $myString, "xyz" ); // Displays '' (false)
```

```php
$username = "matt@example.com";
if ( strpbrk( $username, "@!" ) ) echo "@ and ! are not allowed in usernames";
```

### Replacing Text within Strings

As well as being able to search for text within a larger string, you can also replace portions of a string with different text. This section discusses three useful PHP functions for replacing text:

- str_replace() replaces all occurrences of the search text within the target string
- substr_replace() replaces a specified portion of the target string with another string
- strtr() replaces certain characters in the target string with other characters

### Replacing All Occurrences using str_replace()

str_replace() lets you replace all occurrences of a specified string with a new string. It's the PHP equivalent of using the Replace All option in a word processor.
