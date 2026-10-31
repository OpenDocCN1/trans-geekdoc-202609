We’ve seen anchor tags where a space existed prior to and following the equal sign. So we need to account for occasions when the space exists and when it doesn’t.

```
if (ereg('<a.*href[[:space:]]?=[[:space:]]?"(.*)"',
$anchor, $array))
{
    echo $array[1];
}
```

Since the question mark character means “zero or one of the previous character”, the pairing [[:space:]]? means there can be one whitespace character or none. If you wanted to allow for more than one whitespace character, you could use [[:space:]]+.

Finally, we need to deal with the actual contents of the href attribute. So far, we’ve only accounted for cases where the link destination is delimited by double quotes. But at the very least, we should account for delimiters of either double quotes or single quotes. To do that, we’ll need to put double quotes and single quotes within a character class. Because we’ve surrounded the entire regular expression with single quotes, we will need to escape single quotes within the regular expression with backslashes. The class will be ["\'] .

```
if (ereg('<a.*href[[:space:]]?=[[:space:]]?["\'](.)*["\']',
    $anchor, $array))
{
    echo $array[1];
}
```

To be even more complete, the regular expression should account for cases when no quotation mark at all is used to delimit value of the href. For example, browsers are just fine with a tag like this: <a href=mylink.php>. In a case like this, it might be a good idea to use the greater than sign to mark the end of the string. All you would need to do is add the greater than sign to the last character class

```
if (ereg('<a.*href[[:space:]]?=[[:space:]]?["\']?(.*)["\']?>',
    $anchor, $array))
{
    echo $array[1];
}
```

However, this presents some problems that you may not have anticipated. Imagine that this previous code is attempting to match this string: <a href = ../ my_link.php>this is my link text</a>. When you add the greater than sign to the character class, the regular expression will not match the first greater than sign—it will match to the final greater than sign in the string. This is known as