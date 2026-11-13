
## Appendix G

## Regular Expressions Overview

REGULAR EXPRESSIONS PROVIDE a means for pattern matching in strings. Patterns may be as simple as a literal string (like my dog spot) or a literal string with a wild-card character (like Mr.* Baggins), or they can grow to be very complex. How complex? Check out the following example, which is intended to perform email validation. If you're new to regular expressions this may look nasty, but to tell the truth it's not nearly nasty enough. In fact, to properly validate an email takes about 200 lines of regular expressions.

```
^[_.\0-9a-z-]+@([0-9a-z][0-9a-z-]+\.)+[a-z]{2,3}$
```

When you're working with PHP and MySQL, three variants of regular expressions exist that you might need to use: the regular PHP regular-expression functions, the Perl-Compatible Regular Expression (PCRE) functions, and MySQL regular-expression functions. The PHP ereg(), eregi(), ereg_replace(), eregi_replace(), split(), and spliti() functions use these patterns.

The PCREs are quite different from the standard ereg() functions in places, and they offer some functionality that can't be replicated with the ereg() functions. After you have a good feel for regular expressions, you should probably head over to http://www.perldoc.com/perl5.6/pod/perlre.html to view some of the differences for yourself. The major PCRE functions are preg_match(), preg_match_all(), and preg_replace().

Finally, another slight variant of the regular expressions used in MySQL exists. It is described in the Appendix G of the MySQL manual (http://www.mysql.com/doc/en/Regexp.html).

## Literal Patterns

The simplest possible pattern match is to a series of known characters. For instance, to match jay within a string, you can do the following:

```
$str = "this is a string with my name: jay";
if (ereg("jay", $str))
{
    echo "pattern found";
}
else
{
    echo "string not found";
}
```

This tests true and prints pattern found. However, with a simple string like this, you don't need a regular expression. One of PHP's string functions works and is a good deal faster. For example, in the preceding example, strstr($str, "jay") works equally well and is faster.

### Characters

In regular expressions you can make use of the following characters.

- \n – Newline
- \t – Tab
- \r – Return
- \f – Form feed
- ^ (Shift+6) – Start of string (also known as caret)
- $ – End of string
- . (dot) – Matches any non-newline character

So if you need to match the word jay at the beginning of a string, you can do this:

```
ereg("^jay", $str)
```

And if you want to make sure nothing exists before or after jay in the string, you can do the following:

```
ereg("^jay$", $str)
```

In the preceding listing, notice the meaning of the dot (.). It stands for any non-newline character. If you want to print whatever four characters follow jay in a string, you can do the following:

```
ereg("jay(...)", $str, $arr);
echo $arr[1];
```

Note that the parentheses here represent a substring. When ereg() is processed and a match is found, the array in the third argument contains the entire matched string (including substrings) in $arr[0], and each additional substring indicated by parentheses in the regular expression is assigned to an additional array element. In the preceding example, therefore, the four characters following jay are in $arr[1].

### Character Classes

Often you need to see if a string contains a group of characters. For instance, you might need to make sure that a single character or given set of characters is alphanumeric or consists of a digit or digits. For this you can make use of character classes, either the built-in ones or the ones you make yourself. The built-in character classes are surrounded by two sets of brackets and colons, as seen in the following section. Character classes of your own making are surrounded by a single set of brackets.

### Built-in character classes

- [[:alpha:]] – Any letter, upper or lower case
- [[:digit:]] – Digits (0–9)
- [[:space:]] – Matches any whitespace character, including spaces, tabs, newlines, returns, and form feeds
- [[:upper:]] – Matches only uppercase letters
- [[:lower:]] – Matches only lowercase letters
- [[:punct:]] – Matches any punctuation mark
- [[:xdigit:]] – Matches possible hexadecimal characters (0–9, A–F)

For example, suppose you want to make sure a letter contains punctuation after the salutation “Dear Sir or Madam”:

```
ereg("Madam[[:punct:]]", $str);
```

Note that if you use the caret symbol (^) within a character class it has the effect of saying “not.” So, ereg("Madam[^[:punct:]]", $str) matches only if “Madam” is *not* followed by a punctuation mark.

The caret symbol can get confusing because it has two distinct meanings. At the beginning of a regular expression it indicates the start of a string, and so the following regular expression matches only a string in which a digit is the first character:
`^[[:digit:]]`
But if the caret is not in the first position in the regular expression, it means “not.” The following regular expression matches a string that does not contain any digits:
`[^[:digit:]]`
And to put it all together, the following matches a string that starts with a digit but has a second character that is not a digit:
`^[[:digit:]][^[:digit:]]`

### Self-made character classes

You can use brackets to construct your own character classes, either by using ranges of characters or by mixing characters of your choosing. Here are some typical ranges:

- a–z — Any lowercase letter
- A–Z — Any uppercase letter
- 0–9 — Any digit

Note that though these are the ranges you see most frequently, you can specify a range of a–m or 0–4 if you wish.

Be aware that the ASCII sequence of characters does not always follow human logic. Therefore, the expression [A–Z] does indeed define a range of ASCII characters that includes all the upper- and lowercase letters, but also a lot of other, non-alphabetic characters. Better to define the upper- and lowercase ranges separately, or use the predefined character classes.

These ranges must be put within brackets to become character classes. So [a–zA–Z] is identical to [[:alpha:]].

Self-made classes don't have to contain a range; they can contain any characters you want. For example:

```
[dog0-9]
```

This class matches the letters d, o, or g, or any digit.

```
$str="drat";
if(ereg("^[dog0-9]", $str))
{
    echo "true";
}
else
{
    echo "false";
}
```

This code prints true, because the first character in $str is in the class we have defined. If we replaced the d in drat with a b, this code prints false.

If you need to include a hyphen within a class, the hyphen must be the final character before the closing bracket of the class. For example, [a-zA-Z-].

### Multiple Occurrences

The real fun in regular expressions comes when you deal with multiple occurrences, which is when the syntax starts getting a little thick. We'll start by looking at three commonly used special characters.

- * (asterisk) – Zero or more of the previous character
- + – One or more of the previous character
- ? – Zero or one of the previous character

Note that if you want to match any of these characters literally you need to escape them with a backslash. So, for example, if you want to match the querystring of a URL http://www.mysqlphppaps.com/index.php?foo=mystring, you can do the following:

```
\?.*$
```

The first two characters (\?) match the question mark character (?). Note that the query matches the literal question mark because the question mark is escaped with a backslash. If the question mark were not escaped, its meaning would be as given in the previous listing.

Then, the dot matches any non-newline character. The asterisk matches zero or more of the previous character. So the combination (.*) matches any number of characters until a new line. The .* combination is a common one. The dollar sign is the end-of-string character. So .*$ matches every non-newline character to the end of the string.

You probably want to use a regular expression like the previous one if you need to make use of the querystring in some other context.

The following is code that retrieves a string from a URL and then picks out the relevant portion with a regular expression. It then pops that matched portion into an array and echoes it to output:

```
$str="http://domain.com/index.php?foo=mystring&bar=otherstring";
//see the use of the parenthesized substring
//this will assign the matched portion to $array[1]
if (eregi("\\?(.*)", $str, $array) )
{
    echo "The querystring is ", $array[1];
}
```

Now that you have the querystring in the variable $array[1], you can do further processing on it.

Before you incorporate this code into your script, note that you don't have to. You can use the PHP variables $_SERVER['QUERY_STRING'] or the $_GET array.

Because the plus sign means one or more of the previous character, the following code matches a single digit or multiple digits:

```
[0-9]+
```

Consider the following statement:

```
if (ereg("jay[0-9]+", $str) )
```

jay1 tests true, but jayg tests false. jay2883092002909303 tests true because it's still jay followed by one or more numbers. Even jay8393029jay tests true.

If you need to get more specific about the number of characters you need to match, you can make use of curly braces.

- {3} — If a single digit is surrounded by brackets, it indicates that you want to match exactly that number of the previous character. j{3} matches only jjj.
