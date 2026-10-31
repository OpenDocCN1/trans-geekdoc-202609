
## SUBSTR_REPLACE()

This function operates on the string in the first argument. The portion of the string to be manipulated will be identified by the numbers in the third and fourth arguments.

```
string substr_replace (string string, string replacement, int start
[, int length])
```

The third argument should be the offset of the character you wish to start with. The fourth, which is optional, can have an integer representing the number of characters after the third argument. If the fourth argument is a negative number, the portion will be determined from the end of the string.

For example:

```
echo substr_replace("this are my string", "this is", 0,8);
```

will print “This is my string”. And:

```
echo substr_replace("this is my string", "new string!", 11,-1);
```

will print “This is my new string!”.

## STRCMP()

This function compares two strings.

```
int strcmp (string str1, string str2)
```

If the first string is greater than the second the function will return a number greater than 0. It will return a number less than 0 if string two is greater than string one.

## STRLEN()

This function returns an integer that gives the number of characters in a string.

```
int strlen (string str)
```

For example:

```
echo strlen("My String");
```

will print “9”.

## STRPOS()

This function returns the position of the string in the second argument within the first argument. It will return FALSE if the string isn’t found.

```
int strpos (string to search, string to find [, int offset])
```

For example:

```
$str = "Where is the first space";
echo strpos($str, " ");
```

This will return “5”. If you wanted to get the first space after the fifth character you could make use of the optional third argument.

```
$str = "Where is the first space";
echo strpos($str, " ", 6);
```

This would return “8”.

An interesting note: Suppose you want to test if a string contains a specific character, say a space. You might think the following would work since strpos() returns FALSE if the string in the second argument is not found.

```
if( strpos($str, " ") )
{
    echo "thank you for including a space";
} else
{
    echo "include a space, please";
}
```

But, if you remember back to Chapter 5, the value of zero will also test as FALSE. So in the preceding code, if $str starts with a space, the condition will evaluate as FALSE. Therefore, if you want to use a test like this, you will need to alter the condition. In PHP 4 you can run a test against the constant FALSE. For example,

```
$str = " Whereisthefirstspace";
if( strpos($str, " ")==FALSE )
{
    echo "you have not included a space.";
} else
{
    echo "thank you for the space.";
}
```

## STRRPOS()
This is similar to the strpos() function except that it finds the final position of the character in the second argument.

```
int strrpos (string to search, char to find)
```

For example:

```
$str = "Where is the final space";
echo strrpos($str, " ");
```

will return “18”.

## SUBSTR()
This function returns a portion of a string based on numeric offsets.

```
string substr (string string, int start [, int length])
```

For example:

```
echo substr("this is my string", 5);
```

will return everything after the fifth character. In this case “is my string”. The optional third argument can represent the number of characters to be returned, following the third argument. For example

```
echo substr("this is my string", 5,2);
```

will return “is”. A negative number in the fourth argument specifies a character from the end of the string. For example,

```
echo substr("this is my string", 5,-7);
```

will print “is my”.

![](img/de0823012275cf4ceebdb822a56e6b71_162_0.png)

The substr function works really well with functions like strpos() and strrpos().

## STRREV()
This function reverses the order of a string.

```
string strrev (string string)
```

Use of strrev() may not come up too often in your programming life. In this book, it comes into use in the credit-card validation algorithm.

## STRTOLOWER()
This function makes an entire string lower case.

```
string strtolower (string str)
```

It’s particularly useful when you’re dealing with something like file names. Since Unix file names are case-sensitive, you may want to be sure that all files that you write have all lowercase letters. We also make use of this function when dealing with passwords.

## STRTR()
This function takes the string in the first argument and translates each character in the second argument to the corresponding character in the third argument.

```
string strtr (string str, string from, string to)
or
string strtr (string str, associative array)
```

So in the following, each a will be turned into an i and each o will be turned into a u.

```
strtr ($str, "ao", "iu")
```

Note that it does all of the replacements at once. For example, given this code

```
$str = "i";
echo strtr($str, "iu", "uv");
```

you might think that this function would first turn “i” into “u”, then “u” into “v”. This is not the case. It will do the replacements in a batch, so the output of this operation is “u”.

This function can also work with only two arguments. In such cases, the second argument should be an associative array. Then each key will be replaced by its corresponding value in the string.

```
$str = "this is my strings";
$replace_array = array("this"=>"these", "is"=>"are");
echo strtr($str, $replace_array);
```

This code prints “these are my strings”.

Once again, the replacements are done in a batch. If you had a third element in the preceding array “these”=>“those”, you wouldn’t have to worry about the word “this” being changed to “these” and then being changed to “those”.

## UCFIRST()
This function makes the first character in the string upper case.

```
string ucfirst(string str);
```

Note that it leaves everything after the first character untouched. So if you wanted to make sure that the first and only the first character of a string was capitalized, you would have to do something like this.

```
$str = "this is My string";
echo ucfirst(strtolower($str));
```

This would print out “This is my string”.

## UCWORDS()
This function makes the first character in every word in the string upper case.

```
string ucwords(string str);
```

Like ucfirst(), ucwords() does not touch characters that do not start a word.

## TRIM()
This function removes any white space from the beginning and end of a string including return characters, line feeds, spaces, and tabs.

```
string trim (string str)
```

![](img/de0823012275cf4ceebdb822a56e6b71_164_0.png)

PHP also has the ltrim() function to strip white space from only the start of a string or chop() to remove white space from only the end of a string.

## HTMLSPECIALCHARS()
This function transforms <, >, &, and " into their proper HTML entities: &lt;, &gt;, &amp;, and &quot;.

```
string htmlspecialchars (string string)
```

This function is useful for printing HTML source code to the browser.

![](img/de0823012275cf4ceebdb822a56e6b71_164_1.png)

In addition to htmlspecialchars(), you can make use of htmlentities(). htmlentities() transforms every character that has an HTML entity. For example the copyright symbol is turned into &copy;.

## GET_HTML_TRANSLATION_TABLE()
This function gets a full list of characters that have HTML entities, or just those used by htmlspecialchars(). You can indicate which you need access to by including HTML_ENTITIES or HTML_SPECIALCHARS within the function. For example get_html_translation_table(HTML_ENTITIES), gets a full list of characters and their entities.

Each character and its entity are available as key=>value pairs in an associative array. The resulting array can be of use with the strtr() function.

## NUMBER_FORMAT()
This function formats a number to your specifications.

```
string number_format (float number, int decimals, [[string dec_point], [string thousands_sep]])
```

The first argument will be the number you wish to format. The second argument will state the number of digits you would like after the decimal point. You can use this function with just these two arguments. For example,

```
echo number_format( (10/3), 2 );
```

will print “3.33”, and

```
echo number_format(1000,2);
```

will print “1,000”. Note that if there are two arguments, number_format() includes a comma as a thousands separator.

In the third and fourth arguments you can include a decimal point separator and a thousands separator, respectively. For example,

```
echo number_format( 10000.67, 2, "&", "R");
```

will print, 10R000&67.

![](img/de0823012275cf4ceebdb822a56e6b71_165_0.png)

> If number_format() doesn't cut it for you, you can make use of PHP's sprintf(), printf(), and scanf() functions. If you have a background in Perl or C you probably know how these functions work. They're powerful, complex, and take a good deal of time to get used to. If you want to familiarize yourself with these functions, take a look at the PHP manual (http://www.php.net/manual/function.sprintf.php) and this tutorial: http://wdvl.com/Authoring/Scripting/Tutorial/perl_printf.html.

## HELPFUL STRING FUNCTIONS NOT USED IN THIS BOOK

Just because we didn't use them doesn't mean you won't. And again, it's entirely possible that something we didn't cover will suit your needs perfectly. Please look over the PHP manual for a complete list.
