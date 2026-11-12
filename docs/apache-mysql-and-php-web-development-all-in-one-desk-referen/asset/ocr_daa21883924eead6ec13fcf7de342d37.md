Take a look at this file, which I'm calling myfile2.php:

```
<html>
<head>
<title>Better Example</title>
</head>
<body>
<?php
print "Hi";
?>
<br>
</body>
</html>
```

This is a valid .html file, with a PHP program embedded in it. The PHP program is in the middle, inside the `<?php` and `?>` tags. The rest of the file is basic HTML. Notice two things about this file:

+   - The `print` statement in the PHP code doesn't have a `\n` in it.
+   - The PHP code is followed by a `<br>` tag, which represents a newline in HTML.

Now think about this carefully: The PHP processor reads this file and sends out a file that is valid HTML. Each part of the file that is not part of the PHP code remains as is. But the PHP portion executes as a script, and in this case, that script prints out the word Hi. After processing, the PHP code in the HTML file is replaced by this output.

After the PHP processor runs, the resulting HTML file looks like this:

```
<html>
<head>
<title>Better Example</title>
</head>
<body>
Hi        <br>
</body>
</html>
```

The part that previously contained the PHP code was replaced by the output from the PHP code. The output is the word Hi.

But something might look a little odd here. Notice that the `<br>` tag, which was part of the original `.html` file and not part of the PHP code, is on the same line as the word Hi and spaced out a bit. Why is that? It's because