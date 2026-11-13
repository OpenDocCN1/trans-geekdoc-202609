The first two characters (\?) match the question mark character (?). Note that the query matches the literal question mark because the question mark is escaped with a backslash. If the question mark were not escaped, its meaning would be as given in the previous listing.

Then, the dot matches any non-newline character. The asterisk matches zero or more of the previous character. So the combination (.*) matches any number of characters until a new line. The .* combination is a common one. The dollar sign is the end-of-string character. So .* $ matches every non-newline character to the end of the string.

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

+   (3) — If a single digit is surrounded by brackets, it indicates that you want to match exactly that number of the previous character. j{3} matches only jjj.