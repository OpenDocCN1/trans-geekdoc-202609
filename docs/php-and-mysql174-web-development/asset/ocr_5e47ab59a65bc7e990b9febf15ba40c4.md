```
?>
<!DOCTYPE html>
<html>
<head>
  <title>Bob's Auto Parts - Feedback Submitted</title>
</head>
<body>
<h1>Feedback submitted</h1>
<p>Your feedback (shown below) has been sent.</p>
<p><?php echo nl2br(htmlspecialchars($feedback)); ?>  </p>
</body>
</html>
```

There are many other string processing functions you may find useful. We'll examine these in the remainder of this section.

# Formatting a String for Printing

So far, you have used the echo language construct to print strings to the browser. PHP also supports a print() construct, which does the same thing as echo, but returns a value, which is always equal to 1.

Both of these techniques print a string "as is." You can apply some more sophisticated formatting using the functions printf() and sprintf(). They work the same way, except that printf() outputs a formatted string and sprintf() returns a formatted string.

If you have previously programmed in C, you will find that these functions are conceptually similar to the C versions. Be careful, though, the syntax is not exactly the same. If you haven't, they getting used to them will be useful and powerful.

The prototypes for these functions are

```
string printf(string format [, mixed args...])
int sprintf(string format [, mixed args...])
```

The first parameter passed to both of these functions is a format string that describes the basic shape of the output with codes of variables. The other parameters are variables that will be substituted in the format string.

For example, echo, you can use the variables you want to print inline, like this:

```
echo "Total amount of order is $total.";
```

To get the same effect with printf(), you would use

```
printf("Total amount of order is %s.", $total);
```

The %s in the format string is a conversion specification. This means "replace with a string." In this case, it is replaced with $total interpreted as a string. If the value stored in $total is 12.4, both of these approaches would print it as 12.4.