First, Boolean values such as "false" are usually returned as a null string when you output them, so if register_globals is set to "off" you might see this output:

```
The register_globals value is
```

Second, numeric values are frequently stored in shorthand. For example, if the upload_max_filesize is set to 8,192 bytes, the value returned will be 8KB. Similarly, if the maximum size of an uploaded file is two megabytes, upload_max_filesize is not 2,097,152 bytes but rather 2MB.

This can be a problem if you need to do arithmetic operations on these numbers. The official PHP documentation includes this function that converts Ks and Ms to real numbers:

```
function return_bytes($val) {
    $val = trim($val);
    $last = $val{strlen($val)-1};
    switch(strtoupper($last)) {
        case 'K':
            return (int) $val * 1024;
            break;
        case 'M':
            return (int) $val * 1048576;
            break;
        default:
            return $val;
    }
}
```

# #10: Error Reporting

When you're writing code, it's very easy to forget about a variable name or to write deprecated code. At times, PHP is so user friendly (by programming standards) that it will actually work around many subtle coding mistakes.

For example, PHP allows you to write a program without declaring all of your variables at the start, which is convenient right up until you misspell $string as $stirng, and your program chokes on a null value. You can also pass variables to functions in totally incorrect ways that work *most* of the time because PHP makes some assumptions about what you meant. That's great until PHP guesses incorrectly, and then you'll be scratching your head over a mysterious bug.

To stop PHP from guessy fixing problems, you can enable error reporting, which will cause PHP to flood your screen with every problem—no matter how insignificant—that it finds. You can use these error messages to tighten potential security loopholes and catch bad variables before you go live with