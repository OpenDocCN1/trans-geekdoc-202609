
# Formatting Strings for Output

PHP includes a set of functions that you can use to reformat a string in different ways for different purposes.

# Filtering Strings for Output

Whenever we take user-submitted data and output it somewhere, we need to plan it with the destination in mind. This is because most places we send output to [expect] some characters to be special or control characters and strings, and we don't want the output destination to interpret user-submitted data as commands.

For example, when echoing user input to a browser, we don't want to execute any HTML or JavaScript that the user may have included. This is not only because it could break the formatting, but also because it is a security vulnerability to allow the execution of arbitrary user-submitted code or commands. We will discuss this in a lot more detail in Part III of this book, "Web Application Security." In that section, we will also cover the filter extension, which enables generic filtering per-destination.

## Filtering Strings for Output to Browser with htmlspecialchars()

We used this function in previous chapters, but let's recap here. The htmlspecialchars function converts characters that have a special meaning in HTML to their HTML entity equivalent. For example, the character < is converted to &lt;.

The prototype of this function is as follows:

```
string htmlspecialchars(string string, int flags = ENT_COMPAT | ENT_HTML401, string encoding = 'UTF-8', bool double_encode = true)
```

In general, this function converts characters to their HTML entity equivalents as shown in Table 4.1.

Table 4.1 HTML Entities Encoded by the htmlspecialchars() Function
| Character | Translation |
|---|---|
| & | &amp; |
| " | &quot; |
| ' | &apos; |
| < | &lt; |
| > | &gt; |

The default encoding of quotes is to only encode double quotes. Single quotes will remain untranslated. This behavior is controlled by the flags parameter.

The first parameter is the string to be translated, and the function returns the translated string.

Note: If the input string is not valid in the specified encoding, the function will return the empty string without raising an error. This is intended to help avoid code injection issues.

The first optional parameter, `flags`, specifies how the translation should be done. You may pass in a bitmask representing the values combined together. The default value, as you can see in the prototype above, is `ENT_COMPAT | ENT_HTML401`. The `ENT_COMPAT` constant indicates that double quotes should be kept as-is, while the `ENT_HTML401` constant indicates that code should be treated as HTML 4.01.

The second optional parameter, `encoding`, specifies the encoding used for conversion. From PHP 5.4 onwards, the default is UTF-8. Prior to that, it was ISO-8859-1, commonly known as Latin-1. The list of supported encodings may be found in the PHP documentation.

The third optional parameter, `double_encode`, specifies whether to encode HTML entities. The default is to convert them (again).

The full set of possible values that may be combined in the `flags` parameter can be found in Table 4.2.

Table 4.2 Flags for the htmlspecialchars() Function
| Flag | Meaning |
| --- | --- |
| ENT_COMPAT | Encode double quotes but not single quotes |
| ENT_NOQUOTES | Do not encode single or double quotes |
| ENT_QUOTES | Encodes both single and double quotes |
| ENT_HTML401 | Treat code as HTML 4.01 |
| ENT_XML1 | Treat code as XML |
| ENT_XHTML | Treat code as XHTML |
| ENT_HTML5 | Treat code as HTML5 |
| ENT_IGNORE | Discard invalid code units instead of returning the empty string. Not recommended for security reasons |
| ENT_SUBSTITUTE | Replace invalid code unit sequences with a Unicode Replacement Character |
| ENT_DISALLOWED | Replace invalid code points with a Unicode Replacement Character |

## Filtering Strings for Other Forms of Output

Depending on where you are outputting strings, the characters that may cause problems are different. We previously discussed the `htmlspecialchars()` function for output to the browser.

In the example in Listing 4.1, we are sending out to email. But do we need to take into account here? We don't care if the email contains HTML, so using the `htmlspecialchars()` function is not appropriate here.

The main issue in email headers is that they are separated by the character `\r\n` (carriage return-line feed). We need to make sure that user data we use in the email headers does not contain these characters, or we run the risk of a set of attacks, called header injection. (We discuss this in detail in Part III.)

With many string processing problems, there are many ways to achieve this. One way is by using the `str_replace()` function, as follows:

```php
$mailcontent = "Customer name: ".str_replace("\r\n","","",$name)."\n";
"Customer email: ".str_replace("\r\n","","",$email)."\n";
"Customer comments: ".str_replace("\r\n","","",$feedback)."\n";
```

If you have more complicated replacement or replacement rules, you can use the regular expression functions described later in this chapter. In a simple case like this where you want to entirely replace one string with another, you should always use the `str_replace()``.

# Formatting Strings 107

## Chapter 4 String Manipulation and Regular Expressions

We are sending out to email. But do we need to take into account here? We don't care if the email contains HTML, so using the `htmlspecialchars()` function is not appropriate here.

The main issue in email headers that are separated by the character `\r\n` (carriage return-line feed). We need to make sure that user data we use in the email headers does not contain these characters, or we run the risk of a set of attacks, called header injection. (We discuss this in detail in Part III.)

With many string processing problems, there are many ways to achieve this. One way is by using the `str_replace()` function, as follows:

```php
$mailcontent = "Customer name: ".str_replace("\r\n","","",$name)."\n";
"Customer email: ".str_replace("\r\n","","",$email)."\n";
"Customer comments: ".str_replace("\r\n","","",$feedback)."\n";
```

If you have more complicated replacement or replacement rules, you can use the regular expression functions described later in this chapter. In a simple case like this where you want to entirely replace one string with another, you should always use the `str_replace()`.

## Formatting Strings for Printing

So far, you have used the echo language construct to print strings to the browser. PHP also supports a print() construct, which does the same thing as echo, but returns a value, which is always 1.

Both of these techniques print a string "as is." You can apply some more sophisticated formatting using the printf() and sprintf(). They work the same way, except that printf() outputs a formatted string and sprintf() returns a formatted string.

If you have previously programmed in C, you will find that these functions are conceptually similar to the C versions. Be careful, though, the syntax is not exactly the same. If you haven't, getting used to them will be useful and powerful.

The prototypes for these functions are

```
string printf(string format [, mixed args...])
int sprintf(string format [, mixed args...])
```

The first parameter passed to both of these functions is a format string that describes the basic shape of the output with codes of variables. The other parameters are variables that will be substituted in the format string.

For example, echo, you can use the variables you want to print inline, like this:

```php
echo "Total amount of order is $total.";
```

To get the same effect with printf(), you would use

```php
printf("Total amount of order is %s.", $total);
```

The %s in the format string is a conversion specification. This means "replace with a string." In this case, it is replaced with $total interpreted as a string. If the value stored in $total is 12.4, both of these approaches would print it as 12.4.
