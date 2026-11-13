
## PHP's Regexp PERL Compatible Functions

PHP offers the following functions for searching strings using Perl-compatible regular expressions:

| Function | Description |
| :--- | :--- |
| preg_match() | The preg_match() function searches string for pattern, returning true if pattern exists, and false otherwise. |
| preg_match_all() | The preg_match_all() function matches all occurrences of pattern in string. |
| preg_replace() | The preg_replace() function operates just like ereg_replace(), except that regular expressions can be used in the pattern and replacement input parameters. |
| preg_split() | The preg_split() function operates exactly like split(), except that regular expressions are accepted as input parameters for pattern. |
| preg_grep() | The preg_grep() function searches all elements of input_array, returning all elements matching the regexp pattern. |
| preg_quote() | Quote regular expression characters |

### PHP—Function preg_match()

#### Syntax

```
int preg_match (string pattern, string string [, array pattern_array] [, int $flags [, int $offset]]);
```

#### Definition and Usage

The preg_match() function searches string for pattern, returning true if pattern exists, and false otherwise.

If the optional input parameter pattern_array is provided, then pattern_array will contain various sections of the subpatterns contained in the search pattern, if applicable.

If this flag is passed as PREG_OFFSET_CAPTURE, for every occurring match the appendant string offset will also be returned

Normally, the search starts from the beginning of the subject string. The optional parameter offset can be used to specify the alternate place from which to start the search.

#### Return Value

- Returns true if pattern exists, and false otherwise.

### PHP—Function preg_match_all()

#### Syntax

```
int preg_match_all (string pattern, string string, array pattern_array [, int order]);
```

#### Definition and Usage

The preg_match_all() function matches all occurrences of pattern in string.

It will place these matches in the array pattern_array in the order you specify using the optional input parameter order. There are two possible types of order –

- **PREG_PATTERN_ORDER** – PREG_PATTERN_ORDER specifies the order in the way that you might think most logical; $pattern_array[0] is an array of all complete pattern matches, $pattern_array[1] is an array of all strings matching the first parenthesized regexp, and so on.

- **PREG_SET_ORDER** – PREG_SET_ORDER specifies the order in the way that you might think most logical; $pattern_array[0] contains elements matched by the first parenthesized regexp, $pattern_array[1] contains elements matched by the second parenthesized regexp, and so on.

#### Return Value

- Returns the number of matches.

#### Example

Following is the piece of code, copy and paste this code into a file and verify the result.

```
<?php
$userinfo = "Name: <b>John Poul</b> <br> Title: <b>PHP Guru</b>";
preg_match_all ("/<b>(.*)<\/b>/U", $userinfo, $pat_array);

print $pat_array[0][0]." <br> ".$pat_array[0][1]."\n";
?>
```

This will produce the following result –

John Poul
PHP Guru

### PHP—Function preg_replace()

#### Syntax

```
mixed preg_replace (mixed pattern, mixed replacement, mixed string [, int limit [, int &$count]] );
```

#### Definition and Usage

The preg_replace() function operates just like POSIX function ereg_replace(), except that regular expressions can be used in the pattern and replacement input parameters.

The optional input parameter limit specifies how many matches should take place.

If the optional parameter $count is passed, then this variable will be filled with the number of replacements done.

#### Return Value

- After the replacement has occurred, the modified string will be returned.
- If no matches are found, the string will remain unchanged.

#### Example

Following is the piece of code, copy and paste this code into a file and verify the result.

```
<?php
$copy_date = "Copyright 1999";
$copy_date = preg_replace("([0-9]+)", "2000", $copy_date);

print $copy_date;
?>
```

This will produce the following result –

Copyright 2000

### PHP — Function preg_split()

#### Syntax

```
array preg_split (string pattern, string string [, int limit [, int flags]]);
```

#### Definition and Usage

The preg_split() function operates exactly like split(), except that regular expressions are accepted as input parameters for pattern.

If the optional input parameter limit is specified, then only limit number of substrings are returned.

flags can be any combination of the following types -

- **PREG_SPLIT_NO_EMPTY** – If this flag is set, only non-empty pieces will be returned.
- **PREG_SPLIT_DELIM_CAPTURE** – If this flag is set, parenthesized expressions in the pattern will be captured and returned as well.
- **PREG_SPLIT_OFFSET_CAPTURE** – If this flag is set, for every occurring match the appended string offset will also be returned.

#### Return Value

- Returns an array of strings after splitting up a string.

#### Example

Following is the piece of code, copy and paste this code into a file and verify the result.

```
<?php
$ip = "123.456.789.000"; // some IP address
$iparr = split("/\\./", $ip);
print "$iparr[0] <br />";
print "$iparr[1] <br />" ;
print "$iparr[2] <br />" ;
print "$iparr[3] <br />" ;
?>
```

This will produce the following result –

123.456.789.000

### PHP— Function preg_grep()

#### Syntax

```
array preg_grep ( string $pattern, array $input [, int $flags ] );
```

#### Definition and Usage

Returns the array consisting of the elements of the input array that match the given pattern.

If flag is set to PREG_GREP_INVERT, this function returns the elements of the input array that do not match the given pattern.

#### Return Value

- Returns an array indexed using the keys from the input array.

#### Example

Following is the piece of code, copy and paste this code into a file and verify the result.

```
<?php
$foods = array("pasta", "steak", "fish", "potatoes");

// find elements beginning with "p", followed by one or more letters.
$p_foods = preg_grep("/p(\w+)/", $foods);

print "Found food is " . $p_foods[0];
print "Found food is " . $p_foods[1];
?>
```

This will produce the following result –

Found food is pastaFound food is

### PHP — Function preg_quote()

#### Syntax

```
string preg_quote ( string $str [, string $delimiter] );
```

#### Definition and Usage

preg_quote() takes str and puts a backslash in front of every character that is part of the regular expression syntax.

#### Return Value

- Returns the quoted string.

#### Example

Following is the piece of code, copy and paste this code into a file and verify the result.

```
<?php
 $keywords = '$40 for a g3/400';
 $keywords = preg_quote($keywords, '/');
 echo $keywords;
 ?>
```

This will produce the following result –

```
\$40 for a g3\/400
```

Error handling is the process of catching errors raised by your program and then taking appropriate action. If you would handle errors properly, then it may lead to many unforeseen consequences. It is very simple in PHP to handle errors.

### Using die() function

While writing your PHP program you should check all possible error condition before going ahead and take appropriate action when required.

Try the following example without having /tmp/test.txt file and with this file.

```
<?php
if(!file_exists("/tmp/test.txt"))
{
die("File not found");
}
else
{
$file=fopen("/tmp/test.txt","r");
print "Opened file successfully";
}
// Test of the code here.
?>
```

You can thus write an efficient code. Using the above technique, you can stop your program whenever it errors out and display more meaningful and user-friendly message.

### Defining Custom Error Handling Function

You can write your own function to handling any error. PHP provides you a framework to define error-handling function.

This function must be able to handle a minimum of two parameters (error level and error message) but can accept up to five parameters (optionally: file, line-number, and the error context):

#### Syntax

```
error_function(error_level,error_message, error_file,error_line,error_context);
```
