
Note that the parentheses represent a substring. When preg() is processed and there is a match, the array in the third argument will contain the entire matched string (including substrings) in $arr[0], and each additional substring indicated by parentheses will be assigned to an additional array. So in the preceding example, the four characters following “jay” will be in $arr[1].

The array created in the optional third argument of preg() will always contain 10 elements. The first element is the entire matched string. It can only place nine matched substrings in the other elements. If there are fewer than 9 substrings indicated, those elements will be filled with empty strings.

## Character Classes

Often you will need to see if a string contains a group of characters. For instance, you may need to make sure that a single character or set of characters is alphanumeric or consists of a digit or digits. For this, you will make use of built-in character classes or make your own. The built-in character classes are surrounded by two sets of brackets. Character classes of your own making will be surrounded by a single set of brackets.

## Built-in character classes

- [:alpha:] — Any letter, upper or lower case
- [:digit:] — Digits (0-9)
- [:space:] — Matches any whitespace character, including spaces, tabs, returns, and form feeds
- [:upper:] — Matches only uppercase letters
- [:lower:] — Matches only lowercase letters
- [:punct:] — Matches any punctuation mark
- [:xdigit:] — Matches hexadecimal characters

For example, say you want to make sure a letter contained punctuation in "Dear Sir or Madam" salutation.

```
preg("Madam[:punct:]", $str);
```

## Part V: Appendixes

Note if you use the caret symbol (^) within a character class it has the effect of saying not. So, ereg("Madam[:punct]", $str) would match only if Madam is not followed by a punctuation mark.

![](img/245156cc770929860a3ede93c01f9981_536_0.png)

The caret symbol can get confusing because it has two distinct meanings. At the beginning of a regular expression it indicates the start of a string. So the following regular expression will match only a string in which a digit is the first character:

```
^[:digit:]
```

But if the caret is not in the first position in the regular expression, it means "not." The following regular expression would match a string that does not contain digits.

```
^[:digit:]]
```

And to put it all together, the following matches a string that starts with a digit but has a second character that is not a digit.

```
^[:digit:]][[:digit:]]
```

## Self-made character classes

Using brackets, you can construct your own character classes either by using ranges of characters or by mixing characters of your choosing. Here are some typical ranges:

- a-z — Any lowercase letter
- A-Z — Any uppercase letter
- 0-9 — Any digit

Note that these are the ones you will see most frequently, but a range could contain a-m or 0-4 if you wished. Ranges must be put within brackets to become character classes. So

```
[a-zA-Z]
```

is identical to [[:alpha]]. Self-made classes don't have to contain a range; they can contain any characters you wish.

```
[dog0-9]
```

This class will match the letters d, o, or g, or any digit.

```
$str="drat";if(ereg("^[dog0-9]", $str))
{
    echo "true";
}else
    echo "false";
}
```

This code will print "true", because the first character in $str is in the class I've defined. If we replaced the d in drat with a b, this code would print "false".

![](img/245156cc770929860a3ede93c01f9981_537_0.png)

## Multiple Occurrences

The real fun in regular expressions comes when you deal with multiple occurrences. This is when the syntax starts getting a little thick. I'll start looking at three commonly used special characters.

- * (asterisk)—Zero or more of the previous character
- + One or more of the previous character
- ?Zero or one of the previous character

Note that if you want to match any of these characters literally, you will need to escape it with a backslash. So, for example, if you want to match the querystring of a URL, say, http://www.mysqlphpapps.com/index.php?foo=mysql, you could do the following:

```
\.\**
```

The first two characters (?) match the question mark character (?). It matches the question mark because it is escaped with a backslash. If it was not escaped, the question mark would have the meaning in the previous list. Then the dot matches a non-newline character. The asterisk matches zero or more of the previous character. So the combination .* will match any number of characters until a newline. You will see the .* combination frequently. The dollar

## Part V: Appendixes

sign is the end of string character. So .* matches every non-newline character to the end of the string. You would probably want to use a regular expression like the previous one if you need to make use of the querystring in some other context.

```
$str="http://domain.com/index.php?foo=mysql&bar=other";
if (preg("/(.*)/", $str, $array))
{
    echo "The querystring is ", $array[1];
}
```

Now that you have the querystring in variable $array[1], do further process on it. Before you incorporate this code into your script, note that you don't have to. You could use the QUERY_STRING or PHP_GET array. Moving on, since the plus sign means one or more of the previous:

```
if (preg("/[0-9]+/", $str))
```

one will test true, if one will fail. If you need to get more specific about the number of characters, you can use curly braces.

- {n} — If there is a single digit within brackets, it indicates that you wish to match exactly that number of the character.
- {n,m} — If there are two digits, it indicates an upper and lower limit to the previous character.
- {n,} — If there is a comma and there is no second integer, it will match as many times or more of the character.

## Specifying “Or”

If you want to specify one combination of characters or another, you will need to make use of the pipe (|). Most often, you will use the pipe with parentheses, which group portions of strings. If you wanted to match either or within a string, you could use the following:

```
(jay|brad)
```

Or you might want to check that URLs had a suffix:

```
(com|edu)
```

## Example Expressions

This has been a pretty review of regular expressions. If you’re interested, there have been entire books written on the subject. To get more comfortable with regular expressions, lets look at a practical example. Say you write a anchor that matches the contents of href attribute of an anchor tag. An example anchor looks something like this:

```
<a href="../my_link.php">this is link text</a>
```

At first, you might be tempted to look at this link and think all you need to do is matching everything after href=" to the closing mark. Something like this:

```
if (ereg('<a href="(.**)")', $anchor, $array)) {
  echo $array[1];
}
```

However, you really can’t be sure that the href will immediately follow the <a, there could be another attribute or perhaps javascript event prior to the href. So you’d need to account for that in your regular expression.

```
if (ereg('<a.*href="(.**)")', $anchor, $array)) {
  echo $array[1];
}
```

## Part V: Appendixes

We seen anchor tags where a space existed prior to and following the equal sign. So we need to account for occasions when the space exists and when it doesn't.

```
if (ereg('<a href[[:space:]]=[[:space:]]?(.*)', $anchor, $array))
{
    echo $array[1];
}
```

Since the question mark character means "zero or one of the previous character", the [[:space:]] means there can be one whitespace character or not. If you wanted to allow for more than one whitespace character, you could [[:space:]]+.

Finally, we need to deal with the actual contents of the href attribute. So, we've accounted for cases where the link is delimited by double quotes. At least, we account for delimiters of either double or single quotes. To do that, we will need to put double quotes and single quotes within a class. Because we've surrounded the entire regular expression with single quotes, we will need to escape single quotes within the regular expression with backslashes. The class will be `\\`.

```
if (ereg('<a href[[:space:]]=[[:space:]]?[\\"]?(.*)[\\"]', $anchor, $array))
{
    echo $array[1];
}
```

To even more complex, the regular expression should account for cases when no quotation mark is used to delimit the value of the href. For example, browsers are just fine with a tag like this: <a href=mylink.php>. In a case like it might be a good idea to use the greater than sign to mark the end of the string. All you would need to do is add the greater sign to the last character class

```
if (ereg('<a href[[:space:]]=[[:space:]]?[\\"]?(.*)[\\"]>', $anchor, $array))
{
    echo $array[1];
}
```

However, this presents some problems that you may not have anticipated. Imagine that this previous code is attempting to match this string: <a href = ../my_link.php>this is my link text</a>. When you add the greater sign to the character class, the regular expression will not match the first greater sign—it will match the final greater sign in the string. This is known as
