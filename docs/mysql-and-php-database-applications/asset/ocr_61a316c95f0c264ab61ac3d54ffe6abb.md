# 514 Part V: Appendixes

We seen anchor tags where a space existed prior to and following the equal
sign. So we need to account for occasions when the space exists and when it doesn't.

```
if (ereg('<a.href[[[:space:]]]=[[:space:]]]?(.*)',
$anchor, $array))
{
    echo $array[1];
}
```

Since the question mark character means "zero or one of the previous character",
the [[:space:]] means there can be one whitespace character or not. If
y wanted to allow for more than one whitespace character, you could
[[:space:]]+.

Finally, we need to deal with the actual contents of the href attribute. So, we've
accounted for cases where the link is delimited by double quotes. At
least, we account for delimiters of either double quotes or single
quotes. To do that, we will need to put double quotes and single quotes within a char-
class. Because we've surrounded the entire regular expression with single
quotes, we will need to escape single quotes within the regular expression with back-\lashes. The class will be `\\`.

```
if (ereg('<a.href[[[:space:]]]=[[:space:]]]?[\\"]?(.*)[\\"]',
$anchor, $array))
{
    echo $array[1];
}
```

To even more complex, the regular expression should account for cases when
no quotation mark is used to delimit the value of the href. For example, browsers
are just fine with a tag like this: <a href=mylink.php>. In a case like it might
be a good idea to use the greater than sign to mark the end of the string. All you
would need to do is add the greater sign to the last character class

```
if (ereg('<a.href[[[:space:]]]=[[:space:]]]?[\\"]?(.*)[\\"]>',',
$anchor, $array))
{
    echo $array[1];
}
```

However, this presents some problems that you may not have anticipated.
Imagine that this previous code is attempting to match this string: <a href = ../nmy_link.php>this is my link text</a>. When you add the greater sign to
the character class, the regular expression will not match the first greater
sign—it will match the final greater sign in the string. This is known as