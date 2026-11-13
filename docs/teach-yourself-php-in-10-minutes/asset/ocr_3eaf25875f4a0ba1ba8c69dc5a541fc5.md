prefixed with a dollar sign inside a double-quoted string is replaced with its values, whereas in a single-quoted string, the dollar sign and variable name appear verbatim.

If you want a dollar sign to form part of a double-quoted string, you can also escape this by using a backslash. For example, the following two statements are equivalent:

```
$offer = 'Save $10 on first purchase';
$offer = "Save \$10 on first purchase";
```

Without the backslash, the second example would attempt to find the value of a variable called $10 , which is, in fact, an illegal variable name.

The backslash character can also be used in a double-quoted string to indicate some special values inside strings. When followed by a three-digit number, it indicates the ASCII character with that octal value.

You can send the common nonprintable ASCII characters by using standard escape characters. A newline is \n , tab is \t , and so on. Refer to man ascii on your system or www.ascii.cl for a comprehensive list.

# Concatenation

You have already seen how strings can be joined using the period symbol as a concatenation operator. A compound version of this operator, .= , can be used to append a string to an existing variable.

The following example builds up a string in stages and then displays the result:

```
$phrase = "I want ";
$phrase .= "to teach ";
$phrase .= "the world ";
$phrase .= "to sing";
echo $phrase;
```

The phrase appears as expected. Note the use of spaces after teach and world to ensure that the final string is correctly spaced.

# Comparing Strings

You can compare string values simply by using the standard comparison operators. To check whether two strings are equal, you use the double equals (== ) sign:

```
if ($password == "letmein")
    echo "You have a guessable password";
```