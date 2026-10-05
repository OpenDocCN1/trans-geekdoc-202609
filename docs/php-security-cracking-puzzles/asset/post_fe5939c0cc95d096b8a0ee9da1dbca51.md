
by the entire pattern, the $matches[1] element will hold the substring that matches the subpattern within the first set of parentheses, the $matches[2] element will hold the substring that matches the subpattern within the second set of parentheses, and so on. The format of the returned $matches array is controlled by the optional flag argument. When this parameter is set to PREG_OFFSET_CAPTURE, for each found match the function returns an array containing the matched string in the 0th element and its offset into the 1st string. The search is conducted from the beginning of the string, from left to right. An alternative starting position for the search can be specified using the optional offset parameter. The preg_match() function returns 0 when no matches are found and 1 when a match is found.

The technique used in the previous section will not extract the page title because it may contain angle brackets. Therefore, the <title> and </title> tags must be used, with the “greediness” controlled by the U modifier. By default, regular expressions are “greedy”; that is, they return the longest match from all found matches. The U modifier inverts the “greediness,” with the shortest match of all choices returned.

## Listing II.2.4. Extracting the HTML page title

```php
<?php
// Extracting the contents of the index.html file
$content = file_get_contents("index.html");

// The regular expression
$pattern = "<title>(.*)</title>|si";

// Extracting the title of the HTML page
if (preg_match($pattern, $content, $out)) {
    echo $out[1];
}
?>
```

The greediness of regular expressions can also be used using the * sequence; that is, the regular expression from Listing II.2.4 can be rewritten as <title>(.*)</title>|si. The * sequence allows the greediness to be controlled locally, such as when it is necessary for the overall regular expression to be greedy but a part of it to be not greedy.

## Chapter II.2: Regular Expressions 125

## II.2.4. Converting MySQL Date Format into Calendar Format

The date format can be converted to the calendar format using the script shown in Listing II.2.5.

Listing II.2.5. Converting from the YYYY-MM-DD format to the DD.MM.YYYY format

The search results produced by the preg_match() function can be saved in an array specified by the optional third parameter. The 0 array element will hold the match to the entire regular expression; the first array element will hold the match to the regular expression in the first set of parentheses (the year); the second array element will hold the match to the regular expression in the second set of parentheses (the month); and the third array element will hold the match to the regular expression in the third set of parentheses (the day).

## II.2.5. Verifying the Email Address Format

Assume the format of the address should be something@server.com. Moreover, the address consists of two parts delimited by the @ character; these are the user name and the domain name. The user name can contain uppercase and lowercase letters, digits, underscores, periods, and hyphens. To check the separator between the user name and the domain name, the @ character must be added to the regular expression. Like the user name, the domain name can use uppercase and lowercase letters, digits, underscores, periods, and hyphens. Consequently, the following regular expression for verifying that the user name and the domain name of an email address are in the appropriate format can be constructed:

```
[0-9a-z_]+@[0-9a-z_^\.]+
```

## Part II: Solutions

To check a first-level domain name (e.g., .com, .ed, or .gov), the following regular expression must be added:

\.[a-z]{2,6}

You should be aware that several first-level domain names were created recently, such as .info and .travel. A three-letter regular expression will not work with these new first-level domain names; a regular expression made of two to six letters must be used to check a first-level domain name.

The period is used in regular expressions to denote any character; therefore, periods in a regular expression denoting periods that match those in the target string must be escaped with a backslash.

The combined regular expression for confirming the email address format rules looks as follows:

```
|[0-9a-z_]+\@[0-9a-z_]+\.[a-z]{2,6}|
```

The i modifier tells the interpreter to ignore the case when searching the target string.

If the only information that the target string contains is an email address, the regular expression must be anchored to the beginning and the end of the string with '^' and '$' characters, respectively. The resulting expression will look as follows:

```
^[0-9a-z_]+\@[0-9a-z_]+\.[a-z]{2,6}$
```

The complete code for verifying the email format may look as shown in Listing II.2.6.

## II.2.6. Checking the email format

```php
<form method=post>
<input size=60 type=text name=value=<?php $_POST['name']; ?>>
<input type=submit value='Check'>
</form><br>
<?php
// The HTML form handler
if(isset($_POST['name']))
{
if(preg_match("^[0-9a-z_]+\@[0-9a-z_]+\.[a-z]{2,6}$",
$_POST['name']))
{
  echo "The email address format is correct.";
} else {
  echo "The email address format is wrong.";
}
?>
```

## Chapter II.2: Regular Expressions 127

## II.2.6. Verifying URLs

It is not easy to construct a regular expression that corresponds to all possible URLs. Usually, middle ground is sought between the complexity of the regular expression and the accuracy, with which it represents URL formats.

When constructing the required regular expression, assume that the URL format is the following:

```
http://host/path/
```

A name with different extensions (e.g., .html, .php, .pl, or .cgi) is an optional part of the URL. The file name may be followed by optional parameters.

A regular expression satisfying these URL format conditions may be the:

```
#^((http://)?[-a-zZ-9_\.]+)|([-a-zZ-9_]+))+\.(html|php|pl|cgi))?\n([-a-zZ-9_:&&?+=!/\-\*%$]+)+\#i
```

The script using this regular expression is shown in Listing II.2.7.

## Listing II.2.7. Checking the URL format

```php
<form method=post>
<input size=60 type=text name=name value=<?php $_POST['name']; ?>>
<input type=submit value='Check'>
</form><br>
<?php
// The HTML form handler
if(isset($_POST['name'])) {"
```

## 128 Part II: Solutions

```php
$Pattern = "^##(http://)?[-a-z0-9_\.]+\(([-a-z0-9_]+\]+\.(html|php|pl|cgi))?\([-a-z0-9_@&\;=\=\-!/\*\$]+)?$#i";
if (preg_match($Pattern, $_POST['name']))
{
    echo "The URL format is correct.";
}
else
{
    echo "The URL format is incorrect.";
}
?>
```

## 11.2.7. Converting Text URLs to Hyperlinks

Text URLs can be converted to hyperlinks using the expression considered in Section II.2.6. The complete code is shown in Listing II.2.8.

## 11.2.8. Converting Text URLs to Hyperlinks

```php
<?php
// Extracting the contents of the index.html
$content = file_get_contents("index.html");

// The regular expression
$pattern = "<title>(.*)</title>|si";

// Extracting the title of the HTML page
if (preg_match($pattern, $content, $out)) {
    echo $out[1];
}
?>
```

## Chapter II.2: Regular Expressions 129

## II.2.8. Verifying Numeric Input

Verifying that inputs meet certain requirements is an important task. Web developers often assume that simply because a number should be entered into a field, it will be. However, instead of a number, text can be input into such fields. This may result in the failed execution at the best or in a break-in at the worst (see Chapters I.5 and II.5).

An integer can be easily checked: There is a special class, \d, for this purpose. Moreover, the regular expression must be tied to the beginning and end of the target string with the ^ and $ characters. Failing to do this will make it possible to enter anything after one digit is entered: The regular expression will find the digit and ignore everything else. The regular expression for checking that a string is an integer looks as follows:

```
^\d]*$
```

A regular expression for checking a floating-point number has three parts. The part for checking the whole part is the same as the expression for checking integers: [\d]*. The point is denoted by the period character, which must be escaped with a backslash. The part for checking the decimal portion can be described by \.\d*. Joining these fragments produces the regular expression for checking floating-point numbers: ^[\d]*\.\d]*$. The final touch takes into account different formats of the separator between the whole and decimal parts, for both which the period (e.g., 23.56) and the comma (e.g., 23,56) can be used. The corresponding regular expression is the following: ^[\d]*[.,][d]*$. This expression, however, will not match integers. To take care of this, the mark character must be inserted after the [.,\] class. The final expression looks as follows:

```
^[\d]*[.,][]?\d]*$
```

Thus, the problem can be solved as shown in Listing II.2.9.

## Listing II.2.9. Verifying numeric input

```php
<form method = post>
Quantity <input size=60 type=text-number
value<=?= $_POST['number']; ?> ?><br>
Price <input size=60 type=text-price
value<=?= $_POST['price']; ?> ?><br>
<input type = submit value = 'Verify'>
```
