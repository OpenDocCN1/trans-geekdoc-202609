The output produced is

```
The value of my_age is 21
```

Because this string is enclosed in double quotes, a dollar sign indicates that a variable's value should become part of the string. The construct ${$varname} indicates that the value of the variable named in $varname should become part of the string and is known as a variable variable .

The braces around $varname are used to indicate that it should be referenced first; they are required in double-quoted strings but are otherwise optional. The following example produces the same output as the preceding example, using the concatenation operator:

```
echo 'The value of ' . $varname . ' is ' . $varname;
```